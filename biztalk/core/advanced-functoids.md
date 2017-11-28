---
title: Advanced fonctoids | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bf2547-5e44-45f8-b577-97e5760a0339
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5002b639df79ece1019c2d013c128f615517ae5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-functoids"></a><span data-ttu-id="0d799-102">Fonctoids avancés</span><span class="sxs-lookup"><span data-stu-id="0d799-102">Advanced Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="0d799-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0d799-103">Overview</span></span>
<span data-ttu-id="0d799-104">Les fonctoids avancés se répartissent en cinq catégories différentes en fonction de leur usage :</span><span class="sxs-lookup"><span data-stu-id="0d799-104">Advanced functoids fall into five groups, according to their use:</span></span>  
  
-   <span data-ttu-id="0d799-105">**La gestion des enregistrements de boucle.**</span><span class="sxs-lookup"><span data-stu-id="0d799-105">**Managing looping records.**</span></span> <span data-ttu-id="0d799-106">Le **Index**, **itération**, **bouclage**, **valeur Nil**, **nombre d’enregistrements**, **Table Extracteur**, et **bouclage de Table** fonctoids sont utilisés dans différentes combinaisons lorsque le message d’instance d’entrée contient des sections comportant un imprévisibles nombre d’éléments se répétant, comme représenté par un bouclage enregistrements dans le schéma source.</span><span class="sxs-lookup"><span data-stu-id="0d799-106">The **Index**, **Iteration**, **Looping**, **Nil Value**, **Record Count**, **Table Extractor**, and **Table Looping** functoids are used in various combinations when the input instance message contains sections with an unpredictable number of repeating elements, as represented by looping records in the source schema.</span></span>  
  
-   <span data-ttu-id="0d799-107">**Mappage conditionnel.**</span><span class="sxs-lookup"><span data-stu-id="0d799-107">**Conditional mapping.**</span></span> <span data-ttu-id="0d799-108">Le **mappage** et **Value Mapping (Flattening)** fonctoids sont utilisés pour fournir un mappage conditionnel à partir d’un message d’instance d’entrée et un message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="0d799-108">The **Value Mapping** and **Value Mapping (Flattening)** functoids are used to provide conditional mapping from an input instance message to an output instance message.</span></span> <span data-ttu-id="0d799-109">Lorsque leur premier paramètre d'entrée est True, le second est placé dans l'élément ou l'attribut spécifié dans le message d'instance de sortie. Sinon, cet élément ou cet attribut n'est pas créé dans le message d'instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="0d799-109">When their first input parameter is true, the second input parameter is put into the specified element or attribute in the output instance message; otherwise, that element or attribute is not created in the output instance message.</span></span>  
  
-   <span data-ttu-id="0d799-110">**Script arbitraire.**</span><span class="sxs-lookup"><span data-stu-id="0d799-110">**Arbitrary scripting.**</span></span> <span data-ttu-id="0d799-111">Le **script** fonctoid est utilisé pour exécuter un script arbitraire ou code compilé lorsqu’un message d’instance d’entrée est mappé à un message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="0d799-111">The **Scripting** functoid is used to run arbitrary script or compiled code when an input instance message is being mapped to an output instance message.</span></span> <span data-ttu-id="0d799-112">Un tel script ou code compilé peut être créé de manière à ce qu'il accepte les paramètres d'entrée issus du message d'instance source, des valeurs constantes configurées, de la sortie d'un autre fonctoid, ou d'une combinaison de tout cela.</span><span class="sxs-lookup"><span data-stu-id="0d799-112">Such script or compiled code can be created so that it accepts input parameters from the source instance message, from configured constant values, from the output of another functoid, or some combination thereof.</span></span>  
  
-   <span data-ttu-id="0d799-113">**Mappage simple.**</span><span class="sxs-lookup"><span data-stu-id="0d799-113">**Simple mapping.**</span></span> <span data-ttu-id="0d799-114">Le **copie de masse** fonctoid peut être utilisé pour copier un élément entier, y compris ses sous-éléments jusqu'à une profondeur arbitraire, à partir d’un message d’instance d’entrée et un message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="0d799-114">The **Mass Copy** functoid can be used to copy an entire element, including its subelements to an arbitrary depth, from an input instance message to an output instance message.</span></span>  
  
-   <span data-ttu-id="0d799-115">**Résolution des problèmes**.</span><span class="sxs-lookup"><span data-stu-id="0d799-115">**Troubleshooting**.</span></span> <span data-ttu-id="0d799-116">Le **Assert** fonctoid peut être utilisé pour tester vos hypothèses sur les valeurs d’élément.</span><span class="sxs-lookup"><span data-stu-id="0d799-116">The **Assert** functoid can be used to test your assumptions about element values.</span></span>  
  
## <a name="available-functoids"></a><span data-ttu-id="0d799-117">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="0d799-117">Available functoids</span></span>
  
 <span data-ttu-id="0d799-118">Le **avancé** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="0d799-118">The **Advanced** functoids are:</span></span> 

* <span data-ttu-id="0d799-119">Fonctoid déclarer</span><span class="sxs-lookup"><span data-stu-id="0d799-119">Assert Functoid</span></span>
* <span data-ttu-id="0d799-120">Fonctoid Index</span><span class="sxs-lookup"><span data-stu-id="0d799-120">Index Functoid</span></span> 
* <span data-ttu-id="0d799-121">Fonctoid Itération</span><span class="sxs-lookup"><span data-stu-id="0d799-121">Iteration Functoid</span></span> 
* <span data-ttu-id="0d799-122">Fonctoid Bouclage</span><span class="sxs-lookup"><span data-stu-id="0d799-122">Looping Functoid</span></span> 
* <span data-ttu-id="0d799-123">Fonctoid Copie de masse</span><span class="sxs-lookup"><span data-stu-id="0d799-123">Mass Copy Functoid</span></span> 
* <span data-ttu-id="0d799-124">Fonctoid Valeur nil</span><span class="sxs-lookup"><span data-stu-id="0d799-124">Nil Value Functoid</span></span>
* <span data-ttu-id="0d799-125">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="0d799-125">Record Count Functoid</span></span> 
* <span data-ttu-id="0d799-126">Fonctoid script</span><span class="sxs-lookup"><span data-stu-id="0d799-126">Scripting Functoid</span></span> 
* <span data-ttu-id="0d799-127">Bouclage de table et de fonctoids Extracteur de Table</span><span class="sxs-lookup"><span data-stu-id="0d799-127">Table Looping and Table Extractor Functoids</span></span>
* <span data-ttu-id="0d799-128">Fonctoid Mappage</span><span class="sxs-lookup"><span data-stu-id="0d799-128">Value Mapping Functoid</span></span>
* <span data-ttu-id="0d799-129">Fonctoid Mappage des valeurs (mise à plat)</span><span class="sxs-lookup"><span data-stu-id="0d799-129">Value Mapping (Flattening) Functoid</span></span>

<span data-ttu-id="0d799-130">Plus d’informations sur ces fonctoids sont dans le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="0d799-130">More details on these functoids are in the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="0d799-131">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0d799-131">Next steps</span></span>
  
-   [<span data-ttu-id="0d799-132">Fonctoid déclarer</span><span class="sxs-lookup"><span data-stu-id="0d799-132">Assert Functoid</span></span>](../core/assert-functoid.md)  
  
-   [<span data-ttu-id="0d799-133">Fonctoid Index</span><span class="sxs-lookup"><span data-stu-id="0d799-133">Index Functoid</span></span>](../core/index-functoid.md)  
  
-   [<span data-ttu-id="0d799-134">Fonctoid Itération</span><span class="sxs-lookup"><span data-stu-id="0d799-134">Iteration Functoid</span></span>](../core/iteration-functoid.md)  
  
-   [<span data-ttu-id="0d799-135">Fonctoid Bouclage</span><span class="sxs-lookup"><span data-stu-id="0d799-135">Looping Functoid</span></span>](../core/looping-functoid.md)  
  
-   [<span data-ttu-id="0d799-136">Fonctoid copie de masse</span><span class="sxs-lookup"><span data-stu-id="0d799-136">Mass Copy Functoid</span></span>](../core/mass-copy-functoid.md)  
  
-   [<span data-ttu-id="0d799-137">Fonctoid Valeur nil</span><span class="sxs-lookup"><span data-stu-id="0d799-137">Nil Value Functoid</span></span>](../core/nil-value-functoid.md)  
  
-   [<span data-ttu-id="0d799-138">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="0d799-138">Record Count Functoid</span></span>](../core/record-count-functoid.md)  
  
-   [<span data-ttu-id="0d799-139">Bouclage de table et de fonctoids Extracteur de Table</span><span class="sxs-lookup"><span data-stu-id="0d799-139">Table Looping and Table Extractor Functoids</span></span>](../core/table-looping-and-table-extractor-functoids.md)  
  
-   [<span data-ttu-id="0d799-140">Fonctoid Mappage</span><span class="sxs-lookup"><span data-stu-id="0d799-140">Value Mapping Functoid</span></span>](../core/value-mapping-functoid.md)  
  
-   [<span data-ttu-id="0d799-141">(Mise à plat) fonctoid Mappage</span><span class="sxs-lookup"><span data-stu-id="0d799-141">Value Mapping (Flattening) Functoid</span></span>](../core/value-mapping-flattening-functoid.md)  
  
-   [<span data-ttu-id="0d799-142">Fonctoid script</span><span class="sxs-lookup"><span data-stu-id="0d799-142">Scripting Functoid</span></span>](../core/scripting-functoid.md)