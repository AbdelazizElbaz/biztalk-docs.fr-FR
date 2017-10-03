---
title: "Exemples de scénarios de haute disponibilité de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- examples, high availability
- architecture, examples
- high availability, examples
- examples, architecture
- databases, clustering
- architecture, medium distributions
- scaling
- architecture, large distributions
ms.assetid: ad9e3f57-1a23-41c2-82c9-dc8e1b29ed4d
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff4db96e89dc91ee96aaf5f0b60f0de34ce83425
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-biztalk-server-high-availability-scenarios"></a>Exemples de scénarios BizTalk Server à haute disponibilité
Cette rubrique décrit les scénarios Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournissant une haute disponibilité par le biais de couches hôtes mises à l'échelle. En répartissant des éléments d'une fonctionnalité entre plusieurs hôtes et couches dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les administrateurs peuvent fournir une redondance pour chaque hôte et les mettre à l'échelle indépendamment les uns des autres. Pour que chaque zone fonctionnelle bénéficie de la haute disponibilité, créez des hôtes distincts pour chaque fonction principale (réception, traitement, envoi et suivi), et mettez les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et le serveur de secret principal du système d'authentification unique de l'entreprise en cluster.  
  
## <a name="small-biztalk-server-deployments"></a>Déploiements BizTalk Server à petite échelle  
 Le plus petit déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] garantissant la haute disponibilité de SQL Server et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est constitué de deux ordinateurs qui ont comme serveur SQL Server une configuration de cluster active/active. Les deux ordinateurs contiennent des instances de tous les hôtes BizTalk de l'environnement. Si l'un des ordinateurs s'arrête ou rencontre des problèmes, les autres ordinateurs se chargent de la continuité du service pour les serveurs SQL Server et BizTalk Server. Cette configuration ne fournit pas de disponibilité élevée car elle ne prend pas en compte la mise en cluster du serveur de secret principal. En effet, les instances d'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne démarrent pas sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur lequel la ressource d'authentification unique de l'entreprise est passive. Pour plus d’informations sur le serveur de secret principal de clustering, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
 Pour les petits déploiements [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de moins de cinq ordinateurs, il est recommandé d'exécuter le cluster SQL Server contenant les bases de données BizTalk Server sur des ordinateurs distincts de ceux qui exécutent BizTalk Server. Les ordinateurs BizTalk Server peuvent exécuter tous les hôtes BizTalk (hôtes de réception, de traitement et d'envoi). Pour que ce déploiement soit hautement disponible, mettez en cluster SQL Server et le serveur de secret principal du système d'authentification unique de l'entreprise, et équipez-vous de deux serveurs BizTalk, chacun exécutant une instance des hôtes dans l'environnement.  
  
 L'illustration suivante représente un petit déploiement BizTalk Server hautement disponible.  
  
 ![Déploiement de BizTalk Server à petite](../core/media/tdi-highava-smalldepl.gif "TDI_HighAva_SmallDepl")  
  
## <a name="medium-sized-biztalk-server-deployments"></a>Déploiements BizTalk Server de taille moyenne  
 Pour les déploiements de taille moyenne, comprenant de cinq à dix ordinateurs, il est recommandé de mettre en cluster le serveur SQL Server contenant les bases de données BizTalk Server et le serveur de secret principal du système d'authentification unique de l'entreprise. Si, dans votre scénario, l'accent est mis sur la réception, vous pouvez consacrer deux serveurs BizTalk à l'exécution des instances de l'hôte de réception afin d'obtenir une solution hautement disponible. Vous pouvez ensuite configurer deux ordinateurs supplémentaires pour l'exécution des instances de l'hôte de traitement et de l'hôte d'envoi. Pour que ce déploiement soit hautement disponible, créez des instances d'hôte pour les hôtes de traitement et d'envoi sur deux serveurs BizTalk différents. Par ailleurs, si, dans votre scénario, l'accent est mis sur le traitement, vous pouvez consacrer deux serveurs BizTalk à l'exécution des instances de l'hôte de traitement et garder les deux serveurs BizTalk restants pour l'exécution des instances des hôtes de réception et d'envoi.  
  
 Le schéma suivant représente un environnement BizTalk Server hautement disponible de taille moyenne équipé de deux serveurs BizTalk dédiés aux opérations de réception.  
  
 ![Support &#45; Taille du déploiement de BizTalk Server](../core/media/tdi-highava-meddepl.gif "TDI_HighAva_MedDepl")  
  
 Pour plus d’informations sur la haute disponibilité pour Enterprise Single Sign-On, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
## <a name="large-scale-biztalk-server-deployments"></a>Déploiements BizTalk Server à grande échelle  
 Pour des déploiements à grande échelle contenant dix ordinateurs ou plus, attribuez des ordinateurs BizTalk Server différents à chacune des fonctions de réception, de traitement et d'envoi. De plus, s'il existe un grand nombre d'ordinateurs BizTalk Server dans un groupe, vous pouvez inclure des ordinateurs supplémentaires pour les bases de données MessageBox afin d'améliorer les performances. Dans ce cas, mettez en cluster les bases de données MessageBox et le serveur de secret principal afin d'obtenir une disponibilité élevée.  
  
 Une configuration distribuée de ce type montre la flexibilité de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], qui vous permet d'évaluer et d'identifier les points faibles de votre déploiement et d'allouer de façon stratégique les ressources afin de réduire ces faiblesses. L'environnement commercial actuel, extrêmement dynamique, exige cette flexibilité car le flux de la charge de travail et les besoins des entreprises varient constamment.  
  
 Au lieu d'investir dans la mise à jour ou l'acquisition de matériel supplémentaire, vous pouvez exploiter les ressources existantes et obtenir un environnement hautement disponible en déplaçant les ressources d'ordinateurs utilisant peu de ressources vers des ordinateurs qui en utilisent énormément.  
  
 L'illustration suivante représente un déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à grande échelle.  
  
 ![Grand &#45; L’échelle du déploiement de BizTalk Server](../core/media/tdi-highava-largedepl.gif "TDI_HighAva_LargeDepl")  
  
 Pour plus d’informations sur la haute disponibilité pour Enterprise Single Sign-On, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
## <a name="providing-high-availability-using-hyper-v-and-failover-clustering"></a>Configuration de la haute disponibilité à l'aide d'Hyper-V et du clustering avec basculement  
 Le rôle Hyper-V et la fonctionnalité de clustering avec basculement de Windows® Server 2008 peuvent être combinées pour assurer la haute disponibilité d'un environnement de serveur virtualisé. Les ordinateurs BizTalk Server et SQL Server utilisés dans un déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent être installés dans un environnement virtualisé Hyper-V, puis activés pour la haute disponibilité via le clustering avec basculement. L'exécution d'un système d'exploitation invité sous Hyper-V impliquant la mobilisation de ressources système, il est recommandé de tester les performances de manière approfondie avant le déploiement d'une telle solution dans un environnement de production. Pour plus d’informations sur l’utilisation de Hyper-V et clustering avec basculement pour fournir une haute disponibilité pour les machines virtuelles, consultez « Hyper-V Step Guide : Hyper-V et le Clustering de basculement » à [http://go.microsoft.com/fwlink/?LinkID=129113](http://go.microsoft.com/fwlink/?LinkID=129113). Pour plus d’informations sur le déploiement d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtualisé Hyper-V, consultez le Guide d’Hyper-V BizTalk Server disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=189706](http://go.microsoft.com/fwlink/?LinkId=189706).  
  
## <a name="see-also"></a>Voir aussi  
 [Offrant une haute disponibilité pour les hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)   
 [Offrant une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [Haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md)