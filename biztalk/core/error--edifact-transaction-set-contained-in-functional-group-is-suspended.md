---
title: "Erreur rencontrée lors de l'analyse. Le document informatisé Edifact contenu dans le groupe fonctionnel est interrompu avec les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986a7220-d35a-4047-8996-7d44c7d2b823
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70428ae8f430ea5ccb9ff13e068716cb35555f69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="659fe-103">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="659fe-103">Error encountered during parsing.</span></span> <span data-ttu-id="659fe-104">Le document informatisé EDIFACT contenu dans le groupe fonctionnel est en cours d'interruption avec les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="659fe-104">The Edifact transaction set contained in functional group is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="659fe-105">Détails</span><span class="sxs-lookup"><span data-stu-id="659fe-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="659fe-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="659fe-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="659fe-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="659fe-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="659fe-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="659fe-108">Event ID</span></span>|-|  
|<span data-ttu-id="659fe-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="659fe-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="659fe-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="659fe-110"> EDI</span></span>|  
|<span data-ttu-id="659fe-111">Composant</span><span class="sxs-lookup"><span data-stu-id="659fe-111">Component</span></span>|<span data-ttu-id="659fe-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="659fe-112">EDI Engine</span></span>|  
|<span data-ttu-id="659fe-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="659fe-113">Symbolic Name</span></span>|<span data-ttu-id="659fe-114">EfactTransactionSetReceiveError</span><span class="sxs-lookup"><span data-stu-id="659fe-114">EfactTransactionSetReceiveError</span></span>|  
|<span data-ttu-id="659fe-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="659fe-115">Message Text</span></span>|<span data-ttu-id="659fe-116">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="659fe-116">Error encountered during parsing.</span></span> <span data-ttu-id="659fe-117">Le document informatisé avec l’id de groupe fonctionnel avec l’id « {{1} », ' {0}' dans l’échange avec l’id « {{2} », avec l’expéditeur id '{3}', id de destinataire '\{4\' est interrompu avec les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="659fe-117">The Edifact transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="659fe-118">Explication</span><span class="sxs-lookup"><span data-stu-id="659fe-118">Explanation</span></span>  
 <span data-ttu-id="659fe-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI n'a pas pu analyser un échange EDIFACT entrant avec un groupe en raison des erreurs mentionnées pour le document informatisé identifié.</span><span class="sxs-lookup"><span data-stu-id="659fe-119">This Error/Warning/Information event indicates that the EDI receive pipeline could not parse an incoming EDIFACT interchange with a group because of the stated errors with the identified transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="659fe-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="659fe-120">User Action</span></span>  
 <span data-ttu-id="659fe-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le document informatisé et déterminer une méthode de résolution dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="659fe-121">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the documentation.</span></span>