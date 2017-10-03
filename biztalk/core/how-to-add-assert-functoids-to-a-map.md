---
title: "Comment ajouter des fonctoids déclarer à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccdd79a2-b70f-489b-8711-e00a50d8e2d8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 553daa0c6e97d09e8284d2369e801c5d2ff8beee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-assert-functoids-to-a-map"></a>Ajout de fonctoids Déclarer à un mappage
Le **Assert** fonctoid permet de tester vos hypothèses sur les conditions de votre mappage. Par exemple, si vous effectuez des calculs pour déterminer une remise supplémentaire sur les achats de produits, vous pouvez déclarer que la remise supplémentaire soit pas plus de 100 $ à l’aide d’un fonctoid logique (**supérieur à** ou  **Less than**).  
  
> [!NOTE]
>  Le **Assert** fonctoid se déclenche uniquement dans les versions de développement ou lorsque le **générer des informations de débogage** dans les paramètres de génération de projet est définie sur **True**. Lorsque votre application BizTalk est compilée pour le déploiement et la **générer des informations de débogage** est définie sur **False** (la valeur par défaut), déclarations sont ignorées.  
  
 Pour obtenir des informations conceptuelles sur le **Assert** fonctoid, consultez [déclarer un fonctoid](../core/assert-functoid.md).  
  
## <a name="add-the-assert-functoid-to-a-map-and-configure-it"></a>Ajouter le fonctoid déclarer à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids. La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **Assert** fonctoid (![fonctoid déclarer](../core/media/advanced-assert-functoid.gif "advanced_assert_functoid")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page. 
    >    
    >  Si vous construisez un mappage impliquant plusieurs fonctoids, vous devez tenir compte de leur placement relatif de gauche à droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Le fonctoid doit posséder exactement trois paramètres d'entrée et génère un unique paramètre de sortie. Pour établir le premier paramètre pour le **Assert** fonctoid, créez un lien d’entrée en faisant glisser la sortie à partir d’autres **logiques** fonctoid ou à partir d’un champ de variable booléen dans le message d’instance d’entrée.  
  
4.  Pour établir le deuxième paramètre d’entrée pour le **Assert** fonctoid, créez un lien d’entrée en un nœud de champ du schéma source vers le **Assert** fonctoid, ou insérez une constante.  
  
5.  Pour établir le troisième paramètre d’entrée pour le **Assert** fonctoid, créez un lien d’entrée en un nœud de champ du schéma source vers le **Assert** fonctoid, ou insérez une constante.  
  
6.  Pour utiliser le paramètre de sortie à partir de la **Assert** fonctoid, créez un lien de sortie en faisant glisser le **Assert** fonctoid à un champ dans le schéma de destination.  
  
    > [!NOTE]
    >  Comme avec d’autres fonctoids, la sortie de la **Assert** fonctoid peut être utilisé comme entrée d’un autre fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
-  **Référence du fonctoid déclarer**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)