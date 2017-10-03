---
title: "L’utilisation de Transactions et la gestion des Exceptions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions, orchestrations
- orchestrations, transactions
- orchestrations, errors
- transactions
- errors, orchestrations
- transactions, BizTalk Server Orchestration Engine
- errors, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], errors
- Scope shape [Orchestration Designer], transactions
ms.assetid: bb38f5eb-6641-4e7c-8e2a-c474fc739999
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab32729aa6b4f12aada623587f52728c6bd23240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-transactions-and-handling-exceptions"></a>L’utilisation de Transactions et la gestion des Exceptions
Lorsque vous concevez une orchestration, essayez de prévoir les problèmes qui pourront surgir et comment les résoudre au mieux. Les orchestrations ont souvent plusieurs points faibles potentiels. Les problèmes peuvent avoir des causes diverses : ils peuvent par exemple être liés à l'arrêt d'un serveur ou au mauvais formatage d'un message.  
  
 Avec les orchestrations longues ou complexes, il est particulièrement important d'effectuer le suivi de l'état et de signaler les erreurs au fur et à mesure qu'elles se produisent afin de pouvoir résoudre les problèmes avec précision et avec un minimum d'efforts. Il est tout aussi important de maintenir l’intégrité d’un ensemble d’actions étroitement liées, afin que si une partie d’une transaction a lieu, mais un autre n’est pas le cas, toute la transaction peut être restaurée en retour comme s’il ne s’est produite.  
  
 Orchestration BizTalk vous permet de garantir l'atomicité de votre travail, c'est-à-dire l'intégrité des actions liées entre elles, même lorsque des systèmes externes participent aux transactions. Cela vous fournit des outils pour gérer les erreurs, pour maintenir l'état d'une orchestration et pour résoudre les problèmes à mesure qu'ils se produisent lors des transactions, de la compensation et de la gestion des exceptions.  
  
 En tant qu’infrastructure pour les transactions et la gestion des exceptions, le Concepteur d’Orchestration fournit le **étendue** forme. Une étendue peut avoir un type de transaction, une compensation et n'importe quel nombre de gestionnaires d'exception.  
  
 Les étapes nécessaires pour configurer une transaction et la gestion des transactions sont les suivantes :  
  
-   Créez une étendue.  
  
-   Identifiez le type de transaction dont vous avez besoin.  
  
-   Déterminez ce qui devra être compensé.  
  
-   Identifiez les erreurs potentielles.  
  
-   Ajoutez les gestionnaires d'exceptions et le code de compensation appropriés.  
  
## <a name="examples-of-using-transactions-exception-handlings-and-compensations"></a>Exemples d'utilisation de transactions, de gestions des exceptions et de compensations  
  
-   [(Dossier d’exemples BizTalk Server) de la gestion des erreurs](../core/error-handling-biztalk-server-samples-folder.md)  
  
-   [Compensation (exemple BizTalk Server)](../core/compensation-biztalk-server-sample.md)  
  
-   Téléchargez l’exemple du Kit de développement logiciel « Atomic Transactions avec COM + traités composants in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Téléchargez l’exemple du Kit de développement logiciel « À l’aide du SQL adaptateur avec Atomic Transactions in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Téléchargez l’exemple de kit de développement logiciel « Using longues Transactions in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
-   Téléchargez l’exemple du Kit de développement logiciel « Exception Handling in Orchestrations » à [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étendues](../core/scopes.md)  
  
-   [Comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md)  
  
-   [Rendre les Orchestrations transactionnelles](../core/making-orchestrations-transactional.md)  
  
-   [Exceptions](../core/exceptions.md)  
  
-   [Compensation](../core/compensation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du moteur de messagerie BizTalk](../core/using-the-biztalk-messaging-engine.md)