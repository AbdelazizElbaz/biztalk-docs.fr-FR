---
title: "Publier et s’abonner Architecture | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publish/subscribe architecture, publishers
- architecture, publish/subscribe
- publishing, publish/subscribe architecture
- publish/subscribe architecture, about publish/subscribe architecture
- creating, subscriptions
- publish/subscribe architecture, Messaging Engine
- routing, publishing
- Messaging Engine, publishing
- publish/subscribe architecture, subscribers
- publish/subscribe architecture
- subscriptions, publish/subscribe architecture
- publish/subscribe architecture, creating subscriptions
- subscriptions, creating
- Messaging Engine, subscribing
- publishing, routing
- Messaging Engine, publish/subscribe architecture
- publish/subscribe architecture, events
ms.assetid: 5ed36c1f-077d-468f-a99e-60f97377cef6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24ab84990a83345ea2fd5e78ca84755f2bb67b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publish-and-subscribe-architecture"></a>Architecture « publication-abonnement »
Dans une conception publication/abonnement, trois composants entrent en jeu :  
  
-   Serveurs de publication  
  
-   Abonnés  
  
-   Événements  
  
 Parmi les serveurs de publication, on peut citer les ports de réception qui publient les messages qui arrivent à leur emplacement de destination, les orchestrations qui publient les messages lorsqu'elles envoient des messages ou lorsqu'elles démarrent une autre orchestration de manière asynchrone et répondent à (ou sollicitent) des ports d'envoi qui publient les messages lorsqu'ils reçoivent une réponse de l'application cible ou du transport.  
  
 Dans BizTalk Server, il existe deux principaux types d’abonnements : l’activation et l’instance. Un *abonnement d’activation* Spécifie qu’un message qui correspond à l’abonnement doit activer, ou créez, une nouvelle instance de l’abonné lorsqu’elle est reçue. Les ports d'envoi dotés de filtres ou ceux liés à des orchestrations et les orchestrations qui reçoivent des formes dont la propriété Activer est définie sur True sont des exemples d'éléments qui créent des abonnements d'activation. Un *abonnement d’instance* indique que les messages qui correspondent à l’abonnement doivent être routés vers une instance en cours d’exécution de l’abonné. Les orchestrations dotées de ports de réception corrélés et de style requête/réponse en attente d'une réponse de BizTalk Server sont des exemples d'éléments qui créent des abonnements d'instance.  
  
 Au niveau de l'information, la différence entre ces deux types d'abonnements réside dans le fait qu'un abonnement d'instance inclut l'ID d'instance unique, stocké dans la table des abonnements de la base de données principale MessageBox. Lorsqu'une instance d'orchestration ou un port de réception termine le traitement, les abonnements d'instance sont supprimés de la base de données MessageBox alors que les abonnements d'activation restent actifs tant que l'orchestration ou le port d'envoi est inscrit.  
  
## <a name="creating-subscriptions"></a>Création d'abonnements  
 Les abonnements sont créés par des classes de service dans BizTalk Server répertoriées dans la table adm_ServiceClass de la base de données de gestion BizTalk. Ces services incluent le service de mise en cache des messages In-process et isolés qui est hébergé par le Gestionnaire des points de terminaison et les orchestrations/XLANG hébergées par le sous-service XLANG. Chacune de ces classes de service peut créer des abonnements et recevoir des messages publiés.  
  
 Un abonnement est une collection d'instructions de comparaison, ou prédicats, qui impliquent des propriétés de contexte de message et les valeurs spécifiques à l'abonnement. Par exemple, Type de message est une propriété de contexte de messages et de nombreux abonnements la spécifient. Des informations générales sur l'abonnement sont insérées dans la table d'abonnements par l'agent des messages alors que les prédicats spécifiques sont insérés dans les tables suivantes, en fonction du type d'opération spécifié pour l'abonnement :  
  
-   BitwiseANDPredicates  
  
-   EqualsPredicates  
  
-   EqualsPredicates2ndPass  
  
-   ExistsPredicates  
  
-   FirstPassPredicates  
  
-   GreaterThanOrEqualsPredicates  
  
-   GreaterThanPredicates  
  
-   LessThenOrEqualsPredicates  
  
-   LessThenPredicates  
  
-   NotEqualsPredicates  
  
 Tout ceci s’effectue en appelant le Bts_CreateSubscription_\<nom de l’application > et Bts_InsertPredicate_\<nom de l’application > où la base de données des procédures stockées dans la MessageBox \<nom de l’application > est le nom de l’hôte BizTalk qui crée l’abonnement.  
  
 Quand un port d'envoi est inscrit, le port crée au minimum un abonnement pour tout message avec l'ID de transport de ce port d'envoi dans le contexte. Cela permet au port d'envoi de toujours recevoir des messages qui lui sont spécifiquement destinés. Lorsqu'un port d'orchestration est lié à un port d'envoi particulier, les informations relatives à cette liaison sont stockées dans la base de données de gestion BizTalk. Lorsque des messages sont envoyés de l'orchestration via le port lié au port d'envoi physique, l'ID de transport est inclus dans le contexte de sorte que le message soit acheminé vers ce port d'envoi. Il est cependant important de noter que ce port d'envoi n'est pas le seul port susceptible de recevoir des messages envoyés depuis l'orchestration. Lorsqu'une orchestration envoie un message, le message est publié dans la base de données MessageBox avec toutes les propriétés promues appropriées. Le port d'envoi lié est assuré de recevoir une copie du message, car l'ID de transport figure dans le contexte. Cependant, tout autre port d'envoi, ou orchestration, peut être associé à un abonnement qui correspond également aux propriétés du message. Il est très important de comprendre que chaque fois qu'un message est publié directement dans la base de données MessageBox, tous les abonnés dont les abonnements correspondent recevront une copie du message.  
  
## <a name="publishing-and-routing"></a>Publication et routage  
 Une fois qu'un abonnement est créé et activé, il est nécessaire qu'un message soit publié avant que le traitement ne puisse avoir lieu. Les messages sont publiés lorsqu'ils sont reçus dans BizTalk Server d'un des services précédemment mentionnés. Dans le cadre de cette présentation de l'acheminement, nous allons nous concentrer sur les messages reçus dans BizTalk Server via un adaptateur.  
  
 Lorsque les messages transitent par le pipeline de réception, des propriétés sont promues dans le contexte du message. Une fois qu'un message est prêt à être publié dans la base de données MessageBox après avoir été traité par l'adaptateur de réception et le pipeline, la première chose qui se produit est que l'agent des messages insère les valeurs des propriétés promues et les valeurs de prédicat à partir du contexte du message dans la base de données MessageBox SQL Server principale. La présence de ces valeurs dans la base de données permet à l'agent des messages de prendre des décisions relatives au routage.  
  
 Au cours de l'étape suivante, l'agent des messages demande à la base de données MessageBox principale de rechercher les abonnements correspondant au lot actuel de messages publiés. N'oubliez pas qu'à ce stade, seules les propriétés ont été écrites dans la base de données, ce qui n'est pas le cas des messages. La procédure bts_FindSubscriptions stockée dans la base de données MessageBox interroge les tables d'abonnement et de prédicats et les lie aux propriétés du message stockées pour le lot actuel de messages.  
  
 Muni de ces informations, l'agent des messages insère le message une fois dans chaque base de données MessageBox possédant un abonnement en appelant la procédure stockée bts_InsertMessage. La procédure stockée bts_InsertMessage est d’abord appelée avec un ID d’abonnement. Ce premier passage, les appels de procédure stockée l’int_EvaluateSubscriptions procédure stockée qui est responsable de la recherche les informations de détail d’abonnement, vérifier que le message répond aux exigences de sécurité pour l’application en vérifiant que le prédicat correspond aux propriétés de l’application pour l’ordinateur hôte et l’insertion d’une référence au message dans la file d’attente spécifique des applications ou d’une application spécifique file d’attente suspendue selon l’état de message. Les ID de message, d'abonnement et de service ainsi que les informations sur l'abonnement sont insérés dans la table de files d'attente propre à l'application pour chaque abonnement trouvé pour cette application. Une fois que les messages sont insérés, les valeurs relatives au lot sont effacées des tables de propriétés et de prédicats du message.  
  
 La procédure stockée bts_InsertMessage est ensuite appelée pour chaque partie composant le message. Sur le premier appel, le contexte du message est passé et est ensuite inséré dans la table du SPOULEUR en même temps que les métadonnées relatives au message, telles que le nombre de parties, le nom du corps et l’ID En outre, le corps du message est inséré dans la table des parties à l’aide de la procédure stockée int_insertpart en vue. La procédure stockée bts_InsertMessage est ensuite appelée pour chaque partie restante du message. Ces parties sont simplement transmises à la procédure stockée int_InsertPart en vue d'être enregistrées dans la table des parties.  
  
 Lorsque les messages sont acheminés, des références sont ajoutées pour chaque service qui reçoit l'instance spécifique du message et ses parties en insérant des enregistrements dans les tables suivantes :  
  
-   MessageRefCountLog1  
  
-   MessageRefCountLog2  
  
-   PartRefCountLog1  
  
-   PartRefCountLog2  
  
 Ces références empêchent que les messages et les parties ne soient supprimés par des tâches de nettoyage qui s'exécutent régulièrement pour supprimer de la base de données MessageBox les messages qui n'existent plus dans le système. Deux tables sont utilisées pour limiter les problèmes de conflit et de verrouillage.  
  
 Le message étant désormais acheminé vers la file d'attente appropriée, stocké dans les tables de files d'attente et des parties, puis référencé dans les files d'attente propres à l'application, il doit être retiré des files d'attente par les instances de l'application. Chaque instance d'hôte possède des threads chargés de retirer les messages de la file d'attente. Ces threads interrogent en permanence la base de données à des intervalles configurés dans la table adm_ServiceClass de la base de données de gestion BizTalk. Cette même table comporte une colonne qui indique le nombre de threads chargés du retrait des messages. Chaque thread appelle dans la base de données MessageBox et appelle le bts_DequeueMessages_\<nom de l’application > procédure appropriée pour l’application hôte est stockée. Cette procédure stockée utilise la sémantique de verrouillage pour vous assurer que seule une instance et un thread de retrait sont en mesure de fonctionner sur un message dans la file d’attente à un moment donné. L'instance de l'hôte qui obtient le verrou obtient le message. Il est ensuite chargé de la remise du message au sous-service auquel le message est destiné.  
  
 Si le service qui reçoit le message est le gestionnaire des points de terminaison, le port d'envoi est alors appelé (ou la partie de réponse d'un port de réception requête-réponse). S'il s'agit du sous-service XLANG/s, une orchestration est créée ou recherchée en vue de traiter l'abonnement, selon qu'un ID d'instance figure ou non dans l'abonnement. Le service libère la référence au message et à sa partie de sorte que si aucun autre service ne comporte des références, les données du message peuvent être supprimées.  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie](../core/the-messaging-engine.md)