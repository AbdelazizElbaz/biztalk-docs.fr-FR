---
title: "Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide du modèle de Service WCF | Documents Microsoft"
description: "Utiliser une application .NET pour configurer l’interrogation typée ou interrogation fortement typée à l’aide du Service WCF avec l’adaptateur WCF-SQL dans BizTalk Server"
ms.custom: 
ms.date: 10/09/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b55eda71-1226-43f2-bc2f-e6b35563210b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c616d2a9f10aae5dbf822676174a0de0d4816c19
ms.sourcegitcommit: f9c6ea3c9cfb8a43f765c0d3b8b07dacaa21fc51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2017
---
# <a name="receive-strongly-typed-polling-based-data-changed-messages-from-sql-server-using-wcf-service-model"></a>Recevoir des fortement typée d’interrogation de modification de données de Messages à partir de SQL Server à l’aide du modèle de Service WCF
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de l’interrogation fortement typée à partir de SQL Server. Vous pouvez spécifier une instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats. Vous devez utiliser interrogation fortement typée dans un scénario où vous souhaitez recevoir un jeu de résultats de fortement typée. Pour plus d’informations sur la façon dont l’adaptateur prend en charge l’interrogation fortement typée, consultez [prise en charge de trafic entrant appels à l’aide de l’interrogation](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md).  
  
> [!IMPORTANT]
>  Si vous souhaitez disposer d’interrogation plus d’une opération dans une application unique, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique. L’ID entrant que vous spécifiez est ajouté à l’espace de noms d’opération pour le rendre unique.  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception des données fortement typées les messages de modification, créez une application .NET et générer le contrat de service WCF pour le **TypedPolling** opération. Assurez-vous que vous spécifiez ce qui suit lors de la génération du contrat de service WCF :  
  
-   Vous devez spécifier un **InboundID** dans le cadre de l’URI de connexion.  
  
-   Vous devez spécifier une instruction d’interrogation pour le **PollingStatement** propriété de liaison.  
  
 En outre, si vous souhaitez spécifier une autre interrogation liées des propriétés de liaison lors de la génération de la classe proxy, spécifiez la **PolledDataAvailableStatement** en tant que :  
  
```  
SELECT COUNT(*) FROM Employee  
```  
  
 Le **PolledDataAvailableStatement** doit retourner un jeu de résultats avec la première cellule contenant une valeur positive. Si la première cellule ne contient pas une valeur positive, l’adaptateur n’exécute pas l’instruction d’interrogation.  
  
 Dans le cadre de l’instruction d’interrogation, effectuez les opérations suivantes :  
  
1.  Sélectionnez toutes les lignes de la table Employee.  
  
2.  Exécuter une procédure stockée (MOVE_EMP_DATA) pour déplacer tous les enregistrements de la table Employee pour une table HistoriqueEmployé.  
  
3.  Exécuter une procédure stockée (ADD_EMP_DETAILS) pour ajouter un nouvel enregistrement dans la table Employee. Cette procédure prend le nom de l’employé, désignation et salaire en tant que paramètres.  
  
 Pour effectuer ces opérations, vous devez spécifier les informations suivantes pour le **PollingStatement** propriété de liaison lors de la génération les classes d’assistance et de contrat de service WCF :  
  
```  
SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000   
```  
  
 Après l’exécution de l’instruction d’interrogation, tous les enregistrements de la table Employee sont sélectionnés et la réception du message à partir de SQL Server. Après l’exécution de la procédure stockée de MOVE_EMP_DATA par l’adaptateur, tous les enregistrements sont déplacés vers la table HistoriqueEmployé. Ensuite, la procédure stockée de ADD_EMP_DETAILS est exécutée pour ajouter un nouvel enregistrement dans la table Employee. L’exécution de l’interrogation suivante retourne uniquement un seul enregistrement. Ce cycle se poursuit jusqu'à la fermeture de l’hôte de service.  
  
## <a name="configuring-typed-polling-with-the-sql-adapter-binding-properties"></a>Configuration d’interrogation typée avec l’adaptateur SQL propriétés de liaison  
 Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés que vous utilisez pour configurer l’adaptateur pour recevoir des messages de modification de données de liaison. Autre que le **PollingStatement** propriété de liaison, toutes les autres propriétés de liaison répertoriées dans cette section sont requises lors de l’exécution de l’application .NET. Vous devez spécifier le **PollingStatement** propriété de liaison avant de générer le contrat de service WCF **TypedPolling** opération.  
  
|Propriété de liaison| Description|  
|----------------------|-----------------|  
|**InboundOperationType**|Spécifie si vous souhaitez effectuer **d’interrogation**, **TypedPolling**, ou **Notification** opération entrante. Valeur par défaut est **d’interrogation**. Pour recevoir des messages d’interrogation fortement typée, affectez la valeur **TypedPolling**.|  
|**PolledDataAvailableStatement**|Spécifie l’instruction SQL qui s’exécute pour déterminer si les données sont disponibles pour l’interrogation de l’adaptateur. L’instruction SQL doit retourner un jeu de résultats composé de lignes et de colonnes. Uniquement si une ligne est disponible, l’instruction SQL spécifiée pour le **PollingStatement** liaison de la propriété sera exécutée.|  
|**PollingIntervalInSeconds**|Spécifie l’intervalle, en secondes, à laquelle le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exécute l’instruction spécifiée pour le **PolledDataAvailableStatement** propriété de liaison. La valeur par défaut est 30 secondes. L’intervalle d’interrogation détermine l’intervalle de temps entre deux interrogations successives. Si l’instruction est exécutée dans l’intervalle spécifié, l’adaptateur attend que le temps restant dans l’intervalle.|  
|**PollingStatement**|Spécifie l’instruction SQL pour interroger la table de base de données SQL Server. Vous pouvez spécifier une instruction SELECT simple ou une procédure stockée pour l’instruction d’interrogation. La valeur par défaut est null. Vous devez spécifier une valeur pour **PollingStatement** pour activer l’interrogation. L’instruction d’interrogation est exécutée uniquement si des données disponibles pour l’interrogation, ce qui est déterminée par le **PolledDataAvailableStatement** propriété de liaison. Vous pouvez spécifier n’importe quel nombre d’instructions SQL séparées par un point-virgule. **Important :** pour **TypedPolling**, vous devez spécifier cette propriété de liaison avant de générer des métadonnées.|  
|**PollWhileDataFound**|Spécifie si le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] ignore l’intervalle d’interrogation et exécute en permanence de l’instruction SQL spécifiée pour le **PolledDataAvailableStatement** liaison de propriété, si les données sont disponibles dans la table interrogée. Si aucune donnée n’est disponible dans la table, l’adaptateur revient à exécuter l’instruction SQL à l’intervalle d’interrogation spécifié. Valeur par défaut est **false**.|  
  
 Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour interroger le SQL Server, poursuivre la lecture.  
  
## <a name="configure-strongly-typed-polling-in-the-wcf-service-model"></a>Configurer l’interrogation fortement typée dans le modèle de Service WCF  
 Pour recevoir le **d’interrogation** opération lorsque vous utilisez le modèle de service WCF, vous devez :  
  
1.  Générer un contrat de service WCF (interface) pour le **TypedPolling** opération à partir des métadonnées exposées par l’adaptateur. Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]. Lors de la génération du contrat de service WCF pour cet exemple, assurez-vous que :  
  
    -   Vous spécifiez le **InboundID** en tant que **employé**.  
  
    -   Vous spécifiez une instruction d’interrogation pour le **PollingStatement** propriété de liaison. Pour cet exemple, spécifiez l’instruction d’interrogation en tant que :  
  
        ```  
        SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000  
        ```  
  
2.  Implémenter un service WCF à partir de cette interface.  
  
3.  Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).  
  
## <a name="about-the-examples-used-in-this-topic"></a>À propos des exemples présentés dans cette rubrique  
 Les exemples de cette rubrique interrogent la table Employee. L’exemple utilise également les MOVE_EMP_DATA ADD_EMP_DETAILS procédure stockée. Un script pour générer ces artefacts est fourni avec les exemples. Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md). Un exemple, **TypedPolling_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.  
  
## <a name="the-wcf-service-contract-and-class"></a>Le contrat de Service WCF et la classe  
 Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **TypedPolling** opération. Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).  
  
### <a name="the-wcf-service-contract-interface"></a>Le contrat de Service WCF (Interface)  
 Le code suivant illustre le contrat de service WCF (interface) généré pour le **TypedPolling** opération.  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="TypedPolling_Employee")]  
public interface TypedPolling_Employee {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee) of message TypedPolling  
    // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="TypedPolling")]  
    void TypedPolling(TypedPolling request);  
}  
```  
  
### <a name="the-message-contracts"></a>Les contrats de Message  
 L’espace de noms de contrat de message est modifié par la **InboundID** paramètre dans l’URI, s’il est spécifié de connexion. Dans cet exemple, vous avez spécifié l’ID entrant en tant que **employé**. Le message de requête retourne un jeu de résultats de fortement typée.  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="TypedPolling", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", IsWrapped=true)]  
public partial class TypedPolling {  
  
[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", Order=0)]  
    public schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet0[] TypedPollingResultSet0;  
  
[System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee", Order=1)]  
    public schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet1[] TypedPollingResultSet1;  
  
    public TypedPolling() {  
    }  
  
    public TypedPolling(schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet0[] TypedPollingResultSet0, schemas.microsoft.com.Sql._2008._05.TypedPolling.Employee.TypedPollingResultSet1[] TypedPollingResultSet1) {  
        this.TypedPollingResultSet0 = TypedPollingResultSet0;  
        this.TypedPollingResultSet1 = TypedPollingResultSet1;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a>Classe de Service WCF  
 Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface). Le nom du fichier est SqlAdapterBindingService.cs. Vous pouvez insérer la logique pour traiter les **TypedPolling** opération directement dans cette classe. Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : TypedPolling_Employee {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/TypedPolling/Employee) of message TypedPolling  
        // does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void TypedPolling(TypedPolling request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receive-strongly-typed-inbound-messages-for-polling-operation"></a>Réception fortement typée de Messages entrants pour l’opération d’interrogation  
 Cette section fournit des instructions sur la façon d’écrire une application .NET pour recevoir des messages d’interrogation entrant fortement typée à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
1.  Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **TypedPolling** opération. Assurez-vous que vous spécifiez ce qui suit lors de la génération du contrat de service WCF pour cet exemple :  
  
    -   Vous devez spécifier le **InboundID** en tant que **employé**.  
  
    -   Vous devez spécifier une instruction d’interrogation pour le **PollingStatement** propriété de liaison. Pour cet exemple, spécifiez l’instruction d’interrogation en tant que :  
  
        ```  
        SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000  
        ```  
  
     Pour plus d’informations, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md). Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service. Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.  
  
2.  Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 1. Le **TypedPolling** méthode de cette classe peut lever une exception pour annuler la transaction d’interrogation, si une erreur est rencontrée, le traitement des données reçues à partir de la **TypedPolling** opération ; sinon le méthode ne retourne rien. Vous devez attribuer la classe de service WCF comme suit :  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     Dans le **TypedPolling** (méthode), vous pouvez directement implémenter votre logique d’application. Cette classe peut être trouvée dans SqlAdapterBindingService.cs. Ce code dans cet exemple montre comment des classes le **SqlAdapterBindingService** classe. Dans ce code, le message d’interrogation reçu en tant qu’un jeu de résultats de fortement typée est écrite dans la console.  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void TypedPolling(TypedPolling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Employee ID\tName\tDesignation\tSalary");  
  
            for (int i = 0; i < request.TypedPollingResultSet0.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.TypedPollingResultSet0[i].Employee_ID,  
                request.TypedPollingResultSet0[i].Name,  
                request.TypedPollingResultSet0[i].Designation,  
                request.TypedPollingResultSet0[i].Salary);  
            }  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("\nHit <RETURN> to stop polling");  
        }  
    }  
    ```  
  
3.  Étant donné que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’accepte pas les informations d’identification dans le cadre de l’URI de connexion, vous devez implémenter la classe suivante pour transmettre les informations d’identification pour la base de données SQL Server. Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification SQL Server.  
  
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
  
4.  Créer un **SqlAdapterBinding** et configurer l’opération d’interrogation en spécifiant les propriétés de liaison. Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration. Au minimum, vous devez spécifier le **InboundOperationType**, **PolledDataAvailableStatement**, et **PollingStatement**.  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.TypedPolling;  
    binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
    binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
    ```  
  
5.  Spécifiez les informations d’identification de la base de données SQL Server en instanciant le **PollingCredentials** classe que vous avez créé à l’étape 3.  
  
    ```  
    PollingCredentials credentials = new PollingCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
6.  Créez une instance du service WCF créé à l’étape 2.  
  
    ```  
    // create service instance  
    PollingService service = new PollingService();  
    ```  
  
7.  Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base. L’URI de la connexion de base ne peut pas contenir l’ID de trafic entrant. Vous devez également spécifier les informations d’identification ici.  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
8.  Ajouter un point de terminaison de service à l’hôte de service. Pour effectuer cette opération :  
  
    -   Utilisez la liaison créée à l’étape 4.  
  
    -   Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.  
  
    -   Spécifiez le contrat en tant que « TypedPolling_Employee ».  
  
    ```  
    // Add service endpoint: be sure to specify TypedPolling_Employee as the contract  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?InboundID=Employee");  
    serviceHost.AddServiceEndpoint("TypedPolling_Employee", binding, ConnectionUri);  
    ```  
  
9. Pour recevoir les données d’interrogation, ouvrez l’hôte de service. L’adaptateur retourne les données chaque fois que la requête retourne un jeu de résultats.  
  
    ```  
    // Open the service host to begin polling  
    serviceHost.Open();  
    ```  
  
10. Pour mettre fin à l’interrogation, fermez l’hôte de service.  
  
    > [!IMPORTANT]
    >  La carte va continuer à interroger jusqu'à ce que l’hôte de service est fermé.  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre une requête d’interrogation qui s’exécute à la table Employee. L’instruction d’interrogation effectue les tâches suivantes :  
  
1.  Sélectionne tous les enregistrements de la table Employee.  
  
2.  Exécute la procédure MOVE_EMP_DATA stockées pour déplacer tous les enregistrements à partir de la table Employee à HistoriqueEmployé table.  
  
3.  Exécute la procédure stockée de ADD_EMP_DETAILS pour ajouter un enregistrement unique dans la table Employee.  
  
 Le premier message d’interrogation contiendra tous les enregistrements de la table Employee. Les messages suivants d’interrogation contiendra uniquement le dernier enregistrement inséré par la procédure stockée de ADD_EMP_DETAILS. La carte continuera d’interroger jusqu'à ce que vous fermez l’hôte de service en appuyant sur `<RETURN>`.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
using Microsoft.Adapters.Sql;  
using Microsoft.ServiceModel.Channels;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using System.ServiceModel.Channels;  
using System.Collections.ObjectModel;  
  
namespace TypedPolling_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class PollingService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void TypedPolling(TypedPolling request)  
        {  
            Console.WriteLine("\nNew Polling Records Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine("Employee ID\tName\tDesignation\tSalary");  
  
            for (int i = 0; i < request.TypedPollingResultSet0.Length; i++)  
            {  
                Console.WriteLine("{0}\t{1}\t{2}\t{3}",  
                request.TypedPollingResultSet0[i].Employee_ID,  
                request.TypedPollingResultSet0[i].Name,  
                request.TypedPollingResultSet0[i].Designation,  
                request.TypedPollingResultSet0[i].Salary);  
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
  
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.TypedPolling;  
                binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
                binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
                Console.WriteLine("Binding properties assigned...");  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?InboundId=Employee");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // the InboundID; otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                PollingCredentials credentials = new PollingCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                PollingService service = new PollingService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("TypedPolling_Employee", binding, ConnectionUri);  
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
 [Interrogation SQL Server à l’aide de l’adaptateur SQL avec le modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-wcf-service-model.md)
