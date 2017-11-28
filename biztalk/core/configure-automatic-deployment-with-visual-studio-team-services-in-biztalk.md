---
title: "Configurer le déploiement automatique avec Visual Studio Team Services | Documents Microsoft"
description: "Installer BizTalk Feature Pack pour utiliser la gestion du cycle de vie des applications avec VSTS à déployer vos applications dans différents environnements de BizTalk"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d135960143fed33d1ce4847c681f5b1134489b65
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a>Configurer le déploiement automatique avec Visual Studio Team Services dans BizTalk Server

## <a name="overview"></a>Vue d'ensemble

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fournit une expérience d’application lifecycle management (ALM) et un déploiement automatique amélioré. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, nous avons amélioré cette fonctionnalité :

* Dans Visual Studio, définissez la **nom de l’Application** de votre application BizTalk
* En plus d’utiliser un déploiement de l’agent, vous pouvez également utiliser [groupes de déploiement](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index) pour déployer vos applications BizTalk sur plusieurs serveurs
* Dans la tâche de mise en production, vous pouvez installer l’application BizTalk et entrez l’ordinateur de gestion BizTalk et le chemin d’accès au package de déploiement

À l’aide de Visual Studio Team Services, vous pouvez déployer automatiquement [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications pour différents environnements de BizTalk. 

En règle générale, il existe deux rôles impliqués :

- Développeur BizTalk crée l’application et il génère localement. Vérifie ensuite l’application dans Git ou Team Foundation Version Control.
- VSTS admin crée les définitions de build et de mise en production et déploie l’application BizTalk vers d’autres environnements (développement, UAT, Production).

Si vous n’avez jamais utilisé VSTS, cette procédure pas à pas peut être difficile. Elle nécessite une compréhension des git, y compris le clonage et l’envoi des modifications. 

Nous vous montrons comment le programme d’installation de VSTS avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et ajoutez votre première application à déployer. Nous vous recommandons de vous reporter à la [des conseils de VSTS](https://docs.microsoft.com/vsts/user-guide/), comme l’UI VSTS change. 

## <a name="before-you-begin"></a>Avant de commencer

* Vous devez Visual Studio Team Services (VSTS) prêt. N’en avez pas ? [S’inscrire pour Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).
* Si vous avez déjà un Agent VSTS est installé sur votre ordinateur BizTalk, l’agent existant est remplacé par le dernier Agent VSTS. Vous devrez peut-être mettre à jour votre [service VSTS pour les aligner avec le nouvel agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).
* Avec Feature Pack 1, le déploiement automatique avec VSTS est effectué sur une [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe. Assurez-vous que l’ordinateur dispose de Visual Studio et le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] outils de développement et Kit de développement SDK. Consultez le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [matérielle et logicielle requise](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).
* Avec Feature Pack 2, le déploiement automatique avec VSTS peut être effectué à l’aide [groupes de déploiement](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/howto-deployment-groups). À l’aide de groupes de déploiement, vous pouvez déployer vos applications à plusieurs serveurs BizTalk Server dans le groupe de déploiement.

## <a name="prerequisites"></a>Conditions préalables

* Installer [Feature Pack 2](https://aka.ms/bts2016fp2) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]
* Certains expérience et la base de connaissances avec la création et l’utilisation avec les définitions de VSTS. Si vous êtes débutant VSTS, il peut s’agir de bonnes ressources : 

  [Vue d’ensemble de Visual Studio Team Services](https://www.visualstudio.com/docs/overview)  
  [L’élément de configuration/CD pour les internautes novices](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)

## <a name="get-started"></a>Prise en main
[Étape 1 : Ajouter un projet d'application et mettre à jour le modèle .json](feature-pack-add-application-project.md)  

[Étape 2 : Créer le jeton VSTS et installer l'agent de build](feature-pack-create-vsts-token.md)

[Étape 3 : Création de la build et définitions de version](feature-pack-add-build-release-definitions.md)

[Configurer les variables et les jetons de l’environnement](configure-environmental-tokens-and-variables-for-automatic-deployment.md)