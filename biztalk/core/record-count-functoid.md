---
title: "Fonctoid Nombre d’enregistrements | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- Record Count functoids
ms.assetid: e6aab13f-afbe-4401-abbe-020570e2ff16
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87653709bf5d52c21537064bad286078ad625cf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="record-count-functoid"></a>Fonctoid Nombre d’enregistrements
Le **nombre d’enregistrements** fonctoid Nombre d’enregistrements dans le message d’instance d’entrée.  
  
 Le **nombre d’enregistrements** fonctoid comporte une entrée et une sortie. L’entrée est un lien dans l’enregistrement de boucle du schéma source. La sortie de la **nombre d’enregistrements** fonctoid est le nombre de l’enregistrement de boucle dans un message d’instance d’entrée réel.  
  
 Les enregistrements de boucle correspondent à des éléments qui se répètent un nombre imprévisible de fois dans un message d’instance d’entrée. Par exemple, dans un bon de commande, le **élément** élément peut se produire plusieurs fois. Et le **élément** élément peut inclure des produits, les descriptions, les prix et les quantités. Le code suivant est un exemple simplifié d'un bon de commande de ce type.  
  
```  
<ns0:PurchaseOrder xmlns:ns0="http://RecordFunctoid.PurchaseOrder">  
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
  
 Le **Max Occurs** propriété pour le **élément** enregistrement est défini comme non liée. Cela indique que le **élément** enregistrement boucle et que le Mappeur BizTalk compile cet enregistrement sous forme de boucle.  
  
 Supposons que vous souhaitez trouver le nombre total de **élément** le message, les éléments dans l’instance d’entrée de commande fournisseur et placer le résultat dans un champ dans le message d’instance de sortie.  
  
 L’illustration suivante montre un **nombre d’enregistrements** fonctoid qui compte le nombre d’éléments dans un bon de commande entrant et de placer cette valeur la **ItemCount** champ dans le **SummedPO**message d’instance de sortie.  
  
 ![Mappage illustrant l’utilisation du fonctoid Nombre d’enregistrements. ] (../core/media/recordcountfunctoid.gif "recordcountfunctoid")  
Mappage du fonctoid Nombre d'enregistrements  
  
 Notez que la **Max Occurs** propriété pour le **élément** enregistrement serait **unbounded**. Cela indique que le **élément** enregistrement boucle et que le Mappeur BizTalk compile cet enregistrement sous forme de boucle.  
  
 Pour le message d’instance précédent exemple bon ordre, qui comportait deux **élément** éléments, la valeur de la **ItemCount** champ sera défini à 2.  
  
```  
<ns0:SummedPO xmlns:ns0="http://RecordCountFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
    <ItemCount>2</ItemCount>  
</ns0:SummedPO>  
```  
  
> [!NOTE]
>  Vous pouvez également utiliser le **nombre d’enregistrements** fonctoid pour compter les éléments de champ répétés. Il ne se limite pas aux enregistrements.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids nombre d’enregistrements à une carte](../core/how-to-add-record-count-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Index](../core/index-functoid.md)   
 [Fonctoid Itération](../core/iteration-functoid.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)