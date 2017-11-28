---
title: BizTalk Accelerator pour SWIFT Runtime | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime, architecture
- developing, components
- architecture, topology
- messages, message flow diagram
- runtime, components
- SWIFT runtime
- architecture, runtime architecture
- SWIFT network
- A4SWIFT, network
- topology
ms.assetid: c0f59760-7d7d-4b22-a7dc-54e563971d4a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f312a91d403d125fe6d245b92bf83da57d1031fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-accelerator-for-swift-runtime"></a><span data-ttu-id="c899e-102">BizTalk Accelerator pour SWIFT Runtime</span><span class="sxs-lookup"><span data-stu-id="c899e-102">BizTalk Accelerator for SWIFT Runtime</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="c899e-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit les fonctionnalités sous deux formes : matériaux de développement et les composants d’exécution.</span><span class="sxs-lookup"><span data-stu-id="c899e-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides functionality in two forms: development materials and runtime components.</span></span> <span data-ttu-id="c899e-104">Matériaux de développement inclure des schémas XSD, les règles de validation et les stratégies et les exemples de code.</span><span class="sxs-lookup"><span data-stu-id="c899e-104">Development materials include XSD schemas, validation rules and policies, and sample code.</span></span> <span data-ttu-id="c899e-105">Composants d’exécution incluent le désassembleur SWIFT personnalisé, l’assembleur SWIFT personnalisé, la réparation de Message et d’orchestration (MrsrRepair.odx) de la nouvelle soumission et l’orchestration de rapprochement de réponse de FIN (FrrMain.odx).</span><span class="sxs-lookup"><span data-stu-id="c899e-105">Runtime components include the custom SWIFT disassembler, the custom SWIFT assembler, the Message Repair and New Submission orchestration (MrsrRepair.odx), and the FIN Response Reconciliation orchestration (FrrMain.odx).</span></span> <span data-ttu-id="c899e-106">Pour plus d’informations sur Message Repair et New Submission, consultez [Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).</span><span class="sxs-lookup"><span data-stu-id="c899e-106">For more information on Message Repair and New Submission, see [Message Repair and New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).</span></span> <span data-ttu-id="c899e-107">Pour plus d’informations sur FRR, consultez [rapprochement de réponse de FIN](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md).</span><span class="sxs-lookup"><span data-stu-id="c899e-107">For more information on FRR, see [FIN Response Reconciliation](../../adapters-and-accelerators/accelerator-swift/fin-response-reconciliation.md).</span></span>  
  
 <span data-ttu-id="c899e-108">L’illustration suivante montre l’architecture de haut niveau de système de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c899e-108">The following figure shows the high-level system architecture of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-end-to-end.gif "A4SWIFTSystemArchitecture_End_to_End")  
  
 <span data-ttu-id="c899e-109">La figure suivante illustre le flux des messages entre A4SWIFT et une application back-end et comment A4SWIFT utilise [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaires dans MRSR de site pour Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="c899e-109">The following figure illustrates how messages flow between A4SWIFT and a back-end application, and how A4SWIFT uses [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms in MRSR site for Message Repair and New Submission.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswithbackendapplications.gif "A4SWIFTSystemArchitecture_InterfaceswithBackEndApplications")  
  
 <span data-ttu-id="c899e-110">La figure suivante illustre le flux des messages entre A4SWIFT et le réseau SWIFT.</span><span class="sxs-lookup"><span data-stu-id="c899e-110">The following figure illustrates how messages flow between A4SWIFT and the SWIFT Network.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swiftsystemarchitecture-interfaceswiththeswiftnetwork.gif "A4SWIFTSystemArchitecture_InterfaceswiththeSWIFTNetwork")  
  
 <span data-ttu-id="c899e-111">Vous pouvez définir tous les composants A4SWIFT comme des implémentations spécifiques à la verticale de [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] composants d’application.</span><span class="sxs-lookup"><span data-stu-id="c899e-111">You can define all A4SWIFT components as vertical-specific implementations of [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] application components.</span></span> <span data-ttu-id="c899e-112">Les accélérateurs BizTalk fournissent des fonctionnalités de développement et d’exécution pour accélérer le développement d’applications BizTalk verticales spécifiques sur de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c899e-112">BizTalk accelerators provide development and runtime functionality to accelerate vertical-specific BizTalk application development on top of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c899e-113">Par conséquent, tous les composants A4SWIFT (développement ou runtime) se conformer à et s’adaptent, le [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] architecture d’application.</span><span class="sxs-lookup"><span data-stu-id="c899e-113">Therefore, all A4SWIFT components (development or runtime) abide by, and fit into, the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] application architecture.</span></span> <span data-ttu-id="c899e-114">A4SWIFT installe les composants d’exécution dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime en tant que composants personnalisés.</span><span class="sxs-lookup"><span data-stu-id="c899e-114">A4SWIFT installs runtime components into the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime as custom components.</span></span> <span data-ttu-id="c899e-115">Après le développement des matériaux est compilés et déployés, A4SWIFT et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime les utiliser pour fournir des fonctionnalités de messagerie et d’automatisation de SWIFT.</span><span class="sxs-lookup"><span data-stu-id="c899e-115">After development materials are compiled and deployed, A4SWIFT and the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] runtime use them to provide SWIFT messaging and automation functionality.</span></span>  
  
 <span data-ttu-id="c899e-116">La figure suivante illustre la topologie de l’application de haut niveau pour [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c899e-116">The following figure shows the high-level application topology for [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/fsa-intro1.gif "FSA_Intro1")  
  
 <span data-ttu-id="c899e-117">Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] modèle d’application utilise la base de données MessageBox et le modèle d’éditeur-abonné qui régit le flux de messages vers et depuis la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="c899e-117">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application model uses the MessageBox database and the publisher-subscriber pattern that governs message flow into and out of the MessageBox database.</span></span> <span data-ttu-id="c899e-118">Pour plus d’informations sur la conception d’architecture et l’application BizTalk, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="c899e-118">For more information about BizTalk architecture and application design, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="c899e-119">Le modèle d’application A4SWIFT hérite le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] modèle d’application et lui ajoute des composants SWIFT spécifiques afin de faciliter les solutions SWIFT sur [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c899e-119">The A4SWIFT application model inherits the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application model and adds to it SWIFT-specific components to facilitate SWIFT-related solutions on [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c899e-120">La liste suivante décrit ces composants A4SWIFT spécifiques :</span><span class="sxs-lookup"><span data-stu-id="c899e-120">The following list describes these A4SWIFT-specific components:</span></span>  
  
-   <span data-ttu-id="c899e-121">**Composants d’exécution.**</span><span class="sxs-lookup"><span data-stu-id="c899e-121">**Runtime components.**</span></span> <span data-ttu-id="c899e-122">Désassembleur SWIFT dans le pipeline de réception, l’assembleur SWIFT dans le pipeline d’envoi, Message Repair et New Submission orchestration et d’orchestration de rapprochement de réponse de FIN.</span><span class="sxs-lookup"><span data-stu-id="c899e-122">SWIFT disassembler in the receive pipeline, SWIFT assembler in the send pipeline, Message Repair and New Submission orchestration, and FIN Response Reconciliation orchestration.</span></span>  
  
-   <span data-ttu-id="c899e-123">**Documents de développement.**</span><span class="sxs-lookup"><span data-stu-id="c899e-123">**Development materials.**</span></span> <span data-ttu-id="c899e-124">Schémas SWIFT, des règles, des orchestrations et des exemples de projets à inclure dans les solutions des clients et déployée sur le runtime pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c899e-124">SWIFT schemas, rules, orchestrations, and sample projects to be included in customer solutions and deployed onto the runtime for execution.</span></span>  
  
 <span data-ttu-id="c899e-125">Cette section décrit le runtime A4SWIFT en détail.</span><span class="sxs-lookup"><span data-stu-id="c899e-125">This section describes the A4SWIFT runtime in detail.</span></span>  
  
 <span data-ttu-id="c899e-126">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="c899e-126">This section contains:</span></span>  
  
-   [<span data-ttu-id="c899e-127">Désassembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="c899e-127">SWIFT Disassembler</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler.md)  
  
-   [<span data-ttu-id="c899e-128">Assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="c899e-128">SWIFT Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-assembler.md)  
  
-   [<span data-ttu-id="c899e-129">Envoi de Messages via emplacements de réception et des formulaires InfoPath</span><span class="sxs-lookup"><span data-stu-id="c899e-129">Submitting Messages Through Receive Locations and InfoPath Forms</span></span>](../../adapters-and-accelerators/accelerator-swift/submitting-messages-through-receive-locations-and-infopath-forms.md)  
  
-   [<span data-ttu-id="c899e-130">Moteur de Validation de message</span><span class="sxs-lookup"><span data-stu-id="c899e-130">Message Validation Engine</span></span>](../../adapters-and-accelerators/accelerator-swift/message-validation-engine.md)