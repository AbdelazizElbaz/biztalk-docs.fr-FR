---
title: "Étape 1 : Création du projet EAISchemas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a14ee61-fa27-4f03-997e-42c34a77afee
caps.latest.revision: "55"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e73da569196d564cd9bb0886c8c7f97d94fe9614
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-create-eaischemas-project"></a><span data-ttu-id="4bca1-102">Étape 1 : Création du projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="4bca1-102">Step 1: Create EAISchemas Project</span></span>
<span data-ttu-id="4bca1-103">![Étape 1 sur 5](../core/media/step-1of5.gif "Step_1of5")</span><span class="sxs-lookup"><span data-stu-id="4bca1-103">![Step 1 of 5](../core/media/step-1of5.gif "Step_1of5")</span></span>  
  
 <span data-ttu-id="4bca1-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="4bca1-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="4bca1-105">**Objectif :** dans cette étape, vous créez un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution et un projet.</span><span class="sxs-lookup"><span data-stu-id="4bca1-105">**Objective:** In this step, you create a new [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] solution and a project.</span></span>  
  
 <span data-ttu-id="4bca1-106">**Objectif :** le système de projet BizTalk vous permet de créer tout ou partie d’un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] application ou solution d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="4bca1-106">**Purpose:** You use the BizTalk project system to create part or all of a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] application or business solution.</span></span> <span data-ttu-id="4bca1-107">L'élément principal d'une telle solution est un projet BizTalk : un ensemble d'éléments, tels que des schémas, des orchestrations, des types de messages Web, des classes, des pipelines, des mappages et des références que vous pouvez créer et générer dans un assembly que vous déployez ensuite.</span><span class="sxs-lookup"><span data-stu-id="4bca1-107">The core element of any such solution is a BizTalk project—a collection of items, such as schemas, orchestrations, Web message types, classes, pipelines, maps, and references that you can build and generate into an assembly before deploying it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4bca1-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4bca1-108">Prerequisites</span></span>  
 <span data-ttu-id="4bca1-109">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="4bca1-109">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="4bca1-110">Avant de commencer cette étape, vous devez effectuer les étapes de [avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="4bca1-110">Before you begin this step you must complete the steps in [Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="4bca1-111">Procédures</span><span class="sxs-lookup"><span data-stu-id="4bca1-111">Procedures</span></span>  
  
#### <a name="to-create-a-new-visual-studio-solutionproject"></a><span data-ttu-id="4bca1-112">Pour créer un projet/une solution dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4bca1-112">To create a new Visual Studio solution/project</span></span>  
  
1.  <span data-ttu-id="4bca1-113">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-113">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="4bca1-114">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-114">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="4bca1-115">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4bca1-115">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="4bca1-116">Utiliser</span><span class="sxs-lookup"><span data-stu-id="4bca1-116">Use this</span></span>|<span data-ttu-id="4bca1-117">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="4bca1-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="4bca1-118">**Modèles installés**</span><span class="sxs-lookup"><span data-stu-id="4bca1-118">**Installed Templates**</span></span>|<span data-ttu-id="4bca1-119">Cliquez sur **projets BizTalk**, puis cliquez sur **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-119">Click **BizTalk Projects**, then click **Empty BizTalk Server Project**.</span></span>|  
    |<span data-ttu-id="4bca1-120">**Nom**</span><span class="sxs-lookup"><span data-stu-id="4bca1-120">**Name**</span></span>|<span data-ttu-id="4bca1-121">Type **EAISchemas**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-121">Type **EAISchemas**.</span></span>|  
    |<span data-ttu-id="4bca1-122">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="4bca1-122">**Location**</span></span>|<span data-ttu-id="4bca1-123">Type **C:\tutorial\Lessons**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-123">Type **C:\tutorial\Lessons**.</span></span>|  
    |<span data-ttu-id="4bca1-124">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="4bca1-124">**Solution Name**</span></span>|<span data-ttu-id="4bca1-125">Type **EAISolution**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-125">Type **EAISolution**.</span></span>|  
    |<span data-ttu-id="4bca1-126">**Créer le répertoire pour la solution**</span><span class="sxs-lookup"><span data-stu-id="4bca1-126">**Create directory for solution**</span></span>|<span data-ttu-id="4bca1-127">(sélectionnée)</span><span class="sxs-lookup"><span data-stu-id="4bca1-127">(selected)</span></span>|  
  
4.  <span data-ttu-id="4bca1-128">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-128">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="4bca1-129">Dans le menu **Fichier** , cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="4bca1-129">On the **File** menu, click **Save All**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="4bca1-130">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="4bca1-130">What did I just do?</span></span>  
 <span data-ttu-id="4bca1-131">Au cours de cette étape, vous avez ouvert un nouveau projet et une solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bca1-131">In this step, you opened a new project and a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4bca1-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="4bca1-132">Next Steps</span></span>  
 <span data-ttu-id="4bca1-133">Vous créez le schéma du message de demande de réapprovisionnement de stock.</span><span class="sxs-lookup"><span data-stu-id="4bca1-133">You create the schema for the inventory replenishment request message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bca1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bca1-134">See Also</span></span>  
 <span data-ttu-id="4bca1-135">[Avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="4bca1-135">[Before You Begin the Tutorial](../core/before-you-begin-the-tutorial.md) </span></span>  
 <span data-ttu-id="4bca1-136">[Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="4bca1-136">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="4bca1-137">[Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="4bca1-137">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 <span data-ttu-id="4bca1-138">[Étape 4 : Créer la carte](../core/step-4-create-the-map.md) </span><span class="sxs-lookup"><span data-stu-id="4bca1-138">[Step 4: Create the Map](../core/step-4-create-the-map.md) </span></span>  
 <span data-ttu-id="4bca1-139">[Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="4bca1-139">[Step 5: Build the EAISchemas Project](../core/step-5-build-the-eaischemas-project.md) </span></span>  
 <span data-ttu-id="4bca1-140">[Outils de développement](../core/developer-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4bca1-140">[Developer Tools](../core/developer-tools.md) </span></span>  
 [<span data-ttu-id="4bca1-141">Utilisation des projets BizTalk</span><span class="sxs-lookup"><span data-stu-id="4bca1-141">Working with BizTalk Projects</span></span>](../core/working-with-biztalk-projects.md)