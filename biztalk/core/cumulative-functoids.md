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
# <a name="cumulative-functoids"></a>Fonctoids cumulés

## <a name="overview"></a>Vue d'ensemble
**Cumulative** fonctoids réduisent une série de valeurs à une valeur unique comme une somme, une chaîne concaténée ou une moyenne.  
  
 Tous les **Cumulative** fonctoids acceptent deux paramètres d’entrée :  
  
1.  La valeur à cumuler : Cette valeur est numérique pour tous les **Cumulative** fonctoids à l’exception de la **concaténation cumulée** fonctoid qui attend une valeur de chaîne. La valeur provient d’une liaison, souvent un **attribut de champ**, **élément de champ**, ou **enregistrement** nœud (avec ses **mixte** lavaleurdepropriété**True**).  
  
    > [!NOTE]
    >  Si aucun des ancêtres **enregistrement** nœuds dans l’arborescence de schéma sont bouclage, à l’aide un **Cumulative** fonctoid n’est pas nécessaire.  
  
2.  L’étendue du cumul de la valeur : Cet argument est facultatif. Il indique le degré de parenté que les valeurs spécifiées doivent avoir pour être cumulées.  
  
 Le tableau suivant montre les valeurs pour le paramètre d’étendue et ses effets :  
  
|Valeur du paramètre d’étendue|Effet|  
|-----------------------------|------------|  
|0 (zéro)|Cumuler la valeur sur l’ensemble du message d’instance. La valeur par défaut.|  
|1 (un)|Cumuler la valeur de l’élément ou les valeurs d’attribut avec le même élément parent.|  
|2|Cumuler la valeur de l’élément ou les valeurs d’attribut avec le même élément grand-parent.|  
|Au moins 3|Cumuler la valeur de l’élément ou les valeurs d’attribut d’étendue progressivement plus large selon le modèle précédent (arrière grand-parent, arrière arrière grand-parent, etc.).|  

## <a name="example"></a>Exemple  
 Un exemple d’utilisation une **Cumulative** fonctoid peut être somme des coûts apparaissant sur un bon de commande. Le code suivant correspond à un exemple de bon de commande :  
  
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
  
 Le **Max Occurs** propriété pour le **élément** enregistrement, bien entendu, serait **unbounded**. Cela signifie que l’enregistrement Item est une boucle et que le Mappeur BizTalk compile cet enregistrement en tant que boucle.  
  
 La figure suivante illustre un mappage utilisant un **Multiplication** fonctoid et un **somme cumulée** fonctoid pour agréger les enregistrements item d’un entrant bon de commande et les résultats dans le  **POTotal** champ :  
  
 ![Mappage illustrant l’utilisation du fonctoid Somme cumulée. ] (../core/media/cumulativefunctoids.gif "cumulativefunctoids")  

  
 Le mappage produit le résultat suivant avec les données précédentes et avec la valeur du paramètre d’étendue par défaut, 0 (zéro) :  
  
```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  
  
 Dans cet exemple, tous les le **élément** enregistre sous la **LineItems** enregistrement participent au cumul, la valeur par défaut pour le paramètre d’étendue indique le cumul des valeurs sur l’intégralité du message. Le **prix** et **quantité** champs sont envoyés à un **Multiplication** fonctoid. La sortie de la **Multiplication** fonctoid devient l’entrée de la **somme cumulée** fonctoid. La sortie de la **somme cumulée** fonctoid est la valeur en tant que le **élément** enregistrements sont parcourus dans l’ordre d’achat d’entrée.  
  
> [!NOTE]
>  L’agrégation cumulée des entrées a lieu sur l’enregistrement parent d’où prend naissance la liaison d’entrée. Même lorsque le **Cumulative** fonctoid obtient son entrée à partir d’un autre fonctoid, l’agrégation cumulée intervient sur l’enregistrement parent des liens d’entrée du fonctoid qui sert d’entrée le **Cumulative**fonctoid.  
  
 Si vous changez la valeur du paramètre d’étendue sur 1 (un) et modifiez légèrement le schéma de sortie, le résultat est le suivant :  
  
```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <ItemTotal>1999.95</ItemTotal>  
    <ItemTotal>39.5</ItemTotal>  
</ns0:SummedPO>  
```  
  
 La définition du paramètre d’étendue sur 1 (un) indique le cumul des valeurs des éléments ou attributs ayant le même parent. Ici le **prix** et **quantité** champs ont **élément** en tant que parent afin que le fonctoid totalise les valeurs de chaque individu **élément**.  
  
 Si le paramètre d’étendue est défini sur 2, le fonctoid cumule les valeurs des éléments ou attributs ayant le même grand-parent. Le grand-parent de la **prix** et **quantité** champs est la **LineItems** enregistrement. Étant donné qu’un seul **LineItems** enregistrement dans le message d’instance, le résultat est identique à l’aide de la valeur par défaut :  
  
```  
<ns0:SummedPO xmlns:ns0="http://CumulativeFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
</ns0:SummedPO>  
```  
  
> [!NOTE]
>  Fonctoids cumulés (à l’exception de la **Chaîne cumulée** fonctoid) ignore les entrées non numériques. Par exemple, une valeur d’entrée de « trois » est ignorée.  
  
 Le **moyenne cumulée**, **Minimum cumulé**, et **Maximum cumulé** fonctoids se comportent de la même façon que les **somme cumulée** fonctoid. Le **Chaîne cumulée** concatène les chaînes plutôt que des valeurs numériques.  

## <a name="available-functoids"></a>Fonctoids disponibles
  
 Le **Cumulative** fonctoids sont : 

* Moyenne cumulée
* Concaténation cumulée
* Maximum cumulé
* Minimum cumulé
* Somme cumulée

Plus d’informations sur ces fonctoids [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="see-also"></a>Voir aussi  
-  [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)   
-  **Référence des fonctoids cumulés**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]