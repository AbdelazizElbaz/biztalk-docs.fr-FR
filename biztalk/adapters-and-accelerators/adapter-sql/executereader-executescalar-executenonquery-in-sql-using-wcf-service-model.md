---
title: "Les opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f166af-b657-491b-b20d-1ae7886f27ce
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f886463e2b38b358e5f6a9da8b7e67aabdc9c3ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-sql-using-wcf-service-model"></a><span data-ttu-id="f66f9-102">Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="f66f9-102">ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in SQL using WCF Service Model</span></span>
<span data-ttu-id="f66f9-103">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose des opérations SQL Server générique tel que **ExecuteNonQuery**, **ExecuteReader**, et **ExecuteScalar**.</span><span class="sxs-lookup"><span data-stu-id="f66f9-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes generic SQL Server operations such as **ExecuteNonQuery**, **ExecuteReader**, and **ExecuteScalar**.</span></span> <span data-ttu-id="f66f9-104">Vous pouvez utiliser ces opérations à exécuter n’importe quelle instruction SQL sur une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f66f9-104">You can use these operations to execute any SQL statement on a SQL Server database.</span></span> <span data-ttu-id="f66f9-105">Ces opérations varient en fonction du type de réponse pour l’instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="f66f9-105">These operations differ based on the kind of response you get for the SQL statement.</span></span> <span data-ttu-id="f66f9-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span><span class="sxs-lookup"><span data-stu-id="f66f9-106">For more information about how the adapter supports these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span></span>  
  
 <span data-ttu-id="f66f9-107">Cette rubrique montre comment effectuer une **ExecuteReader** à l’aide de l’opération la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="f66f9-107">This topic demonstrates how to perform an **ExecuteReader** operation using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] using the WCF service model.</span></span> <span data-ttu-id="f66f9-108">Vous pouvez suivre le même ensemble de procédures décrites dans cette rubrique pour effectuer **ExecuteNonQuery** et **ExecuteScalar** operations.</span><span class="sxs-lookup"><span data-stu-id="f66f9-108">You can follow the same set of procedures described in this topic to perform **ExecuteNonQuery** and **ExecuteScalar** operations.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="f66f9-109">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="f66f9-109">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="f66f9-110">L’exemple de cette rubrique utilise le **ExecuteReader** opération à exécuter la ADD_EMP_DETAILS de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="f66f9-110">The example in this topic uses the **ExecuteReader** operation to execute the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="f66f9-111">Cette procédure stockée ajoute un enregistrement à la table Employee et retourne l’ID d’employé pour l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="f66f9-111">This stored procedure adds a record to the Employee table and returns the employee ID for the record.</span></span> <span data-ttu-id="f66f9-112">La procédure stockée de ADD_EMP_DETAILS est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="f66f9-112">The ADD_EMP_DETAILS stored procedure is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="f66f9-113">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f66f9-113">For more information about samples, see [Adapter samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="f66f9-114">Un exemple, **Execute_Reader**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="f66f9-114">A sample, **Execute_Reader**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="f66f9-115">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="f66f9-115">The WCF Client Class</span></span>  
 <span data-ttu-id="f66f9-116">Le nom du client WCF généré pour l’appel d’opérations génériques (ExecuteNonQuery, ExecuteReader ou ExecuteScalar) en utilisant le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="f66f9-116">The name of the WCF client generated for invoking generic operations (ExecuteNonQuery, ExecuteReader, or ExecuteScalar) using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="f66f9-117">Opérations</span><span class="sxs-lookup"><span data-stu-id="f66f9-117">Operations</span></span>|<span data-ttu-id="f66f9-118">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="f66f9-118">WCF Client Name</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="f66f9-119">ExecuteNonQuery, ExecuteReader ou ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="f66f9-119">ExecuteNonQuery, ExecuteReader, or ExecuteScalar</span></span>|<span data-ttu-id="f66f9-120">GenericTableOpClient</span><span class="sxs-lookup"><span data-stu-id="f66f9-120">GenericTableOpClient</span></span>|  
  
### <a name="method-signature-for-invoking-generic-operations"></a><span data-ttu-id="f66f9-121">Signature de méthode pour appeler les opérations génériques</span><span class="sxs-lookup"><span data-stu-id="f66f9-121">Method Signature for Invoking Generic Operations</span></span>  
 <span data-ttu-id="f66f9-122">Le tableau suivant montre la signature de la méthode exposée pour appeler les opérations génériques.</span><span class="sxs-lookup"><span data-stu-id="f66f9-122">The following table shows the signature for the method exposed to invoke the generic operations.</span></span>  
  
|<span data-ttu-id="f66f9-123">Opération</span><span class="sxs-lookup"><span data-stu-id="f66f9-123">Operation</span></span>|<span data-ttu-id="f66f9-124">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="f66f9-124">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="f66f9-125">ExecuteNonQuery</span><span class="sxs-lookup"><span data-stu-id="f66f9-125">ExecuteNonQuery</span></span>|<span data-ttu-id="f66f9-126">int ExecuteNonQuery (chaîne de requête)</span><span class="sxs-lookup"><span data-stu-id="f66f9-126">int ExecuteNonQuery(string Query)</span></span>|  
|<span data-ttu-id="f66f9-127">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="f66f9-127">ExecuteReader</span></span>|<span data-ttu-id="f66f9-128">[] De System.Data.DataSet ExecuteReader (chaîne de requête)</span><span class="sxs-lookup"><span data-stu-id="f66f9-128">System.Data.DataSet[] ExecuteReader(string Query)</span></span>|  
|<span data-ttu-id="f66f9-129">ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="f66f9-129">ExecuteScalar</span></span>|<span data-ttu-id="f66f9-130">chaîne ExecuteScalar(string Query)</span><span class="sxs-lookup"><span data-stu-id="f66f9-130">string ExecuteScalar(string Query)</span></span>|  
  
 <span data-ttu-id="f66f9-131">Par exemple, la signature pour les méthodes d’opération générique est indiquée dans l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f66f9-131">As an example, the signature for the generic operation methods is shown in the following code snippet.</span></span>  
  
```  
public partial class GenericTableOpClient : System.ServiceModel.ClientBase<GenericTableOp>, GenericTableOp {  
  public int ExecuteNonQuery(string Query);  
  public System.Data.DataSet[] ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 <span data-ttu-id="f66f9-132">Dans cet extrait de code</span><span class="sxs-lookup"><span data-stu-id="f66f9-132">In this snippet,</span></span>  
  
-   <span data-ttu-id="f66f9-133">`GenericTableOpClient`est le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="f66f9-133">`GenericTableOpClient` is the name of the class.</span></span> <span data-ttu-id="f66f9-134">Dans cet exemple, vous utilisez cette classe pour créer un client pour appeler l’opération générique, ExecuteReader.</span><span class="sxs-lookup"><span data-stu-id="f66f9-134">In this example, you use this class to create a client to invoke the generic operation, ExecuteReader.</span></span>  
  
-   <span data-ttu-id="f66f9-135">`public System.Data.DataSet[] ExecuteReader(string Query)`est la méthode que vous appelez dans cet exemple, pour appeler le ADD_EMP_DETAILS de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="f66f9-135">`public System.Data.DataSet[] ExecuteReader(string Query)` is the method that you invoke in this example to invoke the ADD_EMP_DETAILS stored procedure.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a><span data-ttu-id="f66f9-136">Création d’un Client WCF pour appeler l’opération ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="f66f9-136">Creating a WCF Client to Invoke an ExecuteReader Operation</span></span>  
 <span data-ttu-id="f66f9-137">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="f66f9-137">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF channel model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-channel-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="f66f9-138">Cette section décrit en particulier comment créer un client WCF qui appelle un **ExecuteReader** opération à exécuter la ADD_EMP_DETAILS de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="f66f9-138">This section specifically describes how to create a WCF client that invokes an **ExecuteReader** operation to execute the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="f66f9-139">Cette procédure stockée est créée en exécutant le script SQL fourni avec chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="f66f9-139">This stored procedure is created by running the SQL script provided with each sample.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a><span data-ttu-id="f66f9-140">Pour créer un client WCF pour appeler l’opération ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="f66f9-140">To create a WCF client to invoke ExecuteReader operation</span></span>  
  
1.  <span data-ttu-id="f66f9-141">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f66f9-141">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="f66f9-142">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="f66f9-142">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="f66f9-143">Générer la classe de client WCF pour le **ExecuteReader** opération générique.</span><span class="sxs-lookup"><span data-stu-id="f66f9-143">Generate the WCF client class for the **ExecuteReader** generic operation.</span></span> <span data-ttu-id="f66f9-144">Cette opération n’est disponible sous le nœud racine lorsque vous vous connectez à la base de données SQL Server à l’aide du [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f66f9-144">This operation is available under the root node when you connect to the SQL Server database using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="f66f9-145">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="f66f9-145">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f66f9-146">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="f66f9-146">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="f66f9-147">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="f66f9-147">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="f66f9-148">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f66f9-148">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
            GenericTableOpClient client = new GenericTableOpClient("SqlAdapterBinding_GenericTableOp");  
    client.ClientCredentials.UserName.UserName = "<Enter username here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="f66f9-149">Dans cet extrait de code, `GenericTableOpClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="f66f9-149">In this snippet, `GenericTableOpClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="f66f9-150">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f66f9-150">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="f66f9-151">`SqlAdapterBinding_GenericTableOp`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="f66f9-151">`SqlAdapterBinding_GenericTableOp` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f66f9-152">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="f66f9-152">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="f66f9-153">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f66f9-153">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="f66f9-154">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="f66f9-154">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="f66f9-155">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="f66f9-155">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="f66f9-156">Appeler le **ExecuteReader** opération pour le ADD_EMP_DETAILS de procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="f66f9-156">Invoke the **ExecuteReader** operation for the ADD_EMP_DETAILS stored procedure.</span></span> <span data-ttu-id="f66f9-157">Avant d’appeler l’opération ExecuteReader, vous devez ajouter le `System.Data` espace de noms à votre code.</span><span class="sxs-lookup"><span data-stu-id="f66f9-157">Before you invoke the ExecuteReader operation, you must add the `System.Data` namespace to your code.</span></span>  
  
    ```  
    string query = "EXEC ADD_EMP_DETAILS 'Tom Smith', 'Manager', 500000";  
    DataSet[] dsArray = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the ADD_EMP_DETAILS stored procedure using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataSet dataSet in dsArray)  
    {  
       foreach (DataTable tab in dsArray[0].Tables)  
       {  
           foreach (DataRow row in tab.Rows)  
           {  
              for (int i = 0; i < tab.Columns.Count; i++)  
              {  
                 Console.WriteLine("The ID for the newly added employee is : " + row[i]);  
              }  
           }  
        }  
    }  
    Console.WriteLine("*****************************************************");  
  
    ```  
  
7.  <span data-ttu-id="f66f9-158">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="f66f9-158">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="f66f9-159">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="f66f9-159">Build the project and then run it.</span></span> <span data-ttu-id="f66f9-160">L’ID de l’employé nouvellement inséré s’affiche sur la console.</span><span class="sxs-lookup"><span data-stu-id="f66f9-160">The employee ID of the newly inserted employee is displayed on the console.</span></span>