---
title: "Définition du routage et de Transformation via plusieurs Orchestrations à l’aide d’itinéraires des messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63141b83-798e-40d0-908d-6b7649923e69
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c5a87b06700794dca6c4aae9588c3068b98d995
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-routing-and-message-transformation-through-multiple-orchestrations-using-itineraries"></a>Définition de routage et de Transformation des messages via plusieurs Orchestrations à l’aide d’itinéraires
Dans ce cas de figure, un message envoyé pour traitement contient un en-tête SOAP d’itinéraire qui décrit la liste des services d’exécuter et de leurs besoins en résolution. L’itinéraire spécifie une ou plusieurs orchestrations Microsoft BizTalk Server par le biais duquel le message sera transmis au cours du cycle de traitement. Si vous le souhaitez, l’itinéraire peut contenir des informations de routage dynamique permet de déterminer les points de terminaison ou des spécifications de transformation pour le message. La figure 1 illustre une vue schématique du processus.  
  
 ![Définition du routage de plusieurs Orchestrations](../esb-toolkit/media/ch3-definingroutingmultipleorchestrations.gif "Ch3-DefiningRoutingMultipleOrchestrations")  
  
 **Figure 1**  
  
 **Définition de transformation de routage et le message via plusieurs orchestrations à l’aide d’itinéraires**  
  
 L’exemple de feuille de route rampe d’entrée fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment créer des itinéraires qui contiennent la résolution, le routage, et obtenir des instructions de l’appel de service comme une série d’étapes d’itinéraire qui définissent comment les [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et BizTalk Server traite le message d’entrée. Unidirectionnel et exemples de requête-réponse.  
  
 Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).