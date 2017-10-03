---
title: "Résolution des problèmes d’un Cluster Windows Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 283cf4cd-ce40-48b7-8549-9ab17d7d2c34
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da1159bafc42f6cfbf47621e3b846764e50e5267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-a-windows-server-cluster"></a>Résolution des problèmes d’un Cluster Windows Server
Microsoft[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge l'utilisation d'un cluster de serveurs Windows Server pour la mise en cluster d'hôtes, afin de garantir la haute disponibilité du serveur de secret principal du système d'authentification unique de l'entreprise et celle des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette section vous donne quelques instructions générales relatives à l'utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement de cluster Windows Server cet aborde certains problèmes connus pouvant survenir lors de l'utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement de cluster Windows Server.  
  
## <a name="general-guidelines"></a>Règles générales  
 Suivez ces recommandations générales pour optimiser la productivité du cluster de serveurs Windows Server et pour résoudre les problèmes pouvant affecter [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
1.  Effectuez un test de validation technique [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec un cluster de serveurs Windows Server dans un environnement de serveur virtualisé Microsoft Virtual Server.  
  
     **Le rôle Hyper-V disponible avec Windows Server 2008 peut être utilisé pour créer un environnement de serveur virtualisé.**  
  
    -   Pour plus d’informations sur Windows Server 2008 Hyper-V, consultez « Virtualisation et Consolidation » à [http://go.microsoft.com/fwlink/?LinkID=121187](http://go.microsoft.com/fwlink/?LinkID=121187).  
  
    -   Pour plus d’informations sur les avantages de l’utilisation de la technologie de virtualisation fournie avec Hyper-V, consultez le livre blanc « Avancé virtualisation avantages de Windows Server 2008 éditions for the Enterprise » disponible en téléchargement à [ http://go.Microsoft.com/fwlink/?LinkId=123530](http://go.microsoft.com/fwlink/?LinkId=123530).  
  
    -   Procédure d’utilisation de Hyper-V pour créer un cluster Windows Server 2008 est disponibles à [http://go.microsoft.com/fwlink/?LinkId=129680](http://go.microsoft.com/fwlink/?LinkId=129680).  
  
     Le test de validation technique [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec un cluster de serveurs Windows Server dans un environnement de serveur virtualisé Microsoft Virtual Server est très flexible et consomme beaucoup moins de ressources que le cluster de serveurs Windows Server lui-même. Si vous choisissez cette solution, prévoyez au moins 512 Mo de mémoire pour chaque ordinateur virtuel en exécution simultanée avec l'ordinateur hôte et 512 Mo de mémoire supplémentaire pour le système d'exploitation hôte. Par exemple, pour une solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec un cluster de serveurs Windows Server qui utilise cinq ordinateurs virtuels (deux nœuds de cluster BizTalk Server, deux nœuds de cluster Microsoft SQL Server et un contrôleur de domaine), vous devez prévoir 3 Go de mémoire pour l'ordinateur hôte. Si l'environnement de test de validation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requiert plus de 2 Go de mémoire, envisagez d'installer une version 64 bits de Windows sur l'ordinateur hôte (requise pour le rôle Hyper-V) pour vous assurer que toute la mémoire installée est accessible depuis le système d'exploitation hôte.  
  
## <a name="troubleshooting-resources"></a>Ressources pour la résolution des problèmes  
 **Ressources pour la résolution des problèmes de clustering de basculement Windows Server 2008**  
  
-   Examinez le [Validation du Cluster de basculement et de résolution des problèmes avec Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=129729) TechNet Webcast sur le site Web Microsoft TechNet. Cette ressource décrit le dépannage du processus de validation du cluster de basculement et la résolution des problèmes avec Windows Server 2008.  
  
-   Pour plus d’informations sur l’analyse des problèmes avec le clustering de basculement Windows Server 2008, consultez la rubrique [afficher les événements et journaux pour un Cluster de basculement](http://go.microsoft.com/fwlink/?LinkId=129730) sur le site Web Microsoft TechNet.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="any-attempt-to-bring-a-clustered-msdtc-resource-online-fails-which-causes-dependent-biztalk-server-services-to-fail"></a>Les tentatives de mise en ligne d'une ressource MSDTC mise en cluster échouent et entraînent l'échec des services BizTalk Server dépendants  
  
##### <a name="problem"></a>Problème  
 Une ressource Distributed Transaction Coordinator (MSDTC) en cluster ne peut pas être mises en ligne la **mettre en ligne** option dans l’administrateur de Cluster, ce qui entraîne [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des opérations d’exécution qui sont dépendantes de MSDTC prise en charge de la transaction échoue.  
  
##### <a name="cause"></a>Cause  
 L'échec de la mise en ligne d'une ressource MSDTC mise en cluster peut se produire pour de nombreuses raisons, y compris les suivantes :  
  
-   La ressource MSDTC mise en cluster n'est pas configurée en fonction des dépendances de ressource Disque et Nom de réseau correctes, ou les dépendances de ressource sont défaillantes.  
  
-   Des problèmes d'autorisation empêchent l'activation de la ressource MSDTC mise en cluster.  
  
##### <a name="resolution"></a>Résolution  
 **Effectuez les étapes suivantes sur un cluster Windows Server 2008 :**  
  
-   Suivez les étapes de [liste de vérification : création d’un MS DTC Resource dans un Cluster de basculement Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=129677) pour la création d’une ou plusieurs ressources MSDTC en cluster sur un cluster de basculement Windows Server 2008.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)   
 [Exemples de scénarios de haute disponibilité BizTalk Server](../core/sample-biztalk-server-high-availability-scenarios.md)   
 [Options d’Installation de l’authentification unique de la haute disponibilité](../core/high-availability-sso-installation-options.md)