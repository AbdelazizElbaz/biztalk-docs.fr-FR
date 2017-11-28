---
title: La gestion des artefacts | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], artifacts
- managing [artifacts]
- artifacts, managing
- managing [artifacts], about managing artificats
ms.assetid: aa7c5e60-7c16-4bcf-b913-b1bdfc5c7543
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ccca48682f009a24f538015b055c45dd79a9587
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-artifacts"></a><span data-ttu-id="742b6-102">Gestion des artefacts</span><span class="sxs-lookup"><span data-stu-id="742b6-102">Managing Artifacts</span></span>
<span data-ttu-id="742b6-103">Cette section explique comment gérer les artefacts, notamment comment les ajouter à une application BizTalk et les en supprimer, et comment configurer leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="742b6-103">This section describes how to manage artifacts, including how to add and remove them from a BizTalk application and how to configure their properties.</span></span>  
  
 <span data-ttu-id="742b6-104">Les artefacts sont les éléments contenus dans une application BizTalk nécessaires à son exécution.</span><span class="sxs-lookup"><span data-stu-id="742b6-104">Artifacts are the items contained in a BizTalk application that are required for it to run.</span></span> <span data-ttu-id="742b6-105">Pour des informations générales sur l’utilisation des artefacts dans une application BizTalk, consultez [qu’est une Application BizTalk ?](../core/what-is-a-biztalk-application.md)</span><span class="sxs-lookup"><span data-stu-id="742b6-105">For background information about how artifacts are used in a BizTalk application, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md)</span></span> <span data-ttu-id="742b6-106">Pour plus d’informations générales sur les artefacts, consultez [Architecture d’exécution](../core/runtime-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="742b6-106">For background information about artifacts, see [Runtime Architecture](../core/runtime-architecture.md).</span></span> <span data-ttu-id="742b6-107">Pour plus d’informations sur la gestion des artefacts lorsque vous créez et modifiez une application BizTalk, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md).</span><span class="sxs-lookup"><span data-stu-id="742b6-107">For information about how you manipulate artifacts when you create and modify a BizTalk application, see [Creating and Modifying BizTalk Applications](../core/creating-and-modifying-biztalk-applications.md).</span></span>  

## <a name="tracking-artifacts"></a><span data-ttu-id="742b6-108">Artefacts de suivi</span><span class="sxs-lookup"><span data-stu-id="742b6-108">Tracking artifacts</span></span>
<span data-ttu-id="742b6-109">Une grande partie de la gestion des artefacts que vous créez est suivi.</span><span class="sxs-lookup"><span data-stu-id="742b6-109">A big part of managing the artifacts you create is tracking.</span></span> <span data-ttu-id="742b6-110">La console Administration de BizTalk Server permet de configurer diverses options de suivi pour les orchestrations, ports d'envoi, ports de réception et pipelines.</span><span class="sxs-lookup"><span data-stu-id="742b6-110">You can configure various tracking options during run time for orchestrations, send ports, receive ports, and pipelines using the BizTalk Server Administration console.</span></span> <span data-ttu-id="742b6-111">Vous pouvez modifier ces options à tout moment, sans interrompre le processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="742b6-111">You can change the tracking options for an item at any time, without interrupting the business process.</span></span>

<span data-ttu-id="742b6-112">Les paramètres de configuration du suivi permettent de suivre les types de données suivants :</span><span class="sxs-lookup"><span data-stu-id="742b6-112">The tracking configuration settings allow you to track the following types of data:</span></span>

- <span data-ttu-id="742b6-113">les données d'événements entrants et/ou sortants,</span><span class="sxs-lookup"><span data-stu-id="742b6-113">Inbound and/or outbound event data.</span></span> <span data-ttu-id="742b6-114">par exemple, l'ID d'un message, les heures de début et de fin d'un artefact ;</span><span class="sxs-lookup"><span data-stu-id="742b6-114">For example, message ID, start and stop times for the artifact.</span></span>

- <span data-ttu-id="742b6-115">les propriétés de messages entrants et/ou sortants,</span><span class="sxs-lookup"><span data-stu-id="742b6-115">Inbound and/or outbound message properties.</span></span> <span data-ttu-id="742b6-116">par exemple, les propriétés générales et promues de chaque message traité par l'artefact ;</span><span class="sxs-lookup"><span data-stu-id="742b6-116">For example, general and promoted properties for each message that the artifact processes.</span></span>

- <span data-ttu-id="742b6-117">les corps et parties de messages entrants et/ou sortants,</span><span class="sxs-lookup"><span data-stu-id="742b6-117">Inbound and/or outbound message bodies and parts.</span></span> <span data-ttu-id="742b6-118">par exemple, le corps et les parties de chaque message traité par l'artefact ;</span><span class="sxs-lookup"><span data-stu-id="742b6-118">For example, body and parts for each message that the artifact processes.</span></span>

- <span data-ttu-id="742b6-119">Orchestrations :</span><span class="sxs-lookup"><span data-stu-id="742b6-119">Orchestrations.</span></span> <span data-ttu-id="742b6-120">données d'exécution des formes d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="742b6-120">Execution data for orchestration shapes.</span></span>

<span data-ttu-id="742b6-121">[Affichage du Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md) fournit des informations de bonne.</span><span class="sxs-lookup"><span data-stu-id="742b6-121">[Viewing Tracked Message and Instance Data](../core/viewing-tracked-message-and-instance-data.md) provides some good info.</span></span> 


> [!TIP]
> <span data-ttu-id="742b6-122">Si vous définissez des options de suivi sur un pipeline, les options de suivi sont définies globalement pour tous les ports qui utilisant le pipeline.</span><span class="sxs-lookup"><span data-stu-id="742b6-122">If you set tracking options on a pipeline, then the tracking options are set globally for every port that uses the pipeline.</span></span> <span data-ttu-id="742b6-123">Par conséquent beaucoup plus de données en cours de suivi que vous éventuellement l’intention d’et pouvez avoir un impact sur les performances du système.</span><span class="sxs-lookup"><span data-stu-id="742b6-123">This results in far more data being tracked than you may intend, and may impact system performance.</span></span> <span data-ttu-id="742b6-124">Pendant le développement, cela peut être normal.</span><span class="sxs-lookup"><span data-stu-id="742b6-124">During development, this may be normal.</span></span> <span data-ttu-id="742b6-125">Dans les scénarios de production, nous vous recommandons d’activer les options de suivi sur les ports d’envoi et de ports, au lieu des pipelines de réception.</span><span class="sxs-lookup"><span data-stu-id="742b6-125">In production scenarios, we recommend you enable any tracking options on the send ports and receive ports, instead of the pipelines.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="742b6-126">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="742b6-126">In this section</span></span>  
  
-   [<span data-ttu-id="742b6-127">La gestion des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="742b6-127">Managing Orchestrations</span></span>](../core/managing-orchestrations.md)  
  
-   [<span data-ttu-id="742b6-128">Gestion des liens de rôle</span><span class="sxs-lookup"><span data-stu-id="742b6-128">Managing Role Links</span></span>](../core/managing-role-links.md)  
  
-   [<span data-ttu-id="742b6-129">La gestion des Ports d’envoi et groupes de ports d’envoi</span><span class="sxs-lookup"><span data-stu-id="742b6-129">Managing Send Ports and Send Port Groups</span></span>](../core/managing-send-ports-and-send-port-groups.md)  
  
-   [<span data-ttu-id="742b6-130">La gestion des Ports de réception</span><span class="sxs-lookup"><span data-stu-id="742b6-130">Managing Receive Ports</span></span>](../core/managing-receive-ports.md)  
  
-   [<span data-ttu-id="742b6-131">La gestion des emplacements de réception</span><span class="sxs-lookup"><span data-stu-id="742b6-131">Managing Receive Locations</span></span>](../core/managing-receive-locations.md)  
  
-   [<span data-ttu-id="742b6-132">Gestion des stratégies</span><span class="sxs-lookup"><span data-stu-id="742b6-132">Managing Policies</span></span>](../core/managing-policies.md)  
  
-   [<span data-ttu-id="742b6-133">Gestion des schémas</span><span class="sxs-lookup"><span data-stu-id="742b6-133">Managing Schemas</span></span>](../core/managing-schemas.md)  
  
-   [<span data-ttu-id="742b6-134">La gestion des mappages</span><span class="sxs-lookup"><span data-stu-id="742b6-134">Managing Maps</span></span>](../core/managing-maps.md)  
  
-   [<span data-ttu-id="742b6-135">Gestion des Pipelines</span><span class="sxs-lookup"><span data-stu-id="742b6-135">Managing Pipelines</span></span>](../core/managing-pipelines.md)  
  
-   [<span data-ttu-id="742b6-136">La gestion des ressources</span><span class="sxs-lookup"><span data-stu-id="742b6-136">Managing Resources</span></span>](../core/managing-resources.md)