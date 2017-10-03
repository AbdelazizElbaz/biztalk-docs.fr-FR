---
title: Installation et configuration de BizTalk Server sur les serveurs frontaux HTTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP server, installing BizTalk Server
- BizTalk Server, installing on HTTP servers
ms.assetid: dc1b3675-483a-478f-b30d-62efb73ad13c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 772c240ef95c294e5e884d94b361d4cd0b102b07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="installing-and-configuring-biztalk-server-on-the-http-front-end-servers"></a>Installation et configuration de BizTalk Server sur les serveurs frontaux HTTP
Cette section décrit comment installer et configurer [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] à utiliser en tant que le serveur frontal HTTP pour l’hébergement du site MRSR et le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaires de modèle.  
  
### <a name="to-install-and-configure-biztalk-server-on-the-biztalk-http-front-end-servers"></a>Pour installer et configurer BizTalk Server sur les serveurs frontaux HTTP BizTalk  
  
1.  Effectuer une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] en choisissant les fonctionnalités suivantes : **moteur des règles d’entreprise** et **adaptateur SharePoint**.  
  
    > [!NOTE]
    >  Autres fonctionnalités ne sont pas requises pour cette installation.  
  
    > [!NOTE]
    >  Sur l’un des serveurs frontaux HTTP BizTalk, lorsque vous effectuez la configuration, créez le groupe BizTalk.  
  
2.  Effectuer la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Installez les correctifs supplémentaires requis par [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme étant disponibles dans le guide d’installation.