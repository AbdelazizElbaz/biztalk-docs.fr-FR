---
title: "Conception de modèles : la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- patterns [service solutions], examples
- examples, programming patterns
- patterns [service solutions], designing
- designing, programming patterns
ms.assetid: c196cd9d-2b2d-4548-bc7d-26196f7c2878
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcfa7f7e4f492de139ae3f5a10f6cb39abaa73be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="designing-with-patterns-the-service-oriented-solution"></a>Conception de modèles : la Solution orientée services
La solution orientée services illustre l'exposition d'une application BizTalk en tant que service destiné à être utilisé par d'autres applications. La présentation d'une application en tant que service permet à d'autres applications d'exploiter facilement les informations et de les réemployer dans les services qu'elles proposent. Pour plus d’informations sur le service interfaces Voir « Service Interface » à [http://go.microsoft.com/fwlink/?LinkId=46185](http://go.microsoft.com/fwlink/?LinkId=46185). Pour plus d’informations sur l’intégration de services, consultez « Service-Oriented Integration » à [http://go.microsoft.com/fwlink/?LinkId=46186](http://go.microsoft.com/fwlink/?LinkId=46186).  
  
 La solution est une application proposant des informations relatives au crédit. Elle fournit ces informations en tant que réponse de service Web, après avoir agrégé des informations pertinentes depuis trois autres applications. L'application consolide les résultats et renvoie un message unique contenant les informations relatives au crédit synthétisées. Les trois systèmes principaux sont les suivants :  
  
-   **Système SAP Enterprise.** il indique la limite de crédit générale du client. La solution communique avec son système principal à l'aide du connecteur SAP dans [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].  
  
-   **Système de Transactions en attente.** il signale le nombre total des transactions en attente dans le compte. La solution fait appel à Microsoft Host Integration Server (HIS) pour communiquer avec le macroordinateur à partir de Windows Server. Elle utilise également la technologie de l'intégrateur de transactions de HIS. Cela permet au système d'interagir avec le macroordinateur en tant que service Web. L'orchestration BizTalk utilise ce service Web.  
  
-   **Système Payment Tracking.** il signale le dernier paiement que la personne a effectué. Il fait appel à MQSeries.  
  
 Comme le suggérait la vue d'ensemble de la solution, il est également possible d'utiliser une interface autre que celle d'un service Web via les files d'attente MQSeries. (Pour plus d’informations sur la structure générale de l’application, consultez [présentation de la Solution orientée services](../core/understanding-the-service-oriented-solution.md)). Bien que les services Web constituent la manière la plus courante de construire des architectures orientées services, toutes les applications ne peuvent pas les utiliser. Les solutions BizTalk Server fournissent aux applications héritées des services Web ainsi que d'autres moyens d'utiliser le service.  
  
 L'accès à MQSeries permet de simuler la manière dont un système de réponse vocal interactif hérité peut utiliser la solution. L'accès à MQSeries ainsi que l'accès au service Web illustrent la manière par laquelle une solution unique peut être utilisée par des applications héritées et de nouvelles applications.  
  
## <a name="patterns-used-in-the-service-oriented-solution"></a>Modèles utilisés dans la solution orientée services  
 Le schéma suivant présente une version simplifiée des modèles de la solution orientée services.  
  
 ![Service &#45; les modèles de Solution orientée services](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")  
  
 La solution se compose de quatre parties principales, chacune représentant un modèle : l’interface de service, un routeur basé sur le contenu, une liste de destinataires et une agrégation. L'interface de service représente le mécanisme d'interface par lequel la connexion à la solution est rendue possible. Le routeur basé sur le contenu vérifie la validité d'un message et envoie un message d'erreur si celui-ci n'est pas valide. La liste de destinataires permet d'envoyer ce message aux trois applications principales. Lorsque les applications principales répondent, l'agrégation combine leur réponse en un message unique. Le message de réponse est ensuite acheminé au demandeur via l'interface de service.  
  
 Notez qu'un grand nombre d'éléments du schéma n'ont pas été spécifiés :  
  
-   Les convertisseurs de messages ont été omis, bien qu'ils soient requis par la solution afin de communiquer avec les systèmes externes.  
  
-   La manière de communiquer avec les processus principaux n'est pas spécifiée.  
  
-   La nature de l'interface de service n'est pas indiquée.  
  
-   Le schéma ne précise pas s'il faut utiliser un mode de communication synchrone ou asynchrone.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md)   
 [Conversion des modèles de Service, la Solution orientée services](../core/translating-the-patterns-of-the-service-oriented-solution.md)