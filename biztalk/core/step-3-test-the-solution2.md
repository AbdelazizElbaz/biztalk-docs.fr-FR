---
title: "Étape 3 : Tester la Solution2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30dbc7c9-3c5f-4953-b26f-5c41141c22ad
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c0e484a9f6af788775ec4ae7309965327378267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-test-the-solution"></a><span data-ttu-id="dc631-102">Étape 3 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="dc631-102">Step 3: Test the Solution</span></span>
<span data-ttu-id="dc631-103">![Étape 3 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span><span class="sxs-lookup"><span data-stu-id="dc631-103">![Step 3 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")</span></span>  
  
 <span data-ttu-id="dc631-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="dc631-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="dc631-105">**Objectif :** dans cette étape, vous testez comment la solution EAI traite les messages.</span><span class="sxs-lookup"><span data-stu-id="dc631-105">**Objective:** In this step, you test how the EAI solution processes messages.</span></span>  
  
 <span data-ttu-id="dc631-106">**Objectif :** dans cette étape, vous vérifiez que l’orchestration EAIProcess traite correctement les messages.</span><span class="sxs-lookup"><span data-stu-id="dc631-106">**Purpose:** In this step, you check that the EAIProcess orchestration processes messages correctly.</span></span> <span data-ttu-id="dc631-107">Pour ce faire, vous allez déposer des exemples de message dans l'emplacement de réception spécifié pour l'application IAE.</span><span class="sxs-lookup"><span data-stu-id="dc631-107">You do this by dropping sample messages into the receive location specified for the EAI application.</span></span> <span data-ttu-id="dc631-108">Lorsque la solution IAE fonctionne correctement, si l'orchestration EAIProcess reçoit un message de l'entrepôt demandant plus de 500 éléments, l'orchestration génère un message de refus de la demande.</span><span class="sxs-lookup"><span data-stu-id="dc631-108">If the EAI solution is working properly, if the EAIProcess orchestration receives a message from the warehouse requesting more than 500 items, the orchestration generates a decline request message.</span></span> <span data-ttu-id="dc631-109">Si l'orchestration EAIProcess reçoit un message de l'entrepôt demandant moins de 500 éléments, l'orchestration transmet le message au système ERP.</span><span class="sxs-lookup"><span data-stu-id="dc631-109">If the EAIProcess orchestration receives a message from the warehouse requesting fewer than 500 items, the orchestration passes the message on to the ERP system.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dc631-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="dc631-110">Prerequisites</span></span>  
 <span data-ttu-id="dc631-111">Avant de commencer cette étape, vous devez effectuer [étape 2 : configurer et démarrer l’Application](../core/step-2-configure-and-start-the-application1.md).</span><span class="sxs-lookup"><span data-stu-id="dc631-111">Before you begin this step you must complete [Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="dc631-112">Procédures</span><span class="sxs-lookup"><span data-stu-id="dc631-112">Procedures</span></span>  
  
#### <a name="to-test-the-eai-solution"></a><span data-ttu-id="dc631-113">Pour tester la solution IAE</span><span class="sxs-lookup"><span data-stu-id="dc631-113">To test the EAI solution</span></span>  
  
1.  <span data-ttu-id="dc631-114">Ouvrez l’Explorateur Windows et accédez à **C:\BTSTutorials\WareHouse**.</span><span class="sxs-lookup"><span data-stu-id="dc631-114">Open Windows Explorer, and navigate to **C:\BTSTutorials\WareHouse**.</span></span>  <span data-ttu-id="dc631-115">Ce dossier est créé pendant l'installation des fichiers de didacticiels.</span><span class="sxs-lookup"><span data-stu-id="dc631-115">This folder is created by installing the tutorial files.</span></span>  
  
2.  <span data-ttu-id="dc631-116">Copie **RequestInstance.XML** et collez-le dans **C:\BTSTutorials\WareHouse\Request**.</span><span class="sxs-lookup"><span data-stu-id="dc631-116">Copy **RequestInstance.XML** and paste it into **C:\BTSTutorials\WareHouse\Request**.</span></span>  
  
3.  <span data-ttu-id="dc631-117">Lorsque le fichier disparaît, consultez **C:\BTSTutorials\ERP\Request**.</span><span class="sxs-lookup"><span data-stu-id="dc631-117">When the file disappears, check **C:\BTSTutorials\ERP\Request**.</span></span>  
  
4.  <span data-ttu-id="dc631-118">Dans l’Explorateur Windows, accédez à **C:\BTSTutorials\WareHouse**.</span><span class="sxs-lookup"><span data-stu-id="dc631-118">In Windows Explorer, navigate to **C:\BTSTutorials\WareHouse**.</span></span>  
  
5.  <span data-ttu-id="dc631-119">Copie **RequestInstance (plus de limite). XML** et collez-le dans **C:\BTSTutorials\WareHouse\Request**.</span><span class="sxs-lookup"><span data-stu-id="dc631-119">Copy **RequestInstance(Over Limit).XML** and paste it into **C:\BTSTutorials\WareHouse\Request**.</span></span>  
  
6.  <span data-ttu-id="dc631-120">Lorsque le fichier disparaît, consultez **C:\BTSTutorials\WareHouse\RequestDecline**.</span><span class="sxs-lookup"><span data-stu-id="dc631-120">When the file disappears, check **C:\BTSTutorials\WareHouse\RequestDecline**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="dc631-121">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="dc631-121">What did I just do?</span></span>  
 <span data-ttu-id="dc631-122">Vous avez testé la solution IAE en plaçant des exemples de message dans l'emplacement de réception de l'application IAE.</span><span class="sxs-lookup"><span data-stu-id="dc631-122">You tested the EAI solution by placing sample messages in the receive location for the EAI application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc631-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc631-123">See Also</span></span>  
 <span data-ttu-id="dc631-124">[Étape 1 : Déployer des projets](../core/step-1-deploy-the-projects.md) </span><span class="sxs-lookup"><span data-stu-id="dc631-124">[Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md) </span></span>  
 [<span data-ttu-id="dc631-125">Étape 2 : Configurer et démarrer l’Application</span><span class="sxs-lookup"><span data-stu-id="dc631-125">Step 2: Configure and Start the Application</span></span>](../core/step-2-configure-and-start-the-application1.md)