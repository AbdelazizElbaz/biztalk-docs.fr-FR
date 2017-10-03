---
title: Boucle se produit sur le nombre maximal de fois | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ac9f5d3-04ec-4c40-8a1f-17ef0b143cda
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 827ab88a2676cd052ee1ea3ba3a4bd7bd80f1912
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loop-occurs-over-maximum-times"></a><span data-ttu-id="0160f-102">Une boucle se produit après un nombre de fois maximal</span><span class="sxs-lookup"><span data-stu-id="0160f-102">Loop Occurs Over Maximum Times</span></span>
## <a name="details"></a><span data-ttu-id="0160f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="0160f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0160f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="0160f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0160f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="0160f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="0160f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0160f-106">Event ID</span></span>|-|  
|<span data-ttu-id="0160f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="0160f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="0160f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="0160f-108"> EDI</span></span>|  
|<span data-ttu-id="0160f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="0160f-109">Component</span></span>|<span data-ttu-id="0160f-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="0160f-110">EDI Engine</span></span>|  
|<span data-ttu-id="0160f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="0160f-111">Symbolic Name</span></span>|<span data-ttu-id="0160f-112">X12LoopOccursOverMaximumTimesDescription</span><span class="sxs-lookup"><span data-stu-id="0160f-112">X12LoopOccursOverMaximumTimesDescription</span></span>|  
|<span data-ttu-id="0160f-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="0160f-113">Message Text</span></span>|<span data-ttu-id="0160f-114">Boucles se produisent dans le temps Maximum</span><span class="sxs-lookup"><span data-stu-id="0160f-114">Loops Occurs Over Maximum Times</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0160f-115">Explication</span><span class="sxs-lookup"><span data-stu-id="0160f-115">Explanation</span></span>  
 <span data-ttu-id="0160f-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car il contenait une boucle qui s'est répétée au-delà du nombre de fois maximal requis par le schéma de message.</span><span class="sxs-lookup"><span data-stu-id="0160f-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained a loop that repeated more times than the maximum number of times required by the message schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0160f-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="0160f-117">User Action</span></span>  
 <span data-ttu-id="0160f-118">Pour résoudre cette erreur, vérifiez que la boucle de l'échange ne se répète pas plus que le nombre de fois indiqué dans la propriété maxOccurs spécifiée pour celle-ci dans le schéma de message, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="0160f-118">To resolve this error, make sure that the loop repeats in the interchange no more than the number of times in the maxOccurs property specified for the loop in the message schema, and then have the interchange resent.</span></span>