---
title: 'Scénario 3 : Dimensionnement de la base de données de suivi pour les Messages envoyés hors aux listes de Distribution | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: bc6e0da0-46d1-42d6-8ec9-29a28719fbb3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dca1722e24e0c76c85699ea00fcf6ffc120b2e14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-3-sizing-the-tracking-database--for-messages-sent-out-to-distribution-lists"></a><span data-ttu-id="c36d8-102">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="c36d8-102">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>
<span data-ttu-id="c36d8-103">Dans le schéma suivant, un message passe par un processus d'orchestration pour être modifié au sein de l'orchestration avant d'être envoyé vers différents ports d'envoi par le biais d'une liste de distribution.</span><span class="sxs-lookup"><span data-stu-id="c36d8-103">In the following figure, you have a message that proceeds through an orchestration, is changed within the orchestration, and is then sent out to several different send ports through a distribution list.</span></span>  
  
 <span data-ttu-id="c36d8-104">![Message à travers une orchestration à plusieurs ports](../core/media/biztalk-server-message-orch-multiple-ports.gif "BizTalk_Server_message_orch_multiple_ports")</span><span class="sxs-lookup"><span data-stu-id="c36d8-104">![Message through an orchestration to multiple ports](../core/media/biztalk-server-message-orch-multiple-ports.gif "BizTalk_Server_message_orch_multiple_ports")</span></span>  
  
 <span data-ttu-id="c36d8-105">**Message de BizTalk Server qui se déroule à travers une orchestration est envoyé vers différents ports**</span><span class="sxs-lookup"><span data-stu-id="c36d8-105">**BizTalk Server message that proceeds through an orchestration and is sent out to several different ports**</span></span>  
  
 <span data-ttu-id="c36d8-106">Voici quelques données relatives au présent scénario :</span><span class="sxs-lookup"><span data-stu-id="c36d8-106">Here are some of the facts concerning this scenario:</span></span>  
  
-   <span data-ttu-id="c36d8-107">Taille du message de 10 Ko.</span><span class="sxs-lookup"><span data-stu-id="c36d8-107">The message size is 10K.</span></span>  
  
-   <span data-ttu-id="c36d8-108">aucune propriété à promouvoir ;</span><span class="sxs-lookup"><span data-stu-id="c36d8-108">You are not promoting any properties.</span></span>  
  
-   <span data-ttu-id="c36d8-109">nombre de messages reçus dans une année : 3,5 millions ;</span><span class="sxs-lookup"><span data-stu-id="c36d8-109">The number of messages you receive in a year is 3.5 million.</span></span>  
  
-   <span data-ttu-id="c36d8-110">suivi activé pour tous les événements,</span><span class="sxs-lookup"><span data-stu-id="c36d8-110">Tracking is turned on for all events.</span></span> <span data-ttu-id="c36d8-111">ici au nombre de cinq :</span><span class="sxs-lookup"><span data-stu-id="c36d8-111">There are five events in this scenario:</span></span>  
  
    -   <span data-ttu-id="c36d8-112">Réception du message M0</span><span class="sxs-lookup"><span data-stu-id="c36d8-112">Receipt of message M0</span></span>  
  
    -   <span data-ttu-id="c36d8-113">Sortie du message M1 provenant du port de réception</span><span class="sxs-lookup"><span data-stu-id="c36d8-113">Output of message M1 from the receive port</span></span>  
  
    -   <span data-ttu-id="c36d8-114">Sortie du message M3 par le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="c36d8-114">Output of message M3 by the send port</span></span>  
  
    -   <span data-ttu-id="c36d8-115">Sortie du message M4 par le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="c36d8-115">Output of message M4 by the send port</span></span>  
  
    -   <span data-ttu-id="c36d8-116">Sortie du message M5 par le port d'envoi</span><span class="sxs-lookup"><span data-stu-id="c36d8-116">Output of message M5 by the send port</span></span>  
  
 <span data-ttu-id="c36d8-117">Application de ces informations à l’équation donne les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="c36d8-117">Applying this information to the equation gives the following:</span></span>  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-a-single-promoted-property"></a><span data-ttu-id="c36d8-118">Messages passant par un processus d'orchestration et envoyés vers une liste de distribution dont une seule propriété est promue</span><span class="sxs-lookup"><span data-stu-id="c36d8-118">Messages in an orchestration that are sent out to a distribution list with a single promoted property</span></span>  
 <span data-ttu-id="c36d8-119">Dans cet exemple, une seule propriété d'environ 10 octets est promue, comme dans un précédent exemple.</span><span class="sxs-lookup"><span data-stu-id="c36d8-119">In this example, let's promote a single property, approximately 10 bytes in size, as we did in an earlier scenario.</span></span> <span data-ttu-id="c36d8-120">L'équation est alors la suivante :</span><span class="sxs-lookup"><span data-stu-id="c36d8-120">The equation now looks like this:</span></span>  
  
```  
[((5*150 bytes) + (10*230 bytes) + (1*5(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 260) * 3,500,000]/1024/1024 = 11048 MB ~ 10.79 GB per year  
```  
  
 <span data-ttu-id="c36d8-121">Si vous souhaitez promouvoir une autre propriété de 20 octets, l'équation prend la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="c36d8-121">If we promote an additional property that is 20 bytes in size the equation now looks like this:</span></span>  
  
```  
[((5*150 bytes) + (10*230 bytes) + ((1*5(52 bytes + 10 bytes) + (1*5(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 670) * 3,500,000]/1024/1024 = 12417 MB ~ 12.13 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-message-body-tracking-activated"></a><span data-ttu-id="c36d8-122">Messages passant par un processus d'orchestration, envoyés vers une liste de distribution et pour lesquels le suivi du corps des messages est activé</span><span class="sxs-lookup"><span data-stu-id="c36d8-122">Messages in an orchestration that are sent out to a distribution list with message body tracking activated</span></span>  
 <span data-ttu-id="c36d8-123">Si, dans cet exemple, le suivi de message est pris en compte, l'équation se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="c36d8-123">If you want to accommodate message tracking, the equation will look like the following for this example:</span></span>  
  
```  
[3,500,000 * 6 * 5KB]/1024 = 102539.06 MB ~ 100.14 GB per year  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c36d8-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c36d8-124">See Also</span></span>  
 <span data-ttu-id="c36d8-125">[À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="c36d8-125">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="c36d8-126">[Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="c36d8-126">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="c36d8-127">[Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="c36d8-127">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="c36d8-128">[Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="c36d8-128">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="c36d8-129">Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages</span><span class="sxs-lookup"><span data-stu-id="c36d8-129">Scenario 4: Sizing the Tracking Database for all Messages</span></span>](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)