---
title: "Segment TA1 trouvé après un groupe fonctionnel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee3d090a-0916-4a0e-82dc-2c9af9f97683
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86e9ac6e1e0c3a3b76dbc144739f3a16fddd0d67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ta1-segment-found-after-a-functional-group"></a><span data-ttu-id="b2888-102">Segment TA1 trouvé après un groupe fonctionnel</span><span class="sxs-lookup"><span data-stu-id="b2888-102">TA1 segment found after a functional group</span></span>
## <a name="details"></a><span data-ttu-id="b2888-103">Détails</span><span class="sxs-lookup"><span data-stu-id="b2888-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2888-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="b2888-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="b2888-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="b2888-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="b2888-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="b2888-106">Event ID</span></span>|-|  
|<span data-ttu-id="b2888-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="b2888-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b2888-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b2888-108"> EDI</span></span>|  
|<span data-ttu-id="b2888-109">Composant</span><span class="sxs-lookup"><span data-stu-id="b2888-109">Component</span></span>|<span data-ttu-id="b2888-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="b2888-110">EDI Engine</span></span>|  
|<span data-ttu-id="b2888-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="b2888-111">Symbolic Name</span></span>|<span data-ttu-id="b2888-112">TA1FoundAfterFunctionalGroup</span><span class="sxs-lookup"><span data-stu-id="b2888-112">TA1FoundAfterFunctionalGroup</span></span>|  
|<span data-ttu-id="b2888-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="b2888-113">Message Text</span></span>|<span data-ttu-id="b2888-114">Segment TA1 trouvé après un groupe fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="b2888-114">TA1 segment found after a functional group.</span></span> <span data-ttu-id="b2888-115">Le message est donc rejeté</span><span class="sxs-lookup"><span data-stu-id="b2888-115">So, the message is being rejected</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b2888-116">Explication</span><span class="sxs-lookup"><span data-stu-id="b2888-116">Explanation</span></span>  
 <span data-ttu-id="b2888-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'accusé de réception entrant car celui-ci contient un groupe fonctionnel puis un segment TA1.</span><span class="sxs-lookup"><span data-stu-id="b2888-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming acknowledgment because the acknowledgment contained a functional group and then a TA1 segment.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b2888-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="b2888-118">User Action</span></span>  
 <span data-ttu-id="b2888-119">Pour résoudre cette erreur, demandez à l'expéditeur de l'accusé de réception TA1 de s'assurer que l'échange ne contient pas de groupe fonctionnel avant le segment TA1, puis de renvoyer l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="b2888-119">To resolve this error, have the sender of the TA1 acknowledgment ensure that the interchange does not contain a functional group before the TA1 segment, and then resend the acknowledgment.</span></span>