---
title: "Appeler faiblement typée les procédures stockées de SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aaf74a40-4c03-4a4a-9b91-c21babe154fa
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ec0b8b8d022b4e96a6df4d7c0d49d8176f6cd1a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-weakly-typed-stored-procedures-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="bd426-102">Appeler faiblement typée les procédures stockées de SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="bd426-102">Invoke Weakly-typed Stored Procedures in SQL using the WCF Service Model</span></span>
<span data-ttu-id="bd426-103">Quand vous appelez une procédure répertoriée sous la **procédures** nœud dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], la sortie est sous la forme d’un tableau de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="bd426-103">When you invoke a procedure listed under the **Procedures** node in the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], the output is in the form of a DataSet array.</span></span> <span data-ttu-id="bd426-104">Cette rubrique fournit des instructions sur la création d’un client WCF pour appeler une procédure stockée dans SQL Server qui retourne un tableau de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="bd426-104">This topic provides instructions on how to create a WCF client to invoke a stored procedure in SQL Server that returns a DataSet array.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd426-105">Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.</span><span class="sxs-lookup"><span data-stu-id="bd426-105">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="bd426-106">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="bd426-106">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="bd426-107">L’exemple dans cette rubrique utilise la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="bd426-107">The example in this topic uses the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="bd426-108">Cette procédure stockée accepte un ID d’employé comme paramètre d’entrée et retourne toutes les colonnes correspondantes de l’employé avec cet ID.</span><span class="sxs-lookup"><span data-stu-id="bd426-108">This stored procedure takes an employee ID as an input parameter and returns all the corresponding columns for the employee with that ID.</span></span> <span data-ttu-id="bd426-109">La procédure stockée de GET_EMP_DETAILS est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="bd426-109">The GET_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="bd426-110">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bd426-110">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="bd426-111">Un exemple, **Execute_StoredProc**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="bd426-111">A sample, **Execute_StoredProc**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="bd426-112">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="bd426-112">The WCF Client Class</span></span>  
 <span data-ttu-id="bd426-113">Le nom du client WCF généré pour l’appel de procédures stockées sous la **procédures** nœud à l’aide du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="bd426-113">The name of the WCF client generated for invoking stored procedures under the **Procedures** node using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="bd426-114">Objet de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="bd426-114">SQL Server Database Artifact</span></span>|<span data-ttu-id="bd426-115">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="bd426-115">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="bd426-116">Procédure (sous la **procédures** nœud)</span><span class="sxs-lookup"><span data-stu-id="bd426-116">Procedure (under the **Procedures** node)</span></span>|<span data-ttu-id="bd426-117">Procedures_ [schéma] Client</span><span class="sxs-lookup"><span data-stu-id="bd426-117">Procedures_[schema]Client</span></span>|  
  
 <span data-ttu-id="bd426-118">[schéma] est le schéma auquel appartient la procédure ; par exemple, « dbo ».</span><span class="sxs-lookup"><span data-stu-id="bd426-118">[schema] is the schema to which the procedure belongs; for example “dbo”.</span></span>  
  
### <a name="method-signature-for-invoking-stored-procedures"></a><span data-ttu-id="bd426-119">Signature de méthode pour appeler des procédures stockées</span><span class="sxs-lookup"><span data-stu-id="bd426-119">Method Signature for Invoking Stored Procedures</span></span>  
 <span data-ttu-id="bd426-120">Le tableau suivant montre la signature de la méthode exposée pour appeler les procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="bd426-120">The following table shows the signature for the method exposed to invoke the stored procedures.</span></span>  
  
|<span data-ttu-id="bd426-121">Opération</span><span class="sxs-lookup"><span data-stu-id="bd426-121">Operation</span></span>|<span data-ttu-id="bd426-122">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="bd426-122">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="bd426-123">Nom de la procédure</span><span class="sxs-lookup"><span data-stu-id="bd426-123">Procedure name</span></span>|<span data-ttu-id="bd426-124">[] De System.Data.DataSet [nom_procédure] (param1, param2,...\)</span><span class="sxs-lookup"><span data-stu-id="bd426-124">System.Data.DataSet[] [procedure_name](param1, param2, …\)</span></span>|  
  
 <span data-ttu-id="bd426-125">[nom_procédure] est le nom de la procédure ; par exemple GET_EMP_DETAILS</span><span class="sxs-lookup"><span data-stu-id="bd426-125">[procedure_name] is the name of the procedure; for example GET_EMP_DETAILS</span></span>  
  
 <span data-ttu-id="bd426-126">Par exemple, la signature de la méthode à appeler la procédure GET_EMP_DETAILS est indiquée dans l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="bd426-126">As an example, the signature for the method to invoke the GET_EMP_DETAILS procedure is shown in the following code snippet.</span></span>  
  
```  
public partial class Procedures_dboClient : System.ServiceModel.ClientBase<Procedures_dbo>, Procedures_dbo {  
  public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue);  
}  
```  
  
 <span data-ttu-id="bd426-127">Dans cet extrait de code</span><span class="sxs-lookup"><span data-stu-id="bd426-127">In this snippet,</span></span>  
  
-   <span data-ttu-id="bd426-128">`Procedures_dboClient`est le nom de la classe de client WCF.</span><span class="sxs-lookup"><span data-stu-id="bd426-128">`Procedures_dboClient` is the name of the WCF client class.</span></span> <span data-ttu-id="bd426-129">Dans cet exemple, vous utilisez cette classe pour créer un client pour appeler la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="bd426-129">In this example, you use this class to create a client to invoke the stored procedure.</span></span>  
  
-   <span data-ttu-id="bd426-130">`public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)`est la méthode que vous appelez dans cet exemple montre comment appeler la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="bd426-130">`public System.Data.DataSet[] GET_EMP_DETAILS(System.Nullable<int> emp_id, out int ReturnValue)` is the method that you invoke in this example to invoke the stored procedure.</span></span> <span data-ttu-id="bd426-131">Cette procédure stockée accepte un ID d’employé et retourne un tableau de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="bd426-131">This stored procedure takes an employee ID and returns a DataSet array.</span></span>  
  
## <a name="create-a-wcf-client-to-invoke-a-stored-procedure-in-sql-server"></a><span data-ttu-id="bd426-132">Créer un Client WCF pour appeler une procédure stockée dans SQL Server</span><span class="sxs-lookup"><span data-stu-id="bd426-132">Create a WCF Client to Invoke a Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="bd426-133">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="bd426-133">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="bd426-134">Cette section décrit en particulier comment créer un client WCF qui appelle une procédure stockée, le jeu de résultats pour ce qui est un tableau de jeu de données.</span><span class="sxs-lookup"><span data-stu-id="bd426-134">This section specifically describes how to create a WCF client that invokes a stored procedure, the result set for which is a DataSet array.</span></span> <span data-ttu-id="bd426-135">Dans cette rubrique, par exemple, vous appelez la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="bd426-135">In this topic, as an example, you invoke the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="bd426-136">Cette procédure stockée est créée en exécutant le script SQL fourni avec chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="bd426-136">This stored procedure is created by running the SQL script provided with each sample.</span></span>  
  
  
1.  <span data-ttu-id="bd426-137">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd426-137">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="bd426-138">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="bd426-138">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="bd426-139">Générer la classe de client WCF pour la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="bd426-139">Generate the WCF client class for the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="bd426-140">Veillez à sélectionner la procédure sous le **procédures** nœud.</span><span class="sxs-lookup"><span data-stu-id="bd426-140">Make sure you select the procedure under the **Procedures** node.</span></span> <span data-ttu-id="bd426-141">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="bd426-141">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bd426-142">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="bd426-142">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="bd426-143">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="bd426-143">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="bd426-144">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="bd426-144">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              Procedures_dboClient client = new Procedures_dboClient("SqlAdapterBinding_Procedures_dbo");  
  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="bd426-145">Dans cet extrait de code, `Procedures_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="bd426-145">In this snippet, `Procedures_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="bd426-146">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd426-146">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="bd426-147">`SqlAdapterBinding_Procedures_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="bd426-147">`SqlAdapterBinding_Procedures_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bd426-148">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="bd426-148">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="bd426-149">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="bd426-149">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="bd426-150">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="bd426-150">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="bd426-151">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="bd426-151">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="bd426-152">Appelez la procédure stockée de GET_EMP_DETAILS.</span><span class="sxs-lookup"><span data-stu-id="bd426-152">Invoke the GET_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="bd426-153">Avant d’appeler la procédure GET_EMP_DETAILS, vous devez ajouter le `System.Data` espace de noms à votre code.</span><span class="sxs-lookup"><span data-stu-id="bd426-153">Before you invoke the GET_EMP_DETAILS procedure, you must add the `System.Data` namespace to your code.</span></span>  
  
    ```  
    DataSet[] dataArray;  
    int returnCode;  
  
    try  
    {  
       Console.WriteLine("Calling a stored procedure...");  
       dataArray = client.GET_EMP_DETAILS(10001, out returnCode);  //Invoke the stored procedure  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
    Console.WriteLine("The details for the employee with ID '10001' are:");  
    Console.WriteLine("*************************************************");  
  
    foreach (DataSet dataSet in dataArray)  
    {  
       foreach (DataTable tab in dataArray[0].Tables)  
       {  
          foreach (DataRow row in tab.Rows)  
          {  
             for (int i = 0; i < tab.Columns.Count; i++)  
             {  
                Console.WriteLine(row[i]);  
             }  
          }  
       }  
    }  
    Console.WriteLine("*************************************************");  
  
    ```  
  
7.  <span data-ttu-id="bd426-154">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="bd426-154">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="bd426-155">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="bd426-155">Build the project and then run it.</span></span> <span data-ttu-id="bd426-156">Les détails de l’employé, pour le pr vous</span><span class="sxs-lookup"><span data-stu-id="bd426-156">The details for the employee, for which you pr</span></span>
9.  <span data-ttu-id="bd426-157">ovided l’ID, sont affichés dans la console.</span><span class="sxs-lookup"><span data-stu-id="bd426-157">ovided the ID, are displayed on the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd426-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bd426-158">See Also</span></span>  
[<span data-ttu-id="bd426-159">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="bd426-159">Develop applications using the WCF Service model</span></span>](develop-sql-applications-using-the-wcf-service-model.md)