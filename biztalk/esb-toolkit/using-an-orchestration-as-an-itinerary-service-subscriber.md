---
title: "À l’aide d’une Orchestration en tant qu’un abonné d’itinéraire Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 278564f1-de9f-4fbf-8c7f-09b3e607c28b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f496884d0aed8d5f351f681ca8cfe59e05684240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-an-orchestration-as-an-itinerary-service-subscriber"></a>À l’aide d’une Orchestration en tant qu’un abonné d’itinéraire de Service
Orchestrations peuvent également agir en tant que services d’itinéraire. Pour participer à un itinéraire, vous devez tout d’abord créer l’orchestration en tant que liaison directe ; Pour ce faire, utilisez un abonnement de filtre similaire à celui du port d’envoi dans la rubrique précédente, [à l’aide d’un Port d’envoi en tant qu’itinéraire Service abonné](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md). La figure 1 montre un exemple d’une expression de filtre pour une orchestration appropriée récupérer un message qui remplit les conditions suivantes :  
  
-   **ServiceName = Microsoft.Practices.ESB.Services.Transform**  
  
-   **ServiceState = en attente**  
  
-   **ServiceType = d’Orchestration**  
  
 ![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "chapitre 4-Orchestration")  
  
 **Figure 1**  
  
 **Exemple d’expression de filtre d’une orchestration qui participe à une feuille de route en tant qu’abonné**  
  
 Lorsque des messages arrivent dans Microsoft BizTalk Server via un ESB rampe d’entrée, l’étape de validation dans le pipeline ESB écrit les valeurs de propriété pour les propriétés de filtre dans les propriétés de contexte BizTalk du message entrant ; les promeut dans le contexte du message. Le service d’itinéraire définit toujours la **ServiceName** propriété pour le service actuellement actif pour le nom du service à traiter suivant et avec un **ServiceState** valeur de propriété  **En attente**. Pour un abonnement, vous devez définir au moins le premier trois propriétés suivantes :  
  
-   **ServiceName.** Ceci est le nom du service, tel que stocké dans la feuille de route ESB et peut être n’importe quel nom. L’itinéraire utilise ce nom pour identifier le service à exécuter.  
  
-   **ServiceState.** Il s’agit de l’état de l’étape actuelle de la feuille de route de service à exécuter. L’étape de service en cours (pour le traitement suivant) ont toujours la valeur **en attente**, défini par l’ESB d’itinéraire composant de pipeline, le composant de pipeline ESB itinéraire sélecteur, ou de code qui appelle la méthode le **avance**  (méthode) de l’API de l’itinéraire.  
  
-   **ServiceType.** Cette propriété définit le type de service, qui indique si elle provenance de l’orchestration ou le sous-système de messagerie dans BizTalk.  
  
-   **IsRequestResponse.** Cette propriété facultative doit avoir la même valeur que la **IsRequestResponse** propriété du service.