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
# <a name="message-schemas-for-the-basic-insert-update-delete-and-select-operations-on-tables-and-views"></a>Schémas de message pour l’insertion de base, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] surfaces base Insert, Update, Delete, et les opérations Select pour chaque table et afficher dans la base de données Oracle. Ces opérations exécuter l’instruction SQL appropriée qualifiée par une clause WHERE. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise les enregistrements de fortement typée et des jeux d’enregistrements dans ces opérations.  
  
## <a name="message-structure-for-basic-table-operations"></a>Structure du message pour les opérations de Table de base  
 Le tableau suivant présente la structure de message XML pour les opérations de table de base exposées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] sur les tables de base de données Oracle. La table cible pour une opération est spécifiée dans l’action du message et s’affiche également dans l’espace de noms cible.  

### <a name="insert"></a>Insert  
Il existe les types suivants d’opérations d’insertion. Un message peut contenir qu’un seul type d’opération d’insertion.

- Insertion de plusieurs enregistrements d’insère le jeu d’enregistrements fourni des données fortement typées dans la table cible.
- Pour chaque enregistrement d’une insertion de plusieurs enregistrement, vous pouvez spécifier la valeur d’un attribut facultatif appelé **InlineValue**. Si spécifié, il remplace la valeur de l’élément.
- Instruction Bulk Insert insère le jeu d’enregistrements retourné par une requête SELECT spécifiée dans l’élément de requête dans la table cible. Cela permet à l’aide de la liste séparée par des virgules des colonnes spécifiées dans l’élément les noms de colonne.

#### <a name="xml-message"></a>Message XML  

**Insertion d’enregistrement multiples**  
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

SQL exécutée par l’adaptateur :`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …)VALUES (value1, value2, …);`


**Insertion en bloc**  
```
<Insert xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>
<QUERY>[SELECT_query]</QUERY>
</Insert>
```

SQL exécutée par l’adaptateur :`INSERT INTO TABLE_NAME (COLUMN_list) SELECT_query;`

### <a name="insert-response"></a>Insérer la réponse
Le nombre de lignes insérées est retourné dans l’élément InsertResult.

#### <a name="xml-message"></a>Message XML  

```
<InsertResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<InsertResult>[rows inserted]</InsertResult> 
</InsertResponse>
```

### <a name="select"></a>Select
Une requête SELECT est exécutée sur la table cible à l’aide de la clause WHERE spécifiée dans l’élément de filtre. Le jeu de résultats contient les colonnes dans la liste séparée par des virgules des noms de colonnes spécifiés dans l’élément les noms de colonne.

#### <a name="xml-message"></a>Message XML  
```
<Select xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   
<FILTER>WHERE_clause</FILTER> 
</Select>
```

SQL exécutée par l’adaptateur :`SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`

### <a name="select-response"></a>Sélectionnez la réponse
Le jeu de résultats généré par la requête SELECT.

#### <a name="xml-message"></a>Message XML  
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

### <a name="update"></a>Update
Les lignes qui correspondent à l’emplacement où clause spécifiée dans l’élément de filtre sont mis à jour avec les valeurs spécifiées dans le jeu d’enregistrements. Seules les colonnes qui sont spécifiés dans le jeu d’enregistrements sont mis à jour dans chaque ligne correspondante.

#### <a name="xml-message"></a>Message XML  
```
<Update xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<RECORDSET>     
<[FIELD1_NAME]>value1</[FIELD1_NAME]>     
<[FIELD2_NAME]>value2</[FIELD2_NAME]>       
…   
</RECORDSET>   
<FILTER>WHERE_clause</FILTER> </Update>
```

SQL exécutée par l’adaptateur :`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`

### <a name="update-response"></a>Réponse de mise à jour
Le nombre de lignes mises à jour est retourné dans l’élément UpdateResult.

#### <a name="xml-message"></a>Message XML  
```
<UpdateResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<UpdateResult>[rows inserted]</UpdateResult> 
</UpdateResponse>
```

### <a name="delete"></a>DELETE
Les lignes correspondant à la clause WHERE spécifiée par l’élément de filtre sont supprimés.

#### <a name="xml-message"></a>Message XML 
```
<Delete xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<FILTER>WHERE_clause</FILTER> 
</Delete>
```

SQL exécutée par l’adaptateur :`DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`

### <a name="delete-response"></a>Réponse de suppression
Le nombre de lignes supprimées est retourné dans l’élément DeleteResult.

#### <a name="xml-message"></a>Message XML 
```
<DeleteResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   
<DeleteResult>[rows inserted]</DeleteResult> 
</DeleteResponse>
```
  
  | Valeur d’espace réservé|  Description |
  | --- | --- |
  | [VERSION] | La chaîne de version de message ; par exemple,`http://Microsoft.LobServices.OracleDB/2007/03`|
  | [SCHÉMA] | Collection d’artefacts d’Oracle ; par exemple,`SCOTT`|
  | [NOM_TABLE] | Nom de la table ; par exemple,`EMP`|
  | [FIELD1_NAME] | Nom du champ de table ; par exemple,`EMPNAME`|
  | [COLUMN_list] | Séparées par des virgules de liste de colonnes ; par exemple,`NAME`|
  | [SELECT_query] | Une instruction SQL SELECT spécifiée dans l’élément de requête d’une opération d’insertion en bloc ; par exemple,`SELECT * from MyTable`|
  | [WHERE_clause] | WHERE_clause pour l’instruction SELECT utilisée pour l’opération ; par exemple,`ID > 10`|
  
> [!IMPORTANT]
>  La structure du message pour les opérations de table de base sur les vues est le même que sur les tables, mais l’espace de noms pour l’opération spécifie une vue, plutôt qu’une table : `<Insert xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.  
  
## <a name="message-actions-for-basic-table-operations"></a>Actions de message pour les opérations de Table de base  
 Le tableau suivant présente les actions de message utilisés par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour les opérations de table de base sur les tables. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise le nom de la table spécifié dans l’action du message pour déterminer la table cible de l’opération.  
  
|Opération|Action du message|Exemple|  
|---------------|--------------------|-------------|  
|Insert|[VERSION] / [schéma] /Table/ [nom_table] / insertion|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/INSERT|  
|Insérer la réponse|[VERSION] / /Table/ [nom_table] / Insert/réponse de [schéma]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/INSERT/Response|  
|Select|[VERSION] / [schéma] /Table/ [nom_table] / sélectionner|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/SELECT|  
|Sélectionnez la réponse|[VERSION] / /Table/ [nom_table] / sélectionner/réponse de [schéma]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/SELECT/Response|  
|Update|[VERSION] / [schéma] /Table/ [nom_table] / mise à jour|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Update|  
|Réponse de mise à jour|[VERSION] / /Table/ [nom_table] / mise à jour/réponse de [schéma]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Update/Response|  
|DELETE|[VERSION] / [schéma] /Table/ [nom_table] / Delete|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Delete|  
|Réponse de suppression|[VERSION] / /Table/ [nom_table] / Delete/réponse de [schéma]|http://Microsoft.LobServices.OracleDB/2007/03/Scott/table/emp/Delete/Response|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.OracleDB/2007/03.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = nom de la table ; par exemple, EMP.  
  
> [!IMPORTANT]
>  L’action du message pour une opération sur une vue est identique à celle d’une table, sauf que la « Vue » remplace « Table » ; par exemple, `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/``View``/EMPVIEW/Insert`.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)