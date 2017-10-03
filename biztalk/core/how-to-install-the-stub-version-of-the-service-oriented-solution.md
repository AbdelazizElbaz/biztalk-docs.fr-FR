---
title: "Comment installer la Version Stub du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IIS, installing virtual directories [service solutions]
- service solution tutorial, IIS virtual directories
- service solution tutorial, stub version
- deploying, BAM solutions [service solutions]
- service solution tutorial, solutions [BAM]
- service solution tutorial, service solutions
- SSO, configuring
- IBM WebSphere MQ Client
- service solution tutorial, IBM WebSphere MQ Client
- installing, tutorials
- service solutions, deploying
- service solution tutorial, SSO
- BAM, deploying solutions
- service solution tutorial, building solutions
- service solution tutorial, installing
ms.assetid: 45de7681-4df0-47a4-a02c-509140423a1e
caps.latest.revision: "53"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c000c733097bffa58f652801b459c429df149e56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-stub-version-of-the-service-oriented-solution"></a>Installation de la version stub du service orienté solutions
La procédure suivante décrit la préparation de votre ordinateur avant l'installation de la version stub de la solution orientée services, puis l'installation de la solution sur votre ordinateur.  
  
-   [Préparer l’ordinateur pour l’installation de la version stub de la Solution orientée services](#step1)  
  
-   [Installer le Client IBM WebSphere MQ pour Windows](#step3)  
  
-   [Créer les répertoires virtuels dans IIS pour la Solution orientée services](#step5)  
  
-   [Générez la Solution orientée services](#step7)  
  
-   [Créer les entrées de Enterprise Single Sign-On (SSO) et les valeurs dans la base de données SSO](#step9)  
  
-   [Déployer la définition BAM pour la Solution orientée services](#step11)  
  
-   [Déployer la Solution orientée services](#step13)  
  
##  <a name="step1"></a>Préparer l’ordinateur pour l’installation de la version stub de la Solution orientée services  
  
#### <a name="to-prepare-the-computer-for-installing-the-stub-version-of-the-service-oriented-solution"></a>Pour préparer l'ordinateur pour l'installation de la version stub de la solution orientée services  
  
1.  Assurez-vous que le **Site Web par défaut** est configuré pour utiliser ASP.NET 2.X.  
  
    1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
    2.  Dans le **Gestionnaire des Services Internet (IIS)**, le nom de l’ordinateur, développez **Sites**, développez **Site Web par défaut**, développez **aspnet_client**, développez **system_web**.  
  
    3.  Vérifiez que le sous-dossier est 2.X.  
  
2.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Services**. À l’aide de la **Services** de la console, assurez-vous que les services suivants sont en cours d’exécution :  
  
    -   **Publication du World Wide Web**  
  
3.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.  
  
4.  Si vous avez installé Windows SharePoint Services, excluez la (racine) de la **Site Web par défaut** à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes** , pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.  
  
    1.  Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.  
  
    2.  Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.  
  
    3.  Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.  
  
    4.  Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.  
  
    5.  Ouvrez une invite de commandes, puis exécutez IISReset.  
  
5.  Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.  
  
6.  Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir l'environnement %BTSSolutionsPath%. Fermez ensuite l'invite de commandes.  
  
    -   setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"  
  
        > [!NOTE]
        >  Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.  
  
        > [!NOTE]
        >  Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).  
  
##  <a name="step3"></a>Installer le Client IBM WebSphere MQ pour Windows  
  
#### <a name="to-install-the-ibm-websphere-mq-client-for-windows"></a>Pour installer le client IBM WebSphere MQ pour Windows  
  
1.  Téléchargez la dernière version du client IBM WebSphere MQ pour Windows.  
  
    > [!NOTE]
    >  Même si la version stub de la solution ne requiert pas IBM WebSphere Server, l'application cliente référence le fichier amqmdnet.dll fourni par le client IBM WebSphere MQ pour Windows, de sorte que vous devez installer ce dernier. Le client de la version stub n'appelle pas réellement une API dans la DLL. Il n'est requis que pour la compilation et l'exécution de l'application cliente. Vous pouvez télécharger le client IBM WebSphere MQ pour Windows depuis le site Web d'IBM.  
  
2.  Installez le client IBM WebSphere MQ pour Windows  
  
    > [!NOTE]
    >  Il n'est pas utile de configurer le client IBM WebSphere MQ pour Windows. Conservez les paramètres par défaut.  
  
3.  Ajoutez les classes WebSphere MQ pour l'assembly .NET au Global Assembly Cache (GAC).  
  
    1.  À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire \<répertoire d’Installation IBM MQSeries > \bin.  
  
    2.  Exécutez la commande suivante (vérifiez que gacutil.exe est inclus dans l'environnement PATH) :  
  
         `gacutil.exe /i amqmdnet.dll`  
  
##  <a name="step5"></a>Créer les répertoires virtuels dans IIS pour la Solution orientée services  
  
#### <a name="to-create-the-virtual-directories-in-iis-for-the-service-oriented-solution"></a>Pour créer les répertoires virtuels dans IIS pour la solution orientée services  
  
1.  Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **ajouter un Pool d’applications**.  
  
     Sur le **ajouter un Pool d’applications** boîte de dialogue, tapez `SSOStubAppPool` dans les **nom** zone de texte, puis cliquez sur **OK**.  
  
     Les répertoires virtuels utilisés par la solution orientée services incluent le service Web publié pour la version stub des orchestrations, le service Web SAP stub, le service Web Payment Tracker stub et le service Web Pending Transaction stub.  
  
2.  Dans le **Gestionnaire des Services Internet (IIS)**, cliquez sur le pool d’applications que vous venez de créée, puis cliquez sur **paramètres avancés**.  
  
3.  Cliquez dans la colonne à droite de la **identité** propriété, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
4.  Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez le **compte personnalisé** option, puis cliquez sur **définir**.  
  
5.  Dans le **définir les informations d’identification** boîte de dialogue, spécifiez un nom d’utilisateur et un mot de passe, confirmez le mot de passe, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Cet utilisateur doit être autorisé à exécuter le service Web Orchestration Proxy et être ajouté au groupe Administrateurs BizTalk Server, Administrateurs de l'authentification unique ou Administrateurs d'applications associées à authentification unique.  
  
6.  Cliquez sur **OK** pour fermer la **identité du Pool d’applications** boîte de dialogue.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue **Paramètres avancés** .  
  
8.  Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.  
  
    1.  À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub  
  
         Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub  
  
         Access Permissions = Read, Run scripts  
  
    2.  À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP  
  
         Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP  
  
         Access Permissions = Read, Run scripts  
  
    3.  À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions  
  
         Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans  
  
         Access Permissions = Read, Run scripts  
  
    4.  À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :  
  
         Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker  
  
         Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack  
  
         Access Permissions = Read, Run scripts  
  
9. Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.  
  
    2.  Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher. Cliquez sur **OK** pour quitter.  
  
10. Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.  
  
    2.  Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
11. Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.  
  
    2.  Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
12. Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :  
  
    1.  Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.  
  
    2.  Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**. Cliquez sur **OK** pour quitter.  
  
##  <a name="step7"></a>Générez la Solution orientée services  
  
#### <a name="to-build-the-service-oriented-solution"></a>Pour générer la solution orientée services  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
    > [!NOTE]
    >  Dans les fichiers **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs** et **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\ customerserviceport.asmx.cs**, remplacez toutes les instances de 17f20caea2afcc8c par a1054514fc67bded.  
  
2.  À l'invite de commandes Visual Studio, accédez au dossier %BTSSolutionsPath%\SO\BTSSoln, puis exécutez la commande suivante pour générer la version stub de la solution orientée services.  
  
    -   `SetupBTSSoln.bat`  
  
    > [!NOTE]
    >  Dans les fichiers répertoriés ci-dessous, remplacez toutes les instances de 17f20caea2afcc8c par le jeton de clé publique actuel.  
    >   
    >  -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs  
    > -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs  
    > -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs  
    > -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs  
    > -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs  
    > -   %BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs  
  
##  <a name="step9"></a>Créer les entrées de Enterprise Single Sign-On (SSO) et les valeurs dans la base de données SSO  
  
#### <a name="to-create-the-enterprise-single-sign-on-sso-entries-and-values-in-the-sso-database"></a>Pour créer les entrées et valeurs de l'authentification unique de l'entreprise (SSO) dans la base de données SSO  
  
1.  Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, puis exécutez les commandes suivantes pour définir l'environnement PATH pour le dossier Authentification unique de l'entreprise.  
  
    -   `Set PATH=%PATH%;%ProgramFiles%\"Common Files\Enterprise Single Sign-On"`  
  
2.  À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, ouvrez le fichier ConfigStoreApp.xml à l'aide du Bloc-notes, puis examinez le contenu du fichier.  
  
    > [!NOTE]
    >  Ce fichier définit l'application de magasin de configuration dans SSO que le scénario utilise pour stocker les paramètres de configuration. Voici quelques-uns des paramètres de configuration le **délai d’attente** valeur utilisée pour communiquer avec SAP (pour les trois versions). Il n'est pas nécessaire de modifier ce fichier.  
  
3.  À l'invite de commandes, exécutez la commande suivante pour créer l'application de magasin de configuration SSO.  
  
    -   `ssomanage -createapps ConfigStoreApp.xml`  
  
4.  À l'invite de commandes, ouvrez SetConfigValuesInSSO.cmd à l'aide du Bloc-notes, puis examinez le contenu du fichier.  
  
    > [!NOTE]
    >  Ce fichier de commandes définit les valeurs des paramètres de configuration dans la base de données SSO. Il contient plusieurs instructions Set qui définissent les valeurs dans les variables locales au début du fichier de commandes. Le **SAPAdapterTimeout**, **PendingTransactionsAdapterTimeout**, et **PaymentTrackingAdapterTimeout** valeurs sont utilisées dans la version stub et d’adaptateur. Les valeurs restantes sont utilisées dans la version Inline. Il n'est pas nécessaire de modifier ce fichier pour la version stub.  
  
5.  À l’invite de commandes, tapez `SetConfigValuesInSSO.cmd`, puis appuyez sur ENTRÉE pour stocker les valeurs dans l’application de magasin de configuration de l’authentification unique.  
  
6.  À l'invite de commandes, exécutez la commande suivante pour activer les tickets dans SSO :  
  
    -   `ssomanage -tickets yes yes`  
  
##  <a name="step11"></a>Déployer la définition BAM pour la Solution orientée services  
  
#### <a name="to-deploy-the-bam-definition-for-the-service-oriented-solution"></a>Pour déployer la définition BAM pour la solution orientée services  
  
1.  À l’invite de commandes, tapez la commande suivante et appuyez sur ENTRÉE. Cela permet de définir le chemin d'accès de l'utilitaire BAM :  
  
    -   SET PATH=%PATH%;%programfiles%\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\Tracking  
  
2.  À l’invite de commandes, accédez au répertoire du dossier %BTSSolutionsPath%\SO\BTSSoln\BAM et tapez la commande suivante, puis appuyez sur ENTRÉE :  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
        > [!NOTE]
        >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
##  <a name="step13"></a>Déployer la Solution orientée services  
  
#### <a name="to-deploy-the-service-oriented-solution"></a>Pour déployer la Solution orientée services  
  
1.  Ouvrez une invite de commandes, puis accédez au dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts.  
  
2.  Modifier la **DeployStubBinding.cmd** fichier en remplaçant toutes les instances de « debug » et « development » par « release ».  
  
3.  Ouvrez une invite de commandes, puis accédez au dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts. Tapez la commande suivante et appuyez sur ENTRÉE :  
  
    -   `DeployStubBinding.cmd`  
  
4.  À l'invite de commandes, exécutez la commande suivante pour démarrer les orchestrations de la version stub.  
  
    -   `Startstub.vbs`  
  
## <a name="next-steps"></a>Étapes suivantes  
 Tester le fonctionne de la version stub de la solution orientée services dans [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md)   
 [Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)   
 [Installation d’ordinateur de développeur pour le Service orienté solutions](../core/developer-machine-setup-for-the-service-oriented-solution.md)