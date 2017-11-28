---
title: "Architecture de l’adaptateur BizTalk pour TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transmit adapter
- one-way receive operations
- architecture
- one-way send operations
- receive adapter
ms.assetid: 304c7236-aacd-4761-8c33-e876b53e84ff
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c7bc6420efb67085e4f3a05f6daf0c5dbd2feb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-tibco-enterprise-message-service"></a><span data-ttu-id="b763e-102">Architecture de l'adaptateur BizTalk pour TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="b763e-102">Architecture of BizTalk Adapter for TIBCO Enterprise Message Service</span></span>
<span data-ttu-id="b763e-103">L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service constitue un moyen d'échanger des données commerciales en temps réel entre les systèmes TIBCO EMS et BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b763e-103">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) provides a means to exchange real-time business data between TIBCO EMS systems and BizTalk Server.</span></span> <span data-ttu-id="b763e-104">L'adaptateur permet l'interaction entre une application XML et TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b763e-104">The adapter enables interaction between an XML application and TIBCO EMS.</span></span>  
  
 <span data-ttu-id="b763e-105">L'adaptateur accepte les messages XML qui permettent aux applications BizTalk de communiquer avec TIBCO EMS à l'aide d'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b763e-105">The adapter accepts XML messages that enable BizTalk applications to communicate with TIBCO EMS using one of the following:</span></span>  
  
-   <span data-ttu-id="b763e-106">**Adaptateur de transmission**: utilise un port d’envoi unidirectionnel statique pour envoyer un message à TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b763e-106">**Transmit Adapter**: Uses a static one-way send port to send a message to TIBCO EMS.</span></span>  
  
-   <span data-ttu-id="b763e-107">**Adaptateur de réception**: utilise un unidirectionnel statique port de réception pour recevoir des messages de TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b763e-107">**Receive Adapter**: Uses a static one-way receive port to receive messages from TIBCO EMS.</span></span>  
  
## <a name="one-way-send-operation"></a><span data-ttu-id="b763e-108">Opération d'envoi unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="b763e-108">One-Way Send Operation</span></span>  
 <span data-ttu-id="b763e-109">La figure suivante illustre l'architecture d'une opération d'envoi unidirectionnelle à l'aide de l'adaptateur BizTalk pour TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b763e-109">The following figure shows the architecture of a one-way send operation using BizTalk Adapter for TIBCO EMS.</span></span>  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
## <a name="one-way-receive-operation"></a><span data-ttu-id="b763e-110">Opération de réception unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="b763e-110">One-Way Receive Operation</span></span>  
 <span data-ttu-id="b763e-111">La figure suivante illustre l'architecture d'une opération de réception unidirectionnelle à l'aide de l'adaptateur BizTalk pour TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="b763e-111">The following figure shows the architecture for a one-way receive operation using BizTalk Adapter for TIBCO EMS.</span></span>  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a><span data-ttu-id="b763e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b763e-112">See Also</span></span>  
 <span data-ttu-id="b763e-113">[Fonctionnalités de l’adaptateur](../core/adapter-features.md) </span><span class="sxs-lookup"><span data-stu-id="b763e-113">[Adapter Features](../core/adapter-features.md) </span></span>  
 [<span data-ttu-id="b763e-114">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="b763e-114">Planning and Architecture</span></span>](../core/planning-and-architecture16.md)