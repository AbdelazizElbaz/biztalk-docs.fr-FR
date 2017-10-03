---
title: "Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 521d58e4-73b1-48a8-9a0a-9e733386c1b5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2cac950ced0fb0d7133e99bc3d12699f9379bcb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-select-statement-with-the-wcf-service-model"></a>Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT avec le modèle de service WCF
Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de modification de données périodiques à l’aide d’une instruction SELECT pour l’interrogation de façon permanente les tables d’interface, interface, des vues, des tables et des vues dans Oracle E-Business Suite. Vous pouvez spécifier une instruction SELECT comme une instruction d’interrogation de l’adaptateur s’exécute périodiquement pour Oracle E-Business Suite. Vous pouvez également spécifier un bloc de code après interrogation PL/SQL que l’adaptateur s’exécute après l’exécution de l’instruction d’interrogation.  
  
 Pour activer l’interrogation, vous devez spécifier certaines propriétés de liaison comme décrit dans cette rubrique.  Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  
  
## <a name="configuring-a-polling-operation-with-oracle-e-business-suite-adapter-binding-properties"></a>Configuration d’une opération d’interrogation avec liaison des propriétés de l’adaptateur Oracle E-Business Suite  
 Le tableau suivant récapitule les [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] messages de modification des propriétés de liaison que vous utilisez pour configurer l’adaptateur pour recevoir des données. Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application d’interrogation.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation** ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. Uniquement si un enregistrement n’est disponible, l’instruction SELECT que vous spécifiez pour le **PollingInput** liaison de la propriété sera exécutée.|  
|**PollingInterval**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur est en veille pendant le temps restant dans l’intervalle.|  
|**PollingInput**|Spécifie l’instruction d’interrogation. Pour interroger à l’aide d’une instruction SELECT, vous devez spécifier une instruction SELECT pour cette propriété de liaison. La valeur par défaut est null.<br /><br /> Vous devez spécifier une valeur pour **PollingInput** propriété pour activer l’interrogation de liaison. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison.|  
|**PollingAction**|Spécifie l’action pour l’opération d’interrogation. Vous pouvez déterminer l’action d’interrogation de l’interface de service généré pour l’opération en utilisant la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)].|  
|**PostPollStatement**|Spécifie un bloc d’instructions qui est exécuté après l’instruction spécifiée par le **PollingInput** propriété de liaison est exécutée.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence l’instruction d’interrogation, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient pour exécuter l’instruction d’interrogation à l’intervalle d’interrogation spécifié. La valeur par défaut est False.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour interroger la base de données Oracle, poursuivre la lecture.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge la réception de données modifier des messages à l’aide des instructions SELECT, vous continuez d’interroger le **MS_SAMPLE_EMPLOYEE** table d’interface dans le **bibliothèque d’objets Application**application. Cette table est créée lorsque vous exécutez le script create_apps_artifacts.sql fourni avec les exemples pour créer ces objets dans Oracle E-Business Suite.  
  
 Pour illustrer une opération d’interrogation, nous les opérations suivantes :  
  
-   Spécifiez une instruction SELECT pour le **PolledDataAvailableStatement** liaison de propriété pour déterminer où l’interface table interrogés (MS_SAMPLE_EMPLOYEE) comporte des données. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     Cela garantit que l’adaptateur s’exécute l’instruction d’interrogation uniquement lorsque la table d’interface MS_SAMPLE_EMPLOYEE a des enregistrements.  
  
-   Spécifiez une instruction SELECT pour le **PollingInput** propriété de liaison. Cette instruction récupère toutes les lignes dans la table d’interface MS_SAMPLE_EMPLOYEE. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE  
    ```  
  
    > [!NOTE]
    >  Pour plus d’informations sur la clause FOR UPDATE utilisée dans l’instruction SELECT, consultez [recevoir des messages d’interrogation de données modifiées à partir d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/receive-polling-based-data-changed-messages-from-oracle-e-business-suite.md).  
  
-   Spécifiez une instruction DELETE en tant que partie de la **PostPollStatement** propriété de liaison. Cette instruction supprime toutes les données à partir de la table d’interface MS_SAMPLE_EMPLOYEE. Dans cet exemple, vous pouvez définir cette propriété de liaison en tant que :  
  
    ```  
    DELETE FROM MS_SAMPLE_EMPLOYEE  
    ```  
  
     Une fois que cela se produit, la prochaine fois que l’instruction spécifiée pour **PollingInput** sera exécutée, elle ne permet pas d’extraire des données.  
  
-   Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas tous les messages d’interrogation, donc vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements. Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table.  
  
## <a name="configuring-polling-in-the-wcf-service-model"></a>Configuration d’interrogation dans le modèle de Service WCF  
 Pour interroger une table d’interface à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec le modèle de service WCF, vous devez :  
  
-   Générer un contrat de service WCF (interface) pour le **interrogation** opération sur la table d’interface MS_SAMPLE_EMPLOYEE. Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   Implémenter un service WCF à partir de cette interface.  
  
-   Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique interrogent la table d’interface MS_SAMPLE_EMPLOYEE. Un script pour générer la table est fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md). Un exemple, **SelectPolling_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.  
  
## <a name="the-wcf-service-contract-and-class"></a>Le contrat de Service WCF et la classe  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **d’interrogation** opération. Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).  
  
### <a name="the-wcf-service-contract-interface"></a>Le contrat de Service WCF (Interface)  
 Le code suivant illustre le contrat de service WCF (interface) généré pour le **interrogation** dans la table d’interface MS_SAMPLE_EMPLOYEE.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/", ConfigurationName="InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE")]  
public interface InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE) of message Poll   
    // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE")]  
    void Poll(Poll request);  
}  
```  
  
### <a name="the-message-contracts"></a>Les contrats de Message  
 Voici le contrat de message pour le **interrogation** dans la table d’interface MS_SAMPLE_EMPLOYEE.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Poll", WrapperNamespace="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE" +  
    "_EMPLOYEE", IsWrapped=true)]  
public partial class Poll {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE" +  
        "_EMPLOYEE", Order=0)]  
    public schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.MS_SAMPLE_EMPLOYEE.SelectRecord[] DATA;  
  
    public Poll() {  
    }  
  
    public Poll(schemas.microsoft.com.OracleEBS._2008._05.TableViewRecord.APPS.MS_SAMPLE_EMPLOYEE.SelectRecord[] DATA) {  
        this.DATA = DATA;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a>Classe de Service WCF  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface). Le nom du fichier est OracleEBSBindingService.cs. Vous pouvez insérer la logique pour traiter les **interrogation** opération directement dans cette classe. Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
```  
namespace OracleEBSBindingNamespace {  
  
    public class OracleEBSBindingService : InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/OracleEBS/2008/05/InterfaceTables/FND/APPS/MS_SAMPLE_EMPLOYEE) of message Poll   
        // does not match the default value (http://schemas.microsoft.com/OracleEBS/)  
        public virtual void Poll(Poll request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-inbound-messages-for-the-poll-operation-using-a-select-statement"></a>Réception des Messages entrants pour l’opération d’interrogation à l’aide d’une instruction SELECT  
 Cette section fournit des instructions sur la façon d’écrire une application .NET pour recevoir des messages entrants d’interrogation à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
#### <a name="to-receive-polling-messages-using-a-select-statement"></a>Pour recevoir des messages d’interrogation à l’aide d’une instruction SELECT  
  
1.  Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **interrogation** opération sur la table d’interface MS_SAMPLE_EMPLOYEE. Pour plus d’informations, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md). Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service. Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.  
  
2.  Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1. Le **interrogation** méthode de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur est rencontrée, le traitement des données reçues à partir de la **interrogation** opération ; dans le cas contraire, la méthode ne pas retourner une valeur. Vous devez attribuer la classe de service WCF comme suit :  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     Dans le **interrogation** (méthode), vous pouvez directement implémenter votre logique d’application. Cette classe peut être trouvée dans OracleEBSBindingService.cs. Ce code dans cet exemple montre comment des classes le **OracleEBSBindingService** classe. Dans ce code, le message de l’interrogation reçu et est écrit dans la console.  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Poll(Poll request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Emp No\tName\tDesignation\tSalary");  
            for (int i = 0; i < request.DATA.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.DATA[i].EMP_NO,  
                request.DATA[i].NAME,  
                request.DATA[i].DESIGNATION,  
                request.DATA[i].SALARY);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  Vous devez implémenter la classe suivante pour éviter de transmettre des informations d’identification en tant que partie de l’URI. Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification.  
  
    ```  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
4.  Créer un **OracleEBSBinding** et configurer l’opération d’interrogation en spécifiant les propriétés de liaison. Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration. Au minimum, vous devez spécifier le **InboundOperationType**, **PolledDataAvailableStatement**, **PollingInput**, et **PollingAction**propriétés de liaison.  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
    binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
    binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
    binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
    ```  
  
5.  Étant donné que vous demandent une table d’interface, vous devez également définir le contexte des applications. Pour plus d’informations sur le contexte de l’application et les propriétés de liaison requises pour le contexte de l’application de paramètre, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
6.  Spécifiez les informations d’identification Oracle E-Business Suite en instanciant le **PollingCredentials** classe que vous avez créé à l’étape 3.  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
7.  Créez une instance du service WCF créé à l’étape 2.  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
8.  Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base. L’URI de la connexion de base ne peut pas contenir l’ID d’entrée, s’il est spécifié. Vous devez également passer les informations d’identification ici.  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. Ajouter un point de terminaison de service à l’hôte de service. Pour effectuer cette opération :  
  
    -   Utilisez la liaison créée à l’étape 4.  
  
    -   Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.  
  
    -   Spécifiez le contrat en tant que « InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE » pour interroger la table d’interface MS_SAMPLE_EMPLOYEE.  
  
    ```  
    // Add service endpoint: be sure to specify InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE as the contract  
    Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
    serviceHost.AddServiceEndpoint("InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE", binding, ConnectionUri);  
    ```  
  
10. Pour recevoir les données d’interrogation, ouvrez l’hôte de service. L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
11. Pour mettre fin à l’interrogation, fermez l’hôte de service.  
  
    > [!IMPORTANT]
    >  La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre une application d’interrogation qui interroge la table d’interface MS_SAMPLE_EMPLOYEE. Le **PollingInput** propriété contient l’instruction select qui lit toutes les données de la table MS_SAMPLE_EMPLOYEE et l’instruction de sondage post supprime toutes les données de la même table. Le premier message d’interrogation fournit tous les enregistrements dans la table d’interface MS_SAMPLE_EMPLOYEE. Les messages suivants d’interrogation ne contient pas d’enregistrements, car l’instruction de sondage post supprime les enregistrements. Jusqu'à ce que davantage de données est ajouté à la table d’interface MS_SAMPLE_EMPLOYEE, vous n’obtiendrez pas les messages d’interrogation. Par conséquent, vous devez remplir de nouveau la table d’interface MS_SAMPLE_EMPLOYEE avec nouveaux enregistrements. Vous pouvez le faire en exécutant le script insert_apps_data.sql fourni avec les exemples. Une fois que vous exécutez ce script, l’opération d’interrogation suivante permet d’extraire les nouveaux enregistrements insérés dans la table. La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur `<RETURN>`.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.Adapters.OracleEBS;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace SelectPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : OracleEBSBindingNamespace.OracleEBSBindingService  
    {  
        public override void Poll(Poll request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Emp No\tName\tDesignation\tSalary");  
            for (int i = 0; i < request.DATA.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.DATA[i].EMP_NO,  
                request.DATA[i].NAME,  
                request.DATA[i].DESIGNATION,  
                request.DATA[i].SALARY);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
  
    class PollingCredentials : ClientCredentials, IServiceBehavior  
    {  
        public void AddBindingParameters(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase, Collection<ServiceEndpoint> endpoints, BindingParameterCollection bindingParameters)  
        {  
            bindingParameters.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        public void Validate(ServiceDescription serviceDescription, ServiceHostBase serviceHostBase)  
        { }  
  
        protected override ClientCredentials CloneCore()  
        {  
            ClientCredentials clone = new PollingCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost serviceHost = null;     
            try  
            {  
                Console.WriteLine("Sample started...");  
                Console.WriteLine("Press any key to start polling...");  
                Console.ReadLine();  
  
                OracleEBSBinding binding = new OracleEBSBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
                binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
                binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
                binding.PostPollStatement = "DELETE FROM MS_SAMPLE_EMPLOYEE";  
                binding.OracleUserName = "myOracleEBSUserName";  
                binding.OraclePassword = "myOracleEBSPassword";  
                binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("oracleebs://ebs_instance_name");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // an InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("oracleebs://ebs_instance_name") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Polling started...");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                /* If there is an error it will be specified in the inner exception */  
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop polling  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation Oracle E-Business Suite à l’aide du modèle de service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-the-wcf-service-model.md)