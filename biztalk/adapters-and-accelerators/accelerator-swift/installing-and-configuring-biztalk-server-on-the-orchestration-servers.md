---
title: "Installation et configuration de BizTalk Server sur les serveurs d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on orchestration server
- orchestration server, installing BizTalk Server
ms.assetid: 72376a80-1377-4058-9478-fee668b804d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d872d58c72110d7af22c6d64e7d212fbee53fae9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-orchestration-servers"></a><span data-ttu-id="8ce0d-102">Installation et configuration de BizTalk Server sur les serveurs d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="8ce0d-102">Installing and Configuring BizTalk Server on the Orchestration Servers</span></span>
<span data-ttu-id="8ce0d-103">Cette section décrit comment installer et configurer [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] à utiliser en tant que le serveur d’orchestration pour l’exécution de l’orchestration de soumission de réparation/nouveau Message et l’orchestration FIN réparation et rapprochement.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-103">This section describes how to install and configure [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] to be used as the orchestration server for running the Message Repair/New Submission orchestration and the FIN Repair and Reconciliation orchestration.</span></span>  
  
### <a name="to-install-and-configure-biztalk-server-on-the-orchestration-server"></a><span data-ttu-id="8ce0d-104">Pour installer et configurer BizTalk Server sur le serveur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="8ce0d-104">To install and configure BizTalk Server on the Orchestration Server</span></span>  
  
1.  <span data-ttu-id="8ce0d-105">Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant de toutes les fonctionnalités à l’exception de MRSR, EDI et Human Workflow Services (HWS), sauf si requis par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR, unless required by other applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ce0d-106">Dans le déploiement sur un seul ordinateur, cet ordinateur est le même ordinateur que celui qui exécute le service frontal HTTP et le serveur de messagerie BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-106">In the single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service and the BizTalk Messaging server.</span></span>  
  
2.  <span data-ttu-id="8ce0d-107">Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8ce0d-107">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ce0d-108">Respectez les consignes suivantes lors de la configuration des serveurs d’Orchestration de BizTalk :</span><span class="sxs-lookup"><span data-stu-id="8ce0d-108">Consider the following guidelines when configuring the BizTalk Orchestration servers:</span></span>  
  
    -   <span data-ttu-id="8ce0d-109">Ce serveur ne nécessite qu’une seule carte réseau pour se connecter à la [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-109">This server requires only one network adapter to connect it to the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer.</span></span> <span data-ttu-id="8ce0d-110">Il ne nécessite pas une autre carte réseau sur le côté public, comme le serveur frontal HTTP ou le serveur de messagerie, et cela le rend plus sécurisé contre le piratage de tentatives provenant d’Internet ou intranet/extranet.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-110">It does not require another network adapter on the public side like the HTTP front-end server or the messaging server, and this makes it more secure against hacking attempts coming from the Internet or intranet/extranet.</span></span>  
  
3.  <span data-ttu-id="8ce0d-111">Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation.</span><span class="sxs-lookup"><span data-stu-id="8ce0d-111">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span>