---
title: "Erreur lors de la sérialisation. Le X12 groupe fonctionnel comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dad987c3-92f3-4a6b-ba1a-b60f6ea2fbe4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27c6b74d713f0d182a07cc6a509cd7d06fc34b82
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-x12-functional-group-had-the-following-errors"></a><span data-ttu-id="2ae62-103">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="2ae62-103">Error encountered during serialization.</span></span> <span data-ttu-id="2ae62-104">Le groupe fonctionnel X12 comporte les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="2ae62-104">The X12 functional group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="2ae62-105">Détails</span><span class="sxs-lookup"><span data-stu-id="2ae62-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ae62-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2ae62-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2ae62-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2ae62-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2ae62-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2ae62-108">Event ID</span></span>|-|  
|<span data-ttu-id="2ae62-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2ae62-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2ae62-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="2ae62-110"> EDI</span></span>|  
|<span data-ttu-id="2ae62-111">Composant</span><span class="sxs-lookup"><span data-stu-id="2ae62-111">Component</span></span>|<span data-ttu-id="2ae62-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="2ae62-112">EDI Engine</span></span>|  
|<span data-ttu-id="2ae62-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2ae62-113">Symbolic Name</span></span>|<span data-ttu-id="2ae62-114">X12FunctionalGroupSendError</span><span class="sxs-lookup"><span data-stu-id="2ae62-114">X12FunctionalGroupSendError</span></span>|  
|<span data-ttu-id="2ae62-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2ae62-115">Message Text</span></span>|<span data-ttu-id="2ae62-116">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="2ae62-116">Error encountered during serialization.</span></span> <span data-ttu-id="2ae62-117">Le X12 fonctionnelle de groupe avec l’id '{0}', dans l’échange possédant l’id « {{1}', id d’expéditeur « {{2} », récepteur id '{3}' comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ae62-117">The X12 functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2ae62-118">Explication</span><span class="sxs-lookup"><span data-stu-id="2ae62-118">Explanation</span></span>  
 <span data-ttu-id="2ae62-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange X12 sortant en raison des erreurs mentionnées pour le groupe fonctionnel identifié.</span><span class="sxs-lookup"><span data-stu-id="2ae62-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors with the identified functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2ae62-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2ae62-120">User Action</span></span>  
 <span data-ttu-id="2ae62-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci dans le groupe fonctionnel et déterminer la méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="2ae62-121">To resolve this error, use the information in the error message to identify the error in the functional group and then determine the problem resolution in the product help.</span></span>