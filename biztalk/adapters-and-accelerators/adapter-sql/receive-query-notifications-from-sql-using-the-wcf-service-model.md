---
title: "Recevoir des Notifications de requête SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9def31-3c5a-4326-b798-31bde0ff2568
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5507bbb21d1b5648a10be2230dd4476eacca1c78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-query-notifications-from-sql-using-the-wcf-service-model"></a><span data-ttu-id="4072e-102">Recevoir des Notifications de requête SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="4072e-102">Receive Query Notifications from SQL using the WCF Service Model</span></span>
<span data-ttu-id="4072e-103">Cette rubrique montre comment configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de notification de requête à partir d’une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4072e-103">This topic demonstrates how to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive query notification messages from a SQL Server database.</span></span> <span data-ttu-id="4072e-104">Pour illustrer des notifications, considérez une table Employee, avec une colonne « État ».</span><span class="sxs-lookup"><span data-stu-id="4072e-104">To demonstrate notifications, consider a table, Employee, with a “Status” column.</span></span> <span data-ttu-id="4072e-105">Lorsqu’un nouvel enregistrement est inséré à cette table, la valeur de la colonne d’état est définie sur 0.</span><span class="sxs-lookup"><span data-stu-id="4072e-105">When a new record is inserted to this table, the value of the Status column is set to 0.</span></span> <span data-ttu-id="4072e-106">Vous pouvez configurer l’adaptateur pour recevoir des notifications par l’inscription aux notifications à l’aide d’une instruction SQL qui Récupère tous les enregistrements dont la colonne d’état en tant que « 0 ».</span><span class="sxs-lookup"><span data-stu-id="4072e-106">You can configure the adapter to receive notifications by registering for notifications using a SQL statement that retrieves all records that have Status column as “0.”</span></span> <span data-ttu-id="4072e-107">Vous pouvez le faire en spécifiant l’instruction SQL pour le **NotificationStatement** propriété de liaison.</span><span class="sxs-lookup"><span data-stu-id="4072e-107">You can do so by specifying the SQL statement for the **NotificationStatement** binding property.</span></span> <span data-ttu-id="4072e-108">Une fois que le client de l’adaptateur reçoit la notification, il peut contenir la logique pour effectuer les tâches suivantes sur la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4072e-108">After the adapter client receives the notification, it can contain the logic to do any subsequent tasks on the SQL Server database.</span></span> <span data-ttu-id="4072e-109">Dans cet exemple, par souci de simplicité, le client de carte répertorie tous les enregistrements dans la table dont la colonne d’état en tant que « 0 ».</span><span class="sxs-lookup"><span data-stu-id="4072e-109">In this example, for the sake of simplicity, the adapter client lists all the records in the table that have the Status column as “0.”</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4072e-110">Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les tables et vues avec des types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) rubrique avant de commencer à développer votre application .</span><span class="sxs-lookup"><span data-stu-id="4072e-110">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on tables and views with user-defined types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) topic before you start developing your application.</span></span>  
  
## <a name="configuring-notifications-with-the-sql-adapter-binding-properties"></a><span data-ttu-id="4072e-111">Configuration des Notifications à l’adaptateur SQL propriétés de liaison</span><span class="sxs-lookup"><span data-stu-id="4072e-111">Configuring Notifications with the SQL Adapter Binding Properties</span></span>  
 <span data-ttu-id="4072e-112">Le tableau suivant récapitule les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] propriétés de liaison qui vous permet de configurer la réception des notifications à partir de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4072e-112">The following table summarizes the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] binding properties that you use to configure receiving notifications from SQL Server.</span></span> <span data-ttu-id="4072e-113">Vous devez spécifier ces propriétés de liaison lors de l’exécution de l’application .NET pour recevoir les notifications à partir d’une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4072e-113">You must specify these binding properties while running the .NET application to receive the notifications from a SQL Server database.</span></span>  
  
|<span data-ttu-id="4072e-114">Propriété de liaison</span><span class="sxs-lookup"><span data-stu-id="4072e-114">Binding Property</span></span>|<span data-ttu-id="4072e-115"> Description</span><span class="sxs-lookup"><span data-stu-id="4072e-115">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="4072e-116">**InboundOperationType**</span><span class="sxs-lookup"><span data-stu-id="4072e-116">**InboundOperationType**</span></span>|<span data-ttu-id="4072e-117">Spécifie l’opération entrante que vous souhaitez effectuer.</span><span class="sxs-lookup"><span data-stu-id="4072e-117">Specifies the inbound operation that you want to perform.</span></span> <span data-ttu-id="4072e-118">Pour recevoir des messages de notification, affectez la valeur **Notification**.</span><span class="sxs-lookup"><span data-stu-id="4072e-118">To receive notification messages, set this to **Notification**.</span></span>|  
|<span data-ttu-id="4072e-119">**NotificationStatement**</span><span class="sxs-lookup"><span data-stu-id="4072e-119">**NotificationStatement**</span></span>|<span data-ttu-id="4072e-120">Spécifie l’instruction SQL (SELECT ou EXEC \< *procédure stockée*>) permet de s’inscrire aux notifications de requête.</span><span class="sxs-lookup"><span data-stu-id="4072e-120">Specifies the SQL statement (SELECT or EXEC \<*stored procedure*>) used to register for query notifications.</span></span> <span data-ttu-id="4072e-121">L’adaptateur reçoit un message de notification de SQL Server que lorsque le jeu de résultats pour que les modifications d’instruction SQL spécifiées.</span><span class="sxs-lookup"><span data-stu-id="4072e-121">The adapter gets a notification message from SQL Server only when the result set for the specified SQL statement changes.</span></span>|  
|<span data-ttu-id="4072e-122">**NotifyOnListenerStart**</span><span class="sxs-lookup"><span data-stu-id="4072e-122">**NotifyOnListenerStart**</span></span>|<span data-ttu-id="4072e-123">Spécifie si l’adaptateur envoie une notification pour les clients de la carte au démarrage de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="4072e-123">Specifies whether the adapter sends a notification to the adapter clients when the listener is started.</span></span>|  
  
 <span data-ttu-id="4072e-124">Pour obtenir une description plus complète de ces propriétés, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4072e-124">For a more complete description of these properties, see [Read about the BizTalk Adapter for SQL Server adapter binding properties](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).</span></span> <span data-ttu-id="4072e-125">Pour obtenir une description complète de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des notifications à partir de SQL Server, poursuivre la lecture.</span><span class="sxs-lookup"><span data-stu-id="4072e-125">For a complete description of how to use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to receive notifications from SQL Server, read further.</span></span>  
  
## <a name="configuring-notifications-using-the-wcf-service-model"></a><span data-ttu-id="4072e-126">Configuration des Notifications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="4072e-126">Configuring Notifications Using the WCF Service Model</span></span>  
 <span data-ttu-id="4072e-127">Pour recevoir les notifications à l’aide du modèle de service WCF, vous devez :</span><span class="sxs-lookup"><span data-stu-id="4072e-127">To receive the notifications using the WCF service model, you must:</span></span>  
  
1.  <span data-ttu-id="4072e-128">Générer un contrat de service WCF (interface) pour le **Notification** opération à partir des métadonnées exposées par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="4072e-128">Generate a WCF service contract (interface) for the **Notification** operation from the metadata exposed by the adapter.</span></span> <span data-ttu-id="4072e-129">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4072e-129">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
2.  <span data-ttu-id="4072e-130">Générer un client WCF pour le **sélectionnez** opération sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="4072e-130">Generate a WCF client for the **Select** operation on the Employee table.</span></span> <span data-ttu-id="4072e-131">Pour ce faire, vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4072e-131">To do this, you could use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
3.  <span data-ttu-id="4072e-132">Implémenter un service WCF à partir de cette interface.</span><span class="sxs-lookup"><span data-stu-id="4072e-132">Implement a WCF service from this interface.</span></span>  
  
4.  <span data-ttu-id="4072e-133">Héberger ce service WCF à l’aide d’un hôte de service (**System.ServiceModel.ServiceHost**).</span><span class="sxs-lookup"><span data-stu-id="4072e-133">Host this WCF service using a service host (**System.ServiceModel.ServiceHost**).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="4072e-134">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="4072e-134">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="4072e-135">Les exemples de cette rubrique recevoir une notification pour la table Employee.</span><span class="sxs-lookup"><span data-stu-id="4072e-135">The examples in this topic receive notification for the Employee table.</span></span> <span data-ttu-id="4072e-136">Un script pour générer la table est fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="4072e-136">A script to generate the table is supplied with the samples.</span></span> <span data-ttu-id="4072e-137">Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="4072e-137">For more information about the samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="4072e-138">Un exemple, **Notification_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="4072e-138">A sample, **Notification_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-service-contract-and-class"></a><span data-ttu-id="4072e-139">Le contrat de Service WCF et la classe</span><span class="sxs-lookup"><span data-stu-id="4072e-139">The WCF Service Contract and Class</span></span>  
 <span data-ttu-id="4072e-140">Vous pouvez utiliser la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour créer un contrat de service WCF (interface) et la prise en charge des classes pour la **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="4072e-140">You can use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF service contract (interface) and supporting classes for the **Notification** operation.</span></span> <span data-ttu-id="4072e-141">Pour plus d’informations sur la génération d’un contrat de service WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="4072e-141">For more information about generating a WCF service contract, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
### <a name="the-wcf-service-contract-interface"></a><span data-ttu-id="4072e-142">Le contrat de Service WCF (Interface)</span><span class="sxs-lookup"><span data-stu-id="4072e-142">The WCF Service Contract (Interface)</span></span>  
 <span data-ttu-id="4072e-143">Le code suivant illustre le contrat de service WCF (interface) généré pour le **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="4072e-143">The following code shows the WCF service contract (interface) generated for the **Notification** operation.</span></span>  
  
```  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.ServiceContractAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/", ConfigurationName="NotificationOperation")]  
public interface NotificationOperation {  
  
    // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Notification/) of message  
    // Notification does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
    [System.ServiceModel.OperationContractAttribute(IsOneWay=true, Action="Notification")]  
    void Notification(Notification request);  
}  
```  
  
### <a name="the-message-contracts"></a><span data-ttu-id="4072e-144">Les contrats de Message</span><span class="sxs-lookup"><span data-stu-id="4072e-144">The Message Contracts</span></span>  
 <span data-ttu-id="4072e-145">Voici le contrat de message pour l’opération de Notification.</span><span class="sxs-lookup"><span data-stu-id="4072e-145">Following is the message contract for the Notification operation.</span></span>  
  
```  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "3.0.0.0")]  
[System.ServiceModel.MessageContractAttribute(WrapperName="Notification", WrapperNamespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", IsWrapped=true)]  
public partial class Notification {  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=0)]  
    public string Info;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=1)]  
    public string Source;  
  
    [System.ServiceModel.MessageBodyMemberAttribute(Namespace="http://schemas.microsoft.com/Sql/2008/05/Notification/", Order=2)]  
    public string Type;  
  
    public Notification() {  
    }  
  
    public Notification(string Info, string Source, string Type) {  
        this.Info = Info;  
        this.Source = Source;  
        this.Type = Type;  
    }  
}  
```  
  
### <a name="wcf-service-class"></a><span data-ttu-id="4072e-146">Classe de Service WCF</span><span class="sxs-lookup"><span data-stu-id="4072e-146">WCF Service Class</span></span>  
 <span data-ttu-id="4072e-147">Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] génère également un fichier qui a un stub pour la classe de service WCF implémenté le contrat de service (interface).</span><span class="sxs-lookup"><span data-stu-id="4072e-147">The [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] also generates a file that has a stub for the WCF service class implemented from the service contract (interface).</span></span> <span data-ttu-id="4072e-148">Le nom du fichier est SqlAdapterBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="4072e-148">The name of the file is SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="4072e-149">Vous pouvez insérer la logique pour traiter les **Notification** opération directement dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="4072e-149">You can insert the logic to process the **Notification** operation directly into this class.</span></span> <span data-ttu-id="4072e-150">Le code suivant illustre la classe de service WCF générée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4072e-150">The following code shows the WCF service class generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
```  
namespace SqlAdapterBindingNamespace {  
  
    public class SqlAdapterBindingService : NotificationOperation {  
  
        // CODEGEN: Generating message contract since the wrapper namespace (http://schemas.microsoft.com/Sql/2008/05/Notification/)   
        // of message Notification does not match the default value (http://schemas.microsoft.com/Sql/2008/05/)  
        public virtual void Notification(Notification request) {  
            throw new System.NotImplementedException("The method or operation is not implemented.");  
        }  
    }  
}  
```  
  
## <a name="receiving-query-notifications-using-wcf-service-model"></a><span data-ttu-id="4072e-151">Réception des Notifications de requête à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="4072e-151">Receiving Query Notifications Using WCF Service Model</span></span>  
 <span data-ttu-id="4072e-152">Cette section fournit des instructions sur l’écriture d’une application .NET pour recevoir des notifications de requête à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4072e-152">This section provides instructions on how to write a .NET application to receive query notifications using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
#### <a name="to-receive-query-notifications"></a><span data-ttu-id="4072e-153">Pour recevoir des notifications de requête</span><span class="sxs-lookup"><span data-stu-id="4072e-153">To receive query notifications</span></span>  
  
1.  <span data-ttu-id="4072e-154">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un client WCF pour **sélectionnez** opération sur le **employé** table.</span><span class="sxs-lookup"><span data-stu-id="4072e-154">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF client for **Select** operation on the **Employee** table.</span></span> <span data-ttu-id="4072e-155">Vous allez utiliser ce client pour effectuer des opérations de sélection après avoir reçu un message de notification.</span><span class="sxs-lookup"><span data-stu-id="4072e-155">You will use this client to perform Select operations after receiving a notification message.</span></span> <span data-ttu-id="4072e-156">Ajoutez une nouvelle classe, TableOperation.cs à votre projet et ajouter l’extrait de code suivant pour effectuer une opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="4072e-156">Add a new class, TableOperation.cs to your project and add the following code snippet to perform a Select operation.</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
  
    namespace Notification_ServiceModel  
    {  
        public class TableOperation  
        {  
            public void TableOp()  
            {  
                ///////////////////////////////////////////////////////////////////////  
                // CREATING THE CLIENT  
                ///////////////////////////////////////////////////////////////////////  
  
                TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
  
                client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
                client.ClientCredentials.UserName.Password = "<Enter password here>";  
  
                ///////////////////////////////////////////////////////////////////////  
                // OPENING THE CLIENT  
                ///////////////////////////////////////////////////////////////////////  
  
                try  
                {  
                    Console.WriteLine("Opening Client...");  
                    client.Open();  
                }  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                ///////////////////////////////////////////////////////////////////////  
                // SELECTING THE LAST INSERTED RECORD FROM THE TABLE  
                ///////////////////////////////////////////////////////////////////////  
                schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
                try  
                {  
                    selectRecords = client.Select("*", "where Status=0");  
                }  
  
                catch (Exception ex)  
                {  
                    Console.WriteLine("Exception: " + ex.Message);  
                    throw;  
                }  
  
                Console.WriteLine("The details of the newly added employee are:");  
                Console.WriteLine("********************************************");  
                for (int i = 0; i \< selectRecords.Length; i++)  
                {  
                    Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
                    Console.WriteLine("Employee Designation: " + selectRecords[i].Designation);  
                    Console.WriteLine("Employee Status    : " + selectRecords[i].Status);  
                    Console.WriteLine();  
                }  
                Console.WriteLine("********************************************");  
  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4072e-157">Étant donné que cet extrait de code effectue des opérations sur la table Employee qui contient une colonne UDT Point, veillez à que placer la DLL UDT dans le dossier \bin\Debug du projet lors de l’exécution de l’application.</span><span class="sxs-lookup"><span data-stu-id="4072e-157">Because this code snippet performs operations on the Employee table that contains a Point UDT column, make sure you put the UDT DLL under the project’s \bin\Debug folder while running the application.</span></span>  
  
2.  <span data-ttu-id="4072e-158">Utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer un contrat de service WCF (interface) et des classes d’assistance pour le **Notification** opération.</span><span class="sxs-lookup"><span data-stu-id="4072e-158">Use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to generate a WCF service contract (interface) and helper classes for the **Notification** operation.</span></span>  
  
     <span data-ttu-id="4072e-159">Pour plus d’informations, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="4072e-159">For more information, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span> <span data-ttu-id="4072e-160">Vous pouvez éventuellement spécifier les propriétés de liaison lors de la génération les classes d’assistance et de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="4072e-160">You can optionally specify the binding properties while generating the service contract and helper classes.</span></span> <span data-ttu-id="4072e-161">Cela garantit qu’ils sont correctement définies dans le fichier de configuration généré.</span><span class="sxs-lookup"><span data-stu-id="4072e-161">This guarantees that they are properly set in the generated configuration file.</span></span>  
  
3.  <span data-ttu-id="4072e-162">Implémenter un service WCF à partir de l’interface et assistance des classes générées à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="4072e-162">Implement a WCF service from the interface and helper classes generated in step 2.</span></span> <span data-ttu-id="4072e-163">Le **Notification** méthode de cette classe peut lever une exception pour annuler l’opération, si une erreur est rencontrée, le traitement des données provenance de la **Notification** opération ; sinon, la méthode ne ne renvoie rien.</span><span class="sxs-lookup"><span data-stu-id="4072e-163">The **Notification** method of this class can throw an exception to abort the operation, if an error is encountered processing the data received from the **Notification** operation; otherwise the method does not return anything.</span></span> <span data-ttu-id="4072e-164">Vous devez attribuer la classe de service WCF comme suit :</span><span class="sxs-lookup"><span data-stu-id="4072e-164">You must attribute the WCF service class as follows:</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    ```  
  
     <span data-ttu-id="4072e-165">Dans le **Notification** (méthode), vous pouvez directement implémenter votre logique d’application.</span><span class="sxs-lookup"><span data-stu-id="4072e-165">Within the **Notification** method, you can implement your application logic directly.</span></span> <span data-ttu-id="4072e-166">Cette classe peut être trouvée dans SqlAdapterBindingService.cs.</span><span class="sxs-lookup"><span data-stu-id="4072e-166">This class can be found in SqlAdapterBindingService.cs.</span></span> <span data-ttu-id="4072e-167">Ce code dans cet exemple montre comment des classes le **SqlAdapterBindingService** classe.</span><span class="sxs-lookup"><span data-stu-id="4072e-167">This code in this example sub-classes the **SqlAdapterBindingService** class.</span></span> <span data-ttu-id="4072e-168">Dans ce code, le message de notification reçu est écrite dans la console.</span><span class="sxs-lookup"><span data-stu-id="4072e-168">In this code, the notification message received is written to the console.</span></span> <span data-ttu-id="4072e-169">En outre, le **TableOp** méthode au sein de la **TableOperation** classe est appelée pour effectuer l’opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="4072e-169">Additionally, the **TableOp** method within the **TableOperation** class is invoked to perform the Select operation.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
  
    public class NotificationService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
  
            // Invoke th TableOp method in the TableOperation class  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
        }  
    }  
    ```  
  
4.  <span data-ttu-id="4072e-170">Étant donné que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’accepte pas les informations d’identification dans le cadre de l’URI de connexion, vous devez implémenter la classe suivante pour transmettre les informations d’identification pour la base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4072e-170">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not accept credentials as part of the connection URI, you must implement the following class to pass credentials for the SQL Server database.</span></span> <span data-ttu-id="4072e-171">Dans la dernière partie de l’application, vous serez instancier cette classe à transmettre les informations d’identification SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4072e-171">In the latter part of the application, you will instantiate this class to pass on the SQL Server credentials.</span></span>  
  
    ```  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
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
            ClientCredentials clone = new NotificationCredentials();  
            clone.UserName.UserName = this.UserName.UserName;  
            clone.UserName.Password = this.UserName.Password;  
            return clone;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="4072e-172">Créer un **SqlAdapterBinding** et configurez la carte pour recevoir des notifications de requête en spécifiant les propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="4072e-172">Create a **SqlAdapterBinding** and configure the adapter to receive query notifications by specifying the binding properties.</span></span> <span data-ttu-id="4072e-173">Ce faire, vous pouvez soit explicitement dans le code ou de façon déclarative dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="4072e-173">You can do this either explicitly in code or declaratively in configuration.</span></span> <span data-ttu-id="4072e-174">Au minimum, vous devez spécifier le **InboundOperationType** et **NotificationStatement** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="4072e-174">At a minimum, you must specify the **InboundOperationType** and **NotificationStatement** binding properties.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    binding.InboundOperationType = InboundOperation.Notification;  
    binding.NotificationStatement = "SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0";  
    binding.NotifyOnListenerStart = true;  
    ```  
  
6.  <span data-ttu-id="4072e-175">Spécifiez les informations d’identification de la base de données SQL Server en instanciant le **NotificationCredentials** classe que vous avez créé à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="4072e-175">Specify SQL Server database credentials by instantiating the **NotificationCredentials** class you created in Step 4.</span></span>  
  
    ```  
    NotificationCredentials credentials = new NotificationCredentials();  
    credentials.UserName.UserName = "<Enter user name here>";  
    credentials.UserName.Password = "<Enter password here>";  
    ```  
  
7.  <span data-ttu-id="4072e-176">Créez une instance du service WCF créé à l’étape 3.</span><span class="sxs-lookup"><span data-stu-id="4072e-176">Create an instance of the WCF service created in step 3.</span></span>  
  
    ```  
    // create service instance  
    NotificationService service = new NotificationService();  
    ```  
  
8.  <span data-ttu-id="4072e-177">Créez une instance de **System.ServiceModel.ServiceHost** à l’aide du service WCF et l’URI de connexion de base.</span><span class="sxs-lookup"><span data-stu-id="4072e-177">Create an instance of **System.ServiceModel.ServiceHost** by using the WCF service and a base connection URI.</span></span> <span data-ttu-id="4072e-178">Vous devez également spécifier les informations d’identification ici.</span><span class="sxs-lookup"><span data-stu-id="4072e-178">You must also specify the credentials here.</span></span>  
  
    ```  
    // Enable service host  
    Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
    ServiceHost serviceHost = new ServiceHost(service, baseUri);  
    serviceHost.Description.Behaviors.Add(credentials);  
  
    ```  
  
9. <span data-ttu-id="4072e-179">Ajouter un point de terminaison de service à l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="4072e-179">Add a service endpoint to the service host.</span></span> <span data-ttu-id="4072e-180">Pour effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="4072e-180">To do this:</span></span>  
  
    -   <span data-ttu-id="4072e-181">Utilisez la liaison créée à l’étape 5.</span><span class="sxs-lookup"><span data-stu-id="4072e-181">Use the binding created in step 5.</span></span>  
  
    -   <span data-ttu-id="4072e-182">Spécifiez une URI qui contient les informations d’identification de connexion et, si nécessaire, un ID d’entrée.</span><span class="sxs-lookup"><span data-stu-id="4072e-182">Specify a connection URI that contains credentials and, if required, an inbound ID.</span></span>  
  
    -   <span data-ttu-id="4072e-183">Spécifiez le contrat en tant que « NotificationOperation ».</span><span class="sxs-lookup"><span data-stu-id="4072e-183">Specify the contract as "NotificationOperation".</span></span>  
  
    ```  
    // Add service endpoint: be sure to specify NotificationOperation as the contract  
    Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
    serviceHost.AddServiceEndpoint("NotificationOperation", binding, ConnectionUri);  
    ```  
  
10. <span data-ttu-id="4072e-184">Pour recevoir un message de notification, ouvrez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="4072e-184">To receive notification message, open the service host.</span></span>  
  
    ```  
    // Open the service host to begin receiving notifications  
    serviceHost.Open();  
    ```  
  
11. <span data-ttu-id="4072e-185">Pour arrêter de recevoir des notifications, fermez l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="4072e-185">To stop receiving notifications, close the service host.</span></span>  
  
    ```  
    serviceHost.Close();  
    ```  
  
### <a name="example"></a><span data-ttu-id="4072e-186">Exemple</span><span class="sxs-lookup"><span data-stu-id="4072e-186">Example</span></span>  
 <span data-ttu-id="4072e-187">L’exemple suivant montre une application .NET pour recevoir des messages de notification pour la table Employee.</span><span class="sxs-lookup"><span data-stu-id="4072e-187">The following example shows a .NET application to receive notification messages for the Employee table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4072e-188">L’extrait de code suivant instancie un **TableOperation.cs** classe et appelle le **TableOp** (méthode).</span><span class="sxs-lookup"><span data-stu-id="4072e-188">The following code snippet instantiates a **TableOperation.cs** class and invokes the **TableOp** method.</span></span> <span data-ttu-id="4072e-189">La classe et la méthode sont décrites à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="4072e-189">The class and the method are described in Step 1.</span></span>  
  
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
  
namespace Notification_ServiceModel  
{  
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
    public class NotificationService : SqlAdapterBindingNamespace.SqlAdapterBindingService  
    {  
        public override void Notification(Notification request)  
        {  
            Console.WriteLine("\nNew Notification Received");  
            Console.WriteLine("*************************************************");  
            Console.WriteLine(request.Info);  
            Console.WriteLine(request.Source);  
            Console.WriteLine(request.Type);  
            Console.WriteLine("*************************************************");  
            TableOperation Ops = new TableOperation();  
            Ops.TableOp();  
        }  
    }  
  
    class NotificationCredentials : ClientCredentials, IServiceBehavior  
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
            ClientCredentials clone = new NotificationCredentials();  
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
                SqlAdapterBinding binding = new SqlAdapterBinding();  
                binding.InboundOperationType = InboundOperation.Notification;  
                binding.NotificationStatement = "SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0";  
                binding.NotifyOnListenerStart = true;  
  
                // This URI is used to specify the address for the ServiceEndpoint  
                // It must contain the InboundId (if any) that was used to generate  
                // the WCF service callback interface  
                Uri ConnectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
  
                // This URI is used to initialize the ServiceHost. It cannot contain  
                // a query_string (InboundID); otherwise,an exception is thrown when  
                // the ServiceHost is initialized.  
                Uri[] baseUri = new Uri[] { new Uri("mssql://mysqlserver//mydatabase") };  
  
                NotificationCredentials credentials = new NotificationCredentials();  
                credentials.UserName.UserName = "<Enter user name here>";  
                credentials.UserName.Password = "<Enter password here>";  
  
                Console.WriteLine("Opening service host...");  
                NotificationService service = new NotificationService();  
                serviceHost = new ServiceHost(service, baseUri);  
                serviceHost.Description.Behaviors.Add(credentials);  
                serviceHost.AddServiceEndpoint("NotificationOperation", binding, ConnectionUri);  
                serviceHost.Open();  
                Console.WriteLine("Service host opened...");  
                Console.WriteLine("Waiting for notification...");  
  
                Console.WriteLine("\nHit <RETURN> to stop receiving notification");  
                Console.ReadLine();  
            }  
            catch (Exception e)  
            {  
                Console.WriteLine("Exception :" + e.Message);  
                Console.ReadLine();  
  
                // If there is an error it will be specified in the inner exception   
                if (e.InnerException != null)  
                {  
                    Console.WriteLine("InnerException: " + e.InnerException.Message);  
                    Console.ReadLine();  
                }  
            }  
            finally  
            {  
                // IMPORTANT: you must close the ServiceHost to stop receiving notifications  
                if (serviceHost.State == CommunicationState.Opened)  
                    serviceHost.Close();  
                else  
                    serviceHost.Abort();  
            }  
        }  
    }  
}  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="4072e-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4072e-190">See Also</span></span>  
[<span data-ttu-id="4072e-191">Développer des applications SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="4072e-191">Develop SQL applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)