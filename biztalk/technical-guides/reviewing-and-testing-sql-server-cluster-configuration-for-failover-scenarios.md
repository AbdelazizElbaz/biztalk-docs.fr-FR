---
title: "Revue de test SQL Server de Configuration du Cluster pour les scénarios de basculement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5dbeb383-5b38-4467-acf8-2a5b244e5fa9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8e7bed17960700aee84631801e3e26cb05b25c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios"></a><span data-ttu-id="49a46-102">Examen et le test de Configuration du Cluster SQL Server pour les scénarios de basculement</span><span class="sxs-lookup"><span data-stu-id="49a46-102">Reviewing and Testing SQL Server Cluster Configuration for Failover Scenarios</span></span>
<span data-ttu-id="49a46-103">Le Clustering Windows et SQL Server permettent d’exécuter SQL Server en mode actif/actif, où chaque nœud du cluster est en cours d’exécution et de « actifs » instances de SQL Server une ou plusieurs.</span><span class="sxs-lookup"><span data-stu-id="49a46-103">Windows Clustering and SQL Server allow you to run SQL Server in Active/Active mode where each node of the cluster is “active” and running one or more SQL Server instances.</span></span> <span data-ttu-id="49a46-104">Cela vous permettrait, par exemple, pour que la base de données MessageBox sur un nœud et tous les autres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sur l’autre nœud.</span><span class="sxs-lookup"><span data-stu-id="49a46-104">This would allow you, for example, to have the MessageBox database on one node and all other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on the other node.</span></span> <span data-ttu-id="49a46-105">Cela vous permet d’optimiser l’utilisation de matériel de cluster.</span><span class="sxs-lookup"><span data-stu-id="49a46-105">This allows you to maximize cluster hardware usage.</span></span>  
  
 <span data-ttu-id="49a46-106">Toutefois, si vous utilisez cette configuration, vous devez vérifier que chaque nœud peut gérer simultanément la charge de toutes les instances de SQL Server lors d’un basculement de nœud de cluster SQL Server.</span><span class="sxs-lookup"><span data-stu-id="49a46-106">If you use this configuration, however, you must verify that each node can simultaneously handle the load of all SQL Server instances during a SQL Server cluster node failover.</span></span>  
  
## <a name="evaluating-failover-for-an-activeactive-cluster"></a><span data-ttu-id="49a46-107">L’évaluation de basculement pour un Cluster actif/actif</span><span class="sxs-lookup"><span data-stu-id="49a46-107">Evaluating Failover for an Active/Active Cluster</span></span>  
 <span data-ttu-id="49a46-108">Considérations lors de la vérification qu’un seul nœud peut gérer la charge de toutes les instances de SQL Server en cas de basculement de nœud de cluster de SQL Server sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="49a46-108">Considerations when verifying that a single node can handle the load of all SQL Server instances in the event of a SQL Server cluster node failover include:</span></span>  
  
-   <span data-ttu-id="49a46-109">Le nœud de basculement dispose des ressources processeur suffisantes ?</span><span class="sxs-lookup"><span data-stu-id="49a46-109">Does the failover node have sufficient CPU resources?</span></span>  
  
-   <span data-ttu-id="49a46-110">Le nœud de basculement dispose d’une mémoire suffisante ?</span><span class="sxs-lookup"><span data-stu-id="49a46-110">Does the failover node have sufficient memory?</span></span>  
  
-   <span data-ttu-id="49a46-111">Existe-t-il une bande passante réseau suffisante ?</span><span class="sxs-lookup"><span data-stu-id="49a46-111">Is there sufficient network bandwidth?</span></span>  
  
-   <span data-ttu-id="49a46-112">Le nœud de basculement peut gérer la contention d’e/s disque accrue ?</span><span class="sxs-lookup"><span data-stu-id="49a46-112">Can the failover node handle the increased disk I/O contention?</span></span>  
  
 <span data-ttu-id="49a46-113">Les scénarios suivants doivent être évaluées lors du test de basculement :</span><span class="sxs-lookup"><span data-stu-id="49a46-113">The following scenarios should be evaluated when testing failover:</span></span>  
  
-   <span data-ttu-id="49a46-114">Panne d’alimentation sur le serveur actif</span><span class="sxs-lookup"><span data-stu-id="49a46-114">Power failure on the active server</span></span>  
  
-   <span data-ttu-id="49a46-115">Panne d’alimentation sur le serveur passif</span><span class="sxs-lookup"><span data-stu-id="49a46-115">Power failure on the passive server</span></span>  
  
-   <span data-ttu-id="49a46-116">Perte de connexion de disque</span><span class="sxs-lookup"><span data-stu-id="49a46-116">Loss of disk connection</span></span>  
  
-   <span data-ttu-id="49a46-117">Interrompu la connexion au réseau public sur le nœud actif</span><span class="sxs-lookup"><span data-stu-id="49a46-117">Broken public network connection on the Active node</span></span>  
  
-   <span data-ttu-id="49a46-118">Rompue de connexion de réseau privé sur le nœud actif</span><span class="sxs-lookup"><span data-stu-id="49a46-118">Broken private network connection on the Active node</span></span>  
  
-   <span data-ttu-id="49a46-119">Interrompu la connexion au réseau public sur le nœud passif</span><span class="sxs-lookup"><span data-stu-id="49a46-119">Broken public network connection on the Passive node</span></span>  
  
-   <span data-ttu-id="49a46-120">Rompue de connexion de réseau privé sur le nœud passif</span><span class="sxs-lookup"><span data-stu-id="49a46-120">Broken private network connection on the Passive node</span></span>  
  
-   <span data-ttu-id="49a46-121">Service SQL Server ayant échoué</span><span class="sxs-lookup"><span data-stu-id="49a46-121">Failed SQL Server service</span></span>  
  
-   <span data-ttu-id="49a46-122">Service de l’Agent SQL Server ayant échoué</span><span class="sxs-lookup"><span data-stu-id="49a46-122">Failed SQL Server Agent service</span></span>  
  
## <a name="using-an-activeactivepassive-cluster"></a><span data-ttu-id="49a46-123">À l’aide d’un Cluster actif/actif/passif</span><span class="sxs-lookup"><span data-stu-id="49a46-123">Using an Active/Active/Passive Cluster</span></span>  
 <span data-ttu-id="49a46-124">Si vous déterminez qu’un nœud ne peut pas gérer toutes les instances de SQL Server dans un scénario de basculement, une alternative consiste à utiliser un modèle de clustering actif/actif/passif.</span><span class="sxs-lookup"><span data-stu-id="49a46-124">If you determine that one node cannot handle all SQL Server instances in a failover scenario, an alternative is to use an Active/Active/Passive clustering model.</span></span> <span data-ttu-id="49a46-125">Le modèle de clustering actif/actif/passif augmente considérablement la probabilité qu’il y aura toujours un nœud passif disponibles pour les scénarios de basculement.</span><span class="sxs-lookup"><span data-stu-id="49a46-125">The Active/Active/Passive clustering model greatly increases the likelihood that there will always be one Passive node available for failover scenarios.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a46-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49a46-126">See Also</span></span>  
 [<span data-ttu-id="49a46-127">Liste de vérification : Configuration de SQL Server</span><span class="sxs-lookup"><span data-stu-id="49a46-127">Checklist: Configuring SQL Server</span></span>](~/technical-guides/checklist-configuring-sql-server.md)