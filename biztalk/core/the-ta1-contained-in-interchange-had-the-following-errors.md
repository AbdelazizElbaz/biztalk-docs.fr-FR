---
title: "Le TA1 contenu dans l’échange comportait les erreurs suivantes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2d63fe9-63ef-44b3-8cb9-45a7abf8d0e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03bd7486d25e2c94fc809e6dc50c43359c152b70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-ta1-contained-in-interchange-had-the-following-errors"></a><span data-ttu-id="f6c3e-102">Le TA1 contenu dans l'échange comportait les erreurs suivantes</span><span class="sxs-lookup"><span data-stu-id="f6c3e-102">The TA1 contained in interchange had the following errors</span></span>
## <a name="details"></a><span data-ttu-id="f6c3e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="f6c3e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f6c3e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="f6c3e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f6c3e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="f6c3e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f6c3e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f6c3e-106">Event ID</span></span>|-|  
|<span data-ttu-id="f6c3e-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="f6c3e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f6c3e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f6c3e-108"> EDI</span></span>|  
|<span data-ttu-id="f6c3e-109">Composant</span><span class="sxs-lookup"><span data-stu-id="f6c3e-109">Component</span></span>|<span data-ttu-id="f6c3e-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="f6c3e-110">EDI Engine</span></span>|  
|<span data-ttu-id="f6c3e-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="f6c3e-111">Symbolic Name</span></span>|<span data-ttu-id="f6c3e-112">X12TA1Error</span><span class="sxs-lookup"><span data-stu-id="f6c3e-112">X12TA1Error</span></span>|  
|<span data-ttu-id="f6c3e-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="f6c3e-113">Message Text</span></span>|<span data-ttu-id="f6c3e-114">Le {0} TA1 contenu dans l’échange avec l’id « {{1} », id d’expéditeur « {{2} », id de destinataire '{3}' comporte les erreurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f6c3e-114">The {0} TA1 contained in interchange with id '{1}', sender id '{2}', receiver id '{3}' had the following errors:</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f6c3e-115">Explication</span><span class="sxs-lookup"><span data-stu-id="f6c3e-115">Explanation</span></span>  
 <span data-ttu-id="f6c3e-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'accusé de réception TA1 entrant en raison de la condition d'erreur indiquée.</span><span class="sxs-lookup"><span data-stu-id="f6c3e-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming TA1 acknowledgment because of the indicated error condition.</span></span> <span data-ttu-id="f6c3e-117">Cela peut indiquer que l'accusé de réception n'est pas conforme au schéma TA1Schema.</span><span class="sxs-lookup"><span data-stu-id="f6c3e-117">This may indicate that the acknowledgment does not conform to the TA1Schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f6c3e-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f6c3e-118">User Action</span></span>  
 <span data-ttu-id="f6c3e-119">Pour résoudre cette erreur, demandez à l'expéditeur de résoudre le problème d'accusé de réception, de s'assurer que l'accusé de réception est conforme au schéma TA1Schema, puis de le renvoyer.</span><span class="sxs-lookup"><span data-stu-id="f6c3e-119">To resolve this error, have the sender of the acknowledgment resolve the issue with the acknowledgment, ensuring that the acknowledgment conforms to the TA1Schema, and then resend the acknowledgment.</span></span>