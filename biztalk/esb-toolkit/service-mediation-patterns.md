---
title: "Modèles de médiation de service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfda54db-75fa-4bc2-9f48-11d8b3cde65b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af76e6c123a3a273bc2e100b1008f40523762695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-mediation-patterns"></a>Modèles de médiation de service
## <a name="vetovetro"></a>VETO/VETRO  
 Le modèle VETRO est un modèle courant composite qui combine plusieurs actions effectuées sur un message lorsqu’elle est reçue. Le terme VETRO est un acronyme validation, enrichissement, transformation, Route, opérer. Dans la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], ces actions peuvent être gérées comme des étapes individuelles dans le pipeline associé à l’emplacement de réception. Pour plus d’informations sur comment chacune de ces étapes peut être implémenté, consultez les scénarios de clé et les tâches de développement.  
  
## <a name="request-response"></a>Requête-réponse  
 Le modèle demande-réponse définit une solution dans lequel un service ou de tiers l’envoie une demande de message et attend un message de réponse en retour à partir du service de destination. Pour obtenir une description détaillée de ce modèle, consultez [demande-réponse](http://go.microsoft.com/fwlink/?LinkId=186849) ([http://go.microsoft.com/fwlink/?LinkId=186849](http://go.microsoft.com/fwlink/?LinkId=186849)) sur le site de modèles d’intégration d’entreprise.  
  
 Pour plus d’informations sur la façon d’implémenter ce modèle, consultez les ressources suivantes :  
  
-   [Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)  
  
-   [Installer et exécuter l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)