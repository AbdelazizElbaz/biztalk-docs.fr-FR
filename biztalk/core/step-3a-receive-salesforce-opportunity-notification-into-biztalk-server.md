---
title: "Étape 3 a : recevoir une Notification d’opportunité de Salesforce dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be9de6e3-6bd9-4275-b2fb-0a756c51aabf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 76ab28e8e70c0b8a222f6772a763a93252f2c413
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-receive-salesforce-opportunity-notification-into-biztalk-server"></a>Étape 3 a : recevoir une Notification d’opportunité de Salesforce dans BizTalk Server
Dans cette étape, nous commençons la création d'un serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Nous devons d'abord comprendre le schéma de message pour le message de notification des opportunités que nous recevrons de Salesforce et, ensuite, commencer à créer une orchestration pour traiter le message.  
  
### <a name="to-include-the-salesforce-opportunities-notification-schema"></a>Pour comprendre le schéma de notification des opportunités Salesforce  
  
1.  Connectez-vous au portail Salesforce.com. Dans le portail Salesforce, cliquez sur votre nom de connexion à l’angle supérieur droit de la page, puis cliquez sur **le programme d’installation**.  
  
2.  Dans le volet gauche, sous **programme d’installation de l’application**, développez **créer**, développez **Workflow & approbations**, puis cliquez sur **les règles de flux de travail**.  
  
3.  Dans le **toutes les règles de flux de travail** , cliquez sur le **opportunité fermée** flux de travail que vous avez créé précédemment.  
  
4.  Dans le **opportunité fermée** page de la règle de flux de travail, cliquez sur **NewOp1** action de flux de travail de message sortant.  
  
5.  Dans le **NewOp1** action de flux de travail de message sortant page, cliquez sur le lien **cliquer pour WSDL**, cliquez sur **enregistrer la cible sous**, puis spécifiez l’emplacement où vous souhaitez enregistrer le WSDL.  
  
    > [!NOTE]
    >  Vous devez enregistrer le fichier avec une extension .wsdl.  
  
6.  Créez un serveur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Pour ce didacticiel, Nommons le projet en tant que `BtsSalesforceIntegration`.  
  
7.  Avec le bouton droit le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **ajouter les éléments générés**.  
  
8.  Dans le **ajouter les éléments générés** boîte de dialogue, cliquez sur **utiliser le Service WCF**, puis cliquez sur **ajouter** pour lancer le **BizTalk WCF Service consommation**Assistant. Dans la page d’accueil, cliquez sur **suivant**.  
  
9. Sur le **Source des métadonnées** page, sélectionnez le **des fichiers de métadonnées (WSDL et XSD)** option, puis cliquez sur **suivant**.  
  
10. Sur le **des fichiers de métadonnées** , cliquez sur **ajouter**, puis accédez à l’emplacement où vous avez enregistré le fichier WSDL téléchargé à partir du portail Salesforce. Sélectionnez le fichier WSDL, puis cliquez **suivant**.  
  
11. Dans la page suivante, définissez l’espace de noms `NotificationService` puis cliquez sur **importation**. L'assistant ajoute les fichiers de schéma et une orchestration au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le schéma de message pour recevoir des notifications d’opportunité de Salesforce est **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.  
  
### <a name="to-create-an-orchestration-to-receive-the-notification-message"></a>Pour créer une orchestration pour recevoir le message de notification  
  
1.  Après avoir terminé la **consommation de Service WCF BizTalk** Assistant, une orchestration (**NotificationService.odx**, dans cet exemple) est ajouté à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet.  
  
2.  Ouvrez le fichier d'orchestration et dans la vue de l'orchestration, ajoutez deux nouvelles variables de message. Nommez-les `NotificationMessage` et `NotificationAck`. Définissez le type de message pour ces variables de message comme suit :  
  
    1.  Définissez **NotificationMessage** à *NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notifications*. Cette variable de message représente le message de notification d'opportunité reçu de Salesforce.  
  
    2.  Définissez **NotificationAck** à *NotificationService.NotificationService_soap_sforce_com_2005_09_outbound.notificationsResponse*. Cette variable de message représente le message d'accusé de réception de notification d'opportunité renvoyé à Salesforce.  
  
3.  Ajoutez une forme de réception à l'orchestration. Définissez les propriétés suivantes sur la forme :  
  
    1.  Définissez **activer** à **True**.  
  
    2.  Définissez **nom** à *ReceiveNotificationMessage*.  
  
    3.  Définissez **Message** à *NotificationMessage*.  
  
4.  Ajoutez une forme Construire un message après la forme Réception. Nom de la forme de message `ConstructNotificationResponse` et définir le **Messages construits** propriété `NotificationAck`. Dans le cadre du message Construire, nous allons également créer un mappage pour générer un message d'accusé de réception de la notification à renvoyer à Salesforce.  
  
    1.  Dans la forme Construire un message, ajoutez une forme Transformer. Double-cliquez sur la forme Transformer et dans la boîte de dialogue, sélectionnez le **nouveau mappage** option.  
  
    2.  Spécifiez le nom de mappage `BtsSalesforceIntegration.MapNotificationResponse`.  
  
    3.  Définissez la Source **NotificationMessage** et de Destination en tant que **NotificationAck**.  
  
    4.  Assurez-vous que la case à cocher **après avoir cliqué sur OK, lancer le Mappeur BizTalk** est sélectionnée.  
  
    5.  Dans **MapNotificationResponse.btm**, nous allons créer une réponse de notification à renvoyer à Salesforce. Chaque fois que Salesforce envoie une notification, il attend un accusé de réception en retour. Le schéma du message de réponse de notification indique que le **l’accusé de réception** élément dans la réponse est de type booléen. Par conséquent, dans le mappage, vous devez supprimer un **mappage** fonctoid et définissez ses deux valeurs d’entrée (Condition et Result) à `true`. Cliquez sur **OK** pour enregistrer le fonctoid.  
  
    6.  Connecter le **mappage** fonctoid à la **l’accusé de réception** élément dans le schéma de destination.  
  
5.  Dans l'orchestration, après la forme Construire un message, ajoutez une forme Envoyer qui sera utilisée pour renvoyer l'accusé de réception à Salesforce.  
  
    -   Définissez **nom** à *SendNotificationAck*.  
  
    -   Définissez **Message** à *NotificationAck*.  
  
6.  Dans l'orchestration, ajoutez un port pour recevoir le message de notification Salesforce et envoyer l'accusé de réception en réponse. Dans l'assistant Configuration du port, sélectionnez les options suivantes :  
  
    -   Spécifiez le nom de port `SalesforceNotificationPort`.  
  
    -   Sélectionnez l'option pour créer un nouveau type de port.  
  
    -   Définissez **modèle de Communication** à *demande-réponse*.  
  
    -   Définir **direction de communication du Port** à *j’être reçoit une demande et envoyer une réponse* et définissez **liaison de Port** à *spécifierultérieure*.  
  
     Connecter le **demande** opération du port à la forme réception (*ReceiveNotificationMessage*) et le **réponse** opération du port sur la forme envoi (*SendNotificationAck*). La capture d'écran ci-dessous illustre la partie de l'orchestration qui reçoit une notification d'opportunité de Salesforce et renvoie un accusé de réception :  
  
     ![Recevoir une notification d’opportunité et envoyer une réponse](../core/media/bts-sf-recvnotificationorch.jpg "BTS_SF_RecvNotificationOrch")  
  
 À l'heure actuelle, nous avons mis en place la solution dans laquelle une notification d'opportunité est reçue de Salesforce et un accusé de réception est renvoyé. Dans les rubriques suivantes, nous allons nous baser sur cette solution pour commencer le traitement de la notification d'opportunité afin d'obtenir plus de détails sur le genre d'opportunité de vente disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer la Solution BizTalk Server dans Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)