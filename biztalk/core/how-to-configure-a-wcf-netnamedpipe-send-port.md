---
title: "Comment configurer un Port d’envoi WCF-NetNamedPipe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57684e09-1f72-4bde-976c-3fcec65dc182
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 297c962294042589ce3b9e7bc3303bcd9a55296e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netnamedpipe-send-port"></a>Configuration d'un port d'envoi WCF-NetNamedPipe
Vous pouvez configurer un port d'envoi WCF-NetNamedPipe par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle d’objet de l’Explorateur BizTalk expose une interface spécifique à l’adaptateur pour les ports d’envoi nommé **ITransportInfo** qui a le **TransportTypeData** propriété en lecture/écriture. Celle-ci accepte le jeu de propriétés de configuration du port d'envoi WCF-NetNamedPipe sous la forme d'une paire nom-valeur de chaînes XML.  
  
 Le **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur utilise les valeurs par défaut pour la configuration du port d'envoi WCF-NetNamedPipe, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour les ports d'envoi WCF-NetNamedPipe.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identité&gt;<br /><br /> &lt;valeur d’userPrincipalName = «username@contoso.com» /&gt;<br /><br /> &lt;/Identity&gt;|Spécifiez l'identité du service attendu par ce port d'envoi. Ces paramètres permettent au port d'envoi d'authentifier le service. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**StaticAction**|Chaîne|Spécifiez le **SOAPAction** champ d’en-tête pour les messages sortants. Cette propriété peut également être définie via la propriété de contexte de message **WCF. Action** dans un pipeline ou une orchestration. Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1-le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.<br /><br /> Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise http://contoso.com/Svc/Op1 pour sortant **SOAPAction** en-tête.<br /><br /> \<BtsActionMapping ><br /><br /> \<Nom de l’opération = « Op1 » Action = « http://contoso.com/Svc/Op1 » / ><br /><br /> \<Nom de l’opération = « Op2 » Action = « http://contoso.com/Svc/Op2 » / ><br /><br /> \</ BtsActionMapping ><br /><br /> Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d’utilisation d’un port d’envoi sollicitation-réponse, cette valeur indique une période pour la réalisation de l’intégralité de l’interaction, même si le service renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**MaxReceivedMessageSize**|Entier|Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.<br /><br /> Valeur par défaut : 65536|  
|**EnableTransaction**|Booléen|Indiquer si un message est transmis au service de destination et supprimé de la base de données MessageBox dans un contexte transactionnel à l’aide de la **WS-AtomicTransaction** protocole.<br /><br /> Valeur par défaut : **False**|  
|**TransactionProtocol**|Enum<br /><br /> -   **OleTransaction**<br />-   **WS-AtomicTransaction**|Spécifiez le protocole de transaction à utiliser avec cette liaison.<br /><br /> Valeur par défaut : **OleTransaction**|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**-la sécurité est désactivée.<br />-   **Transport**:-la sécurité est fournie à l’aide de la sécurité basée sur le transport sous-jacente. Il est possible de contrôler le niveau de protection avec ce mode.|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **Transport**|  
|**TransportProtectionLevel**|Enum<br /><br /> -   **Aucun** -aucune protection.<br />-   **Signe** -les Messages sont signés.<br />-   **EncryptAndSign** -Messages sont chiffrés et signés.|Spécifiez le niveau de protection du canal nommé. La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert. Le chiffrement garantit la confidentialité des données pendant le transport.<br /><br /> Valeur par défaut : **EncryptAndSign**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **XML**<br />-   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage qui utilise de l’adaptateur d’envoi WCF-NetNamedPipe pour décoder le nœud identifié par le chemin de corps spécifié dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **XML**|  
|**PropagateFaultMessage**|Booléen<br /><br /> -   **True** -router le message qui échoue le traitement sortant vers une application abonnée (un autre planification d’orchestration ou le port de réception).<br />-   **False** -suspendre les messages ayant échoué et générer un accusé de réception négatif (NACK).|Spécifiez s’il faut Router ou suspendre les messages que le traitement sortant a échoué.<br /><br /> Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **True**|  
  
## <a name="configure-a-wcf-netnamedpipe-send-port-with-the-biztalk-administration-console"></a>Configurer un Port d’envoi WCF-NetNamedPipe avec la Console Administration de BizTalk
  
 Vous pouvez définir les variables de l'adaptateur du port d'envoi WCF-NetNamedPipe dans la console Administration de BizTalk. Si les propriétés ne sont pas définies pour le port d'envoi, les valeurs par défaut pour la configuration du port d'envoi WCF-NetNamedPipe sont utilisées, comme indiqué dans le tableau précédent.  
  
## <a name="configure-variables-for-a-wcf-netnamedpipe-send-port"></a>Configurer des variables pour un port d’envoi WCF-NetNamedPipe  
  
1.  Dans la console Administration de BizTalk, créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **WCF-NetNamedPipe** pour le **Type** option dans le **Transport** section de la **général**onglet.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **général** onglet, configurez l’adresse de point de terminaison, l’identité du service et le **SOAPAction** en-tête pour le port d’envoi WCF-NetNamedPipe. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **WCF-NetNamedPipe Transport boîte de dialogue Propriétés, envoi, général** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
4.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **liaison** onglet, configurez les propriétés de délai d’attente et de transaction. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-NetNamedPipe, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
5.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **sécurité** onglet, définissez les fonctionnalités de sécurité du port d’envoi WCF-NetNamedPipe. Pour plus d’informations sur la **sécurité** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-NetNamedPipe, envoi, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
6.  Dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-NetNamedPipe** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-NetNamedPipe, envoi, Messages**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="configure-a-wcf-netnamedpipe-send-port-programmatically"></a>Configurer un Port d’envoi WCF-NetNamedPipe par programme
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  
  
```  
<CustomProps>  
  <TransportProtectionLevel vt="8">EncryptAndSign</TransportProtectionLevel>  
  <TransactionProtocol vt="8">OleTransactions</TransactionProtocol>  
  <InboundBodyPathExpression vt="8" />  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EnableTransaction vt="11">0</EnableTransaction>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <MaxReceivedMessageSize vt="3">2097152</MaxReceivedMessageSize>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un port d'envoi WCF-NetNamedPipe :  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetNamedPipe send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-NetNamedPipe"];  
sendPort.PrimaryTransport.Address = "net.pipe://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)   
 [Configuration de l’adaptateur WCF-NetNamedPipe](../core/configuring-the-wcf-netnamedpipe-adapter.md)   
 [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)