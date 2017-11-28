---
title: "Erreur rencontrée lors de l'analyse. Le document informatisé Edifact contenu dans l’échange (sans groupe) est interrompu avec les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 901fef68-4649-480a-997c-b061d7d069d6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dc5633917c708f457f11fc824997fa7eb6d4c59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-interchange-without-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="fa87e-103">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="fa87e-103">Error encountered during parsing.</span></span> <span data-ttu-id="fa87e-104">Le document informatisé EDIFACT contenu dans l'échange (sans groupe) est en cours d'interruption avec les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="fa87e-104">The Edifact transaction set contained in interchange (without group) is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="fa87e-105">Détails</span><span class="sxs-lookup"><span data-stu-id="fa87e-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fa87e-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="fa87e-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="fa87e-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="fa87e-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="fa87e-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="fa87e-108">Event ID</span></span>|-|  
|<span data-ttu-id="fa87e-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="fa87e-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="fa87e-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="fa87e-110"> EDI</span></span>|  
|<span data-ttu-id="fa87e-111">Composant</span><span class="sxs-lookup"><span data-stu-id="fa87e-111">Component</span></span>|<span data-ttu-id="fa87e-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="fa87e-112">EDI Engine</span></span>|  
|<span data-ttu-id="fa87e-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="fa87e-113">Symbolic Name</span></span>|<span data-ttu-id="fa87e-114">EfactTransactionSetReceiveErrorWithoutGroup</span><span class="sxs-lookup"><span data-stu-id="fa87e-114">EfactTransactionSetReceiveErrorWithoutGroup</span></span>|  
|<span data-ttu-id="fa87e-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="fa87e-115">Message Text</span></span>|<span data-ttu-id="fa87e-116">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="fa87e-116">Error encountered during parsing.</span></span> <span data-ttu-id="fa87e-117">Le document informatisé avec l’id '{0}' contenu dans l’échange (sans groupe) avec l’id « {{1}', id d’expéditeur « {{2} », id de destinataire '{3}' est interrompu avec les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa87e-117">The Edifact transaction set with id '{0}' contained in interchange (without group) with id '{1}', with sender id '{2}', receiver id '{3}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="fa87e-118">Explication</span><span class="sxs-lookup"><span data-stu-id="fa87e-118">Explanation</span></span>  
 <span data-ttu-id="fa87e-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors de l'analyse d'un échange EDIFACT entrant dans un groupe en raison des erreurs mentionnées pour le document informatisé identifié dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="fa87e-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange without a group because of the stated errors with the identified transaction set in the interchange.</span></span> <span data-ttu-id="fa87e-120">Notez que le document informatisé ne fait pas partie d'un groupe dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="fa87e-120">Note that the transaction set is not in a group in the interchange.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="fa87e-121">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="fa87e-121">User Action</span></span>  
 <span data-ttu-id="fa87e-122">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le document informatisé et déterminer une méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="fa87e-122">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>