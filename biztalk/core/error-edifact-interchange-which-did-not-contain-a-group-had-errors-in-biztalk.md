---
title: "Erreur lors de la sérialisation. L’échange Edifact qui ne contenait pas de groupe comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af693139-e4cd-4bcb-922c-79caa148d3b7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72108104b359d4d06233cf9a623097bfd046a0ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-interchange-which-did-not-contain-a-group-had-the-following-errors"></a><span data-ttu-id="62c3f-103">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="62c3f-103">Error encountered during serialization.</span></span> <span data-ttu-id="62c3f-104">L'échange EDIFACT qui ne contenait pas de groupe comportait les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="62c3f-104">The Edifact interchange which did not contain a group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="62c3f-105">Détails</span><span class="sxs-lookup"><span data-stu-id="62c3f-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62c3f-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="62c3f-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="62c3f-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="62c3f-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="62c3f-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="62c3f-108">Event ID</span></span>|-|  
|<span data-ttu-id="62c3f-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="62c3f-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="62c3f-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="62c3f-110"> EDI</span></span>|  
|<span data-ttu-id="62c3f-111">Composant</span><span class="sxs-lookup"><span data-stu-id="62c3f-111">Component</span></span>|<span data-ttu-id="62c3f-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="62c3f-112">EDI Engine</span></span>|  
|<span data-ttu-id="62c3f-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="62c3f-113">Symbolic Name</span></span>|<span data-ttu-id="62c3f-114">EfactFunctionalGroupSendErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="62c3f-114">EfactFunctionalGroupSendErrorWithoutGroup</span></span>|  
|<span data-ttu-id="62c3f-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="62c3f-115">Message Text</span></span>|<span data-ttu-id="62c3f-116">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="62c3f-116">Error encountered during serialization.</span></span> <span data-ttu-id="62c3f-117">L’échange Edifact qui ne contenait pas de groupe, avec l’id d’échange '{0}', id d’expéditeur « {{1} », id de récepteur « {{2} » comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="62c3f-117">The Edifact interchange which did not contain a group, with interchange id '{0}', with sender id '{1}', receiver id '{2}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="62c3f-118">Explication</span><span class="sxs-lookup"><span data-stu-id="62c3f-118">Explanation</span></span>  
 <span data-ttu-id="62c3f-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange EDIFACT sortant en raison des erreurs mentionnées pour l'échange identifié.</span><span class="sxs-lookup"><span data-stu-id="62c3f-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified interchange.</span></span> <span data-ttu-id="62c3f-120">Notez que l'échange ne contient pas de groupe.</span><span class="sxs-lookup"><span data-stu-id="62c3f-120">Note that the interchange does not contain a group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="62c3f-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="62c3f-121">User Action</span></span>  
 <span data-ttu-id="62c3f-122">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci dans l'échange et déterminer la méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="62c3f-122">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>