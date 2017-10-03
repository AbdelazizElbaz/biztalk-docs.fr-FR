---
title: "Que se passe-t-il lorsque vous déployez un Assembly à partir de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 421df529-1ddb-4f49-a40a-c06f2a434ffc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66454d80d702cc6b3ca20708b07fd64cdfcb00d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-happens-when-you-deploy-an-assembly-from-visual-studio"></a>Effets du déploiement d'un assembly à partir de Visual Studio
Cette rubrique décrit les effets du déploiement d'assemblys depuis [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans une application BizTalk sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Vous pouvez déployer un projet seul, ou tous les projets d'une solution en même temps. Avant de déployer un projet, séparément ou en tant que partie d’une solution, vous spécifiez l’application dans laquelle vous voulez déployer l’assembly dans les propriétés du projet, comme décrit dans [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Lorsque vous déployez un projet ou une solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], les assemblys sont automatiquement compilés et déployés dans l'application spécifiée. Si une application existante du groupe BizTalk local porte le même nom que l'application spécifiée dans les propriétés du projet, l'assembly est déployé dans l'application existante. Sinon, une nouvelle application dotée du nom spécifié est créée pour recevoir l'assembly. Dans le cadre de ce processus, l'assembly et les orchestrations, pipelines, schémas et mappages qu'il contient (appelés « artefacts ») sont importés dans la base de données de gestion BizTalk locale et associés à l'application spécifiée.  
  
 Vous pouvez déployer les projets d'une solution dans la même application BizTalk ou dans des applications BizTalk différentes, et ce même lorsque les projets de la solution sont déployés en même temps. Le schéma suivant illustre le déploiement de trois assemblys contenus dans une solution BizTalk de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans deux applications BizTalk distinctes.  
  
 ![Déployer des assemblys BizTalk](../core/media/visualstudiodeploy.gif "VisualStudioDeploy")  
  
 Après le déploiement d'un projet ou d'une solution, vous pouvez afficher et gérer les assemblys et leurs artefacts dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou à l'aide de l'outil de ligne de commande BTSTask.  
  
## <a name="destination-locations"></a>Emplacements de destination  
 Lors du déploiement d'assemblys dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l'emplacement de destination par défaut correspond à l'emplacement source de l'assembly. Lors de l'installation ou de l'exportation d'un assembly depuis [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], l'installation échoue si les environnements source et de destination diffèrent. Par exemple, si l'emplacement source est D:[chemin]/[nom_fichier] et que l'ordinateur d'installation cible ne dispose pas d'un lecteur D, l'installation échoue.  
  
 Ce comportement diffère de celui impliqué lors de l'ajout d'une ressource avec l'Administrateur BizTalk et qui définit l'emplacement de destination par défaut sur %BTAD_InstallDir%. La variable d'environnement prend la valeur correspondant au répertoire d'installation spécifié lors de l'installation.  
  
 Pour contourner ce problème, utilisez la procédure suivante :  
  
1.  Déployez l'assembly dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Ouvrez ensuite l'Administrateur BizTalk.  
  
3.  Modifiez l'emplacement de destination selon les besoins. Remplacez-le, par exemple, par %BTAD_InstallDir%.  
  
 Le nouvel emplacement de destination sera utilisé comme emplacement par défaut pour les redéploiements ultérieurs du même assembly.  
  
 Pour plus d’informations, consultez [comment déployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
## <a name="deploying-solutions-vs-projects"></a>Déploiement de Solutions vs. Projets  
 Il est vivement recommandé de toujours déployer une solution plutôt qu'un projet individuel. Si vous déployez un projet individuel et que plusieurs dépendances existent entre l'assembly que vous déployez et un autre assembly, un certain nombre de configurations manuelles seront nécessaires à la réalisation complète du déploiement. En revanche, lorsque vous déployez une solution, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] gère automatiquement ces configurations. Pour plus d’informations, consultez [comment redéployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md).  
  
 Le schéma suivant illustre la procédure suivie par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour redéployer des assemblys faisant l'objet de dépendances au moment du déploiement d'une solution.  
  
 ![Déploiement d’assemblys dans une solution](../core/media/deployassemblies.gif "DeployAssemblies")  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)