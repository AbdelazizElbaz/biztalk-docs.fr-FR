---
title: AS2 Architecture de la Solution | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41e493ba-919b-4520-9c12-92d6757984ef
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c22557059bd13dd99e0b24a2291b7f121d561bbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-solution-architecture"></a><span data-ttu-id="0b5a7-102">Architecture de la solution AS2</span><span class="sxs-lookup"><span data-stu-id="0b5a7-102">AS2 Solution Architecture</span></span>
<span data-ttu-id="0b5a7-103">Le traitement AS2 s'effectue distinctement du traitement EDI.</span><span class="sxs-lookup"><span data-stu-id="0b5a7-103">AS2 processing is performed separately from EDI processing.</span></span> <span data-ttu-id="0b5a7-104">Les messages AS2 sont reçus et traités, puis un accusé de réception est envoyé en marge du traitement de la charge EDI.</span><span class="sxs-lookup"><span data-stu-id="0b5a7-104">AS2 messages are received, processed, and an acknowledgment sent apart from the processing of the EDI payload.</span></span> <span data-ttu-id="0b5a7-105">Par conséquent, le traitement AS2 est conçu et configuré distinctement du traitement EDI.</span><span class="sxs-lookup"><span data-stu-id="0b5a7-105">As a result, AS2 processing is designed and configured apart from EDI processing.</span></span> <span data-ttu-id="0b5a7-106">En outre, vous pouvez utiliser le transport AS2 pour les messages EDI ou les messages non-EDI.</span><span class="sxs-lookup"><span data-stu-id="0b5a7-106">In addition, you can use AS2 to transport either EDI messages or non-EDI messages.</span></span>  
  
 <span data-ttu-id="0b5a7-107">Cette section décrit l'architecture des solutions AS2 sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment le traitement de bout en bout, côté réception et côté envoi.</span><span class="sxs-lookup"><span data-stu-id="0b5a7-107">This section describes the architecture of AS2 solutions on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], including end-to-end, receive-side, and send-side processing.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0b5a7-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0b5a7-108">In This Section</span></span>  
  
-   [<span data-ttu-id="0b5a7-109">Messagerie AS2</span><span class="sxs-lookup"><span data-stu-id="0b5a7-109">AS2 Messaging</span></span>](../core/as2-messaging.md)  
  
-   [<span data-ttu-id="0b5a7-110">Rôle des accords AS2 de traitement</span><span class="sxs-lookup"><span data-stu-id="0b5a7-110">The Role of Agreements in AS2 Processing</span></span>](../core/the-role-of-agreements-in-as2-processing.md)  
  
-   [<span data-ttu-id="0b5a7-111">Réception des Messages AS2 par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0b5a7-111">How BizTalk Server Receives AS2 Messages</span></span>](../core/how-biztalk-server-receives-as2-messages.md)  
  
-   [<span data-ttu-id="0b5a7-112">Envoi des Messages AS2 par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0b5a7-112">How BizTalk Server Sends AS2 Messages</span></span>](../core/how-biztalk-server-sends-as2-messages.md)