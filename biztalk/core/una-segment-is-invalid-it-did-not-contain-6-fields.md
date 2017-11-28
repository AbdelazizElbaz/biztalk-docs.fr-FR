---
title: Le segment UNA n'est pas valide. Il ne contenait pas 6 champs | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c939d8d3-e6fb-4505-836d-31559fc5f1a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00d2a66e414bfe41e03c1e096034a620369064b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="una-segment-is-invalid-it-did-not-contain-6-fields"></a><span data-ttu-id="c66a8-103">Le segment UNA n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c66a8-103">UNA segment is invalid.</span></span> <span data-ttu-id="c66a8-104">Il ne contenait pas 6 champs.</span><span class="sxs-lookup"><span data-stu-id="c66a8-104">It did not contain 6 fields</span></span>
## <a name="details"></a><span data-ttu-id="c66a8-105">Détails</span><span class="sxs-lookup"><span data-stu-id="c66a8-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c66a8-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c66a8-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c66a8-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c66a8-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c66a8-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c66a8-108">Event ID</span></span>|-|  
|<span data-ttu-id="c66a8-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c66a8-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c66a8-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="c66a8-110"> EDI</span></span>|  
|<span data-ttu-id="c66a8-111">Composant</span><span class="sxs-lookup"><span data-stu-id="c66a8-111">Component</span></span>|<span data-ttu-id="c66a8-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c66a8-112">EDI Engine</span></span>|  
|<span data-ttu-id="c66a8-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c66a8-113">Symbolic Name</span></span>|<span data-ttu-id="c66a8-114">UnaDidNotContainSixDelimiters</span><span class="sxs-lookup"><span data-stu-id="c66a8-114">UnaDidNotContainSixDelimiters</span></span>|  
|<span data-ttu-id="c66a8-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c66a8-115">Message Text</span></span>|<span data-ttu-id="c66a8-116">Le segment UNA n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c66a8-116">UNA segment is invalid.</span></span> <span data-ttu-id="c66a8-117">Il ne contenait pas 6 champs.</span><span class="sxs-lookup"><span data-stu-id="c66a8-117">It did not contain 6 fields</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c66a8-118">Explication</span><span class="sxs-lookup"><span data-stu-id="c66a8-118">Explanation</span></span>  
 <span data-ttu-id="c66a8-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange EDIFACT entrant, car le segment UNA contient un nombre d'éléments de données inférieur à 6.</span><span class="sxs-lookup"><span data-stu-id="c66a8-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange because the UNA segment contained fewer than six data elements.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c66a8-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c66a8-120">User Action</span></span>  
 <span data-ttu-id="c66a8-121">Pour résoudre cette erreur, demandez à l'expéditeur de l'échange de s'assurer que le segment UNA contienne 6 éléments de données, puis demandez-lui de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="c66a8-121">To resolve this error, have the sender of the interchange make sure that the UNA segment contains six data elements, and then resend the interchange.</span></span>