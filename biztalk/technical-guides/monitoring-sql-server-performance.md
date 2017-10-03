---
title: Analyse des performances SQL Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020fa764-968e-467c-b146-d069f5606a0f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5abdc3054576e03f28967017767112cea652f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-server-performance"></a>Analyse des performances de SQL Server
[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]fournit plusieurs outils pour surveiller les événements de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et de paramétrer la conception physique de la base de données. Ces outils sont décrits dans la rubrique [outils d’analyse des performances et de réglage](http://go.microsoft.com/fwlink/?LinkId=146357) (http://go.microsoft.com/fwlink/?LinkId=146357) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne. Pour plus d’informations sur les outils spécifiques utilisés pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] analyse et de réglage des performances sont fourni ci-dessous.  
  
## <a name="sql-server-performance-monitoring-tools"></a>Outils de surveillance des performances SQL Server  
 Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est un tel processus nécessitant beaucoup de la base de données, il est souvent utile de prendre un coup de œil ce qui se passe dans SQL Server lors du dépannage [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les problèmes de performances. Le reste de cette rubrique décrit les outils disponibles pour vérifier les données en temps réel et archivées sur d’analyse des performances [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)].  
  
### <a name="sql-server-2008-r2-activity-monitor"></a>Moniteur d’activité SQL Server 2008 R2  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]Moniteur d’activité fournit des informations sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] processus et la façon dont ces processus affectent l’instance actuelle de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations sur [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] moniteur d’activité, consultez [moniteur d’activité](http://go.microsoft.com/fwlink/?LinkId=146355) (http://go.microsoft.com/fwlink/?LinkId=146355) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne. Pour plus d’informations sur la façon d’ouvrir le moniteur d’activité à partir de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, consultez [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.  
  
### <a name="sql-server-2008-r2-data-collection"></a>Collecte de données SQL Server 2008 R2  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] fournit un collecteur de données qui vous permet d'obtenir et d'enregistrer des données rassemblées à partir de plusieurs sources. Le collecteur de données vous permet d'utiliser des conteneurs de collecte de données qui vous permettent de déterminer l'étendue et la fréquence de la collecte de données sur ordinateur qui exécute [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]. Pour plus d’informations sur l’implémentation de [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] collecte de données, consultez [collecte des données](http://go.microsoft.com/fwlink/?LinkId=146356) (http://go.microsoft.com/fwlink/?LinkId=146356) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de la base de données](../technical-guides/optimizing-database-performance.md)