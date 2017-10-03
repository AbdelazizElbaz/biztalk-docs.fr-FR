---
title: "Comment ajouter des fonctoids bouclage à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b24051b7-3e79-4a49-8249-a057c048ddae
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa380b4a92de685ad8dc19c27a98f6578d12dc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-looping-functoids-to-a-map"></a>Ajout de fonctoids Bouclage à un mappage

## <a name="overview"></a>Vue d'ensemble
Le **bouclage** fonctoid combine plusieurs enregistrements ou champs du schéma source en un enregistrement unique dans le schéma de destination.  
  
 Pour obtenir des informations conceptuelles sur le **bouclage** fonctoid, consultez [fonctoid Bouclage](../core/looping-functoid.md).  
  
 Sous certaines conditions, certains fonctoids peuvent ne pas fonctionner comme prévu lorsqu’ils sont utilisés dans un mappage avec un **bouclage** fonctoid. Si un tel fonctoid remplit les conditions suivantes, il ne produit pas les résultats attendus :  
  
-   Plusieurs liens d'entrée sont associés au fonctoid.  
  
-   Deux ou plusieurs des liens d’entrée de fonctoid sont liés aux champs enfants des enregistrements d’entrée pour le **bouclage** fonctoid, où les champs enfants ne sont pas frères.  
  
-   Le fonctoid possède un lien de sortie qui est lié à un champ enfant de l’enregistrement de la sortie de la **bouclage** fonctoid.  
  
## <a name="add-the-looping-functoid-to-a-map-and-configure-it"></a>Ajouter le fonctoid Bouclage à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **bouclage** fonctoid à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
     ![](../core/media/bts-tls-looping.gif "bts_tls_looping")  
Fonctoid Bouclage  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
    > 
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour établir les paramètres d’entrée pour le **bouclage** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement ou champ du schéma source vers le **bouclage** fonctoid, ou en faisant glisser le **bouclage**  fonctoid vers un enregistrement ou un champ du schéma source. Répétez que nécessaire pour inclure tous les enregistrements d’entrée pertinents à la **bouclage** fonctoid.  
  
4.  Pour utiliser le paramètre de sortie à partir de la **bouclage** fonctoid, créez un lien de sortie en faisant glisser le **bouclage** fonctoid vers un enregistrement ou un champ du schéma de destination, ou en faisant glisser un enregistrement ou un champ dans le schéma de destination pour le **bouclage** fonctoid.  
  
    > [!NOTE]
    >  Contrairement à beaucoup d’autres fonctoids, la sortie de la **bouclage** fonctoid ne peut être lié à un élément du schéma de destination.  
  
## <a name="see-also"></a>Voir aussi  
-  [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)   
-  **Référence du fonctoid de bouclage**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]