---
title: "Offrant une haute disponibilité pour les bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- databases, architecture
- SQL Server, clustering
- servers, clustering
- databases, high availability
- architecture
- databases, clustering
- BizTalk Server, architecture
- Windows clustering
- high availability, databases
- clustering, databases
- data, persistence
- SQL Server Analysis Services
ms.assetid: 47fbc402-9e46-41dd-bc12-d1cde1982576
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3648a8f6d48bbfd6cf67995e1d314511b70db7bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="providing-high-availability-for-biztalk-server-databases"></a><span data-ttu-id="85f30-102">Configuration de la haute disponibilité pour les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="85f30-102">Providing High Availability for BizTalk Server Databases</span></span>
<span data-ttu-id="85f30-103">En matière de persistance des données, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appuie en grande partie sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85f30-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] relies heavily on [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] for data persistence.</span></span> <span data-ttu-id="85f30-104">Tous les autres composants et hôtes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] jouent un rôle précis dans le processus d'intégration d'applications d'entreprise hétérogènes (par exemple : la réception, le traitement ou le routage des messages) tandis que l'ordinateur hébergeant les bases de données enregistre ces travaux pour les conserver sur le disque.</span><span class="sxs-lookup"><span data-stu-id="85f30-104">All other components and hosts in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] have specific roles in the process of integrating disparate business applications (for example, receiving, processing, or routing messages), but the database computer captures this work and persists it to disk.</span></span>  
  
 <span data-ttu-id="85f30-105">Pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, utilisez le Clustering de basculement Windows Server pour configurer deux ordinateurs de la base de données qui exécutent SQL Server pour créer un cluster de serveurs.</span><span class="sxs-lookup"><span data-stu-id="85f30-105">To provide high availability for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, use Windows Server Failover Clustering to configure two database computers that are running SQL Server to create a server cluster.</span></span> <span data-ttu-id="85f30-106">Ce cluster vous garantit la redondance et la tolérance de pannes nécessaires aux bases de données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="85f30-106">Server clustering provides redundancy and fault tolerance for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="85f30-107">Dans un cluster à équilibrage de charge, plusieurs ordinateurs forment un groupe et fonctionnent ensemble dans le but d'augmenter la disponibilité et l'évolutivité de l'installation. En revanche, dans un cluster de serveurs, deux ordinateurs dédiés aux bases de données sont configurés sur un modèle actif/passif où l'une des machines fournit les ressources de sauvegarde à l'autre.</span><span class="sxs-lookup"><span data-stu-id="85f30-107">Unlike load-balanced clustering, where a group of computers functions together to increase availability and scalability, server clustering typically involves a pair of database computers in an active/passive configuration so that one computer provides backup resources for the other.</span></span>  
  
 <span data-ttu-id="85f30-108">Le schéma suivant représente un niveau de base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible grâce à un cluster de serveurs actif/passif.</span><span class="sxs-lookup"><span data-stu-id="85f30-108">The following figure shows a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database tier with high availability through active/passive server clustering.</span></span>  
  
 <span data-ttu-id="85f30-109">![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span><span class="sxs-lookup"><span data-stu-id="85f30-109">![BizTalk Server Database Tier](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")</span></span>  
  
 <span data-ttu-id="85f30-110">Si la machine de base de données active rencontre des problèmes ou s'arrête, la machine passive devient active et reprend le contrôle des ressources de base de données jusqu'à ce que la machine défaillante soit de nouveau opérationnelle.</span><span class="sxs-lookup"><span data-stu-id="85f30-110">If the active database computer encounters errors or fails, the passive computer becomes active and assumes control over the database resources until the failed computer is repaired.</span></span> <span data-ttu-id="85f30-111">Le service de base de données bascule vers l'ordinateur actif où une récupération des connexions de données a lieu de manière à ce que l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] continue à fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="85f30-111">The database service fails over and restores data connections to the new active computer and enables the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application to continue functioning.</span></span>  
  
 <span data-ttu-id="85f30-112">Pour plus d’informations sur les bases de données qui sont installés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [bases de données BizTalk Server](../core/databases-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="85f30-112">For information about the databases that are installed by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Databases in BizTalk Server](../core/databases-in-biztalk-server.md).</span></span>  
  
 <span data-ttu-id="85f30-113">Pour plus d’informations sur la sauvegarde votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md).</span><span class="sxs-lookup"><span data-stu-id="85f30-113">For information about backing up your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85f30-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="85f30-114">In This Section</span></span>  
  
-   [<span data-ttu-id="85f30-115">Bases de données à grande échelle</span><span class="sxs-lookup"><span data-stu-id="85f30-115">Scaled-Out Databases</span></span>](../core/scaled-out-databases.md)  
  
-   [<span data-ttu-id="85f30-116">Mise en cluster les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="85f30-116">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)  
  
-   [<span data-ttu-id="85f30-117">Comportement des Instances d’hôte BizTalk Server au cours de basculement SQL Server</span><span class="sxs-lookup"><span data-stu-id="85f30-117">Behavior of BizTalk Server Host Instances during SQL Server Failover</span></span>](../core/behavior-of-biztalk-server-host-instances-during-sql-server-failover.md)  
  
-   [<span data-ttu-id="85f30-118">Base de données SQL Server mise en miroir, le service VSS et AlwaysOn</span><span class="sxs-lookup"><span data-stu-id="85f30-118">SQL Server database mirroring, Volume Shadow Copy service and AlwaysOn</span></span>](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)  
  
## <a name="see-also"></a><span data-ttu-id="85f30-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85f30-119">See Also</span></span>  
 <span data-ttu-id="85f30-120">[Offrant une haute disponibilité pour les hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="85f30-120">[Providing High Availability for BizTalk Hosts](../core/providing-high-availability-for-biztalk-hosts.md) </span></span>  
 [<span data-ttu-id="85f30-121">Exemples de scénarios de haute disponibilité BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="85f30-121">Sample BizTalk Server High Availability Scenarios</span></span>](../core/sample-biztalk-server-high-availability-scenarios.md)