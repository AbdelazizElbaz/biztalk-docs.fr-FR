---
title: "Définition de l’exécution du Service d’Orchestration personnalisée à l’aide d’itinéraires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6089169d-2fa1-4f81-afe1-db9d90a10382
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9336969db2c90168bf7c398276205043b06504ce
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="defining-custom-orchestration-service-execution-using-itineraries"></a>Définition de l’exécution du Service d’Orchestration personnalisée à l’aide d’itinéraires
Dans ce cas de figure, un message envoyé pour traitement contient un en-tête SOAP d’itinéraire qui décrit la liste des services d’exécuter et de leurs besoins en résolution. L’itinéraire spécifie un ou plusieurs orchestrations personnalisées ou les processus via lequel le message sera transmis au cours du cycle de traitement. Orchestrations personnalisées ont un contrôle total de l’itinéraire et les autres propriétés personnalisées exposées dans le contexte du message. Si vous le souhaitez, l’itinéraire peut contenir des informations de résolution dynamique qui détermine les spécifications de transformation et de points de terminaison pour le message. La figure 1 illustre une vue schématique du processus.  
  
 ![Définition d’une Orchestration personnalisée](../esb-toolkit/media/ch3-definingcustomorchestration.gif "Ch3-DefiningCustomOrchestration")  
  
 **Figure 1**  
  
 **Définition de l’exécution du service d’orchestration personnalisée à l’aide d’itinéraires**  
  
 L’exemple de feuille de route rampe d’entrée fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment créer des itinéraires qui contiennent des instructions d’appel de service, de routage et de résolution sous la forme d’une série d’étapes d’itinéraire qui définissent la façon dont l’ESB et BizTalk Server traite le message d’entrée. Unidirectionnel et exemples de requête-réponse.  
  
 Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).