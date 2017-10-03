---
title: Terminateur de Segment non valide | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 508dac21-4731-439d-bf4a-a50858f1ffa0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47d5a79af0616baed6d401b4df7b68f5f596ef07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-segment-terminator"></a><span data-ttu-id="563fe-102">Terminaison de segment non valide</span><span class="sxs-lookup"><span data-stu-id="563fe-102">Invalid Segment Terminator</span></span>
## <a name="details"></a><span data-ttu-id="563fe-103">Détails</span><span class="sxs-lookup"><span data-stu-id="563fe-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="563fe-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="563fe-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="563fe-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="563fe-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="563fe-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="563fe-106">Event ID</span></span>|-|  
|<span data-ttu-id="563fe-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="563fe-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="563fe-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="563fe-108"> EDI</span></span>|  
|<span data-ttu-id="563fe-109">Composant</span><span class="sxs-lookup"><span data-stu-id="563fe-109">Component</span></span>|<span data-ttu-id="563fe-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="563fe-110">EDI Engine</span></span>|  
|<span data-ttu-id="563fe-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="563fe-111">Symbolic Name</span></span>|<span data-ttu-id="563fe-112">X12Ta1InvalidSegmentTerminatorDescription</span><span class="sxs-lookup"><span data-stu-id="563fe-112">X12Ta1InvalidSegmentTerminatorDescription</span></span>|  
|<span data-ttu-id="563fe-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="563fe-113">Message Text</span></span>|<span data-ttu-id="563fe-114">Terminaison de segment non valide</span><span class="sxs-lookup"><span data-stu-id="563fe-114">Invalid Segment Terminator</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="563fe-115">Explication</span><span class="sxs-lookup"><span data-stu-id="563fe-115">Explanation</span></span>  
 <span data-ttu-id="563fe-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car la valeur du terminateur de segment dans l'échange n'est pas limitée aux caractères présents dans le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="563fe-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the segment terminator in the interchange was not limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="563fe-117">Dans X12, la terminaison de segment est définie comme étant le dernier caractère du segment ISA.</span><span class="sxs-lookup"><span data-stu-id="563fe-117">In X12, the segment terminator is defined as the last character in the ISA segment.</span></span> <span data-ttu-id="563fe-118">Dans EDIFACT, la terminaison du segment est le champ UNA6.</span><span class="sxs-lookup"><span data-stu-id="563fe-118">In EDIFACT, the segment terminator is the UNA6 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="563fe-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="563fe-119">User Action</span></span>  
 <span data-ttu-id="563fe-120">Pour résoudre cette erreur, assurez-vous que la terminaison du segment (le dernier caractère du segment ISA dans l'échange X12 ou le champ UNA6 dans l'échange EDIFACT) est limitée aux caractères du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="563fe-120">To resolve this error, make sure that the segment terminator (the last character of the ISA segment in an X12 interchange or the UNA6 field in an EDIFACT interchange) is limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="563fe-121">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="563fe-121">Have the interchange resent.</span></span>