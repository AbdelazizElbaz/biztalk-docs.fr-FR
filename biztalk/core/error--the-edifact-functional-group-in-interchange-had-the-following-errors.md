---
title: "Erreur rencontrée lors de l'analyse. Le groupe fonctionnel Edifact dans l’échange comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77ca78b3-8a1f-4da5-9c15-524ab6802457
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6af00ae6500419fcb3ed687da89415e7594f1adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-edifact-functional-group-in-interchange-had-the-following-errors"></a><span data-ttu-id="2e652-103">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="2e652-103">Error encountered during parsing.</span></span> <span data-ttu-id="2e652-104">Le groupe fonctionnel EDIFACT dans l'échange comporte les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="2e652-104">The Edifact functional group in interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="2e652-105">Détails</span><span class="sxs-lookup"><span data-stu-id="2e652-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2e652-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="2e652-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="2e652-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="2e652-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="2e652-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="2e652-108">Event ID</span></span>|-|  
|<span data-ttu-id="2e652-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="2e652-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2e652-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="2e652-110"> EDI</span></span>|  
|<span data-ttu-id="2e652-111">Composant</span><span class="sxs-lookup"><span data-stu-id="2e652-111">Component</span></span>|<span data-ttu-id="2e652-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="2e652-112">EDI Engine</span></span>|  
|<span data-ttu-id="2e652-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="2e652-113">Symbolic Name</span></span>|<span data-ttu-id="2e652-114">EfactFunctionalGroupReceiveError</span><span class="sxs-lookup"><span data-stu-id="2e652-114">EfactFunctionalGroupReceiveError</span></span>|  
|<span data-ttu-id="2e652-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="2e652-115">Message Text</span></span>|<span data-ttu-id="2e652-116">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="2e652-116">Error encountered during parsing.</span></span> <span data-ttu-id="2e652-117">Le groupe fonctionnel Edifact avec l’id '{0}' dans l’échange possédant l’id « {{1}', id d’expéditeur « {{2} », id de destinataire '{3}' comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e652-117">The Edifact functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2e652-118">Explication</span><span class="sxs-lookup"><span data-stu-id="2e652-118">Explanation</span></span>  
 <span data-ttu-id="2e652-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors de l'analyse d'un échange EDIFACT entrant en raison des erreurs mentionnées pour le groupe fonctionnel identifié.</span><span class="sxs-lookup"><span data-stu-id="2e652-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming EDIFACT interchange because of the stated errors with the identified functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2e652-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="2e652-120">User Action</span></span>  
 <span data-ttu-id="2e652-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le groupe et déterminer la méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="2e652-121">To resolve this error, use the information in the error message to identify the error in the group and then determine the problem resolution in the product help.</span></span>