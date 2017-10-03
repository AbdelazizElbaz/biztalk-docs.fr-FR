---
title: "Présentation des données suivies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- instances, viewing
- service instances, viewing
- viewing, suspended instances
- messages, viewing
- viewing, service details
- viewing, orchestration details
- viewing, message details
- orchestrations, viewing
- suspended instances
- instances, suspended
ms.assetid: dcc3fbd5-cd2c-4780-a577-0ccd521cf5eb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed30934ca154c8b6921682112b12d016c57f92be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-tracked-data"></a>Présentation des données suivies
Lors de l'exécution d'une requête de suivi, les informations de suivi sont affichées dans la liste des résultats, au bas de la fenêtre Résultats de la requête.  
  
## <a name="viewing-message-details"></a>Affichage des détails sur le message  
 Vous pouvez suivre les propriétés de message. Vous pouvez également enregistrer les corps des messages suivis sur un fichier et les consulter à l'aide des outils non-Microsoft.  
  
-   Vous pouvez cliquer avec le bouton droit sur tout message référencé par une instance de service et sélectionner Détails sur le message.  
  
-   Si le message est déjà traité mais qu'il a été suivi (vous aviez activé le suivi), vous pouvez l'enregistrer sur votre disque dur et le lire.  
  
-   Vous pouvez joindre le message à l'instance d'orchestration et utiliser le débogueur de l'orchestration.  
  
## <a name="viewing-service-events"></a>Affichage des événements du service  
 Lorsqu’un service interrompu apparaît dans le journal des événements, vous pouvez analyser un service à l’aide de la **flux Message**, **débogueur Orchestration**, **afficher les événements de Message suivis**, **Afficher les Instances de Service Live**, options de la **contexte** menu.  
  
## <a name="viewing-orchestration-events"></a>Affichage des événements d'orchestration  
 Utilisez le débogueur de l'orchestration pour afficher le chemin emprunté par l'instance d'un message à travers une orchestration. Pendant votre analyse détaillée, une image de l'orchestration montre la progression du message et vous permet de placer des points d'arrêt dans l'orchestration à des fins de débogage.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Quel est le suivi des messages ?](../core/what-is-message-tracking.md)  
  
-   [Quel est le suivi des événements ?](../core/what-is-event-tracking.md)