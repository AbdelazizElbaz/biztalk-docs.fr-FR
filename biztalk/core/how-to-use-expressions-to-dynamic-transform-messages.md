---
title: Comment utiliser des Expressions pour transformer dynamiquement des Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48387d97-9312-4df5-b614-727ea9035bf8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9d16c38fefb4e2732bd05f7c3489acaa8ca645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-dynamic-transform-messages"></a>Utilisation d'expressions pour transformer dynamiquement les messages
Vous pouvez utiliser des expressions pour transformer dynamiquement des messages dans votre orchestration. XLANG expose une méthode qui peut être appelée à partir d’un **assignation du Message** mettre en forme à l’intérieur d’un **construire un Message** forme. C’est la même méthode qui est appelée lorsqu’un **transformer** forme est utilisé, mais vous permet de transformer les messages à l’aide de la carte que vous avez désigné dans l’orchestration par programme. Cela est utile lorsque vous traitez des messages indépendamment de tout type. Par exemple, si votre processus d'entreprise doit choisir un mappage pour transformer des messages entrants en fonction des paramètres fournis par les messages entrants reçus, vous pouvez faire appel à la méthode de transformation de la forme Expression et garantir l'intégrité de votre processus d'entreprise dans son ensemble.  
  
## <a name="transforming-messages"></a>Transformation des messages  
 Vous pouvez utiliser l’exemple de code suivant à transformer par programme les messages dans la **assignation du Message** forme :  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg);  
```  
  
 Dans cet exemple, MyMapType est déclaré en tant que variable de type **System.Type** dans l’orchestration. MyMapName est le nom du mappage créé dans votre projet BizTalk. Pour référencer un mappage figurant dans un assembly BizTalk distinct, vous devrez référencer l'assembly concerné dans votre projet BizTalk. MyInputMsg est le message source et MyOutputMsg le message de destination. Si votre mappage contient plusieurs messages sources, utilisez l'exemple de code suivant pour transformer les messages :  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg1, MyInputMsg2);  
```  
  
> [!NOTE]
>  En cas de messages sources multiples, ces derniers doivent figurer dans l'expression dans l'ordre correspondant au numéro de partie de message indiqué dans le mappage.  
  
> [!IMPORTANT]
>  Lors de la transformation dynamique de messages dans la forme Expression, il est recommandé d'écrire un cache dans le code utilisateur pour mettre en mémoire cache les mappages compilés, puis de vous en servir dans la forme Expression pour récupérer les mappages avant la transformation des messages. Sans cette opération, la mémoire CLR (Common Language Runtime) risque d'être saturée. En effet, lors du mappage dynamique, le composant d'exécution .NET Runtime vérifie l'accès du code et place un objet .NET Evidence dans le tas des objets volumineux lors de chaque transformation. Cet objet est conservé jusqu'à la fin de l'orchestration. Lorsque ces transformations sont effectuées en grand nombre simultanément, la mémoire croît de manière conséquente jusqu'à générer une exception « mémoire insuffisante ».  
  
## <a name="see-also"></a>Voir aussi  
 [Formes d’orchestration](../core/orchestration-shapes.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)