---
title: "Fonctoid Itération | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Iteration functoids
- Greater Than or Equal To functoids
- And functoids
- Less Than or Equal To functoids
ms.assetid: 24d8911d-2282-4b07-910c-eb2e846dc1f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a491b8829f23296e77ba5a89d12985e8ccd32783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="iteration-functoid"></a>Fonctoid Itération
Le **itération** fonctoid sorties commençant à 1 pour le premier enregistrement, 2 pour le deuxième enregistrement de la structure de l’index de l’enregistrement actif dans une boucle et ainsi de suite.  
  
 L’illustration suivante montre un **itération** fonctoid combiné avec un **supérieur ou égal à** fonctoid, un **inférieure ou égale à** fonctoid et un **et**  fonctoid pour créer l’équivalent d’un **pour** boucle.  
  
 ![Mappage illustrant l’utilisation du fonctoid itération](../core/media/iterationfunctoid.gif "iterationfunctoid")  
Mappage du fonctoid Itération  
  
 Supposent que le **supérieur ou égal à** teste fonctoid supérieur ou égal à 2 et le **inférieure ou égale à** des tests pour le fonctoid inférieur ou égal à 4 valeurs. Dans ce cas, le **et** fonctoid retournera **true** uniquement pour les enregistrements de 2, 3 et 4. Par conséquent, l’instance de sortie contiendra enregistre les deux, trois et quatre du message d’instance d’entrée.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids itération à un mappage](../core/how-to-add-iteration-functoids-to-a-map.md)   
 [Fonctoids avancés](../core/advanced-functoids.md)   
 [Fonctoid Index](../core/index-functoid.md)   
 [Fonctoid Bouclage](../core/looping-functoid.md)   
 [Fonctoid Nombre d’enregistrements](../core/record-count-functoid.md)