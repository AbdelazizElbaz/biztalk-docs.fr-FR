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
# <a name="mass-copy-functoid"></a>Fonctoid Copie de masse
Le **copie de masse** fonctoid permet d’utiliser les schémas incluant vos mappages **tout** et **anyAttribute** éléments. Ces éléments sont, par essence, des caractères génériques fournis par le langage de définition du schéma XML pour remplacer des structures ou des attributs non connus.  
  
 En plus de gérer les données dont la structure est inconnue, le **copie de masse** fonctoid vous permet de simplifier le développement du schéma : seules les parties d’un schéma qui seront traités doivent être spécifiées en détail.  
  
 Le **copie de masse** fonctoid copie de l’élément dans le message d’instance d’entrée correspondant au nœud de schéma source connecté à la **copie de masse** fonctoid. Le fonctoid copie également l'élément tout et ses sous-structures et les recrée dans le message d'instance de sortie sur le nœud lié du schéma de destination. Par conséquent, vous pouvez également utiliser le **copie de masse** fonctoid copie de tous les enregistrements de source et de destination présentant des sous-structures identiques.  
  
 L’illustration suivante montre le **copie de masse** fonctoid utilisé dans un mappage.  
  
 ![Mappage illustrant l’utilisation du fonctoid copie de masse](../core/media/masscopyfunctoid.gif "masscopyfunctoid")  
Mappage du fonctoid Copie de masse  
  
 Considérez le message d’instance d’entrée suivant.  
  
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
  
 Si le mappage précédent était utilisé pour traiter ce message, le message d’instance de sortie serait identique au message d’instance d’entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids copie de masse à une carte](../core/how-to-add-mass-copy-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoids de base](../core/basic-functoids.md)   
 [Liens vers et à partir de tout élément et tout attribut nœuds](../core/links-to-and-from-the-any-element-and-anyattribute-nodes.md)