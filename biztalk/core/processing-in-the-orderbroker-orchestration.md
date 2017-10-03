---
title: "Le traitement de l’Orchestration OrderBroker | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, nested scopes
- nested scopes, performance
- processing, examples
- nested scopes, orchestrations
- orchestrations, performance
- performance, orchestrations
- performance, nested scopes
- examples, orchestration processing [process management solution]
- scopes, nesting
ms.assetid: c296e00c-b3ad-4161-baf7-258899185c34
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c6a6571ece3190b6195b207b4c45969ce25ddec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-in-the-orderbroker-orchestration"></a>Traitement de l’Orchestration OrderBroker
Cette section décrit comment la **OrderBroker** orchestration prend des commandes et les prépare pour un gestionnaire de processus. La section commence par le fonctionnement général de l'orchestration. Elle décrit ensuite la manière dont l'orchestration traite un message. Enfin, elle met en évidence la manière dont l'orchestration utilise une transaction atomique pour améliorer les performances.  
  
> [!NOTE]
>  En raison de la longueur de la longueur de la **OrderBroker** code, vous voudrez lire cette section avec l’orchestration ouverte dans Microsoft® Visual Studio.  
  
## <a name="why-an-order-broker"></a>Pourquoi un courtier de commandes ?  
 L’objectif de la **OrderBroker** orchestration est une commande de prétraitement et de router vers le Gestionnaire de processus correct. Le prétraitement consiste ici à produire des messages à titre indicatif pour la base de données de l'historique et pour le système de service, et à accuser réception de la commande. Le **OrderBroker** crée également un message de commande générique à partir de la demande de service client. Cette normalisation de la commande permet une utilisation générique de la commande par des éléments du processus d'entreprise.  
  
 Le message de commande est un message à parties multiples contenant des informations de routage séparées des informations de commande. Les informations de routage sont également génériques et conçues pour être utilisées par n'importe quel gestionnaire de commandes. Elles facilitent, à leur tour, le développement de la solution. Pour plus d’informations sur les messages à parties multiples, consultez [comment utiliser Types Message à parties multiples](../core/how-to-use-multi-part-message-types.md).  
  
 L'isolation de la fonction de courtage vous permet aussi de la déplacer vers un autre groupe BizTalk. Étant donné que la **OrderBroker** publie dans la base de données MessageBox : autrement dit, il est à liaison directe — facilite également de placer le courtier dans un autre groupe--vous pouvez déplacer le courtier sans modifier l’orchestration. Pour plus d’informations sur l’intégration de la **OrderBroker** dans un autre groupe, consultez [Communication entre OrderBroker et OrderManager](../core/communication-between-orderbroker-and-ordermanager.md).  
  
> [!NOTE]
>  Le **OrderBroker** orchestration, car il possède une seule **OrderManager** pour communiquer avec, attribue simplement une constante de chaîne pour le **OrderMgrType** champ dans l’ordre message du gestionnaire. Généralement, dans une application comptant plusieurs gestionnaires de commandes, l'application utilise le Moteur de règles d'entreprise pour déterminer la valeur appropriée de ce champ et le routage de la commande. Pour plus d’informations sur le moteur de règles d’entreprise, consultez [création et à l’aide des règles d’entreprise](../core/creating-and-using-business-rules.md).  
  
## <a name="order-processing"></a>Traitement des commandes  
 Le **OrderBroker** orchestration commence par deux **réception** des formes au sein d’un **écouter** forme. Un **réception** forme prend des messages à partir du système de prise en charge du client ; les autres messages à partir du système de fournisseur. Les messages à partir de ces deux sources ont le même schéma.  
  
 L’orchestration extrait l’adresse de retour du message et l’utilise pour définir l’adresse du port dynamique, **CSRPort**. L'orchestration utilise ce port pour envoyer des accusés de réception et des messages d'erreur.  
  
 Étapes suivantes le **OrderBroker** orchestration créer le message d’historique, le message de service, le message de confirmation et le message de commande à envoyer à la **OrderManager** orchestration. L’orchestration utilise la **InsertOrderBody** fonction utilitaire pour ajouter le message de commande pour le message d’historique.  
  
> [!NOTE]
>  Dans certains cas, la solution peut générer des messages qui sont livrés mais pas utilisés. L'orchestration OrderBroker utilise un port d'envoi pour insérer des informations dans la base de données de l'historique. Ce port d'envoi utilise l'accusé de réception. Configuration mappe le port d’envoi à un groupe de ports d’envoi contenant deux ports : un port pour la configuration de test (**HistoryInsert-Test-SP**), un pour la configuration normale (**HistoryInsert-SP**). Si vous laissez les deux ports en cours d'exécution dans le groupe, la solution envoie des messages aux deux ports. Ainsi, elle demande deux accusés de réception mais n'en traite qu'un.  
>   
>  Pour éviter cette situation, désinscrivez le port de test (**HistoryInsert-Test-SP**), ou arrêtez la version de test de l’application, **BTSScn.BPM.OrderBrokerApp.Test**. Pour plus d’informations sur les accusés de réception, consultez [accusés de réception à l’aide de](../core/using-acknowledgments.md).  
  
 Lors de la construction du message à envoyer à la **OrderManager** orchestration, le **OrderBroker** orchestration crée un message à parties multiples avec deux parties. L'une contient les informations de routage et l'autre, la commande proprement dite. La partie routage du message, **OrderMgrMsg.Routing**, utilise un schéma défini par une classe c# dans le **SchemaClasses** assembly. Le broker le traite l’ordre dans le cadre du message sous la forme d’un type générique ou type indépendant, le document XML (**System.Xml.XmlDocument**) et l’assigne à **OrderMgrMsg.Order**.  
  
 Il existe deux champs dans les informations de routage sont particulièrement importantes pour le Gestionnaire de commandes **OrderMgrMsg.Routing.OrderMgrType** et **OrderMgrMsg.Routing.Status**. Le courtier définit le **OrderMgrType** pour le type du Gestionnaire de commande qui est de gérer l’ordre. Dans la solution, il n'y a qu'un seul gestionnaire de commandes et le champ est défini sur CABLEORDER. Le courtier définit également la **état** champ accepté. Il s'agit de la valeur indiquant au gestionnaire de commandes que le message est une nouvelle commande. Le Gestionnaire de commandes dans la solution, **OrderManager** orchestration, utilise un **réception** forme qui permet de filtrer le type de commande égal à CABLEORDER et l’état égal à ACCEPTED.  
  
 Les étapes restantes dans le **OrderBroker** orchestration envoie les différents messages aux ports appropriés.  
  
## <a name="improving-performance-with-nested-scopes"></a>Amélioration des performances avec des étendues imbriquées  
 Un important de noter que sur le **OrderBroker** orchestration est son utilisation des étendues imbriquées. Les étendues imbriquées sont là, notamment, pour améliorer les performances en limitant les points de persistance.  
  
 Le moteur d'orchestration enregistre régulièrement l'état de toute l'orchestration aux points d'exécution, nommés points de persistance. Le moteur d’orchestration traite automatiquement plusieurs formes d’orchestration, y compris **envoyer** formes, en tant que points de persistance. Pour obtenir la liste de points de persistance et plus d’informations à leur sujet, consultez [persistance et le moteur d’Orchestration](../core/persistence-and-the-orchestration-engine.md).  
  
 Avec cinq **envoyer** formes, le **OrderBroker** orchestration doit avoir cinq points de persistance. Toutefois, lorsque vous regroupez **envoyer** formes à l’intérieur d’une étendue de transaction atomique, le moteur reconnaît qu’il doit uniquement un point de persistance pour l’étendue. Étant donné que quatre le **envoyer** en formes **OrderBroker** orchestration ne font pas partie des gestionnaires d’exceptions et aucune opération ne doit être effectuée après l’envoi, ils peuvent entrer dans une étendue de transaction atomique. Cela réduit le nombre de points de persistance. Pour plus d’informations sur les transactions atomiques, consultez [Transactions atomiques](../core/atomic-transactions.md).  
  
 Par ailleurs, le moteur d'orchestration utilise un seul point de persistance pour les transactions imbriquées si les transactions finissent toutes au même moment. Par conséquent, la méthode **OrderBroker** orchestration imbrique les transactions réduit davantage les points de persistance : l’orchestration a une persistance unique point en raison de l’utilisation de **étendue** formes.  
  
> [!TIP]
>  Vous pouvez améliorer les performances en réduisant le nombre de points de persistance dans une orchestration. Vous pouvez regrouper **envoyer** point de formes dans une transaction atomique pour produire une persistance unique pour tous les **envoyer** formes. L'arrêt simultané des étendues de transactions imbriquées produit un seul point de persistance pour les transactions.  
  
 Une étendue de transaction atomique ne peut pas avoir de gestionnaire d'exceptions. Par conséquent, l'orchestration imbrique l'étendue atomique à l'intérieur d'une transaction longue. Cette transaction externe peut avoir un gestionnaire d’exception et c’est ce gestionnaire qui traite une exception à partir de la **envoyer** formes.  
  
> [!TIP]
>  L'imbrication d'une transaction atomique dans une transaction longue est une méthode courante de gestion des exceptions.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement dans la Solution gestion des processus d’entreprise](../core/processing-in-the-business-process-management-solution.md)   
 [Logique du Gestionnaire de processus](../core/process-manager-logic.md)   
 [Gestion des interruptions dans la Solution gestion des processus d’entreprise](../core/interrupt-handling-in-the-business-process-management-solution.md)   
 [L’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md)