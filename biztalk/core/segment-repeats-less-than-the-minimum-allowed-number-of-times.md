---
title: "Répétitions du segment inférieur au minimum autorisé nombre de fois | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8ca6c3d-f923-49bc-b5d9-65dc2d7adab1
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee7aeb488fb2f8634fba73e7ddf3f44cd02a6529
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="segment-repeats-less-than-the-minimum-allowed-number-of-times"></a><span data-ttu-id="9ca66-102">Nombre de répétition du segment inférieur au nombre minimal autorisé</span><span class="sxs-lookup"><span data-stu-id="9ca66-102">Segment repeats less than the minimum allowed number of times</span></span>
## <a name="details"></a><span data-ttu-id="9ca66-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9ca66-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ca66-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9ca66-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9ca66-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9ca66-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9ca66-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9ca66-106">Event ID</span></span>|-|  
|<span data-ttu-id="9ca66-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9ca66-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9ca66-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9ca66-108"> EDI</span></span>|  
|<span data-ttu-id="9ca66-109">Composant</span><span class="sxs-lookup"><span data-stu-id="9ca66-109">Component</span></span>|<span data-ttu-id="9ca66-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="9ca66-110">EDI Engine</span></span>|  
|<span data-ttu-id="9ca66-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9ca66-111">Symbolic Name</span></span>|<span data-ttu-id="9ca66-112">X12SeSegmentRepeatsLessTimesDescription</span><span class="sxs-lookup"><span data-stu-id="9ca66-112">X12SeSegmentRepeatsLessTimesDescription</span></span>|  
|<span data-ttu-id="9ca66-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9ca66-113">Message Text</span></span>|<span data-ttu-id="9ca66-114">Nombre de répétition du segment inférieur au nombre minimal autorisé</span><span class="sxs-lookup"><span data-stu-id="9ca66-114">Segment repeats less than the minimum allowed number of times</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ca66-115">Explication</span><span class="sxs-lookup"><span data-stu-id="9ca66-115">Explanation</span></span>  
 <span data-ttu-id="9ca66-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas réussi à traiter l'échange X12 entrant, car un segment de l'échange ne se répète pas le nombre de fois minimal requis par le schéma de document.</span><span class="sxs-lookup"><span data-stu-id="9ca66-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because a segment in the interchange does not repeat the minimum number of times required by the document schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ca66-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9ca66-117">User Action</span></span>  
 <span data-ttu-id="9ca66-118">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de modifier le nombre de répétitions du segment de manière à ce que ce dernier se répète le nombre de fois requis par le schéma de document, puis demandez-lui de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="9ca66-118">To resolve this error, have the sender of the interchange as repetition of the segment so that it repeats at least the minimum number of times required by the document schema, and then resend the interchange.</span></span>