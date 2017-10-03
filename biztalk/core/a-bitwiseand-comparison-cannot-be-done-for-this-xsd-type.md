---
title: "Ne peut pas être effectuée une comparaison BitwiseAnd pour ce type XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bc2351-c002-458a-9d35-5fdcc91c6a0e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c0f3aa2b3ae7c60f3c104daaa885ab7ae8cc7ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a-bitwiseand-comparison-cannot-be-done-for-this-xsd-type"></a><span data-ttu-id="a297d-102">Impossible d'effectuer une comparaison BitwiseAnd pour ce type  XSD</span><span class="sxs-lookup"><span data-stu-id="a297d-102">A BitwiseAnd comparison cannot be done for this XSD type</span></span>
## <a name="details"></a><span data-ttu-id="a297d-103">Détails</span><span class="sxs-lookup"><span data-stu-id="a297d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a297d-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="a297d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a297d-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="a297d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a297d-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="a297d-106">Event ID</span></span>|-|  
|<span data-ttu-id="a297d-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="a297d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a297d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="a297d-108"> EDI</span></span>|  
|<span data-ttu-id="a297d-109">Composant</span><span class="sxs-lookup"><span data-stu-id="a297d-109">Component</span></span>|<span data-ttu-id="a297d-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="a297d-110">EDI Engine</span></span>|  
|<span data-ttu-id="a297d-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="a297d-111">Symbolic Name</span></span>|<span data-ttu-id="a297d-112">Err_InvalidBitwiseComparision</span><span class="sxs-lookup"><span data-stu-id="a297d-112">Err_InvalidBitwiseComparision</span></span>|  
|<span data-ttu-id="a297d-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="a297d-113">Message Text</span></span>|<span data-ttu-id="a297d-114">Impossible d'effectuer une comparaison BitwiseAnd pour ce type XSD.</span><span class="sxs-lookup"><span data-stu-id="a297d-114">A BitwiseAnd comparison cannot be done for this XSD type.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a297d-115">Explication</span><span class="sxs-lookup"><span data-stu-id="a297d-115">Explanation</span></span>  
 <span data-ttu-id="a297d-116">Cet événement d’erreur/avertissement/Information indique que BizTalk Server n’a pas pu comparer une propriété de contexte lors de la tentative de décider à un message du lot.</span><span class="sxs-lookup"><span data-stu-id="a297d-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a297d-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="a297d-117">User Action</span></span>  
 <span data-ttu-id="a297d-118">Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas de propriété de contexte dont le type CSD ne peut pas faire l'objet d'une comparaison au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="a297d-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an CSD type that can’t be bitwise compared.</span></span>