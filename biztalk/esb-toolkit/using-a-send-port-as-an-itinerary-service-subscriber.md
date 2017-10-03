---
title: "À l’aide d’un Port d’envoi en tant qu’un abonné d’itinéraire Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 898b461c-4d0d-4703-a8ca-7f52f3f15f70
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5213b22c1bdfaa505dbf4b62a03095bcec5a1746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-send-port-as-an-itinerary-service-subscriber"></a>À l’aide d’un Port d’envoi en tant qu’un abonné d’itinéraire de Service
Figure 1 montre un exemple montrant comment utiliser un port d’envoi en tant qu’un abonné d’itinéraire de service, les conditions de filtre pour un port d’envoi unidirectionnel dynamique récupère les messages qui répondent aux conditions suivantes :  
  
-   **IsRequestResponse = False**  
  
-   **ServiceName = DynamicTest**  
  
-   **ServiceState = en attente**  
  
-   **ServiceType = messagerie**  
  
 ![Port d’envoi](../esb-toolkit/media/ch4-sendport.gif "chapitre 4-ports d’envoi")  
  
 **Figure 1**  
  
 **Exemple de filtres de port d’envoi**  
  
 Expressions de filtre de port pour spécifier les ensembles de propriété et la valeur de messages, elle reprendra à partir de la base de données de la boîte de Message via l’itinéraire rampe d’entrée d’envoi.  
  
> [!NOTE]
>  Il est important d’utiliser des conditions de filtre qui sont aussi spécifique et que la mesure du possible ; Sinon, il est un risque de récupérer des messages inattendus, ce qui peut provoquer des problèmes dans un environnement de haut volume. Le schéma.xsd de système définit les propriétés de filtre d’abonnements.