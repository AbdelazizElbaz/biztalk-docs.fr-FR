---
title: "Répète supérieur au nombre requis | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fec52b5b-e95f-479e-8922-dcf17dcefee7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cb8f9e324c9d09e09649719c98e3f684b0d81f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repeats-more-than-required"></a><span data-ttu-id="daae4-102">Nombre de répétitions supérieur au nombre requis</span><span class="sxs-lookup"><span data-stu-id="daae4-102">Repeats more than required</span></span>
## <a name="details"></a><span data-ttu-id="daae4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="daae4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="daae4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="daae4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="daae4-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="daae4-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="daae4-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="daae4-106">Event ID</span></span>|-|  
|<span data-ttu-id="daae4-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="daae4-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="daae4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="daae4-108"> EDI</span></span>|  
|<span data-ttu-id="daae4-109">Composant</span><span class="sxs-lookup"><span data-stu-id="daae4-109">Component</span></span>|<span data-ttu-id="daae4-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="daae4-110">EDI Engine</span></span>|  
|<span data-ttu-id="daae4-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="daae4-111">Symbolic Name</span></span>|<span data-ttu-id="daae4-112">X12FeRepeatsMoreThanRequiredDescription</span><span class="sxs-lookup"><span data-stu-id="daae4-112">X12FeRepeatsMoreThanRequiredDescription</span></span>|  
|<span data-ttu-id="daae4-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="daae4-113">Message Text</span></span>|<span data-ttu-id="daae4-114">Nombre de répétitions supérieur au nombre requis</span><span class="sxs-lookup"><span data-stu-id="daae4-114">Repeats more than required</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="daae4-115">Explication</span><span class="sxs-lookup"><span data-stu-id="daae4-115">Explanation</span></span>  
 <span data-ttu-id="daae4-116">Cet événement d'erreur/d'avertissement/d'informations indique que des segments d'un échange X12 se trouvant à l'intérieur ou à l'extérieur d'une boucle se sont répétés un nombre de fois supérieur au nombre requis par le schéma du document.</span><span class="sxs-lookup"><span data-stu-id="daae4-116">This Error/Warning/Information event indicates that segments in an X12 interchange that are either inside or outside of a loop repeated more times than required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="daae4-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="daae4-117">User Action</span></span>  
 <span data-ttu-id="daae4-118">Pour résoudre cette erreur, assurez-vous que le nombre de répétitions des segments se trouvant à l'intérieur ou à l'extérieur d'une boucle dans l'échange correspond au nombre spécifié dans le schéma, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="daae4-118">To resolve this error, make sure that the segments that are either inside or outside of a loop in the interchange repeat the numbers of times specified in the schema, and then resend the interchange.</span></span>