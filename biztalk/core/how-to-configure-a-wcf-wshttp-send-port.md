---
title: "Comment configurer un Port d’envoi WCF-WSHttp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035d9a62-b8a3-4705-a7bc-b62676437206
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96d88f9b8556ec3c4fb470f06ae80bae50d78ad0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-wshttp-send-port"></a>Configuration d'un port d'envoi WCF-WSHttp
Vous pouvez configurer un port d'envoi WCF-WSHttp par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle d’objet de l’Explorateur BizTalk expose une interface spécifique à l’adaptateur pour les ports d’envoi nommé **ITransportInfo** qui a le **TransportTypeData** propriété en lecture/écriture. Celle-ci accepte le jeu de propriétés de configuration du port d'envoi WCF-WSHttp sous la forme d'une paire nom-valeur de chaînes XML.  
  
 Le **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur utilise les valeurs par défaut pour la configuration du port d'envoi WCF-WSHttp, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour les ports d'envoi WCF-WSHttp.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identité&gt;<br /><br /> &lt;valeur d’userPrincipalName = «username@contoso.com» /&gt;<br /><br /> &lt;/Identity&gt;|Spécifiez l'identité du service attendu par ce port d'envoi. Ces paramètres permettent au port d'envoi d'authentifier le service. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**StaticAction**|-Chaîne|Spécifiez le **SOAPAction** champ d’en-tête HTTP pour les messages sortants. Cette propriété peut également être définie via la propriété de contexte de message **WCF. Action** dans un pipeline ou une orchestration. Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1-le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.<br /><br /> Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise http://contoso.com/Svc/Op1 pour sortant **SOAPAction** en-tête.<br /><br /> \<BtsActionMapping ><br /><br /> \<Nom de l’opération = « Op1 » Action = « http://contoso.com/Svc/Op1 » / ><br /><br /> \<Nom de l’opération = « Op2 » Action = « http://contoso.com/Svc/Op2 » / ><br /><br /> \</ BtsActionMapping ><br /><br /> Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d’utilisation d’un port d’envoi sollicitation-réponse, cette valeur indique une période pour la réalisation de l’intégralité de l’interaction, même si le service renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> Valeur par défaut : 65536|  
|**MessageEncoding**|Enum<br /><br /> -   **Texte** -utiliser un encodeur de message texte.<br />-   **MTOM** -utiliser un encodeur Message Transmission Organization Mechanism 1.0 (MTOM).|Indiquer l’encodeur utilisé pour coder le message SOAP.<br /><br /> Valeur par défaut : **texte**|  
|**TextEncoding**|Enum<br /><br /> -   **unicodeFFF** -codage Unicode BigEndian.<br />-   **UTF-16** - 16 bits encodage.<br />-   **UTF-8** - 8 bits encodage.|Spécifier le codage à utiliser pour l’émission de messages sur la liaison de jeu de caractères lors de la **MessageEncoding** est définie sur **texte**.<br /><br /> Valeur par défaut : **utf-8**|  
|**EnableTransaction**|Booléen|Indiquer si un message est transmis au service de destination et supprimé de la base de données MessageBox dans un contexte transactionnel à l’aide de la **WS-AtomicTransaction** protocole.<br /><br /> Valeur par défaut : **False**|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**<br />-   **Message**<br />-   **Transport**<br />-   **TransportWithMessageCredential**<br /><br /> Pour plus d’informations sur les noms de membre pour le **SecurityMode** propriété, consultez le **mode de sécurité** propriété dans le **boîte dialogue de propriétés du Transport WCF-WSHttp, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **None**|  
|**TransportClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Base**<br />-   **Windows**<br />-   **Certificat**<br />-   **Digest**<br />-   **NTLM**<br /><br /> Pour plus d’informations sur les noms de membre pour le **TransportClientCredentialType** propriété, consultez le **type d’informations d’identification du client du Transport** propriété dans le **les Transport WCF-WSHttp Sécurité de la boîte de dialogue, envoi, propriétés** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du port d'envoi.<br /><br /> Valeur par défaut : **None**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Windows**<br />-   **Nom d’utilisateur**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MessageClientCredentialType** propriété, consultez le **type d’informations d’identification de client de Message** propriété dans le **propriétés du Transport WCF-WSHttp Boîte de dialogue zone, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.<br /><br /> Valeur par défaut : **nom d’utilisateur**|  
|**AlgorithmSuite**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans le **boîte dialogue de propriétés du Transport WCF-WSHttp, envoi, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Valeur par défaut : **Basic256**|  
|**NegotiateServiceCredential**|Booléen<br /><br /> Pour plus d’informations sur les noms de membre pour le **NegotiateServiceCredential** propriété, consultez le **négocier les informations d’identification du service** propriété dans le **propriétés du Transport WCF-WSHttp Boîte de dialogue zone, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier si les informations d'identification du service sont générées au niveau de ce port d'envoi hors bande ou sont obtenues à partir du service sur ce port d'envoi via un processus de négociation. Une négociation de ce type est un précurseur de l'échange classique des messages.<br /><br /> Valeur par défaut : **False**|  
|**EnableSecurityContext**|Booléen|Spécifiez si un jeton de contexte de sécurité est établi via un **WS-SecureConversation** exchange entre ce port d’envoi et le service. Si cette propriété est définie sur **True** , le service de destination doit prendre en charge **WS-SecureConversation**.<br /><br /> Valeur par défaut : **True**|  
|**ClientCertificate**|Chaîne|Spécifiez l'empreinte du certificat X.509 pour l'authentification de ce port d'envoi auprès des services. Cette propriété est requise si le **ClientCredentialsType** est définie sur **certificat**. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ServiceCertificate**|Chaîne|Spécifiez l'empreinte du certificat X.509 pour l'authentification du service auquel ce port d'envoi envoie des messages. Le certificat à utiliser pour cette propriété doit être installé dans le **autres personnes** stocker dans le **ordinateur Local** emplacement.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**AffiliateApplicationName**|Chaîne|Spécifiez l'application associée à utiliser pour l'authentification unique (SSO) de l'entreprise.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**UseSSO**|Booléen|Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.<br /><br /> Valeur par défaut : **False**|  
|**UserName**|Chaîne|Spécifiez le nom d’utilisateur à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**. Il n'est pas nécessaire de se conformer au format domaine\utilisateur pour cette propriété.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Mot de passe**|Chaîne|Spécifiez le mot de passe à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ProxyToUse**|Enum<br /><br /> -   **Aucun** -n’utilisez pas un serveur proxy pour ce port d’envoi.<br />-   **Par défaut** -utiliser les paramètres du proxy dans le Gestionnaire d’envoi hébergeant ce port d’envoi.<br />-   **UserSpecified** -utiliser le serveur proxy spécifié dans le **ProxyAddress** propriété.|Spécifiez le serveur proxy à utiliser pour le trafic HTTP sortant.<br /><br /> Valeur par défaut : **None**|  
|**ProxyAddress**|Chaîne|Indiquer l’adresse du serveur proxy. Utilisez le **https** ou **http** schéma selon la configuration de sécurité. Cette adresse peut être suivie d'un deux-points et du numéro de port. Par exemple, http://127.0.0.1:8080.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ProxyUserName**|Chaîne|Indiquez le nom d'utilisateur à utiliser pour le proxy. L’adaptateur WCF-WSHttp tire parti du [WSHttpBinding](http://go.microsoft.com/fwlink/?LinkId=81206) dans le mode de transfert mis en mémoire tampon pour communiquer avec un point de terminaison. Informations d’identification de proxy de **WSHttpBinding** sont applicables uniquement lorsque le mode de sécurité est **Transport**, ou **aucun**. Si vous définissez la **SecurityMode** propriété **Message** ou **TransportWithMessageCredential**, l’adaptateur WCF-WSHttp n’utilise pas les informations d’identification spécifiées dans le  **ProxyUserName** et **ProxyPassword** propriétés pour l’authentification du proxy. **Remarque :** WCF-WSHttp adaptateur d’envoi utilise l’authentification de base pour le proxy. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**ProxyPassword**|Chaîne|Indiquez le mot de passe à utiliser pour le proxy.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage qui utilise de l’adaptateur d’envoi WCF-WSHttp pour décoder le nœud identifié par le chemin de corps spécifié dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **XML**|  
|**PropagateFaultMessage**|Booléen<br /><br /> -   **True** -router le message qui échoue le traitement sortant vers une application abonnée (un autre planification d’orchestration ou le port de réception).<br />-   **False** -suspendre les messages ayant échoué et générer un accusé de réception négatif (NACK).|Spécifiez s’il faut Router ou suspendre les messages que le traitement sortant a échoué.<br /><br /> Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **True**|  
  
## <a name="configure-a-wcf-wshttp-send-port-with-the-biztalk-administration-console"></a>Configurer un Port d’envoi WCF-WSHttp avec la Console Administration de BizTalk
  
 Vous pouvez définir les variables de l'adaptateur du port d'envoi WCF-WSHttp dans la console Administration de BizTalk. Si les propriétés ne sont pas définies pour le port d'envoi, les valeurs par défaut pour la configuration du port d'envoi WCF-WSHttp sont utilisées, comme indiqué dans le tableau précédent.  
  
## <a name="configure-variables-for-a-wcf-wshttp-send-port"></a>Configurer des variables pour un port d’envoi WCF-WSHttp  
  
1.  Dans la console Administration de BizTalk, créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **WCF-WSHttp** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **général** onglet, configurez l’adresse de point de terminaison, l’identité du service et le **SOAPAction** en-tête HTTP le port d’envoi WCF-WSHttp. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte de dialogue Propriétés du Transport WCF-WSHttp, envoi, général** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
4.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **liaison** onglet, configurez les propriétés de délai d’attente, le codage et la transaction. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-WSHttp, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **sécurité** onglet, définissez les fonctionnalités de sécurité du port d’envoi WCF-WSHttp. Pour plus d’informations sur la **sécurité** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-WSHttp, envoi, sécurité**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
6.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **Proxy** , onglet de configurer le paramètres du proxy pour le port d’envoi WCF-WSHttp. Pour plus d’informations sur la **Proxy** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-WSHttp, envoi, Proxy** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
7.  Dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-WSHttp** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-WSHttp, envoi, Messages**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="configure-a-wcf-wshttp-send-port-programmatically"></a>Configurer un Port d’envoi WCF-WSHttp par programme
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  

```  
 <CustomProps>    
  <ServiceCertificate vt="8" />  
  <UseSSO vt="11">0</UseSSO>  
  <InboundBodyPathExpression vt="8" />  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <Identity vt="8" />  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Message</SecurityMode>  
  <TransportClientCredentialType vt="8">Windows</TransportClientCredentialType>  
  <TextEncoding vt="8">utf-8</TextEncoding>  
  <NegotiateServiceCredential vt="11">-1</NegotiateServiceCredential>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
  <ClientCertificate vt="8" />  
  <ProxyUserName vt="8" />  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <ProxyToUse vt="8">Default</ProxyToUse>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EstablishSecurityContext vt="11">-1</EstablishSecurityContext>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <ProxyAddress vt="8" />  
  <MessageEncoding vt="8">Text</MessageEncoding>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un port d'envoi WCF-WSHttp :  
  
```  
// Use BizTalk Explorer object model to create new WCF-WSHttp send port.  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-WSHttp"];  
sendPort.PrimaryTransport.Address = "http://mycomputer/samplepath";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [Configuration de l’adaptateur WCF-WSHttp](../core/configuring-the-wcf-wshttp-adapter.md)   
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)