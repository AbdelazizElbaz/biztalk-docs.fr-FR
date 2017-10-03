---
title: Adaptateur dynamique MLLP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e22fabb-0edf-4931-b8b2-74a5daccee4a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf7d1d7046135de1dc1837d1fb8961ef440b5009
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-mllp-adapter"></a><span data-ttu-id="1f685-102">Adaptateur MLLP dynamique</span><span class="sxs-lookup"><span data-stu-id="1f685-102">Dynamic MLLP Adapter</span></span>
<span data-ttu-id="1f685-103">En commençant par [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], les propriétés de l’adaptateur MLLP peuvent être configurées lors de l’exécution à l’aide d’un port d’envoi unidirectionnel ou bidirectionnel (requête-réponse).</span><span class="sxs-lookup"><span data-stu-id="1f685-103">Starting with [!INCLUDE[bts2013r2](../../includes/bts2013r2-md.md)], the MLLP adapter properties can be configured at Runtime using a One-Way or Two-Way (Request-Response) send port.</span></span>  
  
## <a name="dynamic-properties"></a><span data-ttu-id="1f685-104">Propriétés dynamiques</span><span class="sxs-lookup"><span data-stu-id="1f685-104">Dynamic Properties</span></span>  
 <span data-ttu-id="1f685-105">Les propriétés suivantes sont dans le **GlobalPropertySchemas** espace de noms :</span><span class="sxs-lookup"><span data-stu-id="1f685-105">The following properties are in the **GlobalPropertySchemas** namespace:</span></span>  
  
|<span data-ttu-id="1f685-106">Propriété</span><span class="sxs-lookup"><span data-stu-id="1f685-106">Property</span></span>|<span data-ttu-id="1f685-107"> Description</span><span class="sxs-lookup"><span data-stu-id="1f685-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="1f685-108">Message (MLLP.acceptableACKCodes) = « Tous les Codes de l’accusé de réception » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-108">Message(MLLP.acceptableACKCodes)=”All ACK Codes”;</span></span>|<span data-ttu-id="1f685-109">Ces valeurs comprennent :</span><span class="sxs-lookup"><span data-stu-id="1f685-109">Values include:</span></span><br /><br /> <span data-ttu-id="1f685-110">-Tous les Codes de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="1f685-110">-   All ACK Codes</span></span><br /><span data-ttu-id="1f685-111">-AA et l’autorité de certification</span><span class="sxs-lookup"><span data-stu-id="1f685-111">-   AA and CA</span></span><br /><span data-ttu-id="1f685-112">-AA, l’autorité de certification, AE et CE</span><span class="sxs-lookup"><span data-stu-id="1f685-112">-   AA, CA, AE and CE</span></span><br /><span data-ttu-id="1f685-113">-AA, l’autorité de certification, AR et CR</span><span class="sxs-lookup"><span data-stu-id="1f685-113">-   AA, CA, AR and CR</span></span><br /><br /> <span data-ttu-id="1f685-114">Ceci est similaire à la **les Codes de l’accusé de réception Acceptable** propriété dans un Port d’envoi statique MLLP.</span><span class="sxs-lookup"><span data-stu-id="1f685-114">This is similar to the **Acceptable ACK Codes** property in a Static MLLP Send Port.</span></span>|  
|<span data-ttu-id="1f685-115">Message (MLLP. CarriageReturn) = « 0D » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-115">Message(MLLP.CarriageReturn)=”0d”;</span></span>|<span data-ttu-id="1f685-116">Caractère de retour chariot ASCII</span><span class="sxs-lookup"><span data-stu-id="1f685-116">ASCII Carriage Return Character</span></span>|  
|<span data-ttu-id="1f685-117">Message (MLLP.endBlockDelimiter) = « 1c » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-117">Message(MLLP.endBlockDelimiter)=”1c”;</span></span>|<span data-ttu-id="1f685-118">Caractère de fin de bloc ASCII</span><span class="sxs-lookup"><span data-stu-id="1f685-118">ASCII End Block Character</span></span>|  
|<span data-ttu-id="1f685-119">Message (MLLP.startBlockDelimiter) = 0 « b » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-119">Message(MLLP.startBlockDelimiter)=”0b”;</span></span>|<span data-ttu-id="1f685-120">Caractère de début de bloc ASCII</span><span class="sxs-lookup"><span data-stu-id="1f685-120">ASCII Start Block Character</span></span>|  
|<span data-ttu-id="1f685-121">Message (MLLP.timeout) = « 60000 » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-121">Message(MLLP.timeout)=”60000”;</span></span>|<span data-ttu-id="1f685-122">Compter le socket émetteur inactive sur le serveur BTAHL7 arrive à expiration (0 ne correspond à aucun délai d’expiration)</span><span class="sxs-lookup"><span data-stu-id="1f685-122">Period after which inactive sending socket on BTAHL7 server will timeout(0 is no timeout)</span></span>|  
|<span data-ttu-id="1f685-123">SendPortName(Microsoft.XLANGs.BaseTypes.Address) = « 127.0.0.1:11000 » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-123">SendPortName(Microsoft.XLANGs.BaseTypes.Address) = “127.0.0.1:11000”;</span></span>|<span data-ttu-id="1f685-124">Adresse et Port pour le routage du message</span><span class="sxs-lookup"><span data-stu-id="1f685-124">Address and Port for routing the message</span></span>|  
|<span data-ttu-id="1f685-125">SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) = « MLLP » ;</span><span class="sxs-lookup"><span data-stu-id="1f685-125">SendPortName(Microsoft.XLANGs.BaseTypes.TransportType) = “MLLP”;</span></span>|<span data-ttu-id="1f685-126">Type d’adaptateur (MLLP)</span><span class="sxs-lookup"><span data-stu-id="1f685-126">Type of Adapter (MLLP)</span></span>|  
  
## <a name="additional"></a><span data-ttu-id="1f685-127">Supplément</span><span class="sxs-lookup"><span data-stu-id="1f685-127">Additional</span></span>  
  
-   <span data-ttu-id="1f685-128">Lorsque vous créez un message à parties multiples dans une orchestration pour HL7, créez les parties de message dans cet ordre :</span><span class="sxs-lookup"><span data-stu-id="1f685-128">When creating a multipart message in an orchestration for HL7, create the message parts in this following order:</span></span>  
  
    1.  <span data-ttu-id="1f685-129">Segment de MSH</span><span class="sxs-lookup"><span data-stu-id="1f685-129">MSH Segment</span></span>  
  
    2.  <span data-ttu-id="1f685-130">BodySegments</span><span class="sxs-lookup"><span data-stu-id="1f685-130">BodySegments</span></span>  
  
    3.  <span data-ttu-id="1f685-131">ZSegments</span><span class="sxs-lookup"><span data-stu-id="1f685-131">ZSegments</span></span>  
  
     <span data-ttu-id="1f685-132">Si vous spécifiez les parties de message dans un ordre différent, l’erreur suivante se produit :</span><span class="sxs-lookup"><span data-stu-id="1f685-132">If you specify the message parts in a different order, the following error occurs:</span></span>  
  
     <span data-ttu-id="1f685-133">WrongBodyPartException</span><span class="sxs-lookup"><span data-stu-id="1f685-133">WrongBodyPartException</span></span>  
  
-   <span data-ttu-id="1f685-134">Les propriétés de l’itinéraire adaptateur peuvent être spécifiées sur l’orchestration pour prendre en charge le routage dynamique.</span><span class="sxs-lookup"><span data-stu-id="1f685-134">The adapter route properties can be specified on the orchestration to support dynamic routing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f685-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f685-135">See Also</span></span>  
 <span data-ttu-id="1f685-136">[Les paramètres de configuration pour l’envoi et les adaptateurs de réception](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="1f685-136">[Configuration Parameters for Send and Receive Adapters](../../adapters-and-accelerators/accelerator-hl7/configuration-parameters-for-send-and-receive-adapters.md) </span></span>  
 <span data-ttu-id="1f685-137">[Traitement de l’adaptateur de réception de MLLP](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="1f685-137">[MLLP Receive Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-receive-adapter-processing.md) </span></span>  
 <span data-ttu-id="1f685-138">[Traitement d’adaptateur MLLP envoi](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span><span class="sxs-lookup"><span data-stu-id="1f685-138">[MLLP Send Adapter Processing](../../adapters-and-accelerators/accelerator-hl7/mllp-send-adapter-processing.md) </span></span>  
 [<span data-ttu-id="1f685-139">Le traitement des Messages encodés en MLLP</span><span class="sxs-lookup"><span data-stu-id="1f685-139">Processing MLLP-encoded Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)