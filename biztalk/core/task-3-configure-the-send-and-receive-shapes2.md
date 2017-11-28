---
title: "Tâche 3 : Configurer l’envoi et réception Shapes2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ebe7141-f2bd-4e6a-9204-d61bd64286af
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6923a90b43d1bdc3004a03ac588dd2410d81a3cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="task-3-configure-the-send-and-receive-shapes"></a><span data-ttu-id="73211-102">Tâche 3 : Configurer l’envoi et réception des formes</span><span class="sxs-lookup"><span data-stu-id="73211-102">Task 3: Configure the Send and Receive Shapes</span></span>
<span data-ttu-id="73211-103">La procédure suivante permet de configurer les formes Envoi et Réception.</span><span class="sxs-lookup"><span data-stu-id="73211-103">Use the following procedure to configure the Send and Receive shapes.</span></span>  
  
### <a name="to-configure-the-send-and-receive-shapes"></a><span data-ttu-id="73211-104">Pour configurer les formes Envoi et Réception</span><span class="sxs-lookup"><span data-stu-id="73211-104">To configure the Send and Receive shapes</span></span>  
  
1.  <span data-ttu-id="73211-105">Faites glisser les formes Envoi et Réception de la boîte à outils sur le centre de l'orchestration dans l'ordre suivant.</span><span class="sxs-lookup"><span data-stu-id="73211-105">Drag Send and Receive shapes from the tool box into the center of the orchestration in the following order.</span></span>  
  
2.  <span data-ttu-id="73211-106">Définissez les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="73211-106">Set the following parameters:</span></span>  
  
    |<span data-ttu-id="73211-107">Graphique à base de formes</span><span class="sxs-lookup"><span data-stu-id="73211-107">Shape</span></span>|<span data-ttu-id="73211-108">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-108">Name</span></span>|<span data-ttu-id="73211-109">Paramètre</span><span class="sxs-lookup"><span data-stu-id="73211-109">Setting</span></span>|  
    |-----------|----------|-------------|  
    |<span data-ttu-id="73211-110">Receive1</span><span class="sxs-lookup"><span data-stu-id="73211-110">Receive1</span></span>|<span data-ttu-id="73211-111">Activate</span><span class="sxs-lookup"><span data-stu-id="73211-111">Activate</span></span>|<span data-ttu-id="73211-112">True</span><span class="sxs-lookup"><span data-stu-id="73211-112">True</span></span>|  
    ||<span data-ttu-id="73211-113">Message</span><span class="sxs-lookup"><span data-stu-id="73211-113">Message</span></span>|<span data-ttu-id="73211-114">BeginDocMsg</span><span class="sxs-lookup"><span data-stu-id="73211-114">BeginDocMsg</span></span>|  
    ||<span data-ttu-id="73211-115">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-115">Name</span></span>|<span data-ttu-id="73211-116">ReceiveBeginDoc</span><span class="sxs-lookup"><span data-stu-id="73211-116">ReceiveBeginDoc</span></span>|  
    ||<span data-ttu-id="73211-117">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-117">Operation</span></span>|<span data-ttu-id="73211-118">BeginDoc.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="73211-118">BeginDoc.Operation_1.Request</span></span>|  
    |<span data-ttu-id="73211-119">Send1</span><span class="sxs-lookup"><span data-stu-id="73211-119">Send1</span></span>|<span data-ttu-id="73211-120">Message</span><span class="sxs-lookup"><span data-stu-id="73211-120">Message</span></span>|<span data-ttu-id="73211-121">BeginDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="73211-121">BeginDocSessionMsg</span></span>|  
    ||<span data-ttu-id="73211-122">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-122">Name</span></span>|<span data-ttu-id="73211-123">SendBeginDoc</span><span class="sxs-lookup"><span data-stu-id="73211-123">SendBeginDoc</span></span>|  
    ||<span data-ttu-id="73211-124">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-124">Operation</span></span>|<span data-ttu-id="73211-125">JDEPort.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="73211-125">JDEPort.Operation_1.Request</span></span>|  
    |<span data-ttu-id="73211-126">Receive2</span><span class="sxs-lookup"><span data-stu-id="73211-126">Receive2</span></span>|<span data-ttu-id="73211-127">Activate</span><span class="sxs-lookup"><span data-stu-id="73211-127">Activate</span></span>|<span data-ttu-id="73211-128">False</span><span class="sxs-lookup"><span data-stu-id="73211-128">False</span></span>|  
    ||<span data-ttu-id="73211-129">Message</span><span class="sxs-lookup"><span data-stu-id="73211-129">Message</span></span>|<span data-ttu-id="73211-130">BeginDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="73211-130">BeginDocResponseMsg</span></span>|  
    ||<span data-ttu-id="73211-131">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-131">Name</span></span>|<span data-ttu-id="73211-132">ReceiveBeginDocResponse</span><span class="sxs-lookup"><span data-stu-id="73211-132">ReceiveBeginDocResponse</span></span>|  
    ||<span data-ttu-id="73211-133">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-133">Operation</span></span>|<span data-ttu-id="73211-134">JDEPort.Operation_1.Response</span><span class="sxs-lookup"><span data-stu-id="73211-134">JDEPort.Operation_1.Response</span></span>|  
    |<span data-ttu-id="73211-135">Send2</span><span class="sxs-lookup"><span data-stu-id="73211-135">Send2</span></span>|<span data-ttu-id="73211-136">Message</span><span class="sxs-lookup"><span data-stu-id="73211-136">Message</span></span>|<span data-ttu-id="73211-137">EditLineSessionMsg</span><span class="sxs-lookup"><span data-stu-id="73211-137">EditLineSessionMsg</span></span>|  
    ||<span data-ttu-id="73211-138">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-138">Name</span></span>|<span data-ttu-id="73211-139">SendEditLine</span><span class="sxs-lookup"><span data-stu-id="73211-139">SendEditLine</span></span>|  
    ||<span data-ttu-id="73211-140">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-140">Operation</span></span>|<span data-ttu-id="73211-141">JDEPort.Operation_2.Request</span><span class="sxs-lookup"><span data-stu-id="73211-141">JDEPort.Operation_2.Request</span></span>|  
    |<span data-ttu-id="73211-142">Receive3</span><span class="sxs-lookup"><span data-stu-id="73211-142">Receive3</span></span>|<span data-ttu-id="73211-143">Activate</span><span class="sxs-lookup"><span data-stu-id="73211-143">Activate</span></span>|<span data-ttu-id="73211-144">False</span><span class="sxs-lookup"><span data-stu-id="73211-144">False</span></span>|  
    ||<span data-ttu-id="73211-145">Message</span><span class="sxs-lookup"><span data-stu-id="73211-145">Message</span></span>|<span data-ttu-id="73211-146">EditLineResponseMsg</span><span class="sxs-lookup"><span data-stu-id="73211-146">EditLineResponseMsg</span></span>|  
    ||<span data-ttu-id="73211-147">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-147">Name</span></span>|<span data-ttu-id="73211-148">ReceiveEditLine</span><span class="sxs-lookup"><span data-stu-id="73211-148">ReceiveEditLine</span></span>|  
    ||<span data-ttu-id="73211-149">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-149">Operation</span></span>|<span data-ttu-id="73211-150">JDEPort.Operation_2.Response</span><span class="sxs-lookup"><span data-stu-id="73211-150">JDEPort.Operation_2.Response</span></span>|  
    |<span data-ttu-id="73211-151">Send3</span><span class="sxs-lookup"><span data-stu-id="73211-151">Send3</span></span>|<span data-ttu-id="73211-152">Message</span><span class="sxs-lookup"><span data-stu-id="73211-152">Message</span></span>|<span data-ttu-id="73211-153">EndDocSessionMsg</span><span class="sxs-lookup"><span data-stu-id="73211-153">EndDocSessionMsg</span></span>|  
    ||<span data-ttu-id="73211-154">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-154">Name</span></span>|<span data-ttu-id="73211-155">SendEndDoc</span><span class="sxs-lookup"><span data-stu-id="73211-155">SendEndDoc</span></span>|  
    ||<span data-ttu-id="73211-156">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-156">Operation</span></span>|<span data-ttu-id="73211-157">JDEPort.Operation_3.Request</span><span class="sxs-lookup"><span data-stu-id="73211-157">JDEPort.Operation_3.Request</span></span>|  
    |<span data-ttu-id="73211-158">Receive4</span><span class="sxs-lookup"><span data-stu-id="73211-158">Receive4</span></span>|<span data-ttu-id="73211-159">Activate</span><span class="sxs-lookup"><span data-stu-id="73211-159">Activate</span></span>|<span data-ttu-id="73211-160">False</span><span class="sxs-lookup"><span data-stu-id="73211-160">False</span></span>|  
    ||<span data-ttu-id="73211-161">Message</span><span class="sxs-lookup"><span data-stu-id="73211-161">Message</span></span>|<span data-ttu-id="73211-162">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="73211-162">EndDocResponseMsg</span></span>|  
    ||<span data-ttu-id="73211-163">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-163">Name</span></span>|<span data-ttu-id="73211-164">ReceiveEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="73211-164">ReceiveEndDocResponse</span></span>|  
    ||<span data-ttu-id="73211-165">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-165">Operation</span></span>|<span data-ttu-id="73211-166">JDEPort.Operation_3.Response</span><span class="sxs-lookup"><span data-stu-id="73211-166">JDEPort.Operation_3.Response</span></span>|  
    |<span data-ttu-id="73211-167">Send4</span><span class="sxs-lookup"><span data-stu-id="73211-167">Send4</span></span>|<span data-ttu-id="73211-168">Message</span><span class="sxs-lookup"><span data-stu-id="73211-168">Message</span></span>|<span data-ttu-id="73211-169">EndDocResponseMsg</span><span class="sxs-lookup"><span data-stu-id="73211-169">EndDocResponseMsg</span></span>|  
    ||<span data-ttu-id="73211-170">Nom</span><span class="sxs-lookup"><span data-stu-id="73211-170">Name</span></span>|<span data-ttu-id="73211-171">SendEndDocResponse</span><span class="sxs-lookup"><span data-stu-id="73211-171">SendEndDocResponse</span></span>|  
    ||<span data-ttu-id="73211-172">Opération</span><span class="sxs-lookup"><span data-stu-id="73211-172">Operation</span></span>|<span data-ttu-id="73211-173">EndDocOut.Operation_1.Request</span><span class="sxs-lookup"><span data-stu-id="73211-173">EndDocOut.Operation_1.Request</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73211-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73211-174">See Also</span></span>  
 <span data-ttu-id="73211-175">[Tâche 1 : Créer les Ports](../core/task-1-create-the-ports1.md) </span><span class="sxs-lookup"><span data-stu-id="73211-175">[Task 1: Create the Ports](../core/task-1-create-the-ports1.md) </span></span>  
 <span data-ttu-id="73211-176">[Tâche 2 : Créer les Messages](../core/task-2-create-the-messages2.md) </span><span class="sxs-lookup"><span data-stu-id="73211-176">[Task 2: Create the Messages](../core/task-2-create-the-messages2.md) </span></span>  
 <span data-ttu-id="73211-177">[Tâche 4 : Configurer la forme construire un Message](../core/task-4-configure-the-construct-message-shape1.md) </span><span class="sxs-lookup"><span data-stu-id="73211-177">[Task 4: Configure the Construct Message Shape](../core/task-4-configure-the-construct-message-shape1.md) </span></span>  
 [<span data-ttu-id="73211-178">Tâche 5 : Configurer la forme Transformer</span><span class="sxs-lookup"><span data-stu-id="73211-178">Task 5: Configure the Transform Shape</span></span>](../core/task-5-configure-the-transform-shape2.md)