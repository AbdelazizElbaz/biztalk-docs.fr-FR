---
title: 'Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: 5b8fed48-d9c9-4d1f-a320-d3e23b8b1ec9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9c99c99485e34f95c6f6a75b86170d73678518
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-1-sizing-the-tracking-database--for-simple-biztalk-messages"></a><span data-ttu-id="a179a-102">Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples</span><span class="sxs-lookup"><span data-stu-id="a179a-102">Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages</span></span>
<span data-ttu-id="a179a-103">Dans le schéma ci-dessous, un message BizTalk entre et sort du serveur BizTalk Server sans être soumis à aucune transformation.</span><span class="sxs-lookup"><span data-stu-id="a179a-103">In the following figure, a simple BizTalk Server message passes in and out of BizTalk Server without undergoing any message transformation.</span></span>  
  
 <span data-ttu-id="a179a-104">![Message de BizTalk Server simple &#45; Aucune transformation](../core/media/simple-bts-message.gif "Simple_BTS_Message")</span><span class="sxs-lookup"><span data-stu-id="a179a-104">![Simple BizTalk Server message &#45; no transformation](../core/media/simple-bts-message.gif "Simple_BTS_Message")</span></span>  
  
 <span data-ttu-id="a179a-105">**Un message BizTalk Server simple : aucune transformation**</span><span class="sxs-lookup"><span data-stu-id="a179a-105">**A simple BizTalk Server message - no transformation**</span></span>  
  
 <span data-ttu-id="a179a-106">Avant d'appliquer la formule décrite dans la section précédente, vous devez rassembler quelques informations concernant le présent scénario.</span><span class="sxs-lookup"><span data-stu-id="a179a-106">Before you apply the formula in the previous section, you will need to gather some facts about this scenario.</span></span> <span data-ttu-id="a179a-107">Dans cet exemple, les données sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a179a-107">In this example, we use the following:</span></span>  
  
-   <span data-ttu-id="a179a-108">taille du message : 5 Ko ;</span><span class="sxs-lookup"><span data-stu-id="a179a-108">The message size is 5K.</span></span>  
  
-   <span data-ttu-id="a179a-109">aucune propriété promue ;</span><span class="sxs-lookup"><span data-stu-id="a179a-109">No properties will be promoted.</span></span>  
  
-   <span data-ttu-id="a179a-110">nombre de messages reçus dans une année : 3,5 millions ;</span><span class="sxs-lookup"><span data-stu-id="a179a-110">The number of messages you receive in a year is 3.5 million.</span></span>  
  
-   <span data-ttu-id="a179a-111">suivi activé pour tous les événements,</span><span class="sxs-lookup"><span data-stu-id="a179a-111">Tracking is turned on for all events.</span></span> <span data-ttu-id="a179a-112">ici au nombre de quatre</span><span class="sxs-lookup"><span data-stu-id="a179a-112">There are four events in this scenario.</span></span> <span data-ttu-id="a179a-113">Les événements sont :</span><span class="sxs-lookup"><span data-stu-id="a179a-113">The events are:</span></span>  
  
    -   <span data-ttu-id="a179a-114">Réception du message M0</span><span class="sxs-lookup"><span data-stu-id="a179a-114">Receipt of message M0</span></span>  
  
    -   <span data-ttu-id="a179a-115">Sortie du message M1 provenant du port de réception</span><span class="sxs-lookup"><span data-stu-id="a179a-115">Output of message M1 from the receive port</span></span>  
  
    -   <span data-ttu-id="a179a-116">Réception du message M1 par le pipeline de transmission</span><span class="sxs-lookup"><span data-stu-id="a179a-116">Receipt of message M1 by the transmit pipeline</span></span>  
  
    -   <span data-ttu-id="a179a-117">Sortie du message M2 par le pipeline d'envoi</span><span class="sxs-lookup"><span data-stu-id="a179a-117">Output of message M2 by the send pipeline</span></span>  
  
-   <span data-ttu-id="a179a-118">création de deux messages dans ce scénario :</span><span class="sxs-lookup"><span data-stu-id="a179a-118">Two additional messages are created in this scenario.</span></span> <span data-ttu-id="a179a-119">le message M0 étant le message entrant, il n'est pas créé par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a179a-119">Message M0 is the incoming message and is therefore not created by BizTalk Server.</span></span> <span data-ttu-id="a179a-120">le message M1 sortant du port de réception et le message M2 sortant du port de transmission</span><span class="sxs-lookup"><span data-stu-id="a179a-120">Message M1 is the output message from the receive port and M2 is the output from the transmit port.</span></span> <span data-ttu-id="a179a-121">sont créés par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a179a-121">M1 and M2 are created by BizTalk Server.</span></span>  
  
 <span data-ttu-id="a179a-122">L'intégration de ces données à la formule précédemment mentionnée donne le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="a179a-122">Applying this information to the formula gives the following:</span></span>  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-with-a-single-promoted-property"></a><span data-ttu-id="a179a-123">Messages dont la propriété promue est unique</span><span class="sxs-lookup"><span data-stu-id="a179a-123">Messages with a single promoted property</span></span>  
 <span data-ttu-id="a179a-124">Reprenons l'exemple précédemment mentionné et prenons en compte les nouveaux éléments suivants dans le scénario.</span><span class="sxs-lookup"><span data-stu-id="a179a-124">Let's take another look at this example and add one additional fact to the scenario.</span></span> <span data-ttu-id="a179a-125">Vous souhaitez promouvoir un seul champ, d'environ 10 octets, du message d'origine.</span><span class="sxs-lookup"><span data-stu-id="a179a-125">You want to promote a single field, approximately 10 bytes in size, from the original message.</span></span> <span data-ttu-id="a179a-126">La taille maximale d'un champ promu est de 256 caractères, soit environ 256 octets (512 octets s'il s'agit de caractères Unicode).</span><span class="sxs-lookup"><span data-stu-id="a179a-126">The maximum size of a promoted field is 256 characters, or approximately 256 bytes (512 bytes if the characters are Unicode).</span></span>  
  
 <span data-ttu-id="a179a-127">En tenant compte de ces nouvelles données, l'équation se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="a179a-127">With this additional fact, the equation now appears as follows:</span></span>  
  
```  
[(2*150 bytes) + (4*230 bytes) + (1*2(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 124) * 3,500,000]/1024/1024 = 4486 MB ~ 4.38 GB per year  
```  
  
 <span data-ttu-id="a179a-128">Si vous souhaitez promouvoir un autre champ de 10 octets, l'équation est alors la suivante :</span><span class="sxs-lookup"><span data-stu-id="a179a-128">If you wanted to promote an additional field that is 10 bytes in size, the equation would be:</span></span>  
  
```  
[(2*150 bytes) + (4*230 bytes) + ((1*2*(52 bytes + 10 bytes) + (1*2*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 248) * 3,500,000]/1024/1024 = 4899 MB ~ 4.78 GB per year  
```  
  
 <span data-ttu-id="a179a-129">Vous pouvez donc constater que lorsqu'une seule propriété de 10 octets est promue dans ce scénario, la taille de la base de données des suivis augmente de 333,79 Mo (environ 0,33 Go) par an.</span><span class="sxs-lookup"><span data-stu-id="a179a-129">As you can see, if you promote a single 10-byte property in this scenario, it will add an additional 333.79 MB ~ 0.33 GB per year to the size of the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="a179a-130">Deux propriétés de 10 octets promues entraînent donc une augmentation annuelle de l'espace occupé par la base de données des suivis équivalente à 667,58 Mo (environ 0,65 Go).</span><span class="sxs-lookup"><span data-stu-id="a179a-130">Promoting two 10-byte properties will add an additional 667.58 MB ~ 0.65 GB of additional space per year to the size of the BizTalk Tracking database.</span></span>  
  
## <a name="messages-with-message-body-tracking-activated"></a><span data-ttu-id="a179a-131">Messages pour lesquels le suivi du corps des messages est activé</span><span class="sxs-lookup"><span data-stu-id="a179a-131">Messages with message body tracking activated</span></span>  
 <span data-ttu-id="a179a-132">Dans cet exemple, supposons qu'il soit prévu d'activer le suivi du corps des messages.</span><span class="sxs-lookup"><span data-stu-id="a179a-132">In this example, let us also assume that we are planning on activating message body tracking.</span></span> <span data-ttu-id="a179a-133">Il faut alors ajouter la seconde équation de suivi des messages comme indiqué dans la section précédente.</span><span class="sxs-lookup"><span data-stu-id="a179a-133">We will need to add the second equation for message tracking, shown in the previous section.</span></span> <span data-ttu-id="a179a-134">L'équation se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="a179a-134">The equation will look like the following for this example:</span></span>  
  
```  
[3,500,000 * 4 * 5KB]/1024 = 68359.375 MB ~ 66.75 GB per year  
  
```  
  
 <span data-ttu-id="a179a-135">En ajoutant les résultats des deux équations, il est possible d'estimer que la taille de la base de données des suivis augmentera de 54,48 Go à 54,88 Go par an.</span><span class="sxs-lookup"><span data-stu-id="a179a-135">By adding the results of the two equations, we can estimate that the BizTalk Tracking database will grow approximately 54.48 GB to 54.88 GB per year.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a179a-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a179a-136">See Also</span></span>  
 <span data-ttu-id="a179a-137">[À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="a179a-137">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="a179a-138">[Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="a179a-138">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="a179a-139">[Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="a179a-139">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 <span data-ttu-id="a179a-140">[Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="a179a-140">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="a179a-141">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="a179a-141">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)