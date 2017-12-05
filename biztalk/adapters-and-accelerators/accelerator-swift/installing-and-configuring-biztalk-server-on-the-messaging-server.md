---
title: Installation et configuration de BizTalk Server sur le serveur de messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on BizTalk Messaging servers
- BizTalk Server, configuring
- BizTalk Messaging servers, configuring BizTalk Server
- BizTalk Messaging servers, installing BizTalk Server
ms.assetid: 8aaa1b97-90f0-4317-9403-ac8b5b9f80e3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 527b0d707d0f78672018f31e60ea54ac436e1db4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-messaging-server"></a><span data-ttu-id="c9763-102">Installation et configuration de BizTalk Server sur le serveur de messagerie</span><span class="sxs-lookup"><span data-stu-id="c9763-102">Installing and Configuring BizTalk Server on the Messaging Server</span></span>
<span data-ttu-id="c9763-103">Cette section décrit comment installer et configurer BizTalk Server à utiliser en tant que le serveur de messagerie pour la connexion au réseau rapide.</span><span class="sxs-lookup"><span data-stu-id="c9763-103">This section describes how to install and configure BizTalk Server to be used as the messaging server for connecting to the SWIFT network.</span></span>  
  
### <a name="to-install-and-configure-biztalk-server-on-the-messaging-server"></a><span data-ttu-id="c9763-104">Pour installer et configurer BizTalk Server sur le serveur de messagerie</span><span class="sxs-lookup"><span data-stu-id="c9763-104">To install and configure BizTalk Server on the Messaging Server</span></span>  
  
1.  <span data-ttu-id="c9763-105">Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant de toutes les fonctionnalités à l’exception EDI, Human Workflow Services (HWS) et MRSR site, sauf si requis par d’autres applications.</span><span class="sxs-lookup"><span data-stu-id="c9763-105">Perform a custom installation of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] choosing all the features except EDI, Human Workflow Services (HWS), and MRSR site, unless required by other applications.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9763-106">Notez que, dans le déploiement d’un ordinateur unique, cet ordinateur est le même ordinateur que celui qui exécute le service frontal HTTP.</span><span class="sxs-lookup"><span data-stu-id="c9763-106">Note that in single-computer deployment, this computer is the same computer as the one that runs the HTTP front-end service.</span></span>  
  
2.  <span data-ttu-id="c9763-107">Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9763-107">Perform configuration of [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c9763-108">Ne pas installer Message Queuing, car nous installeront la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] version de MSMQ appelé MSMQT.</span><span class="sxs-lookup"><span data-stu-id="c9763-108">Do not install Message Queuing, because we will be installing the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] version of MSMQ known as MSMQT.</span></span> <span data-ttu-id="c9763-109">Pour plus d’informations sur MSMQT, consultez Configuration de BizTalk adaptateur MSMQT (Message Queuing) sur le site Web MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkID=48875](http://go.microsoft.com/fwlink/?LinkID=48875).</span><span class="sxs-lookup"><span data-stu-id="c9763-109">For more information about MSMQT, see BizTalk Message Queuing Adapter (MSMQT) Configuration on the MSDN Web site at [http://go.microsoft.com/fwlink/?LinkID=48875](http://go.microsoft.com/fwlink/?LinkID=48875).</span></span>  
  
3.  <span data-ttu-id="c9763-110">Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation.</span><span class="sxs-lookup"><span data-stu-id="c9763-110">Install any additional hotfixes required by [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as available in the installation guide.</span></span> <span data-ttu-id="c9763-111">Au moment de cette publication, il n’existe aucun correctif requis.</span><span class="sxs-lookup"><span data-stu-id="c9763-111">At the time of this publication, there are no required hotfixes.</span></span>