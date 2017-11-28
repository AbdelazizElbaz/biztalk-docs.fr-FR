---
title: Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for SWIFT, configuring
- BizTalk Accelerator for SWIFT, installing on Messaging servers
- BizTalk Messaging servers, installing BizTalk Accelerator for SWIFT
ms.assetid: 7a8f60aa-5ff2-4584-9d4a-dc4a0ba61aca
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef434603c1740375f4399f368e89f99a923cba86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers"></a><span data-ttu-id="fe5c1-102">Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie</span><span class="sxs-lookup"><span data-stu-id="fe5c1-102">Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers</span></span>
<span data-ttu-id="fe5c1-103">Cette section décrit comment installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sur les serveurs de messagerie.</span><span class="sxs-lookup"><span data-stu-id="fe5c1-103">This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the messaging servers.</span></span> <span data-ttu-id="fe5c1-104">Ces serveurs sont principalement utilisés pour communiquer avec le réseau SWIFT.</span><span class="sxs-lookup"><span data-stu-id="fe5c1-104">These servers are mainly used to communicate with the SWIFT Network.</span></span>  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-a4swift-on-the-messaging-server"></a><span data-ttu-id="fe5c1-105">Pour installer et configurer BizTalk Accelerator pour A4SWIFT sur le serveur de messagerie</span><span class="sxs-lookup"><span data-stu-id="fe5c1-105">To install and configure BizTalk Accelerator for A4SWIFT on the Messaging Server</span></span>  
  
1.  <span data-ttu-id="fe5c1-106">Effectuer une installation personnalisée de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fe5c1-106">Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="fe5c1-107">Installer le **MRSR** et **les Messages SWIFT** fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="fe5c1-107">Install the **MRSR** and **SWIFT Messages** features.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fe5c1-108">Vous n’avez pas besoin d’installer les composants Web pour Message Repair et New Submission fonctionnalité car ce serveur n’a pas de site MRSR.</span><span class="sxs-lookup"><span data-stu-id="fe5c1-108">You do not need to install the Web Components for Message Repair and New Submission feature because this server does not have MRSR site.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fe5c1-109">Une fois l’installation terminée, l’Assistant Configuration démarre.</span><span class="sxs-lookup"><span data-stu-id="fe5c1-109">After installation is complete, the Configuration Wizard starts.</span></span>  
  
2.  <span data-ttu-id="fe5c1-110">Dans Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration de la console, configurez **MCRR**.</span><span class="sxs-lookup"><span data-stu-id="fe5c1-110">In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR**.</span></span>