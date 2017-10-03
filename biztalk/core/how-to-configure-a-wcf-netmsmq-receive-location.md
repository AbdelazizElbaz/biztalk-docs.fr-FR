---
title: "Pour configurer les emplacement de réception WCF-NetMsmq | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82b323b-9870-42fb-9992-c23dca909b4d
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16491259826159f18791e35efb226dd159c12c27
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netmsmq-receive-location"></a>Configuration d'un emplacement de réception WCF-NetMsmq
Vous pouvez configurer un emplacement de réception WCF-NetMsmq par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuratin-properties"></a>Propriétés Configuratin
  
 Le modèle objet de l'Explorateur BizTalk permet de créer et de configurer les emplacements de réception par programme. Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception WCF-NetMsmq sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.  
  
 Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. Dans ce cas, l'adaptateur WCF-NetMsmq utilise les valeurs par défaut pour la configuration de l'emplacement de réception WCF-NetMsmq, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception WCF-NetMsmq.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identité&gt;<br /><br /> &lt;valeur d’userPrincipalName = «username@contoso.com» /&gt;<br /><br /> &lt;/Identity&gt;|Spécifiez l'identité du service fourni par cet emplacement de réception. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité. Ces paramètres permettent au client d'authentifier cet emplacement de réception. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> Valeur par défaut : 65536|  
|**EnableTransaction**|Booléen|Spécifier le type de file d'attente des messages : transactionnelle ou non transactionnelle. Si cette propriété est sélectionnée, chaque message est remis une seule fois et l'expéditeur est notifié des échecs de remise. Pour envoyer des messages via l’envoi transactionnel des ports, les deux le **durables** et **exactlyOnce** éléments du client de liaison doit être définie sur **True**. Si cette propriété est désactivée, les messages sont transférés sans garantie de remise. **Remarque :** si vous utilisez une file d’attente transactionnelle sous cet emplacement de réception, cette propriété doit être sélectionnée. <br /><br /> Valeur par défaut : **False**|  
|**OrderedProcessing**|Booléen|Spécifier si vous voulez traiter les messages par séries. Lorsque cette propriété est activée, cet emplacement de réception livraison chronologique des messages lorsqu’il est utilisé conjointement avec une orchestration ou la messagerie port d’envoi BizTalk a prend en charge la **livraison chronologique des messages** option définie sur `True`. Vous pouvez sélectionner cette uniquement lorsque le **EnableTransaction** est définie sur **True**.<br /><br /> Pour plus d’informations sur la **livraison chronologique des messages** option, consultez les rubriques correspondantes dans la section Voir aussi.<br /><br /> Lorsque cette propriété a la valeur **True**, emplacement de réception WCF-NetMsmq optimise l’utilisation des ressources lors du traitement des messages volumineux en rendant l’adaptateur monothread.<br /><br /> Valeur par défaut : **False**|  
|**Maxconcurrentcalls.**|Entier|Spécifier le nombre d'appels simultanés par instance de service unique. Les appels excédentaires sont mis en file d'attente. La plage de cette propriété est comprise entre 0 et **Int32.MaxValue**.<br /><br /> Valeur par défaut : 200|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**<br />-   **Message**<br />-   **Transport**<br />-   **Les deux**<br /><br /> Pour plus d’informations sur les noms de membre pour le **SecurityMode** propriété, consultez le **mode de sécurité** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-NetMsmq, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **Transport**|  
|**MsmqAuthenticationMode**|Enum<br /><br /> -   **Aucun**<br />-   **WindowsDomain**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MsmqAuthenticationMode** propriété, consultez le **mode d’authentification MSMQ** propriété dans le **boîte boîte de dialogue Propriétés du Transport WCF-NetMsmq, Sécurité, de réception** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifiez le mode d'authentification du message par le transport MSMQ.<br /><br /> Valeur par défaut : **WindowsDomain**|  
|**MsmqProtectionLevel**|Enum<br /><br /> -   **Aucun**: aucune protection.<br />-   **Signe**: les Messages sont signés.<br />-   **EncryptAndSign**: les Messages sont chiffrés et signés. Pour utiliser ce niveau de protection, vous devez activer **l’intégration Active Directory** pour **MSMQ**.|Spécifier le mode de sécurisation des messages au niveau du transport MSMQ. Le chiffrement garantit l'intégrité des messages, tandis que la signature et le chiffrement assurent l'intégrité et la non-répudiation des messages.<br /><br /> Valeur par défaut : **signe**|  
|**MsmqSecureHashAlgorithm**|Enum<br /><br /> -   **MD5**<br />-   **SHA1**<br />-   **SHA25**<br />-   **SHA512**|Spécifiez l'algorithme de hachage à utiliser pour traiter la synthèse du message. Cette propriété n’est pas disponible si le **MsmqProtectionLevel** est définie sur **aucun**.<br /><br /> Valeur par défaut : **SHA1**|  
|**MsmqEncryptionAlgorithm**|Enum<br /><br /> -   **RC4Stream**<br />-   **AES**|Spécifiez l'algorithme à utiliser pour le chiffrement des messages lors de leur transfert entre les gestionnaires de files d'attente. Cette propriété est disponible uniquement si le **MsmqProtectionLevel** est définie sur **EncryptAndSign**.<br /><br /> Valeur par défaut : **RC4Stream**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Windows**<br />-   **Nom d’utilisateur**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MessageClientCredentialType** propriété, consultez le **type d’informations d’identification de client de Message** propriété dans le **propriétés du Transport WCF-NetMsmq Boîte de réception, la sécurité du dialogue** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.<br /><br /> Valeur par défaut : **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-NetMsmq, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Valeur par défaut : **Basic256**|  
|**ServiceCertificate**|Chaîne|Spécifier l'empreinte du certificat X.509 pour cet emplacement de réception permettant au client d'authentifier le service. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement. **Remarque :** vous devez installer le certificat de service dans le **utilisateur actuel** emplacement du compte d’utilisateur du Gestionnaire de réception hébergeant cet emplacement de réception. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage WCF-NetMsmq adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> Valeur par défaut : **XML**|  
|**DisableLocationOnFailure**|Booléen|Spécifiez s'il faut désactiver l'emplacement de réception pour lequel le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **False**|  
|**SuspendMessageOnFailure**|Booléen|Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **True**|  
|**IncludeExceptionDetailInFaults**|Booléen|Spécifiez s'il faut inclure des informations sur l'exception gérée dans le détail des dysfonctionnements SOAP renvoyé au client à des fins de débogage.<br /><br /> Valeur par défaut : **False**|  
  
## <a name="configure-a-wcf-netmsmq-receive-location-with-the-biztalk-administration-console"></a>Configurer un WCF-NetMsmq emplacement de réception avec la Console Administration de BizTalk
  
 Vous pouvez définir des variables d'emplacement de réception pour l'adaptateur WCF-NetMsmq dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer la procédure suivante, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
> [!NOTE]
>  Les configurations de liaison des clients WCF et des emplacements de réception WCF-NetMsmq doivent correspondre. Si elles ne correspondent pas, les emplacements de réception WCF-NetMsmq  peuvent perdre des messages entrant.  
  
## <a name="configure-variables-for-a-wcf-netmsmq-receive-location"></a>Configurer les variables d’emplacement de réception WCF-NetMsmq  
  
1.  Dans la console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application vous souhaitez créer un emplacement de réception.  
  
2.  Dans le volet gauche de la console Administration de BizTalk, cliquez sur le nœud **Port de réception** . Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section ensuite **Type**, sélectionnez **WCF-NetMsmq** à partir de la liste déroulante, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **général** onglet, configurez l’adresse du point de terminaison et emplacement de réception de l’identité du service WCF-netmsmq. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **WCF-NetMsmq Transport boîte de dialogue Propriétés, réception, général**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **liaison** onglet, configurez les propriétés de délai d’attente et de transaction. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-NetMsmq, réception, liaison**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
7.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **sécurité** définir la sécurité, l’onglet emplacement de réception des fonctionnalités de WCF-NetMsmq. Pour plus d’informations sur la **sécurité** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-NetMsmq, réception, sécurité**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
8.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-NetMsmq, réception, Messages**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 
  
## <a name="configure-a-wcf-netmsmq-receive-location-programmatically"></a>Configurer un WCF-NetMsmq par programme l’emplacement de réception
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundBodyPathExpression vt="8" />  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <OrderedProcessing vt="11">0</OrderedProcessing>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <MsmqEncryptionAlgorithm vt="8">RC4Stream</MsmqEncryptionAlgorithm>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <MsmqProtectionLevel vt="8">Sign</MsmqProtectionLevel>  
  <DisableLocationOnFailure vt="11">0</DisableLocationOnFailure>  
  <MsmqSecureHashAlgorithm vt="8">Sha1</MsmqSecureHashAlgorithm>  
  <SuspendMessageOnFailure vt="11">-1</SuspendMessageOnFailure>  
  <EnableTransaction vt="11">-1</EnableTransaction>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <MsmqAuthenticationMode vt="8">WindowsDomain</MsmqAuthenticationMode>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un emplacement de réception WCF-NetMsmq :  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetMsmq receive location   
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
  <InboundBodyLocation vt=""8"">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt=""11"">0</UseSSO>  
  <Identity vt=""8"">  
    <identity>  
    <userPrincipalName value=""username@contoso.com"" />  
    </identity>  
  </Identity>  
</CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-NetMsmq   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-NetMsmq" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "net.msmq://mycomputer/private/sampleQueue";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-NetMsmq"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des métadonnées de Service WCF pour les adaptateurs de réception](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)   
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)   
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Configuration de l’adaptateur WCF-NetMsmq](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md)   
 [Envoi et la récupération des Messages dans une Transaction](http://go.microsoft.com/fwlink/?LinkID=75752)   
 [Message Queuing et Active Directory](http://go.microsoft.com/fwlink/?LinkID=75769)   
 [Files d’attente publiques et privées](http://go.microsoft.com/fwlink/?LinkId=196673)