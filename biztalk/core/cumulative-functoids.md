---
title: "Fonctoids cumulés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0549867-e0e4-4cdb-aae0-cadc99088e03
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6ed3d5037d64cf21e1ee2676a5739f13e18da3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cumulative-functoids"></a><span data-ttu-id="c4220-102">Fonctoids cumulés</span><span class="sxs-lookup"><span data-stu-id="c4220-102">Cumulative Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="c4220-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c4220-103">Overview</span></span>
<span data-ttu-id="c4220-104">**Cumulative** fonctoids réduisent une série de valeurs à une valeur unique comme une somme, une chaîne concaténée ou une moyenne.</span><span class="sxs-lookup"><span data-stu-id="c4220-104">**Cumulative** functoids reduce a series of values to a single value such as a sum, a concatenated string, or an average.</span></span>  
  
 <span data-ttu-id="c4220-105">Tous les **Cumulative** fonctoids acceptent deux paramètres d’entrée :</span><span class="sxs-lookup"><span data-stu-id="c4220-105">All **Cumulative** functoids accept two input parameters:</span></span>  
  
1.  <span data-ttu-id="c4220-106">La valeur à cumuler :</span><span class="sxs-lookup"><span data-stu-id="c4220-106">The value to accumulate.</span></span> <span data-ttu-id="c4220-107">Cette valeur est numérique pour tous les **Cumulative** fonctoids à l’exception de la **concaténation cumulée** fonctoid qui attend une valeur de chaîne.</span><span class="sxs-lookup"><span data-stu-id="c4220-107">This value is numeric for all **Cumulative** functoids except the **Cumulative Concatenate** functoid which expects a string value.</span></span> <span data-ttu-id="c4220-108">La valeur provient d’une liaison, souvent un **attribut de champ**, **élément de champ**, ou **enregistrement** nœud (avec ses **mixte** lavaleurdepropriété**True**).</span><span class="sxs-lookup"><span data-stu-id="c4220-108">The value is a link, often from a **Field Attribute**, **Field Element**, or **Record** node (with its **Mixed** property set to **True**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4220-109">Si aucun des ancêtres **enregistrement** nœuds dans l’arborescence de schéma sont bouclage, à l’aide un **Cumulative** fonctoid n’est pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="c4220-109">If none of the ancestor **Record** nodes in the schema tree are looping, using a **Cumulative** functoid is unnecessary.</span></span>  
  
2.  <span data-ttu-id="c4220-110">L’étendue du cumul de la valeur :</span><span class="sxs-lookup"><span data-stu-id="c4220-110">The scope within which the value is accumulated.</span></span> <span data-ttu-id="c4220-111">Cet argument est facultatif.</span><span class="sxs-lookup"><span data-stu-id="c4220-111">This argument is optional.</span></span> <span data-ttu-id="c4220-112">Il indique le degré de parenté que les valeurs spécifiées doivent avoir pour être cumulées.</span><span class="sxs-lookup"><span data-stu-id="c4220-112">The argument indicates how closely related the specified values must be to be accumulated.</span></span>  
  
 <span data-ttu-id="c4220-113">Le tableau suivant montre les valeurs pour le paramètre d’étendue et ses effets :</span><span class="sxs-lookup"><span data-stu-id="c4220-113">The following table shows the values for the scoping parameter and its effect:</span></span>  
  
|<span data-ttu-id="c4220-114">Valeur du paramètre d’étendue</span><span class="sxs-lookup"><span data-stu-id="c4220-114">Scoping Parameter Value</span></span>|<span data-ttu-id="c4220-115">Effet</span><span class="sxs-lookup"><span data-stu-id="c4220-115">Effect</span></span>|  
|-----------------------------|------------|  
|<span data-ttu-id="c4220-116">0 (zéro)</span><span class="sxs-lookup"><span data-stu-id="c4220-116">0 (zero)</span></span>|<span data-ttu-id="c4220-117">Cumuler la valeur sur l’ensemble du message d’instance.</span><span class="sxs-lookup"><span data-stu-id="c4220-117">Accumulate the value over the entire instance message.</span></span> <span data-ttu-id="c4220-118">La valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="c4220-118">The default.</span></span>|  
|<span data-ttu-id="c4220-119">1 (un)</span><span class="sxs-lookup"><span data-stu-id="c4220-119">1 (one)</span></span>|<span data-ttu-id="c4220-120">Cumuler la valeur de l’élément ou les valeurs d’attribut avec le même élément parent.</span><span class="sxs-lookup"><span data-stu-id="c4220-120">Accumulate the value of element or attribute values with the same parent element.</span></span>|  
|<span data-ttu-id="c4220-121">2</span><span class="sxs-lookup"><span data-stu-id="c4220-121">2</span></span>|<span data-ttu-id="c4220-122">Cumuler la valeur de l’élément ou les valeurs d’attribut avec le même élément grand-parent.</span><span class="sxs-lookup"><span data-stu-id="c4220-122">Accumulate the value of element or attribute values with the same grandparent element.</span></span>|  
|<span data-ttu-id="c4220-123">Au moins 3</span><span class="sxs-lookup"><span data-stu-id="c4220-123">3 or greater</span></span>|<span data-ttu-id="c4220-124">Cumuler la valeur de l’élément ou les valeurs d’attribut d’étendue progressivement plus large selon le modèle précédent (arrière grand-parent, arrière arrière grand-parent, etc.).</span><span class="sxs-lookup"><span data-stu-id="c4220-124">Accumulate the value of element or attribute values of progressively wider scope following the preceding pattern (great-grandparent, great-great-grandparent, etc.).</span></span>|  

## <a name="example"></a><span data-ttu-id="c4220-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="c4220-125">Example</span></span>  
 <span data-ttu-id="c4220-126">Un exemple d’utilisation une **Cumulative** fonctoid peut être somme des coûts apparaissant sur un bon de commande.</span><span class="sxs-lookup"><span data-stu-id="c4220-126">An example of using a **Cumulative** functoid might be summing costs across a purchase order.</span></span> <span data-ttu-id="c4220-127">Le code suivant correspond à un exemple de bon de commande :</span><span class="sxs-lookup"><span data-stu-id="c4220-127">The following code is an example of a purchase order.</span></span>  
  
```  
<ns0:PurchaseOrder xmlns:ns0="http://CumulativeFunctoid.PurchaseOrder">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <LineItems>  
        <Item>  
            <Product>Laptop Computer</Product>  
            <Description>Thin profile laptop</Description>  
            <Price>1999.95</Price>  
            <Quantity>1</Quantity>  
        </Item>  
        <Item>  
            <Product>Monitor Swipes</Product>  
            <Description>Disposable monitor swipes</Description>  
            <Price>3.95</Price>  
            <Quantity>10</Quantity>  
        </Item>  
    </LineItems>  
</ns0:PurchaseOrder>  
```  
  
 <span data-ttu-id="c4220-128">Le **Max Occurs** propriété pour le **élément** enregistrement, bien entendu, serait **unbounded**.</span><span class="sxs-lookup"><span data-stu-id="c4220-128">The **Max Occurs** property for the **Item** record would, of course, be **unbounded**.</span></span> <span data-ttu-id="c4220-129">Cela signifie que l’enregistrement Item est une boucle et que le Mappeur BizTalk compile cet enregistrement en tant que boucle.</span><span class="sxs-lookup"><span data-stu-id="c4220-129">This indicates that the item record loops, and BizTalk Mapper compiles this record as a loop.</span></span>  
  
 <span data-ttu-id="c4220-130">La figure suivante illustre un mappage utilisant un **Multiplication** fonctoid et un **somme cumulée** fonctoid pour agréger les enregistrements item d’un entrant bon de commande et les résultats dans le  **POTotal** champ :</span><span class="sxs-lookup"><span data-stu-id="c4220-130">The following figure shows a map using a **Multiplication** functoid and a **Cumulative Sum** functoid to aggregate item records from an incoming purchase order and output the results in the **POTotal** field:</span></span>  
  
 <span data-ttu-id="c4220-131">![Mappage illustrant l’utilisation du fonctoid Somme cumulée. ] (../core/media/cumulativefunctoids.gif "cumulativefunctoids")</span><span class="sxs-lookup"><span data-stu-id="c4220-131">![Map showing usage of the cumulative sum functoid.](../core/media/cumulativefunctoids.gif "cumulativefunctoids")</span></span>  

  
 <span data-ttu-id="c4220-132">Le mappage produit le résultat suivant avec les données précédentes et avec la valeur du paramètre d’étendue par défaut, 0 (zéro) :</span><span class="sxs-lookup"><span data-stu-id="c4220-132">The map produces the following output with the preceding data and with the default scoping parameter value, 0 (zero):</span></span>  
  
```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  
  
 <span data-ttu-id="c4220-133">Dans cet exemple, tous les le **élément** enregistre sous la **LineItems** enregistrement participent au cumul, la valeur par défaut pour le paramètre d’étendue indique le cumul des valeurs sur l’intégralité du message.</span><span class="sxs-lookup"><span data-stu-id="c4220-133">In this example, all the **Item** records under the **LineItems** record participate in the accumulation—the default for the scoping parameter indicates accumulating the values across the entire message.</span></span> <span data-ttu-id="c4220-134">Le **prix** et **quantité** champs sont envoyés à un **Multiplication** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="c4220-134">The **Price** and **Quantity** fields are sent to a **Multiplication** functoid.</span></span> <span data-ttu-id="c4220-135">La sortie de la **Multiplication** fonctoid devient l’entrée de la **somme cumulée** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="c4220-135">The output of the **Multiplication** functoid becomes the input to the **Cumulative Sum** functoid.</span></span> <span data-ttu-id="c4220-136">La sortie de la **somme cumulée** fonctoid est la valeur en tant que le **élément** enregistrements sont parcourus dans l’ordre d’achat d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c4220-136">The output of the **Cumulative Sum** functoid is the accumulated value as the **Item** records are traversed in the input purchase order.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4220-137">L’agrégation cumulée des entrées a lieu sur l’enregistrement parent d’où prend naissance la liaison d’entrée.</span><span class="sxs-lookup"><span data-stu-id="c4220-137">The cumulative aggregation of input takes place over the parent record from which the input link originates.</span></span> <span data-ttu-id="c4220-138">Même lorsque le **Cumulative** fonctoid obtient son entrée à partir d’un autre fonctoid, l’agrégation cumulée intervient sur l’enregistrement parent des liens d’entrée du fonctoid qui sert d’entrée le **Cumulative**fonctoid.</span><span class="sxs-lookup"><span data-stu-id="c4220-138">Even when the **Cumulative** functoid gets its input from another functoid, the cumulative aggregation takes place over the parent record of the input links to the functoid that serves as input to the **Cumulative** functoid.</span></span>  
  
 <span data-ttu-id="c4220-139">Si vous changez la valeur du paramètre d’étendue sur 1 (un) et modifiez légèrement le schéma de sortie, le résultat est le suivant :</span><span class="sxs-lookup"><span data-stu-id="c4220-139">Changing the scoping parameter to 1 (one) and modifying the output schema slightly, yields output like the following:</span></span>  
  
```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <ItemTotal>1999.95</ItemTotal>  
    <ItemTotal>39.5</ItemTotal>  
</ns0:SummedPO>  
```  
  
 <span data-ttu-id="c4220-140">La définition du paramètre d’étendue sur 1 (un) indique le cumul des valeurs des éléments ou attributs ayant le même parent.</span><span class="sxs-lookup"><span data-stu-id="c4220-140">Setting the scoping parameter to 1 (one) indicates accumulating values for elements or attributes with the same parent.</span></span> <span data-ttu-id="c4220-141">Ici le **prix** et **quantité** champs ont **élément** en tant que parent afin que le fonctoid totalise les valeurs de chaque individu **élément**.</span><span class="sxs-lookup"><span data-stu-id="c4220-141">Here the **Price** and **Quantity** fields have **Item** as a parent so that the functoid sums values for each individual **Item**.</span></span>  
  
 <span data-ttu-id="c4220-142">Si le paramètre d’étendue est défini sur 2, le fonctoid cumule les valeurs des éléments ou attributs ayant le même grand-parent.</span><span class="sxs-lookup"><span data-stu-id="c4220-142">If the scoping parameter is 2, the functoid accumulates values for elements or attributes with the same grandparent.</span></span> <span data-ttu-id="c4220-143">Le grand-parent de la **prix** et **quantité** champs est la **LineItems** enregistrement.</span><span class="sxs-lookup"><span data-stu-id="c4220-143">The grandparent of the **Price** and **Quantity** fields is the **LineItems** record.</span></span> <span data-ttu-id="c4220-144">Étant donné qu’un seul **LineItems** enregistrement dans le message d’instance, le résultat est identique à l’aide de la valeur par défaut :</span><span class="sxs-lookup"><span data-stu-id="c4220-144">Because there is only one **LineItems** record in the instance message, the result is the same as using the default value:</span></span>  
  
```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  
  
> [!NOTE]
>  <span data-ttu-id="c4220-145">Fonctoids cumulés (à l’exception de la **Chaîne cumulée** fonctoid) ignore les entrées non numériques.</span><span class="sxs-lookup"><span data-stu-id="c4220-145">Cumulative functoids (except for the **Cumulative String** functoid) ignore non-numeric input.</span></span> <span data-ttu-id="c4220-146">Par exemple, une valeur d’entrée de « trois » est ignorée.</span><span class="sxs-lookup"><span data-stu-id="c4220-146">For example, an input value of "three" is ignored.</span></span>  
  
 <span data-ttu-id="c4220-147">Le **moyenne cumulée**, **Minimum cumulé**, et **Maximum cumulé** fonctoids se comportent de la même façon que les **somme cumulée** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="c4220-147">The **Cumulative Average**, **Cumulative Minimum**, and **Cumulative Maximum** functoids behave similarly to the **Cumulative Sum** functoid.</span></span> <span data-ttu-id="c4220-148">Le **Chaîne cumulée** concatène les chaînes plutôt que des valeurs numériques.</span><span class="sxs-lookup"><span data-stu-id="c4220-148">The **Cumulative String** concatenates strings rather than aggregating numeric values.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="c4220-149">Fonctoids disponibles</span><span class="sxs-lookup"><span data-stu-id="c4220-149">Available functoids</span></span>
  
 <span data-ttu-id="c4220-150">Le **Cumulative** fonctoids sont :</span><span class="sxs-lookup"><span data-stu-id="c4220-150">The **Cumulative** functoids are:</span></span> 

* <span data-ttu-id="c4220-151">Moyenne cumulée</span><span class="sxs-lookup"><span data-stu-id="c4220-151">Cumulative Average</span></span>
* <span data-ttu-id="c4220-152">Concaténation cumulée</span><span class="sxs-lookup"><span data-stu-id="c4220-152">Cumulative Concatenate</span></span>
* <span data-ttu-id="c4220-153">Maximum cumulé</span><span class="sxs-lookup"><span data-stu-id="c4220-153">Cumulative Maximum</span></span>
* <span data-ttu-id="c4220-154">Minimum cumulé</span><span class="sxs-lookup"><span data-stu-id="c4220-154">Cumulative Minimum</span></span>
* <span data-ttu-id="c4220-155">Somme cumulée</span><span class="sxs-lookup"><span data-stu-id="c4220-155">Cumulative Sum</span></span>

<span data-ttu-id="c4220-156">Plus d’informations sur ces fonctoids [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="c4220-156">More details on these functoids are [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c4220-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4220-157">See Also</span></span>  
-  [<span data-ttu-id="c4220-158">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="c4220-158">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="c4220-159">**Référence des fonctoids cumulés**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c4220-159">**Cumulative Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>