---
title: 'Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tutorials, publishing
- WCF adapters, tutorials
- publishing, WCF services
- WCF-BasicHttp adapters, tutorials
- publishing, tutorials
- WCF services, publishing
- tutorials, WCF adapters
ms.assetid: 43b76215-9cb0-47ab-a085-c4cf265410f9
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca976d2e965d781de352a010bd4ef8c16e712ffb
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter"></a>Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp
## <a name="introduction"></a>Introduction  
 Cette procédure pas à pas consiste à publier un service [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] en tant qu'orchestration BizTalk à l'aide de l'Assistant Publication de services WCF BizTalk et de l'adaptateur WCF-BasicHttp. Une orchestration BizTalk s'affiche pour un client externe, tel qu'un autre service Web ou une application [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], en tant que service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] en exposant un point de terminaison [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à l'aide de l'adaptateur WCF-BasicHttp. L'adaptateur WCF-BasicHttp consiste en un adaptateur d'envoi et un adaptateur de réception. Dans cet exemple, vous allez utiliser uniquement le côté réception de cet adaptateur pour recevoir des demandes de service WCF en provenance d'applications clientes [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] via le protocole HTTP ou HTTPS.  
  
 L’adaptateur WCF-BasicHttp utilise le **BasicHttpBinding** liaison pour fournir une implémentation de pile de transport/protocole compatible avec la version initiale des services Web pour faire Office de pont entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]fonctionnalité. Il assure la communication avec des clients et services Web basés sur des fichiers ASMX conformes à WS-I Basic Profile 1.1, en utilisant le transport HTTP ou HTTPS avec codage de texte. Si vous utilisez l'adaptateur WCF-BasicHttp, vous ne pouvez pas tirer parti des fonctionnalités de communication Web avancées prises en charge par les protocoles WS-*. Pour ce faire, utilisez l'adaptateur WCF-WSHttp.  
  
 Cette procédure pas à pas montre comment créer un emplacement de réception WCF-BasicHttp pour publier une orchestration en tant que service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  Vous allez configurer les Services Internet (IIS) pour fournir un hébergement isolé de ce service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  Une application cliente appelle l'orchestration [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publiée pour montrer la manière dont un client externe peut appeler le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publié sur Internet pour utiliser ses fonctionnalités.  
  
 Une fois cette procédure pas à pas terminée, vous saurez comment effectuer les tâches suivantes :  
  
-   Depuis Visual Studio, utilisez le **déployer** commande pour déployer le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service sous la forme d’une orchestration BizTalk à l’intérieur d’un assembly BizTalk à une instance locale de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le déploiement à partir de Visual Studio crée une application BizTalk qui est renseignée avec les assemblys contenant des ressources telles que des orchestrations, des pipelines, des schémas et des mappages à utiliser dans la solution BizTalk.  
  
-   Une fois déployée, l'orchestration BizTalk est disponible pour la configuration et le contrôle via la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans cette procédure pas à pas, vous allez configurer l'emplacement de réception WCF-BasicHttp pour accepter les messages entrants envoyés au service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] que crée l'Assistant Publication de services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] de BizTalk. L'emplacement de réception est hébergé par l'hôte BizTalk isolé dans les services Internet (IIS). Il agit en tant que service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] pour obtenir les demandes entrantes.  
  
> [!NOTE]
>  Dans cette procédure pas à pas, vous allez utiliser l'Assistant Publication de services WCF BizTalk et/ou l'Assistant Publication de services Web BizTalk pour publier des orchestrations et des schémas BizTalk en tant que services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] avec les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Pour publier des orchestrations et des schémas en tant que services Web avec l’adaptateur SOAP, vous utilisez la **Assistant de publication WCF BizTalk** et/ou **Assistant Publication des Services Web BizTalk**.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter la procédure décrite dans cet exemple, assurez-vous que votre environnement est conforme à la configuration requise décrite ci-dessous :  
  
-   L’ordinateur qui génère les assemblys et exécute le processus de déploiement et de l’ordinateur qui exécute l’exemple, requièrent Microsoft Windows Server 2008 SP2 ou Windows Server 2008 R2, Microsoft .NET Framework 4 et Microsoft BizTalk Server.  
  
-   L’ordinateur utilisé pour générer les assemblys et exécuter le processus de déploiement requiert Microsoft Visual Studio.  
  
-   L'ordinateur qui exécute l'exemple requiert les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et les outils d'administration de [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il s’agit des options d’installation lors de l’installation de Microsoft BizTalk Server.  
  
-   Sur les ordinateurs utilisés pour effectuer des tâches d'administration, vous devez exécuter un compte d'utilisateur membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer les paramètres d'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'intérieur de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce compte d'utilisateur doit également être membre du groupe Administrateurs local pour le déploiement d'application, la gestion d'instances de l'hôte et d'autres tâches éventuellement requises.  
  
-   Sur n’importe quel ordinateur qui nécessite [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fonctionnalité, effectuez la procédure d’installation unique pour le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] exemples [ http://go.microsoft.com/fwlink/?LinkId=135510 ](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
-   Sur l'ordinateur qui exécute l'exemple et importe une liaison ou un fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous que l'hôte n'est pas un hôte approuvé, sans quoi l'importation échoue.  
  
-   Vous devez télécharger le code de procédure pas à pas et l’extraire sur votre ordinateur. Cette procédure pas à pas est une partie de l’ensemble du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] package de la procédure pas à pas de carte. Vous pouvez télécharger le fichier **WCFAdapterWalkthroughs.exe** à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] centre de développement sur [ http://go.microsoft.com/fwlink/?LinkId=194140 ](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
### <a name="to-deploy-the-sample-biztalk-solution-biztalkapp"></a>Pour déployer l'exemple de solution BizTalk (BizTalkApp)  
  
1.  Exécutez le fichier auto-extractible **WCFBasicHttpReceiveAdapter.exe** de fichiers et d’extraire les fichiers dans le **C:\WCFBasicHttpReceiveAdapter** dossier.  
  
2.  Dans Microsoft Visual Studio, ouvrez le **C:\WCFBasicHttpReceiveAdapter\WCFBasicHttpReceiveAdapter.sln** fichier.  
  
3.  Le **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** assembly contient un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration, une carte et deux schémas. Il doit être installé dans le GAC et sera peut-être une clé de nom fort de fichiers pour ce faire. Cliquez sur le **BizTalkApp** de projet, puis cliquez sur **propriétés**. Sur le **propriétés** , cliquez sur **signature**, puis sélectionnez **signer l’assembly**. Cliquez sur la flèche vers le bas dans la **choisir un fichier de clé de nom fort** la liste déroulante, cliquez sur  **\<nouveau\>**et entrez `keyfile.snk` dans le **le nom de fichier de clé**zone de texte. Décochez la case **protéger mon fichier de clé avec un mot de passe**, puis cliquez sur **OK**.  
  
4.  Dans l’Explorateur de solutions, cliquez sur le **BizTalkApp** de projet, puis cliquez sur **reconstruire**.  
  
    > [!NOTE]
    >  N’essayez pas une **générer la Solution**, ou pour créer le **WCFClient** application à ce stade. Le **WCFClient** n’est pas prêt à être générée à ce stade dans l’exemple.  
  
5.  Développez **BizTalkApp**, puis ouvrez **DeliveryProcess.odx** pour passer en revue. L'orchestration prend une demande [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] sur HTTP en utilisant l'adaptateur WCF-BasicHttp. Il modifie la demande à l'aide d'un mappage de transformation, puis renvoie la réponse en utilisant le même adaptateur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
    1.  Cette orchestration dispose d'un port requête-réponse logique qui sera publié avec l'adaptateur WCF-BasicHttp. Il sera lié à un port physique ultérieurement.  
  
    2.  Cliquez sur le nœud supérieur de **DeliveryProcess.odx** dans la fenêtre du concepteur, puis sélectionnez **propriétés**. Assurez-vous que le **modificateur de Type** propriété du type de port est **Public**.  
  
6.  Dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, puis cliquez sur **propriétés**.  
  
    1.  Si la base de données de gestion BizTalk n’est pas hébergé localement, modifiez le **Server** propriété si vous utilisez un serveur de base de données différente. Cliquez sur le **déploiement** onglet et modifiez le **Server** propriété pour pointer vers le serveur de base de données.  
  
    2.  Assurez-vous que le **nom de l’Application** est définie sur **WCFBasicHttpReceiveAdapter**. Il s'agit du nom de l'application BizTalk où la solution BizTalk sera déployée.  
  
    3.  Dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, puis cliquez sur **déployer**. Si vous ne déployez pas localement, vous devez peut-être configurer SQL Server pour autoriser les connexions à distance. Pour plus d’informations, consultez [ http://go.microsoft.com/fwlink/?LinkId=194141 ](http://go.microsoft.com/fwlink/?LinkId=194141).  
  
### <a name="to-publish-the-sample-orchestration-by-using-the-biztalk-wcf-service-publishing-wizard"></a>Pour publier l'exemple d'orchestration à l'aide de l'Assistant Publication de services WCF BizTalk  
  
1.  Au cours de cette étape, vous allez prendre l'assembly d'orchestration qui vient d'être déployé et le publier en tant que service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Pour ce faire, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Assistant Publication du Service WCF BizTalk** .  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des services WCF BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **Type de Service WCF** page, procédez comme suit pour spécifier le type de [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service à publier et les points de terminaison BizTalk pour la réception [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages, puis cliquez sur **suivant**:  
  
    1.  Sélectionnez le **point de terminaison de Service** option, qui stipule que vous allez publier une [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service à partir d’une orchestration dans un assembly. Sélectionnez **WCF-BasicHttp** à partir de la **nom de l’adaptateur (type de Transport)** liste déroulante.  
  
    2.  Sélectionnez le **activer le point de terminaison de métadonnées** case à cocher pour rendre le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] emplacement de réception hébergé par IIS publier son [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] des métadonnées de service. Sélectionner cette case à cocher définit le **httpGetEnabled** attribut de la \< **serviceMetadata** \> élément `true` dans le fichier Web.Config. Ces métadonnées sont récupérées lors de la demande une requête HTTP/GET. Plus tard, vous utiliserez l'outil SvcUtil.exe pour obtenir ces données afin de générer une classe de proxy que le code client utilisera pour appeler le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
    3.  Sélectionnez le **BizTalk de créer des emplacements de réception dans l’application suivante** option permettant de créer les ports de réception et emplacements correspondant à chaque fichier .svc généré pour l’adaptateur WCF-BasicHttp. Choisissez le nom de l’application BizTalk **WCFBasicHttpReceiveAdapter**, où les ports de réception et les emplacements sera générés, puis cliquez sur **suivant**.  
  
         L'Assistant crée un fichier de liaison, Binding.XML, pour représenter les emplacements de réception associés. Ce fichier se trouve dans le répertoire Web. Ultérieurement, vous pourrez l'importer manuellement via la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
        > [!NOTE]
        >  Si vous ne sélectionnez pas ici d'application BizTalk déployée, l'application par défaut est sélectionnée.  
  
4.  Sur le **créer un Service WCF** page, sélectionnez **publier des orchestrations BizTalk en tant que service WCF**, puis cliquez sur **suivant**. Cette opération publie l'orchestration spécifiée dans l'étape suivante en tant que service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
5.  Sélectionnez l'assembly contenant l'orchestration à publier. Sur le **BizTalk Assembly** page, dans le **fichier d’assembly BizTalk (\*.dll)** zone de texte, cliquez sur **Parcourir** pour accéder à la **C:\ WCFBasicHttpReceiveAdapter\BizTalkApp\bin\Development** dossier, double-cliquez sur le **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp** assembly contenant l’exemple l’orchestration à publier, cliquez sur **ouvrir**, puis cliquez sur **suivant**.  
  
6.  Sur le **Orchestrations et Ports** , assurez-vous que le **Port : DeliveryRequestPort** nœud est sélectionné dans la page, puis cliquez sur **suivant**. La sélection de ce nœud signifie que les nœuds de niveau supérieur correspondants sont également sélectionnés. Le port sera publié avec un emplacement de réception de requête-réponse hébergeant l'adaptateur WCF-BasicHttp.  
  
7.  Sur le **propriétés du Service WCF** page, dans le **cible** espace de noms de la **service WCF** zone de texte, tapez l’URI que vous souhaitez que cette publication [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service à utiliser, et puis cliquez sur **suivant**. Pour cette procédure pas à pas, laissez l’URI, par défaut «**http://tempuri.org/»** dans l’espace de noms cible du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] zone de texte de service.  
  
8.  Sur le **l’emplacement du Service WCF** page, procédez comme suit pour spécifier l’emplacement de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services à créer, puis cliquez sur **suivant**:  
  
    1.  Dans le **emplacement** zone de texte, tapez nom du répertoire Web où le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] de service s’exécute, ou cliquez sur **Parcourir** et sélectionnez le répertoire Web. Pour cette procédure pas à pas, car le nom de l’assembly est le même que le répertoire virtuel, conservez l’emplacement par défaut (**http://localhost/Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp**) dans le **emplacement** zone de texte.  
  
    2.  Sélectionnez le **autorise l’accès anonyme au service WCF** option, puis cliquez sur **suivant**. Cette option autorise un accès anonyme au répertoire virtuel créé. Comme cette procédure pas à pas utilise le mode de sécurité Transport sans authentification, vous devez sélectionner cette option afin d'autoriser une authentification anonyme pour l'application Web que cet Assistant va créer.  
  
9. Sur le **récapitulatif du Service WCF** , cliquez sur **créer** pour créer le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Cet étape crée pour l'orchestration spécifiée un port de réception disponible via le répertoire Web spécifié.  
  
10. Sur le **fin Service Assistant Publication WCF BizTalk** , cliquez sur **Terminer**.  
  
### <a name="to-enable-the-sample-biztalk-application"></a>Pour activer l'exemple d'application BizTalk  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Applications**, développez **WCFBasicHttpReceiveAdapter**, développez **Orchestrations**, avec le bouton droit de la  **DeliveryProcess** orchestration, cliquez sur **propriétés**, puis configurez les informations de liaison comme suit :  
  
    1.  Dans le **propriétés d’Orchestration** boîte de dialogue, cliquez sur **liaisons**, puis définissez **hôte** à **BizTalkServerApplication**.  
  
    2.  Dans le **propriétés d’Orchestration** boîte de dialogue, sélectionnez un port de réception le **DeliveryRequestPort** à lier. Pour cette procédure pas à pas, sélectionnez la réception du port qui BizTalk [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] Assistant Publication de services créé dans la procédure précédente, puis cliquez sur **OK**.  
  
3.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **WCFBasicHttpReceiveAdapter**, cliquez sur **Démarrer**, puis cliquez sur **Démarrer** dans le **Démarrer Application** boîte de dialogue.  
  
### <a name="to-configure-the-web-application-hosting-the-published-wcf-service"></a>Pour configurer l'application Web hébergeant le service WCF publié  
  
1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Internet Information Services (IIS) 7.0 Manager**.  
  
2.  Dans le Gestionnaire IIS, développez **Sites**, développez **Site Web par défaut**, puis développez l’application Web **Microsoft.Samples.BizTalk.WCFBasicHttpReceiveAdapter.BizTalkApp**qui le **Assistant Publication du Service WCF BizTalk** créé.  
  
3.  Créer un pool d'applications dans lequel ce service s'exécutera. Avec le bouton droit **Pools d’applications**, cliquez sur **ajouter un Pool d’applications**, entrez un nom pour le pool d’applications, puis cliquez sur **OK**.  
  
4.  Développez **Pools d’applications**, cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **paramètres avancés**. Sous **modèle de processus** section, entrez le compte a accès à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données sous le **identité** champ.  
  
5.  Dans le Gestionnaire des services Internet, cliquez sur **affichage du contenu**.  Dans le volet droit, cliquez sur le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fichier .svc du service qui le **Assistant Publication du Service WCF BizTalk** créé, puis cliquez sur **Parcourir**. Cette action ouvre Internet Explorer qui affiche une page indiquant que vous avez correctement créé un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] opérationnel. Cette page inclut également une adresse WSDL complète, que vous pouvez copier et utiliser avec l'outil de métadonnées de service (svcutil.exe) pour extraire un code proxy et un fichier de configuration utilisables pour créer une application cliente pour le service.  
  
6.  Copiez dans le Presse-papiers la ligne de commande SvcUtil.exe avec l'adresse WSDL complète de la page affichée par Internet Explorer à l'étape précédente.  
  
### <a name="to-create-the-proxy-class-for-the-sample-wcf-client-application-wcfclient"></a>Pour créer la classe de proxy pour l'exemple d'application cliente WCF, WCFClient  
  
1.  Créez une classe de proxy pour permettre à l'exemple d'application cliente [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] d'appeler le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Bien qu'un proxy ne soit pas obligatoire, l'écriture manuelle du code est très complexe. Il est donc recommandé de créer un proxy. Ouvrir un **invite de commandes Visual Studio** et accédez à la **C:\WCFBasicHttpReceiveAdapter\WCFClient** dossier dans lequel vous placerez le fichier de configuration des applications et de la classe proxy.  
  
2.  Coller le **svcutil.exe** ligne de commande avec l’adresse WSDL complète que vous avez copié dans la procédure précédente, puis appuyez sur **entrée** pour créer le fichier de configuration des applications et de la classe proxy. Cette ligne de commande crée **BizTalkServiceInstance.cs** pour la classe de proxy et **output.config** pour le fichier de configuration d’application.  
  
3.  Dans Visual Studio, dans l’Explorateur de solutions, cliquez sur **WCFClient**, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
4.  Dans le **ajouter un élément existant** boîte de dialogue, cliquez sur Parcourir pour le **WCFClient** dossier, sélectionnez **tous les fichiers (\*.\*)**  dans les **types de fichiers** la liste déroulante, sélectionnez le **BizTalkServiceInstance.cs** et **output.config** fichiers, puis cliquez sur  **Ajouter**.  
  
5.  Pour le **WCFClient** de projet, développez **références**et assurez-vous que le **WCFClient** projet a **System.ServiceModel** en tant que une de ses références.  
  
6.  Développez le **WCFClient** de projet, cliquez sur **output.config**, cliquez sur **renommer**, puis tapez **App.config** pour le nouveau nom.  
  
7.  Double-cliquez sur **Program.cs** pour voir comment appeler publié [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service à l’aide de la classe proxy générée par **Svcutil.exe**. Les appels pour instancier et appeler un [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service semble être appels locaux dans la simplicité du codage à l’aide de la **Microsoft_Samples_BizTalk_WCFBasicHttpReceiveAdapter_BizTalkApp_DeliveryProcess_DeliveryRequestPortClient** classe. Aucun code supplémentaire n'est nécessaire pour appeler un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] distant.  
  
8.  Dans Visual Studio, sur le **déboguer** menu, cliquez sur **démarrer sans débogage** pour exécuter WCFClient. Le code client crée un message DeliveryItem et appelle le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] en transmettant les valeurs Address, ProductID et Amount.  
  
    ```  
    DeliveryItem deliveryRequestItem = new DeliveryItem();  
    deliveryRequestItem.Address = "One Microsoft Way";  
    deliveryRequestItem.ProductID = "00A120c";  
    deliveryRequestItem.Amount = "300";  
    DeliveryRequestPortClient deliveryProcessClient = new DeliveryRequestPortClient("BasicHttpBinding_ITwoWayAsync");  
    DeliveryItem1 deliveryConfirmation = deliveryProcessClient.Submit(deliveryRequestItem);  
    ```  
  
     Si le client reçoit correctement le message de réponse du service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publié, il indique le numéro de confirmation de remise (concaténation des valeurs de ProductID et Address) dans le message de réponse.  
  
     **Opération d’envoi appelée avec deliveryRequestItem**  
  
     **Numéro de confirmation de remise renvoyé : 00A120c300One Microsoft Way**  
  
     **Appuyez sur n’importe quelle touche pour continuer...**  
  
## <a name="see-also"></a>Voir aussi  
 [Comment utiliser l’Assistant Publication de services WCF BizTalk pour publier des Orchestrations en tant que Services WCF](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)