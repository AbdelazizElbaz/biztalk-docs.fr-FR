---
title: "Comment ajouter le mappage de fonctoids (mise à plat) à une carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a447c3-58d0-42ab-a5c4-417ee7800a6b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e5fe3f7b55a5bd5ef532bf2727c60bad2a621c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-value-mapping-flattening-functoids-to-a-map"></a>Ajout de fonctoids de mappage des valeurs (mise à plat) à un mappage
Le **Value Mapping (Flattening)** fonctoid vous permet d’aplatir une partie d’un message d’instance d’entrée en convertissant plusieurs enregistrements en un seul enregistrement. Il s’agit d’une opération courante dans la conversion des catalogues Microsoft Commerce Server.  
  
 Pour obtenir des informations conceptuelles sur le **Value Mapping (Flattening)** fonctoid, consultez [fonctoid Mappage des valeurs (mise à plat)](../core/value-mapping-flattening-functoid.md).  
  
### <a name="to-add-the-value-mapping-flattening-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Mappage des valeurs (mise à plat) à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **Value Mapping (Flattening)** fonctoid (![](../core/media/bts-tls-valmapflat.gif "bts_tls_valmapflat")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour établir le premier paramètre d’entrée pour le **Value Mapping (Flattening)** fonctoid, créez un lien d’entrée en faisant glisser le **Value Mapping (Flattening)** fonctoid à un nœud enregistrement ou de champ dans la source schéma, ou un autre fonctoid situé à sa gauche, qui a un type de données booléen et qui produira une valeur d’entrée « true » ou « false ».  
  
    > [!NOTE]
    >  Vous pouvez également faire glisser dans la direction opposée, en faisant glisser la source de la valeur booléenne à la **Value Mapping (Flattening)** fonctoid.  
  
4.  Pour établir le deuxième paramètre d’entrée pour le **Value Mapping (Flattening)** fonctoid, créez un lien d’entrée en faisant glisser le **Value Mapping (Flattening)** fonctoid à un nœud enregistrement ou de champ dans la source schéma, ou en faisant glisser un nœud enregistrement ou de champ dans le schéma source vers le **Value Mapping (Flattening)** fonctoid, ou insérez une constante.  
  
    > [!NOTE]
    >  La deuxième entrée de paramètre à la **Value Mapping (Flattening)** fonctoid peut également être à partir de la sortie d’un autre fonctoid situé à sa gauche. Créez les liens le représentent ces sources d’entrée en faisant glisser un des fonctoids appropriés pour le fonctoid.  
  
5.  Pour utiliser le paramètre de sortie à partir de la **Value Mapping (Flattening)** fonctoid, créez un lien de sortie en faisant glisser le **Value Mapping (Flattening)** fonctoid vers un enregistrement ou un champ du schéma de destination, ou en en faisant glisser un champ d’enregistrement du schéma de destination pour le **Value Mapping (Flattening)** fonctoid.  
  
    > [!NOTE]
    >  Comme avec d’autres fonctoids, la sortie de la **Value Mapping (Flattening)** fonctoid peut être utilisé comme entrée d’un autre fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)