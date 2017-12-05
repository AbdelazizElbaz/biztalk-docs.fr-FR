---
title: "Appeler des fonctions scalaires dans SQL Server à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a331e275-3c81-41a8-9ba1-3a801ebc259a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a04904f1170644498d49670104a842b4c8f9dd2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-scalar-functions-in-sql-server-by-using-the-wcf-service-model"></a><span data-ttu-id="92c9e-102">Appeler des fonctions scalaires dans SQL Server à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="92c9e-102">Invoke Scalar Functions in SQL Server by Using the WCF Service Model</span></span>
<span data-ttu-id="92c9e-103">Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans une application .NET à l’aide du modèle de service WCF pour appeler les fonctions scalaires dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92c9e-103">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in a .NET application using the WCF service model to invoke scalar functions in SQL Server.</span></span> <span data-ttu-id="92c9e-104">L’adaptateur expose les fonctions scalaires en tant que méthodes pouvant être appelées directement sur le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92c9e-104">The adapter exposes the scalar functions as methods that can be invoked directly on SQL Server.</span></span> <span data-ttu-id="92c9e-105">Pour plus d’informations sur la façon dont l’adaptateur prend en charge les fonctions scalaires, consultez [exécuter les fonctions scalaires dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/execute-scalar-functions-in-sql-server-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="92c9e-105">For more information about how the adapter supports scalar functions, see [Execute Scalar Functions in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-scalar-functions-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
## <a name="how-this-topic-demonstrates-invoking-scalar-functions-using-the-wcf-service-model"></a><span data-ttu-id="92c9e-106">Comment cette rubrique illustre l’appel de fonctions scalaires à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="92c9e-106">How This Topic Demonstrates Invoking Scalar Functions Using the WCF Service Model</span></span>  
 <span data-ttu-id="92c9e-107">Cette rubrique montre comment appeler la fonction GET_EMP_ID dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92c9e-107">This topic demonstrates how to invoke the GET_EMP_ID function in a SQL Server database.</span></span> <span data-ttu-id="92c9e-108">La fonction GET_EMP_ID prend la désignation d’un employé dans le **employé** de table et retourne l’ID d’employé correspondant.</span><span class="sxs-lookup"><span data-stu-id="92c9e-108">The GET_EMP_ID function takes the designation of an employee in the **Employee** table and returns the corresponding employee ID.</span></span> <span data-ttu-id="92c9e-109">La fonction GET_EMP_ID et **employé** table sont créées en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="92c9e-109">The GET_EMP_ID function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="92c9e-110">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92c9e-110">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="92c9e-111">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="92c9e-111">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="92c9e-112">L’exemple de cette rubrique appelé la fonction scalaire GET_EMP_ID sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="92c9e-112">The example in this topic invoked the GET_EMP_ID scalar function on the Employee table.</span></span> <span data-ttu-id="92c9e-113">La fonction GET_EMP_ID et **employé** table sont créées en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="92c9e-113">The GET_EMP_ID function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="92c9e-114">Un exemple, **ScalarFunction_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="92c9e-114">A sample, **ScalarFunction_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span> <span data-ttu-id="92c9e-115">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92c9e-115">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="92c9e-116">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="92c9e-116">The WCF Client Class</span></span>  
 <span data-ttu-id="92c9e-117">Le nom du client WCF généré pour l’appel de la fonction scalaire dans SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="92c9e-117">The name of the WCF client generated for invoking the scalar function in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="92c9e-118">Objet de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="92c9e-118">SQL Server Database Artifact</span></span>|<span data-ttu-id="92c9e-119">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="92c9e-119">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="92c9e-120">Fonction scalaire</span><span class="sxs-lookup"><span data-stu-id="92c9e-120">Scalar function</span></span>|<span data-ttu-id="92c9e-121">Client de ScalarFunctions_ [schéma]</span><span class="sxs-lookup"><span data-stu-id="92c9e-121">ScalarFunctions_[SCHEMA]Client</span></span>|  
  
 <span data-ttu-id="92c9e-122">[Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.</span><span class="sxs-lookup"><span data-stu-id="92c9e-122">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-scalar-functions"></a><span data-ttu-id="92c9e-123">Signature de méthode d’appel de fonctions scalaires</span><span class="sxs-lookup"><span data-stu-id="92c9e-123">Method Signature for Invoking Scalar Functions</span></span>  
 <span data-ttu-id="92c9e-124">Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="92c9e-124">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="92c9e-125">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="92c9e-125">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="92c9e-126">Opération</span><span class="sxs-lookup"><span data-stu-id="92c9e-126">Operation</span></span>|<span data-ttu-id="92c9e-127">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="92c9e-127">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="92c9e-128">Nom de la fonction scalaire</span><span class="sxs-lookup"><span data-stu-id="92c9e-128">Scalar function name</span></span>|<span data-ttu-id="92c9e-129">public *< return_type >**< scalar_function_name >*(param1, param2,...)</span><span class="sxs-lookup"><span data-stu-id="92c9e-129">public *<return_type>**<scalar_function_name>*(param1, param2, …)</span></span>|  
  
 <span data-ttu-id="92c9e-130">\<*retrun_type* \> = type de retour définie dans la définition de fonction</span><span class="sxs-lookup"><span data-stu-id="92c9e-130">\<*retrun_type*\> = Return type defined in the function definition</span></span>  
  
 <span data-ttu-id="92c9e-131">\<*scalar_function_name* \> = nom de la fonction scalaire.</span><span class="sxs-lookup"><span data-stu-id="92c9e-131">\<*scalar_function_name*\> = Name of the scalar function.</span></span>  
  
 <span data-ttu-id="92c9e-132">Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **GET_EMP_ID** des fonctions scalaires, dans le schéma dbo, qui prend la désignation de l’employé en tant que paramètre et retourne un employé ID () (entier).</span><span class="sxs-lookup"><span data-stu-id="92c9e-132">As an example, the following code shows the method signatures for a WCF client class generated for the **GET_EMP_ID** scalar functions, in the dbo schema, which takes the employee designation as a parameter and returns an employee ID (integer).</span></span>  
  
```  
public partial class ScalarFunctions_dboClient : System.ServiceModel.ClientBase<ScalarFunctions_dbo>, ScalarFunctions_dbo {      
    public System.Nullable<int> GET_EMP_ID(string emp_desig);  
}  
```  
  
 <span data-ttu-id="92c9e-133">Dans cet extrait de code, **ScalarFunctions_dboClient** est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92c9e-133">In this snippet, **ScalarFunctions_dboClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-invoking-scalar-functions"></a><span data-ttu-id="92c9e-134">Paramètres pour l’appel de fonctions scalaires</span><span class="sxs-lookup"><span data-stu-id="92c9e-134">Parameters for Invoking Scalar Functions</span></span>  
 <span data-ttu-id="92c9e-135">Les paramètres pour les méthodes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour appeler une valeur scalaire (fonction) sont les mêmes que les paramètres définis dans la définition de fonction scalaire dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92c9e-135">The parameters for the methods exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to invoke a scalar function are the same as the parameters defined in the scalar function definition in SQL Server.</span></span> <span data-ttu-id="92c9e-136">Par exemple, le paramètre pour l’appel de la fonction scalaire GET_EMP_ID est emp_desig et prend la désignation d’un employé.</span><span class="sxs-lookup"><span data-stu-id="92c9e-136">For example, the parameter for invoking the GET_EMP_ID scalar function is emp_desig and takes an employee’s designation.</span></span>  
  
 <span data-ttu-id="92c9e-137">Là encore, la valeur de retour pour une fonction scalaire est identique à la valeur de retour définie dans la définition de fonction scalaire dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="92c9e-137">Again, the return value for a scalar function is same as the return value defined in the scalar function definition in SQL Server.</span></span> <span data-ttu-id="92c9e-138">Par exemple, la valeur de retour pour la fonction GET_EMP_ID est ID d’un employé de type entier.</span><span class="sxs-lookup"><span data-stu-id="92c9e-138">For example, the return value for the GET_EMP_ID function is an employee’s ID of type integer.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-scalar-functions"></a><span data-ttu-id="92c9e-139">Création d’un Client WCF pour appeler des fonctions scalaires</span><span class="sxs-lookup"><span data-stu-id="92c9e-139">Creating a WCF Client to Invoke Scalar Functions</span></span>  
 <span data-ttu-id="92c9e-140">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="92c9e-140">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="92c9e-141">Cette section décrit comment créer un client WCF pour appeler le **GET_EMP_ID** fonction scalaire.</span><span class="sxs-lookup"><span data-stu-id="92c9e-141">This section describes how to create a WCF client to invoke the **GET_EMP_ID** scalar function.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="92c9e-142">Pour créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="92c9e-142">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="92c9e-143">Créez un projet Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92c9e-143">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="92c9e-144">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="92c9e-144">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="92c9e-145">Générer la classe de client WCF pour le **GET_EMP_ID** fonction scalaire.</span><span class="sxs-lookup"><span data-stu-id="92c9e-145">Generate the WCF client class for the **GET_EMP_ID** scalar function.</span></span> <span data-ttu-id="92c9e-146">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="92c9e-146">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3.  <span data-ttu-id="92c9e-147">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="92c9e-147">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="92c9e-148">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="92c9e-148">Open the Program.cs and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              ScalarFunctions_dboClient client = new ScalarFunctions_dboClient("SqlAdapterBinding_ScalarFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="92c9e-149">Dans cet extrait de code, `ScalarFunctions_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="92c9e-149">In this snippet, `ScalarFunctions_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="92c9e-150">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92c9e-150">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="92c9e-151">`SqlAdapterBinding_ScalarFunctions_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="92c9e-151">`SqlAdapterBinding_ScalarFunctions_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92c9e-152">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="92c9e-152">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="92c9e-153">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="92c9e-153">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="92c9e-154">Pour plus d’informations sur les différentes façons de spécifier puis liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="92c9e-154">For more information on the different ways of specifying then client binding, see [Configure  a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="92c9e-155">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="92c9e-155">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="92c9e-156">Appeler le **GET_EMP_ID** fonction pour extraire l’ID d’un employé avec la désignation en tant que « Manager ».</span><span class="sxs-lookup"><span data-stu-id="92c9e-156">Invoke the **GET_EMP_ID** function to retrieve the ID for an employee with the designation as “Manager”.</span></span>  
  
    ```  
    Console.WriteLine("Invoking the GET_EMP_ID function");  
    string emp_designation = "Manager";  
    try  
    {  
          System.Nullable<int> emp_id = client.GET_EMP_ID(emp_designation);  
          Console.WriteLine("The Employee ID for the employee with 'Manager' designation is:" + emp_id);  
    }  
    catch (Exception e)  
    {  
          Console.WriteLine("Exception: " + e.Message);  
          throw;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="92c9e-157">Par souci de simplicité, le **employé** table possède un seul employé avec la désignation de « Manager ».</span><span class="sxs-lookup"><span data-stu-id="92c9e-157">For the sake of simplicity, the **Employee** table has only one employee with “Manager” designation.</span></span> <span data-ttu-id="92c9e-158">Si la table cible a plusieurs employés avec la désignation de même, vous devez définir la fonction en conséquence.</span><span class="sxs-lookup"><span data-stu-id="92c9e-158">If your target table has more employees with the same designation, you must define the function accordingly.</span></span>  
  
7.  <span data-ttu-id="92c9e-159">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="92c9e-159">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="92c9e-160">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="92c9e-160">Build the project and then run it.</span></span> <span data-ttu-id="92c9e-161">L’application affiche l’ID de l’employé avec la désignation de « Manager ».</span><span class="sxs-lookup"><span data-stu-id="92c9e-161">The application displays the employee ID of the employee with the designation of “Manager”.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c9e-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92c9e-162">See Also</span></span>  
[<span data-ttu-id="92c9e-163">Développer des applications en utilisant le modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="92c9e-163">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)