---
title: "Catalogue de modèles pour le Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Calling Pipelines from Code pattern [service solutions]
- Recipient List pattern [service solutions]
- filters, design patterns
- Filter pattern [service solutions]
- caching, patterns [service solutions]
- Service Interface pattern [service solutions]
- Content-Based Routing pattern [service solutions]
- Inline Invocation of Back-End Processes pattern [service solutions]
- content-based routing, patterns [service solutions]
- messages, Translator pattern [service solutions]
- aggregations, patterns [service solutions]
- Translator pattern, service solutions
- Caching pattern [service solutions]
- Aggregation pattern [service solutions]
- patterns [service solutions], pattern types
- back-end processes
- services, interface pattern [service solutions]
ms.assetid: 5d8135c5-d5de-4e61-b3e8-2aa7f6de98c8
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9441ead974cdcaba66dd9d038e786a5a8c7b156e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pattern-catalog-for-the-service-oriented-solution"></a>Catalogue de modèles pour le Service orienté solutions
Les modèles de la solution orientée services incluent des modèles associés aux méthodes de programmation spécifiques à BizTalk Server, ainsi que les modèles d'intégration d'entreprise des sections précédentes. La liste de cette section inclut les deux types de modèles.  
  
## <a name="pattern-types"></a>Types de modèles  
 Les entrées dans les rubriques suivantes décrivent brièvement le modèle et renvoient vers d'autres rubriques expliquant l'utilisation du modèle par la solution. Dans le cas des modèles généraux (filtre, par exemple), les entrées renvoient vers des rubriques plus générales.  
  
### <a name="aggregation-pattern"></a>Modèle d'agrégation  
 Ce modèle régit la réception des informations émanant de plusieurs sources et le regroupement de ces informations en un seul message. La solution orientée services associe les informations relatives au crédit de trois sources distinctes dans une réponse unique. Vous pouvez procéder à l'agrégation de différentes manières, selon la nature de la solution créée. Dans certains cas, vous devez attendre toutes les réponses. Dans d'autres (par exemple, simulations de crédit), vous pouvez anticiper l'obtention d'une réponse dès lors que vous avez reçu une quantité minimale d'informations. La solution orientée services attend d'obtenir les trois réponses car celles-ci sont nécessaires au renvoi d'un rapport de crédit complet. Pour plus d’informations, consultez [conversion des modèles de la Solution orientée services](../core/translating-the-patterns-of-the-service-oriented-solution.md).  
  
### <a name="calling-pipelines-from-code-pattern"></a>Modèle d'appel de pipelines à partir du code  
 Vous pouvez désormais appeler des pipelines à partir du code et des orchestrations. Cela permet la réutilisation des pipelines et permet également de préserver la dissociation d’une orchestration, les étapes du pipeline. Pour plus d’informations, consultez [à l’aide de Pipelines à partir de la Solution orientée services](../core/using-pipelines-from-the-service-oriented-solution.md).  
  
### <a name="caching-pattern"></a>Modèle de mise en cache  
 La mise en cache est une stratégie générale de stockage des informations qui évite de devoir extraire celles-ci d'un magasin de données à chaque demande. L'extraction de données de référence ou de configuration d'un système SSO constitue un facteur de limitation dans la solution. La solution met les informations en cache et actualise périodiquement le cache. Pour plus d’informations, consultez [à l’aide de l’authentification unique efficacement dans la Solution orientée services](../core/using-sso-efficiently-in-the-service-oriented-solution.md). La solution de gestion des processus d'entreprise met également les informations d'authentification unique en cache, en utilisant un processus légèrement différent. Pour plus d’informations, consultez [à l’aide de l’authentification unique efficacement dans la Solution de gestion des processus métier](../core/using-sso-efficiently-in-the-business-process-management-solution.md).  
  
### <a name="content-based-routing-pattern"></a>Modèle de routage basé sur le contenu  
 Dans les modèles d'intégration d'entreprise, le routage basé sur le contenu est conçu d'une façon moins spécialisée que dans BizTalk. Il détermine le destinataire d'un message sur la base d'une partie du contenu du message. La solution orientée services utilise une forme simplifiée du routage basé sur le contenu : une forme Décision unique dans une orchestration transmet le message à deux emplacements. Pour plus d’informations, consultez « Traduire les composants en formes d’Orchestration » dans [conversion des modèles de la Solution orientée services](../core/translating-the-patterns-of-the-service-oriented-solution.md).  
  
### <a name="filter-pattern"></a>Modèle de filtre  
 Ce modèle sélectionne les messages à traiter en fonction de critères particuliers. Dans BizTalk Server, le modèle de filtre devient presque toujours un filtre d'expression sur un port. Pour plus d’informations sur les filtres sur les ports, consultez [à l’aide de filtres avec le Message forme réception](../core/using-filters-with-the-receive-message-shape.md).  
  
### <a name="inline-invocation-of-back-end-processes-pattern"></a>Modèle d'appel inline des processus principaux  
 La version Inline de la solution utilise l'appel inline des processus principaux via des assemblys personnalisés. Ceci améliore considérablement les performances. Il faut toutefois procéder à un couplage étroit de l'orchestration et du protocole de transport. Pour plus d’informations, consultez [Invocation de Back-end incorporation](../core/inlining-back-end-invocation.md).  
  
### <a name="recipient-list-pattern"></a>Modèle de liste de destinataires  
 De façon abstraite, la solution orientée services implémente une liste de destinataires dans le sens où elle envoie des messages à trois systèmes distincts. Plus concrètement, l'application déployée détermine les destinataires en mappant les ports logiques aux emplacements spécifiques. Dans la version Inline de l'application, les connexions sont établies à l'aide des informations de configuration dans l'authentification unique. Pour plus d’informations, consultez [conversion des modèles de la Solution orientée services](../core/translating-the-patterns-of-the-service-oriented-solution.md).  
  
### <a name="service-interface-pattern"></a>Modèle d'interface de service  
 La solution orientée services se présente comme un service Web, une manière parmi d'autres d'établir un service. Pour plus d’informations sur l’utilisation des orchestrations en tant que services Web, consultez [à l’aide des Services Web](../core/using-web-services.md).  
  
### <a name="translator-pattern"></a>Modèle de conversion  
 Le modèle de conversion d'entreprise (conversion d'un message d'un format dans un autre format) effectue la plupart du temps une conversion en un mappage BizTalk Server. Pour obtenir des informations générales à propos des mappages de BizTalk Server, consultez [création est mappé à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles dans le Service de la Solution orientée services](../core/patterns-in-the-service-oriented-solution.md)