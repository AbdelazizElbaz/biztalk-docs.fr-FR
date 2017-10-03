---
title: "Considérations relatives aux performances pour la publication d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- publishing, BAM
- BAM, publishing
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 5a99e61a-a3d9-47fd-a933-2297f79817a5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebab873c94c0ae17abf9938883662ca8777cef36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performance-considerations-for-bam-event-publishing"></a>Considérations de performances pour la publication d'événements BAM
Le composant d'analyse BAM prend en charge deux formes de publication d'événements commerciaux :  
  
-   Synchrone  
  
-   Asynchrone  
  
 Le diagramme suivant illustre ces deux modèles :  
  
 ![](../core/media/bam-topologies.gif "bam_topologies")  
Topologies BAM  
  
 L'approche synchrone est beaucoup plus simple pour la gestion et plus facile à utiliser à partir du code. L'approche asynchrone permet, quant à elle, des performances accrues.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Suivi des événements commerciaux synchrone](../core/synchronous-business-event-tracking.md)  
  
-   [Suivi des événements commerciaux asynchrone](../core/asynchronous-business-event-tracking.md)