---
title: "Problèmes d’installation connus | Documents Microsoft"
description: "Problèmes connus et les problèmes courants et solutions lors de l’installation et la configuration de BizTalk Server"
ms.custom: 
ms.date: 11/30/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d0e707-6b9e-49e1-9f17-19b3bac1229e
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90217a4e80df6f017b451dd7c40f6a1dfe3898ac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="troubleshoot-biztalk-server-setup"></a>Résoudre les problèmes d’installation de BizTalk Server

## <a name="introduction"></a>Introduction  
 Ce Guide de dépannage répertorie des problèmes connus, ainsi que des problèmes les plus courants que vous pouvez rencontrer lors de l’installation de BizTalk Server. Ce guide inclut également des actions personnalisées qui fournit des détails sur la certification BizTalk Server pour le programme de logo Windows Server.  Il vous fournit une liste d’actions personnalisées qui peuvent être effectuées pendant l’opération d’installation de BizTalk Server.  
  
## <a name="review-install-steps"></a>Passez en revue les étapes d’installation  
La majorité des problèmes liés à l'installation de BizTalk Server se produisent quand l'ordinateur BizTalk Server n'a pas été correctement préparé avant l'installation ou quand une installation antérieure de BizTalk Server n'a pas été totalement désinstallée avant une nouvelle tentative d'installation.  
  
Passez en revue les deux listes de vérification ci-dessous, que vous pouvez également trouver dans les Guides d’Installation BizTalk Server, pour vous assurer que vos ordinateurs sont correctement configurés pour prendre en charge de BizTalk Server. Si, après consultation de ces informations, votre tentative d'installation échoue, les conseils de dépannage énoncés dans le reste de document pourront vous être utiles.  
  
1. Installer les programmes et les logiciels requis :

    * [BizTalk Server 2016](set-up-and-install-prerequisites-for-biztalk-server-2016.md)
    * [BizTalk Server 2013 R2 & 2013](prepare-your-computer-for-installation.md)

2. Installez et configurez BizTalk Server :  

    1. Installer BizTalk Server : [BizTalk 2016](install-biztalk-server-2016.md) , [BizTalk 2013 R2 / 2013](install-biztalk-server-2013-and-2013-r2.md)  
    2. [Configurer](configure-biztalk-server.md) BizTalk Server
    3. [Étapes à la configuration](post-configuration-steps-to-optimize-your-environment.md)
  
## <a name="some-edias2-artifacts-are-still-active-after-unconfiguring"></a>Certains artefacts EDI/AS2 sont toujours actifs après annulation de la configuration  
  
**Problème**  
 Une fois que vous annulez la configuration de la fonctionnalité de BizTalk EDI/AS2 de BizTalk Server, certains artefacts de BizTalk Server liés au EDI et AS2 traitement seront toujours actif dans le contexte de la configuration du groupe BizTalk. Ces derniers incluent des pipelines EDI et AS2 ainsi que l'orchestration du traitement par lots. Vous pouvez donc continuer à effectuer un traitement EDI et AS2 de base, même après avoir annulé la configuration de la fonction EDI/AS2 BizTalk.  
  
**Cause**   
 Il y a des ports actifs associés au traitement EDI et AS2. Certains artefacts continuent de fonctionner tandis que ces ports restent actifs.  
  
**Résolution**  
 Pour désactiver tous les artefacts EDI/AS2, vous devez désactiver, arrêter ou supprimer les ports associés au traitement EDI et AS2.  
  
## <a name="after-renaming-biztalk-or-sql-server-computer-the-configuration-wizard-fails"></a>Après avoir renommé l’ordinateur BizTalk ou SQL Server, l’Assistant Configuration échoue  
  
**Problème**  
 Ce problème peut se manifester de différentes manières :  
  
-   Le gestionnaire de configuration charge la page Vue d'ensemble correctement, mais, lorsqu'il tente de configurer une fonctionnalité, les options associées ne s'affichent pas à l'écran.  
  
-   L'Assistant Configuration ne peut pas se connecter au serveur SQL Server.  
  
-   Les tentatives d'annulation de la configuration opèrent sur certaines fonctionnalités, mais pas sur toutes.  
  
**Cause**   
 La configuration de BizTalk Server stocke le nom de réseau de l'ordinateur. Lorsque l’ordinateur est renommé, l’Assistant configuration et le Gestionnaire de configuration ne peut pas localiser le serveur BizTalk Server. Un problème semblable se produit si l'ordinateur SQL Server est renommé après la configuration de BizTalk Server.  
  
**Résolution**  
 Ne renommez pas l'ordinateur BizTalk Server ou l'ordinateur SQL Server. Si un serveur doit être renommé, annulez la configuration des fonctionnalités de BizTalk avant de renommer l'ordinateur. Une fois l'ordinateur renommé, reconfigurez les fonctionnalités de BizTalk Server.  
  
## <a name="business-rules-configuration-wizard-fails"></a>Échec de l’Assistant Configuration de règles d’entreprise  
  
**Problème**  
  
-   L’Assistant de Configuration de règles d’entreprise échoue avec l’erreur « Échec de la Configuration de certains composants et aucun paramètre n’a été appliqué pour ces composants ».  
  
-   Sur les ordinateurs BizTalk Server pour lesquels le moteur de règles d'entreprise a déjà été configuré, le service de mise à jour du moteur de règles ne parvient pas à démarrer et ne peut pas être démarré manuellement.  
  
Lorsque ce problème se produit, une erreur similaire à ce qui suit peut être générée dans le journal de l'application de l'ordinateur BizTalk Server :  
  
```  
Service could not be started. : System.Net.Sockets.SocketException (10061): No connection could be made because the target machine actively refused it ::1:3132  
  
```  
  
**Cause**   
 Le Centre de protection Microsoft contre les programmes malveillants a publié un fichier de signature le 9 mars 2010, qui permet de se prémunir contre une menace possible de SettingsModifier:Win32/PossibleHostsFileHijack. Ce fichier de signature mis à jour peut entraîner la mise à jour du fichier HOSTS local par les logiciels Microsoft de détection des programmes malveillants tels que Windows Defender en vue d'atténuer la menace de SettingsModifier:Win32/PossibleHostsFileHijack. Ces modifications peuvent empêcher le démarrage du service de mise à jour du moteur de règles BizTalk Server.  
  
**Résolution**  
 Mettez à jour le fichier HOSTS local pour inclure la ligne suivante :  
  
```  
127.0.0.1         localhost  
```  
  
 Le fichier HOSTS se trouve dans le répertoire %systemroot%\drivers\etc\.  
  
> [!NOTE]
> Consultez la signature Microsoft Malware Protection Center à mettre à jour que les adresses de la menace possible de [settingsmodifier : Win32 / PossibleHostsFileHijack](http://go.microsoft.com/fwlink/?LinkId=146221).  
  
## <a name="configuration-logging"></a>Consignation des informations de configuration  
 Le programme de configuration écrit des informations détaillées dans un fichier journal de configuration qui, par défaut, se trouve dans le répertoire temp de l’ordinateur exécutant BizTalk Server. Pour déterminer le dossier spécifié par la variable d'environnement TEMP, ouvrez une invite de commande sur cet ordinateur, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
 **echo %Temp%**  
  
 Le fichier journal contient un récapitulatif des étapes de configuration effectuées, ainsi que des informations de diagnostic sur les échecs susceptibles de survenir au cours du processus de configuration. En cas d'erreur de configuration, ouvrez le journal dans un éditeur de texte tel que le Bloc-notes, puis recherchez les causes possibles.  
  
## <a name="troubleshooting-tools"></a>Outils de résolution des problèmes  
 SQL Server Profiler, Filemon ou Regmon vous permettent de collecter des informations supplémentaires sur les échecs de configuration. Consultez [outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md).  
  
### <a name="configuration-fails-when-biztalk-and-sql-are-installed-on-separate-computers"></a>Échec de la configuration lorsque BizTalk et SQL sont installés sur des ordinateurs distincts  
  
**Problème**  
 Échec de la configuration avec erreurs similaires à celle indiquée ci-après lors de la tentative de configuration du composant d'authentification unique de l'entreprise :  
  
```
An error occurred while attempting to access the SSO database.  
Function: FieldInfoCreate  
```
  
 -ou-  
  
```Failed to enable the Single Sign-On (SSO) Service (error code 0X800706BA)```  
  
**Cause**    
 Si BizTalk Server et SQL Server sont installés sur des ordinateurs différents, puis les opérations de configuration sont effectuées dans le contexte d’une transaction Microsoft Distributed Transaction Coordinator (MSDTC) et la fonctionnalité MSDTC doit être disponible sur le réseau entre ces ordinateurs. Si la fonctionnalité MSDTC n’est pas disponible sur le réseau entre les ordinateurs exécutant BizTalk Server et SQL Server, cette erreur peut se produire.  
  
**Résolution**    
Utilisez [Troubleshooting Problems with MSDTC](https://support.microsoft.com/help/306843/how-to-troubleshoot-ms-dtc-firewall-issues) pour vérifier la fonctionnalité MSDTC sur le réseau entre les ordinateurs exécutant BizTalk Server et SQL Server.  
  
### <a name="antivirus-software-interferes-with-configuration-and-causes-configuration-failures"></a>Le logiciel antivirus interfère avec la configuration et provoque des échecs de configuration  
  
**Problème**   
 Échec de la configuration de BizTalk Server, lorsque le logiciel antivirus détermine à tort que le programme de configuration est un virus.  
  
**Cause**  
 Le logiciel antivirus n’a pas été mis à jour pour inclure le programme de configuration de BizTalk Server comme un programme légitime (non virus).  
  
**Résolution**  
 Configurez le programme antivirus pour reconnaître le programme de configuration de BizTalk Server comme un programme légitime (non virus) ou bien désactiver temporairement le logiciel antivirus pendant que le programme de configuration est en cours d’exécution.  
  
### <a name="configuration-fails-with-a-file-or-assembly-name-filenamedll-or-one-of-its-dependencies-was-not-found-error"></a>Échec de la configuration avec erreur « Le fichier ou l'assembly nommé FileName.dll ou l'une de ses dépendances est introuvable »  
  
**Problème**  
 Une erreur similaire à celle indiquée ci-après s'affiche lors du processus de configuration :  
  
 Impossible de déployer l’assembly « C:\Program Files\Microsoft\BizTalk Server 20xx\Microsoft.BizTalk.DefaultPipelines.dll. Exception non spécifiée : fichier ou assembly nommé filename.dll ou l’une de ses dépendances, est introuvable. »  
  
**Cause**  
 Cette erreur peut se produire si le Service réseau compte ne dispose pas des autorisations d’écriture sur le dossier temp sur l’ordinateur exécutant BizTalk Server. Lors de la configuration, configuration de BizTalk Server utilise Windows Management Instrumentation (WMI) pour déployer des assemblys .NET pour la base de données de gestion BizTalk. WMI emprunte l’identité du compte Service réseau lors du déploiement de ces assemblys à la base de données de gestion BizTalk et par conséquent, le compte Service réseau doit avoir un accès en écriture au dossier temporaire sur l’ordinateur exécutant BizTalk Server.  
  
**Résolution**  
 Accordez au compte Service réseau d’accès en écriture au dossier temporaire sur l’ordinateur exécutant BizTalk Server et réexécutez le programme de configuration. Pour déterminer le dossier spécifié par la variable d'environnement TEMP, ouvrez une invite de commande sur l'ordinateur, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
```  
echo %TEMP%  
```  
  
### <a name="configuration-fails-if-a-sql-server-database-file-that-has-the-same-name-as-the-specified-database-already-exists-in-the-sql-server-data-folder"></a>Échec de la configuration si le fichier d'une base de données SQL Server a le même nom que la base de données spécifiée qui existe déjà dans le dossier de données SQL Server.  
  
#### <a name="problem"></a>Problème  
 Échec de la configuration avec une erreur similaire à celle indiquée ci-après :  
  
```
Failed to set up BAM database(s)  
  
Cannot open database requested in login 'BAMPrimaryImport'  
  
Logon fails. Logon failed for user '*BizTalk\BizTalkUser*'  
```
  
**Cause**  
 Cette erreur peut se produire si un fichier .mdf ou un fichier .ldf existe déjà dans le dossier \MSSQL\data de l’ordinateur exécutant SQL Server qui a le même nom que le fichier .mdf ou le fichier .ldf qui tente de créer le programme de configuration de BizTalk Server. Les noms de fichier .mdf et .ldf créés pour les bases de données sont dérivées du nom de la base de données qui est spécifié dans le programme de configuration de BizTalk Server avec un .mdf et .ldf extension ajoutée.  
  
**Résolution**  
 Pour résoudre ce problème, utilisez une des méthodes suivantes :  
  
-   Supprimez les fichiers .mdf ou .ldf dont les noms correspondent à ceux des bases de données que vous créez.  
  
-   Choisissez des noms différents de ceux des fichiers .mdf ou .ldf qui existent déjà dans le dossier \Program Files\Microsoft SQL Server\MSSQL\data de votre serveur SQL.  
  
### <a name="configuration-fails-on-a-domain-controller-when-specifying-local-accounts"></a>Échec de la configuration sur un contrôleur de domaine lors de la spécification de comptes locaux  
  
**Problème**  
 Lors de l’exécution des programme de configuration de BizTalk Server sur un contrôleur de domaine, la configuration échoue si vous avez spécifié un groupe local (par exemple, groupe d’utilisateurs hôtes BizTalk) pour l’hôte BizTalkServerApplication ou BizTalkServerIsolatedHost.  
  
**Cause**  
 Un contrôleur de domaine traite automatiquement un groupe Windows local en tant que groupe Windows de domaine (il n'existe pas de groupe Windows local sur un contrôleur de domaine). Si vous avez spécifié un groupe Windows local pour l’hôte lors de l’exécution du programme de configuration, configuration échoue lorsque vous tentez de créer une ouverture de session SQL Server pour le groupe. Le programme de configuration ne désactive pas l'option de groupe Windows local lorsque le serveur est un contrôleur de domaine.  
  
**Résolution**  
 Spécifiez les groupes de domaine des hôtes créés lors de la configuration.  
  
### <a name="configuration-fails-to-create-sql-server-analysis-database-if-the-sql-server-has-been-renamed"></a>Échec de la configuration lors de la création de la base de données SQL Server Analysis si le serveur SQL a été renommé  
  
**Problème**  
 Si vous avez renommé l'ordinateur sur lequel vous avez installé le serveur d'analyse du serveur SQL Server, le programme de configuration échoue lorsqu'il essaie de créer une nouvelle base de données SQL Server Analysis, et une erreur similaire à celle indiquée ci-après est générée :  

```  
 Cannot connect to the repository.  
  
 Analysis server: <machine name\>  
  
 Error:  
  
 '\\\\<machine name\>\MsOLAPRepository$\msmdrep.mdb' is not a valid path.  
  
 Make sure that you correctly spell the path name and that you are  
  
 connected to the server on which the file resides.  
```
  
**Cause**  
 Le programme de configuration ne parvient pas à déterminer le nouveau nom de l'ordinateur sur lequel vous avez installé le serveur d'analyse du serveur SQL Server.  
  
**Résolution**  
 Exécutez manuellement les étapes suivantes afin de mettre à jour le serveur d'analyse avec le nouveau nom de l'ordinateur :  
  
1.  Sur le serveur SQL Server, ouvrez **Microsoft SQL Server**, sélectionnez **Analysis Services**, puis cliquez sur **Analysis Manager**.  
  
2.  Dans le **Analysis Manager** volet de navigation, double-cliquez sur le **serveurs d’analyse** nœud pour le développer.  
  
3.  Cliquez sur le serveur avec la chaîne de connexion référentiel que vous souhaitez modifier, puis sélectionnez **modifier une chaîne de connexion référentiel**.  
  
4.  Dans le **modifier une chaîne de connexion référentiel** boîte de dialogue zone, vérifiez le nom de serveur dans cette chaîne et mettre à jour vers le nouveau nom d’ordinateur s’il est incorrect.  
  
5.  Accédez à l’emplacement suivant : <*répertoire d’installation*> \Program Files\Microsoft Analysis Services\Bin.  
  
6.  Cliquez sur le **Bin** dossier, puis cliquez sur **partage et sécurité**. Le **propriétés de la Corbeille** boîte de dialogue s’affiche.  
  
7.  Dans le **propriétés de la Corbeille** boîte de dialogue, cliquez sur le **partage** onglet pour vérifier que tous les administrateurs de traitement analytique en ligne (OLAP) ont des autorisations complètes à ce dossier.  
  
### <a name="artifacts-disappear-from-configuration-database-on-redeployment-of-assemblies-from-visual-studio"></a>Artefacts disparaissent de la base de données de Configuration lors du redéploiement d’assemblys à partir de Visual Studio  
  
**Problème**  
 Quand un projet BizTalk Server est redéployé au niveau du projet dans Visual Studio, tous les artefacts contenus dans le projet qui référence le projet en cours de redéploiement semblent disparaître lors de l’actualisation de la console MMC de BizTalk Server.  
  
**Cause**  
 Pour illustrer la cause de ce problème, prenons l'exemple suivant basé sur une solution BizTalk Server dans lequel l'utilisateur souhaite redéployer le projet de mappage. Notez que les projets de compilation génèrent des assemblys individuels. La figure suivante indique l'état de la solution avant redéploiement. Les relations entre les artefacts sont les suivantes :  
  
-   Orch1, Orch2, Maps, Pipelines et Schemas sont des projets.  
  
-   Orch1 fait référence à Maps, qui a son tour fait référence à Schemas.  
  
-   Orch2 fait référence à Schemas.  
  
-   Pipelines fait référence à Schemas.  
  
![bcd_ExistingBizTalkServerSolutionc](../install-and-config-guides/media/bcd_ExistingBizTalkServerSolutionc.gif)  
  
Si l'utilisateur redéploie le projet Maps à l'aide des paramètres de projet Visual Studio par défaut, les artefacts Orch1, Orch2 et Pipelines disparaissent, comme le montre la figure suivante.  
  
![bcd_BizTalkSolutionWLostArtifactsc](../install-and-config-guides/media/bcd_BizTalkSolutionWLostArtifactsc.gif)  
  
 Le redéploiement du projet Maps est un processus en deux étapes qui consiste à annuler le déploiement de l'assembly Maps.dll actuellement déployé, puis à déployer le nouveau fichier Maps.dll. Visual Studio exécute ces étapes automatiquement dans le cadre du processus de redéploiement.  
  
> [!NOTE]
>  La phrase précédente n'est pas strictement correcte car Visual Studio exécute systématiquement certaines étapes, donc rien n'indique que ce soit la méthode appropriée.  
  
 Le point essentiel est que, pour pouvoir annuler le déploiement d’un assembly BizTalk Server, Visual Studio doit annuler le déploiement de tous les assemblys qui dépendent de cet assembly qui ont le jeu d’indicateur de déploiement. Dans notre exemple, pour effectuer la première étape d'annulation de déploiement du processus de redéploiement, BizTalk Server doit annuler le déploiement de Orch1.dll (qui dépend de Maps.dll). Lors de l’annulation du déploiement de Maps.dll, Visual Studio annule également celui de Schemas.dll (en supposant qu’il a l’indicateur de déploiement définie). Pour annuler le déploiement de Schemas.dll, Visual Studio doit annuler celui de Orch2.dll et Pipelines.dll (qui dépendent tous deux de Schemas.dll).  
  
 Il existe un problème dans la mesure où Visual Studio redéploie uniquement Maps.dll et les assemblys qui en dépendent : dans ce cas, Schemas.dll. Ainsi, lorsque l’utilisateur actualise la console MMC de BizTalk Server, les assemblys Orch1, Orch2 et Pipeline semblent avoir disparu, mais Maps.dll et Schemas.dll sont toujours visibles.  
  
**Résolution**  
 Pour le projet principal (qui fait référence à d’autres projets), procédez comme suit :  
  
1.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nœud de la solution.  
  
2.  Cliquez sur **propriétés** pour ouvrir le **les Pages de propriétés de Solution** boîte de dialogue.  
  
3.  Cliquez sur **propriétés de Configuration**, puis cliquez sur **Configuration**.  
  
4.  Désactivez le **déployer** case à cocher pour le projet référencé.  
  
5.  Dans l'Explorateur de solutions, exécutez une nouveau déploiement au niveau solution. Pour ce faire, cliquez sur le nœud solution, puis **déployer la Solution**.  
  
### <a name="supported-virtual-directory-types"></a>Types de répertoire virtuel pris en charge  
 Lorsque vous référencez des services Web à partir d’une orchestration et toute tentative d’exportation MSI, l’opération d’exportation réussira uniquement si les répertoires virtuels associés sont de type **IIsWebVirtualDir** ou **IIsWebDirectory** . **IIsWebVirtualDir** et **IIsWebDirectory** sont les types de nœuds qui s’affichent dans la métabase IIS. **IIsWebVirtualDir** est un répertoire virtuel avec un **chemin d’accès** propriété pointe vers un dossier de fichier absolu. **IIsWebDirectory** est un répertoire virtuel sans un **chemin d’accès** propriété et fait donc référence à un dossier de fichiers relatif, généralement un sous-dossier d’un autre **IIsWebVirtualDir** ou  **IIsWebDirectory** nœud. Ces deux types sont ceux qui apparaissent généralement dans la hiérarchie de la métabase pour décrire les dossiers.  
  
 Les répertoires virtuels de type **IIsConfigObject** ne sont pas prises en charge et l’exportation MSI échoue dans ce cas. **IIsConfigObject** est un type de nœud de métabase inattendu qui est soit un type de nœud valide que BizTalk Server ne gère pas correctement ou une indication d’une entrée de métabase créée de manière incorrecte (et donc non valide). Dans ce cas, BizTalk Server affichera un message d’erreur similaire à la suivante : l’entrée d’annuaire inattendu « IIS://LM/W3SVC/1/ROOT/BadVdir/ » de type IIsConfigObject.  
  
### <a name="unable-to-view-group-information-after-removing-stale-logons"></a>Impossible d'afficher les informations sur les groupes après suppression des connexions dépassées  
  
**Problème**  
 Si, lors de la configuration, vous rencontrez et supprimez des connexions dépassées, vous ne pouvez pas afficher les informations sur les groupes.  
  
**Cause**  
 Il s'agit d'un problème de configuration connu.  
  
**Résolution**  
 Supprimez les connexions du groupe Windows de l'hôte, puis exécutez à nouveau le programme de configuration. Si les informations sur les groupes ne sont toujours pas disponibles, contactez le support technique Microsoft.  
  
### <a name="cannot-change-computer-name-after-biztalk-server-is-installed"></a>Impossible de modifier le nom de l'ordinateur après l'installation de BizTalk Server  
  
**Problème**  
 Lorsque vous modifiez le nom de l’ordinateur sur un ordinateur exécutant BizTalk Server et que vous redémarrez les messages (redémarrage) sur l’ordinateur, une erreur peut se produire.  
  
**Cause**  
 SQL Server ne prend pas en charge la modification du nom de l’ordinateur, BizTalk Server ne prend pas en charge la modification du nom de l’ordinateur une fois que BizTalk Server est installé et configuré.  
  
**Résolution**  
 Il est recommandé de ne pas modifier les noms d'ordinateur après l'installation de BizTalk Server.  
  
### <a name="known-issues-with-enterprise-single-sign-on"></a>Problèmes connus avec l'authentification unique de l'entreprise  
 Cette section décrit des problèmes d'installation et de configuration susceptibles de se produire avec l'authentification unique (SSO) de l'entreprise.  
  
##### <a name="entsso-service-fails-to-start"></a>Service ENTSSO ne démarre pas  
  
**Problème**  
 Le service ENTSSO ne démarre pas.  
  
**Cause**  
 Si le service ENTSSO n'est pas exécuté sous un compte d'administrateur SSO valide, il ne démarrera pas.  
  
**Résolution**  
 Spécifiez un compte d'administrateur SSO valide pour le service ENTSSO et redémarrez ce dernier à partir du composant logiciel enfichable Gestionnaire de contrôle des services (SCM).  
  
##### <a name="biztalk-services-dependent-on-the-enterprise-single-sign-on-service-entsso-fail-to-start-after-a-reboot"></a>Échec du démarrage des services BizTalk dépendant du service de l'authentification unique de l'entreprise (ENTSSO) après un redémarrage.  
  
**Problème**  
 BTSSvc$BizTalkServerApplication possède une dépendance vis-à-vis du service de l'authentification unique de l'entreprise (ENTSSO) et risque d'expirer lors du démarrage ou après un redémarrage.  
  
**Cause**  
 Le service de l'authentification unique de l'entreprise prend approximativement 3 minutes pour démarrer.  
  
**Résolution**  
 Configurez le service « Groupe BizTalk des services BizTalk : BizTalkServerApplication » avec l'option de type de démarrage Automatique (début différé). Le démarrage du service sera ainsi initié après la fin de l'exécution des routines de démarrage des services automatiques.  
  
##### <a name="cannot-access-an-affiliate-application"></a>Impossible d'accéder à une application associée  
  
**Problème**  
 Le service SSO de l'entreprise désactive une application associée si le compte d'administrateur d'application qui lui correspond n'est pas valide.  
  
**Cause**  
 Le compte d'administrateur de l'application SSO n'est pas valide.  
  
**Résolution**  
 Assurez-vous que le compte d'administrateur de l'application SSO est valide avant de créer une application associée. Vous devez ensuite activer l'application associée pour utiliser l'application.  
  
##### <a name="rpc-error-occurs-when-connecting-to-a-client-computer"></a>Erreur RPC se produit lors de la connexion à un ordinateur client  
  
**Problème**  
 Lorsque vous exécutez une commande comme **ssomanage - displayapp** *< applicationname\>*, où l’ordinateur tente de se connecter à un serveur SSO distant pour récupérer les informations, vous recevez le l’erreur suivante : erreur : 0x800706BA : le serveur RPC n’est pas disponible.  
  
**Cause**  
 Cette erreur se produit lorsque vous ne spécifiez pas les informations de serveur correctes ou lorsque le service SSO n'est pas disponible sur le serveur distant.  
  
**Résolution**  
  
-   Suivez les étapes de [définition du serveur SSO](../core/how-to-set-the-sso-server.md) pour vous assurer que vous êtes connecté au serveur SSO approprié.  
  
-   Assurez-vous que le service SSO est activé et qu'il s'exécute sur le serveur SSO auquel vous vous connectez.  
  
##### <a name="master-secret-is-missing-or-corrupt"></a>Secret principal est manquant ou endommagé  
  
**Problème**  
 Le secret principal est manquant ou corrompu. Il est normalement généré lors de la configuration. S'il est manquant, l'un des messages suivants s'affiche dans le journal des événements au moment du démarrage du service SSO de l'entreprise.  
  
```
MessageId=10520  
Severity=Warning  
SSO_WARN_NO_SECRETS  
MessageId=10565  
Severity=Error  
SSO_ERROR_SECRET_VALIDATE_FAILED  
MessageId=10521  
Severity=Error  
SSO_ERROR_SECRETS_NOT_LOADED  
```

**Cause**  
 Ce problème peut se produire si un secret a été généré pendant que le service SSO de l'entreprise était exécuté avec un certain compte de service, et que ce compte a ensuite été modifié. Le secret est stocké dans le registre sous une forme chiffrée et son chiffrement est réalisé à l'aide d'une clé en fonction de l'identité du compte de service (sous lequel ENTSSO est exécuté).  
  
**Résolution**  
 Remplacez le compte de service sous lequel ENTSSO est exécuté par le compte de service utilisé lorsque le secret principal a été créé.  
  
1.  Sauvegardez le secret principal. Consultez [sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md).  
  
2.  Arrêtez les services SSO de l'entreprise.  
  
3.  Modifiez le compte du service.  
  
4.  Redémarrez SSO et ignorez les erreurs du journal des événements relevant l'éventuelle corruption d'un secret.  
  
5.  Restaurez le secret principal. Consultez [restaurer le Secret principal](../core/how-to-restore-the-master-secret.md).  
  
### <a name="custom-action"></a>Action personnalisée  
 Cette rubrique fournit des détails sur la certification BizTalk Server pour le programme de logo Windows Server. Vous pouvez exécuter les actions personnalisées suivantes au cours de l'installation de BizTalk Server.  
  
|Action personnalisée| Description|  
|-------------------|-----------------|  
|ReadComplusData|Lit les tables COM+ personnalisées, crée des documents XML et les enregistre dans la propriété Complus_XML_Data.|  
|SchedXmlConfig|Utilisé pour la configuration des ordinateurs contenant des données RFID.|  
|CheckBaseEDI|Vérifie la présence d'une ancienne version d'EDI|  
|CheckMQSeries|Vérifie la présence de MQSeries|  
|CheckNET30Vista|Vérifie la présence de WCF|  
|CheckWSSV3SP1|Vérifie la présence de Windows SharePoint Services 3.0 SP1.|  
|CheckWSSV4|Vérifie la présence de Windows SharePoint Services 4|  
|GetFrameworkPath|Définit les propriétés du programme d'installation qui contient le chemin d'installation de Microsoft .Net Framework 4 et 2.0.|  
|Set_BAMClientExcelDir|Crée un objet application Excel qui définit une propriété spécifiant le chemin d'accès à la bibliothèque Microsoft Office dans le programme d'installation.|  
|Set_CurrentUser|Définit le domaine et le nom de l'utilisateur actuel|  
|ViewInstallGuide|Lance le guide d'installation de BizTalk Server à partir du répertoire source de l'installation.|  
|CA_CheckSTSLanguage|Définit la propriété STS_Language_Property lorsque les langues définies pour WSS et BizTalk sont identiques.|  
|CA_CleanupRegistry|Lorsque vous désinstallez BizTalk Server, cette action nettoie les entrées de Registre créées lors de la configuration de BizTalk Server.|  
|CA_CleanupRegistry_OldProducts|Nettoie les entrées de Registre qui appartiennent à une ancienne version de BizTalk Server et sont inutiles dans le cadre d'une nouvelle installation de BizTalk Server.|  
|CA_RemovePatches|Supprime les mises à jour de Microsoft BizTalk Server lors de la désinstallation de BizTalk Server.|  
|CA_ResolveWellKnownNames|Crée les propriétés du programme d'installation avec des noms connus et leur affecte le SID correspondant.|  
|CA_SaveTargetVSVersionToRegistry|Définit une propriété TargetVSVersion_Property sur la valeur d'une version prise en charge de Visual Studio.|  
|CA_StopServices|Arrête les services IISAdmin, de mise à jour du moteur de règles et du sous-système EDI.|  
|CleanupUsersKeys|Supprime les entrées BizTalk Server de la clé de Registre HKEY_CURRENT_USER.|  
|DevEnvRunning|Vérifie si Visual Studio est en cours d'exécution.|  
|ValidateINSTALLDIR|Valide le format du répertoire d'installation de BizTalk Server|  
|StartHostInstances|Lance les instances d'hôte BizTalk Server.|  
|StopHostInstances|Arrête les instances d'hôte BizTalk Server.|  
|MQSUnConfig|Lance l'Assistant Configuration pour annuler la configuration de l'agent MQSeries.|  
|LaunchConfigFmk|Lance l'Assistant Configuration de BizTalk Server|  
|CHKASPNET|Vérifie l'état d'installation d'ASP.NET|  
|CHKIIS|Vérifie l'état d'installation d'IIS|  
|TBExpired|Vérifie si la période d'évaluation « Timebomb » est arrivée à échéance|  
|BrandSKU|Met à jour la valeur de la période d'évaluation « Timebomb » qui dépend de l'installation du SKU.|  
|CA_ERROR|Renvoie l'échec de l'installation|  
|InstallComplus|Installe les composants et applications ComPlus.|  
|BAM_Add_Perf_Silent|Installe des compteurs de performance à des fins d'analyse BAM|  
|RegsvcsApplicationDeployment|Exécute Regsvcs.exe (outil .NET Services Installation) sur les DLL d'application COM+ de déploiement de BizTalk|  
|RegsvcsDeployment|Exécute Regsvcs.exe sur les DLL|  
|RegsvcsMQSAdapter|Exécute Regsvcs.exe sur les DLL|  
|RegsvcsSQLAdapter|Exécute Regsvcs.exe sur les DLL|  
|WMI_Add_MSBTS_Silent|Inscrit l'espace de noms et les classes BizTalk Server auprès du service WMI.|  
|LaunchConfigFmk_SlashUP|Annule la configuration de BizTalk Server|  
|CleanupComplus|Annule l'installation des composants et applications ComPlus.|  
|RemoveSKU|Supprime les données de la période d'évaluation « Timebomb » de BizTalk Server.|  
|BAM_Remove_Perf|Annule l'installation des compteurs de performance à des fins d'analyse BAM.|  
|LoadBTSCounters|Charge les compteurs de performance BizTalk Server.|  
|RegisterBtprojExtn|Inscrit l'extension de fichier de projet BizTalk (.btproj)|  
|UnRegisterBtprojExtn|Annule l'inscription de l'extension de fichier de projet BizTalk (.btproj)|  
|UnRegsvcsApplicationDeployment|Exécute Regsvcs.exe sur certains fichiers DLL lorsque vous désinstallez BizTalk Server|  
|UnRegsvcsDeployment|Exécute Regsvcs.exe sur certains fichiers DLL lorsque vous désinstallez BizTalk Server|  
|UnRegsvcsMQSAdapter|Exécute Regsvcs.exe sur certains fichiers DLL lorsque vous désinstallez BizTalk Server|  
|UnRegsvcsSQLAdapter|Exécute Regsvcs.exe sur certains fichiers DLL lorsque vous désinstallez BizTalk Server|  
|UnloadBTSCounters|Annule le chargement des compteurs de performance BizTalk Server.|  
|WMI_Remove_MSBTS|Supprime l'espace de noms BizTalk Server du service WMI.|  
|RegisterComsvcs|Exécute regsvr32.exe sur le fichier comsvcs.dll de manière silencieuse.|  
|DevenvSetupUninstall|Exécute DevEnv.exe /Setup/resetskippkgs.|  
|RollbackComplus|Restaure l'installation des composants et applications ComPlus.|  
|ResRegsvcsMQSAdapter|Exécute regsvcs.exe sur un fichier binaire donné|  
|ResRegsvcsSQLAdapter|Exécute regsvcs.exe sur un fichier binaire donné|  
|RestoreRegsvcsApplicationDeployment|Ajoute le chemin d'accès de l'infrastructure avec Microsoft.BizTalk.ApplicationDeployment.Engine.dll.|  
|RestoreRegsvcsDeployment|Ajoute le chemin d'accès de l'infrastructure avec Microsoft.BizTalk.ApplicationDeployment.Engine.dll.|  
|BrandSKURollback|Restaure les informations de SKU enregistrées en cas d'échec d'installation.|  
|CA_RestartServices_rollback|Redémarre les services arrêtés.|  
|RemoveSKURollback|Met à jour les valeurs de SKU à partir du Registre.|  
|BAM_Res_Perf_Silent|Inscrit Microsoft.BizTalk.Bam.EventObservation.dll comme DLL de compteur de performance BAM durant une installation silencieuse.|  
|BAM_Rollback_Perf|Annule l'inscription de Microsoft.BizTalk.Bam.EventObservation.dll comme DLL de compteur de performance BAM|  
|RBKRegsvcsMQSAdapter|Exécute regsvcs.exe sur un fichier binaire donné.|  
|RBKRegsvcsSQLAdapter|Exécute regsvcs.exe sur un fichier binaire donné.|  
|RestoreBTSCounters|Restaure la propriété avec le nom de fichier .ini du compteur de performance.|  
|RollbackBTSCounters|Exécute la commande unlodctr BTSSvc.3.0.|  
|RollbackRegsvcsApplicationDeployment|Configure [FrameworkPath] &#124; [INSTALLDIR] Microsoft.BizTalk.ApplicationDeployment.Engine.dll pour les scénarios d’échec de l’installation.|  
|RollbackRegsvcsDeployment|Appelle regsvcs.exe durant les scénarios de désinstallation/restauration.|  
|WMI_Restore_MSBTS_Silent|Appelle mofcomp pour inscrire les schémas WMI.|  
|WMI_Rollback_MSBTS|Supprime l'espace de noms BizTalk Server du service WMI.|  
|CA_RestartServices_commit|Redémarre les services arrêtés.|  
|DevenvSetup|Exécute DevEnv.exe /Setup /resetskippkgs au cours du processus d'installation/d'annulation de l'installation de BizTalk Server.|  
|ExecXmlConfig|Apporte des modifications de configuration au fichier machine.config pour les données RFID.|  
|ExecXmlConfigRollback|Apporte des modifications de configuration au fichier machine.config pour les données RFID.|  
  
#### <a name="running-biztalk-components"></a>Exécution des composant BizTalk  
 Le tableau suivant répertorie les composants BizTalk que vous devez exécuter à l'aide de privilèges d'administrateur ou des privilèges les plus élevés disponibles.  
  
|Chemin d'accès au dossier|Nom de fichier|Privilèges d'utilisateur|  
|-----------------|---------------|---------------------|  
|\Program fichiers (x86) \Common Files\Microsoft shared\Help 9\Microsoft Document Explorer 2008|Install.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|BTSHatApp.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|BTSMMCLauncher.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|BtsWcfServicePublishingWizard.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|BTSWebSvcWiz.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|Configuration.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|REDeployWiz.exe|Privilèges les plus élevés disponibles|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*|Setup.exe|Privilèges d'administrateur|  
|\Program files (x86) \Microsoft BizTalk Server *votre version*\XSD Schema\EDI|MicrosoftEdiXSDTemplates.exe|Fichier .exe à extraction automatique|  
|\Program fichiers (x86) \Microsoft UDDI Services\config|Configuration .exe|Privilèges d'administrateur|  
|\Program Files\ Microsoft BizTalk RFID\bin|BTSMMCLauncher.exe|Privilèges les plus élevés disponibles|  
|\Program Files\Microsoft BizTalk RFID\BREConfi guration|Configuration .exe|Privilèges d'administrateur|  
