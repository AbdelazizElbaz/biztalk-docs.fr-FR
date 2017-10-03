---
title: "Schémas de message pour LOB spéciaux Operations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LOB data types, message structure of
- LOB data types, message actions for
ms.assetid: 031989d5-3209-41ab-8836-a40539781e74
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 203ffc81b6dc85fcaf7b80ff097bbeb001b747cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-special-lob-operations"></a>Schémas de message pour les opérations métier spéciaux
Les opérations ReadLOB et UpdateLOB sont signalées pour les tables et vues qui contiennent des colonnes LOB ; c'est-à-dire les colonnes qui sont utilisés pour stocker les données Oracle LOB (large object). Ces opérations permettent de lire ou écrire les données métier en tant que flux de données encodées base64Binary. Ils opèrent sur une seule colonne de données LOB dans une seule ligne.  
  
 Pour une vue d’ensemble des opérations ReadLOB et UpdateLOB et les types de données Oracle LOB pris en charge, consultez [opérations sur les tables et les vues qui contiennent des données dans la base de données Oracle LOB](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md).  
  
## <a name="message-structure-of-lob-data-type-operations"></a>Structure des messages d’opérations de Type de données LOB  
 Le tableau suivant montre la structure des messages de demande et de réponse pour les opérations ReadLOB et UpdateLOB. La table cible pour l’opération est spécifiée dans l’action du message et s’affiche également dans l’espace de noms cible.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|ReadLOB|`<ReadLOB xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <LOB_COLUMN>[COL_NAME]</LOB_COLUMN>   <FILTER>[WHERE_clause]</LOB_COLUMN> </ReadLOB>`|Les données LOB de la<br /><br /> -colonne identifiée par l’élément LOB_COLUMN et le<br /><br /> -ligne qui correspond à l’emplacement où clause spécifiée dans l’élément de filtre<br /><br /> est retourné.<br /><br /> Where clause doit correspondre à une seule ligne. S’il existe plus d’une ligne correspondante, les données LOB de la première ligne correspondante sont retournées.<br /><br /> **Important** ReadLOB l’opération est conçue pour prendre en charge la diffusion en continu d’entrée des données LOB dans le modèle de service WCF. Vous devez utiliser une opération de sélection de table pour lire des données LOB à partir d’un modèle de canal WCF ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.|  
|Réponse de ReadLOB|`<ReadLOBResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <ReadLOBResult>     [LOB_DATA]   </ReadLOBResult> </ReadLOBResponse>`|Les données LOB sont retournées en tant que flux de données de base64Binary encodé.<br /><br /> **Important** le WSDL renvoyé par l’adaptateur ne correspond pas au schéma effectivement utilisé par l’adaptateur pour le message de réponse ReadLOB.|  
|UpdateLOB|`<UpdateLOB xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]">   <LOB_COLUMN>[COL_NAME]</LOB_COLUMN>   <FILTER>[WHERE_clause]</LOB_COLUMN>   <Stream>[LOB_DATA]</Stream> </UpdateLOB>`|Les données LOB de la<br /><br /> -colonne identifiée par l’élément LOB_COLUMN et le<br /><br /> -ligne qui correspond à l’emplacement où clause spécifiée dans l’élément de filtre<br /><br /> mise à jour avec les données base64Binary encodées dans le flux de données.<br /><br /> Where clause doit correspondre à une seule ligne. S’il existe plus d’une ligne correspondante, une exception est levée.<br /><br /> **Remarque** UpdateLOB l’opération remplace toutes les données dans la colonne spécifiée et la ligne.|  
|Réponse de UpdateLOB|`<UpdateLOBResponse xmlns="[VERSION]/[SCHEMA]/Table/[TABLE_NAME]"> </UpdateLOBResponse>`|Une réponse vide est retournée.|  
  
 [VERSION] = la chaîne de version de message ; par exemple, « http://Microsoft.LobServices/OracleDB/2007/03 ».  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = la table qui contient la colonne LOB ciblée ; par exemple, EMP.  
  
 [COL_NAME] = nom de la colonne LOB ciblé. par exemple, LOB_FIELD.  
  
 [WHERE_clause] = l’instruction SELECT de base de données Oracle d’une clause WHERE qui correspond à une seule ligne ; par exemple, ID = 1.  
  
 [LOB_DATA] = données de la colonne LOB le dans le type de base64Binary.  
  
> [!IMPORTANT]
>  La structure du message pour les opérations ReadLOB et UpdateLOB sur les vues est le même que sur les tables, sauf que l’espace de noms pour l’opération spécifie une vue, plutôt qu’une table : `<ReadLOB xmlns ="[VERSION]/[SCHEMA]/``View``/[VIEW_NAME]">`.  
  
## <a name="message-actions-for-lob-data-type-operations"></a>Actions de message pour les opérations de Type de données LOB  
 Le tableau suivant présente les actions de message utilisés par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour les opérations ReadLOB et UpdateLOB sur les tables. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise le nom de la table spécifié dans l’action du message pour déterminer la table cible pour l’opération.  
  
|Opération|Action|Exemple|  
|---------------|------------|-------------|  
|ReadLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/ReadLOB`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB`|  
|Réponse de ReadLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/ReadLOB/response`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB/response`|  
|UpdateLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/UpdateLOB`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB`|  
|Réponse de UpdateLOB|`[VERSION]/[SCHEMA]/Table/[TABLE_NAME]/UpdateLOB/response`|`http:/Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB/response`|  
  
 [VERSION] = la chaîne de version de message ; par exemple, « http://Microsoft.LobServices.OracleDB/2007/03 ».  
  
 [Schéma] = des artefacts de la Collection d’Oracle ; par exemple, SCOTT.  
  
 [Nom_table] = la table qui contient la colonne LOB ciblée ; par exemple, le client. (SCOTT. Table CUSTOMER est installée par un script SQL inclus dans les exemples.)  
  
> [!IMPORTANT]
>  L’action du message pour les opérations ReadLOB et UpdateLOB sur les vues est semblable à celle utilisée pour les tables, à ceci près que l’action pour l’opération spécifie une vue, plutôt qu’une table : `[VERSION]/[SCHEMA]/View/[VIEW_NAME]/ReadLOB`.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)