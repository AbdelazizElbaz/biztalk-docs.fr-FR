---
title: "Comment les plusieurs Services Web fonctionnement de l’exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16680ca7-16cc-47df-8c39-a3311d468a46
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b3d9faf350654be69015ea940b6b4f034d4de74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-multiple-web-services-sample-works"></a>Comment les Services Web de plusieurs exemples de fonctionnement
L’exemple de plusieurs Services Web utilise deux techniques distinctes pour appeler plusieurs services Web en série tout en étant en mesure de retourner un résultat incorrect à l’appelant d’origine. Une méthode utilise un composant de pipeline personnalisé dans le pipeline de réponse, et l’autre méthode utilise un bidirectionnels routage basé sur l’orchestration d’itinéraire service personnalisé qui ignore la configuration requise de l’appel d’une rampe pour effectuer un appel de demande/réponse à un site Web service.  
  
 La méthode de composant de pipeline personnalisé utilise le composant de Pipeline du redirecteur. Ce composant conditionnellement promeut les propriétés pour empêcher le routage du message vers le pipeline d’envoi de la bande jusqu'à ce que tous les services d’itinéraire sont traitées de Microsoft BizTalk.  
  
 La méthode de service personnalisé de basée sur l’orchestration utilise l’orchestration TwoWayRouting contenue dans l’architecture ESB. Projet MultipleWebServices.Orchestrations dans le \Source\Samples\MultipleWebSerivces\Source\ESB. MultipleWebServices.Orchestrations dossier. Ce service traite un résolveur associé pour déterminer l’adresse de point de terminaison d’un service Web bidirectionnel. Il configure ensuite un Port d’envoi dynamique Solict-réponse nommé RoutingPort pour envoyer le message au service Web et retourner le résultat à l’orchestration. Ensuite, l’orchestration avance l’itinéraire et retourne le message résultant dans la MessageBox.  
  
 Les itinéraires inclus dans l’exemple utilisent au moins une de ces méthodes afin de conserver le flux de message suivant l’itinéraire. Pour plus d’informations, consultez [l’exemple plusieurs Web Services itinéraires](../esb-toolkit/the-sample-multiple-web-services-itineraries.md).