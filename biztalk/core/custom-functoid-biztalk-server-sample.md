---
title: "Fonctoid personnalisé (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoids, customizing
- examples, functoids
- functoids, examples
- XML tools
- examples, XML tools
ms.assetid: 9f1eb260-ff62-46f5-a517-57f4e9172b35
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5117bed6ea1116047052359eadcd11754e9f85d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="custom-functoid-biztalk-server-sample"></a>Fonctoid personnalisé (exemple BizTalk Server)
L'exemple de fonctoid personnalisé montre comment écrire un fonctoid personnalisé pour le Mappeur BizTalk. Vous pouvez ajouter le fonctoid à la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Le fonctoid est affiché dans la boîte à outils lorsque le Mappeur BizTalk est actif.  
  
 Un fonctoid personnalisé doit résider dans un assembly du Mappeur BizTalk pour être reconnu. Il peut être écrit dans n'importe quel langage compatible .NET, tel que C# ou Visual Basic.  
  
 Par ailleurs, un fonctoid personnalisé doit dériver de la classe `Microsoft.BizTalk.BaseFunctoids` et fournir l'implémentation pour certaines méthodes en les remplaçant. (La classe `BaseFunctoid` est définie dans l'assembly Microsoft.BizTalk.BaseFunctoids.dll inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple de fonctoid personnalisé implémente plusieurs fonctoids qui dérivent de la classe `BaseFunctoid` et remplacent plusieurs méthodes.  
  
 Vous pouvez exposer le code Inline d'un fonctoid personnalisé lors de son implémentation. Le code Inline exécute le calcul pour le fonctoid. Le compilateur du Mappeur BizTalk extrait le code Inline d'un fonctoid et l'intègre dans le XSLT compilé lors de la création du projet.  
  
 Si votre fonctoid personnalisé n'expose aucun code Inline, le Mappeur BizTalk génère le XSLT qui appelle l'assembly dans lequel réside le fonctoid personnalisé. Dans ce cas, vous devez vérifier que l'assembly de votre fonctoid personnalisé est disponible dans le Global Assembly Cache (GAC) afin que le moteur XSLT puisse le trouver. Un fonctoid personnalisé doit avoir également un attribut de GUID unique. Le Mappeur BizTalk utilise le GUID pour identifier l'assembly à charger.  
  
> [!IMPORTANT]
>  Si vous réutilisez l'exemple de code de fonctoid personnalisé pour implémenter vos propres fonctoids, veillez à utiliser un attribut de GUID unique.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès >*\XmlTools\CustomFunctoid  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AssemblyInfo.cs|Code source C# d'informations de l'assembly.|  
|CBuildArray.bmp|Bitmap de la boîte à outils.|  
|CConcat.bmp|Bitmap de la boîte à outils.|  
|CExtractArray.bmp|Bitmap de la boîte à outils.|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC), ainsi que pour supprimer le fichier CustomFunctoid.dll.|  
|CLongestString.bmp|Bitmap de la boîte à outils.|  
|CMultiply.bmp|Bitmap de la boîte à outils.|  
|CustomFunctoid.cs|Code source C# du fonctoid personnalisé.|  
|CustomFunctoid.csproj|Projet C# du fonctoid personnalisé.|  
|CustomFunctoid.sln|Solution du fonctoid personnalisé.|  
|CustomFunctoidResources.resx|Ressources du fonctoid personnalisé.|  
|Setup.bat|Utilisé pour créer, déployer et démarrer l'exemple.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 La procédure suivante permet de créer et d'initialiser l'exemple de fonctoid personnalisé.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \XmlTools\CustomFunctoid  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   création de l'exemple de projet ;  
  
    -   copie de l'assembly généré dans le répertoire Developer Tools\Mapper Extensions ;  
  
    -   ajout de l'assembly généré au GAC.  
  
        > [!NOTE]
        >  Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple de fonctoid personnalisé.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **outils** , puis sélectionnez **choisir des éléments de boîte à outils**.  
  
2.  Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, sélectionnez le **fonctoids du Mappeur BizTalk** onglet.  
  
3.  Cliquez sur **réinitialiser**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si votre fonctoid personnalisé n'expose aucun code Inline, vérifiez que son assembly est disponible dans le GAC.  
  
4.  À partir de la **fichier** menu, sélectionnez **Exit** pour fermer [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
5.  Démarrer **invite de commandes Visual Studio**.  
  
6.  À l’invite de commandes, tapez **devenv /setup**.  
  
7.  Démarrer **Microsoft Visual Studio**.  
  
     Personnalisé fonctoids (fonctoid concaténation personnalisé, chaîne la plus longue, Build tableau fonctoid et tableau fonctoid) s’affichent sur le **fonctoids de chaîne** onglet de la boîte à outils et le fonctoid Multiplication Cumulative apparaît sur le **Fonctoids cumulés** onglet.  
  
## <a name="removing-this-sample"></a>Suppression de cet exemple  
 La procédure suivante permet de supprimer l'exemple de fonctoid personnalisé.  
  
#### <a name="to-remove-this-sample"></a>Pour supprimer cet exemple  
  
1.  Supprimez les fonctoids de la boîte à outils de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
    > [!WARNING]
    >  Si, après l'exécution de Cleanup.bat, les fonctoids personnalisés obsolètes apparaissent toujours dans la boîte à outils (ce qui peut tenir à une mise en cache interne dans Visual Studio), procédez comme suit :  
  
    1.  À partir d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **outils** , puis sélectionnez **choisir des éléments de boîte à outils**.  
  
    2.  Dans le **des éléments de boîte à outils de choisir** boîte de dialogue, sélectionnez le **fonctoids du Mappeur BizTalk** onglet.  
  
    3.  Recherchez les fonctoids personnalisés (fonctoids personnalisés de concaténation, de chaîne la plus longue, de création de tableau, d'extraction de tableau et de multiplication cumulative) dans la liste. Cliquez sur la **case à cocher** à supprimer les fonctoids, puis cliquez sur **OK**.  
  
     Si le problème persiste, procédez comme suit :  
  
    1.  À partir de la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projet BizTalk, cliquez sur le **boîte à outils** onglet lors de la modification d’un mappage pour afficher la Palette de la boîte à outils.  
  
    2.  Avec le bouton droit de la boîte à outils et sélectionnez **choisir des éléments de**.  
  
    3.  Dans la boîte de dialogue Choisir des éléments, cliquez sur **réinitialiser**, puis cliquez sur **OK**.  
  
    4.  Fermez toutes les instances de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
     Si le problème persiste, procédez comme suit :  
  
    1.  Démarrer **invite de commandes Visual Studio** en tant qu’administrateur.  
  
    2.  Fermez toutes les instances de Visual Studio en cours d'exécution.  
  
    3.  Exécutez les commandes suivantes :  
  
         `devenv /resetsettings`  
  
         `devenv /setup`  
  
    4.  Vous pouvez sélectionner manuellement les fonctoids indésirables dans la boîte à outils. Ensuite, cliquez avec le bouton droit sur le fonctoid, puis cliquez sur **supprimer**.  
  
     Si le problème persiste, procédez comme suit :  
  
    1.  Dans un projet BizTalk [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], cliquez sur l'onglet Boîte à outils lors de la modification d'un mappage pour afficher la palette de la boîte à outils.  
  
    2.  Cliquez sur le **fonctoids cumulés** groupe.  
  
    3.  Cliquez avec le bouton droit sur le fonctoid que vous souhaitez supprimer, puis choisissez **supprimer** ou appuyez sur la touche SUPPR.  
  
    4.  Cliquez sur le **fonctoids de chaîne** groupe.  
  
    5.  Cliquez avec le bouton droit sur le fonctoid que vous souhaitez supprimer, puis choisissez **supprimer** ou appuyez sur la touche SUPPR.  
  
2.  Dans une fenêtre de commande, accédez au répertoire (**cd**) dans le dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \XmlTools\CustomFunctoid  
  
3.  Exécutez le fichier Cleanup.bat, qui effectue les actions suivantes :  
  
    -   suppression de l'assembly du répertoire Developer Tools\Mapper Extensions ;  
  
    -   suppression de l'assembly du GAC.  
  
## <a name="classes-or-methods-used-in-this-sample"></a>Classes ou méthodes utilisées dans l'exemple  
 [Microsoft.BizTalk.BaseFunctoids.BaseFunctoid](http://msdn.microsoft.com/library/microsoft.biztalk.basefunctoids.basefunctoid.aspx)  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de BaseFunctoid](../core/using-basefunctoid.md)   
 [Outils XML (dossier d’exemples BizTalk Server)](../core/xml-tools-biztalk-server-samples-folder.md)