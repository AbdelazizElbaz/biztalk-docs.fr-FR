---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service à recevoir des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc5a63ec-1897-4c9b-b37f-cdcec151b1c9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ee9994861772be8fabe04a04e9bb30111cc1bc4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-receive-data"></a>Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour la réception de données
L'adaptateur BizTalk pour TIBCO Enterprise Message Service (EMS) permet de recevoir des données depuis un système TIBCO. Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   L'adaptateur BizTalk pour TIBCO Enterprise Message Service requiert l'ajout de l'API TIBCO EMS C# et du fichier TIBCO.EMS.dll au GAC (Global Assembly Cache). Pour plus d’informations sur l’installation de l’assembly, consultez [TIBCO Enterprise Message Service spécifications et Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).  
  
-   Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour récupérer des données d'un système TIBCO. Le résultat est écrit dans un fichier XML.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple, conçu dans Visual Studio, illustre les fonctionnalités de base à l’aide de l’adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.  
  
> [!NOTE]
>  Cet exemple part du principe que vous savez envoyer un message de TIBCO pour son traitement par l'application.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'emplacement par défaut de l'exemple est  
  
 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWayReceive  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|**Nom de fichier de projet d’exécution**|**Description du fichier de projet d’exécution**|  
|----------------------------------|------------------------------------------|  
|OneWayReceive.btproj,<br /><br /> OneWayReceive.sln|Fichiers de projet et de solution de l'application.|  
|Schema.xsd,|Fichier de schéma de l'application.|  
|Orchestration.odx|Orchestration utilisée par l'application.|  
|TIBCOEMSOneWaySend.snk|Fichier de clé de nom fort.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a>Pour créer une instance de l'adaptateur BizTalk pour TIBCO EMS  
  
1.  Lancez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, **programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.  
  
3.  Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte** pour afficher les **propriétés de l’adaptateur** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **TIBCO EMS**.  
  
5.  Sélectionnez **TIBCO Enterprise Message System** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.  
  
#### <a name="create-a-biztalk-receive-port"></a>Pour créer un port de réception BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.  
  
2.  Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayRP**, puis cliquez sur **OK**.  
  
#### <a name="create-a-biztalk-receive-location"></a>Pour créer un emplacement de réception BizTalk  
  
1.  Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.  
  
2.  Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayRL**.  
  
3.  Sélectionnez l’adaptateur TIBCO EMS dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.  
  
    > [!NOTE]
    >  Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
4.  Entrez des valeurs pour le **définition de la connexion au serveur**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Destination|File d'attente de destination ou nom de la rubrique du serveur.|  
    |Numéro de port|Port sur lequel le serveur TIBCO écoute. Valeur par défaut est 7222.|  
    |Nom de serveur|Nom du serveur TIBCO EMS.|  
  
5.  Entrez des valeurs pour le **informations d’identification utilisateur**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Mot de passe|Mot de passe pour le serveur TIBCO EMS.|  
    |Nom d'utilisateur|Nom d'utilisateur pour le serveur TIBCO EMS.|  
  
     Pour plus d’informations sur les propriétés, consultez [création TIBCO Enterprise Message Service gestionnaires de réception](../core/creating-tibco-enterprise-message-service-receive-handlers.md).  
  
6.  Cliquez sur **OK**.  
  
7.  Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.  
  
8.  Cliquez sur l’emplacement de réception, sur **activer**.  
  
#### <a name="create-a-one-way-file-send-port"></a>Pour créer un port d'envoi de fichier unidirectionnel  
  
1.  Créez un dossier cible destiné à l'usage du port d'envoi (par exemple, C:\FilesOut).  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.  
  
3.  Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayFileSP**.  
  
5.  Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.  
  
6.  Pour le **dossier de Destination** propriété, entrez l’emplacement du dossier que vous avez créé précédemment et cliquez sur **OK**.  
  
7.  Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.  
  
8.  Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.  
  
#### <a name="build-and-deploy-the-project"></a>création et déploiement du projet ;  
  
1.  Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
2.  Cliquez sur le **déploiement** onglet.  
  
3.  Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.  
  
4.  Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.  
  
#### <a name="bind-and-enlist-the-orchestration"></a>Pour lier et inscrire l'orchestration  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.  
  
2.  Cliquez sur le **Actualiser** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] barre d’outils de la console Administration ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.  
  
3.  Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.  
  
4.  Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.  
  
5.  Spécifiez les valeurs appropriées pour les options de liaison, par exemple :  
  
    |**Paramètre**|**Valeur**|  
    |-------------------|---------------|  
    |Hôte|BizTalkServerApplication|  
    |FileSendPort|TIBCOEMSOneWayFileSP|  
    |TibcoEMSOneWayReceiveOperation|TIBCOEMSOneWayRP|  
  
6.  Cliquez sur **OK**.  
  
#### <a name="start-the-orchestration"></a>Démarrer l'orchestration  
  
-   Dans le [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.  
  
#### <a name="verify-that-the-application-receives-a-message"></a>Pour vérifier que l'application a reçu un message  
  
-   Ouvrez le dossier utilisé par le port d'envoi du fichier et vérifiez qu'un document de sortie a été généré. Ce fichier doit contenir les résultats de la requête traitée par l'adaptateur BizTalk pour TIBCO Enterprise Message Service.  
  
 La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :  
  
1.  L'adaptateur TIBCO EMSreçoit un message du système TIBCO et le publie dans la base de données MessageBox en tant que message BizTalk.  
  
2.  L’orchestration s’abonne à ce message publié afin que le moteur de messagerie BizTalk Active une instance de l’orchestration et envoie le message à l’instance d’orchestration.  
  
3.  L'instance d'orchestration republie le message dans la base de données MessageBox.  
  
4.  Le port d'envoi du fichier s'abonne à ce message et BizTalk envoie le message à l'adaptateur FILE.  
  
5.  L'adaptateur FILE écrit le message contenant l'ensemble des résultats dans le dossier de sortie désigné.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service pour envoyer des données](../core/tutorial-use-tibco-enterprise-message-service-adapter-in-biztalk-to-send-data.md)   
 [Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)