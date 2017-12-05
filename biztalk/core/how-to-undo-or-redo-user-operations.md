---
title: "Comment annuler ou rétablir les opérations de l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cb3708e-a9c2-4795-aba0-9c6d9635e08c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8358fc1624346b90d98fd1f1707dd2bfb02446dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-undo-or-redo-user-operations"></a>Annulation ou rétablissement des opérations de l'utilisateur
La prise en charge des options Annuler/Rétablir constitue une aide précieuse fournie par le Mappeur BizTalk. Si vous n'êtes pas satisfait des modifications effectuées, ou si vous avez apporté une modification par erreur, vous pouvez utiliser l'option Annuler pour revenir à un état antérieur à partir duquel vous reprendrez l'opération. L'option Rétablir permet de réappliquer les actions de modification que vous avez annulées. Cette rubrique fournit des informations sur les opérations que vous pouvez annuler/rétablir.  
  
> [!IMPORTANT]
>  Vous pouvez annuler une opération lorsque vous avez apporté au moins une modification au mappage. L'option Rétablir n'est disponible que si vous avez utilisé la commande Annuler.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
## <a name="what-can-you-undoredo"></a>Opérations qu'il est possible d'annuler/rétablir  
 Vous pouvez annuler/rétablir toutes les opérations de modification, à savoir :  
  
-   Couper/copier/coller des fonctoids et/ou des liens  
  
     Il ne suffit pas de sélectionner et de copier des éléments (liens/fonctoids) pour les annuler et les rétablir. La fonction de copie ne change rien au mappage.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de couper/copier/coller un fonctoid, consultez [comment copier, couper et coller un fonctoid](../core/how-to-copy-cut-and-paste-a-functoid.md). Pour plus d’informations sur la façon de couper/copier/coller fonctoid et un lien, consultez [comment copier, couper et collez les liens et fonctoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).  
  
-   Lier un nœud source à un nœud cible, un nœud source à un fonctoid, un fonctoid à un autre ou un fonctoid à un nœud cible  
  
-   Supprimer des fonctoids et/ou des liens  
  
-   Déplacer les liens et les fonctoids sélectionnés vers une autre page de la grille  
  
-   Ajouter, déplacer, réorganiser ou supprimer des pages de la grille  
  
    > [!NOTE]
    >  Pour plus d’informations sur l’ajout, déplacement, la réorganisation ou la suppression de pages de grille, consultez [comment réorganiser les Pages de grille](../core/how-to-reorder-grid-pages.md).  
  
-   Sélectionner les schémas source et de destination lors de la création d'un mappage.  
  
-   Remplacer les schémas source et de destination  
  
    > [!NOTE]
    >  Pour plus d’informations sur la façon de remplacer les schémas source et de destination, consultez [comment remplacer les schémas](../core/how-to-replace-schemas.md).  
  
-   Configurer les paramètres d'entrée des fonctoids  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [comment configurer les paramètres d’entrée du fonctoid](../core/how-to-configure-functoid-input-parameters.md).  
  
-   Configurer et modifier les étiquettes des liens  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [étiquette un lien à](../core/how-to-label-a-link.md).  
  
-   Définir/éditer des étiquettes et/ou des commentaires pour les fonctoids  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).  
  
-   Ignorer les propriétés Espaces de noms des liaisons et Priorité des types de scripts pour la grille du Mappeur.  
  
-   Remplacer une liaison en déplaçant l'un de ses points de terminaison d'un nœud ou fonctoid vers un autre nœud ou fonctoid.  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [comment créer des liens](../core/how-to-create-links.md).  
  
-   Exécution de plusieurs modifications dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue, qui est traitée comme une seule opération.  
  
-   Faire glisser des liens et/ou des fonctoids sur la grille du Mappeur.  
  
    > [!NOTE]
    >  Pour plus d’informations, consultez [comment déplacer une relation entre les Pages de grille](../core/how-to-move-a-relationship-between-grid-pages.md).  
  
## <a name="how-can-you-undoredo-any-operation"></a>Annulation et rétablissement d'une opération  
 Vous pouvez annuler/rétablir une opération à l'aide de l'une des méthodes suivantes :  
  
-   À partir de Visual Studio **modifier** menu.  
  
-   En cliquant sur les icônes Annuler et Rétablir de la barre d'outils.  
  
-   En appuyant sur CTRL+Z pour annuler et CTRL+Y pour rétablir.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des pages de grille](../core/working-with-grid-pages.md)