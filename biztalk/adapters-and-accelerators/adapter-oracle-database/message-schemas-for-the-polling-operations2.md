---
title: "Schémas de message pour l’interrogation Operations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- POLLINGSTMT operation, message actions for
- POLLINGSTMT operation, message structure for
ms.assetid: b82edcc2-9437-4c7b-ba2b-7b966fff3f15
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: beb28e7b769c16f1798023adb8b30c3e636a3407
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-polling-operations"></a>Schémas de message pour les opérations d’interrogation
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des différentes opérations entrantes liées à l’interrogation en fonction de l’objet cible sur la base de données Oracle. Pour interroger les tables et les vues, une seule opération POLLINGSTMT apparaissent alors que chaque procédure stockée, fonctions et les procédures et fonctions sont exposées en tant qu’opérations entrantes pour l’interrogation.  
  
 Vous pouvez spécifier un **PollingId** paramètre dans la chaîne de requête de l’URI pour qualifier l’espace de noms de l’opération POLLINGSTMT de connexion. Ce paramètre ne qualifie l’espace de noms de l’opération POLLINGSTMT ; Il ne modifie pas l’action du message. Pour plus d’informations sur l’URI de connexion de l’adaptateur de base de données Oracle, consultez [créer l’URI de connexion de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).  
  
 Vous configurez les opérations d’interrogation en définissant des propriétés de liaison dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour plus d’informations sur ces propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). Vous définissez la **PollingStatement** liaison de propriété pour spécifier une instruction SQL, procédure stockée, fonction ou une procédure dans un package pour la requête d’interrogation. Le jeu de résultats de cette requête est retourné sous forme de données à votre code dans l’opération d’interrogation.  
  
## <a name="message-structure-for-the-polling-operations"></a>Structure du message pour les opérations d’interrogation  
 Le tableau suivant montre la structure de message XML pour les différentes opérations d’interrogation.  
  
|Opération|Objet cible|Message XML| Description|  
|---------------|-------------------|-----------------|-----------------|  
|POLLINGSTMT|-Tables<br /><br /> -Vues|`<?xml version="1.0" encoding="utf-8" ?>  <POLLINGSTMT xmlns="[VERSION]/POLLINGSTMT[POLLING_ID]">   <POLLINGSTMTRECORD>     <POLLINGSTMTRECORD>       <FIELD1_NAME>val1</FIELD1_NAME>        <FIELD2_NAME>val2</FIELD2_NAME>       …     </POLLINGSTMTRECORD>      …    </POLLINGSTMTRECORD> </POLLINGSTMT>`|La structure du jeu de contenus dans les types POLLINGSTMTRECORD de résultats est déterminée par les métadonnées que l’adaptateur met en évidence de la requête SQL SELECT.<br /><br /> L’espace de noms de l’opération POLLINGSTMT est déterminé par le paramètre PollingId dans l’URI de connexion.|  
|[CustomPollingOperation]|-Procédures stockées<br /><br /> -Fonctions<br /><br /> -Packages|**Procédures stockées**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/[SCHEMA]/PollingProcedure">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Fonctions**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/[Schema]/PollingFunction">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Packages**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/[Schema]/PollingPackage/[PACKAGE_NAME]/">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`|La structure de l’ensemble de résultats dans l’opération d’interrogation est déterminée par le type de données des éléments dans l’objet cible.|  
  
 [Version] = http://Microsoft.LobServices.OracleDB/2007/03.  
  
 [CustomPollingOperation] = il est identique à la procédure stockée, la fonction, ou la procédure empaquetée ou la nom de la fonction qui sont exposées en tant que l’opération d’interrogation entrant.  
  
 [Schéma] = nom du schéma Oracle. Par exemple, SCOTT.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)