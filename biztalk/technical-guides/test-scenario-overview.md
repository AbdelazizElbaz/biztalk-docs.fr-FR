---
title: "Vue d’ensemble du scénario de test | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cde553ad-2540-40d9-a74b-928fee873c31
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 53e20b7d94e44006df1042c9ca202e296508a5d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-scenario-overview"></a>Vue d’ensemble du scénario de test
Cette rubrique fournit une vue d’ensemble de l’application de test ; obtenir une description de la méthodologie utilisée de test et répertorie les indicateurs de performance clés (KPI) capturées pendant le test de charge.  
  
## <a name="test-application"></a>Application de test  
 Une application demande-réponse synchrone a été utilisée pour comparer les performances de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] s’exécutant sur Hyper-V pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] en cours d’exécution sur un matériel physique. Cette application a été utilisée pour illustrer les performances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution qui a été optimisée pour une latence faible. Faible latence de messagerie est essentielle pour certains scénarios tels que des opérations bancaires en ligne dans laquelle un client envoie une demande et attend un message de réponse dans un intervalle très court (par exemple \< 3 secondes).  
  
 La figure ci-dessous illustre l’architecture de haut niveau utilisée. Visual Studio Team System (VSTS) 2008 Test Load Agent appelée une classe de test personnalisée, qui permet de générer une charge sur le transport WCF [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application dans ce scénario a été exposée via WCF-BasicHttp emplacement de réception requête-réponse. VSTS 2008 Test Load Agent a été utilisé en tant que le client de test en raison de la grande flexibilité qu’il fournit, y compris la possibilité de configurer le nombre de messages envoyés dans, nombre de threads simultanés et l’intervalle de veille entre les demandes envoyées.  
  
 Plusieurs ordinateurs VSTS 2008 Test Load Agent peuvent être exécutés en tandem pour simuler les modèles de charge réels. Pour ces tests, les ordinateurs de VSTS 2008 Test Load Agent pilotées par un seul ordinateur de contrôleur de VSTS 2008 Test Load Agent qui exécutait également BizUnit 3.0. Par conséquent, une charge homogène a été envoyée à la fois physique et virtuel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs. Pour plus d’informations sur l’utilisation de VSTS 2008 Test Edition pour générer une charge simulée pour les tests, consultez [http://go.microsoft.com/fwlink/?LinkID=132311](http://go.microsoft.com/fwlink/?LinkID=132311).  
  
 ![Architecture de l’application](../technical-guides/media/testapplicationarchitecture.gif "TestApplicationArchitecture")  
Architecture de l’Application de test  
  
1.  Un WCF-BasicHttp ou l’emplacement de réception requête-réponse WCF-Custom reçoit un nouveau CalculatorRequest à partir d’un ordinateur Agent de Test de charge.  
  
2.  Le composant désassembleur XML promeut l’élément de méthode à l’intérieur du document xml CalculatorRequest. L’Agent de Message envoie le message entrant dans la base de données MessageBox (BizTalkMsgBoxDb).  
  
3.  La demande entrante démarre une nouvelle instance de la LogicalPortsOrchestration. Cette orchestration utilise un port à liaison directe pour recevoir les messages CalculatorRequest avec la propriété de méthode promue = « LogicalPortsOrchestration ».  
  
4.  Le LogicalPortsOrchestration utilise une boucle pour récupérer les opérations et pour chaque élément, il appelle le service web WCF de calculatrice en aval à l’aide d’un Port de sollicitation-réponse logique. Le message de demande pour le service web WCF de calculatrice est créé à l’aide d’un composant d’assistance et publié dans la MessageBox.  
  
5.  Le message de demande est utilisé par un Port d’envoi WCF-BasicHttp.  
  
6.  Le Port d’envoi WCF-BasicHttp appelle l’une des méthodes (ajouter, soustraction, multiplication, division) exposées par le service web WCF de calculatrice.  
  
7.  Le service web WCF de calculatrice renvoie un message de réponse.  
  
8.  Le message de réponse est publié dans la MessageBox.  
  
9. Le message de réponse est renvoyé à l’appelant LogicalPortsOrchestration. L’orchestration répète ce modèle pour chaque opération dans le document xml CalculatorRequest entrant.  
  
10. La LogicalPortsOrchestration publie le message CalculatorResponse vers la MessageBox.  
  
11. Le message de réponse est récupéré par l’emplacement de réception requête-réponse WCF-BasicHttp.  
  
12. Le message de réponse est renvoyé à l’ordinateur de l’Agent de Test de charge.  
  
 Vous trouverez ci-dessous une capture d’écran de l’orchestration utilisée pendant le test de charge :  
  
> [!NOTE]  
>  À des fins d’illustration, l’orchestration représentée ci-dessous est une version simplifiée de l’orchestration qui a été réellement utilisée pendant le test de charge. L’orchestration utilisée pendant le test de charge inclus plusieurs étendues, logique de gestion des erreurs et les types de ports supplémentaires.  
  
 ![Application de l’orchestration](../technical-guides/media/logicalportsorchestration.gif "LogicalPortsOrchestration")  
Orchestration de l'application test  
  
## <a name="testing-methodology"></a>Méthodologie de test  
 Les tests de performances implique de nombreuses tâches, qui si effectuée manuellement répétitives, monotones, et sujet aux erreurs. Afin d’améliorer l’efficacité de test et d’assurer la cohérence entre les séries de tests, [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)] Team System (VSTS) Test Edition avec BizUnit 3.0 a été utilisée pour automatiser les tâches requises pendant le processus de test. Ordinateurs de VSTS 2008 Test Load Agent ont été utilisés en tant que le client de test pour générer la charge de message sur le système et les mêmes types de message ont été utilisés sur chaque série de tests pour améliorer la cohérence. Cette procédure fournit un jeu cohérent de données pour chaque série de tests. Pour plus d’informations sur BizUnit 3.0, consultez [http://go.microsoft.com/fwlink/?LinkID=85168](http://go.microsoft.com/fwlink/?LinkID=85168). Pour plus d’informations sur [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)] Team System Test Edition, consultez [http://go.microsoft.com/fwlink/?LinkID=141387](http://go.microsoft.com/fwlink/?LinkID=141387).  
  
 Les étapes suivantes ont été automatisés :  
  
-   Arrêter les hôtes BizTalk.  
  
-   Nettoyer les répertoires de test.  
  
-   Redémarrez IIS.  
  
-   Nettoyage du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données Messagebox.  
  
-   Redémarrez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
-   Effacer des journaux des événements.  
  
-   Créez un dossier de résultats de test pour chaque exécution stocker des métriques de performances associés et les fichiers journaux.  
  
-   Démarrer les hôtes BizTalk.  
  
-   Charger les compteurs de l’Analyseur de performances.  
  
-   Préchauffage environnement BizTalk avec une petite charge.  
  
-   Envoyer par représentant à exécuter.  
  
-   Écrire des journaux de performances dans un dossier de résultats.  
  
-   Collecter les journaux des applications et d’écriture dans un fichier .csv dans le dossier de résultats.  
  
-   Exécutez l’outil de performances analyse des journaux (PAL), les outils Rejournaliser et de l’Analyseur de journal sur les journaux de performances collectées pour produire des statistiques, des graphiques et des rapports. Pour plus d’informations sur la PAL, Rejournaliser et de l’Analyseur de journal, consultez [annexe d : outils pour mesurer les performances](../technical-guides/appendix-d-tools-for-measuring-performance.md).  
  
> [!NOTE]  
>  Le suivi a été désactivé et le travail de SQL Server Agent BizTalk Server a été désactivé pendant le test.  
  
 Pour vous assurer que les résultats de ce laboratoire ont été en mesure de fournir une comparaison des performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un physique et un environnement Hyper-V, les métriques de performances et les journaux collectés dans un emplacement centralisé pour chaque série de tests.  
  
 Le client test a été utilisé pour créer un répertoire de résultats uniques pour chaque série de tests. Ce répertoire contenus de tous les journaux de performances, les journaux des événements et les données requises pour le test associées. Cette approche fourni les informations nécessaires lors de l’exécution de l’analyse rétrospective de test préalable étaient nécessaire. À la fin de chaque test, les données brutes a été compilées en un jeu de résultats cohérents et indicateurs de performance clés (KPI). Collecte des résultats cohérents définie pour les ordinateurs physiques et virtualisés fournis les points de comparaison nécessaire entre les différents environnements plusieurs séries de tests. Les données collectées inclus :  
  
-   **Environnement** pour enregistrer l’environnement dans lequel le test a été exécuté, BizTalk Server sur du matériel physique ou BizTalk Server sur Hyper-V.  
  
-   **Tester le numéro de série –** pour identifier de façon unique chaque série de tests  
  
-   **Cas de test :** pour enregistrer l’architecture de la solution BizTalk Server utilisée pendant les tests. (Par exemple envoie Orchestration avec Ports logiques par rapport à l’Orchestration à l’aide en ligne)  
  
-   **Date –** pour enregistrer la date et l’heure du test a été exécuté.  
  
-   **Heure commencé –** comme indiqué par l’agent de test de charge VSTS première initié  
  
-   **Temps bloqué –** comme indiqué par l’agent de test de charge VSTS dernier pour terminer  
  
-   **Durée du test en Minutes –** pour enregistrer la durée du test.  
  
-   **Messages envoyés au Total :** pour enregistrer le nombre total de messages envoyés à partir des ordinateurs de l’Agent de charge sur les ordinateurs BizTalk Server pendant le test.  
  
-   **Messages envoyés par seconde –** pour enregistrer les messages envoyés par seconde à partir des ordinateurs de l’Agent de charge sur les ordinateurs BizTalk Server pendant le test.  
  
-   **Latence de Client – moyenne** pour enregistrer la durée moyenne entre les clients de Test Load Agent lancé une demande d’et a reçu une réponse à partir des ordinateurs BizTalk Server pendant le test de charge.  
  
-   **Durée de requête-réponse moyen (ms) :** comme indiqué par le **BizTalk : latence Latency\Request-réponse (s) de messagerie** compteur Analyseur de performances pour BizTalkServerIsolatedHost  
  
    > [!NOTE]  
    >  Où plusieurs hôtes BizTalk virtualisés en cours d’exécution une moyenne de ces compteurs tel que calculé à partir des journaux a été utilisé.  
  
-   **Terminé orchestrations par seconde –** comme indiqué par le **\Orchestrations le Orchestrations XLANG/s (BizTalkServerApplication) réussies par seconde** compteur Analyseur de performances. Ce compteur fournit une bonne mesure du débit de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   **% de Messages traités \< 3 secondes –** pour enregistrer le nombre total de messages traités au sein de 3 secondes pendant le test.  
  
 Test de charge VSTS 2008 a été utilisé pour générer une charge homogène dans l’ensemble de tous les tests. Le test suivant des paramètres d’exécution et le modèle de charge ont été modifiés au cours du test pour ajuster le profil de charge de chaque test :  
  
-   **Paramètres de série de tests**  
  
     Le paramètre d’exécution de test suivant a été modifié selon le test en cours d’exécution :  
  
    -   **Exécutez durée –** spécifie la durée pendant laquelle l’exécution du test.  
  
     ![Tester les paramètres d’exécution](../technical-guides/media/wcfloadtestrunsettings.gif "WCFLoadTestRunSettings")  
Tester des paramètres d'exécution  
  
-   **Paramètres de modèle de test**  
  
     Les paramètres de modèle de test suivants ont été modifiés selon le test en cours d’exécution :  
  
    1.  **Modèle –** spécifie la façon dont la charge utilisateur simulée est ajustée pendant un test de charge. Modèles de charge sont **constante**, **étape**, ou **objectif** en fonction. Tous les tests de charge effectuée étaient constante ou étape.  
  
        > [!NOTE]  
        >  Tous les tests effectuée pour des raisons de ce guide utilisé soit un **constante** modèle de charge ou un **étape** modèle de charge. Modèles de charge constant et les modèles de charge étape fournissent les fonctionnalités suivantes :  
        >   
        >  -   **Modèle de charge constant –** le modèle de charge est la même pour la durée du test, le nombre d’utilisateurs simulés commence à un niveau prédéfini et ne change pas.  
        > -   **Modèle de charge étape –** le modèle de charge augmente pendant la série de tests ; le nombre d’utilisateurs simulés commence à un niveau prédéfini et est incrémenté d’un montant prédéfini à des intervalles prédéfinis pour la durée du test.  
  
    2.  **Nombre d’utilisateurs constant (charger modèle Constant) –** nombre d’utilisateurs virtuels qui génèrent la charge par rapport à l’adresse de point de terminaison spécifié dans le fichier app.config du projet de Test de charge de Visual Studio. Cette valeur est spécifiée dans les paramètres de modèle de charge utilisés pour le test de charge.  
  
    3.  **Nombre initial d’utilisateurs (étape modèle de charge) –** nombre d’utilisateurs virtuels qui génèrent la charge par rapport à l’adresse de point de terminaison spécifié au début d’un test de modèle de charge dans l’étape. Cette valeur est spécifiée dans les paramètres de modèle de charge utilisés pour le test de charge.  
  
    4.  **Nombre maximal d’utilisateurs (étape modèle de charge) –** nombre d’utilisateurs virtuels qui génèrent la charge par rapport à l’adresse de point de terminaison spécifié à la fin d’un test de modèle de charge dans l’étape. Cette valeur est spécifiée dans les paramètres de modèle de charge utilisés pour le test de charge.  
  
    5.  **Durée de l’étape (étape modèle de charge) –** nombre de secondes que les utilisateurs virtuels sont génère une charge par rapport à l’adresse de point de terminaison spécifié pour une étape de test de charge.  
  
    6.  **Nombre d’utilisateurs étape (étape modèle de charge) –** nombre d’utilisateurs virtuels à augmenter à chaque étape lors de l’utilisation d’un modèle de charge d’étape.  
  
     ![Paramètres de modèle de test](../technical-guides/media/wcfloadtestpatternsettings.gif "WCFLoadTestPatternSettings")  
Tester des paramètres du modèle  
  
 Pour plus d’informations sur l’utilisation des tests de charge dans [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)], consultez la rubrique **fonctionne avec des Tests de charge** dans les [!INCLUDE[btsVStudio2008](../includes/btsvstudio2008-md.md)] documentation Team System à l’adresse [http://go.microsoft.com/fwlink/?LinkId=141486](http://go.microsoft.com/fwlink/?LinkId=141486).  
  
## <a name="key-performance-indicators-measured-during-testing"></a>Indicateurs de Performance clés mesurés au cours du test  
 Les compteurs de l’Analyseur de performances suivants ont été capturées en tant qu’indicateurs de performance clés (KPI) pour toutes les séries de tests :  
  
> [!NOTE]  
>  Pour plus d’informations sur l’évaluation des performances avec les compteurs de Performance, consultez [liste de vérification : mesure des performances sur Hyper-V](../technical-guides/checklist-measuring-performance-on-hyper-v.md).  
  
 **Indicateur de performance clé de BizTalk Server**  
  
-   **Documents traités par seconde –** telle que mesurée par le **BizTalk : messagerie/Documents traités par seconde** compteur.  
  
-   **Latence –** mesuré tel que retourné par le contrôleur de Test de charge VSTS 2008.  
  
 **KPI SQL Server**  
  
-   **Utilisation du processeur de SQL Server –** telle que mesurée par le **SQL\Processor(Total)\\% temps processeur** compteur. Ce compteur mesure l’utilisation du processeur de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de traitement sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
-   **Transact des performances de traitement de commande SQL –** telle que mesurée par le **\SQL Server:SQL Statistics\Batch demandes par seconde** compteur. Ce compteur mesure le nombre de lots de commandes Transact-SQL reçues par seconde. Ce compteur est utilisé pour mesurer le débit de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
 **Indicateur de performance clé de la mise en réseau**  
  
-   **Débit du réseau de BizTalk Server –** telle que mesurée par le **\Network Interface (\*) \Bytes/s** compteur Analyseur de performances sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs.  
  
-   **Débit du réseau SQL Server –** telle que mesurée par le **SQL Network Interface\Bytes Total/s (Avg)** retournée par le contrôleur de Test de charge VSTS 2008.  
  
 **Mémoire d’indicateur de performance clé**  
  
-   **Mémoire disponible :** telle que mesurée par le **\Memory\Available Mo** compteur pour les différents scénarios.  
  
## <a name="physical-infrastructure-specifics"></a>Caractéristiques de l’Infrastructure physique  
 Pour chacun des serveurs qui ont été installées, les paramètres suivants ont été ajustées.  
  
 **Pour tous les serveurs :**  
  
-   Le fichier d’échange a été défini à 1,5 fois la quantité de mémoire physique allouée. Le fichier d’échange a été défini sur une taille fixe en vous assurant que la taille initiale et les valeurs maximales sont identiques en Mo.  
  
-   L’option de performances « Ajuster pour de meilleures performances » a été sélectionnée à partir de l’écran Avancé de propriétés système.  
  
-   Il a été vérifié que le système avait été ajusté pour de meilleures performances des services d’arrière-plan dans la section Options de performances des propriétés système.  
  
-   [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]a été installé en tant que le système d’exploitation invité sur chacun des ordinateurs virtuels.  
  
-   Windows Update a été correctement exécutée sur tous les serveurs pour installer les dernières mises à jour de sécurité.  
  
 **Pour SQL Server :**  
  
-   [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]a été installé selon le guide d’installation disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=141021](http://go.microsoft.com/fwlink/?LinkId=141021).  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]utilisé avait le LUN SAN configuré conformément à la table ci-dessous. Les base de données et les fichiers journaux ont été séparés pour sur les LUN comme suit pour réduire la contention d’e/s de disque possibles :  
  
    -   Le volume Data_Sys a été utilisé pour stocker tous les fichiers de base de données (y compris le système et les bases de données BizTalk), à l’exception des bases de données MessageBox et TempDb.  
  
    -   Le volume Log_Sys a été utilisé pour stocker tous les fichiers journaux (y compris le système et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données) à l’exception des bases de données MessageBox et TempDb.  
  
    -   Le volume Data_TempDb a été utilisé pour stocker le fichier de base de données TempDb.  
  
    -   Le volume Logs_TempDb a été utilisé pour stocker les fichiers journaux TempDb.  
  
    -   Le fichier de base de données MessageBox a été stocké sur le volume Data_BtsMsgBox et le fichier journal a été stocké sur le volume Log_BtsMsgBox.  
  
-   En outre, un distinct numéro d’unité logique a été fournie pour le fichier journal MSDTC. Sur les systèmes de BizTalk un débit élevé, l’activité du fichier journal MSDTC a été indiquée pour provoquer un goulot d’étranglement d’e/s s’il est conservé sur le même lecteur physique du système d’exploitation.  
  
    |Nom de volume|Fichiers|Numéro d’unité logique taille Go|Héberger la taille de la Partition Go|Taille de cluster|  
    |-----------------|-----------|-----------------|----------------------------|------------------|  
    |Data_Sys|MASTER et les fichiers de données MSDB|10|10|64 KO|  
    |Logs_Sys|Fichiers journaux de MASTER et MSDB|10|10|64 KO|  
    |Data_TempDb|Fichier de données TempDB|50|50|64 KO|  
    |Logs_TempDb|Fichier journal TempDB|50|50|64 KO|  
    |Data_BtsMsgBox|Fichier de données BizTalkMsgBoxDb|300|100|64 KO|  
    |Logs_BtsMsgBox|Fichier de journal BizTalkMsgBoxDb|100|100|64 KO|  
    |Data_BAMPrimaryImport|Fichier de données BAMPrimaryImport|10|10|64 KO|  
    |Logs_BAMPrimaryImport|Fichier de journal BAMPrimaryImport|10|10|64 KO|  
    |Data_BizTalkDatabases|Autres fichiers de données de base de données BizTalk|20|20|64 KO|  
    |Logs_BizTalkDatabases|Autres fichiers journaux de base de données BizTalk|20|20|64 KO|  
    |Néant|Fichier journal MSDTC|5|5|Néant|  
  
-   [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]a été installé selon les guides d’installation disponibles à l’adresse [http://go.microsoft.com/fwlink/?LinkId=128383](http://go.microsoft.com/fwlink/?LinkId=128383).  
  
-   Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] outil de Best Practices Analyzer (BPA) a été utilisé pour effectuer la validation de plateforme une fois que le système a été configuré. Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] BPA est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67150](http://go.microsoft.com/fwlink/?LinkId=67150).  
  
## <a name="virtualization-specifics"></a>Caractéristiques de la virtualisation  
 Unique 50 Go de disque dur virtuel fixé a été utilisé pour héberger le système d’exploitation pour chaque ordinateur virtuel de Hyper-V.  
  
 Les disques durs virtuels fixes ont été utilisés au lieu de disques durs virtuels de tailles dynamique, car ils immédiatement d’allouer le stockage maximal pour le disque dur virtuel au fichier sur le lecteur sur lequel il est hébergé. Cela réduit la fragmentation du fichier de disque dur virtuel qui se produisent sur le lecteur physique sur lequel il est hébergé, ce qui améliore les performances d’e/s de disque.  
  
 Pour configurer les ordinateurs virtuels, une installation de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] Édition 64 bits a été effectuée sur un disque dur virtuel unique. Une fois que toutes les mises à jour appropriées ont été installés l’ordinateur virtuel de base a été mis en image à l’aide de sysprep utilitaire qui est installé avec [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], dans le répertoire %WINDIR%\system32\sysprep.  
  
 Ce disque dur virtuel de base a été copié, puis utilisé comme base pour tous les ordinateurs virtuels Hyper-V qui ont été déployés dans l’environnement. Sysprep a été exécuté sur l’image de disque dur virtuel de base pour réinitialiser les identificateurs de sécurité système avant tout [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] binaires ont été déployées sur le système.  
  
> [!NOTE]  
>  L’exécution de Sysprep [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] a été installé et configuré sur le serveur peut être effectué via l’utilisation d’un fichier de réponses Sysprep et les scripts fournis avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. Ces exemples de scripts sont conçus pour une utilisation avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] installé sur les versions 32 bits et 64 bits de [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] uniquement. Pour plus d’informations, consultez le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] documentation en ligne.  
  
 La référence de l’installation Windows sans assistance est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=142364](http://go.microsoft.com/fwlink/?LinkId=142364).  
  
## <a name="see-also"></a>Voir aussi  
 [Annexe c : prise en charge Hyper-V BizTalk Server et SQL Server](../technical-guides/appendix-c-biztalk-server-and-sql-server-hyper-v-supportability.md)