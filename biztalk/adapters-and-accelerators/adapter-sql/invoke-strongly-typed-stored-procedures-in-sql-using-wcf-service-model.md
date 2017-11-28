---
title: "Appeler fortement typée de procédures stockées dans SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d56df5f6-b046-4fe4-a5b4-b29906093beb
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 591dd1c42913f44e148cb0c68a084d55f78c4d93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-strongly-typed-stored-procedures-in-sql-using-wcf-service-model"></a><span data-ttu-id="a6c3e-102">Appeler fortement typée de procédures stockées dans SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="a6c3e-102">Invoke Strongly-typed Stored Procedures in SQL using WCF Service Model</span></span>
<span data-ttu-id="a6c3e-103">Quand vous appelez une procédure répertoriée sous la **fortement typée procédures** nœud dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], la sortie est sous la forme d’un jeu de résultats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-103">When you invoke a procedure listed under the **Strongly-Typed Procedures** node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], the output is in the form of a strongly-typed result set.</span></span> <span data-ttu-id="a6c3e-104">Cette rubrique fournit des instructions sur la création d’un client WCF pour appeler des procédures stockées dans SQL Server qui retournent un jeu de résultats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-104">This topic provides instructions on how to create a WCF client to invoke stored procedures in SQL Server that return a strongly-typed result set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6c3e-105">Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec des Types définis par l’utilisateur](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-105">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="a6c3e-106">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="a6c3e-106">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="a6c3e-107">L’exemple dans cette rubrique utilise la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-107">The example in this topic uses the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="a6c3e-108">Cette procédure stockée accepte un ID d’employé comme paramètre d’entrée et retourne toutes les colonnes correspondantes de l’employé avec cet ID.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-108">This stored procedure takes an employee ID as an input parameter and returns all the corresponding columns for the employee with that ID.</span></span> <span data-ttu-id="a6c3e-109">La procédure stockée de GET_EMP_DETAILS est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-109">The GET_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="a6c3e-110">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a6c3e-110">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="a6c3e-111">Un exemple, **Execute_TypedStoredProcedure**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-111">A sample, **Execute_TypedStoredProcedure**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="a6c3e-112">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="a6c3e-112">The WCF Client Class</span></span>  
 <span data-ttu-id="a6c3e-113">Le nom du client WCF généré pour l’appel de procédures stockées sous la **fortement typée procédures** nœud à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-113">The name of the WCF client generated for invoking stored procedures under the **Strongly-Typed Procedures** node using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="a6c3e-114">Objet de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="a6c3e-114">SQL Server Database Artifact</span></span>|<span data-ttu-id="a6c3e-115">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="a6c3e-115">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="a6c3e-116">Procédure (sous la **fortement typée procédures** nœud)</span><span class="sxs-lookup"><span data-stu-id="a6c3e-116">Procedure (under the **Strongly-Typed Procedures** node)</span></span>|<span data-ttu-id="a6c3e-117">TypedProcedures_ [schéma] Client</span><span class="sxs-lookup"><span data-stu-id="a6c3e-117">TypedProcedures_[schema]Client</span></span>|  
  
 <span data-ttu-id="a6c3e-118">[schéma] est le schéma auquel appartient la procédure ; par exemple, « dbo ».</span><span class="sxs-lookup"><span data-stu-id="a6c3e-118">[schema] is the schema to which the procedure belongs; for example “dbo”.</span></span>  
  
### <a name="method-signature-for-invoking-stored-procedures"></a><span data-ttu-id="a6c3e-119">Signature de méthode pour appeler des procédures stockées</span><span class="sxs-lookup"><span data-stu-id="a6c3e-119">Method Signature for Invoking Stored Procedures</span></span>  
 <span data-ttu-id="a6c3e-120">Le tableau suivant montre la signature de la méthode exposée pour appeler les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-120">The following table shows the signature for the method exposed to invoke the stored procedures.</span></span>  
  
|<span data-ttu-id="a6c3e-121">Opération</span><span class="sxs-lookup"><span data-stu-id="a6c3e-121">Operation</span></span>|<span data-ttu-id="a6c3e-122">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="a6c3e-122">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="a6c3e-123">Nom de la procédure</span><span class="sxs-lookup"><span data-stu-id="a6c3e-123">Procedure name</span></span>|<span data-ttu-id="a6c3e-124">[PROC_NS] [nom_procédure] (param1, param2...\)</span><span class="sxs-lookup"><span data-stu-id="a6c3e-124">[PROC_NS] [procedure_name](param1, param2, …\)</span></span>|  
  
 <span data-ttu-id="a6c3e-125">[PROC_NS] est l’espace de noms de procédure ; par exemple [] schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0</span><span class="sxs-lookup"><span data-stu-id="a6c3e-125">[PROC_NS] is the procedure namespace; for example schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[]</span></span>  
  
 <span data-ttu-id="a6c3e-126">[nom_procédure] est le nom de la procédure ; par exemple GET_EMP_DETAILS</span><span class="sxs-lookup"><span data-stu-id="a6c3e-126">[procedure_name] is the name of the procedure; for example GET_EMP_DETAILS</span></span>  
  
 <span data-ttu-id="a6c3e-127">Par exemple, la signature de la méthode à appeler la procédure GET_EMP_DETAILS est indiquée dans l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-127">As an example, the signature for the method to invoke the GET_EMP_DETAILS procedure is shown in the following code snippet.</span></span>  
  
```  
public partial class TypedProcedures_dboClient : System.ServiceModel.ClientBase<TypedProcedures_dbo>, TypedProcedures_dbo{  
public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[]   
  GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 <span data-ttu-id="a6c3e-128">Dans cet extrait de code</span><span class="sxs-lookup"><span data-stu-id="a6c3e-128">In this snippet,</span></span>  
  
-   <span data-ttu-id="a6c3e-129">`TypedProcedures_dboClient`est le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-129">`TypedProcedures_dboClient` is the name of the class.</span></span> <span data-ttu-id="a6c3e-130">Dans cet exemple, vous utilisez cette classe pour créer un client pour appeler la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-130">In this example, you use this class to create a client to invoke the stored procedure.</span></span>  
  
-   <span data-ttu-id="a6c3e-131">`public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)`est la méthode que vous appelez dans cet exemple montre comment appeler la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-131">`public schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)` is the method that you invoke in this example to invoke the stored procedure.</span></span> <span data-ttu-id="a6c3e-132">Cette procédure stockée accepte un ID d’employé et retourne un jeu de résultats de fortement typée.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-132">This stored procedure takes an employee ID and returns a strongly-typed result set.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-a-stored-procedure-in-sql-server"></a><span data-ttu-id="a6c3e-133">Création d’un Client WCF pour appeler une procédure stockée dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="a6c3e-133">Creating a WCF Client to Invoke a Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="a6c3e-134">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="a6c3e-134">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="a6c3e-135">Cette section décrit en particulier comment créer un client WCF qui appelle une procédure stockée, le jeu de résultats pour ce qui est fortement typée.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-135">This section specifically describes how to create a WCF client that invokes a stored procedure, the result set for which is strongly-typed.</span></span> <span data-ttu-id="a6c3e-136">Dans cette rubrique, par exemple, vous appelez la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-136">In this topic, as an example, you invoke the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="a6c3e-137">Cette procédure stockée est créée en exécutant le script SQL fourni avec chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-137">This stored procedure is created by running the SQL script provided with each sample.</span></span>  
  
1.  <span data-ttu-id="a6c3e-138">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-138">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="a6c3e-139">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-139">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="a6c3e-140">Générer la classe de client WCF pour la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-140">Generate the WCF client class for the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="a6c3e-141">Veillez à sélectionner la procédure sous le **fortement typée procédures** nœud.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-141">Make sure you select the procedure under the **Strongly-Typed Procedures** node.</span></span> <span data-ttu-id="a6c3e-142">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="a6c3e-142">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a6c3e-143">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-143">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="a6c3e-144">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-144">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="a6c3e-145">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-145">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TypedProcedures_dboClient client = new TypedProcedures_dboClient("SqlAdapterBinding_TypedProcedures_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter username here>";  
    ```  
  
     <span data-ttu-id="a6c3e-146">Dans cet extrait de code, `TypedProcedures_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-146">In this snippet, `TypedProcedures_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="a6c3e-147">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6c3e-147">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="a6c3e-148">`SqlAdapterBinding_TypedProcedures_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-148">`SqlAdapterBinding_TypedProcedures_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6c3e-149">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-149">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="a6c3e-150">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-150">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="a6c3e-151">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="a6c3e-151">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="a6c3e-152">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a6c3e-152">Open the client as described in the snippet below:</span></span>  
  
    ```  
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
    ```  
  
6.  <span data-ttu-id="a6c3e-153">Appelez la procédure stockée de GET_EMP_DETAILS comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-153">Invoke the GET_EMP_DETAILS stored procedure as described in the snippet below.</span></span>  
  
    ```  
    // Create array of type as specified in the method signature  
    schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[] resultSet =  
       new schemas.microsoft.com.Sql._2008._05.ProceduresResultSets.dbo.GET_EMP_DETAILS.StoredProcedureResultSet0[1];  
    int returnCode;  
  
    try  
    {  
       Console.WriteLine("Calling a stored procedure...");  
       resultSet = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Console.WriteLine("The details for the employee with ID '10001' are:");  
    Console.WriteLine("*************************************************");  
  
    for (int i = 0; i < resultSet.Length; i++)  
       {  
          Console.WriteLine("Employee Name        : " + resultSet[i].Name);  
          Console.WriteLine("Employee Designation : " + resultSet[i].Designation);  
          Console.WriteLine("Employee Salary      : " + resultSet[i].Salary);  
       }  
  
    Console.WriteLine("*************************************************");  
  
    ```  
  
7.  <span data-ttu-id="a6c3e-154">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a6c3e-154">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="a6c3e-155">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-155">Build the project and then run it.</span></span> <span data-ttu-id="a6c3e-156">Le nom, désignation et salaire pour l’ID d’employé, sont affichés sur la console.</span><span class="sxs-lookup"><span data-stu-id="a6c3e-156">The name, designation, and salary for the employee ID, are displayed on the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c3e-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6c3e-157">See Also</span></span>  
[<span data-ttu-id="a6c3e-158">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="a6c3e-158">Develop applications using the WCF Service model</span></span>](develop-sql-applications-using-the-wcf-service-model.md)