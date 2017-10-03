---
title: "Erreur lors de la sérialisation. Le X12 échange comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ca3314-6c66-4400-816a-f9c7c7915122
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b27c08632901fed3d0fc9a9d43646034b044c626
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-encountered-during-serialization-the-x12-interchange-had-the-following-errors"></a><span data-ttu-id="dd821-103">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="dd821-103">Error encountered during serialization.</span></span> <span data-ttu-id="dd821-104">L'échange X12 comportait les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="dd821-104">The X12 interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="dd821-105">Détails</span><span class="sxs-lookup"><span data-stu-id="dd821-105">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dd821-106">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="dd821-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="dd821-107">Version du produit</span><span class="sxs-lookup"><span data-stu-id="dd821-107">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="dd821-108">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="dd821-108">Event ID</span></span>|-|  
|<span data-ttu-id="dd821-109">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="dd821-109">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dd821-110"> EDI</span><span class="sxs-lookup"><span data-stu-id="dd821-110"> EDI</span></span>|  
|<span data-ttu-id="dd821-111">Composant</span><span class="sxs-lookup"><span data-stu-id="dd821-111">Component</span></span>|<span data-ttu-id="dd821-112">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="dd821-112">EDI Engine</span></span>|  
|<span data-ttu-id="dd821-113">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="dd821-113">Symbolic Name</span></span>|<span data-ttu-id="dd821-114">X12InterchangeSendError</span><span class="sxs-lookup"><span data-stu-id="dd821-114">X12InterchangeSendError</span></span>|  
|<span data-ttu-id="dd821-115">Texte du message</span><span class="sxs-lookup"><span data-stu-id="dd821-115">Message Text</span></span>|<span data-ttu-id="dd821-116">Erreur lors de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="dd821-116">Error encountered during serialization.</span></span> <span data-ttu-id="dd821-117">Le X12 échange avec l’id '{0}' avec l’expéditeur id « {{1}', id de récepteur « {{2} » comporte les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="dd821-117">The X12 interchange with id '{0}', with sender id '{1}', receiver id '{2}' had the following errors</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dd821-118">Explication</span><span class="sxs-lookup"><span data-stu-id="dd821-118">Explanation</span></span>  
 <span data-ttu-id="dd821-119">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi EDI a rencontré une erreur lors de la sérialisation d'un échange X12 sortant en raison des erreurs mentionnées.</span><span class="sxs-lookup"><span data-stu-id="dd821-119">This Error/Warning/Information event indicates that the EDI send pipeline encountered an error when serializing an outgoing X12 interchange because of the stated errors.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dd821-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="dd821-120">User Action</span></span>  
 <span data-ttu-id="dd821-121">Pour résoudre cette erreur, exploitez les informations du message d'erreur pour identifier celle-ci dans l'échange et déterminer la méthode de résolution dans l'aide du produit.</span><span class="sxs-lookup"><span data-stu-id="dd821-121">To resolve this error, use the information in the error message to identify the error in the interchange and then determine the problem resolution in the product help.</span></span>