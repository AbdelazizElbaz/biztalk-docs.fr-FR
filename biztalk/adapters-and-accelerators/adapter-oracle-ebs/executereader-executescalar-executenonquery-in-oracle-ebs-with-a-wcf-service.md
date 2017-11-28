---
title: "Les opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54c42db1-9a4d-4003-af69-f75ff48b575a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eaffcdc59cd6093feababc8319c1f9f1964a0d05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executereader-executescalar-or-executenonquery-operations-in-oracle-e-business-suite-using-the-wcf-service-model"></a><span data-ttu-id="647ab-102">Opérations ExecuteReader, ExecuteScalar ou ExecuteNonQuery dans Oracle E-Business Suite à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="647ab-102">ExecuteReader, ExecuteScalar, or ExecuteNonQuery operations in Oracle E-Business Suite using the WCF service model</span></span>
<span data-ttu-id="647ab-103">Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose les opérations génériques tels que **ExecuteNonQuery**, **ExecuteReader**, et **ExecuteScalar**.</span><span class="sxs-lookup"><span data-stu-id="647ab-103">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes generic operations such as **ExecuteNonQuery**, **ExecuteReader**, and **ExecuteScalar**.</span></span> <span data-ttu-id="647ab-104">Vous pouvez utiliser ces opérations à exécuter n’importe quelle instruction dans Oracle E-Business Suite.</span><span class="sxs-lookup"><span data-stu-id="647ab-104">You can use these operations to execute any statement on Oracle E-Business Suite.</span></span> <span data-ttu-id="647ab-105">Ces opérations varient en fonction du type de réponse pour l’instruction.</span><span class="sxs-lookup"><span data-stu-id="647ab-105">These operations differ based on the kind of response you get for the statement.</span></span> <span data-ttu-id="647ab-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span><span class="sxs-lookup"><span data-stu-id="647ab-106">For more information about how the adapter supports these operations, see [Support for ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).</span></span>  
  
 <span data-ttu-id="647ab-107">Cette rubrique montre comment effectuer une **ExecuteReader** à l’aide de l’opération la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="647ab-107">This topic demonstrates how to perform an **ExecuteReader** operation using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] using the WCF service model.</span></span> <span data-ttu-id="647ab-108">Vous pouvez suivre le même ensemble de procédures décrites dans cette rubrique pour effectuer **ExecuteNonQuery** et **ExecuteScalar** operations.</span><span class="sxs-lookup"><span data-stu-id="647ab-108">You can follow the same set of procedures described in this topic to perform **ExecuteNonQuery** and **ExecuteScalar** operations.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="647ab-109">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="647ab-109">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="647ab-110">L’exemple dans cette rubrique effectue une **ExecuteReader** opération à effectuer une opération SELECT sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="647ab-110">The example in this topic performs an **ExecuteReader** operation to perform a SELECT operation on the MS_SAMPLE_EMPLOYEE interface table.</span></span> <span data-ttu-id="647ab-111">La table est créée en exécutant le script fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="647ab-111">The table is created by running the script provided with the samples.</span></span> <span data-ttu-id="647ab-112">Pour plus d’informations sur les exemples, consultez [exemples pour l’adaptateur Oracle eBusiness Suite](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="647ab-112">For more information about samples, see [Samples for the Oracle EBS adapter](../../adapters-and-accelerators/adapter-oracle-ebs/samples-for-the-oracle-ebs-adapter.md).</span></span> <span data-ttu-id="647ab-113">Un exemple, **ExecuteReader**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="647ab-113">A sample, **ExecuteReader**, which is based on this topic, is also provided with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="647ab-114">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="647ab-114">The WCF Client Class</span></span>  
 <span data-ttu-id="647ab-115">Le nom du client WCF généré pour l’appel d’opérations génériques (ExecuteNonQuery, ExecuteReader ou ExecuteScalar) en utilisant le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="647ab-115">The name of the WCF client generated for invoking generic operations (ExecuteNonQuery, ExecuteReader, or ExecuteScalar) using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="647ab-116">Opérations</span><span class="sxs-lookup"><span data-stu-id="647ab-116">Operations</span></span>|<span data-ttu-id="647ab-117">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="647ab-117">WCF Client Name</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="647ab-118">ExecuteNonQuery, ExecuteReader ou ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="647ab-118">ExecuteNonQuery, ExecuteReader, or ExecuteScalar</span></span>|<span data-ttu-id="647ab-119">GenericOperation_Client</span><span class="sxs-lookup"><span data-stu-id="647ab-119">GenericOperation_Client</span></span>|  
  
### <a name="method-signature-for-invoking-generic-operations"></a><span data-ttu-id="647ab-120">Signature de méthode pour appeler les opérations génériques</span><span class="sxs-lookup"><span data-stu-id="647ab-120">Method Signature for Invoking Generic Operations</span></span>  
 <span data-ttu-id="647ab-121">Le tableau suivant montre la signature de la méthode exposée pour appeler les opérations génériques.</span><span class="sxs-lookup"><span data-stu-id="647ab-121">The following table shows the signature for the method exposed to invoke the generic operations.</span></span>  
  
|<span data-ttu-id="647ab-122">Opération</span><span class="sxs-lookup"><span data-stu-id="647ab-122">Operation</span></span>|<span data-ttu-id="647ab-123">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="647ab-123">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="647ab-124">ExecuteNonQuery</span><span class="sxs-lookup"><span data-stu-id="647ab-124">ExecuteNonQuery</span></span>|<span data-ttu-id="647ab-125">int ExecuteNonQuery (chaîne de requête, string [] OutputRefCursorNames, out System.Data.DataSet [] OutputRefCursors)</span><span class="sxs-lookup"><span data-stu-id="647ab-125">int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors)</span></span>|  
|<span data-ttu-id="647ab-126">ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="647ab-126">ExecuteReader</span></span>|<span data-ttu-id="647ab-127">System.Data.DataSet ExecuteReader(string Query)</span><span class="sxs-lookup"><span data-stu-id="647ab-127">System.Data.DataSet ExecuteReader(string Query)</span></span>|  
|<span data-ttu-id="647ab-128">ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="647ab-128">ExecuteScalar</span></span>|<span data-ttu-id="647ab-129">chaîne ExecuteScalar(string Query)</span><span class="sxs-lookup"><span data-stu-id="647ab-129">string ExecuteScalar(string Query)</span></span>|  
  
 <span data-ttu-id="647ab-130">Par exemple, la signature pour les méthodes d’opération générique est indiquée dans l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="647ab-130">As an example, the signature for the generic operation methods is shown in the following code snippet.</span></span>  
  
```  
public partial class GenericOperation_Client : System.ServiceModel.ClientBase<GenericOperation_>, GenericOperation_ {  
  public int ExecuteNonQuery(string Query, string[] OutputRefCursorNames, out System.Data.DataSet[] OutputRefCursors);  
  public System.Data.DataSet ExecuteReader(string Query);  
  public string ExecuteScalar(string Query);  
}  
```  
  
 <span data-ttu-id="647ab-131">Dans cet extrait de code</span><span class="sxs-lookup"><span data-stu-id="647ab-131">In this snippet,</span></span>  
  
-   <span data-ttu-id="647ab-132">`GenericOperation_Client`est le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="647ab-132">`GenericOperation_Client` is the name of the class.</span></span> <span data-ttu-id="647ab-133">Cette classe est utilisée pour créer un client pour appeler l’opération générique, ExecuteReader.</span><span class="sxs-lookup"><span data-stu-id="647ab-133">This class is used to create a client to invoke the generic operation, ExecuteReader.</span></span>  
  
-   <span data-ttu-id="647ab-134">`public System.Data.DataSet ExecuteReader(string Query)`est la méthode que vous appelez pour exécuter une instruction SELECT sur la table d’interface MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="647ab-134">`public System.Data.DataSet ExecuteReader(string Query)` is the method that you invoke to perform a SELECT statement on the MS_SAMPLE_EMPLOYEE interface table.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-an-executereader-operation"></a><span data-ttu-id="647ab-135">Création d’un Client WCF pour appeler l’opération ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="647ab-135">Creating a WCF Client to Invoke an ExecuteReader Operation</span></span>  
 <span data-ttu-id="647ab-136">L’ensemble générique des actions requises pour effectuer une opération sur Oracle E-Business Suite à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de service WCF avec l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="647ab-136">The generic set of actions required to perform an operation on Oracle E-Business Suite using a WCF client involves a set of tasks described in [Overview of the WCF service model with the Oracle E-Business Suite adapter](../../adapters-and-accelerators/adapter-oracle-ebs/overview-of-the-wcf-service-model-with-the-oracle-e-business-suite-adapter.md).</span></span> <span data-ttu-id="647ab-137">Cette section décrit comment créer un client WCF pour appeler le **ExecuteReader** opération.</span><span class="sxs-lookup"><span data-stu-id="647ab-137">This section describes how to create a WCF client to invoke the **ExecuteReader** operation.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-invoke-executereader-operation"></a><span data-ttu-id="647ab-138">Pour créer un client WCF pour appeler l’opération ExecuteReader</span><span class="sxs-lookup"><span data-stu-id="647ab-138">To create a WCF client to invoke ExecuteReader operation</span></span>  
  
1.  <span data-ttu-id="647ab-139">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="647ab-139">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="647ab-140">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="647ab-140">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="647ab-141">Générer la classe de client WCF pour le **ExecuteReader** opération générique.</span><span class="sxs-lookup"><span data-stu-id="647ab-141">Generate the WCF client class for the **ExecuteReader** generic operation.</span></span> <span data-ttu-id="647ab-142">Cette opération n’est disponible sous le nœud racine lorsque vous vous connectez à Oracle E-Business Suite en utilisant le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="647ab-142">This operation is available under the root node when you connect to the Oracle E-Business Suite using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="647ab-143">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un client WCF ou un contrat de service WCF pour les artefacts de solution Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="647ab-143">For more information about generating a WCF client class, see [Generate a WCF client or a WCF service contract for Oracle E-Business Suite solution artifacts](../../adapters-and-accelerators/adapter-oracle-ebs/create-a-wcf-client-or-wcf-service-contract-for-oracle-ebs-solution-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="647ab-144">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="647ab-144">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="647ab-145">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.OracleEBS` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="647ab-145">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleEBS` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="647ab-146">Ouvrez le fichier Program.cs et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="647ab-146">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleEBS`  
  
    -   `System.ServiceModel`  
  
5.  <span data-ttu-id="647ab-147">Dans le fichier Program.cs, créez un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="647ab-147">In the Program.cs file, create a client as described in the snippet below.</span></span>  
  
    ```  
    OracleEBSBinding binding = new OracleEBSBinding();  
    EndpointAddress address = new EndpointAddress("oracleebs://ebs-72-11");  
    GenericOperation_Client client = new GenericOperation_Client(binding, address);  
    ```  
  
     <span data-ttu-id="647ab-148">Dans cet extrait de code, `GenericOperation_Client` est le client WCF défini dans OracleEBSBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="647ab-148">In this snippet, `GenericOperation_Client` is the WCF client defined in OracleEBSBindingClient.cs.</span></span> <span data-ttu-id="647ab-149">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="647ab-149">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="647ab-150">Dans cet extrait de code, vous spécifiez explicitement l’adresse de liaison et le point de terminaison dans votre code d’application.</span><span class="sxs-lookup"><span data-stu-id="647ab-150">In this snippet, you explicitly specify the binding and endpoint address in your application code.</span></span> <span data-ttu-id="647ab-151">Vous pouvez utiliser ces valeurs à partir du fichier de configuration d’application, app.config, également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="647ab-151">You can use these values from the application configuration file, app.config, also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="647ab-152">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer un client de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="647ab-152">For more information about the different ways of specifying client binding, see [Configure a client binding for the Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-client-binding-for-the-oracle-e-business-suite.md).</span></span>  
  
6.  <span data-ttu-id="647ab-153">Définir les informations d’identification pour le client.</span><span class="sxs-lookup"><span data-stu-id="647ab-153">Set the credentials for the client.</span></span>  
  
    ```  
    client.ClientCredentials.UserName.UserName = "myuser";  
    client.ClientCredentials.UserName.Password = "mypassword";  
    ```  
  
7.  <span data-ttu-id="647ab-154">Étant donné que vous effectuez une opération sur une table d’interface, vous devez définir le contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="647ab-154">Because you are performing an operation on an interface table, you must set the application context.</span></span> <span data-ttu-id="647ab-155">Dans cet exemple, pour définir le contexte d’application, que vous spécifiez la **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison.</span><span class="sxs-lookup"><span data-stu-id="647ab-155">In this example, to set the application context, you specify the **OracleUserName**, **OraclePassword**, and **OracleEBSResponsibilityName** binding properties.</span></span> <span data-ttu-id="647ab-156">Pour plus d’informations sur le contexte de l’application, consultez [définir le contexte application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span><span class="sxs-lookup"><span data-stu-id="647ab-156">For more information about application context, see [Set application context](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).</span></span>  
  
    ```  
    binding.OracleUserName = "myOracleEBSUserName";  
    binding.OraclePassword = "myOracleEBSPassword";  
    binding.OracleEBSResponsibilityName = "myOracleEBSResponsibility";  
    ```  
  
8.  <span data-ttu-id="647ab-157">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="647ab-157">Open the client as described in the snippet below:</span></span>  
  
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
  
9. <span data-ttu-id="647ab-158">Appeler le **ExecuteReader** opération pour effectuer l’opération SELECT sur la table MS_SAMPLE_EMPLOYEE.</span><span class="sxs-lookup"><span data-stu-id="647ab-158">Invoke the **ExecuteReader** operation for performing the SELECT operation on MS_SAMPLE_EMPLOYEE table.</span></span> <span data-ttu-id="647ab-159">Avant d’appeler l’opération ExecuteReader, vous devez ajouter le `System.Data` espace de noms à votre code.</span><span class="sxs-lookup"><span data-stu-id="647ab-159">Before you invoke the ExecuteReader operation, you must add the `System.Data` namespace to your code.</span></span>  
  
    ```  
    string query = "SELECT * FROM MS_SAMPLE_EMPLOYEE";  
    DataSet ds = client.ExecuteReader(query);  
  
    Console.WriteLine("Invoking the SELECT statement using ExecuteReader");  
    Console.WriteLine("*****************************************************");  
    foreach (DataTable tab in ds.Tables)  
    {  
       foreach (DataRow row in tab.Rows)  
       {  
          Console.WriteLine("The details of the employee are: ");  
          for (int i = 0; i < tab.Columns.Count; i++)  
          {  
             Console.WriteLine(row[i]);  
          }  
          Console.WriteLine();  
       }  
    }  
    Console.WriteLine("*****************************************************");  
    Console.ReadLine();  
  
    ```  
  
10. <span data-ttu-id="647ab-160">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="647ab-160">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
11. <span data-ttu-id="647ab-161">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="647ab-161">Build the project and then run it.</span></span> <span data-ttu-id="647ab-162">Tous les enregistrements dans la table MS_SAMPLE_EMPLOYEE sont affichés sur la console.</span><span class="sxs-lookup"><span data-stu-id="647ab-162">All the records in the MS_SAMPLE_EMPLOYEE table are displayed on the console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="647ab-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="647ab-163">See Also</span></span>  
 [<span data-ttu-id="647ab-164">Développer des applications d’Oracle E-Business Suite à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="647ab-164">Develop Oracle E-Business Suite applications using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md)