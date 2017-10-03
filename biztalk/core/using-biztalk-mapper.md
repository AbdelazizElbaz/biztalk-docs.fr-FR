---
title: "À l’aide du Mappeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.grid
ms.assetid: 07c69603-ee79-44b2-80b1-6ae4e4c8fb4e
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bf339069f4868aa7c7bff07ae8bdbbb029c5f81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-mapper"></a>Utilisation du Mappeur BizTalk

## <a name="overview"></a>Vue d'ensemble
Le Mappeur BizTalk réside dans le shell [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Certaines fonctionnalités du Mappeur BizTalk reposent sur les éléments de l'interface utilisateur du shell [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Par exemple, vous utilisez la **fichier**, **modifier**, et **vue** menus comme vous le feriez pour d’autres développement dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Informations sur ces fonctionnalités communes sont disponibles à partir de la **aide** menu.  
  
 Le Mappeur BizTalk devient actif lorsque vous ajoutez un nouveau mappage à un projet BizTalk, lorsque vous ouvrez un mappage existant (fichier .btm), ou lorsque vous réactivez un mappage en cliquant sur son onglet principal [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition.  
  
> [!NOTE]
>  Le Mappeur BizTalk enregistre les fichiers de mappage avec le codage de caractères utf-16.  
>
>  Lorsque vous ajoutez un artefact existant à un projet BizTalk, l’action de génération est toujours définie **BtsCompile**. Même lorsque vous renommez un artefact existant, son action de génération est définie à la valeur par défaut **BtsCompile**. C'est pourquoi, lorsque vous ajoutez ou renommez un artefact existant, vous devez définir l'action de création de manière appropriée, selon que vous souhaitiez créer un artefact particulier ou non.  

## <a name="parts-of-the-biztalk-mapper"></a>Parties du Mappeur BizTalk  
 L'illustration suivante affiche les différentes parties du mappeur BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 ![Le Mappeur BizTalk](../core/media/mapper-views.gif "Mapper_Views")  
  
 Les fonctionnalités de chacune de ces vues sont les suivantes :  
  
-   **Visual Studio utilitaire ruban du mappeur.** Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Mappeur fournit un utilitaire ruban pour l’aire de conception les commandes du mappeur. Le ruban fournit des informations relatives au schéma source, un bouton bascule pour une vue Pertinence des schémas source et de destination, un bouton bascule pour afficher ou masquer les liens hors de portée, un bouton bascule pour activer ou désactiver le défilement automatique, un bouton pour afficher un panoramique de la surface du mappeur, des commandes de zoom avant et arrière, ainsi que la zone de texte de recherche. L'illustration suivante représente l'utilitaire Ruban que vous pouvez voir en haut de la page de grille.  
  
     ![Ruban du Mappeur](../core/media/mapper-ribbon.gif "Mapper_Ribbon")  
  
-   **Mode arborescence de schéma source.** Cette vue partage la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] avec la vue de l'arborescence des schémas de destination et la vue Grille.  
  
     Comme son nom l'indique, cette vue affiche le schéma décrivant les messages d’instance constituant la source du mappage. Les liens définissant le mappage vont de l'arborescence du schéma source vers la vue Grille, puis, vers l'arborescence du schéma de destination.  
  
     Pour plus d’informations sur la représentation des schémas BizTalk dans une arborescence de schéma, consultez [représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md).  
  
-   **Vue arborescence des schémas de destination.** Cette vue partage la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] avec la vue d'arborescence des schémas source et la vue Grille.  
  
     Comme son nom l'indique, cette vue affiche le schéma décrivant les messages d'instance constituant la destination du mappage. Les liens définissant le mappage vont vers l'arborescence du schéma de destination à partir de la vue Grille, puis à partir de l'arborescence du schéma source.  
  
     Pour plus d’informations sur la représentation des schémas BizTalk dans une arborescence de schéma, consultez [représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md).  
  
-   **Affichage de grille.** Cette vue partage la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] avec la vue de l'arborescence du schéma source et la vue de l'arborescence du schéma de destination, et se trouve entre ces dernières, la vue de l'arborescence du schéma source à gauche, et celle du schéma de destination à droite.  
  
     Comme son nom l'indique, cette vue joue un rôle critique dans la définition des mappages, car elle contient des liens et des fonctoids qui permettent de contrôler la façon dont les données d'un message d'instance source sont transformées en un message d'instance conforme au schéma de destination.  
  
     La vue Grille peut comporter plusieurs couches, appelées pages de grilles, à l'aide desquelles vous pouvez organiser des mappages complexes en subdivisions logiques. Les pages de grille utilisent généralement plus d’espace que ce qu’elles peuvent afficher en une fois, et plusieurs moyens efficaces sont à votre disposition pour faire défiler une page de grille.  
  
     C'est dans cette vue que vous travaillez pour construire votre mappage.  
  
-   **Fenêtre Visual Studio Toolbox** Vous pouvez utiliser cette vue pour afficher les fonctoids pouvant être utilisés dans les mappages BizTalk, et comme source des opérations glisser-déposer permettant de placer des fonctoids dans une page de grille.  
  
     Les fonctoids affichés dans la boîte à outils sont organisés en catégories. Pour plus d’informations sur les fonctoids disponibles, consultez [fonctoids dans les mappages](../core/functoids-in-maps.md). Consultez également le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
-   **Fenêtre de Visual Studio propriétés.** Vous utilisez cette vue, et les boîtes de dialogue qui y sont associées, pour examiner et définir les propriétés des liens et fonctoids que vous créez pour définir votre mappage.  
  
     Lorsque vous sélectionnez un lien ou un fonctoid dans une page de grille dans l’affichage de grille, sélectionnez un nœud de schéma dans les vues d’arborescence de schéma source ou de destination, ou sélectionnez un mappage dans le **l’Explorateur de solutions** fenêtre ; les propriétés correspondantes de ce lien, fonctoid, nœud de schéma ou mappage apparaissent dans le **propriétés** fenêtre en utilisant les conventions standard de Visual Studio. Par exemple, les propriétés sont groupées en catégories, et peuvent être affichées par catégories ou dans l’ordre alphabétique.  
  
     Pour plus d’informations sur les différents ensembles de propriétés qui sont disponibles pour les liens, fonctoids, nœuds de schéma ou mappage lui-même, consultez le **référence de mappage de propriété** et **référence du schéma de propriété**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
-   **Visual Studio liste des tâches et sortie de windows.** ces vues vous permettent d’examiner les résultats de la validation, de la compilation et du test de vos mappages BizTalk à peu près de la même façon que lors de la compilation du code source et de la génération d'autres types de projets.  
  
 En plus de ces vues, vous pouvez interagir avec plusieurs boîtes de dialogue. Vous ouvrez généralement ces boîtes de dialogue lorsque vous modifiez une propriété complexe telle que les paramètres d'entrée d'un fonctoid.  
  
 Vous utilisez souvent la fenêtre de l’Explorateur de solutions conjointement avec le Mappeur BizTalk. Par exemple, pour créer un nouveau mappage, cliquez sur le projet BizTalk dans le **l’Explorateur de solutions** fenêtre, cliquez sur **ajouter**, cliquez sur **ajouter un nouvel élément**, puis utilisez le  **Ajouter un nouvel élément** boîte de dialogue permet de nommer et de créer un nouveau mappage.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [À l’aide des commandes du Mappeur BizTalk](../core/using-biztalk-mapper-commands.md)  
  
-   [Utilisation des Pages de grille](../core/working-with-grid-pages.md)  
  
-   [Comment gérer les affichages](../core/how-to-manage-views.md)  
  
-   [Comment personnaliser les couleurs et polices dans le Mappeur BizTalk](../core/how-to-customize-colors-and-font-in-biztalk-mapper.md)  
  
-   [Comment développer et réduire les arborescences de schéma](../core/how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees.md)  
  
-   [Comment annuler ou rétablir les opérations de l’utilisateur](../core/how-to-undo-or-redo-user-operations.md)  
  
-   [Comment rechercher des éléments de la carte](../core/how-to-search-for-map-items.md)  
  
-   [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)  
  
-   [Comment afficher des info-bulles](../core/how-to-view-infotip-and-tooltip.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment faire pour optimiser l’affichage des liens](../core/how-to-optimize-the-display-of-links.md)