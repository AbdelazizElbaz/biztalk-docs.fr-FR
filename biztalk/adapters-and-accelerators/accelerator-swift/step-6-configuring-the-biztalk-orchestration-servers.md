---
title: "Étape 6 : Configurer les serveurs d’Orchestration BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestration server, configuring
- configuring, orchestration servers
ms.assetid: 1eb38fac-264d-4730-b16b-572dbb6fabd9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e495be91cc80e072f58a1e8149feb64773f1e51
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-6-configuring-the-biztalk-orchestration-servers"></a><span data-ttu-id="d5ea6-102">Étape 6 : Configurer les serveurs d’Orchestration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="d5ea6-102">Step 6: Configuring the BizTalk Orchestration Servers</span></span>
<span data-ttu-id="d5ea6-103">Cette section fournit des instructions sur la configuration des serveurs d’Orchestration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d5ea6-103">This section provides guidelines on configuring the BizTalk Orchestration servers.</span></span>  
  
### <a name="to-configure-the-biztalk-orchestration-servers"></a><span data-ttu-id="d5ea6-104">Pour configurer les serveurs d’Orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="d5ea6-104">To configure the BizTalk Orchestration servers</span></span>  
  
1.  <span data-ttu-id="d5ea6-105">Activer l’accès de réseau Distributed Transaction Coordinator (DTC) en le sélectionnant à partir de l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous la catégorie de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="d5ea6-105">Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="d5ea6-106">L’accès DTC réseau client a été activée sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur dans une étape antérieure.</span><span class="sxs-lookup"><span data-stu-id="d5ea6-106">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span> <span data-ttu-id="d5ea6-107">Consultez les articles suivants de la Base de connaissances sur le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] site Web aide et Support pour plus d’informations sur la résolution des problèmes DTC :</span><span class="sxs-lookup"><span data-stu-id="d5ea6-107">See the following Knowledge Base articles on the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Help and Support Web site for information about troubleshooting DTC issues:</span></span>  
  
    -   <span data-ttu-id="d5ea6-108">Comment To Troubleshoot MS DTC Firewall Issues, situé dans [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span><span class="sxs-lookup"><span data-stu-id="d5ea6-108">How To Troubleshoot MS DTC Firewall Issues, located at [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span></span>  
  
    -   <span data-ttu-id="d5ea6-109">Comment To Use DTCTester Tool, situé dans [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span><span class="sxs-lookup"><span data-stu-id="d5ea6-109">How To Use DTCTester Tool, located at [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span></span>  
  
    -   <span data-ttu-id="d5ea6-110">Si le DTC se trouve derrière un pare-feu, consultez Configuration [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) au travail via un pare-feu, situé dans [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span><span class="sxs-lookup"><span data-stu-id="d5ea6-110">If DTC is behind a firewall, see Configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) to Work Through a Firewall, located at [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span></span>  
  
2.  <span data-ttu-id="d5ea6-111">Installer les composants logiciels supplémentaires requis pour BizTalk Server et installer et configurer BizTalk Server, comme décrit dans [installation et configuration de BizTalk Server sur les serveurs d’Orchestration](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md).</span><span class="sxs-lookup"><span data-stu-id="d5ea6-111">Install additional software prerequisites for BizTalk Server, and install and configure BizTalk Server, as described in [Installing and Configuring BizTalk Server on the Orchestration Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md).</span></span>  
  
3.  <span data-ttu-id="d5ea6-112">Installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme décrit dans l’installation et [installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span><span class="sxs-lookup"><span data-stu-id="d5ea6-112">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in Installing and [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span></span>  
  
 <span data-ttu-id="d5ea6-113">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="d5ea6-113">This section contains:</span></span>  
  
-   [<span data-ttu-id="d5ea6-114">Installation et configuration de BizTalk Server sur les serveurs d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d5ea6-114">Installing and Configuring BizTalk Server on the Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)  
  
-   [<span data-ttu-id="d5ea6-115">Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs d’orchestration</span><span class="sxs-lookup"><span data-stu-id="d5ea6-115">Installing and Configuring BizTalk Accelerator for SWIFT on Orchestration Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-orchestration-servers.md)