---
title: "Étape 7 (en local) : Création d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c0b6d0e-cf00-4eee-9b89-28210bad46f4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b92a641252a76f4668cdf4c96c8df442c43d4719
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-on-premises-create-an-orchestration"></a>Étape 7 (en local) : Création d’une Orchestration
Selon le scénario d’entreprise, après [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit le message de commande client à partir de la file d’attente de Bus de Service, il doit vérifier si la quantité commandée dans le message est supérieure à 100. Si la quantité est supérieure à 100, le message est inséré dans le **SalesOrder** table. Sinon, le message est envoyé dans un emplacement de fichier partagé. Northwind parvient à mettre en œuvre cette logique métier en créant une orchestration. Cette rubrique fournit des instructions pas à pas pour la créer.  
  
### <a name="to-add-an-orchestration-to-the-includebtsbiztalkservernoversionincludesbtsbiztalkservernoversion-mdmd-project"></a>Pour ajouter une orchestration au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous avez déjà créé, cliquez sur le projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.  
  
2.  Dans le **un nouvel élément** boîte de dialogue, sélectionnez **Orchestration BizTalk**, entrez le nom de mappage `OrderProcessing.odx`, puis cliquez sur **ajouter**.  
  
## <a name="create-messages-for-the-orchestration"></a>Création de messages pour l’orchestration  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, du type défini par le schéma correspondant. Vous devez à présent créer des messages pour l’orchestration, puis les lier aux schémas que vous avez générés précédemment. Vous devez créer les trois messages suivants :  
  
|Nom du message|Correspond au schéma|  
|------------------|---------------------------|  
|Message1_SO_Inbound|Ce message est une instance de la **ECommerceSalesOrder.xsd** schéma.|  
|Message2_SO_Inbound|Ce message est une copie de la **Message1_SO_Inbound**. Il est recommandé de créer une copie du message, puis de modifier le nouveau message de manière à garder intact le message d’orgine. Pour plus d’informations, consultez [messages BizTalk Server](http://msdn.microsoft.com/library/aa560436).|  
|Message1_SO_Outbound|Ce message est une instance de la **TableOperations.dbo.SalesOrder (Insert)** schéma.|  
  
#### <a name="to-create-the-messages"></a>Pour créer les messages  
  
1.  Ouvrez le **Vue Orchestration** fenêtre du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Nom de la propriété|Action à effectuer|  
    |-------------------|--------------------|  
    |Identificateur|Entrez`Message1_SO_Inbound`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *OrderProcessingDemo.ECommerceSalesOrder*, où *OrderProcessingDemo* est le nom de votre BizTalk projet. *ECommerceSalesOrder* est le schéma pour le message de commande reçu à partir de la file d’attente du Bus de Service.|  
  
5.  Répétez les étapes pour créer les messages avec les informations suivantes :  
  
    |Nom du message||  
    |------------------|-|  
    |Message2_SO_Inbound|-Définissez **identificateur** à`Message2_SO_Inbound`<br />-Définissez **Type de Message** à *OrderProcessingDemo.ECommerceSalesOrder*|  
    |Message1_SO_Outbound|-Définissez **identificateur** à`Message1_SO_Outound`<br />-Définissez **Type de Message** à *OrderProcessingDemo.TableOperation_dbo_SalesOrder.Insert*|  
  
## <a name="add-shapes-to-the-orchestration"></a>Ajout de formes à l’orchestration  
 Les formes Orchestration définissent le flux d’une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans cette section, vous allez ajouter les formes requises à l’orchestration.  
  
#### <a name="to-add-shapes-to-the-orchestration"></a>Pour ajouter des formes à l'orchestration  
  
1.  Pour commencer, vous devez ajouter un **réception** forme. Cette forme reçoit le message de commande client entrant en provenance de la file d’attente Service Bus. Définissez les propriétés suivantes sur la forme Réception.  
  
    1.  Définissez **activer** à **True**.  
  
    2.  Définissez **Message** à **Message1_SO_Inbound**.  
  
    3.  Définissez **nom** à **ReceiveOrder**.  
  
2.  Comme indiqué précédemment, vous devez créer une copie du message de commande client d’origine reçu dans l’orchestration.  
  
    1.  Glisser-déposer un **construire un Message** sous la forme la **ReceiveOrder** forme. Étant donné que vous utilisez cette forme pour construire un message de type Message2_SO_Inbound, définissez le **Messages construits** propriété **Message2_SO_Inbound**.  
  
    2.  Ajouter un **assignation du Message** mettre en forme dans le **construire un Message** forme. Double-cliquez sur la forme pour ouvrir l’Éditeur d’expression, puis ajoutez les informations suivantes :  
  
        ```  
        Message2_SO_Inbound = Message1_SO_Inbound; //copy the message  
        Message2_SO_Inbound(*) = Message1_SO_Inbound(*); //copy the context properties on the message  
        ```  
  
         Cliquez sur **OK**.  
  
3.  D’après le scénario d’entreprise, le message doit être envoyé vers différentes destinations en fonction de la quantité d’articles commandés. Aussi, vous devez à présent extraire la valeur de quantité du message de commande client entrant.  
  
    1.  Le **quantité** élément dans le message entrant (ECommerceSalesOrder.xsd) contient la valeur de la quantité commandée. Vous devez promouvoir cette propriété de sorte que l’élément puisse être utilisé dans les expressions au sein de l’orchestration. Pour promouvoir la propriété, ouvrez le **ECommerceSalesOrder.xsd** schéma, avec le bouton droit **quantité**, pointez sur **promouvoir**, puis cliquez sur **Promotions rapides** .  
  
    2.  Créez une variable afin de stocker la valeur de quantité. Pour créer une variable, à partir de la **Vue Orchestration**, avec le bouton droit **Variables**, puis cliquez sur **nouvelle Variable**. Définissez les propriétés suivantes de la variable :  
  
        |Nom de la propriété|Valeur|  
        |-------------------|-----------|  
        |Identificateur|Entrez`quantityOrdered`|  
        |Type|Sélectionnez **Int32**.|  
  
    3.  Vous devez à présent affecter la valeur de la **quantité** élément à la **quantityOrdered** variable. Glisser-déposer un **l’éditeur d’Expression** après le **construire un Message** forme. Ouvrez l’Éditeur, puis entrez l’expression suivante :  
  
        ```  
        quantityOrdered = Message2_SO_Inbound.Quantity;  
        ```  
  
         Cliquez sur **OK**.  
  
4.  Après avoir extrait la quantité commandée, vous devez maintenant créer un bloc de décision dans lequel vous disposez deux chemins d’accès différents que doit emprunter le flux de message. Vous créez le bloc de décision dans une orchestration en ajoutant un **décider** forme.  
  
    1.  Faites glisser et déposez un **décider** forme après la **l’éditeur d’Expression** forme.  
  
    2.  Sélectionnez le **Rule_1** forme et dans le **propriétés** fenêtre, spécifiez les éléments suivants :  
  
        |Nom de la propriété|Valeur|  
        |-------------------|-----------|  
        |Identificateur|Entrez `Yes`. **Remarque :** l’autre itinéraire est nommée par défaut **Else**.|  
        |Expression|Entrez `quantityOrdered > 100`.|  
  
         Vous avez maintenant deux itinéraires possibles. Si la valeur de la **quantityOrdered** variable est supérieure à 100, le message emprunte le **Oui** itinéraire. Dans le cas contraire, il prend le **Else** itinéraire. Vous devez maintenant définir les actions à effectuer au sein de chaque itinéraire.  
  
5.  D’après le scénario d’entreprise, si la quantité commandée est supérieure à 100, le message doit être inséré dans la table SalesOrder. Ainsi, dans le **Oui** itinéraire, vous devez transformer le schéma ECommerceSalesOrder.xsd en schéma TableOperations.SalesOrder.Insert. Vous avez créé le schéma d’insertion dans la rubrique [étape 5 (locaux) : générer le schéma d’insertion d’un Message dans la SalesOrder Table](../core/step-5-generate-the-schema-for-inserting-a-message-into-salesorder-table.md). Après avoir transformé le schéma, vous devez envoyer le message dans la table de base de données SQL Server.  
  
    1.  Dans le **Oui** Router, faites glisser un **construire un Message** forme. Définir le **Messages construits** propriété de la forme à **Message1_SO_Outbound**.  
  
    2.  Dans le **construire un Message** forme ajouter un **transformer** forme. Double-cliquez sur la forme pour ouvrir la **transformer la Configuration** boîte de dialogue. Procédez comme suit :  
  
        1.  Sélectionnez le **mappage existant** option.  
  
        2.  À partir de la **nom de mappage complet** liste déroulante, sélectionnez **OrderProcessingDemo.SalesOrder_SQL**.  
  
        3.  Pour **Source**, sélectionnez **Message2_SO_Inbound**.  
  
        4.  Pour **Destination**, sélectionnez **Message1_SO_Outound**.  
  
    3.  Après le **construire un Message** mettre en forme, faites glisser un **envoyer** mettre en forme et de définir la **Message** propriété de la forme à `Message1_SO_Outbound`.  
  
6.  D’après le scénario d’entreprise, si la quantité commandée est inférieure à 100, le message doit être envoyé dans un emplacement de fichier partagé. Ainsi, dans le **Else** itinéraire, vous devez ajouter une forme envoi.  
  
    1.  Dans le **Else** Router, faites glisser un **envoyer** mettre en forme et de définir la **Message** propriété de la forme à `Message2_SO_Inbound`.  
  
        > [!NOTE]
        >  Vous définissez la propriété Message sur Message2_SO_Inbound, car le même message reçu de la file d’attente Service Bus est envoyé dans l’emplacement de fichier, sans aucun traitement. Message2_SO_Inbound représente le message reçu par la file d’attente Service Bus.  
  
## <a name="add-ports-to-the-orchestration"></a>ajout des ports à l'orchestration  
 Pour une orchestration, les ports représentent les intermédiaires d’entrée et de sortie d’un message. Les messages sont consommés par une orchestration à l’aide d’un port de réception, puis sont renvoyés à l’aide d’un port d’envoi. Dans le scénario d’entreprise, un message est reçu d’un intermédiaire (une file d’attente Service Bus), puis renvoyé vers deux emplacements différents (une base de données SQL Server ou un emplacement de partage de fichiers) en fonction du traitement du message. Ainsi, vous devez créer un port de réception et deux ports d’envoi dans le cadre de l’orchestration.  
  
#### <a name="to-add-ports"></a>Pour ajouter des ports  
  
1.  Glisser- déposer un **Port** à mettre en forme le **Surface du Port** volet de la **le Concepteur d’Orchestration** pour lancer le **Assistant Configuration du Port**. Sur le **Bienvenue** , cliquez sur **suivant**.  
  
2.  Dans le **propriétés de Port** page, nommez le port `ReceiveSO` puis cliquez sur **suivant**.  
  
3.  Dans le **sélectionner un Type de Port** , sélectionnez **créer un nouveau type de port** option, sélectionnez le **unidirectionnel** communication de modèle, laissez la valeur par défaut pour les restrictions d’accès, puis Cliquez sur **suivant**.  
  
4.  Dans le **liaison de Port** page, pour la direction du port, sélectionnez **toujours recevoir les messages sur ce port**, laissez la liaison de port à la valeur par défaut, puis cliquez sur **suivant**.  
  
5.  Dans la dernière page, cliquez sur **Terminer**.  
  
6.  Répétez les étapes pour créer les deux ports d’envoi, en spécifiant les valeurs suivantes.  
  
    |Nom du port|Propriétés|  
    |---------------|----------------|  
    |SendToSQL|-Définissez **nom** à **SendToSQL**<br />-Sélectionnez **créer un nouveau type de port**<br />-Modèle de communication set à **unidirectionnel**<br />-La valeur direction du port **toujours envoyer les messages sur ce port**|  
    |SendToFile|-Définissez **nom** à **SendToFile**<br />-Sélectionnez **créer un nouveau type de port**<br />-Modèle de communication set à **unidirectionnel**<br />-La valeur direction du port **toujours envoyer les messages sur ce port**|  
  
## <a name="connect-ports-and-message-shapes"></a>Connexion des ports et des formes de message  
 Pour terminer l’orchestration, vous devez à présent connecter les ports et les formes de message. L’orchestration démarre lorsque le message est reçu par le **ReceiveOrder** forme et l’orchestration quitte lorsque le message est envoyé par les deux formes d’envoi. Vous devez utiliser ce critère pour connecter les ports et les formes de message.  
  
#### <a name="to-connect-ports-with-message-shapes"></a>Pour connecter les ports aux formes de message  
  
1.  Connecter le **ReceiveSO** port de réception pour le **ReceiveOrder** forme.  
  
2.  Connectez la forme envoi sous la **Oui** router vers le **SendToSQL** port d’envoi. Cela indique que si un message emprunte cet itinéraire (**quantityOrdered** > 100), il est envoyé à la **SalesOrder** table dans la base de données SQL Server.  
  
3.  Connectez la forme envoi sous la **Else** router vers le **SendToFile** port d’envoi. Cela indique que si un message emprunte cet itinéraire (**quantityOrdered** < = 100), il est envoyé vers un emplacement de fichier spécifié.  
  
     L’orchestration doit ressembler à ceci :  
  
     ![Orchestration](../core/media/bts2010r2-tut1-orch.jpg "BTS2010R2_Tut1_Orch")  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)