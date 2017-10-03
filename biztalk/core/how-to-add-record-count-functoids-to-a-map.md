---
title: "Ajout de fonctoids nombre d’enregistrements à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fbfd2a0-fac5-49f1-bcbb-873c287cd278
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd315a637b3efd069361dfa2d780cff179559da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-record-count-functoids-to-a-map"></a>Ajout de fonctoids Nombre d'enregistrements à un mappage
Le **nombre d’enregistrements** fonctoid vous permet de générer le nombre d’occurrences d’un enregistrement dans un message d’instance.  
  
 Pour obtenir des informations conceptuelles sur le **nombre d’enregistrements** fonctoid, consultez [Functoid nombre d’enregistrements](../core/record-count-functoid.md).  
  
### <a name="to-add-the-record-count-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Nombre d’enregistrements à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **nombre d’enregistrements** fonctoid (![](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette autre page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour définir le paramètre d’entrée pour le **nombre d’enregistrements** fonctoid, créez un lien d’entrée en faisant glisser un enregistrement de boucle du schéma source vers le **nombre d’enregistrements** fonctoid, ou en faisant glisser le  **Nombre d’enregistrements** fonctoid vers un enregistrement de boucle dans le schéma source.  
  
4.  Pour utiliser le paramètre de sortie à partir de la **nombre d’enregistrements** fonctoid, créez un lien de sortie en faisant glisser le **nombre d’enregistrements** fonctoid vers un champ du schéma de destination, ou en faisant glisser un champ dans la destination schéma pour le **nombre d’enregistrements** fonctoid.  
  
    > [!NOTE]
    >  Comme avec d’autres fonctoids, la sortie de la **nombre d’enregistrements** fonctoid peut être utilisé comme entrée d’un autre fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)