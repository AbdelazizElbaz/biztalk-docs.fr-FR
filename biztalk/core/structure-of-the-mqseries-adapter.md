---
title: "Structure de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, MQSeries adapters
- MQSeries adapters, architecture
ms.assetid: d25caf6a-3f93-4164-9c92-489b919a624d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6239b78f0b9bd2c44a314b7ba0ba6ace8f3b78e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structure-of-the-mqseries-adapter"></a><span data-ttu-id="7a5ae-102">Structure de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="7a5ae-102">Structure of the MQSeries Adapter</span></span>
<span data-ttu-id="7a5ae-103">L’adaptateur MQSeries comporte deux parties : l’adaptateur s’exécutant sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et une application COM +, MQSAgent, exécutée sous MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-103">The MQSeries adapter has two parts: the adapter running under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and a COM+ application, MQSAgent, running under MQSeries Server for Windows.</span></span> <span data-ttu-id="7a5ae-104">Cette relation est représentée dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-104">The following figure shows this relationship.</span></span>  
  
 <span data-ttu-id="7a5ae-105">![Composants de l’adaptateur MQSeries](../core/media/bts-dev-mqoverallstructure.gif "BTS_Dev_MQOverallStructure")</span><span class="sxs-lookup"><span data-stu-id="7a5ae-105">![MQSeries Adapter components](../core/media/bts-dev-mqoverallstructure.gif "BTS_Dev_MQOverallStructure")</span></span>  
  
 <span data-ttu-id="7a5ae-106">L'adaptateur communique avec l'application MQSAgent,</span><span class="sxs-lookup"><span data-stu-id="7a5ae-106">The adapter communicates with the MQSAgent application.</span></span> <span data-ttu-id="7a5ae-107">qui communique avec MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-107">The MQSAgent application, in turn, communicates with MQSeries Server for Windows.</span></span> <span data-ttu-id="7a5ae-108">Vous pouvez installer l'agent sur le même ordinateur que l'adaptateur si vous y installez également MQSeries Server pour Windows.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-108">You can install the agent on the same computer as the adapter if you install MQSeries Server for Windows on the computer.</span></span>  
  
 <span data-ttu-id="7a5ae-109">Le côté envoi de l'adaptateur envoie le message à MQSAgent.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-109">The send part of the adapter sends the message to the MQSAgent.</span></span> <span data-ttu-id="7a5ae-110">MQSAgent puis, à l’aide de **MQPut**, envoie le message au Gestionnaire de file d’attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-110">MQSAgent then, using **MQPut**, sends the message to the MQSeries Queue Manager.</span></span>  
  
 <span data-ttu-id="7a5ae-111">Le côté réception de l'adaptateur interroge MQSAgent pour rechercher des messages.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-111">The receive part of the adapter polls the MQSAgent to see if there are messages.</span></span> <span data-ttu-id="7a5ae-112">Lorsqu’un message, MQSAgent effectue une **MQGet** pour récupérer le message.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-112">When there is a message, the MQSAgent performs an **MQGet** to retrieve the message.</span></span> <span data-ttu-id="7a5ae-113">MQSAgent inclut un intervalle d'attente codé en dur de trois secondes pour la récupération du message à partir du gestionnaire de file d'attente.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-113">MQSAgent includes a hard-coded three-second wait for retrieving the message from the Queue Manager.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a5ae-114">Vous pouvez définir l'intervalle d'interrogation de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-114">You can set the polling interval of the adapter.</span></span> <span data-ttu-id="7a5ae-115">Lorsque vous définissez l'intervalle d'interrogation sur une valeur inférieure à trois secondes, l'intervalle d'attente est défini sur l'intervalle d'interrogation.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-115">When you set the polling interval to less than three seconds, the wait interval is set to the polling interval.</span></span>  
  
 <span data-ttu-id="7a5ae-116">Les actions d'envoi et de réception des messages peuvent se produire dans les transactions.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-116">Both the send and receive message actions may occur in transactions.</span></span> <span data-ttu-id="7a5ae-117">Ceci permet à l'adaptateur d'annuler le message et, le cas échéant, de retenter les opérations d'envoi ou de réception.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-117">This enables the adapter to roll back the message and, possibly, to retry the send or receive operations.</span></span> <span data-ttu-id="7a5ae-118">Pour plus d’informations sur les transactions, consultez [le traitement par lot de l’adaptateur MQSeries et de traitement des transactions](../core/mqseries-adapter-batching-and-transaction-handling.md).</span><span class="sxs-lookup"><span data-stu-id="7a5ae-118">For more information about transactions, see [MQSeries Adapter Batching and Transaction Handling](../core/mqseries-adapter-batching-and-transaction-handling.md).</span></span>  
  
 <span data-ttu-id="7a5ae-119">Le fait que l'adaptateur fonctionne sur plusieurs ordinateurs peut entraîner des problèmes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-119">Because the adapter works across more than one computer, there is a possible security problem.</span></span> <span data-ttu-id="7a5ae-120">Un programme hostile peut emprunter l'identité de l'agent et capturer des données.</span><span class="sxs-lookup"><span data-stu-id="7a5ae-120">A hostile program could impersonate the agent and capture data.</span></span> <span data-ttu-id="7a5ae-121">Pour plus d’informations sur la protection améliorée de la carte et l’agent, consultez [sécurité de l’adaptateur MQSeries](../core/mqseries-adapter-security.md).</span><span class="sxs-lookup"><span data-stu-id="7a5ae-121">For more information about enhanced protection for the adapter and agent, see [MQSeries Adapter Security](../core/mqseries-adapter-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a5ae-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a5ae-122">See Also</span></span>  
 <span data-ttu-id="7a5ae-123">[Architecture de l’adaptateur MQSeries](../core/mqseries-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="7a5ae-123">[MQSeries Adapter Architecture](../core/mqseries-adapter-architecture.md) </span></span>  
 [<span data-ttu-id="7a5ae-124">Nouveautés de l’adaptateur MQSeries ?</span><span class="sxs-lookup"><span data-stu-id="7a5ae-124">What Is the MQSeries Adapter?</span></span>](../core/what-is-the-mqseries-adapter.md)