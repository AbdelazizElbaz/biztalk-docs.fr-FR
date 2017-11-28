---
title: "Accusé de réception EDIFACT CONTRL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95e1c244-d700-48d3-9416-032ead6d4d6d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baaca02ac076c79be004ed7b3d2c0f4fffce6ff9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-contrl-acknowledgment"></a><span data-ttu-id="f725c-102">Accusé de réception EDIFACT CONTRL</span><span class="sxs-lookup"><span data-stu-id="f725c-102">EDIFACT CONTRL Acknowledgment</span></span>
<span data-ttu-id="f725c-103">L'accusé de réception CONTRL (ACK) sert de notification de transactions techniques et de notification de transactions opérationnelles pour les messages EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="f725c-103">The CONTRL acknowledgment (ACK) serves as both technical and functional acknowledgment for EDIFACT-encoded messages.</span></span> <span data-ttu-id="f725c-104">En tant que notification de transactions techniques, le message CONTRL indique la réception d'un échange.</span><span class="sxs-lookup"><span data-stu-id="f725c-104">As a technical acknowledgment, the CONTRL message indicates receipt of an interchange.</span></span> <span data-ttu-id="f725c-105">En tant que notification de transactions opérationnelles, le message CONTRL indique l'acceptation ou le rejet de l'échange, du groupe ou du message reçu, et répertorie les erreurs ou fonctionnalités non prises en charge.</span><span class="sxs-lookup"><span data-stu-id="f725c-105">As a functional acknowledgment, the CONTRL message indicates acceptance or rejection of the received interchange, group, or message, with a list of errors or unsupported functionality.</span></span>  
  
 <span data-ttu-id="f725c-106">Le message CONTRL complet sert de notification de transactions opérationnelles.</span><span class="sxs-lookup"><span data-stu-id="f725c-106">The full CONTRL message serves as the functional ACK.</span></span> <span data-ttu-id="f725c-107">Les sections de la notification de transactions opérationnelles sont réutilisées pour la notification de transactions techniques.</span><span class="sxs-lookup"><span data-stu-id="f725c-107">Sections of the functional ACK are reused for the technical ACK.</span></span> <span data-ttu-id="f725c-108">Si vous avez sélectionné des accusés de réception techniques et opérationnelles dans les propriétés du tiers pour le tiers expéditeur ou dans les propriétés globales, BizTalk Server génère deux messages CONTRL : un ACK CONTRL technique et un CONTRL ACK..</span><span class="sxs-lookup"><span data-stu-id="f725c-108">If you have selected both technical and functional ACKs in the party properties for a sending party or in global properties, BizTalk Server will generate two CONTRL messages: a technical CONTRL ACK and a functional CONTRL ACK.</span></span>  
  
 <span data-ttu-id="f725c-109">L’ACK CONTRL est conforme à la EFACT_\<numéro de Version > _CONTRL.xsd schéma.</span><span class="sxs-lookup"><span data-stu-id="f725c-109">The CONTRL ACK conforms to the EFACT_\<Version number>_CONTRL.xsd schema.</span></span>  
  
## <a name="technical-acknowledgement"></a><span data-ttu-id="f725c-110">Notification de transactions techniques</span><span class="sxs-lookup"><span data-stu-id="f725c-110">Technical Acknowledgement</span></span>  
 <span data-ttu-id="f725c-111">Une notification de transactions techniques implique que le destinataire de l'échange :</span><span class="sxs-lookup"><span data-stu-id="f725c-111">A technical ACK implies that the recipient of the interchange:</span></span>  
  
-   <span data-ttu-id="f725c-112">ait reçu l'échange d'objet.</span><span class="sxs-lookup"><span data-stu-id="f725c-112">has received the subject interchange;</span></span>  
  
-   <span data-ttu-id="f725c-113">accuse réception des parties de l'échange d'objet qui ont été contrôlées afin de vérifier que les éléments de données copiés dans le segment UCI de rapport sont correctes du point de vue syntaxique.</span><span class="sxs-lookup"><span data-stu-id="f725c-113">acknowledges the parts of the subject interchange that have been checked in order to ensure that the data elements copied into the reporting UCI segment are syntactically correct;</span></span>  
  
-   <span data-ttu-id="f725c-114">a accepté la responsabilité liée à la notification de l'expéditeur de l'acceptation ou du rejet des autres parties de l'échange d'objet.</span><span class="sxs-lookup"><span data-stu-id="f725c-114">has accepted responsibility for notifying the sender of acknowledgement or rejection of the other parts of the subject interchange;</span></span>  
  
-   <span data-ttu-id="f725c-115">a pris des précautions raisonnables pour garantir que l'expéditeur reçoit une notification.</span><span class="sxs-lookup"><span data-stu-id="f725c-115">and has taken reasonable precautions in order to ensure that the sender is so notified.</span></span>  
  
## <a name="functional-acknowledgement"></a><span data-ttu-id="f725c-116">Notification de transactions opérationnelles</span><span class="sxs-lookup"><span data-stu-id="f725c-116">Functional Acknowledgement</span></span>  
 <span data-ttu-id="f725c-117">Une notification de transactions opérationnelles implique que le destinataire de l'échange :</span><span class="sxs-lookup"><span data-stu-id="f725c-117">A functional ACK implies that the recipient of the interchange:</span></span>  
  
-   <span data-ttu-id="f725c-118">ait reçu les niveaux référencés de l'échange acquitté.</span><span class="sxs-lookup"><span data-stu-id="f725c-118">has received the referenced levels(s) of the interchange acknowledged;</span></span>  
  
-   <span data-ttu-id="f725c-119">ait vérifié qu'il n'y a pas d'erreur de syntaxe fatale dans le niveau référencé acquitté susceptible d'empêcher le traitement de l'échange.</span><span class="sxs-lookup"><span data-stu-id="f725c-119">has checked that there are no fatal syntactic errors in the acknowledged referenced level that prevents further processing of the interchange;</span></span>  
  
-   <span data-ttu-id="f725c-120">ait vérifié que toutes les parties acquittées des segments de service sont correctes du point de vue sémantique (si aucune erreur n'est rapportée).</span><span class="sxs-lookup"><span data-stu-id="f725c-120">has checked that all acknowledged parts of service segments are semantically correct (if no errors are reported);</span></span>  
  
-   <span data-ttu-id="f725c-121">se soumette aux actions demandées dans les niveaux référencés acquittés des segments de service.</span><span class="sxs-lookup"><span data-stu-id="f725c-121">will comply with the actions requested in the acknowledged referenced-levels of the service segments;</span></span>  
  
-   <span data-ttu-id="f725c-122">ait accepté la responsabilité liée à la notification de l'expéditeur par d'autres moyens que l'envoi d'un message CONTRL si des erreurs syntaxiques ou sémantiques telles que décrites ci-dessus, sont détectées ultérieurement dans la partie appropriée, ou si la partie ne peut pas être traitée pour d'autres raisons une fois qu'elle a été acquittée dans un message CONTRL envoyé.</span><span class="sxs-lookup"><span data-stu-id="f725c-122">has accepted responsibility for notifying the sender by other means than sending a CONTRL message if any syntactic or semantic errors as described above, are later detected in the relevant part, or the part cannot be processed for some other reason after the part has been acknowledged in a submitted CONTRL message;</span></span>  
  
-   <span data-ttu-id="f725c-123">ait pris des précautions raisonnables pour garantir que de telles erreurs sont détectées et que l'expéditeur reçoit une notification.</span><span class="sxs-lookup"><span data-stu-id="f725c-123">and has taken reasonable precautions in order to ensure that such errors are detected and that the sender is notified.</span></span>  
  
 <span data-ttu-id="f725c-124">Le rejet implique que le destinataire de l'échange :</span><span class="sxs-lookup"><span data-stu-id="f725c-124">Rejection implies that the recipient of the interchange:</span></span>  
  
-   <span data-ttu-id="f725c-125">ne peut pas accuser réception de l'échange d'objet, ou de ses parties appropriées, pour les raisons indiquées dans le message CONTRL.</span><span class="sxs-lookup"><span data-stu-id="f725c-125">cannot acknowledge the subject interchange, or the relevant parts of it, for reasons indicated in the CONTRL message;</span></span>  
  
-   <span data-ttu-id="f725c-126">n'entreprendra aucune autre action sur les informations commerciales contenues dans la partie rejetée de l'échange d'objet.</span><span class="sxs-lookup"><span data-stu-id="f725c-126">and will not take any further action on business information contained in the rejected part of the subject interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f725c-127">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f725c-127">In This Section</span></span>  
  
-   [<span data-ttu-id="f725c-128">Message CONTRL EDIFACT comme accusé de réception technique</span><span class="sxs-lookup"><span data-stu-id="f725c-128">EDIFACT CONTRL Message as Technical Acknowledgment</span></span>](../core/edifact-contrl-message-as-technical-acknowledgment.md)  
  
-   [<span data-ttu-id="f725c-129">Message CONTRL EDIFACT comme accusé de réception fonctionnel</span><span class="sxs-lookup"><span data-stu-id="f725c-129">EDIFACT CONTRL Message as Functional Acknowledgment</span></span>](../core/edifact-contrl-message-as-functional-acknowledgment.md)  
  
## <a name="see-also"></a><span data-ttu-id="f725c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f725c-130">See Also</span></span>  
 [<span data-ttu-id="f725c-131">Structure d’accusé de réception EDI</span><span class="sxs-lookup"><span data-stu-id="f725c-131">EDI Acknowledgment Structure</span></span>](../core/edi-acknowledgment-structure.md)