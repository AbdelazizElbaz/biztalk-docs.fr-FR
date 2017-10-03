---
title: "Le composant de redirecteur d’itinéraire ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 607cc8a0-4964-4751-baca-c3329983c98b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c61643423021701186745ab4275520cb14d3ceca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-itinerary-forwarder-component"></a>Le composant de redirecteur d’itinéraire ESB
Le composant de redirecteur de feuille de route ESB est utilisé lorsqu’un itinéraire doit appeler séquentiellement plusieurs services Web. Le composant peut être utilisé dans des pipelines qui sont associés le côté de la réponse d’un double rampe de réception.  
  
## <a name="installation"></a>Installation  
 L’installation du noyau ESB installe automatiquement le **itinéraire redirecteur** composant dans le dossier composants de Pipeline BizTalk Server.  
  
## <a name="how-it-works"></a>Fonctionnement  
 Lorsque Microsoft BizTalk reçoit un message via un double port de réception que le message est publié dans la base de données de la boîte de Message, un abonnement d’instance est créé. Cet abonnement se compose de la **EpmRRCorrelationToken** propriété promue et une **RouteDirectToTP** propriété promue. Lorsque l’abonné (orchestration ou port d’envoi bidirectionnel) retourne le message de réponse, ces propriétés promues correspond à l’abonnement et la réponse est immédiatement retournée via le pipeline d’envoi du port de réception.  
  
 Le redirecteur de feuille de route ESB doit être utilisé dans le pipeline de réponse pour une bidirectionnelle rampe où la rampe appelle un service Web de requête-réponse. Le composant interfère avec le processus BizTalk classique en modifiant le **RouteDirectToTP** propriété promue à la valeur est False, garantissant ainsi que la réponse ne sera pas retournée à l’initialisation de port de réception. Après la dernière étape de l’itinéraire est atteinte, le **RouteDirectToTP** propriété est modifiée au **True**, par conséquent, en retournant le résultat à l’initiateur rampe d’entrée.  
  
## <a name="using-the-esb-itinerary-forwarder-component"></a>À l’aide du composant de redirecteur d’itinéraire ESB  
 Ajouter le composant ESB ItineraryForwarder à un pipeline de réception, puis utilisez le pipeline avec la partie de la réponse d’une rampe-off bidirectionnelle. Créer un itinéraire lié Web plusieurs services, avec ou sans les services de transformation de feuille de route, avant ou entre les services. Pour obtenir un exemple montrant comment utiliser le composant de redirecteur itinéraire ESB, consultez le [installer et exécuter l’exemple de Services Web plusieurs](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).