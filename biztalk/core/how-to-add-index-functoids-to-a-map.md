---
title: "Ajout de fonctoids Index à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbfccfcc-c333-422f-b40b-13ca4152e588
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6695f7830dcc35fbb0100c012cff10fa207f1ae2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-index-functoids-to-a-map"></a>Ajout de fonctoids Index à un mappage
Le **Index** fonctoid vous permet de sélectionner des informations à partir d’un enregistrement spécifique dans une série d’enregistrements de boucle. Chaque **Index** fonctoid sélectionne des informations à partir d’un champ unique.  
  
 Pour obtenir des informations conceptuelles sur le **Index** fonctoid, consultez [fonctoid Index](../core/index-functoid.md).  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a>Pour ajouter le fonctoid Index à un mappage et le configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **Index** fonctoid (![](../core/media/bts-tls-index.gif "bts_tls_index")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette autre page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur emplacement relatif de gauche à droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
3.  Pour définir le paramètre d’entrée de champ pour le **Index** fonctoid, créez un lien d’entrée en faisant glisser un champ d’un enregistrement de boucle du schéma source vers le **Index** fonctoid, ou en faisant glisser le **Index** fonctoid à un champ d’enregistrement de boucle dans le schéma source.  
  
4.  Pour établir au moins un paramètre d’entrée d’index pour la **Index** fonctoid, procédez comme suit :  
  
    1.  Avec la **Index** fonctoid sélectionné, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété dans le **propriétés** fenêtre.  
  
    2.  Dans le **configurer le fonctoid Index** boîte de dialogue, cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") bouton.  
  
    3.  Dans la zone d'édition, tapez le paramètre d'entrée de l'index sous forme de valeur numérique. Répétez l’opération si les valeurs d’index supplémentaires sont nécessaires, puis cliquez sur **OK**.  
  
5.  Pour utiliser le paramètre de sortie à partir de la **Index** fonctoid, créez un lien de sortie en faisant glisser le **Index** fonctoid vers un champ du schéma de destination, ou en faisant glisser un champ du schéma de destination pour le  **Index** fonctoid.  
  
    > [!NOTE]
    >  Comme avec d’autres fonctoids, la sortie de la **Index** fonctoid peut être utilisé comme entrée d’un autre fonctoid.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)