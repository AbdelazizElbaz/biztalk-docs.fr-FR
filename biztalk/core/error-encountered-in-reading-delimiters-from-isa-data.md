---
title: "Erreur rencontrée lors de la lecture des délimiteurs de données ISA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cb60abd-53c8-45e1-a840-d27dc974aad7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5fcde2519740adc5531363911146164f460f9b3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-in-reading-delimiters-from-isa-data"></a><span data-ttu-id="5ba08-102">Erreur rencontrée lors de la lecture des délimiteurs à partir des données ISA</span><span class="sxs-lookup"><span data-stu-id="5ba08-102">Error encountered in reading delimiters from ISA data</span></span>
## <a name="details"></a><span data-ttu-id="5ba08-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5ba08-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ba08-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5ba08-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5ba08-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5ba08-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5ba08-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5ba08-106">Event ID</span></span>|-|  
|<span data-ttu-id="5ba08-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5ba08-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5ba08-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5ba08-108"> EDI</span></span>|  
|<span data-ttu-id="5ba08-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5ba08-109">Component</span></span>|<span data-ttu-id="5ba08-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5ba08-110">EDI Engine</span></span>|  
|<span data-ttu-id="5ba08-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5ba08-111">Symbolic Name</span></span>|<span data-ttu-id="5ba08-112">InvalidIsaData</span><span class="sxs-lookup"><span data-stu-id="5ba08-112">InvalidIsaData</span></span>|  
|<span data-ttu-id="5ba08-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5ba08-113">Message Text</span></span>|<span data-ttu-id="5ba08-114">Erreur rencontrée lors de la lecture des délimiteurs à partir des données ISA</span><span class="sxs-lookup"><span data-stu-id="5ba08-114">Error encountered in reading delimiters from ISA data</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5ba08-115">Explication</span><span class="sxs-lookup"><span data-stu-id="5ba08-115">Explanation</span></span>  
 <span data-ttu-id="5ba08-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors du traitement d'un échange X12 entrant car il n'a pas pu analyser les séparateurs du segment ISA.</span><span class="sxs-lookup"><span data-stu-id="5ba08-116">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when processing an incoming X12 interchange because it could not parse the separators from the ISA segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5ba08-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ba08-117">User Action</span></span>  
 <span data-ttu-id="5ba08-118">Pour résoudre cette erreur, vérifiez que les séparateurs du segment ISA de l'échange entrant sont uniques et valides.</span><span class="sxs-lookup"><span data-stu-id="5ba08-118">To resolve this error, verify that the separators in the ISA segment of the incoming interchange are unique and valid.</span></span> <span data-ttu-id="5ba08-119">Sinon, demandez à l'expéditeur de l'échange d'entrer des valeurs uniques et valides dans chaque champ de séparateur (segment ISA11 du séparateur de répétition et segment ISA16 du séparateur de composants), puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="5ba08-119">If not, have the sender of the interchange enter unique and valid values into each of the separator fields (the ISA11 segment for the repetition separator and the ISA16 segment for the component separator), and then resend the interchange.</span></span>