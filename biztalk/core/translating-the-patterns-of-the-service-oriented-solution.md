---
title: "Conversion des modèles de Service, la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- patterns [service solutions], translating patterns to orchestration shapes
- artifacts, patterns
- orchestrations, patterns
- patterns [process management solutions], connections
- patterns [service solutions], orchestration boundaries
- patterns [process management solutions], translating patterns to orchestrations
- orchestrations, boundaries
- patterns [service solutions], translating patterns to artifacts
ms.assetid: ff17cc41-2a7b-4304-b5bd-96b1174cea7f
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 95285c93bdb290adbee988305dbcd365e4e729a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="translating-the-patterns-of-the-service-oriented-solution"></a>Conversion des modèles de Service, la Solution orientée services
Cette section décrit les modalités de conversion du diagramme modèle en artefacts BizTalk Server par la solution.  
  
 ![Service &#45; les modèles de Solution orientée services](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")  
  
## <a name="connections-and-completeness-conditions"></a>Connexions et conditions d'exhaustivité  
 Nous pouvons démarrer de n'importe où la conversion des modèles en composants BizTalk Server. Cependant, les connexions entre les composants sont, en effet, l'infrastructure des composants. Il s'agit donc d'un bon endroit pour commencer. En outre, dans le cas du modèle d'agrégation, nous devons penser à ce qui va indiquer l'exhaustivité des informations nécessaires. Cela affecte ses connexions aux autres composants ainsi que sa conception.  
  
 La solution doit fournir une méthode d'utilisation pratique et cohérente. L'interface de service spécifie comment d'autres applications peuvent l'utiliser. Comme la solution doit communiquer avec une application héritée à l'aide d'IBM WebSphere MQ, IBM WebSphere MQ doit faire partie de l'interface de service. Toutefois, pour les applications plus récentes, une interface de service Web semble être un choix évident. Une interface de service Web offre une souplesse maximale pour les autres applications utilisant le service. Ici, nous pouvons bénéficier de la souplesse de BizTalk Server pour avoir une interface de service double. Pour plus d’informations sur l’exposition des orchestrations en tant que services Web, consultez [comment le mappage des Orchestrations aux Services Web](../core/how-to-map-orchestrations-to-web-services.md).  
  
 Les autres connexions sont celles entre l'interface de service et la liste de destinataires, entre la liste de destinataires et les applications principales, ainsi qu'entre les applications principales, l'agrégation et l'interface de service.  
  
 Si la connexion à la liste de destinataires est synchrone, la solution ne doit pas utiliser de corrélations pour veiller à ce que tous les messages adressés à la liste de destinataires soient envoyés et reçus. Les connexions entre les applications principales et l'agrégation peuvent être synchrones pour les mêmes raisons. L'agrégation a besoin des réponses des trois applications principales pour préparer la réponse à la demande. Les temps de réponse doivent être courts afin que les connexions synchrones soient appropriées et simplifient la solution.  
  
 Dans le modèle d'agrégation, il existe généralement une condition d'exhaustivité. Dans les cas où il existe plusieurs serveurs principaux et de longs temps de réponse, la condition d'exhaustivité peut être, par exemple, la réception d'au moins une réponse dans une période donnée. Cette solution orientée services nécessite les trois réponses afin de construire le message final. Par conséquent, ici, la condition d'exhaustivité est la réception des trois réponses.  
  
> [!NOTE]
>  Lors de la réception des demandes via IBM WebSphere MQ, la solution ajoute un identificateur de corrélation en copiant le **MQMD_MsgId** valeur le **MQMD_CorrelId** du message de réponse. Cela fait partie de la méthode d'utilisation standard de l'adaptateur MQSeries dans les scénarios de requête-réponse afin d'éviter une possible condition d'engorgement. Pour plus d’informations, consultez [mise en corrélation de demande-réponse d’à l’aide des Messages](../core/correlating-messages-using-request-reply.md).  
  
## <a name="determining-orchestration-boundaries"></a>Identification des limites de l'orchestration  
 La solution doit être compatible avec les demandes d'une file d'attente IBM WebSphere MQ et via l'interface de service Web. Placer l'interface de service dans une orchestration, l'entrée IBM WebSphere MQ dans une autre et la majeure partie du traitement dans une troisième permet de garder la communication externe séparée du traitement.  
  
## <a name="translating-the-components-into-orchestration-shapes"></a>Conversion des composants en formes d'orchestration  
 Les modèles à convertir en formes sont, dans la solution finale, dans une seule orchestration. Il existe de nombreux moyens de créer un routeur basé sur le contenu dans BizTalk Server, y compris la création d'abonnements MessageBox. Dans la solution, le routage utilise des abonnements MessageBox. Une forme Expression évalue si le message inclut ou non des valeurs pour les champs requis. Une forme Décision évalue la variable définie dans la forme Expression et sélectionne le chemin via l'orchestration.  
  
 Le **CustomerService** orchestration utilise la forme parallèle pour envoyer des messages aux applications principales et recevoir des réponses simultanément. Elle ne doit pas attendre la fin d'une application avant de procéder à la demande suivante. Si le nombre d'applications devait changer régulièrement ou si les connexions aux applications n'étaient pas fiables, alors l'orchestration devrait convertir le modèle différemment.  
  
 Dans la solution, l'agrégation doit combiner des éléments de trois messages de réponse. L'utilisation de la forme parallèle permet de s'assurer que la communication avec les systèmes principaux est parallèle. Comme la forme ne s'arrête pas avant la réception de toutes les réponses ou un délai d'attente, l'agrégation sait toujours quand elle peut procéder. L'orchestration utilise une forme Transformer qui mappe des éléments des trois messages de réponse principaux et le message de demande d'origine aux éléments du message de réponse.  
  
> [!NOTE]
>  Les communications avec les systèmes principaux peut également expirer. Vous pouvez définir le délai d’attente en mettant le **réception** mettre en forme un **étendue** forme et en définissant le **délai d’attente** propriété de l’étendue.  
  
 Pour obtenir une liste complète des formes d’orchestration, consultez [formes d’Orchestration](../core/orchestration-shapes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modèles dans le Service de la Solution orientée services](../core/patterns-in-the-service-oriented-solution.md)   
 [Solution orientée services de composants du Service](../core/components-of-the-service-oriented-solution.md)