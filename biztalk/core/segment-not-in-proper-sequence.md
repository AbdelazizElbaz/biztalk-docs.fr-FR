---
title: "Segment dans l’ordre correct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f0c0fdc-10d9-4b77-a80d-b2b8571e7665
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70b6147ea32bed7adf10640a3291ea9c75f71b1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-not-in-proper-sequence"></a><span data-ttu-id="7f565-102">Segment non placé dans l'ordre correct</span><span class="sxs-lookup"><span data-stu-id="7f565-102">Segment Not In Proper Sequence</span></span>
## <a name="details"></a><span data-ttu-id="7f565-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7f565-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f565-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7f565-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7f565-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7f565-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7f565-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7f565-106">Event ID</span></span>|-|  
|<span data-ttu-id="7f565-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7f565-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7f565-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7f565-108"> EDI</span></span>|  
|<span data-ttu-id="7f565-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7f565-109">Component</span></span>|<span data-ttu-id="7f565-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7f565-110">EDI Engine</span></span>|  
|<span data-ttu-id="7f565-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7f565-111">Symbolic Name</span></span>|<span data-ttu-id="7f565-112">X12SegmentNotInProperSequenceDescription</span><span class="sxs-lookup"><span data-stu-id="7f565-112">X12SegmentNotInProperSequenceDescription</span></span>|  
|<span data-ttu-id="7f565-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7f565-113">Message Text</span></span>|<span data-ttu-id="7f565-114">Segment non placé dans l'ordre correct</span><span class="sxs-lookup"><span data-stu-id="7f565-114">Segment Not In Proper Sequence</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7f565-115">Explication</span><span class="sxs-lookup"><span data-stu-id="7f565-115">Explanation</span></span>  
 <span data-ttu-id="7f565-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange X12 entrant, car un segment de l'échange se trouve en dehors de la séquence spécifiée par le schéma de document.</span><span class="sxs-lookup"><span data-stu-id="7f565-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a segment in the interchange is out of the sequence specified by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7f565-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7f565-117">User Action</span></span>  
 <span data-ttu-id="7f565-118">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de réorganiser les segments de l'échange de manière à ce qu'ils soient dans l'ordre spécifié par le schéma de document, puis de le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="7f565-118">To resolve this error, have the sender of the interchange rearrange the segments in the interchange so they are in the order specified by the document schema, and then resend the interchange.</span></span>