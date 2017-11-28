---
title: "L'échange comportait une erreur structurelle. Une cause possible est le terminateur de segment non valide en raison d’une ligne de chariot manquante et- ou de saut de ligne des séparateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035e37d5-d4a8-49d0-8d75-3bcf2426cac7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e983e44b1284bf16e06dbfc90159afc0ed5608c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-a-likely-cause-is-invalid-segment-terminator-due-to-missing-carriage-line-and-or-line-feed-seperators"></a><span data-ttu-id="f1b02-103">L'échange comportait une erreur structurelle.</span><span class="sxs-lookup"><span data-stu-id="f1b02-103">The interchange had structural error.</span></span> <span data-ttu-id="f1b02-104">Une cause possible est le terminateur de segment non valide en raison d’une ligne de chariot manquante et- ou de saut de ligne des séparateurs</span><span class="sxs-lookup"><span data-stu-id="f1b02-104">A likely cause is invalid segment terminator due to missing Carriage Line and-or Line Feed seperators</span></span>
## <a name="details"></a><span data-ttu-id="f1b02-105">Détails</span><span class="sxs-lookup"><span data-stu-id="f1b02-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1b02-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f1b02-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f1b02-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f1b02-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f1b02-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f1b02-108">Event ID</span></span>|-|  
|<span data-ttu-id="f1b02-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f1b02-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f1b02-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="f1b02-110"> EDI</span></span>|  
|<span data-ttu-id="f1b02-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f1b02-111">Component</span></span>|<span data-ttu-id="f1b02-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f1b02-112">EDI Engine</span></span>|  
|<span data-ttu-id="f1b02-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f1b02-113">Symbolic Name</span></span>|<span data-ttu-id="f1b02-114">EfactInterchangeStructuralErrorAfterUnb</span><span class="sxs-lookup"><span data-stu-id="f1b02-114">EfactInterchangeStructuralErrorAfterUnb</span></span>|  
|<span data-ttu-id="f1b02-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f1b02-115">Message Text</span></span>|<span data-ttu-id="f1b02-116">L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle.</span><span class="sxs-lookup"><span data-stu-id="f1b02-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="f1b02-117">Une cause possible est le terminateur de segment non valide due à l’absence de séparateurs de retour chariot et/ou de saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="f1b02-117">A likely cause is invalid segment terminator due to missing Carriage Line and/or Line Feed seperators.</span></span> <span data-ttu-id="f1b02-118">La partie située après que l’erreur a été interrompue, reportez-vous à la file d’attente pour plus d’informations</span><span class="sxs-lookup"><span data-stu-id="f1b02-118">The part after the error is being suspended, refer to Suspended Queue for details</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f1b02-119">Explication</span><span class="sxs-lookup"><span data-stu-id="f1b02-119">Explanation</span></span>  
 <span data-ttu-id="f1b02-120">Cet événement de type erreur/avertissement/information indique que le pipeline de réception, le pipeline d'envoi ou l'orchestration du traitement par lot n'ont pas pu traiter l'échange EDIFACT, car un segment de ce dernier ne disposait pas du terminateur de segment requis.</span><span class="sxs-lookup"><span data-stu-id="f1b02-120">This Error/Warning/Information event indicates that the receive pipeline, send pipeline, or batching orchestration could not process the EDIFACT interchange, because a segment in the interchange did not have the required segment terminator.</span></span> <span data-ttu-id="f1b02-121">Pour un échange entrant, les séparateurs sont identifiés dans le segment UNA ou, si ce dernier n'est pas présent, dans la propriété de pipeline EfactDelimiters.</span><span class="sxs-lookup"><span data-stu-id="f1b02-121">For an incoming interchange, the separators are identified in the UNA Segment, or if the UNA segment is not present, the EfactDelimiters pipeline property.</span></span> <span data-ttu-id="f1b02-122">Pour un échange sortant, les séparateurs sont identifiés sur la page Définition du segment UNA de la boîte de dialogue Propriétés EDI.</span><span class="sxs-lookup"><span data-stu-id="f1b02-122">For an outgoing interchange, the separators are identified in the UNA Segment Definition page of the EDI Properties dialog box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f1b02-123">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f1b02-123">User Action</span></span>  
 <span data-ttu-id="f1b02-124">Pour résoudre cette erreur, assurez-vous que tous les segments de l'échange disposent du terminateur de segment requis, puis procédez à un nouvel envoi de l'échange.</span><span class="sxs-lookup"><span data-stu-id="f1b02-124">To resolve this error, ensure that all segments in the interchange have the required segment terminator, and then have the interchange resent.</span></span>