---
title: "À l’aide de routage basé sur la feuille de route | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d5b5d13-cbf2-4f3c-8a1a-3bb852f048a0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc0a0eb3a212efccd4ddbe4e275042ecb850095
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-itinerary-based-routing"></a>À l’aide de routage basé sur la feuille de route
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit le message basée sur un itinéraire de routage en implémentant le modèle de routage pour activer des scénarios lorsque les étapes de la séquence de traitement d’un message particulier n’est pas connu au moment du design et peut-être varier pour chaque message. L’implémentation de ce modèle utilise un bordereau de routage pour représenter une collection de ces étapes au format XML et détermine les étapes qui doivent se produire lors de l’exécution. Un état de bordereau, souvent appelé « feuille de route ESB », est un ensemble ordonné d’instructions déclaratives qui définissent les étapes qui doivent être exécutées pour un message comme il est traité par [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composants et l’exécution de BizTalk Server. Une instruction de traitement particulière spécifiée dans la feuille de route ESB est associée le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] composant, qui est également appelé « service d’itinéraire ESB. » Le service d’itinéraire ESB vise à exécuter les instructions de traitement et mettre à jour l’état du bon de routage pour indiquer la prochaine en attente de l’instruction.  
  
 Cette section décrit les fonctionnalités de traitement basé sur la feuille de route de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Elle contient les rubriques suivantes :  
  
-   [Gestion d’itinéraire d’ESB](../esb-toolkit/esb-itinerary-management.md)  
  
-   [Sur les écarts et les écarts](../esb-toolkit/on-ramps-and-off-ramps.md)  
  
-   [Choix entre la messagerie et d’Orchestration d’itinéraire](../esb-toolkit/choosing-between-messaging-and-orchestration-itinerary-services.md)  
  
-   [À l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant](../esb-toolkit/using-a-pipeline-component-to-select-an-existing-itinerary.md)  
  
-   [À l’aide d’un composant de Pipeline pour lire un itinéraire](../esb-toolkit/using-a-pipeline-component-to-read-an-itinerary.md)  
  
-   [À l’aide d’un composant de Pipeline pour mettre en Cache un itinéraire de sollicitation-réponse](../esb-toolkit/using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response.md)  
  
-   [Création d’abonnés d’itinéraire](../esb-toolkit/creating-itinerary-subscribers.md)  
  
-   [L’exécution d’un Service d’itinéraire](../esb-toolkit/executing-an-itinerary-service.md)  
  
-   Lien hypertexte « http://msdn.microsoft.com/en-us/library/ee236752 (BTS.10).aspx » [basée sur un itinéraire de routage artefacts](../esb-toolkit/itinerary-based-routing-artifacts.md)