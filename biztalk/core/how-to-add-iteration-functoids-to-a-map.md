---
title: "Ajout de fonctoids itération à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eaea929-e352-447d-b119-bd69b6b24e6c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2df7cda082a9a85e54e1dce427d73ea15d8f920
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-iteration-functoids-to-a-map"></a>Ajout de fonctoids Itération à un mappage
Le **itération** fonctoid sorties commençant à 1 pour le premier enregistrement, 2 pour le deuxième enregistrement de la structure de l’index de l’enregistrement actif dans une boucle et ainsi de suite.  
  
 Pour obtenir des informations conceptuelles sur le **itération** fonctoid, consultez [fonctoid itération](../core/iteration-functoid.md).  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Index à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **Index** fonctoid (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour établir le paramètre d’entrée d’enregistrement en boucle pour le **itération** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement de boucle du schéma source vers le **itération** fonctoid, ou en faisant glisser le  **Itération** fonctoid vers un enregistrement de boucle dans le schéma source.  
  
4.  Pour utiliser le paramètre de sortie à partir de la **itération** fonctoid, créez un lien de sortie en faisant glisser le **itération** fonctoid à un champ du schéma de destination, ou en faisant glisser un champ dans le schéma de destination le **itération** fonctoid.  
  
    > [!NOTE]
    >  Le type de données du champ correspondant dans le schéma de destination doit être numérique ou convertible en numérique afin qu’il corresponde au type de données de sortie de la **itération** fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)