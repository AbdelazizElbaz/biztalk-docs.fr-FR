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
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-http-front-end-servers"></a>Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP
Cette section décrit comment installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sur les serveurs frontaux HTTP. Ces serveurs sont principalement utilisés pour communiquer avec le réseau SWIFT.  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-http-front-end-server"></a>Pour installer et configurer BizTalk Accelerator pour SWIFT sur le serveur frontal HTTP  
  
1.  Effectuer une installation personnalisée de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. Installer le **MRSR** et **les composants Web pour Message Repair et New Submission** fonctionnalités.  
  
    > [!NOTE]
    >  Une fois l’installation terminée, l’Assistant Configuration démarre.  
  
2.  Dans Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration de la console, configurez **MCRR** et **WebService**.  
  
3.  Après avoir terminé l’Assistant de Configuration sur les serveurs Web, ouvrez le fichier web.config dans le dossier \< *lecteur*> : \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\Service\ dans le bloc-notes. Recherchez « Authorization ». Dans le **autorisation** section, définissez la valeur de rôles sur le nom du groupe d’utilisateurs A4SWIFT.