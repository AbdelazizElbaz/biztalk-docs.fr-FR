---
title: "Recevoir des appels entrants de RFC dans SAP à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving inbound RFC calls
- RFC calls, receiving inbound using the WCF service model
ms.assetid: 064d70d7-1603-467f-9aba-ecab78a567ff
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a415e3ab0ecbaab8778254d817241e5cafb61a92
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model"></a>Recevoir des appels entrants de RFC dans SAP à l’aide du modèle de Service WCF
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] peut agir comme un serveur RFC pour recevoir les documents RFC appelées par un système SAP.  
  
 Pour recevoir les documents RFC entrants dans le modèle de service WCF, vous devez :  
  
-   Vérifiez l’existence d’une destination RFC sur le système SAP.  
  
-   Vérifiez que le document RFC est défini sur le système SAP.  
  
-   Générer un contrat de service WCF (interface) pour l’opération de RFC à partir des métadonnées exposées par l’adaptateur. Pour ce faire, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe).  
  
-   Implémenter un service WCF à partir de cette interface. Les méthodes du service WCF contient la logique nécessaire pour traiter le document RFC et renvoie une réponse à l’adaptateur (et par conséquent, le système SAP).  
  
-   Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).  
  
 Les sections suivantes vous montrent comment recevoir les RFC à partir du système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="how-to-set-up-the-sap-system-to-send-an-rfc-to-the-sap-adapter"></a>Comment faire pour configurer le système SAP pour envoyer une demande de changement de l’adaptateur SAP  
 Avant d’envoyer une demande de changement du système SAP pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], vous devez vous assurer que les éléments suivants sont remplies sur le système SAP :  
  
-   Une destination RFC pour les [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] doit exister. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] s’inscrit auprès d’une destination RFC pour recevoir les documents RFC à partir du système SAP. Vous fournissez des paramètres dans la connexion SAP URI tel que l’hôte de passerelle SAP, le Service de passerelle SAP et l’ID de programme SAP que l’adaptateur utilise pour s’inscrire. Pour plus d’informations sur la configuration d’une destination RFC sur SAP, consultez [créer une demande de changement, la destination RFC et envoyer une demande de changement à partir du système SAP](creating-an-rfc-in-an-sap-system.md).  
  
-   Le document RFC doit être défini sur le système SAP. Vous devez créer un module de fonction qui définit la RFC sur le système SAP. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise la définition de la RFC sur le système SAP pour récupérer des métadonnées sur le document RFC (à la fois au moment du design et au moment de l’exécution). Pour plus d’informations, consultez [création d’une commande RFC dans un système SAP](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md).  
  
    > [!NOTE]
    >  Vous devez définir le RFC sur le système SAP. Toutefois, vous implémentez le RFC dans votre code client de l’adaptateur. Le document RFC doit être défini sur le système SAP afin que l’adaptateur peut récupérer les métadonnées pour le document RFC.  
  
 Voici un exemple de code source sur le système SAP pour une commande RFC qui ajoute deux entiers et retourne son résultat. Le code appelle simplement la RFC via une destination spécifique. L’implémentation de la fonction est effectuée le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] code client.  
  
```  
FUNCTION Z_RFC_SAMPLE_ADD.  
*"---------------------------------------------------------------------*"*"Local interface:  
*"  IMPORTING  
*"     VALUE(X) TYPE  INT4  
*"     VALUE(Y) TYPE  INT4  
*"     VALUE(DEST) TYPE  CHAR20 DEFAULT 'SAPADAPTER'  
*"  EXPORTING  
*"     VALUE(RESULT) TYPE  INT4  
*"---------------------------------------------------------------------CALL FUNCTION 'Z_RFC_MKD_ADD' DESTINATION DEST  
  EXPORTING X = X  
            Y = Y  
  IMPORTING RESULT = RESULT.  
  
ENDFUNCTION.  
```  
  
## <a name="the-wcf-service-contract-for-an-rfc"></a>Le contrat de Service WCF pour une demande de changement  
 Vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour générer un contrat de service WCF pour les documents RFC que vous souhaitez recevoir à partir du système SAP. Les sections suivantes présentent les classes de code managé et les interfaces générées pour l’opération Z_RFC_MKD_ADD.  
  
### <a name="the-rfc-interface-wcf-service-contract"></a>L’Interface de Rfc (contrat de service WCF)  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] couvre toutes les opérations de RFC sous un contrat de service unique, « Rfc ». Cela signifie qu’une seule interface, **Rfc**, est créé pour toutes les opérations RFC que vous souhaitez recevoir. Chaque opération de RFC cible est représentée comme une méthode de cette interface. Chaque méthode prend un seul paramètre, qui représente le contrat de message pour le message de demande de l’opération et retourne un objet qui représente le contrat de message du message de réponse de l’opération.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/", ConfigurationName="Rfc")]  
public interface Rfc {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
    [System.ServiceModel.OperationContractAttribute(Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD", ReplyAction="http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD/response")]  
    Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request);  
}  
  
```  
  
### <a name="the-request-and-response-messages"></a>La demande et les Messages de réponse  
 Chaque opération RFC prend un paramètre qui représente le message de demande et retourne un objet qui représente le message de réponse. Les propriétés du message de demande contiennent l’importation et les paramètres de modification (entrées) de la RFC. Les propriétés du message de réponse contiennent l’exportation et (sortie) de modification des paramètres pour l’opération.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADD", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", IsWrapped=true)]  
public partial class Z_RFC_MKD_ADDRequest {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=0)]  
    public string DEST;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=1)]  
    public System.Nullable<int> X;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=2)]  
    public System.Nullable<int> Y;  
  
    public Z_RFC_MKD_ADDRequest() {  
    }  
  
    public Z_RFC_MKD_ADDRequest(string DEST, System.Nullable<int> X, System.Nullable<int> Y) {  
        this.DEST = DEST;  
        this.X = X;  
        this.Y = Y;  
    }  
}  
  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Z_RFC_MKD_ADDResponse", WrapperNamespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", IsWrapped=true)]  
public partial class Z_RFC_MKD_ADDResponse {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.Sap/2007/03/Rfc/", Order=0)]  
    public int RESULT;  
  
    public Z_RFC_MKD_ADDResponse() {  
    }  
  
    public Z_RFC_MKD_ADDResponse(int RESULT) {  
        this.RESULT = RESULT;  
    }  
}  
```  
  
### <a name="the-generated-wcf-service"></a>Le Service WCF généré  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un service WCF qui implémente le contrat de service WCF (**Rfc**). Les méthodes de cette classe sont extraites. Cette classe est générée dans un fichier distinct. Vous pouvez implémenter votre code directement dans les méthodes de cette classe.  
  
```  
namespace SAPBindingNamespace {  
  
    public class SAPBindingService : Rfc {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.Sap/2007/03/Rfc/) of message Z_RFC_MKD_ADDRequest does not match the default value (http://Microsoft.LobServices.Sap/2007/03/)  
        public virtual Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="how-to-create-an-rfc-server-application"></a>Comment créer une Application de serveur RFC  
 Pour recevoir les documents RFC à partir du système SAP à l’aide du modèle de service WCF, vous pouvez suivre les étapes de [vue d’ensemble du modèle de Service WCF avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/overview-of-the-wcf-service-model-with-the-sap-adapter.md). Veillez à spécifier 'Rfc' pour le contrat de service lorsque vous ajoutez le point de terminaison de service (étape 6 de la procédure de création et implémentation d’un service WCF).  
  
 Le code suivant montre un exemple complet de la réception de la Z_RFC_MKD_RFC à partir d’un système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Ce document RFC accepte deux paramètres entier et retourne le résultat dans le système SAP.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and SAP adapter namepaces  
using System.ServiceModel;  
using Microsoft.Adapters.SAP;  
using Microsoft.ServiceModel.Channels;  
  
// Include this namespace for the WCF LOB Adapter SDK and SAP adapter exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace SapRfcServerSM  
{  
    // Implement a WCF service callback class by sub-classing the generated service callback class (SAPBindingService).  
    // You must annotate this class with the InstanceContextMode.Single ServiceBehavior  
    // If you implement your code in SAPBindingService.cs be sure to annotate the SAPBindingService class  
    // The callback method should return a Z_RFC_MKD_ADDResponse to indicate successful processing  
    // or throw an exception to indicate an error.  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single,UseSynchronizationContext = false)]  
    class RfcServerClass : SAPBindingNamespace.SAPBindingService  
    {  
  
        public override Z_RFC_MKD_ADDResponse Z_RFC_MKD_ADD(Z_RFC_MKD_ADDRequest request)  
        {  
            // If either parameter is null, throw an exception   
            if (request.X == null || request.Y == null)  
                throw new System.ArgumentNullException();  
  
            int result = (int) (request.X + request.Y);  
  
            Console.WriteLine("\nRfc Received");  
            Console.WriteLine("X =\t\t" + request.X.ToString());  
            Console.WriteLine("Y =\t\t" + request.Y.ToString());  
            Console.WriteLine("Result =\t" + result);  
            Console.WriteLine("\nHit <RETURN> to end");  
  
            return new Z_RFC_MKD_ADDResponse(result);  
        }  
  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Listener connection for the service URI -- the connection URI must contain credentials  
            Uri serviceUri = new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/ADAPSAP47/00?ListenerGwServ=SAPGW00&ListenerGwHost=ADAPSAP47&ListenerProgramId=ADDER");  
  
            // The baseUri cannot contain userinfoparams or query_string parameters  
            Uri[] baseUri = new Uri[] { new Uri("sap://a/ADAPSAP47/00") };  
  
            Console.WriteLine("RFC server sample started");  
  
            // create service instance  
            RfcServerClass rfcServerInstance = new RfcServerClass();  
  
            try  
            {  
                Console.WriteLine("Initializing service host -- please wait");  
                // Create and initialize a service host  
                using (ServiceHost srvHost = new ServiceHost(rfcServerInstance, baseUri))  
                {  
  
                    // Add service endpoint   
                    // Specify AcceptCredentalsInUri=true for the binding  
                    // NOTE: The contract for the service endpoint is "Rfc".  
                    //       This is the generated WCF service callback interface (see SAPBindingInterface.cs).  
                    SAPBinding binding = new SAPBinding();  
                    binding.AcceptCredentialsInUri = true;  
                    srvHost.AddServiceEndpoint("Rfc", binding, serviceUri);  
                    srvHost.Open();  
  
                    Console.WriteLine("\nReady to receive Z_RFC_MKD_ADD RFC");  
                    Console.WriteLine("Hit <RETURN> to end");  
  
                    // Wait to receive request  
                    Console.ReadLine();  
                }  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the SAP system");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the SAP system");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md)   
 [Schémas de message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)