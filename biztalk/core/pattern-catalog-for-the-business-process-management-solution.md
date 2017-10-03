---
title: "Modèle de catalogue pour la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Canonical Message pattern [process management solutions]
- Nested Scopes pattern [process management solutions]
- Filter pattern [process management solutions]
- Per-Instance Pipeline Configuration pattern [process management solutions]
- Translator pattern, process management solutions
- patterns [process management solutions], pattern types
- Interruptible Orchestration pattern [process management solutions]
- Decoupled Orchestration pattern [process management solutions]
- Code Retry and Exception Handling pattern [process management solutions]
- Process Manager pattern [process management solutions]
- Asynchronous Reply pattern [process management solutions]
- Custom Exceptions pattern [process management solutions]
- Message Broker pattern [process management solutions]
- Coordination Using Delivery Notification pattern [process management solutions]
- Convoy pattern [process management solutions]
- Versioning pattern [process management solutions]
- Error Routing pattern [process management solutions]
- Application Reference pattern [process management solutions]
- Inverse Direct Partner Binding pattern [process management solutions]
ms.assetid: 246b109e-6006-404d-88b9-e6324ce3473c
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b352cce73e45103437407a013691e604b7b959
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pattern-catalog-for-the-business-process-management-solution"></a>Catalogue de modèles pour la solution de gestion des processus d'entreprise
Les modèles de la solution de gestion des processus d'entreprise incluent des modèles courants de programmation BizTalk Server, ainsi que les modèles d'intégration d'entreprise des sections précédentes. La liste de cette section inclut les deux types de modèles.  
  
## <a name="pattern-types"></a>Types de modèles  
 Les entrées suivantes décrivent brièvement le modèle et renvoient vers d'autres rubriques expliquant l'utilisation du modèle par la solution. Dans le cas des modèles généraux (filtre, par exemple), les entrées renvoient vers des rubriques plus générales.  
  
### <a name="application-reference-patterns"></a>Modèles de référence d'application  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet à une application d'utiliser les artefacts d'une autre application du même groupe en ajoutant une référence à l'autre application. La solution de gestion des processus d'entreprise utilise des références d'application dans la conception de la solution test ainsi que dans la solution principale. Pour plus d’informations sur les références d’application dans la solution, consultez [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
### <a name="asynchronous-reply-patterns"></a>Modèles de réponse asynchrone  
 La communication entre le gestionnaire de commandes et les étapes de traitement de commande est asynchrone. Autrement dit, le gestionnaire continue le traitement jusqu'à ce qu'il reçoive la réponse. Les étapes utilisent des ports dynamiques d'autocorrélation pour envoyer des réponses au gestionnaire. Les ports d'autocorrélation éliminent la nécessité pour le gestionnaire de commandes de gérer un ensemble de corrélations. L'aspect dynamique du port permet au gestionnaire de commandes d'envoyer à l'étape de traitement de commande l'adresse du port pour la réponse. Pour plus d’informations sur les ports de la solution, consultez [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).  
  
### <a name="canonical-message-patterns"></a>Modèles de message canonique  
 Pour simplifier le traitement, une solution convertit souvent les messages externes en un format interne. Ce format est un exemple de message canonique. L'orchestration du courtier de commandes convertit tous les messages de commande en un ou plusieurs messages de commande canoniques. L'orchestration du gestionnaire de commandes et les étapes de traitement utilisent ce format de commande commun. Pour plus d’informations, consultez [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md).  
  
### <a name="code-retry-and-exception-handling-patterns"></a>Modèles de nouvelle tentative de code et de gestion des exceptions  
 La solution centralise la majeure partie de la gestion des exceptions dans le **ExceptionHandler** orchestration. La solution utilise cette orchestration lorsqu'il est possible, dans le contexte d'une connexion réseau interrompue, que l'opération réussisse en cas de nouvelle tentative. L’orchestration utilise la **Recaller** objet pour réexécuter le code qui a échoué. Pour plus d’informations sur l’orchestration, consultez [la gestion des exceptions dans la Solution de gestion des processus métier](../core/exception-handling-in-the-business-process-management-solution.md). Consultez également [l’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md). Pour plus d’informations sur l’utilisation de la **Recaller** d’objets, consultez [l’objet Recaller](../core/the-recaller-object.md).  
  
### <a name="convoy-pattern"></a>Modèle de convoi  
 L'orchestration du gestionnaire de commandes, OrderManager, utilise le modèle de convoi pour intercepter et traiter les modifications subséquentes apportées à une commande en cours de traitement. Pour plus d’informations sur le modèle de convoi dans le Gestionnaire de commandes, consultez « Mise à jour de la commande » dans [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).  
  
### <a name="coordination-using-delivery-notification"></a>Coordination à l'aide de l'accusé de réception  
 Le **OrderBroker** orchestration utilise des accusés de réception pour s’assurer qu’une entrée est créée dans la base de données de l’historique avant de l’historique est mis à jour par la deuxième étape de traitement des commandes (**CableOrder2**). Pour plus d’informations, consultez « Coordination avec les étapes » dans [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md). Pour obtenir des informations générales sur l’accusé de réception, consultez [accusés de réception à l’aide de](../core/using-acknowledgments.md).  
  
### <a name="custom-exceptions-pattern"></a>Modèle d'exceptions personnalisées  
 Pour les exceptions qui ne peuvent pas faire l'objet d'une nouvelle tentative, la solution utilise la gestion des exceptions BizTalk Server habituelle, conjointement avec la gestion des exceptions personnalisée. La gestion des exceptions personnalisée permet une gestion des exceptions plus spécifique. Elle sert également d'indicateur entre les étendues imbriquées pour s'assurer que toutes les parties d'une opération sont conservées. Pour plus d’informations sur l’utilisation de la solution des exceptions personnalisées, consultez [Exceptions personnalisées](../core/custom-exceptions.md). Pour plus d’informations sur les étendues, consultez [comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md).  
  
### <a name="decoupled-orchestration-patterns"></a>Modèles d'orchestration dissociée  
 La conception de la solution de gestion des processus d'entreprise dissocie au maximum les orchestrations. La dissociation des orchestrations facilite le contrôle de version des parties de la solution et simplifie le déplacement des parties de la solution vers d'autres serveurs ou groupes. Pour plus d’informations sur la relation entre le courtier de commandes et le Gestionnaire de commandes, consultez [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md) et [via le Gestionnaire de processus de flux de commande](../core/order-flow-through-the-process-manager.md).  
  
### <a name="error-routing-pattern"></a>Modèle de routage d'erreurs  
 La solution utilise la nouvelle fonctionnalité de création de rapports d'erreurs BizTalk Server. Cette dernière achemine les messages ayant échoué vers un port d'abonnement pour les signaler dans un rapport ou les traiter. Pour obtenir des informations générales sur le rapport d’erreurs, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).  
  
### <a name="filter-pattern"></a>Modèle de filtre  
 Ce modèle sélectionne les messages à traiter en fonction de critères particuliers. Dans BizTalk, le modèle de filtre devient presque toujours un filtre d'expression sur un port. Pour plus d’informations sur les filtres sur les ports, consultez [à l’aide de filtres avec le Message forme réception](../core/using-filters-with-the-receive-message-shape.md).  
  
### <a name="interruptible-orchestration-pattern"></a>Modèle d'orchestration pouvant être interrompue  
 La solution gère les mises à jour ou annulations de commandes en commençant par interrompre la commande en cours. Les orchestrations dans la solution utilisent l'orchestration Interrupt pour traiter les interruptions. Pour plus d’informations, consultez [d’interruption de la gestion dans la Solution de gestion des processus métier](../core/interrupt-handling-in-the-business-process-management-solution.md).  
  
### <a name="inverse-direct-partner-binding-pattern"></a>Modèle de liaison directe de partenaires inversée  
 La solution inverse l'utilisation de la liaison directe pour dissocier les étapes de traitement de commande du gestionnaire de commandes. Pour plus d’informations sur la liaison directe inversée, consultez [Inverse la liaison directe partenaire](../core/inverse-direct-partner-binding.md).  
  
### <a name="message-broker-pattern"></a>Modèle de courtier de messages  
 Le modèle de courtier de messages permet à la solution de déterminer la destination d'un message afin que l'expéditeur n'ait pas besoin de la connaître. La solution de gestion des processus d’entreprise implémente un courtier de messages avec le **OrderBroker** orchestration. Le **OrderBroker** orchestration prend une commande, détermine le type de service commandé et achemine la commande vers le Gestionnaire de commandes correct. Pour plus d’informations sur le courtage de messages dans la **OrderBroker**, consultez [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md).  
  
### <a name="nested-scopes-pattern"></a>Modèle des étendues imbriquées  
 Le **OrderBroker** orchestration utilise des étendues imbriquées afin de réduire les points de persistance et, par conséquent, pour améliorer l’efficacité. Pour plus d’informations, consultez « Amélioration des performances avec des étendues imbriquées » dans [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md).  
  
### <a name="per-instance-pipeline-configuration"></a>Configuration du Pipeline par instance  
 Bien que la solution utilise des pipelines par défaut, elle exploite pleinement la nouvelle configuration de pipeline par instance afin de spécifier une enveloppe pour les messages. Pour plus d’informations, consultez [comment déployer des Pipelines](../core/how-to-deploy-pipelines.md) et [composants de la Solution de gestion des processus métier](../core/components-of-the-business-process-management-solution.md).  
  
### <a name="process-manager-pattern"></a>Modèle de gestionnaire de processus  
 La solution utilise un gestionnaire de commandes relativement générique pour contrôler le flux dans les étapes de traitement de commande. Cela permet de séparer la logique d'entreprise de la gestion du processus de commande. Pour plus d’informations sur le fonctionne de l’orchestration OrderManager en tant qu’un gestionnaire de processus, consultez [logique du Gestionnaire de processus](../core/process-manager-logic.md).  
  
### <a name="terminate-shape-at-end-of-orchestration"></a>Forme Terminer à la fin de l'orchestration  
 Plusieurs orchestrations utilisent une forme Terminer pour s'arrêter sur une erreur même si l'orchestration terminait normalement à ce point. La forme Terminer permet le suivi des instances ayant échoué et des erreurs. Pour plus d’informations, consultez [personnalisé Exceptions](../core/custom-exceptions.md).  
  
### <a name="translator-pattern"></a>Modèle de conversion  
 Le modèle de conversion d'entreprise (conversion d'un message d'un format dans un autre format) effectue la plupart du temps une conversion en un mappage BizTalk. Pour obtenir des informations générales sur les mappages BizTalk, consultez [création est mappé à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
### <a name="versioning-patterns"></a>Modèles de contrôle de version  
 La solution de gestion des processus d'entreprise est conçue pour simplifier le contrôle de version des composants de la solution en dissociant les orchestrations et en utilisant une numérotation des versions dans les espaces de noms de schéma. Pour plus d’informations, consultez [contrôle de version de la Solution de gestion des processus métier](../core/versioning-the-business-process-management-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles dans la Solution gestion des processus d’entreprise](../core/patterns-in-the-business-process-management-solution.md)