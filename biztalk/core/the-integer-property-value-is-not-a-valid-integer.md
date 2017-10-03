---
title: "La valeur de propriété entier n’est pas un entier valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa97f3dd-4a01-4007-b23a-820cbebbc083
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32aebb74d937bb6b57d463598e178ad4d1ca280b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-integer-property-value-is-not-a-valid-integer"></a><span data-ttu-id="9c744-102">La valeur de propriété entier n'est pas un entier valide</span><span class="sxs-lookup"><span data-stu-id="9c744-102">The integer property value is not a valid integer</span></span>
## <a name="details"></a><span data-ttu-id="9c744-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9c744-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9c744-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9c744-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9c744-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9c744-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9c744-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9c744-106">Event ID</span></span>|-|  
|<span data-ttu-id="9c744-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9c744-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9c744-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9c744-108"> EDI</span></span>|  
|<span data-ttu-id="9c744-109">Composant</span><span class="sxs-lookup"><span data-stu-id="9c744-109">Component</span></span>|<span data-ttu-id="9c744-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="9c744-110">Batching Engine</span></span>|  
|<span data-ttu-id="9c744-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9c744-111">Symbolic Name</span></span>|<span data-ttu-id="9c744-112">InvalidIntegerPropertyValue</span><span class="sxs-lookup"><span data-stu-id="9c744-112">InvalidIntegerPropertyValue</span></span>|  
|<span data-ttu-id="9c744-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9c744-113">Message Text</span></span>|<span data-ttu-id="9c744-114">La valeur de propriété entier n'est pas un entier valide</span><span class="sxs-lookup"><span data-stu-id="9c744-114">The integer property value is not a valid integer</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9c744-115">Explication</span><span class="sxs-lookup"><span data-stu-id="9c744-115">Explanation</span></span>  
 <span data-ttu-id="9c744-116">Cet événement d'erreur/d'avertissement/d'informations indique qu'une valeur entrée pour une propriété d'une ligne dans la boîte de dialogue Filtre par lot est non valide, car la propriété requiert une valeur entière et la valeur qui a été entrée n'est pas un nombre entier.</span><span class="sxs-lookup"><span data-stu-id="9c744-116">This Error/Warning/Information event indicates that a value entered for a property in a row of the Batch Filter dialog box was invalid, because the property required an integer value, but the value entered was not an integer.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9c744-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9c744-117">User Action</span></span>  
 <span data-ttu-id="9c744-118">Pour résoudre cette erreur, dans la boîte de dialogue Propriétés EDI, dans la page Paramètres de création de lots d'échange, ouvrez la boîte de dialogue Filtre par lot.</span><span class="sxs-lookup"><span data-stu-id="9c744-118">To resolve this error, open the Batch Filter dialog box from within the Interchange Batch Creation Settings page of the EDI Properties dialog box.</span></span> <span data-ttu-id="9c744-119">Vérifiez que la valeur entrée pour une propriété demandant un nombre entier est appropriée.</span><span class="sxs-lookup"><span data-stu-id="9c744-119">Make sure that the value entered for a property that must be an integer is in fact an integer.</span></span>