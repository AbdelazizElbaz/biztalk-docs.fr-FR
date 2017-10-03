---
title: "La valeur de propriété unsignedShort n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31600ed6-20bc-4382-9eb3-4d6fa9646411
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a62a37bc136f317e05db0e66cf3c2c86af97df41
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-unsigned-short-property-value-is-not-valid"></a><span data-ttu-id="424a2-102">La valeur de propriété unsignedShort n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="424a2-102">The unsigned Short property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="424a2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="424a2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="424a2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="424a2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="424a2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="424a2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="424a2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="424a2-106">Event ID</span></span>|-|  
|<span data-ttu-id="424a2-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="424a2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="424a2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="424a2-108"> EDI</span></span>|  
|<span data-ttu-id="424a2-109">Composant</span><span class="sxs-lookup"><span data-stu-id="424a2-109">Component</span></span>|<span data-ttu-id="424a2-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="424a2-110">EDI Engine</span></span>|  
|<span data-ttu-id="424a2-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="424a2-111">Symbolic Name</span></span>|<span data-ttu-id="424a2-112">Err_InvalidUnsignedShort</span><span class="sxs-lookup"><span data-stu-id="424a2-112">Err_InvalidUnsignedShort</span></span>|  
|<span data-ttu-id="424a2-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="424a2-113">Message Text</span></span>|<span data-ttu-id="424a2-114">La valeur de la propriété unsignedShort n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="424a2-114">The unsigned Short property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="424a2-115">Explication</span><span class="sxs-lookup"><span data-stu-id="424a2-115">Explanation</span></span>  
 <span data-ttu-id="424a2-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à comparer une propriété de contexte lors de la prise de décision concernant le traitement d'un message par lot.</span><span class="sxs-lookup"><span data-stu-id="424a2-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="424a2-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="424a2-117">User Action</span></span>  
 <span data-ttu-id="424a2-118">Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas une propriété de contexte dont le type XSD est unsignedShort avec une valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="424a2-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of unsigned Short with an invalid value.</span></span>