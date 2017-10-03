---
title: "La comparaison peut être uniquement Equals, NotEquals et Exists | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aad902a2-d0dc-4d91-87a7-a6305e2f40e0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: add062aebdbabe7d5965b46c7342595f96a7b8dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-comparison-can-only-be-equals-notequals-and-exists"></a><span data-ttu-id="8fc55-102">La comparaison peut être uniquement Equals, NotEquals et Exists</span><span class="sxs-lookup"><span data-stu-id="8fc55-102">The Comparison can only be Equals, NotEquals and Exists</span></span>
## <a name="details"></a><span data-ttu-id="8fc55-103">Détails</span><span class="sxs-lookup"><span data-stu-id="8fc55-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8fc55-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="8fc55-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="8fc55-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="8fc55-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="8fc55-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="8fc55-106">Event ID</span></span>|-|  
|<span data-ttu-id="8fc55-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="8fc55-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8fc55-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="8fc55-108"> EDI</span></span>|  
|<span data-ttu-id="8fc55-109">Composant</span><span class="sxs-lookup"><span data-stu-id="8fc55-109">Component</span></span>|<span data-ttu-id="8fc55-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="8fc55-110">EDI Engine</span></span>|  
|<span data-ttu-id="8fc55-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="8fc55-111">Symbolic Name</span></span>|<span data-ttu-id="8fc55-112">Err_InvalidComparision</span><span class="sxs-lookup"><span data-stu-id="8fc55-112">Err_InvalidComparision</span></span>|  
|<span data-ttu-id="8fc55-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="8fc55-113">Message Text</span></span>|<span data-ttu-id="8fc55-114">La comparaison peut être uniquement Equals, NotEquals et Exists.</span><span class="sxs-lookup"><span data-stu-id="8fc55-114">The Comparison can only be Equals, NotEquals and Exists.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8fc55-115">Explication</span><span class="sxs-lookup"><span data-stu-id="8fc55-115">Explanation</span></span>  
 <span data-ttu-id="8fc55-116">Cet événement d’erreur/avertissement/Information indique que BizTalk Server n’a pas pu comparer une propriété de contexte lors de la tentative de décider à un message du lot.</span><span class="sxs-lookup"><span data-stu-id="8fc55-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8fc55-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="8fc55-117">User Action</span></span>  
 <span data-ttu-id="8fc55-118">Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas un opérateur autre que Equals, NotEquals et Exists pour les types XSD qui ne prennent pas en charge les autres opérations.</span><span class="sxs-lookup"><span data-stu-id="8fc55-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify an operator  other than Equals, NotEquals and Exists for XSD types that don’t support other operations.</span></span>