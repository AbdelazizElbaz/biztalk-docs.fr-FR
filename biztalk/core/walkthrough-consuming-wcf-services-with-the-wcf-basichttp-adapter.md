---
title: 'Procédure pas à pas : Utilisation des Services WCF avec l’adaptateur WCF-BasicHttp | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d280198-ba55-4937-91c9-19d6d0ed3194
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3c85d550e7a1429e18035629517017c90b44c9e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="walkthrough-consuming-wcf-services-with-the-wcf-basichttp-adapter"></a>Procédure pas à pas : Utilisation des Services WCF avec l’adaptateur WCF-BasicHttp
  
> [!NOTE]
>  Pour plus d’informations à propos des adaptateurs, consultez [adaptateurs dans BizTalk Server](../core/adapters-in-biztalk-server.md).  
  
## <a name="introduction"></a>Introduction
  
 Dans le cadre de cette procédure pas à pas, vous allez utiliser un service [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)] hébergé dans les services Internet (IIS) en vous servant de la messagerie BizTalk et de l'adaptateur d'envoi WCF-BasicHttp. Cet adaptateur utilise le **BasicHttpBinding** liaison pour fournir une implémentation de pile de transport/protocole compatible avec les versions antérieures des services Web pour faire Office de pont entre Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fonctionnalité. Une orchestration peut lier à un port d'envoi utilisant un adaptateur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] pour appeler un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et exploiter ses fonctionnalités dans son processus d'entreprise logique.  
  
 L'adaptateur WCF-BasicHttp consiste en un adaptateur d'envoi et un adaptateur de réception. Dans cet exemple, vous allez utiliser uniquement le côté réception de cet adaptateur pour établir des demandes de service WCF adressées à un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] via le protocole HTTP.  Pour un port d'envoi sollicitation-réponse, l'adaptateur d'envoi envoie une sollicitation à un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et reçoit un résultat en réponse.  Inversement, un adaptateur de réception [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] permet à une application cliente [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de publier et d'appeler de l'extérieur une orchestration [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Reportez-vous à la [publication des Services WCF](../core/publishing-wcf-services.md) pour plus d’informations.  
  
 Une fois cette procédure pas à pas terminée, vous saurez comment effectuer les tâches suivantes :  
  
-   Depuis [!INCLUDE[btsCoName](../includes/btsconame-md.md)]Visual Studio, utilisez le **déployer** commande pour déployer les assemblys contenant le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution et le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service à une instance locale de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous créerez ainsi une application BizTalk contenant ces assemblys.  
  
-   Depuis Visual Studio, utilisez le **Assistant consommation de Service WCF de BizTalk** pour générer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] schémas et les types nécessaires à l’utilisation du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Une orchestration vide est également générée, que vous pouvez utiliser et lier à un port logique. Celle-ci est compilée et déployée en même temps que les schémas et les types. En revanche, le traitement de workflow d'orchestration est vide et non utilisé dans cet exemple car il s'agit simplement d'un pur scénario de messagerie [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], configurez le routage basé sur le contenu à l'aide du port d'envoi WCF-BasicHttp. Vous allez configurer le **SOAPAction** en-tête que la cible [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service s’attend à recevoir.  
  
-   Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], configurez l'expression de filtre pour router tout message d'erreur SOAP qu'un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] peut envoyer à un dossier de sortie.  
  
-   Dans le Gestionnaire des services Internet, configurez l'application Web hébergeant le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] pour exposer ses métadonnées. Une fois qu’il est activé, le **Assistant consommation de Service WCF de BizTalk** peut obtenir ces métadonnées pour générer des types et des schémas pour accéder à la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
## <a name="prerequisites"></a>Configuration requise  
 Pour exécuter la procédure décrite dans cet exemple, assurez-vous que votre environnement est conforme à la configuration requise décrite ci-dessous :  
  
-   L’ordinateur qui génère les assemblys et exécute le processus de déploiement et l’ordinateur qui exécute l’exemple, requièrent Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], Microsoft [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)]et Microsoft BizTalk Server.  
  
-   L’ordinateur utilisé pour générer les assemblys et exécuter le processus de déploiement requiert Microsoft Visual Studio.  
  
-   L'ordinateur qui exécute l'exemple requiert les adaptateurs [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] et les outils d'administration de [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il s’agit des options d’installation lors de l’installation de Microsoft BizTalk Server.  
  
-   Sur les ordinateurs utilisés pour effectuer des tâches d'administration, vous devez exécuter un compte d'utilisateur membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour configurer les paramètres d'application de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'intérieur de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce compte d'utilisateur doit également être membre du groupe Administrateurs local pour le déploiement d'application, la gestion d'instances de l'hôte et d'autres tâches éventuellement requises.  
  
-   Sur n’importe quel ordinateur qui nécessite [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] fonctionnalité, effectuez la procédure d’installation unique pour le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] exemples [ http://go.microsoft.com/fwlink/?LinkId=135510 ](http://go.microsoft.com/fwlink/?LinkId=135510).  
  
-   Sur l'ordinateur qui exécute l'exemple et importe une liaison ou un fichier .msi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], assurez-vous que l'hôte n'est pas un hôte approuvé, sans quoi l'importation échoue.  
  
-   Vous devez télécharger le code de procédure pas à pas et l’extraire sur votre ordinateur.  Cette procédure pas à pas est une partie de l’ensemble du [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] package de la procédure pas à pas de carte. Vous pouvez télécharger le fichier **WCFAdapterWalkthroughs.exe** à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] centre de développement sur[http://go.microsoft.com/fwlink/?LinkId=194140](http://go.microsoft.com/fwlink/?LinkId=194140).  
  
## <a name="deploy-the-sample-wcf-service"></a>Déployer l’exemple de service WCF  
  
1.  Exécutez le fichier auto-extractible **WCFBasicHttpSendAdapter.exe** de fichiers et d’extraire les fichiers dans le **C:\WCFBasicHttpSendAdapter** dossier.  
  
2.  Ouvrez le **C:\WCFBasicHttpSendAdapter\WCFBasicHttpSendAdapter.sln** dans Visual Studio.  
  
3.  Dans l’Explorateur de solutions, développez le **BasicHttpWCFServiceConsuming** projet. Ce projet est le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] qui sera appelé par le port d'envoi. Il sera hébergé dans un environnement d'hôte géré à l'aide des services Internet. Dans les services Internet, l'hébergement utilise une activation basée sur les messages pour gérer l'activation et la durée du service. Développez **App_Code**, puis ouvrez **OrderProcess.cs** pour passer en revue. Cela [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service reçoit des messages de demande de commande via le **OrderRequest** (méthode). Le fichier OrderProcess.cs contient la définition et l'implémentation de l'interface du service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Il renvoie simplement ordre des messages de réponse via la **OrderResponse** (méthode).  
  
4.  Examinez le fichier OrderProcess.svc. Il contient une seule ligne utilisée pour indiquer aux services Internet d'activer le service pour une application cliente. Le **@ServiceHost** attribut utilisé pour héberger le service est un point d’extensibilité dans le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] modèle de programmation. Un modèle de fabrique utilise **ServiceHostFactory** pour créer une instance de **ServiceHost** avec une instance de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service pour gérer les demandes entrantes. L’instanciation de cette instance est basée sur le **ServiceBehaviorAttribute.ConcurrencyMode** propriété qui détermine si un service prend en charge un seul thread, plusieurs threads ou des appels réentrants. L’instanciation est également déterminée par le **ServiceBehavior.InstanceMode** propriété qui détermine si une seule instance servira tous les appelants (singleton), si une instance sera créée par appel (sans état), ou si une seule instance va être créée pour chaque session (stateful).  
  
    ```  
    <%@ServiceHost language=c# Debug="true" Service="Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming.OrderProcessServiceType" %>  
    ```  
  
5.  Dans Visual Studio, dans l’Explorateur de solutions, ouvrez **Web.config** pour passer en revue. Un service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] hébergé dans les services Internet est configuré à l'aide d'un fichier Web.config au lieu d'un fichier app.config comme c'est le cas quand il est hébergé dans une application console.  
  
    -   Assurez-vous que le **httpGetEnabled** attribut de la \< **serviceMetaData** \> a la valeur `true` afin que le **le Service WCF BizTalk Assistant consommation** peuvent consommer les métadonnées pour le service.  
  
    -   Assurez-vous que le **mode** attribut de la \< **sécurité** \> a la valeur **aucun**. Étant donné que cette procédure pas à pas utilise le **aucun** mode de sécurité, le site Web application hébergeant ce service doit être configurée pour autoriser l’accès anonyme.  
  
6.  Étant donné que la **Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming** assembly doit être installé dans le GAC, vous devez un fichier de clé de nom fort pour terminer le processus de déploiement. Cliquez sur le **BasicHttpWcfServiceConsuming** de projet, puis cliquez sur **propriétés**. Sur le **propriétés** , cliquez sur **signature**, puis sélectionnez **signer l’assembly**. Cliquez sur la flèche vers le bas dans la **choisir un fichier de clé de nom fort** la liste déroulante, cliquez sur  **\<nouveau\>**et entrez `keyfile.snk` dans le **le nom de fichier de clé**zone de texte.  Décochez la case **protéger mon fichier de clé avec un mot de passe**, puis cliquez sur **OK**.  
  
7.  Dans l’Explorateur de solutions, cliquez sur **BasicHttpWcfServiceConsuming**, puis cliquez sur **reconstruire**.  
  
8.  À l’aide de l’Explorateur Windows, copiez le contenu du **C:\WCFBasicHttpSendAdapter\BasicHttpWCFServiceConsuming** à la **C:\InetPub\wwwroot** dossier.  
  
9. Configurez l'application Web pour héberger le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] comme suit :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
    2.  Créer un pool d'applications dans lequel ce service s'exécutera. Avec le bouton droit **Pools d’applications**, cliquez sur **ajouter un Pool d’applications...** , entrez un nom pour le pool d’applications, puis cliquez sur **OK**.  
  
    3.  Développez **Pools d’applications**, cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **paramètres avancés**. Sous **modèle de processus** section, entrez le compte a accès à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données sous le **identité** champ.  
  
    4.  Développez **Sites**, développez **Site Web par défaut**, avec le bouton droit **BasicHttpWCFServiceConsuming**, puis cliquez sur **convertir en Application**pour créer une application Web pour ce [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
    5.  Dans le **convertir en Application** boîte de dialogue, cliquez sur **sélectionnez** pour sélectionner le pool d’applications créé précédemment, puis cliquez sur **OK**.  
  
    6.  Dans l’affichage des fonctionnalités, cliquez sur le **authentification** icône et vérifiez que le **l’authentification anonyme** option est **activé**. Il prend en charge [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] services avec le **aucun** mode de sécurité.  
  
10. Testez le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] publié comme suit :  
  
    1.  Dans le Gestionnaire IIS, développez **Sites Web**, puis développez **BasicHttpWCFServiceConsuming**.  
  
    2.  Dans le Gestionnaire des services Internet, dans le volet droit, cliquez sur **OrderProcess.svc**, puis cliquez sur **Parcourir**. Cela ouvre Internet Explorer pour afficher le **OrderProcessServiceType Service** page indiquant que vous avez créé avec succès en cours d’exécution [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Cette page inclut également une adresse WSDL complète, que vous pouvez copier et utiliser avec l'outil de métadonnées de service (svcutil.exe) pour créer un code proxy et un fichier de configuration utilisables pour développer une application cliente pour le service.  
  
    3.  Copiez l'adresse WSDL complète dans le Presse-papiers système. Ne copiez pas le **« svcutil.exe »** partie : **http://localhost/BasicHttpWcfServiceConsuming/OrderProcess.svc?wsdl**  
  
## <a name="add-the-schemas-and-types-for-the-wcf-basichttp-adapter-to-the-sample-biztalk-application"></a>Ajoutez les schémas et les types de l’adaptateur WCF-BasicHttp à l’exemple d’application BizTalk  
  
1.  Comme l'adaptateur appellera le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)], il a besoin d'informations de schémas et de types concernant la manière d'appeler ce service à l'aide des métadonnées. **BizTalkApp** fournit les artefacts pour utiliser la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Dans Visual Studio, dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, cliquez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
2.  Dans le **ajouter les éléments générés** boîte de dialogue le **modèles** section, sélectionnez **utiliser le Service WCF**, puis cliquez sur **ajouter**.  
  
3.  Sur le **Bienvenue dans l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **suivant**. Cet Assistant lit les métadonnées et crée les schémas et les types.  
  
4.  Sur le **source des métadonnées** page, sélectionnez le **point de terminaison MEX (Metadata Exchange)** option pour utiliser les métadonnées de l’URL que vous avez copié dans le Presse-papiers dans la procédure précédente, puis cliquez sur **Suivant**.  
  
5.  Sur le **point de terminaison de métadonnées** page, collez l’adresse WSDL complète que vous avez copié dans la procédure précédente pour le **adresse des métadonnées** liste déroulante, puis cliquez sur **obtenir** obtenir le document de métadonnées pour l’exemple [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. L’obtention des métadonnées permet le **suivant** bouton. Cliquez sur **Suivant** pour continuer.  
  
6.  Sur le **récapitulatif des métadonnées de Service WCF importation** page, vérifiez vos paramètres. Cette boîte de dialogue présente les récapitulatifs d'espace de noms, XSD et WSDL des métadonnées à importer. Elle indique également où les fichiers d'orchestration (.odx), de liaisons (.xml) et de schéma (.xsd) seront écrits durant le processus d'importation. Cliquez sur **importation** pour créer les artefacts BizTalk et les types à utiliser pour consommer l’exemple [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
7.  Sur le **fin de l’Assistant de consommation de Service WCF BizTalk** , cliquez sur **Terminer**.  
  
8.  Dans Visual Studio, dans l’Explorateur de solutions, le **Assistant consommation de Service WCF de BizTalk** génère les fichiers suivants :  
  
    -   Un fichier d’orchestration **OrderProcessServiceType.odx**. Cette orchestration ne comprend pas d'étape du flux de travail. En revanche, vous pouvez l'ajouter et la lier à des ports logiques pour utiliser le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Elle ne contient pas de types BizTalk importants, tels que des types de ports et de messages à parties multiples, utilisés dans cet exemple. Pour afficher ces informations, double-cliquez sur le **OrderProcessServiceType.odx** orchestration. Cliquez sur **vue**, cliquez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**. Développez **Types**, développez **Types de ports**, puis développez **IOrderProcess**. Vous verrez la **Submit** (méthode). Développez cette méthode, et vous verrez la **OrderRequest** et **OrderResponse** types de ports. Cliquez sur chaque type de port et la vue de leur **Description** champs dans l’Explorateur de propriétés et voir le WSDL différents messages d’entrée et de sortie. Cliquez sur **Types Message à parties multiples** et afficher le **OrderRequest** et **OrderResponse** les types de message à parties multiples. Cliquez sur leurs **Description** champs et afficher le WDSL des noms pour chaque type de message de message.  
  
    -   Deux fichiers de schéma sont générés. Le premier fichier de schéma (**OrderProcessServiceType_biztalk_WCF_basichttpsendadapter_basichttpWCFserviceconsuming.xsd**) définit les types de messages que l’exemple [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service utilise. Elle utilise le **OrderID** champ à la fois dans **OrderRequest** et **OrderResponse** appels.  
  
    -   Le deuxième fichier de schéma (**OrderProcessServiceType_schemas_microsoft_com_2003_10_Serialization.xsd**) n’est exportée par [DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722) pour les types, les éléments et les attributs à partir de la espace de noms, http://schemas.microsoft.com/2003/10/Serialization/.  
  
    -   Deux fichiers de liaison sont générés, qui sera utilisé ultérieurement pour créer l’application BizTalk : **OrderProcessServiceType.BindingInfo.xml** et **OrderProcessServiceType_Custom.BindingInfo.xml**. En règle générale, vous utiliserez le fichier de liaison non personnalisée. Toutefois, dans les rares situations où vous avez un élément de liaison personnalisée, utilisez le fichier de liaison personnalisée. L'élément de liaison personnalisée crée des ports d'envoi pour les applications. Double-cliquez sur le **OrderProcessServiceType.BindingInfo.xml** de fichiers et recherchez le **SendPort** ligne de définition et vérifier que le port d’envoi qui sera créé lorsque vous importez cette liaison de fichiers dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]:  
  
        ```  
        <SendPort Name="WCFSendPort_OrderProcessServiceType_ServiceEndpoint" …  >  
        ```  
  
    -   Ces fichiers sont utilisés par le port d'envoi utilisant l'adaptateur [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] pour consommer l'exemple de service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] décrit dans les métadonnées.  
  
## <a name="deploy-the-sample-biztalk-solution-biztalkapp"></a>Déployer l’exemple de solution BizTalk, BizTalkApp  
  
1.  Déployez l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme suit :  
  
    1.  Dans Visual Studio, dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, puis cliquez sur **propriétés** .  
  
    2.  Dans le **Concepteur de projets** fenêtre, cliquez sur **déploiement** onglet, puis modifiez le **Server** propriété si vous utilisez un serveur de base de données différente pour la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Base de données de gestion. Vérifiez que le nom de l’application est **WCFBasicHttpSendAdapter**.  
  
    3.  Dans Visual Studio, dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, puis cliquez sur **reconstruire**.  
  
    4.  Dans Visual Studio, dans l’Explorateur de solutions, cliquez sur **BizTalkApp**, puis cliquez sur **déployer**.  Cela déploie l’assembly Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BizTalkApp dans le GAC et les artefacts à le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application nommée **WCFBasicHttpSendAdapter**.  
  
2.  Configurez un port d'envoi WCF-BasicHttp dans l'application BizTalk comme suit :  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
    2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **WCFBasicHttpSendAdapter**, pointez sur **Importation**, puis cliquez sur **liaisons**.  
  
    3.  Dans le **importer les liaisons** boîte de dialogue, accédez à la **C:\WCFBasicHttpSendAdapter\BizTalkApp** dossier, sélectionnez **OrderProcessServiceType.BindingInfo.xml**, puis cliquez sur **Ouvrir**. Il s’agit d’un des fichiers de liaison créés par le **Assistant consommation de Service WCF de BizTalk** précédemment. Cette opération crée le **WCFSendPort_OrderProcessServiceType_ServiceEndpoint** port d’envoi.  
  
    4.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFBasicHttpSendAdapter**, puis cliquez sur **Ports d’envoi**.  
  
    5.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, dans le volet droit, double-cliquez sur **WCFSendPort_OrderProcessServiceType_ServiceEndpoint**, lequel a été créée en important le fichier de liaison OrderProcessServiceType.BindingInfo.xml. Ceci fait apparaître la **propriétés de Port d’envoi** boîte de dialogue.  
  
    6.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **configurer**.  
  
    7.  Sur le **général** onglet vérifier les **adresse (URI)** champ **http://localhost/BasicHttpWcfServiceConsuming/OrderProcess.svc**. Il s'agit de l'adresse du service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] hébergé dans les services Internet que l'adaptateur WCF-BasicHttp appellera.  
  
    8.  Passez en revue le contenu de la **en-tête d’Action SOAP/Action** zone de texte :  
  
        ```  
        <BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
          <Operation Name="Submit" Action="http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming/IOrderProcess/Submit" />  
        </BtsActionMapping>  
        ```  
  
         Ce champ indique l'intention du message de demande SOAP HTTP sortant. Dans ce cas, il s'agit d'appeler l'opération d'envoi sur l'interface IOrderProcess à partir de l'espace de noms Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWcfServiceConsuming.  
  
        > [!NOTE]
        >  Le fichier de liaison le **Assistant consommation de Service WCF de BizTalk** génère utilise l’action de mappage de format pour le **StaticAction** propriété. Lorsque vous utilisez le routage basé sur le contenu pour envoyer des messages aux services WCF, les adaptateurs d’envoi WCF, vous devez définir le **BTS. Opération** propriété dans les composants de pipeline pour le format de mappage d’action que le champ à utiliser pour le routage basé sur le contenu. Vous pouvez également utiliser le format d'action unique pour le routage basé sur le contenu. Dans cette procédure pas à pas, vous utilisez le format d'action unique. Pour plus d’informations sur le format d’action unique et le format de mappage d’action, consultez le **boîte de dialogue Propriétés du Transport WCF-BasicHttp, envoi, général** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
    9. Cliquez sur **OK** à deux reprises pour revenir à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
3.  Créez un port de réception statique unidirectionnel et un emplacement de réception FILE. Un port de réception est un conteneur logique pour un ou plusieurs emplacements de réception. C'est l'emplacement où vous allez déposer un exemple de message [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] qui sera récupéré par l'adaptateur FILE, puis envoyé au service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFBasicHttpSendAdapter**, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel Port de réception**.  
  
    2.  Dans le **propriétés du Port de réception** boîte de dialogue le **nom** zone de texte, tapez `WCFBasicSendAdapter.ReceivePurchaseOrder`, puis cliquez sur **OK**.  
  
    3.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **WCFBasicHttpSendAdapter.ReceivePurchaseOrder**, pointez sur **nouveau**, puis cliquez sur **un emplacement de réception** .  
  
    4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** zone de texte, tapez `WCFBasicSendAdapter.ReceivePurchaseOrder.FILE`.  
  
    5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **fichier** dans la liste déroulante, puis cliquez sur **configurer**.  
  
    6.  Dans le **propriétés du Transport FILE** boîte de dialogue le **général** sous l’onglet du **dossier de réception** zone de texte, tapez `C:\WCFBasicHttpSendAdapter\OrderRequestIn`, puis cliquez sur **OK**.  
  
    7.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, cliquez sur **OK**.  
  
4.  Créez un fichier pour router les messages vers le port d'envoi WCF-BasicHttp à partir de l'emplacement de réception FILE que vous avez créé à l'étape précédente. Un filtre associé à un port agit comme une clause SQL « where » dans la mesure où si son évaluation est vraie, le message est transmis à ce port.  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFBasicHttpSendAdapter**, cliquez sur **Ports d’envoi**, puis double-cliquez sur **WCFSendPort_OrderProcessServiceType_ ServiceEndpoint**.  
  
    2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **filtres** onglet, sélectionnez **BTS. ReceivePortName** dans les **propriété** , tapez `WCFBasicSendAdapter.ReceivePurchaseOrder` dans les **valeur** champ, puis cliquez sur **OK**. Cette expression de filtre route les messages entrants du port de réception WCFBasicSendAdapter.ReceivePurchaseOrder vers ce port d'envoi WCF-BasicHttp.  
  
5.  Créez deux ports d'envoi FILE pour l'exemple d'application. Le premier port d'envoi envoie des messages de réponse au port FILE à partir du service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)]. Le deuxième port est utilisé pour gérer les messages d'erreur envoyés par le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] au client.  
  
    1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFBasicHttpSendAdapter**, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Port d’envoi unidirectionnel statique**.  
  
    2.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** zone de texte, tapez `WCFBasicSendAdapter.SendPurchaseOrder.FILE`.  
  
    3.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **Transport** section en regard de Type, sélectionnez **fichier** dans la liste déroulante, puis cliquez sur **configurer** .  
  
    4.  Dans le **propriétés du Transport FILE** boîte de dialogue le **général** sous l’onglet du **dossier de Destination** zone de texte, tapez `C:\WCFBasicHttpSendAdapter\OrderResponseOut`, puis cliquez sur **OK** .  
  
    5.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **filtres** onglet, sélectionnez **BTS. MessageType** dans les **propriété** , tapez `http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWCFServiceConsuming#OrderResponse` dans les **valeur** champ pour spécifier le type de message de réponse à partir de l’exemple [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service, et puis cliquez sur **OK**. Cette expression de filtre route les messages de réponse de l'exemple de service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] vers ce port d'envoi FILE. Le port d'envoi s'abonne aux messages du type OrderResponse en spécifiant celui-ci dans la propriété de filtre. Il s'agit du type du message de réponse du service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)].  
  
    6.  Dans le **propriétés de Port d’envoi** boîte de dialogue, cliquez sur **OK**.  
  
    7.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFBasicHttpSendAdapter**, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Port d’envoi unidirectionnel statique**.  
  
    8.  Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** zone de texte, tapez `WCFAdapterErrorSend.FILE`.  
  
    9. Dans le **propriétés de Port d’envoi** boîte de dialogue le **Transport** section à côté **Type**, sélectionnez **fichier** dans la liste déroulante, puis Cliquez sur **configurer**.  
  
    10. Dans le **propriétés du Transport FILE** boîte de dialogue le **général** sous l’onglet du **dossier de Destination** zone de texte, tapez `C:\WCFBasicHttpSendAdapter\WCFAdapterErrorOut\`, puis cliquez sur **OK** .  
  
    11. Dans le **propriétés de Port d’envoi** boîte de dialogue le **filtres** onglet, sélectionnez **WCF. IsFault** dans les **propriété** , tapez `True` dans les **valeur** champ, puis cliquez sur **OK**. Dans une application, une exception ou une erreur peut être détectée en vérifiant la **WCF. IsFault** propriété du message envoyé à l’appelant. Cette propriété est fixée à **True** si le message envoyé est un message d’erreur SOAP. Cette expression de filtre route les messages d'erreur de l'exemple de service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] vers ce port d'envoi FILE.  
  
6.  Spécifiez le nom d'hôte et les liaisons pour l'exemple d'application comme suit :  
  
     Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **WCFBasicHttpSendAdapter**, développez **Orchestrations**, avec le bouton droit le  **Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BizTalkApp.OrderProcessServiceTypeClient** orchestration, cliquez sur **propriétés**, cliquez sur **liaisons**, définissez **Hôte** à **BizTalkServerApplication**, puis cliquez sur **OK** pour enregistrer la configuration.  
  
## <a name="test-the-sample-solution-with-the-wcf-basichttp-send-adapter"></a>Test de l’exemple de solution avec WCF-BasicHttp l’adaptateur d’envoi  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur **WCFBasicHttpSendAdapter**, puis cliquez sur **Démarrer**.  
  
2.  Dans le **Démarrer** boîte de dialogue, cliquez sur **Démarrer**.  
  
3.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **paramètres de plateforme**, développez **Instances d’hôte**, avec le bouton droit **BizTalkServerApplication** ou un autre approprié d’instance d’hôte, puis cliquez sur **redémarrer**.  
  
4.  Ouvrez une invite de commandes, taper **iisreset** à recycler IIS et ses services dépendants, puis appuyez sur ENTRÉE.  
  
5.  À l’invite de commandes, copiez **C:\WCFBasicHttpSendAdapter\TestData\WCFBasicSendAdapter.OrderRequest.Sample.xml** à la **C:\WCFBasicHttpSendAdapter\OrderRequestIn** dossier. Ce message est routé vers bidirectionnel **WcfSendPort_OrderProcessServiceType_ServiceEndpoint** port d’envoi statique avec sollicitation-réponse.  L’envoi de ce bidirectionnelle envoyer des appels de port **Submit** méthode sur la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service hébergé dans IIS. Le résultat est retourné pour le port de réponse de la **WcfSendPort_OrderProcessServiceType_ServiceEndpoint** port d’envoi.  Le **WCFBasicSendAdapter.SendPurchaseOrder.FILE** port d’envoi comporte un abonnement qui est déclenché lorsque le type du message est **http://Microsoft.Samples.BizTalk.WCF.BasicHttpSendAdapter.BasicHttpWCFServiceConsuming#OrderResponse**. Il sera le message traité avec succès et écrire dans le **C:\WCFBasicHttpSendAdapter\OrderResponseOut** dossier.  
  
6.  Vérifiez le **C:\WCFBasicHttpSendAdapter\OrderResponseOut** dossier pour un message de réponse de le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service.  
  
7.  À l’invite de commandes, **C:\WCFBasicHttpSendAdapter\TestData\WCFBasicSendAdapter.OrderRequest.Invalid.xml** à la **C:\WCFBasicHttpSendAdapter\OrderRequestIn** dossier. Ce message contient un espace de noms non valide pour que le service [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] renvoie un message d'erreur.  
  
8.  Vérifiez le **C:\WCFBasicHttpSendAdapter\WCFAdapterErrorOut** dossier pour un fichier XML contenant le message d’erreur à partir de la [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] service. Examinez le \< **faultstring** \> champ indiquant la cause du message d’erreur à un corps de message non valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Publication de Services WCF avec l’adaptateur WCF-BasicHttp](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)   
 [Comment utiliser l’Assistant consommation de Service WCF BizTalk pour utiliser un Service WCF](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)   
 [Spécification du corps de message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)