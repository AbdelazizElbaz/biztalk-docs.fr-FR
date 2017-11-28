---
title: "Tâche 3 : Configurer l’envoi et réception Shapes1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e258d22-755b-48a4-9f9e-e9398f6b68b1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c730cc6bc5cb11c27152613f331bda6b15be390
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-3-configure-the-send-and-receive-shapes"></a><span data-ttu-id="a021d-102">Tâche 3 : Configurer l’envoi et réception des formes</span><span class="sxs-lookup"><span data-stu-id="a021d-102">Task 3: Configure the Send and Receive Shapes</span></span>
<span data-ttu-id="a021d-103">La procédure suivante permet de configurer les formes Envoi et Réception.</span><span class="sxs-lookup"><span data-stu-id="a021d-103">Use the following procedure to configure the Send and Receive shapes.</span></span>  
  
### <a name="to-configure-the-send-and-receive-shapes"></a><span data-ttu-id="a021d-104">Pour configurer les formes Envoi et Réception</span><span class="sxs-lookup"><span data-stu-id="a021d-104">To configure the Send and Receive shapes</span></span>  
  
1.  <span data-ttu-id="a021d-105">Faites glisser les formes Envoi et Réception de la boîte à outils sur le centre de l'orchestration dans l'ordre suivant.</span><span class="sxs-lookup"><span data-stu-id="a021d-105">Drag Send and Receive shapes from the tool box into the center of the orchestration in the following order.</span></span>  
  
2.  <span data-ttu-id="a021d-106">Définissez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="a021d-106">Set the following parameters:</span></span>  
  
    |<span data-ttu-id="a021d-107">Graphique à base de formes</span><span class="sxs-lookup"><span data-stu-id="a021d-107">Shape</span></span>|<span data-ttu-id="a021d-108">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-108">Name</span></span>|<span data-ttu-id="a021d-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="a021d-109">Setting</span></span>|  
    |-----------|----------|-------------|  
    |<span data-ttu-id="a021d-110">Receive1</span><span class="sxs-lookup"><span data-stu-id="a021d-110">Receive1</span></span>|<span data-ttu-id="a021d-111">Activate</span><span class="sxs-lookup"><span data-stu-id="a021d-111">Activate</span></span>|<span data-ttu-id="a021d-112">True</span><span class="sxs-lookup"><span data-stu-id="a021d-112">True</span></span>|  
    ||<span data-ttu-id="a021d-113">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-113">Message</span></span>|<span data-ttu-id="a021d-114">BeginDocMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-114">BeginDocMsg</span></span>|  
    ||<span data-ttu-id="a021d-115">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-115">Name</span></span>|<span data-ttu-id="a021d-116">ReceiveBeginDoc</span><span class="sxs-lookup"><span data-stu-id="a021d-116">ReceiveBeginDoc</span></span>|  
    ||<span data-ttu-id="a021d-117">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-117">Operation</span></span>|<span data-ttu-id="a021d-118">BeginDoc.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="a021d-118">BeginDoc.Operation_1.Request</span></span>|  
    |<span data-ttu-id="a021d-119">Send1</span><span class="sxs-lookup"><span data-stu-id="a021d-119">Send1</span></span>|<span data-ttu-id="a021d-120">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-120">Message</span></span>|<span data-ttu-id="a021d-121">BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-121">BeginDocSessionMsg</span></span>|  
    ||<span data-ttu-id="a021d-122">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-122">Name</span></span>|<span data-ttu-id="a021d-123">SendBeginDoc</span><span class="sxs-lookup"><span data-stu-id="a021d-123">SendBeginDoc</span></span>|  
    ||<span data-ttu-id="a021d-124">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-124">Operation</span></span>|<span data-ttu-id="a021d-125">JDEPort.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="a021d-125">JDEPort.Operation_1.Request</span></span>|  
    |<span data-ttu-id="a021d-126">Receive2</span><span class="sxs-lookup"><span data-stu-id="a021d-126">Receive2</span></span>|<span data-ttu-id="a021d-127">Activate</span><span class="sxs-lookup"><span data-stu-id="a021d-127">Activate</span></span>|<span data-ttu-id="a021d-128">False</span><span class="sxs-lookup"><span data-stu-id="a021d-128">False</span></span>|  
    ||<span data-ttu-id="a021d-129">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-129">Message</span></span>|<span data-ttu-id="a021d-130">BeginDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-130">BeginDocResponseMsg</span></span>|  
    ||<span data-ttu-id="a021d-131">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-131">Name</span></span>|<span data-ttu-id="a021d-132">ReceiveBeginDocResponse</span><span class="sxs-lookup"><span data-stu-id="a021d-132">ReceiveBeginDocResponse</span></span>|  
    ||<span data-ttu-id="a021d-133">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-133">Operation</span></span>|<span data-ttu-id="a021d-134">JDEPort.Operation_1.Response</span><span class="sxs-lookup"><span data-stu-id="a021d-134">JDEPort.Operation_1.Response</span></span>|  
    |<span data-ttu-id="a021d-135">Send2</span><span class="sxs-lookup"><span data-stu-id="a021d-135">Send2</span></span>|<span data-ttu-id="a021d-136">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-136">Message</span></span>|<span data-ttu-id="a021d-137">EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-137">EditLineSessionMsg</span></span>|  
    ||<span data-ttu-id="a021d-138">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-138">Name</span></span>|<span data-ttu-id="a021d-139">SendEditLine</span><span class="sxs-lookup"><span data-stu-id="a021d-139">SendEditLine</span></span>|  
    ||<span data-ttu-id="a021d-140">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-140">Operation</span></span>|<span data-ttu-id="a021d-141">JDEPort.Operation_2.Request</span><span class="sxs-lookup"><span data-stu-id="a021d-141">JDEPort.Operation_2.Request</span></span>|  
    |<span data-ttu-id="a021d-142">Receive3</span><span class="sxs-lookup"><span data-stu-id="a021d-142">Receive3</span></span>|<span data-ttu-id="a021d-143">Activate</span><span class="sxs-lookup"><span data-stu-id="a021d-143">Activate</span></span>|<span data-ttu-id="a021d-144">False</span><span class="sxs-lookup"><span data-stu-id="a021d-144">False</span></span>|  
    ||<span data-ttu-id="a021d-145">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-145">Message</span></span>|<span data-ttu-id="a021d-146">EditLineResponseMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-146">EditLineResponseMsg</span></span>|  
    ||<span data-ttu-id="a021d-147">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-147">Name</span></span>|<span data-ttu-id="a021d-148">ReceiveEditLine</span><span class="sxs-lookup"><span data-stu-id="a021d-148">ReceiveEditLine</span></span>|  
    ||<span data-ttu-id="a021d-149">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-149">Operation</span></span>|<span data-ttu-id="a021d-150">JDEPort.Operation_2.Response</span><span class="sxs-lookup"><span data-stu-id="a021d-150">JDEPort.Operation_2.Response</span></span>|  
    |<span data-ttu-id="a021d-151">Send3</span><span class="sxs-lookup"><span data-stu-id="a021d-151">Send3</span></span>|<span data-ttu-id="a021d-152">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-152">Message</span></span>|<span data-ttu-id="a021d-153">EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-153">EndDocSessionMsg</span></span>|  
    ||<span data-ttu-id="a021d-154">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-154">Name</span></span>|<span data-ttu-id="a021d-155">SendEndDoc</span><span class="sxs-lookup"><span data-stu-id="a021d-155">SendEndDoc</span></span>|  
    ||<span data-ttu-id="a021d-156">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-156">Operation</span></span>|<span data-ttu-id="a021d-157">JDEPort.Operation_3.Request</span><span class="sxs-lookup"><span data-stu-id="a021d-157">JDEPort.Operation_3.Request</span></span>|  
    |<span data-ttu-id="a021d-158">Receive4</span><span class="sxs-lookup"><span data-stu-id="a021d-158">Receive4</span></span>|<span data-ttu-id="a021d-159">Activate</span><span class="sxs-lookup"><span data-stu-id="a021d-159">Activate</span></span>|<span data-ttu-id="a021d-160">False</span><span class="sxs-lookup"><span data-stu-id="a021d-160">False</span></span>|  
    ||<span data-ttu-id="a021d-161">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-161">Message</span></span>|<span data-ttu-id="a021d-162">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-162">EndDocResponseMsg</span></span>|  
    ||<span data-ttu-id="a021d-163">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-163">Name</span></span>|<span data-ttu-id="a021d-164">ReceiveEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="a021d-164">ReceiveEndDocResponse</span></span>|  
    ||<span data-ttu-id="a021d-165">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-165">Operation</span></span>|<span data-ttu-id="a021d-166">JDEPort.Operation_3.Response</span><span class="sxs-lookup"><span data-stu-id="a021d-166">JDEPort.Operation_3.Response</span></span>|  
    |<span data-ttu-id="a021d-167">Send4</span><span class="sxs-lookup"><span data-stu-id="a021d-167">Send4</span></span>|<span data-ttu-id="a021d-168">Message</span><span class="sxs-lookup"><span data-stu-id="a021d-168">Message</span></span>|<span data-ttu-id="a021d-169">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="a021d-169">EndDocResponseMsg</span></span>|  
    ||<span data-ttu-id="a021d-170">Nom</span><span class="sxs-lookup"><span data-stu-id="a021d-170">Name</span></span>|<span data-ttu-id="a021d-171">SendEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="a021d-171">SendEndDocResponse</span></span>|  
    ||<span data-ttu-id="a021d-172">Opération</span><span class="sxs-lookup"><span data-stu-id="a021d-172">Operation</span></span>|<span data-ttu-id="a021d-173">EndDocOut.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="a021d-173">EndDocOut.Operation_1.Request</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a021d-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a021d-174">See Also</span></span>  
 <span data-ttu-id="a021d-175">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports2.md) </span><span class="sxs-lookup"><span data-stu-id="a021d-175">[Task 1: Create the Ports](../core/task-1-create-the-ports2.md) </span></span>  
 <span data-ttu-id="a021d-176">[Tâche 2 : Créer les Messages](../core/task-2-create-the-messages1.md) </span><span class="sxs-lookup"><span data-stu-id="a021d-176">[Task 2: Create the Messages](../core/task-2-create-the-messages1.md) </span></span>  
 <span data-ttu-id="a021d-177">[Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape2.md) </span><span class="sxs-lookup"><span data-stu-id="a021d-177">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape2.md) </span></span>  
 [<span data-ttu-id="a021d-178">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="a021d-178">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape1.md)