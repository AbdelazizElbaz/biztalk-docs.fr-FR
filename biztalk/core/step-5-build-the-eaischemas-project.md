---
title: "Étape 5 : Créer le projet EAISchemas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c20cd368-7446-4861-8d71-5bc25ce408a2
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 394d9df78f7064df8501ed43149bd26793533c47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-build-the-eaischemas-project"></a><span data-ttu-id="13641-102">Étape 5 : Création du projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="13641-102">Step 5: Build the EAISchemas Project</span></span>
<span data-ttu-id="13641-103">![L’étape 5 de 5](../core/media/step-5of5.gif "Step_5of5")</span><span class="sxs-lookup"><span data-stu-id="13641-103">![Step 5 of 5](../core/media/step-5of5.gif "Step_5of5")</span></span>  
  
 <span data-ttu-id="13641-104">**Durée :** 6 minutes</span><span class="sxs-lookup"><span data-stu-id="13641-104">**Time to complete:** 6 minutes</span></span>  
  
 <span data-ttu-id="13641-105">**Objectif :** dans cette étape, vous compilez le projet EAISchemas.</span><span class="sxs-lookup"><span data-stu-id="13641-105">**Objective:** In this step, you compile the EAISchemas project.</span></span>  
  
 <span data-ttu-id="13641-106">**Objectif :** l’aspect le plus important de Microsoft BizTalk Server et le .NET Framework est que tous les artefacts de BizTalk Server ; mappages, schémas, orchestrations et pipelines, sont compilés dans des assemblys .NET.</span><span class="sxs-lookup"><span data-stu-id="13641-106">**Purpose:** The most important aspect of Microsoft BizTalk Server and the .NET Framework is that all BizTalk Server artifacts; maps, schemas, orchestrations, and pipelines, get compiled into .NET assemblies.</span></span> <span data-ttu-id="13641-107">Les deux principales implications d'une telle conception sont que ces assemblys doivent avoir des noms forts. De ce fait, ils suivent également les règles d'établissement de versions .NET.</span><span class="sxs-lookup"><span data-stu-id="13641-107">The two most important implications of this design are that these assemblies must have strong names, and because of that, they also follow .NET versioning rules.</span></span> <span data-ttu-id="13641-108">La principale implication de tout ceci est qu'un projet BizTalk, une fois élaboré à partir d'une version donnée d'un autre projet .NET ou assembly (incluant des projets BizTalk), continue à utiliser cette version jusqu'à ce qu'il soit reconstruit à partir d'une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="13641-108">The main implication of this is that a BizTalk project, once built against a particular version of another .NET project or assembly (including BizTalk projects), continues to use that version until it has been rebuilt against a newer version.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13641-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="13641-109">Prerequisites</span></span>  
 <span data-ttu-id="13641-110">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="13641-110">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="13641-111">Avant de commencer cette étape, vous devez exécuter les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="13641-111">Before you begin this step you must complete the following steps:</span></span>  
  
    -   [<span data-ttu-id="13641-112">Étape 1 : Création du projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="13641-112">Step 1: Create EAISchemas Project</span></span>](../core/step-1-create-eaischemas-project.md)  
  
    -   [<span data-ttu-id="13641-113">Étape 2 : Création du schéma de demande de stock</span><span class="sxs-lookup"><span data-stu-id="13641-113">Step 2: Create the Inventory Request Schema</span></span>](../core/step-2-create-the-inventory-request-schema.md) 
  
    -   [<span data-ttu-id="13641-114">Étape 3 : Créer le schéma de refus de demande</span><span class="sxs-lookup"><span data-stu-id="13641-114">Step 3: Create the Request Decline Schema</span></span>](../core/step-3-create-the-request-decline-schema.md)  
  
    -   [<span data-ttu-id="13641-115">Étape 4 : Créer la carte</span><span class="sxs-lookup"><span data-stu-id="13641-115">Step 4: Create the Map</span></span>](../core/step-4-create-the-map.md)  
  
## <a name="procedures"></a><span data-ttu-id="13641-116">Procédures</span><span class="sxs-lookup"><span data-stu-id="13641-116">Procedures</span></span>  
  
#### <a name="to-build-the-eaischemas-project"></a><span data-ttu-id="13641-117">Pour créer le projet EAISchemas</span><span class="sxs-lookup"><span data-stu-id="13641-117">To build the EAISchemas project</span></span>  
  
1.  <span data-ttu-id="13641-118">Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="13641-118">In Solution Explorer, right-click **EAISchemas**, and then click **Build**.</span></span>  
  
     <span data-ttu-id="13641-119">La partie inférieure de l'écran doit afficher :</span><span class="sxs-lookup"><span data-stu-id="13641-119">The bottom of the screen should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ```  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="13641-120">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="13641-120">What did I just do?</span></span>  
 <span data-ttu-id="13641-121">Au cours de cette étape, vous avez créé le projet EAIOSchémas pour générer un fichier d'assembly (DLL).</span><span class="sxs-lookup"><span data-stu-id="13641-121">In this step, you built the EAISchemas project to generate an assembly file (DLL).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="13641-122">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="13641-122">Next Steps</span></span>  
 <span data-ttu-id="13641-123">Vous créez le processus d’entreprise qui évalue le contenu du message de demande de réapprovisionnement de stock par rapport aux critères d’approbation dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md).</span><span class="sxs-lookup"><span data-stu-id="13641-123">You create the business process that evaluates the contents of the inventory replenishment request message against approval criteria in [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13641-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13641-124">See Also</span></span>  
 <span data-ttu-id="13641-125">[Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md) </span><span class="sxs-lookup"><span data-stu-id="13641-125">[Step 1: Create EAISchemas Project](../core/step-1-create-eaischemas-project.md) </span></span>  
 <span data-ttu-id="13641-126">[Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md) </span><span class="sxs-lookup"><span data-stu-id="13641-126">[Step 2: Create the Inventory Request Schema](../core/step-2-create-the-inventory-request-schema.md) </span></span>  
 <span data-ttu-id="13641-127">[Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md) </span><span class="sxs-lookup"><span data-stu-id="13641-127">[Step 3: Create the Request Decline Schema](../core/step-3-create-the-request-decline-schema.md) </span></span>  
 [<span data-ttu-id="13641-128">Étape 4 : Créer la carte</span><span class="sxs-lookup"><span data-stu-id="13641-128">Step 4: Create the Map</span></span>](../core/step-4-create-the-map.md)