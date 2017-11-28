---
title: "Erreur lors de la sérialisation. Le groupe fonctionnel Edifact comporte les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed81bc79-d99c-4305-805f-ab38eae91ea0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a8166e5a66038d4cbda3a6fcb9597c7827d1eeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-edifact-functional-group-had-the-following-errors"></a><span data-ttu-id="3877b-103">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="3877b-103">Error encountered during serialization.</span></span> <span data-ttu-id="3877b-104">Le groupe fonctionnel Edifact comporte les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="3877b-104">The Edifact functional group had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="3877b-105">Détails</span><span class="sxs-lookup"><span data-stu-id="3877b-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3877b-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3877b-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3877b-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3877b-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3877b-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3877b-108">Event ID</span></span>|-|  
|<span data-ttu-id="3877b-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3877b-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3877b-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="3877b-110"> EDI</span></span>|  
|<span data-ttu-id="3877b-111">Composant</span><span class="sxs-lookup"><span data-stu-id="3877b-111">Component</span></span>|<span data-ttu-id="3877b-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="3877b-112">EDI Engine</span></span>|  
|<span data-ttu-id="3877b-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3877b-113">Symbolic Name</span></span>|<span data-ttu-id="3877b-114">EfactFunctionalGroupSendError</span><span class="sxs-lookup"><span data-stu-id="3877b-114">EfactFunctionalGroupSendError</span></span>|  
|<span data-ttu-id="3877b-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3877b-115">Message Text</span></span>|<span data-ttu-id="3877b-116">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="3877b-116">Error encountered during serialization.</span></span> <span data-ttu-id="3877b-117">Le groupe fonctionnel Edifact avec l’id '{0}' dans l’échange possédant l’id « {{1}', id d’expéditeur « {{2} », id de destinataire '{3}' comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="3877b-117">The Edifact functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3877b-118">Explication</span><span class="sxs-lookup"><span data-stu-id="3877b-118">Explanation</span></span>  
 <span data-ttu-id="3877b-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un groupe fonctionnel au sein de l'échange EDIFACT sortant en raison des erreurs mentionnées pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="3877b-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing a functional group within an outgoing EDIFACT interchange because of the stated errors with the group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3877b-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3877b-120">User Action</span></span>  
 <span data-ttu-id="3877b-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le groupe fonctionnel et déterminer une méthode de résolution dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="3877b-121">To resolve this error, use the information in the error message to identify the error in the functional group and then determine the problem resolution in the documentation.</span></span>