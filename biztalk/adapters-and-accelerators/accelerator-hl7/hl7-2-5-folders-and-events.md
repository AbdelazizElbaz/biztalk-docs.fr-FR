---
title: "HL7 2,5 dossiers et les événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 662ef767-5504-4ff5-8820-994e9cf674ea
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cdb229e2f8adf58397babf637a696bc2437ab626
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-25-folders-and-events"></a><span data-ttu-id="25995-102">HL7 2,5 dossiers et les événements</span><span class="sxs-lookup"><span data-stu-id="25995-102">HL7 2.5 Folders and Events</span></span>
<span data-ttu-id="25995-103">Le tableau suivant répertorie les sous-dossiers créés par l’Assistant Installation dans le dossier de la version 2.5 HL7 pour les messages encodés HL7.</span><span class="sxs-lookup"><span data-stu-id="25995-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.5 folder for HL7-encoded messages.</span></span> <span data-ttu-id="25995-104">Ces sous-dossiers contiennent les schémas utilisés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pour valider, analyser et sérialiser les événements répertoriés dans la colonne d’événements de cette table.</span><span class="sxs-lookup"><span data-stu-id="25995-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="25995-105">Les noms des sous-dossiers décrivent les types d’événements que prend en charge de ces schémas.</span><span class="sxs-lookup"><span data-stu-id="25995-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="25995-106">Sous-dossier</span><span class="sxs-lookup"><span data-stu-id="25995-106">Subfolder</span></span>|<span data-ttu-id="25995-107">Événements</span><span class="sxs-lookup"><span data-stu-id="25995-107">Events</span></span>|  
|---------------|------------|  
|<span data-ttu-id="25995-108">Administration patient</span><span class="sxs-lookup"><span data-stu-id="25995-108">Patient Administration</span></span>|<span data-ttu-id="25995-109">A01-A62, K21-K24, Q21-Q24</span><span class="sxs-lookup"><span data-stu-id="25995-109">A01-A62,K21-K24,Q21-Q24</span></span>|  
|<span data-ttu-id="25995-110">Gestion du personnel</span><span class="sxs-lookup"><span data-stu-id="25995-110">Personnel Management</span></span>|<span data-ttu-id="25995-111">B01-B08, K25, Q25</span><span class="sxs-lookup"><span data-stu-id="25995-111">B01-B08,K25,Q25</span></span>|  
|<span data-ttu-id="25995-112">Création de rapports d’observation</span><span class="sxs-lookup"><span data-stu-id="25995-112">Observation Reporting</span></span>|<span data-ttu-id="25995-113">C01-C12,P07-P09,R01-R02,R04,R21-R24,R30-R32</span><span class="sxs-lookup"><span data-stu-id="25995-113">C01-C12,P07-P09,R01-R02,R04,R21-R24,R30-R32</span></span>|  
|<span data-ttu-id="25995-114">Référence patient</span><span class="sxs-lookup"><span data-stu-id="25995-114">Patient Referral</span></span>|<span data-ttu-id="25995-115">I01-I15</span><span class="sxs-lookup"><span data-stu-id="25995-115">I01-I15</span></span>|  
|<span data-ttu-id="25995-116">Requête</span><span class="sxs-lookup"><span data-stu-id="25995-116">Query</span></span>|<span data-ttu-id="25995-117">J01, J02, K11, K13, K15, Q01-Q05, Q07-Q09, Q 11, Q 13, QUESTION Q15-17, R07-R09, Z75-Z99</span><span class="sxs-lookup"><span data-stu-id="25995-117">J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09,Q11,Q13,Q15-Q17, R07-R09,Z75-Z99</span></span>|  
|<span data-ttu-id="25995-118">Fichiers principaux</span><span class="sxs-lookup"><span data-stu-id="25995-118">Master Files</span></span>|<span data-ttu-id="25995-119">M01-M12</span><span class="sxs-lookup"><span data-stu-id="25995-119">M01-M12</span></span>|  
|<span data-ttu-id="25995-120">Entrée de commande</span><span class="sxs-lookup"><span data-stu-id="25995-120">Order Entry</span></span>|<span data-ttu-id="25995-121">O01-O36, Q06, Q26-Q31, RAR, RDR, RER, RGR, ROR, V01-V04, Z73-Z74</span><span class="sxs-lookup"><span data-stu-id="25995-121">O01-O36,Q06,Q26-Q31,RAR,RDR,RER,RGR,ROR,V01-V04,Z73-Z74</span></span>|  
|<span data-ttu-id="25995-122">Gestion des applications</span><span class="sxs-lookup"><span data-stu-id="25995-122">Application Management</span></span>|<span data-ttu-id="25995-123">N01-N02</span><span class="sxs-lookup"><span data-stu-id="25995-123">N01-N02</span></span>|  
|<span data-ttu-id="25995-124">Gestion financière</span><span class="sxs-lookup"><span data-stu-id="25995-124">Financial Management</span></span>|<span data-ttu-id="25995-125">P01-P03, P05-06, P12-P10</span><span class="sxs-lookup"><span data-stu-id="25995-125">P01-P03,P05-06,P10-P12</span></span>|  
|<span data-ttu-id="25995-126">Soins</span><span class="sxs-lookup"><span data-stu-id="25995-126">Patient Care</span></span>|<span data-ttu-id="25995-127">PC1-PC9, PCA-PCH, PCJ, PCL</span><span class="sxs-lookup"><span data-stu-id="25995-127">PC1-PC9,PCA-PCH,PCJ,PCL</span></span>|  
|<span data-ttu-id="25995-128">Planification</span><span class="sxs-lookup"><span data-stu-id="25995-128">Scheduling</span></span>|<span data-ttu-id="25995-129">S01-S26</span><span class="sxs-lookup"><span data-stu-id="25995-129">S01-S26</span></span>|  
|<span data-ttu-id="25995-130">Gestion des enregistrements/informations médicales</span><span class="sxs-lookup"><span data-stu-id="25995-130">Medical Records/Information Management</span></span>|<span data-ttu-id="25995-131">T01-T12</span><span class="sxs-lookup"><span data-stu-id="25995-131">T01-T12</span></span>|  
|<span data-ttu-id="25995-132">Automation de laboratoire</span><span class="sxs-lookup"><span data-stu-id="25995-132">Clinical Laboratory Automation</span></span>|<span data-ttu-id="25995-133">U01-U13</span><span class="sxs-lookup"><span data-stu-id="25995-133">U01-U13</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="25995-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25995-134">See Also</span></span>  
 <span data-ttu-id="25995-135">[Les événements et les sous-dossiers 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="25995-135">[HL7 2.X Subfolders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md) </span></span>  
 <span data-ttu-id="25995-136">[HL7 2.1 dossiers et événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="25995-136">[HL7 2.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="25995-137">[HL7 2.2 dossiers et les événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="25995-137">[HL7 2.2 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-2-folders-and-events.md) </span></span>  
 <span data-ttu-id="25995-138">[HL7 2.3 dossiers et les événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="25995-138">[HL7 2.3 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-folders-and-events.md) </span></span>  
 <span data-ttu-id="25995-139">[HL7 2.3.1 dossiers et des événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="25995-139">[HL7 2.3.1 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-3-1-folders-and-events.md) </span></span>  
 <span data-ttu-id="25995-140">[HL7 2,4 dossiers et les événements](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="25995-140">[HL7 2.4 Folders and Events](../../adapters-and-accelerators/accelerator-hl7/hl7-2-4-folders-and-events.md) </span></span>  
 [<span data-ttu-id="25995-141">HL7 2,5 dossiers et événements &#91; hl7 &#93;</span><span class="sxs-lookup"><span data-stu-id="25995-141">HL7 2.5 Folders and Events &#91;hl7&#93;</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-5-folders-and-events.md)