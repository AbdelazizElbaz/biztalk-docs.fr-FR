---
title: "Base de données SQL Server mise en miroir, le service VSS et AlwaysOn | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b965cafc-cd34-4657-975d-0dedffd27333
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bea9d6063330e7af15ecb202513deb4def6571fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson"></a>Mise en miroir de bases de données SQL Server, service VSS et AlwaysOn
Microsoft fournit des solutions logicielles appelées SQL Server *mise en miroir de base de données* et le Windows VSS Volume Shadow Copy Service () pour augmenter la haute disponibilité dans certains scénarios particuliers. SQL Server *mise en miroir de base de données* augmente la probabilité qu’une base de données est disponible pendant que le Volume Shadow Copy Service (VSS) fournit une fonctionnalité de sauvegarde et de restauration pour la récupération d’urgence. L’utilisation de SQL Server *mise en miroir de base de données* ou le Service Windows VSS ne sont pas pris en charge des solutions pour garantir la haute disponibilité de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
## <a name="using-sql-server-database-mirroring-to-provide-high-availability-for-biztalk-server-databases"></a>Utilisation de la mise en miroir de bases de données SQL Server à des fins de haute disponibilité des bases de données BizTalk Server  
 L’utilisation de SQL Server *mise en miroir de base de données* n’est pas actuellement pris en charge pour garantir la haute disponibilité de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données en raison de certaines difficultés à maintenir la cohérence des transactions dans le Bases de données BizTalk Server. Pour plus d’informations sur la mise en miroir de base de données et les Transactions entre bases de données dans SQL Server, consultez [http://go.microsoft.com/fwlink/?LinkId=87977](http://go.microsoft.com/fwlink/?LinkId=87977). [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]bases de données doivent être installés sur un cluster SQL Server afin de garantir une haute disponibilité et BizTalk d’envoi de journaux doit être utilisée à des fins de récupération d’urgence. Pour plus d’informations sur la copie des journaux de BizTalk, consultez [journaux](../core/log-shipping.md).  
  
## <a name="using-the-volume-shadow-copy-service-to-provide-high-availability-for-biztalk-server-databases"></a>Utilisation du service VSS à des fins de haute disponibilité des bases de données BizTalk Server  
 Le service VSS offre des fonctionnalités de sauvegarde et de restauration à des fins de récupération d'urgence. Étant donné que Microsoft Distributed Transaction Coordinator (MS DTC) prise en charge de VSS il est limité à des scénarios de coordination de déploiement et de transaction locales (et autres), utilisation du service VSS n’est pas actuellement pris en charge pour garantir la haute disponibilité de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données. Pour plus d’informations sur la prise en charge de Volume Shadow Copy Service avec les Transactions distribuées, consultez [http://go.microsoft.com/fwlink/?LinkId=139505](http://go.microsoft.com/fwlink/?LinkId=139505).  
  
## <a name="using-sql-server-alwayson"></a>Utilisation de SQL Server AlwaysOn 
 Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts, MS DTC (Microsoft Distributed Transaction Coordinator) gère les transactions entre les ordinateurs. 
 
À compter de SQL Server 2016, AlwaysOn prend en charge les transactions MSDTC. Par conséquent, le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] fonctionnalité AlwaysOn est pris en charge lors de l’utilisation de cette version de SQL Server. Avec les versions précédentes de SQL Server, le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] fonctionnalité AlwaysOn ne prend pas en charge les transactions MSDTC, et par conséquent AlwaysOn n’est pas pris en charge. 

Consultez [haute disponibilité à l’aide de SQL Server groupes de disponibilité AlwaysOn](../core/high-availability-using-sql-server-always-on-availability-groups.md).
  
## <a name="see-also"></a>Voir aussi  
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)   
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)