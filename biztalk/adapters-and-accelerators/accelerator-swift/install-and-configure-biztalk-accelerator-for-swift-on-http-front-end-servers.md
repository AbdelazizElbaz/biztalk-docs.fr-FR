---
title: Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP server, installing BizTalk Accelerator for SWIFT
- BizTalk Accelerator for SWIFT, installing on HTTP server
ms.assetid: 1deaa5f7-9da2-4d4b-8367-2d6900065839
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe0a320f9f60f72975faf903c1355b8730840b26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-http-front-end-servers"></a><span data-ttu-id="98ded-102">Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP</span><span class="sxs-lookup"><span data-stu-id="98ded-102">Installing and Configuring BizTalk Accelerator for SWIFT on HTTP Front-End Servers</span></span>
<span data-ttu-id="98ded-103">Cette section décrit comment installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sur les serveurs frontaux HTTP.</span><span class="sxs-lookup"><span data-stu-id="98ded-103">This section describes how to install and configure [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] on the HTTP front-end servers.</span></span> <span data-ttu-id="98ded-104">Ces serveurs sont principalement utilisés pour communiquer avec le réseau SWIFT.</span><span class="sxs-lookup"><span data-stu-id="98ded-104">These servers are mainly used to communicate with the SWIFT Network.</span></span>  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-http-front-end-server"></a><span data-ttu-id="98ded-105">Pour installer et configurer BizTalk Accelerator pour SWIFT sur le serveur frontal HTTP</span><span class="sxs-lookup"><span data-stu-id="98ded-105">To install and configure BizTalk Accelerator for SWIFT on the HTTP front-end server</span></span>  
  
1.  <span data-ttu-id="98ded-106">Effectuer une installation personnalisée de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span><span class="sxs-lookup"><span data-stu-id="98ded-106">Perform a Custom Install of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span> <span data-ttu-id="98ded-107">Installer le **MRSR** et **les composants Web pour Message Repair et New Submission** fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="98ded-107">Install the **MRSR** and **Web Components for Message Repair and New Submission** features.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="98ded-108">Une fois l’installation terminée, l’Assistant Configuration démarre.</span><span class="sxs-lookup"><span data-stu-id="98ded-108">After installation is complete, the Configuration Wizard starts.</span></span>  
  
2.  <span data-ttu-id="98ded-109">Dans Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration de la console, configurez **MCRR** et **WebService**.</span><span class="sxs-lookup"><span data-stu-id="98ded-109">In the Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration console, configure **MCRR** and **WebService**.</span></span>  
  
3.  <span data-ttu-id="98ded-110">Après avoir terminé l’Assistant de Configuration sur les serveurs Web, ouvrez le fichier web.config dans le dossier \< *lecteur*> : \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ dans le bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="98ded-110">After completing the Configuration Wizard, on the Web servers, open the web.config file in the folder \<*Drive*>:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ in Notepad.</span></span> <span data-ttu-id="98ded-111">Recherchez « Authorization ».</span><span class="sxs-lookup"><span data-stu-id="98ded-111">Search for "Authorization".</span></span> <span data-ttu-id="98ded-112">Dans le **autorisation** section, définissez la valeur de rôles sur le nom du groupe d’utilisateurs A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="98ded-112">In the **Authorization** section, set the roles value to the name of the A4SWIFT users group.</span></span>