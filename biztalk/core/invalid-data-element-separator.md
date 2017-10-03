---
title: "Séparateur d’éléments de données non valides | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c50a8b-274f-4f4a-9826-4f6f8123e9d1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d83b8ce3099ebb940507d391881cfd92cde5034d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-data-element-separator"></a><span data-ttu-id="f1edc-102">Séparateur d'éléments de données non valide</span><span class="sxs-lookup"><span data-stu-id="f1edc-102">Invalid Data Element Separator</span></span>
## <a name="details"></a><span data-ttu-id="f1edc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f1edc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f1edc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f1edc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f1edc-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f1edc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f1edc-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f1edc-106">Event ID</span></span>|-|  
|<span data-ttu-id="f1edc-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f1edc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f1edc-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f1edc-108"> EDI</span></span>|  
|<span data-ttu-id="f1edc-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f1edc-109">Component</span></span>|<span data-ttu-id="f1edc-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f1edc-110">EDI Engine</span></span>|  
|<span data-ttu-id="f1edc-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f1edc-111">Symbolic Name</span></span>|<span data-ttu-id="f1edc-112">X12Ta1InvalidDataElementSeparatorDescription</span><span class="sxs-lookup"><span data-stu-id="f1edc-112">X12Ta1InvalidDataElementSeparatorDescription</span></span>|  
|<span data-ttu-id="f1edc-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f1edc-113">Message Text</span></span>|<span data-ttu-id="f1edc-114">Séparateur d'éléments de données non valide</span><span class="sxs-lookup"><span data-stu-id="f1edc-114">Invalid Data Element Separator</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f1edc-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f1edc-115">Explanation</span></span>  
 <span data-ttu-id="f1edc-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car la valeur du terminateur de segment dans l'échange n'est pas limitée aux caractères présents dans le jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="f1edc-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the value of the segment terminator in the interchange was not limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="f1edc-117">Dans X12, le terminateur de segment est défini comme le quatrième caractère du segment ISA.</span><span class="sxs-lookup"><span data-stu-id="f1edc-117">In X12, the segment terminator is defined as the fourth character in the ISA segment.</span></span> <span data-ttu-id="f1edc-118">Dans EDIFACT, le terminateur de segment correspond au champ UNA2.</span><span class="sxs-lookup"><span data-stu-id="f1edc-118">In EDIFACT, the segment terminator is the UNA2 field.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f1edc-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f1edc-119">User Action</span></span>  
 <span data-ttu-id="f1edc-120">Pour résoudre cette erreur, assurez-vous que le terminateur de segment (le quatrième caractère du segment ISA pour un échange X12 ou le champ UNA2 pour un échange EDIFACT) est limité aux caractères du jeu de caractères ASCII.</span><span class="sxs-lookup"><span data-stu-id="f1edc-120">To resolve this error, make sure that the segment terminator (the fourth character of the ISA segment in an X12 interchange or the UNA2 field in an EDIFACT interchange) is limited to the characters in the ASCII character set.</span></span> <span data-ttu-id="f1edc-121">Demandez à l'expéditeur de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="f1edc-121">Have the interchange resent.</span></span>