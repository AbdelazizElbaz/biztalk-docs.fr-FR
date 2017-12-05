---
title: "Mise à niveau vers BizTalk Server 2016 | Documents Microsoft"
ms.custom: 
ms.prod: biztalk-server
ms.date: 06/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975ec82b-ed27-4545-8e4a-0e567507c9ba
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39b5b6b6da7d97d3c763e5f45f215aa03d13c77c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="upgrade-to-biztalk-server-2016"></a>Mise à niveau vers BizTalk Server 2016
Mise à niveau vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] à partir de [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)] ou de BizTalk Server 2013.

Cette rubrique présente le processus de mise à niveau vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], les éléments à prendre en compte, ainsi que les instructions détaillées de mise à niveau de BizTalk Server 2013 R2 ou BizTalk Server 2013.


## <a name="upgrade-overview"></a>Vue d’ensemble de la mise à niveau

- Lisez ce document dans son intégralité avant d'effectuer la mise à niveau. BizTalk Server connecte plusieurs composants hétérogènes, aussi bien internes qu'externes, à votre entreprise. Dans la réalité, la plupart des scénarios de déploiement sont bien plus vastes et comprennent plusieurs serveurs ainsi que des clusters d’ordinateurs physiques et virtuels.

- Les déploiements de BizTalk Server sont tous différents. Avant de commencer la mise à niveau, rassemblez les informations relatives aux besoins de votre entreprise, et discutez de l'étendue de votre déploiement avec les informaticiens, administrateurs système et développeurs qui utilisent BizTalk Server. En étudiant ce guide de mise à niveau et en déterminant les besoins spécifiques de votre entreprise, vous créez votre propre calendrier de déploiement.

- Utilisez l’Analyseur de recommandations (BPA) de BizTalk Server pour examiner un déploiement BizTalk Server et générer une liste de bonnes pratiques. Il procède à une vérification au niveau de la configuration, par lecture et génération de rapport uniquement, et utilise les données collectées pour déterminer si les méthodes conseillées sont suivies ou non.

### <a name="planning-your-upgrade"></a>Planification de la mise à niveau

L’aperçu ci-dessous détaille le processus de mise à niveau. Les étapes listées doivent être exécutées dans l'ordre indiqué.

- Chemins de mise à niveau des systèmes d’exploitation
- Mises à niveau pour Microsoft SQL Server®
- Mise à niveau de Windows® SharePoint® Services
- Coexistence de versions de Visual Studio
- Coexistence des versions Microsoft Office 2016/2013

### <a name="supported-upgrade-paths"></a>Chemins de mise à niveau pris en charge
Le tableau suivant répertorie les systèmes d'exploitation pris en charge pouvant être mis à niveau vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. « Oui » signifie que la version de BizTalk Server s’exécutant sur ce système d’exploitation peut être mise à niveau. « Non » signifie que la version de BizTalk Server s’exécutant sur ce système d’exploitation ne peut pas être mise à niveau. En cas de « Non », l’environnement BizTalk doit être recréé sur un système d’exploitation pris en charge.  La rubrique [Configurations matérielle et logicielle requises pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) répertorie les systèmes d’exploitation pris en charge.

| Systèmes d'exploitation | BizTalk Server 2013 R2 |BizTalk Server 2013 |
| --- | --- | --- |
| Windows Server 2012 R2 | Oui | Non |
| Windows Server 2012 | Non | Non |
| Windows 8.1 | Oui | Non |
| Windows 8 | Non | Non
| Windows 7 SP1 | Non | Non |

Le tableau suivant répertorie les versions de SQL Server prises en charge pouvant être mises à niveau vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. Le serveur SQL Server héberge les bases de données utilisées par BizTalk Server. « Oui » signifie que BizTalk Server utilisant cette version de SQL Server peut être mis à niveau. « Non » signifie que BizTalk Server utilisant cette version de SQL Server ne peut pas être mis à niveau. En cas de « Non », l’environnement BizTalk doit être recréé sur une version de SQL Server prise en charge. La rubrique [Configurations logicielle et matérielle pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) répertorie les versions de SQL Server prises en charge. 

> [!TIP] 
> Si votre version de SQL Server n’est pas prise en charge ou ne figure pas dans la liste suivante, passez en revue la documentation de mise à niveau de SQL Server. La mise à niveau SQL couvre plus de versions que BizTalk n’en prend en charge. Par exemple, si vous utilisez SQL Server 2008, vous pouvez le mettre à niveau vers SQL Server 2016. Ensuite, vous pouvez effectuer la mise à niveau vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. Les rubriques [Mise à niveau vers SQL Server 2016](https://msdn.microsoft.com/library/bb677622.aspx) et [Mise à niveau vers SQL Server 2014](https://msdn.microsoft.com/library/bb677622(v=sql.120).aspx) répertorient les versions de SQL Server qui peuvent être mises à niveau.

| SQL Server | BizTalk Server 2013 R2 |BizTalk Server 2013 |
| --- | --- | --- |
| SQL Server 2014 | Oui | Non |
| SQL Server 2012 SP1| Non | Non |
| SQL Server 2012 | Non | Non |
| SQL Server 2008 R2 SP1 | Non | Non |


Le tableau suivant répertorie le chemin de mise à niveau de l’édition prise en charge à partir de [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. « Oui » signifie que l’édition [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 peut être mise à niveau vers l’édition en question. « Non » signifie que l’édition [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013 ne peut pas être mise à niveau vers l’édition en question. En cas de « Non », l'environnement BizTalk doit être recréé.

| BizTalk Server 2013 R2/2013 | BizTalk Server 2016 Version d’évaluation | BizTalk Server 2016 Édition Agence | BizTalk Server 2016 Édition Développeur | BizTalk Server 2016 Édition Standard | BizTalk Server 2016 Édition Entreprise |
| --- | --- | --- | --- | --- | --- |
| Evaluation | Non | Non | Non | Non | Oui | 
| Agence | Non | Oui | Non | Non | Oui | 
| Développeur | Non | Non | Oui | Non | Oui | 
| Standard | Non | Non | Non | Oui | Oui | 
| Enterprise | Non | Non | Non | Non | Oui | 

## <a name="before-the-upgrade--what-you-need-to-know"></a>Avant la mise à niveau – ce que vous devez savoir


- **Autorisations** : L’utilisateur procédant à la mise à niveau doit être membre de l’un des groupes d’utilisateurs suivants ou disposer des autorisations équivalentes :

    - Groupe Administrateurs sur l’ordinateur local
    - Groupe Administrateurs système SQL Server sur le serveur SQL Server
    - Groupe Administrateurs de BizTalk Server
    - Groupe Administrateurs de l'authentification unique (SSO)

- **SSO** : Le serveur de secret principal du système d’authentification unique et le serveur SQL Server qui héberge la base de données SSO doivent être en cours d’exécution pendant la mise à niveau.

- **Compte de service réseau** : Il doit disposer d’un accès en écriture au répertoire %windir%\temp.

- **Certificats** : Sauvegardez le magasin de certificats Windows :  

    [Windows 7 et Windows Server 2008 R2 : Importer un certificat](http://technet.microsoft.com/library/cc754489.aspx)  
    [Windows 7 et Windows Server 2008 R2 : Exporter un certificat](http://technet.microsoft.com/library/cc730988.aspx)  

- **DTC** : Activez Microsoft Distributed Transaction Coordinator (MSDTC) ([Étapes d’optimisation de l’environnement après configuration](../install-and-config-guides/post-configuration-steps-to-optimize-your-environment.md)), puis activez les règles DTC entrantes et sortantes :

    1. Dans le Gestionnaire de serveur, sélectionnez **Outils**, puis ouvrez **Pare-feu Windows avec fonctions avancées de sécurité**.
    2. Sélectionnez **Règles de trafic entrant**.
    3. Dans **règles de trafic entrant**, avec le bouton droit **Distributed Transaction Coordinator** * (selon le cas), puis **activer la règle**.
    4.  Dans Pare-feu Windows avec fonctions avancées de sécurité, sélectionnez **Règles de trafic sortant**.
    5.  Dans **règles de trafic sortant**, avec le bouton droit **Distributed Transaction Coordinator** * (selon le cas), puis **activer la règle**.
    
- **SharePoint** : Le modèle CSOM (Client Side Object Model) est utilisé pour la connexion à SharePoint Services. Le modèle SSOM (Server Side Object Model) (service web) est supprimé dans [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].

    Si vous utilisez une version de SharePoint qui ne prend pas en charge le modèle CSOM, vous pouvez éventuellement effectuer une mise à niveau vers une version prise en charge de SharePoint :
    
    [Mise à niveau vers SharePoint 2016](https://technet.microsoft.com/library/cc303420(v=office.16).aspx)  
    [Mise à niveau vers SharePoint 2013](https://technet.microsoft.com/library/cc303420(v=office.15).aspx)

- **.NET framework** : Il n’existe aucun concept de coexistence entre .NET Framework 4.5 et .NET Framework 4.6. Les fichiers binaires de .NET Framework 4.6 remplacent les fichiers binaires de .NET Framework 4.5. .NET Framework 4.6 est une condition requise de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] et n’est pas pris en charge (et ne doit pas être installé) dans les versions précédentes de BizTalk Server.

- **Office 2016 et Office 2013** : [Installez et utilisez différentes versions d’Office](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF) sur le même ordinateur. Consultez également [ces problèmes](https://support.microsoft.com/kb/3094527).

- **Hôte BizTalkServerApplication** : La mise à niveau requiert l’existence de l’hôte par défaut. Si l'instance de l'hôte par défaut associée aux ports d'envoi et aux emplacements de réception de l'adaptateur SQL est supprimée, associez l'hôte par défaut à l'adaptateur SQL avant la mise à niveau. Une fois la mise à niveau terminée, vous pouvez supprimer l’hôte par défaut de la liste.

- **Liaisons personnalisées** : Les liaisons personnalisées définies par l’utilisateur qui sont créées avec des versions antérieures du .NET Framework ne sont pas disponibles après la mise à niveau. Pour utiliser les liaisons personnalisées, ajoutez-les manuellement dans le fichier machine.config de .NET Framework 4.6.

- **Fichiers de configuration** : Sauvegardez tous les fichiers de configuration personnalisés dans BizTalk Server 2013 R2/2013. BizTalk Server prend en charge la migration des modifications uniquement dans les fichiers `btsntsvc.exe.config` et `bm.exe.config`.



### <a name="bam-alerts"></a>Alertes BAM

La fonctionnalité Messagerie de base de données SQL Server est nécessaire pour utiliser les alertes BAM. Si SQL Server est mis à niveau à partir d’une version qui utilisait des définitions d’alerte BAM existantes avec Notification Services, vous pouvez sauvegarder vos définitions d’alerte BAM et les déployer après la mise à niveau. Utilisez l’outil en ligne de commande BM.exe (`\Program Files (x86)\Microsoft BizTalk Server <your version>\Tracking`). Les étapes spécifiques sont les suivantes :

1. Ouvrez une invite de commandes et accédez à `\Program Files (x86)\Microsoft BizTalk Server <your version>\Tracking`.
2. Créez un fichier de définition à partir de l’invite de commandes : `bm.exe get-defxml -FileName:YourBAMDefinition.xml`
4. Dans la configuration de [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013, annulez la configuration des alertes BAM.
5. Effectuez une mise à niveau vers SQL Server 2016 ou SQL Server 2014 SP1.
6. Configurez la messagerie de base de données SQL Server.
7. Mise à niveau vers [!INCLUDE[bts2016_md](../includes/bts2016-md.md)].
8. Dans la configuration de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], configurez les alertes BAM.
9. Déployez le fichier de définition enregistré à partir de l’invite de commandes : `bm.exe update-all -DefinitionFile:YourBAMDefinition.xml`

> [!IMPORTANT]
> Si vous ne suivez pas ces étapes dans l’ordre indiqué ou si vous créez un fichier de définition, vous devez recréer les fichiers de définition après la mise à niveau de BizTalk Server.
> 
> Pour afficher l’aide de l’outil BM.exe, tapez : `bm.exe help`.


### <a name="bam"></a>BAM 

- **Lots DTS BAM** : Arrêtez tous les packages DTS (Data Transformation Services) BAM. Sinon, des données peuvent être perdues ou un cube OLAP (Online Analytical Processing) peut être altéré. 

- **Espace disque** : L’espace disque disponible doit correspondre au minimum à la taille des bases de données BAM existantes.

- **Agrégations en temps réel** : Si vous utilisez les agrégations BAM en temps réel dans votre version actuelle de BizTalk Server et que vous effectuez une mise à niveau vers SQL Server, procédez à une installation ou à une mise à niveau vers SQL Server Enterprise Edition. Faute de quoi, la mise à niveau échoue.

- **Valeur maxTimeout** : Si votre base de données BAM est volumineuse, mettez à jour la valeur `maxTimeout` des transactions distribuées dans le fichier machine.config en spécifiant :  

    ```
    <system.transactions>
       <machineSettings maxTimeout="23:59:59" />
    </system.transactions>
    ```

- **Suivi BAM activé avec l’Éditeur de modèle de suivi** : Après la mise à niveau, les modèles de suivi précédemment déployés sont mis à niveau ; cependant, les configurations des intercepteurs associés ne le sont pas. Chaque nouveau message BAM intercepté peut conserver les références à BizTalk Server 2013 R2/2013. Pour mettre à niveau les configurations d'intercepteurs associées, utilisez l'Éditeur de modèle de suivi pour extraire le profil de l'activité, puis réappliquer le profil.

- **Classeur des données actives** : Si vous utilisez l’analyse BAM dans BizTalk Server 2013 R2/2013, une fois la mise à niveau terminée, vous devez régénérer manuellement le classeur des données actives. Pour régénérer le classeur des données actives :

    1. Extrayez la définition BAM en exécutant la commande suivante :  
    `BM get-defxml MyDef.xml`
    2. Recréez les rapports de tableau croisé dynamique en ouvrant Microsoft Office Excel, puis en sélectionnant les compléments BAM. Importez le fichier *MyDef.xml* créé à l’étape (1) et recréez les rapports de tableau croisé dynamique. Enregistrez le nouveau classeur BAM sous le nom *MyNewBook.xls*.
    3. Renommez les rapports de tableau croisé dynamique en recherchant leurs noms dans le fichier *MyDef.xml* sous `<Caption>`, dans le chemin `<BAMDefinition>\<Extension>\<OWC>\<PivotTableView>\<PivotTable>\<PivotView>\<Label>`. Utilisez ces noms pour renommer vos rapports de tableau croisé dynamique dans *MyNewBook.xls*.
    4. Régénérez le classeur des données actives en exécutant la commande suivante :  
    `BM regenerate-livedataworkbook MyNewBook.xls`

    > [!NOTE]
    > Les classeurs ainsi régénérés ne recréent pas les artefacts Excel (par exemple, les graphiques) du classeur d’origine. Recréez manuellement les artefacts.


### <a name="enterprise-single-sign-on-esso"></a>Enterprise Single Sign-On (ESSO)

| Scénario | Informations supplémentaires |
| --- | --- |
| Mise à niveau à partir d’une version antérieure d’Enterprise Single Sign-On | BizTalk Server inclut une version mise à jour d’Enterprise Single Sign-On (ESSO). Si vous installez cette version sur un ordinateur possédant une version antérieure de BizTalk, l'authentification unique de l'entreprise est automatiquement mise à jour au cours de l'installation. Il est recommandé d'effectuer les opérations suivantes préalablement à la mise à niveau. <br/><br/> 1. Vérifiez que la version actuelle de la base de données SSO (SSODB) est sauvegardée dans un emplacement sécurisé. <br/>2. Vérifiez que la clé secrète principale actuelle est sauvegardée dans un emplacement sécurisé.<br/>3. Connaissez le mot de passe du secret principal.<br/><br/>Mettez à niveau tous les serveurs d'un groupe BizTalk vers la même version. Cette règle s’applique également au serveur de secret principal autonome. |
| Mise à niveau à l'aide de l'installation autonome de l'authentification unique de l'entreprise | Utilisez les étapes suivantes pour procéder à une mise à niveau sur des ordinateurs disposant d’une installation autonome d’Enterprise Single Sign-On, tels que des serveurs de secret principal dédiés.<br/><br/>1. Vérifiez que la clé secrète principale actuelle est sauvegardée dans un emplacement sécurisé.<br/>2. Vérifiez que la version actuelle de la base de données d'authentification unique de l'entreprise est sauvegardée dans un emplacement sécurisé.<br/>3. Exécutez le fichier **Setup.exe** d’ESSO à partir du média d’installation de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. Le dossier d’installation par défaut est `\Platform\SSO`.<br/>4. Dans la boîte de dialogue **Exécution automatique**, sélectionnez **Microsoft Enterprise Single Sign-On**.<br/>5. Dans la boîte de dialogue Résumé, sélectionnez **Mise à niveau**. |

### <a name="multicomputer-environment"></a>Environnement à plusieurs ordinateurs
Dans un environnement à plusieurs ordinateurs, mettez à niveau l’ordinateur serveur de secret principal du système SSO. Ensuite, mettez à niveau les autres ordinateurs BizTalk Server. La mise à niveau simultanée des ordinateurs BizTalk d'un groupe n'est pas prise en charge. Mettez à niveau un ordinateur à la fois dans l'ordre suivant :

1. serveur de secret principal du système d'authentification unique ;
2. ordinateurs d'exécution qui exécutent BizTalk Server ;
3. outils d'administration et ordinateur de surveillance ;
4. ordinateur de développement et tous les autres ordinateurs qui exécutent BizTalk Server.

**Supplément**  
Le panneau de configuration vous permet de modifier complètement les paramètres de BizTalk Server dans le but d'optimiser les performances. Vous pouvez également y modifier les paramètres du groupe BizTalk, de l'hôte BizTalk et de l'instance de l'hôte BizTalk. Consultez [Utilisation du panneau de configuration pour le réglage des performances de BizTalk Server](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).

### <a name="general-information"></a>Informations générales

- **Noms de comptes** : Dans la mesure du possible, utilisez les noms de comptes par défaut. Le programme d'installation de BizTalk Server configure automatiquement les composants installés pour qu'ils les utilisent. S'il existe plusieurs groupes BizTalk Server dans une forêt Active Directory, modifiez les noms de comptes pour éviter les conflits. BizTalk Server ne prend en charge que les formats de nom `<NetBIOS domain name>\<user>` pour les comptes de service et les groupes Windows.

- **Noms de comptes avec le service web de gestion BAM** : BizTalk Server ne prend pas en charge les comptes intégrés ou les comptes sans mot de passe pour l’utilisateur de service web de gestion BAM. 

  Même si la configuration de BizTalk Server avec de tels comptes réussit, le service Web de gestion BAM échoue. 

  L’utilisation de tels comptes pour le pool d’applications BAM est prise en charge.

- **BizTalk Assembly Viewer** n’est pas pris en charge sur les systèmes d’exploitation 64 bits.

- **Installation et désinstallation** : Lorsque vous désinstallez BizTalk Server, supprimez manuellement les bases de données BizTalk Server. Si vous installez BizTalk Server en tant que développeur ou évaluateur, envisagez l'installation d'une machine virtuelle. Ainsi, si vous devez procéder à une réinstallation, vous pouvez facilement revenir à un point de contrôle prédéfini sans avoir à suivre le processus de désinstallation.

- **Ordinateurs 32 bits et 64 bits** : Il existe quelques différences lors de l’installation de BizTalk Server sur Windows 32 bits ou sur Windows 64 bits. Ce document couvre les deux types d'installations. Les différences entre elles sont indiquées.

- **Groupes de travail** : L’installation et la configuration de BizTalk Server dans un environnement de groupe de travail sur un seul ordinateur sont prises en charge. Dans ce scénario, les fonctionnalités et composants de SQL Server et BizTalk Server sont installés et configurés sur le même ordinateur.

- **Terminal Server** : L’installation de BizTalk Server à l’aide de Terminal Server en mode application n’est pas prise en charge. Consultez [KB 832027](https://support.microsoft.com/kb/832027).

- La **mise à niveau silencieuse** n’est pas prise en charge.

- **Applications non prises en charge** : BizTalk Server ne prend pas en charge les applications personnalisées basées sur des API non prises en charge, tels que les API PAM, les procédures stockées ou l’accès direct aux bases de données. Exécutez au moins une mise à niveau de test avant de procéder à la mise à niveau de l’environnement de production.

- **Instances SQL Server** : Il est recommandé de mettre à niveau toutes les instances de SQL Server avant de mettre à niveau la plateforme.

## <a name="prepare-your-computer-for-upgrade"></a>Préparation de l’ordinateur pour la mise à niveau

| Tâche | Info |
| --- | --- | 
| Installation des mises à jour Windows critiques | Sélectionnez Windows Update dans le menu Programmes. Vous devez éventuellement redémarrer l’ordinateur. |
| Enregistrement des définitions des alertes BAM | S’applique uniquement si vous utilisez actuellement des définitions d’alertes BAM existantes avec SQL Server Notification Services. Créez un fichier de définition à l’aide de BM.exe et annulez la configuration des alertes BAM dans la configuration de [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013.<br/><br/>La section **Avant la mise à niveau** (dans cette rubrique) répertorie les étapes spécifiques.<br/><br/>Dans le cas contraire, recréez les définitions d'alerte BAM après avoir effectué la mise à niveau. |
| Mise à niveau vers SQL Server | Effectuez la mise à niveau vers une version prise en charge de SQL Server. Consultez :<br/><br/>[Configurations logicielle et matérielle pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)<br/>[Mise à niveau vers SQL Server 2016](https://msdn.microsoft.com/library/bb677622.aspx)<br/>[Mise à niveau vers SQL Server 2014](https://msdn.microsoft.com/library/bb677622(v=sql.120).aspx) |
| Mise à niveau des outils clients SQL Server | Dans un environnement à plusieurs ordinateurs, les outils d'administration peuvent être installés sur un ordinateur distinct. Mettez à niveau les outils clients d'administration SQL Server, y compris les outils de gestion. |
| Installer Visual Studio | Consultez la rubrique [Configurations logicielle et matérielle pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) pour connaître les versions prises en charge. Différentes versions de Visual Studio peuvent être installées côte à côte. Consultez [Visual Studio 2015](https://msdn.microsoft.com/library/ms246609(v=vs.140).aspx) et [Visual Studio 2013](https://msdn.microsoft.com/library/ms246609(v=vs.120).aspx). |
| Installation d’Office | Consultez la rubrique [Installer et utiliser différentes versions d’Office sur le même PC](https://support.office.com/article/Install-and-use-different-versions-of-Office-on-the-same-PC-6EBB44CE-18A3-43F9-A187-B78C513788BF). La rubrique [Configurations logicielle et matérielle pour BizTalk Server 2016](../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md) répertorie les versions d’Office prises en charge. |
| Arrêt des services BizTalk et Windows | - Groupe BizTalk des services BizTalk : *<Nom_application>*<br/>- Service EDI de base BizTalk<br/>- Service de mise à jour du moteur des règles<br/>- Service de publication World Wide Web<br/><br/>**REMARQUE**<br/>Si vous installez des accélérateurs BizTalk Server, arrêtez le service de journalisation HL7. |
| Sauvegarde des bases de données | - Master<br/>- MSDB<br/>- BAMArchive<br/>- BAMPrimaryImport<br/>- BAMStarSchema<br/>- BizTalkDTADb<br/>- BizTalkEDIDb<br/>- BizTalkHwsDb<br/>- BizTalkMgmtDb<br/>- BizTalkMsgBoxDb<br/>- BizTalkRuleEngineDb<br/>- TPM<br/>- BizTalkAnalysisDb<br/>- BAMAnalysis<br/><br/>[SQL Server 2014 : Vue d’ensemble de la sauvegarde](https://technet.microsoft.com/library/ms175477(v=sql.120).aspx)<br/>[SQL Server 2012 : Vue d’ensemble de la sauvegarde](https://technet.microsoft.com/library/ms175477(v=sql.110).aspx) |
| Configuration de la messagerie de base de données SQL Server | S’applique uniquement si vous utilisez des définitions d’alertes BAM avec SQL Server Notification Services.<br/><br/>La section **Avant la mise à niveau** (dans cette rubrique) répertorie les étapes spécifiques.<br/><br/>Dans le cas contraire, recréez les définitions d'alerte BAM après avoir effectué la mise à niveau. |

## <a name="do-the-upgrade"></a>Réalisation de la mise à niveau

> [!IMPORTANT]
> Lorsque vous avez installé SQL Server, le programme d’installation a accordé à votre compte de connexion des droits d’administrateur système. Des droits d’administrateur système sont également requis pour installer BizTalk Server. Procédez de l'une des manières suivantes :
> 
> - Utilisez le même compte que pour l’installation de SQL Server  
> **OU**  
> - Assurez-vous que le compte de connexion actuel dispose des droits d’administrateur système

### <a name="upgrade-steps"></a>Étapes de la mise à niveau

1. Fermez tous les programmes ouverts.
2. Exécutez **Setup.exe** à partir du média d’installation.
3. Dans Démarrer, sélectionnez **Installer Microsoft BizTalk Server**.
4. Dans **Informations sur le client**, entrez votre nom d’utilisateur, votre organisation et votre clé de produit. Sélectionnez **Suivant**.
5. Acceptez le contrat de licence, puis sélectionnez **Suivant**.
6. Dans Programme d’amélioration du produit, entrez votre préférence. Consultez **Annexe A** (dans cette rubrique) pour plus d’informations.
7. Dans **Installation des composants**, passez en revue les composants disponibles et sélectionnez **Suivant**.
8. S’il manque un composant requis sur votre ordinateur, le programme d’installation peut installer les composants redistribuables requis. Vous pouvez effectuer l'une des opérations suivantes :

    - Sélectionnez Installer automatiquement la configuration requise redistribuable à partir du Web  
  
      - ou -  
  
    - Sélectionnez Installer automatiquement la configuration requise redistribuable à partir d’un fichier CAB, si vous avez téléchargé le fichier CAB. Accédez à l’emplacement du fichier CAB et sélectionnez-le.

9. Dans **Résumé**, passez en revue les composants qui peuvent être mis à niveau.
10. Sélectionnez **Mettre à niveau** pour commencer.
11. Facultatif : Sélectionnez **Utiliser Microsoft Update lorsque je recherche les mises à jour (recommandé)**.
12. Dans **Mise à niveau terminée**, décochez la case **Lancer la configuration de BizTalk Server**, puis sélectionnez **Terminer**.

**SUPPLÉMENT**  
En raison de la complexité du processus de mise à niveau de BizTalk Server, des erreurs peuvent se produire. Toutefois, si vous êtes correctement préparé, vous pouvez en résoudre facilement la plupart. Il est recommandé de lire l’**annexe B** (dans cette rubrique) afin d’obtenir des conseils permettant d’éviter les erreurs de mise à niveau et de vous familiariser avec les procédures à suivre en cas d’erreur.

Le processus de mise à niveau ne s'applique qu'aux fonctionnalités présentes sur la version antérieure de BizTalk Server. Les nouvelles fonctionnalités ne sont pas installées pendant une mise à niveau. Pour les installer, réexécutez le programme d’installation après la mise à niveau, choisissez **Modifier**, puis sélectionnez les fonctionnalités à installer. Une fois installées, configurez-les à l’aide du **Gestionnaire de configuration de BizTalk Server**.

Pour vérifier si la mise à niveau a réussi, ouvrez **Programmes et fonctionnalités** et recherchez [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]. Si elle est répertoriée, l'installation a réussi.

## <a name="post-upgrade"></a>Validation de la mise à niveau
Vous ne pouvez pas restaurer [!INCLUDE[bts2013r2_md](../includes/bts2013r2-md.md)]/2013.

- **Si vous avez créé un fichier XML de définition d’alertes BAM** : Dans la configuration de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)], configurez les alertes BAM. Déployez ensuite les définitions enregistrées.

    La section **Avant la mise à niveau** (dans cette rubrique) répertorie les étapes spécifiques. Dans le cas contraire, recréez les définitions d'alerte BAM après avoir effectué la mise à niveau.

- **Installer MQSAgent** : Si le fichier MQSAgent.dll est installé sur un serveur WebSphere MQ distant, installez une nouvelle version de MQ Agent à partir de [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] sur le serveur WebSphere MQ distant.

- **Démarrer MSMQ** : Si vous utilisez l’adaptateur MSMQ, démarrez le service Message Queuing.

- **EXE et BRE personnalisés** : Si un fichier exécutable managé personnalisé fait référence à l’assembly du moteur des règles d’entreprise dans BizTalk Server 2010, ajoutez ce qui suit au fichier de configuration de l’application pour exécuter le processus dans .NET Framework 2.0.

    ```
    <?xml version="1.0" encoding="Windows-1252"?>
    <configuration> 
     <startup>
      <supportedRuntime version="v2.0.50727" />
     </startup>   
    </configuration>
    ```

- **Travail de l’Agent SQL** : Reconfigurez les travaux de l’Agent SQL Server suivants :

    -   Purge et archivage DTA (BizTalkDTADb) : Consultez [Configuration du travail de purge et d’archivage DTA](../core/how-to-configure-the-dta-purge-and-archive-job.md)
    -   Sauvegarde de BizTalk Server (BizTalkMgmtDb) : Consultez [Configuration du travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)

- **Redémarrage des applications** : Redémarrez toutes les applications déployées qui sont mises à niveau.

- **Erreur de portail BAM** : Lorsque vous ouvrez le portail BAM, vous pouvez recevoir le message d’erreur suivant : 

    `The server encountered a critical failure while trying to access the list of Views. The Business Management Web Service requires Administrator's attention.` 

    Cette erreur peut se produire si le portail BAM est configuré sur un site web utilisé par des applications exécutant .NET Framework 2.0. Dans ce scénario, hébergez le portail BAM sur un nouveau site web. Pour ajouter un site web, consultez [Création d’un site web](http://go.microsoft.com/fwlink/p/?LinkID=196470). Après avoir créé le site web, reconfigurez le portail BAM :

    1. Ouvrez **Configuration de BizTalk Server**.
    2. Sélectionnez **Annuler la configuration des composants**. Dans **Annuler la configuration des composants**, cochez la case **Portail BAM**, puis sélectionnez **OK**.
    3. Reconfigurez le portail BAM en sélectionnant le nouveau site web dans la liste **Site Web du portail BAM**.

- **Accélérateur BizTalk 2016 pour SWIFT** : Le processus de mise à niveau de BizTalk Server ne met pas à jour un fichier *BREDeployment.exe.config* modifié. Modifiez manuellement les chemins d’accès dans le fichier *BREDeployment.exe.config* situé dans le dossier `\Program Files\Microsoft BizTalk 2016 Accelerator for SWIFT\SDK\Tools`.

    Par ailleurs, la configuration d’A4SWIFT Web Services and Message Pack est perdue. Reconfigurez après la mise à niveau de BizTalk Server.

## <a name="appendix-a-customer-experience-improvement-program"></a>Annexe A : Programme d’amélioration du produit
Dans le cadre du Programme d’amélioration du produit de BizTalk Server, vous avez la possibilité de fournir un retour d’expérience utile à Microsoft concernant l’utilisation des fonctions de BizTalk Server. Les données ainsi collectées sont anonymes et ne peuvent pas être utilisées pour vous identifier. Dans le cadre de ce programme, Microsoft collecte des statistiques d'utilisation des fonctions.

En participant à ce programme, vous pouvez contribuer à améliorer la fiabilité et les performances de diverses fonctionnalités de BizTalk Server. Pour plus d’informations sur ce programme et sa politique de confidentialité, consultez la rubrique [Politique de confidentialité de Microsoft BizTalk Server CEIP](http://go.microsoft.com/fwlink/p/?LinkId=188553).

## <a name="appendix-b-known-issues"></a>Annexe B : Problèmes connus

- **Configurer les alertes BAM sur l’ordinateur d’administration** : Il existe un environnement à plusieurs ordinateurs avec les composants d’administration, les composants d’exécution et les composants SQL Server installés sur des ordinateurs distincts. Lorsque vous travaillez avec les outils BAM ou les alertes BAM, les problèmes suivants peuvent se produire :

    **PROBLÈME** : Lorsque vous configurez les outils BAM sur un ordinateur d’administration de BizTalk, l’erreur suivante se produit :
    
    `Service BAMAlerts was not found on computer ‘.’.The specified service does not exist as an installed service.`

    **PROBLÈME** : Lorsque vous déployez une définition d’activité BAM à partir de l’ordinateur d’exécution, l’erreur suivante se produit :
    
    `A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) (.Net SqlClient Data Provider)`
    
    Cela se produit si les alertes BAM sont configurées sur l'ordinateur d'exécution. Pour résoudre ce problème, configurez les alertes BAM sur le même ordinateur que la console Administration de BizTalk. Ne configurez pas les alertes BAM sur l'ordinateur d'exécution.

- **Récupération à partir d’un échec de mise à niveau** : Un échec de mise à niveau peut se produire à tout moment pendant la mise à niveau. La méthode de récupération après un échec de mise à niveau est déterminée selon la phase au cours de laquelle s'est produit l'échec.

    - Si la mise à niveau échoue lors de l’installation des prérequis, le programme d’installation arrête l’installation des autres prérequis et renvoie un message avec l’erreur. Vous pouvez alors corriger cette erreur et relancer le programme d’installation.
    
    - Si la mise à niveau échoue lors de la mise à niveau des bases de données, de la suppression des fonctionnalités de la version de BizTalk Server existante ou de l’installation de la nouvelle version, l’installation est interrompue et un message d’erreur s’affiche. Les éventuels changements sont annulés. Les modifications apportées aux bases de données BizTalk Server ne peuvent pas être annulées.
    
        Si les composants de l’installation précédente de BizTalk Server sont supprimés au cours de la mise à niveau, l’ordinateur peut rester dans un état sans aucun composant BizTalk Server. Les informations de configuration des composants de l'installation précédente peuvent être conservées. Donc, en fonction du moment où s’est produit l’échec de la mise à niveau, les bases de données BizTalk Server ont peut-être été mises à niveau. Il peut s’avérer nécessaire de restaurer les bases de données sauvegardées précédemment avant de relancer le programme d’installation.
    
    - Si la mise à niveau échoue lors de la reconfiguration des fonctionnalités BizTalk Server, le programme d'installation retourne un message indiquant le niveau d'achèvement de la mise à niveau. En cas d’échec ou de réussite partielle de la configuration, exécutez la configuration de BizTalk Server afin de terminer la mise à niveau.
    
    Si le processus de mise à niveau continue d’échouer et que vous devez revenir à la version précédente de BizTalk Server, vous devez restaurer les bases de données que vous aviez sauvegardées, puis réinstaller la version précédente de BizTalk Server.

- **Utiliser les mêmes versions** : Dans un groupe d’applications BizTalk, vous ne pouvez pas exécuter des machines sur lesquelles sont installées des versions différentes de BizTalk Server. Par exemple, dans la console Administration de BizTalk, vous ne pouvez pas lier un port d'envoi exécutant une version de BizTalk Server à un emplacement de réception exécutant une autre version de BizTalk Server. 

- **Redémarrer le service SSO** : Si une version antérieure de Visual Studio ou .NET Framework 4.5 est installée sur votre machine, le service SSO des versions antérieures de BizTalk Server cesse de fonctionner. Pour résoudre ce problème, exécutez la commande `regasm SSOSQL.dll` à l’invite de commandes Visual Studio. Cette commande redémarre le service SSO.

    > [!NOTE]
    > Sur un ordinateur 64 bits, exécutez les versions 32 bits et 64 bits de la commande regasm.

- **Impossible d’utiliser SOAP** : Après la mise à niveau d’une plateforme, il se peut que les autorisations vous empêchent d’envoyer des messages SOAP. Pour résoudre ce problème, modifiez le fichier Web.config situé dans `C:\inetpub\wwwroot\<SOAPExternalAppName>\` à l’aide du texte suivant :

    ```
    <securityPolicy>
    <trustLevel name="Full" policyFile="internal" />
    <trustLevel name="High" policyFile="web_hightrust.config" />
    <trustLevel name="Medium" policyFile="web_mediumtrust.config" />
    <trustLevel name="Low" policyFile="web_lowtrust.config" />
    <trustLevel name="Minimal" policyFile="web_minimaltrust.config"/>
    </securityPolicy>
    <trust level="Full" originUrl="" processRequestInApplicationTrust="true"/>
    ```

    Il se peut que vous deviez également modifier le mode d’erreur personnalisé **Remote Only** (À distance uniquement) en spécifiant **Off** (Désactivé).

- **Magasin de certificats** : Après la mise à niveau, vous ouvrez un port d’envoi ou un emplacement de réception à partir de la console Administration de BizTalk Server, et vous obtenez l’erreur : `Could not open certificate store, the system cannot find the file specified (System).`

    Cette erreur se produit si le magasin de certificats est manquant.

- **Portail BAM** : Sur une machine 64 bits, vous ne pouvez pas accéder au portail BAM après la mise à niveau. Résolution possible :

    1. Créez une copie de sauvegarde du fichier web.config situé dans `%BizTalkInstallDir%\BAMPortal\web.config`.

    2. À l’invite de commandes, exécutez la commande suivante en vous aidant du programme bm.exe situé dans le dossier de suivi de BizTalk Server : `bm.exe get-config –FileName:<filepath> -Server:MyServer -Database:MyDB`

    Dans le fichier XML Config, obtenez la valeur correspondant à *BAMVRoot* (xpath: BAMConfiguration\ GlobalProperty\Name="BAMVRoot").

    3. Ouvrez la configuration de BizTalk Server sur l’ordinateur indiqué comme valeur BAMVRoot et annulez la configuration du portail BAM.

    4. Ouvrez la configuration de BizTalk Server et configurez le portail BAM.

    5. Ouvrez le nouveau fichier web.config dans l’emplacement indiqué à l’étape (1).

    6. À l’aide de la copie de sauvegarde du fichier web.config, définissez les valeurs suivantes (sous `configuration\appSettings`) :

        - key="MainPageContentUrl"
        - key="AlertNotificationOptions"

    > [!NOTE] 
    > Sur une machine 64 bits, une fois la mise à niveau du système d’exploitation effectuée, il est recommandé de reconfigurer le portail BAM.

- **Déployer des activités BAM de l’échange de données informatisé (EDI, Electronic Data Interchange)** : La mise à niveau risque de n’aboutir que partiellement. Cela peut se produire lorsque vous mettez à niveau SQL Server (avec EDI configuré). Les activités BAM d'EDI ne peuvent pas être mises à niveau correctement. Pour résoudre ce problème, à l'invite de commande avec informations d'identification d'administration, exécutez les commandes suivantes pour déployer les activités BAM :

    `"<BizTalk Installation Folder>\Tracking\bm.exe" deploy-all -DefinitionFile:"<BizTalk Installation Folder>\AS2ResendActivityDefs.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

    `"<BizTalk Installation Folder>\Tracking\bm.exe" update-all -DefinitionFile:"<BizTalk Installation Folder>\Microsoft.BizTalk.Configuration.EdiAS2.UpgradeR2toR3.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

    `"<BizTalk Installation Folder>\Tracking\bm.exe" update-all -DefinitionFile:"<BizTalk Installation Folder>\Microsoft.BizTalk.Configuration.Batching.UpgradeR2toR3.xml" -Server:"<BAM Database Server Name>" -Database:"<BAM Database Name>"`

- **Erreur SSO sur le cluster** : Dans un environnement de cluster d’exécution BizTalk Server, lorsque vous tentez d’effectuer une mise à niveau, un message d’erreur peut s’afficher :

    `SSO Master Secret Server service is not running on <Cluster name>.Please start the service to continue the upgrade.` 

    Pour résoudre ce problème, actualisez les services SSO dans le cluster SSO et le cluster d’exécution BizTalk Server.

    **Pour actualiser les services SSO dans le cluster SSO** :

    1. Dans Administrateur de cluster, **mettez en ligne** le groupe du cluster qui contient la ressource de service Enterprise SSO en cluster. Cela doit démarrer toutes les ressources dans le groupe du cluster.

    2. **Mettez hors connexion** l’instance en cluster du service Enterprise SSO. Ensuite, remettez-la **en ligne**.

    3. **Déplacez** le groupe du cluster. Cette opération doit déplacer le groupe du cluster contenant la ressource des services Enterprise SSO en cluster du premier nœud vers le second.

    4. **Mettez hors connexion** l’instance en cluster du service Enterprise SSO. Ensuite, remettez-la **en ligne**.

    **Pour actualiser les services SSO dans un cluster d’exécution BizTalk Server** :

    1. Dans Administrateur de cluster, **mettez en ligne** le groupe du cluster qui contient la ressource d’exécution BizTalk Server en cluster. Cela doit démarrer toutes les ressources dans le groupe du cluster.

    2. **Mettez hors connexion** l’instance en cluster des services Enterprise SSO. Ensuite, remettez-la **en ligne**.

    3. **Déplacez** le groupe du cluster. Cette opération doit déplacer le groupe du cluster contenant la ressource d’exécution BizTalk Server en cluster du premier nœud vers le second.

    4. **Mettez hors connexion** l’instance en cluster des services Enterprise SSO. Ensuite, remettez-la **en ligne**.