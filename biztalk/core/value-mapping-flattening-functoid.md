---
title: (Mise à plat) fonctoid Mappage | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Value Mapping (Flattening) functoids
ms.assetid: d30c3ffe-d3ed-46fd-a692-cd26d042033c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d17d5d64409cd434075dfd4c556209864784e4d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="value-mapping-flattening-functoid"></a>Fonctoid Mappage des valeurs (mise à plat)
Le **Value Mapping (Flattening)** fonctoid vous permet d’aplatir une partie d’un message d’instance d’entrée en convertissant plusieurs enregistrements en un seul enregistrement. Il s’agit d’une opération courante dans la conversion des catalogues Microsoft Commerce Server.  
  
> [!NOTE]
>  Le **Value Mapping (Flattening)** fonctoid ne doit pas être combiné avec le **bouclage** fonctoid ou **bouclage de Table** fonctoid. Si elles sont combinées, il en résulte un mappage compilé qui suppose qu’il en existe pas de dépendance pour les nœuds cibles situés au-dessous de bouclage source le **bouclage** ou **bouclage de Table** fonctoid.  
  
 Le code suivant représente une partie d'un catalogue listant des variantes d'un produit où chaque composant d'une variante constitue un enregistrement distinct.  
  
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
  
 Mise à plat de cette portion du catalogue convertirait le **fonctionnalité** enregistrements dans les attributs de la **ProductVariant** enregistrement.  
  
```  
<ns0:Root xmlns:ns0="http://ValueMappingFlat.ProductsOut">  
    <ProductVariant ListPrice="99.99" ID="45-01" Material="Leather" Color="Black" />  
    <ProductVariant ListPrice="69.99" ID="45-02" Material="Vinyl" Color="Brown" />  
</ns0:Root>  
```  
  
 La figure suivante présente un mappage qui réalise cette conversion.  
  
 ![Mapper les enregistrements de la source à l’aide d’un fonctoid. ] (../core/media/valuemappingflattenfunctoid.gif "valuemappingflattenfunctoid")  
Mappage du fonctoid Mappage des valeurs (mise à plat)  
  
 Le **Value Mapping (Flattening)** fonctoid retourne la valeur de son deuxième paramètre si son premier paramètre a la valeur true. Dans ce mappage, le premier **égal** fonctoid vérifie si le **nom** attribut est égal à « Matériel ». Si l’attribut est égal à « Matériel », le **égal** fonctoid retourne **True**. À son tour, cela entraîne la **Value Mapping (Flattening)** fonctoid pour affecter la valeur de la **valeur** d’attribut pour le champ dans le message de sortie.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter le mappage de fonctoids (mise à plat) à une carte](../core/how-to-add-value-mapping-flattening-functoids-to-a-map.md)   
 [Schéma plat au catalogue](../core/flat-schema-to-catalog.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)