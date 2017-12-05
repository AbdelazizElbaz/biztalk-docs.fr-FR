---
title: "Qu'est-ce que l'adaptateur MSMQ ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, about MSMQ adapters
- MSMQ adapters
ms.assetid: 4f4bfe49-19fc-4195-8826-0329f17cbe94
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: caeac28ce33e2f5eeacbb73b03d9873ec1e74c92
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="what-is-the-msmq-adapter"></a><span data-ttu-id="4d35f-103">Qu'est-ce que l'adaptateur MSMQ ?</span><span class="sxs-lookup"><span data-stu-id="4d35f-103">What Is the MSMQ Adapter?</span></span>
<span data-ttu-id="4d35f-104">L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour MSMQ (adaptateur MSMQ) permet d'échanger des messages avec les files d'attentes Microsoft Message Queuing (également appelé MSMQ) à l'aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4d35f-104">With the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Adapter for MSMQ (the MSMQ adapter), you can send and receive messages to Microsoft Message Queuing (also known as MSMQ) queues using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="4d35f-105">L'adaptateur MSMQ prend en charge Message Queuing 4.0.</span><span class="sxs-lookup"><span data-stu-id="4d35f-105">The MSMQ adapter supports Message Queuing 4.0.</span></span> <span data-ttu-id="4d35f-106">Il fonctionne avec les files d'attente transactionnelles et non transactionnelles, publiques et privées, locales et distantes.</span><span class="sxs-lookup"><span data-stu-id="4d35f-106">The adapter works with transactional and non-transactional, public and private, and local and remote queues.</span></span> <span data-ttu-id="4d35f-107">En outre, l'adaptateur MSMQ prend en charge les messages volumineux (dont la taille dépasse 4 Mo) et permet d'accéder aux fonctionnalités de Message Queuing 4.0, telles que les lectures transactionnelles distantes et la lecture à partir des sous-files d'attente.</span><span class="sxs-lookup"><span data-stu-id="4d35f-107">Additionally, the MSMQ adapter provides large (greater than 4 MB) message support and gives you access to Message Queuing 4.0 features such as remote transactional reads and reading from subqueues.</span></span>  
  
 <span data-ttu-id="4d35f-108">Si vous avez mis à niveau votre installation de BizTalk Server à BizTalk Server, l’adaptateur BizTalk Server 2009 pour MSMQ n’est pas supprimé.</span><span class="sxs-lookup"><span data-stu-id="4d35f-108">If you have upgraded your BizTalk Server installation to BizTalk Server, the BizTalk Server 2009 Adapter for MSMQ is not removed.</span></span> <span data-ttu-id="4d35f-109">Étant donné que BizTalk Server installe une nouvelle version de l’adaptateur MSMQ, vous pouvez désinstaller en toute sécurité de l’adaptateur BizTalk Server 2009 pour MSMQ et ensuite supprimer manuellement la structure de répertoires pour cette version de la carte.</span><span class="sxs-lookup"><span data-stu-id="4d35f-109">Because BizTalk Server installs a new version of the MSMQ adapter, you can safely uninstall the BizTalk Server 2009 Adapter for MSMQ and then manually remove the directory structure for this version of the adapter.</span></span>