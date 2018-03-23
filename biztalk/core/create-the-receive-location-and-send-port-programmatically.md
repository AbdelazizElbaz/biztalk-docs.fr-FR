---
title: Créer l’emplacement de réception et le port d’envoi par programme | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47850e66-ce33-4c6a-8190-168071792c0b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2f6871ca730e741ca4877907593931fc362a4d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="create-the-receive-location-and-send-port-programmatically"></a>Créer l’emplacement de réception et le port d’envoi par programme
Configurer un WCF-BasicHttp emplacement de réception et le port d’envoi par programme. Pour utiliser la console Administration de BizTalk, consultez [adaptateur WCF-BasicHttp](../core/wcf-basichttp-adapter.md). 
  
## <a name="configure-the-receive-location-programmatically"></a>Configurer l’emplacement de réception par programmation  
  
 Le modèle objet de l'Explorateur BizTalk permet de créer et de configurer les emplacements de réception par programme. Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception WCF-BasicHttp sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.  
  
 Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. De cette manière, l'adaptateur WCF-BasicHttp utilise les valeurs par défaut pour la configuration de l'emplacement de réception WCF-BasicHttp, comme indiqué dans le tableau suivant.  
 
 Le fragment de code suivant illustre la création d’un WCF-BasicHttp à l’aide du modèle objet de l’Explorateur BizTalk d’emplacement de réception :  
  
```  
// Use BizTalk Explorer object model to create new WCF-BasicHttp receive location   
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
// Find a receive handler for WCF-BasicHttp  
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-BasicHttp" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "/samplepath/sampleservice.svc";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-BasicHttp"];  
recieveLocation.TransportTypeData = transportConfigData;  
// Save  
explorer.SaveChanges();  
  
```  

Vous pouvez utiliser le format suivant pour définir les propriétés `<CustomProps>`: 
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">UserName</MessageClientCredentialType>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <Identity vt="8">  
    <identity>  
    <userPrincipalName value="username@contoso.com" />  
    </identity>  
  </Identity>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">None</SecurityMode>  
  <TransportClientCredentialType vt="8">None</TransportClientCredentialType>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <MaxConcurrentCalls vt="3">16</MaxConcurrentCalls>  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```   
  
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir l’emplacement de réception :  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Spécifiez l'identité du service fourni par cet emplacement de réception. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité. Ces paramètres permettent au client d'authentifier cet emplacement de réception. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d'utilisation d'un port de réception de requête-réponse, cette valeur indique une période pour la réalisation de l'intégralité de l'interaction, même si le client renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> L’adaptateur WCF-BasicHttp tire parti du [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) classe dans le mode de transfert mis en mémoire tampon pour communiquer avec un point de terminaison. Pour le mode de transport de mise en mémoire tampon, la [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) propriété est toujours égale à la valeur de cette propriété.<br /><br /> Valeur par défaut : 65536|  
|**MessageEncoding**|Enum<br /><br /> -   **Texte** -utiliser un encodeur de message texte.<br />-   **MTOM** -utiliser un encodeur Message Transmission Optimization Mechanism 1.0 (MTOM).|Indiquer l’encodeur utilisé pour coder le message SOAP.<br /><br /> Valeur par défaut : **texte**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -codage Unicode BigEndian.<br />-   **UTF-16** - 16 bits encodage.<br />-   **UTF-8** - 8 bits encodage|Spécifier le codage à utiliser pour l’émission de messages sur la liaison de jeu de caractères lors de la **MessageEncoding** est définie sur **texte**.<br /><br /> Valeur par défaut : **utf-8**|  
|**MaxConcurrentCalls**|Entier|Spécifier le nombre d'appels simultanés par instance de service unique. Les appels excédentaires sont mis en file d'attente. La plage de cette propriété est comprise entre 1 et **Int32.MaxValue**.<br /><br /> Valeur par défaut : 200|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br />-   **TransportCredentialOnly**<br /><br /> Pour plus d’informations sur les noms de membre pour le **SecurityMode** propriété, consultez le **mode de sécurité** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-BasicHttp, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **None**|  
|**TransportClientCredentialType**|Pour plus d’informations sur les noms de membre pour le **TransportClientCredentialType** propriété, consultez le **type d’informations d’identification du client du Transport** propriété dans **les Transport WCF-BasicHttp Sécurité de la boîte de dialogue, réception, propriétés** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d’informations d’identification à utiliser lors de l’authentification du client.<br /><br /> Valeur par défaut : **None**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **UserName**<br />-   **Certificate**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MessageClientCredentialType** propriété, consultez le **type d’informations d’identification de client de Message** propriété dans **propriétés du Transport WCF-BasicHttp Boîte de réception, la sécurité du dialogue** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.<br /><br /> Valeur par défaut : **nom d’utilisateur**|  
|**AlgorithmSuite**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans **boîte boîte de dialogue de propriétés du Transport WCF-BasicHttp, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Valeur par défaut : **Basic256**|  
|**ServiceCertificate**|Chaîne|Spécifier l'empreinte du certificat X.509 pour cet emplacement de réception permettant au client d'authentifier le service. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement. **Remarque :** vous devez installer le certificat de service dans le **utilisateur actuel** emplacement du compte d’utilisateur du Gestionnaire de réception hébergeant cet emplacement de réception. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**UseSSO**|Booléen|Indiquez s'il faut utiliser l'authentification unique de l'entreprise pour extraire les informations d'identification du client afin d'émettre un ticket d'authentification unique. Pour plus d’informations sur les configurations de sécurité prenant en charge l’authentification unique, consultez la section, « Enterprise unique de session pour le WCF-BasicHttp adaptateur de réception » dans **boîte boîte de dialogue de propriétés du Transport WCF-BasicHttp, réception, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].<br /><br /> Valeur par défaut : **False**|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage WCF-BasicHttp adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> Valeur par défaut : **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message de réponse sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**SuspendMessageOnFailure**|Booléen|Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **False**|  
|**IncludeExceptionDetailInFaults**|Booléen|Spécifiez s'il faut inclure des informations sur l'exception gérée dans le détail des dysfonctionnements SOAP renvoyé au client à des fins de débogage.<br /><br /> Valeur par défaut : **False**|  
  
## <a name="configure-the-send-port-programmatically"></a>Configurer le port d’envoi par programme   

 Le fragment de code suivant illustre la création d’un port d’envoi WCF-BasicHttp à l’aide du modèle objet de l’Explorateur BizTalk :    
  
```  
// Use BizTalk Explorer object model to create new WCF-BasicHttp send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
                                 <MessageEncoding vt=""8"">Text</MessageEncoding>  
                                 <TextEncoding vt=""8"">utf-8</TextEncoding>  
                                 <OpenTimeout vt=""8"">00:01:00</OpenTimeout>  
                               </CustomProps>";  
//requires project reference to \Program Files\Microsoft BizTalk Server 2009\Developer Tools\Microsoft.BizTalk.ExplorerOM.dll  
BtsCatalogExplorer explorer = new Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer();  
explorer.ConnectionString = connectionString;  
// Add a new BizTalk application  
Application application = explorer.AddNewApplication();  
application.Name = "SampleBizTalkApplication";  
// Save  
explorer.SaveChanges();  
  
// Add a new static one-way send port  
SendPort sendPort = application.AddNewSendPort(false, false);   
sendPort.Name = "SampleSendPort";  
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-BasicHttp"];  
sendPort.PrimaryTransport.Address = "http://mycomputer/samplepath";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```    

Vous pouvez utiliser le format suivant pour définir les propriétés `<CustomProps>`: 
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UseSSO vt="11">0</UseSSO>  
  <MessageClientCredentialType vt="8">UserName</MessageClientCredentialType>  
  <InboundBodyPathExpression vt="8" />  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">None</SecurityMode>  
  <TransportClientCredentialType vt="8">None</TransportClientCredentialType>  
  <ClientCertificate vt="8" />  
  <ProxyUserName vt="8" />  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <ProxyToUse vt="8">Default</ProxyToUse>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <ProxyAddress vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  

Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour le port d’envoi :  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br />-   **TransportCredentialOnly**<br /><br /> Pour plus d’informations sur les noms de membre pour le **SecurityMode** propriété, consultez le **mode de sécurité** propriété dans **boîte dialogue de propriétés du Transport WCF-BasicHttp, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **None**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **UserName**<br />-   **Certificate**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MessageClientCredentialType** propriété, consultez le **type d’informations d’identification de client de Message** propriété dans **propriétés du Transport WCF-BasicHttp Boîte de dialogue zone, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.<br /><br /> Valeur par défaut : **nom d’utilisateur**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Basic**<br />-   **Windows**<br />-   **Certificate**<br />-   **Digest**<br />-   **Ntlm**<br /><br /> Pour plus d’informations sur les noms de membre pour le **TransportClientCredentialType** propriété, consultez le **type d’informations d’identification du client du Transport** propriété dans **les Transport WCF-BasicHttp Sécurité de la boîte de dialogue, envoi, propriétés** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du port d'envoi.<br /><br /> Valeur par défaut : **None**|  
|**UserName**|Chaîne|Spécifiez le nom d’utilisateur à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**. Il n'est pas nécessaire de se conformer au format domaine\utilisateur pour cette propriété.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Mot de passe**|Chaîne|Spécifiez le mot de passe à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**AffiliateApplicationName**|Chaîne|Spécifiez l'application associée à utiliser pour l'authentification unique (SSO) de l'entreprise.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**UseSSO**|Booléen|Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.<br /><br /> Valeur par défaut : **False**|  
|**ClientCertificate**|Chaîne|Spécifiez l'empreinte du certificat X.509 pour l'authentification de ce port d'envoi auprès des services. Cette propriété est requise si le **ClientCredentialsType** est définie sur **certificat**. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ServiceCertificate**|Chaîne|Spécifiez l'empreinte du certificat X.509 pour l'authentification du service auquel ce port d'envoi envoie des messages. Le certificat à utiliser pour cette propriété doit être installé dans le **autres personnes** stocker dans le **ordinateur Local** emplacement.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ProxyToUse**|Enum<br /><br /> -   **Aucun** -n’utilisez pas un serveur proxy pour ce port d’envoi.<br />-   **Par défaut** -utiliser les paramètres du proxy dans le Gestionnaire d’envoi hébergeant ce port d’envoi.<br />-   **UserSpecified** -utiliser le serveur proxy spécifié dans le **ProxyAddress** propriété|Spécifiez le serveur proxy à utiliser pour le trafic HTTP sortant.<br /><br /> Valeur par défaut : **None**|  
|**ProxyAddress**|Chaîne|Indiquer l’adresse du serveur proxy. Utilisez le **https** ou **http** schéma selon la configuration de sécurité. Cette adresse peut être suivie d'un deux-points et du numéro de port. Par exemple, http://127.0.0.1:8080.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ProxyUserName**|Chaîne|Indiquez le nom d'utilisateur à utiliser pour le proxy. L’adaptateur WCF-BasicHttp tire parti du [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) dans le mode de transfert mis en mémoire tampon pour communiquer avec un point de terminaison. Informations d’identification de proxy de **BasicHttpBinding** sont applicables uniquement lorsque le mode de sécurité est **Transport**, **aucun**, ou **TransportCredentialOnly**. Si vous définissez la **SecurityMode** propriété **Message** ou **TransportWithMessageCredential**, l’adaptateur WCF-BasicHttp n’utilise pas les informations d’identification spécifiées dans le  **ProxyUserName** et **ProxyPassword** propriétés pour l’authentification du proxy. **Remarque :** WCF-BasicHttp adaptateur d’envoi utilise l’authentification de base pour le proxy... <br /><br /> La valeur par défaut est une chaîne vide.|  
|**ProxyPassword**|Chaîne|Indiquez le mot de passe à utiliser pour le proxy.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage utilisé par l’adaptateur d’envoi WCF-BasicHttp pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **XML**|  
|**StaticAction**|Chaîne|Spécifiez le **SOAPAction** champ d’en-tête HTTP pour les messages sortants. Cette propriété peut également être définie via la propriété de contexte de message **WCF. Action** dans un pipeline ou une orchestration. Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1: le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.<br /><br /> Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise http://contoso.com/Svc/Op1 pour sortant **SOAPAction** en-tête.<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> L’adaptateur WCF-BasicHttp tire parti du [BasicHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81086) classe dans le mode de transfert mis en mémoire tampon pour communiquer avec un point de terminaison. Pour le mode de transport de mise en mémoire tampon, la [BasicHttpBinding.MaxBufferSize](http://go.microsoft.com/fwlink/?LinkId=80659) propriété est toujours égale à la valeur de cette propriété.<br /><br /> Valeur par défaut : 65 536|  
|**MessageEncoding**|Enum<br /><br /> -   **Texte** -utiliser un encodeur de message texte.<br />-   **MTOM** -utiliser un encodeur Message Transmission Organization Mechanism 1.0 (MTOM).|Indiquer l’encodeur utilisé pour coder le message SOAP.<br /><br /> Valeur par défaut : **texte**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -codage Unicode BigEndian.<br />-   **UTF-16** - 16 bits encodage.<br />-   **UTF-8** - 8 bits encodage|Spécifier le codage à utiliser pour l’émission de messages sur la liaison de jeu de caractères lors de la **MessageEncoding** est définie sur **texte**.<br /><br /> Valeur par défaut : **utf-8**|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d’utilisation d’un port d’envoi sollicitation-réponse, cette valeur indique une période pour la réalisation de l’intégralité de l’interaction, même si le service renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**AlgorithmSuite**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans **boîte dialogue de propriétés du Transport WCF-BasicHttp, envoi, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Valeur par défaut : **Basic256**|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Spécifiez l'identité du service attendu par ce port d'envoi. Ces paramètres permettent au port d'envoi d'authentifier le service. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**PropagateFaultMessage**|Booléen<br /><br /> -   **True** -router le message qui échoue le traitement sortant vers une application abonnée (un autre planification d’orchestration ou le port de réception).<br />-   **False** -suspendre les messages ayant échoué et générer un accusé de réception négatif (NACK).|Spécifiez s’il faut Router ou suspendre les messages que le traitement sortant a échoué.<br /><br /> Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **True**|  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des adaptateurs WCF](../core/what-are-the-wcf-adapters.md)  
 [Publication des Services WCF avec WCF isolé des adaptateurs de réception](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)   
 [Configuration d’IIS pour WCF isolé des adaptateurs de réception](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)   
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)   
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)    
  [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [Configuration des ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)