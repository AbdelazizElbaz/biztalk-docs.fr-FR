---
title: Installation et configuration de BizTalk Server sur le serveur de messagerie | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Server, installing on BizTalk Messaging servers
- BizTalk Server, configuring
- BizTalk Messaging servers, configuring BizTalk Server
- BizTalk Messaging servers, installing BizTalk Server
ms.assetid: 8aaa1b97-90f0-4317-9403-ac8b5b9f80e3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 527b0d707d0f78672018f31e60ea54ac436e1db4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-messaging-server"></a>Installation et configuration de BizTalk Server sur le serveur de messagerie
Cette section décrit comment installer et configurer BizTalk Server à utiliser en tant que le serveur de messagerie pour la connexion au réseau rapide.  
  
### <a name="to-install-and-configure-biztalk-server-on-the-messaging-server"></a>Pour installer et configurer BizTalk Server sur le serveur de messagerie  
  
1.  Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant de toutes les fonctionnalités à l’exception EDI, Human Workflow Services (HWS) et MRSR site, sauf si requis par d’autres applications.  
  
    > [!NOTE]
    >  Notez que, dans le déploiement d’un ordinateur unique, cet ordinateur est le même ordinateur que celui qui exécute le service frontal HTTP.  
  
2.  Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
    > [!NOTE]
    >  Ne pas installer Message Queuing, car nous installeront la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] version de MSMQ appelé MSMQT. Pour plus d’informations sur MSMQT, consultez Configuration de BizTalk adaptateur MSMQT (Message Queuing) sur le site Web MSDN à l’adresse [http://go.microsoft.com/fwlink/?LinkID=48875](http://go.microsoft.com/fwlink/?LinkID=48875).  
  
3.  Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation. Au moment de cette publication, il n’existe aucun correctif requis.