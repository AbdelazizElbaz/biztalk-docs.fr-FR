---
title: "Architecture de l’adaptateur BizTalk pour PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, XML messages
- architecture
- XML, messages
- XML, validating
ms.assetid: f246e974-a082-430c-ad15-23a5e597738b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 377e49af3a20302b92a4214959b534c9d0949a93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-peoplesoft-enterprise"></a>Architecture de l'adaptateur BizTalk pour PeopleSoft Enterprise
Au cours de son fonctionnement de base, l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise reçoit un message XML de BizTalk Server qu'il place dans une enveloppe SOAP. Il transmet ensuite les requêtes SOAP au serveur. Il communique avec le système PeopleSoft à l'aide des classes psjoa, qui se connectent au système PeopleSoft via le protocole JTP (Jolt Transaction Protocol). Le système PeopleSoft reçoit la requête et exécute la logique d'entreprise. Le processus de réponse est similaire.  
  
 ![](../core/media/psadapter-01-architecture.gif "PSAdapter_01_Architecture")  
Architecture de l'adaptateur  
  
## <a name="peoplesoft-component-interface-methods"></a>Méthodes relatives à l'interface de composant PeopleSoft  
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
 [Prise en main](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 [Planification et Architecture](../core/planning-and-architecture13.md)