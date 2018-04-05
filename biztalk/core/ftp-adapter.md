---
title: L’adaptateur FTP | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FTP adapters
ms.assetid: 878dc0b0-d1d8-405a-a697-654dd18ba08e
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ffc72b5166f8971392b41f275338bde593d325af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ftp-adapter"></a>adaptateur FTP
L'adaptateur FTP échange des données entre un serveur FTP et Microsoft BizTalk Server, et permet l'intégration de données vitales stockées sur diverses plateformes avec des applications sectorielles. L'adaptateur peut se connecter au serveur FTP via le serveur proxy SOCKS4 ou SOCKS5.  
  
 L'adaptateur FTP peut transférer un grand nombre de fichiers depuis un serveur FTP vers BizTalk Server. Il peut également transférer des fichiers dans le cadre d'une orchestration.  
  
 L’adaptateur FTP est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d’envoi.  

Cette section décrit les adaptateurs d'envoi et de réception FTP, et donne des informations relatives à la sécurité et aux meilleures pratiques.  
  
 ## <a name="receive-adapter"></a>Adaptateur de réception  
  
 L'adaptateur de réception FTP permet de déplacer des données d'un serveur FTP vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Fonctionnalités clés sont les suivantes :  
  
-   extraction de fichiers du serveur FTP à la demande ;  
  
-   Exécution d’interrogations basées sur une planification configurable  
  
-   interrogation du serveur FTP et envoi de données directement à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ;  
  
-   spécification du serveur FTP sous la forme d'une adresse IP, d'un port, d'un mot de passe et d'un nom d'hôte ;  
  
-   remise de fichier garantie.  
  
     L'adaptateur de réception FTP fonctionne également avec la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'Explorateur BizTalk aux fins de configuration et d'administration des fonctions de réception, lesquelles sont constituées des éléments de configuration suivants :  
  
-   intervalle d'interrogation pour l'exécution d'une commande FTP (par exemple, 60 minutes) ;  
  
-   informations de routage du document vers un port d'envoi BizTalk spécifique ou un emplacement de réception.  
  
> [!NOTE]
>  L'adaptateur de réception FTP ne prend pas en charge la réception de fichiers à partir d'un jeu de données partitionné.  
  
## <a name="send-adapter"></a>L’adaptateur d’envoi  
  
 L'adaptateur d'envoi FTP permet de déplacer des données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vers un serveur FTP. Fonctionnalités clés sont les suivantes :  
  
-   possibilité d'exécuter des envois à la demande ;  
  
-   remise garantie.  
  
## <a name="supported-platforms"></a>Plateformes prises en charge  
Accéder aux informations stockées dans un serveur FTP sur une des plateformes suivantes :  

- [!INCLUDE[btsWinSvrNoVersion_md](../includes/btswinsvrnoversion-md.md)] 2016

- [!INCLUDE[btsWinSrv2k12_md](../includes/btswinsrv2k12-md.md)] R2
  
-   [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]  
  
-   [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 2008  
  
-   [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)]  
  
-   [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 2000 Service Pack 3 (SP3) et versions ultérieures  
  
-   Sun Solaris 9.0  
  
-   HP-UX  
  
-   LINUX (Redhat 7.x)  
  
-   IBM z/OS v1.9 (MVS)  
  
-   IBM O/S 390 exécutant MVS  
  
-   AS/400 OS/400 V5R1  
  
-   i5/OS V5R4 (AS400)  
  
-   i5/OS V6R1 (AS400)  
  
-   GXS ICS  
  
-   AIX  
  
 Tous les Service Packs sont pris en charge, à l'exception de ceux répertoriés.  
  
## <a name="in-this-section"></a>Dans cette section  
  
[Meilleures pratiques et recommandations pour l’adaptateur FTP](../core/best-practices-and-recommendations-for-the-ftp-adapter.md)  

[Configuration de l’adaptateur FTP](../core/configuring-the-ftp-adapter.md)  

[Propriétés et schéma de propriété de l’adaptateur FTP](../core/ftp-adapter-property-schema-and-properties.md)