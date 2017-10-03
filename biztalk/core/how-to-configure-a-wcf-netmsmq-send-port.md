---
title: "Comment configurer un Port d’envoi WCF-NetMsmq | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13f55e53-12af-473b-b73f-1c98edadfc28
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6475e7a33f31a4a2a609f1af90301ad96cecb74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-wcf-netmsmq-send-port"></a>Configuration d'un port d'envoi WCF-NetMsmq
Vous pouvez configurer un port d'envoi WCF-NetMsmq par programme ou à l'aide de la console Administration de BizTalk.  
  
## <a name="configuration-properties"></a>Propriétés de configuration
  
 Le modèle d’objet de l’Explorateur BizTalk expose une interface spécifique à l’adaptateur pour les ports d’envoi nommé **ITransportInfo** qui a le **TransportTypeData** propriété en lecture/écriture. Celle-ci accepte le jeu de propriétés de configuration du port d'envoi WCF-NetMsmq sous la forme d'une paire nom-valeur de chaînes XML.  
  
 Le **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur utilise les valeurs par défaut pour la configuration du port d'envoi WCF-NetMsmq, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour les ports d'envoi WCF-NetMsmq.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**Identity**|Blob XML<br /><br /> Exemple :<br /><br /> &lt;identité&gt;<br /><br /> &lt;valeur d’userPrincipalName = «username@contoso.com» /&gt;<br /><br /> &lt;/Identity&gt;|Spécifiez l'identité du service attendu par ce port d'envoi. Ces paramètres permettent au port d'envoi d'authentifier le service. Lors du processus d'établissement de liaison entre le client et le service, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité du service attendu correspond aux valeurs de cet élément.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**StaticAction**|Chaîne|Spécifiez le **SOAPAction** champ d’en-tête pour les messages sortants. Cette propriété peut également être définie via la propriété de contexte de message **WCF. Action** dans un pipeline ou une orchestration. Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1-le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.<br /><br /> Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise http://contoso.com/Svc/Op1 pour sortant **SOAPAction** en-tête.<br /><br /> \<BtsActionMapping ><br /><br /> \<Nom de l’opération = « Op1 » Action = « http://contoso.com/Svc/Op1 » / ><br /><br /> \<Nom de l’opération = « Op2 » Action = « http://contoso.com/Svc/Op2 » / ><br /><br /> \</ BtsActionMapping ><br /><br /> Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OpenTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**SendTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. En cas d’utilisation d’un port d’envoi sollicitation-réponse, cette valeur indique une période pour la réalisation de l’intégralité de l’interaction, même si le service renvoie un message volumineux.<br /><br /> Valeur par défaut : 00:01:00|  
|**CloseTimeout**|**System.TimeSpan**|Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.<br /><br /> Valeur par défaut : 00:01:00|  
|**EnableTransactional**|Booléen|Spécifiez le type de la file d’attente de message pour le service de destination : transactionnelle ou non transactionnelle. Si cette propriété est définie sur **True**, chaque message traité par ce port d’envoi est remis une seule fois et l’expéditeur est notifié des échecs de remise. Pour envoyer des messages via l’envoi transactionnel des ports, à la fois le **durables** et **exactlyOnce** éléments du service de liaison doit être définie sur **True**. Si cette propriété est définie sur **False**, les messages sont transférés sans garantie de remise.<br /><br /> Valeur par défaut : **True**|  
|**DeadLetterQueue**|Enum<br /><br /> -   **Aucun** -aucune file d’attente de lettres mortes ne doit être utilisé.<br />-   **Système** -utiliser la file d’attente de lettres mortes à l’échelle du système.<br />-   **Personnalisé** -utiliser une file d’attente de lettres mortes personnalisée.|Spécifiez la file d'attente des messages non distribués vers laquelle seront transférés les messages qui n'ont pas pu être remis à l'application. Pour plus d’informations sur les messages remis à la file d’attente de lettres mortes, consultez le **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].<br/><br/> **Remarque**: la file d’attente de lettres mortes personnalisée est pris en charge uniquement dans Message Queuing (MSMQ) 4.0, disponible avec Windows Vista. <br /><br /> Valeur par défaut : **système**|  
|**CustomDeadLetterQueue**|Chaîne|Spécifiez l’adresse URI complète avec le **net.msmq** schéma pour l’emplacement de la file d’attente de lettres mortes par application, où sont placés les messages qui ont expiré ou dont le transfert ou la remise a échoué. Par exemple, net.msmq://localhost/deadLetterQueueName. La file d'attente des messages non distribués fait partie du gestionnaire de file d'attente de l'application émettrice. Elle est réservée aux messages expirés n'ayant pu être remis à leur destinataire. Cette propriété est requise si le **DeadLetterQueue** est définie sur **personnalisé**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Propriété TimeToLive**|**System.TimeSpan**|Spécifiez une durée de validité des messages avant qu'ils ne soient considérés comme expirés et placés dans la file d'attente des messages non distribués. Cette propriété permet de s'assurer que les messages, pour lesquels le temps est un paramètre crucial, ne deviennent pas obsolètes avant leur traitement par le port d'envoi. Tout message d'une file d'attente qui n'aurait pas été utilisé par ce port d'envoi dans le délai spécifié est déclaré comme ayant expiré. Ces messages expirés sont envoyés vers une file d'attente spéciale, appelée file d'attente des messages non distribués. L’emplacement de la file d’attente de lettres mortes est défini avec la **DeadLetterQueue** propriété.<br /><br /> Valeur par défaut : 1.00:00:00|  
|**UseSourceJournal**|Booléen|Spécifiez si les copies des messages traités par ce port d'envoi doivent être stockées dans la file d'attente des journaux sources.<br /><br /> Valeur par défaut : **False**|  
|**SecurityMode**|Enum<br /><br /> -   **Aucun**<br />-   **Message**<br />-   **Transport**<br />-   **Les deux**<br /><br /> Pour plus d’informations sur les noms de membre pour le **SecurityMode** propriété, consultez le **mode de sécurité** propriété dans le **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type de sécurité utilisé.<br /><br /> Valeur par défaut : **Transport**|  
|**MsmqAuthenticationMode**|Enum<br /><br /> -   **Aucun**<br />-   **WindowsDomain**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MsmqAuthenticationMode** propriété, consultez le **mode d’authentification MSMQ** propriété dans le **boîte boîte de dialogue Propriétés du Transport WCF-NetMsmq, Envoyer, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifiez le mode d'authentification du message par le transport MSMQ.<br /><br /> Valeur par défaut : **WindowsDomain**|  
|**MsmqProtectionLevel**|Enum<br /><br /> -   **Aucun**: aucune protection.<br />-   **Signe**: les Messages sont signés.<br />-   **EncryptAndSign**: les Messages sont chiffrés et signés. Pour utiliser ce niveau de protection, vous devez activer **l’intégration Active Directory** pour **MSMQ**.|Spécifier le mode de sécurisation des messages au niveau du transport MSMQ.<br /><br /> Valeur par défaut : **signe**|  
|**MsmqSecureHashAlgorithm**|Enum<br /><br /> -   **MD5**<br />-   **SHA1**<br />-   **SHA25**<br />-   **SHA512**|Spécifiez l'algorithme de hachage à utiliser pour traiter la synthèse du message. Cette propriété n’est pas disponible si le **MsmqProtectionLevel** est définie sur **aucun**.<br /><br /> Valeur par défaut : **SHA1**|  
|**MsmqEncryptionAlgorithm**|Enum<br /><br /> -   **RC4Stream**<br />-   **AES**|Spécifiez l'algorithme à utiliser pour le chiffrement des messages lors de leur transfert entre les gestionnaires de files d'attente. Cette propriété est disponible uniquement si le **MsmqProtectionLevel** est définie sur **EncryptAndSign**.<br /><br /> Valeur par défaut : **RC4Stream**|  
|**MessageClientCredentialType**|Enum<br /><br /> -   **Aucun**<br />-   **Windows**<br />-   **Nom d’utilisateur**<br />-   **Certificat**<br /><br /> Pour plus d’informations sur les noms de membre pour le **MessageClientCredentialType** propriété, consultez le **type d’informations d’identification de client de Message** propriété dans le **propriétés du Transport WCF-NetMsmq Boîte de dialogue zone, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.<br /><br /> Valeur par défaut : **Windows**|  
|**AlgorithmSuite**|Enum<br /><br /> Pour plus d’informations sur les noms de membre pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans le **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, sécurité**  onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).<br /><br /> Valeur par défaut : **Basic256**|  
|**ClientCertificate**|Chaîne|Spécifiez l'empreinte du certificat X.509 pour l'authentification de ce port d'envoi auprès des services. Cette propriété est requise si le **ClientCredentialsType** est définie sur **certificat**. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**ServiceCertificate**|Chaîne|Spécifiez l'empreinte du certificat X.509 pour l'authentification du service auquel ce port d'envoi envoie des messages. Le certificat à utiliser pour cette propriété doit être installé dans le **autres personnes** stocker dans le **ordinateur Local** emplacement.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**AffiliateApplicationName**|Chaîne|Spécifiez l'application associée à utiliser pour l'authentification unique (SSO) de l'entreprise.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**UseSSO**|Booléen|Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.<br /><br /> Valeur par défaut : **False**|  
|**UserName**|Chaîne|Spécifiez le nom d’utilisateur à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**. Il n'est pas nécessaire de se conformer au format domaine\utilisateur pour cette propriété.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**Mot de passe**|Chaîne|Spécifiez le mot de passe à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.<br /><br /> La valeur par défaut est une chaîne vide.|  
|**OutboundBodyLocation**|Enum<br /><br /> -   **UseBodyElement** -le corps du message BizTalk permet de créer le contenu de SOAP **corps** élément d’un message sortant.<br />-   **UseTemplate** -utiliser le modèle fourni dans le **OutboundXMLTemplate** propriété pour créer le contenu de SOAP **corps** élément d’un message sortant.<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants.<br /><br /> Valeur par défaut : **UseBodyElement**|  
|**OutboundXMLTemplate**|Chaîne<br /><br /> Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).|Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**.<br /><br /> La valeur par défaut est une chaîne vide.|  
  
## <a name="configure-a-wcf-netmsmq-send-port-with-the-biztalk-administration-console"></a>Configurer un Port d’envoi WCF-NetMsmq avec la Console Administration de BizTalk
  
 Vous pouvez définir les variables de l'adaptateur du port d'envoi WCF-NetMsmq dans la console Administration de BizTalk. Si les propriétés ne sont pas définies pour le port d'envoi, les valeurs par défaut pour la configuration du port d'envoi WCF-NetMsmq sont utilisées, comme indiqué dans le tableau précédent.  
  
## <a name="configure-variables-for-a-wcf-netmsmq-send-port"></a>Configurer des variables pour un port d’envoi WCF-NetMsmq  
  
1.  Dans la console Administration de BizTalk, créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **WCF-NetMsmq** pour le **Type** option dans le **Transport** section de la **général** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **général** onglet, configurez l’adresse de point de terminaison, l’identité du service et le **SOAPAction** en-tête pour le Port d’envoi WCF-NetMsmq. Pour plus d’informations sur la **général** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **WCF-NetMsmq Transport boîte de dialogue Propriétés, envoi, général**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
4.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **liaison** onglet, configurez les propriétés de délai d’attente et de transaction et les paramètres de la file d’attente. Pour plus d’informations sur la **liaison** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, liaison**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
5.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **sécurité** onglet, définissez les fonctionnalités de sécurité du port d’envoi WCF-NetMsmq. Pour plus d’informations sur la **sécurité** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, sécurité**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
6.  Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue le **Messages** onglet, spécifiez la sélection de données pour le protocole SOAP **corps** élément. Pour plus d’informations sur la **Messages** onglet dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, Messages**onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
## <a name="configure-a-wcf-netmsmq-send-port-programmatically"></a>Configurer un Port d’envoi WCF-NetMsmq par programme
  
 Vous pouvez utiliser le format suivant pour définir les propriétés :  
  
```  
<CustomProps>  
  <ServiceCertificate vt="8" />  
  <UseSSO vt="11">0</UseSSO>  
  <CloseTimeout vt="8">00:01:00</CloseTimeout>  
  <MessageClientCredentialType vt="8">Windows</MessageClientCredentialType>  
  <SendTimeout vt="8">00:01:00</SendTimeout>  
  <OutboundXmlTemplate vt="8"><bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="xml"/></OutboundXmlTemplate>  
  <MsmqProtectionLevel vt="8">Sign</MsmqProtectionLevel>  
  <OpenTimeout vt="8">00:01:00</OpenTimeout>  
  <UseSourceJournal vt="11">0</UseSourceJournal>  
  <AlgorithmSuite vt="8">Basic256</AlgorithmSuite>  
  <SecurityMode vt="8">Transport</SecurityMode>  
  <CustomDeadLetterQueue vt="8" />  
  <ClientCertificate vt="8" />  
  <MsmqEncryptionAlgorithm vt="8">RC4Stream</MsmqEncryptionAlgorithm>  
  <StaticAction vt="8">http://www.northwindtraders.com/Service/Operation</StaticAction>  
  <MsmqSecureHashAlgorithm vt="8">Sha1</MsmqSecureHashAlgorithm>  
  <EnableTransaction vt="11">-1</EnableTransaction>  
  <TimeToLive vt="8">1.00:00:00</TimeToLive>  
  <MsmqAuthenticationMode vt="8">WindowsDomain</MsmqAuthenticationMode>  
  <DeadLetterQueue vt="8">System</DeadLetterQueue>  
  <OutboundBodyLocation vt="8">UseBodyElement</OutboundBodyLocation>  
</CustomProps>  
  
```  
  
 Le fragment de code suivant illustre la création d'un port d'envoi WCF-NetMsmq :  
  
```  
// Use BizTalk Explorer object model to create new WCF-NetMsmq send port.  
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
sendPort.PrimaryTransport.TransportType = explorer.ProtocolTypes["WCF-NetMsmq"];  
sendPort.PrimaryTransport.Address = "net.msmq://mycomputer/private/samplequeue";  
sendPort.PrimaryTransport.TransportTypeData = transportConfigData; // propertyData; // need to change  
sendPort.SendPipeline = explorer.Pipelines["Microsoft.BizTalk.DefaultPipelines.PassThruTransmit"];  
// Save  
explorer.SaveChanges();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)   
 [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)   
 [Configuration de l’adaptateur WCF-NetMsmq](../core/configuring-the-wcf-netmsmq-adapter.md)   
 [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)