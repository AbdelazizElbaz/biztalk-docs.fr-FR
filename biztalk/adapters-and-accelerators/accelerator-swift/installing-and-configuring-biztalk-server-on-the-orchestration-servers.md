---
title: "Installation et configuration de BizTalk Server sur les serveurs d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on orchestration server
- orchestration server, installing BizTalk Server
ms.assetid: 72376a80-1377-4058-9478-fee668b804d0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18a13d553e31739c959ff6baf317240c3c268ecc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-orchestration-servers"></a>Installation et configuration de BizTalk Server sur les serveurs d’Orchestration
Cette section décrit comment installer et configurer BizTalk Server à utiliser en tant que le serveur d’orchestration pour exécutant l’orchestration de soumission de réparation/nouveau Message et la réparation de FIN et l’orchestration de rapprochement.  
  
### <a name="to-install-and-configure-biztalk-server-on-the-orchestration-server"></a>Pour installer et configurer BizTalk Server sur le serveur d’Orchestration  
  
1.  Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant de toutes les fonctionnalités à l’exception de MRSR, EDI et Human Workflow Services (HWS), sauf si requis par d’autres applications.  
  
    > [!NOTE]
    >  Dans le déploiement sur un seul ordinateur, cet ordinateur est le même ordinateur que celui qui exécute le service frontal HTTP et le serveur de messagerie BizTalk.  
  
2.  Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
    > [!NOTE]
    >  Respectez les consignes suivantes lors de la configuration des serveurs d’Orchestration de BizTalk :  
  
    -   Ce serveur ne nécessite qu’une seule carte réseau pour se connecter à la [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur. Il ne nécessite pas une autre carte réseau sur le côté public, comme le serveur frontal HTTP ou le serveur de messagerie, et cela le rend plus sécurisé contre le piratage de tentatives provenant d’Internet ou intranet/extranet.  
  
3.  Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation.