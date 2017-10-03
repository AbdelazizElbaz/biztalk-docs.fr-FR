---
title: Les Transactions longues | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- long-running transactions, about long-running transactions
- atomic transactions, long-running transactions
- long-running transactions, orchestrations
- long-running transactions, nesting
- scopes, examples
- orchestrations, transactions
- compensations, long-running transactions
- compensations, customizing
- transactions, long-running
- transactions, compensation blocks
- long-running transactions
- long-running transactions, timeouts
- compensations, examples
- fault tolerance, long-running transactions
- transactions, examples
- orchestrations, long-running transactions
- transactions, atomic
- transactions, fault tolerance
- scopes, long-running transactions
- long-running transactions, fault tolerance
- transactions, nesting
- examples, scopes
ms.assetid: 4bf4d0c8-903a-411f-963b-bd4cfdfc2958
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c419c79b9de6287a0361dfe4e2e6b9dc555153
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="long-running-transactions"></a>Transactions de longue durée
Les transactions à long terme sont des constructions capitales couramment utilisées dans les orchestrations BizTalk. Elles facilitent la gestion des exceptions d'étendue personnalisée, des compensations d'étendue personnalisée et permettent d'imbriquer les transactions. Vous gagnez ainsi en flexibilité pour concevoir une architecture de transactions fiable.  
  
 Vous faites appel à une transaction à long terme lorsque la transaction doit s'exécuter sur une longue période de temps et que les propriétés ACID complètes ne sont pas nécessaires (autrement dit, lorsqu'il n'est pas nécessaire de garantir l'isolation des données par rapport aux autres transactions). Ce type de transaction peut présenter de longues périodes d'inactivité, notamment lorsqu'elle attend des messages externes.  
  
 Les transactions à long terme se caractérisent par une certaine cohérence et durabilité, mais aussi par l'absence d'atomicité et d'isolation. Les données présentes dans ce type de transaction ne sont pas verrouillées et peuvent donc être modifiées par d'autres processus ou applications. La propriété d'isolation des mises à jour d'état n'est pas gérée car il est impossible de maintenir les verrous sur le long terme.  
  
 La validation d'une transaction à long terme diffère de celle d'une transaction atomique. Il n'existe aucune présomption implicite de coordination distribuée concernant le résultat (une transaction à long terme existe uniquement au sein d'une seule instance d'orchestration). À la place, une transaction à long terme est considérée comme validée une fois que sa dernière instruction a été exécutée. Aucune restauration automatique de l'état n'est effectuée en cas d'abandon de la transaction. Vous pouvez obtenir cette restauration par programme grâce aux gestionnaires d'exception et de compensation.  
  
 Une étendue peut définir son propre état en déclarant des variables, messages et composants .NET. Une transaction à long terme a accès aux informations d'état de sa propre étendue, de l'étendue la renfermant, et à toutes informations d'état globalement définies dans l'orchestration. Elle n'a toutefois pas accès aux informations d'état des étendues qui ne la contiennent pas.  
  
## <a name="nesting"></a>Imbrication  
 Les transactions à long terme peuvent contenir des transactions atomiques ou d'autres transactions à long terme. Leur imbrication peut s'étendre selon des profondeurs arbitraires. Ainsi, votre transaction peut renfermer deux autres transactions à long terme, chacune d'elles contenant à leur tour des transactions atomiques.   
  
 L'imbrication est particulièrement utile lorsqu'un ou plusieurs composants d'une transaction globale doivent être atomiques alors que la transaction globale doit être à long terme. Prenons l'exemple de la réception et de l'exécution d'un bon de commande. Le bon de commande peut arriver à tout moment, et les différentes étapes d'exécution peuvent être longues, mais vous désirez quand même traiter le processus entier en tant que transaction. La transaction globale ici doit sans conteste être à long terme, tandis qu'une étape donnée, telle que le reçu d'un paiement, peut être atomique.  
  
> [!NOTE]
>  Vous ne pouvez pas imbriquer une étendue transactionnelle au sein d'une étendue ou d'une orchestration qui n'est pas elle-même transactionnelle. Une étendue ou une orchestration qui ne serait pas transactionnelle ne pourrait gérer l'état de ses étendues imbriquées comme elle le devrait.  
  
> [!NOTE]
>  Une transaction synchronisée ne peut pas inclure d'autres étendues synchronisées ou transactions.  
  
## <a name="compensation"></a>Compensation  
 Une transaction à long terme peut spécifier un bloc de compensation qui sera appelé pour compenser les activités de la transaction, après sa validation. Cela peut se traduire par une simple annulation de la transaction, lorsque c'est possible, ou par la réalisation d'autres fonctions, comme la notification, afin de limiter les effets de la transaction. En l'absence de votre propre code de compensation, le moteur d'exécution appelle par défaut les blocs de compensation des transactions internes, tant à long terme qu'atomiques, dans l'ordre inverse, en commençant par la dernière transaction validée pour terminer avec la première transaction validée.  
  
> [!NOTE]
>  La fonction de compensation n'est possible que pour une transaction correctement validée.  
  
## <a name="fault-tolerance"></a>Tolérance de panne  
 Les transactions gèrent la tolérance de pannes aussi bien pour les erreurs internes (panne de l'ordinateur et erreurs logicielles) qu'externes (annulation de messages). La restauration des mises à jour partielles au sein des transactions à long terme n'est pas automatique comme avec les transactions ACID, lorsqu'une erreur de transaction survient.  
  
 En cas d'erreur, le bloc de code d'exception de la transaction à long terme est appelé. Il contient un jeu de gestionnaires d'erreurs écrits par vos soins afin de gérer toutes les erreurs qui pourraient éventuellement survenir au cours de l'exécution de la transaction. Pour gérer l'erreur, vous pouvez compter sur le dernier état connu des messages, variables et objets.  
  
 Vous souhaiterez généralement que le gestionnaire d'exceptions puisse évaluer l'état de l'orchestration au moment de l'erreur, prendre les mesures qui s'imposent en fonction de cet état et appeler les compensations des transactions imbriquées.  
  
 En cas d'erreur, l'exécution de la transaction à long terme est interrompue, et ne peut être reprise.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios à l’aide de Transactions à Long terme](../core/scenarios-using-long-running-transactions.md)   
 [Transactions atomiques](../core/atomic-transactions.md)   
 [L’utilisation de Transactions et la gestion des Exceptions](../core/using-transactions-and-handling-exceptions.md)