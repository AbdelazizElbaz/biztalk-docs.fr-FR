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
ms.openlocfilehash: d77ce6572ace3617308a046a422a3422b2dd8df5
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-database-availability"></a>Planification de la disponibilité de base de données
Le moteur de messagerie de BizTalk Server permet de s’assurer que les processus d’entreprise sont fiables et durables par la persistance traiter des données métier et d’état à une base de données SQL Server appelée base de données Messagebox de BizTalk. Comme la fiabilité et la durabilité des données persistantes n’est efficace que la banque de données sous-jacente, il est extrêmement important de planification pour une haute disponibilité des bases de données BizTalk Server.  
  
## <a name="hardware-considerations"></a>Configuration matérielle requise  
 Pour garantir une haute disponibilité pour les bases de données BizTalk Server, considérez les éléments suivants lors de la planification pour le matériel :  
  
1.  Envisagez d’implémenter un réseau de zone de stockage (SAN) pour héberger les bases de données BizTalk Server. Les disques SAN doivent être configurés à l’aide de RAID topologie de 1 + 0 (il s’agit d’une bande de miroir) si possible pour optimiser les performances et haute disponibilité. 
  
2.  Planifier l’installation de plusieurs ordinateurs exécutant SQL Server pour héberger les bases de données BizTalk Server. Plusieurs ordinateurs exécutant SQL Server sera requises pour SQL Server clustering (recommandé) et/ou hébergeant certaines bases de données BizTalk Server sur des instances de SQL Server physiques distincts (également recommandés).  
  
3.  Prévoyez d’installer un ou plusieurs ordinateurs exécutant SQL Server pour mettre en œuvre des journaux de transaction SQL Server à des fins de récupération d’urgence. BizTalk Server implémente des fonctionnalités en attente de base de données via l’utilisation de SQL Server copie des journaux. SQL Server d’envoi de journaux automatise la sauvegarde et la restauration de base de données et les fichiers journaux, ce qui permet un serveur de secours reprendre le traitement de base de données dans le cas où la défaillance du serveur de production. Pour plus d’informations sur l’implémentation des journaux de transaction SQL Server à des fins de récupération d’urgence, consultez [ce qui est BizTalk Server l’envoi de journaux ?](../technical-guides/what-is-biztalk-server-log-shipping.md)  
  
## <a name="software-considerations"></a>Considérations relatives aux logiciels  
 Pour garantir une haute disponibilité pour les bases de données BizTalk Server, considérez les éléments suivants lors de la planification pour les logiciels : envisagez d’installer une version et l’édition de SQL Server qui prend en charge de la prise en charge et/ou la prise en charge de journaux BizTalk de clustering de basculement. Pour obtenir une liste complète des fonctionnalités prises en charge par les éditions de SQL Server, consultez [éditions et les fonctionnalités prises en charge](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016).
  
## <a name="high-availability-vs-disaster-recovery"></a>Haute disponibilité vs. Récupération d'urgence  
 Il existe deux méthodes distinctes pour accroître la disponibilité pour un environnement BizTalk Server : haute disponibilité à l’aide de la tolérance de panne et/ou de charge équilibrage de charge ou la disponibilité à l’aide de la récupération d’urgence. Alors que chaque méthode augmente la disponibilité, la principale différence entre elles est que la tolérance de panne et/ou généralement d’équilibrage de charge fournit des temps de récupération beaucoup plus rapide que la récupération d’urgence ne. Par conséquent, une solution reposant sur la tolérance de panne ou l’équilibrage de charge est généralement considérée comme haute disponibilité au lieu de simplement fournir disponibilité. Les deux méthodes doivent être utilisés dans un environnement BizTalk Server de production.  
  
 Fournir une haute disponibilité pour les bases de données BizTalk Server à l’aide de la tolérance de panne avec le Clustering Windows. Pour plus d’informations sur la fourniture de haute disponibilité pour les bases de données BizTalk Server, consultez [haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md).  
  
 Augmenter la disponibilité avec reprise après sinistre des journaux de récupération à l’aide de BizTalk Server. Pour augmenter la disponibilité des bases de données BizTalk Server avec la récupération d’urgence, suivez les étapes décrites dans la rubrique [Checklist : Increasing Availability with la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md).