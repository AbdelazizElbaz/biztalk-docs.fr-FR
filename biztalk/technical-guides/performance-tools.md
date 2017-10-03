---
title: Outils de performances | Documents Microsoft
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
ms.openlocfilehash: c53894ca4dcf1b1541c020e14a83542a7ce56d56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performance-tools"></a>Outils de performances
Cette rubrique fournit des informations sur les outils que vous pouvez utiliser pour évaluer les performances d’une solution BizTalk Server. Les outils décrits dans cette rubrique ont des objectifs différents ; Certains sont conçus pour évaluer les performances de bout en bout alors que d’autres se concentrent sur l’évaluation des performances d’un aspect particulier d’une solution BizTalk Server.  
  
## <a name="biztalk-server-orchestration-profiler"></a>Profileur d’Orchestration de BizTalk Server  
 Le profileur de d’Orchestration de BizTalk Server permet d’afficher le suivi des données pour une période de temps d’une orchestration et est utile pour déterminer l’emplacement des goulots d’étranglement de performances dans les orchestrations.  
  
 Pour plus d’informations sur le profileur de d’Orchestration de BizTalk Server, consultez [BizTalk Server 2006 Orchestration Profiler](http://go.microsoft.com/fwlink/?LinkId=102209) (http://go.microsoft.com/fwlink/?LinkId=102209).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité. Notez que cet utilitaire a été conçu pour fonctionner avec BizTalk Server 2006 et par conséquent peuvent ne pas fonctionne comme prévu sur BizTalk Server 2010.  
  
## <a name="bizunit-30-and-bizunit-designer"></a>BizUnit 3.0 et le concepteur BizUnit  
 BizUnit est une infrastructure conçue pour les tests automatisés de solutions BizTalk. BizUnit est un excellent outil pour tester les scénarios de bout en bout pour BizTalk Server. Exécution de tests automatisés de solutions BizTalk avec BizUnit est le principal objectif de la [mise en œuvre des tests automatisés](../technical-guides/implementing-automated-testing.md) section de ce guide. Pour plus d’informations sur BizUnit 3.0, consultez [BizUnit - Framework pour automatisée la tester de systèmes distribués](http://go.microsoft.com/fwlink/?LinkID=85168) (http://go.microsoft.com/fwlink/?LinkID=85168).  
  
 Le Concepteur de BizUnit est une interface utilisateur graphique qui permet de créer rapidement des cas de test BizUnit qui peut être utilisé pour le test unitaire ou test des applications distribuées du système. L’outil est disponible à l’adresse [BizUnit concepteur](http://go.microsoft.com/fwlink/?LinkID=117917) (http://go.microsoft.com/fwlink/?LinkID=117917).  
  
> [!IMPORTANT]  
>  Au moment de la rédaction de ce guide, les cas de test générés par le concepteur BizUnit 1.x sont uniquement compatibles avec BizUnit 2.x.  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="iometer"></a>IOMeter  
 IOMeter est un outil open source utilisé pour le disque mesure les performances d’e/s. Pour plus d’informations sur IOMeter, consultez [http://www.iometer.org](http://go.microsoft.com/fwlink/?LinkId=122412) (http://go.microsoft.com/fwlink/?LinkId=122412).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="log-parser"></a>Analyseur de journal  
 Log parser est un outil puissant et flexible qui fournit l’accès de requête universel à des données texte tels que les fichiers journaux, les fichiers XML et fichiers CSV, et sources de données clés sur le système d’exploitation Windows® tels que le journal des événements, le Registre, le système de fichiers et actif Directory®. Analyseur de journal n’est disponible pour téléchargement à l’adresse [journal Parser 2.2](http://go.microsoft.com/fwlink/?LinkID=100882) (http://go.microsoft.com/fwlink/?LinkID=100882).  
  
## <a name="microsoft-biztalk-loadgen-2007"></a>Microsoft BizTalk LoadGen 2007  
 BizTalk LoadGen 2007 est un outil de génération de charge utilisé pour exécuter des performances et des tests de stress sur [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
 Pour plus d’informations sur l’outil Microsoft BizTalk LoadGen 2007, consultez [Microsoft BizTalk LoadGen 2007 outils](http://go.microsoft.com/fwlink/?LinkId=59841) (http://go.microsoft.com/fwlink/?LinkId=59841).  
  
## <a name="pathping"></a>Pathping  
 PathPing fournit des informations sur la perte de données à un ou plusieurs sauts de routeur sur le chemin d’un ordinateur hôte cible. Pour ce faire, pathping envoie des paquets de contrôle Message ICMP (Internet Protocol) à chaque routeur situé dans le chemin d’accès. Pathping.exe est disponible avec toutes les versions de Windows depuis Windows 2000 Server.  
  
## <a name="performance-analysis-of-logs-pal"></a>Analyse des performances des journaux (PAL)  
 L’outil de publication est utilisé pour générer un rapport basé sur HTML graphiquement graphiques des compteurs de performances importants et génère des alertes lorsque les seuils de ces compteurs sont dépassés. Cette dernière constitue un excellent outil pour identifier les goulots d’étranglement dans une solution BizTalk Server afin de faciliter l’affectation des ressources pour optimiser les performances de la solution.  
  
 Pour plus d’informations sur l’outil performances analyse des journaux (PAL), consultez [outil de performances analyse des journaux (PAL)](http://go.microsoft.com/fwlink/?LinkID=98098) (http://go.microsoft.com/fwlink/?LinkID=98098).  
  
> [!NOTE]  
>  Utilisation de cet outil n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce programme. L'utilisation de ce programme relève de votre seule responsabilité.  
  
## <a name="performance-monitor"></a>Analyseur de performances  
 Analyseur de performances fournit un affichage visuel des compteurs de performances Windows intégrés, en temps réel ou comme un moyen pour passer en revue les données d’historique.  
  
## <a name="relog"></a>Reconnecter  
 L’utilitaire Rejournaliser est utilisé pour extraire les compteurs de performances à partir des journaux créés par l’Analyseur de performances et de convertir les données d’autres formats, tels que les fichiers de texte délimité (texte-TSV), les fichiers texte délimité par des virgules (CSV de texte), des fichiers binaires et les bases de données SQL. Ces données peuvent ensuite être analysées et interrogés à l’aide d’autres outils, tels que de l’Analyseur de journal, pour générer des statistiques pour les indicateurs de performance clés (KPI). L’utilitaire Rejournaliser est fourni avec [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] et les versions ultérieures.  
  
## <a name="visual-studio-2010---testing-the-application"></a>Visual Studio 2010 - test de l’Application  
 Microsoft Visual Studio 2010 Ultimate et Visual Studio Test Professional 2010 incluent désormais une nouvelle application appelée Microsoft Test Manager pour vous aider à définir et gérer votre effort de test à l’aide de plans de test. Pour plus d’informations sur l’utilisation des tests de charge, consultez [test de l’Application](http://go.microsoft.com/fwlink/?LinkID=205342) (http://go.microsoft.com/fwlink/?LinkID=205342).  
  
## <a name="visual-studio-2010-profiling-tools"></a>Outils de profilage de Visual Studio 2010  
 Les outils de profilage de Visual Studio vous permet de générer le profil .NET personnalisé composants (composants de pipeline personnalisés, les composants d’assistance appelés par les orchestrations et/ou pipelines des fonctoids personnalisés). Pour plus d’informations sur les outils de profilage de Visual Studio, consultez [analyse des performances des applications à l’aide des outils de profilage](http://go.microsoft.com/fwlink/?LinkID=210555) (http://go.microsoft.com/fwlink/?LinkID=210555).  
  
## <a name="windows-performance-analysis-tools"></a>Outils d’analyse de performances Windows  
 Outils de performances de Windows sont conçus pour l’analyse d’un large éventail de problèmes de performances, y compris les heures de démarrage d’application, les problèmes de démarrage différé des appels de procédure et d’interruption d’activité (DPC et ISR), la réactivité du système émet, la ressource d’application l’utilisation et les vagues d’interruption.  
  
 Pour plus d’informations sur les outils d’analyse de performances Windows, consultez [analyse des performances Windows](http://go.microsoft.com/fwlink/?LinkId=139763) (http://go.microsoft.com/fwlink/?LinkId=139763).  
  
## <a name="sql-server-tools-for-performance-monitoring-and-tuning"></a>Outils SQL Server pour la surveillance et le réglage des performances  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]fournit plusieurs outils pour surveiller les événements de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et de paramétrer la conception physique de la base de données. Ces outils sont décrits dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] rubrique de la documentation en ligne [outils d’analyse des performances et l’optimisation de](http://go.microsoft.com/fwlink/?LinkId=146357) (http://go.microsoft.com/fwlink/?LinkId=146357). Pour plus d’informations sur les outils spécifiques utilisés pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] analyse et de réglage des performances sont fourni ci-dessous :  
  
### <a name="sql-profiler"></a>SQL Profiler  
 Le Générateur de profils Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permet de capturer les instructions Transact-SQL envoyées au serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et les ensembles de résultats du [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provenant de ces instructions. Étant donné que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est étroitement intégré à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], l’analyse d’un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] trace de profil peut être un outil utile pour analyser les problèmes qui peuvent se produire dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] lors de la lecture et écriture à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données. Pour plus d’informations sur l’utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, consultez le [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] rubrique de la documentation en ligne [à l’aide de SQL Server Profiler](http://go.microsoft.com/fwlink/?linkid=104423) (http://go.microsoft.com/fwlink/?linkid=104423).  
  
> [!IMPORTANT]  
>  Il existe une charge considérable associée en cours d’exécution du Générateur de profils SQL. Par conséquent, Générateur de profils SQL est idéale pour une utilisation dans des environnements de test ou de développement. Si vous utilisez SQL Profiler pour résoudre les problèmes d’un environnement de production, tenez compte des coûts de traitement associés et limiter l’utilisation du Générateur de profils SQL en conséquence.  
  
> [!NOTE]  
>  Lorsque vous utilisez SQL Profiler pour capturer les instructions Transact-SQL, configurer le Générateur de profils SQL pour générer la sortie vers un lecteur local au lieu d’un lecteur situé sur un partage réseau distant ou un autre périphérique lente, par exemple, une clé de mémoire USB locale.  
  
### <a name="sql-trace"></a>Trace SQL  
 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Fournit des procédures stockées système Transact-SQL pour créer des traces sur une instance du moteur de base de données SQL Server. Ces procédures stockées système peuvent servir à partir de vos propres applications pour créer des traces manuellement au lieu d’utiliser le Générateur de profils SQL Server. Vous pouvez ainsi écrire des applications personnalisées spécifiques des besoins de votre entreprise. Pour plus d’informations sur l’utilisation de Trace SQL, consultez le [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] rubrique de la documentation en ligne [présentation de SQL Trace](http://go.microsoft.com/fwlink/?LinkId=146354) (http://go.microsoft.com/fwlink/?LinkId=146354).  
  
> [!NOTE]  
>  Lorsque vous utilisez Trace SQL pour capturer les instructions Transact-SQL, configurer la Trace SQL pour générer la sortie vers un lecteur local plutôt que sur un lecteur situé sur un partage réseau distant ou un autre périphérique lent, tel qu’un lecteur flash USB.  
  
### <a name="sql-activity-monitor"></a>Moniteur d’activité SQL  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]Moniteur d’activité fournit des informations sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] processus et la façon dont ces processus affectent l’instance actuelle de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d’informations sur [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] moniteur d’activité, consultez le [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] rubrique de la documentation en ligne [moniteur d’activité](http://go.microsoft.com/fwlink/?LinkId=146355) (http://go.microsoft.com/fwlink/?LinkId=146355). Pour plus d’informations sur la façon d’ouvrir le moniteur d’activité à partir de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Management Studio, consultez le [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] rubrique de la documentation en ligne [Comment : ouvrir le moniteur d’activité (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=135094) (http://go.microsoft.com/fwlink/?LinkId=135094).  
  
### <a name="sql-server-2008-r2-data-collection"></a>Collecte de données SQL Server 2008 R2  
 [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] fournit un collecteur de données qui vous permet d'obtenir et d'enregistrer des données rassemblées à partir de plusieurs sources. Le collecteur de données vous permet d'utiliser des conteneurs de collecte de données qui vous permettent de déterminer l'étendue et la fréquence de la collecte de données sur ordinateur qui exécute [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]. Pour plus d’informations sur l’implémentation de [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] collecte de données, consultez la [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] rubrique de la documentation en ligne [collecte des données](http://go.microsoft.com/fwlink/?LinkId=146356) (http://go.microsoft.com/fwlink/?LinkId=146356).  
  
### <a name="sqlio"></a>SQLIO  
 L’outil SQLIO a été développé par Microsoft pour évaluer la capacité d’e/s d’une configuration donnée. Comme l’indique le nom de l’outil, SQLIO est un outil précieux pour mesurer l’impact du système de fichiers d’e/s sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performances. SQLIO peut être téléchargé à partir de [outil de test d’évaluation de sous-système de disque SQLIO](http://go.microsoft.com/fwlink/?LinkId=115176) (http://go.microsoft.com/fwlink/?LinkId=115176).  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et suppression des goulots d’étranglement](../technical-guides/finding-and-eliminating-bottlenecks.md)