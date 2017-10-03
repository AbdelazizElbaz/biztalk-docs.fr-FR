---
title: "Activités de bouclage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities [BAM], looping activities
- activities [BAM], orchestrations
- orchestrations, looping
- orchestrations, activities
ms.assetid: fb40fdd0-ac8f-486a-b3d0-9d2200a87cda
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f66382a27ed564da0c41257e8abe95accba5e2e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="looping-activities"></a>Activités de bouclage
Les activités de bouclage sont des actions mises en boucle dans une orchestration. Il est possible de capturer les événements d'actions mises en boucle dans une orchestration. Pour ce faire, vous devez créer une autre activité et mapper l'ensemble des données et des étapes majeures de cette nouvelle activité dans la boucle. Cette opération est nécessaire étant donné que le traitement des données dans la boucle se répètera plusieurs fois par exécution planifiée. La figure suivante montre un exemple de cette situation.  
  
 ![](../core/media/handlingloops2.gif "handlingloops2")  
  
 Comme indiqué dans l’illustration, si vous avez un bon de commande comporte plusieurs éléments de ligne traités dans une boucle, les questions du type « les bons de commande doivent prix unitaires de 100 $? » sont ambiguës. Voici ce que seraient des questions sans équivoque :  
  
-   Quels sont les bons de commande contenant des éléments de ligne avec un prix de 100$ ?  
  
-   Quels sont les bons de commande contenant des prix unitaires total/min/max de 100 $ ?  
  
 Pour poser des questions sans ambiguïté, il faut bien distinguer éléments de ligne et bon de commande. Dans l'Éditeur de modèle de suivi, l'activité racine (un bon de commande par exemple) est mappée sur toutes les actions extérieures à la boucle. L’activité enfant (par exemple, élément de ligne) mappe aux actions à l’intérieur de la boucle.  
  
 Vous devez utiliser un élément de charge tel que ActivityID pour l'activité racine. Mettez cet élément de charge à disposition dans quelques-uns des messages de la boucle. Mappez l’activité sur le nœud de relation s’affiche sous l’activité enfant et nommez-le en tant que l’activité racine.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md)