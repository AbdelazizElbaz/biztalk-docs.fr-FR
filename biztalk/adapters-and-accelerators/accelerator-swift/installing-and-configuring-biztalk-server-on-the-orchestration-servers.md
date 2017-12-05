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
ms.openlocfilehash: 18a13d553e31739c959ff6baf317240c3c268ecc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-orchestration-servers"></a><span data-ttu-id="f9d18-102">Installation et configuration de BizTalk Server sur les serveurs d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="f9d18-102">Installing and Configuring BizTalk Server on the Orchestration Servers</span></span>
<span data-ttu-id="f9d18-103">Cette section décrit comment installer et configurer BizTalk Server à utiliser en tant que le serveur d’orchestration pour exécutant l’orchestration de soumission de réparation/nouveau Message et la réparation de FIN et l’orchestration de rapprochement.</span><span class="sxs-lookup"><span data-stu-id="f9d18-103">This section describes how to install and configure BizTalk Server to be used as the orchestration server for running the Message Repair/New Submission orchestration and the FIN Repair and Reconciliation orchestration.</span></span>  
  
### <a name="to-install-and-configure-biztalk-server-on-the-orchestration-server"></a><span data-ttu-id="f9d18-104">Pour installer et configurer BizTalk Server sur le serveur d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="f9d18-104">To install and configure BizTalk Server on the Orchestration Server</span></span>  
  
1.  <span data-ttu-id="f9d18-105">Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant de toutes les fonctionnalités à l’exception de MRSR, EDI et Human Workflow Services (HWS), sauf si requis par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="f9d18-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR, unless required by other applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d18-106">Dans le déploiement sur un seul ordinateur, cet ordinateur est le même ordinateur que celui qui exécute le service frontal HTTP et le serveur de messagerie BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f9d18-106">In the single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service and the BizTalk Messaging server.</span></span>  
  
2.  <span data-ttu-id="f9d18-107">Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9d18-107">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d18-108">Respectez les consignes suivantes lors de la configuration des serveurs d’Orchestration de BizTalk :</span><span class="sxs-lookup"><span data-stu-id="f9d18-108">Consider the following guidelines when configuring the BizTalk Orchestration servers:</span></span>  
  
    -   <span data-ttu-id="f9d18-109">Ce serveur ne nécessite qu’une seule carte réseau pour se connecter à la [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f9d18-109">This server requires only one network adapter to connect it to the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer.</span></span> <span data-ttu-id="f9d18-110">Il ne nécessite pas une autre carte réseau sur le côté public, comme le serveur frontal HTTP ou le serveur de messagerie, et cela le rend plus sécurisé contre le piratage de tentatives provenant d’Internet ou intranet/extranet.</span><span class="sxs-lookup"><span data-stu-id="f9d18-110">It does not require another network adapter on the public side like the HTTP front-end server or the messaging server, and this makes it more secure against hacking attempts coming from the Internet or intranet/extranet.</span></span>  
  
3.  <span data-ttu-id="f9d18-111">Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation.</span><span class="sxs-lookup"><span data-stu-id="f9d18-111">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span>