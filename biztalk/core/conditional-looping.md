---
title: Bouclage conditionnel | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Looping functoids, conditional
- Equal functoids
- maps, conditional looping
ms.assetid: eb16efb8-b12c-47d6-afc9-579fc85ea59c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5452f6b8768442b95ac6bddde0e84ba07f68c85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conditional-looping"></a>Bouclage conditionnel
Vous pouvez ajouter des conditions à un **bouclage** fonctoid en liant la sortie d’un **bouclage** fonctoid et un **logiques** fonctoid au même enregistrement de destination. Les enregistrements de destination sont créés uniquement lorsque la condition logique est remplie.  
  
## <a name="conditional-looping-map"></a>Mappage de bouclage conditionnel  
 ![Mappage qui illustre un fonctoid Bouclage conditionnel. ] (../core/media/loopingconditionalfunctoid.gif "loopingconditionalfunctoid")  
  
 Dans la figure précédente, la première **égal** fonctoid compare le **nom** champ sous **FoodSurvey** à « Wendy Wheeler ». La seconde **égal** fonctoid compare le **nom** champ sous **FlowerSurvey** à « Kelly Focht ». Par conséquent, le mappage crée la destination **adresse** enregistrements uniquement pour les deux noms. À l’aide de l’exemple de données à partir de la **bouclage** exemple de fonctoid, le message d’instance de sortie s’affiche comme suit.  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://ConditionalLoop.MasterAddresses">  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290">  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406">  
</ns0:MasterAddresses>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment ajouter des fonctoids à une carte de bouclage](../core/how-to-add-looping-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Index](../core/index-functoid.md)   
 [Fonctoid Itération](../core/iteration-functoid.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)   
 [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)