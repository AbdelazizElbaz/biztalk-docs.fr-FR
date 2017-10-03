---
title: "Interfaces de récepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7ab77d4-705a-4b39-8c33-a7532ae6484c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77b42530d721a6dcee52e082fe46deae9ae06405
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receiver-interfaces"></a><span data-ttu-id="fbd49-102">Interfaces de réception</span><span class="sxs-lookup"><span data-stu-id="fbd49-102">Receiver Interfaces</span></span>
<span data-ttu-id="fbd49-103">En plus des interfaces d’adaptateur standard, adaptateurs de réception doivent implémenter **IBTTransportConfig**.</span><span class="sxs-lookup"><span data-stu-id="fbd49-103">In addition to the standard adapter interfaces, receive adapters need to implement **IBTTransportConfig**.</span></span> <span data-ttu-id="fbd49-104">C'est dans cette interface que le moteur de messagerie BizTalk fournit la configuration de l'emplacement de réception à l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="fbd49-104">This is the interface on which the BizTalk Messaging Engine delivers receive location configuration to the adapter.</span></span>  
  
## <a name="request-response-adapters"></a><span data-ttu-id="fbd49-105">Adaptateurs de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="fbd49-105">Request-Response Adapters</span></span>  
 <span data-ttu-id="fbd49-106">Les adaptateurs ont parfois également besoin de traiter des messages d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fbd49-106">Receive adapters may also need to handle send messages in some cases.</span></span> <span data-ttu-id="fbd49-107">Les adaptateurs qui en sont capables sont généralement appelés adaptateurs bidirectionnels ou de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="fbd49-107">Adapters that do this are usually referred to as two-way, or Request-Response adapters.</span></span> <span data-ttu-id="fbd49-108">Pour être en mesure d’envoyer des messages, un adaptateur de réception doit implémenter **IBTTransmitter**.</span><span class="sxs-lookup"><span data-stu-id="fbd49-108">To be able to send messages, a receive adapter needs to implement **IBTTransmitter**.</span></span>  
  
 <span data-ttu-id="fbd49-109">L’illustration suivante montre les interfaces implémentées par les adaptateurs de réception.</span><span class="sxs-lookup"><span data-stu-id="fbd49-109">The following figure shows the interfaces implemented by receive adapters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbd49-110">Le **IBTBatchTransmitter** interface n’est pas prise en charge pour les adaptateurs de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="fbd49-110">The **IBTBatchTransmitter** interface is not supported for Request-Response adapters.</span></span>  
  
 ![](../core/media/requestresponseadapters.gif "RequestResponseAdapters")