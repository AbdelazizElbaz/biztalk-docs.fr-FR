---
title: "Adaptateur de réception WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- receive adapters, Web service headers
- SOAP messages, extracting information
- SOAP messages, WCF adapters
- WCF adapters, receive adapters
- messages, SOAP
- receive adapters, WCF adapters
- Web services, headers
- headers [messages]
- SOAP messages, receive adapters
ms.assetid: 6b3d5df1-5d9d-4240-a98f-ea29c3272e38
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb8ea12087b5884370edce13f3ddc6fd6853c7d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wcf-receive-adapter"></a><span data-ttu-id="4d72f-102">Adaptateur de réception WCF</span><span class="sxs-lookup"><span data-stu-id="4d72f-102">WCF Receive Adapter</span></span>
<span data-ttu-id="4d72f-103">L'adaptateur de réception WCF permet de recevoir des demandes de service WCF.</span><span class="sxs-lookup"><span data-stu-id="4d72f-103">The WCF receive adapter enables you to receive WCF service requests.</span></span>  
  
## <a name="extracting-the-biztalk-message-body-from-the-soap-message"></a><span data-ttu-id="4d72f-104">Extraction du corps de message BizTalk dans le message SOAP</span><span class="sxs-lookup"><span data-stu-id="4d72f-104">Extracting the BizTalk Message Body from the SOAP Message</span></span>  
 <span data-ttu-id="4d72f-105">Le corps de message BizTalk entrant peut être extrait du message SOAP à l'aide de l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="4d72f-105">The inbound BizTalk message body can be extracted from the SOAP message by using one of the following options:</span></span>  
  
-   <span data-ttu-id="4d72f-106">Extraction du contenu de l'élément SOAP Body</span><span class="sxs-lookup"><span data-stu-id="4d72f-106">Extract the content of the SOAP Body element</span></span>  
  
-   <span data-ttu-id="4d72f-107">Extraction de l'ensemble de l'enveloppe SOAP</span><span class="sxs-lookup"><span data-stu-id="4d72f-107">Extract the entire SOAP envelope</span></span>  
  
-   <span data-ttu-id="4d72f-108">Extraction du contenu de l'élément se trouvant dans l'enveloppe SOAP à l'aide d'une expression XPath</span><span class="sxs-lookup"><span data-stu-id="4d72f-108">Extract the content of the element inside the SOAP envelope by using an XPath expression</span></span>  
  
 <span data-ttu-id="4d72f-109">Vous pouvez configurer ces options dans la boîte de dialogue des propriétés de transport.</span><span class="sxs-lookup"><span data-stu-id="4d72f-109">You can configure these options in the transport properties dialog box.</span></span>  
  
#### <a name="extract-the-content-of-the-soap-body-element"></a><span data-ttu-id="4d72f-110">Extraction du contenu de l’élément SOAP Body</span><span class="sxs-lookup"><span data-stu-id="4d72f-110">Extract the Content of the SOAP Body Element</span></span>  
 <span data-ttu-id="4d72f-111">Lorsque cette option est activée, le contenu interne de l'élément SOAP Body est lu dans le message SOAP, puis placé dans le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4d72f-111">When this option is selected, the inner content of the SOAP Body element is read from the SOAP message and placed into the body part of the BizTalk message.</span></span>  
  
#### <a name="extract-the-entire-soap-envelope"></a><span data-ttu-id="4d72f-112">Extraire l’enveloppe SOAP entière</span><span class="sxs-lookup"><span data-stu-id="4d72f-112">Extract the Entire SOAP Envelope</span></span>  
 <span data-ttu-id="4d72f-113">Lorsque cette option est activée, l'ensemble de l'enveloppe SOAP, y compris la balise, est placé dans le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4d72f-113">When this option is selected, the entire SOAP envelope including the tag is placed into the body part of the BizTalk message.</span></span>  
  
#### <a name="extract-the-content-of-the-element-by-using-an-xpath-expression"></a><span data-ttu-id="4d72f-114">Extraction du contenu de l'élément à l'aide d'une expression XPath</span><span class="sxs-lookup"><span data-stu-id="4d72f-114">Extract the Content of the Element by Using an XPath Expression</span></span>  
 <span data-ttu-id="4d72f-115">Lorsque cette option est activée, le contenu interne de l'élément se trouvant à l'intérieur de l'élément SOAP Body localisé par l'expression XPath est placé dans le corps du message BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4d72f-115">When this option is selected, the inner content of the element inside the SOAP Body element that is located by the XPath expression is placed into the body part of the BizTalk message.</span></span> <span data-ttu-id="4d72f-116">Le reste des données de l'élément Body est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4d72f-116">The rest of the data in the Body element is ignored.</span></span> <span data-ttu-id="4d72f-117">Vous devez également spécifier le codage de nœud (par exemple un codage XML, Base64, Hex ou String).</span><span class="sxs-lookup"><span data-stu-id="4d72f-117">You also need to specify the node encoding—for example, XML, Base64, Hex, or String encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d72f-118">Lorsque le codage XML est sélectionné, le contenu externe de l'élément est localisé par l'expression XPath, puis il est placé dans le corps.</span><span class="sxs-lookup"><span data-stu-id="4d72f-118">When the XML encoding is selected, the outer content of the element is located by the XPath expression and placed into the body part.</span></span>  
  
## <a name="handling-web-services-headers"></a><span data-ttu-id="4d72f-119">Traitement des en-têtes des services Web</span><span class="sxs-lookup"><span data-stu-id="4d72f-119">Handling Web Services Headers</span></span>  
 <span data-ttu-id="4d72f-120">L'adaptateur de réception promeut un sous-ensemble d'en-têtes des services Web standard dans le contexte du message BizTalk pour faciliter l'accès et l'acheminement sur la base des valeurs de ces en-têtes.</span><span class="sxs-lookup"><span data-stu-id="4d72f-120">The receive adapter promotes a subset of the standard Web services headers onto the BizTalk message context to enable easy access and routing based on values of those headers.</span></span> <span data-ttu-id="4d72f-121">Le tableau suivant répertorie les propriétés qui sont enregistrées par l'adaptateur de réception dans le message de contexte.</span><span class="sxs-lookup"><span data-stu-id="4d72f-121">The following table lists the properties that will be saved onto the message context by the receive adapter.</span></span> <span data-ttu-id="4d72f-122">Les propriétés sont définies dans les espaces de noms suivants : http://www.w3.org/2005/addressing et http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties.</span><span class="sxs-lookup"><span data-stu-id="4d72f-122">The properties are defined under the following namespaces: http://www.w3.org/2005/addressing and http://schemas.microsoft.com/BizTalk/2006/Adapters/WCF-properties.</span></span>  
  
|<span data-ttu-id="4d72f-123">En-tête</span><span class="sxs-lookup"><span data-stu-id="4d72f-123">Header</span></span>|<span data-ttu-id="4d72f-124">Nom de la propriété BizTalk</span><span class="sxs-lookup"><span data-stu-id="4d72f-124">BizTalk property name</span></span>|<span data-ttu-id="4d72f-125">Promue ?</span><span class="sxs-lookup"><span data-stu-id="4d72f-125">Is promoted?</span></span>|  
|------------|---------------------------|------------------|  
|<span data-ttu-id="4d72f-126">Action</span><span class="sxs-lookup"><span data-stu-id="4d72f-126">Action</span></span>|<span data-ttu-id="4d72f-127">Action</span><span class="sxs-lookup"><span data-stu-id="4d72f-127">Action</span></span>|<span data-ttu-id="4d72f-128">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-128">Yes</span></span>|  
|<span data-ttu-id="4d72f-129">MessageID</span><span class="sxs-lookup"><span data-stu-id="4d72f-129">MessageID</span></span>|<span data-ttu-id="4d72f-130">MessageID</span><span class="sxs-lookup"><span data-stu-id="4d72f-130">MessageID</span></span>|<span data-ttu-id="4d72f-131">Non</span><span class="sxs-lookup"><span data-stu-id="4d72f-131">No</span></span>|  
|<span data-ttu-id="4d72f-132">Pour</span><span class="sxs-lookup"><span data-stu-id="4d72f-132">To</span></span>|<span data-ttu-id="4d72f-133">Pour</span><span class="sxs-lookup"><span data-stu-id="4d72f-133">To</span></span>|<span data-ttu-id="4d72f-134">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-134">Yes</span></span>|  
|<span data-ttu-id="4d72f-135">ReplyTo/Address</span><span class="sxs-lookup"><span data-stu-id="4d72f-135">ReplyTo/Address</span></span>|<span data-ttu-id="4d72f-136">ReplyTo</span><span class="sxs-lookup"><span data-stu-id="4d72f-136">ReplyTo</span></span>|<span data-ttu-id="4d72f-137">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-137">Yes</span></span>|  
|<span data-ttu-id="4d72f-138">From/Address</span><span class="sxs-lookup"><span data-stu-id="4d72f-138">From/Address</span></span>|<span data-ttu-id="4d72f-139">De</span><span class="sxs-lookup"><span data-stu-id="4d72f-139">From</span></span>|<span data-ttu-id="4d72f-140">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-140">Yes</span></span>|  
|<span data-ttu-id="4d72f-141">Sequence/Identifier</span><span class="sxs-lookup"><span data-stu-id="4d72f-141">Sequence/Identifier</span></span>|<span data-ttu-id="4d72f-142">SequenceId</span><span class="sxs-lookup"><span data-stu-id="4d72f-142">SequenceId</span></span>|<span data-ttu-id="4d72f-143">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-143">Yes</span></span>|  
|<span data-ttu-id="4d72f-144">Sequence/MessageNumber</span><span class="sxs-lookup"><span data-stu-id="4d72f-144">Sequence/MessageNumber</span></span>|<span data-ttu-id="4d72f-145">SequenceNumber</span><span class="sxs-lookup"><span data-stu-id="4d72f-145">SequenceNumber</span></span>|<span data-ttu-id="4d72f-146">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-146">Yes</span></span>|  
|<span data-ttu-id="4d72f-147">Sequence/LastMessage</span><span class="sxs-lookup"><span data-stu-id="4d72f-147">Sequence/LastMessage</span></span>|<span data-ttu-id="4d72f-148">SequenceLastMessage</span><span class="sxs-lookup"><span data-stu-id="4d72f-148">SequenceLastMessage</span></span>|<span data-ttu-id="4d72f-149">Oui</span><span class="sxs-lookup"><span data-stu-id="4d72f-149">Yes</span></span>|  
|<span data-ttu-id="4d72f-150">\<SOAP : Header ></span><span class="sxs-lookup"><span data-stu-id="4d72f-150">\<soap:Header></span></span>|<span data-ttu-id="4d72f-151">InboundHeaders</span><span class="sxs-lookup"><span data-stu-id="4d72f-151">InboundHeaders</span></span>|<span data-ttu-id="4d72f-152">Non</span><span class="sxs-lookup"><span data-stu-id="4d72f-152">No</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d72f-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d72f-153">See Also</span></span>  
 <span data-ttu-id="4d72f-154">[En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="4d72f-154">[Specifying the Message Body for the WCF Adapters](../core/specifying-the-message-body-for-the-wcf-adapters.md) </span></span>  
 <span data-ttu-id="4d72f-155">[Adaptateur d’envoi WCF](../core/wcf-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="4d72f-155">[WCF Send Adapter](../core/wcf-send-adapter.md) </span></span>  
 [<span data-ttu-id="4d72f-156">Quelles sont les adaptateurs WCF ?</span><span class="sxs-lookup"><span data-stu-id="4d72f-156">What Are the WCF Adapters?</span></span>](../core/what-are-the-wcf-adapters.md)