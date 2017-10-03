---
title: "Configurer le déploiement automatique avec Visual Studio Team Services dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57f769bb-5105-43e2-9096-ed54cdf82b90
caps.latest.revision: "8"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 23d79eae3bd89a572a919cfeff800178f9163796
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-automatic-deployment-with-visual-studio-team-services-in-biztalk-server"></a>Configurer le déploiement automatique avec Visual Studio Team Services dans BizTalk Server
Déployer automatiquement [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] applications à l’aide de Visual Studio Team Services. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fournit une expérience d’application lifecycle management (ALM) et un déploiement automatique amélioré. 

Cette section vous montre comment le programme d’installation de VSTS avec [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]et ajoutez votre première application à déployer.

## <a name="before-you-begin"></a>Avant de commencer

* Vous devez Visual Studio Team Services (VSTS) prêt. N’en avez pas ? [S’inscrire pour Visual Studio Team Services](https://www.visualstudio.com/docs/setup-admin/team-services/sign-up-for-visual-studio-team-services).
* Si vous avez déjà un Agent VSTS est installé sur votre ordinateur BizTalk, l’agent existant est remplacé par le dernier Agent VSTS. Vous devrez peut-être mettre à jour votre [service VSTS pour les aligner avec le nouvel agent](https://www.visualstudio.com/docs/build/actions/agents/v2-windows#replace-an-agent).
* Déploiement automatique avec VSTS est effectué sur une [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe. Assurez-vous que l’ordinateur dispose de Visual Studio et le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] outils de développement et Kit de développement SDK. Consultez le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] [matérielle et logicielle requise](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md).

## <a name="next-steps"></a>Étapes suivantes
[Configurer VSTS pour le déploiement automatique](../core/configure-visual-studio-team-services-to-deploy-biztalk-solutions-or-projects.md)

[Configurer le modèle JSON](../core/configure-the-json-template-for-automatic-deployment.md)

[Configurer les variables et les jetons de l’environnement](../core/configure-environmental-tokens-and-variables-for-automatic-deployment.md)

[Ajouter une application BizTalk dans VSTS](../core/add-a-biztalk-server-application-to-visual-studio-team-services.md)