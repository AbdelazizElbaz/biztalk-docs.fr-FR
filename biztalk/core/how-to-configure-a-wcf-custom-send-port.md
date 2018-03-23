---
title: Comment configurer un Port d’envoi WCF-Custom | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a195c047-5d5c-478b-accd-252e9dc5cfe8
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c615e2f54e1d7db9115a2607162f6eae1dffc01a
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-a-wcf-custom-send-port"></a>Configuration d'un port d'envoi WCF-Custom
Vous pouvez configurer un port d'envoi WCF-Custom par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle d’objet de l’Explorateur BizTalk expose une interface spécifique à l’adaptateur pour les ports d’envoi nommé **ITransportInfo** qui a le **TransportTypeData** propriété en lecture/écriture. Celle-ci accepte le jeu de propriétés de configuration du port d'envoi WCF-Custom sous la forme d'une paire nom-valeur de chaînes XML.  
  
 Le **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur utilise les valeurs par défaut pour la configuration du port d'envoi WCF-Custom, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour les ports d'envoi WCF-Custom.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Spécifiez l'identité du service attendu par ce port d'envoi. Ces paramètres permettent au port d'envoi d'authentifier le service. Lors du processus de communication entre le client et le service, l'infrastructure WCF garantit que l'identité du service attendu correspond aux valeurs de cet élément. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**StaticAction**|Chaîne|Spécifiez le **SOAPAction** champ d’en-tête pour les messages sortants. Cette propriété peut également être définie via la propriété de contexte de message **WCF. Action** dans un pipeline ou une orchestration. Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1- le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.<br /><br /> Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise http://contoso.com/Svc/Op1 pour sortant **SOAPAction** en-tête.<br /><br /> \<BtsActionMapping\><br /><br /> \<Operation Name="Op1" Action="http://contoso.com/Svc/Op1" /\><br /><br /> \<Operation Name="Op2" Action="http://contoso.com/Svc/Op2" /\><br /><br /> \</BtsActionMapping\><br /><br /> Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**BindingType**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **BindingType** propriété, consultez le **Type de liaison** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, liaison**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifiez le type de liaison à utiliser pour le point de terminaison qu'utilise ce port d'envoi. **Remarque :** si vous utilisez une liaison personnalisée, la **BindingType** propriété peut être configurée avec les liaisons personnalisées. Pour plus d’informations sur la façon d’utiliser une liaison personnalisée, consultez [comment activer les Points d’extensibilité WCF avec les adaptateurs WCF](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).|  
|**BindingConfiguration**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;binding name="netNamedPipeBinding"&gt;&lt;readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" /&gt;&lt;security mode="None" /&gt;&lt;/binding&gt;|Spécifiez une chaîne XML avec la **\<liaison\>** élément pour configurer différents types de liaisons prédéfinies fournis par Windows Communication Foundation (WCF). Pour plus d'informations sur la liaison fournie par le système et la liaison personnalisée, consultez les rubriques appropriées répertoriées dans la section Voir aussi. **Remarque :** BizTalk Server ne prend pas en charge tous les types d’éléments d’extension de liaison que vous pouvez configurer avec le **BindingConfiguration** propriété. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**EndpointBehaviorConfiguration**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;nom du comportement = « sampleBehavior »&gt;&lt;callbackTimeouts /&gt;&lt;/behavior&gt;|Spécifier une chaîne XML avec la **\<comportement\>** élément de la **\<endpointBehaviors\>** élément pour configurer les paramètres de comportement d’un Point de terminaison WCF. Pour plus d’informations sur la **\<endpointBehaviors\>** élément, consultez la rubrique appropriée dans Voir aussi. **Remarque :** BizTalk Server ne prend pas en charge tous les types d’éléments d’extension que vous pouvez configurer avec le **EndpointBehaviorConfiguration** propriété. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**AffiliateApplicationName**|Chaîne|Spécifiez l'application associée à utiliser pour l'authentification unique (SSO) de l'entreprise.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**UseSSO**|Booléen|Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.<br /><br /> Valeur par défaut : **False**|  
|**UserName**|Chaîne|Spécifiez le nom d’utilisateur à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**. Il n'est pas nécessaire de se conformer au format domaine\utilisateur pour cette propriété.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Mot de passe**|Chaîne|Spécifiez le mot de passe à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **XML**<br />-   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage qui utilise de l’adaptateur d’envoi WCF-Custom pour décoder le nœud identifié par le chemin de corps spécifié dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **XML**|  
|**PropagateFaultMessage**|Booléen<br /><br /> -   **True** -router le message qui échoue le traitement sortant vers une application abonnée (un autre planification d’orchestration ou le port de réception).<br />-   **False** -suspendre les messages ayant échoué et générer un accusé de réception négatif (NACK).|Spécifiez s’il faut Router ou suspendre les messages que le traitement sortant a échoué.<br /><br /> Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Valeur par défaut : **True**|  
|**ReferencedBindings**|Blob XML<br /><br /> Exemple :<br /><br /> \<**BindingConfiguration** vt="8"\><br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;binding name="sampleBinding"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message issuedKeyType="AsymmetricKey"&gt;<br /><br /> &lt;issuer address="http://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="**contosoSTSBinding**"/&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> \</**BindingConfiguration**\><br /><br /> \<**ReferencedBindings** vt = « 8 »\><br /><br /> &lt;bindings&gt;<br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;nom de liaison = «**contosoSTSBinding**»&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message negotiateServiceCredential="false"&gt;<br /><br /> &lt;issuer address="http://northwind.com/samplests" bindingConfiguration="**northwindBinding**" binding="wsHttpBinding"&gt;<br /><br /> &lt;/issuer&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> &lt;wsHttpBinding&gt;<br /><br /> &lt;binding name="**northwindBinding**"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message clientCredentialType="Certificate" /&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsHttpBinding&gt;<br /><br /> &lt;/bindings&gt;<br /><br /> \</**ReferencedBindings** \> **Remarque :** le **ReferencedBinding** propriété ne doit pas contenir la configuration de liaison utilisée dans les **BindingConfiguration**  propriété.|Spécifier les configurations de liaison référencées par le **bindingConfiguration** attribut de la **\<émetteur\>** , élément pour les  **wsFederationHttpBinding** et **customBinding**, ce qui indique le Service STS (Security Token) qui émet des jetons de sécurité. Pour plus d’informations sur la **\<émetteur\>** élément, consultez la rubrique «\<émetteur\>» à [ http://go.microsoft.com/fwlink/?LinkId=83476 ](http://go.microsoft.com/fwlink/?LinkId=83476).<br /><br /> Les informations de liaison, y compris le **\<émetteur\>** , élément pour les **wsFederationHttpBinding** et **customBinding** peut être configuré via la **BindingConfiguration** propriété de WCF-Custom et les adaptateurs WCF-CustomIsolated. Toutes les configurations de liaison référencées pour cette propriété doivent être placé dans le formulaire de la [ \<liaisons\> ](http://go.microsoft.com/fwlink/?LinkID=80878) élément. **Remarque :** vous ne pouvez pas configurer cette propriété sur le **liaison** onglet dans la boîte de dialogue Propriétés du transport. Vous pouvez importer et exporter cette propriété via le **Import/Export** onglet dans la boîte de dialogue des propriétés de transport des adaptateurs WCF-Custom et WCF-CustomIsolated. **Remarque :** le **bindingConfiguration** attribut de la **\<émetteur\>** élément doit faire référence à un nom de liaison valide dans cette propriété. **Remarque :** le **\<émetteur\>** élément dans les configurations de liaison référencées peut également faire référence à une configuration de liaison différentes dans t sa propriété si cette chaîne de référence n’est pas un cercle dépendance. <br /><br /> La valeur par défaut est une chaîne vide.|  
  
## <a name="configure-a-wcf-custom-send-port-with-the-biztalk-administration-console"></a>Configurer un Port d’envoi WCF-Custom avec la Console Administration de BizTalk
  
 Vous pouvez définir les variables de l'adaptateur du port d'envoi WCF-Custom dans la console Administration de BizTalk. Si les propriétés ne sont pas définies pour le port d'envoi, les valeurs par défaut pour la configuration du port d'envoi WCF-Custom sont utilisées, comme indiqué dans le tableau précédent.  
  
## <a name="configure-variables-for-a-wcf-custom-send-port"></a>Configurer des variables pour un port d’envoi WCF-Custom  
  
1.  Lors de la configuration de l'adaptateur WCF-Custom, si vous envisagez d'utiliser les points d'extensibilité WCF tels que les éléments de liaison personnalisés, l'élément de comportement personnalisé et les composants du canal personnalisés, vous devez ajouter les assemblys qui implémentent les points d'extensibilité ainsi que tous les assemblys dépendants dans le GAC (Global Assembly Cache) à la fois sur l'ordinateur de traitement BizTalk (ordinateur d'exécution) et sur l'ordinateur d'administration. En outre, vous devez inscrire les composants d'extension dans le fichier machine.config. Pour plus d’informations sur l’utilisation des points d’extensibilité WCF avec l’adaptateur WCF Custom, consultez [comment activer les Points d’extensibilité WCF avec les adaptateurs WCF](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).  
  
2.  Dans la console Administration de BizTalk, créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **WCF-Custom** pour le **Type** option dans le **Transport** section de la **général** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
3.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
4.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **général** onglet, configurez l’adresse de point de terminaison, l’identité du service et le **SOAPAction** en-tête pour le Port d’envoi WCF-Custom. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte de dialogue Propriétés du Transport WCF-Custom, envoi, général** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **liaison** , onglet de configurer différents types de liaisons prédéfinies ou personnalisées pour WCF. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **comportement** onglet, configurez le comportement de point de terminaison pour ce port d’envoi. Le comportement de point de terminaison est représenté par un jeu d'éléments d'extension de comportement qui modifie ou étend la fonction du service ou du client. Pour plus d’informations sur la **comportement** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, comportement**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
7.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **informations d’identification** onglet, spécifiez les informations d’identification à utiliser lors de l’envoi de messages. Pour plus d’informations sur la **informations d’identification** onglet dans le **propriétés du Transport WCF-Custom** Voir boîte de dialogue le **informations d’identification de la boîte de dialogue de propriétés du Transport WCF-Custom, envoi,**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
8.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, Messages**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
9. Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **Import/Export** onglet, importer et exporter le **adresse (URI)** et **identité de point de terminaison** propriétés sur le **général** onglet, les informations de liaison de la **liaison** onglet et le comportement de point de terminaison sur le **comportement** onglet pour ce port d’envoi. Pour plus d’informations sur la **Import/Export** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, importation-exportation** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## <a name="configure-a-wcf-custom-send-port-programmatically"></a>Configurer un Port d’envoi WCF-Custom par programme  
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  
  
```  
<CustomProps>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <InboundBodyPathExpression vt="8" />  
  <EndpointBehaviorConfiguration vt="8"><behavior name="sampleBehavior"><callbackTimeouts /></behavior></EndpointBehaviorConfiguration>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <BindingConfiguration vt="8"><binding name="NetNamedPipeOrderProcessService.OrderProcessServieEndpoint"><readerQuotas maxDepth="32" maxStringContentLength="8192" maxArrayLength="16384" maxBytesPerRead="4096" maxNameTableCharCount="16384" /><security mode="None" /></binding></BindingConfiguration>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <UseSSO vt="11">0</UseSSO>  
  <AffiliateApplicationName vt="8" />  
  <BindingType vt="8">netNamedPipeBinding</BindingType>  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <UserName vt="8" />  
  <PropagateFaultMessage vt="11">-1</PropagateFaultMessage>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un port d'envoi WCF-Custom :  
  
```  
// Use BizTalk Explorer object model to create new WCF-Custom send port.  
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
                                 <StaticAction vt=""8"">http://www.northwindtraders.com/Service/Operation</StaticAction>  
                                 <EndpointBehaviorConfiguration vt=""8""><behavior name=""sampleBehavior""><callbackTimeouts /></behavior></EndpointBehaviorConfiguration>  
                                 <BindingType vt=""8"">netNamedPipeBinding</BindingType>  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-Custom"];  
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
 [Configuration de l’adaptateur WCF-Custom](../core/configuring-the-wcf-custom-adapter.md)   
 [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<comportement\> de \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)