---
title: "Appeler les RFC dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invoking RFCs, using the WCF service model
- WCF service model, invoking RFCs
ms.assetid: 06a373e2-5d16-4480-81ec-611bd0b9749c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8a18e9ae4990ecd5e85c57fc86919f239d51cbe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-rfcs-in-sap-using-the-wcf-service-model"></a>Appeler les RFC dans SAP à l’aide du modèle de Service WCF
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] met en évidence les RFC sur le système SAP en tant qu’opérations qui peuvent être appelées par un programme client. Dans le modèle de service WCF, ces opérations sont appelées en tant que méthodes d’une classe de client WCF générée. Vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF qui contient des méthodes pour chaque RFC que vous souhaitez appeler dans votre code. Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également des types .NET pour encapsuler les paramètres et types de données qui sont utilisés par chaque RFC. Vous pouvez ensuite créer une instance de cette classe de client WCF et appeler ses méthodes pour appeler la cible de RFC.  
  
 Les sections suivantes vous montrent comment appeler les RFC sur le système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="the-wcf-client-class"></a>La classe de Client WCF  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] couvre toutes les opérations de RFC sous un contrat de service unique, « Rfc ». Cela signifie qu’une seule classe de client WCF, **RfcClient**, est créé pour toutes les opérations RFC que vous souhaitez appeler. Chaque cible RFC est représentée comme une méthode de cette classe. Dans chaque méthode :  
  
-   Paramètres d’exportation SAP sont exposés en tant que **hors** paramètres  
  
-   Les paramètres de modification de SAP sont exposés en tant que **ref** paramètres.  
  
-   Les types SAP complexes telles que les structures sont signalées en tant que classes .NET avec des propriétés qui correspondent aux champs de type SAP. Ces classes sont définies dans l’espace de noms suivant : microsoft.lobservices.sap._2007._03.Types.Rfc.  
  
 Le code suivant montre une partie de la **RfcClient** classe et la méthode qui appelle SD_RFC_CUSTOMER_GET sur le système SAP.  
  
```  
 [System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
public partial class RfcClient : System.ServiceModel.ClientBase<Rfc>, Rfc {  
  
    ...  
  
    /// <summary>The metadata for this RFC was generated using the RFC SDK.</summary>  
    /// <param name="KUNNR">Customer number</param>  
    /// <param name="NAME1">Name of the customer</param>  
    /// <param name="CUSTOMER_T">Table of the selected customers</param>  
    /// <returns></returns>  
    public void SD_RFC_CUSTOMER_GET(string KUNNR, string NAME1, ref microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] CUSTOMER_T) {...}  
}  
```  
  
## <a name="how-to-create-an-rfc-client-application"></a>Comment créer une Application cliente RFC  
 Pour créer une application cliente RFC, procédez comme suit.  
  
#### <a name="to-create-an-rfc-client-application"></a>Pour créer une application cliente RFC  
  
1.  Générer un **RfcClient** classe. Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un **RfcClient** classe ciblant les RFC avec lequel vous souhaitez travailler. Pour plus d’informations sur la façon de générer un client WCF, consultez [générer un Client WCF ou un contrat de Service WCF pour les artefacts de Solution SAP](../../adapters-and-accelerators/adapter-sap/generate-a-wcf-client-or-a-wcf-service-contract-for-sap-solution-artifacts.md).  
  
2.  Créez une instance de la **RfcClient** classe généré à l’étape 1, et spécifier une liaison de client. Spécification d’une liaison de client implique la spécification de la liaison et le point de terminaison adresse utilisée par le **RfcClient** utilisera. Ce faire, vous pouvez soit impérativement dans du code ou de façon déclarative dans la configuration. Pour plus d’informations sur la façon de spécifier une liaison de client, consultez [configurer une liaison de Client pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-a-client-binding-for-the-sap-system.md). Le code suivant initialise les **RfcClient** à partir de la configuration et définit les informations d’identification pour le système SAP.  
  
    ```  
    RfcClient rfcClient = new RfcClient("SAPBinding_Rfc");  
  
    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
    ```  
  
3.  Ouvrez le client WCF.  
  
    ```  
    rfcClient.Open();  
    ```  
  
4.  Appeler des méthodes sur le **RfcClient** créé à l’étape 2 pour effectuer des opérations sur le système SAP. Le code suivant appelle la **SD_RFC_CUSTOMER_GET** méthode de la **RfcClient** pour appeler le RFC sur le système SAP.  
  
    ```  
    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers =   
        new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
    ```  
  
5.  Fermez le client WCF.  
  
    ```  
    rfcClient.Close();   
    ```  
  
### <a name="example"></a>Exemple  
 Voici un exemple de code complet qui appelle SD_RFC_CUSTOMER_GET pour retourner une liste de clients avec des noms qui commencent par « AB » et écrit le nom et l’ID de chaque client dans la console. Cet exemple crée la **RfcClient** à l’intérieur d’un **à l’aide de** instruction. Il n’est pas nécessaire de fermer explicitement le **RfcClient**; va être fermée lorsque le chemin d’exécution quitte le contexte.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.SAP;  
  
namespace SapRfcClientSM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            try  
            {  
                // Create client from configuration  
                using (RfcClient rfcClient = new RfcClient("SAPBinding_Rfc"))  
                {  
  
                    rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
                    rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
  
                    // Open client  
                    rfcClient.Open();  
  
                    microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[] customers = new microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST[0];  
  
                    // Invoke SD_RFC_CUSTOMER_GET  
                    rfcClient.SD_RFC_CUSTOMER_GET(string.Empty, "AB*", ref customers);  
  
                    // Write the results to the console  
                    foreach (microsoft.lobservices.sap._2007._03.Types.Rfc.RFCCUST customer in customers)  
                    {  
                        Console.WriteLine("Customer Name = " + customer.NAME1);  
                        Console.WriteLine("         Id   = " + customer.KUNNR);  
                        Console.WriteLine();  
                    }  
                }  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
                if (ex.InnerException != null)  
                    Console.WriteLine("Inner exception is :" + ex.InnerException);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [Schémas de message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)