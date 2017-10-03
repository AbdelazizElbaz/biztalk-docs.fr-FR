---
title: "Schémas de message pour Insert, Update, Delete, puis sélectionnez les opérations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b8de271-67db-4279-8f95-0b4dd92fa3c4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15bb515eee9a052852952f0ec245f8c954953a9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-insert-update-delete-and-select-operations"></a>Schémas de message pour insérer, mettre à jour, supprimer et sélectionner des opérations
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]surfaces base Insert, Update, Delete et les opérations Select pour chaque table d’interface dans Oracle E-Business Suite et de chaque table dans la base de données sous-jacente. L’adaptateur met également en évidence l’opération Select pour chaque vue de l’interface dans Oracle E-Business Suite et chaque vue dans la base de données sous-jacente. Ces opérations exécuter l’instruction SQL appropriée qualifiée par une clause WHERE. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise les enregistrements de fortement typée et des jeux d’enregistrements dans ces opérations.  
  
## <a name="message-structure-for-basic-operations"></a>Structure du message pour les opérations de base  
 Le tableau suivant présente la structure de message XML pour les opérations de base exposées par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] sur les tables d’interface Oracle E-Business Suite et de vues de l’interface et sur les tables de base de données sous-jacentes et les vues. L’objet cible pour une opération est spécifié dans l’action du message et s’affiche également dans l’espace de noms cible.  
  
> [!NOTE]
>  Consultez les descriptions de l’attribut après la table.  
  
|Opération|Message XML| Description|SQL exécutée par l’adaptateur|  
|---------------|-----------------|-----------------|---------------------------------|  
|Insert|`<Insert xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <RECORDSET>     <InsertRecord>       <[FIELD1_NAME] InlineValue="value">[value1]</[FIELD1_NAME]>       <[FIELD2_NAME] InlineValue="value">[value2]</[FIELD2_NAME]>       …     </InsertRecord>   </RECORDSET> </Insert>`|La valeur de la **InlineValue** attribut, si spécifiée, remplace la valeur d’un élément.|`INSERT INTO TABLE_NAME (FIELD1_NAME, FIELD2_NAME, …) VALUES (value1, value2, …);`|  
|Insérer la réponse|`<InsertResponse xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <InsertResult>[rows inserted]</InsertResult> </InsertResponse>`|Le nombre de lignes insérées est retourné dans le **InsertResult** élément.|--|  
|Select|`<Select xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <COLUMN_NAMES>[COLUMN_list]</COLUMN_NAMES>   <FILTER>WHERE_clause</FILTER> </Select>`|Une requête SELECT est exécutée sur la table cible à l’aide de la clause WHERE spécifiée dans l’élément de filtre. Le jeu de résultats contient les colonnes dans la liste séparée par des virgules de noms de colonnes spécifié dans le **les noms de colonne** élément.<br /><br /> **Important :** c’est la seule opération qui s’applique aux vues de l’interface et les vues de base de données.|`SELECT COLUMN_list FROM TABLE_NAME WHERE WHERE_clause;`|  
|Sélectionnez la réponse|`<SelectResponse  xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <SelectResult>     <SelectRecord>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </SelectRecord>   </SelectResult> </SelectResponse>`|Le jeu de résultats généré par la requête SELECT.|--|  
|Update|`<Update xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <RECORDSET>     <[FIELD1_NAME]>value1</[FIELD1_NAME]>     <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …   </RECORDSET>   <FILTER>WHERE_clause</FILTER> </Update>`|Les lignes qui correspondent à l’emplacement où clause spécifiée dans le **filtre** élément sont mis à jour avec les valeurs spécifiées dans le **RECORDSET**. Seules les colonnes qui sont spécifiés dans le **RECORDSET** élément sont mis à jour dans chaque ligne correspondante.|`UPDATE [TABLE_NAME] SET [FIELD1_NAME] = value1, [FIELD2_NAME] = value2, … WHERE WHERE_clause;`|  
|Réponse de mise à jour|`<UpdateResponse xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <UpdateResult>[rows inserted]</UpdateResult> </UpdateResponse>`|Le nombre de lignes mises à jour est retourné dans le **UpdateResult** élément.|--|  
|DELETE|`<Delete xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <FILTER>WHERE_clause</FILTER> </Delete>`|Les lignes correspondant à la clause WHERE spécifiée par le **filtre** élément sont supprimés.|`DELETE FROM [TABLE_NAME] WHERE WHERE_clause;`|  
|Réponse de suppression|`<DeleteResponse xmlns="[VERSION]/InterfaceTables/[SCHEMA]/[APP_NAME]/[INTERFACETABLE_NAME]">   <DeleteResult>[rows deleted]</DeleteResult> </DeleteResponse>`|Le nombre de lignes supprimées est retourné dans le **DeleteResult** élément.|--|  
  
 Description de l’attribut :  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://schemas.microsoft.com/OracleEBS/2008/05.  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_application] = nom court de l’Application.  
  
 [INTERFACETABLE_NAME] = nom de la table d’interface.  
  
 [FIELD1_NAME] = nom de champ de Table.  
  
 [COLUMN_list] = séparées par des virgules de liste de colonnes.  
  
 [WHERE_clause] = WHERE_clause pour l’instruction SELECT utilisée pour l’opération ; par exemple, l’ID 10 >.  
  
> [!IMPORTANT]
>  La structure du message pour les opérations de base sur les vues de l’interface, les tables de base de données et les vues de base de données est le même que sur les tables d’interface, mais l’espace de noms pour l’opération spécifie une vue de l’interface, table de base de données, ou vue de base de données plutôt qu’une interface table.  
  
## <a name="message-actions-for-basic-operations"></a>Actions de message pour les opérations de base  
 Le tableau suivant montre les actions de message que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise pour les opérations de base sur les tables d’interface et affichage de l’interface dans Oracle E-Business Suite et les tables et les vues dans la base de données sous-jacente. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise la table d’interface, vue de l’interface, la table de base de données ou vue de base de données spécifiée dans l’action du message pour déterminer la cible de l’opération.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après la table.  
  
|Opération|Action du message|Exemple|  
|---------------|--------------------|-------------|  
|Insert|**Applications**: InterfaceTables/Insert / [SHORT_NAME] / [nom_application] / [nom_table]<br /><br /> **Base de données**: Tables/Insert / [schéma] / [nom_table]|**Applications**: InterfaceTables/Insert/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **Base de données**: Tables/Insert/GL/GL_ALLOC_HISTORY|  
|Insérer la réponse|**Applications**: InterfaceTables/Insert / [SHORT_NAME] / [nom_application] / [nom_table] / réponse<br /><br /> **Base de données**: Tables/Insert / [schéma] / [nom_table] / réponse|**Applications**: insertion/InterfaceTables/SQLGL/GL_ALLOC_HISTORY/GL/réponse<br /><br /> **Base de données**: Tables/Insert/GL/GL_ALLOC_HISTORY/réponse.|  
|Select|**Applications**: InterfaceTables/sélectionner / [SHORT_NAME] / [nom_application] / [nom_table]<br /><br /> **Base de données**: Tables/sélectionner / [schéma] / [nom_table]|**Applications**: InterfaceTables/sélectionner/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **Base de données**: Tables/sélectionner/GL/GL_ALLOC_HISTORY|  
|Sélectionnez la réponse|**Applications**: InterfaceTables/sélectionner / [SHORT_NAME] / [nom_application] / [nom_table] / réponse<br /><br /> **Base de données**: Tables/sélectionner / [schéma] / [nom_table] / réponse|**Applications**: sélectionnez/InterfaceTables/SQLGL/GL_ALLOC_HISTORY/GL/réponse<br /><br /> **Base de données**: Tables/sélectionner/GL/GL_ALLOC_HISTORY/réponse.|  
|Update|**Applications**: InterfaceTables/mise à jour / [SHORT_NAME] / [nom_application] / [nom_table]<br /><br /> **Base de données**: mise à jour de Tables / / [schéma] / [nom_table]|**Applications**: InterfaceTables/mise à jour/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **Base de données**: Tables/mise à jour/GL/GL_ALLOC_HISTORY|  
|Réponse de mise à jour|**Applications**: InterfaceTables/mise à jour / [SHORT_NAME] / [nom_application] / [nom_table] / réponse<br /><br /> **Base de données**: mise à jour de Tables / / [schéma] / [nom_table] / réponse|**Applications**: mise à jour/InterfaceTables/SQLGL/GL_ALLOC_HISTORY/GL/réponse<br /><br /> **Base de données**: Tables/mise à jour/GL/GL_ALLOC_HISTORY/réponse.|  
|DELETE|**Applications**: InterfaceTables/Delete / [SHORT_NAME] / [nom_application] / [nom_table]<br /><br /> **Base de données**: Tables/Delete / [schéma] / [nom_table]|**Applications**: InterfaceTables/Delete/SQLGL/GL/GL_ALLOC_HISTORY<br /><br /> **Base de données**: Tables/Delete/GL/GL_ALLOC_HISTORY|  
|Réponse de suppression|**Applications**: InterfaceTables/Delete / [SHORT_NAME] / [nom_application] / [nom_table] / réponse<br /><br /> **Base de données**: Tables/Delete / [schéma] / [nom_table] / réponse|**Applications**: Delete/InterfaceTables/SQLGL/GL_ALLOC_HISTORY/GL/réponse<br /><br /> **Base de données**: Tables/Delete/GL/GL_ALLOC_HISTORY/réponse.|  
  
 Descriptions de l’entité :  
  
-   [Schéma] - artefacts (par exemple, GL) de la Collection d’Oracle.  
  
-   [Nom_table] - nom de la table (par exemple, GL_ALLOC_HISTORY).  
  
> [!IMPORTANT]
>  L’action du message pour l’opération Select sur une vue de l’interface est identique à celui pour la table d’interface, à ceci près que « InterfaceViews » remplace « InterfaceTables ». De même, l’action du message pour l’opération Select sur une vue de base de données est identique à celle de la table de base de données, à ceci près que « Vues » remplace « Tables ».  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)