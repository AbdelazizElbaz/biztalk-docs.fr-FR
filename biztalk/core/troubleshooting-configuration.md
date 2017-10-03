---
title: "Résolution des problèmes de Configuration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 902e591a-4ff4-4053-b329-0c022f44999a
caps.latest.revision: "37"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c16e2ee6d09afa3479a0540838086cb92270132
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-configuration"></a>Résolution des problèmes de configuration
Le programme de configuration de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée des bases de données sur un ou plusieurs ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], alimente les bases de données à l'aide de tables, rôles et procédures stockées utilisées par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et déploie les assemblys .NET utilisés pendant l'exécution vers la base de données de gestion BizTalk.  
  
 Cette section présente les techniques permettant de résoudre les erreurs de configuration. Elle présente également des problèmes de configuration courants et les méthodes utilisées pour les résoudre.  
  
## <a name="configuration-logging"></a>Consignation des informations de configuration  
 Le programme de configuration écrit les informations détaillées dans un fichier journal de configuration qui se trouve par défaut dans le répertoire temporaire de l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour déterminer le dossier spécifié par la variable d'environnement TEMP, ouvrez une invite de commande sur cet ordinateur, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
 **echo %Temp%**  
  
 Le fichier journal contient un récapitulatif des étapes de configuration effectuées, ainsi que des informations de diagnostic sur les échecs susceptibles de survenir au cours du processus de configuration. En cas d'erreur de configuration, ouvrez le journal dans un éditeur de texte tel que le Bloc-notes, puis recherchez les causes possibles.  
  
## <a name="troubleshooting-tools"></a>Outils de résolution des problèmes  
 SQL Server Profiler, Filemon ou Regmon vous permettent de collecter des informations supplémentaires sur les échecs de configuration. Pour plus d’informations sur ces outils, consultez [outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md).  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="configuration-fails-when-biztalk-server-and-sql-server-are-installed-on-separate-computers"></a>Échec de la configuration lorsque BizTalk Server et SQL Server sont installés sur des ordinateurs distincts  
  
##### <a name="problem"></a>Problème  
 Échec de la configuration avec erreurs similaires à celle indiquée ci-après lors de la tentative de configuration du composant d'authentification unique de l'entreprise :  
  
 Une erreur s'est produite lors de la tentative d'accès à la base de données SSO.  
  
 Fonction : FieldInfoCreate  
  
 -ou-  
  
 Impossible d'activer le service d'authentification unique (code d'erreur 0X800706BA)  
  
##### <a name="cause"></a>Cause  
 Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs différents, les opérations de configuration sont effectuées dans le contexte d'une transaction MSDTC (Microsoft Distributed Transaction Coordinator) et la fonctionnalité MSDTC doit être disponible sur le réseau entre ces ordinateurs. Si la fonctionnalité MSDTC n’est pas disponible sur le réseau entre les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ensuite cette erreur peut se produire.  
  
##### <a name="resolution"></a>Résolution  
 Suivez les étapes de [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) pour vérifier la fonctionnalité MSDTC sur le réseau entre les ordinateurs exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
#### <a name="antivirus-software-interferes-with-configuration-and-causes-configuration-failures"></a>Le logiciel antivirus interfère avec la configuration et provoque des échecs de configuration  
  
##### <a name="problem"></a>Problème  
 Échec de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] car le logiciel antivirus détermine à tort que le programme de configuration est un virus.  
  
##### <a name="cause"></a>Cause  
 Le logiciel antivirus n'a pas été configuré pour reconnaître le programme de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme un programme légitime (non virus).  
  
##### <a name="resolution"></a>Résolution  
 Configurez le programme antivirus afin qu'il reconnaisse le programme de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme un programme légitime (non virus), ou désactivez temporairement le logiciel antivirus lors de l'exécution du programme de configuration.  
  
#### <a name="configuration-fails-with-a-file-or-assembly-name-filenamedll-or-one-of-its-dependencies-was-not-found-error"></a>Échec de la configuration avec erreur « Le fichier ou l'assembly nommé FileName.dll ou l'une de ses dépendances est introuvable »  
  
##### <a name="problem"></a>Problème  
 Une erreur similaire à celle indiquée ci-après s'affiche lors du processus de configuration :  
  
 Impossible de déployer l'assembly C:\Program Files\Microsoft\ du système BizTalk  
  
 BizTalk Server 2009\Microsoft.BizTalk.DefaultPipelines.dll. Non spécifié  
  
 exception : fichier ou l’assembly nommé filename.dll ou l’un de ses  
  
 dépendances est introuvable. Le fichier ou l'assembly nommé FileName.dll ou  
  
 l'une de ses dépendances est introuvable.  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si le compte de service réseau ne dispose pas d'un accès en écriture au dossier temporaire de l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Lors de la configuration, la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise WMI (Windows Management Instrumentation) pour déployer les assembys .NET dans la base de données de gestion BizTalk. WMI emprunte l'identité du compte de service réseau lors du déploiement de ces assemblys dans la base de données de gestion BizTalk Management, et ce compte doit donc disposer d'un accès en écriture au dossier temporaire de l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##### <a name="resolution"></a>Résolution  
 Octroyez au compte de service réseau l'accès en écriture au dossier temporaire de l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis exécutez de nouveau le programme de configuration. Pour déterminer le dossier spécifié par la variable d'environnement TEMP, ouvrez une invite de commande sur l'ordinateur, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
```  
echo %TEMP%  
```  
  
#### <a name="configuration-of-the-group-fails-if-the-netbios-name-of-the-computer-running-sql-server-exceeds-15-characters"></a>Échec de la configuration du groupe si le nom NetBIOS de l'ordinateur exécutant SQL Server dépasse 15 caractères  
  
##### <a name="problem"></a>Problème  
 Échec de la configuration du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec erreur similaire à celle indiquée ci-après générée dans le journal de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
 2006-08-29 23:54:00:0902 [avertissement] AdminLib GetBTSMessage : hrErr = 80070547 ;  
  
 Msg=Les informations de configuration n'ont pas pu être lues sur le contrôleur  
  
 de domaine car l'ordinateur n'est pas disponible ou l'accès  
  
 a été refusé.;  
  
##### <a name="cause"></a>Cause  
 Ce problème se produit si la longueur du nom NetBIOS de l'ordinateur exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dépasse 15 caractères. Si le nom NetBIOS dépasse 15 caractères, Windows le tronque à 15 caractères et celui-ci ne correspond donc pas à la première partie du nom FQDN (Fully Qualified Domain Name) ou DNS de cet ordinateur. Si le nom NetBIOS ne correspond pas à la première partie du nom FQDN de l'ordinateur, la configuration du groupe échoue.  
  
##### <a name="resolution"></a>Résolution  
 Limitez le nom NetBIOS de l'ordinateur exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] à 15 caractères, puis exécutez de nouveau la configuration.  
  
> [!NOTE]
>  Si vous modifiez le nom, vous devez redémarrer l'ordinateur.  
  
#### <a name="configuration-fails-if-a-sql-server-database-file-that-has-the-same-name-as-the-specified-database-already-exists-in-the-sql-server-data-folder"></a>Échec de la configuration si le fichier d'une base de données SQL Server a le même nom que la base de données spécifiée qui existe déjà dans le dossier de données SQL Server.  
  
##### <a name="problem"></a>Problème  
 Échec de la configuration avec une erreur similaire à celle indiquée ci-après :  
  
 Impossible de configurer une ou plusieurs bases de données BAM  
  
 Impossible d'ouvrir la base de données demandée dans la connexion « BAMPrimaryImport »  
  
 Échec de l'ouverture de session. Échec d’ouverture de session pour l’utilisateur '*BizTalk\BizTalkUser*'  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si un fichier .mdf ou .ldf qui existe déjà dans le dossier \MSSQL\data de l'ordinateur exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] a le même nom que le fichier .mdf ou .ldf que le programme de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] essaye de créer. Les noms des fichiers .mdf et .ldf créés pour les bases de données sont dérivés du nom de la base de données spécifiée dans le programme de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], une extension .mdf et .ldf étant ajoutée.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, utilisez une des méthodes suivantes :  
  
-   Supprimez les fichiers .mdf ou .ldf dont les noms correspondent à ceux des bases de données que vous créez.  
  
-   Choisissez des noms différents de ceux des fichiers .mdf ou .ldf qui existent déjà dans le dossier \Program Files\Microsoft SQL Server\MSSQL\data de votre serveur SQL.  
  
#### <a name="configuration-fails-on-a-domain-controller-when-specifying-local-accounts"></a>Échec de la configuration sur un contrôleur de domaine lors de la spécification de comptes locaux  
  
##### <a name="problem"></a>Problème  
 Lors de l'exécution du programme de configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un contrôleur de domaine, la configuration échoue si vous avez spécifié un groupe local (par exemple, groupe Utilisateurs hôtes BizTalk) au niveau de l'hôte BizTalkServerApplication ou BizTalkServerIsolatedHost.  
  
##### <a name="cause"></a>Cause  
 Un contrôleur de domaine traite automatiquement un groupe Windows local en tant que groupe Windows de domaine (il n'existe pas de groupe Windows local sur un contrôleur de domaine). Si vous spécifiez un groupe Windows local pour l'hôte lors de l'exécution du programme de configuration, la configuration échoue lors de la tentative de création d'une connexion [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour ce groupe. Le programme de configuration ne désactive pas l'option de groupe Windows local lorsque le serveur est un contrôleur de domaine.  
  
##### <a name="resolution"></a>Résolution  
 Spécifiez les groupes de domaine des hôtes créés lors de la configuration.  
  
#### <a name="configuration-fails-to-create-sql-server-analysis-database-if-the-sql-server-has-been-renamed"></a>Échec de la configuration lors de la création de la base de données SQL Server Analysis si le serveur SQL a été renommé  
  
##### <a name="problem"></a>Problème  
 Si vous avez renommé l'ordinateur sur lequel vous avez installé le serveur d'analyse du serveur SQL Server, le programme de configuration échoue lorsqu'il essaie de créer une nouvelle base de données SQL Server Analysis, et une erreur similaire à celle indiquée ci-après est générée :  
  
 Impossible de se connecter au référentiel.  
  
 Serveur d’analyse : \<nom de l’ordinateur >  
  
 Erreur :  
  
 '\\\\< nom de l’ordinateur\>\MsOLAPRepository$\msmdrep.mdb » n’est pas un chemin d’accès valide.  
  
 Assurez-vous que le nom du chemin d’accès est correct et qu’une  
  
 connexion est établie avec le serveur sur lequel réside le fichier.  
  
##### <a name="cause"></a>Cause  
 Le programme de configuration ne parvient pas à déterminer le nouveau nom de l'ordinateur sur lequel vous avez installé le serveur d'analyse du serveur SQL Server.  
  
##### <a name="resolution"></a>Résolution  
 Exécutez manuellement les étapes suivantes afin de mettre à jour le serveur d'analyse avec le nouveau nom de l'ordinateur :  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server**, pointez sur **Analysis Services**, puis cliquez sur **Analysis Manager**.  
  
2.  Dans le **Analysis Manager** volet de navigation, double-cliquez sur le **serveurs d’analyse** nœud pour le développer.  
  
3.  Cliquez sur le serveur avec la chaîne de connexion référentiel que vous souhaitez modifier, puis sélectionnez **modifier une chaîne de connexion référentiel**.  
  
4.  Dans le **modifier une chaîne de connexion référentiel** boîte de dialogue zone, vérifiez le nom de serveur dans cette chaîne et mettre à jour vers le nouveau nom d’ordinateur s’il est incorrect.  
  
5.  Accédez à l’emplacement suivant : \< *répertoire d’installation*> \Program Files\Microsoft Analysis Services\Bin.  
  
6.  Cliquez sur le **Bin** dossier, puis cliquez sur **partage et sécurité**. Le **propriétés de la Corbeille** boîte de dialogue s’affiche.  
  
7.  Dans le **propriétés de la Corbeille** boîte de dialogue, cliquez sur le **partage** onglet pour vérifier que tous les administrateurs de traitement analytique en ligne (OLAP) ont des autorisations complètes à ce dossier.  
  
#### <a name="artifacts-disappear-from-configuration-database-on-redeployment-of-assemblies-from-visual-studio"></a>Les artefacts disparaissent de la base de données de configuration lors du redéploiement d'assemblys à partir de Visual Studio  
  
##### <a name="problem"></a>Problème  
 Lors du redéploiement d'un projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au niveau projet dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], tous les artéfacts associés faisant référence à ce projet semblent disparaître lorsque la console MMC de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est actualisée.  
  
##### <a name="cause"></a>Cause  
 Pour illustrer la cause de ce problème, prenons l'exemple suivant basé sur une solution BizTalk Server dans lequel l'utilisateur souhaite redéployer le projet de mappage. Notez que les projets de compilation génèrent des assemblys individuels. La figure suivante indique l'état de la solution avant redéploiement. Les relations entre les artefacts sont les suivantes :  
  
-   Orch1, Orch2, Maps, Pipelines et Schemas sont des projets.  
  
-   Orch1 fait référence à Maps, qui a son tour fait référence à Schemas.  
  
-   Orch2 fait référence à Schemas.  
  
-   Pipelines fait référence à Schemas.  
  
 ![](../core/media/bcd-existingbiztalkserversolutionc.gif "bcd_ExistingBizTalkServerSolutionc")  
  
 Si l'utilisateur redéploie le projet Maps à l'aide des paramètres de projet Visual Studio par défaut, les artefacts Orch1, Orch2 et Pipelines disparaissent, comme le montre la figure suivante.  
  
 ![](../core/media/bcd-biztalksolutionwlostartifactsc.gif "bcd_BizTalkSolutionWLostArtifactsc")  
  
 Le redéploiement du projet Maps est un processus en deux étapes qui consiste à annuler le déploiement de l'assembly Maps.dll actuellement déployé, puis à déployer le nouveau fichier Maps.dll. Visual Studio exécute ces étapes automatiquement dans le cadre du processus de redéploiement.  
  
> [!NOTE]
>  La phrase précédente n'est pas strictement correcte car Visual Studio exécute systématiquement certaines étapes, donc rien n'indique que ce soit la méthode appropriée.  
  
 Le point clé est que, pour pouvoir annuler le déploiement d'un assembly BizTalk Server, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] doit annuler le déploiement de tous les assemblys qui en dépendent et dont l'indicateur de déploiement est défini. Dans notre exemple, pour effectuer la première étape d'annulation de déploiement du processus de redéploiement, BizTalk Server doit annuler le déploiement de Orch1.dll (qui dépend de Maps.dll). Lors de l'annulation du déploiement de Maps.dll, [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] annule également celui de Schemas.dll (en partant du principe que son indicateur de déploiement est défini). Pour annuler le déploiement de Schemas.dll, Visual Studio doit annuler celui de Orch2.dll et Pipelines.dll (qui dépendent tous deux de Schemas.dll).  
  
 Il existe un problème dans qui [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] redéploie uniquement Maps.dll et les assemblys qui en dépendent : dans ce cas, Schemas.dll. Ainsi, lorsque l’utilisateur actualise la console MMC de BizTalk Server, les assemblys Orch1, Orch2 et Pipeline semblent avoir disparu, mais Maps.dll et Schemas.dll sont toujours visibles.  
  
##### <a name="resolution"></a>Résolution  
 Pour le projet principal (qui fait référence à d’autres projets), procédez comme suit :  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nœud de la solution.  
  
2.  Cliquez sur **propriétés** pour ouvrir le **les Pages de propriétés de Solution** boîte de dialogue.  
  
3.  Cliquez sur **propriétés de Configuration**, puis cliquez sur **Configuration**.  
  
4.  Désactivez le **déployer** case à cocher pour le projet référencé.  
  
5.  Dans l'Explorateur de solutions, exécutez une nouveau déploiement au niveau solution. Pour ce faire, cliquez sur le nœud solution, puis **déployer la Solution**.  
  
#### <a name="supported-virtual-directory-types"></a>Types de répertoire virtuel pris en charge  
 Lorsque vous référencez des services Web à partir d’une orchestration et toute tentative d’exportation MSI, l’opération d’exportation réussira uniquement si les répertoires virtuels associés sont de type **IIsWebVirtualDir** ou **IIsWebDirectory** . **IIsWebVirtualDir** et **IIsWebDirectory** sont les types de nœuds qui s’affichent dans la métabase IIS. **IIsWebVirtualDir** est un répertoire virtuel avec un **chemin d’accès** propriété pointe vers un dossier de fichier absolu. **IIsWebDirectory** est un répertoire virtuel sans un **chemin d’accès** propriété et fait donc référence à un dossier de fichiers relatif, généralement un sous-dossier d’un autre **IIsWebVirtualDir** ou  **IIsWebDirectory** nœud. Ces deux types sont ceux qui apparaissent généralement dans la hiérarchie de la métabase pour décrire les dossiers.  
  
 Les répertoires virtuels de type **IIsConfigObject** ne sont pas prises en charge et l’exportation MSI échoue dans ce cas. **IIsConfigObject** est un type de nœud de métabase inattendu qui est soit un type de nœud valide que BizTalk Server ne gère pas correctement ou une indication d’une entrée de métabase créée de manière incorrecte (et donc non valide). Dans ce cas, BizTalk Server affichera un message d’erreur similaire à la suivante : l’entrée d’annuaire inattendu « IIS://LM/W3SVC/1/ROOT/BadVdir/ » de type IIsConfigObject.  
  
#### <a name="unable-to-view-group-information-after-removing-stale-logons"></a>Impossible d'afficher les informations sur les groupes après suppression des connexions dépassées  
  
##### <a name="problem"></a>Problème  
 Si, lors de la configuration, vous rencontrez et supprimez des connexions dépassées, vous ne pouvez pas afficher les informations sur les groupes.  
  
##### <a name="cause"></a>Cause  
 Il s'agit d'un problème de configuration connu.  
  
##### <a name="resolution"></a>Résolution  
 Supprimez les connexions du groupe Windows de l'hôte, puis exécutez à nouveau le programme de configuration. Si les informations sur les groupes ne sont toujours pas disponibles, contactez le support technique Microsoft.  
  
##### <a name="cannot-change-computer-name-after-biztalk-server-is-installed"></a>Impossible de modifier le nom de l'ordinateur après l'installation de BizTalk Server  
  
###### <a name="problem"></a>Problème  
 Lorsque vous modifiez le nom d'un ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et que vous redémarrez l'ordinateur, des messages d'erreur peuvent être affichés.  
  
###### <a name="cause"></a>Cause  
 SQL Server ne prend pas en charge la modification du nom de l'ordinateur, de sorte que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend pas en charge la modification du nom de l'ordinateur une fois [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installé et configuré.  
  
###### <a name="resolution"></a>Résolution  
 Il est recommandé de ne pas modifier les noms d'ordinateur après l'installation de BizTalk Server.