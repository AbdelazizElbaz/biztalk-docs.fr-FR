---
title: "Modifications des stratégies de mise en attente de BizTalk Server 2004 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c760bffe-5f64-4eb2-bc23-89d7c9310f39
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 167c53d953369d7b35138995b4f38ad8994c18cb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="changes-in-dehydration-policy-from-biztalk-server-2004"></a>Modifications dans la stratégie de mise en attente de BizTalk Server 2004
Stratégie de mise en attente de BizTalk Server a changé depuis [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] à BizTalk Server. L’explication de la différence entre [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et BizTalk Server peut être résumée par l’expression booléenne suivante qui détermine la mise en attente dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] (true = mise en attente)  
  
```  
Dehydrate = (WaitingHistory == -1 OR WaitingHistory > TestThreshold)  
```  
  
 Stratégie de mise en attente pour BizTalk Server a changé de cette façon secondaire. BizTalk Server met toujours à une réception attente ou d’écoute s’il existe une attente plue de 2 ***MaxThreshold**.