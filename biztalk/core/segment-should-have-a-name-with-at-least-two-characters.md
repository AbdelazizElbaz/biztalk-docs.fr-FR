---
title: "Segment doit avoir un nom comportant au moins deux caractères | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f80bbc4a-151a-4094-8640-1944e8812730
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70d4b39aa9421e4b60fd9e0c4415c69862c00526
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-should-have-a-name-with-at-least-two-characters"></a><span data-ttu-id="24d55-102">Le nom du segment doit comporter au moins deux caractères</span><span class="sxs-lookup"><span data-stu-id="24d55-102">Segment should have a name with at least two characters</span></span>
## <a name="details"></a><span data-ttu-id="24d55-103">Détails</span><span class="sxs-lookup"><span data-stu-id="24d55-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24d55-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="24d55-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="24d55-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="24d55-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="24d55-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="24d55-106">Event ID</span></span>|-|  
|<span data-ttu-id="24d55-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="24d55-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="24d55-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="24d55-108"> EDI</span></span>|  
|<span data-ttu-id="24d55-109">Composant</span><span class="sxs-lookup"><span data-stu-id="24d55-109">Component</span></span>|<span data-ttu-id="24d55-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="24d55-110">EDI Engine</span></span>|  
|<span data-ttu-id="24d55-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="24d55-111">Symbolic Name</span></span>|<span data-ttu-id="24d55-112">SchemaCode103EInvalidTagLength</span><span class="sxs-lookup"><span data-stu-id="24d55-112">SchemaCode103EInvalidTagLength</span></span>|  
|<span data-ttu-id="24d55-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="24d55-113">Message Text</span></span>|<span data-ttu-id="24d55-114">Segment doit avoir un nom au moins 2 caractères</span><span class="sxs-lookup"><span data-stu-id="24d55-114">Segment should have a name with at least 2 characters</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="24d55-115">Explication</span><span class="sxs-lookup"><span data-stu-id="24d55-115">Explanation</span></span>  
 <span data-ttu-id="24d55-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le nom d'un segment de l'échange ne contient pas au moins deux caractères.</span><span class="sxs-lookup"><span data-stu-id="24d55-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the name of a segment in the interchange does not have at least two characters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="24d55-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="24d55-117">User Action</span></span>  
 <span data-ttu-id="24d55-118">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de s'assurer que le nom de chaque segment de l'échange contient au moins deux caractères, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="24d55-118">To resolve this error, have the sender of the interchange ensure that the name of each segment in the interchange has at least two characters, and then resend the interchange.</span></span>