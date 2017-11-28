---
title: "Étape 1 : Ajouter un projet EAIOrchestration à la Solution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9aa0d9-2075-4c7e-8baf-1ecd2721859a
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3b8e2b9c197e01ed695311c67bc79cf5056c4d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-eaiorchestration-project-to-the-solution"></a><span data-ttu-id="8b9ae-102">Étape 1 : ajout d'un projet EAIOrchestration à la solution</span><span class="sxs-lookup"><span data-stu-id="8b9ae-102">Step 1: Add EAIOrchestration Project to the Solution</span></span>
<span data-ttu-id="8b9ae-103">![Étape 1 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span><span class="sxs-lookup"><span data-stu-id="8b9ae-103">![Step 1 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")</span></span>  
  
 <span data-ttu-id="8b9ae-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="8b9ae-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="8b9ae-105">**Objectif :** dans cette étape, vous ajoutez un deuxième projet à la solution EAI.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-105">**Objective:** In this step, you add a second project to the EAI solution.</span></span> <span data-ttu-id="8b9ae-106">Ajouter une orchestration au nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-106">Then you add an orchestration to the new project.</span></span>  
  
 <span data-ttu-id="8b9ae-107">**Objectif :** vous créez un projet distinct pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-107">**Purpose:** You create a separate project for the orchestration.</span></span> <span data-ttu-id="8b9ae-108">Cela s'avère utile lorsque plusieurs personnes travaillent sur une même solution.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-108">This is helpful when you have several different people working on one solution.</span></span> <span data-ttu-id="8b9ae-109">Dans cette leçon, vous utilisez la nouvelle orchestration pour automatiser le processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-109">You use the new orchestration to automate the business process in this lesson.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b9ae-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8b9ae-110">Prerequisites</span></span>  
 <span data-ttu-id="8b9ae-111">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="8b9ae-111">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="8b9ae-112">Avant de commencer cette étape, vous devez effectuer [leçon 1 : définir des schémas et un mappage](../core/lesson-1-define-schemas-and-a-map.md).</span><span class="sxs-lookup"><span data-stu-id="8b9ae-112">Before you begin this step you must complete [Lesson 1: Define Schemas and a Map](../core/lesson-1-define-schemas-and-a-map.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8b9ae-113">Procédures</span><span class="sxs-lookup"><span data-stu-id="8b9ae-113">Procedures</span></span>  
 <span data-ttu-id="8b9ae-114">Si vous avez fermé la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre, suivez la procédure « pour ouvrir le projet Visual Studio » dans [étape 2 : création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-114">If you have closed the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] window, follow the procedure “To open the Visual Studio project” in [Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) to open it.</span></span>  
  
#### <a name="to-add-another-project-to-your-solution"></a><span data-ttu-id="8b9ae-115">Pour ajouter un autre projet à votre solution</span><span class="sxs-lookup"><span data-stu-id="8b9ae-115">To add another project to your solution</span></span>  
  
1.  <span data-ttu-id="8b9ae-116">À partir de Visual Studio, sur le **fichier** menu, pointez sur **ajouter**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-116">From Visual Studio, on the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="8b9ae-117">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b9ae-117">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8b9ae-118">Utiliser</span><span class="sxs-lookup"><span data-stu-id="8b9ae-118">Use this</span></span>|<span data-ttu-id="8b9ae-119">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="8b9ae-119">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8b9ae-120">**Modèles installés**</span><span class="sxs-lookup"><span data-stu-id="8b9ae-120">**Installed Templates**</span></span>|<span data-ttu-id="8b9ae-121">Cliquez sur **projets BizTalk**, puis cliquez sur **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-121">Click **BizTalk Projects**, and then click **Empty BizTalk Server Project**.</span></span>|  
    |<span data-ttu-id="8b9ae-122">**Nom**</span><span class="sxs-lookup"><span data-stu-id="8b9ae-122">**Name**</span></span>|<span data-ttu-id="8b9ae-123">Tapez `EAIOrchestration`.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-123">Type `EAIOrchestration`.</span></span>|  
    |<span data-ttu-id="8b9ae-124">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="8b9ae-124">**Location**</span></span>|<span data-ttu-id="8b9ae-125">Tapez `C:\BTSTutorials\EAISolution`.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-125">Type `C:\BTSTutorials\EAISolution`.</span></span>|  
  
3.  <span data-ttu-id="8b9ae-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-126">Click **OK**.</span></span>  
  
#### <a name="to-add-an-orchestration"></a><span data-ttu-id="8b9ae-127">Pour ajouter une orchestration</span><span class="sxs-lookup"><span data-stu-id="8b9ae-127">To add an orchestration</span></span>  
  
1.  <span data-ttu-id="8b9ae-128">Dans l’Explorateur de solutions, cliquez sur **EAIOrchestration**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-128">In Solution Explorer, right-click **EAIOrchestration**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="8b9ae-129">Dans le **ajouter un nouvel élément - EAIOrchestration** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="8b9ae-129">In the **Add New Item - EAIOrchestration** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="8b9ae-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="8b9ae-130">Use this</span></span>|<span data-ttu-id="8b9ae-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="8b9ae-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="8b9ae-132">**Modèles installés**</span><span class="sxs-lookup"><span data-stu-id="8b9ae-132">**Installed Templates**</span></span>|<span data-ttu-id="8b9ae-133">Cliquez sur **fichiers d’Orchestration**, puis cliquez sur **Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-133">Click **Orchestration Files**, and then click **BizTalk Orchestration**.</span></span>|  
    |<span data-ttu-id="8b9ae-134">**Nom**</span><span class="sxs-lookup"><span data-stu-id="8b9ae-134">**Name**</span></span>|<span data-ttu-id="8b9ae-135">Type **EAIProcess.odx**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-135">Type **EAIProcess.odx**.</span></span>|  
  
3.  <span data-ttu-id="8b9ae-136">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-136">Click **Add**.</span></span>  
  
     <span data-ttu-id="8b9ae-137">Le Concepteur d'orchestration s'ouvre.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-137">Orchestration Designer opens.</span></span> <span data-ttu-id="8b9ae-138">La figure suivante illustre le Concepteur d'orchestration avec l'orchestration EAIProcess.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-138">The following figure shows Orchestration Designer with the EAIProcess orchestration.</span></span>  
  
     <span data-ttu-id="8b9ae-139">![Nouvelle orchestration](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")</span><span class="sxs-lookup"><span data-stu-id="8b9ae-139">![New orchestration](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="8b9ae-140">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="8b9ae-140">What did I just do?</span></span>  
 <span data-ttu-id="8b9ae-141">Au cours de cette étape, vous avez ajouté un deuxième projet à la solution EAI.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-141">In this step, you added a second project to the EAI solution.</span></span> <span data-ttu-id="8b9ae-142">Puis vous avez ajouté une orchestration au nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="8b9ae-142">Then you added an orchestration to the new project.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8b9ae-143">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8b9ae-143">Next Steps</span></span>  
 <span data-ttu-id="8b9ae-144">Vous définissez le processus d’entreprise dans [étape 2 : définir le processus d’entreprise](../core/step-2-define-the-business-process.md).</span><span class="sxs-lookup"><span data-stu-id="8b9ae-144">You define the business process in [Step 2: Define the Business Process](../core/step-2-define-the-business-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9ae-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b9ae-145">See Also</span></span>  
 <span data-ttu-id="8b9ae-146">[Étape 2 : Définir le processus d’entreprise](../core/step-2-define-the-business-process.md) </span><span class="sxs-lookup"><span data-stu-id="8b9ae-146">[Step 2: Define the Business Process](../core/step-2-define-the-business-process.md) </span></span>  
 <span data-ttu-id="8b9ae-147">[Étape 3 : Ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="8b9ae-147">[Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span></span>  
 [<span data-ttu-id="8b9ae-148">Étape 4 : Création du projet EAIOrchestration</span><span class="sxs-lookup"><span data-stu-id="8b9ae-148">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)