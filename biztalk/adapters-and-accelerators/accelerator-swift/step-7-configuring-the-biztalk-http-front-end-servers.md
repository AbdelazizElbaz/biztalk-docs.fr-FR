---
title: "Étape 7 : Configuration des serveurs frontaux HTTP BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, HTTP servers
- HTTP server, configuring
ms.assetid: 6b7e0b48-bb20-42f4-84a5-092ff3a02741
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5840099816149265711744373e08d3a9a9d91cd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-configuring-the-biztalk-http-front-end-servers"></a><span data-ttu-id="2af39-102">Étape 7 : Configuration des serveurs frontaux HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="2af39-102">Step 7: Configuring the BizTalk HTTP Front-End Servers</span></span>
<span data-ttu-id="2af39-103">Cette section fournit des instructions sur la configuration des serveurs Web de votre [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] déploiement.</span><span class="sxs-lookup"><span data-stu-id="2af39-103">This section provides guidelines on configuring the Web servers in your [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2af39-104">Dans le déploiement sur un seul ordinateur, cet ordinateur est le même ordinateur que celui qui effectue la messagerie et le traitement.</span><span class="sxs-lookup"><span data-stu-id="2af39-104">In the single-computer deployment, this computer is the same computer as the one that does the messaging and processing.</span></span>  
  
### <a name="to-configure-the-biztalk-http-front-end-servers"></a><span data-ttu-id="2af39-105">Pour configurer les serveurs frontaux HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="2af39-105">To configure the BizTalk HTTP front-end servers</span></span>  
  
1.  <span data-ttu-id="2af39-106">Installez Internet Information Services (IIS) et ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2af39-106">Install Internet Information Services (IIS) and ASP.NET.</span></span>  
  
2.  <span data-ttu-id="2af39-107">Ouvrez le Gestionnaire des services Internet, puis sélectionnez **Extensions du Service Web**.</span><span class="sxs-lookup"><span data-stu-id="2af39-107">Open IIS Manager and select **Web Service Extensions**.</span></span> <span data-ttu-id="2af39-108">Assurez-vous que ASP.NET version 1.1 et ASP.NET 2.0 sont définis sur **autorisées**.</span><span class="sxs-lookup"><span data-stu-id="2af39-108">Ensure that ASP.NET v1.1 and ASP.NET v2.0 are set to **Allowed**.</span></span>  
  
3.  <span data-ttu-id="2af39-109">Vérifiez que le **Message Queuing** service (MSMQ) avec **prise en charge de routage** est installée à partir de l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous l’Application serveur/MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2af39-109">Ensure that the **Message Queuing** service (MSMQ) with **Routing Support** is installed from the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under Application Server/Message Queuing.</span></span>  
  
4.  <span data-ttu-id="2af39-110">Vérifiez que l’accès DTC réseau est activé dans l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous la catégorie de serveur d’applications.</span><span class="sxs-lookup"><span data-stu-id="2af39-110">Ensure that Network DTC access is enabled in the Add/Remove [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Components under the Application Server category.</span></span> <span data-ttu-id="2af39-111">L’accès DTC réseau client a été activée sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur dans une étape antérieure.</span><span class="sxs-lookup"><span data-stu-id="2af39-111">Network DTC client access was enabled on the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] computer in an earlier step.</span></span>  
  
5.  <span data-ttu-id="2af39-112">Implémenter le protocole Secure Sockets Layer (SSL) dans votre déploiement, comme décrit dans [prise en charge de couche SSL (Secure Sockets)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md).</span><span class="sxs-lookup"><span data-stu-id="2af39-112">Implement the Secure Sockets Layer (SSL) protocol in your deployment, as described in [Supporting Secure Sockets Layer (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md).</span></span>  
  
6.  <span data-ttu-id="2af39-113">Installez et configurez Windows SharePoint Services 3.0 SP1.</span><span class="sxs-lookup"><span data-stu-id="2af39-113">Install and configure Windows SharePoint Services 3.0 SP1.</span></span>  
  
7.  <span data-ttu-id="2af39-114">Installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme décrit dans [installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md).</span><span class="sxs-lookup"><span data-stu-id="2af39-114">Install and configure [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] as described in [Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md).</span></span>  
  
 <span data-ttu-id="2af39-115">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="2af39-115">This section contains:</span></span>  
  
-   [<span data-ttu-id="2af39-116">Prise en charge de Secure Sockets Layer (SSL)</span><span class="sxs-lookup"><span data-stu-id="2af39-116">Supporting Secure Sockets Layer (SSL)</span></span>](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)  
  
-   [<span data-ttu-id="2af39-117">Installer et configurer les serveurs frontaux HTTP BizTalk</span><span class="sxs-lookup"><span data-stu-id="2af39-117">Installing and Configuring BizTalk HTTP Front-End Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)  
  
-   [<span data-ttu-id="2af39-118">Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP</span><span class="sxs-lookup"><span data-stu-id="2af39-118">Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers</span></span>](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-http-front-end-servers.md)