---
title: Fonctoids logiques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e37cdfc3-66de-4333-84eb-a8765afa8407
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7907d1045fde39d5ece963bd78e00d027e8a9da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="logical-functoids"></a><span data-ttu-id="fa7b6-102">Fonctoids logiques</span><span class="sxs-lookup"><span data-stu-id="fa7b6-102">Logical Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="fa7b6-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="fa7b6-103">Overview</span></span>
<span data-ttu-id="fa7b6-104">**Logique** fonctoids permettent d’effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="fa7b6-104">**Logical** functoids are used to perform the following types of operations:</span></span>  
  
-   <span data-ttu-id="fa7b6-105">Effectuer des tests logiques spécifiques au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-105">Perform specific logical tests at run time.</span></span> <span data-ttu-id="fa7b6-106">Le **OR logique**, **NOT logique** et **logiques et** fonctoids peuvent être utilisées pour déterminer si un enregistrement est créé dans un message d’instance de destination, tel que le suivant :</span><span class="sxs-lookup"><span data-stu-id="fa7b6-106">The **Logical OR**, **Logical NOT** and **Logical AND** functoids can be used to determine whether a record is created in a destination instance message, such as the following:</span></span>  
  
     <span data-ttu-id="fa7b6-107">Si ShipTo **ou** OrderedBy sont présents, créez l’enregistrement d’adresse BillTo.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-107">If ShipTo **OR** OrderedBy are present, create BillTo address record.</span></span>  
  
     <span data-ttu-id="fa7b6-108">Vous pouvez également utiliser ces fonctoids conjointement avec la **bouclage** fonctoid pour configurer le nombre de fois où un enregistrement de boucle.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-108">You can also use these functoids in conjunction with the **Looping** functoid to configure how many times a record loops.</span></span>  
  
-   <span data-ttu-id="fa7b6-109">Contrôler si un enregistrement spécifique est créé dans un message d’instance de destination au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-109">Control whether a specific record is created in a destination instance message at run time.</span></span> <span data-ttu-id="fa7b6-110">Fonctoids tels que **IsNil**, **Nombre logique**, **moins**, et **supérieur à** peut être utilisée pour contrôler si un enregistrement est créé.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-110">Functoids such as **IsNil**, **Logical Numeric**, **Less Than**, and **Greater Than** can be used to control whether a record is created.</span></span>  
  
     <span data-ttu-id="fa7b6-111">Si le résultat de l’un de ces fonctoids logiques est **True**, l’enregistrement correspondant dans le message d’instance de destination est généré.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-111">If the result of one of these logical functoids is **True**, the corresponding record in the destination instance message is generated.</span></span> <span data-ttu-id="fa7b6-112">Si le résultat est **False**, l’enregistrement correspondant dans le message d’instance de destination n’est pas généré.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-112">If the result is **False**, the corresponding record in the destination instance message is not generated.</span></span>  
  
 <span data-ttu-id="fa7b6-113">Les fonctoids **IsNil**, **Date logique**, **Existence logique**, **NOT logique**, **numérique logique**, et **chaîne logique** n'accepter qu’un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-113">The functoids **IsNil**, **Logical Date**, **Logical Existence**, **Logical NOT**, **Logical Numeric**, and **Logical String** accept only one parameter.</span></span> <span data-ttu-id="fa7b6-114">Les fonctoids **égal**, **supérieur à**, **supérieur ou égal à**, **moins**, **inférieur ou égal à**, et **n’est pas égal** acceptent deux paramètres d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-114">The functoids **Equal**, **Greater Than**, **Greater Than or Equal To**, **Less Than**, **Less Than or Equal To**, and **Not Equal** accept two input parameters.</span></span> <span data-ttu-id="fa7b6-115">Alors que, dans le **logiques et** et **OR logique** fonctoids acceptent des paramètres d’entrée entre 2 et 100.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-115">Whereas, the **Logical AND** and **Logical OR** functoids accept input parameters between 2 and 100.</span></span>  
  
 <span data-ttu-id="fa7b6-116">La sortie d’un **logiques** fonctoid peut également être accepté comme entrée pour d’autres fonctoids dans un mappage.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-116">The output of a **Logical** functoid can also be accepted as input to other functoids in a map.</span></span> <span data-ttu-id="fa7b6-117">Si les deux un **logiques** fonctoid et un fonctoid Bouclage sont liés entre eux et ensuite liés à un enregistrement dans le schéma de destination, le fonctoid Bouclage est utilisé uniquement lorsque le **logiques** sortie du fonctoid est  **True**.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-117">If both a **Logical** functoid and a looping functoid are linked together, and then linked to a record in the destination schema, the looping functoid is used only when the **Logical** functoid output is **True**.</span></span>  
  
 <span data-ttu-id="fa7b6-118">Vous pouvez également utiliser **logiques** fonctoids avec les **mappage** ou **Value Mapping (Flattening)** fonctoids pour contrôler si un enregistrement dans le message d’instance de destination est créé.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-118">You can also use **Logical** functoids with the **Value Mapping** or **Value Mapping (Flattening)** functoids to control whether a record in the destination instance message is created.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa7b6-119">Si vous liez deux enregistrements ou champs du schéma source à deux **logiques** fonctoids et vous liez chacun de la **logiques** fonctoids au même enregistrement dans le schéma de destination, seul le premier  **Logique** fonctoid est utilisé dans le généré Language Transformations XSLT (Extensible Stylesheet).</span><span class="sxs-lookup"><span data-stu-id="fa7b6-119">If you link two records or fields in the source schema to two different **Logical** functoids, and then link each of the **Logical** functoids to the same record in the destination schema, only the first **Logical** functoid is used in the generated Extensible Stylesheet Language Transformations (XSLT).</span></span> <span data-ttu-id="fa7b6-120">Le deuxième lien, de la seconde **logiques** fonctoid, est ignoré.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-120">The second link, from the second **Logical** functoid, is ignored.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa7b6-121">Les fonctoids logiques font la distinction entre les majuscules et les minuscules lorsque deux chaînes sont comparées.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-121">Logical functoids are case-sensitive when comparing two strings.</span></span> <span data-ttu-id="fa7b6-122">Par exemple, les chaînes « Abc » et « abc » ne sont pas équivalentes.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-122">For example, "Abc" and "abc" are not equal.</span></span> <span data-ttu-id="fa7b6-123">L’exception à cette règle est quand **logiques** fonctoids comparent des chaînes qui représentent les valeurs booléennes **True** et **False**.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-123">The exception to this rule is when **Logical** functoids compare strings that represent the Boolean values **True** and **False**.</span></span> <span data-ttu-id="fa7b6-124">Dans ce cas, « True » et « true » sont équivalents.</span><span class="sxs-lookup"><span data-stu-id="fa7b6-124">For example, "True" and "true" are equal.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="fa7b6-125">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="fa7b6-125">Available functoids</span></span>  
 <span data-ttu-id="fa7b6-126">Le **logiques** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="fa7b6-126">The **Logical** functoids are:</span></span> 

* <span data-ttu-id="fa7b6-127">Égal à</span><span class="sxs-lookup"><span data-stu-id="fa7b6-127">Equal</span></span>
* <span data-ttu-id="fa7b6-128">Supérieur à</span><span class="sxs-lookup"><span data-stu-id="fa7b6-128">Greater Than</span></span>
* <span data-ttu-id="fa7b6-129">Supérieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="fa7b6-129">Greater Than or Equal To</span></span>
* <span data-ttu-id="fa7b6-130">IsNil</span><span class="sxs-lookup"><span data-stu-id="fa7b6-130">IsNil</span></span>
* <span data-ttu-id="fa7b6-131">Inférieur à</span><span class="sxs-lookup"><span data-stu-id="fa7b6-131">Less Than</span></span>
* <span data-ttu-id="fa7b6-132">Inférieur ou égal à</span><span class="sxs-lookup"><span data-stu-id="fa7b6-132">Less Than or Equal To</span></span>
* <span data-ttu-id="fa7b6-133">ET logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-133">Logical AND</span></span>
* <span data-ttu-id="fa7b6-134">Date logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-134">Logical Date</span></span>
* <span data-ttu-id="fa7b6-135">Existence logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-135">Logical Existence</span></span>
* <span data-ttu-id="fa7b6-136">NOT logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-136">Logical NOT</span></span>
* <span data-ttu-id="fa7b6-137">Nombre logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-137">Logical Numeric</span></span>
* <span data-ttu-id="fa7b6-138">OU logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-138">Logical OR</span></span>
* <span data-ttu-id="fa7b6-139">Chaîne logique</span><span class="sxs-lookup"><span data-stu-id="fa7b6-139">Logical String</span></span>
* <span data-ttu-id="fa7b6-140">Non égal</span><span class="sxs-lookup"><span data-stu-id="fa7b6-140">Not Equal</span></span>

<span data-ttu-id="fa7b6-141">Plus d’informations sur ces fonctions sont [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="fa7b6-141">More details on these functions are [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fa7b6-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa7b6-142">See Also</span></span>  
-  [<span data-ttu-id="fa7b6-143">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="fa7b6-143">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="fa7b6-144">**Référence des fonctoids logiques**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="fa7b6-144">**Logical Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>