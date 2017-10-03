---
title: BizTalk ESB Toolkit Cycle de vie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c72fdbda-b9ef-431a-8322-56dba98e9eab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cb15a4c87a497a5595327b65019ca95b3201664
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit-message-life-cycle"></a><span data-ttu-id="96b64-102">BizTalk ESB Toolkit Cycle de vie</span><span class="sxs-lookup"><span data-stu-id="96b64-102">BizTalk ESB Toolkit Message Life Cycle</span></span>
<span data-ttu-id="96b64-103">Voici le cycle de vie d’un message qui provient d’un système externe et parcourt l’ESB d’atteindre sa destination finale :</span><span class="sxs-lookup"><span data-stu-id="96b64-103">The following is the life cycle of a message that originates from an external system and traverses through the ESB to reach its final destination:</span></span>  
  
1.  <span data-ttu-id="96b64-104">Une rampe d’entrée reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="96b64-104">An on-ramp receives the message.</span></span> <span data-ttu-id="96b64-105">Selon le tiers émetteur ou le client, le message peut ou ne peut pas contenir un itinéraire qui définit les instructions de traitement du message.</span><span class="sxs-lookup"><span data-stu-id="96b64-105">Depending on the submitting party or client, the message may or may not contain an itinerary that defines the processing instructions for the message.</span></span>  
  
2.  <span data-ttu-id="96b64-106">Composants de pipeline ESB copient la feuille de route (s’il est présent dans l’en-tête SOAP) dans le contexte du message en tant que propriétés promues.</span><span class="sxs-lookup"><span data-stu-id="96b64-106">ESB pipeline components copy the itinerary (if present in the SOAP header) into the context of the message as promoted properties.</span></span> <span data-ttu-id="96b64-107">Si le message est reçu sans un itinéraire, un composant de pipeline spécifique peut être configuré pour sélectionner l’itinéraire approprié à partir d’une base de données, selon le contenu du message ou le contexte, puis copiez la feuille de route dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="96b64-107">If the message is received without an itinerary, a specific pipeline component can be configured to select the appropriate itinerary from a database, depending on message content or context, and then copy the itinerary into the context of the message.</span></span> <span data-ttu-id="96b64-108">Pendant la durée de la durée de vie du message, l’itinéraire est conservée dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="96b64-108">For the duration of the lifetime of the message, the itinerary is maintained within the message context.</span></span>  
  
3.  <span data-ttu-id="96b64-109">Dans le pipeline, l’itinéraire est évaluée et basée sur message des services d’itinéraire peuvent traiter le message.</span><span class="sxs-lookup"><span data-stu-id="96b64-109">While still in the pipeline, the itinerary is evaluated and message-based itinerary services can process the message.</span></span> <span data-ttu-id="96b64-110">Ces services d’itinéraire peuvent transformer le message ou configurer des points de terminaison de routage.</span><span class="sxs-lookup"><span data-stu-id="96b64-110">These itinerary services may transform the message or configure routing endpoints.</span></span>  
  
4.  <span data-ttu-id="96b64-111">Le message est publié dans la base de données de la boîte de Message de Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="96b64-111">The message is published to the Microsoft BizTalk Server Message Box database.</span></span>  
  
5.  <span data-ttu-id="96b64-112">BizTalk Server évalue les propriétés promues du message et les files d’attente du message pour un ou plusieurs abonnés.</span><span class="sxs-lookup"><span data-stu-id="96b64-112">BizTalk Server evaluates the promoted properties of the message and queues the message for one or more subscribers.</span></span>  
  
6.  <span data-ttu-id="96b64-113">Les abonnés traitent le message à l’aide des mécanismes standards de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="96b64-113">The subscriber(s) process the message using typical BizTalk Server mechanisms.</span></span> <span data-ttu-id="96b64-114">Un abonné peut être une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="96b64-114">A subscriber can be either of the following:</span></span>  
  
    -   <span data-ttu-id="96b64-115">Port de réception une orchestration BizTalk Server avec un filtre configuré sur une liaison directe</span><span class="sxs-lookup"><span data-stu-id="96b64-115">A BizTalk Server orchestration with a filter configured on a direct-bound receive port</span></span>  
  
    -   <span data-ttu-id="96b64-116">Un serveur BizTalk dynamique port d’envoi, qui est également appelé une ESB rampe.</span><span class="sxs-lookup"><span data-stu-id="96b64-116">A dynamic BizTalk Server send port, which is also referred to as an ESB off-ramp.</span></span> <span data-ttu-id="96b64-117">La feuille de route détermine la façon dont le port est configuré pour continuer le traitement du message.</span><span class="sxs-lookup"><span data-stu-id="96b64-117">The itinerary determines how the port will be configured to continue processing the message.</span></span>  
  
 <span data-ttu-id="96b64-118">Comme alternative à un message arrive via un itinéraire rampe d’entrée, les orchestrations BizTalk Server peuvent également publier des messages dans la boîte de Message pour le traitement d’ESB :</span><span class="sxs-lookup"><span data-stu-id="96b64-118">As an alternative to a message arriving through an itinerary on-ramp, BizTalk Server orchestrations can also publish messages to the Message Box for ESB processing:</span></span>  
  
1.  <span data-ttu-id="96b64-119">Un message est créé dans une orchestration BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="96b64-119">A message is created within a BizTalk Server orchestration.</span></span>  
  
2.  <span data-ttu-id="96b64-120">Contexte du message est remplie avec la feuille de route ESB.</span><span class="sxs-lookup"><span data-stu-id="96b64-120">The message's context is populated with the ESB itinerary.</span></span>  
  
3.  <span data-ttu-id="96b64-121">Le message est publié via un port de liaison directe à la base de données de la boîte de Message.</span><span class="sxs-lookup"><span data-stu-id="96b64-121">The message is published through a direct-bound port to the Message Box database.</span></span>