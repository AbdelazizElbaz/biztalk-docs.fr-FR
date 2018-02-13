---
title: "Propriétés et schéma de propriété des adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 02/09/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2093745e-86c0-4276-a7cc-a0187391ca4a
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04bb48f54347eabeb886d91fa245bae18c34de55
ms.sourcegitcommit: 50798e04fdcaf5dce5288aa18608e2a981b162fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2018
---
# <a name="wcf-adapters-property-schema-and-properties"></a>Propriétés et schéma de propriété des adaptateurs WCF
Informations sur les propriétés promues dans le schéma de propriété de l’adaptateur WCF. Les adaptateurs WCF attribuent des valeurs aux propriétés que vous pouvez utiliser dans votre application. L'adaptateur WCF offre également un mécanisme permettant d'écrire (mais non de promouvoir) les propriétés personnalisées dans le contexte de message BizTalk et un mécanisme permettant de promouvoir les propriétés personnalisées dans le contexte de message BizTalk. Pour plus d’informations, consultez [les en-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md).  

## <a name="promoted-properties"></a>Propriétés promues  
**Namespace:** http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties  

#### <a name="action"></a>Action
Spécifiez le **SOAPAction** champ d’en-tête pour les messages sortants. Vous pouvez spécifier cette valeur de deux manières différentes : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d’action unique, par exemple, http://contoso.com/Svc/Op1 : le **SOAPAction** en-tête pour les messages sortants sont toujours défini sur la valeur spécifiée dans cette propriété.

Si vous définissez cette propriété dans le format de mappage d’action, sortant **SOAPAction** en-tête est déterminé par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant et le **BTS. Opération** est définie sur Op1, l’adaptateur d’envoi WCF utilise `http://contoso.com/Svc/Op1` pour sortant **SOAPAction** en-tête.

```
<BtsActionMapping>
<Operation Name="Op1" Action="http://contoso.com/Svc/Op1">
<Operation Name="Op2" Action="http://contoso.com/Svc/Op2">
</BtsActionMapping>
```

Si les messages sortants proviennent d’un port d’orchestration, les instances d’orchestration définir dynamiquement le **BTS. Opération** propriété avec le nom de l’opération du port. Si les messages sortants sont acheminés avec le routage basé sur le contenu, vous pouvez définir le **BTS. Opération** propriété dans les composants de pipeline.
Cette propriété est automatiquement promue à partir de messages entrants, avec le format d'action unique.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : WCF tous les adaptateurs d’envoi

#### <a name="affiliateapplicationname"></a>AffiliateApplicationName
Spécifiez l'application associée à utiliser pour l'authentification unique (SSO) de l'entreprise. Cette propriété est requise si le **UseSSO** est définie sur **True**. 

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe

#### <a name="algorithmsuite"></a>AlgorithmSuite
Spécifier les algorithmes de chiffrement et Key Wrap du message. Ces algorithmes sont associés à ceux définis dans la spécification Security Policy Language (WS-SecurityPolicy).

Pour plus d’informations sur les valeurs applicables pour le **AlgorithmSuite** propriété, consultez le **suite d’algorithmes** propriété dans le **boîte de dialogue Propriétés du Transport WCF-NetTcp, envoi, Sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

Type : Chaîne  
Valeur par défaut : **Basic256**  
S'applique à : 

- Adaptateur WCF-BasicHttp
- Adaptateur WCF-NetMsmq
- Adaptateur WCF-NetTcp
- Adaptateur WCF-WSHttp

#### <a name="bindingconfiguration"></a>BindingConfiguration
Spécifiez une chaîne XML avec la  **\<liaison\>**  élément pour configurer différents types de liaisons prédéfinies fournis par Windows Communication Foundation (WCF). Pour plus d'informations sur la liaison fournie par le système et la liaison personnalisée, consultez les rubriques correspondantes de la section Voir aussi.

Exemple :

```
<binding name="wsHttpBinding" transactionFlow="true">
<security><message clientCredentialType="UserName"></security>
</binding>
```

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : l’adaptateur WCF-Custom, l’adaptateur WCF-CustomIsolated

#### <a name="bindingtype"></a>BindingType
Spécifiez le type de liaison à utiliser pour le point de terminaison. Pour plus d’informations sur les valeurs applicables pour le **BindingType** propriété, consultez le **Type de liaison** propriété dans le **boîte boîte de dialogue de propriétés du Transport WCF-Custom, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : l’adaptateur WCF-Custom, l’adaptateur WCF-CustomIsolated

#### <a name="clientcertificate"></a>ClientCertificate
Spécifiez l'empreinte du certificat X.509 pour l'authentification de ce port d'envoi auprès des services. Cette propriété est requise si le **ClientCredentialsType** est définie sur **certificat**. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S'applique à : 

- Adaptateur d'envoi WCF-BasicHttp
- Adaptateur d'envoi WCF-WSHttp
- Adaptateur d’envoi WCF-NetTcp
- Adaptateur d’envoi WCF-NetMsmq

#### <a name="closetimeout"></a>CloseTimeout
Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération de fermeture de canal soit réalisée.

Type : Chaîne  
Valeur par défaut : 00:01:00  
S’applique à : tous les adaptateurs WCF *sauf* WCF-Custom et WCF-CustomIsolated

#### <a name="customdeadletterqueue"></a>CustomDeadLetterQueue
Spécifiez l’adresse URI complète avec le **net.msmq** schéma pour l’emplacement de la file d’attente de lettres mortes par application, où sont placés les messages qui ont expiré ou dont le transfert ou la remise a échoué. Par exemple, net.msmq://localhost/deadLetterQueueName. La file d'attente des messages non distribués fait partie du gestionnaire de file d'attente de l'application émettrice. Elle est réservée aux messages expirés n'ayant pu être remis à leur destinataire. Cette propriété est requise si le **DeadLetterQueue** est définie sur **personnalisé**.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : adaptateur d’envoi WCF-NetMsmq

#### <a name="deadletterqueue"></a>DeadLetterQueue
Spécifiez la file d'attente des messages non distribués vers laquelle seront transférés les messages qui n'ont pas pu être remis à l'application. Pour plus d’informations sur les messages remis à la file d’attente de lettres mortes, consultez le **boîte dialogue de propriétés du Transport WCF-NetMsmq, envoi, liaison** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

Type : Chaîne  
Valeur par défaut : **système**  
S’applique à : adaptateur d’envoi WCF-NetMsmq

#### <a name="disablelocationonfailure"></a>DisableLocationOnFailure
Spécifiez s'il faut désactiver l'emplacement de réception pour lequel le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage. Souhaité définir cette propriété sur **True** quand recevoir les emplacements peuvent être désactivés et le déni de Service (DoS) n’est pas un problème.

Par exemple :  
- Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **netMsmqBinding**.
- Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur les transports en file d’attente, tels que MSMQ.
- Adaptateur WCF-CustomIsolated : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur des transports en file d’attente, tels que MSMQ
- Adaptateur WCF-NetMsmq

Type : booléen  
Valeur par défaut : **False**  
S'applique à :  
- Adaptateur de réception WCF-NetMsmq
- Adaptateur de réception WCF-Custom
- Adaptateur de réception WCF-CustomIsolated

#### <a name="enabletransaction"></a>EnableTransaction
L'effet de cette propriété varie selon l'adaptateur WCF. Pour plus d’informations sur cette propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).

Type : booléen  
S'applique à : 

- Adaptateur WCF-WSHttp
- Adaptateur WCF-NetTcp
- Adaptateur WCF-NetNamedPipe
- Adaptateur WCF-NetMsmq

#### <a name="endpointbehaviorconfiguration"></a>EndpointBehaviorConfiguration
Spécifier une chaîne XML avec la  **\<comportement\>**  élément de la  **\<endpointBehaviors\>**  élément pour configurer les paramètres de comportement d’un Point de terminaison WCF. Pour plus d’informations sur la  **\<endpointBehaviors\>**  élément, consultez la rubrique appropriée dans Voir aussi.

Exemple : 
```
<behavior name="sampleBehavior"><callbackTimeouts/></behavior>
```

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : adaptateur d’envoi WCF-Custom

#### <a name="establishsecuritycontext"></a>EstablishSecurityContext
Spécifiez si le canal de sécurité établit une session sécurisée. Une session sécurisée établit un jeton de contexte de sécurité (SCT, Security Context Token) avant d'échanger les messages d'application.

Type : booléen  
Valeur par défaut : True  
Appliqué aux : l’adaptateur WCF-WSHttp

#### <a name="fromaddress"></a>FromAddress
Indiquez l'adresse du point de terminaison source par le biais duquel les messages WCF entrants sont envoyés. La propriété est automatiquement promue à partir de messages entrants.

Type : Chaîne  
S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq
  
#### <a name="headers"></a>En-têtes
Spécifiez les références de point de terminaison utilisées pour fournir des informations d'adressage supplémentaires au-delà de l'URI. Lorsque cette propriété est utilisée, cette propriété doit avoir la \< **en-têtes** \> élément comme élément racine. Tous les en-têtes d’adresse doivent être placé à l’intérieur de la \< **en-têtes** \> élément. Cette propriété est automatiquement promue pour les messages entrants.

Exemple :
```
<headers>
<Region xmlns="Uri">"String"</Region>
<Member xmlns="Uri">"String"</Member> 
</headers>
```

Type : Chaîne  
S’applique à : tous les adaptateurs WCF
  
#### <a name="identity"></a>Identity
Spécifiez l'identité du service fourni par un emplacement de réception ou attendu par un port d'envoi. Les valeurs qui peuvent être spécifiés pour le **identité** propriété diffèrent en fonction de la configuration de sécurité. Ces paramètres permettent aux clients d'authentifier les services. Lors du processus d'établissement de liaison entre les clients et les services, l'infrastructure WCF (Windows Communication Foundation) garantit que l'identité des services correspond aux valeurs des clients.

Exemple :
```
<identity>
<userPrincipalName value="username@contoso.com"/>
</identity>
```

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : tous les adaptateurs WCF

#### <a name="inboundbodylocation"></a>InboundBodyLocation
Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF entrants. Pour plus d’informations sur l’utilisation de la **InboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).

Type : Chaîne  
Valeur par défaut : UseBodyElement  

    Applicable values are:  
        - UseBodyElement: Use the content of the SOAP **Body** element of an incoming message to create the BizTalk message body part. If the **Body** element has more than one child element, only the first element becomes the BizTalk message body part.
        - UseEnvelope: Create the BizTalk message body part from the entire SOAP **Envelope** of an incoming message.
        - UseBodyPath: Use the body path expression in the **InboundBodyPathExpression** property to create the BizTalk message body part. The body path expression is evaluated against the immediate child element of the SOAP **Body** element of an incoming message. This property is valid only for solicit-response ports.  

S’applique à : tous les adaptateurs WCF *sauf* envoi WCF-NetMsmq  

#### <a name="inboundbodypathexpression"></a>InboundBodyPathExpression
Spécifiez l'expression de chemin de corps afin d'identifier une partie spécifique du message entrant utilisée pour créer le corps du message BizTalk. Cette expression de chemin de corps est évaluée par rapport à l’élément enfant immédiat de SOAP **corps** nœud d’un message entrant. Si cette expression de chemin de corps retourne plusieurs nœuds, seul le premier devient le corps du message BizTalk. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**. Pour plus d’informations sur l’utilisation de la **InboundBodyPathExpression** propriété, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq

#### <a name="inboundheaders"></a>InboundHeaders
Utilisez le **InboundHeaders** propriété pour accéder aux en-têtes SOAP des messages WCF entrants. Les adaptateurs WCF copient toutes les valeurs d'en-tête SOAP des messages entrants dans cette propriété, ce qui inclut les en-têtes SOAP personnalisés et les en-têtes SOAP standard utilisés par l'infrastructure WCF, par exemple, pour WS-Addressing, WS-Security et WS-AtomicTransaction. La valeur contenue dans la propriété de contexte est une chaîne contenant des données XML avec le \< **en-têtes** \> élément racine et les en-têtes SOAP entrants sont copiés comme éléments enfants de la \< **en-têtes** \> élément. Pour plus d’informations sur l’accès aux en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).

Type : Chaîne  
S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq

#### <a name="inboundnodeencoding"></a>InboundNodeEncoding
Spécifiez le type de codage que WCF adaptateur de réception pour décoder le nœud identifié par l’expression de chemin de corps spécifiée dans **InboundBodyPathExpression**. Cette propriété est requise si le **InboundBodyLocation** est définie sur **UseBodyPath**.

Type : Chaîne  
Valeur par défaut : XML  

    Applicable values are:  
        - Base64: Base64 encoding
        - Hex: Hexadecimal encoding
        - String: Text encoding - UTF-8
        - XML: The WCF adapters create the BizTalk message body with the outer XML of the node selected by the body path expression in **InboundBodyPathExpression**.  

S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq

#### <a name="isfault"></a>IsFault
Indiquez si les messages d'erreur SOAP sont reçus. La propriété est automatiquement promue à partir de messages entrants. 

**Remarque**  
Le **IsFault** propriété ne peut pas être utilisée pour vérifier les messages reçus pour les erreurs de transport tels que l’erreur HTTP 404 (fichier ou répertoire introuvable).

Type : booléen  
S’applique à : tous les adaptateurs WCF *sauf* adaptateur d’envoi WCF-NetMsmq

#### <a name="leasetimeout"></a>LeaseTimeout
Spécifiez la durée de vie maximale d'une connexion active placée dans le pool. Une fois le temps spécifié écoulé, la connexion est fermée une fois la demande en cours traitée.

L’adaptateur WCF-NetTcp tire parti du [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) classe pour communiquer avec un point de terminaison. Lorsque vous utilisez la [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087) dans les scénarios de charge équilibrée, réduisez le délai d’expiration du bail par défaut. Pour plus d’informations sur l’équilibrage de charge lorsque vous utilisez la [NetTcpBinding](http://go.microsoft.com/fwlink/?LinkId=81087), consultez la rubrique appropriée dans Voir aussi.

Type : Chaîne  
Valeur par défaut : 00:05:00  
S’applique à : adaptateur de réception WCF-NetTcp  

#### <a name="maxconcurrentcalls"></a>MaxConcurrentCalls
Spécifier le nombre d'appels simultanés par instance de service unique. Les appels excédentaires sont mis en file d'attente. La définition de cette valeur sur 0 équivaut à la définir sur **Int32.MaxValue**. 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi. 

Type : entier  
Valeur par défaut : 200  
S’applique à : WCF tous les adaptateurs de réception *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated

#### <a name="maxconnections"></a>MaxConnections
Spécifier un nombre maximal de connexions que l’écouteur peut mettre en attente d’acceptation par l’application. Lorsque ce quota est dépassé, les nouvelles connexions entrantes sont interrompues plutôt que mises en attente d'acceptation. 

**Remarque**  
Comme il s'agit d'une propriété du gestionnaire d'adaptateur, elle ne peut pas être configurée dans les composants de pipeline et les orchestrations. 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi. 

Type : entier  
Valeur par défaut : 10  
S’applique à : l’adaptateur WCF-NetNamedPipe, l’adaptateur WCF-NetTcp  

#### <a name="maxreceivedmessagesize"></a>MaxReceivedMessageSize
Spécifiez la taille maximale en octets d'un message (en-têtes inclus) et pouvant être reçu sur le câble. La taille des messages est limitée par la quantité de mémoire allouée pour chacun d'eux. Vous pouvez vous servir de cette propriété afin de limiter les expositions aux attaques de type refus de service.

Type : entier  
Valeur par défaut : 65536  
S'applique à : 
- Adaptateur WCF-BasicHttp
- Adaptateur WCF-WSHttp
- Adaptateur WCF-NetTcp
- Adaptateur WCF-NetNamedPipe
- Adaptateur de réception WCF-NetMsmq

#### <a name="messageclientcredentialtype"></a>MessageClientCredentialType
Spécifier le type d'informations d'identification à utiliser lors de l'authentification du client à l'aide de la sécurité basée sur le message.

Les valeurs applicables diffèrent pour chaque adaptateur WCF. Pour plus d’informations sur la **MessageClientCredentialType** propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).

Type : Chaîne  
S'applique à : 
- Adaptateur WCF-BasicHttp
- Adaptateur WCF-WSHttp
- Adaptateur WCF-NetTcp
- Adaptateur WCF-NetNamedPipe

#### <a name="messageencoding"></a>MessageEncoding
Indiquer l’encodeur utilisé pour coder le message SOAP.

Type : Chaîne  
Valeur par défaut : texte  

    Applicable values: 
        - Text: Use a text message encoder
        - Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder  

S’applique à : l’adaptateur WCF-BasicHttp, l’adaptateur WCF-WSHttp


#### <a name="msmqauthenticationmode"></a>MsmqAuthenticationMode
Spécifiez le mode d'authentification du message par le transport MSMQ.

Type : Chaîne  
Valeur par défaut : **WindowsDomain**  
    Pour plus d’informations sur les valeurs applicables pour le **MsmqAuthenticationMode** propriété, consultez le **mode d’authentification MSMQ** propriété dans le **propriétés du Transport WCF-NetMsmq Boîte de dialogue zone, envoi, sécurité** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
S’applique à : l’adaptateur WCF-NetMsmq  

#### <a name="msmqencryptionalgorithm"></a>MsmqEncryptionAlgorithm
Spécifiez l'algorithme à utiliser pour le chiffrement des messages lors de leur transfert entre les gestionnaires de files d'attente. Cette propriété est disponible uniquement si le **MsmqProtectionLevel** est définie sur **EncryptAndSign**.

Type : Chaîne  
Valeur par défaut : **RC4Stream**  

    Applicable values are: RC4Stream, AES

S’applique à : l’adaptateur WCF-NetMsmq  

#### <a name="msmqprotectionlevel"></a>MsmqProtectionLevel
Spécifier le mode de sécurisation des messages au niveau du transport MSMQ.

Type : Chaîne  
Valeur par défaut : **signe**  

    Applicable values are:
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed. To use this protection level, you must enable **Active Directory Integration** for **MSMQ**  

S’applique à : l’adaptateur WCF-NetMsmq  

#### <a name="msmqsecurehashalgorithm"></a>MsmqSecureHashAlgorithm
Spécifiez l'algorithme de hachage à utiliser pour traiter la synthèse du message. Cette propriété n’est pas disponible si le **MsmqProtectionLevel** est définie sur **aucun**.

Type : Chaîne  
Valeur par défaut : **SHA1**  

    Applicable values are: MD5, SHA1, SHA25, SHA512  

S’applique à : l’adaptateur WCF-NetMsmq  

#### <a name="negotiateservicecredential"></a>NegotiateServiceCredential
Spécifiez si les informations d'identification du service sont générées au niveau du client hors bande ou sont obtenues à partir du service sur ce client via un processus de négociation. Une négociation de ce type est un précurseur de l'échange classique des messages.

Si le **MessageClientCredentialType** égal à la propriété **aucun**, **nom d’utilisateur**, ou **certificat**, définir cette propriété sur  **False** implique que le certificat de service est disponible au niveau du client hors bande et que le client spécifier le certificat de service. Ce mode est interopérable avec les piles SOAP qui implémentent WS-Trust et WS-SecureConversation.

Si le **MessageClientCredentialType** est définie sur **Windows**, si cette propriété **False** Spécifie l’authentification Kerberos. Cela implique que le client et le service fassent partie du même domaine Kerberos. Ce mode est interopérable avec les piles SOAP qui implémentent le profil de jeton Kerberos (tel que défini au niveau OASIS WSS TC) ainsi que WS-Trust et WS-SecureConversation.

Lorsque cette propriété est **True**, elle génère une négociation .NET SOAP qui utilise l’échange SPNego sur les messages SOAP.

Type : booléen  
Valeur par défaut : True  
S’applique à : l’adaptateur WCF-WSHttp  

#### <a name="opentimeout"></a>OpenTimeout
Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'ouverture de canal soit réalisée. 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi. 

Type : Chaîne  
Valeur par défaut : 00:01:00  
S’applique à : tous les adaptateurs WCF *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated

#### <a name="orderedprocessing"></a>OrderedProcessing
Spécifier si vous voulez traiter les messages par séries. Lorsque cette propriété est activée, cet emplacement de réception livraison chronologique des messages lorsqu’il est utilisé conjointement avec une orchestration ou la messagerie port d’envoi BizTalk a prend en charge la **livraison chronologique des messages** option définie sur `True`. Pour plus d’informations sur la **livraison chronologique des messages** option, consultez les rubriques correspondantes dans la section Voir aussi.

Cette propriété est applicable dans les cas suivants :
- Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **netMsmqBinding**
- Adaptateur WCF-Custom : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur des transports prenant en charge la livraison chronologique des messages, tels que MSMQ.
- Adaptateur WCF-CustomIsolated : lorsque le **BindingType** est définie sur **customBinding**et le **BindingConfiguration** propriété est configurée pour utiliser des canaux personnalisés qui s’appuient sur les transports prenant en charge la livraison chronologique des messages.
- Adaptateur WCF-NetMsmq

Type : Chaîne  
Valeur par défaut : **False**  
S'applique à : 
- Adaptateur de réception WCF-NetMsmq
- Adaptateur de réception WCF-Custom
- Adaptateur de réception WCF-CustomIsolated

#### <a name="outboundbodylocation"></a>OutboundBodyLocation
Spécifiez la sélection de données pour le protocole SOAP **corps** élément des messages WCF sortants. Pour plus d’informations sur l’utilisation de la **OutboundBodyLocation** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).

Type : Chaîne  
Valeur par défaut : UseBodyElement  

    Applicable values are:
        - UseBodyElement: Use the BizTalk message body part to create the content of the SOAP **Body** element for an outgoing message
        - **UseTem****plate**: Use the template supplied in the OutboundXMLTemplate property to create the content of the SOAP **Body** element for an outgoing message

S’applique à : tous les adaptateurs WCF *sauf* adaptateur de réception WCF-NetMsmq

#### <a name="outboundcustomheaders"></a>OutboundCustomHeaders
Spécifiez les en-têtes SOAP personnalisés pour les messages sortants. Lorsque cette propriété est utilisée, la propriété doit avoir la \< **en-têtes** \> élément comme élément racine. Tous les en-têtes SOAP personnalisés doivent être placés dans le \< **en-têtes** \> élément. Si la valeur d’en-tête SOAP personnalisée est une chaîne vide, vous devez affecter \< **en-têtes**\>\</**en-têtes** \> ou \< **en-têtes** \> à cette propriété. Pour plus d’informations sur l’utilisation des en-têtes SOAP avec les adaptateurs WCF, consultez l’exemple de kit de développement logiciel, à l’aide des en-têtes SOAP personnalisés avec les adaptateurs WCF, à partir de [http://go.microsoft.com/fwlink/?LinkId=79960](http://go.microsoft.com/fwlink/?LinkId=79960).

Type : Chaîne  
S’applique à : tous les adaptateurs WCF *sauf* adaptateur de réception WCF-NetMsmq

#### <a name="outboundxmltemplate"></a>OutboundXmlTemplate
Spécifiez le modèle au format XML pour le contenu de SOAP **corps** élément d’un message sortant. Cette propriété est requise si le **OutboundBodyLocation** est définie sur **UseTemplate**. Pour plus d’informations sur l’utilisation de la **OutboundXMLTemplate** propriété, consultez [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : tous les adaptateurs WCF *sauf* adaptateur de réception WCF-NetMsmq

#### <a name="password"></a>Mot de passe
Spécifiez le mot de passe à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe  

#### <a name="propagatefaultmessage"></a>PropagateFaultMessage
Spécifiez si les messages dont le traitement sortant a échoué sont acheminés ou interrompus. Cette propriété est valide uniquement pour des ports de sollicitation-réponse. 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.

Type : booléen  
Valeur par défaut : **True**  

    Applicable values are:  
        - True: Route the message that fails outbound processing to a subscribing application (such as another receive port or orchestration schedule)
        - False: Suspend failed messages and generate a negative acknowledgment (NACK)

S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetMsmq
  
#### <a name="proxyaddress"></a>ProxyAddress
Indiquer l’adresse du serveur proxy. Utilisez le **https** ou **http** schéma selon la configuration de sécurité. Cette adresse peut être suivie d'un deux-points et du numéro de port. La propriété est requise si le **ProxyToUse** est définie sur **UserSpecified** (par exemple, http://127.0.0.1 : 8080)

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp  

#### <a name="proxypassword"></a>ProxyPassword
Spécifiez le mot de passe à utiliser pour le serveur proxy spécifié dans le **ProxyAddress** propriété.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp

#### <a name="proxytouse"></a>ProxyToUse
Spécifiez le serveur proxy à utiliser pour le trafic HTTP sortant.

Type : Chaîne  
Valeur par défaut : **None**  

    Applicable values are:  
        - None: Do not use a proxy server for this send port
        - Default: Use the proxy settings in the send handler hosting this send port
        - UserSpecified: Use the proxy server specified in the **ProxyAddress** property

S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp  

#### <a name="proxyusername"></a>ProxyUserName
Spécifiez le nom d’utilisateur à utiliser pour le serveur proxy spécifié dans le **ProxyAddress** propriété. La propriété est requise si le **ProxyToUse** est définie sur **UserSpecified**.

Pour plus d’informations sur cette propriété, consultez [comment configurer un Port d’envoi WCF-WSHttp](../core/how-to-configure-a-wcf-wshttp-send-port.md) et [comment configurer un Port d’envoi WCF-BasicHttp](http://msdn.microsoft.com/library/acdb50fa-57fe-4657-9561-b6b2f4919c7f).

Type : Chaîne  
S’applique à : adaptateur d’envoi WCF-BasicHttp, l’adaptateur d’envoi WCF-WSHttp

#### <a name="replytoaddress"></a>ReplyToAddress
Indiquez l'adresse du point de terminaison de réponse pour les messages WCF sortants qui correspondent aux messages entrants reçus par les emplacements de réception de requête-réponse. La propriété est automatiquement promue à partir de messages entrants.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : tous les adaptateurs WCF *sauf* l’adaptateur WCF-NetMsmq

#### <a name="securitymode"></a>SecurityMode
Spécifier le type de sécurité utilisé. Les valeurs applicables diffèrent pour chaque adaptateur WCF. Pour plus d’informations sur la **SecurityMode** propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md). 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi.

Type : Chaîne  
S’applique à : tous les adaptateurs WCF *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated

#### <a name="sendtimeout"></a>SendTimeout
Spécifier une valeur de période qui indique l'intervalle de temps donné pour qu'une opération d'envoi soit réalisée. Cette valeur spécifie une période pour l'exécution de toute l'interaction, même si le correspondant envoie un message volumineux.

Type : Chaîne  
Valeur par défaut : 00:01:00  
S’applique à : tous les adaptateurs WCF *sauf* les adaptateurs WCF-Custom et WCF-CustomIsolated

#### <a name="servicebehaviorconfiguration"></a>ServiceBehaviorConfiguration
Spécifiez une chaîne XML avec la  **\<comportement\>**  élément de la  **\<serviceBehaviors\>**  élément pour configurer les paramètres de comportement d’un service WCF service. Pour plus d’informations sur la  **\<serviceBehaviors\>**  élément, consultez la rubrique appropriée dans Voir aussi.

Exemple :

```
<behavior name="SampleServiceBehavior">
<serviceAuthorization principalPermissionMode="UseAspNetRoles"/>
<serviceCredentials>
<serviceCertificate findValue="539d9ab3089bb6dc187fa7dbb382cf01f8d78f5f" storeLocation="CurrentUser" x509FindType="FindByThumbprint"/>
</serviceCredentials>
<serviceMetadata httpGetEnabled="true"/>
</behavior>
```

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : l’adaptateur WCF-CustomIsolated, l’adaptateur de réception WCF-Custom

#### <a name="servicecertificate"></a>ServiceCertificate
Si cette propriété est utilisée pour les emplacements de réception, spécifiez l'empreinte du certificat X.509 pour les emplacements de réception que les clients utilisent pour authentifier le service. Le certificat à utiliser pour cette propriété doit être installé dans le **mon** stocker dans le **utilisateur actuel** emplacement.

Si cette propriété est utilisée pour les ports d'envoi, spécifiez l'empreinte du certificat X.509 pour l'authentification du service auquel ce port d'envoi envoie des messages. Le certificat à utiliser pour cette propriété doit être installé dans le **autres personnes** stocker dans le **ordinateur Local** emplacement.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S'applique à : 
- Adaptateur WCF-BasicHttp
- Adaptateur WCF-NetMsmq
- Adaptateur WCF-WSHttp
- Adaptateur de réception WCF-NetTcp

#### <a name="suspendmessageonfailure"></a>SuspendMessageOnFailure
Spécifier s'il faut interrompre le message de requête dont le traitement entrant a échoué en raison d'une erreur de pipeline de réception ou d'un échec de routage.

Type : booléen  
Valeur par défaut : True  
S’applique à : WCF tous les adaptateurs de réception  

#### <a name="textencoding"></a>TextEncoding
Spécifier le codage à utiliser pour l’émission de messages sur la liaison de jeu de caractères lors de la **MessageEncoding** est définie sur **texte**. 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi. 

Type : Chaîne  
Valeur par défaut : utf-8  

    Applicable values are:  
        - unicodeFFF: Unicode BigEndian encoding
        - utf-16: 16-bit encoding
        - utf-8: 8-bit encoding

S’applique à : l’adaptateur WCF-BasicHttp, l’adaptateur WCF-WSHttp
  
#### <a name="timetolive"></a>TimeToLive
Spécifiez une durée de validité des messages avant qu'ils ne soient considérés comme expirés et placés dans la file d'attente des messages non distribués. Cette propriété permet de s'assurer que les messages, pour lesquels le temps est un paramètre crucial, ne deviennent pas obsolètes avant leur traitement par un port d'envoi. Tout message d'une file d'attente qui n'aurait pas été utilisé par ce port d'envoi dans le délai spécifié est déclaré comme ayant expiré. Ces messages expirés sont envoyés vers une file d'attente spéciale, appelée file d'attente des messages non distribués. L’emplacement de la file d’attente de lettres mortes est défini avec la **DeadLetterQueue** propriété.

Type : Chaîne  
Valeur par défaut : 1.00:00:00  
S’applique à : adaptateur d’envoi WCF-NetMsmq

#### <a name="to"></a>Pour
Spécifiez l'adresse du point de terminaison de destination pour les messages WCF sortants qu'envoient les ports d'envoi WCF.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : WCF tous les adaptateurs d’envoi  

#### <a name="transactionprotocol"></a>TransactionProtocol
Spécifiez le protocole de transaction à utiliser avec cette liaison. Cette propriété est requise si le **EnableTransaction** est définie sur **True**.

Type : Chaîne  
Valeur par défaut : OleTransaction  

    Applicable values are: OleTransaction, WS-AtomicTransaction

S’applique à : l’adaptateur WCF-NetNamedPipe, l’adaptateur WCF-NetTcp  

#### <a name="transportclientcredentialtype"></a>TransportClientCredentialType
Spécifier le type d'informations d'identification à utiliser lors de l'authentification du port d'envoi. Les valeurs applicables diffèrent pour chaque adaptateur WCF. Pour plus d’informations sur la **TransportClientCredentialType** propriété, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).

Type : Chaîne  
S’applique à : l’adaptateur WCF-Basic, l’adaptateur WCF-NetTcp, l’adaptateur WCF-WSHttp  

#### <a name="transportprotectionlevel"></a>TransportProtectionLevel
Définissez la sécurité au niveau du transport TCP. La signature des messages limite le risque qu'un tiers puisse falsifier le message pendant son transfert. Le chiffrement garantit la confidentialité des données pendant le transport.

Type : Chaîne  
Valeur par défaut : **EncryptAndSign**  

    Applicable values are:  
        - None: No protection
        - Sign: Messages are signed
        - EncryptAndSign: Messages are encrypted and signed

S’applique à : l’adaptateur WCF-NetTcp, l’adaptateur WCF-NetNamedPipe  

#### <a name="username"></a>UserName
Spécifiez le nom d’utilisateur à utiliser pour l’authentification avec le serveur de destination lorsque la **UseSSO** est définie sur **False**. Il n'est pas nécessaire de se conformer au format domaine\utilisateur pour cette propriété.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe

#### <a name="usesourcejournal"></a>UseSourceJournal
Spécifiez si les copies des messages traités par ce port d'envoi doivent être stockées dans la file d'attente des journaux sources.

Type : booléen  
Valeur par défaut : False  
S’applique à : adaptateur d’envoi WCF-NetMsmq  

#### <a name="usesso"></a>UseSSO
Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination. 

**Remarque**  
Cette propriété ne peut pas être suivie dans la base de données d'importation principale BAM avec les modèles de suivi. 

Type : booléen  
Valeur par défaut : False  
S’applique à : WCF tous les adaptateurs d’envoi *sauf* l’adaptateur WCF-NetNamedPipe

#### <a name="referencedbindings"></a>ReferencedBindings
Spécifier les configurations de liaison référencées par le **bindingConfiguration** attribut de la  **\<émetteur\>**  , élément pour les  **wsFederationHttpBinding** et **customBinding**, ce qui indique le Service STS (Security Token) qui émet des jetons de sécurité. Pour plus d’informations sur la  **\<émetteur\>**  élément, consultez la rubrique «\<émetteur\>» à [http://go.microsoft.com/fwlink/?LinkId=83476](http://go.microsoft.com/fwlink/?LinkId=83476).

Les informations de liaison, y compris le  **\<émetteur\>**  , élément pour les **wsFederationHttpBinding** et **customBinding** peut être configuré via la **BindingConfiguration** propriété des adaptateurs WCF-Custom et WCF-CustomIsolated. Toutes les configurations de liaison référencées pour cette propriété doivent être placé dans le formulaire de la [ \<liaisons\> ](http://go.microsoft.com/fwlink/?LinkID=80878) élément. 

**Remarque**  
Le **bindingConfiguration** attribut de la  **\<émetteur\>**  doit faire référence à un nom de liaison valide dans cette propriété. 

**Remarque**  
Le  **\<émetteur\>**  élément dans les configurations de liaison référencées peut également faire référence à une configuration de liaison différents dans cette propriété si cette chaîne de référence n’est pas une dépendance circulaire. 

Exemple : 

```
WCF.BindingConfiguration = @"<wsFederationHttpBinding>
<binding name=""sampleBinding"">
<security mode=""Message"">
<message issuedKeyType=""AsymmetricKey"">
<issuer address=""http://www.contoso.com/samplests"" binding=""wsFederationHttpBinding"" bindingConfiguration=""**contosoSTSBinding**""/>
</message>
</security>
</binding>
</wsFederationHttpBinding>";
WCF.ReferencedBinding =@"<bindings>
<wsFederationHttpBinding>
<binding name=""**contosoSTSBinding**"">
<security mode=""Message"">
<message negotiateServiceCredential=""false"">
<issuer address=""http://northwind.com/samplests"" bindingConfiguration=""**northwindBinding**"" binding=""wsHttpBinding"">
</issuer>
</message>
</security>
</binding>
</wsFederationHttpBinding>
<wsHttpBinding>
<binding name=""**northwindBinding**"">
<security mode=""Message"">
<message clientCredentialType=""Certificate""/>
</security>
</binding>
</wsHttpBinding>
</bindings>" 
``` 

**Remarque**  
**ReferencedBinding** propriété ne doit pas contenir la configuration de liaison utilisée dans les **BindingConfiguration** propriété.

Type : Chaîne  
Valeur par défaut : une chaîne vide  
S’applique à : l’adaptateur WCF-Custom, l’adaptateur WCF-CustomIsolated
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateurs WCF](../core/wcf-adapters.md)   
 [\<comportement\> de \<endpointBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=80879)   
 [\<bindings\>](http://go.microsoft.com/fwlink/?LinkId=80878)   
 [\<comportement\> de \<serviceBehaviors\>](http://go.microsoft.com/fwlink/?LinkId=81095)   
 [Livraison chronologique des Messages](../core/ordered-delivery-of-messages.md)   
 [L’équilibrage de charge](http://go.microsoft.com/fwlink/?LinkId=81089)
