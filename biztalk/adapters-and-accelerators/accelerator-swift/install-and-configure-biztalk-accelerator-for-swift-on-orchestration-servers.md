---
title: "Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration server, installing BizTalk Accelerator for SWIFT
- BizTalk Accelerator for SWIFT, installing on orchestration server
ms.assetid: 127113ae-46b4-4290-a2c1-6a3db04cd178
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 384548de9fb0b7a5ee4ce440869c42fdfa1e93ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-orchestration-servers"></a><span data-ttu-id="3b5a3-102">Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="3b5a3-102">Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers</span></span>
<span data-ttu-id="3b5a3-103">Cette section décrit comment installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sur les serveurs d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="3b5a3-103">This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the orchestration servers.</span></span> <span data-ttu-id="3b5a3-104">Ces serveurs sont principalement utilisés pour exécuter l’orchestration FIN réparation et réconciliation et l’orchestration de soumission de réparation/nouveau Message.</span><span class="sxs-lookup"><span data-stu-id="3b5a3-104">These servers are mainly used to run the FIN Repair and Reconciliation orchestration and the Message Repair/New Submission orchestration.</span></span>  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-orchestration-server"></a><span data-ttu-id="3b5a3-105">Pour installer et configurer BizTalk Accelerator pour SWIFT sur le serveur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="3b5a3-105">To install and configure BizTalk Accelerator for SWIFT on the orchestration server</span></span>  
  
1.  <span data-ttu-id="3b5a3-106">Effectuer une installation personnalisée de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b5a3-106">Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="3b5a3-107">Installer le **MRSR** fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="3b5a3-107">Install the **MRSR** feature.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3b5a3-108">Vous n’avez pas besoin d’installer les composants Web pour Message Repair et New Submission fonctionnalité car ce serveur n’a pas de site MRSR.</span><span class="sxs-lookup"><span data-stu-id="3b5a3-108">You do not need to install the Web Components for Message Repair and New Submission feature because this server does not have MRSR site.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3b5a3-109">Une fois l’installation terminée, l’Assistant Configuration démarre.</span><span class="sxs-lookup"><span data-stu-id="3b5a3-109">After installation is complete, the Configuration Wizard starts.</span></span>  
  
2.  <span data-ttu-id="3b5a3-110">Dans Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration de la console, configurez **MCRR**.</span><span class="sxs-lookup"><span data-stu-id="3b5a3-110">In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR**.</span></span>