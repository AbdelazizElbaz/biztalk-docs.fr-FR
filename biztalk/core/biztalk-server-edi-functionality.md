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
ms.openlocfilehash: c259b3f46105afc0cf164ec0781c2c0d8f1f226b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-edi-functionality"></a><span data-ttu-id="33815-102">Fonctionnalités EDI de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="33815-102">BizTalk Server EDI Functionality</span></span>
[!INCLUDE[prague](../includes/prague-md.md)]<span data-ttu-id="33815-103"> traite les messages EDI à l'aide d'une combinaison de fonctionnalités [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] principales et de fonctionnalités [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] spécifiques à EDI.</span><span class="sxs-lookup"><span data-stu-id="33815-103"> processes EDI messages using a combination of core [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features and EDI-specific [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features.</span></span> <span data-ttu-id="33815-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut alors effectuer le traitement spécifique à la messagerie EDI tout en exploitant sa fonctionnalité principale de messagerie.</span><span class="sxs-lookup"><span data-stu-id="33815-104">This enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to perform the processing that is unique to EDI messaging, while leveraging its core messaging functionality.</span></span>  
  
 <span data-ttu-id="33815-105">Cette section présente le fonctionnement de la messagerie EDI de base et la manière dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les implémente.</span><span class="sxs-lookup"><span data-stu-id="33815-105">This section describes how basic EDI messaging works and how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] implements it.</span></span> <span data-ttu-id="33815-106">Elle illustre également la manière dont une définition d'accord de partenariat commercial dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut être exploitée dans la messagerie EDI ainsi que dans le traitement EDI , côté réception et côté envoi.</span><span class="sxs-lookup"><span data-stu-id="33815-106">It also describes how a trading partner agreement definition in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be leveraged for EDI messaging, receive-side EDI processing, and send-side EDI processing.</span></span>  
  
 <span data-ttu-id="33815-107">Pour obtenir une description de la prise en charge le traitement EDI dans [!INCLUDE[prague](../includes/prague-md.md)] et d’autres versions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]et pour obtenir une description de la prise en charge des normes EDI et la prise en charge des schémas de document EDI, consultez [problèmes de prise en charge EDI](../core/edi-support-issues.md).</span><span class="sxs-lookup"><span data-stu-id="33815-107">For a description of how EDI processing is supported in [!INCLUDE[prague](../includes/prague-md.md)] and other versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and for a description of EDI standards support and EDI document schema support, see [EDI Support Issues](../core/edi-support-issues.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="33815-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="33815-108">In This Section</span></span>  
  
-   [<span data-ttu-id="33815-109">Prise en charge EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="33815-109">EDI Support in BizTalk Server</span></span>](../core/edi-support-in-biztalk-server1.md)  
  
-   [<span data-ttu-id="33815-110">Prise en charge HIPAA dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="33815-110">HIPAA Support in BizTalk Server</span></span>](../core/hipaa-support-in-biztalk-server.md)  
  
-   [<span data-ttu-id="33815-111">Le traitement EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="33815-111">EDI Processing in BizTalk Server</span></span>](../core/edi-processing-in-biztalk-server.md)  
  
-   [<span data-ttu-id="33815-112">Problèmes de prise en charge EDI</span><span class="sxs-lookup"><span data-stu-id="33815-112">EDI Support Issues</span></span>](../core/edi-support-issues.md)  
  
## <a name="see-also"></a><span data-ttu-id="33815-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33815-113">See Also</span></span>  
 <span data-ttu-id="33815-114">[Fonctionnalités AS2 de BizTalk Server](../core/biztalk-server-as2-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="33815-114">[BizTalk Server AS2 Functionality](../core/biztalk-server-as2-functionality.md) </span></span>  
 <span data-ttu-id="33815-115">[Architecture de la Solution EDI](../core/edi-solution-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="33815-115">[EDI Solution Architecture](../core/edi-solution-architecture.md) </span></span>  
 [<span data-ttu-id="33815-116">Développement et la configuration des Solutions EDI BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="33815-116">Developing and Configuring BizTalk Server EDI Solutions</span></span>](../core/developing-and-configuring-biztalk-server-edi-solutions.md)