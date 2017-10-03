---
title: "Contrôler le flux de l’adaptateur BizTalk pour JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling
- control flows
- apartment threading
- apartment threading, business functions
ms.assetid: 1ec865d0-2257-453b-9230-1f3787ebac38
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fc5a8be6516b61c4049242952967ce939513e9c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="control-flow-in-biztalk-adapter-for-jd-edwards-oneworld"></a>Flux de contrôle dans l'adaptateur BizTalk pour JD Edwards OneWorld
Cette rubrique décrit les flux de contrôle de la conception et de l'exécution dans l'adaptateur BizTalk pour JD Edwards OneWorld.  
  
## <a name="design-time-flow"></a>Flux de conception  
 À l'ouverture de l'adaptateur (à l'aide des informations d'identification et des informations système à partir de la boîte de dialogue Propriétés du transport), une ou plusieurs instances de la fonction d'entreprise de l'application JD Edwards OneWorld sont créées et regroupées. Lorsque vous accédez à l'espace de noms dans l'Assistant Adaptateur, la liste des fonctions d'entreprise est affichée. Lorsque vous cliquez sur une fonction d'entreprise, les méthodes logiques associées et les signatures de celles-ci sont affichées.  
  
## <a name="run-time-flow"></a>Flux d'exécution  
 Les instances de la fonction d'entreprise JD Edwards OneWorld sont créées et regroupées pour chaque thread. Lorsqu'un appel de méthode est envoyé à un service d'entreprise, les métadonnées de la méthode sont lues à l'aide de la fonction d'entreprise de l'application JD Edwards OneWorld. Toutefois, si celles-ci ont déjà été mises en cache, la fonction d'entreprise utilise les informations mises en cache avant d'effectuer un appel vers la méthode appropriée. Au moment de l'exécution, une couche d'interface JD Edwards OneWorld est créée dynamiquement. Celle-ci permet à l'adaptateur BizTalk pour JD Edwards OneWorld de prendre en charge l'appel et la conversion des données.  
  
 L'adaptateur BizTalk pour JD Edwards OneWorld mappe les descriptions d'interface des signatures de méthode de l'application JD Edwards OneWorld, ce qui permet à BizTalk Server d'interagir avec ces descriptions.  
  
 L'adaptateur permet aux applications de l'entreprise d'interagir avec l'application JD Edwards OneWorld en étendant les fonctionnalités de l'application sous la forme d'un ou plusieurs des éléments suivants :  
  
-   formats de données natifs ;  
  
-   Procédures  
  
-   Méthodes  
  
-   Messages  
  
-   Propriétés  
  
-   interfaces d'application.  
  
 Au moment de l'exécution, l'adaptateur BizTalk pour JD Edwards OneWorld génère une description des interfaces de l'application pour les applications clientes qui interagissent avec JD Edwards OneWorld. L'adaptateur peut créer, supprimer et appeler des objets d'entreprise (le cas échéant) pour effectuer des calculs dans l'application et appeler directement des méthodes. Tous les appels vers JD Edwards OneWorld sont synchrones. L'adaptateur reçoit les messages XML de BizTalk Server, les place dans une enveloppe SOAP et transforme les données de l'appel de messages SOAP en types Java.  
  
 Le processus de réponse est similaire :  
  
1.  Les types Java sont transformés en messages SOAP.  
  
2.  Les messages SOAP sont convertis en messages XML.  
  
3.  Les messages XML sont soumis à BizTalk Server pour traitement.  
  
### <a name="apartment-threading-of-business-functions"></a>Thread cloisonné des fonctions d'entreprise  
 Une fonction d'entreprise JD Edwards OneWorld et une instance ne peuvent être utilisées que sur le thread où elles ont été créées ou obtenues. Il s’agit en tant que *de thread apartment*. L'infrastructure de regroupement de connexions de l'adaptateur BizTalk pour JD Edwards OneWorld gère un pool de connexions disponibles.  
  
### <a name="connection-pooling"></a>Regroupement de connexions  
 Le regroupement de connexions améliore les performances des appels en gardant ouvertes les connexions aux systèmes serveur et en réutilisant celles-ci au lieu de les fermer après chaque appel. L'adaptateur BizTalk pour JD Edwards OneWorld permet de regrouper les connexions au sein d'ID de connexion spécifiques, tout en continuant à contrôler le nombre total de connexions parmi les différents pools.  
  
 Chaque nouvelle instance de fonction d'entreprise utilise le thread sur lequel elle a été créée, et elle est détruite après chaque opération. Tous les appels JD Edwards OneWorld vers les fonctions d'entreprise sont sans état ; cependant, durant l'opération, l'adaptateur vérifie que la fonction d'entreprise est utilisée sur le thread approprié.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’Applications](../core/developing-applications3.md)   
 [Planification et Architecture](../core/planning-and-architecture17.md)