---
title: "MQSeries le traitement par lot de l’adaptateur et la gestion des transactions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IBM WebSphere MQ queues
- transactions, MQSeries adapters
- MQSeries adapters, transactions
- MQSeries adapters, IBM WebSphere MQ queues
- MQSeries adapters, batching
- batching, MQSeries adapters
ms.assetid: 2e43fca9-acbd-4fd3-8df3-5f7398553830
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffcdec02c464b9398acbece35657e0c3d1dc4432
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-batching-and-transaction-handling"></a>Le traitement par lot de l’adaptateur MQSeries et gestion des transactions
L'adaptateur MQSeries arrête une transaction uniquement s'il ne reçoit pas toutes les données. Les limites d'une transaction pour l'adaptateur sont le point de terminaison de l'adaptateur (file d'attente MQSeries sur le serveur MQSeries) et la base de données MessageBox.  
  
 Si l'application BizTalk invalide un message, l'adaptateur déplace le message vers la file d'attente des messages interrompus. Comme il s'agit toujours d'une transaction valide du point de vue de l'adaptateur (l'adaptateur reçoit toutes les données), celui-ci valide tout de même la transaction.  
  
 Vous pouvez contrôler le traitement par lots et la gestion des transactions en définissant diverses propriétés lors de la configuration de l'adaptateur. Pour plus d’informations, consultez [configuration de l’adaptateur MQSeries](../core/configuring-the-mqseries-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md)