---
title: "Considérations de sécurité pour le développement d’Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, orchestrations
- messages, subscriptions
- orchestrations, security
- messages, security
ms.assetid: a29b2018-4a8f-49ad-a817-6f279db3f801
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e020759a8d389461978a4de4138bcc139d527539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-developing-orchestrations"></a><span data-ttu-id="8603a-102">Considérations de sécurité pour le développement d’Orchestrations</span><span class="sxs-lookup"><span data-stu-id="8603a-102">Security Considerations for Developing Orchestrations</span></span>
<span data-ttu-id="8603a-103">Lorsque vous concevez vos orchestrations, vous devez envisager l'éventualité de problèmes de sécurité.</span><span class="sxs-lookup"><span data-stu-id="8603a-103">When designing your orchestrations, you should consider potential security issues.</span></span>  
  
## <a name="avoid-subscriptions-based-on-content-from-untrusted-messages"></a><span data-ttu-id="8603a-104">Évitez les abonnements basés sur des contenus de messages non approuvés</span><span class="sxs-lookup"><span data-stu-id="8603a-104">Avoid subscriptions based on content from untrusted messages</span></span>  
 <span data-ttu-id="8603a-105">Pour vous assurer qu'un message doté de peu de privilèges n'initie pas une instance d'orchestration qui pourrait créer des abonnements basés sur le contenu du message ou le contexte, nous vous recommandons fortement d'empêcher vos orchestrations de créer leurs abonnements de message sur la base du contenu ou du contexte d'un message non approuvé.</span><span class="sxs-lookup"><span data-stu-id="8603a-105">To ensure that a low-privilege message does not initiate an orchestration instance that could potentially create subscriptions based on the message content or context, it is highly recommended that your orchestrations do not create their message subscriptions based on the content or context of a message that is not trusted.</span></span>  
  
 <span data-ttu-id="8603a-106">Pour plus d’informations sur la sécurité dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [sécurisation de BizTalk Server](../core/securing-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="8603a-106">For information about security in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Securing BizTalk Server](../core/securing-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8603a-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8603a-107">See Also</span></span>  
 <span data-ttu-id="8603a-108">[Création d’Orchestrations](../core/creating-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="8603a-108">[Creating Orchestrations](../core/creating-orchestrations.md) </span></span>  
 [<span data-ttu-id="8603a-109">À propos des Orchestrations</span><span class="sxs-lookup"><span data-stu-id="8603a-109">About Orchestrations</span></span>](../core/about-orchestrations.md)