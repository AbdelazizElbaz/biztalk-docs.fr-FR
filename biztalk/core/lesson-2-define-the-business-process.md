---
title: 'Leçon 2 : Définir le processus d’entreprise | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial, defining business processes
ms.assetid: 644aa049-4dd7-4392-b97f-31b1f29e12bd
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5a2a9512fe847fdf50957456ec3d3eeff087c33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-define-the-business-process"></a><span data-ttu-id="dd29e-102">Leçon 2 : Définition du processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="dd29e-102">Lesson 2: Define the Business Process</span></span>
<span data-ttu-id="dd29e-103">Dans cette leçon, vous créez le deuxième projet dans la solution Enterprise Application Integration(EAI).</span><span class="sxs-lookup"><span data-stu-id="dd29e-103">In this lesson, you create the second project in the Enterprise Application Integration(EAI) solution.</span></span> <span data-ttu-id="dd29e-104">Ce projet contient une orchestration.</span><span class="sxs-lookup"><span data-stu-id="dd29e-104">This project contains an orchestration.</span></span>  
  
 <span data-ttu-id="dd29e-105">Dans le scénario IAE, l’application de l’entrepôt envoie un message de demande de réapprovisionnement de stock à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="dd29e-105">In the EAI scenario, the warehouse application sends an inventory replenishment message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] for processing.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dd29e-106">utilise l’orchestration créée pour automatiser le processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="dd29e-106"> uses the orchestration you create to automate the business process.</span></span> <span data-ttu-id="dd29e-107">L'orchestration fournit le workflow, les actions et les expressions nécessaires pour déplacer les messages dans le système et traiter leur contenu.</span><span class="sxs-lookup"><span data-stu-id="dd29e-107">The orchestration provides the workflow, actions, and expressions to move messages through the system and process their contents.</span></span>  
  
 <span data-ttu-id="dd29e-108">Enfin, vous générez le projet avant de démarrer [leçon 3 : déployer la Solution](../core/lesson-3-deploy-the-solution.md).</span><span class="sxs-lookup"><span data-stu-id="dd29e-108">Finally you build the project before starting [Lesson 3: Deploy the Solution](../core/lesson-3-deploy-the-solution.md).</span></span>  
  
 <span data-ttu-id="dd29e-109">Pour plus d’informations, consultez [création d’Orchestrations à l’aide de concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md).</span><span class="sxs-lookup"><span data-stu-id="dd29e-109">For more information, see [Creating Orchestrations Using Orchestration Designer](../core/creating-orchestrations-using-orchestration-designer.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd29e-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dd29e-110">In This Section</span></span>  
  
-   [<span data-ttu-id="dd29e-111">Étape 1 : Ajouter un projet EAIOrchestration à la Solution</span><span class="sxs-lookup"><span data-stu-id="dd29e-111">Step 1: Add EAIOrchestration Project to the Solution</span></span>](../core/step-1-add-eaiorchestration-project-to-the-solution.md)  
  
-   [<span data-ttu-id="dd29e-112">Étape 2 : Définir le processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="dd29e-112">Step 2: Define the Business Process</span></span>](../core/step-2-define-the-business-process.md)  
  
-   [<span data-ttu-id="dd29e-113">Étape 3 : Ajouter des Ports à l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="dd29e-113">Step 3: Add Ports to the Orchestration</span></span>](../core/step-3-add-ports-to-the-orchestration.md)  
  
-   [<span data-ttu-id="dd29e-114">Étape 4 : Création du projet EAIOrchestration</span><span class="sxs-lookup"><span data-stu-id="dd29e-114">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)  
  
## <a name="see-also"></a><span data-ttu-id="dd29e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd29e-115">See Also</span></span>  
 <span data-ttu-id="dd29e-116">[Avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="dd29e-116">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="dd29e-117">[Leçon 1 : Définir des schémas et un mappage](../core/lesson-1-define-schemas-and-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="dd29e-117">[Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md) </span></span>  
 [<span data-ttu-id="dd29e-118">Leçon 3 : Déployer la Solution</span><span class="sxs-lookup"><span data-stu-id="dd29e-118">Lesson 3: Deploy the Solution</span></span>](../core/lesson-3-deploy-the-solution.md)