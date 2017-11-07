---
title: "Architecture de l’adaptateur BizTalk pour PeopleSoft Enterprise | Documents Microsoft"
description: "Décrit la façon dont les messages sont reçus, comment les messages sont valide et fournit des informations sur les méthodes d’interface de composant à l’aide de l’adaptateur PeopleSoft avec BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f246e974-a082-430c-ad15-23a5e597738b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eb0f43dacdbd6036ef59fa3fe16102d4fe12379
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="peoplesoft-enterprise-adapter-architecture"></a>Architecture de l’adaptateur PeopleSoft Enterprise
Au cours de son fonctionnement de base, l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise reçoit un message XML de BizTalk Server qu'il place dans une enveloppe SOAP. Il transmet ensuite les requêtes SOAP au serveur. Il communique avec le système PeopleSoft à l'aide des classes psjoa, qui se connectent au système PeopleSoft via le protocole JTP (Jolt Transaction Protocol). Le système PeopleSoft reçoit la requête et exécute la logique d'entreprise. Le processus de réponse est similaire.  
  
 ![](../core/media/psadapter-01-architecture.gif "PSAdapter_01_Architecture")  

  
## <a name="component-interface-methods"></a>méthodes relatives à l'interface de composant  
 Par défaut, les API fournies par l'interface de composant PeopleSoft sont des API de base que le client doit appeler à plusieurs reprises. Par exemple, pour obtenir la propriété d'une instance d'une interface de composant, le client doit effectuer un ou plusieurs appels pour définir les valeurs de clé, puis un appel de la méthode Get de bas niveau. Il doit ensuite envoyer plusieurs appels pour obtenir les propriétés. L'adaptateur BizTalk pour PeopleSoft Enterprise fournit un nouvel ensemble de méthodes standard (Get, Create, Find et Update) qui permettent au client d'effectuer un seul appel pour obtenir le même résultat. Pour ce faire, l'adaptateur BizTalk pour PeopleSoft Enterprise doit effectuer plusieurs appels au nom du client. Pour plus d’informations sur les méthodes, consultez [annexe a : composant Interface méthodes](../core/appendix-a-component-interface-methods.md).  
  
 Pour créer un schéma pour PeopleSoft, l'adaptateur BizTalk pour PeopleSoft Enterprise extrait les définitions ou métadonnées de l'interface de composant PeopleSoft.  
  
 L'adaptateur BizTalk pour PeopleSoft Enterprise est basé sur les interfaces de composant de la fonctionnalité Envoi et ne requiert pas PeopleSoft Integration Broker. Les interfaces de composant sont exposées en tant que services Web, accessibles à partir de BizTalk Server.  
  
### <a name="validation"></a>Validation  
 Lorsque l'adaptateur BizTalk pour PeopleSoft Enterprise reçoit un message XML de BizTalk Server, deux niveaux de validation ont lieu :  
  
-   Le message XML doit être conforme à la spécification XML.  
  
-   Le message XML doit correspondre aux composants requis par le service Web spécifique (par exemple, mise en correspondance des types de données de l'interface).  
  
> [!NOTE]
>  Aucune validation de la logique d'entreprise (domaine du système PeopleSoft transparent à l'adaptateur BizTalk pour PeopleSoft Enterprise) n'est nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   