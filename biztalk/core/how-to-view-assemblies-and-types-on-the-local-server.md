---
title: Comment afficher les assemblys et les Types sur le serveur Local | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ddf6f60-9fef-4997-8b42-24eefd7ab0d1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c0f49559de7c4b1a13982578478cf249520479
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-assemblies-and-types-on-the-local-server"></a>Affichage des assemblys et types sur le serveur local
Vous pouvez utiliser BizTalk Assembly Viewer pour observer tous les assemblys et types BizTalk installés sur le serveur local.  
  
### <a name="to-view-all-biztalk-server-assemblies-installed-in-the-gac"></a>Pour afficher tous les assemblys BizTalk installés dans le GAC  
  
-   Pour ouvrir BizTalk Assembly Viewer, double-cliquez sur **poste**, puis double-cliquez sur **assemblys BizTalk Server**.  
  
     Tous les assemblys BizTalk installés dans le Global Assembly Cache (GAC) sur l'ordinateur apparaissent.  
  
     ![](../core/media/ebiz-deply-asblyvieweropenpage.gif "ebiz_deply_asblyvieweropenpage")  
Page d'ouverture de BizTalk Assembly Viewer  
  
### <a name="to-view-types-attributes-and-references-for-a-biztalk-assembly"></a>Pour afficher les type, les attributs et les références d'un assembly BizTalk  
  
1.  Pour ouvrir BizTalk Assembly Viewer, double-cliquez sur **poste**, puis double-cliquez sur **assemblys BizTalk Server**.  
  
2.  Double-cliquez sur l'assembly approprié.  
  
     Les types de l'assembly BizTalk apparaissent dans le volet de droite. Les attributs et types apparaissent dans le volet de gauche.  
  
     Vous pouvez également accéder à l’emplacement d’installation de l’assembly en cliquant sur le **Codebase** lien dans la partie supérieure gauche du volet de tâches. (Vous ne pouvez pas voir ce lien lorsque l'Explorateur Windows est ouvert en mode Dossiers car le volet des tâches est remplacé par la liste des dossiers.)  
  
### <a name="to-view-the-contents-of-a-type-in-a-biztalk-assembly"></a>Pour afficher le contenu d'un type d'un assembly BizTalk  
  
1.  Pour ouvrir BizTalk Assembly Viewer, double-cliquez sur **poste**, puis double-cliquez sur **assemblys BizTalk Server**.  
  
2.  Double-cliquez sur l'assembly approprié.  
  
3.  Dans le volet de droite, double-cliquez sur le type approprié.  
  
     Le **visionneuse de contenu de Type** fenêtre s’ouvre et la définition XML s’affiche.  
  
### <a name="to-add-a-biztalk-assembly-in-the-gac"></a>Pour ajouter un assembly BizTalk au GAC  
  
1.  Pour ouvrir BizTalk Assembly Viewer, double-cliquez sur **poste**, puis double-cliquez sur **assemblys BizTalk Server**.  
  
2.  Utilisez l'Explorateur Windows pour accéder à l'assembly que vous souhaitez ajouter au GAC.  
  
3.  Faites glisser l'assembly et déposez-le dans BizTalk Assembly Viewer.  
  
     BizTalk Assembly Viewer accepte uniquement les assemblys BizTalk Server. Si vous y déposez un autre type d'assembly, il sera ignoré.  
  
### <a name="to-remove-a-biztalk-assembly-from-the-gac"></a>Pour supprimer un assembly BizTalk du GAC  
  
1.  Pour ouvrir BizTalk Assembly Viewer, double-cliquez sur **poste**, puis double-cliquez sur **assemblys BizTalk Server**.  
  
2.  Avec le bouton droit de l’assembly que vous souhaitez supprimer du GAC, puis cliquez sur **supprimer**.  
  
### <a name="to-search-for-a-type-in-all-biztalk-assemblies"></a>Pour rechercher un type dans tous les assemblys BizTalk  
  
1.  Pour ouvrir BizTalk Assembly Viewer, double-cliquez sur **poste**, puis double-cliquez sur **assemblys BizTalk Server**.  
  
2.  Dans la barre de menus, cliquez sur le **Biz Talk Server Search** icône.  
  
3.  Dans la fenêtre de recherche, spécifiez le type dans le **trouver les Types** liste déroulante.  
  
4.  Dans le **rechercher dans les assemblys BizTalk Server** liste déroulante, sélectionnez les assemblys à rechercher.  
  
5.  Pour restreindre la recherche afin d'inclure uniquement les types référencés par un type spécifié, procédez comme suit :  
  
    1.  Cliquez sur le **critères de recherche avancés** lien.  
  
    2.  Dans le **qui sont référencés par** liste déroulante, sélectionnez le type.  
  
    3.  Cliquez sur **Rechercher**.  
  
         Les types apparaissent dans les résultats de recherche.  
  
         ![](../core/media/ebiz-depl-asblyviewtypes.gif "ebiz_depl_asblyviewtypes")  
Types d'assembly BizTalk  
  
## <a name="see-also"></a>Voir aussi  
 [Afficher des assemblys avec BizTalk Assembly Viewer](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)