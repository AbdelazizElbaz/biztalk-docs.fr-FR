---
title: "Tâches de déploiement d’application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, deploying
- applications, tasks
- deploying [applications], tasks
ms.assetid: 8cb29292-9868-41fa-9f2c-d1c20dfdddbb
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed5dd5b2a15bd8408ee11934d7dd6274e81651b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="application-deployment-tasks"></a>Tâches de déploiement d'applications
Les rubriques de cette section fournissent des informations détaillées sur les tâches présentées ci-après et impliquées dans chaque phase du processus de déploiement d'applications de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
1.  **Développement.** Le développeur déploie les assemblys BizTalk qui doivent être inclus dans l’application BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur l’ordinateur de développement. Cela crée automatiquement l'application et l'alimente avec les artefacts contenus dans les assemblys. Les artefacts désignent l'ensemble des éléments comportant une solution d'entreprise BizTalk, et notamment les assemblys BizTalk, assemblys .NET, schémas, mappages, liaisons, certificats, etc. Le développeur complète l'application en lui ajoutant d'autres artefacts ou en procédant à des configurations supplémentaires. Puis il l'installe à partir du fichier .msi, la teste afin de vérifier sa fonctionnalité, corrige les problèmes éventuels, puis l'exporte depuis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sous la forme d'un fichier .msi.  
  
2.  **Test.** Le testeur importe le fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur un ordinateur de test, ce qui crée l’application dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il installe également l'application sur les ordinateurs hôtes à partir du fichier .msi. Une fois les tests et la correction des bogues terminés, il l'exporte depuis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sous la forme d'un fichier .msi.  
  
3.  **Mise en lots.** L’administrateur importe le fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur un serveur intermédiaire, configure pour l’environnement de production, installe le logiciel sur les ordinateurs hôtes, vérifie sa fonctionnalité, puis exporte l’application terminée sous forme de fichier .msi.  
  
4.  **Production.** L’administrateur importe le fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution dans un environnement de production, installe l’application sur les ordinateurs hôtes et démarre l’application.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Tâches de développement pour le déploiement d’applications BizTalk](../core/development-tasks-for-biztalk-application-deployment.md)  
  
-   [Tâches de test pour le déploiement d’applications BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md)  
  
-   [Tâches de mise en lots pour le déploiement d’applications BizTalk](../core/staging-tasks-for-biztalk-application-deployment.md)  
  
-   [Tâches de production pour le déploiement d’applications BizTalk](../core/production-tasks-for-biztalk-application-deployment.md)