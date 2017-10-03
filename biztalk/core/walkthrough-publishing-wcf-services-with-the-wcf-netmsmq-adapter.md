---
title: "Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e623b6dc-32e5-467c-bb7d-68b7a75723c1
caps.latest.revision: "46"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7c80859e83d915d835aa99b0456ca763ed267f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter"></a>Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-NetMsmq
  
> [!NOTE]
>  Pour plus d’informations à propos des adaptateurs, consultez [adaptateurs dans BizTalk Server](../core/adapters-in-biztalk-server.md).  
  
## <a name="introduction"></a>Introduction
  
 Dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], une orchestration peut être publiée en tant que service [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)]. Par l'intermédiaire d'un emplacement de réception BizTalk, une orchestration peut exposer un point de terminaison [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] qui lui permet d'être appelée par un client [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Le **Assistant Publication du Service WCF BizTalk** fournit un moyen simple pour exposer une orchestration comme emplacement de réception.  
  
 L’adaptateur WCF-NetMsmq utilise le **NetMsmqBinding** liaison pour prendre en charge à l’aide de Microsoft Message Queuing (également appelé MSMQ) comme son transport sous-jacent. Le client d'un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] envoie des messages [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à une file d'attente MSMQ à l'aide de l'emplacement de réception configuré pour utiliser l'adaptateur WCF-NetMSMQ. L'adaptateur récupère ces [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages dans la file d'attente MSMQ, les convertit au format [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les écrit dans la base de données MessageBox de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Cette procédure pas à pas illustre la manière dont une application console cliente [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] exploite l'adaptateur WCF-NetMsmq afin de communiquer avec un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], hébergé dans une application console .NET, via une file d'attente des messages MSMQ. Elle présente une méthode de publication de métadonnées pour un emplacement de réception à l'aide de l'Assistant Publication de services WCF BizTalk. Elle décrit également la configuration d'une application Web pour prendre en charge la publication des métadonnées.  
  
 Une fois cette procédure pas à pas terminée, vous saurez comment effectuer les tâches suivantes :  
  
-   Depuis [!INCLUDE[vs2010](../includes/vs2010-md.md)], utilisez le **déployer** commande pour déployer des assemblys BizTalk à une instance locale de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous créerez ainsi une application BizTalk contenant ces assemblys. Un assembly BizTalk contient des informations sur les ressources utilisées dans une solution BizTalk Server (par exemple, des orchestrations, des pipelines, des schémas et des mappages).  
  
-   À partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], configurez un emplacement de réception WCF-NetMsmq de manière à héberger le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publié.  
  
-   À partir de la **Assistant Publication du Service WCF BizTalk**, créer l’application Web pour publier des métadonnées pour l’emplacement de réception existant. Ces métadonnées sont exploitées par le client qui envoie des messages vers cet emplacement de réception.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cet exemple, assurez-vous que votre environnement est conforme à la configuration requise décrite ci-dessous :  
  
-   L’ordinateur qui génère les assemblys et exécute le processus de déploiement et l’ordinateur qui exécute l’exemple, requièrent Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]et Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
-   L'ordinateur utilisé pour générer les assemblys et exécuter le processus de déploiement requiert Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
-   L'ordinateur qui exécute l'exemple requiert les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et les outils d'administration de [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il s'agit d'options à installer lors de l'installation de Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
-   Sur les ordinateurs utilisés pour effectuer des tâches d'administration, vous devez exécuter un compte d'utilisateur membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer les paramètres d'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'intérieur de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce compte d'utilisateur doit également être membre du groupe Administrateurs local pour le déploiement d'application, la gestion d'instances de l'hôte et d'autres tâches éventuellement requises.  
  
-   Sur n’importe quel ordinateur qui nécessite [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fonctionnalité, effectuez la procédure d’installation unique pour le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] exemples [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
-   Sur l'ordinateur qui exécute l'exemple et importe une liaison ou un fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous que l'hôte n'est pas un hôte approuvé, sans quoi l'importation échoue.  
  
-   Vous devez télécharger le code de procédure pas à pas et l’extraire sur votre ordinateur. Cette procédure pas à pas est une partie de l’ensemble du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] package de la procédure pas à pas de carte. Vous pouvez télécharger le fichier **WCFAdapterWalkthroughs.exe** à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] centre de développement sur [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
## <a name="build-and-deploy-the-biztalk-solution-biztalkapp"></a>Générer et déployer la solution BizTalk, BizTalkApp  
  
1.  Extrayez WCFNetMsmqAdapterPublishing.exe à **C:\WCFNetMsmqAdapterPublishing**.  
  
2.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], ouvrez le **WCFNetMsmqAdapterPublishing.sln** fichier.  
  
3.  Dans l’Explorateur de solutions, développez **BizTalkApp**, puis ouvrez **OrderProcess.odx** pour passer en revue. L'exemple d'orchestration reçoit des messages de demande de commande et renvoie simplement des messages de réponse de commande.  
  
4.  Étant donné que la **BizTalkApp** assembly doit être installé dans le GAC, vous devez un fichier de clé de nom fort pour terminer le processus de déploiement. Cliquez sur le **BizTalkApp** de projet, puis cliquez sur **propriétés**. Sur le **propriétés** , cliquez sur **signature**, puis sélectionnez **signer l’assembly**. Cliquez sur la flèche vers le bas dans la **choisir un fichier de clé de nom fort** la liste déroulante, cliquez sur  **\<Nouveau >** et entrez `keyfile.snk` dans les **nom de fichier de clé** zone de texte. Décochez la case **protéger mon fichier de clé avec un mot de passe**, puis cliquez sur **OK**.  
  
5.  Cliquez sur le **déploiement** onglet, puis modifiez le **Server** propriété si vous utilisez un serveur de base de données différente pour la base de données de gestion BizTalk en plus de **LOCALHOST**.  Vérifiez **Application BizTalk** a la valeur **WCFNetMsmqAdapterPublishing**. Vérifiez **installer dans le Global Assembly Cache** a la valeur **True**.  
  
6.  Dans l’Explorateur de solutions, cliquez sur le **BizTalkApp** de projet, puis cliquez sur **reconstruire**.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, puis cliquez sur **déployer**.  
  
## <a name="configure-the-application"></a>Configurez l'application  
  
1.  Assurez-vous que le composant Microsoft Message Queuing (MSMQ) est installé sur votre ordinateur en procédant comme suit :  
  
    1.  Cliquez sur **Démarrer**, avec le bouton droit **ordinateur**, puis cliquez sur **gérer** pour ouvrir **le Gestionnaire de serveur**.  
  
    2.  Développez le **fonctionnalités** nœud.  Si **Message Queuing** est ne pas installé, cliquez sur **fonctionnalités**, puis sélectionnez **ajouter des fonctionnalités**. Vérifiez **Message Queuing**, cliquez sur **suivant**, puis cliquez sur **installer** pour installer MSMQ sur ce système.  
  
2.  Assurez-vous que le service Message Queuing est en cours d'exécution sur l'ordinateur destiné à être utilisé par l'adaptateur WCF-NetMsmq en procédant comme suit :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Services**.  
  
    2.  Dans **Services**, assurez-vous que le **état** de la **Message Queuing** service est **démarré**. Si le service n’est pas démarré, cliquez sur **Message Queuing**, puis cliquez sur **Démarrer**.  
  
3.  Créez la file d'attente cible que l'emplacement de réception utilise et à partir de laquelle l'adaptateur WCF-NetMsmq récupère les messages [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] entrants en provenance des clients.  
  
    1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **gestion de l’ordinateur**.  
  
    2.  Dans **gestion de l’ordinateur**, développez **Services et Applications**, développez **Message Queuing**, avec le bouton droit **files d’attente privées**, pointez sur **Nouveau**, puis cliquez sur **file d’attente privée**.  
  
    3.  Dans le **nouvelle file d’attente privée** boîte de dialogue, tapez `WCFNetMsmqAdapterPublishing` dans les **nom de la file d’attente** zone de texte, sélectionnez le **transactionnel** case à cocher, puis cliquez sur **OK** .  
  
4.  Créez un emplacement de réception WCF-NetMsmq pour l'exemple d'application en procédant comme suit :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
    2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez **Applications**, développez **WCFNetMsmqAdapterPublishing**, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
    3.  Dans le **propriétés du Port de réception** boîte de dialogue le **nom** zone de texte, tapez `WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder`, puis cliquez sur **OK**.  
  
    4.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder**, pointez sur **nouveau**, puis cliquez sur **un emplacement de réception**.  
  
    5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** zone de texte, tapez `WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder.NetMsmq`.  
  
    6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section ensuite **Type**, sélectionnez **WCF-NetMsmq** à partir de la liste déroulante, puis cliquez sur **configurer**.  
  
    7.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **général** sous l’onglet du **adresse (URI)** zone de texte, tapez `net.msmq://localhost/private/WCFNetMsmqAdapterPublishing`.  
  
    8.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **liaison** onglet, vérifiez que le **transactionnel** case à cocher est activée.  
  
        > [!NOTE]
        >  Étant donné que la file d'attente cible que vous avez créée est transactionnelle, vous devez activer cette case à cocher. Si elle ne l'est pas, l'emplacement de réception ne sera pas activé, car il y aura une différence entre les exigences transactionnelles de cet emplacement de réception et celles de la file d'attente MSMQ sous-jacente.  
  
    9. Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **sécurité** onglet, sélectionnez **aucun** à partir de la **mode de sécurité** liste déroulante .  
  
        > [!NOTE]
        >  Cette procédure pas à pas implique que MSMQ soit installé avec l'intégration [!INCLUDE[btsAD](../includes/btsad-md.md)] désactivée sur votre ordinateur. La valeur par défaut, **WindowsDomain**, pour le **mode d’authentification MSMQ** propriété n’est disponible lorsque [!INCLUDE[btsAD](../includes/btsad-md.md)] l’intégration est activée.  
  
    10. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
5.  Créez un port d'envoi FILE pour l'exemple d'application. Ce port permet d'acheminer la réponse du bon de commande via l'orchestration sous-jacente du service.  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFNetMsmqAdapterPublishing**, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
    2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** zone de texte, tapez `WCFNetMsmqAdapterPublishing.SendPurchaseOrder.File`.  
  
    3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **Transport** section à côté **Type**, sélectionnez **fichier** dans la liste déroulante, puis Cliquez sur **configurer**.  
  
    4.  Dans le **propriétés du Transport FILE** boîte de dialogue le **général** sous l’onglet du **dossier de Destination** zone de texte, tapez `C:\WCFNetMsmqAdapterPublishing\Out`, puis cliquez sur **OK** .  
  
    5.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
6.  Spécifiez le nom d'hôte et les liaisons pour l'exemple d'application comme suit :  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFNetMsmqAdapterPublishing**, développez **Orchestrations**, avec le bouton droit de l’exemple d’orchestration, cliquez sur **depropriétés**, cliquez sur **liaisons**et la valeur **hôte** à **BizTalkServerApplication** ou un autre hôte approprié.  
  
    2.  Dans le **propriétés d’Orchestration** boîte de dialogue, sélectionnez **WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder** à partir de la **Ports de réception** liste déroulante pour le  **PurchaseOrderRequestPort**.  
  
    3.  Dans le **propriétés d’Orchestration** boîte de dialogue, sélectionnez **WCFNetMsmqAdapterPublishing.SendPurchaseOrder.File** à partir de la **groupes de ports d’envoi d’envoi** liste déroulante pour le **PurchaseOrderResponsePort**.  
  
    4.  Dans le **propriétés d’Orchestration** boîte de dialogue, cliquez sur **OK** pour enregistrer la configuration.  
  
## <a name="publish-the-metadata-for-the-wcf-netmsmq-receive-location"></a>Publier les métadonnées pour l’emplacement de réception WCF-NetMsmq  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Publication du Service WCF BizTalk**.  
  
2.  Sur le **Bienvenue dans l’Assistant de publication des services WCF BizTalk** , cliquez sur **suivant**.  
  
3.  Sur le **Type de Service WCF** page, sélectionnez le **point de terminaison métadonnées uniquement (MEX)** case à cocher pour publier les métadonnées pour le WCFNetMsmq l’emplacement de réception. Sélectionnez **WCFNetMsmqAdapterPublishing.ReceivePurchaseOrder.NetMsmq** à partir de la **emplacement de réception de publier les métadonnées pour** liste déroulante, puis cliquez sur **suivant**.  
  
4.  Sur le **créer un Service WCF** page, sélectionnez **publier des orchestrations BizTalk en tant que service WCF**, puis cliquez sur **suivant**.  
  
5.  Sur le **BizTalk Assembly** page, dans le **fichier d’assembly BizTalk (\*.dll)** zone de texte, cliquez sur **Parcourir** pour accéder à la **C:\ WCFNetMsmqAdapterPublishing\BizTalkApp\bin\Development** dossier, double-cliquez sur l’assembly contenant l’exemple d’orchestration à publier, puis cliquez sur **suivant**.  
  
6.  Sur le **Orchestrations et Ports** , assurez-vous que le **Port : PurchaseOrderRequestPort** nœud est sélectionné dans la page, puis cliquez sur **suivant**.  
  
     Le point de terminaison MEX de l'emplacement de réception est publié et utilisé par le client afin d'envoyer des messages vers l'emplacement de réception.  
  
7.  Sur le **propriétés du Service WCF** page, dans le **espace de noms cible du service WCF** zone de texte, tapez l’URI que vous souhaitez que cette publication [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] de service pour l’utiliser, puis cliquez sur **suivant**. Pour cette procédure pas à pas, laissez l’URI, par défaut `http://tempuri.org/`.  
  
8.  Sur le **l’emplacement du Service WCF** page, procédez comme suit pour spécifier l’emplacement de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services à créer, puis cliquez sur **suivant**:  
  
    1.  Dans le **emplacement** zone de texte, tapez nom du répertoire Web où le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] de service s’exécute, ou cliquez sur **Parcourir** et sélectionnez un répertoire Web. Pour cette procédure pas à pas, conservez l’emplacement par défaut (http://localhost/*\<nom de l’Assembly BizTalk >*) dans le **emplacement** zone de texte.  
  
    2.  Sélectionnez le **autorise l’accès anonyme au service WCF** option. Cette option permet d'ajouter un accès anonyme au répertoire virtuel créé. Vous devez sélectionner cette option afin d'autoriser une authentification anonyme pour l'application Web que cet Assistant va créer.  
  
9. Sur le **récapitulatif du Service WCF** , cliquez sur **créer** pour créer le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
10. Sur le **fin Service Assistant Publication WCF BizTalk** , cliquez sur **Terminer**.  
  
## <a name="configure-the-web-application-hosting-the-published-metadata-service"></a>Configurer l’application Web hébergeant le service de métadonnées publié  
  
1.  Ouvrez une invite de commandes, accédez à la **C:\inetpub\wwwroot\Microsoft.Samples.BizTalk.WCF.NetMsmqPublishing.BizTalkApp** dossier où le **Assistant Publication du Service WCF BizTalk** créé le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]service. Ouvrez le **Web.config** fichier à l’aide du bloc-notes.  
  
2.  Dans le bloc-notes, ajoutez la ligne suivante à l’intérieur de la  **\<system.web >** élément :  
  
    ```  
    <trust level="Full" originUrl="" />  
    ```  
  
    > [!NOTE]
    >  Ce paramètre est facultatif. Il autorise l'accès de l'application ASP.NET hébergeant le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publié à n'importe quelle ressource exposée à la sécurité du système d'exploitation.  
  
3.  Testez le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publié à l'aide d'Internet Explorer en procédant comme suit :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
    2.  Dans le Gestionnaire des services Internet, créez un pool d'applications au sein duquel ce service sera exécuté qui dispose des autorisations d'accès à la base de données BizTalk appropriées. Avec le bouton droit **Pools d’applications**, cliquez sur **ajouter un Pool d’applications**, entrez un nom pour le pool d’applications, puis cliquez sur **OK**.  
  
    3.  Développez **Pools d’applications**, cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **paramètres avancés**. Sous **modèle de processus** section, entrez le compte a accès à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données sous le **identité** champ.  
  
    4.  Développez **Sites Web**, développez **Site Web par défaut**, puis développez l’application Web créés par l’Assistant de publication des services WCF BizTalk.  
  
    5.  Dans le Gestionnaire des services Internet, dans le volet central, cliquez sur **affichage du contenu** pour afficher les fichiers de l’application.  
  
    6.  Avec le bouton droit le **Microsoft_Samples_BizTalk_WCF_NetMsmqPublishing_BizTalkApp_OrderProcess_PurchaseOrderRequestPort.svc** service de fichiers qui le **Assistant Publication du Service WCF BizTalk** créé, puis cliquez sur **Parcourir**. S’ouvre Internet Explorer pour afficher le **BizTalkServerInstance Service** page indiquant qu’une instance de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service est en cours d’exécution. Cette page affiche une adresse WSDL complète, que vous pouvez copier et utiliser avec l'outil de métadonnées de service (svcutil.exe) ou dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], pour extraire un code proxy et un fichier de configuration utilisables pour créer une application cliente pour le service.  
  
    7.  Copier dans le Presse-papiers la ligne de commande avec l’adresse WSDL complète à partir de **BizTalkServerInstance Service** page Internet Explorer s’affiche à l’étape précédente.  
  
         **SvcUtil.exe http://localhost/Microsoft.Samples.BizTalk.WCF.NetMsmqPublishing.BizTalkApp/Microsoft_Samples_BizTalk_WCF_NetMsmqPublishing_BizTalkApp_OrderProcess_PurchaseOrderRequestPort.svc?wsdl**  
  
## <a name="build-the-client-application"></a>Générez l’application cliente  
  
1.  Ouvrir un [!INCLUDE[vs2010](../includes/vs2010-md.md)] invite de commandes en tant qu’administrateur et accédez à la **C:\WCFNetMsmqAdapterPublishing\WCFClient** dossier. Il s'agit de l'emplacement où vous allez placer la classe de proxy et le fichier de configuration de l'application.  
  
2.  Collez la ligne de commande svcutil.exe entière contenant l'adresse WSDL complète que vous avez copiée dans la procédure précédente, puis appuyez sur ENTRÉE. Cela crée la classe proxy, **BizTalkServiceInstance.cs**et le fichier de configuration d’application, **output.config**. Conservez la fenêtre de l'invite de commandes ouverte pour l'utiliser dans la dernière section.  
  
3.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], dans l’Explorateur de solutions, cliquez sur **WCFClient**, pointez sur **ajouter**, puis cliquez sur **élément existant**.  
  
4.  Dans le **ajouter un élément existant** boîte de dialogue, cliquez sur Parcourir pour le **WCFClient** dossier, sélectionnez **tous les fichiers (\*.\*)**  dans les **types de fichiers** la liste déroulante, sélectionnez le **BizTalkServiceInstance.cs** et **output.config** fichiers, puis cliquez sur  **Ajouter**.  
  
5.  Développez **WCFClient**, avec le bouton droit **output.config**, cliquez sur **renommer**, puis tapez `App.config` comme nouveau nom.  
  
6.  Double-cliquez sur **Program.cs** pour voir comment appeler publié [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service à l’aide de la classe proxy générée par svcutil.exe.  
  
7.  Développez **références**et assurez-vous que le **WCFClient** projet a **System.ServiceModel.dll** référencé.  
  
8.  Avec le bouton droit le **WCFClient** de projet et sélectionnez **Build**. Conservez [!INCLUDE[vs2010](../includes/vs2010-md.md)] ouvert et passez à la section suivante.  
  
## <a name="test-the-sample-solution-with-the-wcf-netmsmq-adapter"></a>Tester l’exemple de solution avec l’adaptateur WCF-NetMsmq  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **WCFNetMsmqAdapterPublishing** application, puis sur **Démarrer**. Dans le **Démarrer** boîte de dialogue, cliquez sur **Démarrer**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication** ou un autre approprié d’instance d’hôte, puis cliquez sur **redémarrer**. Si cette étape n'est pas obligatoire, il est conseillé de vérifier que l'exemple fonctionne correctement à ce stade.  
  
3.  Dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], dans le **déboguer** menu, cliquez sur **démarrer sans débogage** pour exécuter l’application WCFClient. Cela envoie un exemple de message vers l'emplacement de réception WCF-NetMsmq. Vous visualiserez le message sortant ci-dessous indiquant que le message a été envoyé.  
  
     **Emplacement de réception de l’appel de l’opération d’envoi WCF-NetMsmq**  
  
     **Appuyez sur n’importe quelle touche pour fermer l’application cliente WCF**  
  
4.  Appuyez sur n'importe quelle touche pour fermer l'application WCFClient.  
  
5.  Dans le [!INCLUDE[vs2010](../includes/vs2010-md.md)] invite de commandes, accédez à la **C:\WCFNetMsmqAdapterPublishing\Out** dossier, puis assurez-vous que le message de réponse que l’application WCFClient a renvoyé existe.  
  
6.  Double-cliquez sur le fichier {GUID} .xml pour l’ouvrir dans Internet Explorer et afficher la **OrderID** valeur traitée par le service.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer un WCF-NetMsmq emplacement de réception](../core/how-to-configure-a-wcf-netmsmq-receive-location.md)   
 [Procédures pas à pas l’adaptateur WCF](../core/wcf-adapter-walkthroughs.md)   
 [Publication des métadonnées de Service WCF pour les adaptateurs de réception](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)