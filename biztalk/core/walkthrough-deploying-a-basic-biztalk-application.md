---
title: "Procédure pas à pas : Déploiement d’une Application de base BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, tutorials
- tutorials, deploying
- tutorials, applications
- applications, tutorials
ms.assetid: 21b67153-0f8c-406a-a224-fc792b16192f
caps.latest.revision: "69"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db86f672cd17965ec76877cc3867594bf82b40d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-deploying-a-basic-biztalk-application"></a>Procédure pas à pas : Déploiement d’une Application de base BizTalk
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient des fonctionnalités qui simplifient la gestion et le déploiement des solutions d'entreprise BizTalk. Il fournit désormais un conteneur d'applications pour les éléments qui composent les solutions d'entreprise (orchestrations, pipelines, schémas, mappages et assemblys .NET). Vous pouvez gérer, modifier, déployer et installer tous les éléments d’une application comme une unité unique. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]inclut également des Assistants pour vous aider à automatiser les tâches de déploiement d’application. Pour plus d’informations, consultez [déploiement d’Application et les fonctionnalités de gestion](../core/application-deployment-and-management-features.md) et [déploiement d’Application et les outils de gestion](../core/application-deployment-and-management-tools.md).  
  
 Cette procédure pas à pas vous fournit des instructions détaillées sur l'utilisation des fonctionnalités de déploiement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et vous montre leur fonctionnement. Le processus de déploiement expliqué dans cette procédure pas à pas ne reflète pas nécessairement le processus de déploiement d'applications utilisé par votre entreprise.  
  
 Dans cette procédure, vous allez créer une simple application BizTalk et la déployer à partir de l'environnement de développement dans un environnement de test, puis dans les environnements intermédiaire et de production. Une fois cette procédure pas à pas terminée, vous saurez comment effectuer les tâches suivantes :  
  
-   À partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur un ordinateur de développement, vous saurez utiliser la commande Déployer afin de procéder au déploiement d'assemblys BizTalk dans une instance locale de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous créerez ainsi une application BizTalk contenant ces assemblys. Un assembly BizTalk contient des informations sur les ressources utilisées dans une solution BizTalk Server (par exemple, des orchestrations, des pipelines, des schémas et des mappages).  
  
-   À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, ajouter, créer, configurer et supprimer des éléments (appelé *artefacts*) en fonction des besoins pour créer une solution d’entreprise pleinement fonctionnelle, telles que d’envoyer et recevoir des ports, les stratégies et les assemblys, et scripts.  
  
-   Vous saurez utiliser les Assistants Exportation, Importation et Installation pour le déploiement de l'application BizTalk sur un ordinateur de test afin de procéder au test du système et de ses fonctionnalités.  
  
-   Vous saurez utiliser les Assistants Exportation, Importation et Installation pour le déploiement de l'application sur un serveur intermédiaire afin de procéder à sa configuration finale et à son déploiement dans un serveur de production.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Deux options s'offrent à vous pour la configuration de votre environnement de test pour cette procédure pas à pas :  
  
-   Vous pouvez exécuter les tâches décrites dans cette procédure pas à pas sur un seul ordinateur.  
  
-   Vous pouvez simuler avec plus de précision le déploiement réel en paramétrant divers ordinateurs qui vous serviront pour les étapes de développement, intermédiaires, de test et de production. Cependant, aucune des tâches de cette procédure pas à pas ne doit être effectuée dans un véritable environnement de production.  
  
 Avant de suivre les étapes de cette procédure pas à pas, assurez-vous que votre environnement de test répond aux critères suivants :  
  
-   Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] est installé sur l'ordinateur de développement à partir duquel vous déployez les assemblys BizTalk ;  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur chaque ordinateur utilisé dans le processus de déploiement d'application décrit dans cette procédure pas à pas, y compris l'ordinateur de développement ;  
  
-   chaque instance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] correspond à une installation distincte ; en d'autres termes, elle possède ses propres bases de données et groupes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Outre les conditions requises ci-dessus, vous avez également besoin d'une solution [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ou d'un projet qui contienne des assemblys BizTalk. Si vous ne possédez aucune solution ou aucun projet, utilisez l'exemple de solution ErrorHandling inclus dans le kit de développement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à cet effet. Vous trouverez des instructions relatives à l'utilisation de cet exemple dans cette procédure.  
  
 Vous devez également posséder un compte d'utilisateur membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et du groupe Administrateurs locaux sur les ordinateurs que vous utiliserez pour effectuer les tâches de cette procédure.  
  
 Pour plus d’informations sur l’installation et la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [nouveautés, installer, configurer et mise à niveau](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).
  
##  <a name="BKMK_Assumptions"></a>Hypothèses  
 Cette procédure pas à pas repose sur les hypothèses suivantes :  
  
-   Vous possédez des connaissances de base sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [Prise en main de BizTalk Server](../core/getting-started-with-biztalk-server.md) devraient vous aider.
  
-   Les assemblys BizTalk que vous avez utilisés n'ont pas déjà été déployés dans une application de votre environnement de test. Dans le cas contraire, vous devez annuler le déploiement de l'application BizTalk dans laquelle ils ont été déployés. Pour obtenir des instructions, consultez [annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md).  
  
-   Les ressources de l'application ne sont pas partagées avec d'autres applications.  
  
##  <a name="BKMK_Audience"></a>Public visé  
 Cette procédure pas à pas vise le public suivant :  
  
-   **Développeurs d’applications BizTalk.** Les développeurs peuvent apprendre à définir les propriétés du projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et déployer des assemblys BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] à une application BizTalk. Ils peuvent également apprendre à ajouter des artefacts à l'application puis à exporter l'application dans un fichier .msi. Pour des informations générales sur les tâches de déploiement d’applications pour un développeur, consultez [tâches de développement pour le déploiement d’applications BizTalk](../core/development-tasks-for-biztalk-application-deployment.md).  
  
-   **Testeurs d’applications BizTalk.** Les testeurs peuvent apprendre à importer le fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en cours d’exécution sur leur ordinateur de test, ce qui l’inscrit comme une application BizTalk. Ils peuvent également apprendre à installer l'application sur l'ordinateur de test et à vérifier l'installation. Pour plus d’informations générales sur les tâches de déploiement d’application pour le test, consultez [tâches de test pour le déploiement d’applications BizTalk](../core/testing-tasks-for-biztalk-application-deployment.md).  
  
-   **Administrateurs IT BizTalk Server.** les administrateurs IT responsables du déploiement des applications BizTalk dans les serveurs intermédiaires et de production peuvent apprendre les bases requises à cette fin. Pour des informations générales sur les tâches de déploiement d’applications pour un administrateur informatique, consultez [des tâches de mise en lots pour le déploiement d’applications BizTalk](../core/staging-tasks-for-biztalk-application-deployment.md) et [des tâches de Production pour le déploiement d’Application BizTalk](../core/production-tasks-for-biztalk-application-deployment.md).  
  
##  <a name="BKMK_Overview"></a>Vue d’ensemble de cette procédure pas à pas  
 L'objectif de cette procédure est de déployer une application BizTalk dans un environnement de laboratoire afin d'évaluer le fonctionnement de cette technologie si elle était déployée dans votre environnement de production. Le scénario simple couvert par cette procédure (le déploiement d'un fichier .msi unique en tant qu'application BizTalk sur un seul ordinateur) vous aidera à vous familiariser avec les tâches de base impliquées dans le déploiement d'applications.  
  
> [!NOTE]
>  Cette procédure n'aborde pas la configuration des applications (liaison des orchestrations, configuration des ports, etc.), nécessaire à leur fonctionnement. Elle vise uniquement à vous présenter les nouvelles fonctionnalités de déploiement d'applications.  
  
 Les instructions fournies dans ce document concernent les tâches suivantes :  
  
1.  **Configuration des autorisations nécessaires.** avant de commencer à suivre la procédure, vous devez vous assurer que vous disposez des autorisations nécessaires à l'exécution de chaque tâche.  
  
2.  **Déploiement d’assemblys BizTalk à partir de Visual Studio.** cette étape est assurée par le développeur d'applications. Le déploiement d'assemblys BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] entraîne la création automatique des assemblys et le déploiement de leur contenu dans une application BizTalk. Si l'application n'existe pas encore, le déploiement des assemblys la crée automatiquement. Les artefacts de l'application sont inscrits et leurs données stockées dans la base de données de gestion BizTalk. De plus, les assemblys sont installés par défaut dans le Global Assembly Cache (GAC) de l'ordinateur local. Une fois l'application créée, vous pouvez afficher et gérer ses artefacts dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans la console Administration, chaque application est stockée dans son propre dossier, avec des sous-dossiers contenant les références à l'ensemble des artefacts de l'application.  
  
3.  **Configuration de l’application.** cette étape est assurée par le développeur d'applications ou l'administrateur IT et consiste à ajouter, créer et à configurer les artefacts requis pour le bon fonctionnement de l'application. Dans la console Administration de BizTalk Server, vous pouvez aisément ajouter, créer, configurer et supprimer des artefacts tels que des ports d'envoi et de réception, des scripts et des assemblys supplémentaires. Lorsque vous considérez que l'application contient les artefacts requis et qu'ils sont correctement configurés, vous pouvez l'exporter dans un fichier .msi, comme décrit ci-dessous.  
  
4.  **Exportation de l’application dans un fichier .msi.** cette étape est assurée par le développeur, le testeur ou l'administrateur IT et consiste à générer un fichier .msi qui peut servir à déployer une application BizTalk dans un environnement différent. Par exemple, le développeur peut exporter un fichier .msi que le testeur utilisera pour déployer l'application dans un serveur de test. Une fois l'étape de test terminée, l'administrateur IT peut alors utiliser le fichier .msi testé pour déployer l'application dans un serveur intermédiaire ou de production (comme décrit ci-dessous). Cette procédure pas à pas décrit l'exportation d'une application dans un fichier .msi à l'aide de l'Assistant Exportation, accessible à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
5.  **Importation et installation de l’application à partir du fichier .msi.** cette étape est assurée par le testeur ou l'administrateur IT et consiste à déployer une application BizTalk dans un serveur intermédiaire ou de production. Par exemple, le testeur peut importer l'application à partir d'un fichier .msi mis à disposition par le développeur dans un groupe BizTalk sur un ordinateur de test, puis installer l'application à partir du fichier .msi afin de la tester. De la même manière, l'administrateur IT peut déployer l'application à partir d'un fichier .msi fourni par le testeur dans un serveur intermédiaire ou de production. Cette procédure pas à pas décrit l'utilisation de l'Assistant Importation pour importer le fichier .msi dans une application d'un groupe BizTalk. Comme dans l'étape 2, les artefacts de l'application sont inscrits et leurs données stockées dans les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette procédure pas à pas décrit également l'installation de l'application sur le serveur actuel à l'aide de l’Assistant Installation ou en double-cliquant sur le fichier .msi. Vous pouvez ainsi exécuter l'application sur le serveur actuel.  
  
##  <a name="BKMK_Step-by-step"></a>Guide pas à pas pour déployer une application BizTalk  
 Cette section fournit des instructions détaillées pour le déploiement d'une application BizTalk en plusieurs phases, du développement à la production en passant par le test et la phase intermédiaire. Comme indiqué précédemment, vous pouvez accomplir ces étapes sur le même ordinateur ou, pour une simulation plus précise de votre environnement, sur plusieurs ordinateurs.  
  
#### <a name="1-configure-permissions"></a>1. Configuration des autorisations  
 La première étape consiste à vous assurer que vous disposez des autorisations nécessaires à l'exécution des tâches de cette procédure. Consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [sécurité minimales](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx).
  
#### <a name="2-deploy-the-biztalk-assemblies"></a>2. Déploiement des assemblys BizTalk  
 Suivez les instructions de cette étape pour déployer des assemblys BizTalk dans une application BizTalk à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] sur l'ordinateur de développement.  
  
 Avant de commencer, vérifiez que vous disposez d'une solution BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous pouvez créer votre propre solution ou projet, ou utiliser l'exemple de solution ErrorHandling inclus dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. Vous pouvez utiliser l'exemple de solution ErrorHandling dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] en procédant comme suit.  
  
###### <a name="to-set-up-the-errorhandling-solution"></a>Pour utiliser la solution ErrorHandling  
  
1.  Sur l'ordinateur de développement, accédez au répertoire :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Messaging\ErrorHandling\ErrorHandler  
  
2.  Double-cliquez sur **ErrorHandler.btproj**.  
  
     La solution ErrorHandler s'ouvre dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Cette solution se compose de deux projets : ErrorHandler et PipelinesAndSchemas.  
  
     ![Les projets Visual Studio dans une solution](../core/media/errorhandlingprojects.gif "ErrorHandlingProjects")  
  
 Ensuite, vous devez définir les propriétés de chacun des projets de la solution. L’exemple de solution ErrorHandling inclut deux projets pour lesquels vous devez définir les propriétés : ErrorHandler et PipeLinesAndSchemas. Configurez les propriétés de manière à ce qu'elles reflètent l'environnement de l'ordinateur de développement. Par exemple, le serveur SQL spécifié doit correspondre à l'instance en cours d'exécution sur l'ordinateur de développement, qui héberge la base de données de gestion BizTalk locale.  
  
###### <a name="to-configure-project-properties"></a>Pour configurer les propriétés de projet  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, avec le bouton droit un projet pour lequel vous souhaitez configurer les propriétés, puis cliquez sur **propriétés**.  
  
2.  Cliquez sur le **déploiement** onglet Concepteur de projets.  
  
     ![Feuille de propriétés de déploiement dans Visual Studio 2005](../core/media/deploymentproperties.gif "DeploymentProperties")  
  
3.  Configurer les propriétés de projet, comme décrit dans le tableau suivant, puis cliquez sur **OK**.  
  
    |Propriété|Valeur|Explication|  
    |--------------|-----------|-----------------|  
    |Application Name|\<Name>|Nom de l'application BizTalk dans laquelle déployer les assemblys de ce projet. Si l'application existe déjà, les assemblys seront ajoutés à celle-ci lors du déploiement du projet. Si l'application n'existe pas, elle sera créée. Si ce champ est vide, les assemblys sont déployés dans l'application BizTalk par défaut du groupe courant, soit « BizTalk Application 1 ». Les noms incluant des espaces doivent être placés entre guillemets doubles (").|  
    |Base de données de configuration|\<Nom de base de données de gestion BizTalk >|Nom de la base de données de gestion BizTalk pour le groupe, BizTalkMgmtDb par défaut.|  
    |Server|\<Nom du serveur >|Nom de l'instance SQL Server qui héberge la base de données de gestion BizTalk sur l'ordinateur local. Dans le cas d'une installation sur un seul ordinateur, il s'agit généralement du nom de l'ordinateur local. **Remarque :** si vous déplacez ce projet BizTalk vers un autre ordinateur, vous devez modifier la propriété de serveur afin de refléter le nouveau nom d’ordinateur avant de pouvoir déployer l’assembly.|  
    |Redéployer|True ou False|La définition de cette propriété sur True (valeur par défaut) vous permet de redéployer les assemblys BizTalk sans changer le numéro de version.|  
    |Installer dans le Global Assembly Cache|True ou False|La définition de cette propriété sur True (valeur par défaut) installe les assemblys dans le Global Assembly Cache (GAC) de l'ordinateur local lors du déploiement de l'application.|  
    |Redémarrer les instances d’hôte|True ou False|La définition de cette propriété sur True redémarre automatiquement toues les instances d'hôte s'exécutant sur l'ordinateur local lors du redéploiement de l'assembly. Si vous la définissez sur False (valeur par défaut), vous devez redémarrer les instances d'hôte manuellement lors du redéploiement d'un assembly. **Remarque :** si vous redéployez des assemblys de niveau de la solution, les instances d’hôte seront redémarrées une fois pour chaque projet dispose cette option est définie sur True. Cela peut donner lieu à des redémarrages multiples. Si vous prévoyez de redéployer au niveau de la solution, vous pouvez définir cette propriété sur True sur un seul projet de la solution afin d'éviter des redémarrages d'instance d'hôte multiples. Elle doit être définie sur le dernier projet qui sera redéployé dans la solution. Par ailleurs, si une instance d'hôte est arrêtée lors de l'exécution du redéploiement, elle ne sera pas démarrée.|  
    |Activer les tests unitaires|True ou False|Spécifie s’il faut activer les tests unitaires pour le projet.|  
  
4.  Répétez les étapes 1 à 3 pour chaque projet de la solution.  
  
 Le processus de déploiement requiert la signature avec un nom fort de l'assembly. Pour ce faire, associez le projet à un fichier de clé d'assembly de nom fort. Si cela n'a pas déjà été fait, suivez la procédure ci-dessous pour générer un fichier de clé d'assembly de nom fort.  
  
###### <a name="to-create-a-strong-name-assembly-key-file"></a>Pour créer un fichier de clé d'assembly de nom fort  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  À l'invite de commandes, à partir du dossier dans lequel vous voulez stocker le fichier de clé, tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
     **sn -k***nom_fichier* **.snk**   
  
     Exemple : **sn -k ErrorHandling.snk**  
  
     Un message de confirmation, **paire écrite dans la clé \<**  *nom_fichier***> .snk** `,` affiche sur la ligne de commande.  
  
 Ensuite, vous devez associer chaque projet de la solution au fichier de clé.  
  
###### <a name="to-associate-your-projects-with-the-key-file"></a>Pour associer vos projets au fichier de clé  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur le projet, puis **propriétés**.  
  
2.  Cliquez sur le **signature** onglet Concepteur de projets.  
  
3.  Dans le volet droit, activez la **signer l’assembly** boîte.  
  
4.  Cliquez sur la zone de liste déroulante sous **choisir un fichier de clé de nom fort**, cliquez sur  **\<Parcourir... >**, puis accédez au fichier de clé.  
  
5.  Cliquez sur le fichier de clé, puis cliquez sur **ouvrir**.  
  
6.  Répétez les étapes 1 à 5 pour chaque projet de la solution.  
  
 Vous pouvez désormais créer et déployer tous les assemblys de la solution en une étape, en procédant comme suit.  
  
###### <a name="to-deploy-the-assemblies-in-a-solution"></a>Pour déployer les assemblys dans une solution  
  
-   Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] l’Explorateur de solutions, cliquez sur la solution, puis cliquez sur **déployer la Solution**.  
  
     L'état du processus de compilation et de déploiement s'affiche dans l'angle inférieur gauche de la page. Si vous utilisez l'exemple de solution ErrorHandling, plusieurs messages d'avertissement s'affichent dans la fenêtre de sortie. Pour les besoins de cette procédure, vous pouvez les ignorer. Lorsque le déploiement est terminé, « déployer : 2 a réussi, 0 a échoué, 0 a été ignoré » s’affiche dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Sortie.  
  
 Le fait de déployer les assemblys BizTalk les inscrit en tant que composants de l'application BizTalk spécifiée dans la base de données de gestion BizTalk. Il remplit également la base de données avec tous les éléments, ou *artefacts*, contenus dans les assemblys. Si l'application n'existait pas avant le déploiement, cette étape la crée automatiquement. Vous pouvez désormais afficher l'application BizTalk et ses artefacts dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l'ordinateur de développement.  
  
###### <a name="to-view-the-biztalk-application-and-its-artifacts"></a>Pour afficher l'application BizTalk et ses artefacts  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez le dossier de l'application dans lequel vous venez de déployer vos assemblys.  
  
4.  Pour afficher le contenu d'un dossier, cliquez sur son nom dans le dossier de l'application. Dans les dossiers appropriés, vous devez voir les artefacts contenus dans les assemblys que vous avez déployés. Si vous avez déployé l'exemple de solution BizTalk ErrorHandling, vous devez voir les artefacts des dossiers Orchestrations, Schémas et Ressources. Vous pouvez cliquez sur un artefact et cliquez sur **propriétés** pour afficher ses paramètres de configuration.  
  
5.  Développez le **ressources** dossier, cliquez sur un des assemblys, puis cliquez sur **modifier**.  
  
6.  Dans le **Options** zone, notez les options de déploiement qui sont configurées pour l’assembly.  
  
7.  Dans **l’emplacement de Destination**, notez le chemin d’accès à l’emplacement où le fichier d’assembly sera copié lorsque l’application est installée. Il s'agit de l'emplacement source par défaut de l'assembly.  
  
> [!NOTE]
>  Si votre application ne s’affiche pas, cliquez sur **groupe BizTalk** et cliquez sur **Actualiser**.  
  
 Pour plus d’informations sur le déploiement des assemblys, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
#### <a name="3-configure-the-application"></a>3. Configurez l'application  
 Vous pouvez configurer votre application BizTalk en créant, en ajoutant et en configurant des artefacts dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour qu'une application fonctionne, elle doit être correctement configurée. Il faut, par exemple, que les orchestrations soient liées à un hôte, et que les ports d'envoi et les emplacements de réception soient configurés. Si vous avez déployé l'exemple de solution ErrorHandling, vous remarquerez que l'application ne possède ni port d'envoi, ni port de réception, ni emplacement de réception. Cela signifie que les orchestrations ne peuvent envoyer ni recevoir des messages. Cette procédure n'aborde pas les étapes de configuration d'une application. Pour les suivre, le plus simple est d'utiliser la boîte de dialogue Configurer l'application, accessible en cliquant avec le bouton droit sur l'application, puis en cliquant sur Configurer. Pour plus d’informations, consultez [comment configurer une Application](../core/how-to-configure-an-application.md). Il est également possible de configurer des orchestrations et de créer, configurer et supprimer des ports d'envoi, des groupes de ports d'envoi, des ports de réception et des emplacements de réception de manière individuelle. Pour plus d’informations, consultez les rubriques correspondantes de [la gestion des artefacts](../core/managing-artifacts.md).  
  
 Vous pouvez également ajouter des artefacts à votre application, tels que des scripts de pré-traitement ou des fichiers Lisezmoi, ou en supprimer. Cette fonction peut être testée en suivant les procédures ci-dessous. (L'exemple ErrorHandling ne comprend aucun artefact supplémentaire à ajouter ; cependant, vous pouvez tester cette fonction en ajoutant des éléments existant déjà dans votre environnement.)  
  
> [!NOTE]
>  Les scripts de pré-traitement et de post-traitement permettent de réaliser certaines actions avant ou après l'importation, l'installation ou la désinstallation d'une application. Par exemple, vous pouvez utiliser un script de pré-traitement pour désinstaller des assemblys du GAC suite à la désinstallation. Pour plus d’informations, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
###### <a name="to-add-an-artifact-to-an-application"></a>Pour ajouter un artefact à une application  
  
1.  Ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Pour ajouter les types suivants d’artefacts, cliquez sur le dossier d’application ErrorHandling, puis cliquez sur **ajouter**. Notez que lorsque vous ajoutez un assembly BizTalk, les artefacts qu'il contient sont également ajoutés aux dossiers appropriés de l'application.  
  
    -   Assemblys BizTalk  
  
    -   Scripts de pré-traitement  
  
    -   Scripts de post-traitement  
  
    -   Ressources (assemblys BizTalk, assemblys .NET, scripts de pré-traitement, scripts de post-traitement, fichiers, certificats, composants COM, artefacts BAM, fichiers de liaison et répertoires virtuels)  
  
    -   Stratégies  
  
 Vous pouvez également supprimer un artefact d'une application.  
  
###### <a name="to-remove-an-artifact-from-an-application"></a>Pour supprimer un artefact d'une application  
  
1.  Ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Développez le dossier contenant l’artefact, cliquez sur l’artefact, puis cliquez sur **supprimer**.  
  
 Pour plus d’informations sur la configuration de votre application, consultez [création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md).  
  
#### <a name="4-export-the-application"></a>4. Exportation de l'application  
 Après avoir créé une application BizTalk et l'avoir modifiée en fonction de vos besoins, vous pouvez l'exporter à l'aide de l'Assistant Exportation de fichier MSI de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Il permet de créer un fichier .msi que vous pouvez ensuite importer dans un autre groupe BizTalk pour y recréer l'application. Pour pouvoir exécuter l'application sur un serveur particulier, vous devez également l'installer localement à partir du fichier .msi.  
  
###### <a name="to-export-the-application"></a>Pour exporter l'application  
  
1.  Ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.  
  
3.  Cliquez sur l’application BizTalk, pointez sur **exporter**, puis cliquez sur **fichier MSI**.  
  
4.  Sur le **Bienvenue dans l’Assistant Exportation de fichier MSI** , cliquez sur **suivant**.  
  
5.  Sur le **sélectionner les ressources** , sélectionnez les ressources à exporter dans le fichier .msi, puis cliquez sur **suivant**. Pour les besoins de cette procédure, vous pouvez accepter les valeurs par défaut.  
  
6.  Si vous y êtes invité, dans le **spécifier les hôtes IIS** , tapez le nom du serveur de l’ordinateur qui héberge le répertoire virtuel que vous souhaitez inclure, puis cliquez sur **suivant**. Vous êtes invité à indiquer le serveur uniquement si le répertoire virtuel n'a pas encore été ajouté à la base de données de gestion BizTalk, comme lorsqu'il a été ajouté à l'application ou importé dans une application.  
  
    > [!NOTE]
    >  Il n'existe aucun répertoire virtuel inclus dans l'exemple de solution ErrorHandling.  
  
7.  Sur le **dépendances** page, vérifiez les dépendances de l’application, puis cliquez sur **suivant**.  
  
8.  Sur le **Destination** page **nom de l’application Destination**, tapez le nom de l’application.  
  
9. Dans **fichier MSI à générer**, tapez le chemin d’accès complet pour le fichier .msi, puis cliquez sur **exporter**. Exemple : C:\MSI\Errorhandling.msi  
  
    > [!NOTE]
    >  Nous vous recommandons d'enregistrer les fichiers .msi dans un dossier sécurisé.  
  
10. Sur le **Résumé** page, prenez note de l’emplacement du fichier journal pour cette opération, puis cliquez sur **Terminer**.  
  
 Dans le système de fichiers, vérifiez que le fichier .msi a été créé à l'emplacement spécifié.  
  
> [!NOTE]
>  Pour des raisons de sécurité, pendant l'exportation d'une application, les mots de passe sont supprimés des liaisons d'application. Après avoir installé l’application à partir du fichier .msi, vous devez reconfigurer les mots de passe afin que l’application de fonctionner. Les mots de passe ne sont cependant pas supprimés des fichiers de liaison ajoutés à l'application.  
  
 Pour plus d’informations sur l’exportation des applications et des artefacts, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
#### <a name="5-import-and-install-the-application"></a>5. Importation et installation de l'application  
 L'étape suivante consiste à importer l'application à partir du fichier .msi que vous venez de créer dans un autre groupe BizTalk, mais aussi à installer l'application sur l'ordinateur local. Pour ce faire, utilisez l'Assistant Importation de fichier MSI et l'Assistant Installation de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Vous devez installer l'application sur les ordinateurs du groupe qui doivent l'exécuter. Double-cliquez sur le fichier .msi pour l'installer sur d'autres ordinateurs.  
  
 Répétez les tâches de cette étape à chaque fois que vous voulez migrer une application d'un groupe BizTalk vers un autre, par exemple d'un environnement de développement vers un environnement de test, d'un environnement de test vers un environnement intermédiaire, ou d'un environnement intermédiaire vers un environnement de production.  
  
 À ce stade, si vous utilisez un seul ordinateur pour accomplir cette procédure, vous devez supprimer l'application du groupe BizTalk. Vous devez également désinstaller les assemblys du GAC (Global Assembly Cache). Ainsi, lorsque vous importerez l'application, vous pourrez vérifier qu'elle a été correctement recréée. Si vous utilisez plusieurs ordinateurs pour accomplir cette procédure, cela n'est pas nécessaire.  
  
###### <a name="to-delete-the-application-from-the-biztalk-group"></a>Pour supprimer l'application du groupe BizTalk  
  
1.  Ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Cliquez sur l’application et cliquez sur **supprimer**.  
  
###### <a name="to-delete-assemblies-from-the-gac"></a>Pour supprimer des assemblys du GAC  
  
1.  Dans le système de fichiers, accédez à %systemdrive%\Windows\assembly.  
  
2.  Sur chaque fichier d’assembly qui a été générée pour votre solution, cliquez **désinstallation**, puis cliquez sur **Oui** pour confirmer. Par exemple, les fichiers d'assembly associés au projet ErrorHandling sont ErrorHandling.ErrorHandler et ErrorHandling.PipelinesAndSchemas.  
  
     ![Supprimer un assembly dans le GAC](../core/media/deleteassembly.gif "DeleteAssembly")  
  
 Vous pouvez désormais importer l'application dans un groupe BizTalk. Si vous voulez importer l'application dans un groupe BizTalk s'exécutant sur un autre ordinateur, le fichier .msi doit être accessible à partir de cet ordinateur.  
  
> [!CAUTION]
>  Avant d'installer une application, assurez-vous que le fichier .msi provient d'une source approuvée. Un utilisateur malveillant peut inclure du code dans un fichier .msi, ce qui peut affecter votre système ou votre réseau. Pour plus d’informations, consultez [sécurité et Windows Installer](../core/security-and-windows-installer.md).  
  
###### <a name="to-import-and-install-the-application"></a>Pour importer et installer l'application  
  
1.  Ouvrez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'instance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans laquelle vous voulez importer l'application. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis développez **groupe BizTalk**.  
  
3.  Avec le bouton droit **Applications**, pointez sur **importation**, puis cliquez sur **fichier MSI**.  
  
4.  Sur le **Bienvenue dans l’Assistant Importation de** page **fichier MSI à importer**, tapez le chemin d’accès complet du fichier .msi, puis cliquez sur **suivant**. Exemple : C:\msi\MyApplication.msi  
  
5.  Sur le **paramètres de l’Application** page **applications disponibles auxquelles ajouter des références aux**, sélectionnez les applications auxquelles ajouter des références, puis cliquez sur **suivant**. Si vous utilisez l'exemple de solution ErrorHandling, vous pouvez accepter les valeurs par défaut.  
  
     ![Ajouter des références à une application](../core/media/appreferences.gif "AppReferences")  
  
6.  Sur le **paramètres d’environnement cible Application** page, vérifiez que  **\<par défaut >** est sélectionné, cliquez sur **suivant**.  
  
7.  Sur le **résumé d’importation** page, vérifiez que les informations de résumé sont correctes, puis cliquez sur **importation**.  
  
8.  Dans l’écran final de l’Assistant MSI d’importation, sélectionnez **exécuter l’Assistant Installation de Application pour installer l’application sur l’ordinateur local**, puis cliquez sur **Terminer**.  
  
     ![Démarrer l’installation à partir de l’Assistant Importation de](../core/media/startinstallation.gif "StartInstallation")  
  
9. Sur le **sélectionner le dossier** page **dossier**, tapez le chemin d’accès de l’installation de l’application BizTalk, puis cliquez sur **suivant**.  
  
10. Cliquez sur **suivant** sur les trois pages suivantes pour poursuivre l’installation.  
  
     Windows Installer installe l'application sur l'ordinateur local.  
  
11. Sur le **Installation complète** , cliquez sur **fermer**.  
  
 Pour plus d’informations sur l’importation d’applications, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Pour plus d’informations sur l’installation des applications, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
 Ensuite, assurez-vous que l'application a été importée et installée en vérifiant ce qui suit :  
  
-   l'application et tous ses artefacts existent dans le dossier de l'application dans la console Administration ;  
  
-   les assemblys de l'application existent dans le GAC ;  
  
-   les fichiers associés à l'application existent au niveau du chemin d'accès spécifié lors de l'installation de l'application ;  
  
-   l'application s'affiche dans la liste Ajout/Suppression de programmes du Panneau de configuration.  
  
-   Si vous avez configuré l’application afin qu’il peut fonctionne, par exemple en spécifiant l’envoi et ports de réception, vous pouvez démarrer l’application en dessus et en cliquant sur **Démarrer**. L'exemple d'application ErrorHandling n'est pas destiné à fonctionner ; vous ne pouvez donc pas le démarrer, sauf si vous l'avez configuré manuellement.  
  
-   Pour supprimer complètement l’application à partir du groupe BizTalk et de l’ordinateur local, suivez les instructions de [annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md).  
  
## <a name="see-also"></a>Voir aussi  
[Présentation de gestion et déploiement d’applications BizTalk](../core/understanding-biztalk-application-deployment-and-management.md)