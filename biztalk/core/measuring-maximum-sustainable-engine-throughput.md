---
title: "Mesurer le débit de moteur maximal acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST)
- maximum sustainable throughput (MST), about maximum sustainable throughput (MST)
- performance, maximum sustainable thoughput (MST)
ms.assetid: d83f734f-1a44-4da0-a755-45ba204cadaf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5507aca58669ed5c81034ba91e16d1183e07188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="measuring-maximum-sustainable-engine-throughput"></a>Mesure du débit maximal acceptable du moteur
L'une des principaux points à prendre en compte lors de la planification d'un système BizTalk Server est le débit maximal acceptable du système. Le débit maximal acceptable d'un système BizTalk Server correspond à la charge maximale de flux de messages qu'un système BizTalk est capable de gérer indéfiniment dans un environnement de production. Cette valeur est très importante car lorsque la charge dépasse le débit maximal acceptable, les messages sont mis en file d'attente dans la base de données MessageBox, ce qui peut en retarder la livraison. Si vous calculez le débit maximal acceptable de votre système BizTalk Server dans le cadre d'un test normal, vous pouvez adapter votre système de façon à éviter des scénarios de surcharge étendue dans l'environnement de production.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Facteurs qui affectent les performances maximales admissibles](../core/factors-that-affect-maximum-sustainable-performance.md)  
  
-   [Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md)  
  
-   [Recommandations pour le test de performances du moteur](../core/recommendations-when-testing-engine-performance.md)