---
title: "Formes d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer]
- Loop shape [Orchestration Designer]
- Throw Exception shape [Orchestration Designer]
- Expression shape [Orchestration Designer]
- Decide shape [Orchestration Designer]
- Receive shape [Orchestration Designer]
- Compensate shape [Orchestration Designer]
- orchestrations, shapes
- Suspend shape [Orchestration Designer]
- Send shape [Orchestration Designer]
- Group shape [Orchestration Designer]
- Listen shape [Orchestration Designer]
- shapes, about shapes
- Construct Message shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer]
- Call Rules shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer]
- Transform shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Role Link shape [Orchestration Designer]
- Call Orchestration shape [Orchestration Designer]
- Port shape [Orchestration Designer]
- shapes
- Scope shape [Orchestration Designer]
- Terminate shape [Orchestration Designer]
- Orchestration Designer, shapes
- Insufficient Configuration Smart Tag [Orchestration Designer]
ms.assetid: a1d03baa-a267-499d-94fc-700b3e959458
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 181656208b757c595feb9d19ee786fe91f1b78f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-shapes"></a><span data-ttu-id="5a5d4-102">Formes d'orchestration</span><span class="sxs-lookup"><span data-stu-id="5a5d4-102">Orchestration Shapes</span></span>
<span data-ttu-id="5a5d4-103">Le Concepteur d'orchestration est un outil visuel permettant de créer des orchestrations</span><span class="sxs-lookup"><span data-stu-id="5a5d4-103">Orchestration Designer is a visual tool for creating orchestrations.</span></span> <span data-ttu-id="5a5d4-104">Il fournit plusieurs formes que vous pouvez placer sur la surface de conception en tant que représentations visuelles d'actions sous-jacentes, et qui vous permettent de concevoir et d'implémenter efficacement une orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-104">It provides several shapes that you can place on the design surface as visual representations of underlying actions, and they can help you to efficiently design and implement an orchestration.</span></span>  
  
 <span data-ttu-id="5a5d4-105">**Action de Configuration insuffisante**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-105">**Insufficient Configuration Action**</span></span>  
  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!NOTE]
>  <span data-ttu-id="5a5d4-106">L’action relative à une configuration insuffisante s’affiche dans le Concepteur d’orchestration lorsque celui-ci détecte que la forme associée n’est pas complètement configurée.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-106">The Insufficient Configuration Action is displayed in the Orchestration designer when the Orchestration Designer detects that the associated shape is not completely configured.</span></span> <span data-ttu-id="5a5d4-107">Si une forme dans une orchestration n'est pas complètement configurée, l'orchestration associée ne se compilera pas.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-107">If a shape in an Orchestration is not completely configured then the associated Orchestration will not compile.</span></span>  
  
 <span data-ttu-id="5a5d4-108">Le tableau suivant répertorie les formes disponibles et propose une brève description de la fonction de chacune d'elles.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-108">The following table lists the available shapes, along with a brief description of the function of each shape.</span></span>  
  
|<span data-ttu-id="5a5d4-109">Graphique à base de formes</span><span class="sxs-lookup"><span data-stu-id="5a5d4-109">Shape</span></span>|<span data-ttu-id="5a5d4-110">Nom de la forme</span><span class="sxs-lookup"><span data-stu-id="5a5d4-110">Shape Name</span></span>|<span data-ttu-id="5a5d4-111">Fonction</span><span class="sxs-lookup"><span data-stu-id="5a5d4-111">Purpose</span></span>|  
|-----------|----------------|-------------|  
|![](../core/media/ebiz-orch-callorchestrat.gif "ebiz_orch_callorchestrat")|<span data-ttu-id="5a5d4-112">**Appeler Orchestration**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-112">**Call Orchestration**</span></span>|<span data-ttu-id="5a5d4-113">Permet à l'orchestration d'en appeler une autre de façon synchronisée.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-113">Enables your orchestration to call another orchestration synchronously.</span></span>|  
|![](../core/media/ebiz-orch-call-rules.gif "ebiz_orch_call_rules")|<span data-ttu-id="5a5d4-114">**Appeler règles**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-114">**Call Rules**</span></span>|<span data-ttu-id="5a5d4-115">Permet de configurer une stratégie de règles d'entreprise à exécuter dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-115">Enables you to configure a Business Rules policy to be executed in your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-compensate.gif "ebiz_orch_compensate")|<span data-ttu-id="5a5d4-116">**Compenser**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-116">**Compensate**</span></span>|<span data-ttu-id="5a5d4-117">Permet d'appeler un code pour annuler ou compenser les opérations déjà effectuées par l'orchestration en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-117">Enables you to call code to undo or compensate for operations already performed by the orchestration when an error occurs.</span></span>|  
|![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")|<span data-ttu-id="5a5d4-118">**Forme construire un Message**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-118">**Construct Message**</span></span>|<span data-ttu-id="5a5d4-119">Permet de construire un message.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-119">Enables you to construct a message.</span></span>|  
|![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")|<span data-ttu-id="5a5d4-120">**Décider**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-120">**Decide**</span></span>|<span data-ttu-id="5a5d4-121">Permet d'exécuter la branche sous certaines conditions dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-121">Enables you to conditionally branch in your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")|<span data-ttu-id="5a5d4-122">**Délai**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-122">**Delay**</span></span>|<span data-ttu-id="5a5d4-123">Permet de créer des délais d'attente dans l'orchestration en fonction d'un intervalle.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-123">Enables you to build delays in your orchestration based on a time-out interval.</span></span>|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|<span data-ttu-id="5a5d4-124">**Expression**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-124">**Expression**</span></span>|<span data-ttu-id="5a5d4-125">Permet d'affecter des valeurs aux variables ou d'exécuter des appels .NET.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-125">Enables you to assign values to variables or make .NET calls.</span></span>|  
|![](../core/media/ebiz-orch-group.gif "ebiz_orch_group")|<span data-ttu-id="5a5d4-126">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-126">**Group**</span></span>|<span data-ttu-id="5a5d4-127">Vous permet de regrouper des opérations dans une seule unité réductible et développable pour des raisons de commodité visuelle.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-127">Enables you to group operations into a single collapsible and expandable unit for visual convenience.</span></span>|  
|![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")|<span data-ttu-id="5a5d4-128">**Écouter**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-128">**Listen**</span></span>|<span data-ttu-id="5a5d4-129">Permet à l'orchestration d'exécuter la branche sous certaines conditions selon les messages reçus ou l'expiration du délai.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-129">Enables your orchestration to conditionally branch depending on messages received or the expiration of a timeout period.</span></span>|  
|![](../core/media/ebiz-orch-loop.gif "ebiz_orch_loop")|<span data-ttu-id="5a5d4-130">**Boucle**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-130">**Loop**</span></span>|<span data-ttu-id="5a5d4-131">Permet à l'orchestration de boucler jusqu'à ce que la condition soit remplie.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-131">Enables your orchestration to loop until a condition is met.</span></span>|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|<span data-ttu-id="5a5d4-132">**Assignation du message**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-132">**Message Assignment**</span></span>|<span data-ttu-id="5a5d4-133">Permet d'attribuer des valeurs de message.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-133">Enables you to assign message values.</span></span>|  
|![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")|<span data-ttu-id="5a5d4-134">**Actions parallèles**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-134">**Parallel Actions**</span></span>|<span data-ttu-id="5a5d4-135">Permet à l'orchestration d'exécuter plusieurs opérations indépendamment les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-135">Enables your orchestration to perform two or more operations independently of each other.</span></span>|  
|![](../core/media/ebiz-orch-port.gif "ebiz_orch_port")|<span data-ttu-id="5a5d4-136">**Port**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-136">**Port**</span></span>|<span data-ttu-id="5a5d4-137">Définit le moment et le mode de transmission des messages.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-137">Defines where and how messages are transmitted.</span></span>|  
|![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")|<span data-ttu-id="5a5d4-138">**Réception**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-138">**Receive**</span></span>|<span data-ttu-id="5a5d4-139">Permet de recevoir un message dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-139">Enables you to receive a message in your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-rolelink.gif "ebiz_orch_rolelink")|<span data-ttu-id="5a5d4-140">**Lien de rôle**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-140">**Role Link**</span></span>|<span data-ttu-id="5a5d4-141">Permet de créer un ensemble de ports communiquant avec le même partenaire logique, éventuellement via des transports ou points de terminaison différents.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-141">Enables you to create a collection of ports that communicate with the same logical partner, perhaps through different transports or endpoints.</span></span>|  
|![](../core/media/ebiz-orch-scope.gif "ebiz_orch_scope")|<span data-ttu-id="5a5d4-142">**Portée**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-142">**Scope**</span></span>|<span data-ttu-id="5a5d4-143">Fournit un cadre pour la gestion des transactions et des exceptions.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-143">Provides a framework for transactions and exception handling.</span></span>|  
|![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")|<span data-ttu-id="5a5d4-144">**Envoyer**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-144">**Send**</span></span>|<span data-ttu-id="5a5d4-145">Permet d'envoyer un message à partir de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-145">Enables you to send a message from your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-strtorchestrat.gif "ebiz_orch_strtorchestrat")|<span data-ttu-id="5a5d4-146">**Démarrer Orchestration**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-146">**Start Orchestration**</span></span>|<span data-ttu-id="5a5d4-147">Permet l’orchestration à appeler une autre orchestration de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-147">Enables your orchestration to call another orchestration asynchronously.</span></span>|  
|![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")|<span data-ttu-id="5a5d4-148">**Suspendre**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-148">**Suspend**</span></span>|<span data-ttu-id="5a5d4-149">Suspend l'opération de l'orchestration afin de permettre une intervention en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-149">Suspends the operation of your orchestration to enable intervention in the event of some error condition.</span></span>|  
|![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")|<span data-ttu-id="5a5d4-150">**Arrêter**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-150">**Terminate**</span></span>|<span data-ttu-id="5a5d4-151">Permet de mettre fin immédiatement à l'opération de l'orchestration en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-151">Enables you to immediately end the operation of your orchestration in the event of some error condition.</span></span>|  
|![](../core/media/ebiz-orch-throwexcept.gif "ebiz_orch_throwexcept")|<span data-ttu-id="5a5d4-152">**Lever Exception**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-152">**Throw Exception**</span></span>|<span data-ttu-id="5a5d4-153">Permet de lever une exception de façon explicite en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-153">Enables you to explicitly throw an exception in the event of an error.</span></span>|  
|![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")|<span data-ttu-id="5a5d4-154">**Transformation**</span><span class="sxs-lookup"><span data-stu-id="5a5d4-154">**Transform**</span></span>|<span data-ttu-id="5a5d4-155">Vous permet de mapper les champs des messages existants dans les nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="5a5d4-155">Enables you to map the fields from existing messages into new messages.</span></span>|