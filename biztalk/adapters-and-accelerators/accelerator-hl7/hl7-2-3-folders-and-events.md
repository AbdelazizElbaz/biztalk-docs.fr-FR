---
title: "HL7 2.3 dossiers et les événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HL7, default sub-folders
- events, 2.X versions
- HL7, events
ms.assetid: 555a8620-a714-4102-80ba-1424d60387bf
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a396fca582defb8601bdda23280f92d0acbd90be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-23-folders-and-events"></a><span data-ttu-id="b53fb-102">HL7 2.3 dossiers et les événements</span><span class="sxs-lookup"><span data-stu-id="b53fb-102">HL7 2.3 Folders and Events</span></span>
<span data-ttu-id="b53fb-103">Le tableau suivant répertorie les sous-dossiers créés par l’Assistant Installation dans le dossier de la version 2.3 HL7 pour les messages encodés HL7.</span><span class="sxs-lookup"><span data-stu-id="b53fb-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.3 folder for HL7-encoded messages.</span></span> <span data-ttu-id="b53fb-104">Ces sous-dossiers contiennent les schémas utilisés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pour valider, analyser et sérialiser les événements répertoriés dans la colonne d’événements de cette table.</span><span class="sxs-lookup"><span data-stu-id="b53fb-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="b53fb-105">Les noms des sous-dossiers décrivent les types d’événements que prend en charge de ces schémas.</span><span class="sxs-lookup"><span data-stu-id="b53fb-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="b53fb-106">Sous-dossier</span><span class="sxs-lookup"><span data-stu-id="b53fb-106">Subfolder</span></span>|<span data-ttu-id="b53fb-107">Événements</span><span class="sxs-lookup"><span data-stu-id="b53fb-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="b53fb-108">Administration patient</span><span class="sxs-lookup"><span data-stu-id="b53fb-108">Patient Administration</span></span>|<span data-ttu-id="b53fb-109">A01-A51</span><span class="sxs-lookup"><span data-stu-id="b53fb-109">A01-A51</span></span>|  
|<span data-ttu-id="b53fb-110">Création de rapports d’observation</span><span class="sxs-lookup"><span data-stu-id="b53fb-110">Observation Reporting</span></span>|<span data-ttu-id="b53fb-111">C01-C12, P07-P09, R01-R06, W01-W02</span><span class="sxs-lookup"><span data-stu-id="b53fb-111">C01-C12, P07-P09, R01-R06, W01-W02</span></span>|  
|<span data-ttu-id="b53fb-112">Référence patient</span><span class="sxs-lookup"><span data-stu-id="b53fb-112">Patient Referral</span></span>|<span data-ttu-id="b53fb-113">I01-I15</span><span class="sxs-lookup"><span data-stu-id="b53fb-113">I01-I15</span></span>|  
|<span data-ttu-id="b53fb-114">Fichier principal</span><span class="sxs-lookup"><span data-stu-id="b53fb-114">Master File</span></span>|<span data-ttu-id="b53fb-115">M01-M11</span><span class="sxs-lookup"><span data-stu-id="b53fb-115">M01-M11</span></span>|  
|<span data-ttu-id="b53fb-116">Entrée de commande</span><span class="sxs-lookup"><span data-stu-id="b53fb-116">Order Entry</span></span>|<span data-ttu-id="b53fb-117">O01-O02, Q06, RAR, RDR, RER, RGR, ROR, V01-V04</span><span class="sxs-lookup"><span data-stu-id="b53fb-117">O01-O02,Q06, RAR,RDR,RER,RGR,ROR, V01-V04</span></span>|  
|<span data-ttu-id="b53fb-118">Gestion financière</span><span class="sxs-lookup"><span data-stu-id="b53fb-118">Financial Management</span></span>|<span data-ttu-id="b53fb-119">P01-P06</span><span class="sxs-lookup"><span data-stu-id="b53fb-119">P01-P06</span></span>|  
|<span data-ttu-id="b53fb-120">Soins</span><span class="sxs-lookup"><span data-stu-id="b53fb-120">Patient Care</span></span>|<span data-ttu-id="b53fb-121">EN-TÊTE PRÉCOMPILÉ PC1, PCJ-PCL</span><span class="sxs-lookup"><span data-stu-id="b53fb-121">PC1-PCH, PCJ-PCL</span></span>|  
|<span data-ttu-id="b53fb-122">Requête</span><span class="sxs-lookup"><span data-stu-id="b53fb-122">Query</span></span>|<span data-ttu-id="b53fb-123">CNQ, Q01-Q03, Q05</span><span class="sxs-lookup"><span data-stu-id="b53fb-123">CNQ, Q01-Q03, Q05</span></span>|  
|<span data-ttu-id="b53fb-124">Planification</span><span class="sxs-lookup"><span data-stu-id="b53fb-124">Scheduling</span></span>|<span data-ttu-id="b53fb-125">S01-S26</span><span class="sxs-lookup"><span data-stu-id="b53fb-125">S01-S26</span></span>|  
|<span data-ttu-id="b53fb-126">Gestion des informations et des dossiers médicaux</span><span class="sxs-lookup"><span data-stu-id="b53fb-126">Medical Records and Information Management</span></span>|<span data-ttu-id="b53fb-127">T01-T12</span><span class="sxs-lookup"><span data-stu-id="b53fb-127">T01-T12</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b53fb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b53fb-128">See Also</span></span>  
 <span data-ttu-id="b53fb-129">[Les événements et les sous-dossiers 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="b53fb-129">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="b53fb-130">[HL7 2.1 dossiers et événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="b53fb-130">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="b53fb-131">[HL7 2.2 dossiers et les événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="b53fb-131">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="b53fb-132">[HL7 2.3.1 dossiers et des événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="b53fb-132">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="b53fb-133">[HL7 2,4 dossiers et les événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="b53fb-133">[HL7 2.4 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span></span>  
 [<span data-ttu-id="b53fb-134">HL7 2,5 dossiers et les événements</span><span class="sxs-lookup"><span data-stu-id="b53fb-134">HL7 2.5 Folders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)