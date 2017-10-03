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
# <a name="step-7-configuring-the-biztalk-http-front-end-servers"></a>Étape 7 : Configuration des serveurs frontaux HTTP BizTalk
Cette section fournit des instructions sur la configuration des serveurs Web de votre [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] déploiement.  
  
> [!NOTE]
>  Dans le déploiement sur un seul ordinateur, cet ordinateur est le même ordinateur que celui qui effectue la messagerie et le traitement.  
  
### <a name="to-configure-the-biztalk-http-front-end-servers"></a>Pour configurer les serveurs frontaux HTTP BizTalk  
  
1.  Installez Internet Information Services (IIS) et ASP.NET.  
  
2.  Ouvrez le Gestionnaire des services Internet, puis sélectionnez **Extensions du Service Web**. Assurez-vous que ASP.NET version 1.1 et ASP.NET 2.0 sont définis sur **autorisées**.  
  
3.  Vérifiez que le **Message Queuing** service (MSMQ) avec **prise en charge de routage** est installée à partir de l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous l’Application serveur/MSMQ.  
  
4.  Vérifiez que l’accès DTC réseau est activé dans l’ajout/suppression [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composants sous la catégorie de serveur d’applications. L’accès DTC réseau client a été activée sur le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] ordinateur dans une étape antérieure.  
  
5.  Implémenter le protocole Secure Sockets Layer (SSL) dans votre déploiement, comme décrit dans [prise en charge de couche SSL (Secure Sockets)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md).  
  
6.  Installez et configurez Windows SharePoint Services 3.0 SP1.  
  
7.  Installer et configurer [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] comme décrit dans [installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md).  
  
 Contenu de cette section :  
  
-   [Prise en charge de Secure Sockets Layer (SSL)](../../adapters-and-accelerators/accelerator-swift/supporting-secure-sockets-layer-ssl.md)  
  
-   [Installer et configurer les serveurs frontaux HTTP BizTalk](../../adapters-and-accelerators/accelerator-swift/installing-and-configuring-biztalk-server-on-the-http-front-end-servers.md)  
  
-   [Installation et configuration de BizTalk Accelerator pour SWIFT sur les serveurs frontaux HTTP](../../adapters-and-accelerators/accelerator-swift/install-and-configure-biztalk-accelerator-for-swift-on-http-front-end-servers.md)