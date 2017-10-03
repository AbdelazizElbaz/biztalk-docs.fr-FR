---
title: "Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF service model, receiving polling-based messages
- how to, receive polling-based message
- polling-based messages, receiving by using the WCF service model
ms.assetid: 0324e8bf-d9d1-46f5-b896-b9fc8e61d514
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd36081bd92c3bfae13916ed7d984fcd5de9763f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-service-model"></a>Recevoir des Messages d’interrogation de données modifiées dans la base de données Oracle à l’aide du modèle de Service WCF
Vous pouvez configurer le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] réception reposant sur l’interrogation des données modifiées messages par rapport à une table Oracle ou une vue. Pour recevoir des messages de données modifiées, l’adaptateur exécute régulièrement une requête SQL sur une table Oracle ou d’une vue, suivi d’un bloc de code PL/SQL facultatif. Les résultats de la requête SQL sont ensuite retournées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à votre application comme fortement typée jeu de résultats en une opération POLLINGSTMT entrante. Pour plus d’informations sur le mécanisme utilisé pour configurer et effectuer d’interrogation sur Oracle de base de données à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md). Nous vous recommandons fortement de lire cette rubrique avant de continuer.  
  
 Pour recevoir l’opération POLLINGSTMT lorsque vous utilisez le modèle de service WCF, vous devez :  
  
-   Générer un contrat de service WCF (interface) pour l’opération POLLINGSTMT à partir des métadonnées exposées par l’adaptateur. Pour ce faire, vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe).  
  
-   Implémenter un service WCF à partir de cette interface.  
  
-   Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).  
  
 Les rubriques de cette section fournissent des informations et des procédures pour vous aider à effectuer d’interrogation sur des tables de base de données Oracle et les vues dans le modèle de service WCF.  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique utilisent la table /SCOTT/ACCOUNTACTIVITY et la fonction /SCOTT/Package/ACCOUNT_PKG/PROCESS_ACTIVITY. Un script pour générer ces artefacts est fourni avec les [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples. Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a>Configuration d’interrogation dans le modèle de Service WCF  
 Vous configurez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour effectuer d’interrogation sur des tables de base de données Oracle et des vues en définissant les propriétés de liaison et une propriété de connexion facultatifs (paramètre). Certaines de ces propriétés sont obligatoires, et certains, avoir un effet, doivent être définie à la fois au moment du design et au moment.  
  
-   Au moment du design, vous définissez les paramètres de connexion et les propriétés de liaison lorsque vous vous connectez à la base de données Oracle pour générer un contrat de service WCF.  
  
-   Lors de l’exécution, vous définissez des propriétés de liaison sur l’objet OracleDBBinding qui vous permet de créer l’hôte de service. Vous définissez le paramètre de connexion lorsque vous ajoutez un écouteur de service à l’hôte de service.  
  
 La liste suivante fournit une vue d’ensemble des propriétés de liaison et les paramètres de connexion utilisés pour configurer d’interrogation :  
  
-   Le **PollingStatement** propriété de liaison. Vous devez définir cette propriété de liaison à la fois au moment du design et au moment de l’exécution.  
  
-   Propriétés de liaison facultative. Ils doivent uniquement être définie au moment de l’exécution.  
  
-   Le **AcceptCredentialsInUri** propriété de liaison. Vous devez définir cette propriété de liaison **true** pendant l’exécution si vous souhaitez activer les informations d’identification dans l’URI de connexion. Le nom d’utilisateur et un mot de passe doivent être présents dans l’URI de connexion lorsque vous ajoutez un point de terminaison de service à l’hôte de service.  
  
-   Le **PollingId** dans l’URI de connexion paramètre de chaîne de requête. Si vous souhaitez modifier l’espace de noms de l’opération POLLINGSTMT, vous devez définir cette propriété de connexion à la fois au moment de la conception et d’exécution.  
  
 Pour obtenir une description complète des propriétés de liaison et les paramètres de connexion utilisés pour configurer l’interrogation, consultez [recevoir des messages d’interrogation de données modifiées dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).  
  
## <a name="the-wcf-service-contract-and-class"></a>Le contrat de Service WCF et la classe  
 Vous utilisez la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] ou le service Model Metadata Utility Tool (svcutil.exe) pour créer un service WCF service contrat (interface) et les classes de prise en charge pour l’opération POLLINGSTMT.  
  
 Lorsque vous vous connectez à la base de données Oracle avec un de ces outils pour générer un contrat de service pour l’opération POLLINGSTMT :  
  
-   Vous devez spécifier le **PollingStatement** propriété de liaison. L’adaptateur utilise l’instruction SELECT dans cette propriété de liaison pour générer les métadonnées correctes pour le jeu de résultats de fortement typé retourné par l’opération POLLINGSTMT.  
  
-   Vous pouvez éventuellement spécifier un paramètre PollingId dans l’URI de connexion. L’adaptateur utilise ce paramètre pour générer l’espace de noms pour l’opération POLLINGSTMT.  
  
 Dans les exemples suivants :  
  
-   **PollingStatement** est défini sur « Sélectionner * à partir de ACCOUNTACTIVITY de mise à jour ».  
  
-   **PollingId** est défini sur « AcctActivity ».  
  
### <a name="the-wcf-service-contract-interface"></a>Le contrat de Service WCF (Interface)  
 Le code suivant illustre le contrat de service WCF (interface) généré pour l’opération POLLINGSTMT.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03", ConfigurationName="POLLINGSTMT_OperationGroup")]  
public interface POLLINGSTMT_OperationGroup {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)  
    // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMT")]  
    void POLLINGSTMT(POLLINGSTMT request);  
}  
```  
  
### <a name="the-message-contracts"></a>Les contrats de Message  
 L’espace de noms de contrat de message est modifié par le paramètre PollingId dans l’URI de connexion. Le message de requête retourne un jeu d’enregistrements de fortement typée.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="POLLINGSTMT", WrapperNamespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", IsWrapped=true)]  
public partial class POLLINGSTMT {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity", Order=0)]  
    public microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD;  
  
    public POLLINGSTMT() {  
    }  
  
    public POLLINGSTMT(microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity.POLLINGSTMTRECORD[] POLLINGSTMTRECORD) {  
        this.POLLINGSTMTRECORD = POLLINGSTMTRECORD;  
    }  
}  
```  
  
### <a name="the-data-contract-namespace"></a>Le Namespace de contrat de données  
 Un contrat de données est un contrat formel entre un service et un client qui due décrit l’échange de données. Autrement dit, afin de communiquer, le client et le service est inutile de partager les mêmes types, les mêmes contrats de données.  
  
 En cas de données des messages de modification, l’espace de noms de contrat de données est également modifiée par le paramètre PollingId (si spécifiée) dans l’URI de connexion. Le contrat de données se compose d’une classe qui représente un enregistrement dans le jeu de résultats de requête fortement typée. Dans cet exemple, les détails de la définition de classe sont omis. La classe contient des propriétés qui représentent les colonnes dans le jeu de résultats.  
  
 Dans l’exemple suivant, la PollingId « AcctActivity » est utilisé.  
  
```  
namespace microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity {  
    using System.Runtime.Serialization;  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
    [System.Runtime.Serialization.DataContractAttribute(Name="POLLINGSTMTRECORD", Namespace="http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity")]  
    public partial class POLLINGSTMTRECORD : object, System.Runtime.Serialization.IExtensibleDataObject {…}  
     }  
}  
```  
  
### <a name="wcf-service-class"></a>Classe de Service WCF  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface). Le nom du fichier est OracleDBBindingService.cs. Vous pouvez insérer la logique pour traiter l’opération POLLINGSTMT directement dans cette classe. Si vous utilisez svcutil.exe pour générer l’interface de contrat de service, vous devez implémenter cette classe vous-même. Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
```  
namespace OracleDBBindingNamespace {  
  
    public class OracleDBBindingService : POLLINGSTMT_OperationGroup {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://Microsoft.LobServices.OracleDB/2007/03/POLLINGSTMTAcctActivity)   
        // of message POLLINGSTMT does not match the default value (http://Microsoft.LobServices.OracleDB/2007/03)  
        public virtual void POLLINGSTMT(POLLINGSTMT request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-the-pollingstmt-operation"></a>Réception de l’opération POLLINGSTMT  
  
#### <a name="to-receive-polling-data-from-the-oracle-database-adapter"></a>Pour recevoir des données de l’interrogation de l’adaptateur de base de données Oracle  
  
1.  Utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou svcutil.exe pour générer un service WCF service contrat (interface) et des classes d’assistance pour l’opération POLLINGSTMT. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-wcf-client-or-wcf-service-contract-for-oracle-db-solution-artifacts.md). Au minimum, vous devez définir le **PollingStatement** propriété de liaison lorsque vous vous connectez à l’adaptateur. Vous pouvez éventuellement spécifier un paramètre PollingId dans l’URI de connexion. Si vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous devez définir tous les paramètres de liaison est nécessaire pour votre configuration. Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.  
  
2.  Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1. La méthode POLLINGSTMT de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur s’est produite le traitement des données provenance de l’opération POLLINGSTMT ; Sinon, la méthode ne retourne rien. Vous devez attribuer la classe de service WCF comme suit :  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
    1.  Si vous avez utilisé le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer l’interface, vous pouvez implémenter votre logique directement dans le **POLLINGSTMT** méthode dans le texte généré **OracleDBBindingService** classe. Cette classe peut être trouvée dans OracleDBBindingService.cs. Ce code dans cet exemple montre comment des classes le **OracleDBBindingService** classe.  
  
        ```  
        [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
        public class PollingStmtService : OracleDBBindingService  
        {  
            public override void POLLINGSTMT(POLLINGSTMT request)  
            {  
                Console.WriteLine("\nNew Polling Records Received");  
                Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
                for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
                {  
                    Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                        request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                        request.POLLINGSTMTRECORD[i].AMOUNT,  
                                        request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                        request.POLLINGSTMTRECORD[i].DESCRIPTION);  
                }  
            }  
        }  
        ```  
  
    2.  Si vous utilisez svcutil.exe pour générer l’interface, vous devez créer un service WCF qui implémente l’interface et implémenter votre logique dans le **POLLINGSTMT** méthode de cette classe.  
  
3.  Créez une instance du service WCF créé à l’étape 2.  
  
    ```  
    // create service instance  
    PollingStmtService pollingInstance = new PollingStmtService();  
    ```  
  
4.  Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base. L’URI de la connexion de base ne peut pas contenir userinfoparams ou un query_string.  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracledb://Adapter") };  
    ServiceHost srvHost = new ServiceHost(pollingInstance, baseUri);  
    ```  
  
5.  Créer un **OracleDBBinding** et configurer l’opération d’interrogation en définissant ses propriétés de liaison. Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration. Au minimum, vous devez spécifier l’instruction de l’interrogation et l’intervalle d’interrogation. Dans cet exemple, vous spécifiez les informations d’identification en tant que partie de l’URI que vous devez également attribuer le **AcceptCredentialsInUri** à **true**.  
  
    ```  
    // Create and configure a binding for the service endpoint. NOTE: binding  
    // parameters are set here for clarity, but these are already set in the  
    // the generated configuration file  
    OracleDBBinding binding = new OracleDBBinding();  
  
    // The credentials are included in the connection URI, so set this property to true  
    binding.AcceptCredentialsInUri = true;  
  
    // Same as statement specified in Configure Adapter dialog box  
    binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
    // Be sure to set the interval long enough to complete processing before  
    // the next poll  
    binding.PollingInterval = 15;  
    // Polling is transactional; be sure to set an adequate isolation level   
    // for your environment  
    binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
    ```  
  
6.  Ajouter un point de terminaison de service à l’hôte de service. Pour effectuer cette opération :  
  
    -   Utilisez la liaison créée à l’étape 5.  
  
    -   Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un PollingId.  
  
    -   Spécifiez le contrat en tant que « POLLINGSTMT_OperationGroup ».  
  
    ```  
    // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
    Uri serviceUri = new Uri("oracledb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
    srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
    ```  
  
7.  Pour recevoir les données d’interrogation, ouvrez l’hôte de service. L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.  
  
    ```  
    // Open the service host to begin polling  
    srvHost.Open();  
    ```  
  
8.  Pour mettre fin à l’interrogation, fermez l’hôte de service.  
  
    > [!IMPORTANT]
    >  La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.  
  
    ```  
    srvHost.Close();  
    ```  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre une requête d’interrogation qui s’exécute sur la table ACCOUNTACTIVITY/SCOTT. L’instruction après interrogation appelle une fonction d’Oracle qui déplace les enregistrements traités à une autre table /SCOTT/ACCOUNTHISTORY. L’espace de noms de l’opération POLLINGSTMT est modifié en définissant le paramètre PollingId à « AccountActivity » dans l’URI de connexion. Dans cet exemple, le service WCF pour l’opération POLLINGSTMT est créé en définissant une sous-classe généré **OracleDBBindingService** classe ; Toutefois, vous pouvez implémenter votre logique directement dans la classe générée.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add these three references to use the Oracle adapter  
using System.ServiceModel;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
using microsoft.lobservices.oracledb._2007._03.POLLINGSTMTAcctActivity;  
using OracleDBBindingNamespace;  
  
namespace OraclePollingSM  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingStmtService : OracleDBBindingService  
    {  
        public override void POLLINGSTMT(POLLINGSTMT request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("Tx Id\tAccount\tAmount\tDate\t\t\tDescription");  
            for (int i = 0; i < request.POLLINGSTMTRECORD.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}\t{4}", request.POLLINGSTMTRECORD[i].TID,  
                                    request.POLLINGSTMTRECORD[i].ACCOUNT,  
                                    request.POLLINGSTMTRECORD[i].AMOUNT,  
                                    request.POLLINGSTMTRECORD[i].TRANSDATE,  
                                    request.POLLINGSTMTRECORD[i].DESCRIPTION);  
  
            }  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
         }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost srvHost = null;  
  
            // This URI is used to specify the address for the ServiceEndpoint  
            // It must contain credentials and the PollingId (if any) that was used to generate  
            // the WCF service callback interface  
            Uri serviceUri = new Uri("OracleDb://User=SCOTT;Password=TIGER@Adapter?PollingId=AcctActivity");  
  
            // This URI is used to initialize the ServiceHost. It cannot contain  
            // userinfoparms (credentials) or a query_string (PollingId); otherwise,  
            // an exception is thrown when the ServiceHost is initialized.  
            Uri[] baseUri = new Uri[] { new Uri("OracleDb://Adapter") };  
  
            Console.WriteLine("Sample started, initializing service host -- please wait");  
  
            // create an instanc of the WCF service callback class  
            PollingStmtService pollingInstance = new PollingStmtService();  
  
            try  
            {  
                // Create a ServiceHost with the service callback instance and a base URI (address)  
                srvHost = new ServiceHost(pollingInstance, baseUri);  
  
                // Create and configure a binding for the service endpoint. Note: binding  
                // parameters are set here for clarity but these are already set in the  
                // generated configuration file  
                //  
                // The following properties are set  
                //    AcceptCredentialsInUri (true) to enable credentials in the connection URI for AddServiceEndpoint  
                //    PollingStatement  
                //    PostPollStatement calls PROCESS_ACTIVITY on Oracle. This procedure moves the queried records to  
                //                      the ACCOUNTHISTORY table  
                //    PollingInterval (15 seconds)  
                //    TransactionIsolationLevel   
  
                OracleDBBinding binding = new OracleDBBinding();  
  
                // The Credentials are included in the Connection Uri so set this property true  
                binding.AcceptCredentialsInUri = true;  
  
                // Same as statement specified in Configure Adapter dialog box  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Be sure to set the interval long enough to complete processing before  
                // the next poll  
                binding.PollingInterval = 15;  
  
                // Polling is transactional, be sure to set an adequate isolation level   
                // for your environment  
                binding.TransactionIsolationLevel = TransactionIsolationLevel.ReadCommitted;  
  
                // Add service endpoint: be sure to specify POLLINGSTMT_OperationGroup as the contract  
                srvHost.AddServiceEndpoint("POLLINGSTMT_OperationGroup", binding, serviceUri);  
  
                Console.WriteLine("Opening the service host");  
                // Open the service host to begin polling  
                srvHost.Open();  
  
                // Wait to receive request  
                Console.WriteLine("\nPolling started. Returned records will be written to the console.");  
                Console.WriteLine("Hit <RETURN> to stop polling");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an Oracle Error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (srvHost.State == CommunicationState.Opened)  
                    srvHost.Close();  
                else  
                    srvHost.Abort();  
            }  
  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md)