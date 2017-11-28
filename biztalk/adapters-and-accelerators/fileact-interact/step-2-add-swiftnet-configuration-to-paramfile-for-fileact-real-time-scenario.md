---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4feec3f-4755-477e-b3d6-1dd6d075255e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 793378e25c3ba92170e1da36b0c8276ab13357ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-real-time-scenario"></a><span data-ttu-id="de35e-102">Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="de35e-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="de35e-103">Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="de35e-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
 <span data-ttu-id="de35e-104">Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="de35e-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="de35e-105">Pour ajouter des SWIFTNet configuration à le paramfile</span><span class="sxs-lookup"><span data-stu-id="de35e-105">To add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="de35e-106">Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="de35e-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="de35e-107">Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="de35e-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
2.  <span data-ttu-id="de35e-108">Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :</span><span class="sxs-lookup"><span data-stu-id="de35e-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
  
     <span data-ttu-id="de35e-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="de35e-109">username:snlowner</span></span>  
  
     <span data-ttu-id="de35e-110">subsystem_name:FileactStub</span><span class="sxs-lookup"><span data-stu-id="de35e-110">subsystem_name:FileactStub</span></span>  
  
     <span data-ttu-id="de35e-111">\#subsystem_group:FileAct</span><span class="sxs-lookup"><span data-stu-id="de35e-111">\#subsystem_group:fileact</span></span>  
  
     <span data-ttu-id="de35e-112">\#subsystem_dependency:support, essaim</span><span class="sxs-lookup"><span data-stu-id="de35e-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="de35e-113">subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="de35e-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="de35e-114">subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="de35e-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="de35e-115">**Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour fileact RT > - AdapterMode fileact »**</span><span class="sxs-lookup"><span data-stu-id="de35e-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact RT > -AdapterMode fileact"**</span></span>  
  
     <span data-ttu-id="de35e-116">* FIN</span><span class="sxs-lookup"><span data-stu-id="de35e-116">*END</span></span>  
  
     <span data-ttu-id="de35e-117">subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="de35e-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="de35e-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="de35e-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="de35e-119">* FIN</span><span class="sxs-lookup"><span data-stu-id="de35e-119">*END</span></span>  
  
     <span data-ttu-id="de35e-120">subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="de35e-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="de35e-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="de35e-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="de35e-122">* FIN</span><span class="sxs-lookup"><span data-stu-id="de35e-122">*END</span></span>  
  
     <span data-ttu-id="de35e-123">start_event:SNL001:Subsystem FileactStub est activé</span><span class="sxs-lookup"><span data-stu-id="de35e-123">start_event:SNL001:subsystem FileactStub is up</span></span>  
  
     <span data-ttu-id="de35e-124">stop_event:SNL002:Subsystem FileactStub est arrêté</span><span class="sxs-lookup"><span data-stu-id="de35e-124">stop_event:SNL002:subsystem FileactStub is down</span></span>  
  
     <span data-ttu-id="de35e-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="de35e-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="de35e-126">\##subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="de35e-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="de35e-127">\##subsystem_dependency :</span><span class="sxs-lookup"><span data-stu-id="de35e-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="de35e-128">\#subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="de35e-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="de35e-129">\#subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="de35e-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="de35e-130">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="de35e-130">\#*END</span></span>  
  
     <span data-ttu-id="de35e-131">\#subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="de35e-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="de35e-132">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="de35e-132">\#*END</span></span>  
  
     <span data-ttu-id="de35e-133">\#subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="de35e-133">\#subsystem_status:</span></span>  
  
     #<a name="end"></a><span data-ttu-id="de35e-134">* FIN</span><span class="sxs-lookup"><span data-stu-id="de35e-134">*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="de35e-135">start_event:SNL001:Subsystem utilisateur est activé</span><span class="sxs-lookup"><span data-stu-id="de35e-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="de35e-136">stop_event:SNL002:Subsystem utilisateur est arrêté</span><span class="sxs-lookup"><span data-stu-id="de35e-136">stop_event:SNL002:subsystem User is down</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de35e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de35e-137">See Also</span></span>  
 <span data-ttu-id="de35e-138">[Scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="de35e-138">[FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="de35e-139">[Étape 1 : Configurer l’adaptateur SWIFT pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="de35e-139">[Step 1: Configure the SWIFT Adapter for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="de35e-140">[Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="de35e-140">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="de35e-141">Étape 4 : Tester le scénario de bout en bout FileAct en temps réel</span><span class="sxs-lookup"><span data-stu-id="de35e-141">Step 4: Test FileAct Real-Time End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)