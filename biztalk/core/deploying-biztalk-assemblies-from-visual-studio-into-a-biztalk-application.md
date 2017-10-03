---
title: "Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: accef4b8-acdf-4043-8fd7-2db9ea752074
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1165fb461d5d54419ea56a42f7fe428ab027089
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application"></a>Déploiement des assemblys BizTalk à partir de Visual Studio dans une application BizTalk
Déployer et redéployer les assemblys BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans une application BizTalk. Vous pouvez le faire pour tester la fonctionnalité des assemblys que vous avez développés et les regrouper pour la remise.  

## <a name="overview"></a>Vue d'ensemble  
 Applications BizTalk permettent d’afficher et gérer les éléments, appelés « artefacts », qui constituent une solution d’entreprise BizTalk. Les artefacts incluent des assemblys BizTalk (contenant des orchestrations, schémas, mappages et pipelines), que vous pouvez déployer dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Ils incluent également des éléments tels que des assemblys, certificats, scripts, fichiers Readme et stratégies .NET que vous ajoutez à votre application BizTalk à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou de l'outil de ligne de commande BTSTask. Le développeur de solutions ou l'administrateur peut ensuite visualiser, regrouper, déployer et gérer l'application et ses artefacts en tant qu'entité unique. Pour plus d’informations sur la création, déploiement et la gestion des applications BizTalk, consultez [déploiement et la gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md).  
  
 Pour pouvoir créer et déployer un assembly BizTalk, vous devez créer un projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis créer ou ajouter les éléments à inclure dans l'assembly. Vous pouvez créer une solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] permettant de contenir plusieurs projets, puis créer et déployer leurs assemblys tous en même temps dans la même application ou dans des applications différentes. Pour obtenir des instructions sur la réalisation de ces tâches, consultez [comment créer des projets BizTalk](../core/how-to-create-biztalk-projects.md).  
  
 Une fois ces tâches terminées, vous pouvez créer, déployer et annuler le déploiement des assemblys BizTalk en procédant comme suit, tel que décrit dans les rubriques de cette section :  
  
-   Configurez un fichier de clé d'assembly de nom fort pour chaque projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
-   Définissez les propriétés de déploiement du projet, y compris l'option de redéploiement permettant de redéployer aisément l'assembly.  
  
-   La commande de déploiement de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] permet de créer les assemblys BizTalk contenus dans une solution et de les déployer dans une application BizTalk. Cette commande vous permet également de créer et de déployer un assembly dans un seul projet, mais nous vous le déconseillons.  
  
-   Après avoir testé l'application et apporté les modifications nécessaires, utilisez la commande de déploiement de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour recréer et redéployer l'assembly.  
  
-   Installez l'assembly dans le GAC, si nécessaire, ou supprimez-le de celui-ci.  
  
-   Annulez le déploiement de l'assembly.  
  
 Après avoir déployé un ou plusieurs assemblys dans une application BizTalk, terminez la configuration de l'application et déployez-la dans un environnement de test, puis de production. Pour plus d’informations, consultez [tâches de développement pour le déploiement d’applications BizTalk](../core/development-tasks-for-biztalk-application-deployment.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Que se passe-t-il lorsque vous déployez un Assembly à partir de Visual Studio](../core/what-happens-when-you-deploy-an-assembly-from-visual-studio.md)  
  
-   [Installation de l’assembly dans le GAC](../core/assembly-installation-in-the-gac.md)  
  
-   [Comment configurer un fichier de clé de nom fort Assembly](../core/how-to-configure-a-strong-name-assembly-key-file.md)  
  
-   [Comment définir des propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md)  
  
-   [Comment déployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [Comment redéployer un Assembly BizTalk à partir de Visual Studio](../core/how-to-redeploy-a-biztalk-assembly-from-visual-studio.md)  
  
-   [Comment installer ou désinstaller un Assembly dans le GAC](../core/how-to-install-an-assembly-in-the-gac.md)  