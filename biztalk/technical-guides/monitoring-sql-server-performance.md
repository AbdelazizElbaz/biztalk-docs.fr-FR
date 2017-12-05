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
# <a name="monitor-sql-server-performance"></a><span data-ttu-id="3437e-103">Analyseur de performances SQL Server</span><span class="sxs-lookup"><span data-stu-id="3437e-103">Monitor SQL Server Performance</span></span>
<span data-ttu-id="3437e-104">SQL Server fournit plusieurs outils pour surveiller les événements de SQL Server et de paramétrer la structure de base de données physique.</span><span class="sxs-lookup"><span data-stu-id="3437e-104">SQL Server provides several tools for monitoring events in SQL Server and for tuning the physical database design.</span></span> <span data-ttu-id="3437e-105">[Outils d’analyse des performances et de réglage](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) décrit ces outils.</span><span class="sxs-lookup"><span data-stu-id="3437e-105">[Tools for Performance Monitoring and Tuning](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools) describes these tools.</span></span> 
  
<span data-ttu-id="3437e-106">BizTalk Server est un processus nécessitant beaucoup de la base de données.</span><span class="sxs-lookup"><span data-stu-id="3437e-106">BizTalk Server is a database-intensive process.</span></span> <span data-ttu-id="3437e-107">lors de la résolution des problèmes de performances de BizTalk Server, il peut être utile vérifier également les performances de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3437e-107">when troubleshooting BizTalk Server performance issues, it can be beneficial to also check the SQL Server performance.</span></span> <span data-ttu-id="3437e-108">Les outils suivants peuvent aider à.</span><span class="sxs-lookup"><span data-stu-id="3437e-108">The following tools can help.</span></span>  
  
## <a name="sql-server-activity-monitor"></a><span data-ttu-id="3437e-109">Moniteur d’activité SQL Server</span><span class="sxs-lookup"><span data-stu-id="3437e-109">SQL Server Activity Monitor</span></span>  
<span data-ttu-id="3437e-110">Moniteur d’activité SQL Server fournit des informations sur les processus SQL Server et la façon dont ces processus affectent l’instance actuelle de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3437e-110">SQL Server Activity Monitor provides information about SQL Server processes and how these processes affect the current instance of SQL Server.</span></span> <span data-ttu-id="3437e-111">Pour plus d’informations, consultez [moniteur d’activité](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), et [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio).</span><span class="sxs-lookup"><span data-stu-id="3437e-111">For more information, see [Activity Monitor](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), and [How to: Open Activity Monitor (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio).</span></span> 
  
## <a name="sql-serverdata-collection"></a><span data-ttu-id="3437e-112">Collection de ServerData SQL</span><span class="sxs-lookup"><span data-stu-id="3437e-112">SQL ServerData Collection</span></span>  
<span data-ttu-id="3437e-113">SQL Server fournit un collecteur de données que vous pouvez utiliser pour obtenir et enregistrer les données collectées à partir de plusieurs sources.</span><span class="sxs-lookup"><span data-stu-id="3437e-113">SQL Server provides a data collector that you can use to obtain and save data that is gathered from several sources.</span></span> <span data-ttu-id="3437e-114">Le collecteur de données vous permet d’utiliser des conteneurs de collecte de données, qui vous permettent de déterminer l’étendue et la fréquence de collecte de données sur un ordinateur qui exécute SQL Server.</span><span class="sxs-lookup"><span data-stu-id="3437e-114">The data collector enables you to use data collection containers, which enable you to determine the scope and frequency of data collection on a computer that is running SQL Server.</span></span> <span data-ttu-id="3437e-115">Consultez [collecte des données](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).</span><span class="sxs-lookup"><span data-stu-id="3437e-115">See [Data Collection](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3437e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3437e-116">See Also</span></span>  
 [<span data-ttu-id="3437e-117">Optimisation des performances des bases de données</span><span class="sxs-lookup"><span data-stu-id="3437e-117">Optimizing Database Performance</span></span>](../technical-guides/optimizing-database-performance.md)