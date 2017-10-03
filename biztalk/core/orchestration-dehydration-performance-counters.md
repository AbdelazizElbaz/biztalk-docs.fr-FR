---
title: "Compteurs de performances de mise en attente d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ab92e0e-6a33-4aaa-ab14-0c82322b04d5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e81052f0061ff4ad802a084536c09d48cb6cb55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-dehydration-performance-counters"></a>Compteurs de performances de la mise en attente des orchestrations
Le tableau suivant répertorie les noms des compteurs de performance du moteur d'orchestration propres à la surveillance du comportement de mise en attente. Servez-vous de l'Analyseur de performances pour observer ces compteurs pendant le réglage des paramètres de mise en attente.  
  
|Compteurs de performance de la mise en attente|Description|  
|-------------------------------------|-----------------|  
|Orchestrations pouvant être en attente|Nombre d'instances d'orchestration pouvant être mises en attente et actuellement hébergées par l'instance de l'hôte.|  
|Mise en attente des orchestrations|Nombre d'orchestrations qui se trouvent dans le processus de mise en attente.|  
|Cycle de mise en attente en cours|Indique s'il y a un cycle de mise en attente actuellement en cours.|  
|Cycles de mise en attente|Nombre de cycles de mise en attente réussis.|  
|Seuil de mise en attente|Nombre, en millisecondes, qui détermine la rapidité avec laquelle les orchestrations sont mises en attente. Si le moteur d'orchestration prévoit qu'une instance pourra être mise en attente dans un délai supérieur à ce seuil, il la met en attente.|  
|Orchestrations dehydrated (Orchestrations mises en attente)|Nombre d'instances d'orchestration mises en attente depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations dehydrated/sec (Orchestrations mises en attente par seconde)|Nombre moyen d'orchestrations mises en attente par seconde.|  
|Orchestrations rehydrated (Orchestrations réalimentées)|Nombre d'instances d'orchestration réalimentées depuis le démarrage de l'instance de l'hôte.|  
|Orchestrations rehydrated/sec (Orchestrations réalimentées par seconde)|Nombre moyen d'orchestrations réalimentées par seconde|  
|Orchestrations avec mise en attente planifiée|Nombre d'orchestrations pouvant être mises en attente pour lesquelles une requête de mise en attente est en cours.|