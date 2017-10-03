---
title: "Groupes d’éléments XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XSLT, XSLT variations
- BizTalk Mapper, XSLT variations
- maps, groups
- Choice Group node
- XSD element groups
- XSLT, warnings
ms.assetid: a6ea22cb-6066-480e-8a2a-75fade3e5970
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b850841819ce844a10e407827d02993ce3559bad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xsd-element-groups"></a>Groupes d'éléments XSD
L'utilisation de certaines structures dans un schéma peut créer des variations dans les transformations XSLT (Extensible Stylesheet Language Transformations) générées par le Mappeur BizTalk.  
  
 Cela peut se produire lors de l'inclusion dans le mappage d'un schéma qui définit des groupes d'éléments Séquence, Choix ou Tous. Par exemple, si vous utilisez un schéma qui inclut un **groupe choix** nœud, il est possible de créer un mappage qui requiert au moins deux des enfants de la **groupe choix** nœud s’affichent dans une instance de sortie Message. Dans ce cas, le Mappeur BizTalk affiche un avertissement quand vous compilez le mappage. Cet avertissement signale qu'un seul des champs obligatoires que vous avez mappés peut être renseigné dans la même itération de la boucle parente lors de l'exécution. Le Mappeur BizTalk ne vous signale pas que la logique du mappage est incorrecte.  
  
 Vous pouvez aussi générer des variations dans les transformations XSLT quand les conditions suivantes sont réunies :  
  
-   **Enregistrement A** a un enfant **B d’élément de champ**.  
  
-   **Enregistrement A** et enfant **B d’élément de champ** se produire qu’une seule fois.  
  
-   **Enregistrement A** fait partie d’un **groupe choix** qui se répète.  
  
 Dans ce cas, le Mappeur BizTalk génère des transformations XSLT qui contiennent une logique d'itération pour gérer la possibilité des nombreuses variations des enregistrements sources.  
  
> [!NOTE]
>  Vous devez être explicite concernant les mappages impliquant des groupes. Par exemple, si un schéma de destination contient un **groupe choix** nœud avec des nœuds enfants A et B, il n’est pas valide A et B simultanément dans la même itération de leur groupe parent. Le Mappeur BizTalk ne vous empêche pas de créer des mappages non valides. Par conséquent, vous devez utiliser des fonctoids logiques pour définir des mappages dans lesquels A et B n'apparaissent jamais ensemble.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)