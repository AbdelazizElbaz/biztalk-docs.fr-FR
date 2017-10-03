---
title: Types de liens | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compiler directives, links
- elastic links [maps]
- maps, links
- BizTalk Mapper, links
- partial links [maps]
- fixed links [maps]
ms.assetid: 348fae77-2e25-4b79-93bb-d42f3d18a3f7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d6f1039e65989a2de0243a1a9a09f30165e603
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="types-of-links"></a>Types de liens
Voici une liste des différents types de liens disponibles dans le Mappeur BizTalk :  
  
-   **Liaisons souples.** le terme « souple » s’applique à un lien en cours de création, avant que les deux terminaisons du lien ne soient connectées. Par exemple, si vous faites glisser un lien depuis un champ d'un schéma source, mais que vous ne l'avez pas encore connecté à son champ correspondant dans le schéma de destination, le lien est souple. La connexion achevée, la liaison souple devient liaison fixe.  
  
     Vous pouvez déplacer un point de terminaison de liaison vers un autre nœud ou fonctoid. Pour plus d’informations sur le remplacement de lien, consultez [comment créer des liens](../core/how-to-create-links.md).  
  
-   **Liaisons fixes.** le terme « fixe » s'applique à un lien que vous avez explicitement construit pour représenter le mouvement d'une valeur entre un message d'instance source et un message d'instance de destination, ou au moins une partie du mouvement. Liens fixes qui sont directement connectés un **enregistrement** ou **champ** nœud dans le schéma source vers un **enregistrement** ou **champ** nœud dans la destination schéma représente une copie directe des données en cours d’exécution. Les liaisons fixes qui effectuent une connexion à l'une des extrémités d'un fonctoid représentent une partie du mouvement des données entre un message d’instance d’entrée et un message d’instance de sortie au moment de l’exécution. Plusieurs de ces liaisons, achevant le lien entre les schémas source et de destination, représentent l'ensemble du mouvement d'un élément de donnée.  
  
-   **Liaisons partielles.** Le terme « partiel » s’applique aux liens pour lesquelles vous ne pouvez pas actuellement voir exactement **enregistrement** ou **champ** nœud auquel elles sont connectées dans les schémas source et de destination. Cela se produit lorsque le **enregistrement** ou **champ** nœud auquel elles sont attachées n’est pas affiché, car un de ses nœuds ancêtres est réduit dans la représentation sous forme de l’arborescence du schéma. Pour plus d’informations sur les liaisons partielles, consultez [comment optimiser l’affichage de liens](../core/how-to-optimize-the-display-of-links.md).  
  
-   **Liaisons du compilateur.** le terme « compilateur » s'applique aux liens que le Mappeur BizTalk crée automatiquement lorsque vous générez un projet BizTalk. Par exemple, si vous configurez un bouclage piloté par la table, les liaisons du compilateur affichent la relation et les liens existant entre les enregistrements et les champs du schéma source et les enregistrements et les champs du schéma de destination. Ce type de lien peut être généré automatiquement par des directives de compilateur ; il peut également être dirigé par l’utilisateur.  
  
 Par défaut, le Mappeur BizTalk affiche ces différents types de liens dans différentes couleurs de ligne pour vous aider à distinguer plus facilement les détails de vos mappages. Vous pouvez modifier les couleurs utilisées pour ces différents types de liens avec la **Options** commande sur le **outils** menu. Pour plus d’informations sur la modification de la couleur du rendu de différentes catégories de liens, consultez [comment personnaliser les couleurs et la police dans le Mappeur BizTalk](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)