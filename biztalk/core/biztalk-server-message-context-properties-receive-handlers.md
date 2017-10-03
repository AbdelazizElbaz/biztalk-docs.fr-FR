---
title: "Propriétés de contexte de Message BizTalk Server (gestionnaires de réception) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message context properties
- receive handlers, message context properties
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a60896a8e1cace909a160c1dc942e63e9258d85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-message-context-properties-receive-handlers"></a><span data-ttu-id="f6f67-102">Propriétés de contexte de Message BizTalk Server (gestionnaires de réception)</span><span class="sxs-lookup"><span data-stu-id="f6f67-102">BizTalk Server Message Context Properties (Receive Handlers)</span></span>
<span data-ttu-id="f6f67-103">En plus de la charge, les informations supplémentaires composant le message doivent être accessibles à partir d'une orchestration BizTalk Server au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="f6f67-103">In addition to the message payload, the supplementary information that composes a message must be accessible from a BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="f6f67-104">Informations de message TIBCO RV promues en tant que propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="f6f67-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
 <span data-ttu-id="f6f67-105">Le tableau suivant répertorie ces informations supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="f6f67-105">The following table lists this supplementary information:</span></span>  
  
|<span data-ttu-id="f6f67-106">Identification des données</span><span class="sxs-lookup"><span data-stu-id="f6f67-106">Data Identification</span></span>|<span data-ttu-id="f6f67-107">Type</span><span class="sxs-lookup"><span data-stu-id="f6f67-107">Type</span></span>|<span data-ttu-id="f6f67-108">Routable</span><span class="sxs-lookup"><span data-stu-id="f6f67-108">Routable</span></span>|<span data-ttu-id="f6f67-109">Emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="f6f67-109">Receive Location</span></span>|  
|-------------------------|----------|--------------|----------------------|  
|<span data-ttu-id="f6f67-110">Objet d'envoi [null]</span><span class="sxs-lookup"><span data-stu-id="f6f67-110">Send Subject [null]</span></span>|<span data-ttu-id="f6f67-111">chaîne</span><span class="sxs-lookup"><span data-stu-id="f6f67-111">string</span></span>|<span data-ttu-id="f6f67-112">Oui</span><span class="sxs-lookup"><span data-stu-id="f6f67-112">Yes</span></span>|<span data-ttu-id="f6f67-113">Communique à l'orchestration l'objet auquel ce message a été envoyé.</span><span class="sxs-lookup"><span data-stu-id="f6f67-113">Tells orchestration which subject this message was sent to.</span></span>|  
|<span data-ttu-id="f6f67-114">Objet de réponse [null]</span><span class="sxs-lookup"><span data-stu-id="f6f67-114">Reply Subject [null]</span></span>|<span data-ttu-id="f6f67-115">chaîne</span><span class="sxs-lookup"><span data-stu-id="f6f67-115">string</span></span>|<span data-ttu-id="f6f67-116">Oui</span><span class="sxs-lookup"><span data-stu-id="f6f67-116">Yes</span></span>|<span data-ttu-id="f6f67-117">Communique à l'orchestration l'emplacement où l'expéditeur attend que la réponse soit envoyée, si une réponse est attendue.</span><span class="sxs-lookup"><span data-stu-id="f6f67-117">Tells orchestration where the sender expects the reply to be sent, if one is expected.</span></span>|  
|<span data-ttu-id="f6f67-118">Nombre de champs [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="f6f67-118">Field Count [read only]</span></span>|<span data-ttu-id="f6f67-119">nombre entier non signé</span><span class="sxs-lookup"><span data-stu-id="f6f67-119">unsigned int</span></span>|<span data-ttu-id="f6f67-120">Non</span><span class="sxs-lookup"><span data-stu-id="f6f67-120">No</span></span>|<span data-ttu-id="f6f67-121">Nombre de champs dans un message de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="f6f67-121">Number of fields in upper level message.</span></span> <span data-ttu-id="f6f67-122">Cette propriété est fournie par TIBCO RV.</span><span class="sxs-lookup"><span data-stu-id="f6f67-122">A property provided by TIBCO RV.</span></span>|  
|<span data-ttu-id="f6f67-123">Nom de l'expéditeur CM [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="f6f67-123">CM Sender Name [read-only]</span></span>|<span data-ttu-id="f6f67-124">chaîne</span><span class="sxs-lookup"><span data-stu-id="f6f67-124">string</span></span>|<span data-ttu-id="f6f67-125">Oui</span><span class="sxs-lookup"><span data-stu-id="f6f67-125">Yes</span></span>|<span data-ttu-id="f6f67-126">Nom du destinataire CM de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="f6f67-126">CM Correspondent name of the sender.</span></span>|  
|<span data-ttu-id="f6f67-127">Numéro de séquence CM [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="f6f67-127">CM Sequence Number [read only]</span></span>|<span data-ttu-id="f6f67-128">long</span><span class="sxs-lookup"><span data-stu-id="f6f67-128">long</span></span>|<span data-ttu-id="f6f67-129">Non</span><span class="sxs-lookup"><span data-stu-id="f6f67-129">No</span></span>|<span data-ttu-id="f6f67-130">Numéro de séquence attribué par l'objet de transport TIBCO d'envoi.</span><span class="sxs-lookup"><span data-stu-id="f6f67-130">Sequence number assigned by the sending TIBCO transport object.</span></span>|  
|<span data-ttu-id="f6f67-131">Délai CM [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="f6f67-131">CM Time Limit [read-only]</span></span>|<span data-ttu-id="f6f67-132">double</span><span class="sxs-lookup"><span data-stu-id="f6f67-132">double</span></span>|<span data-ttu-id="f6f67-133">Non</span><span class="sxs-lookup"><span data-stu-id="f6f67-133">No</span></span>|<span data-ttu-id="f6f67-134">Délai après lequel le programme d'envoi n'attend plus que son transport CM certifie la livraison du message.</span><span class="sxs-lookup"><span data-stu-id="f6f67-134">A time limit, after which the sending program no longer expects its CM transport to certify delivery of the message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6f67-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6f67-135">See Also</span></span>  
 <span data-ttu-id="f6f67-136">[Mappage des messages dans TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="f6f67-136">[Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="f6f67-137">Gestionnaires de réception création TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="f6f67-137">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)