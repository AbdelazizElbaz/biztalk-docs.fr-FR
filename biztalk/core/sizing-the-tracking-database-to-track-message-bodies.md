---
title: "Dimensionnement de la base de données de suivi pour suivre les corps de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
- message variables [Tracking database], MsgNum
- HAT, ports
- Tracking database, messages
- tracking, orchestrations
- tracking, messages
- HAT, orchestrations
- tracking, ports
ms.assetid: ee75e530-f15d-4ceb-ba67-0b0b24d9df6b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b5abc3f2a48f2baea5d158e1a0268a7eede51c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sizing-the-tracking-database-to-track-message-bodies"></a><span data-ttu-id="0465f-102">Dimensionnement de la base de données des suivis pour suivre les corps de message</span><span class="sxs-lookup"><span data-stu-id="0465f-102">Sizing the Tracking Database to Track Message Bodies</span></span>
<span data-ttu-id="0465f-103">Si vous envisagez de mettre en place un suivi des corps de message dans la base de données des suivis BizTalk, vous devez prendre en compte la taille du corps de ces messages dans vos calculs.</span><span class="sxs-lookup"><span data-stu-id="0465f-103">If you plan to track the message bodies in the BizTalk Tracking database, then you will also need to account for the size of these bodies in your calculation.</span></span> <span data-ttu-id="0465f-104">Pour cela, utilisez l'équation suivante :</span><span class="sxs-lookup"><span data-stu-id="0465f-104">Use the following equation:</span></span>  
  
```  
[Msgs * MsgNum * (MsgSize)]/1024 = Data size in MB  
```  
  
 <span data-ttu-id="0465f-105">Pensez à ajouter la taille moyenne du contexte de message à MsgSize s'il est beaucoup plus important que la taille des messages.</span><span class="sxs-lookup"><span data-stu-id="0465f-105">Consider adding the average size of the message context to MsgSize above if it is significant compared to the message size.</span></span>  
  
 <span data-ttu-id="0465f-106">La variable MsgNum est déterminée par l'activation des fonctionnalités de suivi au niveau du port ou de l'orchestration à l'aide de l'événement de message et du suivi des instances de service dans la page Hub du groupe.</span><span class="sxs-lookup"><span data-stu-id="0465f-106">The MsgNum variable is determined by turning on the tracking features at the port level or at the orchestration level using the message event and service instance tracking in the Group Hub page.</span></span> <span data-ttu-id="0465f-107">Vous devez appliquer cette formule à chaque traitement de message.</span><span class="sxs-lookup"><span data-stu-id="0465f-107">You must apply this formula to each message process as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0465f-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0465f-108">See Also</span></span>  
 <span data-ttu-id="0465f-109">[À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="0465f-109">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="0465f-110">[Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="0465f-110">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="0465f-111">[Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="0465f-111">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 <span data-ttu-id="0465f-112">[Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="0465f-112">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="0465f-113">Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution</span><span class="sxs-lookup"><span data-stu-id="0465f-113">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)