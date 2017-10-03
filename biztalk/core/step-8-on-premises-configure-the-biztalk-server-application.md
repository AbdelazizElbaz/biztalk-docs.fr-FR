---
title: "Étape 8 (en local) : Configurer l’Application BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 2015-12-08
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5109fb54-8453-444f-bc9c-070a65053397
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47332edbf974b7e45d3ab65644f28d9d2bd6a623
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-on-premises-configure-the-biztalk-server-application"></a>Étape 8 (en local) : Configurer l’Application BizTalk Server
Lors de l’étape précédente, vous avez créé une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans cette étape, vous allez générer, déployer et configurer l’application.  
  
## <a name="build-and-deploy-the-application"></a>Créer et déployer l'application  
  
1.  Dans Visual Studio, cliquez sur le nom de la solution dans l’Explorateur de solutions, puis cliquez sur **Build**.  
  
2.  Le processus de déploiement requiert la signature avec un nom fort de l'assembly.  Vous devez vous connecter à vos assemblys en associant le projet avec un fichier de clé de nom fort assembly.  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le **OrderProcessingDemo** de projet, puis cliquez sur **propriétés**.  
  
    2.  Cliquez sur le **signature** et sélectionnez le **signer l’assembly** case à cocher.  
  
    3.  Dans la liste déroulante de la **choisir un fichier de clé de nom fort** boîte, sélectionnez  **\<nouveau... >**.  
  
    4.  Dans le **créer une clé de nom fort** boîte de dialogue, entrez un nom pour le fichier de clé, par exemple `OrderProcessingDemo.snk`. Désactivez la case à cocher pour protéger le fichier de clé avec un mot de passe, puis cliquez sur **OK**.  
  
3.  Cliquez sur le **déploiement** onglet, dans la zone à droite de **nom de l’Application**, type `OrderProcessingDemo`.  
  
4.  Dans la liste déroulante dans la zone à droite de **redéployer**, sélectionnez **True**.  
  
5.  Dans l’Explorateur de solutions, cliquez sur **OrderProcessingDemo**, puis cliquez sur **déployer**.  La fenêtre Sortie doit s'afficher :  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
## <a name="configure-the-application"></a>Configurez l'application  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]** , puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].  
  
2.  Dans l’arborescence de la console, dans le volet gauche, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.  
  
3.  Développez **groupe BizTalk**, développez **Applications**, développez **OrderProcessingDemo**, puis cliquez sur **Orchestrations**. Vous verrez que le **OrderProcessingDemo.OrderProcessing** orchestration est déployée.  
  
4.  Dans l’orchestration, vous avez créé un port logique (**ReceiveSO**) pour recevoir des messages à partir de la file d’attente du Bus de Service. Dans cette étape, vous allez créer un port de réception physique à mapper vers le port logique.  
  
    1.  À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **OrderProcessingDemo** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.  
  
    2.  Sous l'onglet **Général** , effectuez les paramétrages suivants :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Type **ReceiveSO**.|  
        |**Activer le routage des messages ayant échoué**|(désactivé)|  
  
    3.  Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.  
  
    4.  Dans la boîte de dialogue Emplacement de réception 1 - Propriétés d’emplacement de réception, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Type **ReceiveOrders_SO**.|  
        |**Type**|Sélectionnez **SB-Messaging**.|  
        |**Gestionnaire de réception**|Sélectionnez **BizTalkServerApplication**.|  
        |**Pipeline de réception**|Sélectionnez **XMLReceive**.|  
  
    5.  Cliquez sur **configurer**.  
  
    6.  À partir de la boîte de dialogue Propriétés du Transport SB-Messaging, sur le **général** onglet, pour **file d’attente ou abonnement URL**, entrez **sb://mynamespace.servicebus.appfabriclabs.com/queueordersedi** . Ici, *mynamespace* est l’espace de noms Service Bus et *file_attente_commandes_edi* est la file d’attente du Bus de Service que vous avez créé dans [étape 3 (pour Azure) : créer une file d’attente du Bus de Service](../core/step-3-for-azure-create-a-service-bus-queue.md).  
  
    7.  À partir de la boîte de dialogue Propriétés du Transport SB-Messaging, sur le **authentification** onglet, spécifiez les valeurs suivantes :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**STS Uri de Service de contrôle d’accès**|Type`https://mynamespace-sb.accesscontrol.appfabriclabs.com/`|  
        |**Nom de l’émetteur**|Spécifiez le nom de l’émetteur. En général, il est défini sur `owner`.|  
        |**Clé de l’émetteur**|Spécifiez la clé de l’émetteur.|  
  
        > [!NOTE]
        >  Vous pouvez obtenir les valeurs de l’émetteur de l’URL de la file d’attente, les URL des services ACS, nom et la clé à partir de la [portail de gestion Windows Azure CTP](http://go.microsoft.com/fwlink/p/?LinkId=202886).  
  
    8.  Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.  
  
5.  Dans l’orchestration, vous avez créé un port logique (**SendToSQL**) pour envoyer des messages à la **SalesOrder** table de base de données. Dans cette étape, vous allez créer un port d’envoi physique à mapper vers le port logique.  
  
    1.  À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **OrderProcessingDemo** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
    2.  Sous l’onglet Général, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Type **SendToSQL**.|  
        |**Type**|Sélectionnez **WCF-SQL**.|  
        |**Gestionnaire d’envoi**|Sélectionnez **BizTAlkServerApplication**.|  
        |**Pipeline d’envoi**|Sélectionnez **PassThruTransmit**.|  
  
    3.  Cliquez sur **configurer**.  
  
    4.  À partir des propriétés du Transport WCF-SQL, sur le **général** onglet, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Adresse (URI)**|Type **MSSQL://Nom_Ordinateur/nom_instance_base_de_donn ées/nom_base_de_données**. Par exemple, pour se connecter à un **DemoDB** de la base de données sur l’ordinateur local en cours d’exécution sous l’instance de base de données par défaut, entrez`mssql://.//DemoDB`<br /><br /> Pour plus d’informations, consultez [créer l’URI de connexion SQL Server](../adapters-and-accelerators/adapter-sql/create-the-sql-server-connection-uri.md).|  
        |**Action**|Type **TableOp/Insert/dbo/SalesOrder**.|  
  
    5.  À partir des propriétés du Transport WCF-SQL, sur le **informations d’identification** onglet, sélectionnez **n’utilisez pas l’authentification unique sur**et spécifiez les informations d’identification (respecte la casse) pour se connecter à SQL Server de base de données spécifiée dans la chaîne de connexion. Si vous souhaitez vous connecter à l’aide de l’authentification Windows, ne renseignez pas les informations d’identification.  
  
    6.  Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.  
  
6.  Dans l’orchestration, vous avez créé un port logique (**SendToFile**) pour envoyer des messages vers un emplacement de fichier partagé. Dans cette étape, vous allez créer un port d’envoi physique à mapper vers le port logique.  
  
    1.  À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la Console, sous le **OrderProcessingDemo** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.  
  
    2.  Sous l’onglet Général, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Nom**|Type **SendToFile**.|  
        |**Type**|Sélectionnez **fichier**.|  
        |**Gestionnaire d’envoi**|Sélectionnez **BizTAlkServerApplication**.|  
        |**Pipeline d’envoi**|Sélectionnez **XML Transmit**.|  
  
    3.  Cliquez sur **configurer**.  
  
    4.  Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |**Dossier de réception**|Spécifier l’emplacement dans lequel vous souhaitez envoyer le message.|  
        |**Nom de fichier**|Conserver **%MessageID%.xml**.|  
  
    5.  Cliquez sur **OK** jusqu'à ce que vous quittiez toutes les boîtes de dialogue.  
  
7.  Pour configurer l’application, vous devez maintenant lier le port logique et le port physique.  
  
    1.  À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **OrderProcessingDemo**, puis cliquez sur **configurer**.  
  
    2.  Configurer l’application, dans le volet gauche, cliquez sur **OrderProcessing**.  
  
    3.  Utilisez les valeurs du tableau suivant pour configurer l’application.  
  
        |Utiliser|Pour effectuer cette opération|  
        |--------------|----------------|  
        |Pour **hôte**|Sélectionnez **BizTalkServerApplication**|  
        |Port logique **ReceiveSO**|Sélectionner le port physique **ReceiveSO**|  
        |Port logique **SendToSQL**|Sélectionner le port physique **SendToSQL**|  
        |Port logique **SendToFile**|Sélectionner le port physique **SendToFile**|  
  
    4.  Cliquez sur **OK** pour enregistrer la configuration.  
  
## <a name="start-the-application"></a>Démarrer l’application  
  
1.  À partir de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, avec le bouton droit **OrderProcessingDemo**, puis cliquez sur **Démarrer**.  
  
2.  Dans la boîte de dialogue, cliquez sur **Démarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 4 : Création d’une Application hybride à l’aide de BizTalk Server 2013](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)