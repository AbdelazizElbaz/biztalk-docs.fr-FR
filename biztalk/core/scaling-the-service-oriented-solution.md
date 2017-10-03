---
title: "Le Service de mise à l’échelle de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling, service solutions
- service solution tutorial, scaling
ms.assetid: 6c22a68d-03e7-4174-b612-0e2246aa9413
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3026664d3a365630c93bf1c61d7cf635fdd9dc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-the-service-oriented-solution"></a>Le Service de mise à l’échelle de la Solution orientée services
Pour faire évoluer la solution de manière à ce qu'elle prenne en charge un débit plus élevé tout en conservant une faible latence pour les messages, vous devez utilisez la version Inline de la solution. Celle-ci contourne la base de données MessageBox lors de l'interaction avec les systèmes principaux.  
  
 Vous pouvez également ajouter des serveurs de traitement BizTalk Server destinés à exécuter les orchestrations. Cela permet de réduire l'utilisation de chaque serveur et d'augmenter la rapidité du traitement des nouvelles demandes. Vous pouvez aussi faire évoluer le serveur MessageBox en augmentant sa capacité de traitement de manière à ce qu'il puisse répondre au débit de messages.  
  
 Toutefois, la solution d'architecture orientée services ne tire pas profit d'avoir à disposition plusieurs bases de données MessageBox. En effet, cette situation exige des transactions DTC (Distributed Transaction Coordinator). Les transactions augmentent la latence globale au niveau des messages.  
  
 Vous pouvez améliorer le temps de réponse en supprimant le composant de pipeline qui ajoute des informations d'en-tête MQSeries. Pour plus d’informations, consultez [met en surbrillance de l’implémentation de la Solution orientée services](../core/implementation-highlights-of-the-service-oriented-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md)