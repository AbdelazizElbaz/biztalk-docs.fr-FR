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
# <a name="record-count-functoid"></a><span data-ttu-id="1edd8-102">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="1edd8-102">Record Count Functoid</span></span>
<span data-ttu-id="1edd8-103">Le **nombre d’enregistrements** fonctoid Nombre d’enregistrements dans le message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1edd8-103">The **Record Count** functoid counts records in the input instance message.</span></span>  
  
 <span data-ttu-id="1edd8-104">Le **nombre d’enregistrements** fonctoid comporte une entrée et une sortie.</span><span class="sxs-lookup"><span data-stu-id="1edd8-104">The **Record Count** functoid has one input and one output.</span></span> <span data-ttu-id="1edd8-105">L’entrée est un lien dans l’enregistrement de boucle du schéma source.</span><span class="sxs-lookup"><span data-stu-id="1edd8-105">The input is a link from a looping record in the source schema.</span></span> <span data-ttu-id="1edd8-106">La sortie de la **nombre d’enregistrements** fonctoid est le nombre de l’enregistrement de boucle dans un message d’instance d’entrée réel.</span><span class="sxs-lookup"><span data-stu-id="1edd8-106">The output of the **Record Count** functoid is the count of the looping record in an actual input instance message.</span></span>  
  
 <span data-ttu-id="1edd8-107">Les enregistrements de boucle correspondent à des éléments qui se répètent un nombre imprévisible de fois dans un message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="1edd8-107">Looping records correspond to elements that repeat an unpredictable number of times in an input instance message.</span></span> <span data-ttu-id="1edd8-108">Par exemple, dans un bon de commande, le **élément** élément peut se produire plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="1edd8-108">For example, in a purchase order, the **Item** element might occur many times.</span></span> <span data-ttu-id="1edd8-109">Et le **élément** élément peut inclure des produits, les descriptions, les prix et les quantités.</span><span class="sxs-lookup"><span data-stu-id="1edd8-109">And, the **Item** element might include products, descriptions, prices, and quantities.</span></span> <span data-ttu-id="1edd8-110">Le code suivant est un exemple simplifié d'un bon de commande de ce type.</span><span class="sxs-lookup"><span data-stu-id="1edd8-110">The following code is a simplified example of such a purchase order.</span></span>  
  
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
  
 <span data-ttu-id="1edd8-111">Le **Max Occurs** propriété pour le **élément** enregistrement est défini comme non liée.</span><span class="sxs-lookup"><span data-stu-id="1edd8-111">The **Max Occurs** property for the **Item** record is set as unbounded.</span></span> <span data-ttu-id="1edd8-112">Cela indique que le **élément** enregistrement boucle et que le Mappeur BizTalk compile cet enregistrement sous forme de boucle.</span><span class="sxs-lookup"><span data-stu-id="1edd8-112">This indicates that the **Item** record loops, and BizTalk Mapper compiles this record as a loop.</span></span>  
  
 <span data-ttu-id="1edd8-113">Supposons que vous souhaitez trouver le nombre total de **élément** le message, les éléments dans l’instance d’entrée de commande fournisseur et placer le résultat dans un champ dans le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="1edd8-113">Suppose you want to find the total number of **Item** elements in the purchase order input instance message and place the result in a field in the output instance message.</span></span>  
  
 <span data-ttu-id="1edd8-114">L’illustration suivante montre un **nombre d’enregistrements** fonctoid qui compte le nombre d’éléments dans un bon de commande entrant et de placer cette valeur la **ItemCount** champ dans le **SummedPO**message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="1edd8-114">The following figure shows a **Record Count** functoid that counts the number of items in an incoming purchase order and puts that value in the **ItemCount** field in the **SummedPO** output instance message.</span></span>  
  
 <span data-ttu-id="1edd8-115">![Mappage illustrant l’utilisation du fonctoid Nombre d’enregistrements. ] (../core/media/recordcountfunctoid.gif "recordcountfunctoid")</span><span class="sxs-lookup"><span data-stu-id="1edd8-115">![Map showing the use of the record count functoid.](../core/media/recordcountfunctoid.gif "recordcountfunctoid")</span></span>  
<span data-ttu-id="1edd8-116">Mappage du fonctoid Nombre d'enregistrements</span><span class="sxs-lookup"><span data-stu-id="1edd8-116">Record Count Functoid Map</span></span>  
  
 <span data-ttu-id="1edd8-117">Notez que la **Max Occurs** propriété pour le **élément** enregistrement serait **unbounded**.</span><span class="sxs-lookup"><span data-stu-id="1edd8-117">Notice that the **Max Occurs** property for the **Item** record would be **unbounded**.</span></span> <span data-ttu-id="1edd8-118">Cela indique que le **élément** enregistrement boucle et que le Mappeur BizTalk compile cet enregistrement sous forme de boucle.</span><span class="sxs-lookup"><span data-stu-id="1edd8-118">This indicates that the **Item** record loops, and BizTalk Mapper compiles this record as a loop.</span></span>  
  
 <span data-ttu-id="1edd8-119">Pour le message d’instance précédent exemple bon ordre, qui comportait deux **élément** éléments, la valeur de la **ItemCount** champ sera défini à 2.</span><span class="sxs-lookup"><span data-stu-id="1edd8-119">For the preceding sample purchase order instance message, which contained two **Item** elements, the value of the **ItemCount** field will be set to 2.</span></span>  
  
```  
<ns0:SummedPO xmlns:ns0="http://RecordCountFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
    <ItemCount>2</ItemCount>  
</ns0:SummedPO>  
```  
  
> [!NOTE]
>  <span data-ttu-id="1edd8-120">Vous pouvez également utiliser le **nombre d’enregistrements** fonctoid pour compter les éléments de champ répétés.</span><span class="sxs-lookup"><span data-stu-id="1edd8-120">You can also use the **Record Count** functoid to count repeating field elements.</span></span> <span data-ttu-id="1edd8-121">Il ne se limite pas aux enregistrements.</span><span class="sxs-lookup"><span data-stu-id="1edd8-121">It is not restricted to records.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1edd8-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1edd8-122">See Also</span></span>  
 <span data-ttu-id="1edd8-123">[Ajout de fonctoids nombre d’enregistrements à une carte](../core/how-to-add-record-count-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="1edd8-123">[How to Add Record Count Functoids to a Map](../core/how-to-add-record-count-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="1edd8-124">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="1edd8-124">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="1edd8-125">[Fonctoid Index](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="1edd8-125">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="1edd8-126">[Fonctoid Itération](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="1edd8-126">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 [<span data-ttu-id="1edd8-127">Fonctoid Bouclage</span><span class="sxs-lookup"><span data-stu-id="1edd8-127">Looping Functoid</span></span>](../core/looping-functoid.md)