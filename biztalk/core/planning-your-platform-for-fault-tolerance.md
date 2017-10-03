---
title: "Planification de votre plateforme de la tolérance de panne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- MessageBox database, fault tolerance
- clustering, fault tolerance
- SQL Server RAID
- databases [BAM], fault tolerance
- BizTalk Server, planning
- fault tolerance
- clustering, fail-overs
- planning, fault tolerance
- Primary Import database [BAM]
- BizTalk Server, backing up
- fault tolerance, planning
- planning, BizTalk Server
- Primary Import database [BAM], fault tolerance
- fail-over clustering
ms.assetid: 512ed6b8-db1e-434a-8009-63e952cf5500
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32cb8913ff48ed954e6e57140417966846641f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-your-platform-for-fault-tolerance"></a>Planification de votre plateforme de la tolérance de panne
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est basé sur les plateformes Microsoft Windows et Microsoft SQL Server. Les capacités de résistance et de récupération de BizTalk Server après un sinistre dépendent de celles de la plateforme sous-jacente.  
  
 Pour vos bases de données analyse BAM (Business Activity) et votre base de données MessageBox, nous vous recommandons de que procéder comme suit :  
  
-   Définissez un système de clusters avec basculement en cas de sinistre, disponible avec SQL Server Enterprise Edition. La mise en place de serveurs en cluster avec basculement permet à SQL Server de basculer automatiquement le traitement d'une instance SQL Server entre un serveur défaillant et un serveur opérationnel.  
  
     La base de données d'importation principale BAM collecte les données d'événement. En cas de sinistre, les données ajoutées à cette base de données depuis la dernière sauvegarde seront perdues. Sachant qu'il n'existe aucune solution pour régénérer les événements perdus, il est très important d'activer le système de clusters avec basculement pour la base de données d'importation principale BAM.  
  
-   Utilisez le RAID (redundant array of independent disks) SQL Server, notamment pour la base de données MessageBox et celle d'importation principale BAM.  
  
 Servez-vous des ressources ci-dessous pour élaborer les déploiements Windows et SQL Server et les doter d'une tolérance de pannes. Prenez le temps de vous familiariser avec les technologies de redondance de serveurs et de matériels (mise en cluster et mise en miroir du disque) afin d'éviter les pannes de service et les pertes de données.  
  
-   [Livre blanc : Haute disponibilité : Always On Technologies](http://go.microsoft.com/fwlink/?LinkId=130376)  
  
     Le livre blanc « High Availability – Always On Technologies » présente les fonctionnalités de haute disponibilité disponibles avec SQL Server 2008.  
  
-   [Vue d’ensemble des Solutions de haute disponibilité](http://go.microsoft.com/fwlink/?LinkId=130377)  
  
     Présente plusieurs solutions haute disponibilité SQL Server 2008 qui améliorent la disponibilité des serveurs ou des bases de données.  
  
-   [Chapitre 15 - Options de haute disponibilité SQL Server Resource Kit](http://go.microsoft.com/fwlink/?LinkId=24431)  
  
     Ce kit aborde un certain nombre de questions portant sur l'administration et la planification du déploiement. Le chapitre 15 traite plus particulièrement de la planification d'une tolérance de pannes et de la récupération.  
  
-   [Guide pas à pas des Services de déploiement Windows](http://go.microsoft.com/fwlink/?LinkId=130379)  
  
     Contient des instructions détaillées pour savoir comment utiliser le rôle Services de déploiement Windows dans Windows Server 2008  
  
-   [Kit de déploiement de Windows Server 2003 : Planification des déploiements de serveur](http://go.microsoft.com/fwlink/?LinkId=24433).  
  
     Ce document fournit des informations sur la planification du stockage sur un serveur et sur la conception et le déploiement de serveurs de fichiers, de serveurs d'impression et de Terminal Server dans les moyennes et grandes entreprises.  
  
     Vous pouvez également vous référer aux instructions de ce document pour accroître la disponibilité et l'évolutivité des serveurs grâce à une planification de la gestion à distance des serveurs et à la conception et au déploiement de clusters de serveurs et de clusters d'équilibrage de la charge réseau.  
  
## <a name="backing-up-your-platform"></a>Sauvegarde de votre plateforme.  
 Après avoir configuré le système, préparez des sauvegardes complètes des différents serveurs afin de pouvoir rapidement rétablir un serveur à l'identique en cas de perte de données.  
  
 Pour sauvegarder la plateforme, suivez les procédures des documentations de chacune des technologies suivantes :  
  
-   Microsoft Windows Server Standard, Enterprise ou Datacenter Edition  
  
-   Internet Information Services (IIS)  
  
-   Microsoft SQL Server  
  
-   Windows SharePoint Services, utilisé par l'adaptateur Windows SharePoint Services.  
  
 Suivez les recommandations de « BizTalk Server Operations Guide » pour « Sauvegarde de BizTalk Server » disponible à l’adresse [Checklist : Increasing Availability with la récupération d’urgence](http://go.microsoft.com/fwlink/?LinkId=130498).  
  
 Testez minutieusement les procédures de sauvegarde et de restauration et conservez-les sur un emplacement distant et sécurisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md)