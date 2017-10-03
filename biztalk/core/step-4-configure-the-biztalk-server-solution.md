---
title: "Étape 4 : Configurer la Solution BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d60e6a82-51af-41e5-a755-5f337492ba2f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6587e0a8ff84b352ba6f029a7687139daabb72a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-the-biztalk-server-solution"></a>Étape 4 : Configurer la Solution BizTalk Server
Dans l'étape précédente, vous avez créé et déployé une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour recevoir une notification de Salesforce dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et insérer les détails dans une base de données SQL Server sur site. Dans cette étape, nous allons configurer l'application dans la console d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. La configuration de l'application consiste principalement à créer des ports physiques correspondant aux ports logiques que nous avons créés dans l'orchestration. Il s'agit aussi de lier le port physique aux ports logiques. Nous allons effectuer les étapes suivantes pour configurer l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   Configurer un emplacement de réception de requête-réponse WCF-BasicHttpRelay pour recevoir des notifications d'opportunité de Salesforce.  
  
-   Configurer un port d'envoi de requête-réponse WCF-WebHttp pour envoyer des requêtes à Salesforce afin de récupérer des détails du produit relatives à la notification d'opportunité reçue. Ce port d'envoi reçoit également la réponse à la requête de Salesforce.  
  
-   Configurer un port d'envoi unidirectionnel WCF-SQL pour insérer la réponse à la requête de Salesforce dans une base de données SQL Server sur site.  
  
-   Configurer l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en associant le port logique dans l'orchestration aux ports physiques créés dans la console d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-configure-the-wcf-basichttprelay-receive-location"></a>Pour configurer l'emplacement de réception WCF-BasicHttpRelay  
  
1.  Ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Développez le nœud Applications et recherchez le **SalesforceIntegration** application. L'application est créée quand vous déployez le projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir de Visual Studio.  
  
2.  Développez le **SalesforceIntegration** application, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception requête-réponse**. Spécifiez le nom de port `ReceiveOppNotification` et dans le volet gauche, cliquez sur **emplacements de réception**.  
  
3.  Dans la boîte de dialogue Propriétés d'emplacement de réception, spécifiez les valeurs suivantes :  
  
    |||  
    |-|-|  
    |Nom|Entrez `ReceiveOppNotification`.|  
    |Type|Sélectionnez **WCF-BasicHttpRelay**|  
    |Gestionnaire de réception|Sélectionnez **BizTalkServerApplication**|  
    |Pipeline de réception|Sélectionnez **XMLReceive**|  
    |Pipeline d'envoi|Sélectionnez **PassThruTransmit**|  
  
     Cliquez sur **configurer** pour le type de port.  
  
4.  Dans la boîte de dialogue Propriétés du transport WCF-BasicHttpRelay, spécifiez les valeurs suivantes :  
  
    1.  Sur le **général** onglet, pour **adresse (URI)**, entrez `https://btssalesforce.servicebus.windows.net/notifications/opportunity`. Ici, **btssalesforce** est créé à l’espace de noms [étape 1 : créer un Namespace de Bus de Service](../core/step-1-create-a-service-bus-namespace.md). L’URL que vous spécifiez ici est la même URL que vous avez spécifié lors de la création d’un workflow dans Salesforce dans [étape 2 : configurer le système Salesforce](../core/step-2-set-up-the-salesforce-system.md). Permet de paramétrer un flux de travail dans lequel chaque fois que l’étape de l’opportunité est défini sur fermées/gagnées, Salesforce envoie une notification à l’URL *https://btssalesforce.servicebus.windows.net/notifications/opportunity*. Nous spécifions la même URL ici dans le cadre de cette configuration d'emplacement de réception. Lorsque l'emplacement de réception est activé, le point de terminaison de relais spécifié par l'URL est créé dans [!INCLUDE[winazure](../includes/winazure-md.md)].  
  
    2.  Sur le **sécurité** onglet, spécifiez les éléments suivants :  
  
        -   Pour **mode de sécurité**, sélectionnez **Transport** et **type d’authentification client de relais**, sélectionnez **aucun**.  
  
        -   Sélectionnez le **activer la découverte du service** case à cocher pour publier le comportement de service dans le [Registre du Service](http://msdn.microsoft.com/library/windowsazure/dd582704.aspx). Spécifiez le **nom d’affichage** qui désigne le nom sous lequel le service est publié dans le Registre. Vous pouvez définir le **mode de découverte** sur public ou privé. Pour ce didacticiel, définissez **nom d’affichage** à `SF Outbound Notification` et **mode de découverte** à **Public**.  
  
        -   Dans la zone de service de contrôle de l’accès, cliquez sur **modifier**. Pour **Uri STS Service de contrôle d’accès**, entrez `https://btssalesforce-sb.accesscontrol.windows.net/`. Pour **nom de l’émetteur** et **clé d’émetteur**, entrez les valeurs que vous avez enregistré dans [étape 1 : créer un Namespace de Bus de Service](../core/step-1-create-a-service-bus-namespace.md) pour **utilisateur par défaut** et **Clé par défaut** champs.  
  
    3.  Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.  
  
### <a name="to-configure-the-wcf-webhttp-send-port"></a>Pour configurer le port d’envoi WCF-WebHttp  
  
1.  Développez le **SalesforceIntegration** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
2.  Dans la boîte de dialogue Propriétés de port d'envoi, spécifiez les valeurs suivantes :  
  
    |||  
    |-|-|  
    |Nom|Entrez `SalesforceREST`.|  
    |Type|Sélectionnez **WCF-WebHttp**|  
    |Gestionnaire d’envoi|Sélectionnez **BizTalkServerApplication**|  
    |Pipeline d'envoi|Sélectionnez **PassThruTransmit**|  
    |Pipeline de réception|Sélectionnez **AddNamespace** et cliquez sur le bouton de sélection sur le pipeline pour configurer le pipeline.<br /><br /> -Sous **étape 1 : décoder**, pour **NamespaceBase**, entrez `http://BtsSalesforceIntegration.QueryResult`. Il s’agit du schéma QueryResult.xsd que vous avez créé dans l’espace de noms [étape 3 b : récupérer les détails d’opportunité de Salesforce à l’aide de l’adaptateur WCF-WebHttp](../core/step-3b-retrieve-opportunities-from-salesforce-using-the-wcf-webhttp-adapter.md). Lorsque le **AddNamespace** réception pipeline reçoit la réponse de Salesforce, il ajoute cet espace de noms au message de réponse. Par défaut, le message de réponse de Salesforce n'inclut aucun espace de noms.<br />     Pour **NamespacePrefix**, entrez `sf`.<br />-Sous **phase 2 : désassembler**, acceptez les valeurs par défaut, puis sur **OK**.|  
  
     Dans la boîte de dialogue Propriétés de Port d’envoi, cliquez sur **configurer** pour le type de port.  
  
3.  Dans la boîte de dialogue Propriétés du transport WCF-WebHttp, spécifiez les valeurs suivantes :  
  
    1.  Sous l'onglet **Général** , effectuez les paramétrages suivants :  
  
        -   pour **adresse (URI)**, entrez `https://<Salesforce_instance_name>.salesforce.com/services/data/v24.0`. Vous pouvez récupérer le nom de l'instance Salesforce en copiant le texte entre https:// et Salesforce.com dans la barre d'adresse où le portail Salesforce.com est ouvert. Par exemple, si l’URL dans le portail Salesforce est *https://**na15**.salesforce.com/home/home.jsp*, le nom d’instance Salesforce est **na15**.  
  
        -   Sous **méthode HTTP et mappage d’URL** , spécifiez les éléments suivants :  
  
            ```  
            <BtsHttpUrlMapping>  
            <Operation Method="GET" Url="/query?q={VAR}" />  
            </BtsHttpUrlMapping>  
            ```  
  
             Voici comment ce paramètre est utilisé, pour interroger Salesforce pour récupérer plus d’informations sur la notification d’opportunité, nous devons effectuer une opération GET sur le point de terminaison REST de Salesforce (spécifié dans le **adresse** champ) et ajouter le requête pour récupérer les détails de l’opportunité. L'URL doit donc être de type :  
  
            ```  
            https://na15.salesforce.com/services/data/v24.0/query?q=<query_string>  
            ```  
  
             Nous avons déjà le point de terminaison REST de Salesforce dans le cadre de la **adresse (URI)** champ. Par conséquent, dans le cadre de **méthode HTTP et mappage d’URL** propriété, nous spécifions à l’aide de la méthode GET et en ajoutant le **{VAR}** en tant que variable.  
  
        -   Dans le **mappage de la Variable** , cliquez sur **modifier**. Dans cette zone, vous spécifiez comment la valeur de la **{VAR}** variable est déduite lors de l’exécution.  
  
             Dans [étape 3 b : récupérer les détails d’opportunité de Salesforce à l’aide de l’adaptateur WCF-WebHttp](../core/step-3b-retrieve-opportunities-from-salesforce-using-the-wcf-webhttp-adapter.md), nous avions promu la propriété de requête, ce qui a entraîné la création d’un **PropertySchema.xsd**. Nous allons utiliser la **requête** élément dans ce schéma pour passer la chaîne de requête en mappant cet élément à la variable {VAR} dans l’URL.  
  
             Dans la boîte de dialogue mappage de la Variable, le **Variable** colonne répertorie le nom de la variable que vous avez spécifié précédemment, par exemple, **VAR**. Dans le **nom de la propriété** colonne, spécifiez le nom de la propriété promue qui comporte la chaîne de requête à passer à la variable. Dans ce didacticiel, le nom de cette propriété est **requête**. Enfin, pour **propriété Namespace**, spécifiez l’espace de noms pour le **PropertySchema.xsd**, qui est `https://BtsSalesforceIntegration.PropertySchema`. Cliquez sur **OK**.  
  
             ![Onglet Général de WCF &#45; Adaptateur WebHttp](../core/media/bts-sf-webhttp-general.jpg "BTS_SF_WebHttp_General")  
  
    2.  Sur le **sécurité** onglet, pour **mode de sécurité**, sélectionnez **Transport**.  
  
    3.  Sur le **comportement** onglet, utilisez le comportement personnalisé que vous avez créé dans [étape 3d : l’activation de BizTalk Server pour envoyer et recevoir des Messages de Salesforce](../core/step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce.md) pour s’authentifier auprès de Salesforce. Pour utiliser le comportement, procédez comme suit :  
  
        -   Avec le bouton droit **EndpointBehavior** , puis sélectionnez **ajouter une extension**.  
  
        -   Dans le **sélectionner une Extension de comportement** boîte de dialogue, sélectionnez **Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce**. Nous avions utilisé ce nom de comportement tout en ajoutant le comportement à la machine.config.  
  
        -   Sélectionnez le comportement nouvellement ajouté puis spécifiez les valeurs suivantes :  
  
            |||  
            |-|-|  
            |consumerKey (obligatoire)|Spécifiez la clé utilisateur de votre compte Salesforce. Vous pouvez récupérer la clé de consommateur en accédant à l’application Salesforce connectée que vous avez créé dans [étape 2 : configurer le système Salesforce](../core/step-2-set-up-the-salesforce-system.md).|  
            |consumerSecret (obligatoire)|Récupérer la question secrète de la force de vente connecté l’application que vous avez créé dans [étape 2 : configurer le système Salesforce](../core/step-2-set-up-the-salesforce-system.md).|  
            |Mot de passe (obligatoire)|Indiquer le mot de passe du compte Salesforce. Pour vous connecter à Salesforce à partir d'une application tierce, vous devez indiquer le mot de passe dans le format mot de passe suivi par le jeton de sécurité. Par exemple, si le mot de passe est **mot de passe** et le jeton est **XXXXXX**, vous devez entrer `passwordXXXXXX`.|  
            |sessionTimeout|Ceci a la valeur par défaut 300.|  
            |Username (obligatoire)|Spécifiez le compte de connexion du développeur Salesforce.|  
  
             ![Onglet comportement pour WCF &#45; Adaptateur WebHttp](../core/media/bts-sf-webhttp-behavior.jpg "BTS_SF_WebHttp_Behavior")  
  
    4.  Sur le **Messages** sous l’onglet sous **Message sortant** boîte pour **supprimer le corps en fonction de verbes**, entrez `GET`. Ainsi, pour la méthode GET, il n'y a pas de charge du message dans la requête envoyée à Salesforce.  
  
    5.  Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.  
  
### <a name="to-configure-the-wcf-sql-send-port"></a>Pour configurer le port d’envoi WCF-SQL  
  
1.  Développez le **SalesforceIntegration** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **statique Port d’envoi unidirectionnel**.  
  
2.  Dans la boîte de dialogue Propriétés de port d'envoi, spécifiez les valeurs suivantes :  
  
    |||  
    |-|-|  
    |Nom|Entrez `SendToSQL`.|  
    |Type|Sélectionnez **WCF-SQL**|  
    |Gestionnaire d’envoi|Sélectionnez **BizTalkServerApplication**|  
    |Pipeline d'envoi|Sélectionnez **XMLTransmit**|  
  
     Dans la boîte de dialogue Propriétés de Port d’envoi, cliquez sur **configurer** pour le type de port.  
  
3.  Dans la boîte de dialogue Propriétés du transport WCF-SQL, spécifiez les valeurs suivantes :  
  
    1.  Sous l'onglet **Général** , effectuez les paramétrages suivants :  
  
        -   Sous `Endpoint Address`, cliquez sur **configurer**. Pour le **InitialCatalog** propriété, spécifiez le nom de la base de données qui contient la table où les données à partir de la réponse de Salesforce doivent être entrées. Pour ce didacticiel, entrez la valeur `Orders`. Pour **Server** propriété, entrez le nom du serveur sur lequel la base de données SQL Server est installé.  
  
        -   Sous **en-tête d’Action SOAP**, indiquez l’action à être utilisée pour insérer dans le **OrderDetails** table. Vous devez entrer `TableOp/Insert/dbo/OrderDetails`.  
  
    2.  Sous l'onglet Informations d'identification, si vous laissez tout en blanc, l'adaptateur utilise l'authentification Windows pour se connecter à la base de données SQL Server. Si vous voulez utiliser une autre forme d'authentification, vous pouvez spécifier les valeurs correspondantes.  
  
    3.  Cliquez sur **OK** jusqu'à ce que vous quittez toutes les boîtes de dialogue Ouvrir.  
  
### <a name="to-configure-the-biztalk-server-application"></a>Pour configurer l'application BizTalk Server  
  
1.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit le **SalesforceIntegration** application, puis sur **configurer**.  
  
2.  Dans la boîte de dialogue Configurer l’Application, sélectionnez le **NotificationServiceClient** orchestration, dans le volet droit, procédez comme suit :  
  
    1.  Pour l’ordinateur hôte, sélectionnez **BizTalkServerApplication**.  
  
    2.  Port de réception de la logique de la carte **SalesforceNotificationPort** jusqu’au port de réception, **ReceiveOppNotification**.  
  
    3.  Mappez le port d’envoi logique **SalesforceRESTInterface** jusqu’au port d’envoi, **SalesforceREST**.  
  
    4.  Mappez le port d’envoi logique **SendToSQL** jusqu’au port d’envoi, **SendToSQL**.  
  
     Cliquez sur **OK**.  
  
3.  Cliquez sur le **SalesforceIntegration** application, puis sur **Démarrer**. Cela démarre le **NotificationServiceClient** orchestration, permet à l’emplacement de réception et démarre le port d’envoi.  
  
 Dans cette rubrique, nous avons effectué la configuration de la solution dans la console d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en associant les ports logiques dans l'orchestration avec les ports physiques.