---
title: "Insérer, mettre à jour, supprimer ou sélectionner des opérations dans SQL à l’aide du modèle de service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 340048ad-ce28-4acf-ae4e-f18bdb3b6f47
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2bc522a1b0b60a9ba0b8407228dd1db65c4e6f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-or-select-operations-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="31d04-102">Insérer, mettre à jour, supprimer ou sélectionner des opérations dans SQL à l’aide du modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="31d04-102">Insert, update, delete, or select operations in SQL using the WCF service model</span></span>
<span data-ttu-id="31d04-103">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] détecte un ensemble d’opérations de base sur les tables de base de données SQL Server et les vues Insert, Select, Update et Delete.</span><span class="sxs-lookup"><span data-stu-id="31d04-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] discovers a set of basic Insert, Select, Update, and Delete operations on SQL Server database tables and views.</span></span> <span data-ttu-id="31d04-104">À l’aide de ces opérations, vous pouvez effectuer simple SQL Insert, Select, Update et supprimer les instructions qualifiées par Where clause sur une table ou vue cible.</span><span class="sxs-lookup"><span data-stu-id="31d04-104">By using these operations, you can perform simple SQL Insert, Select, Update, and Delete statements qualified by a Where clause on a target table or view.</span></span> <span data-ttu-id="31d04-105">Cette rubrique fournit des instructions sur la façon d’effectuer ces opérations à l’aide du modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="31d04-105">This topic provides instructions on how to perform these operations using the WCF service model.</span></span>  
  
 <span data-ttu-id="31d04-106">Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="31d04-106">For more information on how the adapter supports these operations, see [Insert, Update, Delete, and Select Operations on Tables and Views with the SQL adapter](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31d04-107">Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.</span><span class="sxs-lookup"><span data-stu-id="31d04-107">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) before you start developing your application.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="31d04-108">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="31d04-108">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="31d04-109">L’exemple de cette rubrique effectue des opérations sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-109">The example in this topic performs operations on the Employee table.</span></span> <span data-ttu-id="31d04-110">La table Employee est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="31d04-110">The Employee table is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="31d04-111">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31d04-111">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="31d04-112">Un exemple, **EmployeeBasicOps**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="31d04-112">A sample, **EmployeeBasicOps**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="31d04-113">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="31d04-113">The WCF Client Class</span></span>  
 <span data-ttu-id="31d04-114">Le nom du client WCF généré pour les opérations SQL de base qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="31d04-114">The name of the WCF client generated for the basic SQL operations that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers is based on the name of the table or view, as listed in the following table.</span></span>  
  
|<span data-ttu-id="31d04-115">Objet de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="31d04-115">SQL Server Database Artifact</span></span>|<span data-ttu-id="31d04-116">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="31d04-116">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="31d04-117">Table</span><span class="sxs-lookup"><span data-stu-id="31d04-117">Table</span></span>|<span data-ttu-id="31d04-118">TableOp_ [schéma] _ [nom_table] Client</span><span class="sxs-lookup"><span data-stu-id="31d04-118">TableOp_[Schema]_[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="31d04-119">Affichage</span><span class="sxs-lookup"><span data-stu-id="31d04-119">View</span></span>|<span data-ttu-id="31d04-120">ViewOp_ [schéma] _ [VIEW_NAME] Client</span><span class="sxs-lookup"><span data-stu-id="31d04-120">ViewOp_[Schema]_[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="31d04-121">[Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.</span><span class="sxs-lookup"><span data-stu-id="31d04-121">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
 <span data-ttu-id="31d04-122">[Nom_table] = nom de la table ; par exemple, les employés.</span><span class="sxs-lookup"><span data-stu-id="31d04-122">[TABLE_NAME] = The name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="31d04-123">[VIEW_NAME] = le nom de la vue ; par exemple, Employee_View.</span><span class="sxs-lookup"><span data-stu-id="31d04-123">[VIEW_NAME] = The name of the view; for example, Employee_View.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-tables"></a><span data-ttu-id="31d04-124">Signature de méthode pour appeler des opérations sur les Tables</span><span class="sxs-lookup"><span data-stu-id="31d04-124">Method Signature for Invoking Operations on Tables</span></span>  
 <span data-ttu-id="31d04-125">Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="31d04-125">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="31d04-126">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="31d04-126">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="31d04-127">Opération</span><span class="sxs-lookup"><span data-stu-id="31d04-127">Operation</span></span>|<span data-ttu-id="31d04-128">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="31d04-128">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="31d04-129">Insert</span><span class="sxs-lookup"><span data-stu-id="31d04-129">Insert</span></span>|<span data-ttu-id="31d04-130">[] long Insert ([TABLE_NS]. [ Lignes [] nom_table]) ;</span><span class="sxs-lookup"><span data-stu-id="31d04-130">long[] Insert([TABLE_NS].[TABLE_NAME][] Rows);</span></span>|  
|<span data-ttu-id="31d04-131">Select</span><span class="sxs-lookup"><span data-stu-id="31d04-131">Select</span></span>|<span data-ttu-id="31d04-132">[TABLE_NS]. [NOM_TABLE] [] Sélectionnez (chaîne, chaîne de requête les colonnes) ;</span><span class="sxs-lookup"><span data-stu-id="31d04-132">[TABLE_NS].[TABLE_NAME][] Select(string COLUMNS, string QUERY);</span></span>|  
|<span data-ttu-id="31d04-133">Update</span><span class="sxs-lookup"><span data-stu-id="31d04-133">Update</span></span>|<span data-ttu-id="31d04-134">int mise à jour ([TABLE_NS]. [ NOM_TABLE]. Lignes [] RowPair) ;</span><span class="sxs-lookup"><span data-stu-id="31d04-134">int Update([TABLE_NS].[TABLE_NAME].RowPair[] Rows);</span></span>|  
|<span data-ttu-id="31d04-135">DELETE</span><span class="sxs-lookup"><span data-stu-id="31d04-135">Delete</span></span>|<span data-ttu-id="31d04-136">int Delete ([TABLE_NS]. [ Lignes [] nom_table]) ;</span><span class="sxs-lookup"><span data-stu-id="31d04-136">int Delete([TABLE_NS].[TABLE_NAME][] Rows);</span></span>|  
  
 <span data-ttu-id="31d04-137">[TABLE_NS] = le nom de l’espace de noms de table ; par exemple, schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-137">[TABLE_NS] = The name of the table namespace; for example, schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee.</span></span>  
  
 <span data-ttu-id="31d04-138">[Nom_table] = nom de la table ; par exemple, les employés.</span><span class="sxs-lookup"><span data-stu-id="31d04-138">[TABLE_NAME] = The name of the table; for example, Employee.</span></span>  
  
 <span data-ttu-id="31d04-139">Par exemple, le code suivant montre les signatures de méthode pour une classe de client WCF généré pour les opérations Delete, Insert, Select et Update sur la table Employee sous le schéma par défaut « dbo ».</span><span class="sxs-lookup"><span data-stu-id="31d04-139">As an example, the following code shows the method signatures for a WCF client class generated for the Delete, Insert, Select and Update operations on the Employee table under the default “dbo” schema.</span></span>  
  
```  
public partial class TableOp_dbo_EmployeeClient : System.ServiceModel.ClientBase<TableOp_dbo_Employee>, TableOp_dbo_Employee {      
    public int Delete(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public long[] Insert(schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Rows);  
  
    public schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] Select(string Columns, string Query);  
  
    public int Update(schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] Rows);  
}  
```  
  
 <span data-ttu-id="31d04-140">Dans cet extrait de code, TableOp_dbo_EmployeeClient est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31d04-140">In this snippet, TableOp_dbo_EmployeeClient is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-table-operations"></a><span data-ttu-id="31d04-141">Paramètres pour les opérations de Table</span><span class="sxs-lookup"><span data-stu-id="31d04-141">Parameters for Table Operations</span></span>  
 <span data-ttu-id="31d04-142">Cette section fournit les paramètres requis par chaque opération de table</span><span class="sxs-lookup"><span data-stu-id="31d04-142">This section provides the parameters required by each table operation</span></span>  
  
 <span data-ttu-id="31d04-143">**Opération d’insertion**</span><span class="sxs-lookup"><span data-stu-id="31d04-143">**Insert Operation**</span></span>  
  
|<span data-ttu-id="31d04-144">Insérer le type d’opération</span><span class="sxs-lookup"><span data-stu-id="31d04-144">Insert operation type</span></span>|<span data-ttu-id="31d04-145">JEU D’ENREGISTREMENTS</span><span class="sxs-lookup"><span data-stu-id="31d04-145">RECORDSET</span></span>|  
|---------------------------|---------------|  
|<span data-ttu-id="31d04-146">Enregistrement de plusieurs</span><span class="sxs-lookup"><span data-stu-id="31d04-146">Multiple record</span></span>|<span data-ttu-id="31d04-147">Collection de INSERTRECORDS doivent être insérés dans la table.</span><span class="sxs-lookup"><span data-stu-id="31d04-147">A collection of INSERTRECORDS that should be inserted into the table.</span></span>|  
  
 <span data-ttu-id="31d04-148">L’opération d’insertion, retourne un tableau de type de données Long et stocke les valeurs d’identité de lignes insérées, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="31d04-148">The insert operation returns an array of Long data type and stores the identity values of the inserted rows, if any.</span></span> <span data-ttu-id="31d04-149">Si elle n’existe aucune colonne d’identité dans une table, la valeur de retour est NULL.</span><span class="sxs-lookup"><span data-stu-id="31d04-149">If there is no identity column in a table, the return value is NULL.</span></span>  
  
 <span data-ttu-id="31d04-150">**Sélectionnez l’opération**</span><span class="sxs-lookup"><span data-stu-id="31d04-150">**Select Operation**</span></span>  
  
|<span data-ttu-id="31d04-151">NOMS DE COLONNE</span><span class="sxs-lookup"><span data-stu-id="31d04-151">COLUMN_NAMES</span></span>|<span data-ttu-id="31d04-152">QUERY</span><span class="sxs-lookup"><span data-stu-id="31d04-152">QUERY</span></span>|  
|-------------------|-----------|  
|<span data-ttu-id="31d04-153">Une liste délimitée par des virgules de noms de colonnes dans la cible. par exemple, « Employee_ID, désignation ».</span><span class="sxs-lookup"><span data-stu-id="31d04-153">A comma-delimited list of column names in the target; for example, "Employee_ID, Designation".</span></span> <span data-ttu-id="31d04-154">La liste de colonnes spécifie les colonnes de la cible doit être retournée dans le jeu de résultats.</span><span class="sxs-lookup"><span data-stu-id="31d04-154">The column list specifies the columns of the target that should be returned in the result set.</span></span> <span data-ttu-id="31d04-155">Colonnes non spécifiées dans la liste des colonnes seront fixés à leurs valeurs par défaut de .NET dans le jeu d’enregistrements retourné.</span><span class="sxs-lookup"><span data-stu-id="31d04-155">Columns not specified in the column list will be set to their .NET default values in the returned record set.</span></span> <span data-ttu-id="31d04-156">Pour les colonnes « nillable », cette valeur est **null**.</span><span class="sxs-lookup"><span data-stu-id="31d04-156">For nillable columns, this value is **null**.</span></span>|<span data-ttu-id="31d04-157">Le contenu d’une clause SQL WHERE qui spécifie les lignes de la cible de la requête. par exemple, « désignation = 'Manager' ».</span><span class="sxs-lookup"><span data-stu-id="31d04-157">The contents of a SQL WHERE clause that specifies the target rows of the query; for example, "Designation = 'Manager'".</span></span> <span data-ttu-id="31d04-158">Vous pouvez définir ce paramètre **null** renvoie toutes les lignes de la cible.</span><span class="sxs-lookup"><span data-stu-id="31d04-158">You can set this parameter to **null** to return all rows of the target.</span></span>|  
  
 <span data-ttu-id="31d04-159">La valeur de retour de l’opération de sélection est un jeu de résultats de fortement typé qui contient les colonnes spécifiées et les lignes à partir de la table ou vue cible.</span><span class="sxs-lookup"><span data-stu-id="31d04-159">The return value of the Select operation is a strongly-typed result set that contains the specified columns and rows from the target table or view.</span></span>  
  
 <span data-ttu-id="31d04-160">**Opération de mise à jour**</span><span class="sxs-lookup"><span data-stu-id="31d04-160">**Update Operation**</span></span>  
  
|<span data-ttu-id="31d04-161">Première ligne de la paire</span><span class="sxs-lookup"><span data-stu-id="31d04-161">First row of the pair</span></span>|<span data-ttu-id="31d04-162">Deuxième ligne de la paire</span><span class="sxs-lookup"><span data-stu-id="31d04-162">Second row of the pair</span></span>|  
|---------------------------|----------------------------|  
|<span data-ttu-id="31d04-163">Le premier enregistrement de l’enregistrement de paire correspond aux nouvelles valeurs qui doivent être mis à jour, autrement dit, il correspond à la clause SET de l’instruction de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="31d04-163">The first record of the record pair corresponds to new values that need to be updated, that is, it corresponds to the SET clause of the UPDATE statement.</span></span> <span data-ttu-id="31d04-164">Cela peut être définie à l’aide de `RowPair.After`.</span><span class="sxs-lookup"><span data-stu-id="31d04-164">This can be set using `RowPair.After`.</span></span>|<span data-ttu-id="31d04-165">Le deuxième enregistrement de la paire d’enregistrement correspond aux anciennes valeurs des lignes, autrement dit, il correspond à la clause WHERE de l’instruction de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="31d04-165">The second record of the record pair corresponds to the old values of the rows, that is, it corresponds to the WHERE clause of the UPDATE statement.</span></span> <span data-ttu-id="31d04-166">Cela peut être définie à l’aide de `RowPair.Before`.</span><span class="sxs-lookup"><span data-stu-id="31d04-166">This can be set using `RowPair.Before`.</span></span>|  
  
 <span data-ttu-id="31d04-167">La valeur de retour de l’opération de mise à jour est de type de données Int32 et indique le nombre de lignes mises à jour.</span><span class="sxs-lookup"><span data-stu-id="31d04-167">The return value of the Update operation is of Int32 data type, and denotes the number of rows updated.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31d04-168">Lors de la spécification de l’enregistrement qui doit être mis à jour, vous devez fournir des valeurs pour toutes les colonnes, même si toutes les valeurs ne sont pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="31d04-168">While specifying the record that has to be updated, you must provide values for all the columns, even if all values are not being updated.</span></span> <span data-ttu-id="31d04-169">Par exemple, si une ligne possède cinq colonnes et seules 2 colonnes, des mises à jour de l’opération de mise à jour dans le cadre de RowPair.Before, vous devez passer toutes les valeurs de 5 colonne.</span><span class="sxs-lookup"><span data-stu-id="31d04-169">For example, if a row has five columns and the Update operation updates only 2 columns, as part of RowPair.Before, you must pass all the 5 column values.</span></span> <span data-ttu-id="31d04-170">Toutefois, pour RowPair.After, vous pouvez spécifier uniquement les colonnes qui seront mises à jour.</span><span class="sxs-lookup"><span data-stu-id="31d04-170">However, for RowPair.After, you can specify only the columns that will be updated.</span></span>  
  
 <span data-ttu-id="31d04-171">**L’opération de suppression**</span><span class="sxs-lookup"><span data-stu-id="31d04-171">**Delete Operation**</span></span>  
  
 <span data-ttu-id="31d04-172">L’opération de suppression accepte en tant que tableau d’entrée fortement typé d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="31d04-172">The Delete operation takes as input a strongly-typed array of records.</span></span> <span data-ttu-id="31d04-173">La valeur de retour de l’opération de suppression est de type de données Int32 et indique le nombre de lignes supprimées.</span><span class="sxs-lookup"><span data-stu-id="31d04-173">The return value of the Delete operation is of Int32 data type, and denotes the number of rows deleted.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-tables-and-views"></a><span data-ttu-id="31d04-174">Création d’un Client WCF pour appeler des opérations sur les Tables et vues</span><span class="sxs-lookup"><span data-stu-id="31d04-174">Creating a WCF Client to Invoke Operations on Tables and Views</span></span>  
 <span data-ttu-id="31d04-175">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="31d04-175">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="31d04-176">Cette section décrit comment créer un client WCF pour appeler base Insert, Select, Update, les opérations de suppression sur une table.</span><span class="sxs-lookup"><span data-stu-id="31d04-176">This section describes how to create a WCF client to invoke basic Insert, Select, Update, Delete operations on a table.</span></span>  
  
#### <a name="to-create-a-wcf-client-to-perform-operations-on-tables"></a><span data-ttu-id="31d04-177">Pour créer un client WCF pour effectuer des opérations sur les tables</span><span class="sxs-lookup"><span data-stu-id="31d04-177">To create a WCF client to perform operations on tables</span></span>  
  
1.  <span data-ttu-id="31d04-178">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="31d04-178">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="31d04-179">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="31d04-179">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="31d04-180">Générer la classe de client WCF pour l’insertion, de sélectionner, de mise à jour et suppression sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-180">Generate the WCF client class for the Insert, Select, Update, and Delete operation on the Employee table.</span></span> <span data-ttu-id="31d04-181">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="31d04-181">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="31d04-182">Avant de générer la classe de client WCF, veillez à définir le **EnableBizTalkCompatibilityMode** liaison de propriété à false.</span><span class="sxs-lookup"><span data-stu-id="31d04-182">Before generating the WCF client class, make sure you set the **EnableBizTalkCompatibilityMode** binding property to false.</span></span>  
  
3.  <span data-ttu-id="31d04-183">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql` et `Microsoft.ServiceModel.Channels`.</span><span class="sxs-lookup"><span data-stu-id="31d04-183">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql` and `Microsoft.ServiceModel.Channels`.</span></span>  
  
4.  <span data-ttu-id="31d04-184">Ouvrez le fichier Program.cs et créer un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="31d04-184">Open the Program.cs file and create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient("SqlAdapterBinding_TableOp_dbo_Employee");  
    client.ClientCredentials.UserName.UserName = "<Enter user name here>";  
    client.ClientCredentials.UserName.Password = "<Enter password here>";  
    ```  
  
     <span data-ttu-id="31d04-185">Dans cet extrait de code, `TableOp_dbo_EmployeeClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="31d04-185">In this snippet, `TableOp_dbo_EmployeeClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="31d04-186">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31d04-186">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="31d04-187">`SqlAdapterBinding_TableOp_dbo_Employee`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="31d04-187">`SqlAdapterBinding_TableOp_dbo_Employee` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31d04-188">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="31d04-188">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="31d04-189">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="31d04-189">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="31d04-190">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="31d04-190">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
5.  <span data-ttu-id="31d04-191">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="31d04-191">Open the client as described in the snippet below:</span></span>  
  
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
  
6.  <span data-ttu-id="31d04-192">Appeler l’opération Insert sur la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-192">Invoke the Insert operation on the Employee table.</span></span>  
  
    ```  
    long[] recordsInserted;  
  
    schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] insertRecord =  
    new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
    insertRecord[0] = new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
    insertRecord[0].Name = "John Smith";  
    insertRecord[0].Designation = "Manager";  
    insertRecord[0].Salary = 500000;  
  
    try  
    {  
       Console.WriteLine("Inserting new table entry...");  
       recordsInserted = client.Insert(insertRecord);  
    }  
    catch (Exception ex)  
    {  
       Console.WriteLine("Exception: " + ex.Message);  
       throw;  
    }  
  
    Console.WriteLine("Record inserted");  
    Console.WriteLine("Press any key to continue ...");  
    Console.ReadLine();  
    ```  
  
     <span data-ttu-id="31d04-193">Vous pouvez remplacer l’extrait de code précédent pour exécuter Select, Update ou Delete ainsi les opérations.</span><span class="sxs-lookup"><span data-stu-id="31d04-193">You can replace the preceding code snippet to perform Select, Update, or Delete operations as well.</span></span> <span data-ttu-id="31d04-194">Vous pouvez également ajouter des extraits de code pour effectuer toutes les opérations dans une application unique.</span><span class="sxs-lookup"><span data-stu-id="31d04-194">You can also append the code snippets to perform all operation in a single application.</span></span> <span data-ttu-id="31d04-195">Extraits de code sur la façon d’effectuer ces opérations.</span><span class="sxs-lookup"><span data-stu-id="31d04-195">For code snippets on how to perform these operations.</span></span>  
  
7.  <span data-ttu-id="31d04-196">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="31d04-196">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
8.  <span data-ttu-id="31d04-197">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="31d04-197">Build the project and then run it.</span></span> <span data-ttu-id="31d04-198">L’application insère un enregistrement dans la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-198">The application inserts a record in the Employee table.</span></span>  
  
###   <a name="select-operation"></a><span data-ttu-id="31d04-199">Sélectionnez l’opération</span><span class="sxs-lookup"><span data-stu-id="31d04-199">Select Operation</span></span>  
 <span data-ttu-id="31d04-200">Le code suivant illustre une opération de sélection qui cible la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-200">The following code shows a Select operation that targets the Employee table.</span></span> <span data-ttu-id="31d04-201">L’opération Select sélectionne le dernier enregistrement inséré dans la table.</span><span class="sxs-lookup"><span data-stu-id="31d04-201">The Select operation selects the last record inserted into the table.</span></span> <span data-ttu-id="31d04-202">Les enregistrements retournés sont écrites dans la console.</span><span class="sxs-lookup"><span data-stu-id="31d04-202">The returned records are written to the console.</span></span>  
  
```  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] selectRecords;  
  
try  
{  
   Console.WriteLine("Selecting Row...");  
   selectRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("The details of the newly added employee are:");  
Console.WriteLine("********************************************");  
for (int i = 0; i < selectRecords.Length; i++)  
{  
   Console.WriteLine("Employee ID        : " + selectRecords[i].Employee_ID);  
   Console.WriteLine("Employee Name      : " + selectRecords[i].Name);  
   Console.WriteLine("Employee Desigation: " + selectRecords[i].Designation);  
   Console.WriteLine();  
}  
Console.WriteLine("********************************************");  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="update-operation"></a><span data-ttu-id="31d04-203">Opération de mise à jour</span><span class="sxs-lookup"><span data-stu-id="31d04-203">Update Operation</span></span>  
 <span data-ttu-id="31d04-204">Le code suivant montre une opération de mise à jour qui cible la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-204">The following code shows an Update operation that targets the Employee table.</span></span>  
  
```  
int result;  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair updateRecordPair =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair();  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee updateRecord =   
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee();  
  
schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[] updateArray =  
   new schemas.microsoft.com.Sql._2008._05.TableOp.dbo.Employee.RowPair[1];  
  
updateRecord = insertRecord[0];  
updateRecord.Name = "Jeff Smith";  
  
updateRecordPair.After = updateRecord;  
updateRecordPair.Before = selectRecords[0];  
  
updateArray[0] = updateRecordPair;  
  
try  
{  
   Console.WriteLine("Updating the database...");  
   result = client.Update(updateArray);  
}  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
  
Console.WriteLine("Updated Record for {0}", updateRecordPair.Before.Name);  
Console.WriteLine("The new name for the employee is {0}", updateRecordPair.After.Name);  
Console.WriteLine("Press any key to continue ...");  
Console.ReadLine();  
```  
  
###   <a name="delete-operation"></a><span data-ttu-id="31d04-205">Opération de suppression</span><span class="sxs-lookup"><span data-stu-id="31d04-205">Delete Operation</span></span>  
 <span data-ttu-id="31d04-206">Le code suivant montre une opération de suppression qui cible la table Employee.</span><span class="sxs-lookup"><span data-stu-id="31d04-206">The following code shows a Delete operation that targets the Employee table.</span></span>  
  
```  
int deleteSuccess;  
  
schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[] deleteRecords =  
   new schemas.microsoft.com.Sql._2008._05.Types.Tables.dbo.Employee[1];  
  
deleteRecords = client.Select("*", "where [Employee_ID] = (select IDENT_CURRENT('Employee'))");  
  
Console.WriteLine("Following employees will be deleted from the database:");  
for (int i = 0; i < deleteRecords.Length; i++)  
{  
   Console.WriteLine("Name: {0}", deleteRecords[i].Name);  
}  
Console.WriteLine("Press any key to begin deletion...");  
Console.ReadLine();  
  
try  
{  
   Console.WriteLine("Deleting employee record...");  
   deleteSuccess = client.Delete(deleteRecords);  
}  
  
catch (Exception ex)  
{  
   Console.WriteLine("Exception: " + ex.Message);  
   throw;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="31d04-207">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31d04-207">See Also</span></span>  
[<span data-ttu-id="31d04-208">Développer des applications à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="31d04-208">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)