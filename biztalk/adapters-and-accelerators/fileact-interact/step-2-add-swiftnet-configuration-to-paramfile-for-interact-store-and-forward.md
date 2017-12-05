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
ms.openlocfilehash: 05524abd4cd57b8d804ab5995072905392fd3645
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="ebeca-102">Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="ebeca-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="ebeca-103">Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="ebeca-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="ebeca-104">Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="ebeca-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="ebeca-105">Pour ajouter des SWIFTNet configuration à le paramfile</span><span class="sxs-lookup"><span data-stu-id="ebeca-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="ebeca-106">Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="ebeca-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ebeca-107">Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span><span class="sxs-lookup"><span data-stu-id="ebeca-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.</span></span>  
  
2.  <span data-ttu-id="ebeca-108">Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :</span><span class="sxs-lookup"><span data-stu-id="ebeca-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="ebeca-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="ebeca-109">username:snlowner</span></span>  
  
     <span data-ttu-id="ebeca-110">subsystem_name:InteractStub</span><span class="sxs-lookup"><span data-stu-id="ebeca-110">subsystem_name:InteractStub</span></span>  
  
     <span data-ttu-id="ebeca-111">\#subsystem_group:Interactsnf</span><span class="sxs-lookup"><span data-stu-id="ebeca-111">\#subsystem_group:Interactsnf</span></span>  
  
     <span data-ttu-id="ebeca-112">\#subsystem_dependency:support, essaim</span><span class="sxs-lookup"><span data-stu-id="ebeca-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="ebeca-113">subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="ebeca-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="ebeca-114">subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="ebeca-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="ebeca-115">**Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour interagir MSNG\> - AdapterMode interagir »**</span><span class="sxs-lookup"><span data-stu-id="ebeca-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for Interact SnF\> -AdapterMode Interact"**</span></span>  
  
     <span data-ttu-id="ebeca-116">* FIN</span><span class="sxs-lookup"><span data-stu-id="ebeca-116">*END</span></span>  
  
     <span data-ttu-id="ebeca-117">subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="ebeca-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="ebeca-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="ebeca-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="ebeca-119">* FIN</span><span class="sxs-lookup"><span data-stu-id="ebeca-119">*END</span></span>  
  
     <span data-ttu-id="ebeca-120">subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="ebeca-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="ebeca-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="ebeca-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="ebeca-122">* FIN</span><span class="sxs-lookup"><span data-stu-id="ebeca-122">*END</span></span>  
  
     <span data-ttu-id="ebeca-123">start_event:SNL001:Subsystem InteractStubSnF est activé</span><span class="sxs-lookup"><span data-stu-id="ebeca-123">start_event:SNL001:subsystem InteractStubSnF is up</span></span>  
  
     <span data-ttu-id="ebeca-124">stop_event:SNL002:Subsystem InteractStubSnF est arrêté</span><span class="sxs-lookup"><span data-stu-id="ebeca-124">stop_event:SNL002:subsystem InteractStubSnF is down</span></span>  
  
     <span data-ttu-id="ebeca-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="ebeca-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="ebeca-126">\##subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="ebeca-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="ebeca-127">\##subsystem_dependency :</span><span class="sxs-lookup"><span data-stu-id="ebeca-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="ebeca-128">\#subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="ebeca-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="ebeca-129">\#subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="ebeca-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="ebeca-130">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="ebeca-130">\#*END</span></span>  
  
     <span data-ttu-id="ebeca-131">\#subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="ebeca-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="ebeca-132">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="ebeca-132">\#*END</span></span>  
  
     <span data-ttu-id="ebeca-133">\#subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="ebeca-133">\#subsystem_status:</span></span>  
  
     <span data-ttu-id="ebeca-134">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="ebeca-134">\#*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="ebeca-135">start_event:SNL001:Subsystem utilisateur est activé</span><span class="sxs-lookup"><span data-stu-id="ebeca-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="ebeca-136">stop_event:SNL002:Subsystem utilisateur est arrêté</span><span class="sxs-lookup"><span data-stu-id="ebeca-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebeca-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebeca-137">See Also</span></span>  
 <span data-ttu-id="ebeca-138">[Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ebeca-138">[InterAct Store and Forward (Push) Scenario](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md) </span></span>  
 <span data-ttu-id="ebeca-139">[Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ebeca-139">[Step 1: Configure the SWIFT Adapter for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="ebeca-140">[Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ebeca-140">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="ebeca-141">Étape 4 : Tester le scénario de stockage et de redirection InterAct de bout en bout</span><span class="sxs-lookup"><span data-stu-id="ebeca-141">Step 4: Test the InterAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)