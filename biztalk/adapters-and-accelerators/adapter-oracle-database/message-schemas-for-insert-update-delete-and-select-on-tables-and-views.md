---
title: "Schémas de message pour la base Insert, Update, Delete, puis sélectionnez les opérations sur les Tables et vues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations on tables, message actions for
- table operations, message actions for
- table operations, message structure for
- operations on tables, message schemas for
- table operations, message schemas for
- operations on tables, message structure for
ms.assetid: 8228d5e6-14af-49e0-b34b-be03aea59189
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 571a6a192ca85eb0bd3e5abeb8ef8f3715818236
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-basic-insert-update-delete-and-select-operations-on-tables-and-views"></a><span data-ttu-id="e8ec0-102">Schémas de message pour l’insertion de base, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues</span><span class="sxs-lookup"><span data-stu-id="e8ec0-102">Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views</span></span>
<span data-ttu-id="e8ec0-103">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces base Insert, Update, Delete, et les opérations Select pour chaque table et afficher dans la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces basic Insert, Update, Delete, and Select operations for each table and view in the Oracle database.</span></span> <span data-ttu-id="e8ec0-104">Ces opérations exécuter l’instruction SQL appropriée qualifiée par une clause WHERE.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-104">These operations perform the appropriate SQL statement qualified by a WHERE clause.</span></span> <span data-ttu-id="e8ec0-105">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise les enregistrements de fortement typée et des jeux d’enregistrements dans ces opérations.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-105">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses strongly-typed records and record sets in these operations.</span></span>  
  
## <a name="message-structure-for-basic-table-operations"></a><span data-ttu-id="e8ec0-106">Structure du message pour les opérations de Table de base</span><span class="sxs-lookup"><span data-stu-id="e8ec0-106">Message Structure for Basic Table Operations</span></span>  
 <span data-ttu-id="e8ec0-107">Le tableau suivant présente la structure de message XML pour les opérations de table de base exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] sur les tables de base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-107">The following table shows the XML message structure for the basic table operations exposed by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] on Oracle database tables.</span></span> <span data-ttu-id="e8ec0-108">La table cible pour une opération est spécifiée dans l’action du message et s’affiche également dans l’espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-108">The target table for an operation is specified in the message action and also appears in the target namespace.</span></span>  

### <a name="insert"></a><span data-ttu-id="e8ec0-109">Insert</span><span class="sxs-lookup"><span data-stu-id="e8ec0-109">Insert</span></span>  
<span data-ttu-id="e8ec0-110">Il existe les types suivants d’opérations d’insertion.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-110">There are the following types of Insert operations.</span></span> <span data-ttu-id="e8ec0-111">Un message peut contenir qu’un seul type d’opération d’insertion.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-111">A message can contain only one kind of Insert operation.</span></span>

- <span data-ttu-id="e8ec0-112">Insertion de plusieurs enregistrements d’insère le jeu d’enregistrements fourni des données fortement typées dans la table cible.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-112">Multiple Record Insert inserts the supplied record set of strongly-typed data into the target table.</span></span>
- <span data-ttu-id="e8ec0-113">Pour chaque enregistrement d’une insertion de plusieurs enregistrement, vous pouvez spécifier la valeur d’un attribut facultatif appelé **InlineValue**.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-113">For each record in a multiple record insert, you can specify value for an optional attribute called **InlineValue**.</span></span> <span data-ttu-id="e8ec0-114">Si spécifié, il remplace la valeur de l’élément.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-114">If specified, it overrides the value of the element.</span></span>
- <span data-ttu-id="e8ec0-115">Instruction Bulk Insert insère le jeu d’enregistrements retourné par une requête SELECT spécifiée dans l’élément de requête dans la table cible.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-115">Bulk Insert inserts the record set returned by a SELECT query specified in the QUERY element into the target table.</span></span> <span data-ttu-id="e8ec0-116">Cela permet à l’aide de la liste séparée par des virgules des colonnes spécifiées dans l’élément les noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-116">This is done by using the comma-separated list of columns specified in the COLUMN_NAMES element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-117">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-117">XML message</span></span>  

<span data-ttu-id="e8ec0-118">**Insertion d’enregistrement multiples**</span><span class="sxs-lookup"><span data-stu-id="e8ec0-118">**Multiple record insert**</span></span>  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[TABLE_NAME]RECORDINSERT>       
<[FIELD1_NAME InlineValue="value"]>value1</[FIELD1_NAME]>       
<[FIELD2_NAME InlineValue="value"]>value2</[FIELD2_NAME]>       
…     
</[TABLE_NAME]RECORDINSERT>       
<[TABLE_NAME]RECORDINSERT >       
<[FIELD1_NAME InlineValue="value"]>value1</[FIELD1_NAME]>       
<[FIELD2_NAME InlineValue="value"]>value2</[FIELD2_NAME]>       
…     
</[TABLE_NAME]RECORDINSERT>     
…   
</RECORDSET> 
</Insert>
```

<span data-ttu-id="e8ec0-119">SQL exécutée par l’adaptateur :`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-119">SQL executed by the adapter: `INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`</span></span>


<span data-ttu-id="e8ec0-120">**Insertion en bloc**</span><span class="sxs-lookup"><span data-stu-id="e8ec0-120">**Bulk Insert**</span></span>  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>
<QUERY>[SELECT_query]</QUERY>
</Insert>
```

<span data-ttu-id="e8ec0-121">SQL exécutée par l’adaptateur :`INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-121">SQL executed by the adapter: `INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`</span></span>

### <a name="insert-response"></a><span data-ttu-id="e8ec0-122">Insérer la réponse</span><span class="sxs-lookup"><span data-stu-id="e8ec0-122">Insert Response</span></span>
<span data-ttu-id="e8ec0-123">Le nombre de lignes insérées est retourné dans l’élément InsertResult.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-123">The number of rows inserted is returned in the InsertResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-124">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-124">XML message</span></span>  

```
<InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<InsertResult>[rows inserted]</InsertResult> 
</InsertResponse>
```

### <a name="select"></a><span data-ttu-id="e8ec0-125">Select</span><span class="sxs-lookup"><span data-stu-id="e8ec0-125">Select</span></span>
<span data-ttu-id="e8ec0-126">Une requête SELECT est exécutée sur la table cible à l’aide de la clause WHERE spécifiée dans l’élément de filtre.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-126">A SELECT query is performed on the target table using the WHERE clause specified in the FILTER element.</span></span> <span data-ttu-id="e8ec0-127">Le jeu de résultats contient les colonnes dans la liste séparée par des virgules des noms de colonnes spécifiés dans l’élément les noms de colonne.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-127">The result set contains the columns in the comma-separated list of column names specified in the COLUMN_NAMES element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-128">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-128">XML message</span></span>  
```
<Select xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   
<FILTER>WHERE_clause</FILTER> 
</Select>
```

<span data-ttu-id="e8ec0-129">SQL exécutée par l’adaptateur :`SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-129">SQL executed by the adapter: `SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`</span></span>

### <a name="select-response"></a><span data-ttu-id="e8ec0-130">Sélectionnez la réponse</span><span class="sxs-lookup"><span data-stu-id="e8ec0-130">Select Response</span></span>
<span data-ttu-id="e8ec0-131">Le jeu de résultats généré par la requête SELECT.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-131">The result set generated by the SELECT query.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-132">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-132">XML message</span></span>  
```
<SelectResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<SelectResult>     
<[TABLE_NAME]RECORDSELECT>       
<[FIELD1_NAME]>value1</[FIELD1_NAME]>       
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…     
</[TABLE_NAME]RECORDSELECT>   
</SelectResult> 
</SelectResponse>
``` 

### <a name="update"></a><span data-ttu-id="e8ec0-133">Update</span><span class="sxs-lookup"><span data-stu-id="e8ec0-133">Update</span></span>
<span data-ttu-id="e8ec0-134">Les lignes qui correspondent à l’emplacement où clause spécifiée dans l’élément de filtre sont mis à jour avec les valeurs spécifiées dans le jeu d’enregistrements.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-134">Rows that match the where clause specified in the FILTER element are updated to the values specified in the RECORDSET.</span></span> <span data-ttu-id="e8ec0-135">Seules les colonnes qui sont spécifiés dans le jeu d’enregistrements sont mis à jour dans chaque ligne correspondante.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-135">Only the columns that are specified in the RECORDSET are updated in each matching row.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-136">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-136">XML message</span></span>  
```
<Update xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[FIELD1_NAME]>value1</[FIELD1_NAME]>     
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…   
</RECORDSET>   
<FILTER>WHERE_clause</FILTER> </Update>
```

<span data-ttu-id="e8ec0-137">SQL exécutée par l’adaptateur :`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-137">SQL executed by the adapter: `UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`</span></span>

### <a name="update-response"></a><span data-ttu-id="e8ec0-138">Réponse de mise à jour</span><span class="sxs-lookup"><span data-stu-id="e8ec0-138">Update Response</span></span>
<span data-ttu-id="e8ec0-139">Le nombre de lignes mises à jour est retourné dans l’élément UpdateResult.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-139">The number of rows updated is returned in the UpdateResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-140">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-140">XML message</span></span>  
```
<UpdateResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<UpdateResult>[rows inserted]</UpdateResult> 
</UpdateResponse>
```

### <a name="delete"></a><span data-ttu-id="e8ec0-141">DELETE</span><span class="sxs-lookup"><span data-stu-id="e8ec0-141">Delete</span></span>
<span data-ttu-id="e8ec0-142">Les lignes correspondant à la clause WHERE spécifiée par l’élément de filtre sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-142">Rows matching the WHERE clause specified by the FILTER element are deleted.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-143">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-143">XML message</span></span> 
```
<Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<FILTER>WHERE_clause</FILTER> 
</Delete>
```

<span data-ttu-id="e8ec0-144">SQL exécutée par l’adaptateur :`DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-144">SQL executed by the adapter: `DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`</span></span>

### <a name="delete-response"></a><span data-ttu-id="e8ec0-145">Réponse de suppression</span><span class="sxs-lookup"><span data-stu-id="e8ec0-145">Delete Response</span></span>
<span data-ttu-id="e8ec0-146">Le nombre de lignes supprimées est retourné dans l’élément DeleteResult.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-146">The number of rows deleted is returned in the DeleteResult element.</span></span>

#### <a name="xml-message"></a><span data-ttu-id="e8ec0-147">Message XML</span><span class="sxs-lookup"><span data-stu-id="e8ec0-147">XML message</span></span> 
```
<DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<DeleteResult>[rows inserted]</DeleteResult> 
</DeleteResponse>
```
  
  | <span data-ttu-id="e8ec0-148">Valeur d’espace réservé</span><span class="sxs-lookup"><span data-stu-id="e8ec0-148">Placeholder value</span></span>| <span data-ttu-id="e8ec0-149"> Description</span><span class="sxs-lookup"><span data-stu-id="e8ec0-149">Description</span></span> |
  | --- | --- |
  | <span data-ttu-id="e8ec0-150">[VERSION]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-150">[VERSION]</span></span> | <span data-ttu-id="e8ec0-151">La chaîne de version de message ; par exemple,`http://Microsoft.LobServices.OracleDB/2007/03`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-151">The message version string; for example, `http://Microsoft.LobServices.OracleDB/2007/03`</span></span>|
  | <span data-ttu-id="e8ec0-152">[SCHÉMA]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-152">[SCHEMA]</span></span> | <span data-ttu-id="e8ec0-153">Collection d’artefacts d’Oracle ; par exemple,`SCOTT`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-153">Collection of Oracle artifacts; for example, `SCOTT`</span></span>|
  | <span data-ttu-id="e8ec0-154">[NOM_TABLE]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-154">[TABLE_NAME]</span></span> | <span data-ttu-id="e8ec0-155">Nom de la table ; par exemple,`EMP`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-155">Name of the table; for example, `EMP`</span></span>|
  | <span data-ttu-id="e8ec0-156">[FIELD1_NAME]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-156">[FIELD1_NAME]</span></span> | <span data-ttu-id="e8ec0-157">Nom du champ de table ; par exemple,`EMPNAME`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-157">Table field name; for example, `EMPNAME`</span></span>|
  | <span data-ttu-id="e8ec0-158">[COLUMN_list]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-158">[COLUMN_list]</span></span> | <span data-ttu-id="e8ec0-159">Séparées par des virgules de liste de colonnes ; par exemple,`NAME`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-159">Comma-separated list of columns; for example, `NAME`</span></span>|
  | <span data-ttu-id="e8ec0-160">[SELECT_query]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-160">[SELECT_query]</span></span> | <span data-ttu-id="e8ec0-161">Une instruction SQL SELECT spécifiée dans l’élément de requête d’une opération d’insertion en bloc ; par exemple,`SELECT * from MyTable`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-161">A SQL SELECT statement specified in the QUERY element of a Bulk Insert operation; for example, `SELECT * from MyTable`</span></span>|
  | <span data-ttu-id="e8ec0-162">[WHERE_clause]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-162">[WHERE_clause]</span></span> | <span data-ttu-id="e8ec0-163">WHERE_clause pour l’instruction SELECT utilisée pour l’opération ; par exemple,`ID > 10`</span><span class="sxs-lookup"><span data-stu-id="e8ec0-163">WHERE_clause for the SELECT statement used for the operation; for example, `ID > 10`</span></span>|
  
> [!IMPORTANT]
>  <span data-ttu-id="e8ec0-164">La structure du message pour les opérations de table de base sur les vues est le même que sur les tables, mais l’espace de noms pour l’opération spécifie une vue, plutôt qu’une table : `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-164">The message structure for the basic table operations on views is the same as that on tables, but the namespace for the operation specifies a view rather than a table: `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.</span></span>  
  
## <a name="message-actions-for-basic-table-operations"></a><span data-ttu-id="e8ec0-165">Actions de message pour les opérations de Table de base</span><span class="sxs-lookup"><span data-stu-id="e8ec0-165">Message Actions for Basic Table Operations</span></span>  
 <span data-ttu-id="e8ec0-166">Le tableau suivant présente les actions de message utilisés par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour les opérations de table de base sur les tables.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-166">The following table shows the message actions that are used by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for the basic table operations on tables.</span></span> <span data-ttu-id="e8ec0-167">Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise le nom de la table spécifié dans l’action du message pour déterminer la table cible de l’opération.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-167">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses the table name specified in the message action to determine the target table of the operation.</span></span>  
  
|<span data-ttu-id="e8ec0-168">Opération</span><span class="sxs-lookup"><span data-stu-id="e8ec0-168">Operation</span></span>|<span data-ttu-id="e8ec0-169">Action du message</span><span class="sxs-lookup"><span data-stu-id="e8ec0-169">Message Action</span></span>|<span data-ttu-id="e8ec0-170">Exemple</span><span class="sxs-lookup"><span data-stu-id="e8ec0-170">Example</span></span>|  
|---------------|--------------------|-------------|  
|<span data-ttu-id="e8ec0-171">Insert</span><span class="sxs-lookup"><span data-stu-id="e8ec0-171">Insert</span></span>|<span data-ttu-id="e8ec0-172">[VERSION] / [schéma] /Table/ [nom_table] / insertion</span><span class="sxs-lookup"><span data-stu-id="e8ec0-172">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Insert</span></span>|<span data-ttu-id="e8ec0-173">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/INSERT</span><span class="sxs-lookup"><span data-stu-id="e8ec0-173">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert</span></span>|  
|<span data-ttu-id="e8ec0-174">Insérer la réponse</span><span class="sxs-lookup"><span data-stu-id="e8ec0-174">Insert Response</span></span>|<span data-ttu-id="e8ec0-175">[VERSION] / /Table/ [nom_table] / Insert/réponse de [schéma]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-175">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Insert/response</span></span>|<span data-ttu-id="e8ec0-176">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/INSERT/Response</span><span class="sxs-lookup"><span data-stu-id="e8ec0-176">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Insert/response</span></span>|  
|<span data-ttu-id="e8ec0-177">Select</span><span class="sxs-lookup"><span data-stu-id="e8ec0-177">Select</span></span>|<span data-ttu-id="e8ec0-178">[VERSION] / [schéma] /Table/ [nom_table] / sélectionner</span><span class="sxs-lookup"><span data-stu-id="e8ec0-178">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Select</span></span>|<span data-ttu-id="e8ec0-179">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/SELECT</span><span class="sxs-lookup"><span data-stu-id="e8ec0-179">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select</span></span>|  
|<span data-ttu-id="e8ec0-180">Sélectionnez la réponse</span><span class="sxs-lookup"><span data-stu-id="e8ec0-180">Select Response</span></span>|<span data-ttu-id="e8ec0-181">[VERSION] / /Table/ [nom_table] / sélectionner/réponse de [schéma]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-181">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Select/response</span></span>|<span data-ttu-id="e8ec0-182">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/SELECT/Response</span><span class="sxs-lookup"><span data-stu-id="e8ec0-182">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select/response</span></span>|  
|<span data-ttu-id="e8ec0-183">Update</span><span class="sxs-lookup"><span data-stu-id="e8ec0-183">Update</span></span>|<span data-ttu-id="e8ec0-184">[VERSION] / [schéma] /Table/ [nom_table] / mise à jour</span><span class="sxs-lookup"><span data-stu-id="e8ec0-184">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Update</span></span>|<span data-ttu-id="e8ec0-185">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Update</span><span class="sxs-lookup"><span data-stu-id="e8ec0-185">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update</span></span>|  
|<span data-ttu-id="e8ec0-186">Réponse de mise à jour</span><span class="sxs-lookup"><span data-stu-id="e8ec0-186">Update Response</span></span>|<span data-ttu-id="e8ec0-187">[VERSION] / /Table/ [nom_table] / mise à jour/réponse de [schéma]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-187">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Update/response</span></span>|<span data-ttu-id="e8ec0-188">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Update/Response</span><span class="sxs-lookup"><span data-stu-id="e8ec0-188">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Update/response</span></span>|  
|<span data-ttu-id="e8ec0-189">DELETE</span><span class="sxs-lookup"><span data-stu-id="e8ec0-189">Delete</span></span>|<span data-ttu-id="e8ec0-190">[VERSION] / [schéma] /Table/ [nom_table] / Delete</span><span class="sxs-lookup"><span data-stu-id="e8ec0-190">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Delete</span></span>|<span data-ttu-id="e8ec0-191">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Delete</span><span class="sxs-lookup"><span data-stu-id="e8ec0-191">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete</span></span>|  
|<span data-ttu-id="e8ec0-192">Réponse de suppression</span><span class="sxs-lookup"><span data-stu-id="e8ec0-192">Delete Response</span></span>|<span data-ttu-id="e8ec0-193">[VERSION] / /Table/ [nom_table] / Delete/réponse de [schéma]</span><span class="sxs-lookup"><span data-stu-id="e8ec0-193">[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/Delete/response</span></span>|<span data-ttu-id="e8ec0-194">http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Delete/Response</span><span class="sxs-lookup"><span data-stu-id="e8ec0-194">http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Delete/response</span></span>|  
  
 <span data-ttu-id="e8ec0-195">[VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.OracleDB/2007/03.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-195">[VERSION] = The message version string; for example, http://Microsoft.LobServices.OracleDB/2007/03.</span></span>  
  
 <span data-ttu-id="e8ec0-196">[Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-196">[SCHEMA] = Collection of Oracle artifacts; for example, SCOTT.</span></span>  
  
 <span data-ttu-id="e8ec0-197">[Nom_table] = nom de la table ; par exemple, EMP.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-197">[TABLE_NAME] = Name of the table; for example, EMP.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e8ec0-198">L’action du message pour une opération sur une vue est identique à celle d’une table, sauf que la « Vue » remplace « Table » ; par exemple, `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`.</span><span class="sxs-lookup"><span data-stu-id="e8ec0-198">The message action for an operation on a view is the same as that for a table except that "View" replaces "Table"; for example, `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ec0-199">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8ec0-199">See Also</span></span>  
 [<span data-ttu-id="e8ec0-200">Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="e8ec0-200">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)