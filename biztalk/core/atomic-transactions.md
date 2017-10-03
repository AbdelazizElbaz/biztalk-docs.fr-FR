---
title: Les Transactions atomiques | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- atomic transactions
- scopes, examples
- transactions, orchestrations
- orchestrations, transactions
- transactions, isolation levels
- transactions, ACID concept
- transactions, examples
- transactions, atomic
- scopes, transactions
- scopes
ms.assetid: 5030e1fd-943f-42bc-9296-4f315bd5f733
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc07f379c1f7aa1c846b2c20c19cbfb3393e8174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="atomic-transactions"></a>Transactions atomiques
Vous pouvez concevoir les orchestrations BizTalk de sorte qu'elles exécutent des tâches discrètes, selon le concept 'ACID' classique d'une transaction. Ces unités de travail discrètes ou atomiques, quand elles sont exécutées, permettent de faire passer le processus d'entreprise d'un état cohérent à un autre état, nouveau, cohérent et durable, qui se trouve isolé des autres unités de travail. Cela est généralement effectué à l’aide de la **étendue** construction qui encapsule les unités de travail avec la sémantique transactionnelle. Vous pouvez également définir l'orchestration complète en tant que transaction atomique sans utiliser d'étendues. Les étendues ne peuvent toutefois être transactionnelles que si l'orchestration elle-même est de type transaction atomique ou à long terme. Les transactions atomiques garantissent que les mises à jour partielles sont automatiquement annulées en cas d'échec lors de la mise à jour transactionnelle et que les effets de la transaction sont effacés (à l'exception des effets des appels .NET effectués dans la transaction). Les transactions atomiques des orchestrations BizTalk sont similaires aux transactions DTC (distributed transaction coordinator) dans le sens où elles sont généralement de courte durée et où elles possèdent les quatre attributs « ACID » (atomicité, cohérence, isolation et durabilité) :  
  
-   **Atomicité**  
  
     Une transaction représente une unité de travail atomique. Toutes les modifications d'une transaction sont appliquées, ou aucune d'entre elles.  
  
-   **Cohérence**  
  
     La validation d'une transaction ne doit pas altérer l'intégrité des données d'un système. Si des modifications sont apportées par une transaction dans une base de données jugée cohérente en interne avant le début de la transaction, il faut que la base de données conserve sa cohérence une fois la transaction validée. C'est essentiellement au développeur d'applications qu'il revient de garantir cette propriété.  
  
-   **Isolement**  
  
     Les modifications apportées par des transactions simultanées doivent être isolées des modifications effectuées par d'autres transaction simultanées. Les transactions isolées s'exécutant simultanément procèdent à des modifications qui préservent la cohérence interne de la base de données de la même façon que si elles étaient exécutées en série.  
  
-   **Durabilité**  
  
     Après la validation d'une transaction, toutes les modifications demeurent définitivement en place par défaut dans le système. Les modifications sont conservées même en cas de défaillance du système.  
  
 Les niveaux d'isolation suivants sont pris en charge par les transactions atomiques utilisées dans les orchestrations BizTalk :  
  
-   **Lecture validée**  
  
     Les verrous partagés sont conservés pendant la lecture des données afin d'éviter tout défaut de lecture, mais les données peuvent être modifiées avant la fin de la transaction, entraînant ainsi des données fantômes ou des lectures qui ne peuvent pas être répétées.  
  
-   **Lecture renouvelable**  
  
     Des verrous sont placés sur toutes les données utilisées dans une requête afin d'empêcher d'autres utilisateurs de mettre à jour les données. Cette opération permet d'empêcher les lectures non renouvelées, mais les lignes fantômes sont toujours possibles.  
  
-   **Sérialisable**  
  
     Un verrou de plage est placé afin d'empêcher les autres utilisateurs de mettre à jour ou d'insérer des lignes dans la base de données avant la fin de la transaction.  
  
 BizTalk Server veille à ce que les modifications d'état apportées au sein d'une transaction atomique, telles que les modifications de variables, de messages et d'objets, ne soient visibles hors de l'étendue de la transaction atomique qu'après la validation de la transaction. Les modifications d'état intermédiaires sont isolées des autres parties d'une orchestration.  
  
> [!NOTE]
>  Si une transaction atomique contient une **réception** mettre en forme un **envoyer** forme, ou un **démarrer Orchestration** forme, les actions correspondantes n’auront lieu jusqu'à ce que le transaction a été validée.  
  
 Si des propriétés ACID complètes sont exigées pour les données, par exemple, si les données doivent être isolées des autres transactions, vous devez uniquement faire appel aux transactions atomiques.  
  
 Lors de l'échec d'une transaction atomique, tous les états sont réinitialisés comme si l'instance d'orchestration n'avait jamais été dans l'étendue. La règle BizTalk sur les transactions atomiques veut que toutes les variables (et pas seulement les variables locales à l'étendue) participent à la transaction. Toutes les variables non sérialisables et les messages utilisés dans une transaction atomique doivent être déclarés locaux à l'étendue, faute de quoi, le compilateur génère une erreur de type « la variable….n'est pas marquée comme sérialisable ». Toutes les étendues atomiques sont supposées être « synchronisées » et le compilateur d'orchestration génère un avertissement en cas d'utilisation redondante si le mot clé synchronisé est vraiment employé pour les étendues atomiques. Le domaine de synchronisation des données partagées s'étend du début de l'étendue jusqu'à l'achèvement complet de cette dernière (persistance de l'état, à la fin de l'étendue, incluse) ou jusqu'à la fin du gestionnaire d'exceptions (en cas d'erreurs). Il ne s'étend pas jusqu'au gestionnaire de compensation.  
  
 Il est possible d'associer les transactions atomiques à des délais d'expiration, de sorte que l'orchestration arrête la transaction et suspend l'instance. Si une transaction atomique contient une forme Réception, Envoi ou Démarrer orchestration, les actions correspondantes n'auront lieu qu'après la validation de la transaction.  
  
 Une transaction atomique effectue une nouvelle tentative lorsque l’utilisateur lève délibérément une **RetryTransactionException** ou si un **PersistenceException** est déclenché au moment de la transaction atomique tente de valider. Ce dernier cas peut se produire lorsque la transaction atomique fait partie d'une transaction DTC distribuée et qu'un des autres participants met fin à la transaction, par exemple. De même, s’il existe des problèmes de connectivité de base de données en temps lorsque la transaction a été la tentative de validation, il serait également un **PersistenceException** déclenché. Si cela se produit pour une étendue atomique a **réessayer = True**, puis il réessaiera jusqu'à 21 tentatives suivantes. L'intervalle entre chaque nouvelle tentative est, par défaut, de deux secondes, mais vous pouvez changer cette valeur. Après que 21 tentatives sont atteint, si la transaction est toujours Impossible de valider, l’instance de l’ensemble de l’orchestration est suspendue. Vous pouvez la reprendre manuellement, auquel cas le cycle complet redémarre avec un compteur réinitialisé au début de l'étendue atomique problématique.  
  
> [!NOTE]
>  Uniquement les **RetryTransactionException** et **PersistenceException** peut entraîner une étendue atomique réessayer. Toute autre exception levée dans une étendue atomique ne peut pas entraîner de nouvelles tentatives, même si le **réessayer** est définie sur **True**. Le délai par défaut de deux secondes entre chaque tentative consécutive peut être substitué à l’aide d’une propriété publique sur **RetryTransactionException** (si c’est l’exception qui est utilisée à l’origine des nouvelles tentatives).  
  
 Les étendues atomiques des restrictions autres transactions qui ne peut pas imbriquer d’autres transactions ou inclure **Catch - Exception** blocs.  
  
## <a name="dtc-transactions"></a>Transactions DTC  
 Les transactions atomiques ont beau se comporter comme des transactions DTC, elles n'en sont pas par défaut. Vous pouvez les rendre DTC de manière explicite, à condition que les objets utilisés dans les transactions soient des objets COM+ dérivés de System.EnterpriseServices.ServicedComponents, et que les niveaux d'isolation des composants de transaction soient compatibles.  
  
> [!NOTE]
>  Une transaction atomique ne peut pas contenir d'autres transactions en son sein, de même qu'elle ne peut contenir de gestionnaires d'exception.  
  
> [!NOTE]
>  Une transaction atomique ne peut pas contenir d'actions d'envoi et de réception correspondantes, à savoir une paire requête-réponse ou des actions d'envoi et de réception se servant du même ensemble de corrélations.  
  
## <a name="non-serializable-objects"></a>Objets non sérialisables  
 Pour utiliser un objet non sérialisable dans une orchestration, il vous faut le faire au sein d'une transaction atomique. Toute utilisation d'objet non sérialisable hors d'une transaction atomique risque d'entraîner la perte de données chaque fois que l'orchestration est conservée par le moteur.  
  
> [!CAUTION]
>  Chaque étendue atomique représente un point de persistance. En d'autres termes, l'état de l'orchestration est enregistré dans la base de données au niveau de chaque point de persistance. Une utilisation fréquente de l'étendue atomique augmente la latence dans l'orchestration. Au lieu d'avoir recours à l'étendue atomique pour la création d'objets non sérialisables, utilisez la méthode Static qui ne requiert aucune étendue atomique, supprimant ainsi la nécessité des points de persistance.  
  
## <a name="see-also"></a>Voir aussi  
 [Scénarios à l’aide de Transactions atomiques](../core/scenarios-using-atomic-transactions.md)   
 [Transactions à long terme](../core/long-running-transactions.md)