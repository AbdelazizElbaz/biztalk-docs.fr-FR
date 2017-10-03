---
title: "Appeler des fonctions table dans SQL Server à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48688bcc-36b4-4cc1-b078-17e7a5e1cf8c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a736a82e57f71568f8718a6e4d41e7b649004120
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-table-valued-functions-in-sql-server-by-using-the-wcf-service-model"></a><span data-ttu-id="9c2d8-102">Appeler des fonctions table dans SQL Server à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="9c2d8-102">Invoke Table-Valued Functions in SQL Server by Using the WCF Service Model</span></span>
<span data-ttu-id="9c2d8-103">Vous pouvez utiliser la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] dans une application .NET à l’aide du modèle de service WCF pour appeler des fonctions table dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-103">You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] in a .NET application using the WCF service model to invoke table-valued functions in SQL Server.</span></span> <span data-ttu-id="9c2d8-104">L’adaptateur expose les fonctions table en tant que méthodes pouvant être appelées directement sur le serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-104">The adapter exposes the table-valued functions as methods that can be invoked directly on SQL Server.</span></span> <span data-ttu-id="9c2d8-105">Pour plus d’informations sur la façon dont l’adaptateur prend en charge les fonctions scalaires, consultez [Execute Table-Valued des fonctions dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d8-105">For more information about how the adapter supports scalar functions, see [Execute Table-Valued Functions in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md).</span></span>  
  
 <span data-ttu-id="9c2d8-106">Cette rubrique montre comment appeler la fonction TVF_EMPLOYEE dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-106">This topic demonstrates how to invoke the TVF_EMPLOYEE function in a SQL Server database.</span></span> <span data-ttu-id="9c2d8-107">La fonction TVF_EMPLOYEE prend la désignation d’un employé dans le **employé** de table et retourne l’enregistrement de l’employé.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-107">The TVF_EMPLOYEE function takes the designation of an employee in the **Employee** table and returns the record for the employee.</span></span> <span data-ttu-id="9c2d8-108">La fonction TVF_EMPLOYEE et **employé** table sont créées en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-108">The TVF_EMPLOYEE function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="9c2d8-109">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d8-109">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="9c2d8-110">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="9c2d8-110">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="9c2d8-111">L’exemple de cette rubrique a appelé la fonction table TVF_EMPLOYEE sur le **employé** table.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-111">The example in this topic invoked the TVF_EMPLOYEE table-valued function on the **Employee** table.</span></span> <span data-ttu-id="9c2d8-112">Fonction TVF_EMPLOYEE et **employé** table sont créées en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-112">TVF_EMPLOYEE function and the **Employee** table are created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="9c2d8-113">Un exemple, **TableFunction_ServiceModel**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-113">A sample, **TableFunction_ServiceModel**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span> <span data-ttu-id="9c2d8-114">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d8-114">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="9c2d8-115">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="9c2d8-115">The WCF Client Class</span></span>  
 <span data-ttu-id="9c2d8-116">Le nom du client WCF généré pour l’appel de la fonction scalaire dans SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est répertorié dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-116">The name of the WCF client generated for invoking the scalar function in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is listed in the following table.</span></span>  
  
|<span data-ttu-id="9c2d8-117">Objet de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="9c2d8-117">SQL Server Database Artifact</span></span>|<span data-ttu-id="9c2d8-118">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="9c2d8-118">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="9c2d8-119">Fonction table</span><span class="sxs-lookup"><span data-stu-id="9c2d8-119">Table-valued function</span></span>|<span data-ttu-id="9c2d8-120">Client de TableValuedFunctions_ [schéma]</span><span class="sxs-lookup"><span data-stu-id="9c2d8-120">TableValuedFunctions_[SCHEMA]Client</span></span>|  
  
 <span data-ttu-id="9c2d8-121">[Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-121">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-table-valued-functions"></a><span data-ttu-id="9c2d8-122">Signature de méthode pour appeler des fonctions table</span><span class="sxs-lookup"><span data-stu-id="9c2d8-122">Method Signature for Invoking Table-valued Functions</span></span>  
 <span data-ttu-id="9c2d8-123">Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-123">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="9c2d8-124">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-124">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="9c2d8-125">Opération</span><span class="sxs-lookup"><span data-stu-id="9c2d8-125">Operation</span></span>|<span data-ttu-id="9c2d8-126">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="9c2d8-126">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="9c2d8-127">Nom de la fonction table</span><span class="sxs-lookup"><span data-stu-id="9c2d8-127">Table-valued function name</span></span>|<span data-ttu-id="9c2d8-128">public [NAMESPACE] [nom_fonction] [,] [nom_fonction] (param1, param2,...\)</span><span class="sxs-lookup"><span data-stu-id="9c2d8-128">public [NAMESPACE][FUNCTION_NAME][] [FUNCTION_NAME](param1, param2, …\)</span></span>|  
  
 <span data-ttu-id="9c2d8-129">[Espace de noms] = l’espace de noms, par exemple, schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE</span><span class="sxs-lookup"><span data-stu-id="9c2d8-129">[NAMESPACE] = The namespace, for example, schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE</span></span>  
  
 <span data-ttu-id="9c2d8-130">[Nom_fonction] = nom de la fonction table.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-130">[FUNCTION_NAME] = Name of the table-valued function.</span></span>  
  
 <span data-ttu-id="9c2d8-131">Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **TVF_EMPLOYEE** des fonctions scalaires, dans le schéma dbo, qui prend la désignation de l’employé en tant que paramètre et retourne l’employé enregistrement.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-131">As an example, the following code shows the method signatures for a WCF client class generated for the **TVF_EMPLOYEE** scalar functions, in the dbo schema, which takes the employee designation as a parameter and returns the employee record.</span></span>  
  
```  
public partial class TableValuedFunctions_dboClient : System.ServiceModel.ClientBase<TableValuedFunctions_dbo>, TableValuedFunctions_dbo {      
    public schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] TVF_EMPLOYEE(string emp_desig);  
}  
```  
  
 <span data-ttu-id="9c2d8-132">Dans cet extrait de code, **TableValuedFunctions_dboClient** est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c2d8-132">In this snippet, **TableValuedFunctions_dboClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-invoking-table-valued-functions"></a><span data-ttu-id="9c2d8-133">Paramètres pour l’appel de fonctions table</span><span class="sxs-lookup"><span data-stu-id="9c2d8-133">Parameters for Invoking Table-valued Functions</span></span>  
 <span data-ttu-id="9c2d8-134">Les paramètres pour les méthodes exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour appeler une fonction table sont les mêmes que les paramètres définis dans la définition de fonction dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-134">The parameters for the methods exposed by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to invoke a table-valued function are the same as the parameters defined in the function definition in SQL Server.</span></span> <span data-ttu-id="9c2d8-135">Par exemple, le paramètre pour l’appel de la fonction table TVF_EMPLOYEE est emp_desig et prend la désignation d’un employé.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-135">For example, the parameter for invoking the TVF_EMPLOYEE table-valued function is emp_desig and takes an employee’s designation.</span></span>  
  
 <span data-ttu-id="9c2d8-136">Là encore, la valeur de retour pour une fonction table est identique à la valeur de retour définie dans la définition de fonction dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-136">Again, the return value for a table-valued function is same as the return value defined in the function definition in SQL Server.</span></span> <span data-ttu-id="9c2d8-137">Par exemple, la valeur de retour pour la fonction TVF_EMPLOYEE est un tableau d’enregistrements de type schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE [].</span><span class="sxs-lookup"><span data-stu-id="9c2d8-137">For example, the return value for the TVF_EMPLOYEE function is an array of records of type schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[].</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-table-valued-functions"></a><span data-ttu-id="9c2d8-138">Création d’un Client WCF pour appeler des fonctions table</span><span class="sxs-lookup"><span data-stu-id="9c2d8-138">Creating a WCF Client to Invoke Table-valued Functions</span></span>  
 <span data-ttu-id="9c2d8-139">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d8-139">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="9c2d8-140">Cette section décrit comment créer un client WCF pour appeler le **TVF_EMPLOYEE** fonction table.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-140">This section describes how to create a WCF client to invoke the **TVF_EMPLOYEE** table-valued function.</span></span>  
  
 
1.  <span data-ttu-id="9c2d8-141">Créez un projet Visual c# dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c2d8-141">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsVStudioNoVersion-md.md)].</span></span> <span data-ttu-id="9c2d8-142">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-142">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="9c2d8-143">Générer la classe de client WCF pour le **TVF_EMPLOYEE** fonction scalaire.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-143">Generate the WCF client class for the **TVF_EMPLOYEE** scalar function.</span></span> <span data-ttu-id="9c2d8-144">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d8-144">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3.  <span data-ttu-id="9c2d8-145">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-145">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="9c2d8-146">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-146">Open the Program.cs and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TableValuedFunctions_dboClient client = new TableValuedFunctions_dboClient("SqlAdapterBinding_TableValuedFunctions_dbo");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="9c2d8-147">Dans cet extrait de code, `TableValuedFunctions_dboClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-147">In this snippet, `TableValuedFunctions_dboClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="9c2d8-148">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9c2d8-148">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="9c2d8-149">`SqlAdapterBinding_TableValuedFunctions_dbo`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-149">`SqlAdapterBinding_TableValuedFunctions_dbo` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9c2d8-150">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-150">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="9c2d8-151">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-151">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="9c2d8-152">Pour plus d’informations sur les différentes façons de spécifier puis liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="9c2d8-152">For more information on the different ways of specifying then client binding, see [Configure a Client Binding for the SQL Adapter](configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="9c2d8-153">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9c2d8-153">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="9c2d8-154">Appeler le **TVF_EMPLOYEE** fonction pour récupérer tous les enregistrements de l’employé ayant la désignation « Manager ».</span><span class="sxs-lookup"><span data-stu-id="9c2d8-154">Invoke the **TVF_EMPLOYEE** function to retrieve all the employee records having the “Manager” designation.</span></span>  
  
    ```  
    Console.WriteLine("Invoking the TVF_EMPLOYEE function");  
    schemas.microsoft.com.Sql._2008._05.Types.TableFunctionReturnTables.dbo.TVF_EMPLOYEE[] emp_details;  
    string emp_designation = "Manager";  
  
    try  
    {  
        emp_details = client.TVF_EMPLOYEE(emp_designation);  
    }  
    catch (Exception e)  
    {  
        Console.WriteLine("Exception: " + e.Message);  
        throw;  
    }  
    Console.WriteLine("The details for the employee with the 'Manager' designation are:");  
    Console.WriteLine("*******************************************************************");  
    for (int i = 0; i < emp_details.Length; i++)  
    {  
        Console.WriteLine("Employee ID        : " + emp_details[i].Employee_ID);  
        Console.WriteLine("Employee Name      : " + emp_details[i].Name);  
        Console.WriteLine("Employee Desigation: " + emp_details[i].Designation);  
        Console.WriteLine("Employee Salary    : " + emp_details[i].Salary);  
        Console.WriteLine();  
    }  
    ```  
  
7.  <span data-ttu-id="9c2d8-155">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="9c2d8-155">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="9c2d8-156">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="9c2d8-156">Build the project and then run it.</span></span> <span data-ttu-id="9c2d8-157">L’application affiche l’ID d’employé, le nom et le salaire de tous les employés avec une désignation « Manager ».</span><span class="sxs-lookup"><span data-stu-id="9c2d8-157">The application displays the employee ID, name, and salary of all the employees with a “Manager” designation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2d8-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c2d8-158">See Also</span></span>  
[<span data-ttu-id="9c2d8-159">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="9c2d8-159">Develop applications using the WCF Service model</span></span>](develop-sql-applications-using-the-wcf-service-model.md)