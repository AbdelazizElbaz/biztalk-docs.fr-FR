---
title: "N’a pas trouvé les identités d’entreprise correspondant au lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c9baf11-e9c6-482d-a47d-aa99852939bf
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f1027186e5b001d21e08bbabcfc100400a02d5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-find-business-identities-corresponding-to-batch"></a><span data-ttu-id="c7e0f-102">Impossible de trouver des identités d'entreprise correspondant au lot</span><span class="sxs-lookup"><span data-stu-id="c7e0f-102">Could not find Business Identities corresponding to batch</span></span>
## <a name="details"></a><span data-ttu-id="c7e0f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="c7e0f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c7e0f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="c7e0f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c7e0f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="c7e0f-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c7e0f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="c7e0f-106">Event ID</span></span>|-|  
|<span data-ttu-id="c7e0f-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="c7e0f-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c7e0f-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="c7e0f-108"> EDI</span></span>|  
|<span data-ttu-id="c7e0f-109">Composant</span><span class="sxs-lookup"><span data-stu-id="c7e0f-109">Component</span></span>|<span data-ttu-id="c7e0f-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="c7e0f-110">EDI Engine</span></span>|  
|<span data-ttu-id="c7e0f-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="c7e0f-111">Symbolic Name</span></span>|<span data-ttu-id="c7e0f-112">IdentitiesNotFoundForBatch</span><span class="sxs-lookup"><span data-stu-id="c7e0f-112">IdentitiesNotFoundForBatch</span></span>|  
|<span data-ttu-id="c7e0f-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="c7e0f-113">Message Text</span></span>|<span data-ttu-id="c7e0f-114">Impossible de trouver des identités d'entreprise correspondant au lot {0}.</span><span class="sxs-lookup"><span data-stu-id="c7e0f-114">Could not find Business Identities corresponding to batch {0}.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c7e0f-115">Explication</span><span class="sxs-lookup"><span data-stu-id="c7e0f-115">Explanation</span></span>  
 <span data-ttu-id="c7e0f-116">Cet événement de type erreur/avertissement/information indique que BizTalk Server n'a pas pu traiter un message de traitement par lot en raison d'une quantité insuffisante de données.</span><span class="sxs-lookup"><span data-stu-id="c7e0f-116">This Error/Warning/Information event indicates BizTalk Server was not able to process a batch message because of insufficient data.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c7e0f-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="c7e0f-117">User Action</span></span>  
 <span data-ttu-id="c7e0f-118">Pour résoudre cette erreur, assurez-vous qu'un lot portant l'ID donné soit présent dans les propriétés de l'accord contenant et que les identités d'entreprise adéquates soient spécifiées dans l'accord.</span><span class="sxs-lookup"><span data-stu-id="c7e0f-118">To resolve this error, ensure that a batch with the given Id is present in the Agreement properties of the containing Agreement and proper business identities are specified for the agreement.</span></span>