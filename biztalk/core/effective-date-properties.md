---
title: "Propriétés de la Date d’effet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- effective-dated items
- getHistoryItems parameter
- Effective Date
- EFFDT
- planned items, scheduling and tracking
ms.assetid: 0d9a153c-7ea5-41cf-9e4e-055e1c18f64b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34f1c4cf3579a3381c846ddbb9896b2e5be26f6b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="effective-date-properties"></a>Propriétés de la Date d’effet
PeopleSoft Enterprise permet de planifier et d'assurer le suivi d'éléments planifiés à l'aide d'une propriété spécifique nommée Date d'effet (abrégée par EFFDT). De tels éléments sont soit effectifs, soit planifiés, selon que leur date soit antérieure ou ultérieure à la date actuelle de PeopleSoft.  
  
 Si les propriétés d'une interface de composant contiennent des éléments à date d'effet (c'est-à-dire un champ nommé EFFDT), l'adaptateur permet aux appelants de récupérer l'intégralité des valeurs ou uniquement les valeurs qui n'ont pas encore pris effet (et qui sont donc toujours modifiables).  
  
## <a name="gethistoryitems-parameter"></a>Paramètre getHistoryItems  
 Dans les interfaces de composant dont les propriétés incluent une date d'effet, l'adaptateur fournit un paramètre supplémentaire nommé `getHistoryItems` aux opérations « Get ». Ce paramètre est de type booléen ; s'il est défini sur True, tous les éléments ayant une date d'effet sont renvoyés, Ceux-ci incluent tous les auparavant, les éléments à date d’effet actuels et futurs.  
  
 Si le paramètre `getHistoryItems` est défini sur False, seuls les éléments actuels et futurs ayant une date d'effet sont renvoyés. Sélectionnez False si vous envisagez d'ajouter ou de modifier ces éléments (car il est impossible de modifier des éléments passés).  
  
 Il est également possible que plusieurs éléments à date d'effet possèdent la même date d'effet. Dans ce cas, une propriété supplémentaire, Séquence d'effet (EFFSEQ), doit également être fournie. Les valeurs de la propriété EFFSEQ doivent être uniques afin de différencier les éléments possédant la même date d'effet. Pour plus d'informations, consultez la documentation de PeopleSoft.  
  
## <a name="modifying-past-effective-dated-items"></a>Modification des éléments passés ayant une date d'effet  
 Le `correctionMode` argument à la fois dans le [UpdateEx](../core/updateex-method.md) et [DeleteOnly](../core/deleteonly-method.md) méthodes permettent de contrôler si les derniers éléments peuvent être modifiés. S'il est défini sur True, tous les éléments peuvent être modifiés. Sinon, la modification d'un élément passé associé à une date d'effet génère une exception.  
  
 Lors de l'appel de la méthode `Update` supprimée sur une interface de composant dotée d'éléments à date d'effet, vous devez veiller à ne pas inclure les dates d'effet d'une valeur antérieure à la date d'effet actuelle de PeopleSoft. Sinon, l'appel échoue en générant une exception. Cependant, l'élément actuel ayant une date d'effet peut être inclus car il est contourné lors de la définition des propriétés. Si une séquence d'effet existe, tous les éléments actuels à date d'effet du serveur (dont les séquences d'effet correspondent) sont ignorés lors de la définition des propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe a : méthodes d’Interface de composant](../core/appendix-a-component-interface-methods.md)