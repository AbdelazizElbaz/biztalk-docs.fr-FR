---
title: "Propriétés de la Date d’effet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- effective-dated items
- getHistoryItems parameter
- Effective Date
- EFFDT
- planned items, scheduling and tracking
ms.assetid: 0d9a153c-7ea5-41cf-9e4e-055e1c18f64b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f1c4cf3579a3381c846ddbb9896b2e5be26f6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="effective-date-properties"></a><span data-ttu-id="38822-102">Propriétés de la Date d’effet</span><span class="sxs-lookup"><span data-stu-id="38822-102">Effective Date Properties</span></span>
<span data-ttu-id="38822-103">PeopleSoft Enterprise permet de planifier et d'assurer le suivi d'éléments planifiés à l'aide d'une propriété spécifique nommée Date d'effet (abrégée par EFFDT).</span><span class="sxs-lookup"><span data-stu-id="38822-103">PeopleSoft Enterprise provides the ability to schedule and keep track of planned items by using a special property called Effective Date (abbreviated EFFDT).</span></span> <span data-ttu-id="38822-104">De tels éléments sont soit effectifs, soit planifiés, selon que leur date soit antérieure ou ultérieure à la date actuelle de PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="38822-104">Such items are either in effect or merely planned, depending on whether their date is before or after the PeopleSoft current date.</span></span>  
  
 <span data-ttu-id="38822-105">Si les propriétés d'une interface de composant contiennent des éléments à date d'effet (c'est-à-dire un champ nommé EFFDT), l'adaptateur permet aux appelants de récupérer l'intégralité des valeurs ou uniquement les valeurs qui n'ont pas encore pris effet (et qui sont donc toujours modifiables).</span><span class="sxs-lookup"><span data-stu-id="38822-105">If the properties of a component interface contain such effective-dated items (that is, a field with a name of EFFDT), the adapter makes it possible for callers to retrieve the complete set of values or only those values not yet effective—those that can still be changed.</span></span>  
  
## <a name="gethistoryitems-parameter"></a><span data-ttu-id="38822-106">Paramètre getHistoryItems</span><span class="sxs-lookup"><span data-stu-id="38822-106">getHistoryItems Parameter</span></span>  
 <span data-ttu-id="38822-107">Dans les interfaces de composant dont les propriétés incluent une date d'effet, l'adaptateur fournit un paramètre supplémentaire nommé `getHistoryItems` aux opérations « Get ».</span><span class="sxs-lookup"><span data-stu-id="38822-107">For component interfaces with properties that include an effective date, the adapter provides an additional parameter, called `getHistoryItems`, to the Get operations.</span></span> <span data-ttu-id="38822-108">Ce paramètre est de type booléen ; s'il est défini sur True, tous les éléments ayant une date d'effet sont renvoyés,</span><span class="sxs-lookup"><span data-stu-id="38822-108">This parameter is of type Boolean, and if it is set to True, all effective-dated items are returned.</span></span> <span data-ttu-id="38822-109">Ceux-ci incluent tous les auparavant, les éléments à date d’effet actuels et futurs.</span><span class="sxs-lookup"><span data-stu-id="38822-109">These include all past, current, and future effective-dated items.</span></span>  
  
 <span data-ttu-id="38822-110">Si le paramètre `getHistoryItems` est défini sur False, seuls les éléments actuels et futurs ayant une date d'effet sont renvoyés.</span><span class="sxs-lookup"><span data-stu-id="38822-110">If the `getHistoryItems` parameter is set to False, only the current and future effective-dated items are returned.</span></span> <span data-ttu-id="38822-111">Sélectionnez False si vous envisagez d'ajouter ou de modifier ces éléments (car il est impossible de modifier des éléments passés).</span><span class="sxs-lookup"><span data-stu-id="38822-111">Choose False if your intention is to add or change these items (because past items cannot be changed).</span></span>  
  
 <span data-ttu-id="38822-112">Il est également possible que plusieurs éléments à date d'effet possèdent la même date d'effet.</span><span class="sxs-lookup"><span data-stu-id="38822-112">It is also possible to have multiple effective-dated items having the same effective date.</span></span> <span data-ttu-id="38822-113">Dans ce cas, une propriété supplémentaire, Séquence d'effet (EFFSEQ), doit également être fournie.</span><span class="sxs-lookup"><span data-stu-id="38822-113">In this situation, an additional property, Effective Sequence (EFFSEQ), must also be provided.</span></span> <span data-ttu-id="38822-114">Les valeurs de la propriété EFFSEQ doivent être uniques afin de différencier les éléments possédant la même date d'effet.</span><span class="sxs-lookup"><span data-stu-id="38822-114">The values of the EFFSEQ must be unique to differentiate items with the same effective date.</span></span> <span data-ttu-id="38822-115">Pour plus d'informations, consultez la documentation de PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="38822-115">See the PeopleSoft documentation for more information.</span></span>  
  
## <a name="modifying-past-effective-dated-items"></a><span data-ttu-id="38822-116">Modification des éléments passés ayant une date d'effet</span><span class="sxs-lookup"><span data-stu-id="38822-116">Modifying Past Effective-Dated Items</span></span>  
 <span data-ttu-id="38822-117">Le `correctionMode` argument à la fois dans le [UpdateEx](../core/updateex-method.md) et [DeleteOnly](../core/deleteonly-method.md) méthodes permettent de contrôler si les derniers éléments peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="38822-117">The `correctionMode` argument in both the [UpdateEx](../core/updateex-method.md) and [DeleteOnly](../core/deleteonly-method.md) methods control whether past effective dated items can be modified.</span></span> <span data-ttu-id="38822-118">S'il est défini sur True, tous les éléments peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="38822-118">If it is set to true, all items can be modified.</span></span> <span data-ttu-id="38822-119">Sinon, la modification d'un élément passé associé à une date d'effet génère une exception.</span><span class="sxs-lookup"><span data-stu-id="38822-119">Otherwise, modifying past effective dated item generates an exception.</span></span>  
  
 <span data-ttu-id="38822-120">Lors de l'appel de la méthode `Update` supprimée sur une interface de composant dotée d'éléments à date d'effet, vous devez veiller à ne pas inclure les dates d'effet d'une valeur antérieure à la date d'effet actuelle de PeopleSoft. Sinon, l'appel échoue en générant une exception.</span><span class="sxs-lookup"><span data-stu-id="38822-120">When calling the deprecated `Update` method on a component interface that has effective-dated items, you must take care not to include any effective dates of a value earlier than the PeopleSoft current effective date, or the call fails with an exception.</span></span> <span data-ttu-id="38822-121">Cependant, l'élément actuel ayant une date d'effet peut être inclus car il est contourné lors de la définition des propriétés.</span><span class="sxs-lookup"><span data-stu-id="38822-121">However, the current effective-dated item can be included as it is bypassed when setting properties.</span></span> <span data-ttu-id="38822-122">Si une séquence d'effet existe, tous les éléments actuels à date d'effet du serveur (dont les séquences d'effet correspondent) sont ignorés lors de la définition des propriétés.</span><span class="sxs-lookup"><span data-stu-id="38822-122">If Effective Sequence exists, then all current effective-dated items with matching Effective Sequences in the server are skipped when setting properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38822-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38822-123">See Also</span></span>  
 [<span data-ttu-id="38822-124">Annexe a : méthodes d’Interface de composant</span><span class="sxs-lookup"><span data-stu-id="38822-124">Appendix A: Component Interface Methods</span></span>](../core/appendix-a-component-interface-methods.md)