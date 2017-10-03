---
title: Analyse des serveurs SQL Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
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
ms.openlocfilehash: 6ac37905574090fb346aeee198ea8e92a0f436f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-sql-servers"></a><span data-ttu-id="a4a62-102">Analyse des serveurs SQL</span><span class="sxs-lookup"><span data-stu-id="a4a62-102">Monitoring SQL Servers</span></span>
<span data-ttu-id="a4a62-103">Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration fournit une analyse proactive et réactive de [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] dans un environnement d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="a4a62-103">The Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] management pack provides both proactive and reactive monitoring of [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] and [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] in an enterprise environment.</span></span> <span data-ttu-id="a4a62-104">Disponibilité et configuration d’analyse, collecte des données de performances et seuils par défaut sont générés pour l’analyse du niveau de l’entreprise.</span><span class="sxs-lookup"><span data-stu-id="a4a62-104">Availability and configuration monitoring, performance data collection, and default thresholds are built for enterprise-level monitoring.</span></span> <span data-ttu-id="a4a62-105">Connectivité locale et distante permettent de garantir la disponibilité de base de données.</span><span class="sxs-lookup"><span data-stu-id="a4a62-105">Both local and remote connectivity checks help ensure database availability.</span></span>  
  
 <span data-ttu-id="a4a62-106">L’expertise incorporée dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration, vous pouvez gérer de façon proactive [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]et identifier les problèmes avant qu’ils deviennent critiques.</span><span class="sxs-lookup"><span data-stu-id="a4a62-106">With the embedded expertise in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] management pack, you can proactively manage [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], and identify issues before they become critical.</span></span> <span data-ttu-id="a4a62-107">Ce pack d’administration augmente la sécurité, disponibilité et les performances de votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] infrastructure.</span><span class="sxs-lookup"><span data-stu-id="a4a62-107">This management pack increases the security, availability, and performance of your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] infrastructure.</span></span>  
  
 <span data-ttu-id="a4a62-108">Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] guide du Pack d’administration qui est fourni avec le pack décrit le contenu du pack d’administration et décrit comment le déployer.</span><span class="sxs-lookup"><span data-stu-id="a4a62-108">The Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] management pack guide that comes with the pack describes the content of the management pack, and describes how to deploy it.</span></span> <span data-ttu-id="a4a62-109">Fonctionnalités du pack d’administration :</span><span class="sxs-lookup"><span data-stu-id="a4a62-109">Features of the management pack include:</span></span>  
  
-   <span data-ttu-id="a4a62-110">Analyse l’état des services inclus comme [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], l’Agent SQL, le serveur de rapports, les Services de Notification</span><span class="sxs-lookup"><span data-stu-id="a4a62-110">Monitoring the state of the included services such as [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], SQL Agent, Report Server, Notification Services</span></span>  
  
-   <span data-ttu-id="a4a62-111">Analyse de l’état des bases de données</span><span class="sxs-lookup"><span data-stu-id="a4a62-111">Monitoring the state of databases</span></span>  
  
-   <span data-ttu-id="a4a62-112">Analyse l’espace disponible dans les bases de données, configurables par % ou Mo</span><span class="sxs-lookup"><span data-stu-id="a4a62-112">Monitoring the available space in databases, configurable by % or MB</span></span>  
  
-   <span data-ttu-id="a4a62-113">S’assurer que des bases de données sont correctement configurés.</span><span class="sxs-lookup"><span data-stu-id="a4a62-113">Ensuring databases are configured correctly</span></span>  
  
-   <span data-ttu-id="a4a62-114">Vérifiez les clients peuvent se connecter à la[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4a62-114">Ensure clients can connect to the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="a4a62-115">Surveiller les processus bloqués</span><span class="sxs-lookup"><span data-stu-id="a4a62-115">Monitor blocked processes</span></span>  
  
-   <span data-ttu-id="a4a62-116">Surveiller l’agent a échoué de tâches prend un temps excessif pour exécuter des tâches</span><span class="sxs-lookup"><span data-stu-id="a4a62-116">Watch for failed agent jobs, and jobs taking an excessive time to execute</span></span>  
  
-   <span data-ttu-id="a4a62-117">Surveiller l’intégrité de la réplication et d’alerte en cas d’échec</span><span class="sxs-lookup"><span data-stu-id="a4a62-117">Monitor the health of replication and alert on failures</span></span>  
  
-   <span data-ttu-id="a4a62-118">Surveiller l’état de mise en miroir de base de données</span><span class="sxs-lookup"><span data-stu-id="a4a62-118">Monitor the state of Database Mirroring</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4a62-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a4a62-119">In This Section</span></span>  
  
-   [<span data-ttu-id="a4a62-120">Analyse des travaux de l’Agent SQL Server et les bases de données</span><span class="sxs-lookup"><span data-stu-id="a4a62-120">Monitoring SQL Server Agent Jobs and Databases</span></span>](../technical-guides/monitoring-sql-server-agent-jobs-and-databases.md)  
  
-   [<span data-ttu-id="a4a62-121">Comment marquer les bases de données BizTalk Server pour une analyse personnalisée</span><span class="sxs-lookup"><span data-stu-id="a4a62-121">How to Mark BizTalk Server Databases for Customized Monitoring</span></span>](../technical-guides/how-to-mark-biztalk-server-databases-for-customized-monitoring.md)  
  
-   [<span data-ttu-id="a4a62-122">Surveiller les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a4a62-122">Monitor the BizTalk Server Databases</span></span>](../technical-guides/monitor-the-biztalk-server-databases.md)