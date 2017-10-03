---
title: "Ajout de fonctoids copie de masse à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cff63fc-8f34-4bd0-8501-a8401bde6349
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cee6f2c53bbd3b3dbabe55f0160309532d0ebf3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-mass-copy-functoids-to-a-map"></a>Ajout de fonctoids Copie de masse à un mappage
Le **copie de masse** fonctoid permet d’utiliser les schémas incluant vos mappages **tout** et **anyAttribute** éléments. Ces éléments sont, par essence, des caractères génériques fournis par le langage de définition du schéma XML pour remplacer des structures ou ensembles d'attributs non connus.  
  
 Pour obtenir des informations conceptuelles sur le **copie de masse** fonctoid, consultez [fonctoid copie de masse](../core/mass-copy-functoid.md).  
  
### <a name="to-add-the-mass-copy-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Copie de masse à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **copie de masse** fonctoid (![](../core/media/advmasscopy.gif "advmasscopy")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour définir le paramètre d’entrée pour le **copie de masse** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement du schéma source vers le **copie de masse** fonctoid, ou en faisant glisser le **copie de masse** fonctoid vers un enregistrement dans le schéma source.  
  
4.  Pour utiliser le paramètre de sortie à partir de la **copie de masse** fonctoid, créez un lien de sortie en faisant glisser le **copie de masse** fonctoid vers un enregistrement dans le schéma de destination, ou en faisant glisser un enregistrement dans le schéma de destination le **copie de masse** fonctoid.  
  
    > [!NOTE]
    >  Contrairement à d’autres fonctoids, vous ne pouvez pas utiliser la sortie de la **copie de masse** fonctoid comme entrée d’un autre fonctoid.  
  
> [!NOTE]
>  Vous pouvez insérer et configurer le **copie de masse** fonctoid en liant deux enregistrements directement. Pour plus d’informations, consultez la section « pour lier à l’aide d’un fonctoid copie de masse » dans [comment lier des enregistrements automatiquement](../core/how-to-link-records-automatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)