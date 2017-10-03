---
title: "Erreur rencontrée lors de l'analyse. L’échange Edifact qui ne contenait pas de groupe comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6b324fd-f365-41b9-81aa-b6c5c5d3f673
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 550e5ca207bef7fdcb42ffcbd52e114ad3dc95ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a><span data-ttu-id="8be8f-103">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="8be8f-103">Error encountered during parsing.</span></span> <span data-ttu-id="8be8f-104">L'échange EDIFACT qui ne contenait pas de groupe comportait les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="8be8f-104">The Edifact interchange which did not contain a group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="8be8f-105">Détails</span><span class="sxs-lookup"><span data-stu-id="8be8f-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8be8f-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8be8f-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8be8f-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8be8f-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8be8f-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8be8f-108">Event ID</span></span>|-|  
|<span data-ttu-id="8be8f-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8be8f-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8be8f-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="8be8f-110"> EDI</span></span>|  
|<span data-ttu-id="8be8f-111">Composant</span><span class="sxs-lookup"><span data-stu-id="8be8f-111">Component</span></span>|<span data-ttu-id="8be8f-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="8be8f-112">EDI Engine</span></span>|  
|<span data-ttu-id="8be8f-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8be8f-113">Symbolic Name</span></span>|<span data-ttu-id="8be8f-114">EfactFunctionalGroupReceiveErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="8be8f-114">EfactFunctionalGroupReceiveErrorWithoutGroup</span></span>|  
|<span data-ttu-id="8be8f-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8be8f-115">Message Text</span></span>|<span data-ttu-id="8be8f-116">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="8be8f-116">Error encountered during parsing.</span></span> <span data-ttu-id="8be8f-117">L’échange Edifact qui ne contenait pas de groupe, avec l’id d’échange '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="8be8f-117">The Edifact interchange which did not contain a group, with interchange id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8be8f-118">Explication</span><span class="sxs-lookup"><span data-stu-id="8be8f-118">Explanation</span></span>  
 <span data-ttu-id="8be8f-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors de l'analyse d'un échange EDIFACT entrant qui ne contenait pas de groupe en raison des erreurs mentionnées.</span><span class="sxs-lookup"><span data-stu-id="8be8f-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange that did not contain a group because of the stated errors.</span></span> <span data-ttu-id="8be8f-120">Notez que les groupes sont facultatifs dans les échanges EDIFACT.</span><span class="sxs-lookup"><span data-stu-id="8be8f-120">Note that groups are optional in EDIFACT interchanges.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8be8f-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8be8f-121">User Action</span></span>  
 <span data-ttu-id="8be8f-122">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci et déterminer la méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="8be8f-122">To resolve this error, use the information in the error message to identify the error and then determine the problem resolution in the product help.</span></span>