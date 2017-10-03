---
title: "Planification de la haute disponibilité et récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7efba36-6d9c-4ae0-a4f5-893eb5d62a05
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 742073de6f0e992e5fd0155b1939f0680fa7b3bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-high-availability-and-disaster-recovery"></a>Planification de la haute disponibilité et récupération d’urgence
Les solutions développées avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont souvent critiques au niveau de l’entreprise des applications qui nécessitent une disponibilité maximale. Lorsque ces solutions sont placées en production, les coûts associés aux temps d’arrêt peuvent être mesurées en milliers de dollars par seconde. Pour cette raison, vous devez utiliser des stratégies spécifiques afin d’optimiser les fonctionnalités de récupération d’urgence et disponibilité élevées sont disponibles avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les logiciels de dépendance et le matériel requis pour prendre en charge un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.  
  
## <a name="hardware-considerations"></a>Configuration matérielle requise  
 Pour garantir une haute disponibilité pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, considérez les éléments suivants lors de la planification pour le matériel :  
  
-   Envisagez d’exécuter plusieurs serveurs BizTalk Server (au moins deux) dans un groupe BizTalk pour prendre en charge de plusieurs instances d’hôtes BizTalk en cours d’exécution sur tous les serveurs BizTalk du groupe. Il prend en charge les charge et équilibrage de la tolérance de panne de processus en cours d’exécution dans les instances d’hôte.  
  
-   Envisagez d’implémenter un réseau de stockage (SAN) pour héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Les disques SAN doivent être configurés à l’aide de RAID topologie de 1 + 0 (il s’agit d’une bande de miroir) si possible pour optimiser les performances et haute disponibilité. Pour plus d’informations sur l’utilisation d’un réseau SAN pour héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez la [livre blanc de l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
-   Prévoyez d’installer plusieurs instances de SQL Server pour héberger la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Plusieurs serveurs SQL Server est requis pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] clustering (recommandé) et/ou hébergeant certains [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données physiques distincts [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances (également recommandés).  
  
-   Envisagez d’utiliser un environnement virtuel pour contrôler les coûts du matériel. Microsoft propose une gamme de produits de virtualisation telles que Microsoft Virtual Server 2005 R2, Windows Server 2008 Hyper-V et Microsoft Hyper-V Server 2008. Pour obtenir des recommandations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement virtuel, consultez [Guide BizTalk Server 2009 Hyper-V](http://go.microsoft.com/fwlink/?LinkId=151834) (http://go.microsoft.com/fwlink/?LinkId=151834).  
  
-   Planifier l’installation d’un ou plusieurs serveurs Windows dans un domaine de réseau de périmètre pour fournir des services Internet pour votre organisation. Configurer plusieurs serveurs Windows dans le domaine de réseau de périmètre à l’aide d’une solution (NLB) d’équilibrage de charge réseau. Pour plus d’informations, consultez [Guide déploiement de l’équilibrage de charge réseau](http://go.microsoft.com/fwlink/?LinkId=153139) (http://go.microsoft.com/fwlink/?LinkId=153139).  
  
     Pour plus d’informations sur l’installation des serveurs dans un réseau de périmètre, consultez [configuration de votre domaine lorsque exposer les Transports à Internet](../technical-guides/planning-for-sending-and-receiving.md#BKMK_InternetTrans).  
  
    > [!NOTE]  
    >  Un réseau de périmètre est également appelé un réseau DMZ, zone démilitarisée et sous-réseau filtré.  
  
## <a name="software-considerations"></a>Considérations relatives aux logiciels  
 Pour garantir une haute disponibilité pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, considérez les éléments suivants lors de la planification pour les logiciels :  
  
-   Envisagez d’utiliser l’édition Enterprise de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour répondre à des scénarios qui pourraient tirer parti de la mise en cluster des hôtes BizTalk ou qui pourraient tirer parti de plusieurs bases de données MessageBox en cours d’exécution. En règle générale, la seule raison que vous devez mettre en cluster un hôte BizTalk serait offre une haute disponibilité pour certains adaptateurs BizTalk. Pour plus d’informations sur la fourniture de haute disponibilité pour les adaptateurs BizTalk à l’aide du cluster hôte, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](http://go.microsoft.com/fwlink/?LinkID=151284) (http://go.microsoft.com/fwlink/?LinkID=151284).  
  
-   Envisagez d’implémenter un cluster Windows Server pour héberger la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Enterprise Single Sign-On serveur de secret principal et les bases de données. Pour plus d’informations sur l’utilisation de Windows Server cluster pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données et Enterprise Single Sign-On serveur de secret principal, consultez [haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md) et [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md).  
  
## <a name="high-availability-vs-disaster-recovery"></a>Haute disponibilité vs. Récupération d'urgence  
 Il existe deux méthodes prescrites pour accroître la disponibilité pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement : haute disponibilité à l’aide de la tolérance de panne et/ou de charge équilibrage de charge ou en fournissant une disponibilité accrue à l’aide de la récupération d’urgence. Alors que chaque méthode augmente la disponibilité, la principale différence entre elles est que la tolérance de panne et/ou généralement d’équilibrage de charge fournit des temps de récupération beaucoup plus rapide que la récupération d’urgence. La tolérance de panne et/ou l’équilibrage de charge fournit **haute disponibilité** tandis que la récupération d’urgence fournit **disponibilité renforcée**. Pour plus d’informations sur l’implémentation de la récupération d’urgence, consultez [Checklist : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md) et [la récupération d’urgence](../technical-guides/disaster-recovery.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Augmentation de la disponibilité de BizTalk Server](../technical-guides/increasing-availability-for-biztalk-server.md)   
 [Liste de vérification : Offrant une haute disponibilité avec une tolérance de panne ou l’équilibrage de charge](../technical-guides/checklist-providing-high-availability-with-fault-tolerance-or-load-balancing.md)