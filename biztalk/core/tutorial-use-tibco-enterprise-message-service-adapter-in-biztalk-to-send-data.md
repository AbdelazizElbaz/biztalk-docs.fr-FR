---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service pour envoyer des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1912d594-3839-4e04-bc40-93bd7cc0b309
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 913e8c0a3f44673d5bf06bf48d7c1ccf8b7a4ee2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-enterprise-message-service-to-send-data"></a>Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour l'envoi de données
L'adaptateur BizTalk pour TIBCO Enterprise Message Service (EMS) permet d'envoyer des données à un système TIBCO. Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   L'adaptateur BizTalk pour TIBCO EMS requiert l'ajout de l'API TIBCO EMS C# et du fichier TIBCO.EMS.dll au GAC (Global Assembly Cache). Pour plus d’informations sur l’installation de l’assembly, consultez [TIBCO Enterprise Message Service spécifications et Limitations](../core/tibco-enterprise-message-service-requirements-and-limitations.md).  
  
-   Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Enterprise Message Service pour créer un enregistrement dans le système TIBCO.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple, conçu dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'emplacement par défaut de l'exemple est  
  
 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Enterprise Message Service(TM)\Sdk\OneWaySend  
  
 Le tableau suivant répertorie et décrit les fichiers de l'exemple.  
  
|**Nom de fichier de projet d’exécution**|**Description du fichier de projet d’exécution**|  
|----------------------------------|------------------------------------------|  
|OneWaySend.btproj<br /><br /> OneWaySend.sln|Fichiers de projet et de solution de l'application.|  
|Schema.xsd|Fichier de schéma de l'application.|  
|Orchestration.odx|Orchestration utilisée par l'application.|  
|TIBCOEMSOneWaySend.snk|Fichier de clé de nom fort.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-ems"></a>Pour créer une instance de l'adaptateur BizTalk pour TIBCO EMS  
  
1.  Lancez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, **tous les programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.  
  
3.  Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte** pour afficher les **propriétés de l’adaptateur** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **TIBCO EMS**.  
  
5.  Sélectionnez **TIBCO Enterprise Message System** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.  
  
#### <a name="create-a-biztalk-send-port"></a>Pour créer un port d'envoi BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.  
  
2.  Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique** pour afficher les **propriétés de Port d’envoi** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWaySP**.  
  
4.  Sélectionnez l’adaptateur TIBCO EMS dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.  
  
    > [!NOTE]
    >  Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO Enterprise Message System dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
5.  Entrez des valeurs pour le **définition de la connexion au serveur**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Destination|File d'attente de destination ou nom de la rubrique du serveur.|  
    |Numéro de port|Port sur lequel le serveur TIBCO écoute. Valeur par défaut est 7222.|  
    |Nom de serveur|Nom du serveur TIBCO EMS.|  
  
6.  Entrez des valeurs pour le **informations d’identification utilisateur**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Mot de passe|Mot de passe pour le serveur TIBCO EMS.|  
    |Nom d'utilisateur|Nom d'utilisateur pour le serveur TIBCO EMS.|  
  
     Pour plus d’informations sur les propriétés, consultez [création TIBCO Enterprise Message Service gestionnaires d’envoi](../core/creating-tibco-enterprise-message-service-send-handlers.md).  
  
7.  Cliquez sur **OK**.  
  
8.  Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.  
  
9. Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.  
  
#### <a name="create-a-file-receive-port"></a>Pour créer un port de réception du fichier  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.  
  
2.  Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel** pour afficher la boîte de dialogue Propriétés du Port de réception.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayFileRP**, puis cliquez sur **OK**.  
  
#### <a name="create-a-file-receive-location"></a>Pour créer un emplacement de réception du fichier  
  
1.  Créez un dossier correspondant à l'emplacement de réception du fichier à analyser (par exemple, C:\Filesource).  
  
2.  Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception** pour afficher les **propriétés de l’emplacement de réception** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCOEMSOneWayFileRL**.  
  
4.  Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.  
  
5.  Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.  
  
6.  Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.  
  
7.  Cliquez sur l’emplacement de réception, sur **activer**.  
  
#### <a name="generate-a-document-instance-from-the-adapter-schema"></a>Pour générer une instance de document à partir du schéma de l'adaptateur  
  
1.  Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** catégorie.  
  
3.  Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.  
  
4.  Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.  
  
    > [!NOTE]
    >  Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.  
  
5.  Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.  
  
#### <a name="modify-the-generated-document-instance"></a>Pour modifier l'instance de document générée  
  
1.  Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez-en le contenu de telle sorte que les données génèrent un enregistrement unique dans le système TIBCO. Par exemple, le code suivant illustre la première partie du fichier de données :  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoEMSOne_WaySend.TibcoEMSOneWaySendSchema">  
      <Name>Punya Palit</Name>  
      <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  Enregistrez l'instance de document modifiée.  
  
#### <a name="build-and-deploy-the-project"></a>création et déploiement du projet ;  
  
1.  Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
2.  Cliquez sur le **déploiement** onglet.  
  
3.  Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.  
  
4.  Cliquez sur le projet OneWaySend dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.  
  
#### <a name="bind-and-enlist-the-orchestration"></a>Pour lier et inscrire l'orchestration  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.  
  
2.  Cliquez sur le **Actualiser** bouton dans la barre d’outils MMC ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.  
  
3.  Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.  
  
4.  Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.  
  
5.  Spécifiez les valeurs appropriées pour les options de liaison, par exemple :  
  
    |**Paramètre**|**Valeur**|  
    |-------------------|---------------|  
    |Hôte|BizTalkServerApplication|  
    |FileReceivePort|TIBCOEMSOneWayFileRP|  
    |TibcoEMSOneWaySendPort|TIBCOEMSOneWaySP|  
  
6.  Cliquez sur OK.  
  
#### <a name="start-the-orchestration"></a>Démarrer l'orchestration  
  
-   Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.  
  
#### <a name="drop-a-document-instance-into-the-folder-monitored-by-the-file-receive-location"></a>Pour placer une instance de document dans le dossier surveillé par l'emplacement de réception du fichier  
  
-   Copiez l'instance de document créée précédemment dans le dossier correspondant à l'emplacement de réception du fichier surveillé par l'application.  
  
#### <a name="verify-that-the-tibco-system-is-updated"></a>Pour vérifier la mise à jour du système TIBCO  
  
-   Utilisez l'interface Web TIBCO pour vérifier que l'enregistrement a été créé à partir des données du fichier XML.  
  
 La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :  
  
1.  L'adaptateur FILE récupère le fichier dans le dossier et le publie dans la base de données MessageBox comme message BizTalk.  
  
2.  L'orchestration s'abonne à ce message publié et le moteur de messagerie BizTalk active une instance de l'orchestration avant d'envoyer le message à l'instance d'orchestration.  
  
3.  L'instance d'orchestration traite le message à l'aide de la logique spécifiée dans l'orchestration, puis republie le message dans la base de données MessageBox.  
  
4.  Le port d'envoi TIBCO s'abonne à ce message publié et le moteur de messagerie BizTalk envoie le message au port d'envoi TIBCO.  
  
5.  Le port d'envoi remet le message à l'adaptateur BizTalk pour TIBCO Enterprise Message Service.  
  
6.  L'adaptateur BizTalk pour TIBCO Enterprise Message Service envoie le message au système TIBCO.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Enterprise Message Service à recevoir des données](../core/tutorial-us-the-biztalk-adapter-for-tibco-message-service-to-receive-data.md)   
 [Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service](../core/tutorials-use-the-microsoft-biztalk-adapter-for-tibco-message-service.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)