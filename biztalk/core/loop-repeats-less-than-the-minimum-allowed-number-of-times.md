---
title: "Inférieure à la valeur minimale autorisée nombre de fois où une boucle se répète | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0be21d1d-86da-456b-83e6-c91f1dc9fb48
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00d9b38712d8b8336daa9357bd20eb34148691b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loop-repeats-less-than-the-minimum-allowed-number-of-times"></a><span data-ttu-id="7876f-102">Le nombre de répétition de la boucle est inférieur au nombre minimal autorisé</span><span class="sxs-lookup"><span data-stu-id="7876f-102">Loop repeats less than the minimum allowed number of times</span></span>
## <a name="details"></a><span data-ttu-id="7876f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="7876f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7876f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="7876f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7876f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="7876f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="7876f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="7876f-106">Event ID</span></span>|-|  
|<span data-ttu-id="7876f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="7876f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7876f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="7876f-108"> EDI</span></span>|  
|<span data-ttu-id="7876f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="7876f-109">Component</span></span>|<span data-ttu-id="7876f-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="7876f-110">EDI Engine</span></span>|  
|<span data-ttu-id="7876f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="7876f-111">Symbolic Name</span></span>|<span data-ttu-id="7876f-112">X12SeLoopRepeatsLessTimesDescription</span><span class="sxs-lookup"><span data-stu-id="7876f-112">X12SeLoopRepeatsLessTimesDescription</span></span>|  
|<span data-ttu-id="7876f-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="7876f-113">Message Text</span></span>|<span data-ttu-id="7876f-114">Le nombre de répétition de la boucle est inférieur au nombre minimal autorisé</span><span class="sxs-lookup"><span data-stu-id="7876f-114">Loop repeats less than the minimum allowed number of times</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7876f-115">Explication</span><span class="sxs-lookup"><span data-stu-id="7876f-115">Explanation</span></span>  
 <span data-ttu-id="7876f-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car il contenait une boucle dont le nombre de répétitions était inférieur au nombre de fois minimal requis par le schéma de message.</span><span class="sxs-lookup"><span data-stu-id="7876f-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained a loop that repeated fewer times than the minimum number of times required by the message schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7876f-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7876f-117">User Action</span></span>  
 <span data-ttu-id="7876f-118">Pour résoudre cette erreur, vérifiez que le nombre de répétitions de la boucle de l'échange est au moins égal au nombre de fois indiqué dans la propriété minOccurs spécifiée pour celle-ci dans le schéma de message, puis renvoyez l'échange.</span><span class="sxs-lookup"><span data-stu-id="7876f-118">To resolve this error, make sure that the loop repeats in the interchange at least the number of times in the minOccurs property specified for the loop in the message schema, and then have the interchange resent.</span></span>