---
title: "Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3df95d78-3a9c-48c0-81ab-1f3206c5e3f7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bceb236b660b80c1e46cb0410d799d994516c40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-an-insert-operation-on-a-table-in-sql-using-the-wcf-channel-model"></a><span data-ttu-id="1c871-102">Exécuter une opération Insert sur une Table dans SQL à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="1c871-102">Run an Insert Operation on a Table in SQL using the WCF Channel Model</span></span>
<span data-ttu-id="1c871-103">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte un ensemble d’opérations de base sur les tables de base de données SQL Server et les vues Insert, Select, Update et Delete.</span><span class="sxs-lookup"><span data-stu-id="1c871-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on SQL Server database tables and views.</span></span> <span data-ttu-id="1c871-104">À l’aide de ces opérations, vous pouvez effectuer simple SQL Insert, Select, Update et supprimer les instructions qualifiées par Where clause sur une table ou vue cible.</span><span class="sxs-lookup"><span data-stu-id="1c871-104">By using these operations, you can perform simple SQL Insert, Select, Update, and Delete statements qualified by a Where clause on a target table or view.</span></span> <span data-ttu-id="1c871-105">Cette rubrique fournit des instructions sur la façon d’effectuer une opération d’insertion sur une table de base de données SQL Server à l’aide du modèle de canal WCF.</span><span class="sxs-lookup"><span data-stu-id="1c871-105">This topic provides instructions on how to perform an Insert operation on a SQL Server database table using the WCF channel model.</span></span>  
  
 <span data-ttu-id="1c871-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1c871-106">For more information on how the adapter supports these operations, see [Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).</span></span> <span data-ttu-id="1c871-107">Pour plus d’informations sur la façon d’effectuer des opérations sur SQL Server à l’aide du modèle de canal WCF, consultez [vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1c871-107">For more information about how to perform operations on SQL Server using the WCF Channel model, see [Overview of the WCF channel model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="1c871-108">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="1c871-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="1c871-109">L’exemple de cette rubrique effectue des opérations sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="1c871-109">The example in this topic performs operations on the Employee table.</span></span> <span data-ttu-id="1c871-110">La table Employee est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="1c871-110">The Employee table is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="1c871-111">Pour plus d’informations sur les exemples, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="1c871-111">For more information about samples, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).</span></span> <span data-ttu-id="1c871-112">Un exemple, **EmployeeInsertOp**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="1c871-112">A sample, **EmployeeInsertOp**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-insert-message"></a><span data-ttu-id="1c871-113">Le Message d’insertion</span><span class="sxs-lookup"><span data-stu-id="1c871-113">The Insert Message</span></span>  
 <span data-ttu-id="1c871-114">Pour effectuer des opérations sur la base de données SQL Server à l’aide du modèle de canal WCF, vous devez disposer du message de demande spécifique à l’opération.</span><span class="sxs-lookup"><span data-stu-id="1c871-114">To perform operations on the SQL Server database using the WCF channel model, you must have the request message specific to the operation.</span></span> <span data-ttu-id="1c871-115">Pour effectuer une opération d’insertion sur la table Employee dans la base de données SQL Server, le message de demande ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="1c871-115">The request message to perform an Insert operation on the Employee table in the SQL Server database resembles the following:</span></span>  
  
```  
<Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Rows>  
    <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
      <Name>Tom Smith</Name>  
      <Designation>Manager</Designation>  
      <Salary>500000</Salary>  
   </Employee>  
  </Rows>  
</Insert>  
```  
  
 <span data-ttu-id="1c871-116">Ce message de demande insère un enregistrement avec les détails suivants :</span><span class="sxs-lookup"><span data-stu-id="1c871-116">This request message inserts a record with following details:</span></span>  
  
```  
Name = Tom Smith  
Designation = Manager  
Salary = 500000  
```  
  
 <span data-ttu-id="1c871-117">Vous devez copier le message vers un fichier, par exemple, InsertRequest.xml.</span><span class="sxs-lookup"><span data-stu-id="1c871-117">You must copy the message to a file, e.g. InsertRequest.xml.</span></span> <span data-ttu-id="1c871-118">Ce fichier est utilisé dans cet exemple pour envoyer le message de demande à SQL Server à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c871-118">This file is used in this example to send the request message to SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="1c871-119">Pour plus d’informations sur le schéma de message pour les opérations sur la table, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span><span class="sxs-lookup"><span data-stu-id="1c871-119">For more information about the message schema for operations on table, see [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span>  
  
## <a name="creating-a-wcf-channel-application"></a><span data-ttu-id="1c871-120">Création d’une Application de canal WCF</span><span class="sxs-lookup"><span data-stu-id="1c871-120">Creating a WCF Channel Application</span></span>  
 <span data-ttu-id="1c871-121">Cette section fournit des instructions sur la création d’une application de canal WCF pour effectuer une opération d’insertion sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="1c871-121">This section provides instructions on how to create a WCF channel application to perform an Insert operation on the Employee table.</span></span>  
  
#### <a name="to-create-a-wcf-channel-application-for-inserting-records-into-the-employee-table"></a><span data-ttu-id="1c871-122">Pour créer une application de canal WCF pour insérer des enregistrements dans la table Employee</span><span class="sxs-lookup"><span data-stu-id="1c871-122">To create a WCF channel application for inserting records into the Employee table</span></span>  
  
1.  <span data-ttu-id="1c871-123">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c871-123">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="1c871-124">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="1c871-124">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="1c871-125">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, et `System.Runtime.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="1c871-125">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="1c871-126">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="1c871-126">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.Sql`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
4.  <span data-ttu-id="1c871-127">Créer la liaison et le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1c871-127">Create the binding and endpoint.</span></span>  
  
    ```  
    SqlAdapterBinding binding = new SqlAdapterBinding();  
    EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
    ```  
  
5.  <span data-ttu-id="1c871-128">Créez et ouvrez la fabrication de canal.</span><span class="sxs-lookup"><span data-stu-id="1c871-128">Create and open the channel factory.</span></span> <span data-ttu-id="1c871-129">Cette application envoie un message de demande à SQL Server et qu’il reçoit une réponse, donc vous devez implémenter l’interface IRequestChannel.</span><span class="sxs-lookup"><span data-stu-id="1c871-129">This application sends request message to SQL Server and receives a response, hence you must implement the IRequestChannel interface.</span></span>  
  
    ```  
    ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
    factory.Credentials.UserName.UserName = "<Enter user name here>";  
    factory.Credentials.UserName.Password = "<Enter password here>";  
    factory.Open();  
    ```  
  
6.  <span data-ttu-id="1c871-130">Créer et ouvrir le canal.</span><span class="sxs-lookup"><span data-stu-id="1c871-130">Create and open the channel.</span></span>  
  
    ```  
    IRequestChannel channel = factory.CreateChannel();  
    channel.Open();  
    ```  
  
7.  <span data-ttu-id="1c871-131">Créer et envoyer le message de demande.</span><span class="sxs-lookup"><span data-stu-id="1c871-131">Create and send the request message.</span></span>  
  
    ```  
    XmlReader readerIn;  
    Console.WriteLine("Creating the message");  
    try  
    {  
       readerIn = XmlReader.Create("InsertRequest.xml");  
       Console.WriteLine("Reader created");  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Message messageIn = Message.CreateMessage(MessageVersion.Default, "TableOp/Insert/dbo/Employee", readerIn);  
    Message messageOut = channel.Request(messageIn);  
  
    ```  
  
     <span data-ttu-id="1c871-132">Lors de la création du message de demande, vous devez spécifier l’action du message qui indique l’action que l’adaptateur effectue sur la table SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1c871-132">While creating the request message, you must specify the message action that indicates the action that the adapter performs on the SQL Server table.</span></span> <span data-ttu-id="1c871-133">Pour effectuer une opération d’insertion sur la table Employee, l’action du message est `TableOp/Insert/dbo/Employee`.</span><span class="sxs-lookup"><span data-stu-id="1c871-133">To perform an Insert operation on the Employee table, the message action is `TableOp/Insert/dbo/Employee`.</span></span> <span data-ttu-id="1c871-134">Pour plus d’informations sur la façon dont vous pouvez déterminer l’action du message pour différentes opérations sur les tables, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span><span class="sxs-lookup"><span data-stu-id="1c871-134">For information about how you can determine the message action for various operations on tables, see [Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).</span></span>  
  
8.  <span data-ttu-id="1c871-135">Obtenir le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="1c871-135">Get the response message.</span></span>  
  
    ```  
    XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
    XmlDocument doc = new XmlDocument();  
    doc.Load(readerOut);  
    doc.Save("C:\\Response.xml");  
    ```  
  
9. <span data-ttu-id="1c871-136">Fermez le message, le canal et la fabrique de canaux.</span><span class="sxs-lookup"><span data-stu-id="1c871-136">Close the message, channel, and channel factory.</span></span>  
  
    ```  
    messageOut.Close();  
    channel.Close();  
    factory.Close();  
    ```  
  
10. <span data-ttu-id="1c871-137">créer le projet ;</span><span class="sxs-lookup"><span data-stu-id="1c871-137">Build the project.</span></span> <span data-ttu-id="1c871-138">Après avoir généré le projet, vous devez effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="1c871-138">After building the project, you must perform the following tasks:</span></span>  
  
    -   <span data-ttu-id="1c871-139">Copiez le message de demande, InsertRequest.xml, au même emplacement que votre projet exécutable.</span><span class="sxs-lookup"><span data-stu-id="1c871-139">Copy the request message, InsertRequest.xml, at the same location as your project executable.</span></span> <span data-ttu-id="1c871-140">En règle générale, cet emplacement est \bin\Debug\ sous le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="1c871-140">Typically, this location is \bin\Debug\ under your project directory.</span></span>  
  
    -   <span data-ttu-id="1c871-141">Le tableau « Employee » utilisé dans cet exemple comporte une colonne de type de Point défini par l’utilisateur (UDT).</span><span class="sxs-lookup"><span data-stu-id="1c871-141">The "Employee" table used in this example has a column of Point user-defined type (UDT).</span></span> <span data-ttu-id="1c871-142">Par conséquent, avant d’exécuter le projet, vous devez créer l’assembly de l’UDT Point comme décrit dans [Creating Types](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types).</span><span class="sxs-lookup"><span data-stu-id="1c871-142">So, before running the project, you must create the assembly for the Point UDT as described at [Creating User-Defined Types](https://docs.microsoft.com/sql/relational-databases/clr-integration-database-objects-user-defined-types/creating-user-defined-types).</span></span> <span data-ttu-id="1c871-143">Vous devez également copier la DLL dans le même emplacement que le projet exécutable d’assembly.</span><span class="sxs-lookup"><span data-stu-id="1c871-143">You must also copy the assembly DLL at the same location as the project executable.</span></span> <span data-ttu-id="1c871-144">En règle générale, cet emplacement est \bin\Debug\ sous le répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="1c871-144">Typically, this location is \bin\Debug\ under your project directory.</span></span>  
  
11. <span data-ttu-id="1c871-145">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="1c871-145">Run the application.</span></span> <span data-ttu-id="1c871-146">Le message de réponse, Response.xml, est enregistré dans l’emplacement spécifié dans l’application.</span><span class="sxs-lookup"><span data-stu-id="1c871-146">The response message, Response.xml, is saved at the location you specified in the application.</span></span> <span data-ttu-id="1c871-147">Le message de réponse contient l’ID de l’employé et ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="1c871-147">The response message contains the ID of the newly added employee and resembles the following:</span></span>  
  
    ```  
    <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <InsertResult>  
        <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10006</long>  
      </InsertResult>  
    </InsertResponse>  
    ```  
  
     <span data-ttu-id="1c871-148">Étant donné que la table Employee comporte la colonne Employee_ID en tant que la colonne d’identité, l’opération d’insertion retourne la valeur de la colonne d’identité de l’enregistrement qui vient d’être inséré.</span><span class="sxs-lookup"><span data-stu-id="1c871-148">Because the Employee table has the Employee_ID column as the identity column, the Insert operation returns the value for the identity column of the newly inserted record.</span></span> <span data-ttu-id="1c871-149">Si elle n’existe aucune colonne d’identité dans une table, la valeur de retour est NULL.</span><span class="sxs-lookup"><span data-stu-id="1c871-149">If there is no identity column in a table, the return value is NULL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c871-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c871-150">See Also</span></span>  
[<span data-ttu-id="1c871-151">Développer des applications SQL à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="1c871-151">Develop SQL applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)