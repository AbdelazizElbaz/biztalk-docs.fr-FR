---
title: "Cette boucle contient un nœud terminal. Il ne peut contenir de Segments ou autres boucles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a0ee5e6-519d-4c95-8681-de5a37741d56
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03349389fb108d434cce67afc5be13fd2a3d513
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-loop-contains-a-leaf-node-it-can-only-contain-other-loops-or-segments"></a><span data-ttu-id="fe229-103">Cette boucle contient un nœud terminal.</span><span class="sxs-lookup"><span data-stu-id="fe229-103">The loop contains a leaf node.</span></span> <span data-ttu-id="fe229-104">Elle peut contenir uniquement d'autres boucles ou des segments</span><span class="sxs-lookup"><span data-stu-id="fe229-104">It can only contain other Loops or Segments</span></span>
## <a name="details"></a><span data-ttu-id="fe229-105">Détails</span><span class="sxs-lookup"><span data-stu-id="fe229-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fe229-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fe229-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fe229-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fe229-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="fe229-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fe229-108">Event ID</span></span>|-|  
|<span data-ttu-id="fe229-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fe229-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fe229-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="fe229-110"> EDI</span></span>|  
|<span data-ttu-id="fe229-111">Composant</span><span class="sxs-lookup"><span data-stu-id="fe229-111">Component</span></span>|<span data-ttu-id="fe229-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="fe229-112">EDI Engine</span></span>|  
|<span data-ttu-id="fe229-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fe229-113">Symbolic Name</span></span>|<span data-ttu-id="fe229-114">SchemaCode125ELoopContainsLeafNode</span><span class="sxs-lookup"><span data-stu-id="fe229-114">SchemaCode125ELoopContainsLeafNode</span></span>|  
|<span data-ttu-id="fe229-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fe229-115">Message Text</span></span>|<span data-ttu-id="fe229-116">Cette boucle contient un nœud terminal.</span><span class="sxs-lookup"><span data-stu-id="fe229-116">The loop contains a leaf node.</span></span> <span data-ttu-id="fe229-117">Elle peut contenir uniquement d'autres boucles ou des segments</span><span class="sxs-lookup"><span data-stu-id="fe229-117">It can only contain other Loops or Segments</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fe229-118">Explication</span><span class="sxs-lookup"><span data-stu-id="fe229-118">Explanation</span></span>  
 <span data-ttu-id="fe229-119">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car il n'était pas conforme au schéma de document.</span><span class="sxs-lookup"><span data-stu-id="fe229-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, because the interchange did not conform to the document schema.</span></span> <span data-ttu-id="fe229-120">Dans ce cas, une boucle contenait un nœud terminal sans enfant, alors que le schéma spécifiait qu'elle ne pouvait comporter que des segments ou d'autres boucles.</span><span class="sxs-lookup"><span data-stu-id="fe229-120">In this case, a loop contained a childless leaf node, whereas the schema specified that the loop could only contain other loops or segments.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fe229-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fe229-121">User Action</span></span>  
 <span data-ttu-id="fe229-122">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de modifier la boucle afin qu'elle ne contienne pas de nœuds terminaux, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="fe229-122">To resolve this error, have the sender of the interchange fix the loop so that it does not contain leaf nodes, and then resend the interchange.</span></span>