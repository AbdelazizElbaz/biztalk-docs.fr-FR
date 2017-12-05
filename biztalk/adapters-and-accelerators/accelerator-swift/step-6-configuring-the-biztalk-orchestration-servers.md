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
# <a name="step-6-configuring-the-biztalk-orchestration-servers"></a>Étape 6 : Configurer les serveurs d’Orchestration de BizTalk Server
Cette section fournit des instructions sur la configuration des serveurs d’Orchestration de BizTalk.  
  
### <a name="to-configure-the-biztalk-orchestration-servers"></a>Pour configurer les serveurs d’Orchestration BizTalk  
  
1.  Activer l’accès de réseau Distributed Transaction Coordinator (DTC) en le sélectionnant à partir de l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous la catégorie de serveur d’applications. L’accès DTC réseau client a été activée sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur dans une étape antérieure. Consultez les articles suivants de la Base de connaissances sur le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] site Web aide et Support pour plus d’informations sur la résolution des problèmes DTC :  
  
    -   Comment To Troubleshoot MS DTC Firewall Issues, situé dans [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).  
  
    -   Comment To Use DTCTester Tool, situé dans [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).  
  
    -   Si le DTC se trouve derrière un pare-feu, consultez Configuration [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) au travail via un pare-feu, situé dans [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).  
  
2.  Installer les composants logiciels supplémentaires requis pour BizTalk Server et installer et configurer BizTalk Server, comme décrit dans [installation et configuration de BizTalk Server sur les serveurs d’Orchestration](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md).  
  
3.  Installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme décrit dans l’installation et [installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).  
  
 Contenu de cette section :  
  
-   [Installation et configuration de BizTalk Server sur les serveurs d’orchestration](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-orchestration-servers.md)  
  
-   [Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs d’orchestration](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-orchestration-servers.md)