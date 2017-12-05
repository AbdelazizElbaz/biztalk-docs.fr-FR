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
ms.openlocfilehash: 8d45567918cebd18bfea7bf30f31b299f6bed02d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="testing-biztalk-server-virtualization-performance"></a>Test des performances de la virtualisation de BizTalk Server
Les scénarios de test de performances décrits dans ce guide ont été déployés sur des ordinateurs physiques dans un laboratoire de test de Microsoft, et ensuite le même test de charge a été effectué sur chaque architecture système distinctes. Le système d’exploitation hôte sur chaque ordinateur physique a été d’une installation complète de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] entreprise, Édition 64 bits, avec le rôle de serveur Hyper-V installé. Les ordinateurs virtuels utilisés pour le test de BizTalk Server ont été configurés avec [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] entreprise, Édition 64 bits en tant que le système d’exploitation invité. L’ordinateur virtuel utilisé pour le test de SQL Server a été configuré avec [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] entreprise, Édition 64 bits en tant que le système d’exploitation invité. Les scénarios de test de méthodes de test, résultats des tests de performances et une analyse ultérieure ont été utilisées pour formuler une série de meilleures pratiques et conseils pour la conception, l’implémentation, et l’optimisation virtualisés [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Scénario de test 1 : Ligne de base** : le premier scénario a été conçu pour établir des performances de ligne de base d’un environnement BizTalk Server en cours d’exécution sur un matériel physique uniquement. Pour ce scénario BizTalk Server et SQL Server a été installé et exécuté sur un matériel physique uniquement.  
  
-   **Scénario de test de 2 : BizTalk Server/physique serveur SQL Server virtuel** -le deuxième scénario a été conçu pour déterminer l’impact sur les performances de BizTalk Server d’hébergement sur plusieurs machines virtuelles d’invité sur le même serveur physique. Résultats des tests provenant de plusieurs machines virtuelles configurations ont été comparées à un traitement de l’ordinateur physique avec le même nombre de processeurs logiques que le nombre total dispersée dans tous les ordinateurs virtuels.  
  
-   **Scénario de test 3 : Virtuel BizTalk Server/virtuel SQL Server sur des hôtes Hyper-V physiques distincts** -le troisième scénario a été élaboré pour déterminer l’impact sur les performances de l’exécution de BizTalk Server et SQL Server dans un environnement virtualisé. Les tests ont été effectuées à l’aide de BizTalk Server s’exécutant sur des ordinateurs virtuels Hyper-V avec les bases de données BizTalk hébergés sur une instance de SQL Server s’exécutant sur un ordinateur virtuel Hyper-V. Pour ce scénario, les machines virtuelles BizTalk Server et les machines virtuelles SQL Server étaient hébergés sur des hôtes Hyper-V physiques distincts.  
  
-   **Test scénario 4 : Consolidation de serveurs-consolidation complète BizTalk groupe, y compris SQL sur un serveur physique sur Hyper-V** – dans le scénario, toutes les machines virtuelles (VM) nécessaires pour exécuter l’application de test sont hébergés sur un seul serveur physique. L’objectif de ce scénario est de déterminer les coûts de performances de SQL Server et les machines virtuelles de BizTalk Server dans un environnement consolidé d’hébergement.  
  
 Cette section fournit une vue d’ensemble de l’application de test et de l’architecture de serveur utilisée pour chaque scénario et présente également les indicateurs de performance clés (KPI) observés pendant le test.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue d’ensemble du scénario de test](../technical-guides/test-scenario-overview.md)  
  
-   [Architecture du serveur du scénario de test](../technical-guides/test-scenario-server-architecture.md)  
  
-   [Résultats des tests : Indicateurs de performances clés de BizTalk Server](../technical-guides/test-results-biztalk-server-key-performance-indicators.md)  
  
-   [Résultats des tests : Indicateurs de performances clés de SQL Server](../technical-guides/test-results-sql-server-key-performance-indicators.md)  
  
-   [Résultats des tests : Indicateurs de performances clés du réseau](../technical-guides/test-results-networking-key-performance-indicators.md)  
  
-   [Résultats des tests : Indicateurs de performances clés de la mémoire](../technical-guides/test-results-memory-key-performance-indicators.md)  
  
-   [Récapitulatif des résultats des tests](../technical-guides/summary-of-test-results.md)