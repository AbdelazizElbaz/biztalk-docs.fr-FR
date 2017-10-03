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
# <a name="mqseries-adapter-batching-and-transaction-handling"></a><span data-ttu-id="6c4f6-102">Le traitement par lot de l’adaptateur MQSeries et gestion des transactions</span><span class="sxs-lookup"><span data-stu-id="6c4f6-102">MQSeries Adapter Batching and Transaction Handling</span></span>
<span data-ttu-id="6c4f6-103">L'adaptateur MQSeries arrête une transaction uniquement s'il ne reçoit pas toutes les données.</span><span class="sxs-lookup"><span data-stu-id="6c4f6-103">The MQSeries adapter stops a transaction only if it does not receive all the data.</span></span> <span data-ttu-id="6c4f6-104">Les limites d'une transaction pour l'adaptateur sont le point de terminaison de l'adaptateur (file d'attente MQSeries sur le serveur MQSeries) et la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="6c4f6-104">The boundaries of a transaction for the adapter are the adapter endpoint (MQSeries queue on the MQSeries Server) and the MessageBox database.</span></span>  
  
 <span data-ttu-id="6c4f6-105">Si l'application BizTalk invalide un message, l'adaptateur déplace le message vers la file d'attente des messages interrompus.</span><span class="sxs-lookup"><span data-stu-id="6c4f6-105">If the BizTalk application invalidates a message, the adapter moves the message to the suspended queue.</span></span> <span data-ttu-id="6c4f6-106">Comme il s'agit toujours d'une transaction valide du point de vue de l'adaptateur (l'adaptateur reçoit toutes les données), celui-ci valide tout de même la transaction.</span><span class="sxs-lookup"><span data-stu-id="6c4f6-106">However, because it is still a valid transaction from the point of view of the adapter (the adapter received all the data), the adapter commits the transaction.</span></span>  
  
 <span data-ttu-id="6c4f6-107">Vous pouvez contrôler le traitement par lots et la gestion des transactions en définissant diverses propriétés lors de la configuration de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6c4f6-107">You can control batching and transaction handling by setting properties when configuring the adapter.</span></span> <span data-ttu-id="6c4f6-108">Pour plus d’informations, consultez [configuration de l’adaptateur MQSeries](../core/configuring-the-mqseries-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="6c4f6-108">For more information, see [Configuring the MQSeries Adapter](../core/configuring-the-mqseries-adapter.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4f6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c4f6-109">See Also</span></span>  
 [<span data-ttu-id="6c4f6-110">Propriétés de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6c4f6-110">MQSeries Adapter Properties</span></span>](../core/mqseries-adapter-properties.md)