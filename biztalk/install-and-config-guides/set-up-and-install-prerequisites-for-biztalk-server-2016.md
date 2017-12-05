---
title: Configurer et installer les composants requis pour BizTalk Server 2016 | Documents Microsoft
description: "Instructions détaillées pour installer et configurer les logiciels requis et les paramètres de BizTalk Server 2016"
author: MandiOhlinger
manager: anneta
ms.prod: biztalk-server
ms.custom: 
ms.date: 11/30/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa70b621-903a-4cfa-9cb0-c6a82ed8f733
caps.latest.revision: "11"
ms.author: mandia
ms.openlocfilehash: 2f03aaf7d33cc494320d1ef0944b48286bc1b24c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="set-up-and-install-prerequisites-for-biztalk-server-2016"></a>Installation et configuration des composants logiciels requis pour BizTalk Server 2016
Configurez le serveur, puis installez et configurez les composants logiciels requis.

## <a name="join-the-administrators-group"></a>Rejoindre le groupe d’administrateurs
Pour installer et configurer BizTalk Server, connectez-vous au serveur à l’aide d’un compte d’administrateur sur l’ordinateur local. Ajoutez les comptes d’utilisateurs qui administrent le serveur BizTalk Server au groupe Administrateurs local :

1.  Dans le menu Démarrer, ouvrez **Gestion de l’ordinateur**.

    * Ou, ouvrez **Outils d’administration**, puis sélectionnez **Gestion de l’ordinateur**.
    * Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Gestion de l’ordinateur**.
  
2.  Développez **Utilisateurs et groupes locaux** et sélectionnez **Groupes**.
3.  Cliquez avec le bouton droit sur le groupe **Administrateurs** et sélectionnez **Ajouter au groupe**. **Ajoutez** vos comptes et sélectionnez **OK** pour enregistrer les modifications. 

## <a name="change-the-computer-name-optional"></a>Modifier le nom d’ordinateur (facultatif)
Si le nom de votre ordinateur est supérieur à 15 caractères, la configuration de BizTalk Server échoue. Pour modifier le nom d’ordinateur en moins de 15 caractères :

1.  Dans **Gestionnaire de serveur** > **Tableau de bord**, sélectionnez **Serveur local**. 
2.  Dans **Propriétés**, sélectionnez la propriété Nom de l’ordinateur pour la modifier.
3. Redémarrez l’ordinateur. 

**VOIR AUSSI** : Commande Windows PowerShell [Rename-Computer](https://technet.microsoft.com/library/hh849792.aspx)

## <a name="enable-network-dtc-access"></a>Activation de l’accès DTC réseau
Si BizTalk et SQL Server sont installés sur des ordinateurs distincts, activez l’accès DTC réseau sur le serveur BizTalk Server et le serveur SQL Server. 

1. Dans le menu Démarrer, ouvrez « dcomcnfg ».

    * Ou, ouvrez **Outils d’administration**, puis sélectionnez **Services de composants**.
    * Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Services de composants**.
  
2. Développez **Services de composants**, **Ordinateurs**, **Poste de travail**, puis **Distributed Transaction Coordinator**.
3. Cliquez avec le bouton droit sur **DTC local**, puis sélectionnez **Propriétés**.
4. Accédez à l’onglet **Sécurité** et vérifiez les éléments suivants :  
    * Accès DTC réseau
    * Autoriser les transactions entrantes
    * Autoriser les transactions sortantes
    * Aucune authentification requise
5. Sélectionnez **OK**. Si vous êtes invité à redémarrer MS DTC, sélectionnez **Oui**. 

Pour obtenir des paramètres supplémentaires qui peuvent être nécessaires, consultez [Résolution des problèmes liés à MSDTC](../core/troubleshooting-problems-with-msdtc.md).

## <a name="configure-application-event-log-optional"></a>Configurer le journal des événements Application (facultatif)

Le programme d'installation de BizTalk Server conserve un enregistrement des événements dans le journal des événements de l'application. Selon les fonctionnalités de BizTalk Server installées, il se peut que la limite d'espace requis dans le journal soit dépassée. L’installation échoue si le journal des événements de l’application ne dispose plus de suffisamment d’espace lors de l’installation. Le fait de modifier les paramètres du journal d'événements d'applications permet d'empêcher cet échec.

1. Dans le menu Démarrer, ouvrez l’**Observateur d’événements** :

    * Ou, ouvrez **Outils d’administration**, puis sélectionnez **Observateur d’événements**.
    * Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Observateur d’événements**.
  
2. Développez **Journaux Windows**, cliquez avec le bouton droit sur **Application**, puis sélectionnez **Propriétés**. 
3. Pour déterminer l’espace disponible, comparez les propriétés **Taille du journal** et **Taille maximale du journal**. 

    * Pour ajouter de l’espace, entrez un plus grand nombre dans **Taille maximale du journal**.
    * Pour activer le remplacement des anciens événements lorsque le journal est plein, sélectionnez **Remplacer les événements si nécessaire**.
    * Pour effacer les événements du journal, sélectionnez **Effacer le journal**.

4. Sélectionnez **OK**.

## <a name="edge-cant-be-opened-optional"></a>Bord ne peut pas être ouvert (facultatif)

Lorsque vous utilisez Edge, le message suivant s’affiche :  
`Microsoft Edge can't be opened using the Built-in Administrator account. Sign in with a different account and try again.`

Pour permettre d’ouvrir Edge à l’aide du compte Administrateur intégré :

1. Dans le menu Démarrer, ouvrez **Stratégie de sécurité locale**. Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Outils**, puis sélectionnez **Stratégie de sécurité locale**.
2.  Développez **Stratégies locales** et sélectionnez **Options de sécurité**. 
3.  Accédez à la stratégie **Contrôle de compte d’utilisateur : mode Approbation administrateur pour le compte Administrateur intégré** et **activez** la stratégie. 
4. Sélectionnez **OK** et redémarrez l’ordinateur.

## <a name="install-windows-updates"></a>Installation des mises à jour Windows

Veillez à installer les dernières mises à jour critiques de Windows. 

1. Dans le menu Démarrer, ouvrez **Mises à jour Windows** et recherchez des mises à jour. Vous pouvez également ouvrir **Paramètres** et sélectionner **Mise à jour et sécurité**.
2. Après avoir installé les mises à jour, vous devrez peut-être redémarrer l'ordinateur.

## <a name="enable-iis"></a>Activer IIS
BizTalk Server requiert IIS pour les composants suivants :

- adaptateur HTTP
- adaptateur SOAP
- Adaptateur Windows SharePoint Services
- Chiffrement SSL (Secure Sockets Layer)
- Portail BAM
- Routage

IIS est fourni avec le système d’exploitation comme **rôle** ou **fonctionnalité**, selon le système d’exploitation. Pour installer :

1. Dans le menu Démarrer, ouvrez **Activer ou désactiver des fonctionnalités Windows**. Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Gérer**, puis sélectionnez **Ajouter des rôles et des fonctionnalités**.
2. Sélectionnez **Services Internet (IIS)** ou **Serveur Web (IIS)**. En plus des options activées par défaut, sélectionnez également ce qui suit : 

    **Windows 10**
    - Dans **Outils d’administration Web**, cochez également :  
        - Compatibilité avec la gestion IIS 6
        - Console de gestion IIS 6
        - Outils de script IIS 6 (installe adsutil.vbs)
        - Compatibilité avec la métabase IIS et la configuration IIS 6
        - Console de gestion IIS
    - Dans **Services World Wide Web**, développez **Sécurité** et cochez également :
        - Authentification de base
        - Authentification Windows    

    **Windows Server**
    - Dans **Sécurité**, cochez également : 
        - Authentification de base
        - Authentification Windows    
    - Dans **Outils de gestion**, cochez également :  
        - Console de gestion IIS
        - Compatibilité avec la gestion IIS 6
        - Compatibilité avec la métabase de données IIS 6
        - Console de gestion IIS 6
        - Outils de script IIS 6 (installe adsutil.vbs)

3. Poursuivez l’installation et redémarrez l’ordinateur si vous y êtes invité. 

**VOIR AUSSI** : Installation d’IIS sur [Windows 8 ou Windows Server 2012](http://www.iis.net/learn/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012).


## <a name="run-64-bit-bam-portal-optional"></a>Exécution 64 bits du portail BAM (facultatif)
Si vous n’utilisez pas le portail BAM, vous pouvez ignorer cette section. 

Le portail BAM s’exécute en mode 32 bits. Si vous utilisez Internet Information Services (IIS) dans un environnement 64 bits, puis définissez le pool d’applications à s’exécuter en mode 32 bits. 

#### <a name="using-adsutilvbs"></a>Utilisation d’adsutil.vbs
1.  Ouvrez une invite de commandes comme administrateur. 
2.  À l’invite de commandes, tapez :  
    `cscript c:\inetpub\adminscripts\adsutil.vbs SET W3SVC/AppPools/Enable32bitAppOnWin64 1`
3. Appuyez sur Entrée.

#### <a name="using-iis-manager"></a>Utilisation du Gestionnaire des services Internet
1. Dans le menu Démarrer, ouvrez « inetmgr ».
2.  Développez le nom de l’ordinateur et sélectionnez **Pools d’applications**.
3.  Cliquez avec le bouton droit sur **DefaultAppPool** et sélectionnez **Paramètres avancés**. 
4.  Modifiez la valeur de **Activer les applications 32 bits** en spécifiant **True**. 
5.  Sélectionnez **OK**.

## <a name="install-windows-identity-foundation-wif-optional"></a>Installation de Windows Identity Foundation (WIF) (facultatif)
Si vous utilisez l’adaptateur SharePoint Services, BizTalk Server requiert WIF. Si vous n’utilisez pas l’adaptateur SharePoint Services, vous pouvez ignorer cette section.

Windows Identity Foundation est inclus dans le système d’exploitation comme **fonctionnalité**.

1. Dans le menu Démarrer, ouvrez **Activer ou désactiver des fonctionnalités Windows**. Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Gérer**, puis sélectionnez **Ajouter des rôles et des fonctionnalités**.
2. Sélectionnez **Windows Identity Foundation 3.5** et poursuivez l’installation. 
3. Redémarrez l’ordinateur, si vous y êtes invité.

## <a name="install--configure-smtp-server-optional"></a>Installer et configurer le serveur SMTP (facultatif)
Si vous utilisez des alertes BAM, BizTalk Server requiert serveur SMTP. Si vous n’utilisez pas les alertes BAM, vous pouvez ignorer cette section.

La fonctionnalité Messagerie de base de données SQL Server utilise un serveur SMTP pour envoyer les alertes BAM. Le serveur SMTP peut être installé localement sur le serveur BizTalk Server ou sur un autre serveur doté d’IIS. Le serveur SMTP n’est pas disponible sur les systèmes d’exploitation clients, tels que Windows 8.1 ou Windows 10. 

Le serveur SMTP est inclus avec les systèmes d’exploitation serveurs comme **fonctionnalité**.

1. Dans le menu Démarrer, ouvrez **Activer ou désactiver des fonctionnalités Windows**. Ou, ouvrez le **Gestionnaire de serveur**, sélectionnez **Gérer**, puis sélectionnez **Ajouter des rôles et des fonctionnalités**.
2. Sélectionnez **Serveur SMTP** et poursuivez l’installation. 
3. Redémarrez l’ordinateur, si vous y êtes invité.

## <a name="install-excel-2016-or-2013-optional"></a>Installez Excel 2016 ou 2013 (facultatif)
Si vous utilisez analyse BAM (Business Activity), BizTalk Server requiert Excel. Si vous n’utilisez pas BAM, vous pouvez ignorer cette section.

Le classeur BAM Office Excel définit les processus d'entreprise que vous souhaitez analyser. Vous utilisez également le classeur Excel BAM pour définir la manière dont les utilisateurs des activités visualisent les données collectées par l’analyse BAM.

> [!IMPORTANT] 
> * BizTalk Server prend en charge uniquement la version 32 bits de Microsoft Office. 
> * Pour charger correctement le fichier BAM.xla dans Excel, installez **Visual Basic pour Applications** (sous **Composants partagés d’Office**). Sinon, vous pouvez obtenir l’erreur : `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`

#### <a name="install-excel-2016"></a>Installation d’Excel 2016

Office 2016 est installé à l’aide de la fonctionnalité « Démarrer en un clic » ou « Programme d’installation C2R ». L’installation C2R télécharge et installe tous les programmes dans Office. Pour l’analyse BAM, nous avons besoin d’Excel uniquement. Pour contourner ce problème, téléchargez et installez l’[outil de déploiement Office 2016](https://www.microsoft.com/download/details.aspx?id=49117) pour personnaliser le programme d’installation C2R.

1. Téléchargez et installez l’[outil de déploiement Office 2016](https://www.microsoft.com/download/details.aspx?id=49117).
2. Dans le dossier contenant les fichiers de l’outil de déploiement Office 2016 que vous avez extraits, ouvrez le fichier **configuration.xml** avec un éditeur de texte tel que le bloc-notes.
3. Remplacez la section `<Configuration>` par ce qui suit :  

    ```
    <Configuration>
    <Add SourcePath="D:\" OfficeClientEdition="32">
    <Product ID="O365ProPlusRetail" >
      <Language ID="en-us" />
      <ExcludeApp ID="Access" />
      <ExcludeApp ID="Groove" />
      <ExcludeApp ID="InfoPath" />
      <ExcludeApp ID="Lync" />
      <ExcludeApp ID="OneDrive" />
      <ExcludeApp ID="OneNote" />
      <ExcludeApp ID="Outlook" />
      <ExcludeApp ID="PowerPoint" />
      <ExcludeApp ID="Project" />
      <ExcludeApp ID="Publisher" />
      <ExcludeApp ID="SharePointDesigner" />
      <ExcludeApp ID="Visio" />
      <ExcludeApp ID="Word" />
    </Product>
    </Add>
    </Configuration>
    ```
    
    Remplacez « SourcePath » par l’emplacement de votre fichier ISO d’Office 2016.
4. Dans le dossier contenant les fichiers de l’outil de déploiement Office 2016, maintenez la touche **Maj** enfoncée et cliquez avec le bouton droit sur une zone vide du dossier. Sélectionnez **Ouvrir une fenêtre de commandes ici**. 
5. Démarrez l’installation d’Excel en entrant la commande suivante :  
  `setup.exe /configure configuration.xml`

    > [!TIP]
    > `setup.exe /download configuration.xml` télécharge les fichiers d’installation Office nécessaires.
 
6. Sélectionnez Excel et poursuivez l’installation. 
 
**VOIR AUSSI** : [Options de configuration pour l’outil Déploiement d’Office](https://technet.microsoft.com/library/jj219426.aspx) et [Installer Office 2016 ou 2013](https://support.office.com/article/Install-Office-on-your-PC-or-Mac-4414eaaf-0478-48be-9c42-23adc4716658)

#### <a name="install-excel-2013"></a>Installation d’Excel 2013
1. Exécutez le programme d'installation de Microsoft Office.
2. Sélectionnez une **installation personnalisée**, puis sélectionnez Excel.
3. Poursuivez l’installation.   

## <a name="install-visual-c-redistributable-package"></a>Installer le package redistribuable Visual C++

Téléchargez et installez le [package redistribuable Visual C++](https://support.microsoft.com/help/3179560/update-for-visual-c-2013-and-visual-c-redistributable-package). La version 2013 est requise, même si Visual Studio 2015 est utilisé.

Le [téléchargements de Visual C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads) répertorie toutes les versions disponibles.

## <a name="install-visual-studio-2015-optional"></a>Installation de Visual Studio 2015 (facultatif)
BizTalk Server nécessite Visual Studio pour créer des projets BizTalk à l’aide des outils de développement. S’il s’agit d’un serveur intermédiaire ou de production, ou si vous ne faites aucun développement BizTalk, ignorez cette section.

L’édition Visual Studio Enterprise est recommandée, mais les éditions Professionnal et Community sont également prises en charge. 

1. Exécutez l'installation de Visual Studio en tant qu'administrateur.
2. Sélectionnez une installation **par défaut**. BizTalk Server ne nécessite aucune des fonctionnalités facultatives.

    > [!NOTE]
    > Si vous utilisez Visual Studio pour plusieurs projets BizTalk, sélectionnez l’installation **personnalisée** pour installer d'autres fonctionnalités. Certaines fonctionnalités courantes incluent Microsoft Web Developer Tools, les outils de développement Microsoft Office, les outils PowerShell pour Visual Studio et les outils de publication ClickOnce.
 
3. Poursuivez l’installation et redémarrez l’ordinateur si vous y êtes invité.

**VOIR AUSSI** : [Installation de Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)

> [!IMPORTANT]
> - Si vous installez Visual Studio avant d’installer BizTalk Server, puis effectuez une mise à niveau vers Visual Studio Team Explorer, vous devrez peut-être réparer votre installation BizTalk Server.
> - Visual Studio installe automatiquement Microsoft SQL Server Express, qui n’est pas utilisé par BizTalk Server. Désinstallez Microsoft SQL Server Express. Vous pouvez également désinstaller Microsoft SQL Server Compact.  
> - Les outils de développement de BizTalk Server sont basés sur Visual Studio. Au minimum, installez le composant Microsoft Visual C#® .NET avant d’installer les outils et kit de développement de BizTalk Server.
> - Le composant d’exécution de BizTalk Server nécessite .NET Framework 4.6. Si l’adaptateur de Windows Communication Foundation (WCF) ou l’intercepteur WCF est installé, .NET Framework 3.0 est requis

#### <a name="uninstall-sql-server-express"></a>Désinstallation de SQL Server Express
1. Dans le menu Démarrer, ouvrez **Programmes et fonctionnalités**. Ou, ouvrez le **Panneau de configuration** et sélectionnez **Désinstaller un programme**.
2. Désinstallation : 
    - Microsoft SQL Server 2014 Express LocalDb
    - Microsoft SQL Server Compact 4.0 SP1 x64 ENU
    - Microsoft SQL Server 2016 LocalDB (SQL Server 2016 Express LocalDB)
    
3. Poursuivez la désinstallation et redémarrez l’ordinateur si vous y êtes invité. 

## <a name="install-sql-server-2016"></a>Installer SQL Server 2016
BizTalk Server nécessite SQL Server. SQL Server peut être installé sur le même ordinateur que BizTalk ou sur un autre ordinateur. La plupart des environnements de production installent BizTalk et SQL sur des serveurs distincts. 

> [!IMPORTANT]
> - SQL Server Express Edition n’est pas recommandé ou pris en charge. Cette édition n'inclut pas certaines fonctionnalités requises par BizTalk Server.
> - BizTalk Server prend en charge l’édition SQL Standard. Toutefois, pour pouvoir utiliser l’agrégation en temps réel (RTA) de Business Activity Monitoring, installez SQL Server Enterprise Edition. L’agrégation en temps réel (RTA) de BAM n’est pas prise en charge dans SQL Server Standard Edition.
> - Pour utiliser pleinement le kit SDK BizTalk Server ou déployer des applications BizTalk Server à partir de Visual Studio, installez les outils de développement SQL Server.
> - BizTalk Server prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l’exception des classements binaires. Les classements binaires ne sont pas pris en charge.

**Pour les étapes d’installation spécifiques, consultez** [installer SQL Server 2016](https://docs.microsoft.com/sql/database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup) ou [installer SQL Server 2014](https://msdn.microsoft.com/library/bb500469(v=sql.120).aspx).

1. Démarrez l’installation de SQL Server. 
2. Durant la configuration des fonctionnalités, sélectionnez les éléments suivants :
    - Services Moteur de base de données
        - Réplication SQL Server
        - R Services (de-de base de données) (**facultatif**; info à [SQL Server R Services](https://docs.microsoft.com/sql/advanced-analytics/r/sql-server-r-services))
        - Extraction en texte intégral et extraction sémantique de recherche
    - Analysis Services
    - Reporting Services - Natif
    - Fonctionnalités partagées
        - Connectivité des outils clients
        - Integration Services

    > [!NOTE]
    > **SQL Server Data Tools** n’est pas inclus dans l’installation par défaut de SQL Server. Il n’est pas obligatoire, mais peut être téléchargé dans [Télécharger SSDT (SQL Server Data Tools)](https://docs.microsoft.com/sql/ssdt/download-sql-server-data-tools-ssdt). Téléchargez [**SQL Server Management Studio (SSMS)**](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms) qui fonctionne avec toutes les versions prises en charge de SQL Server, y compris la base de données SQL Azure. 

3. Poursuivez l’installation et redémarrez l’ordinateur si vous y êtes invité.

## <a name="disable-shared-memory"></a>Désactivez la mémoire partagée

1. Ouvrez le **Gestionnaire de configuration SQL Server**.
2. Dans le Gestionnaire de Configuration SQL Server, développez **Configuration du réseau SQL Server**, puis sélectionnez **protocoles pour MSSQLSERVER**.
3. Cliquez avec le bouton droit sur **Mémoire partagée**, puis sélectionnez **Désactiver**.
4. Sélectionnez **SQL Server Services**, avec le bouton droit SQL **Server (MSSQLSERVER)**, puis sélectionnez **arrêter**. Une fois le service arrêté, cliquez sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Démarrer**.
5. Fermez le **Gestionnaire de configuration SQL Server**.

En règle générale, le protocole de mémoire partagée affecte uniquement les clients (BizTalk Server) qui sont installés sur le même ordinateur que SQL Server. Dans certains cas de surcharge (comme des clients accédant à SQL Server à partir d'un seul ordinateur), il est possible que le protocole de mémoire partagée pour SQL Server diminue les performances de BizTalk Server. La désactivation du protocole réseau de mémoire partagée pour résoudre le problème.

> [!TIP]
> Si l’Agent SQL Server ne parvient pas à démarrer après la désactivation de mémoire partagée, puis confirmez [ODBC Driver 13.1 for SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) est installé.

## <a name="install-sql-xml-4"></a>Installation de SQL XML 4
Requis pour le moteur d’exécution BizTalk Server, les outils d’administration et l’analyse BAM. 

Téléchargez et installez [SqlXml 4.0](https://www.microsoft.com/download/details.aspx?id=30403).

## <a name="configure-sql-database-mail-optional"></a>Configurer la messagerie de base de données SQL (facultatif)
Si vous utilisez des alertes BAM, BizTalk Server requiert la messagerie de base de données SQL Server. Si vous n’utilisez pas les alertes BAM, ignorez cette section. 

**VOIR AUSSI** : Informations complémentaires sur la [messagerie de base de données](https://docs.microsoft.com/sql/relational-databases/database-mail/database-mail).

> [!IMPORTANT]
> - Vous devez connaître le nom de serveur et le numéro de port TCP du serveur SMTP. Si vous avez installé IIS et le serveur SMTP sur cet ordinateur, vous utilisez le serveur SMTP local. Si le serveur SMTP nécessite une authentification, préparez le nom d’utilisateur et le mot de passe.
> - Le portail BAM et les alertes BAM sont des fonctionnalités distinctes. Si vous utilisez des alertes BAM, la messagerie de base de données SQL Server est requise. Si vous n’utilisez pas les alertes BAM, la messagerie de base de données SQL Server n’est pas requise.

**Pour les étapes de configuration spécifiques, consultez**: configurer [messagerie de base de données SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/database-mail/configure-database-mail) ou [messagerie de base de données SQL Server 2014](https://msdn.microsoft.com/library/hh245116(v=sql.120).aspx).

   
Pour envoyer un e-mail de test : 
1.  Cliquez avec le bouton droit sur **Messagerie de base de données** et sélectionnez **Envoyer un message électronique de test**. 
2.  Entrez une adresse e-mail **À :**, puis sélectionnez **Envoyer un message électronique de test**.  
 
Si le destinataire **À :** a reçu l’e-mail, la messagerie de base de données est configurée. 

## <a name="install-winscp-optional"></a>Installer WinSCP (facultatif)
Requis par l’adaptateur FTP. Si vous n’utilisez pas l’adaptateur FTP, ignorez cette section. 

Téléchargez et installez [WinSCP](http://winscp.net). 

## <a name="next-step"></a>Étape suivante
Installez [BizTalk Server 2016](../install-and-config-guides/install-biztalk-server-2016.md).
