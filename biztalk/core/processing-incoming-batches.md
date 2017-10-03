---
title: Traitement des lots entrants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98f47903-933a-4bde-b320-f7689c3d8366
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca3781d9b7c1ed2190a8334f272c04d304669ace
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-incoming-batches"></a><span data-ttu-id="4003d-102">Traitement des lots entrants</span><span class="sxs-lookup"><span data-stu-id="4003d-102">Processing Incoming Batches</span></span>
<span data-ttu-id="4003d-103">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un échange EDI par lot, il peut fractionner l'échange en documents informatisés qui le composent, en traitant chaque document séparément, ou il peut préserver l'échange, en traitant tous les documents informatisés comme un groupe.</span><span class="sxs-lookup"><span data-stu-id="4003d-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a batched EDI interchange, it can either split the interchange into its transaction sets, processing each one separately, or it can preserve the interchange, processing all transaction sets as a group.</span></span>  
  
 <span data-ttu-id="4003d-104">Vous déterminez le traitement par lots dans le **paramètres d’hôte Local** page des onglets d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour les contrats X12 et EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="4003d-104">You determine batch processing in the **Local Host Settings** page of the one-way agreement tabs in the **Agreement Properties** dialog box for both X12 and EDIFACT agreements.</span></span> <span data-ttu-id="4003d-105">Lorsque vous préservez l'échange, vous pouvez choisir de suspendre l'échange ou les documents informatisés en cas d'erreur.</span><span class="sxs-lookup"><span data-stu-id="4003d-105">When you preserve the interchange, you have the choice to suspend either the interchange or the transaction sets if an error occurs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4003d-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4003d-106">In This Section</span></span>  
  
-   [<span data-ttu-id="4003d-107">Fractionnement d’un échange EDI par lot</span><span class="sxs-lookup"><span data-stu-id="4003d-107">Splitting a Batched EDI Interchange</span></span>](../core/splitting-a-batched-edi-interchange.md)  
  
-   [<span data-ttu-id="4003d-108">Fractionnement de sous-documents HIPAA</span><span class="sxs-lookup"><span data-stu-id="4003d-108">Splitting HIPAA Subdocuments</span></span>](../core/splitting-hipaa-subdocuments.md)  
  
-   [<span data-ttu-id="4003d-109">En conservant un reçu par lot échange EDI</span><span class="sxs-lookup"><span data-stu-id="4003d-109">Preserving a Received Batched EDI Interchange</span></span>](../core/preserving-a-received-batched-edi-interchange.md)