---
title: "Comment configurer les paramètres d’entrée du fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bts10.mapper.functoid.inputs
ms.assetid: 2c8f773a-932c-423d-b3fe-724265304b0a
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab04111835e7732aa8384e1d701a15ae8d268378
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-functoid-input-parameters"></a>Configuration des paramètres d’entrée de fonctoid
La configuration des paramètres d'entrée des fonctoids de votre mappage est un des aspects les plus importants (et les plus sujets aux erreurs) de l'utilisation des fonctoids. Vous pouvez configurer ces paramètres comme suit :  
  
-   Créer des liens d’entrée visibles par les nœuds de schéma qui se connecte et les fonctoids correspondants (glisser-déplacer la souris à partir d’un nœud de schéma pour le fonctoid).  
  
-   Modifier directement la liste des paramètres d’entrée à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue.  
  
 Cette rubrique fournit des instructions étape par étape pour configurer les paramètres d'entrée d'un fonctoid à l'aide de ces deux méthodes.  
  
 L'opération de glisser-déposer utilisée pour définir les paramètres d'entrée de fonctoid constitue une méthode pratique pour spécifier les paramètres d'entrée comportant des spécifications XPath dans le schéma source. Pour plus d’informations sur la création d’un schéma de paramètres d’entrée de fonctoid et de nœud, consultez [comment ajouter des fonctoids à un mappage](../core/how-to-add-basic-functoids-to-a-map.md). Toutefois, le **configurer \<fonctoid\> fonctoid** boîte de dialogue est le mécanisme par excellence pour afficher tous les paramètres d’entrée d’un fonctoid, pour créer et modifier tous les paramètres constants et pour réorganiser l’ordre des paramètres d’entrée lorsque cela est nécessaire.  
  
 Lorsque vous configurez les paramètres d'entrée d'un fonctoid directement sur la page de grille (en dessinant des lignes, via une opération de glisser-déposer à l'aide de la souris, en partant du nœud du schéma et en reliant celui-ci au fonctoid) et si le nombre d'entrées atteint sa limite, le pointeur change d'état pour indiquer que l'action est impossible. La barre d'état affiche également le motif. La figure ci-dessous illustre un fonctoid qui accepte un seul lien d'entrée.  
  
 ![AUCUN état de configuration du paramètre d’entrée du fonctoid](../core/media/configure-input-parameters-no-state.gif "Configure_input_parameters_NO_state")  
  
 Vous pouvez configurer les fonctoids de script et bouclage de Table à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue. Pour plus d’informations sur la façon de configurer les fonctoids, consultez [comment configurer le fonctoid script](../core/how-to-configure-the-scripting-functoid.md) et [la configuration de bouclage de Table et de fonctoids Extracteur de Table](../core/how-to-configure-the-table-looping-and-table-extractor-functoids.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
## <a name="what-is-an-input-parameter"></a>Qu'est ce qu'un paramètre d'entrée ?  
 Un paramètre d'entrée peut prendre n'importe laquelle des formes suivantes :  
  
-   un lien partant du nœud du schéma source et se dirigeant vers un fonctoid ;  
  
-   un lien partant d'un fonctoid et se dirigeant vers un autre fonctoid valide ;  
  
-   une valeur constante.  
  
> [!NOTE]
>  Il existe quelques fonctoids, tels que **Date**, **temps**, **Date et heure**, et **Nil**, ne requièrent aucun paramètre d’entrée.  
  
 La figure ci-dessous illustre un fonctoid (l'élément mis en surbrillance en rouge) qui dispose de deux paramètres d'entrée (Input[0] et Input[1]) et d'un paramètre constant (Input[2]).  
  
 ![Afficher les paramètres d’entrée d’un fonctoid](../core/media/identifying-input-parameters.gif "Identifying_input_parameters")  
  
## <a name="to-open-the-configure-functoid-functoid-dialog-box"></a>Pour ouvrir la page Configurer \<fonctoid\> boîte de dialogue fonctoid  
 Vous pouvez ouvrir le **configurer \<fonctoid\> fonctoid** boîte de dialogue de l’une des manières suivantes :  
  
-   Dans la page de grille correspondante, cliquez sur le fonctoid, puis cliquez sur **configurer les entrées de fonctoid**.  
  
-   Double-cliquez sur le fonctoid pour lequel vous souhaitez configurer les paramètres d'entrée.  
  
-   Sélectionnez le fonctoid, puis cliquez sur le bouton de sélection (**...** ) dans Visual Studio **propriétés** fenêtre.  
  
-   Sélectionnez le fonctoid, puis appuyez sur la touche Entrée du clavier.  
  
-   Sélectionnez le fonctoid, puis appuyez sur les touches CTRL+M, CTRL+I du clavier. Pour obtenir la liste des touches de raccourci du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
### <a name="to-insert-constant-input-parameters"></a>Pour insérer des paramètres d'entrée constants  
  
1.  Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, sélectionnez le **les entrées de fonctoid** onglet.  
  
    > [!NOTE]
    >  Le **les entrées de fonctoid** onglet est sélectionné par défaut.  
  
2.  Cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") bouton. Une nouvelle ligne est ajoutée.  
  
3.  La valeur du nouveau paramètre d’entrée, puis tapez **OK**.  
  
    > [!NOTE]
    >  Si le bouton d'ajout n'est pas activé, le fonctoid n'accepte ou n'exige aucun paramètre d'entrée, ou celui-ci a atteint le nombre maximal d'entrées autorisées.  
  
### <a name="to-edit-existing-constant-input-parameters"></a>Pour modifier des paramètres d'entrée constants  
  
1.  Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur la constante existante d’entrée de paramètre que vous souhaitez modifier. La valeur actuelle est sélectionnée.  
  
    > [!IMPORTANT]
    >  Vous pouvez uniquement modifier les paramètres d'entrées constantes. Il est impossible de modifier les paramètres d'entrée de tout autre type. Vous ne pouvez que les réorganiser ou les supprimer.  
  
2.  Cliquez sur le ![modification des paramètres d’entrée constants](../core/media/edit-input-parameters.gif "Edit_input_parameters") bouton. Apportez les modifications appropriées à la valeur constante, puis cliquez sur **OK**.  
  
     Vous pouvez également double-cliquer sur le paramètre d'entrée constant pour le modifier ou appuyer sur la touche F2 du clavier.  
  
## <a name="to-select-multiple-input-parameters"></a>Sélection de plusieurs paramètres d'entrée  
 Pour sélectionner plusieurs paramètres d'entrée, maintenez la touche CTRL enfoncée et cliquez sur les lignes souhaitées, puis effectuez l'une des opérations suivantes. Appuyez sur les touches CTRL+A du clavier pour sélectionner toutes les lignes.  
  
-   Déplacez la sélection vers le haut/bas.  
  
    > [!NOTE]
    >  Si la sélection comprend la ligne supérieure ou la ligne inférieure, vous ne pouvez pas déplacer la sélection vers le haut/bas respectivement.  
  
-   Réorganisez la sélection.  
  
-   Supprimez la sélection.  
  
### <a name="to-change-the-order-of-existing-input-parameters"></a>Pour modifier l’ordre des paramètres d’entrée existants  
  
1.  Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur existant d’entrée de paramètre que vous souhaitez déplacer vers un autre emplacement dans la liste des paramètres d’entrée.  
  
2.  Cliquez sur le ![déplacer vers le haut dans la liste](../core/media/move-up-button.gif "Move_up_button") bouton pour déplacer le paramètre vers le haut dans la liste de paramètres. Répétez l'opération jusqu'à ce que le paramètre d'entrée sélectionné se trouve à la position souhaitée. Vous pouvez également appuyer sur la flèche HAUT du clavier. Pour obtenir la liste des touches de raccourci du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
     -OU-  
  
     Cliquez sur le ![déplacement vers le bas dans une liste](../core/media/move-down-button.gif "Move_down_button") bouton Déplacer le paramètre vers le bas dans la liste de paramètres. Répétez l'opération jusqu'à ce que le paramètre d'entrée sélectionné se trouve à la position souhaitée. Vous pouvez également appuyer sur la flèche BAS du clavier. Pour obtenir la liste des touches de raccourci du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
    > [!IMPORTANT]
    >  Vous pouvez réorganiser la séquence des entrées uniquement dans les **configurer \<fonctoid\> fonctoid** boîte de dialogue. Si vous sélectionnez la ligne supérieure ou inférieure, la ![déplacer vers le haut dans la liste](../core/media/move-up-button.gif "Move_up_button") ou ![déplacement vers le bas dans une liste](../core/media/move-down-button.gif "Move_down_button")boutons sont désactivées, respectivement.  
  
### <a name="to-delete-an-input-parameter-by-deleting-the-input-link"></a>Pour supprimer un paramètre d’entrée en supprimant le lien d’entrée  
  
1.  Dans la page de grille correspondante, cliquez sur le lien d'entrée correspondant au paramètre d'entrée que vous souhaitez supprimer.  
  
2.  Sur le **modifier** menu, cliquez sur **supprimer**.  
  
    > [!NOTE]
    >  Ou bien, vous pouvez appuyer sur la touche SUPPR, ou cliquez sur le lien dans la page de grille correspondante, puis cliquez sur **supprimer** dans le menu contextuel.  
  
    > [!IMPORTANT]
    >  Le lien d'entrée est supprimé sans avertissement. Il est toujours possible d'annuler la suppression si vous n'êtes pas sûr de vouloir réellement le faire. Pour plus d’informations sur les opérations d’annulation/de rétablissement, consultez [comment annuler ou rétablir les opérations utilisateur](../core/how-to-undo-or-redo-user-operations.md).  
  
### <a name="to-delete-existing-input-parameters-within-the-configure-functoid-functoid-dialog-box"></a>Pour supprimer des paramètres d’entrée existants dans la page Configurer \<fonctoid\> boîte de dialogue fonctoid  
  
1.  Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur existant d’entrée de paramètre que vous souhaitez supprimer.  
  
    > [!NOTE]
    >  Vous pouvez supprimer n’importe quel paramètre d'entrée de cette façon, même ceux correspondant à un lien d'entrée.  
  
2.  Cliquez sur le ![suppression de la sélection](../core/media/delete-button.gif "Delete_button") bouton. Le paramètre d'entrée existant sélectionné est supprimé de la liste des paramètres. Cliquez sur **OK**.  
  
     Vous pouvez également sélectionner la ligne à supprimer, puis appuyer sur la touche SUPPR du clavier.  
  
    > [!IMPORTANT]
    >  Le paramètre d'entrée est supprimé sans avertissement. Il est toujours possible d'annuler la suppression si vous n'êtes pas sûr de vouloir réellement le faire. Pour plus d’informations sur les opérations d’annulation/de rétablissement, consultez [comment annuler ou rétablir les opérations utilisateur](../core/how-to-undo-or-redo-user-operations.md).  
  
    > [!NOTE]
    >  Le bouton de suppression n'est pas activé tant qu'il n'existe pas de paramètres d'entrée dans la liste des paramètres.  
  
## <a name="to-set-labels-and-comments-for-functoids"></a>Pour définir des étiquettes et des commentaires pour les fonctoids  
 Vous pouvez définir des étiquettes et des commentaires à l’aide des fonctoids le **configurer \<fonctoid\> fonctoid** boîte de dialogue.  
  
1.  Dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, cliquez sur le **étiquette et commentaires** onglet.  
  
2.  Type de la **étiquette** et **commentaires**, puis cliquez sur **OK**.  
  
    > [!IMPORTANT]
    >  Pour plus d’informations sur l’étiquette et commentaires aux fonctoids et/ou liens, consultez [l’étiquette à un lien](../core/how-to-label-a-link.md) et [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modification des propriétés et paramètres d’entrée de fonctoid](../core/editing-functoid-properties-and-input-parameters.md)