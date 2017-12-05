---
title: "Envoyer des IDOC à SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, sending IDOCs to SAP
- IDOCs, sending to SAP by using the WCF service model
ms.assetid: 84077234-b82b-4e88-b858-ce2cb1383fb4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d9d550887271e2ba54d858456347ea85825554e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="send-idocs-to-sap-using-the-wcf-service-model"></a>Envoyer des IDOC à SAP à l’aide du modèle de Service WCF
En interne, le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] envoie IDOC au système SAP en appelant une des deux normes RFC suivantes :  
  
-   IDOC_INBOUND_ASYNCHRONOUS des IDOC de version 3.  
  
-   INBOUND_IDOC_PROCESS des IDOC de version 2.  
  
 Vous pouvez envoyer un IDOC à l’adaptateur en appelant le RFC (ou tRFC) ; Toutefois, vous pouvez également utiliser les deux opérations suivantes pour envoyer des IDOC à la carte :  
  
-   **SendIdoc** apparaissent directement sous le nœud racine IDOC. L’opération SendIdoc envoie l’IDOC comme données (faiblement typée) de chaîne pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   **Envoyer** apparaissent individuellement pour chaque IDOC. L’opération d’envoi envoie l’IDOC en tant que données fortement typées pour les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
 Ces opérations de déterminent la façon dont les données IDOC sont envoyées à l’adaptateur, pas comment il est envoyé au système SAP. L’adaptateur envoie toujours l’IDOC au système SAP à l’aide de la tRFC appropriée.  
  
 Étant donné que le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] envoie l’IDOC comme un tRFC, les opérations de l’envoi et la SendIdoc présentent un paramètre GUID qui vous permet de confirmer (commit) l’IDOC. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en interne mappe ce GUID à l’aide de la transaction SAP ID (TID) qui est associé à le tRFC. Vous pouvez vérifier l’IDOC de deux manières :  
  
-   À l’aide de la **AutoConfirmSentIdocs** propriété de liaison. Si cette propriété de liaison est définie à **true**, l’adaptateur confirme automatiquement le tRFC permet d’envoyer l’IDOC.  
  
-   En appelant RfcConfirmTransID. Vous appelez cette opération avec le GUID associé à l’IDOC.  
  
 Les sections suivantes vous montrent comment envoyer des IDOC à un système SAP en utilisant les opérations SendIdoc et d’envoi. Pour plus d’informations pour vous aider à envoyer un IDOC comme un tRFC, consultez [appeler tRFCs dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md).  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
  
### <a name="the-sendidoc-operation"></a>L’opération SendIdoc  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence une seule opération (et le contrat de service) pour envoyer un IDOC sous forme de chaîne. Le nom du contrat de service est « Idoc » et de la classe de client WCF est **IdocClient**.  
  
 Vous pouvez envoyer n’importe quel IDOC à SAP à l’aide de ce client. Il contient une méthode unique, **SendIdoc**, qui accepte deux paramètres :  
  
-   **idocData** est une chaîne qui contient les données IDOC  
  
-   **GUID** GUID qui est mappé sur le TID SAP.  
  
 Le code suivant illustre le client WCF qui est généré pour l’opération SendIdoc.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocClient : System.ServiceModel.ClientBase<Idoc>, Idoc {  
  
    public void SendIdoc(string idocData, ref System.Nullable\<System.Guid\> guid) {…}  
}  
```  
  
### <a name="the-send-operation"></a>L’opération d’envoi  
 Étant donné que l’opération d’envoi utilise les données fortement typées, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence un contrat de service unique pour chaque IDOC. Le nom de l’interface (et la classe de client WCF) généré pour ce contrat est basé sur le type IDOC, une version, un numéro de version et un type CIM (le cas échéant). Par exemple pour l’IDOC ORDERS03.v3.620, l’interface est nommé « IdocORDERS03V3R620 » et la classe de client WCF est **IdocORDERS03V3R620Client**.  
  
 Vous devez générer un client unique pour chaque type d’IDOC. Ce client contient une méthode unique, **envoyer**, qui accepte deux paramètres :  
  
-   **idocData** est une classe qui représente les données IDOC fortement typée.  
  
-   **GUID** est une représentation de chaîne du GUID qui est mappé sur le TID SAP.  
  
 Le code suivant illustre le client WCF qui est généré pour l’opération d’envoi signalée pour l’IDOC ORDERS03.v3.620.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class IdocORDERS03V3R620Client : System.ServiceModel.ClientBase<IdocORDERS03V3R620>, IdocORDERS03V3R620 {  
  
    ...  
  
    public void Send(ORDERS03 idocData, ref string guid) { ... }  
}  
```  
  
## <a name="how-to-create-an-application-to-send-idocs"></a>Comment créer une Application pour envoyer des IDOC  
 Pour envoyer un IDOC à un système SAP, procédez comme suit.  
  
#### <a name="to-send-an-idoc-to-an-sap-system"></a>Pour envoyer un IDOC à un système SAP  
  
1.  Générer une classe de client WCF. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer la classe de client WCF qui cible l’IDOC avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [génération d’un Client WCF ou un contrat de Service WCF pour les artefacts de Solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md). Si vous souhaitez confirmer explicitement IDOC, assurez-vous que vous générez le client WCF pour l’opération RfcConfirmTransID. Vous trouverez des opérations sous les nœuds suivants :  
  
    -   Opération SendIdoc. Directement sous le nœud IDOC.  
  
    -   Opération d’envoi. Sous le nœud correspondant au numéro de version, la version et type de la cible IDOC.  
  
    -   Opération RfcConfirmTransID. Directement sous le nœud TRFC.  
  
2.  Créez une instance de la classe de client WCF générée à l’étape 1, et spécifier une liaison de client. Spécification d’une liaison de client implique la spécification de la liaison et l’adresse de point de terminaison utilisé par le client WCF. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md). Le code suivant initialise un IdocClient (pour l’opération d’envoi) à partir de la configuration et définit les informations d’identification pour le système SAP.  
  
    ```  
    SAPBinding binding = new SAPBinding();  
  
    // Set endpoint address  
    EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
    // Create client and set credentials  
    idocClient = new IdocClient(binding, endpointAddress);  
    idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
    idocClient.ClientCredentials.UserName.Password = "YourPassword";;  
    ```  
  
3.  Si vous souhaitez que la carte pour confirmer la tRFC sur le système SAP après qu’il envoie l’IDOC, définissez la **AutoConfirmSentIdocs** liaison de propriété **true**. Vous devez le faire avant d’ouvrir le client WCF.  
  
    ```  
    // Set AutoConfirmSentIdocs property to true  
    binding.AutoConfirmSentIdocs = true;  
    ```  
  
4.  Ouvrez le client WCF.  
  
    ```  
    idocClient.Open();  
    ```  
  
5.  Appelez la méthode appropriée sur le client WCF créé à l’étape 2 pour envoyer l’IDOC au système SAP. Vous pouvez passer une variable qui contient un GUID ou qui a la valeur **null** pour le **guid** paramètre. Si vous ne spécifiez pas un GUID, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère un pour l’opération (**guid** est un **ref** paramètre). Le code suivant lit un IDOC (au format de chaîne) à partir d’un fichier et l’envoie au système SAP à l’aide de l’opération SendIdoc.  
  
    ```  
    // Read IDOC into string variable  
    using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
    {  
    idocData = reader.ReadToEnd();  
    }  
  
    //Get a new GUID to pass to SendIdoc. You can also assign a null  
    //value to have the adapter generate a GUID.  
    adapterTxGuid = Guid.NewGuid();  
  
    //Invoke SendIdoc on the client to send the IDOC to the SAP system  
    idocClient.SendIdoc(idocData, ref adapterTxGuid);  
    ```  
  
6.  Si vous n’avez pas défini la **AutoConfirmSentIdocs** liaison de propriété **true** (à l’étape 3), vous devez confirmer le tRFC sur le système SAP. Pour cela, vous devez appeler la **RfcConfirmTransID** méthode sur un **TrfcClient** (création ne pas affichée). Spécifiez que le GUID est renvoyé à l’étape 4 pour le paramètre.  
  
    ```  
    trfcClient.RfcConfirmTransID(adapterTxGuid);  
    ```  
  
7.  Fermez le client WCF (et **TrfcClient**, le cas échéant) quand vous avez terminé l’utiliser (une fois que vous avez terminé l’envoi IDOC).  
  
    ```  
    idocClient.Close();   
    ```  
  
### <a name="example"></a>Exemple  
 L’exemple suivant envoie un IDOC à un système SAP à l’aide de la méthode SendIdoc. L’IDOC est lu à partir d’un fichier, ORDERS03.txt. Ce fichier contient un ORDERS03. V3.620 IDOC et est inclus avec les exemples ; Toutefois, l’opération de SendIdoc peut être utilisée pour envoyer n’importe quel IDOC.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.IO;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for WCF LOB Adapter SDK and SAP exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
// This example sends a flat IDOC to the SAP system by using the SendIdoc operation.  
namespace SapIdocStringClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // variable for the IDOC client  
            IdocClient idocClient = null;  
  
            Console.WriteLine("IDOC string client sample started");  
            try  
            {  
                // Variable for the GUID  
                System.Nullable<System.Guid> adapterTxGuid;  
                // string to hold the Idoc data  
                string idocData;  
                // string to hold the SAP transaction ID (TID)  
                string sapTxId;  
  
                // The client can be configured from app.config, but it is   
                // explicitly configured here for demonstration.  
                // set AutoConfirmSentIdocs property to true  
                SAPBinding binding = new SAPBinding();  
                binding.AutoConfirmSentIdocs = true;  
  
                // Set endpoint address  
                EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPServer/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
                // Create client and set credentials  
                idocClient = new IdocClient(binding, endpointAddress);  
                idocClient.ClientCredentials.UserName.UserName = "YourUserName";  
                idocClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                // Open the client and send the Idoc  
                idocClient.Open();  
  
                // Read IDOC into string variable  
                using (StreamReader reader = new StreamReader("ORDERS03.txt"))  
                {  
                    idocData = reader.ReadToEnd();  
                }  
  
                //Get a new GUID to pass to SendIdoc. You can also assign a null.  
                //value to have the adapter generate a GUID.  
                adapterTxGuid = Guid.NewGuid();  
  
                //Invoke SendIdoc on the client to send the IDOC to the SAP system.  
                idocClient.SendIdoc(idocData, ref adapterTxGuid);  
  
                // The AutoConfirmSentIdocs binding property is set to true, so there is no need to  
                // confirm the IDOC. If this property is not set to true, you must call the   
                // RfcConfirmTransID method of a TrfcClient with adapterTxGuid to   
                // confirm the transaction on the SAP system.   
  
                // Get SAP tx id from GUID  
                sapTxId = SAPAdapterUtilities.ConvertGuidToTid((Guid) adapterTxGuid);  
  
                Console.WriteLine("IDOC sent");  
                Console.WriteLine("The SAP Transaction Id is : " + sapTxId);  
  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // Close the IDOC client  
                if (idocClient != null)  
                {  
                    if (idocClient.State == CommunicationState.Opened)  
                        idocClient.Close();  
                    else  
                        idocClient.Abort();  
                }  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)