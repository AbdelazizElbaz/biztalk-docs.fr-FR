---
title: "L’exemple Web plusieurs Services itinéraires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f67a4c6-b547-4261-ab3f-db78603ac588
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df8beeda266ae29eb4bb3e7c2a373c9ac6fc2b2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-sample-multiple-web-services-itineraries"></a>L’exemple Web plusieurs Services d’itinéraires
Le tableau suivant répertorie tous les fichiers d’itinéraire prédéfinis inclus dans l’exemple de plusieurs Services Web. Ceux-ci se trouvent dans le dossier \Source\Samples\MultipleWebServices\Itineraries.  
  
|Nom de fichier| Description|  
|---------------|-----------------|  
|OneWayMessagingMultipleServices.xml|Cette feuille de route unidirectionnel transforme un message NAOrderDoc à un message CNOrderDoc et puis l’achemine vers le Service de commande canadiens à l’aide de la DynamicResolutionSolicitResp rampe. La réponse est transformée puis au message CNOrderDoc à l’aide du service de transformation avec messagerie et puis il est acheminé à nouveau vers le Service de commande Canada à l’aide de la DynamicResolutionSolicitResp rampe. La réponse retournée est acheminée vers le dossier Source\Samples\DynamicResolution\Test\Filedrop\Out à l’aide du service de routage.|  
|TwoWayMessagingMultipleServices.xml|Cette feuille de route bidirectionnelle transforme un message NAOrderDoc à un message CNOrderDoc et puis l’achemine vers le Service de commande Canada. Prend ensuite la réponse du Service de commande Canada, transforme en un message CNOrderDoc et puis l’achemine à nouveau vers le Service de commande Canada. Le résultat est ensuite retourné à l’appelant. Tous les de transformation et de routage prend place via les services de messagerie. Les deux écarter utilise le port d’envoi DynamicResolutionSolicitRespForwarder.|  
|TwoWayMessagingOrchestrationMultipleServices.xml|Cette feuille de route bidirectionnelle utilise des services de messagerie pour transformer un message NAOrderDoc à un message CNOrderDoc, et il achemine ensuite ce message au Canada commande Service à l’aide du port d’envoi DynamicResolutionSolicitRespForwarder. La réponse est transformée à l’aide de l’implémentation du service de transformation d’orchestration, et il est ensuite passé à la Microsoft.Practices.ESB.Routing.TwoWay basée sur l’orchestration d’itinéraire service personnalisé fourni en tant que partie de l’exemple. Ce service envoie un message au service Web spécifié par le programme de résolution associé (dans ce cas, le Service de commande Canada), puis il reçoit et renvoie la réponse du service. Cette réponse est ensuite envoyée à l’appelant.|  
|TwoWayOrchestrationsMultipleServices.xml|Cet itinéraire bidirectionnelle utilise un service de messagerie pour transformer un message NAOrderDoc à un message CNOrderDoc, et il utilise ensuite l’orchestration Microsoft.Practices.ESB.Routing.TwoWay pour acheminer ce message au Service de commande canadien et retournent le résultat. Le message est transformé puis à un message CNOrderDoc à l’aide du service de transformation avec orchestration ; Après cela, il est envoyé au service de commande canadien l’utilisation du service Microsoft.Practices.ESB.Routing.TwoWay basée sur l’orchestration d’itinéraire. Le résultat est ensuite retourné à l’appelant.|  
|TwoWay (bidirectionnel)-partielle-sélecteur-Required.xml|Ce deux manière d’itinéraire utilise un service de messagerie pour acheminer un NAOrderDoc du message au Service de commande canadien via la DynamicResolutionSolicitResp rampe. Le NAOrderDoc est transformé en CNOrderDoc utilisant le service de transformation avec messagerie et le Canada service appelé. La réponse est ensuite retournée vers l’appelant.|