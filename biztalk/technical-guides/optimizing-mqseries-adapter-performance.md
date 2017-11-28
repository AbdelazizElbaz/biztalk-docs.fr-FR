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
# <a name="optimizing-mqseries-adapter-performance"></a><span data-ttu-id="a6373-102">Optimisation des performances de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="a6373-102">Optimizing MQSeries Adapter Performance</span></span>
<span data-ttu-id="a6373-103">Configurer l’adaptateur MQSeries en utilisant les paramètres suivants lorsqu’il est possible d’augmenter les performances.</span><span class="sxs-lookup"><span data-stu-id="a6373-103">Configure the MQSeries adapter by using the following settings when possible to increase performance.</span></span>  
  
## <a name="adjust-the-value-for-the-mqseries-receive-adapter-polling-threads"></a><span data-ttu-id="a6373-104">Ajuster la valeur de threads de l’interrogation de l’adaptateur de réception les MQSeries</span><span class="sxs-lookup"><span data-stu-id="a6373-104">Adjust the value for the MQSeries receive adapter polling threads</span></span>  
 <span data-ttu-id="a6373-105">Augmentez la valeur spécifiée pour **Threads** dans les **propriétés du Transport MQSeries** lorsque l’adaptateur MQSeries de configuration des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="a6373-105">Increase the value specified for **Threads** in the **MQSeries Transport Properties** when configuring MQSeries adapter receive locations.</span></span> <span data-ttu-id="a6373-106">Si vous augmentez la valeur par défaut de 2 à une valeur de 5 améliore considérablement la vitesse à laquelle les messages peuvent être reçus à l’aide de l’adaptateur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="a6373-106">Increasing this property from the default value of 2 to a value of 5 will significantly improve the rate at which messages can be received using the MQSeries adapter.</span></span>  
  
## <a name="disable-transaction-support-on-mqseries-receive-locations-where-not-required"></a><span data-ttu-id="a6373-107">Emplacements de réception de la prise en charge des transactions de désactiver sur MQSeries où ne pas requis</span><span class="sxs-lookup"><span data-stu-id="a6373-107">Disable transaction support on MQSeries receive locations where not required</span></span>  
 <span data-ttu-id="a6373-108">Prise en charge des transactions de l’adaptateur MQSeries entraîne une surcharge significative.</span><span class="sxs-lookup"><span data-stu-id="a6373-108">MQSeries adapter transaction support incurs significant overhead.</span></span> <span data-ttu-id="a6373-109">Si la prise en charge de la transaction n’est pas une exigence, définissez la **Transaction prise en charge** valeur dans le **propriétés du Transport MQSeries** boîte de dialogue à partir de la valeur par défaut **Oui**à **non**.</span><span class="sxs-lookup"><span data-stu-id="a6373-109">If transaction support is not a business requirement, set the **Transaction Supported** value in the **MQSeries Transport Properties** dialog box from the default value of **Yes** to **No**.</span></span>  
  
## <a name="disable-ordered-delivery-of-messages-on-the-mqseries-adapter-when-not-required"></a><span data-ttu-id="a6373-110">Désactiver la livraison chronologique des messages sur l’adaptateur MQSeries lorsque ne pas requis</span><span class="sxs-lookup"><span data-stu-id="a6373-110">Disable Ordered delivery of messages on the MQSeries Adapter when not required</span></span>  
 <span data-ttu-id="a6373-111">L’activation de cette propriété applique la livraison chronologique des messages entre comme ils sont reçus ou envoyés à la file d’attente MQSeries mais affectera les performances.</span><span class="sxs-lookup"><span data-stu-id="a6373-111">Enabling this property will enforce ordered delivery of messages as they are received from or sent to the MQSeries queue but will affect performance.</span></span> <span data-ttu-id="a6373-112">Lors de la livraison chronologique des messages sont activé, le runtime de messagerie utilisera un thread unique pour recevoir des messages à partir d’une file d’attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="a6373-112">When ordered delivery is enabled, the messaging runtime will use a single thread to receive messages from a given MQSeries queue.</span></span> <span data-ttu-id="a6373-113">Si ordonné de remise de messages n’est pas une exigence, puis ne modifiez pas la valeur par défaut **commandé** propriété dans le **propriétés du Transport MQSeries** boîte de dialogue qui est défini comme **N° Classement**.</span><span class="sxs-lookup"><span data-stu-id="a6373-113">If ordered delivery of messages is not a business requirement, then do not change the default value of **Ordered** property in the **MQSeries Transport Properties** dialog box which is set as **No Ordering**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6373-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6373-114">See Also</span></span>  
 [<span data-ttu-id="a6373-115">Optimisation des performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a6373-115">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)