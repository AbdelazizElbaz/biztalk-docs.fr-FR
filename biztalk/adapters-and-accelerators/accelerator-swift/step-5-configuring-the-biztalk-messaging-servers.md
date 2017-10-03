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
# <a name="step-5-configuring-the-biztalk-messaging-servers"></a>Étape 5 : Configuration des serveurs de messagerie BizTalk
Cette section fournit des instructions sur la configuration des serveurs de messagerie BizTalk.  
  
### <a name="to-configure-the-biztalk-messaging-servers"></a>Pour configurer les serveurs de messagerie BizTalk  
  
1.  Activer l’accès de réseau Distributed Transaction Coordinator (DTC) en le sélectionnant à partir de l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous la catégorie de serveur d’applications. L’accès DTC réseau client a été activée sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur dans une étape antérieure. Consultez les articles suivants de la Base de connaissances sur le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] site Web aide et Support pour plus d’informations sur la résolution des problèmes DTC :  
  
    -   Comment To Troubleshoot MS DTC Firewall Issues, situé dans [http://go.microsoft.com/fwlink/?linkid=48870](http://go.microsoft.com/fwlink/?linkid=48870).  
  
    -   Comment To Use DTCTester Tool, situé dans [http://go.microsoft.com/fwlink/?linkid=48871](http://go.microsoft.com/fwlink/?linkid=48871).  
  
    -   Si le DTC se trouve derrière un pare-feu, consultez « Configuration [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Distributed Transaction Coordinator (DTC) pour le travail à travers un pare-feu », situé dans [http://go.microsoft.com/fwlink/?linkid=48872](http://go.microsoft.com/fwlink/?linkid=48872).  
  
2.  Configurer et vérifier l’équilibrage de charge réseau sur BizTalk reçoivent des serveurs comme décrit dans [étape 2 : configuration d’équilibrage de charge réseau sur les serveurs](../../adapters-and-accelerators/accelerator-swift/step-2-configuring-nlb-on-the-servers.md).  
  
3.  Installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme décrit dans [installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md).  
  
 Contenu de cette section :  
  
-   [Installation et configuration de BizTalk Server sur le serveur de messagerie](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-messaging-server.md)  
  
-   [Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers.md)