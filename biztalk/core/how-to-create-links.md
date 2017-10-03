---
title: "Comment créer des liens | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 670b831f-be03-4612-93d5-a894f7bb3c11
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01171ddeaab8424087e8f04c29fb747e9479c1eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-links"></a>Création de liens
Création d’un lien à partir d’un **enregistrement** ou **champ** nœud dans un schéma source et un **enregistrement** ou **champ** nœud dans un schéma de destination est le plus simple activité en créant des cartes. Cette rubrique fournit des instructions détaillées à propos de plusieurs variations de cette opération et notamment concernant la création de liens vers et à partir de fonctoids. Pour plus d’informations sur l’utilisation des fonctoids, voir [à l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md).  
  
 Avant de suivre les instructions de cette rubrique, vous devez avoir déjà ouvert un mappage BizTalk et choisi des schémas source et de destination pour ce dernier. Pour plus d’informations sur l’ouverture de mappages et en choisissant les schémas de la carte, consultez [gestion est mappé au sein de projets](../core/managing-maps-within-projects.md).  
  
### <a name="to-create-links-between-field-and-record-nodes"></a>Pour créer des liens entre des nœuds Champ et Enregistrement  
  
1.  Dans le Mappeur BizTalk, faites glisser un **champ** ou **enregistrement** nœud à partir de l’arborescence du schéma source à un **champ** ou **enregistrement** nœud dans le schéma de destination arborescence.  
  
     **- Ou -**  
  
2.  Dans le Mappeur BizTalk, faites glisser un **champ** ou **enregistrement** nœud à partir de l’arborescence du schéma de destination à un **champ** ou **enregistrement** nœud dans le schéma source arborescence.  
  
 La création de liens suppose la prise en considération de plusieurs aspects :  
  
-   Le type de données d’un **champ** ou **enregistrement** nœud dans l’arborescence du schéma source doit correspondre au type de données d’un **champ** ou **enregistrement** nœud vers lequel il est lié dans l’arborescence de schéma de destination.  
  
-   Si un **champ** ou **enregistrement** nœud dans le schéma source est facultatif et un message d’instance source particulier ne contient pas l’élément ou attribut correspondant, le Mappeur BizTalk ne créera un élément correspondant ou un attribut dans le message d’instance de destination, même si le **champ** ou **enregistrement** nœuds ont un lien direct entre eux dans le mappage.  
  
-   Vous ne pouvez pas lier à un **champ** ou **enregistrement** nœud dans le schéma de destination qui a une valeur de constante associée. En revanche, vous pouvez lier à une valeur obligatoire **champ** ou **enregistrement** nœud dans le schéma de destination qui a une valeur par défaut associée. Sachez toutefois que la valeur par défaut sera utilisée lors du test du mappage.  
  
-   Vous ne pouvez pas créer un lien vers ou depuis le **tout élément**, **tout attribut**, **groupe séquence**, ou **groupe choix** nœuds. Pour plus d’informations sur ces types de nœuds, consultez les rubriques suivantes, consultez [nœuds tout élément](../core/any-element-nodes.md), [nœuds groupe séquence](../core/sequence-group-nodes.md) ou [nœuds groupe choix](../core/choice-group-nodes.md).  
  
-   Vous risquez d'avoir besoin de développer les arborescences de schéma afin de visualiser les champs que vous désirez mapper. Pour plus d’informations, consultez [comment développer et réduire les arborescences de schéma](https://msdn.microsoft.com/library/ee253802(v=bts.10).aspx).  
  
#### <a name="to-create-links-between-record-or-field-nodes-and-functoids"></a>Pour créer des liens entre des nœuds Champ ou Enregistrement et des fonctoids  
  
1.  Dans le Mappeur BizTalk, faites glisser un **enregistrement** ou **champ** nœud à partir du schéma source ou de destination vers un fonctoid dans une page de grille.  
  
     **- Ou -**  
  
2.  Faites glisser le fonctoid à partir d’une page de grille pour un **enregistrement** ou **champ** nœud dans le schéma source ou de destination.  
  
     Lorsque vous créez un lien entre un **enregistrement** ou **champ** nœud dans le schéma source et un fonctoid, vous créez une entrée pour ce fonctoid. Lorsque vous créez un lien entre un **enregistrement** ou **champ** nœud dans le schéma de destination et un fonctoid, vous créez une sortie à partir de ce fonctoid.  
  
    > [!IMPORTANT]
    >  Vous ne pouvez pas lier entre un fonctoid et un **tout élément** nœud ou un **tout attribut** nœud.  
  
    > [!NOTE]
    >  Vous devez d’abord ajouter un fonctoid à une page de grille avant de pouvoir ajouter un lien entre un **enregistrement** ou **champ** nœud et ce fonctoid. Pour plus d’informations sur l’ajout de fonctoids à une page de grille, consultez [comment ajouter des fonctoids à un mappage](../core/how-to-add-basic-functoids-to-a-map.md). Consultez également [Ajout de fonctoids avancés à un mappage](../core/adding-advanced-functoids-to-a-map.md).  
  
    > [!NOTE]
    >  Vous ne pouvez pas lier à un **champ** nœud dans le schéma de destination qui a une valeur de constante associée. En revanche, vous pouvez lier à une valeur obligatoire **champ** nœud dans le schéma de destination qui a une valeur par défaut associée. Sachez toutefois que la valeur par défaut sera utilisée lors du test du mappage.  
  
#### <a name="to-create-links-between-functoids"></a>Pour créer des liens entre des fonctoids  
  
-   Dans le Mappeur BizTalk, faites glisser un fonctoid vers un autre fonctoid dans une page de grille.  
  
    > [!NOTE]
    >  Dans les pages de grille, les liens sont traités de gauche à droite. Il est impossible d'établir un lien entre deux fonctoids directement au-dessus ou au-dessous du premier. Les liens entre fonctoids s'interprètent de la façon suivante : sortie à partir du fonctoid de gauche et entrée vers le fonctoid de droite.  
  
### <a name="to-change-the-endpoint-of-a-link"></a>Pour modifier le point de terminaison d'un lien  
 Dans un mappage, vous pouvez faire glisser le point de terminaison d'un lien et le déposer sur un autre nœud ou fonctoid.  
  
 Pour modifier le point de terminaison d'un lien :  
  
1.  Cliquez sur le lien pour lequel vous voulez modifier le nœud/fonctoid source ou de destination. Les points de terminaison du lien sont affichés en gras.  
  
2.  Maintenez le bouton de la souris enfoncé sur un point de terminaison en gras et faites glisser le lien sur le nœud/fonctoid souhaité. Cette action modifie la liaison entre le nœud/fonctoid précédent et le nouveau nœud/fonctoid.  
  
 Vous ne pouvez toutefois pas effectuer cette opération pour une liaison non valide :  
  
-   ajout d'un lien comme entrée de fonctoids Date/heure. Les fonctoids Date/heure ne requièrent pas de liens d'entrée.  
  
-   duplication de liens à partir de fonctoids intermédiaires.  
  
     Si vous liez le nœud 1 au nœud 2, et le nœud 1 au nœud 3, vous ne pouvez pas faire glisser le point de terminaison du lien au niveau du nœud 2 pour modifier et définir un lien au niveau du nœud 3.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md)