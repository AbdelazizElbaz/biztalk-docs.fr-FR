---
title: "Création d’un Service d’itinéraire personnalisé à l’aide d’une Orchestration BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bd7ed38-02a3-41b1-9990-754d5539f15e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723c0bc93192267f404d42e7fe859bb37ea59895
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-itinerary-service-using-a-biztalk-orchestration"></a>Création d’un Service d’itinéraire personnalisé à l’aide d’une Orchestration BizTalk
L’infrastructure d’itinéraire qui fait partie de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge l’exécution des étapes d’itinéraire à l’aide des orchestrations. Vous pouvez implémenter un service d’itinéraire personnalisé en tant qu’une orchestration Microsoft BizTalk Server en fonction de vos exigences fonctionnelles, qui peuvent inclure les éléments suivants :  
  
-   Plusieurs appels de service (comme indiqué par le [l’installation et l’exécution de l’exemple de ventilation-regroupement](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))  
  
-   Médiation et le message de corrélation de protocole (par exemple, HTTP-MQSeries)  
  
-   Les décisions de routage complexes basée sur l’enrichissement de message à partir de données externes des sources  
  
-   Logique de traitement  
  
 Chaque service d’itinéraire implémentée à l’aide d’une orchestration BizTalk Server est chargé pour les éléments suivants :  
  
-   Exception et la gestion des erreurs à l’aide de l’infrastructure de gestion d’Exception ESB ou les gestionnaires d’exceptions personnalisées facultatives qui prennent en charge la nouvelle soumission (itinéraires unidirectionnels)  
  
-   Avancer la feuille de route et la publication de messages sortants via BizTalk Server afin que l’étape suivante de la feuille de route de service peut s’exécuter.  
  
#### <a name="to-create-a-custom-itinerary-service-using-a-biztalk-server-orchestration"></a>Pour créer un service d’itinéraire personnalisé à l’aide d’une orchestration BizTalk Server  
  
1.  Créer le projet BizTalk Server qui contient une nouvelle orchestration ; par exemple, MyCustomeItineraryService.odx.  
  
2.  Ajoutez des références aux assemblys suivants :  
  
    -   **Microsoft.Practices.ESB.Itinerary**  
  
    -   **Microsoft.Practices.ESB.Itinerary.Schemas**  
  
    -   **Microsoft.Practices.ESB.ExceptionHandling**  
  
    -   **Microsoft.Practices.ESB.ExceptionHandling.Faults**  
  
3.  Définir une liaison directe logique port de réception et une forme réception activée dans l’orchestration.  
  
4.  Définir un filtre d’abonnement pour activer l’orchestration du contexte de message d’itinéraire afin que l’orchestration exécute la **MyCustomItineraryService** étape. Le code suivant montre un exemple d’un filtre approprié.  
  
    ```csharp  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName   
        == "MyCustomItineraryService")   
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
        == "Orchestration")  
    ```  
  
5.  Définir une orchestration de type **Microsoft.Practices.ESB.Itinerary.ItineraryStep**. Ajouter une activité d’expression à l’orchestration qui remplit cette variable, comme indiqué dans le code suivant.  
  
    ```csharp  
    // Retrieve the current itinerary step.  
    itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
    step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
    itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
    step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  
    ```  
  
6.  Ajoutez votre implémentation personnalisée à l’itinéraire qui crée le message sortant pour les étapes d’itinéraire ; par exemple, OutboundMsg.  
  
7.  Avance l’itinéraire à l’aide de l’activité d’expression suivant qui utilise le contexte de message à partir du message entrant.  
  
    ```csharp  
    OutboundMessage(*) = InboundMessage(*);   
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
8.  Envoyer le message sortant avec l’itinéraire de mise à jour via un port d’envoi de la liaison directe pour activer le service d’itinéraire suivant.  
  
 Pour plus d’informations sur l’implémentation d’un service d’itinéraire personnalisé à l’aide des orchestrations BizTalk Server, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) et [installer et exécuter la ventilation-regroupement. Exemple](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).