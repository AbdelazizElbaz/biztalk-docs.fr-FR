---
title: "Pour configurer les emplacement de réception WCF-WSHttp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b38cce4a-9c81-4716-b847-1acada4afc15
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f817949b105fa99402db7ca8b9df3a2ba3a0a76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-wshttp-receive-location"></a>Configuration d'un emplacement de réception WCF-WSHttp
Vous pouvez configurer un emplacement de réception WCF-WSHttp par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle objet de l'Explorateur BizTalk permet de créer et de configurer les emplacements de réception par programme. Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception WCF-WSHttp sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.  
  
 Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. De cette manière, l'adaptateur WCF-WSHttp utilise les valeurs par défaut pour la configuration de l'emplacement de réception WCF-WSHttp, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception WCF-WSHttp.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identité&gt;<br /><br /> &lt;valeur d’userPrincipalName = «username@contoso.com» /&gt;<br /><br /> &lt;/Identity&gt;|Spécifiez l'identité du service fourni par cet emplacement de réception. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité. Ces paramètres permettent au client d'authentifier cet emplacement de réception. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d'utilisation d'un port de réception de requête-réponse, cette valeur indique une période pour la réalisation de l'intégralité de l'interaction, même si le client renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> Valeur par défaut : 65536|  
|**MessageEncoding**|Enum<br /><br /> -   **Texte** -utiliser un encodeur de message texte.<br />-   **MTOM** -utiliser un encodeur Message Transmission Optimization Mechanism 1.0 (MTOM).|Indiquer l’encodeur utilisé pour coder le message SOAP.<br /><br /> Valeur par défaut : **texte**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -codage Unicode BigEndian.<br />-   **UTF-16** - 16 bits encodage.<br />-   **UTF-8** - 8 bits encodage|Spécifier le codage à utiliser pour l’émission de messages sur la liaison de jeu de caractères lors de la **MessageEncoding** est définie sur **texte**.<br /><br /> Valeur par défaut : **utf-8**|  
|**EnableTransaction**|Booléen|Spécifiez si un message est envoyé à la base de données MessageBox à l'aide de la transaction transmise depuis des clients. Si cette propriété est `True`, les clients doivent soumettre des messages à l’aide de la **WS-AtomicTransaction** protocole. Si les clients envoient des messages hors de l'étendue transactionnelle, cet emplacement de réception renvoie une exception aux clients et aucun message n'est interrompu.<br /><br /> Cette option n'est disponible que pour les emplacements de réception unidirectionnels. Si les clients envoient des messages dans un contexte transactionnel d'emplacements de réception avec requête-réponse, une exception est renvoyée aux clients et aucun message n'est interrompu.<br /><br /> Valeur par défaut :`False`|  
|**Maxconcurrentcalls.**|Entier|Spécifier le nombre d'appels simultanés par instance de service unique. Les appels excédentaires sont mis en file d'attente. La plage de cette propriété s'étend de 1 à Int32.MaxValue. Valeur par défaut : 200|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br /><br /> Pour plus d’informations sur les noms de membre pour le **SecurityMode** propriété, consultez le **mode de sécurité** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-WSHttp, réception, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. |Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **Message**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Base**<br />-   **NTLM**<br />-   **Windows**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **TransportClientCredentialType** propriété, consultez le **type d’informations d’identification du client du Transport** propriété dans le **les Transport WCF-WSHttp Sécurité de la boîte de dialogue, réception, propriétés** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d’informations d’identification à utiliser lors de l’authentification du client.<br /><br /> Valeur par défaut : **Windows**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Windows**<br />-   **Nom d’utilisateur**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MessageClientCredentialType** propriété, consultez le **type d’informations d’identification de client de Message** propriété dans le **propriétés du Transport WCF-WSHttp Boîte de réception, la sécurité du dialogue** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.<br /><br /> Valeur par défaut : **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-WSHttp, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Valeur par défaut : **Basic256**|  
|**NegotiateServiceCredential**|Booléen|Spécifiez si les informations d'identification du service sont générées au niveau du client hors bande ou sont obtenues à partir du service sur ce client via un processus de négociation. Une négociation de ce type est un précurseur de l'échange classique des messages.<br /><br /> Si le **MessageClientCredentialType** égal à la propriété **aucun**, **nom d’utilisateur**, ou **certificat**, définir cette propriété sur  **False** implique que le certificat de service est disponible au niveau du client hors bande et que le client spécifier le certificat de service. Ce mode est interopérable avec les piles SOAP qui implémentent WS-Trust et WS-SecureConversation.<br /><br /> Si le **MessageClientCredentialType** est définie sur **Windows**, si cette propriété **False** Spécifie l’authentification Kerberos. Cela implique que le client et le service fassent partie du même domaine Kerberos. Ce mode est interopérable avec les piles SOAP qui implémentent le profil de jeton Kerberos (tel que défini au niveau OASIS WSS TC) ainsi que WS-Trust et WS-SecureConversation.<br /><br /> Lorsque cette propriété est **True**, elle génère une négociation .NET SOAP qui utilise l’échange SPNego sur les messages SOAP.<br /><br /> Valeur par défaut : **True**|  
|**EstablishSecurityContext**|Booléen|Spécifiez si le canal de sécurité établit une session sécurisée. Une session sécurisée établit un jeton de contexte de sécurité (SCT, Security Context Token) avant d'échanger les messages d'application.<br /><br /> Valeur par défaut : **True**|  
|**ServiceCertificate**|Chaîne|Spécifier l'empreinte du certificat X.509 pour cet emplacement de réception permettant au client d'authentifier le service. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement. **Remarque :** vous devez installer le certificat de service dans le **utilisateur actuel** emplacement du compte d’utilisateur du Gestionnaire de réception hébergeant cet emplacement de réception. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**UseSSO**|Booléen|Indiquez s'il faut utiliser l'authentification unique de l'entreprise pour extraire les informations d'identification du client afin d'émettre un ticket d'authentification unique. Pour plus d’informations sur les configurations de sécurité prenant en charge l’authentification unique, consultez la section, « Enterprise unique de session pour le WCF-WSHttp adaptateur de réception » dans la **boîte boîte de dialogue de propriétés du Transport WCF-WSHttp, réception, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage WCF-WSHttp adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> Valeur par défaut : **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message de réponse sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**SuspendMessageOnFailure**|Booléen|Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **True**|  
|**IncludeExceptionDetailInFaults**|Booléen|Spécifiez s'il faut inclure des informations sur l'exception gérée dans le détail des dysfonctionnements SOAP renvoyé au client à des fins de débogage.<br /><br /> Valeur par défaut : **False**|  
  
## <a name="configure-a-wcf-wshttp-receive-location-with-the-biztalk-administration-console"></a>Configurer un WCF-WSHttp emplacement de réception avec la Console Administration de BizTalk
  
 Vous pouvez définir des variables d'emplacement de réception pour l'adaptateur WCF-WSHttp dans la console Administration de BizTalk. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer les procédures suivantes, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
## <a name="configure-variables-for-a-wcf-wshttp-receive-location"></a>Configurer les variables d’emplacement de réception WCF-WSHttp  
  
1.  Dans la console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, puis développez l’application que vous souhaitez créer un emplacement de réception.  
  
2.  Dans le volet gauche de la console Administration de BizTalk, cliquez sur le nœud **Port de réception** . Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
4.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section à côté **Type**, sélectionnez **WCF-WSHttp** dans la liste déroulante. liste, puis cliquez sur **configurer**.  
  
5.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **général** onglet, configurez l’adresse du point de terminaison et emplacement de réception de l’identité du service WCF-WSHttp. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **WCF-WSHttp Transport boîte de dialogue Propriétés, réception, général**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **liaison** onglet, configurez les propriétés de délai d’attente, le codage et la transaction. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-WSHttp, réception, liaison**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
7.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **sécurité** définir la sécurité, l’onglet emplacement de réception des fonctionnalités de WCF-WSHttp. Pour plus d’informations sur la **sécurité** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-WSHttp, réception, sécurité**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
8.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-WSHttp, réception, Messages**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="configure-a-wcf-wshttp-receive-location-programmatically"></a>Configurer un WCF-WSHttp par programme l’emplacement de réception
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  
  
```  
<CustomProps>  
  <InboundBodyPathExpression vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Message</SecurityMode>  
  <TransportClientCredentialType vt="8">Windows</TransportClientCredentialType>  
  <NegotiateServiceCredential vt="11">-1</NegotiateServiceCredential>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EstablishSecurityContext vt="11">-1</EstablishSecurityContext>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <ServiceCertificate vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un emplacement de réception WCF-WSHttp :  
  
```  
// Use BizTalk Explorer object model to create new WCF-WSHttp receive location   
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
application.Name = "SampleBizTalkApplication1001";  
// Save  
explorer.SaveChanges();  
  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-WSHttp   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-WSHttp" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "/samplepath/sampleservice.svc";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-WSHttp"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Publication des Services WCF avec WCF isolé des adaptateurs de réception](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [Configuration d’IIS pour WCF isolé des adaptateurs de réception](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)   
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Configuration de l’adaptateur WCF-WSHttp](../core/configuring-the-wcf-wshttp-adapter.md)