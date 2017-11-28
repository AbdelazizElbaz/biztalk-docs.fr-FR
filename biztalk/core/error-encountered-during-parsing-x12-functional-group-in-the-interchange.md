---
title: "Erreur rencontrée lors de l'analyse. Le X12 groupe fonctionnel dans l’échange comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2229c83-89bd-491f-9504-4afbf0084297
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4e519e8f89f00574ad2b51c1f9884889077c902
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-parsing-the-x12-functional-group-in-the-interchange-had-the-following-errors"></a><span data-ttu-id="5ed8c-103">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="5ed8c-103">Error encountered during parsing.</span></span> <span data-ttu-id="5ed8c-104">Le groupe fonctionnel X12 dans l'échange comporte les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="5ed8c-104">The X12 functional group in the interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="5ed8c-105">Détails</span><span class="sxs-lookup"><span data-stu-id="5ed8c-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ed8c-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5ed8c-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5ed8c-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5ed8c-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5ed8c-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5ed8c-108">Event ID</span></span>|-|  
|<span data-ttu-id="5ed8c-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5ed8c-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5ed8c-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="5ed8c-110"> EDI</span></span>|  
|<span data-ttu-id="5ed8c-111">Composant</span><span class="sxs-lookup"><span data-stu-id="5ed8c-111">Component</span></span>|<span data-ttu-id="5ed8c-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="5ed8c-112">EDI Engine</span></span>|  
|<span data-ttu-id="5ed8c-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5ed8c-113">Symbolic Name</span></span>|<span data-ttu-id="5ed8c-114">X12FunctionalGroupReceiveError</span><span class="sxs-lookup"><span data-stu-id="5ed8c-114">X12FunctionalGroupReceiveError</span></span>|  
|<span data-ttu-id="5ed8c-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5ed8c-115">Message Text</span></span>|<span data-ttu-id="5ed8c-116">Erreur rencontrée lors de l'analyse.</span><span class="sxs-lookup"><span data-stu-id="5ed8c-116">Error encountered during parsing.</span></span> <span data-ttu-id="5ed8c-117">Le X12 fonctionnelle de groupe avec l’id '{0}', dans l’échange possédant l’id « {{1}', id d’expéditeur « {{2} », récepteur id '{3}' comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ed8c-117">The X12 functional group with id '{0}', in interchange with id '{1}', with sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5ed8c-118">Explication</span><span class="sxs-lookup"><span data-stu-id="5ed8c-118">Explanation</span></span>  
 <span data-ttu-id="5ed8c-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception EDI a rencontré une erreur lors de l'analyse d'un échange X12 entrant en raison des erreurs mentionnées pour le groupe fonctionnel identifié.</span><span class="sxs-lookup"><span data-stu-id="5ed8c-119">This Error/Warning/Information event indicates that the EDI receive pipeline encountered an error when parsing an incoming X12 interchange because of the stated errors with the identified functional group.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5ed8c-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5ed8c-120">User Action</span></span>  
 <span data-ttu-id="5ed8c-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier l'erreur dans le groupe et déterminer la méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="5ed8c-121">To resolve this error, use the information in the error message to identify the error in the group and then determine the problem resolution in the product help.</span></span>