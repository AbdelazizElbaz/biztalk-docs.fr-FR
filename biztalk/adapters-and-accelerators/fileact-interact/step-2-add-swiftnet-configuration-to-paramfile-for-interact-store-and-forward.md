---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a18a43c-1dd9-4113-bf32-8bc7bf9338b0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78aa75762e40bfcdd033a057610cb34f38825dd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="d2e28-102">Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="d2e28-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="d2e28-103">Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="d2e28-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="d2e28-104">Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="d2e28-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="d2e28-105">Pour ajouter des SWIFTNet configuration à le paramfile</span><span class="sxs-lookup"><span data-stu-id="d2e28-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="d2e28-106">Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="d2e28-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d2e28-107">Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span><span class="sxs-lookup"><span data-stu-id="d2e28-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span></span>  
  
2.  <span data-ttu-id="d2e28-108">Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :</span><span class="sxs-lookup"><span data-stu-id="d2e28-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="d2e28-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="d2e28-109">username:snlowner</span></span>  
  
     <span data-ttu-id="d2e28-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="d2e28-110">subsystem_name:InteractStub</span></span>  
  
     <span data-ttu-id="d2e28-111">\#subsystem_group:Interactsnf</span><span class="sxs-lookup"><span data-stu-id="d2e28-111">\#subsystem_group:Interactsnf</span></span>  
  
     <span data-ttu-id="d2e28-112">\#subsystem_dependency:support, essaim</span><span class="sxs-lookup"><span data-stu-id="d2e28-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="d2e28-113">subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="d2e28-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="d2e28-114">subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="d2e28-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="d2e28-115">**Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour interagir MSNG > - AdapterMode interagir »**</span><span class="sxs-lookup"><span data-stu-id="d2e28-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact SnF> -AdapterMode Interact"**</span></span>  
  
     <span data-ttu-id="d2e28-116">* FIN</span><span class="sxs-lookup"><span data-stu-id="d2e28-116">*END</span></span>  
  
     <span data-ttu-id="d2e28-117">subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="d2e28-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="d2e28-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="d2e28-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="d2e28-119">* FIN</span><span class="sxs-lookup"><span data-stu-id="d2e28-119">*END</span></span>  
  
     <span data-ttu-id="d2e28-120">subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="d2e28-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="d2e28-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="d2e28-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="d2e28-122">* FIN</span><span class="sxs-lookup"><span data-stu-id="d2e28-122">*END</span></span>  
  
     <span data-ttu-id="d2e28-123">start_event:SNL001:Subsystem InteractStubSnF est activé</span><span class="sxs-lookup"><span data-stu-id="d2e28-123">start_event:SNL001:subsystem InteractStubSnF is up</span></span>  
  
     <span data-ttu-id="d2e28-124">stop_event:SNL002:Subsystem InteractStubSnF est arrêté</span><span class="sxs-lookup"><span data-stu-id="d2e28-124">stop_event:SNL002:subsystem InteractStubSnF is down</span></span>  
  
     <span data-ttu-id="d2e28-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="d2e28-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="d2e28-126">\##subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="d2e28-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="d2e28-127">\##subsystem_dependency :</span><span class="sxs-lookup"><span data-stu-id="d2e28-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="d2e28-128">\#subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="d2e28-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="d2e28-129">\#subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="d2e28-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="d2e28-130">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="d2e28-130">\#*END</span></span>  
  
     <span data-ttu-id="d2e28-131">\#subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="d2e28-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="d2e28-132">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="d2e28-132">\#*END</span></span>  
  
     <span data-ttu-id="d2e28-133">\#subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="d2e28-133">\#subsystem_status:</span></span>  
  
     <span data-ttu-id="d2e28-134">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="d2e28-134">\#*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="d2e28-135">start_event:SNL001:Subsystem utilisateur est activé</span><span class="sxs-lookup"><span data-stu-id="d2e28-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="d2e28-136">stop_event:SNL002:Subsystem utilisateur est arrêté</span><span class="sxs-lookup"><span data-stu-id="d2e28-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e28-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2e28-137">See Also</span></span>  
 <span data-ttu-id="d2e28-138">[Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d2e28-138">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="d2e28-139">[Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d2e28-139">[Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="d2e28-140">[Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="d2e28-140">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="d2e28-141">Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant</span><span class="sxs-lookup"><span data-stu-id="d2e28-141">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)