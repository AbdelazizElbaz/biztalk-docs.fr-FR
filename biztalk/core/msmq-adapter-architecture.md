---
title: "Architecture de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, MSMQ adapters
- MSMQ adapters, architecture
ms.assetid: acecc2a4-0670-487e-be39-28a24c8c3f16
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd314b6f835568b6336121478268b84381a288ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msmq-adapter-architecture"></a><span data-ttu-id="f8b5f-102">Architecture de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="f8b5f-102">MSMQ Adapter Architecture</span></span>
<span data-ttu-id="f8b5f-103">L'adaptateur MSMQ vous permet de tirer parti des fonctionnalités du service Microsoft Message Queuing (également appelé MSMQ), normalement indisponibles dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-103">The MSMQ adapter lets you take advantage of Microsoft Message Queuing (also known as MSMQ) features that are otherwise unavailable in BizTalk Server.</span></span>  
  
## <a name="adapter-structure"></a><span data-ttu-id="f8b5f-104">Structure de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="f8b5f-104">Adapter Structure</span></span>  
 <span data-ttu-id="f8b5f-105">L'adaptateur MSMQ présente la même structure que d'autres adaptateurs BizTalk et utilise l'Infrastructure d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-105">The MSMQ adapter has the same structure as other BizTalk adapters and uses the Adapter Framework.</span></span> <span data-ttu-id="f8b5f-106">Il est constitué d'un composant de conception et d'un composant d'exécution.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-106">It is made up of a design-time component and a run-time component.</span></span> <span data-ttu-id="f8b5f-107">Le composant d'exécution, à son tour, contient les éléments qui implémentent le transport de messages.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-107">The run-time component, in turn, contains the elements that implement the message transport.</span></span>  
  
 <span data-ttu-id="f8b5f-108">Le composant de conception permet de configurer les propriétés de l'adaptateur pour l'envoi et la réception.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-108">The design-time component lets you configure the adapter properties for sending and receiving.</span></span>  
  
 <span data-ttu-id="f8b5f-109">Le composant d'exécution peut envoyer des messages à une file d'attente définie au moment de la conception ou recevoir des messages d'une file d'attente désignée.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-109">The run-time component can send messages to a queue defined at design time or receive messages from a designated queue.</span></span> <span data-ttu-id="f8b5f-110">L'exécution de l'adaptateur a lieu dans le même processus que celle de l'application BizTalk Server et n'est pas effectuée sur un hôte isolé.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-110">The adapter runtime runs in the same process as the BizTalk Server application and does not run in an isolated host.</span></span>  
  
 <span data-ttu-id="f8b5f-111">Tout le traitement des messages dépend du service Message Queuing local, même pour les files d'attente distantes.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-111">All message handling relies on the local Message Queuing service, even for remote queues.</span></span> <span data-ttu-id="f8b5f-112">Pour les files d'attente distantes, l'adaptateur transmet les messages au service Message Queuing local.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-112">For remote queues, the adapter hands messages off to the local Message Queuing service.</span></span> <span data-ttu-id="f8b5f-113">À son tour, ce dernier envoie les messages à la file d'attente distante.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-113">It, in turn, sends the messages to the remote queue.</span></span>  
  
 <span data-ttu-id="f8b5f-114">Pour obtenir une liste complète de l’envoi et réception des propriétés de configuration, consultez [comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md) et [comment configurer un emplacement de réception MSMQ](../core/how-to-configure-an-msmq-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="f8b5f-114">For a complete list of send and receive configuration properties, see [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md) and [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md).</span></span>  
  
 <span data-ttu-id="f8b5f-115">Pour plus d'informations sur le service Message Queuing, consultez les rubriques suivantes de la bibliothèque TechNet de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f8b5f-115">For more information about Message Queuing, see the following topics available in the Microsoft TechNet Library:</span></span>  
  
-   <span data-ttu-id="f8b5f-116">**Guide de conception de files d’attente de messages** à [http://go.microsoft.com/fwlink/?LinkId=137080](http://go.microsoft.com/fwlink/?LinkId=137080).</span><span class="sxs-lookup"><span data-stu-id="f8b5f-116">**Message Queuing Design Guide** at [http://go.microsoft.com/fwlink/?LinkId=137080](http://go.microsoft.com/fwlink/?LinkId=137080).</span></span>  
  
-   <span data-ttu-id="f8b5f-117">**Guide des opérations files d’attente de messages** à [http://go.microsoft.com/fwlink/?LinkId=137079](http://go.microsoft.com/fwlink/?LinkId=137079).</span><span class="sxs-lookup"><span data-stu-id="f8b5f-117">**Message Queuing Operations Guide** at [http://go.microsoft.com/fwlink/?LinkId=137079](http://go.microsoft.com/fwlink/?LinkId=137079).</span></span>  
  
-   <span data-ttu-id="f8b5f-118">**Guide de dépannage de Message Queuing** à [http://go.microsoft.com/fwlink/?LinkId=137081](http://go.microsoft.com/fwlink/?LinkId=137081).</span><span class="sxs-lookup"><span data-stu-id="f8b5f-118">**Message Queuing Troubleshooting Guide** at [http://go.microsoft.com/fwlink/?LinkId=137081](http://go.microsoft.com/fwlink/?LinkId=137081).</span></span>  
  
-   <span data-ttu-id="f8b5f-119">**Message Queuing Technical Reference** à [http://go.microsoft.com/fwlink/?LinkId=137082](http://go.microsoft.com/fwlink/?LinkId=137082).</span><span class="sxs-lookup"><span data-stu-id="f8b5f-119">**Message Queuing Technical Reference** at [http://go.microsoft.com/fwlink/?LinkId=137082](http://go.microsoft.com/fwlink/?LinkId=137082).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b5f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8b5f-120">See Also</span></span>  
 [<span data-ttu-id="f8b5f-121">Nouveautés de l’adaptateur MSMQ ?</span><span class="sxs-lookup"><span data-stu-id="f8b5f-121">What Is the MSMQ Adapter?</span></span>](../core/what-is-the-msmq-adapter.md)