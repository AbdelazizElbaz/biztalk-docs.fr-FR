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
# <a name="scenario-updating-application-artifacts"></a><span data-ttu-id="6be57-102">Scénario : Mise à jour des artefacts de l’Application</span><span class="sxs-lookup"><span data-stu-id="6be57-102">Scenario: Updating Application Artifacts</span></span>
<span data-ttu-id="6be57-103">Il existe deux scénarios de base pour la mise à jour des artefacts d'une application déployée dans un environnement de production :</span><span class="sxs-lookup"><span data-stu-id="6be57-103">There are two basic scenarios for updating the artifacts in an application that has been deployed into a production environment:</span></span>  
  
-   <span data-ttu-id="6be57-104">Mise à niveau d'une orchestration à l'aide d'une nouvelle version lorsque l'orchestration gère des transactions à long terme ou attend une réponse d'un port sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="6be57-104">Updating an orchestration with a new version when the orchestration handles long-running transactions or is waiting for a response from a solicit-response port.</span></span>  
  
-   <span data-ttu-id="6be57-105">Le cas de mise à jour le plus général, lorsqu'il n'y a pas de problème d'attente de fin du traitement des messages, comme la mise à jour d'un schéma ou le mappage avec une nouvelle version.</span><span class="sxs-lookup"><span data-stu-id="6be57-105">The more general update case, when you are not concerned with completing message processing, such as updating a schema or map with a new version.</span></span>  
  
 <span data-ttu-id="6be57-106">Dans ce cas général, vous pouvez effectuer la mise à jour d'un artefact au moyen d'une nouvelle version, par exemple pour prendre en compte une modification des besoins de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="6be57-106">In the general update case, you may be updating an artifact with a new version, for example to address a change in business requirements.</span></span> <span data-ttu-id="6be57-107">Ce scénario est relativement direct et vous pouvez remplacer l'ancien artefact par l'artefact mis à jour.</span><span class="sxs-lookup"><span data-stu-id="6be57-107">This scenario is relatively straightforward, and you can overwrite the original artifact with the updated one.</span></span> <span data-ttu-id="6be57-108">Pour obtenir la liste des étapes impliquées, consultez [liste de vérification : mise à jour les artefacts dans une Application BizTalk](../core/checklist-update-the-artifacts-in-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="6be57-108">For a list of the steps involved, see [Checklist: Update the Artifacts in a BizTalk Application](../core/checklist-update-the-artifacts-in-a-biztalk-application.md).</span></span>  
  
 <span data-ttu-id="6be57-109">Le second scénario est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="6be57-109">The second scenario is more complex.</span></span> <span data-ttu-id="6be57-110">Dans ce cas, vous devez autoriser l'orchestration existante à terminer le traitement des messages.</span><span class="sxs-lookup"><span data-stu-id="6be57-110">In this case, you must allow the existing orchestration to finish processing the messages.</span></span> <span data-ttu-id="6be57-111">Parallèlement, vous devez éviter que l'orchestration existante ne commence le traitement de nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="6be57-111">At the same time, you must prevent the existing orchestration from processing any new messages.</span></span> <span data-ttu-id="6be57-112">Vous souhaitez à la place que ce soit la version mise à jour de l'orchestration qui prenne le relais.</span><span class="sxs-lookup"><span data-stu-id="6be57-112">Instead, you want the updated version of the orchestration to take over.</span></span> <span data-ttu-id="6be57-113">Pour y parvenir, vous devez déployer l'assembly contenant l'orchestration modifiée dans la même application BizTalk que la version originale, puis exécuter simultanément les deux orchestrations.</span><span class="sxs-lookup"><span data-stu-id="6be57-113">To accomplish this, you deploy the assembly containing the updated orchestration into the same BizTalk application as the original version, and then run both orchestrations simultaneously.</span></span> <span data-ttu-id="6be57-114">(Le nouvel assembly doit disposer d'un numéro de version différent de l'assembly contenant l'orchestration d'origine, faute de quoi, vous ne pourrez pas le déployer dans le même groupe BizTalk.) Vous arrêtez ensuite l'orchestration d'origine, de sorte que plus aucun message ne puisse être acheminé vers elle, puis démarrez la version mise à jour, de sorte à y envoyer les nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="6be57-114">(The new assembly must have a different version number than the assembly containing the original orchestration, or you will not be able to deploy it into the same BizTalk group.) You then stop the original orchestration, so that no new messages are routed to it, and start the updated version, so that all new messages are sent to it.</span></span> <span data-ttu-id="6be57-115">Une fois que l'orchestration d'origine a fini de traiter tous ses messages, vous pouvez alors annuler son déploiement.</span><span class="sxs-lookup"><span data-stu-id="6be57-115">After the original version has finished processing all of its messages, you can then undeploy it.</span></span> <span data-ttu-id="6be57-116">Pour obtenir des instructions sur la réalisation de ces tâches, consultez [la mise à niveau d’une Orchestration](../core/how-to-upgrade-an-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="6be57-116">For instructions on performing these tasks, see [How to Upgrade an Orchestration](../core/how-to-upgrade-an-orchestration.md).</span></span>  
  
 <span data-ttu-id="6be57-117">Le schéma suivant montre un déploiement d'orchestrations côte à côte type.</span><span class="sxs-lookup"><span data-stu-id="6be57-117">The following diagram shows a typical side-by-side orchestration deployment.</span></span>  
  
 <span data-ttu-id="6be57-118">![Scénario de déploiement côte à côte](../core/media/ebiz-depl-sidebyside-scenario.gif "ebiz_depl_sidebyside_scenario")</span><span class="sxs-lookup"><span data-stu-id="6be57-118">![Side by Side Deployment Scenario](../core/media/ebiz-depl-sidebyside-scenario.gif "ebiz_depl_sidebyside_scenario")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be57-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6be57-119">See Also</span></span>  
 <span data-ttu-id="6be57-120">[Déploiement d’applications et scénarios de gestion](../core/application-deployment-and-management-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="6be57-120">[Application Deployment and Management Scenarios](../core/application-deployment-and-management-scenarios.md) </span></span>  
 [<span data-ttu-id="6be57-121">Considérations importantes pour la mise à jour des Applications</span><span class="sxs-lookup"><span data-stu-id="6be57-121">Important Considerations for Updating Applications</span></span>](../core/important-considerations-for-updating-applications.md)