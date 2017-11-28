---
title: "Le document informatisé Edifact comportait un nombre incompatible dans UNT01 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2859274-78e8-4e16-92b7-c143da6da421
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 180abe338441917afa6691400a02a42e88026052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-edifact-transaction-set-had-a-mismatched-count-in-unt01"></a><span data-ttu-id="22629-102">Le document informatisé EDIFACT comportait un nombre incompatible dans UNT01</span><span class="sxs-lookup"><span data-stu-id="22629-102">The Edifact Transaction set had a mismatched count in UNT01</span></span>
## <a name="details"></a><span data-ttu-id="22629-103">Détails</span><span class="sxs-lookup"><span data-stu-id="22629-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22629-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="22629-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="22629-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="22629-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="22629-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="22629-106">Event ID</span></span>|-|  
|<span data-ttu-id="22629-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="22629-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="22629-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="22629-108"> EDI</span></span>|  
|<span data-ttu-id="22629-109">Composant</span><span class="sxs-lookup"><span data-stu-id="22629-109">Component</span></span>|<span data-ttu-id="22629-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="22629-110">EDI Engine</span></span>|  
|<span data-ttu-id="22629-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="22629-111">Symbolic Name</span></span>|<span data-ttu-id="22629-112">EfactUnhUntCountMismatch</span><span class="sxs-lookup"><span data-stu-id="22629-112">EfactUnhUntCountMismatch</span></span>|  
|<span data-ttu-id="22629-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="22629-113">Message Text</span></span>|<span data-ttu-id="22629-114">Le document informatisé EDIFACT comportait un nombre incompatible dans UNT01.</span><span class="sxs-lookup"><span data-stu-id="22629-114">The Edifact Transaction set had a mismatched count in UNT01.</span></span> <span data-ttu-id="22629-115">UNT01 était {0}, alors qu’elle aurait dû être {{1}.</span><span class="sxs-lookup"><span data-stu-id="22629-115">UNT01 was {0}, whereas it should have been {1}.</span></span> <span data-ttu-id="22629-116">Il a été corrigé.</span><span class="sxs-lookup"><span data-stu-id="22629-116">It has been corrected.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22629-117">Explication</span><span class="sxs-lookup"><span data-stu-id="22629-117">Explanation</span></span>  
 <span data-ttu-id="22629-118">Cet avertissement indique que le champ UNT01, qui représente le nombre de segments, ne correspond pas au nombre de segments du document informatisé.</span><span class="sxs-lookup"><span data-stu-id="22629-118">This Warning indicates that the UNT01 field, which is the segment count, did not match the number of segments in the transaction set.</span></span> <span data-ttu-id="22629-119">La valeur de UNT01 a été soit modifiée soit corrompue ou des segments ont été ajoutés ou supprimés après le calcul de ce nombre.</span><span class="sxs-lookup"><span data-stu-id="22629-119">Either the value of UNT01 was changed or corrupted, or segments were added or deleted after the count was determined.</span></span> <span data-ttu-id="22629-120">Le pipeline d'envoi a rétabli le champ UNT01 sur le nombre de segments correct, puis il a renvoyé l'échange.</span><span class="sxs-lookup"><span data-stu-id="22629-120">The send pipeline reset the UNT01 field to the correct number of segments, and then sent the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22629-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="22629-121">User Action</span></span>  
 <span data-ttu-id="22629-122">Aucune action utilisateur n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="22629-122">No user action is necessary.</span></span>