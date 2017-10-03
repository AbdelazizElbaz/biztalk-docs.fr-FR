---
title: "Un segment dépasse la Description d’utilisation maximale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e1704a-5d49-4549-af50-d1a89a1e70f0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 71f5e5a0ae590be850a4560324814c756d51e9fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-exceeds-maximum-use-description"></a><span data-ttu-id="21469-102">Un segment dépasse la description d'utilisation maximale</span><span class="sxs-lookup"><span data-stu-id="21469-102">Segment Exceeds Maximum Use Description</span></span>
## <a name="details"></a><span data-ttu-id="21469-103">Détails</span><span class="sxs-lookup"><span data-stu-id="21469-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21469-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="21469-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="21469-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="21469-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="21469-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="21469-106">Event ID</span></span>|-|  
|<span data-ttu-id="21469-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="21469-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="21469-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="21469-108"> EDI</span></span>|  
|<span data-ttu-id="21469-109">Composant</span><span class="sxs-lookup"><span data-stu-id="21469-109">Component</span></span>|<span data-ttu-id="21469-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="21469-110">EDI Engine</span></span>|  
|<span data-ttu-id="21469-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="21469-111">Symbolic Name</span></span>|<span data-ttu-id="21469-112">X12SegmentExceedsMaximumUseDescription</span><span class="sxs-lookup"><span data-stu-id="21469-112">X12SegmentExceedsMaximumUseDescription</span></span>|  
|<span data-ttu-id="21469-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="21469-113">Message Text</span></span>|<span data-ttu-id="21469-114">Un segment dépasse la description d'utilisation maximale</span><span class="sxs-lookup"><span data-stu-id="21469-114">Segment Exceeds Maximum Use Description</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21469-115">Explication</span><span class="sxs-lookup"><span data-stu-id="21469-115">Explanation</span></span>  
 <span data-ttu-id="21469-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant car celui-ci contient un nombre d'instances de segment supérieur au nombre autorisé par le schéma.</span><span class="sxs-lookup"><span data-stu-id="21469-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained more instances of a segment than allowed by the schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21469-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="21469-117">User Action</span></span>  
 <span data-ttu-id="21469-118">Pour résoudre cette erreur, assurez-vous que l'échange n'inclut que le nombre maximum autorisé de segments, puis renvoyez-le.</span><span class="sxs-lookup"><span data-stu-id="21469-118">To resolve this error, make sure that the interchange does not have more than the maximum allowed number of segments, and then resend the interchange.</span></span>