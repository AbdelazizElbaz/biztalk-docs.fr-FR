---
title: "Utilisation d’opérateurs dans des Expressions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, operators
- XLANG/s, operators
- orchestrations, XLANG/s
ms.assetid: f0948ce2-c508-48aa-af79-d207f577b22f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 155aad11ecddd021b8e16892b5a5294087fedd4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-operators-in-expressions"></a>Utilisation d'opérateurs dans les expressions
Les opérateurs XLANG/s suivants peuvent être utilisés dans les expressions des orchestrations. Ils sont strictement conformes à la fonction des opérateurs correspondants en C#.  
  
|Opérateur| Description|Exemple|  
|--------------|-----------------|-------------|  
|checked()|signale une erreur de dépassement arithmétique positif|checked(x = y * 1000)|  
|unchecked()|ignore l'erreur de dépassement arithmétique positif|unchecked(x = y * 1000)|  
|new|créer une instance d'une classe|myObject = new MyClass;|  
|typeof|récupération de type|myMapType = typeof(myMap)|  
|succeeded()|test de réussite d'étendue transactionnelle ou d'orchestration|a réussi (\<ID de transaction enfant de l’étendue actuelle ou de service >)|  
|existe|vérifie l'existence d'une propriété de contexte de message|BTS.RetryCount exists Message_In|  
|+|plus unaire|+(int x)|  
|-|moins unaire|-(int x)|  
|!|négation logique|!myBool|  
|~|complément de bits|x = ~y|  
|()|Cast|(bool) myInt|  
|*|times|Poids = MyMsg.numOrders * 20|  
|/|divisé par|x / y|  
|+|plus|x + y|  
|-|moins|x - y|  
|<<|décalage vers la gauche|x <\< 2|  
|>>|décalage vers la droite|x >> 2|  
|<|inférieur à|Si (MyMsg.numOrders \< 10)...|  
|>|supérieur à|Si (MyMsg.numOrders > 10)...|  
|<=|inférieur ou égal à|Si (MyMsg.numOrders \<= 10)...|  
|>=|supérieur ou égal à|Si (MyMsg.numOrders > = 10)...|  
|==|égal à|If (MyMsg.numOrders == 10)...|  
|!=|différent de|If (MyMsg.numOrders != 10)...|  
|&|et|If (myByte & 255)...|  
|^|or exclusif|If (myByte ^ 1)...|  
|&#124;|ou|Si (myByte &#124; 1)...|  
|&&|and conditionnel|If (MyMsg.numOrders > 10) && (MyMsg.numOrders < 100)|  
|&#124;&#124;|or conditionnel|Si (MyMsg.numOrders \< 10) &#124; &#124; (MyMsg.numOrders > 100)|  
|//|commentaire|//Ceci est le commentaire|  
  
> [!NOTE]
>  Les règles diffèrent entre les expressions générales et les expressions de filtre qui sont utilisées avec la **réception** forme.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des filtres avec la forme d’un Message de réception](../core/using-filters-with-the-receive-message-shape.md)