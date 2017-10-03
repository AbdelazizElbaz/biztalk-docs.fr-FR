---
title: "L'échange comportait une erreur structurelle. Dernier groupe structurellement valide était d’ID : | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd62855b-ecc6-4cfd-be9c-0025348eb841
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 565a4865455cabef3cd53988d601a89ecf1549e0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-had-structural-error-last-structurally-valid-functional-group-id-was"></a><span data-ttu-id="f0873-103">L'échange comportait une erreur structurelle.</span><span class="sxs-lookup"><span data-stu-id="f0873-103">The interchange had structural error.</span></span> <span data-ttu-id="f0873-104">Le dernier ID de groupe structurellement valide était :</span><span class="sxs-lookup"><span data-stu-id="f0873-104">Last structurally valid functional group ID was:</span></span>
## <a name="details"></a><span data-ttu-id="f0873-105">Détails</span><span class="sxs-lookup"><span data-stu-id="f0873-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0873-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f0873-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f0873-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f0873-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f0873-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f0873-108">Event ID</span></span>|-|  
|<span data-ttu-id="f0873-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f0873-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f0873-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="f0873-110"> EDI</span></span>|  
|<span data-ttu-id="f0873-111">Composant</span><span class="sxs-lookup"><span data-stu-id="f0873-111">Component</span></span>|<span data-ttu-id="f0873-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f0873-112">EDI Engine</span></span>|  
|<span data-ttu-id="f0873-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f0873-113">Symbolic Name</span></span>|<span data-ttu-id="f0873-114">X12InterchangeStructuralErrorAfter1stGroup</span><span class="sxs-lookup"><span data-stu-id="f0873-114">X12InterchangeStructuralErrorAfter1stGroup</span></span>|  
|<span data-ttu-id="f0873-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f0873-115">Message Text</span></span>|<span data-ttu-id="f0873-116">L’échange avec l’id '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comportait une erreur structurelle.</span><span class="sxs-lookup"><span data-stu-id="f0873-116">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error.</span></span> <span data-ttu-id="f0873-117">Dernier ID de groupe structurellement valide était '{3}'</span><span class="sxs-lookup"><span data-stu-id="f0873-117">Last structurally valid functional group ID was '{3}'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f0873-118">Explication</span><span class="sxs-lookup"><span data-stu-id="f0873-118">Explanation</span></span>  
 <span data-ttu-id="f0873-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange X12 entrant, car une erreur structurelle s'est produite dans l'échange après le groupe fonctionnel indiqué.</span><span class="sxs-lookup"><span data-stu-id="f0873-119">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange, because a structural error occurred in the interchange after the indicated functional group.</span></span> <span data-ttu-id="f0873-120">Cela peut être survenu avec un échange qui a été conservé, avec des documents informatisés suspendus sur l’erreur.</span><span class="sxs-lookup"><span data-stu-id="f0873-120">This may have occurred with an interchange that was being preserved, with transaction sets suspended on the error.</span></span> <span data-ttu-id="f0873-121">Par conséquent, les documents informatisés qui incluaient l'erreur ont été suspendus et les autres documents informatisés ont été traités dans le cadre du lot conservé.</span><span class="sxs-lookup"><span data-stu-id="f0873-121">As a result of this error, the transaction set (or sets) that included the error was suspended, but the rest of the transaction sets were processed as part of the preserved batch.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f0873-122">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0873-122">User Action</span></span>  
 <span data-ttu-id="f0873-123">Pour résoudre cette erreur, demandez à l'expéditeur de corriger l'erreur structurelle, puis de renvoyer l'échange.</span><span class="sxs-lookup"><span data-stu-id="f0873-123">To resolve this error, have the sender of the interchange fix the structural error, and then resend the interchange.</span></span>