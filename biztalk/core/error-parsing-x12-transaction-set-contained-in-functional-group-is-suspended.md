---
title: "Erreur rencontrée lors de l'analyse. Le document informatisé contenue dans le groupe fonctionnel est interrompu avec les erreurs suivantes de X12 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51c6fa8e-d81c-4ccb-93b4-852ab184c4e9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6aa837fb86b34cfdd696874dd02ba26635bf7356
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-x12-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="5f14b-103">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="5f14b-103">Error encountered during parsing.</span></span> <span data-ttu-id="5f14b-104">Le document informatisé X12 contenu dans le groupe fonctionnel est interrompu avec les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f14b-104">The X12 transaction set contained in functional group is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="5f14b-105">Détails</span><span class="sxs-lookup"><span data-stu-id="5f14b-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f14b-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5f14b-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5f14b-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5f14b-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5f14b-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f14b-108">Event ID</span></span>|-|  
|<span data-ttu-id="5f14b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5f14b-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5f14b-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="5f14b-110"> EDI</span></span>|  
|<span data-ttu-id="5f14b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5f14b-111">Component</span></span>|<span data-ttu-id="5f14b-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5f14b-112">EDI Engine</span></span>|  
|<span data-ttu-id="5f14b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5f14b-113">Symbolic Name</span></span>|<span data-ttu-id="5f14b-114">X12TransactionSetReceiveError</span><span class="sxs-lookup"><span data-stu-id="5f14b-114">X12TransactionSetReceiveError</span></span>|  
|<span data-ttu-id="5f14b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5f14b-115">Message Text</span></span>|<span data-ttu-id="5f14b-116">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="5f14b-116">Error encountered during parsing.</span></span> <span data-ttu-id="5f14b-117">Le X12 document informatisé avec l’id '{0}' contenue dans groupe fonctionnel avec l’id « {{1} », dans l’échange avec l’id « {{2} », avec l’expéditeur id '{3}', id de destinataire '\{4\' est interrompu avec les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f14b-117">The X12 transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5f14b-118">Explication</span><span class="sxs-lookup"><span data-stu-id="5f14b-118">Explanation</span></span>  
 <span data-ttu-id="5f14b-119">Cet événement de type erreur/avertissement/information indique que le pipeline de réception EDI a rencontré un problème lors de l'analyse d'un échange X12 entrant en raison des erreurs indiquées au niveau du document informatisé identifié.</span><span class="sxs-lookup"><span data-stu-id="5f14b-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming X12 interchange because of the stated errors with the identified transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5f14b-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5f14b-120">User Action</span></span>  
 <span data-ttu-id="5f14b-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le document informatisé et déterminer une méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="5f14b-121">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>