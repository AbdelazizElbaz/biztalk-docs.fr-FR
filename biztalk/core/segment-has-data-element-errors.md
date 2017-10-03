---
title: "Segment comporte des erreurs d’élément de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 469622e2-6500-4f55-ab53-f8d89ee0a978
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27c8c9e43bfe0a733a3e95b7812195a0b7f3990c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-has-data-element-errors"></a><span data-ttu-id="42e3b-102">Segment comporte des erreurs d’élément de données</span><span class="sxs-lookup"><span data-stu-id="42e3b-102">Segment has data element errors</span></span>
## <a name="details"></a><span data-ttu-id="42e3b-103">Détails</span><span class="sxs-lookup"><span data-stu-id="42e3b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="42e3b-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="42e3b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="42e3b-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="42e3b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="42e3b-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="42e3b-106">Event ID</span></span>|-|  
|<span data-ttu-id="42e3b-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="42e3b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="42e3b-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="42e3b-108"> EDI</span></span>|  
|<span data-ttu-id="42e3b-109">Composant</span><span class="sxs-lookup"><span data-stu-id="42e3b-109">Component</span></span>|<span data-ttu-id="42e3b-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="42e3b-110">EDI Engine</span></span>|  
|<span data-ttu-id="42e3b-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="42e3b-111">Symbolic Name</span></span>|<span data-ttu-id="42e3b-112">X12SegmentHasDataElementErrorsDescription</span><span class="sxs-lookup"><span data-stu-id="42e3b-112">X12SegmentHasDataElementErrorsDescription</span></span>|  
|<span data-ttu-id="42e3b-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="42e3b-113">Message Text</span></span>|<span data-ttu-id="42e3b-114">Un segment comporte des erreurs d'élément de données</span><span class="sxs-lookup"><span data-stu-id="42e3b-114">Segment Has Data Element Errors</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="42e3b-115">Explication</span><span class="sxs-lookup"><span data-stu-id="42e3b-115">Explanation</span></span>  
 <span data-ttu-id="42e3b-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car il contenait des segments incluant des éléments de données non conformes au schéma de document.</span><span class="sxs-lookup"><span data-stu-id="42e3b-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained segments that included data elements that did not conform to the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="42e3b-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="42e3b-117">User Action</span></span>  
 <span data-ttu-id="42e3b-118">Pour résoudre cette erreur, vérifiez que les éléments de données de l'échange sont conformes au schéma de document, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="42e3b-118">To resolve this error, make sure that the data elements in the interchange conform to the document schema, and then resend the interchange.</span></span>