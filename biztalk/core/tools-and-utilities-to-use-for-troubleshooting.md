---
title: "Outils et utilitaires à utiliser pour le dépannage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c817384f-e328-439d-9c41-a94ed75670ce
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86eab8504ab3dff93370783cca6c8fce1a0b9388
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tools-and-utilities-to-use-for-troubleshooting"></a>Outils et utilitaires à utiliser en cas de dépannage
Cette rubrique présente divers outils et utilitaires dont vous pouvez vous servir pour diagnostiquer la cause principale d'un problème dans un composant Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou une dépendance.  
  
## <a name="event-viewer"></a>Observateur d'événements  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] consigne les informations, avertissements et erreurs dans le journal des événements de l'ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé. Pour résoudre un problème dans un composant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou une dépendance, vous devez en premier lieu consulter le journal des événements afin de rechercher des informations qui vous aideront à le diagnostiquer. Pour plus d'informations sur l'Observateur d'événements, consultez la documentation de Windows.  
  
## <a name="network-monitor"></a>Moniteur réseau  
 Cet utilitaire permet de capturer le trafic réseau entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les serveurs ou clients distants. Vous pouvez alors analyser le trafic réseau capturé afin de diagnostiquer des problèmes réseau.  
  
 Le Moniteur réseau est disponible sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] via la **ajouter/supprimer des composants Windows** option est disponible dans **Ajout/Suppression de programmes**.  
  
 La fonctionnalité Moniteur réseau est fournie sous Windows XP par le biais de l'utilitaire NETCAP.exe installé avec les outils de support de Windows qui se trouvent sur le CD de Windows XP. Pour plus d’informations sur la voir utilitaire NETCAP.exe [Description de l’utilitaire de Capture Moniteur réseau](http://go.microsoft.com/fwlink/?LinkId=66227).  
  
 Pour plus d’informations sur la façon de capturer le trafic réseau avec le Moniteur réseau, consultez [comment capturer le trafic réseau avec le Moniteur réseau](http://go.microsoft.com/fwlink/?LinkId=66230).  
  
## <a name="fiddler-tool"></a>Outil Fiddler  
 Utilisez Fiddler pour enregistrer l'ensemble du trafic HTTP entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les clients ou serveurs distants. Fiddler est compatible avec Visual Studio Team Edition for Testers et permet de sauvegarder des enregistrements sous la forme de fichiers de test Web qui peuvent ensuite être ajoutés aux projets Visual Studio Team Edition for Testers.  
  
 Fiddler comporte quelques inconvénients : il ne prend pas encore en charge SSL, il n'assure pas le suivi automatique des champs masqués (à la différence de ViewState par exemple) et il ne filtre pas les demandes dépendantes.  
  
 Fiddler est disponible à l’adresse [http://www.fiddlertool.com](http://go.microsoft.com/fwlink/?LinkId=119605). Pour plus d’informations sur l’utilisation de Fiddler, consultez [http://go.microsoft.com/fwlink/?LinkId=84814](http://go.microsoft.com/fwlink/?LinkId=84814).  
  
## <a name="sql-server-profiler"></a>SQL Server Profiler  
 Le Générateur de profils Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permet de capturer les instructions Transact-SQL envoyées au serveur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et les ensembles de résultats du [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] provenant de ces instructions. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] étant intégré à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], l'analyse de suivi du Générateur de profils [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] s'avère utile pour l'étude des problèmes susceptibles de survenir sur BizTalk Server lors de la lecture à partir des bases de données [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Pour plus d'informations sur l'utilisation du Générateur de profils [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], reportez-vous à la documentation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## <a name="sql-server-query-editor"></a>Éditeur de requête SQL Server  
 L'éditeur de requête SQL Server permet d'exécuter des instructions SQL directement dans les bases de données SQL Server. Cette fonctionnalité s'avère utile pour l'interrogation des bases de données BizTalk Server ou pour la mise à jour des bases de données BizTalk Server dans certains cas. Pour plus d'informations sur l'éditeur de requête, consultez la documentation de [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] ou de [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)].  
  
## <a name="dtctester"></a>DTCTester  
 La plupart des opérations du moteur d'exécution BizTalk Server requièrent une prise en charge du service MSDTC (Microsoft Distributed Transaction Coordinator) afin de garantir la cohérence transactionnelle des opérations. Si la prise en charge des transactions MSDTC n'est pas disponible, alors les opérations d'exécution de BizTalk Server associées ne peuvent pas se poursuivre. L'outil DTCTester permet de vérifier la prise en charge des transactions distribuées sur les pare-feu ou sur les réseaux. Il utilise ODBC pour vérifier cette prise en charge dans une base de données SQL Server ; il requiert par conséquent l'installation d'un serveur SQL Server sur l'un des ordinateurs testés. Pour plus d’informations sur l’utilitaire DTCTester, consultez [comment To Use DTCTester Tool](http://support.microsoft.com/kb/293799).  
  
## <a name="dtcping"></a>DTCPing  
 L'outil DTCPing permet de vérifier la prise en charge des transactions distribuées sur les pare-feu ou sur les réseaux. L'utilitaire DTCPing doit être installé à la fois sur l'ordinateur client et sur l'ordinateur serveur, et constitue une alternative à l'utilitaire DTCTester lorsque SQL Server n'est installé sur aucun des deux ordinateurs. Pour plus d’informations sur l’utilisation de DTCPing pour vérifier la prise en charge des transactions distribuées, consultez [comment résoudre les problèmes de pare-feu MS DTC](http://go.microsoft.com/fwlink/?LinkId=61915).  
  
## <a name="performance-console"></a>Console de performance  
 Cette console permet de capturer les données d'analyse des performances dans votre environnement BizTalk. Consultez [les compteurs de Performance](../core/performance-counters.md) pour obtenir la liste complète des compteurs de performance inclus avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d'informations sur l'utilisation de la console de performances, consultez la documentation de Windows.  
  
## <a name="regmon-filemon-and-debugview"></a>RegMon, FileMon et DebugView  
 RegMon affiche l'activité d'accès au Registre en temps réel : il répertorie chaque appel d'une application au Registre et consigne le résultat. Il vous permet de savoir quand une application ne parvient pas à accéder à une clé de registre. De la même manière, FileMon affiche l'activité du système de fichiers en temps réel : il répertorie chaque appel d'une application au système et enregistre le résultat. DebugView vous permet d'analyser la sortie de débogage sur votre système local ou sur tout ordinateur du réseau accessible via TCP/IP.  
  
 RegMon et FileMon permettent à l'administrateur de tester une application et d'identifier l'échec des appels effectués par l'application au Registre ou au système de fichiers. L'administrateur peut alors minimiser l'échec, par exemple, en modifiant les autorisations d'accès au système de fichiers ou à la clé de registre.  
  
 DebugView permet à l'administrateur de tester une application et d'analyser la sortie de débogage sur le système local ou sur tout ordinateur du réseau accessible via TCP/IP.  
  
 Pour plus d’informations sur ces utilitaires, consultez le site Web de Windows Sysinternals à [http://www.microsoft.com/technet/sysinternals/default.mspx](http://go.microsoft.com/fwlink/?LinkId=66235).  
  
## <a name="debug-diagnostics-tool-of-the-iis-diagnostics-toolkit"></a>Outil de diagnostic de débogage de l'ensemble d'outils de diagnostic IIS  
 Cet outil permet de générer une image mémoire du processus ayant échoué et d'effectuer une analyse élémentaire du fichier généré. Pour plus d’informations sur l’utilisation de l’outil de diagnostic de débogage de la boîte à outils de Diagnostic de IIS pour capturer une image mémoire, consultez [comment capturer une image mémoire d’un processus BizTalk](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md).