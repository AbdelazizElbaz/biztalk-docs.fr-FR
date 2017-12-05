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
# <a name="changes-in-dehydration-policy-from-biztalk-server-2004"></a><span data-ttu-id="8de5f-102">Modifications dans la stratégie de mise en attente de BizTalk Server 2004</span><span class="sxs-lookup"><span data-stu-id="8de5f-102">Changes in Dehydration Policy from BizTalk Server 2004</span></span>
<span data-ttu-id="8de5f-103">Stratégie de mise en attente de BizTalk Server a changé depuis [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8de5f-103">BizTalk Server dehydration policy has changed from [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] to BizTalk Server.</span></span> <span data-ttu-id="8de5f-104">L’explication de la différence entre [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] et BizTalk Server peut être résumée par l’expression booléenne suivante qui détermine la mise en attente dans [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] (true = mise en attente)</span><span class="sxs-lookup"><span data-stu-id="8de5f-104">The explanation for the difference between [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] and BizTalk Server can be summarized by the following Boolean that determines dehydration in [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] (true = dehydrate)</span></span>  
  
```  
Dehydrate = (WaitingHistory == -1 OR WaitingHistory > TestThreshold)  
```  
  
 <span data-ttu-id="8de5f-105">Stratégie de mise en attente pour BizTalk Server a changé de cette façon secondaire.</span><span class="sxs-lookup"><span data-stu-id="8de5f-105">Dehydration policy for BizTalk Server has changed in this minor way.</span></span> <span data-ttu-id="8de5f-106">BizTalk Server met toujours à une réception attente ou d’écoute s’il existe une attente plue de 2 ***MaxThreshold**.</span><span class="sxs-lookup"><span data-stu-id="8de5f-106">BizTalk Server always dehydrates at a receive/delay/listen if there is a wait longer than 2***MaxThreshold**.</span></span>