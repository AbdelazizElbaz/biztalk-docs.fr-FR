---
title: "Étape 5 : Configuration des serveurs de messagerie BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, BizTalk Messaging servers
- BizTalk Messaging servers, configuring
ms.assetid: 598d336d-b006-4d02-9249-e9d6d9b6b7b5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e1aea1187417b77071f0821547869a5b84549c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-configuring-the-biztalk-messaging-servers"></a><span data-ttu-id="0018d-102">Étape 5 : Configuration des serveurs de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="0018d-102">Step 5: Configuring the BizTalk Messaging Servers</span></span>
<span data-ttu-id="0018d-103">Cette section fournit des instructions sur la configuration des serveurs de messagerie BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0018d-103">This section provides guidelines on configuring the BizTalk Messaging servers.</span></span>  
  
### <a name="to-configure-the-biztalk-messaging-servers"></a><span data-ttu-id="0018d-104">Pour configurer les serveurs de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="0018d-104">To configure the BizTalk Messaging servers</span></span>  
  
1.  <span data-ttu-id="0018d-105">Activer l’accès de réseau Distributed Transaction Coordinator (DTC) en le sélectionnant à partir de l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous la catégorie de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="0018d-105">Enable Network Distributed Transaction Coordinator (DTC) access by selecting it from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="0018d-106">L’accès DTC réseau client a été activée sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur dans une étape antérieure.</span><span class="sxs-lookup"><span data-stu-id="0018d-106">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span> <span data-ttu-id="0018d-107">Consultez les articles suivants de la Base de connaissances sur le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] site Web aide et Support pour plus d’informations sur la résolution des problèmes DTC :</span><span class="sxs-lookup"><span data-stu-id="0018d-107">See the following Knowledge Base articles on the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Help and Support Web site for information about troubleshooting DTC issues:</span></span>  
  
    -   <span data-ttu-id="0018d-108">Comment To Troubleshoot MS DTC Firewall Issues, situé dans [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span><span class="sxs-lookup"><span data-stu-id="0018d-108">How To Troubleshoot MS DTC Firewall Issues, located at [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).</span></span>  
  
    -   <span data-ttu-id="0018d-109">Comment To Use DTCTester Tool, situé dans [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span><span class="sxs-lookup"><span data-stu-id="0018d-109">How To Use DTCTester Tool, located at [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).</span></span>  
  
    -   <span data-ttu-id="0018d-110">Si le DTC se trouve derrière un pare-feu, consultez « Configuration [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) pour le travail à travers un pare-feu », situé dans [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span><span class="sxs-lookup"><span data-stu-id="0018d-110">If DTC is behind a firewall, see "Configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) to Work Through a Firewall", located at [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).</span></span>  
  
2.  <span data-ttu-id="0018d-111">Configurer et vérifier l’équilibrage de charge réseau sur BizTalk reçoivent des serveurs comme décrit dans [étape 2 : configuration d’équilibrage de charge réseau sur les serveurs](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md).</span><span class="sxs-lookup"><span data-stu-id="0018d-111">Configure and verify Network Load Balancing on the BizTalk receive servers as described in [Step 2: Configuring NLB on the Servers](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md).</span></span>  
  
3.  <span data-ttu-id="0018d-112">Installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme décrit dans [installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span><span class="sxs-lookup"><span data-stu-id="0018d-112">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in [Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).</span></span>  
  
 <span data-ttu-id="0018d-113">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="0018d-113">This section contains:</span></span>  
  
-   [<span data-ttu-id="0018d-114">Installation et configuration de BizTalk Server sur le serveur de messagerie</span><span class="sxs-lookup"><span data-stu-id="0018d-114">Installing and Configuring BizTalk Server on the Messaging Server</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)  
  
-   [<span data-ttu-id="0018d-115">Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie</span><span class="sxs-lookup"><span data-stu-id="0018d-115">Installing and Configuring BizTalk Accelerator for SWIFT on Messaging Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)