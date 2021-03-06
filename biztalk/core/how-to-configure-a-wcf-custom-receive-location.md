---
title: Pour configurer les emplacement de réception WCF-Custom | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2092cd4-6612-4ac3-81f3-dd25438837ae
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9c46434f22fe94ce046b7e7caf855d7f7a3eed4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-configure-a-wcf-custom-receive-location"></a>Configuration d'un emplacement de réception WCF-Custom
Vous pouvez configurer un emplacement de réception WCF-Custom par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle objet de l'Explorateur BizTalk permet de créer et de configurer les emplacements de réception par programme. Le modèle d’objet de l’Explorateur BizTalk expose le**IReceiveLocation** emplacement interface de configuration de recevoir un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception WCF-Custom sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, vous devez définir le **InboundTransportLocation** propriété de la **IReceiveLocation** interface.  
  
 Le **TransportTypeData** propriété de la **IReceiveLocation** interface n’a pas à définir. Dans ce cas, l'adaptateur WCF-Custom utilise les valeurs par défaut pour la configuration de l'emplacement de réception WCF-Custom, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception WCF-Custom.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identity&gt;<br /><br /> &lt;userPrincipalName value="username@contoso.com" /&gt;<br /><br /> &lt;/identity&gt;|Spécifiez l'identité du service fourni par cet emplacement de réception. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité. Ces paramètres permettent au client d'authentifier cet emplacement de réception. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**BindingType**|Enum<br /><br /> -   **basicHttpBinding**<br />-   **customBinding**<br />-   **mexHttpBinding**<br />-   **mexHttpsBinding**<br />-   **mexNamedPipeBinding**<br />-   **mexTcpBinding**<br />-   **netMsmqBinding**<br />-   **netNamedPipeBinding**<br />-   **netPeerTcpBinding**<br />-   **netTcpBinding**<br />-   **wsDualHttpBinding**<br />-   **wsFederationHttpBinding**<br />-   **wsHttpBinding**|Spécifiez le type de liaison à utiliser pour le point de terminaison qu'utilise cet emplacement de réception. **Remarque :** si vous utilisez une liaison personnalisée, la **BindingType** propriété peut être configurée avec les liaisons personnalisées. Pour plus d’informations sur la façon d’utiliser une liaison personnalisée, consultez [comment activer les Points d’extensibilité WCF avec les adaptateurs WCF](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md). <br /><br /> La valeur par défaut est une chaîne vide.|  
|**BindingConfiguration**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;nom de liaison = « netNamedPipeBinding »&gt;&lt;mode de sécurité « None » = /&gt; &lt; /liaison&gt;|Spécifiez une chaîne XML avec la **\<liaison\>** élément pour configurer différents types de liaisons prédéfinies fournis par Windows Communication Foundation (WCF). Pour plus d'informations sur la liaison fournie par le système et la liaison personnalisée, consultez les rubriques correspondantes de la section Voir aussi. **Remarque :** BizTalk Server ne prend pas en charge tous les types d’éléments d’extension de liaison que vous pouvez configurer avec le **BindingConfiguration** propriété. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**ServiceBehaviorConfiguration**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;behavior name="SampleServiceBehavior"&gt;&lt;serviceMetadata httpGetEnabled="true" httpGetUrl="http://mycomputer:9995/SampleMex" /&gt;&lt;serviceCredentials /&gt;&lt;/behavior&gt;|Spécifiez une chaîne XML avec la **\<comportement\>** élément de la **\<serviceBehaviors\>** élément pour configurer les paramètres de comportement d’un service WCF service. Pour plus d’informations sur la **\<serviceBehaviors\>** élément, consultez la rubrique appropriée dans Voir aussi.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**EndpointBehaviorConfiguration**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;nom du comportement = « sampleBehavior »&gt;&lt;callbackTimeouts /&gt;&lt;/behavior&gt;|Spécifier une chaîne XML avec la **\<comportement\>** élément de la **\<endpointBehaviors\>** élément pour configurer les paramètres de comportement d’un Point de terminaison WCF. Pour plus d’informations sur la **\<endpointBehaviors\>** élément, consultez la rubrique appropriée dans Voir aussi. **Remarque :** BizTalk Server ne prend pas en charge tous les types d’éléments d’extension que vous pouvez configurer avec le **EndpointBehaviorConfiguration** propriété. <br /><br /> La valeur par défaut est une chaîne vide.|  
|**CredentialType**|Enum<br /><br /> -   **Aucun**: ne pas utiliser les informations d’identification lorsque cet emplacement de réception envoie des sollicitations pour interroger un service externe ou cet emplacement de réception n’avez pas besoin d’interroger un service externe.<br />-   **IssueTicket**: utilisez Enterprise unique Sign-On (SSO) pour récupérer les informations d’identification du client pour émettre un ticket SSO. Cette option requiert l'utilisation du mode de sécurité permettant à cet emplacement de réception d'emprunter l'identité du compte d'utilisateur pour émettre un ticket SSO.<br />-   **UserAccount**: utiliser les informations d’identification spécifiées dans le **nom d’utilisateur** et **mot de passe** propriétés lorsque cela emplacement de réception envoie des sollicitations pour interroger un service externe.<br />-   **GetCredentials**: utiliser l’application associée SSO spécifiée dans le **AffiliateApplicationName** propriété lorsque cet emplacement de réception envoie des sollicitations pour interroger un service externe.|Spécifiez le type d'informations d'identification de cet emplacement de réception à utiliser lors de l'interrogation d'un service externe.<br /><br /> Valeur par défaut : **None**|  
|**UserName**|Chaîne|Indiquez le nom d'utilisateur de cet emplacement de réception à utiliser lors de l'interrogation d'un service externe pour récupérer des messages de réponse. Cette propriété est requise lorsque la **CredentialType** est définie sur **UserAccount**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Mot de passe**|Chaîne|Indiquez le mot de passe de cet emplacement de réception à utiliser lors de l'interrogation d'un service externe pour récupérer des messages de réponse. Cette propriété est requise lorsque la **CredentialType** est définie sur **UserAccount**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**AffiliateApplicationName**|Chaîne|Indiquez l'application associée SSO pour renvoyer des informations d'identification externes à utiliser lorsque cet emplacement de réception envoie des messages de sollicitation pour interroger un service externe. L'application associée SSO spécifiée doit comporter un mappage entre le compte Windows d'exécution de cet emplacement de réception et le compte du service externe. Cette propriété est requise lorsque la **CredentialType** est définie sur **GetCredentials**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OrderedProcessing**|Booléen|Spécifier s'il est nécessaire de conserver ou non l'ordre des messages lors de leur traitement (à utiliser avec la liaison NetMsmq).<br /><br /> Valeur par défaut : **False**|  
|**InboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -utiliser le contenu de SOAP **corps** élément d’un message entrant pour créer le corps du message BizTalk. Si l'élément **Body** a plusieurs éléments enfants, seul le premier élément devient le corps du message BizTalk.<br />-   **UseEnvelope** -créer le corps du message BizTalk à partir de l’ensemble SOAP **enveloppe** d’un message entrant.<br />-   **UseBodyPath** -utiliser l’expression de chemin d’accès au corps de la **InboundBodyPathExpression** propriété pour créer le corps du message BizTalk. L'expression du chemin du corps est évaluée en fonction de l'élément enfant immédiat de l'élément SOAP **Body** d'un message entrant. Cette propriété est valide uniquement pour des ports de sollicitation-réponse.<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**InboundBodyPathExpression**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).|Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**InboundNodeEncoding**|Enum<br /><br /> -   **Base64** -encodage Base64.<br />-   **Hex** - hexadécimal encodage.<br />-   **Chaîne** : codage de texte - UTF-8.<br />-   **XML** -les adaptateurs WCF créent le corps du message BizTalk avec le XML externe du nœud sélectionné par l’expression de chemin d’accès au corps de **InboundBodyPathExpression**.|Spécifiez le type de codage WCF-Custom adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.<br /><br /> Valeur par défaut : **XML**|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message de réponse sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message de réponse sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**DisableLocationOnFailure**|Booléen|Spécifiez s'il faut désactiver l'emplacement de réception pour lequel le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **False**|  
|**SuspendMessageOnFailure**|Booléen|Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.<br /><br /> Valeur par défaut : **True**|  
|**IncludeExceptionDetailInFaults**|Booléen|Spécifiez s'il faut inclure des informations sur l'exception gérée dans le détail des dysfonctionnements SOAP renvoyé au client à des fins de débogage.<br /><br /> Valeur par défaut : **False**|  
|**ReferencedBindings**|Blob XML<br /><br /> Exemple :<br /><br /> \<**BindingConfiguration** vt="8"\><br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;binding name="sampleBinding"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message issuedKeyType="AsymmetricKey"&gt;<br /><br /> &lt;issuer address="http://www.contoso.com/samplests" binding="wsFederationHttpBinding" bindingConfiguration="**contosoSTSBinding**"/&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> \</**BindingConfiguration**\><br /><br /> \<**ReferencedBindings** vt = « 8 »\><br /><br /> &lt;bindings&gt;<br /><br /> &lt;wsFederationHttpBinding&gt;<br /><br /> &lt;nom de liaison = «**contosoSTSBinding**»&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message negotiateServiceCredential="false"&gt;<br /><br /> &lt;issuer address="http://northwind.com/samplests" bindingConfiguration="**northwindBinding**" binding="wsHttpBinding"&gt;<br /><br /> &lt;/issuer&gt;<br /><br /> &lt;/message&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsFederationHttpBinding&gt;<br /><br /> &lt;wsHttpBinding&gt;<br /><br /> &lt;binding name="**northwindBinding**"&gt;<br /><br /> &lt;security mode="Message"&gt;<br /><br /> &lt;message clientCredentialType="Certificate" /&gt;<br /><br /> &lt;/security&gt;<br /><br /> &lt;/binding&gt;<br /><br /> &lt;/wsHttpBinding&gt;<br /><br /> &lt;/bindings&gt;<br /><br /> \</**ReferencedBindings** \> **Remarque :** le **ReferencedBinding** propriété ne doit pas contenir la configuration de liaison utilisée dans les **BindingConfiguration**  propriété.|Spécifier les configurations de liaison référencées par le **bindingConfiguration** attribut de la **\<émetteur\>** , élément pour les  **wsFederationHttpBinding** et **customBinding**, ce qui indique le Service STS (Security Token) qui émet des jetons de sécurité. Pour plus d’informations sur la **\<émetteur\>** élément, consultez la rubrique «\<émetteur\>» à [ http://go.microsoft.com/fwlink/?LinkId=83476 ](http://go.microsoft.com/fwlink/?LinkId=83476).<br /><br /> Les informations de liaison, y compris le **\<émetteur\>** , élément pour les **wsFederationHttpBinding** et **customBinding** peut être configuré via la **BindingConfiguration** propriété de WCF-Custom et les adaptateurs WCF-CustomIsolated. Toutes les configurations de liaison référencées pour cette propriété doivent être placé dans le formulaire de la [ \<liaisons\> ](http://go.microsoft.com/fwlink/?LinkID=80878) élément. **Remarque :** vous ne pouvez pas configurer cette propriété sur le **liaison** onglet dans la boîte de dialogue Propriétés du transport. Vous pouvez importer et exporter cette propriété via le **Import/Export** onglet dans la boîte de dialogue des propriétés de transport des adaptateurs WCF-Custom et WCF-CustomIsolated. **Remarque :** le **bindingConfiguration** attribut de la **\<émetteur\>** élément doit faire référence à un nom de liaison valide dans cette propriété. **Remarque :** le **\<émetteur\>** élément dans les configurations de liaison référencées peut également faire référence à une configuration de liaison différentes dans t sa propriété si cette chaîne de référence n’est pas un cercle dépendance. <br /><br /> La valeur par défaut est une chaîne vide.|  
  
## <a name="configure-a-wcf-custom-receive-location-with-the-biztalk-administration-console"></a>Configurer WCF-Custom emplacement de réception avec la Console Administration de BizTalk
  
 Vous pouvez définir des variables d'emplacement de réception pour l'adaptateur WCF-Custom dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer la procédure suivante, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
## <a name="configure-variables-for-a-wcf-custom-receive-location"></a>Configurer les variables d’emplacement de réception WCF-Custom  
  
1.  Lors de la configuration de l'adaptateur WCF-Custom, si vous envisagez d'utiliser les points d'extensibilité WCF tels que les éléments de liaison personnalisés, l'élément de comportement personnalisé et les composants du canal personnalisés, vous devez ajouter les assemblys qui implémentent les points d'extensibilité ainsi que tous les assemblys dépendants dans le GAC (Global Assembly Cache) à la fois sur l'ordinateur de traitement BizTalk (ordinateur d'exécution) et sur l'ordinateur d'administration. En outre, vous devez inscrire les composants d'extension dans le fichier machine.config. Pour plus d’informations sur l’utilisation des points d’extensibilité WCF avec l’adaptateur WCF Custom, consultez [comment activer les Points d’extensibilité WCF avec les adaptateurs WCF](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md).  
  
2.  Dans la console Administration de BizTalk, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**, puis développez l’application dans laquelle vous souhaitez créer un emplacement de réception.  
  
3.  Dans le volet gauche de la console Administration de BizTalk, cliquez sur le nœud **Port de réception** . Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
4.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**, puis dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau**pour créer un nouvel emplacement de réception.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section à côté **Type**, sélectionnez **WCF-Custom** dans la liste déroulante. liste, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **général** onglet, configurez l’adresse du point de terminaison et emplacement de réception de l’identité du service WCF-Custom. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **WCF-Custom Transport boîte de dialogue Propriétés, réception, général**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
7.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **liaison** , onglet de configurer différents types de liaisons prédéfinies ou personnalisées pour WCF. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte de dialogue de propriétés du Transport WCF-Custom, réception, liaison**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
8.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **comportement** onglet, configurez le point de terminaison et les comportements de service pour cet emplacement de réception. Le comportement du point de terminaison est représenté par un jeu d'éléments d'extension de comportement qui modifie ou étend la fonction du service ou du client. Pour plus d’informations sur la **comportement** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **comportement de la boîte de dialogue de propriétés du Transport WCF-Custom, réception,**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
9. Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **autres** onglet, configurez les informations d’identification pour cet emplacement de réception à utiliser lors de l’interrogation d’un service externe, et si cet emplacement de réception ordre du message conserve lors du traitement des messages. Pour plus d’informations sur la **autres** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte de dialogue Propriétés du Transport WCF-Custom, réception, autres** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
10. Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte de dialogue de propriétés du Transport WCF-Custom, réception, Messages**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
11. Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **Import/Export** onglet, importer et exporter le **adresse (URI)** et **identité de point de terminaison** propriétés sur le **général** onglet, les informations de liaison de la **liaison** onglet et le comportement de point de terminaison sur le **comportement** onglet pour cette activité de réception emplacement. Pour plus d’informations sur la **Import/Export** onglet dans le **propriétés du Transport WCF-Custom** boîte de dialogue, consultez la **boîte de dialogue de propriétés du Transport WCF-Custom, réception, importation-exportation**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  

## <a name="configure-a-wcf-custom-receive-location-programmatically"></a>Configurer un emplacement de réception WCF-Custom par programme
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  
  
```  
<CustomProps>  
  <InboundBodyPathExpression vt="8" />  
  <InboundBodyLocation vt="8">UseBodyElement</InboundBodyLocation>  
  <BindingConfiguration vt="8"><binding name="netNamedPipeBinding"><security mode="None" /></binding></BindingConfiguration>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <CredentialType vt="8">GetCredentials</CredentialType>  
  <Identity vt="8" />  
  <ServiceBehaviorConfiguration vt="8"><behavior name="SampleServiceBehavior"><serviceMetadata httpGetEnabled="true" httpGetUrl="http://mycomputer:9995/SampleService/Mex" /><serviceCredentials /></behavior></ServiceBehaviorConfiguration>  
  <Password vt="1" />  
  <OrderedProcessing vt="11">-1</OrderedProcessing>  
  <IncludeExceptionDetailInFaults vt="11">0</IncludeExceptionDetailInFaults>  
  <AffiliateApplicationName vt="8">SampleAffiliateApplication</AffiliateApplicationName>  
  <DisableLocationOnFailure vt="11">0</DisableLocationOnFailure>  
  <SuspendMessageOnFailure vt="11">0</SuspendMessageOnFailure>  
  <BindingType vt="8">netNamedPipeBinding</BindingType>  
  <UserName vt="8">Hello</UserName>  
  <InboundNodeEncoding vt="8">Xml</InboundNodeEncoding>  
  <EndpointBehaviorConfiguration vt="8"><behavior name="EndpointBehavior" /></EndpointBehaviorConfiguration>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un emplacement de réception WCF-Custom :  
  
```  
// Use BizTalk Explorer object model to create new WCF-Custom receive location   
string server = System.Environment.MachineName;  
string database = "BizTalkMgmtDb";  
string connectionString = string.Format("Server={0};Database={1};Integrated Security=true", server, database);  
string transportConfigData = @"<CustomProps>  
  <BindingConfiguration vt=""8""><binding name=""netNamedPipeBinding""><security mode=""None"" /></binding></BindingConfiguration>  
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
  
// Add a new one-way receive port  
IReceivePort receivePort = application.AddNewReceivePort(false);  
receivePort.Name = "SampleReceivePort";  
// Add a new one-way receive location  
IReceiveLocation recieveLocation = receivePort.AddNewReceiveLocation();  
recieveLocation.Name = "SampleReceiveLocation";  
// Find a receive handler for WCF-Custom   
int i = 0;  
for(i=0; i < explorer.ReceiveHandlers.Count; ++i)   
{  
    if("WCF-Custom" == explorer.ReceiveHandlers[i].TransportType.Name)  
        break;  
}  
recieveLocation.ReceiveHandler = explorer.ReceiveHandlers[i];  
recieveLocation.Address = "net.pipe://mycomputer/samplePipeName";  
recieveLocation.ReceivePipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruReceive"];  
recieveLocation.TransportType = explorer.ProtocolTypes["WCF-Custom"];  
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
 [Configuration de l’adaptateur WCF-Custom](../core/configuring-the-wcf-custom-adapter.md)   
 [Comment créer une Application associée](../core/how-to-create-an-affiliate-application.md)   
 [\<comportement\> de \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<comportement\> de \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095)