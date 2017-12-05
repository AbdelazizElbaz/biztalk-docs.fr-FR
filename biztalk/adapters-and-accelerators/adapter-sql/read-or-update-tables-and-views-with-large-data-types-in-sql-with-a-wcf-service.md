---
title: "Exécuter des opérations sur les Tables et vues avec des Types de données volumineux dans SQL à l’aide du modèle de Service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d33e17c-e09e-4a57-9acc-43095e67ed8c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1da0def828c1dbfa8511dc61b529fa02cb53ca5a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-operations-on-tables-and-views-with-large-data-types-in-sql-using-the-wcf-service-model"></a><span data-ttu-id="2f32e-102">Exécuter des opérations sur les Tables et vues avec des Types de données volumineux dans SQL à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="2f32e-102">Run Operations on Tables and Views with Large Data Types in SQL using the WCF Service Model</span></span>
<span data-ttu-id="2f32e-103">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet à des clients de l’adaptateur pour lire et mettre à jour des données dans des colonnes de types de données volumineuses, autrement dit, varchar (max), nvarchar (max) ou varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="2f32e-103">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables adapter clients to read and update data in columns of large data types, that is, varchar(max), nvarchar(max), or varbinary(max).</span></span> <span data-ttu-id="2f32e-104">Pour lire des données à partir de ces colonnes, les clients de la carte peuvent utiliser l’opération de sélection.</span><span class="sxs-lookup"><span data-stu-id="2f32e-104">To read data from such columns, adapter clients can use the Select operation.</span></span> <span data-ttu-id="2f32e-105">Pour insérer ou mettre à jour des données dans ces colonnes, l’adaptateur expose un ensemble\<*column_name* \> opération, où \< *column_name* \> est le nom de la colonne de type varchar (max), nvarchar (max) ou varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="2f32e-105">To insert or update data into such columns, the adapter exposes a Set\<*column_name*\> operation, where \<*column_name*\> is the name of the column of type varchar(max), nvarchar(max), or varbinary(max).</span></span>  
  
 <span data-ttu-id="2f32e-106">En outre, dans SQL Server, vous pouvez avoir la colonne varbinay(max) stocker des données non structurées, telles que des documents de texte et des images.</span><span class="sxs-lookup"><span data-stu-id="2f32e-106">Additionally, in SQL Server, you can have the varbinay(max) column store unstructured data such as text documents and images.</span></span> <span data-ttu-id="2f32e-107">Ces données non structurées sont appelées données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-107">Such unstructured data is called FILESTREAM data.</span></span> <span data-ttu-id="2f32e-108">Les données FILESTREAM peuvent être stockées en tant que fichiers sur le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="2f32e-108">FILESTREAM data can be stored as files on the file system.</span></span> <span data-ttu-id="2f32e-109">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet au client d’entrer des données FILESTREAM dans des colonnes de type varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="2f32e-109">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] enables the client to enter FILESTREAM data into columns of type varbinary(max).</span></span> <span data-ttu-id="2f32e-110">[Stockage FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server) contient des informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="2f32e-110">[FILESTREAM storage](https://docs.microsoft.com/sql/relational-databases/blob/filestream-sql-server) has more information.</span></span> 
  
 <span data-ttu-id="2f32e-111">Cette rubrique fournit des informations sur certaines tâches, vous devez effectuer sur l’ordinateur exécutant SQL Server et l’ordinateur exécutant le client de l’adaptateur pour être en mesure d’insérer ou de mettre à jour les données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-111">This topic provides information about certain tasks you must perform on the computer running SQL Server and the computer running the adapter client to be able to insert or update FILESTREAM data.</span></span> <span data-ttu-id="2f32e-112">Cette rubrique fournit également des instructions sur l’exécution de jeu\<*column_name* \> operations pour insérer des données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-112">This topic also provides instructions on performing Set\<*column_name*\> operations to insert FILESTREAM data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f32e-113">Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-113">If you are performing operation on tables that have columns of user-defined types, make sure you refer to [Operations on Tables and Views with User-Defined Types using the SQL adapter](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2f32e-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2f32e-114">Prerequisites</span></span>  
 <span data-ttu-id="2f32e-115">Vous devez effectuer les tâches suivantes sur l’ordinateur exécutant SQL Server et de l’ordinateur exécutant le client de la carte.</span><span class="sxs-lookup"><span data-stu-id="2f32e-115">You must perform the following tasks on the computer running SQL Server and the computer running the adapter client.</span></span>  
  
-   <span data-ttu-id="2f32e-116">**Sur l’ordinateur exécutant SQL Server**</span><span class="sxs-lookup"><span data-stu-id="2f32e-116">**On the computer running SQL Server**</span></span>  
  
    -   <span data-ttu-id="2f32e-117">Vous devez l’activer sur l’instance de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2f32e-117">You must enable FILESTREAM on the SQL Server instance.</span></span> <span data-ttu-id="2f32e-118">Consultez [activer et configurer FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream).</span><span class="sxs-lookup"><span data-stu-id="2f32e-118">See [Enable and Configure FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/enable-and-configure-filestream).</span></span>
  
    -   <span data-ttu-id="2f32e-119">Vous devez créer une base de données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-119">You must create a FILESTREAM-enabled database.</span></span> <span data-ttu-id="2f32e-120">Consultez [créer une base de données compatible FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database).</span><span class="sxs-lookup"><span data-stu-id="2f32e-120">See [Create a FILESTREAM-Enabled Database](https://docs.microsoft.com/sql/relational-databases/blob/create-a-filestream-enabled-database).</span></span>
  
    -   <span data-ttu-id="2f32e-121">Vous devez disposer d’une table pour stocker les données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-121">You must have a table for storing FILESTREAM data.</span></span> <span data-ttu-id="2f32e-122">Consultez [créer une Table pour stocker des données FILESTREAM](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data),</span><span class="sxs-lookup"><span data-stu-id="2f32e-122">See [Create a Table for Storing FILESTREAM Data](https://docs.microsoft.com/sql/relational-databases/blob/create-a-table-for-storing-filestream-data),</span></span>
  
-   <span data-ttu-id="2f32e-123">**Sur l’ordinateur exécutant le client de carte**</span><span class="sxs-lookup"><span data-stu-id="2f32e-123">**On the computer running the adapter client**</span></span>  
  
    -   <span data-ttu-id="2f32e-124">Vous devez disposer de la connectivité du Client SQL SDK installé.</span><span class="sxs-lookup"><span data-stu-id="2f32e-124">You must have the SQL Client Connectivity SDK installed.</span></span> <span data-ttu-id="2f32e-125">Vous pouvez installer le SDK de connectivité Client SQL, exécutez le programme d’installation de SQL Server et sélectionnez **SQL Client Connectivity SDK** dans les **sélection des fonctionnalités** page de l’Assistant.</span><span class="sxs-lookup"><span data-stu-id="2f32e-125">You can install the SQL Client Connectivity SDK by running the SQL Server setup and selecting **SQL Client Connectivity SDK** in the **Feature Selection** page of the wizard.</span></span> <span data-ttu-id="2f32e-126">L’adaptateur utilise le sqlncli10.dll, installé avec le SDK de connectivité Client SQL, pour effectuer des opérations FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-126">The adapter uses the sqlncli10.dll, installed with the SQL Client Connectivity SDK, to perform FILESTREAM operations.</span></span>  
  
 <span data-ttu-id="2f32e-127">Une fois ces tâches terminées, vous sont tous définis pour insérer ou mettre à jour les données FILESTREAM dans les tables de base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="2f32e-127">After you have completed these tasks, you are all set to insert or update FILESTREAM data in SQL Server database tables.</span></span>  
  
## <a name="how-this-topic-demonstrates-operations-on-large-data-types"></a><span data-ttu-id="2f32e-128">Comment cette rubrique illustre les opérations sur les Types de données de grande taille</span><span class="sxs-lookup"><span data-stu-id="2f32e-128">How This Topic Demonstrates Operations on Large Data Types</span></span>  
 <span data-ttu-id="2f32e-129">Pour illustrer comment exécuter ensemble\<*column_name* \> opérations sur les tables avec les types de données de grande taille, prenez une table, **enregistrements**, qui a des colonnes **Id** et **Document**:</span><span class="sxs-lookup"><span data-stu-id="2f32e-129">To demonstrate how to perform Set\<*column_name*\> operations on tables with large data types, take a table, **Records**, that has columns **Id** and **Document**:</span></span>  
  
-   <span data-ttu-id="2f32e-130">Le **enregistrements** table, toutes les données, est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="2f32e-130">The **Records** table, with all the data, is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="2f32e-131">Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-131">For more information, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
-   <span data-ttu-id="2f32e-132">Le **Id** la colonne est de type uniqueidentifier et accepte un GUID.</span><span class="sxs-lookup"><span data-stu-id="2f32e-132">The **Id** column is of type uniqueidentifier and takes a GUID.</span></span> <span data-ttu-id="2f32e-133">Supposons que la **Id** colonne a déjà un GUID '`438B7B4C-5491-409F-BCC1-78817C399EC3`'.</span><span class="sxs-lookup"><span data-stu-id="2f32e-133">Assume that the **Id** column already has a GUID ‘`438B7B4C-5491-409F-BCC1-78817C399EC3`’.</span></span>  
  
-   <span data-ttu-id="2f32e-134">Le **Document** colonne est de type varbinary (max).</span><span class="sxs-lookup"><span data-stu-id="2f32e-134">The **Document** column is of type VARBINARY(MAX).</span></span> <span data-ttu-id="2f32e-135">Pour mettre à jour le **Document** expose de colonne, l’adaptateur le **SetDocument** opération.</span><span class="sxs-lookup"><span data-stu-id="2f32e-135">To update the **Document** column, the adapter exposes the **SetDocument** operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f32e-136">Pour SQL Server, pour illustrer les opérations FILESTREAM, supposons que qui le **Document** colonne peut stocker les données FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2f32e-136">For SQL Server, to demonstrate FILESTREAM operations, assume that the **Document** column can store FILESTREAM data.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="2f32e-137">À propos des exemples présentés dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="2f32e-137">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="2f32e-138">L’exemple de cette rubrique effectue des opérations sur le **enregistrements** table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-138">The example in this topic performs operations on the **Records** table.</span></span> <span data-ttu-id="2f32e-139">Le **enregistrements** table est créée en exécutant le script SQL fourni avec les exemples.</span><span class="sxs-lookup"><span data-stu-id="2f32e-139">The **Records** table is created by running the SQL script provided with the samples.</span></span> <span data-ttu-id="2f32e-140">Pour plus d’informations sur les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-140">For more information about samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span> <span data-ttu-id="2f32e-141">Un exemple, **Records_FILESTREAM_Op**, qui est basé sur cette rubrique, est également fourni avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="2f32e-141">A sample, **Records_FILESTREAM_Op**, which is based on this topic, is also provided with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] samples.</span></span>  
  
## <a name="the-wcf-client-class"></a><span data-ttu-id="2f32e-142">La classe de Client WCF</span><span class="sxs-lookup"><span data-stu-id="2f32e-142">The WCF Client Class</span></span>  
 <span data-ttu-id="2f32e-143">Le nom du client WCF généré pour les opérations sur les données de grande taille en types qui le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] détecte, est basé sur le nom de la table ou vue, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="2f32e-143">The name of the WCF client generated for the operations on large data types that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] discovers, is based on the name of the table or view, as listed in the following table.</span></span>  
  
|<span data-ttu-id="2f32e-144">Objet de base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f32e-144">SQL Server Database Artifact</span></span>|<span data-ttu-id="2f32e-145">Nom de Client WCF</span><span class="sxs-lookup"><span data-stu-id="2f32e-145">WCF Client Name</span></span>|  
|----------------------------------|---------------------|  
|<span data-ttu-id="2f32e-146">Table</span><span class="sxs-lookup"><span data-stu-id="2f32e-146">Table</span></span>|<span data-ttu-id="2f32e-147">TableOp_ [schéma] _ [nom_table] Client</span><span class="sxs-lookup"><span data-stu-id="2f32e-147">TableOp_[Schema]_[TABLE_NAME]Client</span></span>|  
|<span data-ttu-id="2f32e-148">Affichage</span><span class="sxs-lookup"><span data-stu-id="2f32e-148">View</span></span>|<span data-ttu-id="2f32e-149">ViewOp_ [schéma] _ [VIEW_NAME] Client</span><span class="sxs-lookup"><span data-stu-id="2f32e-149">ViewOp_[Schema]_[VIEW_NAME]Client</span></span>|  
  
 <span data-ttu-id="2f32e-150">[Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.</span><span class="sxs-lookup"><span data-stu-id="2f32e-150">[SCHEMA] = Collection of SQL Server artifacts; for example, dbo.</span></span>  
  
### <a name="method-signature-for-invoking-operations-on-columns-of-large-data-types"></a><span data-ttu-id="2f32e-151">Signature de méthode pour appeler des opérations sur les colonnes de Types de données volumineuses</span><span class="sxs-lookup"><span data-stu-id="2f32e-151">Method Signature for Invoking Operations on Columns of Large Data Types</span></span>  
 <span data-ttu-id="2f32e-152">Le tableau suivant montre les signatures de méthode pour les opérations de base sur une table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-152">The following table shows the method signatures for the basic operations on a table.</span></span> <span data-ttu-id="2f32e-153">Les signatures sont identiques pour une vue, à ceci près que le nom et l’espace de noms de vue remplacent ceux de la table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-153">The signatures are the same for a view, except that the view namespace and name replace those of the table.</span></span>  
  
|<span data-ttu-id="2f32e-154">Opération</span><span class="sxs-lookup"><span data-stu-id="2f32e-154">Operation</span></span>|<span data-ttu-id="2f32e-155">Signature de méthode</span><span class="sxs-lookup"><span data-stu-id="2f32e-155">Method Signature</span></span>|  
|---------------|----------------------|  
|<span data-ttu-id="2f32e-156">Définissez\<*nom_colonne*\></span><span class="sxs-lookup"><span data-stu-id="2f32e-156">Set\<*column_name*\></span></span>|<span data-ttu-id="2f32e-157">public Set void\<*column_name*\>(filtre, byte [] données de chaîne) ;</span><span class="sxs-lookup"><span data-stu-id="2f32e-157">public void Set\<*column_name*\>(string Filter, byte[] Data);</span></span>|  
  
 <span data-ttu-id="2f32e-158">\<*column_name* \> = nom de la colonne de type de données de grande taille.</span><span class="sxs-lookup"><span data-stu-id="2f32e-158">\<*column_name*\> = Name of the column of large data type.</span></span>  
  
 <span data-ttu-id="2f32e-159">Par exemple, le code suivant illustre les signatures de méthode pour une classe de client WCF généré pour le **SetDocument** opération sur le **enregistrements** table sous le schéma de « dbo » par défaut.</span><span class="sxs-lookup"><span data-stu-id="2f32e-159">As an example, the following code shows the method signatures for a WCF client class generated for the **SetDocument** operation on the **Records** table under the default “dbo” schema.</span></span>  
  
```  
public partial class TableOp_dbo_RecordsClient : System.ServiceModel.ClientBase<TableOp_dbo_Records>, TableOp_dbo_Records {      
    public void SetDocument (string Filter, byte[] Data);  
}  
```  
  
 <span data-ttu-id="2f32e-160">Dans cet extrait de code, **TableOp_dbo_RecordsClient** est le nom de la classe WCF dans le SqlAdapterBindingClient.cs généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f32e-160">In this snippet, **TableOp_dbo_RecordsClient** is the name of the WCF class in the SqlAdapterBindingClient.cs generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span>  
  
### <a name="parameters-for-operations-on-columns-of-large-data-types"></a><span data-ttu-id="2f32e-161">Paramètres pour les opérations sur des colonnes de Types de données volumineuses</span><span class="sxs-lookup"><span data-stu-id="2f32e-161">Parameters for Operations on Columns of Large Data Types</span></span>  
 <span data-ttu-id="2f32e-162">Cette section fournit les paramètres requis par le jeu de\<*column_name* \> opération.</span><span class="sxs-lookup"><span data-stu-id="2f32e-162">This section provides the parameters required by the Set\<*column_name*\> operation.</span></span>  
  
|<span data-ttu-id="2f32e-163">Nom du paramètre</span><span class="sxs-lookup"><span data-stu-id="2f32e-163">Parameter name</span></span>|<span data-ttu-id="2f32e-164"> Description</span><span class="sxs-lookup"><span data-stu-id="2f32e-164">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2f32e-165">chaîne de filtre</span><span class="sxs-lookup"><span data-stu-id="2f32e-165">string Filter</span></span>|<span data-ttu-id="2f32e-166">Spécifie la clause WHERE en fonction sur laquelle l’adaptateur met à jour l’enregistrement de la colonne de type de données de grande taille.</span><span class="sxs-lookup"><span data-stu-id="2f32e-166">Specifies the WHERE clause based on which the adapter updates the record for the column of large data type.</span></span>|  
|<span data-ttu-id="2f32e-167">Byte [] données</span><span class="sxs-lookup"><span data-stu-id="2f32e-167">byte[] Data</span></span>|<span data-ttu-id="2f32e-168">Spécifie la valeur qui doit être mis à jour pour la colonne de type de données de grande taille.</span><span class="sxs-lookup"><span data-stu-id="2f32e-168">Specifies the value that must be updated for the column of large data type.</span></span>|  
  
 <span data-ttu-id="2f32e-169">Le jeu de\<*column_name* \> opération ne renvoie aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="2f32e-169">The Set\<*column_name*\> operation does not return any values.</span></span>  
  
## <a name="creating-a-wcf-client-to-invoke-operations-on-columns-of-large-data-types"></a><span data-ttu-id="2f32e-170">Création d’un Client WCF pour appeler des opérations sur des colonnes de Types de données volumineuses</span><span class="sxs-lookup"><span data-stu-id="2f32e-170">Creating a WCF Client to Invoke Operations on Columns of Large Data Types</span></span>  
 <span data-ttu-id="2f32e-171">L’ensemble générique des actions requises pour effectuer une opération sur SQL Server à l’aide d’un client WCF implique un ensemble de tâches décrites dans [vue d’ensemble du modèle de Service WCF avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-171">The generic set of actions required to perform an operation on SQL Server using a WCF client involves a set of tasks described in [Overview of the WCF Service Model with the SQL Adapter](../../adapters-and-accelerators/adapter-sql/overview-of-the-wcf-service-model-with-the-sql-adapter.md).</span></span> <span data-ttu-id="2f32e-172">Cette section décrit comment créer un client WCF pour appeler le **SetDocument** opération sur le **enregistrements** table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-172">This section describes how to create a WCF client to invoke the **SetDocument** operation on the **Records** table.</span></span> <span data-ttu-id="2f32e-173">L’adaptateur expose le **SetDocument** opération pour mettre à jour des données dans des colonnes de types de données volumineuses.</span><span class="sxs-lookup"><span data-stu-id="2f32e-173">The adapter exposes the **SetDocument** operation to update data in columns of large data types.</span></span>  
  
#### <a name="to-create-a-wcf-client"></a><span data-ttu-id="2f32e-174">Pour créer un client WCF</span><span class="sxs-lookup"><span data-stu-id="2f32e-174">To create a WCF client</span></span>  
  
1.  <span data-ttu-id="2f32e-175">Créez un projet Visual c# dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2f32e-175">Create a Visual C# project in Visual Studio.</span></span> <span data-ttu-id="2f32e-176">Pour cette rubrique, créez une application console.</span><span class="sxs-lookup"><span data-stu-id="2f32e-176">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="2f32e-177">Générer la classe de client WCF pour le **SetDocument** opération sur le **enregistrements** table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-177">Generate the WCF client class for the **SetDocument** operation on the **Records** table.</span></span> <span data-ttu-id="2f32e-178">Pour plus d’informations sur la génération d’une classe de client WCF, consultez [générer un Client WCF ou le contrat de Service WCF pour les artefacts de SQL Server](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-178">For more information about generating a WCF client class, see [Generate a WCF Client or WCF Service Contract for SQL Server Artifacts](../../adapters-and-accelerators/adapter-sql/generate-a-wcf-client-or-wcf-service-contract-for-sql-server-artifacts.md).</span></span>  
  
3.  <span data-ttu-id="2f32e-179">Dans l’Explorateur de solutions, ajoutez la référence à `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, et `System.Transactions`.</span><span class="sxs-lookup"><span data-stu-id="2f32e-179">In the Solution Explorer, add reference to `Microsoft.Adapters.Sql`, `Microsoft.ServiceModel.Channels`, and `System.Transactions`.</span></span>  
  
4.  <span data-ttu-id="2f32e-180">Ouvrez le fichier Program.cs et ajoutez le `System.Transactions` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="2f32e-180">Open the Program.cs file and add the `System.Transactions` namespace.</span></span>  
  
5.  <span data-ttu-id="2f32e-181">Dans le fichier Program.cs, créez un client, comme décrit dans l’extrait de code ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="2f32e-181">In the Program.cs, create a client as described in the snippet below.</span></span>  
  
    ```  
  
              TableOp_dbo_RecordsClient client = new TableOp_dbo_RecordsClient("SqlAdapterBinding_TableOp_dbo_Records");  
    client.ClientCredentials.UserName.UserName = "";  
    client.ClientCredentials.UserName.Password = "";  
  
    ```  
  
     <span data-ttu-id="2f32e-182">Dans cet extrait de code, `TableOp_dbo_RecordsClient` est le client WCF défini dans SqlAdapterBindingClient.cs.</span><span class="sxs-lookup"><span data-stu-id="2f32e-182">In this snippet, `TableOp_dbo_RecordsClient` is the WCF client defined in SqlAdapterBindingClient.cs.</span></span> <span data-ttu-id="2f32e-183">Ce fichier est généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f32e-183">This file is generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].</span></span> <span data-ttu-id="2f32e-184">`SqlAdapterBinding_TableOp_dbo_Records`est le nom de la configuration de point de terminaison de client et est défini dans le fichier app.config. Ce fichier est également généré par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et contient les propriétés de liaison et d’autres paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="2f32e-184">`SqlAdapterBinding_TableOp_dbo_Records` is the name of the client endpoint configuration and is defined in the app.config. This file is also generated by the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] and contains the binding properties and other configuration settings.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="2f32e-185">Pour effectuer des opérations sur les données FILESTREAM, vous devez toujours vous connecter à SQL Server à l’aide de l’authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="2f32e-185">To perform operations on FILESTREAM data, you must always connect to SQL Server using Windows authentication.</span></span> <span data-ttu-id="2f32e-186">Pour vous connecter à l’aide de l’authentification Windows, vous devez fournir des nom d’utilisateur vide et le mot de passe, comme indiqué dans l’extrait de code précédent.</span><span class="sxs-lookup"><span data-stu-id="2f32e-186">To connect using Windows authentication, you must provide empty username and password, as shown in the preceding snippet.</span></span> <span data-ttu-id="2f32e-187">En outre, avant d’utiliser l’authentification Windows pour se connecter à SQL Server, vous devez avoir exécuté les étapes indiquées dans [se connecter à SQL Server à l’aide de l’authentification Windows avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-187">Also, before using Windows authentication to connect to SQL Server, you must have performed the steps mentioned in [Connect to SQL Server Using Windows Authentication with the SQL adapter](../../adapters-and-accelerators/adapter-sql/connect-to-sql-server-using-windows-authentication-with-the-sql-adapter.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2f32e-188">Dans cet extrait de code, vous utilisez la liaison et l’adresse de point de terminaison à partir du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="2f32e-188">In this snippet, you use the binding and endpoint address from the configuration file.</span></span> <span data-ttu-id="2f32e-189">Vous pouvez également spécifier explicitement ces valeurs dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2f32e-189">You can also explicitly specify these values in your code.</span></span> <span data-ttu-id="2f32e-190">Pour plus d’informations sur les différentes façons de spécifier la liaison du client, consultez [configurer une liaison de Client de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="2f32e-190">For more information on the different ways of specifying client binding, see [Configure a Client Binding for the SQL Adapter](../../adapters-and-accelerators/adapter-sql/configure-a-client-binding-for-the-sql-adapter.md).</span></span>  
  
6.  <span data-ttu-id="2f32e-191">Ouvrez le client comme indiqué dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2f32e-191">Open the client as described in the snippet below:</span></span>  
  
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
  
7.  <span data-ttu-id="2f32e-192">Appeler le **SetDocument** opération sur le **enregistrements** table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-192">Invoke the **SetDocument** operation on the **Records** table.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="2f32e-193">Le jeu de*< nom_colonne >* opérations doivent toujours être exécutées dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="2f32e-193">The Set*<column_name>* operations must always be performed in a transaction.</span></span> <span data-ttu-id="2f32e-194">Pour garantir cela, le jeu de*< nom_colonne >* opération doit être appelée au sein d’une étendue de transaction et la **UseAmbientTransaction** liaison de la propriété doit être définie sur **true**dans le fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="2f32e-194">To ensure this, the Set*<column_name>* operation must be invoked within a transaction scope and the **UseAmbientTransaction** binding property must be set to **true** in the app.config.</span></span>  
  
    ```  
    using (TransactionScope tx = new TransactionScope())  
    {  
        string filter = "WHERE Id='438B7B4C-5491-409F-BCC1-78817C399EC3'";  
        byte[] data = ASCIIEncoding.ASCII.GetBytes("Sample data");  
        client.SetDocument(filter, data);  
        tx.Complete();  
    }  
    ```  
  
     <span data-ttu-id="2f32e-195">Ici, l’application convertit la chaîne « Exemples de données » dans une chaîne codée en base64 et il met à jour dans l’enregistrement qui satisfait aux critères de filtre.</span><span class="sxs-lookup"><span data-stu-id="2f32e-195">Here, the application converts the string “Sample data” into a base64 encoded string, and updates it in the record that satisfies the filter criteria.</span></span>  
  
8.  <span data-ttu-id="2f32e-196">Fermez le client, comme décrit dans l’extrait de code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="2f32e-196">Close the client as described in the snippet below:</span></span>  
  
    ```  
    client.Close();  
    Console.WriteLine("Press any key to exit...");  
    Console.ReadLine();  
    ```  
  
9. <span data-ttu-id="2f32e-197">Générez le projet et exécutez-le.</span><span class="sxs-lookup"><span data-stu-id="2f32e-197">Build the project and then run it.</span></span> <span data-ttu-id="2f32e-198">Les mises à jour de l’application le **Document** colonne dans la **enregistrements** table.</span><span class="sxs-lookup"><span data-stu-id="2f32e-198">The application updates the **Document** column in the **Records** table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f32e-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f32e-199">See Also</span></span>  
[<span data-ttu-id="2f32e-200">Développer des applications en utilisant le modèle de service WCF</span><span class="sxs-lookup"><span data-stu-id="2f32e-200">Develop applications using the WCF Service model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-service-model.md)