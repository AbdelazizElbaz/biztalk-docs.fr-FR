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
# <a name="reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios"></a>Examen et le test de Configuration du Cluster SQL Server pour les scénarios de basculement
Le Clustering Windows et SQL Server permettent d’exécuter SQL Server en mode actif/actif, où chaque nœud du cluster est en cours d’exécution et de « actifs » instances de SQL Server une ou plusieurs. Cela vous permettrait, par exemple, pour que la base de données MessageBox sur un nœud et tous les autres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sur l’autre nœud. Cela vous permet d’optimiser l’utilisation de matériel de cluster.  
  
 Toutefois, si vous utilisez cette configuration, vous devez vérifier que chaque nœud peut gérer simultanément la charge de toutes les instances de SQL Server lors d’un basculement de nœud de cluster SQL Server.  
  
## <a name="evaluating-failover-for-an-activeactive-cluster"></a>L’évaluation de basculement pour un Cluster actif/actif  
 Considérations lors de la vérification qu’un seul nœud peut gérer la charge de toutes les instances de SQL Server en cas de basculement de nœud de cluster de SQL Server sont les suivantes :  
  
-   Le nœud de basculement dispose des ressources processeur suffisantes ?  
  
-   Le nœud de basculement dispose d’une mémoire suffisante ?  
  
-   Existe-t-il une bande passante réseau suffisante ?  
  
-   Le nœud de basculement peut gérer la contention d’e/s disque accrue ?  
  
 Les scénarios suivants doivent être évaluées lors du test de basculement :  
  
-   Panne d’alimentation sur le serveur actif  
  
-   Panne d’alimentation sur le serveur passif  
  
-   Perte de connexion de disque  
  
-   Interrompu la connexion au réseau public sur le nœud actif  
  
-   Rompue de connexion de réseau privé sur le nœud actif  
  
-   Interrompu la connexion au réseau public sur le nœud passif  
  
-   Rompue de connexion de réseau privé sur le nœud passif  
  
-   Service SQL Server ayant échoué  
  
-   Service de l’Agent SQL Server ayant échoué  
  
## <a name="using-an-activeactivepassive-cluster"></a>À l’aide d’un Cluster actif/actif/passif  
 Si vous déterminez qu’un nœud ne peut pas gérer toutes les instances de SQL Server dans un scénario de basculement, une alternative consiste à utiliser un modèle de clustering actif/actif/passif. Le modèle de clustering actif/actif/passif augmente considérablement la probabilité qu’il y aura toujours un nœud passif disponibles pour les scénarios de basculement.  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de SQL Server](~/technical-guides/checklist-configuring-sql-server.md)