---
title: "Préparation à l’utilisation de la Tutorial1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a792b2-8351-4ae8-9d7c-75420c00af03
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efedfeb184b8b0105b8622b6b3f068faffd6a906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preparing-to-use-the-tutorial"></a><span data-ttu-id="8dce5-102">Préparation à l’utilisation du didacticiel</span><span class="sxs-lookup"><span data-stu-id="8dce5-102">Preparing to Use the Tutorial</span></span>
<span data-ttu-id="8dce5-103">Vous devez procédez comme suit avant d’utiliser le didacticiel de bout en bout pour l’adaptateur A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="8dce5-103">You must do the following before using the A4SWIFT adapter end-to-end tutorial.</span></span>  
  
1.  <span data-ttu-id="8dce5-104">Vous devez les artefacts SWIFT suivants pour ce didacticiel :</span><span class="sxs-lookup"><span data-stu-id="8dce5-104">You will need the following SWIFT artifacts for this tutorial:</span></span>  
  
    -   <span data-ttu-id="8dce5-105">Alliance SWIFT passerelle (trous) 6.1</span><span class="sxs-lookup"><span data-stu-id="8dce5-105">SWIFT Alliance Gateway (SAG) 6.1</span></span>  
  
    -   <span data-ttu-id="8dce5-106">Accès à distance (RA) 6.1</span><span class="sxs-lookup"><span data-stu-id="8dce5-106">Remote Access (RA) 6.1</span></span>  
  
    -   <span data-ttu-id="8dce5-107">SWIFT WebStation 6.0</span><span class="sxs-lookup"><span data-stu-id="8dce5-107">SWIFT WebStation 6.0</span></span>  
  
    -   <span data-ttu-id="8dce5-108">Lien SWIFTNet (SNL) 6.1</span><span class="sxs-lookup"><span data-stu-id="8dce5-108">SWIFTNet Link (SNL) 6.1</span></span>  
  
2.  <span data-ttu-id="8dce5-109">Vous devez configurer des trous : créer les MessagePartners, les Points de terminaison et les règles de routage dans les trous et tester la connectivité des trous sur l’ordinateur sur lequel vous installez les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="8dce5-109">You must configure SAG: create the MessagePartners, End Points, and Routing Rules in SAG, and test SAG connectivity on the computer where you install the adapters.</span></span> <span data-ttu-id="8dce5-110">Pour plus d’informations, consultez la documentation de trous.</span><span class="sxs-lookup"><span data-stu-id="8dce5-110">For information, see the SAG documentation.</span></span>  
  
3.  <span data-ttu-id="8dce5-111">Suivez les instructions figurant dans la rubrique « Comment pour créer un nouvel hôte » dans l’aide de Microsoft BizTalk Server ([http://go.microsoft.com/fwlink/? LinkId = 100422](http://go.microsoft.com/fwlink/?LinkId=100422)) pour créer un hôte in-process pour l’adaptateur InterAct, nommé *interacthost*et un hôte in-process pour l’adaptateur FileAct, nommé *fileacthost*.</span><span class="sxs-lookup"><span data-stu-id="8dce5-111">Follow the instructions listed in the topic “How to Create a New Host” in Microsoft BizTalk Server Help ([http://go.microsoft.com/fwlink/?LinkId=100422](http://go.microsoft.com/fwlink/?LinkId=100422)) to create one in-process Host for the InterAct adapter, named *interacthost*, and one in-process Host for the FileAct adapter, named *fileacthost*.</span></span> <span data-ttu-id="8dce5-112">Vous allez utiliser ces ordinateurs hôtes lors de la création de gestionnaires pour les adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="8dce5-112">You will use these hosts while creating handlers for the adapters.</span></span>  
  
4.  <span data-ttu-id="8dce5-113">Créez les dossiers suivants pour le didacticiel :</span><span class="sxs-lookup"><span data-stu-id="8dce5-113">Create the following folders for the tutorial:</span></span>  
  
    -   <span data-ttu-id="8dce5-114">c:\SWIFTAdapterTutorial\Fileact\ClientLocation</span><span class="sxs-lookup"><span data-stu-id="8dce5-114">c:\SWIFTAdapterTutorial\Fileact\ClientLocation</span></span>  
  
    -   <span data-ttu-id="8dce5-115">c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime</span><span class="sxs-lookup"><span data-stu-id="8dce5-115">c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime</span></span>  
  
    -   <span data-ttu-id="8dce5-116">c:\SWIFTAdapterTutorial\Fileact\ResponseClient</span><span class="sxs-lookup"><span data-stu-id="8dce5-116">c:\SWIFTAdapterTutorial\Fileact\ResponseClient</span></span>  
  
    -   <span data-ttu-id="8dce5-117">c:\SWIFTAdapterTutorial\Fileact\ResponseServer</span><span class="sxs-lookup"><span data-stu-id="8dce5-117">c:\SWIFTAdapterTutorial\Fileact\ResponseServer</span></span>  
  
    -   <span data-ttu-id="8dce5-118">c:\SWIFTAdapterTutorial\Fileact\ServerLocation</span><span class="sxs-lookup"><span data-stu-id="8dce5-118">c:\SWIFTAdapterTutorial\Fileact\ServerLocation</span></span>  
  
    -   <span data-ttu-id="8dce5-119">c:\SWIFTAdapterTutorial\Fileact\StatusEvents</span><span class="sxs-lookup"><span data-stu-id="8dce5-119">c:\SWIFTAdapterTutorial\Fileact\StatusEvents</span></span>  
  
    -   <span data-ttu-id="8dce5-120">c:\SWIFTAdapterTutorial\Fileact\PullRequest</span><span class="sxs-lookup"><span data-stu-id="8dce5-120">c:\SWIFTAdapterTutorial\Fileact\PullRequest</span></span>  
  
    -   <span data-ttu-id="8dce5-121">c:\SWIFTAdapterTutorial\Fileact\PullResponse</span><span class="sxs-lookup"><span data-stu-id="8dce5-121">c:\SWIFTAdapterTutorial\Fileact\PullResponse</span></span>  
  
    -   <span data-ttu-id="8dce5-122">c:\SWIFTAdapterTutorial\Interact\HandleRequest</span><span class="sxs-lookup"><span data-stu-id="8dce5-122">c:\SWIFTAdapterTutorial\Interact\HandleRequest</span></span>  
  
    -   <span data-ttu-id="8dce5-123">c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime</span><span class="sxs-lookup"><span data-stu-id="8dce5-123">c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime</span></span>  
  
    -   <span data-ttu-id="8dce5-124">c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF</span><span class="sxs-lookup"><span data-stu-id="8dce5-124">c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF</span></span>  
  
    -   <span data-ttu-id="8dce5-125">c:\SWIFTAdapterTutorial\Interact\Response</span><span class="sxs-lookup"><span data-stu-id="8dce5-125">c:\SWIFTAdapterTutorial\Interact\Response</span></span>  
  
    -   <span data-ttu-id="8dce5-126">c:\SWIFTAdapterTutorial\Interact\PullRequest</span><span class="sxs-lookup"><span data-stu-id="8dce5-126">c:\SWIFTAdapterTutorial\Interact\PullRequest</span></span>  
  
    -   <span data-ttu-id="8dce5-127">c:\SWIFTAdapterTutorial\Interact\Pullresponse</span><span class="sxs-lookup"><span data-stu-id="8dce5-127">c:\SWIFTAdapterTutorial\Interact\Pullresponse</span></span>  
  
5.  <span data-ttu-id="8dce5-128">Vous devez disposer d’une connexion à SWIFT ITB ou un environnement dynamique à l’adaptateur de test.</span><span class="sxs-lookup"><span data-stu-id="8dce5-128">You must have a connection to SWIFT ITB or live environment to test the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dce5-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8dce5-129">See Also</span></span>  
 <span data-ttu-id="8dce5-130">[BizTalk FileAct et interagir didacticiel de bout en bout pour les cartes](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="8dce5-130">[BizTalk FileAct and InterAct Adapters End-to-End Tutorial](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md) </span></span>  
 <span data-ttu-id="8dce5-131">[Interagir scénario en temps réel](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8dce5-131">[InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="8dce5-132">[Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8dce5-132">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="8dce5-133">[Scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8dce5-133">[FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="8dce5-134">Scénario de transfert et de FileAct</span><span class="sxs-lookup"><span data-stu-id="8dce5-134">FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)