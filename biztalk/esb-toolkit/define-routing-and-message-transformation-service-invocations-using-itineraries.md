---
title: "Définition du routage et d’appels de Service de Transformation à l’aide d’itinéraires de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6f2448e-a5a7-496c-86d3-47f12e6f1251
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 975c830f73e0de362b25f312a8d41c4b15368cfd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-routing-and-message-transformation-service-invocations-using-itineraries"></a>Définition de routage et d’appels de Service de Transformation de Message à l’aide d’itinéraires
Dans ce cas de figure, un message envoyé pour traitement contient un en-tête SOAP d’itinéraire qui décrit la liste des services d’exécuter et de leurs besoins en résolution. Plus précisément, une transformation et le service de routage sont définis, chacun éventuellement nécessitant une résolution d’une recherche Universal Description, Discovery et Integration (UDDI), stratégie de moteur de règles d’entreprise, XML Path Language (XPath) ou statique. Ce cas de figure peut être étendu en ajoutant d’autres services à l’itinéraire au moment de la publication des messages.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] propose deux types d’écarts d’itinéraire : ceux qui prennent en charge la communication unidirectionnelle et ceux qui prennent en charge les scénarios de requête-réponse. Car le mécanisme de résolution dynamique peut utiliser des informations dans la feuille de route pour rechercher des points de terminaison ou de la liaison dynamique aux points de terminaison, il n’est pas nécessaire pour Microsoft BizTalk Server contenir les informations de routage de point de terminaison spécifique. La figure 1 illustre une vue schématique du processus.  
  
 ![Définir le service de routage appel](../esb-toolkit/media/ch3-definingroutingserviceinvocation.gif "Ch3-DefiningRoutingServiceInvocation")  
  
 **Figure 1**  
  
 **Définition de message et routage des appels de service de transformation à l’aide d’itinéraires**  
  
 L’exemple de feuille de route rampe d’entrée fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment créer des itinéraires qui contiennent la résolution, le routage, et obtenir des instructions de l’appel de service comme une série d’étapes d’itinéraire qui définissent comment les [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et BizTalk Server traite le message à l’aide de la publication-s’abonner à des fonctionnalités de BizTalk Server. Unidirectionnel et exemples de requête-réponse.  
  
 Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).