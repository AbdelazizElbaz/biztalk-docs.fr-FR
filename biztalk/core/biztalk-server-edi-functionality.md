---
title: "Fonctionnalité EDI de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fd91569-f246-40dc-acb1-4f9296479296
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10a037349cb967fab3d9c0d79bdf47c2f0f8a194
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-server-edi-functionality"></a><span data-ttu-id="b3812-102">Fonctionnalités EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3812-102">BizTalk Server EDI Functionality</span></span>
<span data-ttu-id="b3812-103">BizTalk Server traite les messages EDI à l’aide d’une combinaison du noyau [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI spécifiques et des fonctionnalités [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="b3812-103">BizTalk Server processes EDI messages using a combination of core [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features and EDI-specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features.</span></span> <span data-ttu-id="b3812-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut alors effectuer le traitement spécifique à la messagerie EDI tout en exploitant sa fonctionnalité principale de messagerie.</span><span class="sxs-lookup"><span data-stu-id="b3812-104">This enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform the processing that is unique to EDI messaging, while leveraging its core messaging functionality.</span></span>  
  
 <span data-ttu-id="b3812-105">Cette section présente le fonctionnement de la messagerie EDI de base et la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les implémente.</span><span class="sxs-lookup"><span data-stu-id="b3812-105">This section describes how basic EDI messaging works and how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implements it.</span></span> <span data-ttu-id="b3812-106">Elle illustre également la manière dont une définition d'accord de partenariat commercial dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut être exploitée dans la messagerie EDI ainsi que dans le traitement EDI , côté réception et côté envoi.</span><span class="sxs-lookup"><span data-stu-id="b3812-106">It also describes how a trading partner agreement definition in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be leveraged for EDI messaging, receive-side EDI processing, and send-side EDI processing.</span></span>  
  
 <span data-ttu-id="b3812-107">Pour obtenir une description de la prise en charge le traitement EDI dans BizTalk Server et d’autres versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]et pour obtenir une description de la prise en charge des normes EDI et la prise en charge des schémas de document EDI, consultez [problèmes de prise en charge EDI](../core/edi-support-issues.md).</span><span class="sxs-lookup"><span data-stu-id="b3812-107">For a description of how EDI processing is supported in BizTalk Server and other versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and for a description of EDI standards support and EDI document schema support, see [EDI Support Issues](../core/edi-support-issues.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3812-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b3812-108">In This Section</span></span>  
  
-   [<span data-ttu-id="b3812-109">Prise en charge EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3812-109">EDI Support in BizTalk Server</span></span>](../core/edi-support-in-biztalk-server1.md)  
  
-   [<span data-ttu-id="b3812-110">Prise en charge de la loi HIPAA dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3812-110">HIPAA Support in BizTalk Server</span></span>](../core/hipaa-support-in-biztalk-server.md)  
  
-   [<span data-ttu-id="b3812-111">Traitement EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3812-111">EDI Processing in BizTalk Server</span></span>](../core/edi-processing-in-biztalk-server.md)  
  
-   [<span data-ttu-id="b3812-112">Problèmes de prise en charge EDI</span><span class="sxs-lookup"><span data-stu-id="b3812-112">EDI Support Issues</span></span>](../core/edi-support-issues.md)  
  
## <a name="see-also"></a><span data-ttu-id="b3812-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3812-113">See Also</span></span>  
 <span data-ttu-id="b3812-114">[Fonctionnalités AS2 de BizTalk Server](../core/biztalk-server-as2-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="b3812-114">[BizTalk Server AS2 Functionality](../core/biztalk-server-as2-functionality.md) </span></span>  
 <span data-ttu-id="b3812-115">[Architecture de la Solution EDI](../core/edi-solution-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="b3812-115">[EDI Solution Architecture](../core/edi-solution-architecture.md) </span></span>  
 [<span data-ttu-id="b3812-116">Développement et configuration de solutions EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b3812-116">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)