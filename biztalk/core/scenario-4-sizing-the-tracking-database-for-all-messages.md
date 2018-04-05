---
title: 'Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: db1126c7-0b86-4635-bfdc-3b69a82cc64b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 327953843b2d9b70f500796f43302320924a330c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-4-sizing-the-tracking-database-for-all-messages"></a>Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages
Si ces trois scénarios se présentent dans une implémentation de Microsoft® BizTalk Server® 2004, il faut ajouter les résultats obtenus pour chaque scénario afin de déterminer la taille de la base de données des suivis BizTalk.  
  
 D'après les exemples précédents :  
  
|Scénario|Espace requis par an en Go|  
|--------------|-------------------------------------|  
|Messages simples|4.78|  
|Messages passant par des orchestrations|7.18|  
|Messages passant par des orchestrations et envoyés vers des listes de distribution|10.8|  
|**Total**|22.04|  
  
 Si le suivi du corps des messages est activé dans les trois scénarios, les résultats sont les suivants :  
  
|Scénario|Espace requis par an en Go|  
|--------------|-------------------------------------|  
|Messages simples|50.1|  
|Messages passant par des orchestrations|50.1|  
|Messages passant par des orchestrations et envoyés vers des listes de distribution|83.45|  
|**Total**|183.65|  
  
 On obtient donc une augmentation totale de 205,69 Go par an pour la base de données des suivis BizTalk. Dans cet exemple, aucun imprévu n'est pris en compte. C'est pourquoi il est recommandé d'ajouter 10 % à la taille totale obtenue. Vous pouvez donc compter sur une augmentation de la base de données des suivis BizTalk de 227,94 Go par an. En plus de cela, vous devez envisager la surcharge en raison de l’index SQL, stockage, etc.. Vous devez baser le facteur multiplicateur après avoir exécuté les scénarios de test dans test si possible.  
  
## <a name="other-factors-affecting-biztalk-tracking-database-size"></a>Autres facteurs ayant une incidence sur la taille de la base de données des suivis BizTalk  
 Des éléments tels que les formes utilisées au sein d'une orchestration ont également une incidence sur la taille de la base de données des suivis BizTalk.  
  
 Lorsque l'option de débogage d'orchestration est activée (configuration par défaut), l'état de chaque forme de l'orchestration est enregistré dans la base de données des suivis BizTalk.  
  
 La formule permettant de calculer la taille requise pour le suivi de l'état de la forme est la suivante :  
  
```  
[(# of object shapes ] * 76 bytes  
```  
  
 Dans l'exemple ci-dessous, la formule suivante doit être utilisée pour déterminer la taille de la base de données des suivis BizTalk :  
  
```  
((4) * 76 bytes = 304 bytes  
```  
  
 ![Exemple d’orchestration](../core/media/sample-orchestration.gif "Sample_orchestration")  
  
 En admettant que cette orchestration traite 3,5 millions de messages, l'espace supplémentaire requis pour en effectuer le suivi doit être de :  
  
```  
304 bytes * 3,500,000/1024/1024 = 1015 MB ~ 0.99 GB.  
```  
  
 Il est nécessaire de prendre en compte toutes les orchestrations pour lesquelles le débogage est activé afin d'obtenir une estimation de la taille de la base de données des suivis BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md)   
 [Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)