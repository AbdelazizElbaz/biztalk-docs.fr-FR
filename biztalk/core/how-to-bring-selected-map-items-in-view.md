---
title: "Comment afficher le mappage sélectionné dans la vue des éléments | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e287b22-5738-428a-aa35-cced877e51ea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1dff8e981b65b6b91c744ce26648a5f4e06adea
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-bring-selected-map-items-in-view"></a>Placement des éléments de mappage sélectionnés dans la vue
Dans les versions précédentes du Mappeur BizTalk, si un mappage incluait de grands schémas, vous deviez faire défiler manuellement le volet du schéma source, la page de grille et le volet du schéma cible pour afficher tous les éléments de mappage appropriés dans une vue unique. Le Mappeur BizTalk dans BizTalk Server vous permet de mettre tous les éléments de mappage appropriés du fonctoid/lien sélectionné dans une vue unique en faisant défiler automatiquement de la page de grille. Cette rubrique fournit des informations sur l'exécution de cette opération.  
  
 En fonction de votre sélection (un nœud de schéma source, un élément dans la vue de relation ou un nœud de schéma cible), le Mappeur BizTalk fait défiler automatiquement les vues de schéma et de relation de manière synchronisée, tout en affichant la vue de l'ensemble des relations de l'élément sélectionné.  
  
> [!NOTE]
>  La fonctionnalité de défilement automatique est activée après que le Mappeur BizTalk ait mis en surbrillance tous les éléments de mappage appropriés. En d'autres termes, les éléments associés à la sélection sont d'abord mis en surbrillance, puis le Mappeur BizTalk utilise le défilement automatique pour placer les éléments associés dans la vue.  
  
 Le Mappeur BizTalk ne déplace pas réellement les objets de la grille. Ceux-ci retrouvent leurs emplacements respectifs lorsque vous supprimez ou modifiez la sélection.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Cette opération nécessite l'exécution du Mappeur BizTalk.  
  
### <a name="to-bring-the-selected-map-items-in-view"></a>Pour placer les éléments de mappage sélectionnés dans la vue  
  
1.  Sur le ruban de l’utilitaire mappeur, cliquez sur l’icône de défilement automatique ![automatique &#45; icône de défilement](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") à désactiver.  
  
    > [!NOTE]
    >  Le ![automatique &#45; icône de défilement](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") icône est activée (OFF) par défaut.  
  
2.  Cliquez sur un fonctoid ou un lien. Les éléments de mappage appropriés sont mis en surbrillance.  
  
     La figure suivante affiche le lien sélectionné en bleu. À son tour, le Mappeur BizTalk met en surbrillance les autres éléments de mappage appropriés de la sélection, en vert. Dans la figure, vous pouvez voir que tous les éléments de la relation sélectionnée, bien que mis en surbrillance, ne figurent pas entièrement dans la vue active.  
  
     ![Liens lorsque automatique &#45; le défilement est mis hors tension](../core/media/autoscroll-switchoff.gif "AutoScroll_SwitchOff")  
  
3.  Cliquez sur l’icône de défilement automatique ![automatique &#45; icône de défilement](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") à sa mise sous tension.  
  
     Le Mappeur BizTalk utilise le défilement automatique pour placer tous les éléments appropriés dans la vue de mappage active.  
  
     ![Afficher lorsque le défilement automatique est allumé](../core/media/autoscroll-switchon.gif "AutoScroll_SwitchOn")  
  
    > [!NOTE]
    >  Vous pouvez également utiliser les combinaisons de touches CTRL+M, CTRL+U. Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)