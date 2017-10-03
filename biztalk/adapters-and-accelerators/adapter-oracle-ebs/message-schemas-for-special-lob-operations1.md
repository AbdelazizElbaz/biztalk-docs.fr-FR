---
title: "Schémas de message pour LOB spéciaux Operations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2e418a6-8bc7-42d9-9672-a9c149f32778
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ecc0554162b1cf8298b441c0d129bee83540011
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-special-lob-operations"></a>Schémas de message pour les opérations métier spéciaux
Le Read_\<LOBColName > et en attente_\<LOBColName > opérations sont signalées pour les tables et vues qui contiennent des colonnes LOB, où \<LOBColName > est la colonne LOB de la table ou la vue. Ces opérations permettent de lire ou écrire les données métier en tant que flux de données encodées base64Binary. Ils opèrent sur une seule colonne de données LOB dans une seule ligne.  
  
 Pour une vue d’ensemble de la Read_\<LOBColName > et en attente_\<LOBColName > opérations et Oracle LOB types de données pris en charge, consultez [opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues que contiennent LOB Données](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md).  
  
## <a name="message-structure-of-lob-data-type-operations"></a>Structure des messages d’opérations de Type de données LOB  
 Le tableau suivant montre la structure des messages de demande et de réponse pour le Read_\<LOBColName > et en attente_\<LOBColName > opérations. La table cible pour l’opération est spécifiée dans l’action du message et s’affiche également dans l’espace de noms cible.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|Read_\<LOBColName >|`<Read_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</FILTER></Read_[LOBColName]>`|Les données LOB de la ligne qui correspond à l’emplacement où clause spécifiée dans l’élément de filtre est retourné. Where clause doit correspondre à une seule ligne. S’il existe plus d’une ligne correspondante, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] lève une exception.|  
|Read_\<LOBColName > réponse|`<Read_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <Read_[LOBColName]Result>    [LOB_DATA]  </Read_[LOBColName]Result></Read_[LOBColName]Response>`|Les données LOB sont retournées en tant que flux de données de base64Binary encodé.|  
|En attente_\<LOBColName >|`<Update_[LOBColName] xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]">  <FILTER>[WHERE_clause]</LOB_COLUMN>  <DATA>[Value]</DATA></Update_[LOBColName]>`|Les données LOB dans la ligne qui correspond à l’emplacement où la clause spécifiée dans l’élément de filtre est mis à jour avec les données de la \<données > élément. Where clause doit correspondre à une seule ligne. S’il existe plus d’une ligne correspondante, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] lève une exception.<br /><br /> **Remarque** lors de la mise à jour des colonnes BLOB, la \<données > élément doit toujours contenir une valeur codée en base64. Pour CLOB et NCLOB, le \<données > élément peut avoir des valeurs de chaîne.|  
|En attente_\<LOBColName > réponse|`<Update_[LOBColName]Response xmlns="[VERSION]/Tables/[SCHEMA]/[TABLE_NAME]"></Update_[LOBColName]Response>`|Une réponse vide est retournée.|  
  
 Descriptions de l’entité :  
  
 [VERSION] = la chaîne de version de message ; par exemple, « http://schemas.microsoft.com/OracleEBS/2008/05 ».  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = la table qui contient la colonne LOB ciblée ; par exemple, le client.  
  
 [LOBCol_Name] = le nom d’une colonne LOB ; par exemple, la Photo.  
  
 [WHERE_clause] = l’instruction SELECT de base de données Oracle d’une clause WHERE qui correspond à une seule ligne ; par exemple, ID = 1.  
  
 [LOB_DATA] = données de la colonne LOB le dans le type de base64Binary.  
  
> [!IMPORTANT]
>  La structure du message pour le Read_\<LOBColName > et en attente_\<LOBColName > opérations sur des vues est le même que celui sur les tables, sauf que l’espace de noms pour l’opération spécifie une vue, plutôt qu’une table : `<ReadLOB xmlns ="[VERSION]/Views/[SCHEMA]/[VIEW_NAME]">`.  
  
## <a name="message-actions-for-lob-data-type-operations"></a>Actions de message pour les opérations de Type de données LOB  
 Le tableau suivant présente les actions de message utilisés par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour le Read_\<LOBColName > et en attente_\<LOBColName > opérations sur les tables. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise le nom de table et le nom de la colonne LOB spécifié dans l’action du message pour déterminer la table cible et LOB de colonne pour l’opération.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Action|Exemple|  
|---------------|------------|-------------|  
|Read_\<LOBColName >|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo`|  
|Read_\<LOBColName > réponse|`Tables/ReadLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|`Tables/ReadLOB/SCOTT/CUSTOMER/Photo/response`|  
|En attente_\<LOBColName >|**Pour l’objet BLOB**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`<br /><br /> **Pour CLOB et NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]`|**Pour l’objet BLOB**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/`<br /><br /> **Pour CLOB et NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/`|  
|En attente_\<LOBColName > réponse|**Pour l’objet BLOB**:<br /><br /> `Tables/UpdateBLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`<br /><br /> **Pour CLOB et NCLOB**:<br /><br /> `Tables/UpdateCLOB/[SCHEMA]/[TABLE_NAME]/[LOBColName]/response`|**Pour l’objet BLOB**:<br /><br /> `Tables/UpdateBLOB/SCOTT/CUSTOMER/Photo/response`<br /><br /> **Pour CLOB et NCLOB**:<br /><br /> `Tables/UpdateCLOB/SCOTT/CUSTOMER/Photo1/response`|  
  
 Descriptions de l’entité :  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = la table qui contient la colonne LOB ciblée ; par exemple, le client. (SCOTT. Table CUSTOMER est installée par un script SQL inclus dans les exemples.)  
  
 [LOBCol_Name] = le nom d’une colonne LOB ; par exemple, la Photo.  
  
> [!IMPORTANT]
>  L’action du message pour Read_\<LOBColName > et en attente_\<LOBColName > opérations sur des vues est semblable à celle utilisée pour les tables, à ceci près que l’action pour l’opération spécifie une vue, plutôt qu’une table : `Views/ReadLOB/[SCHEMA]/[VIEW_NAME]/[LOBColName]`.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)