---
title: "La valeur de propriété entier n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31d4e9a7-4336-40f1-997a-9f79d86b26d2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acbb350d9dd8fe77e42bb7e8b3cdf4617c87a2f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-integer-property-value-is-not-valid"></a><span data-ttu-id="eec4d-102">La valeur de propriété entier n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="eec4d-102">The integer property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="eec4d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="eec4d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eec4d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="eec4d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="eec4d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="eec4d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="eec4d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="eec4d-106">Event ID</span></span>|-|  
|<span data-ttu-id="eec4d-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="eec4d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eec4d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="eec4d-108"> EDI</span></span>|  
|<span data-ttu-id="eec4d-109">Composant</span><span class="sxs-lookup"><span data-stu-id="eec4d-109">Component</span></span>|<span data-ttu-id="eec4d-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="eec4d-110">EDI Engine</span></span>|  
|<span data-ttu-id="eec4d-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="eec4d-111">Symbolic Name</span></span>|<span data-ttu-id="eec4d-112">Err_InvalidInteger</span><span class="sxs-lookup"><span data-stu-id="eec4d-112">Err_InvalidInteger</span></span>|  
|<span data-ttu-id="eec4d-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="eec4d-113">Message Text</span></span>|<span data-ttu-id="eec4d-114">La valeur de la propriété integer n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="eec4d-114">The integer property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eec4d-115">Explication</span><span class="sxs-lookup"><span data-stu-id="eec4d-115">Explanation</span></span>  
 <span data-ttu-id="eec4d-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à comparer une propriété de contexte lors de la prise de décision concernant le traitement d'un message par lot.</span><span class="sxs-lookup"><span data-stu-id="eec4d-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eec4d-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="eec4d-117">User Action</span></span>  
 <span data-ttu-id="eec4d-118">Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas une propriété de contexte dont le type d'entier est XSD avec une valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="eec4d-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of integer with an invalid value.</span></span>