---
title: Outils de performances | Documents Microsoft
description: "Examiner les problèmes de performances de BizTalk Server à l’aide de BizUnit IOMeter, Orchestration du Générateur de profils, analyseur de journal, LoadGen, outils et SQL"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d26c17a-3eb9-41a5-b0dc-31b974bf3d9b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96bc63c4473d1a48b65024d4e9f7ee67bbb1d722
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="performance-tools"></a>Outils de performances
Cette rubrique fournit des informations sur les outils que vous pouvez utiliser pour évaluer les performances d’une solution BizTalk Server. Les outils décrits dans cette rubrique ont des objectifs différents ; Certains sont conçus pour évaluer les performances de bout en bout alors que d’autres se concentrent sur l’évaluation des performances d’un aspect particulier d’une solution BizTalk Server.  
 
## <a name="bizunit-and-bizunit-designer"></a>BizUnit et BizUnit Concepteur  
 BizUnit est une infrastructure conçue pour les tests automatisés de solutions BizTalk. BizUnit est un excellent outil pour tester les scénarios de bout en bout pour BizTalk Server. Exécution de tests automatisés de solutions BizTalk avec BizUnit est le principal objectif de la [mise en œuvre des tests automatisés](../technical-guides/implementing-automated-testing.md) section de ce guide. Consultez [BizUnit](https://github.com/BizUnit/BizUnit).
  
 Le Concepteur de BizUnit est une interface utilisateur graphique qui permet de créer rapidement des cas de test BizUnit qui peut être utilisé pour le test unitaire ou test des applications distribuées du système. L’outil est disponible à l’adresse [BizUnit concepteur](http://go.microsoft.com/fwlink/?LinkID=117917).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="iometer"></a>IOMeter  
 IOMeter est un outil open source utilisé pour le disque mesure les performances d’e/s. Consultez [http://www.iometer.org](http://www.iometer.org/).
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="log-parser"></a>Analyseur de journal  
 Log parser est un outil puissant et flexible qui fournit l’accès de requête universel à des données texte tels que les fichiers journaux, les fichiers XML et fichiers CSV, et sources de données clés sur le système d’exploitation Windows® tels que le journal des événements, le Registre, le système de fichiers et actif Directory®. Télécharger [connecter analyseur](https://www.microsoft.com/download/details.aspx?id=24659).
  
## <a name="microsoft-biztalk-loadgen"></a>Microsoft BizTalk LoadGen  
 BizTalk LoadGen est un outil de génération de charge utilisé pour exécuter des tests de contrainte et de performances par rapport à BizTalk Server. Télécharger [BizTalk LoadGen 2007 outils](https://www.microsoft.com/download/details.aspx?id=14925).
  
## <a name="pathping"></a>Pathping  
 PathPing fournit des informations sur la perte de données à un ou plusieurs sauts de routeur sur le chemin d’un ordinateur hôte cible. Pour ce faire, pathping envoie des paquets de contrôle Message ICMP (Internet Protocol) à chaque routeur situé dans le chemin d’accès. Pathping.exe est disponible avec toutes les versions de Windows depuis Windows 2000 Server.  
  
## <a name="performance-analysis-of-logs-pal"></a>Analyse des performances des journaux (PAL)  
 L’outil de publication est utilisé pour générer un rapport basé sur HTML graphiquement graphiques des compteurs de performances importants et génère des alertes lorsque les seuils de ces compteurs sont dépassés. Cette dernière constitue un excellent outil pour identifier les goulots d’étranglement dans une solution BizTalk Server afin de faciliter l’affectation des ressources pour optimiser les performances de la solution.  
  
 Pour plus d’informations sur l’outil performances analyse des journaux (PAL), consultez [outil de performances analyse des journaux (PAL)](https://github.com/clinthuffman/PAL).
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="performance-monitor"></a>Analyseur de performances  
 Analyseur de performances fournit un affichage visuel des compteurs de performances Windows intégrés, en temps réel ou comme un moyen pour passer en revue les données d’historique.  
  
## <a name="relog"></a>Reconnecter  
 L’utilitaire Rejournaliser est utilisé pour extraire les compteurs de performances à partir des journaux créés par l’Analyseur de performances et de convertir les données d’autres formats, tels que les fichiers de texte délimité (texte-TSV), les fichiers texte délimité par des virgules (CSV de texte), des fichiers binaires et les bases de données SQL. Ces données peuvent ensuite être analysées et interrogés à l’aide d’autres outils, tels que de l’Analyseur de journal, pour générer des statistiques pour les indicateurs de performance clés (KPI). 
  
## <a name="visual-studio---testing-the-application"></a>Visual Studio - Test de l’Application  
 Microsoft Visual Studio Ultimate et Professional inclut des tests pour vous aider à définir et gérer votre effort de test à l’aide de plans de test. Consultez [test de l’Application](https://docs.microsoft.com/vsts/manual-test/overview).
  
## <a name="visual-studio-profiling-tools"></a>Outils de profilage Visual Studio  
 Les outils de profilage de Visual Studio vous permet de générer le profil .NET personnalisé composants (composants de pipeline personnalisés, les composants d’assistance appelés par les orchestrations et/ou pipelines des fonctoids personnalisés). Consultez, [analyse des performances de l’Application en utilisant les outils de profilage](https://docs.microsoft.com/visualstudio/profiling/performance-explorer).
  
## <a name="windows-performance-analysis-tools"></a>Outils d’analyse de performances Windows  
Outils de performances de Windows sont conçus pour l’analyse d’un large éventail de problèmes de performances, y compris les heures de démarrage d’application, les problèmes de démarrage différé des appels de procédure et d’interruption d’activité (DPC et ISR), la réactivité du système émet, la ressource d’application l’utilisation et les vagues d’interruption.  
  
Consultez [analyse des performances Windows](https://docs.microsoft.com/windows-hardware/test/weg/performance-tools).
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>Outils SQL Server pour la surveillance et le réglage des performances  
 SQL Server fournit plusieurs outils pour surveiller les événements de SQL Server et de paramétrer la structure de base de données physique. Consultez [surveillance et outils de réglage des performances](https://docs.microsoft.com/en-us/sql/relational-databases/performance/performance-monitoring-and-tuning-tools). 
  
### <a name="sql-profiler"></a>SQL Profiler  
 Microsoft SQL Server Profiler peut être utilisé pour capturer les instructions Transact-SQL envoyées à SQL Server et les jeux de résultats SQL Server de ces instructions. Étant donné que SQL Server est étroitement intégré à SQL Server, l’analyse d’une trace de profil SQL Server peut être un outil utile pour analyser les problèmes qui peuvent se produire dans BizTalk Server lors de la lecture et écriture aux bases de données SQL Server. Consultez [à l’aide du Générateur de profils SQL Server](https://docs.microsoft.com/sql/tools/sql-server-profiler/sql-server-profiler-templates-and-permissions).
  
> [!IMPORTANT]  
>  Il existe une charge considérable associée en cours d’exécution du Générateur de profils SQL. Par conséquent, Générateur de profils SQL est idéale pour une utilisation dans des environnements de test ou de développement. Si vous utilisez SQL Profiler pour résoudre les problèmes d’un environnement de production, tenez compte des coûts de traitement associés et limiter l’utilisation du Générateur de profils SQL en conséquence.  
> 
>  Lorsque vous utilisez SQL Profiler pour capturer les instructions Transact-SQL, configurer le Générateur de profils SQL pour générer la sortie vers un lecteur local au lieu d’un lecteur situé sur un partage réseau distant ou un autre périphérique lente, par exemple, une clé de mémoire USB locale.  
  
### <a name="sql-trace"></a>Trace SQL  
 SQL Server fournit les procédures stockées système Transact-SQL pour créer des traces sur une instance du moteur de base de données SQL Server. Ces procédures stockées système peuvent servir à partir de vos propres applications pour créer des traces manuellement au lieu d’utiliser le Générateur de profils SQL Server. Vous pouvez ainsi écrire des applications personnalisées spécifiques des besoins de votre entreprise. Consultez [SQL Trace](https://docs.microsoft.com/sql/relational-databases/sql-trace/sql-trace). 
  
> [!NOTE]  
>  Lorsque vous utilisez Trace SQL pour capturer les instructions Transact-SQL, configurer la Trace SQL pour générer la sortie vers un lecteur local plutôt que sur un lecteur situé sur un partage réseau distant ou un autre périphérique lent, tel qu’un lecteur flash USB.  
  
### <a name="sql-activity-monitor"></a>Moniteur d’activité SQL  
Moniteur d’activité SQL Server fournit des informations sur les processus SQL Server et la façon dont ces processus affectent l’instance actuelle de SQL Server. Consultez [moniteur d’activité](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor), et [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio](https://docs.microsoft.com/sql/relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio). 
  
### <a name="sql-server-data-collection"></a>Collection de données SQL Server  
SQL Server fournit un collecteur de données que vous pouvez utiliser pour obtenir et enregistrer les données collectées à partir de plusieurs sources. Le collecteur de données vous permet d’utiliser des conteneurs de collecte de données, qui vous permettent de déterminer l’étendue et la fréquence de collecte de données sur un ordinateur qui exécute SQL Server. Consultez [collecte des données](https://docs.microsoft.com/sql/relational-databases/data-collection/data-collection).
  
### <a name="sqlio"></a>SQLIO  
 L’outil SQLIO a été développé par Microsoft pour évaluer la capacité d’e/s d’une configuration donnée. Comme l’indique le nom de l’outil, SQLIO est un outil précieux pour mesurer l’impact du système de fichiers d’e/s sur les performances de SQL Server. Télécharger [SQLIO](https://www.microsoft.com/download/details.aspx?id=20163).
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et suppression des goulots d’étranglement](../technical-guides/finding-and-eliminating-bottlenecks.md)