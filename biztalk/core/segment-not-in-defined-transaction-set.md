---
title: "Pas de Transaction définie par l’ensemble du segment | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 914e333f-96e4-4094-880d-51a5f25915c3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2f0b330110ef08196681e54e543173c3f2bd0f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-not-in-defined-transaction-set"></a><span data-ttu-id="7e43d-102">Segment non défini dans le document informatisé</span><span class="sxs-lookup"><span data-stu-id="7e43d-102">Segment Not In Defined Transaction set</span></span>
## <a name="details"></a><span data-ttu-id="7e43d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7e43d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7e43d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7e43d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7e43d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7e43d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7e43d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7e43d-106">Event ID</span></span>|-|  
|<span data-ttu-id="7e43d-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7e43d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7e43d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7e43d-108"> EDI</span></span>|  
|<span data-ttu-id="7e43d-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7e43d-109">Component</span></span>|<span data-ttu-id="7e43d-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7e43d-110">EDI Engine</span></span>|  
|<span data-ttu-id="7e43d-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7e43d-111">Symbolic Name</span></span>|<span data-ttu-id="7e43d-112">X12SegmentNotInDefinedTSDescription</span><span class="sxs-lookup"><span data-stu-id="7e43d-112">X12SegmentNotInDefinedTSDescription</span></span>|  
|<span data-ttu-id="7e43d-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7e43d-113">Message Text</span></span>|<span data-ttu-id="7e43d-114">Segment non défini dans le document informatisé</span><span class="sxs-lookup"><span data-stu-id="7e43d-114">Segment Not In Defined Transaction set</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7e43d-115">Explication</span><span class="sxs-lookup"><span data-stu-id="7e43d-115">Explanation</span></span>  
 <span data-ttu-id="7e43d-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant car un document informatisé faisant partie de cet échange ne contient pas un segment requis par le schéma de document.</span><span class="sxs-lookup"><span data-stu-id="7e43d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a transaction set in that interchange does not contain a segment required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7e43d-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7e43d-117">User Action</span></span>  
 <span data-ttu-id="7e43d-118">Pour résoudre cette erreur, demandez à l'expéditeur d'ajouter le segment requis au document informatisé dans l'échange, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="7e43d-118">To resolve this error, have the sender of the interchange add the required segment to the transaction set in the interchange, and then resend the interchange.</span></span>