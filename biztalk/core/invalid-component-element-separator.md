---
title: "Séparateur d’éléments de composant non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738a1107-86e6-4475-a61d-ed1d9ab7e5d2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4abf047a61dc8b8f2eb89e436594e47e6f4cb067
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-component-element-separator"></a><span data-ttu-id="59dc7-102">Séparateur d'éléments composites non valide</span><span class="sxs-lookup"><span data-stu-id="59dc7-102">Invalid Component Element Separator</span></span>
## <a name="details"></a><span data-ttu-id="59dc7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="59dc7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="59dc7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="59dc7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="59dc7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="59dc7-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="59dc7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="59dc7-106">Event ID</span></span>|-|  
|<span data-ttu-id="59dc7-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="59dc7-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="59dc7-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="59dc7-108"> EDI</span></span>|  
|<span data-ttu-id="59dc7-109">Composant</span><span class="sxs-lookup"><span data-stu-id="59dc7-109">Component</span></span>|<span data-ttu-id="59dc7-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="59dc7-110">EDI Engine</span></span>|  
|<span data-ttu-id="59dc7-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="59dc7-111">Symbolic Name</span></span>|<span data-ttu-id="59dc7-112">X12Ta1InvalidComponentElementSeparatorDescription\\</span><span class="sxs-lookup"><span data-stu-id="59dc7-112">X12Ta1InvalidComponentElementSeparatorDescription\\</span></span>|  
|<span data-ttu-id="59dc7-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="59dc7-113">Message Text</span></span>|<span data-ttu-id="59dc7-114">Séparateur d'éléments composites non valide</span><span class="sxs-lookup"><span data-stu-id="59dc7-114">Invalid Component Element Separator</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="59dc7-115">Explication</span><span class="sxs-lookup"><span data-stu-id="59dc7-115">Explanation</span></span>  
 <span data-ttu-id="59dc7-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car la valeur du séparateur de composants dans l'échange n'est pas limitée aux caractères présents dans le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="59dc7-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the component separator in the interchange was not limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="59dc7-117">Dans X12, le terminateur de segment correspond au champ ISA16.</span><span class="sxs-lookup"><span data-stu-id="59dc7-117">In X12, the segment terminator is the ISA16 field.</span></span> <span data-ttu-id="59dc7-118">Dans EDIFACT, le terminateur de segment correspond au champ UNA1.</span><span class="sxs-lookup"><span data-stu-id="59dc7-118">In EDIFACT, the segment terminator is the UNA1 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="59dc7-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="59dc7-119">User Action</span></span>  
 <span data-ttu-id="59dc7-120">Pour résoudre cette erreur, assurez-vous que le terminateur de segment (le champ ISA16 pour un échange X12 et le champ UNA1 pour un échange EDIFACT) est limité aux caractères du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="59dc7-120">To resolve this error, make sure that the segment terminator (the ISA16 field in an X12 interchange or the UNA1 field in an EDIFACT interchange) is limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="59dc7-121">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="59dc7-121">Have the interchange resent.</span></span>