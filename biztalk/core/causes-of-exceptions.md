---
title: Causes des Exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, errors
- errors, orchestrations
- errors, causes
ms.assetid: b0422382-d034-4c58-87c6-fc269dbbfe43
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9006234d71751078269e5a88559839fdadd91e91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="causes-of-exceptions"></a>Causes des exceptions 
Les exceptions peuvent être générées dans une orchestration de plusieurs façons :  
  
-   Par un **lever Exception** forme, qui lève une exception immédiatement et sans condition. Le contrôle passe à partir de la **lever Exception** forme directement au gestionnaire d’exceptions approprié.  
  
-   Par expiration du délai d'attente dans une transaction longue. Une exception système prédéfinies :**Microsoft.XLANG.BaseTypes.TimeOutException**— est levée dans ce cas.  
  
-   Par d'autres échecs de transaction. Pour ces échecs, le moteur d'exécution lève un message défini par le système du type Microsoft.XLANG.BaseTypes.PersistenceException.  
  
-   Par une exception de code utilisateur. Lorsque des appels vers le code utilisateur externe sont effectués dans une orchestration, les classes du Common Language Runtime appelées peuvent lever des exceptions. Si ces exceptions ne sont pas gérées dans le code utilisateur, elles se propagent finalement dans l'étendue dans laquelle l'appel vers le code utilisateur est effectué.  
  
-   Par d'autres exceptions système (par exemple, un échec de persistance, une autre exception système ou .NET telle qu'une exception de chargeur de type, ou une erreur de conversion des données).  
  
> [!NOTE]
>  Lorsqu’une exception de chargeur de type est levée, l’exception ne peut pas être interceptée dans le **intercepter l’Exception** bloquer dans la même **étendue** forme. Cela est dû au fait que l'exception provient du chargeur de type, et non pas du processus d'orchestration  BizTalk. En conséquence, elle ne suit pas les règles BizTalk de flux de contrôle.  
  
-   Par une branche frère dans une étendue voisine interrompant l'exécution. Dans ce cas, l'exception Microsoft.XLANG.BaseTypes.ForcedTerminationException est levée pour chaque branche, et vous pouvez ajouter un gestionnaire d'exceptions à chacune d'elles. Un gestionnaire d'exceptions de ce type ne peut ni lever à nouveau son exception, ni lever d'autres types d'exception.  
  
-   Par réception d'un message externe indiquant une erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur](../core/fault-messages.md)   
 [Exceptions](../core/exceptions.md)