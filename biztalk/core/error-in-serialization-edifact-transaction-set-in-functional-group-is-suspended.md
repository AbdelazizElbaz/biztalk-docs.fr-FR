---
title: "Erreur lors de la sérialisation. Le document informatisé Edifact contenu dans le groupe fonctionnel est interrompu avec les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24b76086-334b-45fb-85f8-82e3335daac4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb09bfecc2efc5e6878b7cc3d0149f2b56c07b68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-transaction-set-contained-in-functional-group-is-being-suspended-with-following-errors"></a><span data-ttu-id="4b7be-103">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="4b7be-103">Error encountered during serialization.</span></span> <span data-ttu-id="4b7be-104">Le document informatisé EDIFACT contenu dans le groupe fonctionnel est en cours d'interruption avec les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="4b7be-104">The Edifact transaction set contained in functional group is being suspended with following errors</span></span>
## <a name="details"></a><span data-ttu-id="4b7be-105">Détails</span><span class="sxs-lookup"><span data-stu-id="4b7be-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b7be-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4b7be-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4b7be-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4b7be-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4b7be-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4b7be-108">Event ID</span></span>|-|  
|<span data-ttu-id="4b7be-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4b7be-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4b7be-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="4b7be-110"> EDI</span></span>|  
|<span data-ttu-id="4b7be-111">Composant</span><span class="sxs-lookup"><span data-stu-id="4b7be-111">Component</span></span>|<span data-ttu-id="4b7be-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="4b7be-112">EDI Engine</span></span>|  
|<span data-ttu-id="4b7be-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4b7be-113">Symbolic Name</span></span>|<span data-ttu-id="4b7be-114">EfactTransactionSetSendError</span><span class="sxs-lookup"><span data-stu-id="4b7be-114">EfactTransactionSetSendError</span></span>|  
|<span data-ttu-id="4b7be-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4b7be-115">Message Text</span></span>|<span data-ttu-id="4b7be-116">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="4b7be-116">Error encountered during serialization.</span></span> <span data-ttu-id="4b7be-117">Le document informatisé avec l’id de groupe fonctionnel avec l’id « {{1} », ' {0}' dans l’échange avec l’id « {{2} », avec l’expéditeur id '{3}', id de destinataire '\{4\' est interrompu avec les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b7be-117">The Edifact transaction set with id '{0}' contained in functional group with id '{1}', in interchange with id '{2}', with sender id '{3}', receiver id '{4}' is being suspended with following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4b7be-118">Explication</span><span class="sxs-lookup"><span data-stu-id="4b7be-118">Explanation</span></span>  
 <span data-ttu-id="4b7be-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange EDIFACT sortant en raison des erreurs mentionnées pour le document informatisé.</span><span class="sxs-lookup"><span data-stu-id="4b7be-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing EDIFACT interchange because of the stated errors with the identified transaction set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4b7be-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4b7be-120">User Action</span></span>  
 <span data-ttu-id="4b7be-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le document informatisé et déterminer une méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="4b7be-121">To resolve this error, use the information in the error message to identify the error in the transaction set and then determine the problem resolution in the product help.</span></span>