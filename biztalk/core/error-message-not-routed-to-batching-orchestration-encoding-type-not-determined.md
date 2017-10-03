---
title: "Le message ne peut pas être acheminé à l’orchestration de traitement par lot, comme le type de codage n’a pas pu être déterminé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d2ee38d-22c0-4fcf-bb68-b2ef00088c4c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe5054f53f779274c9b25f2751fdcb9d85545560
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-message-cannot-be-routed-to-the-batching-orchestration-as-the-encoding-type-could-not-be-determined"></a><span data-ttu-id="3d5b9-102">Le message ne peut pas être acheminé à l'orchestration de traitement par lots, car le type de codage n'a pu être déterminé</span><span class="sxs-lookup"><span data-stu-id="3d5b9-102">The message cannot be routed to the batching orchestration as the Encoding type could not be determined</span></span>
## <a name="details"></a><span data-ttu-id="3d5b9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3d5b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d5b9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3d5b9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3d5b9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3d5b9-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3d5b9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3d5b9-106">Event ID</span></span>|-|  
|<span data-ttu-id="3d5b9-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3d5b9-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3d5b9-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="3d5b9-108"> EDI</span></span>|  
|<span data-ttu-id="3d5b9-109">Composant</span><span class="sxs-lookup"><span data-stu-id="3d5b9-109">Component</span></span>|<span data-ttu-id="3d5b9-110">Moteur de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="3d5b9-110">Batching Engine</span></span>|  
|<span data-ttu-id="3d5b9-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3d5b9-111">Symbolic Name</span></span>|<span data-ttu-id="3d5b9-112">UnknownEncodingType</span><span class="sxs-lookup"><span data-stu-id="3d5b9-112">UnknownEncodingType</span></span>|  
|<span data-ttu-id="3d5b9-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3d5b9-113">Message Text</span></span>|<span data-ttu-id="3d5b9-114">Le message ne peut pas être acheminé à l'orchestration de traitement par lots, car le type de codage n'a pu être déterminé.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-114">The message cannot be routed to the batching orchestration as the Encoding type could not be determined.</span></span> <span data-ttu-id="3d5b9-115">Pour que le message puisse être traité par lots, le type de codage ne doit être ni X12 ni EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-115">The encoding type needs to be either X12 or EDIFACT for the message to be batched.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3d5b9-116">Explication</span><span class="sxs-lookup"><span data-stu-id="3d5b9-116">Explanation</span></span>  
 <span data-ttu-id="3d5b9-117">Cet événement de type erreur/avertissement/information indique qu'un élément par lot autre que de type EDI n'a pas été acheminé à l'instance d'orchestration par lot, même si le document informatisé correspond aux critères de filtre pour le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-117">This Error/Warning/Information event indicates that a non-EDI batch element was not routed to the batching orchestration instance, even though the transaction set meets the filter criteria for batching.</span></span> <span data-ttu-id="3d5b9-118">Le document informatisé n'a pas pu être acheminé à l'instance d'orchestration par lot, car la propriété de contexte EDI.EncodingType n'a pas été promue avec une valeur 0 pour X12 ou 1 pour EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-118">The transaction set could not be routed to the batching orchestration instance because the EDI.EncodingType context property was not promoted with a value of 0 for X12 or 1 for EDIFACT.</span></span> <span data-ttu-id="3d5b9-119">Cette erreur s'est produite lorsque l'élément par lot a été acheminé par le composant de pipeline BatchMarker à l'orchestration de routage, mais l'élément par lot autre que de type EDI n'était pas converti par un mappage en un message EDI.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-119">This error occurred when the batch element was routed by the BatchMarker pipeline component to the routing orchestration, but the non-EDI batch element was not converted by a map into an EDI message.</span></span> <span data-ttu-id="3d5b9-120">Par conséquent, l'orchestration de routage n'a pas pu déterminer le type de codage depuis les en-têtes EDI.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-120">As a result, the routing orchestration could not determine the encoding type from the EDI headers.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3d5b9-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3d5b9-121">User Action</span></span>  
 <span data-ttu-id="3d5b9-122">Pour résoudre cette erreur, vérifiez que le message autre que de type EDI est converti par un mappage en un message EDI avant d'être acheminé à l'orchestration de routage.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-122">To resolve this error, make sure that the non-EDI message is converted by a map into an EDI message before it is routed to the routing orchestration.</span></span> <span data-ttu-id="3d5b9-123">Vous devez aussi inclure un composant de pipeline personnalisé (avec le composant BatchMarker) ou une orchestration personnalisée pour traiter l'élément par lot n'étant pas de type EDI.</span><span class="sxs-lookup"><span data-stu-id="3d5b9-123">You must also include a custom pipeline component (with the BatchMarker component) or custom orchestration to process the non-EDI batch element.</span></span> <span data-ttu-id="3d5b9-124">Pour plus d'informations, consultez la rubrique « Assemblage d'un échange EDI par lot » dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3d5b9-124">For more information, see "Assembling a Batched EDI Interchange" in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>