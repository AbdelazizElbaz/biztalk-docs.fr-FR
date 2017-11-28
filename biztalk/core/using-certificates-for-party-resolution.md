---
title: "L’utilisation de certificats pour la résolution du tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eb9b616-be1c-4b68-b3de-8721a344a423
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b157191e4004671a8b276f47d15a8589974dfbac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-certificates-for-party-resolution"></a><span data-ttu-id="bc840-102">Utilisation des certificats pour la résolution de tiers</span><span class="sxs-lookup"><span data-stu-id="bc840-102">Using Certificates for Party Resolution</span></span>
<span data-ttu-id="bc840-103">A *tiers* est une entité externe à BizTalk Server qui interagit avec une orchestration.</span><span class="sxs-lookup"><span data-stu-id="bc840-103">A *party* is an entity outside BizTalk Server that interacts with an orchestration.</span></span> <span data-ttu-id="bc840-104">Lorsque BizTalk Server reçoit un message, il se sert du certificat de clé publique pour en identifier l'expéditeur et pour l'associer à un tiers connu dans l'environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bc840-104">When BizTalk Server receives a message, it uses the public key certificate to determine who sent the message, and to resolve the sender to a known party in the BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="bc840-105">Cette section fournit des informations sur la configuration des pipelines [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], des emplacements de réception, des ports et de l'environnement BizTalk Server pour la résolution de tiers.</span><span class="sxs-lookup"><span data-stu-id="bc840-105">This section provides information about how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines, receive locations, ports, and the BizTalk Server environment for party resolution.</span></span>  
  
 <span data-ttu-id="bc840-106">Pour plus d’informations sur l’authentification d’un message, consultez [authentification de l’expéditeur d’un Message](../core/authenticating-the-sender-of-a-message.md).</span><span class="sxs-lookup"><span data-stu-id="bc840-106">For more information about authentication of a message, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc840-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bc840-107">In This Section</span></span>  
 [<span data-ttu-id="bc840-108">Comment configurer BizTalk Server pour la résolution du tiers</span><span class="sxs-lookup"><span data-stu-id="bc840-108">How to Configure BizTalk Server for Party Resolution</span></span>](../core/how-to-configure-biztalk-server-for-party-resolution.md)