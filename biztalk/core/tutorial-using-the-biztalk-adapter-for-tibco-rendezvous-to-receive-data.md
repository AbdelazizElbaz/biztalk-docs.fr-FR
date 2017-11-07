---
title: "Didacticiel : Utiliser l’adaptateur TIBCO Rendezvous pour recevoir | Documents Microsoft"
description: "Guide pas à pas pour utiliser l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server pour recevoir des données à partir du système TIBCO"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58e7a739-701d-4085-a840-54f81c55e943
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75aaba0cc2e455676e78381c04934dda30741a85
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-receive-data"></a>Didacticiel : utilisation de l'adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données
L'adaptateur BizTalk pour TIBCO Rendezvous permet de recevoir des données d'un système TIBCO. Cette procédure pas à pas décrit un exemple de kit de développement logiciel qui illustre ce comportement.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
Installez [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] dans la version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur laquelle l'adaptateur est exécuté afin de créer et de déployer l'exemple.  
  
## <a name="about-the-sample"></a>À propos de l’exemple 
- Cet exemple utilise l'adaptateur BizTalk pour TIBCO Rendezvous pour recevoir des données d'un système TIBCO. Une orchestration traite le message et écrit les données dans un fichier XML situé dans un dossier spécifié à l'aide de l'adaptateur FILE.  
  
- Cet exemple, conçu dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], illustre les fonctionnalités de base liées à l'utilisation de l'adaptateur BizTalk pour TIBCO Enterprise Message Service avec une orchestration BizTalk.  
  
    > [!NOTE]
    >  Cet exemple part du principe que vous savez envoyer un message de TIBCO pour son traitement par l'application.  
  
- L’emplacement par défaut de l’exemple est `C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\TIBCO(r) Rendezvous(r)\Sdk\OneWayReceive`et inclut les fichiers suivants : 
  
    |**Nom de fichier de projet d’exécution**|**Description du fichier de projet d’exécution**|  
    |---|---|  
    |OneWayReceive.btproj,<br /><br /> OneWayReceive.sln|Fichiers de projet et de solution de l'application.|  
    |PureMessage.xsd,|Fichier de schéma de l'application.|  
    |TIBCORvOWR.odx|Orchestration utilisée par l'application.|  
    |TIBCORv.snk|Fichier de clé de nom fort.|  
  
  
## <a name="step-1-add-the-adapter-to-biztalk-administration"></a>Étape 1 : Ajouter l’adaptateur à l’Administration de BizTalk
  
1.  Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur **cartes**.  
  
3.  Avec le bouton droit **cartes** et pointez sur **nouveau**, **carte...** Pour afficher le **propriétés de l’adaptateur** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **TIBCO Rendezvous**.  
  
5.  Sélectionnez **TIBCO Rendezvous(r)** à partir de la liste des adaptateurs disponibles dans le **carte** liste déroulante et cliquez sur **OK**.  
  
## <a name="step-2-create-a-receive-port"></a>Étape 2 : Créer un Port de réception  
  
1.  Dans **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports de réception**.  
  
2.  Cliquez sur le dossier Ports de réception, puis sur **nouveau**, **Port de réception unidirectionnel...**  pour afficher les **propriétés du Port de réception** boîte de dialogue.  
  
3.  Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayRP**, puis cliquez sur **OK**.  
  
## <a name="step-3-create-a-receive-location"></a>Étape 3 : Créer un emplacement de réception  
  
1.  Avec le bouton, le nouveau port de réception, puis cliquez sur **nouveau**, **un emplacement de réception...** Pour afficher le **propriétés de l’emplacement de réception** boîte de dialogue.  
  
2.  Entrez une valeur pour le **nom** champ. Par exemple, entrez **TIBCORvOneWayRL**.  
  
3.  Sélectionnez l’adaptateur TIBCO Rendezvous à partir de la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **propriétés du Transport** boîte de dialogue.  
  
    > [!NOTE]
    >  Cette valeur correspond au nom spécifié lors de la création de l'adaptateur TIBCO dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
4.  Entrez une valeur pour le **RendezvousSubjectName** sous le **AdapterRequiredProperties**.  
  
5.  Entrez des valeurs pour le **propriétés de l’écouteur certifié**:  
  
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
  
     Pour plus d’informations sur les propriétés, consultez [de réception créer les artefacts](../core/creating-tibco-rendezvous-receive-handlers.md).  
  
8.  Cliquez sur **OK**.  
  
9. Sélectionnez **XMLReceive** dans la liste des pipelines disponibles dans le **pipeline de réception** liste déroulante, puis cliquez sur **OK**.  
  
10. Cliquez sur l’emplacement de réception, sur **activer**.  
  
## <a name="step-4-create-a-one-way-send-port"></a>Étape 4 : Créer un port d’envoi unidirectionnel  
  
1.  Créez un dossier cible destiné à l'usage du port d'envoi (par exemple, C:\FilesOut).  
  
2.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Ports d’envoi**.  
  
3.  Avec le bouton droit **Ports d’envoi** et pointez sur **nouveau**, **Port d’envoi unidirectionnel statique...** Pour afficher le **propriétés de Port d’envoi** boîte de dialogue.  
  
4.  Entrez une valeur pour le **nom** champ, par exemple **TIBCORvOneWayFileSP**.  
  
5.  Sélectionnez **fichier** dans la liste des adaptateurs disponibles dans le **Type** liste déroulante, puis cliquez sur le **configurer** bouton pour afficher la carte **Transport Propriétés** boîte de dialogue.  
  
6.  Pour le **dossier de Destination** propriété, entrez l’emplacement du dossier que vous avez créé précédemment et cliquez sur **OK**.  
  
7.  Sélectionnez le **XMLTransmit** pipeline à partir de la liste des pipelines disponibles dans le **pipeline d’envoi** liste déroulante et cliquez sur **OK**.  
  
8.  Cliquez sur le port d’envoi, sur **Démarrer** pour inscrire et démarrer le port d’envoi.  
  
## <a name="step-5-build-and-deploy-the-project"></a>Étape 5 : Créer et déployer le projet  
  
1.  Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
2.  Cliquez sur le **déploiement** onglet.  
  
3.  Entrez les valeurs appropriées pour le **Server** propriété et la **base de données de Configuration** propriété sous **groupe BizTalk** catégorie.  
  
4.  Cliquez sur le projet OneWayReceive dans l’Explorateur de solutions, puis cliquez sur **déployer** pour générer le projet et déployer l’assembly dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données de configuration.  
  
## <a name="step-6-bind-enlist-and-start-the-orchestration"></a>Étape 6 : Lier, inscrire et démarrer l’orchestration  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BizTalk Application 1**, puis cliquez sur **Orchestrations**.  
  
2.  Cliquez sur le **Actualiser** situé dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] barre d’outils de la console Administration ou appuyez sur la **F5** clé de votre clavier pour actualiser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] affichage de la console Administration.  
  
3.  Double-cliquez sur l’orchestration pour afficher le **propriétés d’Orchestration** boîte de dialogue.  
  
4.  Cliquez sur **liaisons** dans le volet gauche de la boîte de dialogue pour afficher les options de liaisons de l’orchestration.  
  
5.  Spécifiez les valeurs appropriées pour les options de liaison, par exemple :  
  
    |**Paramètre**|**Valeur**|  
    |-------------------|---------------|  
    |Hôte|BizTalkServerApplication|  
    |SendPort|TIBCORvOneWayFileSP|  
    |ReceivePort|TIBCORvOneWayRP|  
  
6.  Cliquez sur **OK**.  
  
7. Avec le bouton droit de l’orchestration, puis cliquez sur **Démarrer** pour inscrire et démarrer l’orchestration.  
  
## <a name="step-7-confirm-the-application-receives-a-message"></a>Étape 7 : Vérifier que l’application reçoit un message.  
  
-   Ouvrez le dossier que le port d’envoi file est configuré pour envoyer et vérifier qu’un document de sortie a été généré.  
  
 La séquence suivante d'événements se produit si l'instance de document est traitée avec succès :  
  
1.  L'adaptateur TIBCO Rendezvous reçoit un message du système TIBCO et le publie dans la base de données MessageBox en tant que message BizTalk.  
  
2.  L’orchestration s’abonne à ce message publié afin que le moteur de messagerie BizTalk Active une instance de l’orchestration et envoie le message à l’instance d’orchestration.  
  
3.  L'instance d'orchestration republie le message dans la base de données MessageBox.  
  
4.  Le port d'envoi du fichier s'abonne à ce message et BizTalk envoie le message à l'adaptateur FILE.  
  
5.  L'adaptateur FILE écrit le message contenant l'ensemble des résultats dans le dossier de sortie désigné.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour TIBCO Rendezvous pour envoyer des données](../core/tutorial-using-the-biztalk-adapter-for-tibco-rendezvous-to-send-data.md)   
 [Didacticiels : À l’aide de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)   
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)