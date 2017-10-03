---
title: "Document informatisé EDIFACT contenu dans l’erreur d’échange | Documents Microsoft"
description: "Erreur lors de la sérialisation. Le document informatisé EDIFACT contenu dans l'échange (sans groupe) est en cours d'interruption avec les erreurs suivantes"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a0a33ac-d83e-495c-ba75-88c15ad7cfcd
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f089e49941ffec7d3392b3bc35edcbc4eefec5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edifact-transaction-set-is-suspended-error-and-details"></a><span data-ttu-id="11373-104">Document informatisé EDIFACT est détails et l’erreur suspendu</span><span class="sxs-lookup"><span data-stu-id="11373-104">Edifact transaction set is suspended error and details</span></span>

`Error encountered during serialization. The Edifact transaction set contained in interchange (without group) is being suspended with following errors`

## <a name="details"></a><span data-ttu-id="11373-105">Détails</span><span class="sxs-lookup"><span data-stu-id="11373-105">Details</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="11373-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="11373-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="11373-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="11373-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="11373-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="11373-108">Event ID</span></span>|-|  
|<span data-ttu-id="11373-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="11373-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="11373-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="11373-110"> EDI</span></span>|  
|<span data-ttu-id="11373-111">Composant</span><span class="sxs-lookup"><span data-stu-id="11373-111">Component</span></span>|<span data-ttu-id="11373-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="11373-112">EDI Engine</span></span>|  
|<span data-ttu-id="11373-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="11373-113">Symbolic Name</span></span>|<span data-ttu-id="11373-114">EfactTransactionSetSendErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="11373-114">EfactTransactionSetSendErrorWithoutGroup</span></span>|  
|<span data-ttu-id="11373-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="11373-115">Message Text</span></span>|<span data-ttu-id="11373-116">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="11373-116">Error encountered during serialization.</span></span> <span data-ttu-id="11373-117">Le document informatisé avec l’id '{0}' contenu dans l’échange (sans groupe) avec l’id « {{1}', id d’expéditeur « {{2} », id de destinataire '{3}' est interrompu avec les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="11373-117">The Edifact transaction set with id '{0}' contained in interchange (without group)  with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="11373-118">Explication</span><span class="sxs-lookup"><span data-stu-id="11373-118">Explanation</span></span>  
 <span data-ttu-id="11373-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange EDIFACT sortant en raison des erreurs mentionnées pour le document informatisé.</span><span class="sxs-lookup"><span data-stu-id="11373-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified transaction set.</span></span> <span data-ttu-id="11373-120">Notez que le document informatisé ne fait pas partie d'un groupe dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="11373-120">Note that the transaction set is not in a group in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="11373-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="11373-121">User Action</span></span>  
 <span data-ttu-id="11373-122">Pour résoudre cette erreur, utilisez les informations dans le message d’erreur pour identifier l’erreur dans le document informatisé et déterminer la résolution du problème.</span><span class="sxs-lookup"><span data-stu-id="11373-122">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution.</span></span>