---
title: Ajouter une application BizTalk Server pour Visual Studio Team Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2c7a1ff-0f26-45f3-9a9b-4c99a67b51a9
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: d3fc8c0253c8e2517f78c2d60fdc7c74a983bdbd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-a-biztalk-server-application-to-visual-studio-team-services"></a>Ajouter une application BizTalk Server pour Visual Studio Team Services
Ajouter un [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projet VSTS pour déployer automatiquement à l’aide de l’intégration continue.  

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez déployer automatiquement vos applications pour votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements à l’aide de Visual Studio Team Services (VSTS). 

Cette rubrique fournit une vue d’ensemble et répertorie les principales étapes pour déployer votre solution à partir de Visual Studio pour votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]. 

## <a name="prerequisites"></a>Conditions préalables
* Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* [Configurer VSTS pour le déploiement automatique](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)
* Base de connaissances et expérience avec Git et des référentiels dans Visual Studio. Si vous êtes débutant dépôts et le contrôle de version, il peut s’agir de bonnes ressources : 

    [En savoir plus Git](https://www.visualstudio.com/learn-git/)  
    [GIT et Team Services](https://www.visualstudio.com/docs/git/overview)
* Base de connaissances et expérience des projets BizTalk dans[!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]

## <a name="add-biztalk-project-to-vsts"></a>Ajouter un projet BizTalk pour VSTS
1. Dans **Visual Studio**, se connecter à votre **référentiel Source**, et **Clone** à votre ordinateur.
2. Ouvrez ou créez un **projet BizTalk** (.btproj).

   > [!NOTE]
   > Vous pouvez ajouter plusieurs projets dans la même solution.
   
3. Ajouter un nouveau **projet d’Application de BizTalk Server** (.btaproj).
4. Cliquez sur le projet dans le **l’Explorateur de solutions**, puis sélectionnez **propriétés**.
5. Configurer le **Version** et les propriétés de connexion pour votre **Visual Studio Team Services** compte.

    ![Visual Studio Configuration FP1 BizTalk](../core/media/visual-studio-configuration-fp1-biztalk.png)

6. Ajoutez tous les assemblys et les artefacts requis par votre application.
7. Mise à jour la **binding.xml** fichier avec les informations de liaison correct.
8. Mise à jour la **BizTalkServerInventory.json** avec tous les artefacts et le bon ordre pour les artefacts doit être installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].
9. Avec le bouton droit et **générer** votre solution pour vérifier les erreurs. 
10. Lorsque la build se termine correctement, avec le bouton droit de votre solution, puis sélectionnez **déployer**.
11. Votre application doit déployer automatiquement sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].

## <a name="see-also"></a>Voir aussi
[Configurer le Pack de fonctionnalités](../core/configure-the-feature-pack.md)