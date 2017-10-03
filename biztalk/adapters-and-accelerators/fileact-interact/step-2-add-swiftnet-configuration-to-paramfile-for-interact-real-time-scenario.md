---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a900a6e-3e08-430a-8766-4a7192adba5e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 249bfb8120a7b7d44ee0f73e7b5e5cef34126670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-real-time-scenario"></a><span data-ttu-id="2b6ee-102">Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="2b6ee-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="2b6ee-103">Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="2b6ee-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span> <span data-ttu-id="2b6ee-104">Avant de commencer la procédure, vous devez effectuer les instructions de [étape 1 : configurer l’adaptateur SWIFT pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="2b6ee-104">Before you begin the procedure, you must complete the instructions in [Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="2b6ee-105">Pour ajouter des SWIFTNet configuration à le paramfile</span><span class="sxs-lookup"><span data-stu-id="2b6ee-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="2b6ee-106">Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="2b6ee-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
     <span data-ttu-id="2b6ee-107">Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="2b6ee-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
2.  <span data-ttu-id="2b6ee-108">Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="2b6ee-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="2b6ee-109">username:snlowner</span></span>  
  
     <span data-ttu-id="2b6ee-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="2b6ee-110">subsystem_name:InteractStub</span></span>  
  
     <span data-ttu-id="2b6ee-111">\#subsystem_group:InteractRT</span><span class="sxs-lookup"><span data-stu-id="2b6ee-111">\#subsystem_group:InteractRT</span></span>  
  
     <span data-ttu-id="2b6ee-112">\#subsystem_dependency:support, essaim</span><span class="sxs-lookup"><span data-stu-id="2b6ee-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="2b6ee-113">subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="2b6ee-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="2b6ee-114">subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="2b6ee-115">**Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour interagir RT > - AdapterMode interagir »**</span><span class="sxs-lookup"><span data-stu-id="2b6ee-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact RT > -AdapterMode Interact"**</span></span>  
  
     <span data-ttu-id="2b6ee-116">* FIN</span><span class="sxs-lookup"><span data-stu-id="2b6ee-116">*END</span></span>  
  
     <span data-ttu-id="2b6ee-117">subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="2b6ee-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="2b6ee-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="2b6ee-119">* FIN</span><span class="sxs-lookup"><span data-stu-id="2b6ee-119">*END</span></span>  
  
     <span data-ttu-id="2b6ee-120">subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="2b6ee-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="2b6ee-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="2b6ee-122">* FIN</span><span class="sxs-lookup"><span data-stu-id="2b6ee-122">*END</span></span>  
  
     <span data-ttu-id="2b6ee-123">start_event:SNL001:Subsystem InteractStub est activé</span><span class="sxs-lookup"><span data-stu-id="2b6ee-123">start_event:SNL001:subsystem InteractStub is up</span></span>  
  
     <span data-ttu-id="2b6ee-124">stop_event:SNL002:Subsystem InteractStub est arrêté</span><span class="sxs-lookup"><span data-stu-id="2b6ee-124">stop_event:SNL002:subsystem InteractStub is down</span></span>  
  
     <span data-ttu-id="2b6ee-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="2b6ee-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="2b6ee-126">\##subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="2b6ee-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="2b6ee-127">\##subsystem_dependency :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="2b6ee-128">\#subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="2b6ee-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="2b6ee-129">\#subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="2b6ee-130">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="2b6ee-130">\#*END</span></span>  
  
     <span data-ttu-id="2b6ee-131">\#subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="2b6ee-132">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="2b6ee-132">\#*END</span></span>  
  
     <span data-ttu-id="2b6ee-133">\#subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="2b6ee-133">\#subsystem_status:</span></span>  
  
     #<a name="end"></a><span data-ttu-id="2b6ee-134">* FIN</span><span class="sxs-lookup"><span data-stu-id="2b6ee-134">*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="2b6ee-135">start_event:SNL001:Subsystem utilisateur est activé</span><span class="sxs-lookup"><span data-stu-id="2b6ee-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="2b6ee-136">stop_event:SNL002:Subsystem utilisateur est arrêté</span><span class="sxs-lookup"><span data-stu-id="2b6ee-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6ee-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b6ee-137">See Also</span></span>  
 <span data-ttu-id="2b6ee-138">[Interagir scénario en temps réel](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2b6ee-138">[InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="2b6ee-139">[Étape 1 : Configurer l’adaptateur SWIFT pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2b6ee-139">[Step 1: Configure the SWIFT Adapter for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="2b6ee-140">[Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2b6ee-140">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="2b6ee-141">Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel</span><span class="sxs-lookup"><span data-stu-id="2b6ee-141">Step 4: Test the InterAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)