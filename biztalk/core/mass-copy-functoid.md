---
title: Copie de masse fonctoid | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- anyAttribute node
- Mass Copy functoids, about Mass Copy functoids
- any node
- Mass Copy functoids
ms.assetid: 228ff569-2e21-4e81-b564-6936241cdf6b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe0a9bc65369327a17591fb6adecb6bd6105333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mass-copy-functoid"></a><span data-ttu-id="b57cd-102">Fonctoid Copie de masse</span><span class="sxs-lookup"><span data-stu-id="b57cd-102">Mass Copy Functoid</span></span>
<span data-ttu-id="b57cd-103">Le **copie de masse** fonctoid permet d’utiliser les schémas incluant vos mappages **tout** et **anyAttribute** éléments.</span><span class="sxs-lookup"><span data-stu-id="b57cd-103">The **Mass Copy** functoid enables your maps to use schemas that include **any** and **anyAttribute** elements.</span></span> <span data-ttu-id="b57cd-104">Ces éléments sont, par essence, des caractères génériques fournis par le langage de définition du schéma XML pour remplacer des structures ou des attributs non connus.</span><span class="sxs-lookup"><span data-stu-id="b57cd-104">These elements are, in essence, wildcards provided in the XML Schema definition language to match unknown structures or attributes.</span></span>  
  
 <span data-ttu-id="b57cd-105">En plus de gérer les données dont la structure est inconnue, le **copie de masse** fonctoid vous permet de simplifier le développement du schéma : seules les parties d’un schéma qui seront traités doivent être spécifiées en détail.</span><span class="sxs-lookup"><span data-stu-id="b57cd-105">In addition to handling data with unknown structure, the **Mass Copy** functoid enables you to simplify schema development: only the portions of a schema that will be processed need to be specified in detail.</span></span>  
  
 <span data-ttu-id="b57cd-106">Le **copie de masse** fonctoid copie de l’élément dans le message d’instance d’entrée correspondant au nœud de schéma source connecté à la **copie de masse** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="b57cd-106">The **Mass Copy** functoid copies the element in the input instance message corresponding to the source schema node connected to the **Mass Copy** functoid.</span></span> <span data-ttu-id="b57cd-107">Le fonctoid copie également l'élément tout et ses sous-structures et les recrée dans le message d'instance de sortie sur le nœud lié du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="b57cd-107">The functoid also copies any and all of its substructure, and re-creates it in the output instance message at the linked node in the destination schema.</span></span> <span data-ttu-id="b57cd-108">Par conséquent, vous pouvez également utiliser le **copie de masse** fonctoid copie de tous les enregistrements de source et de destination présentant des sous-structures identiques.</span><span class="sxs-lookup"><span data-stu-id="b57cd-108">Thus, you can also use the **Mass Copy** functoid to copy any source and destination records having identical substructures.</span></span>  
  
 <span data-ttu-id="b57cd-109">L’illustration suivante montre le **copie de masse** fonctoid utilisé dans un mappage.</span><span class="sxs-lookup"><span data-stu-id="b57cd-109">The following figure shows the **Mass Copy** functoid used in a map.</span></span>  
  
 <span data-ttu-id="b57cd-110">![Mappage illustrant l’utilisation du fonctoid copie de masse](../core/media/masscopyfunctoid.gif "masscopyfunctoid")</span><span class="sxs-lookup"><span data-stu-id="b57cd-110">![Map illustrating the use of the mass copy functoid](../core/media/masscopyfunctoid.gif "masscopyfunctoid")</span></span>  
<span data-ttu-id="b57cd-111">Mappage du fonctoid Copie de masse</span><span class="sxs-lookup"><span data-stu-id="b57cd-111">Mass Copy Functoid Map</span></span>  
  
 <span data-ttu-id="b57cd-112">Considérez le message d’instance d’entrée suivant.</span><span class="sxs-lookup"><span data-stu-id="b57cd-112">Consider the following input instance message.</span></span>  
  
```  
<ns0:Root xmlns:ns0="http://MassCopy.ComplexDocument">  
    <PurchaseOrder>  
        <From>Kevin F. Browne</From>  
        <To>Northwind Traders</To>  
        <LineItems>  
            <Item>  
                <Product>Laptop Computer</Product>  
                <Description>Thin profile laptop</Description>  
                <Price>1999.95</Price>  
                <Quantity>1</Quantity>  
            </Item>  
        </LineItems>  
    </PurchaseOrder>  
</ns0:Root>  
```  
  
 <span data-ttu-id="b57cd-113">Si le mappage précédent était utilisé pour traiter ce message, le message d’instance de sortie serait identique au message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="b57cd-113">If the preceding map were used to process this message, the output instance message would be identical to the input instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b57cd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b57cd-114">See Also</span></span>  
 <span data-ttu-id="b57cd-115">[Ajout de fonctoids copie de masse à une carte](../core/how-to-add-mass-copy-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="b57cd-115">[How to Add Mass Copy Functoids to a Map](../core/how-to-add-mass-copy-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="b57cd-116">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="b57cd-116">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="b57cd-117">[Fonctoids de base](../core/basic-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="b57cd-117">[Basic Functoids](../core/basic-functoids.md) </span></span>  
 [<span data-ttu-id="b57cd-118">Liens vers et à partir de tout élément et tout attribut nœuds</span><span class="sxs-lookup"><span data-stu-id="b57cd-118">Links To and From the Any Element and anyAttribute Nodes</span></span>](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)