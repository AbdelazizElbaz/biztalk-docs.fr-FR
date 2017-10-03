---
title: "Ajout de fonctoids valeur Nil à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e193ed-fe5c-4b12-aab8-ff2d81fd45e1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cc7d8b0035161b4a2126ace021072ffcd1d17e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-nil-value-functoids-to-a-map"></a>Ajout de fonctoids Valeur nil à un mappage
Le **valeur Nil** fonctoid définit la valeur du nœud de destination à **Nil**.  
  
 Pour obtenir des informations conceptuelles sur le **valeur Nil** fonctoid, consultez [fonctoid valeur Nil](../core/nil-value-functoid.md).  
  
## <a name="add-the-nil-value-functoid-to-a-map-and-configure-it"></a>Ajouter le fonctoid valeur Nil à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids. La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **valeur Nil** fonctoid (![fonctoid valeur Nil](../core/media/advanced-nil-value-functoid.gif "advanced_nil_value_functoid")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
    >
    >  Si vous construisez un mappage impliquant plusieurs fonctoids, vous devez tenir compte de leur placement relatif de gauche à droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Le **valeur Nil** fonctoid peut avoir zéro à un seul des paramètres d’entrée. S’il n’existe aucun paramètre d’entrée pour ce fonctoid, le nœud cible a la valeur **Nil**. Pour définir le paramètre d’entrée pour le **valeur Nil** fonctoid, créez un lien d’entrée en faisant glisser la sortie à partir d’autres **logiques** fonctoid ou à partir d’un champ de variable booléen dans le message d’instance d’entrée.  
  
4.  Pour utiliser le paramètre de sortie à partir de la **valeur Nil** fonctoid, créez un lien de sortie en faisant glisser le **valeur Nil** fonctoid vers un enregistrement ou un champ du schéma de destination.  
  
    > [!NOTE]
    >  Comme avec d’autres fonctoids, la sortie de la **valeur Nil** fonctoid peut être utilisé comme entrée d’un autre fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
-  **Référence du fonctoid Valeur nil**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)