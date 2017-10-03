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
# <a name="installing-and-configuring-biztalk-accelerator-for-swift-on-orchestration-servers"></a>Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs d’Orchestration
Cette section décrit comment installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] sur les serveurs d’orchestration. Ces serveurs sont principalement utilisés pour exécuter l’orchestration FIN réparation et réconciliation et l’orchestration de soumission de réparation/nouveau Message.  
  
### <a name="to-install-and-configure-biztalk-accelerator-for-swift-on-the-orchestration-server"></a>Pour installer et configurer BizTalk Accelerator pour SWIFT sur le serveur d’orchestration  
  
1.  Effectuer une installation personnalisée de [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]. Installer le **MRSR** fonctionnalité.  
  
    > [!NOTE]
    >  Vous n’avez pas besoin d’installer les composants Web pour Message Repair et New Submission fonctionnalité car ce serveur n’a pas de site MRSR.  
  
    > [!NOTE]
    >  Une fois l’installation terminée, l’Assistant Configuration démarre.  
  
2.  Dans Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] Configuration de la console, configurez **MCRR**.