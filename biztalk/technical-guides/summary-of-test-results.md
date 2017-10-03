---
title: "Résumé des résultats des tests | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d95fbaa6-0e07-4086-bea2-0577d39ae7cd
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2eebcdef457716cab9ad61415bf3fe46db301b55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="summary-of-test-results"></a>Résumé des résultats des tests
Cette rubrique récapitule les résultats dans les scénarios de test.  
  
## <a name="summary-of-test-results"></a>Résumé des résultats des tests  
 Le [test des performances de BizTalk Server virtualisation](../technical-guides/testing-biztalk-server-virtualization-performance.md) de ce guide décrit l’application de test utilisé et la configuration des différents [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnements sur lesquels l’application de test a été exécutée. Les tests ont été effectués pour comparer les performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  /  [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] environnement en cours d’exécution sur du matériel physique pour les performances de l’environnement en cours d’exécution sur des ordinateurs virtuels Hyper-V. Indicateurs de Performance clés (KPI) mesurée au cours des tests inclus comme suit.  
  
1.  Débit des messages est mesuré sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs.  
  
2.  Latence requête-réponse, mesurée sur le client de Test Visual Studio qui a envoyé des demandes synchrones à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
3.  Utilisation du processeur et requêtes de lots par seconde observées sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
4.  Débit du réseau observées sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs.  
  
5.  Mémoire disponible pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs.  
  
### <a name="throughput-comparison-sample-results"></a>Exemples de comparaison de débit résultats  
 Avec tous les autres facteurs étant égaux, débit de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution telle que mesurée par le « BizTalk : messagerie/Documents traités par seconde » compteur Perfmon comprise 67 % % 94.3 du débit réalisable lorsque à la fois le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les ordinateurs et les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs dans l’environnement ont été installés sur du matériel physique.  
  
 Lorsque le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs dans l’environnement ont été installés sur les ordinateurs virtuels Hyper-V, a été observé de réduire considérablement le débit de la solution, cette réduction de débit peut être attribuée à la surcharge du processeur requise par Hyper-V.  
  
### <a name="latency-comparison-sample-results"></a>Exemples de comparaison de latence résultats  
 Avec tous les autres facteurs étant égaux, lorsque les ordinateurs BizTalk Server dans l’environnement BizTalk Server ont été exécutées sur des machines virtuelles de Hyper-V, la latence de la solution BizTalk Server, telle que mesurée par le « BizTalk : messagerie requête-réponse/latence latence (s ) « compteur Perfmon comprise 66.9 % et % 94.3 de la latence atteignables lorsque les ordinateurs BizTalk Server dans l’environnement BizTalk Server ont été installés sur du matériel physique.  
  
 Lorsque le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs dans l’environnement ont été installés sur les ordinateurs virtuels Hyper-V, a été observé de réduire considérablement le débit de la solution, cette réduction de débit peut être attribuée à la surcharge du processeur requise par Hyper-V sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines virtuelles.  
  
### <a name="sql-server-processor-utilization-and-batch-requests-per-second-sample-results"></a>L’utilisation du processeur SQL Server et les requêtes de lots par le deuxième exemple de résultats  
 L’utilisation du processeur de SQL Server telle que mesurée par \SQL\Processor(_Total)\\compteur % temps processeur était environ le même sur tous les environnements de test, allant de faible niveau de 88 % et 90.1 %. Il existe toutefois une différence significative entre les \SQL Server:SQL Statistics\Batch mesurée de demandes par seconde sur l’environnement consolidé (4520) et le \SQL Server:SQL Statistics\Batch exprimé de demandes par seconde sur l’environnement physique (6350). Le \SQL Server:SQL Statistics\Batch compteur de moniteur de performances de requêtes/s constitue un bon indicateur de la quantité de travail est effectuée par SQL Server. La réduction de requêtes de lots/s lorsque SQL Server est en cours d’exécution dans un environnement Hyper-V peut être attribuée à la surcharge du processeur requise par Hyper-V.  
  
### <a name="biztalk-server-and-sql-server-network-throughput-sample-results"></a>BizTalk Server et SQL Server réseau débit exemples de résultats  
 Débit du réseau pour BizTalk Server s’exécutant sur des ordinateurs virtuels Hyper-V a été observé à la plage d’environ 70 à 96 % du débit du réseau effectué sur les serveurs BizTalk physique, en fonction de l’environnement de test particulière. Débit du réseau pour SQL Server s’exécutant sur un ordinateur virtuel Hyper-V a été observé à la plage d’environ 68 à 81 % du débit du réseau effectué sur le serveur SQL physique, à nouveau en fonction de l’environnement de test particulière. Le delta dans le débit observées sur le réseau peut être attribué pour les besoins en ressources de l’hyperviseur Hyper-V.  
  
### <a name="biztalk-server-and-sql-server-available-memory-sample-results"></a>BizTalk Server et SQL Server résultats d’exemple de mémoire disponible  
 Mémoire totale disponible pour SQL Server et BizTalk Server, telle que mesurée par le compteur du moniteur performances \Memory\Available en mégaoctets était assez cohérente pour tous les scénarios de test.