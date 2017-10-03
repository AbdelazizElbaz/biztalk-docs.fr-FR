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
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-messaging-servers"></a>Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs de messagerie
Cette section décrit comment installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sur les serveurs de messagerie. Ces serveurs sont principalement utilisés pour communiquer avec le réseau SWIFT.  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-a4swift-on-the-messaging-server"></a>Pour installer et configurer BizTalk Accelerator pour A4SWIFT sur le serveur de messagerie  
  
1.  Effectuer une installation personnalisée de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. Installer le **MRSR** et **les Messages SWIFT** fonctionnalités.  
  
    > [!NOTE]
    >  Vous n’avez pas besoin d’installer les composants Web pour Message Repair et New Submission fonctionnalité car ce serveur n’a pas de site MRSR.  
  
    > [!NOTE]
    >  Une fois l’installation terminée, l’Assistant Configuration démarre.  
  
2.  Dans Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration de la console, configurez **MCRR**.