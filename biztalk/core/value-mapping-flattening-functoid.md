---
title: "(Mise à plat) fonctoid Mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Value Mapping (Flattening) functoids
ms.assetid: d30c3ffe-d3ed-46fd-a692-cd26d042033c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d17d5d64409cd434075dfd4c556209864784e4d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="value-mapping-flattening-functoid"></a><span data-ttu-id="d5431-102">Fonctoid Mappage des valeurs (mise à plat)</span><span class="sxs-lookup"><span data-stu-id="d5431-102">Value Mapping (Flattening) Functoid</span></span>
<span data-ttu-id="d5431-103">Le **Value Mapping (Flattening)** fonctoid vous permet d’aplatir une partie d’un message d’instance d’entrée en convertissant plusieurs enregistrements en un seul enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d5431-103">The **Value Mapping (Flattening)** functoid enables you to flatten a portion of an input instance message by converting multiple records into a single record.</span></span> <span data-ttu-id="d5431-104">Il s’agit d’une opération courante dans la conversion des catalogues Microsoft Commerce Server.</span><span class="sxs-lookup"><span data-stu-id="d5431-104">This is a common operation in converting Microsoft Commerce Server catalogs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5431-105">Le **Value Mapping (Flattening)** fonctoid ne doit pas être combiné avec le **bouclage** fonctoid ou **bouclage de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="d5431-105">The **Value Mapping (Flattening)** functoid should not be combined with the **Looping** functoid or the **Table Looping** functoid.</span></span> <span data-ttu-id="d5431-106">Si elles sont combinées, il en résulte un mappage compilé qui suppose qu’il en existe pas de dépendance pour les nœuds cibles situés au-dessous de bouclage source le **bouclage** ou **bouclage de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="d5431-106">If they are combined, it results in a compiled map that assumes there is no source looping dependency for the target nodes that are below the **Looping** or **Table Looping** functoid.</span></span>  
  
 <span data-ttu-id="d5431-107">Le code suivant représente une partie d'un catalogue listant des variantes d'un produit où chaque composant d'une variante constitue un enregistrement distinct.</span><span class="sxs-lookup"><span data-stu-id="d5431-107">The following code shows a portion of a catalog listing product variants with each feature of the variant in a separate record.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlat.ProductsIn">  
    <ProductVariant ListPrice="99.99" ID="45-01">  
        <Feature Name="Material" Value="Leather" />  
        <Feature Name="Color" Value="Black" />  
    </ProductVariant>  
    <ProductVariant ListPrice="69.99" ID="45-02">  
        <Feature Name="Material" Value="Vinyl" />  
        <Feature Name="Color" Value="Brown" />  
    </ProductVariant>  
</nso0:Root>  
```  
  
 <span data-ttu-id="d5431-108">Mise à plat de cette portion du catalogue convertirait le **fonctionnalité** enregistrements dans les attributs de la **ProductVariant** enregistrement.</span><span class="sxs-lookup"><span data-stu-id="d5431-108">Flattening this portion of the catalog would convert the **Feature** records into attributes of the **ProductVariant** record.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlat.ProductsOut">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 <span data-ttu-id="d5431-109">La figure suivante présente un mappage qui réalise cette conversion.</span><span class="sxs-lookup"><span data-stu-id="d5431-109">The following figure shows a map that performs this conversion.</span></span>  
  
 <span data-ttu-id="d5431-110">![Mapper les enregistrements de la source à l’aide d’un fonctoid. ] (../core/media/valuemappingflattenfunctoid.gif "valuemappingflattenfunctoid")</span><span class="sxs-lookup"><span data-stu-id="d5431-110">![Map source records using a functoid.](../core/media/valuemappingflattenfunctoid.gif "valuemappingflattenfunctoid")</span></span>  
<span data-ttu-id="d5431-111">Mappage du fonctoid Mappage des valeurs (mise à plat)</span><span class="sxs-lookup"><span data-stu-id="d5431-111">Value Mapping (Flattening) Functoid Map</span></span>  
  
 <span data-ttu-id="d5431-112">Le **Value Mapping (Flattening)** fonctoid retourne la valeur de son deuxième paramètre si son premier paramètre a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="d5431-112">The **Value Mapping (Flattening)** functoid returns the value of its second parameter if its first parameter is true.</span></span> <span data-ttu-id="d5431-113">Dans ce mappage, le premier **égal** fonctoid vérifie si le **nom** attribut est égal à « Matériel ».</span><span class="sxs-lookup"><span data-stu-id="d5431-113">In this map, the first **Equal** functoid tests to see if the **Name** attribute is equal to "Material".</span></span> <span data-ttu-id="d5431-114">Si l’attribut est égal à « Matériel », le **égal** fonctoid retourne **True**.</span><span class="sxs-lookup"><span data-stu-id="d5431-114">If the attribute is equal to "Material", the **Equal** functoid returns **True**.</span></span> <span data-ttu-id="d5431-115">À son tour, cela entraîne la **Value Mapping (Flattening)** fonctoid pour affecter la valeur de la **valeur** d’attribut pour le champ dans le message de sortie.</span><span class="sxs-lookup"><span data-stu-id="d5431-115">In turn, this causes the **Value Mapping (Flattening)** functoid to assign the value of the **Value** attribute to the field in the output message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5431-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5431-116">See Also</span></span>  
 <span data-ttu-id="d5431-117">[Comment ajouter le mappage de fonctoids (mise à plat) à une carte](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="d5431-117">[How to Add Value Mapping (Flattening) Functoids to a Map](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="d5431-118">[Schéma plat au catalogue](../core/flat-schema-to-catalog.md) </span><span class="sxs-lookup"><span data-stu-id="d5431-118">[Flat Schema to Catalog](../core/flat-schema-to-catalog.md) </span></span>  
 [<span data-ttu-id="d5431-119">Fonctoids avancés</span><span class="sxs-lookup"><span data-stu-id="d5431-119">Advanced Functoids</span></span>](../core/advanced-functoids.md)