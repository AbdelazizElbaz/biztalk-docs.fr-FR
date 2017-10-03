---
title: "Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b761ce2d-3465-43e0-bd8d-4d68b523226a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 63540402ca8e060d26c8398af010a81eaad0a6fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data"></a>Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données
L'adaptateur BizTalk pour TIBCO Rendezvous permet d'envoyer des données vers un système TIBCO. Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.  
  
-   L'exemple utilise une DLL contenant des propriétés de contexte de message : Microsoft.BizTalk.Adapters.TibRV.Properties.dll. Vous devrez mettre la référence de solution à jour en fonction de cette bibliothèque. Pour plus d’informations, consultez [propriétés de contexte du Message BizTalk Server (gestionnaires d’envoi)](../core/biztalk-server-message-context-properties-send-handlers.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple récupère un fichier XML dans un dossier, le transmet à une orchestration, puis utilise l'adaptateur BizTalk pour TIBCO Rendezvous pour créer un enregistrement dans le système TIBCO.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple, conçu dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous avec une orchestration BizTalk.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'emplacement par défaut de l'exemple est  
  
 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWaySend  
  
 Le tableau suivant répertorie et décrit les fichiers de l'exemple.  
  
|**Nom de fichier de projet d’exécution**|**Description du fichier de projet d’exécution**|  
|----------------------------------|------------------------------------------|  
|OneWaySend.btproj<br /><br /> OneWaySend.sln|Fichiers de projet et de solution de l'application.|  
|Schema.xsd<br /><br /> PropertySchema.xsd|Fichiers de schéma et fichiers de schéma de propriété pour l'application.|  
|Orchestration.odx|Orchestration utilisée par l'application.|  
|TIBCORendezvousOneWaySend.snk|Fichier de clé de nom fort.|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
  
#### <a name="create-a-new-instance-of-the-biztalk-adapter-for-tibco-rendezvous"></a>Pour créer une instance de l'adaptateur BizTalk pour TIBCO Rendezvous  
  
1.  Lancez la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cliquez sur **Démarrer**, **programmes**, **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Adaptateurs**.  
  
3.  Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...** Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **TIBCO Rendezvous**.  
  
5.  Sélectionnez **TIBCO Rendezvous(r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.  
  
#### <a name="create-a-biztalk-send-port"></a>Pour créer un port d'envoi BizTalk  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.  
  
2.  Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique...** Pour afficher le **propriétés de Port d’envoi** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWaySP**.  
  
4.  Sélectionnez l’adaptateur TIBCO Rendezvous à partir de la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.  
  
    > [!NOTE]
    >  Cette valeur est le nom spécifié lors de la création de l’adaptateur TIBCO Enterprise Message System dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
5.  Entrez des valeurs pour le **propriétés d’expéditeur certifié**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Nom du fichier de comptabilité|Nom du fichier de comptabilité à utiliser pour la remise des messages certifiés persistants.|  
    |Nom réutilisable|Nom de destinataire réutilisable à utiliser pour la remise des messages certifiés. Le nom doit être unique parmi les noms de destinataires de messages certifiés sur le réseau.|  
  
6.  Entrez des valeurs pour le **informations d’identification**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Mot de passe|Mot de passe pour le serveur TIBCO Rendezvous.|  
    |Nom d'utilisateur|Nom d'utilisateur pour le serveur TIBCO Rendezvous.|  
  
7.  Entrez des valeurs pour le **RendezvousTransport**:  
  
    |**Propriété**|**Valeur**|  
    |------------------|---------------|  
    |Daemon|Paramètre Daemon du transport Rendezvous.|  
    |Réseau|Paramètre Réseau du transport Rendezvous.|  
    |Service|Paramètre Service du transport Rendezvous.|  
  
     Pour plus d’informations sur les propriétés, consultez [comment définir les propriétés de Transport TIBCO Rendezvous](../core/how-to-set-tibco-rendezvous-transport-properties.md).  
  
8.  Cliquez sur **OK**.  
  
9. Sélectionnez le **XML Transmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.  
  
10. Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.  
  
#### <a name="create-a-file-receive-port"></a>Pour créer un port de réception du fichier  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.  
  
2.  Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel...**  pour afficher la boîte de dialogue Propriétés du Port de réception.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWayFileRP**, puis cliquez sur **OK**.  
  
#### <a name="create-a-file-receive-location"></a>Pour créer un emplacement de réception du fichier  
  
1.  Créez un dossier correspondant à l'emplacement de réception du fichier à analyser (par exemple, C:\Filesource).  
  
2.  Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception...** Pour afficher le **propriétés de l’emplacement de réception** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCORndOneWayFileRL**.  
  
4.  Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.  
  
5.  Entrez l’emplacement du dossier que vous avez créé précédemment pour le **dossier de réception** propriété et cliquez sur **OK**.  
  
6.  Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.  
  
7.  Cliquez sur l’emplacement de réception, sur **activer**.  
  
#### <a name="generate-a-document-instance-from-the-schema"></a>Pour générer une instance de document à partir du schéma  
  
1.  Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **propriétés**.  
  
2.  Dans la fenêtre Propriétés, cliquez pour sélectionner le **nom de fichier de sortie Instance** sous le **général** section.  
  
3.  Cliquez sur le bouton points de suspension (...) pour afficher la **sélectionner le fichier de sortie** boîte de dialogue.  
  
4.  Spécifiez le dossier et le nom de l’instance de fichier de sortie, par exemple **C:\instance.xml** et cliquez sur **enregistrer**.  
  
    > [!NOTE]
    >  Ne spécifiez pas l'emplacement de dossier spécifié pour l'emplacement de réception du fichier dans ce champ.  
  
5.  Avec le bouton droit Schema.xsd dans l’Explorateur de solutions, puis cliquez sur **générer l’Instance** pour générer une instance de document à l’emplacement spécifié.  
  
#### <a name="modify-the-generated-document-instance"></a>Pour modifier l'instance de document générée  
  
1.  Ouvrez l'instance de document générée dans un éditeur de texte tel que le Bloc-notes et modifiez-en le contenu de telle sorte que les données génèrent un enregistrement unique dans le système TIBCO. Par exemple, le code suivant illustre la première partie du fichier de données :  
  
    ```  
    <ns0:Root xmlns:ns0="http://TibcoRendezvousOneWaySend.TibcoRendezvousOneWaySendSchema">  
        <Name>Punya Palit</Name>  
        <MailAddress>Prose Ware, Inc.</MailAddress>  
    </ns0:Root>  
    ```  
  
2.  Enregistrez l'instance de document modifiée.  
  
#### <a name="build-and-deploy-the-project"></a>création et déploiement du projet ;  
  
1.  Avec le bouton droit le **OneWaySend** de projet dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
2.  Cliquez sur le **déploiement** onglet.  
  
3.  Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk**.  
  
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
    |FileReceivePort|TIBCORndOneWayFileRP|  
    |TibcoRendezvousSend|TIBCORndOneWaySP|  
  
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
  
5.  Le port d'envoi remet le message à l'adaptateur BizTalk pour TIBCO Rendezvous.  
  
6.  L'adaptateur BizTalk pour TIBCO Rendezvous envoie le message au système TIBCO.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data.md)   
 [Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)