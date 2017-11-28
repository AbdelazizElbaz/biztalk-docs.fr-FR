---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088ab41f-8325-4330-b6f2-0164aa1911b1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b3048198747dd8d283ea9f7b329db27db615436
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="8ee70-102">Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="8ee70-102">Step 2: Add SWIFTNet Configuration to the Paramfile for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="8ee70-103">Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="8ee70-103">The Server message partners created in SAG must be specified in the SWIFTNet paramfile to enable Receivers to initialize with these values.</span></span>  
  
<span data-ttu-id="8ee70-104">Complète [étape 1 : configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) avant de commencer cette étape.</span><span class="sxs-lookup"><span data-stu-id="8ee70-104">Complete [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) before you begin this step.</span></span>
  
## <a name="add-swiftnet-configuration-to-the-paramfile"></a><span data-ttu-id="8ee70-105">Ajouter des configurations de SWIFTNet à la paramfile</span><span class="sxs-lookup"><span data-stu-id="8ee70-105">Add SWIFTNet configuration to the paramfile</span></span>  
  
1.  <span data-ttu-id="8ee70-106">Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="8ee70-106">Open the paramfile in a text editor, such as Notepad.</span></span>  
  
2.  <span data-ttu-id="8ee70-107">Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span><span class="sxs-lookup"><span data-stu-id="8ee70-107">The paramfile is typically located at: C:\SWIFTAlliance\RA\Ra1\cfg\paramfile</span></span>  
  
3.  <span data-ttu-id="8ee70-108">Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :</span><span class="sxs-lookup"><span data-stu-id="8ee70-108">In the paramfile, make the highlighted change to specify the Server Message partner name:</span></span>  
    
     <span data-ttu-id="8ee70-109">username:snlowner</span><span class="sxs-lookup"><span data-stu-id="8ee70-109">username:snlowner</span></span>  
  
     <span data-ttu-id="8ee70-110">subsystem_name:FileactStub</span><span class="sxs-lookup"><span data-stu-id="8ee70-110">subsystem_name:FileactStub</span></span>  
  
     <span data-ttu-id="8ee70-111">\#subsystem_group:fileactsnf</span><span class="sxs-lookup"><span data-stu-id="8ee70-111">\#subsystem_group:fileactsnf</span></span>  
  
     <span data-ttu-id="8ee70-112">\#subsystem_dependency:support, essaim</span><span class="sxs-lookup"><span data-stu-id="8ee70-112">\#subsystem_dependency:Support,Swarm</span></span>  
  
     <span data-ttu-id="8ee70-113">subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="8ee70-113">subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="8ee70-114">subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="8ee70-114">subsystem_start:</span></span>  
  
     <span data-ttu-id="8ee70-115">**Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour fileact MSNG > - AdapterMode fileact »**</span><span class="sxs-lookup"><span data-stu-id="8ee70-115">**spawn "snlreceiver -SagMessagePartner \<Server MessagePartnerName for fileact SnF> -AdapterMode fileact"**</span></span>  
  
     <span data-ttu-id="8ee70-116">* FIN</span><span class="sxs-lookup"><span data-stu-id="8ee70-116">*END</span></span>  
  
     <span data-ttu-id="8ee70-117">subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="8ee70-117">subsystem_stop:</span></span>  
  
     <span data-ttu-id="8ee70-118">* KILL9:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="8ee70-118">*KILL9:snlreceiver</span></span>  
  
     <span data-ttu-id="8ee70-119">* FIN</span><span class="sxs-lookup"><span data-stu-id="8ee70-119">*END</span></span>  
  
     <span data-ttu-id="8ee70-120">subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="8ee70-120">subsystem_status:</span></span>  
  
     <span data-ttu-id="8ee70-121">* NB:1:snlreceiver</span><span class="sxs-lookup"><span data-stu-id="8ee70-121">*NB:1:snlreceiver</span></span>  
  
     <span data-ttu-id="8ee70-122">* FIN</span><span class="sxs-lookup"><span data-stu-id="8ee70-122">*END</span></span>  
  
     <span data-ttu-id="8ee70-123">start_event:SNL001:Subsystem FileactStubSnF est activé</span><span class="sxs-lookup"><span data-stu-id="8ee70-123">start_event:SNL001:subsystem FileactStubSnF is up</span></span>  
  
     <span data-ttu-id="8ee70-124">stop_event:SNL002:Subsystem FileactStubSnF est arrêté</span><span class="sxs-lookup"><span data-stu-id="8ee70-124">stop_event:SNL002:subsystem FileactStubSnF is down</span></span>  
  
     <span data-ttu-id="8ee70-125">\#subsystem_name:User</span><span class="sxs-lookup"><span data-stu-id="8ee70-125">\#subsystem_name:User</span></span>  
  
     <span data-ttu-id="8ee70-126">\##subsystem_group:user</span><span class="sxs-lookup"><span data-stu-id="8ee70-126">\##subsystem_group:user</span></span>  
  
     <span data-ttu-id="8ee70-127">\##subsystem_dependency :</span><span class="sxs-lookup"><span data-stu-id="8ee70-127">\##subsystem_dependency:</span></span>  
  
     <span data-ttu-id="8ee70-128">\#subsystem_nature : critique</span><span class="sxs-lookup"><span data-stu-id="8ee70-128">\#subsystem_nature:critical</span></span>  
  
     <span data-ttu-id="8ee70-129">\#subsystem_start :</span><span class="sxs-lookup"><span data-stu-id="8ee70-129">\#subsystem_start:</span></span>  
  
     <span data-ttu-id="8ee70-130">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="8ee70-130">\#*END</span></span>  
  
     <span data-ttu-id="8ee70-131">\#subsystem_stop :</span><span class="sxs-lookup"><span data-stu-id="8ee70-131">\#subsystem_stop:</span></span>  
  
     <span data-ttu-id="8ee70-132">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="8ee70-132">\#*END</span></span>  
  
     <span data-ttu-id="8ee70-133">\#subsystem_status :</span><span class="sxs-lookup"><span data-stu-id="8ee70-133">\#subsystem_status:</span></span>  
  
     <span data-ttu-id="8ee70-134">\#* FIN</span><span class="sxs-lookup"><span data-stu-id="8ee70-134">\#*END</span></span>  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a><span data-ttu-id="8ee70-135">start_event:SNL001:Subsystem utilisateur est activé</span><span class="sxs-lookup"><span data-stu-id="8ee70-135">start_event:SNL001:subsystem User is up</span></span>  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a><span data-ttu-id="8ee70-136">stop_event:SNL002:Subsystem utilisateur est arrêté</span><span class="sxs-lookup"><span data-stu-id="8ee70-136">stop_event:SNL002:subsystem User is down</span></span>  
    
  
## <a name="complete-steps"></a><span data-ttu-id="8ee70-137">Étapes à suivre</span><span class="sxs-lookup"><span data-stu-id="8ee70-137">Complete steps</span></span>
 <span data-ttu-id="8ee70-138">[Scénario de transfert et de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8ee70-138">[FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="8ee70-139">[Étape 1 : Configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="8ee70-139">[Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="8ee70-140">[Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="8ee70-140">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="8ee70-141">Étape 4 : Tester et de scénario de bout en bout avant de FileAct</span><span class="sxs-lookup"><span data-stu-id="8ee70-141">Step 4: Test FileAct Store and Forward End-to-End Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)