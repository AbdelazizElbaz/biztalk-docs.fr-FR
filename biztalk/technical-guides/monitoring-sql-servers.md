---
title: Surveiller les serveurs SQL Server | Documents Microsoft
description: "Utiliser le Pack d’administration de SQL Server pour vérifier performances, espace disponible, configuration de la base de données, les processus bloqués, connectivité, ayant échoué SQL travaux de l’agent, la réplication et plus dans BizTalk Server"
ms.custom: 
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31871432-e13d-4ef3-b886-16c833371f6d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0e3ea9ecb9d9d910549790568d5891b72d06de
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="monitoring-sql-servers"></a><span data-ttu-id="83870-103">Analyse des serveurs SQL</span><span class="sxs-lookup"><span data-stu-id="83870-103">Monitoring SQL Servers</span></span>

## <a name="use-sql-management-pack"></a><span data-ttu-id="83870-104">Utiliser le Pack d’administration SQL</span><span class="sxs-lookup"><span data-stu-id="83870-104">Use SQL management pack</span></span>
<span data-ttu-id="83870-105">Le Pack d’administration de Microsoft SQL Server fournit proactive et réactive de surveillance de SQL Server dans un environnement d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="83870-105">The Microsoft SQL Server management pack provides both proactive and reactive monitoring of SQL Server in an enterprise environment.</span></span> <span data-ttu-id="83870-106">Disponibilité et configuration d’analyse, collecte des données de performances et seuils par défaut sont générés pour l’analyse du niveau de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="83870-106">Availability and configuration monitoring, performance data collection, and default thresholds are built for enterprise-level monitoring.</span></span> <span data-ttu-id="83870-107">Connectivité locale et distante permettent de garantir la disponibilité de base de données.</span><span class="sxs-lookup"><span data-stu-id="83870-107">Both local and remote connectivity checks help ensure database availability.</span></span>  
  
 <span data-ttu-id="83870-108">L’expertise incorporée dans le Pack d’administration de SQL Server, vous pouvez gérer proactivement SQL Server et identifier les problèmes avant qu’ils deviennent critiques ;</span><span class="sxs-lookup"><span data-stu-id="83870-108">With the embedded expertise in the SQL Server management pack, you can proactively manage SQL Server, and identify issues before they become critical.</span></span> <span data-ttu-id="83870-109">Ce pack d’administration augmente la sécurité, disponibilité et les performances de votre infrastructure SQL Server.</span><span class="sxs-lookup"><span data-stu-id="83870-109">This management pack increases the security, availability, and performance of your SQL Server infrastructure.</span></span>  
  
 <span data-ttu-id="83870-110">Le guide du Pack d’administration Microsoft SQL Server qui est fourni avec le pack décrit le contenu du pack d’administration et décrit comment le déployer.</span><span class="sxs-lookup"><span data-stu-id="83870-110">The Microsoft SQL Server management pack guide that comes with the pack describes the content of the management pack, and describes how to deploy it.</span></span> <span data-ttu-id="83870-111">Fonctionnalités du pack d’administration :</span><span class="sxs-lookup"><span data-stu-id="83870-111">Features of the management pack include:</span></span>  
  
-   <span data-ttu-id="83870-112">Analyse de l’état des services inclus tels que SQL Server, l’Agent SQL, serveur de rapports, les Services de Notification</span><span class="sxs-lookup"><span data-stu-id="83870-112">Monitoring the state of the included services such as SQL Server, SQL Agent, Report Server, Notification Services</span></span>  
  
-   <span data-ttu-id="83870-113">Analyse de l’état des bases de données</span><span class="sxs-lookup"><span data-stu-id="83870-113">Monitoring the state of databases</span></span>  
  
-   <span data-ttu-id="83870-114">Analyse l’espace disponible dans les bases de données, configurables par % ou Mo</span><span class="sxs-lookup"><span data-stu-id="83870-114">Monitoring the available space in databases, configurable by % or MB</span></span>  
  
-   <span data-ttu-id="83870-115">S’assurer que des bases de données sont correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="83870-115">Ensuring databases are configured correctly</span></span>  
  
-   <span data-ttu-id="83870-116">Vérifiez les clients peuvent se connecter à SQL Server</span><span class="sxs-lookup"><span data-stu-id="83870-116">Ensure clients can connect to the SQL Server</span></span>  
  
-   <span data-ttu-id="83870-117">Surveiller les processus bloqués</span><span class="sxs-lookup"><span data-stu-id="83870-117">Monitor blocked processes</span></span>  
  
-   <span data-ttu-id="83870-118">Surveiller l’agent a échoué de tâches prend un temps excessif pour exécuter des tâches</span><span class="sxs-lookup"><span data-stu-id="83870-118">Watch for failed agent jobs, and jobs taking an excessive time to execute</span></span>  
  
-   <span data-ttu-id="83870-119">Surveiller l’intégrité de la réplication et d’alerte en cas d’échec</span><span class="sxs-lookup"><span data-stu-id="83870-119">Monitor the health of replication and alert on failures</span></span>  
  
-   <span data-ttu-id="83870-120">Surveiller l’état de mise en miroir de base de données</span><span class="sxs-lookup"><span data-stu-id="83870-120">Monitor the state of Database Mirroring</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="83870-121">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="83870-121">Next steps</span></span>
  
-   [<span data-ttu-id="83870-122">Surveillance des bases de données et des tâches SQL Server Agent</span><span class="sxs-lookup"><span data-stu-id="83870-122">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)  
  
-   [<span data-ttu-id="83870-123">Comment marquer des bases de données BizTalk Server pour une surveillance personnalisée</span><span class="sxs-lookup"><span data-stu-id="83870-123">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
-   [<span data-ttu-id="83870-124">Surveiller les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="83870-124">Monitor the BizTalk Server Databases</span></span>](../technical-guides/monitor-the-biztalk-server-databases.md)