---
title: "En détail les Instructions de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed5d92fb-d53b-49a2-b2c7-8558708d6554
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cf0a726d2c8c4f6242ed19a7dcd1e5430775e63
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="processing-instructions-in-detail"></a>Instructions de traitement en détail
Cette rubrique décrit le format et la structure du schéma de propriété système-.xsd, qui définit plusieurs propriétés de contexte pour le traitement d’itinéraire. Ces propriétés sont promues lorsqu’un message est reçu et traité via des pipelines de BizTalk Server ; comme ce sont des propriétés promues, elles sont accessibles aux composants BizTalk Server. Les propriétés suivantes sont définies dans le schéma de propriété système-.xsd :  
  
-   **ItineraryHeader.** Cette propriété contient toutes les informations d’itinéraire et une liste des services d’itinéraire à être appelée par une séquence d’étapes d’itinéraire. L’API de l’itinéraire utilise cette propriété en interne.  
  
-   **ServiceName.** Cette propriété contient le nom du service en cours d’itinéraire à traiter.  
  
-   **ServiceState.** Cette propriété contient l’état du service en cours d’itinéraire : **en attente**, **Complete**, ou **Active**. Tous les services s’abonner à une étape de l’itinéraire contenant un **ServiceState** valeur **en attente**.  
  
-   **ServiceType.** Cette propriété définit le type de l’étape de l’itinéraire (**messagerie** ou **Orchestration**).  
  
-   **IsRequestResponse.** Cette propriété définit le type de messagerie (unidirectionnel ou requête-réponse).  
  
 Le service itinéraire exécute les étapes d’itinéraire dans un des deux façons, selon la valeur de la **ServiceType** propriété :  
  
-   Composants de pipeline d’itinéraire exécutent toutes les étapes d’itinéraire avec une **ServiceType** propriété du **messagerie**. Les développeurs peuvent étendre ce processus à l’aide d’un pipeline personnalisé et l’API de l’itinéraire.  
  
-   Lorsque le **ServiceType** propriété **Orchestration**, une orchestration, activée par un abonnement à des propriétés de contexte d’itinéraire, exécute l’étape de l’itinéraire.  
  
 Lorsqu’un service de l’itinéraire traite une étape de l’itinéraire, le service est responsable de l’avancement de la feuille de route et distribuer le message avec un nouveau contexte d’itinéraire pour le traitement à l’aide de la publication-abonnement des fonctionnalités de BizTalk Server. Un itinéraire service dispose du contrôle total de la feuille de route dans le contexte du message et pouvez passer à l’étape appropriée en fonction de sa logique interne et le contenu du message.  
  
 Le mécanisme de traitement d’itinéraire prend en charge la combinaison de la messagerie et orchestration des étapes d’itinéraire dans un seul itinéraire. Les développeurs peuvent également définir des services personnalisés d’itinéraire et configurer les étapes d’itinéraire personnalisées.  
  
 Pour plus d’informations sur les itinéraires, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).  
  
 Pour plus d’informations sur les services d’itinéraire personnalisées et des étapes d’itinéraire personnalisées, consultez [création d’un Service personnalisé de la feuille de route](../esb-toolkit/creating-a-custom-itinerary-service.md).