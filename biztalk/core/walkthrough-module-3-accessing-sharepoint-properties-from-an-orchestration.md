---
title: "Procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, orchestrations
- Windows SharePoint Services adapter tutorials, accessing SharePoint properties
ms.assetid: 310c4002-3416-44c6-b409-1d5467063e28
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23bc9f0b1f2d350864509536a393de639e108e2d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="walkthrough-module-3---accessing-sharepoint-properties-from-an-orchestration"></a>Procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration
Cette procédure pas à pas est la suite de [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) et vous montre comment accéder aux propriétés de contexte Windows SharePoint Services d’un message entrant à durée d’exécution, puis déterminer la destination de ce message basée sur une propriété à l’aide des ports dynamiques dans une orchestration. Pour une présentation de l’adaptateur Windows SharePoint Services, consultez [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez disposer d’un déploiement de serveur unique avec une installation complète de BizTalk Server s’exécutant [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].  
  
-   Vous devez effectuer les procédures suivantes : [procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) et [procédure pas à pas : Module 2 - intégration d’Office avec Windows Adaptateur SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)  
  
 Pour plus d’informations sur l’utilisation de l’adaptateur Windows SharePoint Services dans un déploiement de serveurs multiples, consultez [configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).  
  
## <a name="modify-the-biztalk-project"></a>Modification du projet BizTalk  
 Cette procédure vous permet de modifier le schéma PurchaseOrder de [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md). Cette procédure montre comment promouvoir une propriété de schéma pour un accès facile dans une orchestration BizTalk.  
  
#### <a name="modify-the-purchaseorderxsd-schema"></a>Modification du schéma PurchaseOrder.xsd  
  
1.  Démarrer **Microsoft Visual Studio**.  
  
2.  Cliquez sur **fichier**, cliquez sur **ouvrir**, puis cliquez sur **projet/Solution**.  
  
3.  Accédez à la `OrderProcess.sln` de fichiers, puis cliquez sur **ouvrir**.  
  
4.  Dans **l’Explorateur de solutions**, avec le bouton droit le `OrderProcessSchema.xsd` de fichiers, puis cliquez sur **ouvrir**.  
  
5.  Dans **l’Éditeur BizTalk**, développez `PurchaseOrder`.  
  
6.  Avec le bouton droit `Amount`, cliquez sur **promouvoir**, puis cliquez sur **Promotion rapide**.  
  
7.  Cliquez sur **OK**.  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] crée un schéma de propriété ad hoc dans le projet en cours.  
  
8.  Enregistrez `PurchaseOrder.xsd`.  
  
## <a name="create-an-orchestration"></a>Création d'une orchestration  
 Cette procédure permet de créer une orchestration BizTalk. Cette procédure crée l'orchestration utilisée pour traiter un message reçu par l'adaptateur Windows Sharepoint Services.  
  
#### <a name="add-a-biztalk-orchestration"></a>Ajout d'une orchestration BizTalk  
  
1.  Dans **l’Explorateur de solutions**, avec le bouton droit le `OrderProcess` de projet, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Sous **catégories**, sélectionnez **fichiers d’Orchestration**.  
  
3.  Sous **modèles**, sélectionnez **Orchestration BizTalk**.  
  
4.  Type `MyCompanyOrderProcessing` dans les **nom** champ, puis cliquez sur **ajouter**.  
  
## <a name="create-receive-information"></a>Création d'informations de réception  
 Cette procédure permet de créer un message, un port de réception et une forme Réception pour l'orchestration. Elle montre comment configurer une orchestration pour recevoir un message de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="create-a-new-message"></a>Création d'un message  
  
1.  Dans **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**. Cette action génère un nouveau message nommé `Message_1`.  
  
2.  Avec le bouton droit `Message_1`, cliquez sur **renommer**, puis tapez `Message_PO`.  
  
3.  Avec le bouton droit `Message_PO`, puis cliquez sur **fenêtre Propriétés**.  
  
4.  Dans le **Type de Message** propriétés, développez **schémas**, puis sélectionnez `OrderProcess.OrderProcessSchema` schéma.  
  
#### <a name="add-a-receive-port-to-the-orchestration"></a>Ajout d'un port de réception à l'orchestration  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Port** forme sur la Surface du Port. L'Assistant Configuration du port démarre.  
  
2.  Dans l’écran d’accueil, cliquez sur **suivant**.  
  
3.  Type `ReceivePurchaseOrder` dans les **nom** champ, puis cliquez sur **suivant**.  
  
4.  Sélectionnez **créer un nouveau Type de Port**.  
  
5.  Type `PurchaseOrderPT` dans les **nom du Type de Port** champ, puis cliquez sur **suivant**.  
  
6.  Sur le **écran de liaison de Port**, conservez les valeurs par défaut, puis cliquez sur **suivant**.  
  
7.  Cliquez sur **Terminer**.  
  
8.  Dans **Vue Orchestration**, sous **Types de ports**, développez le `PurchaseOrderPT` type de port.  
  
9. Avec le bouton droit `Operation_1`, cliquez sur **renommer**, puis tapez `PurchaseOrderOperation`.  
  
#### <a name="add-a-receive-shape-to-the-orchestration"></a>Ajout d'une forme Réception à l'orchestration  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **réception** forme à l’Orchestration.  
  
2.  Avec le bouton droit de la forme réception, puis cliquez sur **fenêtre Propriétés**.  
  
3.  Définir le **activer** propriété `True`.  
  
    > [!NOTE]
    >  Si la propriété Activer est définie sur false, vous obtenez l'erreur suivante : « erreur X2214 : vous devez indiquer au moins un ensemble de corrélations déjà initialisé pour une réception sans activation située sur un port autre qu'un port d'autocorrélation ».  
  
4.  Type `Receive_PO` dans les **nom** champ.  
  
5.  Dans le **fenêtre Propriétés**, sélectionnez `Message_PO` pour la propriété de Message.  
  
6.  Sélectionnez `ReceivePurchaseOrder.PurchaseOrderOperation.Request` pour le **opération** propriété. Cela lie le port à la forme Réception dans le Concepteur d'orchestration.  
  
## <a name="create-send-information"></a>Création d'informations d'envoi  
 Cette procédure permet de créer un message, des ports d'envoi et une structure de décision pour l'orchestration. Cette procédure montre comment configurer une orchestration avec une logique de décision et comment configurer une orchestration pour envoyer un message à un port d'envoi.  
  
#### <a name="create-a-new-message"></a>Création d'un message  
  
1.  Dans **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**. Cette action génère un nouveau message nommé `Message_1`.  
  
2.  Avec le bouton droit `Message_1`, cliquez sur **renommer**, puis tapez `Message_Task`.  
  
3.  Avec le bouton droit `Message_Task`, puis cliquez sur **fenêtre Propriétés**.  
  
4.  Dans le **Type de Message** propriétés, développez **schémas**, puis sélectionnez `OrderProcess.OrderProcessSchema` schéma.  
  
#### <a name="add-a-send-port-to-the-orchestration"></a>Ajout d'un port d'envoi à l'orchestration  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Port** forme sur la Surface du Port. L'Assistant Configuration du port démarre.  
  
2.  Dans l’écran d’accueil, cliquez sur **suivant**.  
  
3.  Type `SendPurchaseOrder` dans les **nom** champ, puis cliquez sur **suivant**.  
  
4.  Sélectionnez **utiliser un Type de Port existant**.  
  
5.  Sous **Types de ports disponibles**, sélectionnez `OrderProcess.PurchaseOrderPT`, puis cliquez sur **suivant**.  
  
6.  Sur le **écran de liaison de Port**, sous **direction de communication du Port**, sélectionnez `I'll always be sending messages on this port`, puis cliquez sur **suivant**.  
  
7.  Cliquez sur **Terminer**.  
  
#### <a name="add-a-send-shape-to-the-orchestration"></a>Ajout d'une forme Envoi à l'orchestration  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **envoyer** forme pour le Concepteur d’Orchestration. Placez-la sous la forme Réception `Receive_PO`.  
  
2.  Avec le bouton droit de la forme envoi, puis cliquez sur **fenêtre Propriétés**.  
  
3.  Type `Send_PO` dans les **nom** champ.  
  
4.  Sélectionnez `Message_PO` pour le **Message** propriété.  
  
5.  Sélectionnez `SendPurchaseOrder.PurchaseOrderOperation.Request` pour le **opération** propriété. Cela lie le port à la forme Envoi dans le Concepteur d'orchestration.  
  
#### <a name="add-a-decide-shape-to-the-orchestration"></a>Ajout d'une forme Décider à l'orchestration  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **décider** forme pour le Concepteur d’Orchestration. Placez-la sous la forme Envoi `Send_PO`.  
  
2.  Avec le bouton droit de la forme décider, puis cliquez sur **fenêtre Propriétés.**  
  
3.  Type `NeedsApproval` dans les **nom** champ.  
  
4.  Dans le Concepteur d’Orchestration, cliquez sur **Rule_1** sur la forme décider.  
  
5.  Dans la fenêtre Propriétés, tapez `ApprovalRequired` pour le **nom** propriété.  
  
6.  Cliquez sur le **Expression** propriété de champ, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
7.  Dans l'Éditeur d'expression BizTalk, tapez ou copiez ce qui suit :  
  
    ```  
    Message_PO(OrderProcess.PropertySchema.Amount) > 1000  
    ```  
  
8.  Cliquez sur **OK**.  
  
#### <a name="add-another-send-port-to-the-orchestration"></a>Ajout d'un autre port d'envoi à l'orchestration  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Port** forme sur la Surface du Port. L'Assistant Configuration du port démarre.  
  
2.  Dans l’écran d’accueil, cliquez sur **suivant**.  
  
3.  Type `SendToTasksList` dans les **nom** champ, puis cliquez sur **suivant**.  
  
4.  Sélectionnez **utiliser un Type de Port existant**.  
  
5.  Sous **Types de ports disponibles**, sélectionnez `OrderProcess.PurchaseOrderPT`, puis cliquez sur **suivant**.  
  
6.  Sur le **écran de liaison de Port**, sous **direction de communication du Port**, sélectionnez `I'll always be sending messages on this port`.  
  
7.  Sous **liaison de Port**, sélectionnez `Dynamic`, puis cliquez sur **suivant**.  
  
8.  Cliquez sur **Terminer**.  
  
#### <a name="add-a-send-shape-to-the-decide-shape"></a>Ajout d'une forme Envoi à la forme Décider  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **envoyer** forme pour le Concepteur d’Orchestration. Placez-la sous la forme `ApprovalRequired`.  
  
2.  Avec le bouton droit de la forme envoi, puis cliquez sur **fenêtre Propriétés**  
  
3.  Type `CreateApprovalTask` dans les **nom** champ.  
  
4.  Sélectionnez `Message_Task` pour le **Message** propriété.  
  
5.  Sélectionnez `SendToTasksList.PurchaseOrderOperation.Request` pour le **opération** propriété. Cela lie le port à la forme Envoi dans le Concepteur d'orchestration.  
  
## <a name="create-an-expression"></a>Créer une expression  
 Dans cette procédure, vous allez ajouter une forme Expression à votre solution, qui attribue la valeur du chemin des tâches à une variable. Cette procédure montre comment ajouter une logique à une orchestration pour modifier les propriétés d'un port d'envoi dynamique.  
  
#### <a name="create-a-new-expression"></a>Création d'une expression  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Expression** avant de mettre en forme le `CreateApprovalTask` forme envoi.  
  
2.  Avec le bouton droit de la forme Expression, puis cliquez sur **fenêtre Propriétés.**  
  
3.  Type `SetPortDestination` dans les **nom** champ.  
  
4.  Cliquez sur le **Expression** propriété de champ, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
5.  Dans le **Éditeur d’Expression BizTalk**, tapez la commande suivante :  
  
    ```  
    SendToTasksList(Microsoft.XLANGs.BaseTypes.Address) = "wss://localhost/sites/WSSAdapterWalkthrough/Lists/Tasks/";  
    ```  
  
6.  Cliquez sur **OK**.  
  
## <a name="construct-a-new-message"></a>Construction d'un nouveau message  
 Dans cette procédure, vous allez ajouter une forme Construire à la solution, qui construira une nouvelle instance d'un type de message à l'intérieur de l'orchestration. Cette procédure montre comment créer un message qui est une copie du message entrant, puis modifier les propriétés de contexte du nouveau message. Cette étape est obligatoire parce que les messages sont immuables dans BizTalk. Une fois que vous avez construit un message original, vous ne pouvez plus le modifier.  
  
#### <a name="add-a-construct-shape"></a>Ajout d'une forme Construction  
  
1.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **construire un Message** avant de mettre en forme le `SetPortDestination` forme Expression.  
  
2.  Avec le bouton droit de la forme construire un Message, puis cliquez sur **fenêtre Propriétés.**  
  
3.  Type `ConstructTaskMessage`dans les **nom** champ.  
  
4.  Sélectionnez `Message_Task` pour le **Messages construits** propriété.  
  
5.  Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **assignation du Message** mettre en forme le `ConstructTaskMessage` **construire un Message** forme.  
  
6.  Dans le **fenêtre Propriétés**, type `InitTaskMessage` dans les **nom** champ.  
  
7.  Cliquez sur le **Expression** propriété de champ, puis cliquez sur le bouton de sélection (**...** ) bouton.  
  
8.  Dans le **Éditeur d’Expression BizTalk**, tapez ou copiez les éléments suivants :  
  
    ```  
    Message_Task = Message_PO;  
    Message_Task(WSS.ConfigOverwrite) = "no";  
    Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";  
    Message_Task(WSS.ConfigPropertiesXml) = "<ConfigPropertiesXml><PropertyName1>Title</PropertyName1><PropertySource1>Approve %XPATH=//orchns:PurchaseOrder/orchns:PurchaseOrderID%</PropertySource1><PropertyName3>Status</PropertyName3><PropertySource3>Not Started</PropertySource3><PropertyName4>Priority</PropertyName4><PropertySource4>(1) High</PropertySource4></ConfigPropertiesXml>";  
    ```  
  
    > [!IMPORTANT]
    >  Les valeurs fournies pour ces propriétés de contexte respectent la casse. Lors de la définition de valeurs de configuration pour un port dynamique avec des propriétés de contexte, vous devez veiller à utiliser la casse appropriée, sans quoi une erreur se produit quand BizTalk tente de router le document vers le port d'envoi désigné.  
  
9. Cliquez sur **OK**.  
  
10. Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.  
  
## <a name="build-the-biztalk-project"></a>Création du projet BizTalk  
 Dans cette procédure, vous allez construire et déployer le projet BizTalk. Cette étape est nécessaire pour créer et déployer l'assembly que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise au moment de l'exécution.  
  
#### <a name="build-and-deploy-the-solution"></a>Création et déploiement de la solution  
  
1.  Cliquez sur **générer**, puis cliquez sur **OrderProcess de Build**.  
  
2.  Cliquez sur **générer**, puis cliquez sur **OrderProcess de déployer**.  
  
3.  Fermez Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
## <a name="modify-the-receive-location-and-send-port"></a>Modification de l'emplacement de réception et du port d'envoi  
 Dans cette procédure, vous allez modifier l'emplacement de réception et le port d'envoi existants pour utiliser le traitement XML pour les pipelines. Le pipeline de réception XML conserve les propriétés de message utilisées durant le traitement de l'orchestration, puis le pipeline d'envoi XML conserve les propriétés de message appliquées dans l'orchestration, qui sont ensuite utilisées pour le routage des messages.  
  
#### <a name="modify-the-receive-location"></a>Modification de l'emplacement de réception  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server.**  
  
2.  Développez **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **composant logiciel enfichable Administration**, développez **groupe BizTalk**, développez **Applications**, développez  **BizTalk Application 1**, puis cliquez sur le **emplacements de réception** nœud.  
  
3.  Avec le bouton droit `SourceLocation`, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue **général**, sélectionnez `XMLReceive` pour le **pipeline de réception** propriété.  
  
5.  Cliquez sur **OK**.  
  
#### <a name="modify-the-send-port"></a>Modification du port d'envoi  
  
1.  Cliquez sur le **Ports d’envoi** nœud.  
  
2.  Avec le bouton droit `SendToDestination`, puis cliquez sur **propriétés**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue **général**, sélectionnez `XMLTransmit` pour le **pipeline d’envoi** propriété.  
  
4.  Sélectionnez le **filtres** onglet.  
  
5.  Sélectionnez la condition existante, appuyez sur SUPPR, puis cliquez sur **OK**.  
  
#### <a name="start-a-new-send-port"></a>Démarrage d'un nouveau port d'envoi  
  
1.  Cliquez sur le **Ports d’envoi** nœud.  
  
2.  Avec le bouton droit `OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`, puis cliquez sur **Démarrer**.  
  
> [!NOTE]
>  Vous devrez peut-être actualiser la console si elle n'est pas visible.  
  
## <a name="bind-the-orchestration"></a>Liaison de l'orchestration  
 Dans cette procédure, vous allez lier l'orchestration aux ports spécifiés. Cette procédure est obligatoire pour lier des ports physiques à l'orchestration que vous avez construite et déployée.  
  
#### <a name="bind-the-orchestration"></a>Liaison de l'orchestration  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Orchestrations** nœud.  
  
2.  Cliquez sur le `OrderProcess.MyCompanyOrderProcessing` orchestration, puis cliquez sur **propriétés**.  
  
3.  Sélectionnez le **liaisons** onglet.  
  
4.  Sous **hôte**, sélectionnez `BizTalkServerApplication` dans les **hôte** champ.  
  
5.  Sous **liaisons**, sélectionnez `FromSource` pour la `ReceivePurchaseOrder` ports logiques entrants.  
  
6.  Sous **liaisons**, sélectionnez `SendToDestination` pour la `SendPurchaseOrder` ports logiques sortants.  
  
7.  Cliquez sur **OK**.  
  
8.  Bouton droit sur `OrderProcess.MyCompanyOrderProcessing` orchestration, puis cliquez sur **Démarrer**.  
  
## <a name="send-a-message-through-the-system"></a>Envoi d'un message via le système  
 Dans cette procédure, vous allez créer un formulaire InfoPath et le télécharger sur le site Web Windows SharePoint Services. L'adaptateur Windows SharePoint Services prend ce message, l'archive dans la bibliothèque de documents d'archive, puis l'envoie dans la bibliothèque de documents de destination. Durant le traitement de ce message, des propriétés de contexte Windows SharePoint Services seront utilisées pour déterminer la destination.  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a>Création d'un formulaire InfoPath pour envoi via le système  
  
1.  Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.  
  
2.  Dans le menu de lancement rapide, cliquez sur `InfoPathSolutions`.  
  
3.  Cliquez sur le `PurchaseOrder` fichier pour afficher la **télécharger le fichier** boîte de dialogue, puis cliquez sur **ouvrir**. InfoPath va charger le formulaire.  
  
4.  Dans le **Purchase Order ID** , tapez `1003`.  
  
5.  Dans le **facturation** , tapez `John Doe`.  
  
6.  Dans le **quantité** , tapez `1750`.  
  
7.  Dans le **Purchase Order Date** , tapez `1/3/2005`.  
  
8.  Cliquez sur **Enregistrer**.  
  
9. Dans le **enregistrer en tant que** boîte de dialogue, tapez `http://<server_name>/sites/WSSAdapterWalkthrough/Source`dans les **nom de fichier** champ, puis appuyez sur ENTRÉE.  
  
10. Type `PurchaseOrder3.xml` dans les **nom de fichier** champ, puis cliquez sur **enregistrer**.  
  
11. Fermez InfoPath.  
  
12. Dans le navigateur Web, cliquez sur **Documents et listes**.  
  
13. Sous **bibliothèques de documents**, cliquez sur **Destination**.  
  
14. Dans la bibliothèque de documents de destination, vous allez voir votre message répertorié dans cette bibliothèque. Vous y trouverez également une copie archivée dans la bibliothèque de documents d’Archive.  
  
15. Cliquez sur **Accueil**.  
  
16. Sous **répertorie**, cliquez sur **tâches**.  
  
17. Dans la liste Tâches, vous verrez la tâche d'approbation créée.  
  
> [!NOTE]
>  Comme le montant du bon de commande était supérieur à 1 000,00 $, la tâche a été créée.  
  
## <a name="summary"></a>Résumé  
 Cette procédure pas à pas vous a montré comment accéder aux propriétés de contexte Windows SharePoint Services et déterminer la destination des messages transitant par les ports dynamiques.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Continuez à consulter le reste de la section sur l'adaptateur Windows SharePoint. Pour plus d'informations, consultez les rubriques sous Voir aussi.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md)   
 [Procédures pas à pas relatives à l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-walkthroughs.md)