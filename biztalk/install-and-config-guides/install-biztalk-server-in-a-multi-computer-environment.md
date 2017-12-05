---
title: Installation de BizTalk Server dans un environnement multiserveur | Documents Microsoft
description: "Guide d’installation et le programme d’installation multiserveur lorsque BizTalk et SQL Server sont installés sur des ordinateurs différents, y compris BAM"
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
ms.openlocfilehash: 26100e268e6dd657369bb044461c42a6ba0b5a9c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="install-biztalk-server-in-a-multi-computer-environment"></a>Installer BizTalk Server dans un environnement multiserveur

## <a name="overview"></a>Vue d'ensemble

Il existe de nombreux éléments à prendre en compte lors de la planification d’une installation multiserveur de Microsoft® BizTalk® Server. Bien souvent, l’infrastructure réseau existe et que BizTalk Server doit coexister avec d’autres applications réseau. Ce guide décrit certaines des considérations qui s’appliquent pour le serveur BizTalk et l’installation de l’analyse BAM (Business Activity) dans un déploiement multiserveur distribué. Ces informations permettent de planifier l’installation et la configuration de BizTalk Server et d’analyse BAM (Business Activity) et des applications et composants qu'il dépend.

Le guide d’installation de serveur unique contient des procédures importantes et plus d’informations qui ne sont pas dupliqués dans ce document. Par exemple, les informations suivantes sont décrite en détail dans le guide d’installation de serveur unique :

- procédures d'installation détaillées ;
- description des fonctionnalités et dépendances de BizTalk Server ;
- détails des paramètres de configuration de base de BizTalk Server ;
- les configurations matérielle et logicielle requises ;
- la liste des composants redistribuables des fichiers CAB.

## <a name="high-availability"></a>Haute disponibilité
BizTalk Server fournit une solution de haute disponibilité qui utilise le clustering (NLB) et le clustering de basculement d’équilibrage de la charge réseau et SQL Server Always On à l’aide de groupes de disponibilité (AG). Une solution haute disponibilité permet de réduire le temps mort en cas de panne matérielle ou logicielle. 

**Clusters d’équilibrage de charge réseau et de basculement** se complètent mutuellement dans des architectures complexes. Cluster d’équilibrage de charge réseau est utilisé pour charger les équilibrer les demandes entre les serveurs web frontaux. Le clustering avec basculement offre une haute disponibilité pour les hôtes BizTalk Server de type In-process, le serveur de secret principal du système d'authentification unique de l'entreprise et les bases de données BizTalk Server. Cela est généralement utilisé pour les environnements sur site. Bonnes ressources sont les suivantes : 

* [BizTalk Server : Guide de survie de haute disponibilité](http://social.technet.microsoft.com/wiki/contents/articles/6532.biztalk-server-high-availability-survival-guide.aspx)

* [Amélioration de la tolérance de pannes dans BizTalk Server à l’aide d’un cluster de basculement Windows Server ou Windows Server](http://go.microsoft.com/fwlink/p/?LinkId=154499)

**SQL Server toujours sur AG** peut être utilisé avec les environnements locaux et machines virtuelles. Prise en charge des groupes de disponibilité commence par BizTalk Server 2016 et est pris en charge dans les versions plus récentes de BizTalk Server. Groupe de disponibilité comprend des réplicas de base de données primaire et les réplicas de base de données secondaire. BizTalk Server se connecte aux réplicas de base de données primaire, tandis que les réplicas de base de données secondaire fournissent une redondance et de basculement. [Groupes de disponibilité AlwaysOn (SQL Server)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/always-on-availability-groups-sql-server) fournit des détails sur le fonctionnement du groupe de disponibilité. 

[BizTalk à haute disponibilité à l’aide de SQL Server toujours sur AG](../core/high-availability-using-sql-server-always-on-availability-groups.md) fournit plus de détails à partir d’une perspective de BizTalk.

## <a name="separate-runtime-and-administration"></a>Administration et exécution distincte
BizTalk Server prend en charge différents scénarios d’installation dans l’environnement de production. Par exemple, vous pouvez installer, configurer et déployer sur un ordinateur une installation en mode exécution uniquement et sur un second ordinateur, une installation ne comportant que les outils d'administration.

Lors de l'installation des outils d'administration uniquement, les composants suivants sont installés : la console Administration de Biztalk et les fichiers BM.exe et BTSDeploy.exe. Considérez les éléments suivants lors de la création d’une installation des outils de BizTalk Server Administration :

- SQL Server Agent doit être en cours d'exécution sur tous les ordinateurs hébergeant les bases de données MessageBox de BizTalk Server. L’Agent SQL Server est requis pour effectuer le suivi du corps des messages dans le moteur de messagerie de BizTalk Server.

- Lorsque vous exécutez l’Assistant Configuration de BizTalk Server, vous créez une base de données Analysis Services.

- À l’aide de la base de données des suivis BizTalk avec SQL Server Analysis Services n’est pas pris en charge.

- À l’aide d’instances nommées de SQL Server Analysis Services n’est pas pris en charge.

Pour installer uniquement les outils d’Administration de BizTalk Server, sélectionnez uniquement **les outils d’Administration** pendant l’installation. Une fois l'installation terminée, ouvrez le gestionnaire de configuration personnalisée et rejoignez un système d'authentification unique de l'entreprise existant, ainsi qu'un groupe BizTalk.
Haut de page

## <a name="enable-msdtc"></a>Activation du service MSDTC
Avant d’installer et de configuration de BizTalk Server dans un environnement multiserveur, activez l’accès DTC réseau et accès COM + réseau sur tous les serveurs BizTalk et toutes les instances de SQL Server à distance utilisés par BizTalk Server. Consultez [à la configuration des étapes pour optimiser votre environnement](post-configuration-steps-to-optimize-your-environment.md).

Supplémentaires :

- Tous les serveurs BizTalk Server et les serveurs SQL Server dans un groupe doivent avoir la même procédure distante RPC (appel) l’authentification niveau appliquée. Le proxy DTC ne peut pas s’authentifier correctement DTC lorsque les ordinateurs utilisent des systèmes d’exploitation différents, sont jointes à des groupes de travail ou sont dans des domaines différents, ne faites pas confiance à l’autre. Consultez [MSDTC ne parvient pas à s’authentifier mutuellement](https://msdn.microsoft.com/library/ms686976(VS.85).aspx).

- Si vous utilisez un pare-feu, ouvrez les ports DTC et RPC requis. Consultez [vue d’ensemble du Service et pour Windows, les exigences de ports réseau](http://support.microsoft.com/kb/832017).

- Pour vous assurer que les paramètres DTC sont corrects, utilisez les outils de DTC testeur et les commandes Ping DTC. Ces outils et le dépannage de DTC plus sont décrites sur [BizTalk Server - résolution des problèmes liés à MSDTC](https://social.technet.microsoft.com/wiki/contents/articles/2031.biztalk-server-troubleshooting-problems-with-msdtc.aspx).

## <a name="remote-sql-server"></a>SQL Server à distance
Lorsque SQL Server est installé sur un ordinateur distant :

- [Outils d’administration SQL Server](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) (versions plus récentes de SQL) ou de la connectivité des outils clients SQL Server (versions antérieures de SQL) doit être installée sur l’ordinateur BizTalk Server local lorsque SQL Server est distant. Les outils SQL Server installe les bibliothèques clientes requises pour communiquer avec l’instance distante de SQL Server. La version des outils SQL Server sur l’ordinateur BizTalk Server local doit être la même version que celle qui est installée sur le serveur SQL distant.

- Le client OLAP de SQL Server doit être installé sur l'ordinateur local si vous envisagez d'utiliser les services Analysis Services à distance. Le client OLAP peut-être être inclus avec [SQL Server 2016 Feature Pack](https://www.microsoft.com/download/details.aspx?id=52676).

- Le serveur SQL Server distant doit être en cours d'exécution lors de la configuration de BizTalk Server.

- Les ports TCP et UDP que vous avez indiqués au cours du processus d'installation du serveur SQL Server doivent être ouverts lors de la configuration de BizTalk Server.

- Pour configurer les outils BAM, installer les outils d’administration SQL Server - base et complets sur le serveur d’analyse BAM de BizTalk Server. Pour plus d’informations sur la configuration et configurez l’analyse BAM dans un environnement multiserveur, consultez [installer et configurer analyse BAM (Business Activity Monitoring) dans un environnement multiserveur](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx). 

- Les instances nommées de SQL Server Analysis Services ne sont pas pris en charge.

### <a name="sql-server-topologies"></a>Topologies de SQL Server
SQL Server peut être installé localement sur le serveur BizTalk Server, ou sur un autre serveur dédié à SQL Server. La plupart des scénarios de production sont BizTalk Server et SQL Server installés sur des ordinateurs distincts. 

Pour obtenir la liste des versions de SQL Server prises en charge, consultez : 

* [Configuration logicielle requise pour BizTalk Server 2016](hardware-and-software-requirements-for-biztalk-server-2016.md) 
* [BizTalk Server 2013R2 et 2013 configuration logicielle requise](hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)

> [!IMPORTANT]
> Les Service Packs supplémentaires et mises à jour Windows sont pris en charge et doivent être installés.

### <a name="maintain-and-troubleshoot-databases"></a>Gérer et dépanner les bases de données

Consultez [comment gérer et dépanner les bases de données BizTalk Server](http://support.microsoft.com/kb/952555).

## <a name="business-activity-monitoring-bam"></a>BAM (Business Activity Monitoring)
BizTalk Server fournit plusieurs outils pour les travailleurs de l’information, parmi les BAM. Comprendre l’architecture de composant vous permet de planifier l’installation de BizTalk Server pour utiliser les ressources du serveur auquel vous avez accès.
Analyse BAM (Business Activity) est une collection d’outils permettant de gérer les agrégations, les alertes et les profils pour surveiller les métriques d’entreprise pertinents, connu en tant qu’indicateurs de performance clés ou des indicateurs de performance clés.

BAM est un module qui vous donne la visibilité de bout en bout dans vos processus d’entreprise fournit des informations sur l’état et les résultats de plusieurs processus opérationnels et de transactions. Vous pouvez utiliser la sortie de l'analyse BAM pour identifier les sources d'incident et résoudre les problèmes liés à votre activité. Pour plus d’informations sur le cycle de vie BAM, consultez poster analyse BAM (Business Activity) à [affiches de BizTalk Server BAP](https://www.microsoft.com/download/details.aspx?id=56123).

Analyse BAM se compose des couches suivantes :

| Couche | Ce qu’il fait | Exemples | Où installé |
|---| ---|---|---|
| Présentation et outils | Fournit des services frontaux aux développeurs et aux utilisateurs des activités. Affiche les données, permet aux utilisateurs professionnels et développeurs de définissent et gérer les modèles et profils ; parmi d’autres fonctions. | Office Excel, portail BAM | Excel, les outils de gestion et les interfaces utilisateur personnalisées sont installés sur la station de travail du développeur ou de l'utilisateur des activités. Les applications de portail et personnalisé web BAM repose sur l’infrastructure BAM sont installées sur un serveur. |
| Services Web et traitement | Lien entre les couches de présentation et de base de données, implémentation des règles d'entreprise et des processus, agrégation de données et analyses. | Windows Sharepoint Services (WSS), Services Web de gestion des partenaires commerciaux, service Web de gestion BAM et moteur de BizTalk Server. | Sur un serveur avec IIS, les services web de service et éventuellement personnalisé de Notification SQL, en fonction de l’application. Les services d’hôte BizTalk peuvent également être installés sur ce serveur, ou sur un serveur distinct dans la configuration de plusieurs ordinateurs disposant d’au moins trois ordinateurs. |
| Base de données et services de plateforme | Stockage et récupération des données, sécurité et authentification, mise en réseau, fonctions du système d'exploitation | SQL Server, Windows Server, Enterprise Single Sign-On (SSO), un basculement et des clusters d’équilibrage de charge réseau | Sur un serveur avec Windows Server, SQL Server. Pour des raisons de performances, ce serveur n’exécute généralement pas les services d’hôte BizTalk. |

### <a name="install-bam"></a>Installer l’analyse BAM
Guide pas à pas : [installer et configurer analyse BAM (Business Activity Monitoring) dans un environnement multiserveur](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)

Il est plus facile à comprendre BAM, l’installation et les processus de configuration et les dépendances en fractionnant en trois environnements BizTalk Server décrits dans le tableau suivant :

| Environnement d'exécution | Environnement au moment de la conception | Environnement au moment de l'utilisation |
|---|---|---|
| Un environnement d’exécution BizTalk Server base peut inclure les serveurs suivants : <ul><li>BizTalk Server</li><li>SQL Server</li><li>Serveur BizTalk Server d'analyse BAM</li><li>Serveur Web</li></ul> | Trois rôles sont impliqués dans le processus de déploiement et de développement de l'analyse BAM. Les rôles sont les suivants : <ul><li>Analyste d'entreprise</li><li>Administrateur des activités</li><li>Développeur d'applications</li></ul> | Une fois une solution BAM implémentée et déployée, les utilisateurs finaux peuvent afficher les rapports générés par divers outils de création de rapports. Ces outils incluent : <ul><li>Portail BAM </li><li>SQL Server Reporting Services</li><li>Microsoft PerformancePoint Monitoring Server</li><li>Applications de création de rapports BAM personnalisées</li></ul> |

Le tableau suivant décrit les composants BAM à installer :

|Catégorie |Composant BAM|Fonction|
|---|---|---|
| Composants du portail | Analyse BAM (Business Activity Monitoring) | La sélection du composant BAM installe le logiciel qui donne aux utilisateurs une vue en temps réel de leurs différents processus d’entreprise, ce qui leur permet d’importantes décisions commerciales. |
| Logiciels complémentaires | Alertes BAM | Installe les logiciels nécessaires permettant à BizTalk Server de générer des alertes BAM. <br/><br/>Alertes BAM sur BizTalk Server 2013 R2 et versions ultérieures utilisent la messagerie de base de données SQL Server. SQL Notification Services n'est ni utilisé ni pris en charge.<br/><br/>Alertes BAM dans BizTalk Server 2013 avec SQL Server 2012 utilise SQL Notification Services. Alertes BAM dans BizTalk Server 2013 avec SQL Server 2008 R2 utilise SQL Notification Services. |
| | Client BAM | Le composant Client BAM installe le logiciel côté client qui permet aux utilisateurs d’entreprise d’utiliser le composant BAM de BizTalk Server. | 
| | BAM-Événements | Sélectionnez le composant prise en charge de l’analyse BAM-événements installe le logiciel pour les intercepteurs BAM-événements de Windows Workflow Foundation et Windows Communication Foundation. Cette action installe également l'API d'événements BAM, qui envoie les événements vers la base de données BAM à partir d'applications personnalisées. Prise en charge de l’analyse BAM-événements fait partie de la fonctionnalité d’analyse BAM dans BizTalk Server. | 

### <a name="configure-bam"></a>Configurer l'analyse BAM
Guide pas à pas : [installer et configurer analyse BAM (Business Activity Monitoring) dans un environnement multiserveur](https://social.technet.microsoft.com/wiki/contents/articles/1888.install-and-configure-bam-business-activity-monitoring-in-a-multi-computer-environment.aspx)

Ouvrez la Configuration de BizTalk Server, puis choisissez [Configuration personnalisée](configure-biztalk-server.md). Configuration personnalisée, vous pouvez configurer les options avancées et sélectivement configurer ou annuler la configuration de chaque fonctionnalité. 

### <a name="install-and-configure-sql-server-for-bam"></a>Installer et configurer SQL Server pour l’analyse BAM

Dans [nouveautés, Installation, Configuration et mise à niveau](biztalk-server-what-s-new-installation-configuration-and-upgrade.md), vous pouvez : 

- Consultez la configuration logicielle pris en charge pour BizTalk Server, y compris les versions de SQL Server prises en charge
- Installer les logiciels requis, y compris SQL Server. Pour les étapes d’installation spécifiques à SQL Server, consultez [installer SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) ou [installer SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).

En plus des Services de base de données requis par les fonctions principales de BizTalk Server, BAM requiert également les éléments suivants :

- SQL Server Analysis Services (SSAS)

- SQL Server Integration Services (SSIS)

- Messagerie de base de données SQL Server ou SQL Server Notification Services (numéros de sécurité sociale)

##### <a name="configure-ssis"></a>Configurer SSIS
Si votre serveur SQL Server est installé sur un ordinateur autre que le serveur BizTalk Server, puis configurer SSIS. Cette tâche vous permet de configurer SSIS de façon à utiliser la base de données msdb sur un serveur SQL Server distant.

1. Ouvrez une invite de commandes.

2. Accédez au répertoire dans %ProgramFiles%\Microsoft SQL Server\100\DTS\Binn.
 
3. Exécutez la commande suivante : notepad MsDtsSrvr.ini.xml

4. Dans le bloc-notes, remplacez le texte à l’intérieur de la «<ServerName>« balise pour le nom d’hôte de SQL Server. Enregistrez vos modifications.

5. À partir de l’invite de commandes, exécutez la commande suivante : net stop MsDtsServer

6. À partir de l’invite de commandes, exécutez la commande suivante : net start MsDtsServer

    **Supplémentaires**:  
    Par défaut, le service Integration Services est configuré de manière à gérer les packages stockés dans la base de données msdb dans une instance locale par défaut du moteur de base de données. Pour gérer les packages qui sont stockés dans une instance nommée ou une instance distante du moteur de base de données, ou dans plusieurs instances du moteur de base de données, modifiez le fichier de configuration. Par exemple, vous pouvez créer plusieurs dossiers racine du type SqlServerFolder pour gérer les packages dans la base de données msdb de plusieurs instances du moteur de base de données. Si le service s'arrête, vous pouvez également modifier le fichier de configuration pour autoriser la poursuite de l'exécution des packages. Cette option affiche davantage de dossiers racine dans l'Explorateur d'objets ou spécifie un autre dossier ou davantage de dossiers dans le système de fichiers géré par le service Integration Services.

    Le `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDTS\ServiceConfigFile` clé de Registre spécifie l’emplacement et le nom du fichier de configuration que le service Integration Services utilise. La valeur par défaut de cette clé est la suivante : C:\Program Files\Microsoft SQL Server\100\DTS\Binn\ MsDtsSrvr.ini.xml. Vous pouvez mettre à jour la valeur de la clé de Registre de sorte à utiliser un nom et un emplacement différents pour le fichier de configuration.

#### <a name="configure-bam-databases"></a>Configurer des bases de données BAM
Vous pouvez configurer les bases de données d'importation principale BAM, des archives BAM, de schémas en étoile BAM, d'analyse BAM et de l'application des services de notification BAM sur différents ordinateurs. Voici la configuration logicielle requise lorsque SQL Server est installé sur un ordinateur autre que le serveur BizTalk Server :

| Fonctionnalité d’analyse BAM | Configuration du composant | BizTalk Server | SQL Server | 
|---|---|---|---|
|Outils BAM | Tables d'importation principale BAM et base de données des archives BAM | ADOMD.NET SQL Server Integration Services | Version de SQL Server prise en charge. Consultez [quelles sont les nouveautés, Installation, Configuration et mise à niveau](biztalk-server-what-s-new-installation-configuration-and-upgrade.md).|
| Outils BAM| Activer Analysis Services pour les agrégations BAM| SQL Server Integration Services| SQL Server Analysis Services| 
| Base de données BAM Notification Services Application| Alertes BAM| Alertes BAM <br/>Conditions requises répertoriées dans [nouveautés, Installation, Configuration et mise à niveau](biztalk-server-what-s-new-installation-configuration-and-upgrade.md).| Si vous utilisez SQL Server 2012 ou SQL Server 2014, configurez la messagerie de base de données SQL Server. Si vous utilisez SQL Server 2008 R2, installer les composants de moteur SQL Server 2005 Notification Services.<br/><br/>Les exigences d’alertes BAM sont documentés dans la préparation de votre ordinateur pour l’Installation.

> [!NOTE] 
> Le compte utilisé pour le service OLAP doit disposer du droit d'accès db_datareader sur la base de données de schémas en étoile BAM.

##### <a name="notification-services--biztalk-2013--sql-server-2008-r2-only"></a>Services de notification : BizTalk 2013 / SQL Server 2008 R2 uniquement

> [!IMPORTANT]
> Cette section s’applique uniquement si SQL Server 2008 R2 est utilisé.

Vous pouvez installer les services SQL Server Notification Services dans un environnement multiserveur où les rôles Fournisseur, Générateur et Distributeur résident sur des ordinateurs différents. Les dépendances inhérentes à ce scénario sont décrites ci-après :

- Le fichier AggregationEventProvider.dll doit être installé sur l’ordinateur qui héberge le rôle de fournisseur. Ce fichier .dll est installé lorsque vous installez le fournisseur d’événements d’agrégation BAM alertes pendant l’installation de BizTalk Server. Le fournisseur d'événement d'agrégation des alertes BAM existe si le composant d'exécution BizTalk, les outils d'administration ou les outils de développement et le kit SDK sont installés.

- Les fichiers EmailNotification.xslt et FileNotification.xslt sont requis sur l’ordinateur qui héberge le rôle de serveur de distribution. Vous pouvez copier les fichiers dans le chemin d’accès suivant à partir d’un serveur BizTalk existant : \Program Files\Microsoft BizTalk Server *version*\Tracking

- Mettre à jour le fichier de définition d’Application des Services de Notification (fichier .adf) avec l’emplacement exact des fichiers .xslt sur l’ordinateur qui héberge le rôle de serveur de distribution. 

**Mettre à jour le fichier de définition d’Application (fichier .adf)**:  

1. Sur l’ordinateur sur lequel BizTalk Server est installé, ouvrez l’invite de commandes de Notification Services.
2. Accédez à \Program Files\Microsoft BizTalk Server *version*\Tracking.
3. Exécutez le fichier ProcessBamNsFiles.vbs pour créer le fichier .adf initial.
4. Modifiez le fichier .adf en y précisant le chemin d'accès au fichier .xslt.
5. Exécutez une nouvelle fois ProcessBamNsFiles.vbs pour mettre à jour le fichier .adf.
6. Redémarrez le service NT BAMAlerts.

##### <a name="bam-scale-out-alerts-topology"></a>Topologie des alertes en matière d'évolution horizontale de l'analyse BAM
Si vous mettez à niveau votre topologie de montée en puissance parallèle alertes BAM existante vers BizTalk Server 2013, puis effectuez les étapes suivantes sur chaque serveur :

1. Arrêtez le service de notification, puis annulez l'inscription d'une instance du service de notification :
    1. Dans **programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **invite de commandes de Services de Notification**.
    1. À l’invite de commandes, tapez : `net stop NS$<instance_name>`. Par exemple, tapez : `net stop NS$BamAlerts`.
    1. Pour annuler l’inscription de l’instance, tapez la commande suivante : `nscontrol unregister -name BamAlerts`. 

        L'annulation de l'enregistrement d'une instance supprime les entrées de Registre, le service NS$instance_name (s'il est présent) et les compteurs de performance pour le service.

2. Mettre à niveau vos serveurs possédant des instances Notification Services vers une édition supérieure de SQL Server 2005 Notification Services.

3. Pour migrer vos bases de données BAM en fonction de la version de SQL Server que vous mettez à niveau, exécutez le programme bm.exe commande de base de données de migration situé dans le dossier Tracking de BizTalk Server. Par exemple, si SQL Server 2005 est mis à niveau vers SQL Server 2008 R2, exécutez la commande suivante dans l’invite de commandes avec des informations d’identification d’administration : `bm.exe migrate-sql –From:sql2005 –To:sql2008 –NSUser:<username>`.

4. Réinscrivez le Service de Notification sur tous les serveurs à l’exception du serveur sur lequel le programme de migration (bm.exe) est utilisé.

    1. Dans **programmes**, cliquez sur **Microsoft SQL Server 2005**, cliquez sur **outils de Configuration**, puis cliquez sur **invite de commandes de Services de Notification**.
    2. À l’invite de commandes, tapez :`nscontrol register -name BamAlerts -server <NS DB Server> -service -serviceusername "<NSServiceUserName>" -servicepassword "<NSServicePassword>"`

    Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le Registre de l'ordinateur du service).

    > [!IMPORTANT] 
    > N’oubliez pas d’utiliser le nouveau serveur de base de données de Notification Services dans l’option - server lors de la réinscription du service. En outre, utilisez le même nom d’utilisateur pour le nouveau service Notification Services que l’ancien.

5. Validez les alertes BAM : ouvrez le **invite de commandes de Notification Services** et type : `nscontrol.exe status –name BAMAlerts –server <NS DB Server>`.

### <a name="bam-portal"></a>Portail BAM
Les composants du portail sont un ensemble de services utilisés par les professionnels pour communiquer, collaborer et prendre des décisions leur permettent d’interagir, configurer et surveiller le processus d’entreprise et flux de travail. Pour utiliser cette fonctionnalité, installez Internet Information Services (IIS). Les conditions requises d’IIS sont [nouveautés, Installation, Configuration et mise à niveau](biztalk-server-what-s-new-installation-configuration-and-upgrade.md).

### <a name="bam-add-in-from-excel"></a>Complément BAM à partir d’Excel
[Ajouter ou supprimer des compléments](https://support.office.com/article/add-or-remove-add-ins-0af570c4-5cf3-4fa9-9b88-403625a0b460) répertorie les étapes pour Excel. Le nom du complément BAM est **Business Activity Monitoring**.

### <a name="configure-multiple-biztalk-groups-to-use-a-single-bam-database"></a>Configurer plusieurs groupes BizTalk pour utiliser une base de données BAM
Partager des bases de données BAM sur plusieurs groupes BizTalk :

1. Configurez le premier groupe BizTalk avec les composants BAM Ces fonctionnalités comprennent les outils BAM, la base de données analyse BAM, les alertes BAM et le portail BAM.

2. Configurer les autres groupes BizTalk et procédez comme suit dans l’Assistant Configuration de BizTalk Server :

    1. Sélectionnez **Outils BAM**, puis sélectionnez le **activer les outils d’analyse** et **Activer Analysis Services pour les agrégations BAM** cases à cocher.

    2. Modifier la **nom du serveur** et **nom de la base de données** de banques de données BAM pour faire correspondre les mêmes noms que celui utilisés lors de la configuration du premier groupe BizTalk.

    3. Sélectionnez **alertes BAM** , puis sélectionnez **activer les alertes BAM**.

    4. Modifier le compte de service pour les alertes BAM, il est un nom d’utilisateur vide et un mot de passe.

    5. Modifier le serveur SMTP d’alertes BAM, emplacement du fichier Alertes BAM, SQL Server pour la base de données des alertes et de préfixe pour les noms de base de données d’alertes faire correspondre les mêmes noms que celui utilisés lors de la configuration du premier groupe BizTalk.

    > ! Remarque] le même principal Import Tables (PIT) peut être utilisé, mais avec des archives BAM différentes, l’analyse BAM et bases de données de schémas en étoile. Toutefois, cette option affecte tous les groupes qui utilisent la même table d'importation principale.

3. Sélectionnez **portail BAM**, puis sélectionnez le **activer le portail BAM** case à cocher.

    > [!NOTE]
    > Tous les champs de cet écran sont en lecture seule, car une relation de type un-à-un régit les correspondances entre la base de données pour la table d'importation principale BAM et le portail BAM. Plusieurs groupes BizTalk partagent le portail BAM lorsque configuré par rapport aux mêmes bases de données BAM.

4. Sélectionnez **appliquer la Configuration**.

### <a name="bam-client-software-requirements"></a>Configuration logicielle requise pour le Client BAM
- Pour le client web, vous devez Internet Explorer et Office Web Components 11 version 4.0 ou version ultérieure.

- Si vous exécutez le client web et à l’aide de SQL Server 2008 R2 Analysis Services, installez Microsoft SQL Server 2008 R2 Analysis Services 10.0 fournisseur OLE DB. 

- Pour le client Excel, vous avez besoin de Microsoft Excel et le complément Excel BAM fourni avec BizTalk Server.


## <a name="groups-and-service-accounts"></a>Groupes et comptes de Service
Créer manuellement tous les comptes et groupes de domaine avant de configurer BizTalk Server dans une installation multiserveur. Les informations suivantes sont utiles pour créer ces groupes et comptes.

Dans un environnement multiserveur, BizTalk Server ne prend en charge que les groupes de domaine et les comptes de service de domaine. 

- BizTalk Server prend uniquement en charge <NetBIOSDomainName> \<utilisateur > nom de formats pour les groupes Windows et comptes de service.

- BizTalk Server prend en charge uniquement les groupes de domaine Active Directory et les comptes d'utilisateur dans les configurations multiserveur. Groupes de domaine comprennent les groupes locaux de domaine, des groupes globaux et des groupes universels, qui sont pris en charge dans un seul ordinateur et environnements multiserveurs.

- En règle générale, les groupes locaux de domaine ne sont pas recommandées car leur utilisation requiert que tous les serveurs, y compris les serveurs SQL Server, dans l’infrastructure BizTalk Server appartiennent au même domaine. Cette remarque ne s'applique pas aux petits réseaux dans lesquels tous les serveurs et comptes d'utilisateur se trouvent dans un seul domaine. [Groupes Active Directory](http://technet.microsoft.com/library/cc733001.aspx) fournit plus d’informations.

- Comptes intégrés tels que NT AUTHORITY\LOCAL SERVICE, NT AUTHORITY\NETWORK SERVICE, NT AUTHORITY\SERVICE, NT AUTHORITY\SYSTEM et tout le monde ne sont pas pris en charge lorsque vous installez et configurez BizTalk Server dans un environnement multiserveur.

- L’utilisateur qui exécute la configuration de BizTalk Server doit appartenir aux groupes d’utilisateurs suivants : groupe d’administrateurs sur l’ordinateur local, le groupe des administrateurs système sur l’ordinateur SQL Server, le groupe de domaine utilisé pour les administrateurs BizTalk Server groupe et le groupe de domaine utilisé pour le groupe Administrateurs de l’authentification unique.

- Si possible, utilisez les noms de compte par défaut créés pendant l’installation. Le programme d’installation de BizTalk Server configure automatiquement les composants installés pour utiliser les comptes par défaut. L'utilisation des noms par défaut simplifie l'installation et la configuration, mais elle n'est pas toujours possible. Par exemple, il peut être plusieurs groupes BizTalk Server dans une forêt de domaines actifs. Dans ce cas, les noms de compte doivent être modifiés pour éviter les conflits. Ou bien, votre organisation peut utiliser des normes d’affectation de noms pour les comptes d’utilisateur et de service afin de modifier les comptes par défaut pour le rendre conforme à la norme.

### <a name="windows-groups"></a>Groupes Windows
Le tableau suivant répertorie les groupes Windows et leur appartenance utilisés par BizTalk Server. Il identifie également les rôles de serveur SQL Server ou les rôles de base de données pour les groupes.

| Grouper | Description du groupe | Adhésion | Rôles de serveur SQL Server ou rôles de base de données | 
| ---|---|---|---|
| Administrateurs SSO | Administrateur du service d'authentification unique de l'entreprise [Spécifiez l’administrateur SSO et Affiliate Administrators Accounts](../core/how-to-specify-sso-administrators-and-affiliate-administrators-accounts.md) contient des informations supplémentaires. | Contient les comptes de service pour le service d'authentification unique de l'entreprise. Contient les utilisateurs/groupes qui doivent être capables de configurer et d'administrer BizTalk Server et le service d'authentification unique. Contient les comptes utilisés pour exécuter le Gestionnaire de configuration BizTalk lors de la configuration du serveur de secret principal de l'authentification unique. | **db_owner** rôle de base de données SQL Server pour l’authentification unique <br/><br/>**securityadmin** rôle SQL Server pour SQL Server où se trouve l’authentification unique. |
| Administrateurs d'applications associées à authentification unique | Administrateurs de certaines applications associées à authentification unique. Peut créer/supprimer des applications associées à authentification unique, administrer des mappages d'utilisateur et définir des informations d'identification pour des utilisateurs d'applications associées. | Ne contient aucun compte de service. Contient le compte utilisé pour les administrateurs BizTalk Server.| |
|Administrateurs BizTalk Server | Possède les privilèges minimaux requis pour exécuter les tâches d'administration. Peut déployer des solutions, gérer des applications et résoudre des problèmes liés au traitement des messages. Pour effectuer des tâches d'administration pour les adaptateurs, les gestionnaires de réception et d'envoi et les emplacements de réception, les administrateurs BizTalk Server doivent être ajoutés aux administrateurs d'applications associées à authentification unique. Consultez [gérer la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md). | Contient les utilisateurs/groupes qui doivent être capables de configurer et d'administrer BizTalk Server. | **BTS_ADMIN_USERS** rôle de base de données SQL Server dans les bases de données suivantes :<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport<br/><br/>**db_owner** rôle de base de données SQL Server pour les bases de données suivantes :<br/>BAMStarSchema<br/>BAMPrimaryImport<br/>BAMArchive<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**NSAdmin** rôle de base de données SQL Server dans les bases de données suivantes : <br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>Rôle de base de données du serveur SQL Server dans les bases de données suivantes : <br/>BizTalkDTADb<br/>BizTalkMgmtDb. <br/><br/>**Administrateurs OLAP** sur l’ordinateur qui héberge la base de données OLAP BAMAnalysis. |
| Opérateurs BizTalk Server | A un rôle à faible privilège avec accès uniquement à l’analyse et le dépannage des actions. | Contient des utilisateurs/groupes qui surveillent les solutions. Ne contient aucun compte de service. | **BTS_OPERATORS** rôle de base de données SQL Server dans les bases de données suivantes : <br/>BizTalkDTADb<br/>BizTalkEDIDb<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb | 
| Utilisateurs d'applications BizTalk | Nom par défaut du premier groupe d'hôtes BizTalk In-Process créé par le Gestionnaire de configuration. Utilisez un groupe d'hôtes BizTalk pour chaque hôte In-Process de votre environnement. Inclut des comptes ayant accès aux hôtes BizTalk In-Process (processus hôte dans BizTalk Server, BTSNTSvc.exe). | Contient des comptes de service pour l'instance d'hôte BizTalk In-Process dans l'hôte auquel est associé le groupe d'hôtes BizTalk.  | **BTS_HOST_USERS** rôle de base de données SQL Server dans les bases de données suivantes :<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport<br/><br/> **BAM_EVENT_WRITER** rôle de base de données SQL Server dans le BAMPrimaryImport. | 
| Utilisateurs d'hôtes BizTalk isolés | Nom par défaut du premier groupe d'hôtes BizTalk isolés créé par le Gestionnaire de configuration. Hôtes BizTalk isolés ne s'exécutant pas sur BizTalk Server, tels que HTTP et SOAP. Utilisez un groupe d'hôtes BizTalk isolés unique pour chaque hôte isolé de votre environnement. | Contient des comptes de service pour l'instance d'hôte BizTalk isolé dans l'hôte auquel est associé le groupe d'hôtes BizTalk isolés. | **BTS_HOST_USERS** rôle de base de données SQL Server dans les bases de données suivantes :<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BizTalkDTADb<br/>BAMPrimaryImport | 
| Utilisateurs du sous-système EDI | Dispose de l'accès à la base de données EDI. | Contient les comptes de service pour le service EDI de base BizTalk. | **EDI_ADMIN_USERS** rôle de base de données SQL Server dans le BizTalkEDIDb. | 
| Utilisateurs du portail BAM | A accès au site Web du portail BAM. | Le groupe Tout le monde est utilisé par défaut pour ce rôle. Ne contient aucun compte de service. |  | 
| Hôtes avec adaptateur BizTalk SharePoint activé | A accès pour le Service Web adaptateur Windows SharePoint Services. | Contient des comptes de service pour l’instance d’hôte BizTalk utiliser l’adaptateur SharePoint. |  | 
| Groupe Opérateurs B2B BizTalk | Un rôle BizTalk qui réduit la charge sur les administrateurs à effectuer l’opération de gestion tous les tiers. Ce rôle permet aux utilisateurs Windows associés au rôle de réaliser toutes les opérations de gestion des tiers. | Il contient les utilisateurs/groupes qui doivent être en mesure de configurer et de gérer les données GPC BizTalk Server ainsi que de surveiller les solutions. | **BTS_OPERATORS** rôle de base de données SQL Server dans les bases de données suivantes : <br/>BizTalkDTADb<br/>BizTalkMgmtDb<br/>BizTalkMsgBoxDb<br/>BizTalkRuleEngineDb<br/>BAMPrimaryImport |

### <a name="user-and-service-accounts"></a>Comptes d'utilisateur et de service
Le tableau suivant répertorie les comptes d'utilisateur ou de service Windows et les affiliations de groupe utilisés par BizTalk Server. Il identifie également les rôles de serveur SQL Server ou les rôles de base de données pour les comptes.

| Utilisateur| Description de l'utilisateur| Affiliation de groupe | Rôles de serveur SQL Server ou rôles de base de données| 
| ---|---|---|---|
| Service d'authentification unique de l'entreprise | Compte de service utilisé pour exécuter Enterprise Sign-On Service unique, qui accède à la base de données SSO. | Administrateurs SSO | | 
| Compte de l'instance de l'hôte BizTalk | Compte de service utilisé pour exécuter l'instance de l'hôte BizTalk de type In-Process (BTNTSVC). | Utilisateurs d'applications BizTalk | | 
| Compte de l'instance de l'hôte BizTalk isolé | Compte de service utilisé pour exécuter l'instance de l'hôte BizTalk isolé (HTTP/SOAP). | Utilisateurs d'hôtes BizTalk isolés IIS_WPG | | 
| Service de mise à jour du moteur des règles | Compte de service utilisé pour exécuter le service de mise à jour du moteur de règles qui reçoit des notifications de stratégie de déploiement ou d'annulation du déploiement à partir de la base de données du moteur de règles.| | **RE_HOST_USERS** rôle de base de données SQL Server dans le BizTalkRuleEngineDb.| 
| Utilisateur des services de notification BAM | Compte de service utilisé pour exécuter les services de notification BAM et qui accède aux bases de données BAM. | SQLServer2005NotificationServicesUser$<ComputerName> | **NSRunService** rôle de base de données SQL Server dans les bases de données suivantes :<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**BAM_ManagementNSReader** rôle SQL Server pour le BAMPrimaryImport. | 
| Utilisateur de service Web de gestion de l'analyse BAM | Compte d'utilisateur pour le service Web de gestion de l'analyse BAM (BAMManagementService) pour l'accès aux diverses ressources BAM. Le portail BAM appelle BAMManagementService avec les informations d'identification des utilisateurs entrées sur le portail BAM pour gérer les alertes, obtenir le fichier XML de définition BAM et des vues BAM. | IIS_WPG | **NSSubscriberAdmin** rôle de base de données SQL Server dans les bases de données suivantes :<br/>BAMAlertsApplication<br/>BAMAlertsNSMain<br/><br/>**BAM_ManagementWS** rôle SQL Server pour le BAMPrimaryImport. | 
| Compte de Pool d’applications BAM| Compte de pool d’applications pour BAMAppPool qui héberge le site Web du portail BAM. | IIS_WPG | | 

> [!IMPORTANT]
> Pour plus d’informations sur les groupes Windows et les comptes de service utilisés dans BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).

## <a name="databases-list"></a>Liste des bases de données
Voici la liste des bases de données SQL Server utilisée dans BizTalk Server :

| Nom de la banque de données | Nom par défaut de la base de données | Volume | Augmentation |  Description | 
| ---|---|---|---|---|
| Base de données SSO | SSODB | Faible | Faible | Cette base de données d'informations d'identification pour l'authentification unique de l'entreprise stocke de manière sécurisée le nom et le mot de passe de l'utilisateur.| 
| Base de données de gestion BizTalk | BizTalkMgmtDb | Faible | Faible | Cette base de données constitue la banque centrale de méta-informations de toutes les instances de BizTalk Server.| 
| Base de données MessageBox BizTalk | BizTalkMsgBoxDb | Élevée | Moyenne | Le moteur de BizTalk Server utilise cette base de données pour le routage, queuing, gestion des instances et diverses autres tâches.<br/><br/>**Remarque**<br/>Mise à jour automatique des statistiques, création automatique des statistiques et le paramétrage du parallélisme sont volontairement désactivées dans l’instance de base de données SQL Server qui héberge la base de données BizTalk Server BizTalkMsgBoxDB. N'activez pas ces paramètres. | 
| Base de données de suivi BizTalk | BizTalkDTADb | Élevée | Élevée | Cette base de données stocke les données d'entreprise et d'analyse du fonctionnement traitées par le moteur de suivis BizTalk Server. | 
| Base de données du moteur de règles | BizTalkRuleEngineDb | Faible | Faible | Cette base de données constitue un référentiel de stratégies (ensembles de règles et de vocabulaires associés). Les vocabulaires sont des ensembles de noms conviviaux et propres au domaine permettant de référencer les données dans les règles. | 
| Base de données d’importation principale BAM | BAMPrimaryImport | Moyenne | Moyenne | Cette base de données collecte des données de suivi BAM brutes. | 
| Base de données des archives BAM | BAMArchive | Moyenne | Moyenne | Base de données dans laquelle sont archivées les anciennes données d'activité d'entreprise. Créer une base de données des archives BAM pour réduire l’accumulation des données d’activité entreprise dans la base de données d’importation principale BAM. | 
| Base de données de schéma en étoile BAM | BAMStarSchema | Moyenne | Moyenne | Cette base de données contient le tableau intermédiaire et les tables de mesures et de dimensions. | 
| Base de données de l'application des services de notification BAM | BAMAlertsApplication | Moyenne | Moyenne | Cette base de données contient des informations d'alerte relatives aux notifications BAM. Par exemple, lorsque vous créez une alerte à l’aide du portail BAM, les entrées sont insérées dans cette base de données qui spécifient les conditions et les événements qui se rapporte l’alerte, ainsi que d’autres données de prise en charge de l’alerte. | 
| Base de données de l'instance des services de notification BAM | BAMAlertsNSMain | Moyenne | Moyenne | Cette base de données contient des informations sur l’instance qui spécifie comment les services de notification se connectent au système par l’analyse BAM. | 

#### <a name="sql-server-databases-used-by-sharepoint"></a>Les bases de données SQL Server utilisés par SharePoint

| Nom de la banque de données | Nom par défaut de la base de données | Volume | Augmentation |  Description | 
|---|---|---|---|---|
| Base de données de configuration de Windows SharePoint Services | Définie par l'utilisateur | Faible | Faible | Cette base de données contient tous les paramètres généraux du serveur. | 
| Base de données de contenu Windows SharePoint Services | Définie par l'utilisateur | Moyenne | Moyenne | Cette base de données stocke tout le contenu du site, notamment les éléments de liste et les documents. | 

## <a name="install-biztalk-a-multi-server-environment"></a>Installez un environnement multiserveur de BizTalk

1. **Installer les Services de domaine Active Directory** -la première étape nécessaire pour l’installation de BizTalk Server dans un environnement multiserveur consiste à installer les services de domaine Active Directory pour les comptes et groupes de serveurs BizTalk différents. Pour créer le domaine Active Directory, consultez les éléments suivants :

    - Windows Server 2012 et les versions ultérieures : [installer Active Directory Domain Services](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/install-active-directory-domain-services--level-100-)
    - Windows Server 2008 R2 : [Installation AD DS et Guide pas à pas de suppression](https://technet.microsoft.com/library/cc755258(WS.10).aspx)

    > [!IMPORTANT]
    > Les groupes BizTalk Server décrits dans le **utilisateur et le Service des comptes utilisés dans BizTalk Server** table (dans cette rubrique) doit être créée avant d’installer BizTalk Server dans un environnement multiserveur.

2. **Installer plusieurs Instances de SQL Server en fonction des besoins** – si vos exigences de charge que vous avez besoin de plusieurs bases de données MessageBox ou que vous avez besoin de répartir la charge d’e/s de BizTalk Server sur plusieurs instances de SQL Server, puis installez plus de SQL Server instances en fonction des besoins. 

    Pour plus d’informations sur les performances de test de votre environnement BizTalk Server et optimisation de la base de données, consultez la [Guide des optimisations de performances BizTalk Server](../technical-guides/biztalk-server-2013-performance-optimization-guide.md). 

3. **Installer plusieurs ordinateurs dans votre groupe BizTalk Server en fonction des besoins** – si vos exigences de charge que vous avez besoin de plusieurs ordinateurs BizTalk Server dans votre groupe BizTalk Server, puis utilisez le composant BizTalk Server Enterprise Edition pour faire évoluer vos exigences de traitement sur plusieurs serveurs BizTalk. 

    > [!IMPORTANT]
    > De nombreuses fonctionnalités d'entreprise de BizTalk Server (mise en cluster, ajout de plusieurs serveurs à un groupe, traitement 64 bits natif, etc.) ne sont disponibles que dans l'édition Entreprise.

4. **Installer les mises à jour cumulatives** -mises à jour cumulatives sont répertoriées dans Windows Update. L’[article 2555976 de la Base de connaissances](http://support.microsoft.com/kb/2555976) répertorie les Services Pack et les mises à jour cumulatives disponibles.

## <a name="cluster-considerations"></a>Considérations relatives au cluster

- **Clustering de MSDTC** – le Microsoft Distributed Transaction Coordinator (MSDTC) est un composant central de n’importe quel environnement BizTalk Server. Si d'autres composants de l'environnement BizTalk Server sont mis en cluster, il est recommandé de mettre également MSDTC en cluster. 

- **Installez le Clustering de basculement SQL Server** : permet de fournir une haute disponibilité/tolérance pour les bases de données BizTalk Server, il est recommandé que les bases de données BizTalk Server sont installés sur un cluster de basculement SQL Server. Pour plus d’informations sur l’installation de cluster de basculement SQL Server, consultez : 

    * SQL Server 2016 : [toujours sur des Instances de Cluster de basculement (SQL Server)](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server)
    * SQL Server 2014 : [(WSFC) avec SQL Server le Clustering de basculement Windows Server](https://msdn.microsoft.com/library/ms189134(v=sql.120).aspx)

    Une fois SQL Server est configuré pour la haute disponibilité/tolérance, l’instance en cluster de SQL Server peut être référencé comme n’importe quelle autre instance de SQL Server à la configuration de BizTalk Server.

- **Configurer l’entreprise seule l’authentification serveur de secret principal en tant que ressource de cluster** – une défaillance de l’entreprise seule l’authentification serveur de secret principal peut entraîner une défaillance du système de l’environnement BizTalk Server. Il est donc recommandé de configurer le serveur de secret principal du système d'authentification unique de l'entreprise à des fins de haute disponibilité et de tolérance de pannes en définissant le serveur de secret principal en tant que ressource de cluster. Étant donné que le serveur de secret principal n’est pas un composant de l’utilisation intensive des ressources d’un environnement BizTalk Server, il est recommandé que le serveur de secret principal de mettre en cluster sur les nœuds de cluster même en tant que les instances de SQL Server. Pour plus d’informations sur la configuration de l’entreprise seule l’authentification serveur de secret principal en tant que ressource de cluster, consultez [le serveur de secret principal du Cluster](../core/how-to-cluster-the-master-secret-server1.md). 

- **Configurer un hôte BizTalk en tant que ressource de cluster** – exécuter plusieurs instances d’un hôte BizTalk Server fournit une haute disponibilité/tolérance de panne. Par conséquent, la configuration de l'hôte BizTalk en tant que ressource de cluster est déconseillée, sauf cas particuliers. Par exemple, vous pouvez configurer un hôte BizTalk en tant que ressource de cluster lors de la prise en charge de la haute disponibilité/tolérance de panne ou pour le mode de livraison chronologique des messages pour certains adaptateurs BizTalk Server. Pour plus d’informations sur quand il convient de configurer un hôte BizTalk en tant que ressource de cluster, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md). Consultez également [comment configurer un hôte BizTalk en tant que ressource de Cluster](../core/how-to-configure-a-biztalk-host-as-a-cluster-resource1.md). 

- **Cluster Message Queuing** – consultez [installer et en cluster MSMQ](https://blogs.msdn.microsoft.com/biztalknotes/2013/03/20/how-to-install-and-cluster-msmq-on-windows-server-2012/).

- **Le système de fichiers de cluster** – consultez [mise en Cluster du système de fichiers](http://go.microsoft.com/fwlink/p/?LinkId=189517).

## <a name="use-scom"></a>Utilisation SCOM
Le Pack d’administration de BizTalk Server pour Operations Manager fournit des fonctionnalités étendues de découverte et surveillance des composants de BizTalk Server et des applications qui s’exécutent sur plusieurs machines. Pour plus d’informations sur le Pack d’administration de BizTalk Server, consultez http://www.microsoft.com/download/details.aspx?id=39617.
  
## <a name="next"></a>Suivant  
[Configuration de BizTalk](configure-biztalk-server.md)