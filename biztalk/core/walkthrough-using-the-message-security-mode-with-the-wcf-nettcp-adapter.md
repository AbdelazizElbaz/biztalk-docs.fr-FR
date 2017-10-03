---
title: "Procédure pas à pas : À l’aide du Mode de sécurité de Message avec l’adaptateur WCF-NetTcp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f6e892-34ce-4132-8867-54cc3bbfe507
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68fc5e0a90fdfcaa6c3b6e5f6ae280d320be5647
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-using-the-message-security-mode-with-the-wcf-nettcp-adapter"></a>Procédure pas à pas : À l’aide du Mode de sécurité de Message avec l’adaptateur WCF-NetTcp
  
> [!NOTE]
>  Pour plus d’informations à propos des adaptateurs, consultez [adaptateurs dans BizTalk Server](../core/adapters-in-biztalk-server.md).  
  
## <a name="introduction"></a>Introduction
  
 Cette procédure pas à pas détaille la configuration de l'adaptateur WCF-NetTcp pour l'utilisation du mode de sécurité Message [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)], qui utilise la spécification WS-Security pour sécuriser les messages que transmet l'adaptateur. Cette spécification présente les améliorations apportées au protocole de messagerie SOAP pour assurer la confidentialité, l'intégrité et l'authentification au niveau des messages SOAP. Le mode de sécurité Message nécessite que le certificat de service soit spécifié pour des opérations telles que le chiffrement/déchiffrement et la signature/vérification en fonction des combinaisons de modes de sécurité.  
  
 L’adaptateur WCF-NetTcp utilise la liaison NetTcpBinding pour communiquer entre [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] les clients et [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services à distance. Il fournit un accès total aux fonctionnalités de sécurité, de fiabilité et de transaction SOAP. Il permet la publication d'orchestrations et de schémas en tant que services [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], et offre à une orchestration la possibilité d'utiliser des services WCF externes. Cet adaptateur utilise le transport TCP et les messages ont un codage binaire. L'adaptateur WCF-NetTcp consiste en un adaptateur d'envoi et un adaptateur de réception.  
  
 Cette procédure pas à pas détaille la création de certificats pour le mode de sécurité Message à l'aide du service de certificats Active Directory. Vous allez créer des certificats pour le client et le serveur, puis configurer un emplacement de réception WCF-NetTcp pour utiliser ces certificats dans le mode de sécurité Message. À l'aide d'un client [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], vous enverrez à cet emplacement de réception des messages à l'état chiffré selon le traitement et la syntaxe du chiffrement XML.  
  
 Une fois cette procédure pas à pas terminée, vous saurez comment effectuer les tâches suivantes :  
  
-   utiliser le service de certificats Active Directory pour créer une demande de certificat et terminer le processus par l'émission du certificat ;  
  
-   configurer l'adaptateur WCF-NetTcp à partir de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour utiliser le mode de sécurité Message.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter la procédure décrite dans cet exemple, assurez-vous que votre environnement installe les composants requis suivants :  
  
-   L’ordinateur qui génère les assemblys et exécute le processus de déploiement et l’ordinateur qui exécute l’exemple, requièrent Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]et Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
-   L'ordinateur utilisé pour générer les assemblys et exécuter le processus de déploiement requiert Microsoft [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
-   L'ordinateur qui exécute l'exemple requiert les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et les outils d'administration de [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il s'agit d'options à installer lors de l'installation de Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
-   Sur les ordinateurs utilisés pour effectuer des tâches d'administration, vous devez exécuter un compte d'utilisateur membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer les paramètres d'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'intérieur de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce compte d'utilisateur doit également être membre du groupe Administrateurs local pour le déploiement d'application, la gestion d'instances de l'hôte et d'autres tâches éventuellement requises.  
  
-   Sur n’importe quel ordinateur qui nécessite [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fonctionnalité, effectuez la procédure d’installation unique pour le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] exemples [http://go.microsoft.com/fwlink/?LinkId=135510](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
-   Sur l'ordinateur qui exécute l'exemple et importe une liaison ou un fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous que l'hôte n'est pas un hôte approuvé, sans quoi l'importation échoue.  
  
-   Sur l'ordinateur qui exécute l'exemple, assurez-vous que les services de certificats Active Directory sont installés.  
  
-   Vous devez télécharger le code de procédure pas à pas et l’extraire sur votre ordinateur.  Cette procédure pas à pas est une partie de l’ensemble du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] package de la procédure pas à pas de carte. Vous pouvez télécharger le fichier **WCFAdapterWalkthroughs.exe** à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] centre de développement sur [http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
## <a name="create-the-certificates-for-this-walkthrough"></a>Créer les certificats pour cette procédure pas à pas  
  
1.  Dans cette section, vous allez effectuer des demandes de certificats pour le service et le client, émettre ces certificats et les installer dans les magasins appropriés. Les services de certificats Active Directory permettent de créer un certificat contenant une chaîne de certificats approuvée. Si vous n'avez pas installé les services de certificats Active Directory dans le cadre de la configuration requise, installez-les maintenant sur votre ordinateur. S'ils sont déjà installés, passez à l'étape 2.  
  
    1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **le Gestionnaire de serveur**.  
  
    2.  Sous le **le Gestionnaire de serveur** nœud, cliquez sur **ajouter**, puis cliquez sur **rôles**.  
  
    3.  Ceci fait apparaître la **avant de commencer** boîte de dialogue pour le **Assistant Ajout de rôles**. Cliquez sur **Suivant**.  
  
    4.  Sur le **sélectionner des rôles de serveur** , sélectionnez **Active Directory Certificate Services**, cliquez sur **suivant**, puis suivez l’à l’écran des instructions pour terminer le installation.  
  
2.  Créez une demande de certificat pour l'authentification du service comme suit :  
  
    1.  Dans Internet Explorer, visitez le site Web `http://localhost/certsrv`. Sur le **Bienvenue** , cliquez sur **demander un certificat**, puis cliquez sur **demande de certificat avancée** sur la **demander un certificat** page.  
  
        > [!NOTE]
        >  Lorsque vous utilisez [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] en tant que l’autorité de certification et de la demande d’une demande de certificat à partir d’un [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateur, vous risquez d’obtenir l’erreur **« afin de terminer l’inscription de certificats, le site Web de l’autorité de certification doit être configuré pour utiliser le protocole HTTPS l’authentification »**. Si cette erreur se produit, le site Web d'inscription doit être configuré à l'aide d'un certificat Web (SSL). Pour plus d'informations sur l'accomplissement de cette tâche, consultez les liens suivants :  
        >   
        >  [Les services AD CS : Inscription par le Web](http://technet.microsoft.com/library/cc732517.aspx)  
        >   
        >  [Instructions d’Installation du certificat serveur IIS](http://msdn.microsoft.com/library/ms751408.aspx)  
  
    2.  Sur le **demande de certificat avancée** , cliquez sur **créer et soumettre une demande à cette autorité de certification**.  
  
    3.  Sur le **demande de certificat avancée** , tapez `localhost` dans les **nom** zone de texte, sélectionnez **certificat d’authentification serveur** à partir de la  **Type de certificat nécessaire** liste déroulante, puis cliquez sur **Submit**.  
  
3.  Créez une demande de certificat pour l'authentification du client comme suit :  
  
    1.  Dans Internet Explorer, visitez le site Web `http://localhost/certsrv`. Sur le **Bienvenue** , cliquez sur **demander un certificat**, puis cliquez sur **demande de certificat avancée** sur la **demander un certificat** page.  
  
    2.  Sur le **demande de certificat avancée** , cliquez sur **créer et soumettre une demande à cette autorité de certification**.  
  
    3.  Sur le **demande de certificat avancée** , tapez `contoso` dans les **nom** zone de texte, sélectionnez **certificat d’authentification Client** à partir de la  **Type de certificat nécessaire** liste déroulante, puis cliquez sur **Submit**.  
  
    > [!NOTE]
    >  Le certificat d'authentification client est utilisé si vous exécutez [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur un ordinateur distinct du contrôleur de domaine. La configuration s'effectue dans la boîte de dialogue des propriétés de l'adaptateur.  
  
4.  Émettez les certificats à l'aide de la console de gestion d’autorité de certification comme suit :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **autorité de Certification**.  
  
    2.  Dans le **autorité de Certification** console d’administration, développez le nom de votre autorité de certification, puis double-cliquez sur **demande en attente**.  
  
    3.  Dans le volet droit de la **autorité de Certification** console de gestion, cliquez sur la demande pour le certificat d’authentification de service, pointez sur **toutes les tâches**, puis cliquez sur **problème** .  
  
    4.  Dans le volet droit de la **autorité de Certification** console de gestion, avec le bouton droit de la demande de certificat d’authentification client, pointez sur **toutes les tâches**, puis cliquez sur **problème** .  
  
    5.  Fermer le **autorité de Certification** console de gestion.  
  
5.  Installez les certificats émis sur votre ordinateur comme suit :  
  
    1.  Dans Internet Explorer, visitez le site Web `http://localhost/certsrv`.  
  
    2.  Sur le **Bienvenue** , cliquez sur **afficher l’état d’une demande de certificat en attente**.  
  
    3.  Sur le **afficher l’état d’une demande de certificat en attente** , cliquez sur le certificat d’authentification serveur.  
  
    4.  Sur le **délivré** , cliquez sur **installer ce certificat**.  
  
    5.  Dans Internet Explorer, visitez le site Web `http://localhost/certsrv`.  
  
    6.  Sur le **Bienvenue** , cliquez sur **afficher l’état d’une demande de certificat en attente**.  
  
    7.  Sur le **afficher l’état d’une demande de certificat en attente** , cliquez sur le certificat d’authentification client.  
  
    8.  Sur le **délivré** , cliquez sur **installer ce certificat**.  
  
6.  Assurez-vous que les certificats émis sont correctement installés comme suit :  
  
    1.  Ouvrez Microsoft Management Console (MMC). Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, type `mmc`, puis cliquez sur **OK**.  
  
    2.  Dans la console MMC, sur le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.  
  
    3.  Dans la boîte de dialogue **Ajouter/Supprimer un composant logiciel enfichable** , cliquez sur **Ajouter**.  
  
    4.  Dans le **ajouter Standalone Snap-in** boîte de dialogue, sélectionnez **certificats** à partir de la **le composant logiciel enfichable autonome disponible** liste, puis cliquez sur **ajouter**.  
  
    5.  Dans le **enfichable Certificats** boîte de dialogue, sélectionnez le **mon compte d’utilisateur** option, puis cliquez sur **Terminer**.  
  
    6.  Fermez toutes les boîtes de dialogue ouvertes.  
  
    7.  Dans la console MMC, dans la fenêtre racine de la Console, développez **certificats - utilisateur actuel**, développez **personnel**, développez **certificats**et vérifiez que les certificats que vous avez installé à l’étape précédente sont affichés.  
  
## <a name="create-the-biztalk-application-for-this-walkthrough"></a>Créer l’application BizTalk pour cette procédure pas à pas  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, avec le bouton droit **Applications**, pointez sur **nouveau**, puis cliquez sur **Application** .  
  
3.  Dans le **propriétés de l’Application** boîte de dialogue le **général** , tapez `WcfMessageSecurity`, puis cliquez sur **OK**.  
  
4.  Créez un emplacement de réception à l'aide de l'adaptateur WCF-NetTcp pour l'application BizTalk comme suit :  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WcfMessageSecurity**, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel Port de réception.**  
  
    2.  Dans le **propriétés du Port de réception** boîte de dialogue le **nom** zone de texte, tapez `WcfMessageSecurity.OrderRequest.Receive`, puis cliquez sur **OK**. Le nom de ce port de réception est totalement arbitraire, mais il possède une signification logique.  
  
    3.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **emplacements de réception**, cliquez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**. Le client [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] envoie un message [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] à cet emplacement de réception. Sélectionnez le **WcfMessageSecurity.OrderRequest.Receive** port de réception, puis cliquez sur **OK**.  
  
    4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** zone de texte, tapez `WcfMessageSecurity.OrderRequest.Receive.NetTcp`. Le nom de cet emplacement de réception est totalement arbitraire, mais il possède une signification logique.  
  
    5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section à côté **Type**, sélectionnez **WCF-NetTcp** dans la liste déroulante. liste, puis cliquez sur **configurer**.  
  
    6.  Dans le **propriétés du Transport WCF-NetTcp** boîte de dialogue le **général** sous l’onglet du **adresse (URI)** zone de texte, tapez `net.tcp://localhost/WcfMessageSecurity`.  
  
    7.  Dans le **propriétés du Transport WCF-NetTcp** boîte de dialogue le **sécurité** onglet, sélectionnez **Message** à partir de la **mode de sécurité** liste déroulante liste, puis sélectionnez **certificat** à partir de la **type d’informations d’identification de client de Message** liste déroulante. Cela a pour effet de configurer l'adaptateur WCF-NetTcp de manière à utiliser le mode de sécurité Message.  
  
    8.  Configurez le certificat de service à utiliser avec le mode de sécurité Message. Dans le **propriétés du Transport WCF-NetTcp** boîte de dialogue le **certification du Service** , cliquez sur **Parcourir**. Dans le **certificat de service Select** boîte de dialogue, sélectionnez le certificat d’authentification serveur installé dans la procédure précédente, puis cliquez sur **OK** pour fermer la boîte de dialogue et enregistrer les modifications.  
  
    9. Fermez toutes les boîtes de dialogue ouvertes.  
  
        > [!NOTE]
        >  Pour authentifier les certificats clients à l'aide des adaptateurs de réception [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], la chaîne de certificat de l'autorité de certification des certificats clients doit être installée dans le magasin de certificats Autorités de certification racine approuvées de l'ordinateur exécutant les instances d'hôte des adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Étant donné que cette procédure pas à pas suppose que le service de certificat soit installé sur le même ordinateur que le client [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], il est inutile d'installer la chaîne de certificats de l'autorité de certification sur votre ordinateur.  
  
5.  Créez un port d'envoi FILE pour l'application BizTalk. Il s'agit de l'emplacement où le message sortant de la demande de commande est envoyé par l'orchestration représentant le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WcfMessageSecurity**, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi unidirectionnel.**  
  
    2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **général** sous l’onglet du **nom** zone de texte, tapez `WcfMessageSecurity.OrderRequest.Send.FILE`.  
  
    3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **Transport** section à côté **Type**, sélectionnez **fichier** dans la liste déroulante, puis Cliquez sur **configurer**.  
  
    4.  Dans le **propriétés du Transport FILE** boîte de dialogue le **général** , tapez `C:\WCFMessageSecurity\OrderRequestOut` dans les **dossier de Destination** zone de texte, puis cliquez sur **OK** .  
  
    5.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **filtres** onglet, sélectionnez **BTS. ReceivePortName** pour le **propriété** , entrez `WcfMessageSecurity.OrderRequest.Receive` pour le **valeur** champ, puis cliquez sur **OK**. Cette expression de filtre route entrant [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] des messages du client dans le **WcfMessageSecurity.OrderRequest.Receive** port de réception pour ce port d’envoi.  
  
## <a name="test-the-wcf-client-against-the-biztalk-application"></a>Tester le client WCF par rapport à l’application BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **WcfMessageSecurity**, puis cliquez sur **Démarrer**. Dans le **Démarrer** boîte de dialogue, cliquez sur **Démarrer**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication** ou un autre approprié d’instance d’hôte, puis cliquez sur **redémarrer**.  
  
3.  Créez un dossier nommé **C:\WCFMessageSecurity** pour le dossier de travail pour cette procédure pas à pas. Extrayez les fichiers de la procédure pas à pas dans ce dossier.  
  
4.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **WcfMessageSecurity.sln** de fichiers dans le **C:\WCFMessageSecurity** dossier.  
  
5.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, développez **WcfClient**, puis ouvrez **Program.cs** pour passer en revue.  
  
    -   Le client envoie un message à l'emplacement de réception WCF-NetTcp que vous avez créé dans la procédure précédente.  
  
    -   Le client crée un canal avec le **NetTcpBinding**, puis configure la liaison à utiliser des certificats pour le type d’informations d’identification du client.  
  
    -   Le client configure le comportement du point de terminaison pour qu'il utilise le certificat d'authentification client que vous avez installé dans la procédure précédente pour l'authentification du client.  
  
    -   La classe, **programme**, implémente la **IClientMessageInspector** et **IEndpointBehavior** interfaces pour afficher la sortie [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] messages à partir de ce client à une invite de commandes.  
  
6.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur le **WcfMessageSecurity** solution, puis cliquez sur **reconstruire**.  
  
7.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **déboguer** menu, cliquez sur **démarrer sans débogage** pour exécuter WCFClient de manière à envoyer des emplacements de réception d’un message WCF-NetTcp. Une invite de commandes apparaît pour afficher le résultat de l'exécution.  
  
    1.  À l'invite de commandes, examinez le message de demande de commande. Faites attention à la **OrderId** champ et la structure du message.  
  
    2.  À l’invite de commandes, accédez à la `C:\WCFMessageSecurity\OrderRequestOut` dossier, puis assurez-vous que le message de demande de commande envoyé par le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] client s’affiche.  
  
    3.  Fermez l'invite de commande.