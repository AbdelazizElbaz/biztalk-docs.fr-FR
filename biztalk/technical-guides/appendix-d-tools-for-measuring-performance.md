---
title: "Annexe d : des outils pour mesurer les performances | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 024f4a08-f3fd-4786-8549-0da5463c0bb9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 887272c841aacc0eaa85c197854067133166f783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appendix-d-tools-for-measuring-performance"></a>Annexe d : des outils pour mesurer les performances
Cette rubrique décrit les différents outils qui peuvent être utilisés pour analyser et évaluer les performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
## <a name="performance-analysis-of-logs-pal-tool"></a>Outil d’analyse des journaux (PAL) de performances  
 L’outil de publication est utilisé pour générer un rapport basé sur HTML graphiquement graphiques des compteurs de performances importants et génère des alertes lorsque les seuils de ces compteurs sont dépassés. Cette dernière constitue un excellent outil pour identifier les goulots d’étranglement dans un [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] solution afin de faciliter l’affectation des ressources pour optimiser les performances de la solution. Pour plus d’informations sur l’outil performances analyse des journaux (PAL), consultez [http://go.microsoft.com/fwlink/?LinkID=98098](http://go.microsoft.com/fwlink/?LinkID=98098).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="performance-monitor"></a>Analyseur de performances  
 Analyseur de performances fournit un affichage visuel des compteurs de performances Windows intégrés, en temps réel ou comme un moyen pour passer en revue les données d’historique.  
  
## <a name="log-parser"></a>Analyseur de journal  
 Log parser est un outil puissant et flexible qui fournit l’accès de requête universel à des données texte tels que les fichiers journaux, les fichiers XML et fichiers CSV, et sources de données clés sur le système d’exploitation Windows® tels que le journal des événements, le Registre, le système de fichiers et actif Directory®. Analyseur de journal n’est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkID=100882](http://go.microsoft.com/fwlink/?LinkID=100882).  
  
## <a name="relog"></a>Reconnecter  
 L’utilitaire Rejournaliser est utilisé pour extraire les compteurs de performances à partir des journaux créés par l’Analyseur de performances et de convertir les données d’autres formats, tels que les fichiers de texte délimité (texte-TSV), les fichiers texte délimité par des virgules (CSV de texte), des fichiers binaires et les bases de données SQL. Ces données peuvent ensuite être analysées et interrogés à l’aide d’autres outils, tels que de l’Analyseur de journal, pour générer des statistiques pour les indicateurs de performance clés (KPI). L’utilitaire Rejournaliser est fourni avec [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] et les versions ultérieures.  
  
## <a name="loadgen"></a>Outil LoadGen  
 BizTalk LoadGen 2007 est un outil de génération de charge utilisé pour exécuter des performances et des tests de stress sur [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. L’outil Microsoft BizTalk LoadGen 2007 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).  
  
## <a name="visual-studio-team-system-2008-load-testing"></a>Visual Studio Team System 2008 Load Testing  
 Le Visual Studio Team System (VSTS) 2008 fournit un outil de création et exécution de tests de charge. Pour plus d’informations sur l’utilisation des tests de charge, consultez [http://go.microsoft.com/fwlink/?LinkId=141486](http://go.microsoft.com/fwlink/?LinkId=141486).  
  
## <a name="bizunit"></a>BizUnit  
 BizUnit est une infrastructure conçue pour les tests d’automatisés [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solutions. BizUnit est un excellent outil pour le test de bout en bout [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] scénarios. Pour plus d’informations sur BizUnit 3.0, consultez [http://go.microsoft.com/fwlink/?LinkID=85168](http://go.microsoft.com/fwlink/?LinkID=85168).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="iometer"></a>IOMeter  
 IOMeter est un outil open source utilisé pour le disque mesure les performances d’e/s. Pour plus d’informations sur IOMeter, consultez [http://go.microsoft.com/fwlink/?LinkId=122412](http://go.microsoft.com/fwlink/?LinkId=122412).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="biztalk-server-orchestration-profiler"></a>Profileur d’Orchestration de BizTalk Server  
 Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] profileur d’Orchestration est utilisé pour obtenir une vue consolidée de l’orchestration des données de suivi pour une période spécifiée. Cela fournit aux développeurs un aperçu de la façon dont sont traitées les orchestrations et le niveau de couverture de test qui est appliqué. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de profil de l’Orchestration pour identifier les problèmes potentiels avec les exceptions de chemin d’accès de latence et le code en surbrillance longue en cours d’exécution et d’erreur susceptible d’engendrer des formes d’orchestration, qui sont critiques pour le test de performances efficaces. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Orchestration profileur est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkID=102209](http://go.microsoft.com/fwlink/?LinkID=102209).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="pathping"></a>Pathping  
 PathPing fournit des informations sur la perte de données à un ou plusieurs sauts de routeur sur le chemin d’un ordinateur hôte cible. Pour ce faire, pathping envoie des paquets de contrôle Message ICMP (Internet Protocol) à chaque routeur situé dans le chemin d’accès. Pathping.exe est disponible avec toutes les versions de Windows depuis Windows 2000 Server.  
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>Outils SQL Server pour la surveillance et le réglage des performances  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]fournit plusieurs outils pour surveiller les événements de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et de paramétrer la conception physique de la base de données. Ces outils sont décrits dans la rubrique « Outils de surveillance et réglage des performances » dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?LinkId=146357](http://go.microsoft.com/fwlink/?LinkId=146357). Pour plus d’informations sur les outils spécifiques utilisés pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] analyse et de réglage des performances sont fourni ci-dessous :  
  
### <a name="sql-profiler"></a>SQL Profiler  
 Le Générateur de profils Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permet de capturer les instructions Transact-SQL envoyées au serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et les ensembles de résultats du [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provenant de ces instructions. Étant donné que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est étroitement intégré à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], l’analyse d’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] trace de profil peut être un outil utile pour analyser les problèmes qui peuvent se produire dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de la lecture et écriture à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données. Pour plus d’informations sur l’utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, consultez « À l’aide de SQL Server Profiler » dans le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?linkid=104423](http://go.microsoft.com/fwlink/?linkid=104423).  
  
> [!IMPORTANT]  
>  Il existe une charge considérable associée en cours d’exécution du Générateur de profils SQL. Par conséquent, Générateur de profils SQL est idéale pour une utilisation dans des environnements de test ou de développement. Si vous utilisez SQL Profiler pour résoudre les problèmes d’un environnement de production, tenez compte des coûts de traitement associés et limiter l’utilisation du Générateur de profils SQL en conséquence.  
  
> [!NOTE]  
>  Lorsque vous utilisez SQL Profiler pour capturer les instructions Transact-SQL, configurer le Générateur de profils SQL pour générer la sortie vers un lecteur local au lieu d’un lecteur situé sur un partage réseau distant ou un autre périphérique lente, par exemple, une clé de mémoire USB locale.  
  
### <a name="sql-trace"></a>Trace SQL  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Fournit des procédures stockées système Transact-SQL pour créer des traces sur une instance du moteur de base de données SQL Server. Ces procédures stockées système peuvent servir à partir de vos propres applications pour créer des traces manuellement au lieu d’utiliser le Générateur de profils SQL Server. Vous pouvez ainsi écrire des applications personnalisées spécifiques des besoins de votre entreprise. Pour plus d’informations sur l’utilisation de Trace SQL, consultez « Présentation SQL Trace dans le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?LinkId=146354](http://go.microsoft.com/fwlink/?LinkId=146354).  
  
> [!NOTE]  
>  Lorsque vous utilisez Trace SQL pour capturer les instructions Transact-SQL, configurer la Trace SQL pour générer la sortie vers un lecteur local plutôt que sur un lecteur situé sur un partage réseau distant ou un autre périphérique lent, tel qu’un lecteur flash USB.  
  
### <a name="sql-activity-monitor"></a>Moniteur d’activité SQL  
 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]Moniteur d’activité fournit des informations sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] processus et la façon dont ces processus affectent l’instance actuelle de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations sur [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] moniteur d’activité, consultez « Moniteur d’activité » dans le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?LinkId=146355](http://go.microsoft.com/fwlink/?LinkId=146355). Pour plus d’informations sur la façon d’ouvrir le moniteur d’activité à partir de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, consultez « Comment : ouvrir le moniteur d’activité ([!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio) dans le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?LinkId=135094](http://go.microsoft.com/fwlink/?LinkId=135094).  
  
### <a name="sql-server-2008-data-collection"></a>Collecte de données SQL Server 2008  
 [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] fournit un collecteur de données qui vous permet d'obtenir et d'enregistrer des données rassemblées à partir de plusieurs sources. Le collecteur de données vous permet d'utiliser des conteneurs de collecte de données qui vous permettent de déterminer l'étendue et la fréquence de la collecte de données sur ordinateur qui exécute [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]. Pour plus d’informations sur l’implémentation de [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] collecte de données, consultez « Collecte des données » dans le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] la documentation en ligne à [http://go.microsoft.com/fwlink/?LinkId=146356](http://go.microsoft.com/fwlink/?LinkId=146356).  
  
### <a name="sql-server-2005-performance-dashboard-reports"></a>Rapports de tableau de bord de surveillance des performances de SQL Server 2005  
 [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)]Les rapports de tableau de bord performances sont utilisés pour surveiller et résoudre les problèmes de performances sur votre [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] serveur de base de données. Pour plus d’informations sur [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] rapports du tableau de bord de performances, consultez [http://go.microsoft.com/fwlink/?LinkID=118673](http://go.microsoft.com/fwlink/?LinkID=118673).  
  
### <a name="sqlio"></a>SQLIO  
 L’outil SQLIO a été développé par Microsoft pour évaluer la capacité d’e/s d’une configuration donnée. Comme l’indique le nom de l’outil, SQLIO est un outil précieux pour mesurer l’impact du système de fichiers d’e/s sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performances. SQLIO peut être téléchargé à partir de [http://go.microsoft.com/fwlink/?LinkId=115176](http://go.microsoft.com/fwlink/?LinkId=115176).