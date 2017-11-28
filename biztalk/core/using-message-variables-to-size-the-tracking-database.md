---
title: "À l’aide de Variables de Message à la taille de la base de données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message variables [Tracking database], CMsgs
- message variables [Tracking database], Events
- message variables [Tracking database], Properties
- Tracking database, database size
- message variables [Tracking database], Nserv
- message variables [Tracking database], Msgs
- message variables [Tracking database], PropSize
- message variables [Tracking database]
- message variables [Tracking database], MsgSize
- message variables [Tracking database], MsgNum
- Tracking database, messages
ms.assetid: 2d31ae25-3d16-4002-b5a5-dca25e764ecd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5418cdf79499302e6127db7fb66f108825a0d8c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-message-variables-to-size-the-tracking-database"></a><span data-ttu-id="04684-102">Utilisation de variables de message pour déterminer la taille de la base de données des suivis</span><span class="sxs-lookup"><span data-stu-id="04684-102">Using Message Variables to Size the Tracking Database</span></span>
<span data-ttu-id="04684-103">Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un certain nombre de variables permettent de déterminer la taille que la base de données des suivis BizTalk (BizTalkDTADb) est susceptible d'atteindre au bout d'une période donnée.</span><span class="sxs-lookup"><span data-stu-id="04684-103">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can use a number of variables to determine how large the BizTalk Tracking (BizTalkDTADb) database will become over a given period of time.</span></span> <span data-ttu-id="04684-104">Ces variables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="04684-104">These variables are:</span></span>  
  
-   <span data-ttu-id="04684-105">nombre de pipelines utilisés ;</span><span class="sxs-lookup"><span data-stu-id="04684-105">Number of pipelines used</span></span>  
  
-   <span data-ttu-id="04684-106">nombre d'orchestrations concernées ;</span><span class="sxs-lookup"><span data-stu-id="04684-106">Number of orchestrations involved</span></span>  
  
-   <span data-ttu-id="04684-107">nombre d'événements générés ;</span><span class="sxs-lookup"><span data-stu-id="04684-107">Number of events generated</span></span>  
  
-   <span data-ttu-id="04684-108">Nombre de propriétés de message soumises à un suivi</span><span class="sxs-lookup"><span data-stu-id="04684-108">Number of message properties tracked</span></span>  
  
-   <span data-ttu-id="04684-109">nombre de messages créés ;</span><span class="sxs-lookup"><span data-stu-id="04684-109">Number of additional messages created</span></span>  
  
-   <span data-ttu-id="04684-110">estimation du nombre de messages reçus dans le laps de temps spécifié.</span><span class="sxs-lookup"><span data-stu-id="04684-110">Estimated number of messages received in the specified timeframe</span></span>  
  
 <span data-ttu-id="04684-111">Bien que l'équation à utiliser afin d'obtenir une estimation de la taille de la base de données des suivis soit simple, vous devez l'appliquer à chaque processus de messagerie entrant et sortant qui utilise l'implémentation BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="04684-111">While the equation you use to estimate the size of the BizTalk Tracking database is straightforward, you must apply it to each incoming and outgoing message process that uses the BizTalk Server implementation.</span></span> <span data-ttu-id="04684-112">En d'autres termes, vous devez appliquer cette équation à chacun des différents scénarios de message et ajouter les résultats obtenus pour arriver à une estimation de la taille finale de la base de données.</span><span class="sxs-lookup"><span data-stu-id="04684-112">In other words, you will need to apply this equation for every distinct message scenario and then add up the results to obtain the final estimated database size.</span></span> <span data-ttu-id="04684-113">Dans le cas présent, nous examinerons deux scénarios.</span><span class="sxs-lookup"><span data-stu-id="04684-113">In this document we will look at two scenarios.</span></span> <span data-ttu-id="04684-114">Il s'agit des scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="04684-114">The scenarios are:</span></span>  
  
1.  <span data-ttu-id="04684-115">Réception et transformation d'un message, puis envoi du message ainsi obtenu</span><span class="sxs-lookup"><span data-stu-id="04684-115">Receiving a message, transforming the message, and then sending the resulting message</span></span>  
  
2.  <span data-ttu-id="04684-116">Réception d'un message, application d'un processus d'entreprise, puis envoi du message ainsi obtenu</span><span class="sxs-lookup"><span data-stu-id="04684-116">Receiving a message, running a business process using the message, and then sending the resulting message.</span></span>  
  
 <span data-ttu-id="04684-117">Ces deux types de scénarios peuvent se présenter dans un environnement BizTalk Server et chacun d'entre eux génère une quantité différente de données de suivi.</span><span class="sxs-lookup"><span data-stu-id="04684-117">Both of these scenarios may be present in a BizTalk Server installation, and each scenario generates a different amount of tracking data.</span></span> <span data-ttu-id="04684-118">La quantité totale de données de suivi générée par l'installation de BizTalk Server est égale à la somme de tous les scénarios.</span><span class="sxs-lookup"><span data-stu-id="04684-118">The total tracking data generated for the BizTalk Server installation is the sum of all the scenarios.</span></span>  
  
 <span data-ttu-id="04684-119">Voici quelques-unes des variables utilisées pour l'équation :</span><span class="sxs-lookup"><span data-stu-id="04684-119">The following are some variables used in the equation:</span></span>  
  
|<span data-ttu-id="04684-120">Variable</span><span class="sxs-lookup"><span data-stu-id="04684-120">Variable</span></span>|<span data-ttu-id="04684-121"> Description</span><span class="sxs-lookup"><span data-stu-id="04684-121">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="04684-122">**Nserv**</span><span class="sxs-lookup"><span data-stu-id="04684-122">**Nserv**</span></span>|<span data-ttu-id="04684-123">Nombre de services (nombre de pipelines + nombre d'orchestrations)</span><span class="sxs-lookup"><span data-stu-id="04684-123">Number of services (number of pipelines + number of orchestrations)</span></span>|  
|<span data-ttu-id="04684-124">**Événements**</span><span class="sxs-lookup"><span data-stu-id="04684-124">**Events**</span></span>|<span data-ttu-id="04684-125">Nombre d'événements de message générés</span><span class="sxs-lookup"><span data-stu-id="04684-125">Number of generated message events</span></span>|  
|<span data-ttu-id="04684-126">**Propriétés**</span><span class="sxs-lookup"><span data-stu-id="04684-126">**Properties**</span></span>|<span data-ttu-id="04684-127">Nombre de propriétés de message soumises à un suivi</span><span class="sxs-lookup"><span data-stu-id="04684-127">Number of message properties tracked</span></span>|  
|<span data-ttu-id="04684-128">**PropSize**</span><span class="sxs-lookup"><span data-stu-id="04684-128">**PropSize**</span></span>|<span data-ttu-id="04684-129">Taille en octets de la propriété promue (champ)</span><span class="sxs-lookup"><span data-stu-id="04684-129">Size (in bytes) of the promoted property (field)</span></span>|  
|<span data-ttu-id="04684-130">**CMsgs**</span><span class="sxs-lookup"><span data-stu-id="04684-130">**CMsgs**</span></span>|<span data-ttu-id="04684-131">Nombre de messages créés par message entrant</span><span class="sxs-lookup"><span data-stu-id="04684-131">Number of additional messages created per incoming message</span></span>|  
|<span data-ttu-id="04684-132">**Empilés**</span><span class="sxs-lookup"><span data-stu-id="04684-132">**Msgs**</span></span>|<span data-ttu-id="04684-133">Estimation du nombre de messages entrants dans un laps de temps donné</span><span class="sxs-lookup"><span data-stu-id="04684-133">Number of estimated incoming messages in a given time period</span></span>|  
|<span data-ttu-id="04684-134">**MsgSize**</span><span class="sxs-lookup"><span data-stu-id="04684-134">**MsgSize**</span></span>|<span data-ttu-id="04684-135">Taille du message</span><span class="sxs-lookup"><span data-stu-id="04684-135">Message size</span></span>|  
|<span data-ttu-id="04684-136">**MsgNum**</span><span class="sxs-lookup"><span data-stu-id="04684-136">**MsgNum**</span></span>|<span data-ttu-id="04684-137">Nombre de messages suivis pour chaque message entrant</span><span class="sxs-lookup"><span data-stu-id="04684-137">Number of messages tracked for each incoming message</span></span>|  
  
 <span data-ttu-id="04684-138">L'équation est la suivante :</span><span class="sxs-lookup"><span data-stu-id="04684-138">The equation is as follows:</span></span>  
  
```  
[((Nserv * 150 bytes) + (Events * 230 bytes) + (Properties * CMsgs*(52 bytes + PropSize))) * Msgs]/1024/1024 = Data size in MB  
```  
  
 <span data-ttu-id="04684-139">Cette équation permet de calculer uniquement les données de suivi générées par les messages mais ne prend pas en compte les données de suivi générées pour le débogueur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="04684-139">This equation calculates only the tracking data generated by the messages and does not include the tracking data generated for the Orchestration Debugger.</span></span> <span data-ttu-id="04684-140">Vous devez appliquer cette formule à chaque processus de message afin d'estimer la taille de la base de données des suivis.</span><span class="sxs-lookup"><span data-stu-id="04684-140">You must apply this formula to each message process to estimate the size of the BizTalk Tracking database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04684-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04684-141">See Also</span></span>  
 <span data-ttu-id="04684-142">[Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="04684-142">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="04684-143">[Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="04684-143">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="04684-144">[Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="04684-144">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 <span data-ttu-id="04684-145">[Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="04684-145">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="04684-146">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="04684-146">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)