---
title: Test des performances de la virtualisation de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09121b1-cdd6-4c01-9d69-0f1923464f0e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cec992ab489c63f68ac4d77652209e65eff258a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testing-biztalk-server-virtualization-performance"></a>Test des performances de la virtualisation de BizTalk Server
Les scénarios de test de performances décrits dans ce guide ont été déployés sur des ordinateurs physiques dans un laboratoire de test de Microsoft, et ensuite le même test de charge a été effectué sur chaque architecture système distinctes. Le système d’exploitation hôte sur chaque ordinateur physique a été d’une installation complète de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] entreprise, Édition 64 bits, avec le rôle de serveur Hyper-V installé. Les ordinateurs virtuels utilisés pour le test [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ont été configurés avec [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] entreprise, Édition 64 bits en tant que le système d’exploitation invité. L’ordinateur virtuel utilisé pour le test [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] a été configuré avec [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] entreprise, Édition 64 bits en tant que le système d’exploitation invité. Les scénarios de test de méthodes de test, résultats des tests de performances et une analyse ultérieure ont été utilisées pour formuler une série de meilleures pratiques et conseils pour la conception, l’implémentation, et l’optimisation virtualisés [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Scénario de test 1 : Ligne de base** : le premier scénario a été conçu pour établir des performances de ligne de base d’un environnement BizTalk Server en cours d’exécution sur un matériel physique uniquement. Pour ce scénario BizTalk Server et SQL Server a été installé et exécuté sur un matériel physique uniquement.  
  
-   **Scénario de test de 2 : BizTalk Server/physique serveur SQL Server virtuel** -le deuxième scénario a été conçu pour déterminer l’impact sur les performances de BizTalk Server d’hébergement sur plusieurs machines virtuelles d’invité sur le même serveur physique. Résultats des tests provenant de plusieurs machines virtuelles configurations ont été comparées à un traitement de l’ordinateur physique avec le même nombre de processeurs logiques que le nombre total dispersée dans tous les ordinateurs virtuels.  
  
-   **Scénario de test 3 : Virtuel BizTalk Server/virtuel SQL Server sur des hôtes Hyper-V physiques distincts** -le troisième scénario a été élaboré pour déterminer l’impact sur les performances de l’exécution de BizTalk Server et SQL Server dans un environnement virtualisé. Les tests ont été effectuées à l’aide de BizTalk Server s’exécutant sur des ordinateurs virtuels Hyper-V avec les bases de données BizTalk hébergés sur un [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] instance en cours d’exécution sur un ordinateur virtuel Hyper-V. Pour ce scénario, les machines virtuelles BizTalk Server et les machines virtuelles SQL Server étaient hébergés sur des hôtes Hyper-V physiques distincts.  
  
-   **Test scénario 4 : Consolidation de serveurs-consolidation complète BizTalk groupe, y compris SQL sur un serveur physique sur Hyper-V** – dans le scénario, toutes les machines virtuelles (VM) nécessaires pour exécuter l’application de test sont hébergés sur un seul serveur physique. L’objectif de ce scénario consiste à déterminer les coûts de performances de l’hébergement [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] et [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] machines virtuelles dans un environnement consolidé.  
  
 Cette section fournit une vue d’ensemble de l’application de test et de l’architecture de serveur utilisée pour chaque scénario et présente également les indicateurs de performance clés (KPI) observés pendant le test.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du scénario de test](../technical-guides/test-scenario-overview.md)  
  
-   [Architecture de serveur de scénario de test](../technical-guides/test-scenario-server-architecture.md)  
  
-   [Résultats des tests : Indicateurs de Performance clés de BizTalk Server](../technical-guides/test-results-biztalk-server-key-performance-indicators.md)  
  
-   [Résultats des tests : Indicateurs de Performance clés SQL Server](../technical-guides/test-results-sql-server-key-performance-indicators.md)  
  
-   [Résultats des tests : Indicateurs de Performance clés de la mise en réseau](../technical-guides/test-results-networking-key-performance-indicators.md)  
  
-   [Résultats des tests : Indicateurs de Performance clés de mémoire](../technical-guides/test-results-memory-key-performance-indicators.md)  
  
-   [Résumé des résultats des tests](../technical-guides/summary-of-test-results.md)