---
title: "Les propriétés de contexte de Message de réception pour TIBCO Rendezvous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36f4de92dbe7c4c235a1c9ebd092b28b3a198c92
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="biztalk-server-message-context-properties-receive-handlers"></a><span data-ttu-id="53966-102">Propriétés de contexte de Message BizTalk Server (gestionnaires de réception)</span><span class="sxs-lookup"><span data-stu-id="53966-102">BizTalk Server Message Context Properties (Receive Handlers)</span></span>
<span data-ttu-id="53966-103">En plus de la charge, les informations supplémentaires composant le message doivent être accessibles à partir d'une orchestration BizTalk Server au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="53966-103">In addition to the message payload, the supplementary information that composes a message must be accessible from a BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="53966-104">Informations de message TIBCO RV promues en tant que propriétés de contexte</span><span class="sxs-lookup"><span data-stu-id="53966-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
 <span data-ttu-id="53966-105">Le tableau suivant répertorie ces informations supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="53966-105">The following table lists this supplementary information:</span></span>  
  
|<span data-ttu-id="53966-106">Identification des données</span><span class="sxs-lookup"><span data-stu-id="53966-106">Data Identification</span></span>|<span data-ttu-id="53966-107">Type</span><span class="sxs-lookup"><span data-stu-id="53966-107">Type</span></span>|<span data-ttu-id="53966-108">Routable</span><span class="sxs-lookup"><span data-stu-id="53966-108">Routable</span></span>|<span data-ttu-id="53966-109">Emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="53966-109">Receive Location</span></span>|  
|-------------------------|----------|--------------|----------------------|  
|<span data-ttu-id="53966-110">Objet d'envoi [null]</span><span class="sxs-lookup"><span data-stu-id="53966-110">Send Subject [null]</span></span>|<span data-ttu-id="53966-111">chaîne</span><span class="sxs-lookup"><span data-stu-id="53966-111">string</span></span>|<span data-ttu-id="53966-112">Oui</span><span class="sxs-lookup"><span data-stu-id="53966-112">Yes</span></span>|<span data-ttu-id="53966-113">Communique à l'orchestration l'objet auquel ce message a été envoyé.</span><span class="sxs-lookup"><span data-stu-id="53966-113">Tells orchestration which subject this message was sent to.</span></span>|  
|<span data-ttu-id="53966-114">Objet de réponse [null]</span><span class="sxs-lookup"><span data-stu-id="53966-114">Reply Subject [null]</span></span>|<span data-ttu-id="53966-115">chaîne</span><span class="sxs-lookup"><span data-stu-id="53966-115">string</span></span>|<span data-ttu-id="53966-116">Oui</span><span class="sxs-lookup"><span data-stu-id="53966-116">Yes</span></span>|<span data-ttu-id="53966-117">Communique à l'orchestration l'emplacement où l'expéditeur attend que la réponse soit envoyée, si une réponse est attendue.</span><span class="sxs-lookup"><span data-stu-id="53966-117">Tells orchestration where the sender expects the reply to be sent, if one is expected.</span></span>|  
|<span data-ttu-id="53966-118">Nombre de champs [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="53966-118">Field Count [read only]</span></span>|<span data-ttu-id="53966-119">nombre entier non signé</span><span class="sxs-lookup"><span data-stu-id="53966-119">unsigned int</span></span>|<span data-ttu-id="53966-120">Non</span><span class="sxs-lookup"><span data-stu-id="53966-120">No</span></span>|<span data-ttu-id="53966-121">Nombre de champs dans un message de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="53966-121">Number of fields in upper level message.</span></span> <span data-ttu-id="53966-122">Cette propriété est fournie par TIBCO RV.</span><span class="sxs-lookup"><span data-stu-id="53966-122">A property provided by TIBCO RV.</span></span>|  
|<span data-ttu-id="53966-123">Nom de l'expéditeur CM [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="53966-123">CM Sender Name [read-only]</span></span>|<span data-ttu-id="53966-124">chaîne</span><span class="sxs-lookup"><span data-stu-id="53966-124">string</span></span>|<span data-ttu-id="53966-125">Oui</span><span class="sxs-lookup"><span data-stu-id="53966-125">Yes</span></span>|<span data-ttu-id="53966-126">Nom du destinataire CM de l'expéditeur.</span><span class="sxs-lookup"><span data-stu-id="53966-126">CM Correspondent name of the sender.</span></span>|  
|<span data-ttu-id="53966-127">Numéro de séquence CM [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="53966-127">CM Sequence Number [read only]</span></span>|<span data-ttu-id="53966-128">long</span><span class="sxs-lookup"><span data-stu-id="53966-128">long</span></span>|<span data-ttu-id="53966-129">Non</span><span class="sxs-lookup"><span data-stu-id="53966-129">No</span></span>|<span data-ttu-id="53966-130">Numéro de séquence attribué par l'objet de transport TIBCO d'envoi.</span><span class="sxs-lookup"><span data-stu-id="53966-130">Sequence number assigned by the sending TIBCO transport object.</span></span>|  
|<span data-ttu-id="53966-131">Délai CM [lecture seule]</span><span class="sxs-lookup"><span data-stu-id="53966-131">CM Time Limit [read-only]</span></span>|<span data-ttu-id="53966-132">double</span><span class="sxs-lookup"><span data-stu-id="53966-132">double</span></span>|<span data-ttu-id="53966-133">Non</span><span class="sxs-lookup"><span data-stu-id="53966-133">No</span></span>|<span data-ttu-id="53966-134">Délai après lequel le programme d'envoi n'attend plus que son transport CM certifie la livraison du message.</span><span class="sxs-lookup"><span data-stu-id="53966-134">A time limit, after which the sending program no longer expects its CM transport to certify delivery of the message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53966-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53966-135">See Also</span></span>  
 <span data-ttu-id="53966-136">[Mappage des messages dans TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="53966-136">[Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="53966-137">Création de gestionnaires de réception TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="53966-137">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)