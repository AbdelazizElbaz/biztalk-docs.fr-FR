---
title: "Schémas de message pour Insert, Update, Delete, puis sélectionnez les opérations sur les Tables et vues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4fff9cd3-26c0-4d5c-8162-3fd7966a5020
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73270b3d096a8d72de5b339835737cc74d264c9c
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="message-schemas-for-insert-update-delete-and-select-operations-on-tables-and-views"></a>Schémas de message pour insérer, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces Insert, Update, Delete et des opérations Select pour chaque table et vue dans la base de données SQL Server. Ces opérations exécuter l’instruction SQL appropriée qualifiée par une clause WHERE. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise les enregistrements de fortement typée et des jeux d’enregistrements dans ces opérations.  
  
## <a name="message-structure-for-table-operations"></a>Structure du message pour les opérations de Table  
 Le tableau suivant présente la structure de message XML pour les opérations de table de base exposées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sur SQL Server les tables de base de données. La table cible pour une opération est spécifiée dans l’action du message et s’affiche également dans l’espace de noms cible.  
  
|Opération|Message XML| Description|SQL exécutée par l’adaptateur|  
|---------------|-----------------|-----------------|---------------------------------|  
|Insert|`<Insert xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Rows>     <[TABLE_NAME]>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </Rows> </Insert>`|Insère le jeu d’enregistrements fourni des données fortement typées dans la table cible.|`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …) VALUES (value1, value2, …);`|  
|Insérer la réponse|`<InsertResponse xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <InsertResult>     <long>[Value]</long>   </InsertResult> </InsertResponse>`|Le message de réponse d’insérer contient un tableau de type de données Long. Le tableau stocke les valeurs d’identité de lignes insérées, le cas échéant. Si elle n’existe aucune colonne d’identité dans une table, la valeur de retour est NULL.|--|  
|Select|Sélection de tous les enregistrements :<br /><br /> `<Select xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Columns>*</COLUMNS>   <Query></Query> </Select>`<br /><br /> Sélection de colonnes spécifiques dans un jeu d’enregistrements :<br /><br /> `<Select xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Columns>[COLUMN_list]</COLUMNS>   <Query>where [WHERE_clause]</Query> </Select>`<br /><br /> Mise à jour des enregistrements dans le cadre de l’opération Select :<br /><br /> `<Select xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Columns>[COLUMN_list]</Columns>   <Query>where [WHERE_clause];UPDATE [TABLE_NAME] SET [FIELD1_NAME] = [value1] where [WHERE_clause]</Query> </Select>`|Une requête SELECT est exécutée sur la table cible à l’aide de la clause WHERE spécifiée dans l’élément. Le jeu de résultats contient les colonnes dans la liste séparée par des virgules de noms de colonnes spécifié dans le \<colonnes\> élément.<br /><br /> Il est obligatoire pour fournir la valeur dans la \<colonnes\> élément. Si toutes les colonnes doivent être récupérées dans une table ou une vue, * doit être spécifié dans le \<colonnes\> élément. Si des colonnes spécifiques doivent être extraits, les noms de colonne doivent être séparés par des virgules et spécifiés dans le même ordre qu’ils sont définis dans la table ou la vue.<br /><br /> Il est obligatoire pour inclure la clause WHERE dans l’instruction SELECT. Si vous ne souhaitez pas spécifier une clause WHERE, vous pouvez soit supprimer la \<requête\> élément ou la laisser vide.<br /><br /> Vous pouvez mettre à jour des enregistrements à l’aide de l’opération Select. Une instruction UPDATE est placée dans le \<requête\> élément de la requête SELECT XML, séparée de la clause WHERE par un point-virgule. Notez que l’instruction UPDATE ne pas une opération sur le jeu de résultats de l’instruction SELECT.|Sélection de tous les enregistrements :<br /><br /> `SELECT * FROM [TABLE_NAME] WHERE [WHERE_clause];`<br /><br /> Sélection de colonnes spécifiques dans un jeu d’enregistrements :<br /><br /> `SELECT [COLUMN_list] FROM [TABLE_NAME] WHERE [WHERE_clause];`<br /><br /> Mise à jour des enregistrements dans le cadre de l’opération Select :<br /><br /> `SELECT [COLUMN_list] FROM [TABLE_NAME] WHERE [WHERE_clause]; UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1 [WHERE_clause];`|  
|Sélectionnez la réponse|`<SelectResponse  xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <SelectResult>     <[TABLE_NAME]>       <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>       <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </SelectResult> <SelectResponse>`|Le jeu de résultats de fortement typé généré par la requête SELECT.|--|  
|Update|`<SelectResponse  xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <SelectResult>     <[TABLE_NAME]>       <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>       <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </SelectResult> </SelectResponse>`<br /><br /> `<Update xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Rows>     <RowPair>       <After>         <[FIELD1_NAME]>[value1]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value2]</[FIELD2_NAME]>         …       </After>       <Before>         <[FIELD1_NAME]>[value3]</[FIELD1_NAME]>         <[FIELD2_NAME]>[value4]</[FIELD2_NAME]>         …       </Before>     </RowPair>   </Rows> </Update>`|Prend un tableau de paires d’enregistrement en tant qu’entrée. Chaque paire d’enregistrement est une collection de deux enregistrements fortement typée :<br /><br /> Tout d’abord enregistrer (dans le `<After>` élément) correspond aux nouvelles valeurs qui doivent être mis à jour.<br /><br /> Deuxième enregistrement (dans le `<Before>`) correspond aux valeurs des lignes anciennes.|`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE [FIELD1_NAME] = value3, [FIELD2_NAME] = value4, …;`|  
|Réponse de mise à jour|`<UpdateResponse xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <UpdateResult>[rows updated]</UpdateResult> </UpdateResponse>`|Le nombre de lignes mises à jour est retourné dans le **UpdateResult** élément.|--|  
|Supprimer|`<Delete xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <Rows>     <[TABLE_NAME]>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </[TABLE_NAME]>   </Rows> </Delete>`|--|`DELETE FROM [TABLE_NAME] WHERE [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, …;`|  
|Réponse de suppression|`<DeleteResponse xmlns="[VERSION]/TableOp/[SCHEMA]/[TABLE_NAME]">   <DeleteResult>[rows deleted]</DeleteResult> </DeleteResponse>`|Le nombre de lignes supprimées est retourné dans le **DeleteResult** élément.|--|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://schemas.microsoft.com/Sql/2008/05.  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
 [FIELD1_NAME] = nom du champ de Table ; par exemple, un nom.  
  
 [COLUMN_list] = séparées par des virgules de liste de colonnes ; par exemple, nom, âge, désignation.  
  
 [SELECT_query] = une SQL instruction SELECT spécifiée dans l’élément de requête d’une opération d’insertion en bloc ; par exemple, « SELECT * from MyTable »  
  
 [WHERE_clause] = WHERE_clause pour l’instruction SELECT utilisée pour l’opération ; par exemple, l’ID 10 >.  
  
> [!IMPORTANT]
>  La structure du message pour les opérations de table de base sur les vues est le même que sur les tables, sauf que la vue remplace la table : `Insert xmlns="[VERSION]/ViewOp/[SCHEMA]/[VIEW_NAME]"`.  
  
## <a name="message-actions-for-basic-table-operations"></a>Actions de message pour les opérations de Table de base  
 Le tableau suivant présente les actions de message utilisés par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour les opérations de table de base sur les tables. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise le nom de la table spécifié dans l’action du message pour déterminer la table cible de l’opération.  
  
|Opération|Action du message|Exemple|  
|---------------|--------------------|-------------|  
|Insert|TableOp/Insert/[SCHEMA]/[TABLE_NAME]|TableOp/Insert/dbo/employé|  
|Insérer la réponse|TableOp/Insert/[SCHEMA]/[TABLE_NAME]/response|TableOp/Insert/dbo/Employee/response|  
|Select|TableOp/Select/[SCHEMA]/[TABLE_NAME]|TableOp/sélectionner/dbo/employé|  
|Sélectionnez la réponse|TableOp/Select/[SCHEMA]/[TABLE_NAME]/response|TableOp/Select/dbo/Employee/response|  
|Update|TableOp/Update/[SCHEMA]/[TABLE_NAME]|TableOp/mise à jour/dbo/employé|  
|Réponse de mise à jour|TableOp/Update/[SCHEMA]/[TABLE_NAME]/response|TableOp/Update/dbo/Employee/response|  
|Supprimer|TableOp/Delete/[SCHEMA]/[TABLE_NAME]|TableOp/Delete/dbo/employé|  
|Réponse de suppression|TableOp/Delete/[SCHEMA]/[TABLE_NAME]/response|TableOp/Delete/dbo/Employee/response|  
  
 [Schéma] = des artefacts de la Collection de SQL Server ; par exemple, dbo.  
  
 [Nom_table] = nom de la table ; par exemple, les employés.  
  
> [!IMPORTANT]
>  L’action du message pour une opération sur une vue est identique à celle d’une table, sauf que « ViewOp » remplace « TableOp » ; par exemple, `ViewOp``/Insert/dbo/Employee_View`.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)