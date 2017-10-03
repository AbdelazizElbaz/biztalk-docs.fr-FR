---
title: "Étendues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scopes, exception handling
- Scope shape [Orchestration Designer], nesting
- scopes, variables
- scopes, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], exception handling
- scopes, transactions
- scopes, synchronization
- scopes, nesting
- Scope shape [Orchestration Designer], transactions
ms.assetid: 51d81ce4-0034-4415-b6ab-4c952737c1bd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc4d1b5d926540477293591ade8123126be1b84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scopes"></a>Étendues
Une étendue est une structure de regroupement des actions. Elle est utilisée principalement pour l'exécution transactionnelle et la gestion des exceptions.  
  
 Une étendue contient un ou plusieurs blocs. Elle se compose d'un corps et peut se voir éventuellement associée à un certain nombre de blocs de gestion d'exception. Elle peut également comporter un bloc de compensation facultatif, en fonction de sa nature. Certaines étendues, entièrement destinées à la gestion d'exception, ne requièrent pas de compensation. D'autres, explicitement transactionnelles, comportent toujours un gestionnaire de compensation par défaut, ainsi qu'un gestionnaire de compensation facultatif créé par vos soins. Une étendue transactionnelle dispose, enfin, d'un gestionnaire d'exception par défaut, et d'un certain nombre de gestionnaires d'exception supplémentaires que vous aurez créés.  
  
## <a name="synchronized-scopes"></a>Étendues synchronisées  
 Les étendues peuvent être ou non synchronisées. La synchronisation d'une étendue permet de garantir que, lorsqu'un processus accède aux données partagées qu'elle contient, aucune des actions parallèles de votre orchestration ne peut y accéder en écriture. De même, aucun accès en écriture n'est possible lorsqu'une autre action y accède en lecture.  
  
 Les étendues de transaction atomique sont toujours synchronisées. Toutes les actions au sein d'une étendue synchronisée sont considérées comme synchronisées, tout comme les actions de ses gestionnaires d'exception. Les actions du gestionnaire de compensation d'une étendue transactionnelle, quant à elles, ne sont pas synchronisées.  
  
> [!CAUTION]
>  Notez que vous pouvez rencontrer une situation de blocage si vos processus ne sont pas correctement conçus. Par exemple, deux branches d'une action parallèle dans une orchestration A accèdent au même message, la première pour l'envoyer, la seconde pour le recevoir. Leur étendue doit donc être synchronisée. Une deuxième orchestration reçoit le message et le renvoie. Il est possible que la branche chargée de l'envoi dans l'orchestration A reçoive ses verrous avant la branche de réception, aboutissant à une situation de blocage.  
  
## <a name="nesting-of-scopes"></a>Imbrication d'étendues  
 Vous pouvez imbriquer des **étendue** formes dans les autres **étendue** formes. Les règles d'imbrication sont les suivantes :  
  
-   Il n'est pas possible d'imbriquer des étendues transactionnelles et/ou synchronisées dans des étendues synchronisées, y compris les gestionnaires d'exception des étendues synchronisées.  
  
-   Aucune étendue transactionnelle ne peut être imbriquée dans une étendue de transaction atomique.  
  
-   Aucune étendue transactionnelle ne peut être imbriquée dans une orchestration ou une étendue non transactionnelle.  
  
-   L'imbrication peut atteindre une profondeur maximale de 21 niveaux.  
  
-   **Appeler Orchestration** formes peuvent être inclus dans les étendues, mais les orchestrations appelées sont traitées le même que toute autre instruction transaction imbriquée, et les mêmes règles s’appliquent.  
  
-   **Démarrer l’Orchestration** formes peuvent être inclus dans les étendues. Les orchestrations démarrées ne sont concernées par aucune des limitations d'imbrication.  
  
## <a name="scope-variables"></a>Variables de l'étendue  
 Vous pouvez déclarer des variables, telles que des messages et des ensembles de corrélations, au niveau de l'étendue. Une variable d'étendue et une variable d'orchestration ne peuvent toutefois pas porter le même nom. Le masquage de nom n'est pas autorisé.  
  
## <a name="see-also"></a>Voir aussi  
 [L’utilisation de Transactions et la gestion des Exceptions](../core/using-transactions-and-handling-exceptions.md)   
 [Transactions atomiques](../core/atomic-transactions.md)