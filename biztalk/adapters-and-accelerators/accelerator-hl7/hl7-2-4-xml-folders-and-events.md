---
title: "Dossiers XML 2,4 HL7 et événements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, HL7 2.XML versions
- HL7, default sub-folders
- HL7, events
ms.assetid: bc6c5d75-66c7-4269-bfb9-59cab5999a73
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10c9445a1d5c7978b526fd0347dc6defa3214640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-24-xml-folders-and-events"></a><span data-ttu-id="4613a-102">Les événements et les dossiers XML 2,4 HL7</span><span class="sxs-lookup"><span data-stu-id="4613a-102">HL7 2.4 XML Folders and Events</span></span>
<span data-ttu-id="4613a-103">Le tableau suivant répertorie les sous-dossiers créés par l’Assistant Installation dans le dossier de la version 2.4 HL7 pour les messages encodés en XML.</span><span class="sxs-lookup"><span data-stu-id="4613a-103">The following table lists the subfolders created by the setup wizard within the HL7 version 2.4 folder for XML-encoded messages.</span></span> <span data-ttu-id="4613a-104">Ces sous-dossiers contiennent les schémas utilisés par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) pour valider, analyser et sérialiser les événements répertoriés dans la colonne d’événements de cette table.</span><span class="sxs-lookup"><span data-stu-id="4613a-104">These subfolders contain the schemas used by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) to validate, parse, and serialize the events listed in the Events column of this table.</span></span> <span data-ttu-id="4613a-105">Les noms des sous-dossiers décrivent les types d’événements que prend en charge de ces schémas.</span><span class="sxs-lookup"><span data-stu-id="4613a-105">The subfolder names describe the types of events these schemas support.</span></span>  
  
|<span data-ttu-id="4613a-106">Sous-dossier</span><span class="sxs-lookup"><span data-stu-id="4613a-106">Sub folder</span></span>|<span data-ttu-id="4613a-107">Événements</span><span class="sxs-lookup"><span data-stu-id="4613a-107">Events</span></span>|  
|----------------|------------|  
|<span data-ttu-id="4613a-108">Administration patient</span><span class="sxs-lookup"><span data-stu-id="4613a-108">Patient Administration</span></span>|<span data-ttu-id="4613a-109">A01-A62, K21, K22, K23, K24, Q21-Q24</span><span class="sxs-lookup"><span data-stu-id="4613a-109">A01-A62, K21,K22,K23,K24,Q21-Q24</span></span>|  
|<span data-ttu-id="4613a-110">Entrée de commande</span><span class="sxs-lookup"><span data-stu-id="4613a-110">Order Entry</span></span>|<span data-ttu-id="4613a-111">O01-O22, Q06, Q26-Q30, RAR, RDR, RER, RGR, ROR, V01-V04, Z73, Z74</span><span class="sxs-lookup"><span data-stu-id="4613a-111">O01-O22, Q06, Q26-Q30, RAR,RDR,RER,RGR,ROR, V01-V04, Z73, Z74</span></span>|  
|<span data-ttu-id="4613a-112">Requête</span><span class="sxs-lookup"><span data-stu-id="4613a-112">Query</span></span>|<span data-ttu-id="4613a-113">J01, J02, K11, K13, K15, Q01-Q05, Q07-Q09, Q 11, Q 13, QUESTION Q15-17, R07-R09, Z75-Z99</span><span class="sxs-lookup"><span data-stu-id="4613a-113">J01,J02,K11,K13,K15, Q01-Q05, Q07-Q09, Q11,Q13,Q15-Q17, R07-R09, Z75-Z99</span></span>|  
|<span data-ttu-id="4613a-114">Gestion financière</span><span class="sxs-lookup"><span data-stu-id="4613a-114">Financial Management</span></span>|<span data-ttu-id="4613a-115">P01 ~ P06, P10</span><span class="sxs-lookup"><span data-stu-id="4613a-115">P01~P06, P10</span></span>|  
|<span data-ttu-id="4613a-116">Création de rapports d’observation</span><span class="sxs-lookup"><span data-stu-id="4613a-116">Observation Reporting</span></span>|<span data-ttu-id="4613a-117">C01-C12, P07, P08, P09, R01, R02, R04, R21, W01, W02</span><span class="sxs-lookup"><span data-stu-id="4613a-117">C01-C12, P07,P08,P09, R01,R02,R04, R21, W01, W02</span></span>|  
|<span data-ttu-id="4613a-118">Fichiers principaux</span><span class="sxs-lookup"><span data-stu-id="4613a-118">Master Files</span></span>|<span data-ttu-id="4613a-119">M01-M12, L’AUTHENTIFICATION MULTIFACTEUR</span><span class="sxs-lookup"><span data-stu-id="4613a-119">M01-M12, MFA</span></span>|  
|<span data-ttu-id="4613a-120">Gestion des enregistrements/informations médicales</span><span class="sxs-lookup"><span data-stu-id="4613a-120">Medical Records/Information Management</span></span>|<span data-ttu-id="4613a-121">T01-T12</span><span class="sxs-lookup"><span data-stu-id="4613a-121">T01-T12</span></span>|  
|<span data-ttu-id="4613a-122">Planification</span><span class="sxs-lookup"><span data-stu-id="4613a-122">Scheduling</span></span>|<span data-ttu-id="4613a-123">S01-S26</span><span class="sxs-lookup"><span data-stu-id="4613a-123">S01-S26</span></span>|  
|<span data-ttu-id="4613a-124">Référence patient</span><span class="sxs-lookup"><span data-stu-id="4613a-124">Patient Referral</span></span>|<span data-ttu-id="4613a-125">I01-I15</span><span class="sxs-lookup"><span data-stu-id="4613a-125">I01-I15</span></span>|  
|<span data-ttu-id="4613a-126">Soins</span><span class="sxs-lookup"><span data-stu-id="4613a-126">Patient Care</span></span>|<span data-ttu-id="4613a-127">EN-TÊTE PRÉCOMPILÉ PC1, PCJ, PCK, PCL</span><span class="sxs-lookup"><span data-stu-id="4613a-127">PC1-PCH, PCJ,PCK,PCL</span></span>|  
|<span data-ttu-id="4613a-128">Automation de laboratoire</span><span class="sxs-lookup"><span data-stu-id="4613a-128">Clinical Laboratory Automation</span></span>|<span data-ttu-id="4613a-129">U01-U13</span><span class="sxs-lookup"><span data-stu-id="4613a-129">U01-U13</span></span>|  
|<span data-ttu-id="4613a-130">Gestion des applications</span><span class="sxs-lookup"><span data-stu-id="4613a-130">Application Management</span></span>|<span data-ttu-id="4613a-131">N01, N02</span><span class="sxs-lookup"><span data-stu-id="4613a-131">N01,N02</span></span>|  
|<span data-ttu-id="4613a-132">Gestion du personnel</span><span class="sxs-lookup"><span data-stu-id="4613a-132">Personnel Management</span></span>|<span data-ttu-id="4613a-133">B01-B06, K25, Q25</span><span class="sxs-lookup"><span data-stu-id="4613a-133">B01-B06, K25,Q25</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4613a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4613a-134">See Also</span></span>  
 [<span data-ttu-id="4613a-135">Utilisation de schémas XML de 2 HL7</span><span class="sxs-lookup"><span data-stu-id="4613a-135">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)