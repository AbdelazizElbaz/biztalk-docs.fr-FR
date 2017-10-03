---
title: "Pour configurer les emplacement de réception WCF-NetNamedPipe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2e8242a-64c7-43de-af5e-25c22e182c72
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 29c52e8a92a842958ed9d4dcf30f7b02eedfa749
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netnamedpipe-receive-location"></a>Configuration d'un emplacement de réception WCF-NetNamedPipe
Vous pouvez configurer un emplacement de réception WCF-NetNamedPipe par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle objet de l'Explorateur BizTalk permet de créer et de configurer les emplacements de réception par programme. Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception WCF-NetNamedPipe sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.  
  
 Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. Dans ce cas, l'adaptateur WCF-NetNamedPipe utilise les valeurs par défaut pour la configuration de l'emplacement de réception WCF-NetNamedPipe, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception WCF-NetNamedPipe.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identité&gt;<br /><br /> &lt;valeur d’userPrincipalName = «username@contoso.com» /&gt;<br /><br /> &lt;/Identity&gt;|Spécifiez l'identité du service fourni par cet emplacement de réception. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité. Ces paramètres permettent au client d'authentifier cet emplacement de réception. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d'utilisation d'un port de réception de requête-réponse, cette valeur indique une période pour la réalisation de l'intégralité de l'interaction, même si le client renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> Valeur par défaut : 65536|  
|**EnableTransaction**|Booléen|Spécifiez si un message est envoyé à la base de données MessageBox à l'aide de la transaction transmise depuis des clients. Si cette propriété est définie sur **True**, les clients doivent soumettre des messages à l’aide du protocole thetransaction spécifié dans le **TransactionProtocol** propriété. Si les clients envoient des messages hors de l'étendue transactionnelle, cet emplacement de réception renvoie une exception aux clients et aucun message n'est interrompu.<br /><br /> Cette option n'est disponible que pour les emplacements de réception unidirectionnels. Si les clients envoient des messages dans un contexte transactionnel d'emplacements de réception avec requête-réponse, une exception est renvoyée aux clients et aucun message n'est interrompu.<br /><br /> Valeur par défaut :`False`|  
|**TransactionProtocol**|Enum<br /><br /> -   **OleTransaction**<br />-   **WS-AtomicTransaction**|Indiquez le protocole de transaction à utiliser avec cet emplacement de réception.<br /><br /> Valeur par défaut : **OleTransaction**|  
|**Maxconcurrentcalls.**|Entier|Spécifier le nombre d'appels simultanés par instance de service unique. Les appels excédentaires sont mis en file d'attente. La plage de cette propriété s'étend de 1 à Int32.MaxValue.<br /><br /> Valeur par défaut : 200|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**: la sécurité est désactivée.<br />-   **Transport**: la sécurité est fournie à l’aide de sous-jacent de sécurité basée sur le transport. Il est possible de contrôler le niveau de protection avec ce mode.|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **Transport**|  
|**TransportProtectionLevel**|Enum<br /><br /> -   **Aucun**: aucune protection.<br />-   **Signe**: les Messages sont signés.<br />-   **EncryptAndSign**: les Messages sont chiffrés et signés.|Définir la sécurité au niveau du transport TCP. La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert. Le chiffrement garantit la confidentialité des données pendant le transport.<br /><br /> Valeur par défaut : **EncryptAndSign**|  
|**UseSSO**|Booléen|Indiquez s'il faut utiliser l'authentification unique de l'entreprise pour extraire les informations d'identification du client afin d'émettre un ticket d'authentification unique.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage WCF-NetNamedPipe adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> Valeur par défaut : **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message de réponse sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**SuspendMessageOnFailure**|Booléen|Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **True**|  
|**IncludeExceptionDetailInFaults**|Booléen|Spécifiez s'il faut inclure des informations sur l'exception gérée dans le détail des dysfonctionnements SOAP renvoyé au client à des fins de débogage.<br /><br /> Valeur par défaut : **False**|  
  
## <a name="configure-a-wcf-netnamedpipe-receive-location-with-the-biztalk-administration-console"></a>Configurer un WCF-NetNamedPipe emplacement de réception avec la Console Administration de BizTalk
  
 Vous pouvez définir des variables d'emplacement de réception pour l'adaptateur WCF-NetNamedPipe dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer la procédure suivante, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
## <a name="configure-variables-for-a-wcf-netnamedpipe-receive-location"></a>Configurer les variables d’emplacement de réception WCF-NetNamedPipe  
  
1.  Dans la console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, puis développez l’application que vous souhaitez créer un emplacement de réception.  
  
2.  Dans le volet gauche de la console Administration de BizTalk, cliquez sur le nœud **Port de réception** . Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section ensuite **Type**, sélectionnez **WCF-NetNamedPipe** à partir de la liste déroulante, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **général** onglet, configurez l’adresse du point de terminaison et emplacement de réception de l’identité du service WCF-NetNamedPipe. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte de dialogue Propriétés du Transport WCF-NetNamedPipe, réception, général**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **liaison** onglet, configurez les propriétés de délai d’attente et de transaction. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-NetNamedPipe, réception, liaison**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
7.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **sécurité** définir la sécurité, l’onglet emplacement de réception des fonctionnalités de WCF-NetNamedPipe. Pour plus d’informations sur la **sécurité** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-NetNamedPipe, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
8.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-NetNamedPipe, réception, Messages**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="configure-a-wcf-netnamedpipe-receive-location-programmatically"></a>Configurer un WCF-NetNamedPipe par programme l’emplacement de réception
  
 Pour définir les propriétés, utilisez le format suivant :  
  
```  
<CustomProps>  
  <UseSSO vt="11">0</UseSSO>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <TransactionProtocol vt="8">WSAtomicTransactions</TransactionProtocol>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TransportProtectionLevel vt="8">EncryptAndSign</TransportProtectionLevel>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <EnableTransaction vt="11">-1</EnableTransaction>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un emplacement de réception WCF-NetNamedPipe :  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetNamedPipe receive location   
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
// Find a receive handler for WCF-NetNamedPipe   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-NetNamedPipe" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "net.pipe://mycomputer/samplePipeName";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-NetNamedPipe"];  
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
 [Configuration de l’adaptateur WCF-NetNamedPipe](../core/configuring-the-wcf-netnamedpipe-adapter.md)