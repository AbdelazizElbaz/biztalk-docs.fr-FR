---
title: "Nombre de répétitions inférieur à celui requis | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bebc13-0e70-4f73-99c0-fed917d79fba
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d88fe1868a91bce7208c0da557f20211cde23109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repeats-less-than-required"></a><span data-ttu-id="ce881-102">Nombre de répétitions inférieur au nombre requis</span><span class="sxs-lookup"><span data-stu-id="ce881-102">Repeats less than required</span></span>
## <a name="details"></a><span data-ttu-id="ce881-103">Détails</span><span class="sxs-lookup"><span data-stu-id="ce881-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce881-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="ce881-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ce881-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="ce881-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="ce881-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="ce881-106">Event ID</span></span>|-|  
|<span data-ttu-id="ce881-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="ce881-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ce881-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="ce881-108"> EDI</span></span>|  
|<span data-ttu-id="ce881-109">Composant</span><span class="sxs-lookup"><span data-stu-id="ce881-109">Component</span></span>|<span data-ttu-id="ce881-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="ce881-110">EDI Engine</span></span>|  
|<span data-ttu-id="ce881-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="ce881-111">Symbolic Name</span></span>|<span data-ttu-id="ce881-112">X12FeRepeatsLessThanRequiredDescription</span><span class="sxs-lookup"><span data-stu-id="ce881-112">X12FeRepeatsLessThanRequiredDescription</span></span>|  
|<span data-ttu-id="ce881-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="ce881-113">Message Text</span></span>|<span data-ttu-id="ce881-114">Nombre de répétitions inférieur au nombre requis</span><span class="sxs-lookup"><span data-stu-id="ce881-114">Repeats less than required</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ce881-115">Explication</span><span class="sxs-lookup"><span data-stu-id="ce881-115">Explanation</span></span>  
 <span data-ttu-id="ce881-116">Cet événement d'erreur/d'avertissement/d'informations indique que des segments d'un échange X12 se trouvant à l'intérieur ou à l'extérieur d'une boucle se sont répétés un nombre de fois inférieur au nombre requis par le schéma du document.</span><span class="sxs-lookup"><span data-stu-id="ce881-116">This Error/Warning/Information event indicates that segments in an X12 interchange that are either inside or outside of a loop repeated fewer times than required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ce881-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ce881-117">User Action</span></span>  
 <span data-ttu-id="ce881-118">Pour résoudre cette erreur, assurez-vous que le nombre de répétitions des segments se trouvant à l'intérieur ou à l'extérieur d'une boucle dans l'échange correspond au nombre spécifié dans le schéma, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="ce881-118">To resolve this error, make sure that the segments that are either inside or outside of a loop in the interchange repeat the numbers of times specified in the schema, and then resend the interchange.</span></span>