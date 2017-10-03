---
title: "Envoi et réception de Messages volumineux à l’aide de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, large messages
- configuring [MSMQ adapters], large messages
- MSMQ adapters, large messages
ms.assetid: 208efbed-7b58-4da5-ba27-65a315c2713b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a23265be84f2767849e4d61c2e9a95bfc9ed4ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-and-receiving-large-messages-using-the-msmq-adapter"></a>Envoi et réception de messages volumineux à l'aide de l'adaptateur MSMQ
Le traitement des messages par défaut de l'adaptateur MSMQ dépend en partie de la taille du message. Lorsqu'un message est inférieur à quatre mégaoctets (4 Mo), l'adaptateur MSMQ utilise la bibliothèque de classes .NET Framework. Sinon, il utilise les extensions de messages volumineux dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Si votre application reçoit et envoie constamment des messages volumineux, vous pouvez contrôler la quantité de mémoire que l'adaptateur utilise. Pour plus d’informations sur la conservation de la mémoire, consultez [optimisation des performances de l’adaptateur MSMQ](../core/optimizing-performance-of-the-msmq-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de l’adaptateur MSMQ](../core/optimizing-performance-of-the-msmq-adapter.md)   
 [Configuration de l’adaptateur MSMQ](../core/configuring-the-msmq-adapter.md)