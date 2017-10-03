---
title: "Ajout et suppression de fonctoids personnalisés à partir de la boîte à outils Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28f798cc-da97-4332-a842-ba87ac7b13b8
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b34d546de0bbb2a79300c4f672bdfcecdab5958
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-and-removing-custom-functoids-from-the-visual-studio-toolbox"></a>Ajout et suppression de fonctoids personnalisés dans la boîte à outils de Visual Studio
Cette rubrique décrit l'ajout et la suppression des fonctoids personnalisés dans la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="adding-custom-functoids-to-visual-studio"></a>Ajout de fonctoids personnalisés à Visual Studio  
 Pour pouvoir utiliser des fonctoids personnalisés dans un mappage, vous devez les avoir préalablement ajoutés dans la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. La procédure suivante permet d'ajouter des fonctoids personnalisés.  
  
#### <a name="to-add-a-custom-functoid"></a>Pour ajouter un fonctoid personnalisé  
  
1.  Ajoutez le fonctoid à la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    1.  À l'aide de l'Explorateur Windows, recherchez l'assembly qui implémente vos fonctoids personnalisés.  
  
    2.  Copiez l’assembly dans le \< *dossier d’installation de BizTalk Server*>**\Developer Tools\Mapper Extensions** active. Le Mappeur BizTalk recherche les fonctoids personnalisés dans ce répertoire.  
  
    3.  À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.  
  
    4.  Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, cliquez sur le **fonctoids du Mappeur BizTalk** onglet.  
  
    5.  Cliquez sur **réinitialiser**, puis cliquez sur **OK**. Ce processus peut prendre quelques instants.  
  
         Vos fonctoids personnalisés doivent maintenant apparaître dans la boîte à outils sous les onglets correspondant à leur catégorie.  
  
     \- - OU -  
  
    1.  À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.  
  
    2.  Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, cliquez sur le **fonctoids du Mappeur BizTalk** onglet.  
  
    3.  Cliquez sur **réinitialiser**, puis cliquez sur **OK**.  
  
        > [!NOTE]
        >  Si votre fonctoid personnalisé n'expose aucun code Inline, vérifiez que son assembly est disponible dans le Global Assembly Cache.  
  
    4.  Sur le **fichier** menu, cliquez sur **Exit** pour fermer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    5.  Démarrer **invite de commandes Visual Studio**.  
  
    6.  À l’invite de commandes, tapez **devenv /setup**.  
  
    7.  Démarrer **Microsoft Visual Studio**.  
  
         Le ou les fonctoids personnalisés doivent apparaître sous l'onglet approprié.  
  
2.  Ajoutez l'assembly au Global Assembly Cache. Si votre assembly contient uniquement des fonctoids Inline, vous pouvez ignorer cette étape.  
  
    1.  Démarrer **invite de commandes Visual Studio**.  
  
    2.  Placez-vous dans le dossier contenant votre assembly.  
  
    3.  À l’invite de commandes, tapez **gacutil /if < assembly_path >**. Par exemple, si votre nom de l’assembly est FunctoidLibrary.dll, tapez **gacutil /if FunctoidLibrary.dll**.  
  
    4.  Lorsque vous avez terminé, tapez **quitter**.  
  
## <a name="removing-custom-functoids-from-visual-studio"></a>Suppression de fonctoids personnalisés de Visual Studio  
 La procédure suivante permet de supprimer des fonctoids personnalisés.  
  
#### <a name="to-remove-a-custom-functoid"></a>Pour supprimer un fonctoid personnalisé  
  
1.  Supprimez le fonctoid à partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils.  
  
    1.  À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, dans le **outils** menu, cliquez sur **choisir des éléments de boîte à outils**.  
  
    2.  Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, cliquez sur le **fonctoids du Mappeur BizTalk** onglet.  
  
    3.  Recherchez le fonctoid personnalisé dans la liste, sélectionnez le **supprimer** case à cocher, puis cliquez sur **OK**.  
  
     \- - OU -  
  
    1.  Lors de la modification d’un mappage dans un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **boîte à outils** onglet pour afficher la palette de boîte à outils.  
  
    2.  Cliquez sur le groupe de fonctoids contenant votre fonctoid personnalisé.  
  
    3.  Cliquez sur le fonctoid que vous souhaitez supprimer, puis cliquez sur **supprimer** ou appuyez sur la touche SUPPR.  
  
2.  Supprimez l’assembly fonctoid à partir de la **Developer Tools\Mapper Extensions** active.  
  
    > [!CAUTION]
    >  Si un assembly contient des fonctoids actifs, ne le supprimez pas. Vous risqueriez de supprimer d'autres mappages.  
  
    1.  Démarrez l’Explorateur Windows et accédez à la **Developer Tools\Mapper Extensions** de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    2.  Avec le bouton droit de l’assembly contenant le fonctoid supprimé, puis cliquez sur **supprimer** pour supprimer le fichier.  
  
3.  Supprimez l'assembly du fonctoid du Global Assembly Cache. Si votre assembly contient uniquement des fonctoids Inline, vous pouvez ignorer cette étape.  
  
    > [!CAUTION]
    >  Si un assembly contient des fonctoids actifs, ne le supprimez pas du Global Assembly Cache. Vous risqueriez de supprimer d'autres mappages.  
  
    1.  Démarrer **invite de commandes Visual Studio**.  
  
    2.  À l’invite de commandes, tapez **gacutil /u < assembly_display_name >**. Par exemple, si votre nom de l’assembly est FunctoidLibrary.dll, tapez **gacutil /if FunctoidLibrary**.  
  
    3.  Lorsque vous avez terminé, tapez **quitter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de fonctoids personnalisés](../core/developing-custom-functoids.md)