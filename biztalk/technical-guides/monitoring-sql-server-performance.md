---
title: Surveiller les performances de SQL Server | Documents Microsoft
description: "Surveiller les bases de données BizTalk Server à l’aide des outils de performances moniteur d’activité et la collecte de données"
ms.custom: 
ms.date: 11/29/2017
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
ms.openlocfilehash: 1e4f9db738298ec2a242350faae3ba5bc9da1c92
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="monitor-sql-server-performance"></a>Analyseur de performances SQL Server
SQL Server fournit plusieurs outils pour surveiller les événements de SQL Server et de paramétrer la structure de base de données physique. [Outils d’analyse des performances et de réglage](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) décrit ces outils. 
  
BizTalk Server est un processus nécessitant beaucoup de la base de données. lors de la résolution des problèmes de performances de BizTalk Server, il peut être utile vérifier également les performances de SQL Server. Les outils suivants peuvent aider à.  
  
## <a name="sql-server-activity-monitor"></a>Moniteur d’activité SQL Server  
Moniteur d’activité SQL Server fournit des informations sur les processus SQL Server et la façon dont ces processus affectent l’instance actuelle de SQL Server. Pour plus d’informations, consultez [moniteur d’activité](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), et [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio). 
  
## <a name="sql-serverdata-collection"></a>Collection de ServerData SQL  
SQL Server fournit un collecteur de données que vous pouvez utiliser pour obtenir et enregistrer les données collectées à partir de plusieurs sources. Le collecteur de données vous permet d’utiliser des conteneurs de collecte de données, qui vous permettent de déterminer l’étendue et la fréquence de collecte de données sur un ordinateur qui exécute SQL Server. Consultez [collecte des données](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des bases de données](../technical-guides/optimizing-database-performance.md)