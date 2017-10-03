---
title: "Optimisation des performances de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a46455c-a8d2-4427-99bb-4e3c6dbd9566
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d4a2bd1f2cfa338d31fd574879d73249d74d08b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-mqseries-adapter-performance"></a>Optimisation des performances de l’adaptateur MQSeries
Configurer l’adaptateur MQSeries en utilisant les paramètres suivants lorsqu’il est possible d’augmenter les performances.  
  
## <a name="adjust-the-value-for-the-mqseries-receive-adapter-polling-threads"></a>Ajuster la valeur de threads de l’interrogation de l’adaptateur de réception les MQSeries  
 Augmentez la valeur spécifiée pour **Threads** dans les **propriétés du Transport MQSeries** lorsque l’adaptateur MQSeries de configuration des emplacements de réception. Si vous augmentez la valeur par défaut de 2 à une valeur de 5 améliore considérablement la vitesse à laquelle les messages peuvent être reçus à l’aide de l’adaptateur MQSeries.  
  
## <a name="disable-transaction-support-on-mqseries-receive-locations-where-not-required"></a>Emplacements de réception de la prise en charge des transactions de désactiver sur MQSeries où ne pas requis  
 Prise en charge des transactions de l’adaptateur MQSeries entraîne une surcharge significative. Si la prise en charge de la transaction n’est pas une exigence, définissez la **Transaction prise en charge** valeur dans le **propriétés du Transport MQSeries** boîte de dialogue à partir de la valeur par défaut **Oui**à **non**.  
  
## <a name="disable-ordered-delivery-of-messages-on-the-mqseries-adapter-when-not-required"></a>Désactiver la livraison chronologique des messages sur l’adaptateur MQSeries lorsque ne pas requis  
 L’activation de cette propriété applique la livraison chronologique des messages entre comme ils sont reçus ou envoyés à la file d’attente MQSeries mais affectera les performances. Lors de la livraison chronologique des messages sont activé, le runtime de messagerie utilisera un thread unique pour recevoir des messages à partir d’une file d’attente MQSeries. Si ordonné de remise de messages n’est pas une exigence, puis ne modifiez pas la valeur par défaut **commandé** propriété dans le **propriétés du Transport MQSeries** boîte de dialogue qui est défini comme **N° Classement**.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de BizTalk Server](../technical-guides/optimizing-biztalk-server-performance.md)