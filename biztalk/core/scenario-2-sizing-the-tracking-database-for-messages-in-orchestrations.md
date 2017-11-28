---
title: "Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracking database, database size
ms.assetid: d1cfb8b9-d4e2-4069-8db3-18f72358652b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62ea6e463dfb3a44e2628f57b632634d7a9bd212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-2-sizing-the-tracking-database--for-messages-in-orchestrations"></a><span data-ttu-id="28b23-102">Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="28b23-102">Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations</span></span>
<span data-ttu-id="28b23-103">Examinons un exemple comprenant une orchestration.</span><span class="sxs-lookup"><span data-stu-id="28b23-103">Let's look at an example that includes an orchestration.</span></span> <span data-ttu-id="28b23-104">Le schéma suivant représente le processus d'entreprise dans sa totalité.</span><span class="sxs-lookup"><span data-stu-id="28b23-104">The following figure displays the entire business process.</span></span> <span data-ttu-id="28b23-105">Dans ce scénario, un message entre dans le serveur BizTalk pour passer dans une orchestration avant d'y être modifié, puis il sort par un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="28b23-105">In this scenario, a message comes into BizTalk Server, is sent through an orchestration, is changed within the orchestration, and is then sent out through a send port.</span></span>  
  
 <span data-ttu-id="28b23-106">![Processus de message BizTalk Server](../core/media/biztalk-server-message-process.gif "BizTalk_Server_Message_Process")</span><span class="sxs-lookup"><span data-stu-id="28b23-106">![BizTalk Server message process](../core/media/biztalk-server-message-process.gif "BizTalk_Server_Message_Process")</span></span>  
  
 <span data-ttu-id="28b23-107">**Le processus de message BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="28b23-107">**The BizTalk Server message process**</span></span>  
  
 <span data-ttu-id="28b23-108">Voici quelques données relatives au présent scénario :</span><span class="sxs-lookup"><span data-stu-id="28b23-108">Here are some of the facts concerning this scenario:</span></span>  
  
-   <span data-ttu-id="28b23-109">taille du message : 5 Ko ;</span><span class="sxs-lookup"><span data-stu-id="28b23-109">The message size is 5K.</span></span>  
  
-   <span data-ttu-id="28b23-110">Nous ne sommes pas promouvoir des propriétés.</span><span class="sxs-lookup"><span data-stu-id="28b23-110">We are not promoting any properties.</span></span>  
  
-   <span data-ttu-id="28b23-111">Le nombre de messages que nous avons reçus dans une année : 3,5 millions.</span><span class="sxs-lookup"><span data-stu-id="28b23-111">The number of messages we receive in a year is 3.5 million.</span></span>  
  
-   <span data-ttu-id="28b23-112">suivi activé pour tous les événements,</span><span class="sxs-lookup"><span data-stu-id="28b23-112">Tracking is turned on for all events.</span></span> <span data-ttu-id="28b23-113">ici au nombre de six :</span><span class="sxs-lookup"><span data-stu-id="28b23-113">There are six events in this scenario:</span></span>  
  
    -   <span data-ttu-id="28b23-114">Réception du message M0</span><span class="sxs-lookup"><span data-stu-id="28b23-114">Receipt of message M0</span></span>  
  
    -   <span data-ttu-id="28b23-115">Sortie du message M1 provenant du port de réception</span><span class="sxs-lookup"><span data-stu-id="28b23-115">Output of message M1 from the receive port</span></span>  
  
    -   <span data-ttu-id="28b23-116">Réception du message M1 par l'orchestration</span><span class="sxs-lookup"><span data-stu-id="28b23-116">Receipt of message M1 by the orchestration</span></span>  
  
    -   <span data-ttu-id="28b23-117">Sortie du message M2 provenant de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="28b23-117">Output of message M2 from the orchestration</span></span>  
  
    -   <span data-ttu-id="28b23-118">Réception du message M2 par le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="28b23-118">Receipt of message M2 by the send port</span></span>  
  
    -   <span data-ttu-id="28b23-119">Sortie du message M3 par le pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="28b23-119">Output of message M3 by the send pipeline</span></span>  
  
-   <span data-ttu-id="28b23-120">création de trois messages dans ce scénario :</span><span class="sxs-lookup"><span data-stu-id="28b23-120">Three additional messages are created in this scenario.</span></span> <span data-ttu-id="28b23-121">le message M0 étant le message entrant, il n'est pas créé par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="28b23-121">Message M0 is the incoming message and is therefore not created by BizTalk Server.</span></span> <span data-ttu-id="28b23-122">Le message M1 est le message sortant du port de réception, le message M2 est celui généré par l'orchestration et le message M3, celui qui provient du port de transmission.</span><span class="sxs-lookup"><span data-stu-id="28b23-122">Message M1 is the output message from the receive port, M2 is the output message from the orchestration, and M3 is the output message from the transmit port.</span></span>  
  
 <span data-ttu-id="28b23-123">L'intégration de ces données à la formule donne le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="28b23-123">Applying this information to the formula gives the following result:</span></span>  
  
```  
[(3*150 bytes) + (6*230 bytes) + (0*0(52 bytes + 0) * 3,500,000]/1024/1024  
[(450 + 1380 + 0) * 3,500,000]/1024/1024 = 6108 MB ~ 5.96 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-a-single-promoted-property"></a><span data-ttu-id="28b23-124">Messages passant par des orchestrations et dont la propriété promue est unique</span><span class="sxs-lookup"><span data-stu-id="28b23-124">Messages in orchestrations with a single promoted property</span></span>  
 <span data-ttu-id="28b23-125">Dans cet exemple, un seul champ est promu, comme dans un exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="28b23-125">Now let's promote a single field in this scenario, as in the earlier example.</span></span> <span data-ttu-id="28b23-126">La taille de la propriété promue est d'environ 10 octets.</span><span class="sxs-lookup"><span data-stu-id="28b23-126">The promoted property is approximately 10 bytes in size.</span></span> <span data-ttu-id="28b23-127">L'équation est alors la suivante :</span><span class="sxs-lookup"><span data-stu-id="28b23-127">The equation now looks like this:</span></span>  
  
```  
[((3*150 bytes) + (6*230 bytes) + (1*3*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 186) * 3,500,000]/1024/1024 = 6729 MB ~ 6.57 GB per year  
```  
  
 <span data-ttu-id="28b23-128">Si vous devez promouvoir une autre propriété de 20 octets, la formule se présente comme indiqué ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="28b23-128">If you need to promote an additional property that is 20 bytes in size, the formula now looks like this:</span></span>  
  
```  
[(3*150 bytes) + (6*230 bytes) + ((1*3*(52 bytes + 10 bytes) + (1*3*(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 372) * 3,500,000]/1024/1024 = 7350 MB ~ 7.18 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-message-body-tracking-activated"></a><span data-ttu-id="28b23-129">Messages passant par des orchestrations et pour lesquels le suivi du corps des messages est activé</span><span class="sxs-lookup"><span data-stu-id="28b23-129">Messages in orchestrations with message body tracking activated</span></span>  
 <span data-ttu-id="28b23-130">Si, dans cet exemple, le suivi de message est pris en compte, le résultat obtenu après avoir calculé l'espace supplémentaire nécessaire est identique à celui obtenu dans le scénario précédent, à savoir 50,1 Go par an.</span><span class="sxs-lookup"><span data-stu-id="28b23-130">If you want to accommodate message tracking, the result from calculating the additional space needed is identical to the result in the earlier scenario, or 50.1 GB per year.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b23-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28b23-131">See Also</span></span>  
 <span data-ttu-id="28b23-132">[À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="28b23-132">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="28b23-133">[Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="28b23-133">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="28b23-134">[Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="28b23-134">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="28b23-135">[Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="28b23-135">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="28b23-136">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="28b23-136">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)