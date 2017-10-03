---
title: "Schémas de message pour l’interrogation Operations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c572c4ec-0a3f-42b8-bebd-40eb584438ad
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee61aa47a7f991c140e0c0659b67da658a11a7ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-polling-operations"></a>Schémas de message pour les opérations d’interrogation
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]met en évidence des différentes opérations entrantes liées à l’interrogation en fonction de l’objet cible dans Oracle E-Business Suite. Pour les tables d’interface, les vues de l’interface, les tables et les vues, une seule opération d’interrogation apparaissent alors que vous pouvez avoir plusieurs opérations d’appel personnalisées pour les API PL/SQL, fonctions et procédures stockées.  
  
 Vous configurez les opérations d’interrogation en définissant des propriétés de liaison dans le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour plus d’informations sur ces propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Vous définissez la **PollingStatement** liaison de propriété pour spécifier une instruction SQL, procédure stockée, fonction ou une procédure dans un package pour la requête d’interrogation. Le jeu de résultats de cette requête est retourné sous forme de données à votre code dans l’opération d’interrogation.  
  
## <a name="message-structure-for-the-polling-operations"></a>Structure du message pour les opérations d’interrogation  
 Le tableau suivant montre la structure de message XML pour les différentes opérations d’interrogation.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Objet cible|Message XML| Description|  
|---------------|-------------------|-----------------|-----------------|  
|Interrogation|-Interface de Tables<br /><br /> : Vues de l’interface<br /><br /> -Tables<br /><br /> -Vues|`<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/[TargetObject]/[Schema]/[TargetObject_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|Par exemple, le message XML pour l’opération d’interrogation sur les Tables d’Interface sera comme suit :<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <Poll xmlns="[Version]/InterfaceTables/[Schema]/[InterfaceTable_Name]">    <DATA>      <SelectRecord>        <Column1>[Value]</Column1>        <Column2>[Value]</Column2>        …        </SelectRecord>    </DATA> </Poll>`|  
|[CustomPollingOperation]|-API PL/SQL<br /><br /> -Procédures stockées<br /><br /> -Fonctions|**API PL/SQL**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingPackageAPis/[Schema]/[PL/SQL API]">    <[CustomPollingOperation]Result>[Value]</[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Fonctions**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?> <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <COL1>[Value]</COL1]>      <COL2>[Value]</COL2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`<br /><br /> **Procédures stockées**<br /><br /> `<?xml version="1.0" encoding="utf-8" ?>  <[CustomPollingOperation] xmlns="[Version]/PollingFunctions/[Schema]">    <[CustomPollingOperation]Result>      <PRM1>[Value]</PRM1>      <PRM2>[Value]</PRM2>      …    </[CustomPollingOperation]Result> </[CustomPollingOperation]>`|La structure de l’ensemble de résultats dans l’opération d’interrogation est déterminée par le type de données des éléments dans l’objet cible.|  
  
 Descriptions de l’entité :  
  
 [Version] = http://schemas.microsoft.com/OracleEBS/2008/05.  
  
 [CustomPollingOperation] = nom de l’opération d’appel personnalisées.  
  
 [Schéma] = nom du schéma Oracle. Par exemple, SCOTT.  
  
 [API PL/SQL] = nom de l’API PL/SQL sur lequel une opération d’interrogation personnalisée est effectuée.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)