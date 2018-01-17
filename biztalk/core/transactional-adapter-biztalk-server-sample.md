---
title: Adaptateur transactionnel (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31a13377-cc89-4763-ad1b-508a16fc9708
caps.latest.revision: "36"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f934857103952a035159cc08678c8ce8c8e51a56
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="transactional-adapter-biztalk-server-sample"></a>Adaptateur transactionnel (exemple BizTalk Server)
L'exemple d'adaptateur transactionnel montre comment créer et utiliser une transaction Microsoft Distributed Transaction Coordinator (MSDTC) explicite sur une base de données lors du traitement d'un message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple contient un adaptateur de réception qui exécute une instruction SQL, à un intervalle spécifié par l'utilisateur, afin d'obtenir des données d'une base de données SQL Server à l'aide d'une transaction MSDTC. Ces données sont alors transmises à la base de données MessageBox de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sous la forme d'un message, dans le contexte de la même transaction.  
  
 L'adaptateur d'envoi correspondant exécute une procédure stockée SQL spécifiée par l'utilisateur via l'entrée d'un message BizTalk dans le contexte d'une transaction. Il utilise les données spécifiques de ce message pour localiser et supprimer le message correspondant de la base de données MessageBox, sous cette même transaction.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Cet exemple inclut deux projets dans sa solution. Le premier, le projet administratif (Admin), est utilisé avant l'exécution pour permettre à un utilisateur de configurer les emplacements de réception et les ports d'envoi qui utilisent cet adaptateur. Le deuxième, le projet d'exécution (Runtime), est exécuté lorsque les adaptateurs d'envoi et de réception sont exécutés.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans l'emplacement SDK suivant :  
  
 \<*Exemples de chemin d’accès*\>\Samples\AdaptersDevelopment\TransactionalAdapter. Le projet administratif de configuration se trouve dans le dossier \Admin, et le projet d'exécution dans le dossier \Runtime.  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Nom du fichier de projet Admin|Description du fichier de projet Admin|  
|----------------------------|------------------------------------|  
|TransactionalAdmin.csproj|Fichier du projet administratif de l'adaptateur utilisé pour la configuration antérieure à l'exécution|  
|TransactionalReceiveHandler.xsd|XSD pour les propriétés du gestionnaire de réception|  
|TransactionalReceiveLocation.xsd|XSD pour les propriétés de l'emplacement de réception|  
|TransactionalTransmitLocation.xsd|XSD pour les propriétés de l'emplacement de transmission|  
|TransactionalTransmitHandler.xsd|XSD pour les propriétés du gestionnaire de transmission|  
|TransactionalAdapterManagement.cs|Gestion de la configuration de l'adaptateur. Contient GetConfigSchema qui est appelé par l'infrastructure d'adaptateurs BizTalk pour renvoyer un schéma de configuration XSD pour chacun des (quatre) types de configurations possibles qu'il prend en charge.|  
  
|Nom du fichier de projet au moment de l'exécution|Description du fichier de projet au moment de l'exécution|  
|------------------------------|--------------------------------------|  
|Transactional.csproj|Fichier du projet d'exécution de l'adaptateur|  
|TransactionalAsyncBatch.cs|Implémentation asynchrone du port d'envoi de l'adaptateur|  
|TransactionalDeleteBatch.cs|Supprime un lot de messages et valide ou abandonne une transaction|  
|TransactionalProperties.cs|Extrait et définit les propriétés de configuration|  
|TransactionalReceiver.cs|Crée et gère les points de terminaison de réception|  
|TransactionalReceiverEndpoint.cs|Écoute réelle ou interrogation pour chaque emplacement de réception|  
|TransactionalTransmitter.cs|Accepte un lot de messages du moteur de messagerie à transmettre|  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Cet exemple est conçu comme une infrastructure que vous utilisez pour créer des adaptateurs d'envoi et de réception personnalisés à l'aide de transactions explicites.  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
> [!IMPORTANT]
>  Si l'installation BizTalk est 64 bits ou si son emplacement a été modifié, les valeurs OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath doivent être modifiées en conséquence.  
  
#### <a name="create-a-strong-name-key-for-the-transactional-adapter-sample"></a>Créer une clé de nom fort de l’exemple d’adaptateur transactionnel  
  
1.  Démarrer **invite de commandes Visual Studio**.  
  
2.  À l'invite de commandes, tapez la commande suivante, puis appuyez sur Entrée :  
  
    ```  
    cd \Program Files\Microsoft BizTalk Server <version>\SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Runtime  
    ```  
  
3.  À l'invite de commandes, tapez la commande suivante, puis appuyez sur Entrée :  
  
    ```  
    sn –k TransactionalAdapter.snk  
    ```  
  
4.  À l’invite de commandes, tapez **quitter**, puis appuyez sur ENTRÉE pour fermer la fenêtre d’invite de commandes.  
  
#### <a name="build-the-transactional-adapter-solution"></a>Générez la Solution d’adaptateur transactionnel  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\AdaptersDevelopment\TransactionalAdapter, puis double-cliquez sur **TransactionalAdapter.sln** pour ouvrir cette solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
3.  Pour générer les deux projets d’adaptateur transactionnel (Admin et Runtime) dans l’Explorateur de solutions, cliquez sur **Solution d’adaptateur transactionnel**, puis cliquez sur **reconstruire**.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="register-the-transactional-adapter"></a>Inscrire l’adaptateur transactionnel  
  
1.  Dans l'Explorateur Windows, accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] SDK\Samples\AdaptersDevelopment\TransactionalAdapter\Admin.  
  
2.  Pour ajouter les données de l’adaptateur transactionnel au Registre, double-cliquez sur **TransactionalAdmin.reg**.  
  
    > [!NOTE]
    >  **TransactionalAdmin.reg** inclut des chemins codés en dur vers C:\Program Files\Microsoft BizTalk Server\\. Si vous n'avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'emplacement par défaut ou si vous avez mis à niveau votre installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une version antérieure, vous devez modifier le fichier TransactionalAdmin.reg en y indiquant les chemins d'accès appropriés. Mettez à jour les chemins d'accès associés aux valeurs « InboundAssemblyPath », « OutboundAssemblyPath » et « AdapterMgmtAssemblyPath » afin qu'ils pointent vers l'emplacement correct des fichiers spécifiés.  
  
    > [!IMPORTANT]
    >  Si vous installez BizTalk sur un ordinateur 64 bits, modifiez toutes les instances de l’entrée de Registre HKEY_CLASSES_ROOT\CLSID\ à HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ dans le **TransactionalAdmin.reg** fichier de Registre.  
  
3.  Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK**.  
  
4.  Pour fermer l’Explorateur Windows, cliquez sur **fichier**, puis cliquez sur **fermer**.  
  
#### <a name="add-the-transactional-adapter-to-biztalk-server"></a>Pour ajouter l'adaptateur transactionnel à BizTalk Server  
  
1.  Cliquez sur le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez **Administration de BizTalk Server**.  
  
2.  Dans le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le **Administration de BizTalk Server** d’arborescence, développez le **groupe BizTalk** d’arborescence, puis cliquez sur le **paramètres de plateforme** arborescence.  
  
3.  Avec le bouton droit **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.  
  
4.  Dans le **propriétés de l’adaptateur** boîte de dialogue zone, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Nom|Type **TransactionalAdapter**.|  
    |Adaptateur|Sélectionnez **Txn** dans la liste déroulante. Cette entrée apparaît à la suite en cours d’exécution le **TransactionalAdmin.reg** fichier précédemment.|  
    | Description|Type **exemple adaptateur transactionnel**.|  
  
5.  Cliquez sur **OK.** L'adaptateur apparaît dans la liste des adaptateurs, dans la fenêtre droite de la console Administration de BizTalk.  
  
#### <a name="create-a-receive-port-and-location-that-uses-the-adapter"></a>Pour créer un port de réception et un emplacement qui utilise l'adaptateur  
  
1.  Développez le **le groupe BizTalk [nom serveur]** nœud [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **Applications** nœud, développez **BizTalk Application 1** nœud.  
  
2.  Avec le bouton droit **Ports de réception**, puis cliquez sur **nouveau**, sélectionnez **Port de réception unidirectionnel.**  
  
3.  Pour **nom**, entrez **TxnReceivePort1**, puis cliquez sur **OK**.  
  
4.  Avec le bouton droit le **emplacements de réception** nœud, cliquez sur **nouveau**, puis sélectionnez **emplacement de réception unidirectionnel**.  
  
5.  Dans le**sélectionner un Port de réception** boîte de dialogue, sélectionnez **TxnReceivePort1**, puis cliquez sur **OK**.  
  
6.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue, sous le **général** , entrez **TxnReceiveLocation1** pour **nom**. Vérifiez le **Port de réception** étiquette affiche **TxnReceivePort1**.  
  
7.  Dans le**Type** zone, de liste déroulante dans le **Transport** frame, sélectionnez **TransactionalAdapter.**  
  
8.  Dans le **réception *** Pipeline** zone, vérifiez que **PassThruReceive** est sélectionnée. Conservez les paramètres par défaut pour les propriétés restantes.  
  
9. Cliquez sur le **configurer** situé en regard du **Type** zone déroulante. Cela permet d'afficher une boîte de dialogue spécifique à cet adaptateur. Spécifiez les éléments suivants si nécessaire, puis cliquez sur **OK**.  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |Chaîne de connexion|Chaîne de connexion à la base de données SQL utilisée pour la connexion et l'authentification auprès de la base de données Northwind. Nous exécuterons ultérieurement un script SQL qui utilisera cette base de données.|  
    |Texte de la commande|Instructions SQL exécutées sur la base de données Northwind pour obtenir des données à placer dans un message BizTalk.|  
    |Cookie|Comprend une partie de l'URI. Entrez une valeur unique, telle que le nom de l'emplacement de réception ; par exemple, TxnReceiveLocation1.|  
    |Unité intervalle d'interrogation|Nombre d'unités de mesure de temps pour l'interrogation des données. Définissez cette propriété sur secondes.|  
    |Intervalle d’interrogation|Unité de mesure de temps pour l'interrogation des données. Définissez cette propriété sur 15 secondes.|  
  
10. Cliquez sur **OK** pour fermer la boîte de dialogue Configurer, puis **OK** à nouveau pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue pour revenir à la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
#### <a name="create-a-send-port-and-send-handler-that-use-the-adapter"></a>Pour créer un port d'envoi et un gestionnaire d'envoi qui utilisent l'adaptateur  
  
1.  Avec la **BizTalk Application 1** toujours le nœud développé, cliquez sur **Ports d’envoi**, puis cliquez sur **nouveau**, puis sélectionnez **statique Port d’envoi unidirectionnel**.  
  
2.  Dans le **nom** , entrez **TxnSendPort1**.  
  
3.  Dans le **Transport** frame, dans le **Type** la liste déroulante, sélectionnez**TransactionalAdapter**`.`  
  
4.  Dans le **Pipeline d’envoi** zone, vérifiez que **PassThruTransmit** est sélectionnée.  
  
5.  Cliquez sur le **configurer** situé en regard du **transport** liste déroulante. Dans la boîte de dialogue qui s’affiche, spécifiez les éléments suivants si nécessaire, puis cliquez sur **OK**.  
  
    |Propriété|Paramètre|  
    |--------------|-------------|  
    |Cookie|Comprend une partie de l’URI - Entrez une valeur unique comme le nom de l’emplacement de réception pour l’instance : **TxnSendPort1**.|  
    |Chaîne de connexion|Chaîne de connexion à la base de données SQL utilisée pour la connexion et l'authentification auprès de la base de données Northwind. Il s’agira probablement le même que celui utilisé pour configurer le **TxnReceiveLocation1** emplacement de réception.|  
    |Procédure stockée|Le nom de procédure stockée exécuté pour interroger la base de données - **sp_txnProc**. Le corps du message est transmis à que BizTalk de procédure stockée comme paramètre de chaîne appelé @Data. Par exemple, l’utilisateur dans ce cas plus tard configurera la procédure stockée avec le nom **sp_txnProc**. L'exécution de l'adaptateur exécuterait l'équivalent de cet appel à la base de données.<br /><br /> EXEC sp_txnProc @Data = « le contenu du message BizTalk »|  
  
6.  Dans le volet de navigation gauche, cliquez sur **filtre**.  
  
7.  Dans l'éditeur d'expression de filtre, entrez l'expression suivante pour définir un abonnement à ce port d'envoi et obtenir les messages reçus par le port de réception TxnReceivePort1.  
  
     Entrez ces valeurs :**BTS. ReceivePortName == TxnReceivePort1**  
  
    1.  `(property)`  **BTS.ReceivePortName**  
  
    2.  `(operator)`  **==**  
  
    3.  `(value)`  **TxnReceivePort1**  
  
8.  Utilisez les valeurs par défaut pour le reste des propriétés de l’adaptateur et sélectionnez **OK**.  
  
## <a name="run-the-sample"></a>Exécuter l'exemple  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2008 R2**, sélectionnez **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue zone, assurez-vous que **Type de serveur** a la valeur **moteur de base de données**, entrez les informations d’identification pour s’authentifier auprès du serveur de base de données, puis sélectionnez  **Se connecter**.  
  
3.  Sélectionnez le **nouvelle requête** bouton de barre d’outils et collez le code suivant dans la nouvelle fenêtre de requête pour insérer une table de test, les données de test et un test de procédure stockée dans la base de données Northwind. Sélectionnez le **Execute** bouton de barre d’outils.  
  
    ```  
    use [Northwind]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[scratch]') and OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    drop table [dbo].[scratch]  
    GO  
    CREATE TABLE [dbo].[scratch] (  
         [id] [int] IDENTITY (1, 1) NOT NULL ,  
         [msg] [nvarchar] (4000) NOT NULL   
    ) ON [PRIMARY]  
    GO  
    GRANT SELECT , UPDATE , INSERT ON [dbo].[scratch] TO [public]  
    GO  
    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[sp_txnProc]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[sp_txnProc]  
    GO  
    CREATE PROCEDURE [dbo].[sp_txnProc] @Data nvarchar (4000)  
    AS   
    INSERT scratch ( msg ) values ( @Data )  
    GO  
    GRANT EXECUTE ON [dbo].[sp_txnProc] TO [public]  
    GO  
    ```  
  
4.  Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le **Ports d’envoi** nœud, sélectionnez le **TxnSendPort1** port d’envoi, puis sélectionnez **Démarrer**.  
  
5.  Dans [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le **ReceiveLocations** nœud, sélectionnez le **TxnRecieveLocation1** emplacement de réception, puis sélectionnez **activer**.  
  
6.  Une fois l'emplacement de réception activé, il interroge automatiquement la base de données aux intervalles définis pour obtenir des données.  
  
## <a name="classes-or-methods-used-in-the-sample"></a>Classes ou méthodes utilisées dans l’exemple  
* Interface IBTTransmitterBatch (COM)
  
* Interface IBTTransportProxy (COM)

Ces méthodes sont décrites [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs - développement](../core/adapter-samples-development.md)   
 [Inscription d’un adaptateur](../core/registering-an-adapter.md)