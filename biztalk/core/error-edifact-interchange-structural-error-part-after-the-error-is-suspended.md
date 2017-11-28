---
title: "L'échange comportait une erreur structurelle. La partie située après l’erreur a été interrompue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9071825d-7b90-42bf-bcf9-2a15ae36086d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a028608e9843ee40c26bc7e8b158d97552a58163
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-the-part-after-the-error-is-being-suspended"></a><span data-ttu-id="f173a-103">L'échange comportait une erreur structurelle.</span><span class="sxs-lookup"><span data-stu-id="f173a-103">The interchange had structural error.</span></span> <span data-ttu-id="f173a-104">La partie située après l'erreur a été interrompue</span><span class="sxs-lookup"><span data-stu-id="f173a-104">The part after the error is being suspended</span></span>
## <a name="details"></a><span data-ttu-id="f173a-105">Détails</span><span class="sxs-lookup"><span data-stu-id="f173a-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f173a-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f173a-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f173a-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f173a-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f173a-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f173a-108">Event ID</span></span>|-|  
|<span data-ttu-id="f173a-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f173a-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f173a-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="f173a-110"> EDI</span></span>|  
|<span data-ttu-id="f173a-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f173a-111">Component</span></span>|<span data-ttu-id="f173a-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f173a-112">EDI Engine</span></span>|  
|<span data-ttu-id="f173a-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f173a-113">Symbolic Name</span></span>|<span data-ttu-id="f173a-114">EfactInterchangeStructuralError</span><span class="sxs-lookup"><span data-stu-id="f173a-114">EfactInterchangeStructuralError</span></span>|  
|<span data-ttu-id="f173a-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f173a-115">Message Text</span></span>|<span data-ttu-id="f173a-116">L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle.</span><span class="sxs-lookup"><span data-stu-id="f173a-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="f173a-117">La partie située après que l’erreur a été interrompue, reportez-vous à la file d’attente pour plus d’informations</span><span class="sxs-lookup"><span data-stu-id="f173a-117">The part after the error is being suspended, refer to Suspended Queue for details</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f173a-118">Explication</span><span class="sxs-lookup"><span data-stu-id="f173a-118">Explanation</span></span>  
 <span data-ttu-id="f173a-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange EDIFACT entrant car une erreur structurelle s'est produite dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="f173a-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming EDIFACT interchange, because a structural error occurred in the interchange.</span></span> <span data-ttu-id="f173a-120">Cette erreur s'est produite avec un échange qui était conservé, avec des documents informatisés suspendus au moment de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="f173a-120">This occurred with an interchange that was being preserved, with transaction sets suspended on the error.</span></span> <span data-ttu-id="f173a-121">Par conséquent, les documents informatisés qui incluaient l'erreur ont été suspendus et les autres documents informatisés ont été traités dans le cadre du lot conservé.</span><span class="sxs-lookup"><span data-stu-id="f173a-121">As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f173a-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f173a-122">User Action</span></span>  
 <span data-ttu-id="f173a-123">Pour résoudre cette erreur, demandez à l'expéditeur de corriger l'erreur structurelle, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="f173a-123">To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.</span></span>