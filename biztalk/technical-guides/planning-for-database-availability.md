---
title: "Planification de la disponibilité de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa74257-4159-46f6-b538-f7e9083d74ad
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea5aa21ad9db78236d7b1e5335053b7c9ce28770
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-database-availability"></a>Planification de la disponibilité de base de données
Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] moteur de messagerie garantit que les processus d’entreprise fiables et durable par la persistance traiter des données métier et d’état à un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] base de données appelé base de données Messagebox de BizTalk. Étant donné que la fiabilité et la durabilité des données persistantes est uniquement efficace que le magasin de données sous-jacent, de planification pour la haute disponibilité de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données est essentiel.  
  
## <a name="hardware-considerations"></a>Configuration matérielle requise  
 Pour garantir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, considérez les éléments suivants lors de la planification pour le matériel :  
  
1.  Envisagez d’implémenter un réseau de stockage (SAN) pour héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Les disques SAN doivent être configurés à l’aide de RAID topologie de 1 + 0 (il s’agit d’une bande de miroir) si possible pour optimiser les performances et haute disponibilité. Pour plus d’informations sur l’utilisation d’un réseau SAN pour héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données voir le [l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) livre blanc ([http://go.microsoft.com/fwlink/?LinkID=101578](http://go.microsoft.com/fwlink/?LinkID=101578)).  
  
2.  Prévoyez d’installer plusieurs ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour héberger le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Plusieurs ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sera nécessaire pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] clustering (recommandé) et/ou hébergeant certains [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données physiques distincts [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances (également recommandés).  
  
3.  Plan sur l’installation d’un ou plusieurs ordinateurs en cours d’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour implémenter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des journaux à des fins de récupération d’urgence. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]implémente des fonctionnalités en attente à l’aide de la base de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] journaux de transaction. [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]envoi de journaux automatise la sauvegarde et la restauration de base de données et les fichiers journaux, ce qui permet un serveur de secours reprendre le traitement de base de données dans le cas où la défaillance du serveur de production. Pour plus d’informations sur l’implémentation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des journaux à des fins de récupération d’urgence, consultez [ce qui est BizTalk Server l’envoi de journaux ?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="software-considerations"></a>Considérations relatives aux logiciels  
 Pour garantir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, considérez les éléments suivants lors de la planification pour les logiciels : envisagez d’installer une version et l’édition de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui prend en charge le basculement de cluster prise en charge et/ou la prise en charge de copie des journaux de BizTalk. Pour obtenir la liste complète des fonctionnalités prises en charge par les éditions de [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], consultez [fonctionnalités prises en charge par les éditions de SQL Server 2008](http://go.microsoft.com/fwlink/?LinkId=151940) ([http://go.microsoft.com/fwlink/? LinkId = 151940](http://go.microsoft.com/fwlink/?LinkId=151940)) dans le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] documentation.  
  
## <a name="high-availability-vs-disaster-recovery"></a>Haute disponibilité vs. Récupération d'urgence  
 Il existe deux méthodes distinctes pour accroître la disponibilité pour un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement : haute disponibilité à l’aide de la tolérance de panne et/ou de charge équilibrage de charge ou la disponibilité à l’aide de la récupération d’urgence. Alors que chaque méthode augmente la disponibilité, la principale différence entre elles est que la tolérance de panne et/ou généralement d’équilibrage de charge fournit des temps de récupération beaucoup plus rapide que la récupération d’urgence ne. Par conséquent, une solution reposant sur la tolérance de panne ou l’équilibrage de charge est généralement considérée comme haute disponibilité au lieu de simplement fournir disponibilité. Les deux méthodes doivent être utilisés dans une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
 Fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données à l’aide de la tolérance de panne avec le Clustering Windows. Pour plus d’informations sur la haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md).  
  
 Augmenter la disponibilité à l’aide de récupération d’urgence [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction. Pour augmenter la disponibilité de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données avec récupération d’urgence, suivez les étapes décrites dans la rubrique [Checklist : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).