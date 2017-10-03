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
ms.openlocfilehash: 9daf93fd6c925e5412aef3f4e985dd966f576eee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="changes-in-dehydration-policy-from-biztalk-server-2004"></a>Modifications dans la stratégie de mise en attente de BizTalk Server 2004
La stratégie de mise en attente de BizTalk Server a été modifiée entre [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. L'explication de la différence entre [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] peut être résumée par la valeur booléenne suivante, qui détermine la mise en attente dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] (true = mettre en attente).  
  
```  
Dehydrate = (WaitingHistory == -1 OR WaitingHistory > TestThreshold)  
```  
  
 Stratégie de mise en attente pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] a changé de cette façon secondaire. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]met toujours à une réception attente ou d’écoute s’il existe une attente plue de 2 ***MaxThreshold**.