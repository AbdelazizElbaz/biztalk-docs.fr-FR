---
title: "Étape 3 : Tester le dans lot scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c487d39d-b2be-41d4-963e-d0ee9ba169fb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d84c34eb3019f83ecd28f30425a93708affcecb2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-3-test-the-batch-inbatch-out-scenario"></a><span data-ttu-id="de502-102">Étape 3 : Tester le lot dans / lots scénario</span><span class="sxs-lookup"><span data-stu-id="de502-102">Step 3: Test the Batch In/Batch Out Scenario</span></span>
<span data-ttu-id="de502-103">Dans cette étape, vous testez le lot dans / hors lot didacticiel par la suppression du lot dans une instance de test / message du lot dans un dossier.</span><span class="sxs-lookup"><span data-stu-id="de502-103">In this step, you test the Batch In/Batch Out tutorial by dropping a test instance of the batch in/batch out message into a folder.</span></span> <span data-ttu-id="de502-104">Le port d’envoi que vous avez configurée envoie le message, il recevra le port de réception et le pipeline de réception traite et la placer dans le dossier de destination.</span><span class="sxs-lookup"><span data-stu-id="de502-104">The send port that you set up will send the message, the receive port will receive it, and the receive pipeline will process it and drop it into the destination folder.</span></span>  
  
### <a name="to-test-the-batch-inbatch-out-scenario"></a><span data-ttu-id="de502-105">Pour tester le traitement par lots dans / lots scénario</span><span class="sxs-lookup"><span data-stu-id="de502-105">To test the Batch In/Batch Out scenario</span></span>  
  
1.  <span data-ttu-id="de502-106">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\< *lecteur*\>: \Batching Tutorial\Instances** dossier.</span><span class="sxs-lookup"><span data-stu-id="de502-106">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Batching Tutorial\Instances** folder.</span></span>  
  
2.  <span data-ttu-id="de502-107">Bouton droit sur **BatchInBatchOut.txt**, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="de502-107">Right click **BatchInBatchOut.txt**, and then click **Copy**.</span></span>  
  
3.  <span data-ttu-id="de502-108">Accédez à la  **\< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7PickUp** dossier.</span><span class="sxs-lookup"><span data-stu-id="de502-108">Browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7PickUp** folder.</span></span>  
  
4.  <span data-ttu-id="de502-109">Cliquez avec le bouton droit, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="de502-109">Right-click the folder, and then click **Paste**.</span></span>  
  
### <a name="to-verify-the-results-of-the-batch-inbatch-out-tutorial"></a><span data-ttu-id="de502-110">Pour vérifier les résultats du lot dans / Out didacticiel du lot</span><span class="sxs-lookup"><span data-stu-id="de502-110">To verify the results of the Batch In/Batch Out Tutorial</span></span>  
  
-   <span data-ttu-id="de502-111">À l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorateur de solutions, cliquez sur Parcourir pour le  **\< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BTAHL7Drop** dossier.</span><span class="sxs-lookup"><span data-stu-id="de502-111">Using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to the **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BTAHL7Drop** folder.</span></span> <span data-ttu-id="de502-112">Après une courte période, vous devez voir l’instance traitée du message de lot et un accusé de réception, apparaissent dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="de502-112">After a short period, you should see the processed instance of the batch message, and an acknowledgment, appear in the folder.</span></span> <span data-ttu-id="de502-113">Si elles n’apparaissent pas, vérifiez le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements pour un message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="de502-113">If they do not appear, check the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer for an error message.</span></span> <span data-ttu-id="de502-114">Chaque fichier doit avoir un nom différent dans le formulaire \< *Guid*\>.txt.</span><span class="sxs-lookup"><span data-stu-id="de502-114">Each file should have a different name in the form \<*Guid*\>.txt.</span></span>  
  
     <span data-ttu-id="de502-115">Le premier message doit être le lot composé de deux messages.</span><span class="sxs-lookup"><span data-stu-id="de502-115">The first message should be the batch consisting of two messages.</span></span> <span data-ttu-id="de502-116">BizTalk Accelerator pour HL7 (BTAHL7) a inclus dans le fichier .txt les ces deux messages de manière séquentielle.</span><span class="sxs-lookup"><span data-stu-id="de502-116">BizTalk Accelerator for HL7 (BTAHL7) has included these two messages sequentially in the .txt file.</span></span> <span data-ttu-id="de502-117">Ce lot ne contient pas de FHS/recherche en texte intégral et les balises BHS/BTS.</span><span class="sxs-lookup"><span data-stu-id="de502-117">This batch does not contain FHS/FTS and BHS/BTS tags.</span></span> <span data-ttu-id="de502-118">Un lot doit contenir soit toutes les balises FHS/FTS et BHS/BTS, like ou ce message de lot, aucun FHS/FTS et aucune balise BHS/BTS.</span><span class="sxs-lookup"><span data-stu-id="de502-118">A batch must contain either all FHS/FTS and BHS/BTS tags, or like this batch message, no FHS/FTS and no BHS/BTS tags.</span></span>  
  
    |<span data-ttu-id="de502-119">MSH.9</span><span class="sxs-lookup"><span data-stu-id="de502-119">MSH.9</span></span>|<span data-ttu-id="de502-120">MSH.10</span><span class="sxs-lookup"><span data-stu-id="de502-120">MSH.10</span></span>|<span data-ttu-id="de502-121">MSH.3</span><span class="sxs-lookup"><span data-stu-id="de502-121">MSH.3</span></span>|<span data-ttu-id="de502-122">MSH.5</span><span class="sxs-lookup"><span data-stu-id="de502-122">MSH.5</span></span>|  
    |-----------|------------|-----------|-----------|  
    |<span data-ttu-id="de502-123">ADT^A03</span><span class="sxs-lookup"><span data-stu-id="de502-123">ADT^A03</span></span>|<span data-ttu-id="de502-124">000001</span><span class="sxs-lookup"><span data-stu-id="de502-124">000001</span></span>|<span data-ttu-id="de502-125">Tutorial_BatchSource</span><span class="sxs-lookup"><span data-stu-id="de502-125">Tutorial_BatchSource</span></span>|<span data-ttu-id="de502-126">MESA_IS</span><span class="sxs-lookup"><span data-stu-id="de502-126">MESA_IS</span></span>|  
    |<span data-ttu-id="de502-127">ADT^A03</span><span class="sxs-lookup"><span data-stu-id="de502-127">ADT^A03</span></span>|<span data-ttu-id="de502-128">000002</span><span class="sxs-lookup"><span data-stu-id="de502-128">000002</span></span>|<span data-ttu-id="de502-129">Tutorial_BatchSource</span><span class="sxs-lookup"><span data-stu-id="de502-129">Tutorial_BatchSource</span></span>|<span data-ttu-id="de502-130">MESA_IS</span><span class="sxs-lookup"><span data-stu-id="de502-130">MESA_IS</span></span>|  
  
     <span data-ttu-id="de502-131">Le second message doit être un accusé de réception unique application envoyé en réponse au message de lot, avec les champs suivants :</span><span class="sxs-lookup"><span data-stu-id="de502-131">The second message should be a single application acknowledgment sent in response to the batch message, with the following fields:</span></span>  
  
    |<span data-ttu-id="de502-132">MSH.9</span><span class="sxs-lookup"><span data-stu-id="de502-132">MSH.9</span></span>|<span data-ttu-id="de502-133">MSH.3</span><span class="sxs-lookup"><span data-stu-id="de502-133">MSH.3</span></span>|<span data-ttu-id="de502-134">MSH.5</span><span class="sxs-lookup"><span data-stu-id="de502-134">MSH.5</span></span>|<span data-ttu-id="de502-135">MSA.1</span><span class="sxs-lookup"><span data-stu-id="de502-135">MSA.1</span></span>|<span data-ttu-id="de502-136">MSA.2</span><span class="sxs-lookup"><span data-stu-id="de502-136">MSA.2</span></span>|  
    |-----------|-----------|-----------|-----------|-----------|  
    |<span data-ttu-id="de502-137">ACK^A03^ACK</span><span class="sxs-lookup"><span data-stu-id="de502-137">ACK^A03^ACK</span></span>|<span data-ttu-id="de502-138">MESA_IS</span><span class="sxs-lookup"><span data-stu-id="de502-138">MESA_IS</span></span>|<span data-ttu-id="de502-139">Tutorial_BatchSource</span><span class="sxs-lookup"><span data-stu-id="de502-139">Tutorial_BatchSource</span></span>|<span data-ttu-id="de502-140">AA</span><span class="sxs-lookup"><span data-stu-id="de502-140">AA</span></span>|<span data-ttu-id="de502-141">000001</span><span class="sxs-lookup"><span data-stu-id="de502-141">000001</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="de502-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de502-142">See Also</span></span>  
 <span data-ttu-id="de502-143">[Partie 1 : Scénario de lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="de502-143">[Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span></span>  
 [<span data-ttu-id="de502-144">Partie 3 : Scénario de création de lot</span><span class="sxs-lookup"><span data-stu-id="de502-144">Part 3: Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)