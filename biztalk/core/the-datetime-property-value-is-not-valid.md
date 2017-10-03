---
title: "La valeur de propriété datetime n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0dc527e-82d5-40dc-941e-f2e056163017
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f6f784bc04e243de3bbb3cfb1c1acc760c35015
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-datetime-property-value-is-not-valid"></a><span data-ttu-id="9d0e0-102">La valeur de la propriété datetime n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="9d0e0-102">The datetime property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="9d0e0-103">Détails</span><span class="sxs-lookup"><span data-stu-id="9d0e0-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9d0e0-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="9d0e0-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="9d0e0-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="9d0e0-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="9d0e0-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="9d0e0-106">Event ID</span></span>|-|  
|<span data-ttu-id="9d0e0-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="9d0e0-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9d0e0-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="9d0e0-108"> EDI</span></span>|  
|<span data-ttu-id="9d0e0-109">Composant</span><span class="sxs-lookup"><span data-stu-id="9d0e0-109">Component</span></span>|<span data-ttu-id="9d0e0-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="9d0e0-110">EDI Engine</span></span>|  
|<span data-ttu-id="9d0e0-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="9d0e0-111">Symbolic Name</span></span>|<span data-ttu-id="9d0e0-112">Err_InvalidDateTime</span><span class="sxs-lookup"><span data-stu-id="9d0e0-112">Err_InvalidDateTime</span></span>|  
|<span data-ttu-id="9d0e0-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="9d0e0-113">Message Text</span></span>|<span data-ttu-id="9d0e0-114">La valeur de la propriété datetime n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="9d0e0-114">The datetime property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9d0e0-115">Explication</span><span class="sxs-lookup"><span data-stu-id="9d0e0-115">Explanation</span></span>  
 <span data-ttu-id="9d0e0-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à comparer une propriété de contexte lors de la prise de décision concernant le traitement d'un message par lot.</span><span class="sxs-lookup"><span data-stu-id="9d0e0-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9d0e0-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="9d0e0-117">User Action</span></span>  
 <span data-ttu-id="9d0e0-118">Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas une propriété de contexte associée à un type de date XSD et dont la valeur de date est non valide.</span><span class="sxs-lookup"><span data-stu-id="9d0e0-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of date and the value is invalid date.</span></span>