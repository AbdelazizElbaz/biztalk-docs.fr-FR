---
title: "Comment gérer la vue XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3245ebf0-6128-47b4-8e88-ea06ececbc15
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 945f3fc4d8eac3b09279ea774209a9f43a0f6bd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-xsd-view"></a>Gestion de la vue XSD
Tâches de gestion relatives à la vue XSD peuvent être divisés en trois catégories : modifier sa taille, la modification de sa couleur d’arrière-plan et la police et la modification de ses caractéristiques d’actualisation.  
  
 Cette dernière catégorie, concernant les caractéristiques d'actualisation, est particulièrement utile lorsque vous travaillez avec de grands schémas, pour lesquels une actualisation automatique risquerait de provoquer des délais indésirables. Dans ce cas, vous pouvez désactiver l'actualisation automatique (permanente) et procéder manuellement à l'actualisation de la vue XSD lorsque cela est nécessaire.  
  
 Cette rubrique contient des instructions détaillées sur ces tâches.  
  
### <a name="to-make-the-xsd-view-taller-or-shorter"></a>Pour agrandir ou réduire la vue XSD  
  
1.  Déplacez le pointeur de la souris sur le bord inférieur de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition principale, qui affiche le XSD vue-côte à l’arborescence du schéma, jusqu'à ce que le curseur se transforme l’icône de redimensionnement vertical de fenêtre standard.  
  
2.  Cliquez avec le bouton gauche, maintenez-le enfoncé et déplacez le bord de la fenêtre vers le haut ou vers le bas.  
  
     Vous avez redimensionné verticalement la vue XSD en redimensionnant verticalement la fenêtre d'édition principale.  
  
### <a name="to-make-the-xsd-view-wider-or-more-narrow"></a>Pour élargir ou rétrécir la vue XSD  
  
1.  Placez le pointeur de la souris sur le trait séparant les volets de la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], qui sépare la vue XSD de l'arborescence des schémas, jusqu'à ce que le curseur se transforme en icône de redimensionnement horizontal de la fenêtre standard.  
  
2.  Cliquez avec le bouton gauche, maintenez-le enfoncé et déplacez le bord du volet vers la gauche (pour élargir) ou vers la droite (pour rétrécir).  
  
     Vous avez redimensionné horizontalement la vue XSD en modifiant l'espace de la fenêtre d'édition principale consacré à la vue XSD, par rapport à la vue de l’arborescence des schémas.  
  
     Vous pouvez également élargir ou rétrécir la vue XSD en redimensionnant horizontalement la fenêtre d'édition principale.  
  
### <a name="to-change-the-background-color-andor-font-used-by-the-xsd-view"></a>Pour modifier la couleur d'arrière-plan et/ou la police utilisées par la vue XSD  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans le **Options** boîte de dialogue, cliquez sur le dossier de l’Éditeur BizTalk et si nécessaire, développez le **affichage du schéma** catégorie en cliquant sur le signe plus (+) icône.  
  
3.  Modifier la couleur d’arrière-plan et/ou la police en utilisant le sélecteur de couleur déroulant et/ou **police** boîte de dialogue associé à la **couleur d’arrière-plan la vue XSD** et **police de la vue XSD** propriétés, respectivement.  
  
     Accès le **police** boîte de dialogue en utilisant les points de suspension (**...** ) situé à l’extrémité droite de la **police de la vue XSD** zone de valeur de propriété.  
  
### <a name="to-turn-automatic-refresh-of-the-xsd-view-on-and-off"></a>Pour activer ou désactiver l'actualisation automatique de la vue XSD   
  
-   Dans l’Éditeur BizTalk, sous la **XSD** , cliquez sur **désactiver l’actualisation automatique** ou **activer l’actualisation automatique**.  
  
     Lorsque l’actualisation automatique est désactivée, la vue XSD est vide.  
  
    > [!IMPORTANT]
    >  Par défaut, l’actualisation automatique est activée. À mesure que la taille de vos schémas augmente, il devient de plus en plus important pour vous de désactiver la fonction d'actualisation automatique et d'actualiser le schéma manuellement lorsque cela est nécessaire.  
  
### <a name="to-manually-refresh-the-xsd-view"></a>Pour actualiser manuellement la vue XSD  
  
-   Sur le **BizTalk** menu, cliquez sur **actualiser XSD**.  
  
     La vue XSD est mise à jour afin de répercuter toutes les modifications que vous avez apportées à l'arborescence de schéma.  
  
    > [!NOTE]
    >  Vous pouvez également actualiser manuellement la vue XSD en cliquant sur **actualiser XSD** dans le menu contextuel associé à chaque nœud dans l’arborescence du schéma, ou en cliquant sur le **Actualiser** lien ci-dessous le **XSD** onglet dans la vue XSD.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md)