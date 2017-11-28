---
title: "État de l’échange et rapport d’état de détails de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebba4af5-6dff-4bb8-9c63-739ef49bbbb8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cc596a99d1a49b01ccc417abccb73d12ed34ad5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interchange-status-and-ack-details-status-report"></a><span data-ttu-id="fb039-102">État de l'échange et rapport Détails de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-102">Interchange Status and ACK Details Status Report</span></span>
<span data-ttu-id="fb039-103">Ce rapport d'état affiche les détails d'un échange, de son accusé de réception d'échange corrélé (technique) et de ses accusés de réception fonctionnels.</span><span class="sxs-lookup"><span data-stu-id="fb039-103">This status report displays details of an interchange and its correlated interchange (technical) acknowledgment and functional acknowledgments.</span></span> <span data-ttu-id="fb039-104">Afficher ce rapport pour le droit d’un échange dans le rapport d’état de l’échange/accusé de réception, puis en cliquant sur **détails de l’état et l’accusé de réception de l’échange**.</span><span class="sxs-lookup"><span data-stu-id="fb039-104">You display this report for right-clicking an interchange within the Interchange/ACK status report, and then clicking **Interchange status and ack details**.</span></span>  
  
 <span data-ttu-id="fb039-105">Ce rapport fournit les vues distinctes suivantes pour l'échange et les accusés de réception corrélés :</span><span class="sxs-lookup"><span data-stu-id="fb039-105">This report provides the following separate views for the interchange and the correlated acknowledgments:</span></span>  
  
## <a name="interchange-status"></a><span data-ttu-id="fb039-106">État de l'échange</span><span class="sxs-lookup"><span data-stu-id="fb039-106">Interchange Status</span></span>  
 <span data-ttu-id="fb039-107">Cette vue inclut un tableau indiquant les valeurs des champs suivants :</span><span class="sxs-lookup"><span data-stu-id="fb039-107">This view provides a table showing the values for the following fields:</span></span>  
  
-   <span data-ttu-id="fb039-108">ID du tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="fb039-108">Sender party ID</span></span>  
  
-   <span data-ttu-id="fb039-109">ID du tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="fb039-109">Receiver party ID</span></span>  
  
-   <span data-ttu-id="fb039-110">ID de contrôle</span><span class="sxs-lookup"><span data-stu-id="fb039-110">Control ID</span></span>  
  
-   <span data-ttu-id="fb039-111">Nom du tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="fb039-111">Receiver party name</span></span>  
  
-   <span data-ttu-id="fb039-112">Nom du tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="fb039-112">Sender party name</span></span>  
  
-   <span data-ttu-id="fb039-113">Sens</span><span class="sxs-lookup"><span data-stu-id="fb039-113">Direction</span></span>  
  
-   <span data-ttu-id="fb039-114">date/heure de l'échange ;</span><span class="sxs-lookup"><span data-stu-id="fb039-114">Interchange Date Time</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fb039-115">Pour les documents reçus, si la date spécifiée dans l'échange est au format AAMMJJ et que AA est supérieur ou égal à 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affiche l'année sous la forme 19AA.</span><span class="sxs-lookup"><span data-stu-id="fb039-115">For received documents, if the date specified in the interchange is YYMMDD format and YY is greater than or equal to 75, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the year as 19YY.</span></span> <span data-ttu-id="fb039-116">Si la date est antérieure à 75, l'année est affichée sous la forme 20AA.</span><span class="sxs-lookup"><span data-stu-id="fb039-116">If the date is less than 75, it will be displayed as 20YY.</span></span>  
    >   
    >  <span data-ttu-id="fb039-117">Par exemple, si vous recevez un échange contenant la valeur 991113 dans ISA09, la date de l'échange est affichée dans le rapport sous la forme 11/13/1999.</span><span class="sxs-lookup"><span data-stu-id="fb039-117">For example, if you receive an interchange that contains the value 991113 in ISA09, the Interchange Date will be listed in the report as 11/13/1999.</span></span>  
  
-   <span data-ttu-id="fb039-118">Nombre de groupes</span><span class="sxs-lookup"><span data-stu-id="fb039-118">Group count</span></span>  
  
-   <span data-ttu-id="fb039-119">ID de port</span><span class="sxs-lookup"><span data-stu-id="fb039-119">Port ID</span></span>  
  
-   <span data-ttu-id="fb039-120">État de l'échange</span><span class="sxs-lookup"><span data-stu-id="fb039-120">Interchange Status</span></span>  
  
-   <span data-ttu-id="fb039-121">Type de codage EDI</span><span class="sxs-lookup"><span data-stu-id="fb039-121">EDI encoding type</span></span>  
  
-   <span data-ttu-id="fb039-122">ID de corrélation du document informatisé</span><span class="sxs-lookup"><span data-stu-id="fb039-122">Transaction Set Correlation Id</span></span>  
  
 <span data-ttu-id="fb039-123">Si un accusé de réception technique est activé pour un tiers en tant que récepteur d'échanges (dans la page Traitement des accusés de réception et paramètres de validation de la boîte de dialogue Propriétés EDI), BizTalk Server attend qu'un accusé de réception technique (d'échange) soit renvoyé en réponse à un échange qu'il envoie.</span><span class="sxs-lookup"><span data-stu-id="fb039-123">If a technical acknowledgment is enabled for a party as an interchange receiver (in the ACK Processing and Validation Settings page of the EDI Properties dialog box), BizTalk Server expects a technical (interchange) acknowledgment to be returned in response to an interchange that it sends.</span></span> <span data-ttu-id="fb039-124">Lorsqu'il crée initialement une entrée d'état d'échange pour un échange sortant, il entre la valeur Accusé de réception attendu dans le champ État de l'échange.</span><span class="sxs-lookup"><span data-stu-id="fb039-124">When it initially creates an interchange status entry for an outbound interchange, it will enter ACK Expected in the Interchange Status field.</span></span> <span data-ttu-id="fb039-125">Lorsqu'il reçoit un accusé de réception technique et le met en corrélation avec l'échange d'origine, il met à jour le champ État de l'échange pour indiquer qu'il a reçu l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="fb039-125">When it receives a technical acknowledgment and correlates it to the original interchange, it will update the Interchange Status field to indicate that it has received the acknowledgment.</span></span>  
  
## <a name="interchange-ack-status"></a><span data-ttu-id="fb039-126">État de l'accusé de réception d'échange</span><span class="sxs-lookup"><span data-stu-id="fb039-126">Interchange Ack Status</span></span>  
 <span data-ttu-id="fb039-127">Cette vue affiche les valeurs d'état pour un accusé de réception d'échange (technique) :</span><span class="sxs-lookup"><span data-stu-id="fb039-127">This view displays status values for an interchange (technical) acknowledgment:</span></span>  
  
-   <span data-ttu-id="fb039-128">ID de contrôle de l'échange d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-128">Ack Interchange Control ID</span></span>  
  
-   <span data-ttu-id="fb039-129">Tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="fb039-129">Receiver party</span></span>  
  
-   <span data-ttu-id="fb039-130">Tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="fb039-130">Sender party</span></span>  
  
-   <span data-ttu-id="fb039-131">Sens</span><span class="sxs-lookup"><span data-stu-id="fb039-131">Direction</span></span>  
  
-   <span data-ttu-id="fb039-132">Date de l'échange d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-132">Ack Interchange Date</span></span>  
  
-   <span data-ttu-id="fb039-133">Heure de l'échange d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-133">Ack Interchange Time</span></span>  
  
-   <span data-ttu-id="fb039-134">État de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-134">Ack Status</span></span>  
  
-   <span data-ttu-id="fb039-135">Code de l'état</span><span class="sxs-lookup"><span data-stu-id="fb039-135">Status Code</span></span>  
  
-   <span data-ttu-id="fb039-136">Code d'accusé de réception 1</span><span class="sxs-lookup"><span data-stu-id="fb039-136">Ack Note Code1</span></span>  
  
-   <span data-ttu-id="fb039-137">Code d'accusé de réception 2</span><span class="sxs-lookup"><span data-stu-id="fb039-137">Ack Note Code2</span></span>  
  
## <a name="functional-acks"></a><span data-ttu-id="fb039-138">Ack(s) fonctionnel</span><span class="sxs-lookup"><span data-stu-id="fb039-138">Functional Ack(s)</span></span>  
 <span data-ttu-id="fb039-139">Cette vue affiche les valeurs d'état d'un accusé de réception fonctionnel :</span><span class="sxs-lookup"><span data-stu-id="fb039-139">This view displays status values for an functional acknowledgment:</span></span>  
  
-   <span data-ttu-id="fb039-140">Numéro de contrôle du groupe</span><span class="sxs-lookup"><span data-stu-id="fb039-140">Group Control Number</span></span>  
  
-   <span data-ttu-id="fb039-141">Tiers récepteur</span><span class="sxs-lookup"><span data-stu-id="fb039-141">Receiver party</span></span>  
  
-   <span data-ttu-id="fb039-142">Tiers expéditeur</span><span class="sxs-lookup"><span data-stu-id="fb039-142">Sender party</span></span>  
  
-   <span data-ttu-id="fb039-143">Sens</span><span class="sxs-lookup"><span data-stu-id="fb039-143">Direction</span></span>  
  
-   <span data-ttu-id="fb039-144">État</span><span class="sxs-lookup"><span data-stu-id="fb039-144">Status</span></span>  
  
-   <span data-ttu-id="fb039-145">Code de l'état</span><span class="sxs-lookup"><span data-stu-id="fb039-145">Status Code</span></span>  
  
-   <span data-ttu-id="fb039-146">Code de l'ID fonctionnel</span><span class="sxs-lookup"><span data-stu-id="fb039-146">Functional ID Code</span></span>  
  
-   <span data-ttu-id="fb039-147">Nombre de segments TS</span><span class="sxs-lookup"><span data-stu-id="fb039-147">TS Count</span></span>  
  
-   <span data-ttu-id="fb039-148">ID de contrôle de l'échange d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-148">Ack Interchange Control ID</span></span>  
  
-   <span data-ttu-id="fb039-149">Date de l'échange d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-149">Ack Interchange Date</span></span>  
  
-   <span data-ttu-id="fb039-150">Heure de l'échange d'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-150">Ack Interchange Time</span></span>  
  
-   <span data-ttu-id="fb039-151">Nombre de segments TS transmis</span><span class="sxs-lookup"><span data-stu-id="fb039-151">Delivered TS Count</span></span>  
  
-   <span data-ttu-id="fb039-152">Nombre de segments TS acceptés</span><span class="sxs-lookup"><span data-stu-id="fb039-152">Accepted TS Count</span></span>  
  
-   <span data-ttu-id="fb039-153">ErrorCode 1</span><span class="sxs-lookup"><span data-stu-id="fb039-153">ErrorCode 1</span></span>  
  
-   <span data-ttu-id="fb039-154">Code d’erreur 2</span><span class="sxs-lookup"><span data-stu-id="fb039-154">ErrorCode 2</span></span>  
  
-   <span data-ttu-id="fb039-155">Code d’erreur 3</span><span class="sxs-lookup"><span data-stu-id="fb039-155">ErrorCode 3</span></span>  
  
-   <span data-ttu-id="fb039-156">Code d’erreur 4</span><span class="sxs-lookup"><span data-stu-id="fb039-156">ErrorCode 4</span></span>  
  
-   <span data-ttu-id="fb039-157">Code d’erreur 5</span><span class="sxs-lookup"><span data-stu-id="fb039-157">ErrorCode 5</span></span>  
  
-   <span data-ttu-id="fb039-158">Heure de réception</span><span class="sxs-lookup"><span data-stu-id="fb039-158">Time Received</span></span>