---
title: "Comment ajouter des fonctoids de mappage à un mappage de valeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc70067a-67a1-4a0e-95e5-b0cb327d2cee
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e463489332c3a1d2887dab5f7bd734fdd20af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-value-mapping-functoids-to-a-map"></a>Ajout de fonctoids de mappage des valeurs à un mappage
Le **mappage** fonctoid retourne la valeur de son deuxième paramètre si son premier paramètre a la valeur true. Un fonctoid sert souvent à modifier les attributs d'un champ en attributs d'un enregistrement.  
  
 Pour obtenir des informations conceptuelles sur le **mappage** fonctoid, consultez [fonctoid Mappage des valeurs](../core/value-mapping-functoid.md).  
  
### <a name="to-add-the-value-mapping-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Mappage des valeurs à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **mappage** fonctoid (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour établir le premier paramètre d’entrée pour le **mappage des valeurs** fonctoid, créer un lien d’entrée en faisant glisser le **mappage** fonctoid à un nœud enregistrement ou de champ dans le schéma source ou à un autre fonctoid pour de gauche, qui possède un type de données booléen et qui produira une valeur d’entrée « true » ou « false ».  
  
    > [!NOTE]
    >  Vous pouvez également faire glisser dans la direction opposée, en faisant glisser la source de la valeur booléenne à la **mappage** fonctoid.  
  
4.  Pour établir le deuxième paramètre d’entrée pour le **mappage des valeurs** fonctoid, créer un lien d’entrée en faisant glisser le **mappage** fonctoid vers un nœud enregistrement ou de champ du schéma source, ou en faisant glisser un enregistrement ou nœud de champ dans le schéma source vers le **mappage** fonctoid.  
  
    > [!NOTE]
    >  La deuxième entrée de paramètre à la **mappage** fonctoid peut également être à partir de la sortie d’un autre fonctoid situé à sa gauche. Créez les liens qui représentent ces sources d'entrée en faisant glisser un des fonctoids appropriés vers l'autre fonctoid approprié.  
  
5.  Pour utiliser le paramètre de sortie à partir de la **mappage des valeurs** fonctoid, créez un lien de sortie en faisant glisser le **mappage des valeurs** fonctoid vers un enregistrement ou un champ du schéma de destination, ou en faisant glisser un champ d’enregistrement le schéma de destination le **mappage** fonctoid.  
  
    > [!NOTE]
    >  Comme avec d’autres fonctoids, la sortie de la **mappage** fonctoid peut servir d’entrée à un autre fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)