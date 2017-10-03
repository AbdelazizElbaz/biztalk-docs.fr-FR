---
title: "Correspondance au niveau de hiérarchie de nœuds | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Field nodes
- BizTalk Mapper, processing
- Record node
- BizTalk Mapper, compiler directives
- destination schemas, matching nodes
- source schemas, matching nodes
- maps, links
- Target Links property
- BizTalk Mapper, links
- compiler directives, matching schema nodes
- compiler directives, flattening source hierarchies
- maps, processing
ms.assetid: 5ba1ac77-0e70-4c58-9b8c-1b379dbbb3bd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b2d0c363abfefb9e3d0eb8abfb332c59539bb67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="node-hierarchy-level-matching"></a>Correspondance au niveau de la hiérarchie de nœuds
Le Mappeur BizTalk vous permet de configurer une propriété de lien pour contrôler la manière dont le compilateur fait correspondre les hiérarchies de nœuds entre les schémas source et de destination. Lorsque vous créez un lien entre un champ du schéma source et un champ du schéma de destination, le Mappeur BizTalk ajoute automatiquement des liens de compilateur. Ces liens de compilateur dépendent de la correspondance que vous sélectionnez.  
  
 Lorsque vous sélectionnez un lien dans la page de grille affichée, une des propriétés affichées dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés est le **liaisons cibles** propriété. Vous avez le choix entre les valeurs suivantes pour chaque lien de votre mappage :  
  
-   **Liaisons aplaties.** utilisez cette valeur pour mettre à plat toutes les hiérarchies sources au niveau de l'enregistrement parent dans le nœud du schéma de destination.  
  
-   **Correspondance descendante des liaisons.** utilisez cette valeur pour faire correspondre les niveaux de nœud du haut vers le bas dans les schémas.  
  
-   **Correspondance ascendante des liaisons.** utilisez cette valeur pour faire correspondre les niveaux de nœud du bas vers le haut dans les schémas.  
  
## <a name="flatten-links"></a>Liaisons aplaties  
 Dans ce mode, toutes les hiérarchies sources sont mises à plat au niveau de l'enregistrement parent du nœud de destination. Dans le premier cas, le schéma source est plus complexe que le schéma de destination. Dans le second cas, le schéma de destination est plus complexe.  
  
 ![](../core/media/bts-tls-flatten.gif "bts_tls_flatten")  
Liaisons aplaties  
  
 ![](../core/media/bts-tls-flatten-2.gif "bts_tls_flatten_2")  
Liaisons aplaties, second cas  
  
## <a name="match-links-top-down"></a>Correspondance descendante des liaisons :  
 Ce mode établit des correspondances niveau par niveau de façon descendante. Dans le premier cas, le schéma source est plus complexe que le schéma de destination. Dans le second cas, le schéma de destination est plus complexe.  
  
 ![](../core/media/bts-tls-topdown.gif "bts_tls_topdown")  
Correspondance descendante  
  
 ![](../core/media/bts-tls-topdown-2.gif "bts_tls_topdown_2")  
Correspondance descendante, second cas  
  
## <a name="match-links-bottom-up"></a>Correspondance ascendante des liaisons  
 Ce mode établit des correspondances niveau par niveau de façon ascendante. Dans le premier cas, le schéma source est plus complexe que le schéma de destination. Dans le second cas, le schéma de destination est plus complexe.  
  
 ![](../core/media/bts-tls-bottomup.gif "bts_tls_bottomup")  
Correspondance ascendante  
  
 ![](../core/media/bts-tls-bottomup-2.gif "bts_tls_bottomup_2")  
Correspondance ascendante, second cas  
  
## <a name="how-biztalk-mapper-processes-link-types"></a>Traitement des types de liens par le Mappeur BizTalk  
 Étant donné que vous pouvez définir le **liaisons cibles** propriété des valeurs différentes pour différents liens, le Mappeur BizTalk doit pouvoir résoudre les divers paramètres lorsqu’ils peuvent entrer en conflit.  
  
 Par exemple, si vous utilisez une directive de compilation aplatie, une directive de compilation de haut en bas et une directive de compilation de bas en haut des liens à partir **champ** nœuds **champ** nœuds dans le schéma de destination et ces nœuds partagent le même parent **enregistrement** nœud, le Mappeur BizTalk ignore les directives de compilateur descendant et ascendant en conflit et traite tous les liens comme s’ils étaient définis sur la directive de compilation aplanie.  
  
 Le tableau suivant montre comment le Mappeur BizTalk traite des liens vers des **champ** nœuds dans la même **enregistrement** nœud dans le schéma de destination, basé sur les paramètres pour le **liaisons cibles** propriété pour les liens au sein du même **enregistrement** nœud.  
  
|Mise à plat|Descendant|Ascendant|Résultat|  
|-------------|---------------|----------------|------------|  
|0 ou plus|1 ou plus|1 ou plus|Le Mappeur BizTalk traite tous les liens comme s'ils étaient définis sur la directive de compilateur de mise à plat.|  
|1 ou plus|1 ou plus|0|Le Mappeur BizTalk traite tous les liens comme s'ils étaient définis sur la directive de compilateur descendant.|  
|1 ou plus|0|1 ou plus|Le Mappeur BizTalk traite tous les liens comme s'ils étaient définis sur la directive de compilateur ascendant.|  
  
 Les directives de compilateur descendant et ascendant ont priorité sur la directive de compilateur de mise à plat, mais s'annulent l'une l'autre lorsqu'elles coexistent.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctoid copie de masse](../core/mass-copy-functoid.md)   
 [Comment définir la valeur du compilateur Source de liens](../core/how-to-set-the-source-links-compiler-value.md)   
 [Compilation des mappages](../core/compiling-maps.md)