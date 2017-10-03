---
title: "Création d’un environnement hautement disponible BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, high availability
- architecture, databases
- databases, architecture
- performance
- hosts, multiple
- hosts, architecture
- architecture, hosts
- databases, clustering
- high availability, designing
- BizTalk Server, architecture
- installation, planning
- clustering, databases
- installation, availability
ms.assetid: 758eb3bd-a25b-4863-a4ca-d7a1635f7542
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87044102248d371ea19ed07d676a0e7a0861296e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-highly-available-biztalk-server-environment"></a>Création d'un environnement BizTalk Server à haute disponibilité
Cette section décrit comment fournir une haute disponibilité des données et communications dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de l’intégration des applications et des systèmes disparates. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]sépare les données des hôtes qui les traitent, ce qui vous permet de résoudre les problèmes par la mise à l’échelle les bases de données de disponibilité et héberge indépendamment.  
  
## <a name="demonstrating-high-availability"></a>Mise en évidence des besoins en termes de haute disponibilité  
 Pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], la haute disponibilité est surtout orientée sur la récupération des composants fonctionnels susceptibles d'interrompre la disponibilité dans un déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour savoir si la haute disponibilité est nécessaire dans un environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez provoquer une panne et mesurer l'efficacité du produit en matière de récupération. Un déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible permet une transparence des erreurs et des défaillances pour les systèmes et les applications externes et garantit un fonctionnement correct de l'ensemble des services en évitant les interruptions au maximum.  
  
## <a name="designing-for-high-availability"></a>Conception de la haute disponibilité  
 Conception d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement qui offre une haute disponibilité implique l’implémentation de redondance pour chacun des composants fonctionnels impliqués dans un scénario de l’intégration de processus entreprise ou application. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]simplifie l’implémentation de ces scénarios en séparant conceptuellement les données des hôtes qui les traitent. Pour doter [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de la haute disponibilité, il faut donc exécuter plusieurs instances d'hôte et mettre en cluster les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme suit :  
  
-   **Architecture pour les hôtes BizTalk** [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de séparer les hôtes et d’exécuter plusieurs instances d’hôte pour fournir une haute disponibilité pour les fonctions clés telles que la réception des messages, le traitement des orchestrations et envoyer des messages. Ces hôtes ne requièrent pas de mise en cluster ou de mécanisme d'équilibrage de charge, car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] répartit automatiquement la charge entre les différents ordinateurs par le biais des instances d'hôte. Cependant, pour fournir une disponibilité élevée, les hôtes sur lesquels s'exécute le gestionnaire de réception pour les adaptateurs HTTP et SOAP doivent être dotés d'un mécanisme d'équilibrage de charge tel que celui qui permet d'équilibrer la charge réseau.  
  
-   **Architecture des bases de données BizTalk Server** haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données se compose généralement de deux ou plusieurs ordinateurs de base de données configurées dans une configuration de cluster de serveurs actif/passif. Ces ordinateurs partagent une ressource de disque commune (ex. : baie de stockage RAID5 SCSI ou SAN) et utilisent le clustering Windows afin de disposer d'une redondance des sauvegardes et d'une tolérance de pannes.  
  
> [!NOTE]
>  Les environnements hautement disponibles sont, par définition, des environnements à plusieurs ordinateurs. Lorsque vous configurez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement multiserveur, vous devez utiliser des groupes de domaine et des comptes.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] étant basé sur Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et Microsoft SQL Server 2008, assurez-vous de déployer ces produits de façon à les doter de la haute disponibilité avant de configurer les hôtes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les liens suivants comportent des informations sur la façon d'assurer la haute disponibilité pour ces produits sous-jacents :  
  
-   **High Availability – Always On Technologies**à l’adresse [http://go.microsoft.com/fwlink/?LinkId=130376](http://go.microsoft.com/fwlink/?LinkId=130376).  
  
     Ce livre blanc décrit les fonctionnalités de haute disponibilité disponibles dans SQL Server 2008.  
  
-   **Vue d’ensemble des Solutions haute disponibilité**à l’adresse [http://go.microsoft.com/fwlink/?LinkId=130377](http://go.microsoft.com/fwlink/?LinkId=130377).  
  
     Présente plusieurs solutions haute disponibilité SQL Server 2008 qui améliorent la disponibilité des serveurs ou des bases de données.  
  
-   **Guide pas à pas de Services de déploiement Windows**à l’adresse [http://go.microsoft.com/fwlink/?LinkId=130379](http://go.microsoft.com/fwlink/?LinkId=130379).  
  
     Ce guide contient des instructions pas à pas sur l'utilisation du rôle Services de déploiement Windows dans Windows Server 2008.  
  
-   **Kit de déploiement de Windows Server 2003 : Planification des déploiements de serveur**à l’adresse [http://go.microsoft.com/fwlink/?LinkId=24433](http://go.microsoft.com/fwlink/?LinkId=24433).  
  
     Ce document fournit des informations sur la planification du stockage sur un serveur et sur la conception et le déploiement de serveurs de fichiers, de serveurs d'impression et de Terminal Server dans les moyennes et grandes entreprises.  
  
-   **Augmentation de la disponibilité de BizTalk Server**à l’adresse [http://go.microsoft.com/fwlink/?LinkId=130457](http://go.microsoft.com/fwlink/?LinkId=130457).  
  
     Section de la [Guide des opérations BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=130458) qui décrit les manières d’accroître la disponibilité de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration de la haute disponibilité pour des hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)  
  
-   [Offrant une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de scénarios de haute disponibilité BizTalk Server](../core/sample-biztalk-server-high-availability-scenarios.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)