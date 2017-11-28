---
title: "Messagerie fiable avec l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, reliability
- reliability
- reliability, MSMQ adapters
- MSMQ adapters, reliability
- reliability, messages
ms.assetid: 1a4b4f77-c508-4c3f-82f9-5722d0af6c63
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc90ce4619527a6c53cbaf5a2546cb8708362b65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reliable-messaging-with-the-msmq-adapter"></a><span data-ttu-id="349bb-102">Messagerie fiable avec l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="349bb-102">Reliable Messaging with the MSMQ Adapter</span></span>
<span data-ttu-id="349bb-103">Vous pouvez améliorer la fiabilité des opérations d'envoi et de réception des messages avec l'adaptateur MSMQ grâce à l'utilisation de paramètres de configuration particuliers et des transactions.</span><span class="sxs-lookup"><span data-stu-id="349bb-103">You can improve the reliability of sending and receiving messages with the MSMQ adapter by using particular configuration settings and by using transactions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="349bb-104">Vous risquez de perdre des messages au sein d'une configuration en cluster si vous n'utilisez pas les transactions et si un ordinateur rencontre une défaillance.</span><span class="sxs-lookup"><span data-stu-id="349bb-104">If you do not use transactions, you can lose messages in clustered configurations if a computer fails.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="349bb-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="349bb-105">In This Section</span></span>  
  
-   [<span data-ttu-id="349bb-106">Propriétés de la messagerie fiable avec l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="349bb-106">Properties for Reliable Messaging with the MSMQ Adapter</span></span>](../core/properties-for-reliable-messaging-with-the-msmq-adapter.md)  
  
-   [<span data-ttu-id="349bb-107">La gestion avec l’adaptateur MSMQ de transaction</span><span class="sxs-lookup"><span data-stu-id="349bb-107">Transaction Handling with the MSMQ Adapter</span></span>](../core/transaction-handling-with-the-msmq-adapter.md)