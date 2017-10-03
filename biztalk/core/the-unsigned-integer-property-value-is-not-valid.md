---
title: "La valeur de la propriété unsigned integer n’est pas valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63b0398f-7848-4971-8c08-95923d80cbe3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e5f6ac36eb2b7322a2252f4759539d721dc2e63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-unsigned-integer-property-value-is-not-valid"></a><span data-ttu-id="eac5a-102">La valeur de la propriété unsigned integer n'est pas valide</span><span class="sxs-lookup"><span data-stu-id="eac5a-102">The unsigned integer property value is not valid</span></span>
## <a name="details"></a><span data-ttu-id="eac5a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="eac5a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eac5a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="eac5a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="eac5a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="eac5a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="eac5a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="eac5a-106">Event ID</span></span>|-|  
|<span data-ttu-id="eac5a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="eac5a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="eac5a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="eac5a-108"> EDI</span></span>|  
|<span data-ttu-id="eac5a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="eac5a-109">Component</span></span>|<span data-ttu-id="eac5a-110">Moteur EDI</span><span class="sxs-lookup"><span data-stu-id="eac5a-110">EDI Engine</span></span>|  
|<span data-ttu-id="eac5a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="eac5a-111">Symbolic Name</span></span>|<span data-ttu-id="eac5a-112">Err_InvalidUnsignedInteger</span><span class="sxs-lookup"><span data-stu-id="eac5a-112">Err_InvalidUnsignedInteger</span></span>|  
|<span data-ttu-id="eac5a-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="eac5a-113">Message Text</span></span>|<span data-ttu-id="eac5a-114">La valeur de la propriété unsigned integer n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="eac5a-114">The unsigned integer property value is not valid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="eac5a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="eac5a-115">Explanation</span></span>  
 <span data-ttu-id="eac5a-116">Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas réussi à comparer une propriété de contexte lors de la prise de décision concernant le traitement d'un message par lot.</span><span class="sxs-lookup"><span data-stu-id="eac5a-116">This Error/Warning/Information event indicates BizTalk Server was unable to compare a context property while trying to decide whether to Batch a message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="eac5a-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="eac5a-117">User Action</span></span>  
 <span data-ttu-id="eac5a-118">Pour résoudre cette erreur, assurez-vous que le filtre fourni dans les lots actifs ne spécifie pas de valeur non valide pour une propriété de contexte dont le type d'entier non signé est XSD.</span><span class="sxs-lookup"><span data-stu-id="eac5a-118">To resolve this error, ensure that the filter provided in Active batches doesn’t specify a context property which has an XSD type of unsigned integer with an invalid value.</span></span>