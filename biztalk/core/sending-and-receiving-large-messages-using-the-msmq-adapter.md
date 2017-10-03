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
# <a name="sending-and-receiving-large-messages-using-the-msmq-adapter"></a><span data-ttu-id="ff56b-102">Envoi et réception de messages volumineux à l'aide de l'adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="ff56b-102">Sending and Receiving Large Messages Using the MSMQ Adapter</span></span>
<span data-ttu-id="ff56b-103">Le traitement des messages par défaut de l'adaptateur MSMQ dépend en partie de la taille du message.</span><span class="sxs-lookup"><span data-stu-id="ff56b-103">The MSMQ adapter default message handling depends, in part, on the size of the message.</span></span> <span data-ttu-id="ff56b-104">Lorsqu'un message est inférieur à quatre mégaoctets (4 Mo), l'adaptateur MSMQ utilise la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff56b-104">When a message is less than four megabytes (4 MB), the MSMQ adapter uses the .NET Framework Class Library.</span></span> <span data-ttu-id="ff56b-105">Sinon, il utilise les extensions de messages volumineux dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ff56b-105">Otherwise, it uses the large message extensions in Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="ff56b-106">Si votre application reçoit et envoie constamment des messages volumineux, vous pouvez contrôler la quantité de mémoire que l'adaptateur utilise.</span><span class="sxs-lookup"><span data-stu-id="ff56b-106">If your application consistently receives or sends large messages, you may have to control the amount of memory that the adapter uses.</span></span> <span data-ttu-id="ff56b-107">Pour plus d’informations sur la conservation de la mémoire, consultez [optimisation des performances de l’adaptateur MSMQ](../core/optimizing-performance-of-the-msmq-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ff56b-107">For more information about conserving memory, see [Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff56b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff56b-108">See Also</span></span>  
 <span data-ttu-id="ff56b-109">[Optimisation des performances de l’adaptateur MSMQ](../core/optimizing-performance-of-the-msmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="ff56b-109">[Optimizing Performance of the MSMQ Adapter](../core/optimizing-performance-of-the-msmq-adapter.md) </span></span>  
 [<span data-ttu-id="ff56b-110">Configuration de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="ff56b-110">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)