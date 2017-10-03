---
title: Programmation Guide1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, programming guide
- programming guide
ms.assetid: fb2d5e3b-1907-49c4-806d-a2604c702322
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb77912db0bfb3eaf5cc4ad22c4737d443d90998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="programming-guide"></a><span data-ttu-id="ab2eb-102">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="ab2eb-102">Programming Guide</span></span>
<span data-ttu-id="ab2eb-103">Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Guide de programmation explique les concepts et les procédures pour les développeurs écrivant du code avec BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="ab2eb-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Programming Guide explains concepts and procedures for developers writing code with BTAHL7.</span></span> <span data-ttu-id="ab2eb-104">Utilisez ce guide avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] documentation.</span><span class="sxs-lookup"><span data-stu-id="ab2eb-104">Use this guide in conjunction with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab2eb-105">Avant de lire ce guide, vous devez être familiarisé avec [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] développement, [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], et [Découvrez l’accélérateur HL7 et les outils BizTalk disponibles](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span><span class="sxs-lookup"><span data-stu-id="ab2eb-105">Before reading this guide, you should be familiar with [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] development, [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], and [Learn the HL7 accelerator and the BizTalk tools available](../../adapters-and-accelerators/accelerator-hl7/learn-the-hl7-accelerator-and-the-biztalk-tools-available.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ab2eb-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ab2eb-106">In This Section</span></span>  
  
-   [<span data-ttu-id="ab2eb-107">Le traitement des Messages HL7</span><span class="sxs-lookup"><span data-stu-id="ab2eb-107">Processing HL7 Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)  
  
-   [<span data-ttu-id="ab2eb-108">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="ab2eb-108">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)  
  
-   [<span data-ttu-id="ab2eb-109">Utilisation de schémas XML de 2 HL7</span><span class="sxs-lookup"><span data-stu-id="ab2eb-109">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)  
  
-   [<span data-ttu-id="ab2eb-110">Le traitement des Messages encodés en MLLP</span><span class="sxs-lookup"><span data-stu-id="ab2eb-110">Processing MLLP-encoded Messages</span></span>](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)  
  
-   [<span data-ttu-id="ab2eb-111">Création et le traitement des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="ab2eb-111">Creating and Processing Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)  
  
-   [<span data-ttu-id="ab2eb-112">Utilisation de la Validation de données dynamiques</span><span class="sxs-lookup"><span data-stu-id="ab2eb-112">Using Dynamic Data Validation</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-dynamic-data-validation.md)  
  
-   [<span data-ttu-id="ab2eb-113">Création d’un récepteur WMI pour l’audit et la journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="ab2eb-113">Creating a WMI Sink for Auditing and Logging Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-a-wmi-sink-for-auditing-and-logging-events.md)  
  
-   [<span data-ttu-id="ab2eb-114">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="ab2eb-114">Additional Resources</span></span>](../../adapters-and-accelerators/accelerator-hl7/additional-resources.md)