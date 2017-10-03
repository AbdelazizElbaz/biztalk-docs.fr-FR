---
title: "Scénario : Mise à jour des artefacts de l’Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, artifacts
- updating, artifacts
- artifacts, examples
- updating, examples
- examples, updating
- artifacts, updating
ms.assetid: 76833df3-2330-48af-84d8-731028b192ff
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e95e6a66fb0e6bccc1fcc2fb4a7664538e50d3e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-updating-application-artifacts"></a>Scénario : Mise à jour des artefacts de l’Application
Il existe deux scénarios de base pour la mise à jour des artefacts d'une application déployée dans un environnement de production :  
  
-   Mise à niveau d'une orchestration à l'aide d'une nouvelle version lorsque l'orchestration gère des transactions à long terme ou attend une réponse d'un port sollicitation-réponse.  
  
-   Le cas de mise à jour le plus général, lorsqu'il n'y a pas de problème d'attente de fin du traitement des messages, comme la mise à jour d'un schéma ou le mappage avec une nouvelle version.  
  
 Dans ce cas général, vous pouvez effectuer la mise à jour d'un artefact au moyen d'une nouvelle version, par exemple pour prendre en compte une modification des besoins de l'entreprise. Ce scénario est relativement direct et vous pouvez remplacer l'ancien artefact par l'artefact mis à jour. Pour obtenir la liste des étapes impliquées, consultez [liste de vérification : mise à jour les artefacts dans une Application BizTalk](../core/checklist-update-the-artifacts-in-a-biztalk-application.md).  
  
 Le second scénario est plus complexe. Dans ce cas, vous devez autoriser l'orchestration existante à terminer le traitement des messages. Parallèlement, vous devez éviter que l'orchestration existante ne commence le traitement de nouveaux messages. Vous souhaitez à la place que ce soit la version mise à jour de l'orchestration qui prenne le relais. Pour y parvenir, vous devez déployer l'assembly contenant l'orchestration modifiée dans la même application BizTalk que la version originale, puis exécuter simultanément les deux orchestrations. (Le nouvel assembly doit disposer d'un numéro de version différent de l'assembly contenant l'orchestration d'origine, faute de quoi, vous ne pourrez pas le déployer dans le même groupe BizTalk.) Vous arrêtez ensuite l'orchestration d'origine, de sorte que plus aucun message ne puisse être acheminé vers elle, puis démarrez la version mise à jour, de sorte à y envoyer les nouveaux messages. Une fois que l'orchestration d'origine a fini de traiter tous ses messages, vous pouvez alors annuler son déploiement. Pour obtenir des instructions sur la réalisation de ces tâches, consultez [la mise à niveau d’une Orchestration](../core/how-to-upgrade-an-orchestration.md).  
  
 Le schéma suivant montre un déploiement d'orchestrations côte à côte type.  
  
 ![Scénario de déploiement côte à côte](../core/media/ebiz-depl-sidebyside-scenario.gif "ebiz_depl_sidebyside_scenario")  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md)   
 [Considérations importantes pour la mise à jour des Applications](../core/important-considerations-for-updating-applications.md)