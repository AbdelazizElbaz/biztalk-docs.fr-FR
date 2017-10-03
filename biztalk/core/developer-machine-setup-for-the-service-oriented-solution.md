---
title: "Installation d’ordinateur de développeur pour le Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developer servers
- service solution tutorial, deployment prerequisites
- service solution tutorial, developer servers
ms.assetid: a088696f-c1ee-4578-ac02-af29b6de086b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb3407dbccbc4dccc902892cf04fa71991b8d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developer-machine-setup-for-the-service-oriented-solution"></a><span data-ttu-id="907c0-102">Installation de l'ordinateur de développement pour la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="907c0-102">Developer Machine Setup for the Service Oriented Solution</span></span>
<span data-ttu-id="907c0-103">L'architecture orientée services (SOA) est une approche de la génération de systèmes distribués.</span><span class="sxs-lookup"><span data-stu-id="907c0-103">Service Oriented Architecture (SOA) is an approach to building distributed systems.</span></span> <span data-ttu-id="907c0-104">La solution orientée services montre comment plusieurs systèmes principaux utilisant différents protocoles peuvent être agrégés en un service unique que les clients peuvent consommer.</span><span class="sxs-lookup"><span data-stu-id="907c0-104">The service oriented solution demonstrates how several back-end systems using different protocols can be aggregated into a single service that clients can consume.</span></span> <span data-ttu-id="907c0-105">Cette solution intègre les services avec une approche qui garantit les caractéristiques de fourniture et de performance pour l'accord de niveau de service que vous devez respecter.</span><span class="sxs-lookup"><span data-stu-id="907c0-105">This solution integrates services with an approach that guarantees delivery and performance characteristics for the service level agreement that you need to satisfy.</span></span>  
  
 <span data-ttu-id="907c0-106">La solution orientée services est modélisée selon un scénario d'accord de niveau de service où BizTalk Server et les serveurs d'applications métier (LOB) qui y sont connectés ont trois secondes pour répondre avec une demande de service.</span><span class="sxs-lookup"><span data-stu-id="907c0-106">The service oriented solution is modeled after a service-level agreement scenario in which BizTalk Server and the Line of Business (LOB) application servers connected to it are given three seconds to respond with a service request.</span></span> <span data-ttu-id="907c0-107">L'une de ces trois secondes peut être utilisée par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="907c0-107">One of those three seconds may be taken up by the BizTalk Server.</span></span>  
  
 <span data-ttu-id="907c0-108">Il existe trois versions de la solution orientée services : adaptateur, inline et stub.</span><span class="sxs-lookup"><span data-stu-id="907c0-108">There are three versions of the service oriented solution: adapter, inline, and stub.</span></span> <span data-ttu-id="907c0-109">Pour plus d’informations sur les différences entre les trois versions de la solution orientée services, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="907c0-109">For more information about the differences between three versions of the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span> <span data-ttu-id="907c0-110">En tant que développeur, vous mettez en œuvre le scénario à l'aide de la version stub de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="907c0-110">As a developer, you get the scenario running by using the stub version of the scenario.</span></span> <span data-ttu-id="907c0-111">Cette version ne nécessite pas de serveurs principaux métier pour l'exécution.</span><span class="sxs-lookup"><span data-stu-id="907c0-111">This version does not require any LOB back-end servers in order to run.</span></span> <span data-ttu-id="907c0-112">Après cela, vous pouvez utiliser la version adaptateur du scénario pour savoir comment les divers adaptateurs et serveurs principaux peuvent être intégrés et configurés pour répondre en utilisant les serveurs BizTalk en tant que service unique.</span><span class="sxs-lookup"><span data-stu-id="907c0-112">After this you can use the adapter version of the scenario to learn how various adapters and back-end servers can be integrated and configured to respond using the BizTalk servers as a single service.</span></span> <span data-ttu-id="907c0-113">Vous pouvez ensuite mesurer la latence induite par BizTalk Server et ses adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="907c0-113">You can then measure the latency induced by BizTalk Server and its adapters.</span></span>  
  
 <span data-ttu-id="907c0-114">Si la latence du serveur BizTalk dépasse la configuration requise pour le service, vous contourner ignorer les points de persistance de l'adaptateur métier en installant et en exécutant la version inline de l'architecture orientée services.</span><span class="sxs-lookup"><span data-stu-id="907c0-114">If the latency for the BizTalk server is in excess of its service requirement, you can bypass the LOB adapter persistence points by installing and running the SOA in-line version.</span></span> <span data-ttu-id="907c0-115">Cette version contourne les adaptateurs et, par la suite, leurs contributions à la latence en raison du point de persistance MessageBox.</span><span class="sxs-lookup"><span data-stu-id="907c0-115">This version bypasses the adapters and subsequently their latency contributions due to the MessageBox persistence point.</span></span> <span data-ttu-id="907c0-116">Au lieu de cela, la version inline communique directement avec les serveurs principaux au travers de mécanismes RPC (appel de procédure distante), tels que DCOM.</span><span class="sxs-lookup"><span data-stu-id="907c0-116">Instead, the inline version talks straight to the back-end servers through Remote Procedure Calls (RPC) mechanisms such as DCOM.</span></span>  
  
 <span data-ttu-id="907c0-117">Pour plus d’informations sur le point de persistance MessageBox, consultez [persistance et le moteur d’Orchestration](../core/persistence-and-the-orchestration-engine.md).</span><span class="sxs-lookup"><span data-stu-id="907c0-117">For more information about the MessageBox persistence point, see [Persistence and the Orchestration Engine](../core/persistence-and-the-orchestration-engine.md).</span></span>  
  
 <span data-ttu-id="907c0-118">Ce guide de déploiement décrit comment installer et tester les trois versions de la solution orientée services sur un ordinateur unique.</span><span class="sxs-lookup"><span data-stu-id="907c0-118">This deployment guide describes how to install and test the three versions of the service-oriented solution on a single computer.</span></span>  
  
 <span data-ttu-id="907c0-119">Pour plus d’informations sur la solution orientée services, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="907c0-119">For more information about the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="907c0-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="907c0-120">In This Section</span></span>  
  
-   [<span data-ttu-id="907c0-121">Avant d’installer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="907c0-121">Before Installing the Service Oriented Solution</span></span>](../core/before-installing-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="907c0-122">Pour installer la Version Stub de Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="907c0-122">How to Install the Stub Version of the Service Oriented Solution</span></span>](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="907c0-123">Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="907c0-123">How to Install the Inline and Adapter Versions of the Service Oriented Solution</span></span>](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="907c0-124">Pour exécuter le Service Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="907c0-124">How to Run the Service Oriented Solution</span></span>](../core/how-to-run-the-service-oriented-solution.md)