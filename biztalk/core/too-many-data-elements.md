---
title: "Trop d’éléments de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5000577d-5748-4e81-a394-86b2a780d70f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebf1fb61e4870b2a661876bf9375b3d3fe9abdd2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="too-many-data-elements"></a><span data-ttu-id="4b2bc-102">Trop d'éléments de données</span><span class="sxs-lookup"><span data-stu-id="4b2bc-102">Too many data elements</span></span>
## <a name="details"></a><span data-ttu-id="4b2bc-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4b2bc-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b2bc-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4b2bc-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4b2bc-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4b2bc-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4b2bc-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4b2bc-106">Event ID</span></span>|-|  
|<span data-ttu-id="4b2bc-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4b2bc-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4b2bc-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4b2bc-108"> EDI</span></span>|  
|<span data-ttu-id="4b2bc-109">Composant</span><span class="sxs-lookup"><span data-stu-id="4b2bc-109">Component</span></span>|<span data-ttu-id="4b2bc-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="4b2bc-110">EDI Engine</span></span>|  
|<span data-ttu-id="4b2bc-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4b2bc-111">Symbolic Name</span></span>|<span data-ttu-id="4b2bc-112">X12DeTooManyDataElementsDescription</span><span class="sxs-lookup"><span data-stu-id="4b2bc-112">X12DeTooManyDataElementsDescription</span></span>|  
|<span data-ttu-id="4b2bc-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4b2bc-113">Message Text</span></span>|<span data-ttu-id="4b2bc-114">Trop d'éléments de données</span><span class="sxs-lookup"><span data-stu-id="4b2bc-114">Too many data elements</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4b2bc-115">Explication</span><span class="sxs-lookup"><span data-stu-id="4b2bc-115">Explanation</span></span>  
 <span data-ttu-id="4b2bc-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant ou que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car un segment de l'échange contient plus d'éléments de données que ce qui est autorisé par le schéma de document ou de service.</span><span class="sxs-lookup"><span data-stu-id="4b2bc-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because a segment in the interchange contained more data elements than allowed by the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4b2bc-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4b2bc-117">User Action</span></span>  
 <span data-ttu-id="4b2bc-118">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de s'assurer que le segment comporte le nombre requis d'éléments de données, en supprimant, le cas échéant, ceux qui s'avèrent être en trop dans le segment, jusqu'à ce que ce dernier soit conforme au schéma.</span><span class="sxs-lookup"><span data-stu-id="4b2bc-118">To resolve this error, have the sender of the interchange ensure that segments include the required number of data elements, removing excess data elements from the segment if necessary, until the segment conforms to the schema.</span></span>