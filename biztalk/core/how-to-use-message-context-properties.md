---
title: "Comment utiliser les propriétés de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, building
- building, insufficient configuration
ms.assetid: 6ca95017-74e0-42d7-befa-93e0c1e1ecd1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f5e222567c60596f572412bdcae9aadf6025ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-message-context-properties"></a>Utilisation des propriétés du contexte de message
Les propriétés système sont essentiellement utilisées en interne par le moteur de messagerie de BizTalk Server et ses composants. En général, la modification des valeurs définies par le moteur pour ces propriétés n'est pas conseillée car elle peut affecter la logique d'exécution du moteur. Toutefois, un certain nombre de propriétés peuvent être modifiées.  
  
 Le tableau suivant contient une liste des propriétés du contexte de message que peut promouvoir le moteur de messagerie. Vous pouvez vous servir de ces propriétés pour créer des expressions de filtre sur les ports d'envoi et orchestrations dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Par exemple :  
  
```  
PortName = MyMessage(BTS.ReceivePortName);  
MyFileName = MyMessage(BTS.ReceivedFileName);  
MySubject= MyMessage(POP3.Subject);  
```  
  
 Un tableau distinct répertorie les propriétés supplémentaires qui peuvent être utiles dans certaines applications BizTalk qui ne peuvent être promues.  
  
|Propriété|Moment et emplacement de la promotion|Type| Description|  
|--------------|-----------------------------------|----------|-----------------|  
|BTS.AckFailureCategory|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:int|Identifie la **ErrorCategory**, ce qui donne le lieu et la raison de l’interruption.|  
|BTS.AckFailureCode|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **ErrorCode**, ce qui donne le lieu et la raison de l’interruption.|  
|BTS.AckID|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **MessageID** du message d’origine.|  
|BTS.AckInboundTransportLocation|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **InboundTransportLocation** du message d’origine.|  
|BTS.AckOutboundTransportLocation|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **OutboundTransportLocation** à partir du message d’origine.|  
|BTS.AckOwnerID|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie l’ID d’instance de message d’origine.|  
|BTS.AckReceivePortID|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **ReceivePortID** à partir du message d’origine.|  
|BTS.AckReceivePortName|Promue par le moteur de messagerie pour l'accusé de réception.|xs:string|Identifie la **ReceivePortName** du message d’origine.|  
|BTS.AckSendPortID|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **SendPortID** à partir du message d’origine.|  
|BTS.AckSendPortName|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **SendPortName** à partir du message d’origine.|  
|BTS.AckType|Promue par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Permet la surveillance des accusés de réception et accusés de réception négatifs par une orchestration. La valeur sera l’accusé de réception pour un accusé de réception et un accusé de réception négatif pour un accusé de réception négatif.|  
|BTS.ActionOnFailure|Cette propriété peut être définie par un adaptateur avant d'appeler IBTTTransportBatch::SubmitMessage() API pour soumettre le message à BizTalk.|xs:int|Détermine le comportement du moteur de messagerie en cas de défaillance du pipeline de réception. En principe, le moteur de pessagerie suspend les messages ayant échoué, toutefois certains adaptateurs (comme HTTP) signalent l'échec au client au lieu de suspendre le message en cas de défaillance du pipeline de réception.<br /><br /> Valeurs valides :<br /><br /> -Valeur par défaut. Si la propriété n'existe pas, le moteur de messagerie tente automatiquement de suspendre le message.<br />-   0. Indique que le moteur de messagerie ne doit pas suspendre automatiquement le message.<br /><br /> Les autres valeurs sont réservées pour un usage ultérieur.|  
|BTS.CorrelationToken|Si cette propriété est définie dans le contexte du message, elle est promue par le moteur de messagerie. Cette propriété est définie implicitement sur un contexte lorsque l'adaptateur de requête-réponse ou une orchestration soumet un message de requête dans la base de données MessageBox.|xs:string|Permet le routage de la réponse vers les ports de requête-réponse.|  
|BTS.EpmRRCorrelationToken|Promue par le moteur de messagerie lors de l'exécution du message de requête-réponse. Cette propriété est promue avant que les messages ne soient soumis dans la base de données MessageBox.|xs:int|Utilisée en interne par le moteur de messagerie. Spécifie le nom du serveur, l'ID du processus et un GUID unique pour un flux de requête-réponse de messages.|  
|BTS.InboundTransportLocation|Promue par le moteur de messagerie après la réception d'un message en provenance d'un adaptateur de réception et avant sa publication dans la base de données MessageBox.|xs:string|Spécifie l'emplacement (URI) sur lequel le message a été reçu par le gestionnaire.|  
|BTS.InboundTransportType|Promue par le moteur de messagerie après la réception d'un message en provenance d'un adaptateur de réception et avant sa publication dans la base de données MessageBox.|xs:string|Spécifie le type d’adaptateur qui a reçu ce message et l’a soumis le serveur : fichier, HTTP, etc..|  
|BTS.InterchangeSequenceNumber|Promue par le moteur de messagerie après la réception d'un message en provenance de l'adaptateur de réception et avant sa publication dans la base de données MessageBox.|xs:int|Indique le numéro de séquence du document dans l'échange. Si le document n’est pas partie d’un échange qui a été désassemblé en plusieurs documents, cette valeur sera 1. La propriété peut être lue dans une orchestration, un pipeline d’envoi et de l’adaptateur d’envoi.|  
|BTS.IsDynamicSend|Cette propriété peut être définie dans le contexte de message. Elle ne sera pas promue et ne s'applique qu'aux opérations d'envoi.|xs:boolean|Elle est écrite dans le contexte de message par le moteur de messagerie avec une valeur true lorsque l'opération d'envoi se fait sur un port d'envoi dynamique. Pour définir de manière dynamique des propriétés pour les ports d'envoi statiques des pipelines d'envoi, vous devez définir cette valeur sur true.|  
|BTS.MessageDestination|Cette propriété peut être définie dans le pipeline de réception par un composant de pipeline Désassembleur lorsqu'il retourne un message en provenance de GetNext().|xs:string|Utilisée essentiellement pour prendre en charge le traitement des échanges récupérables dans les désassembleurs, cette propriété détermine si un message est publié dans la boîte de message ou suspendu dans la file d'attente des messages interrompus. Si un pipeline rencontre un message défectueux dans un échange et qu'il souhaite le suspendre et continuer le traitement, il peut le faire en définissant MessageDestination = SuspendQueue et en retournant le message lorsque le moteur appelle GetNext() sur le désassembleur.<br /><br /> Valeurs valides :<br /><br /> -Valeur par défaut. Si la propriété n'existe pas, le message est supposé correct et est publié dans la boîte de message.<br />-SuspendQueue. Indique au moteur de messagerie de suspendre le message. **Remarque :** le message suspendu sera le message post-mappage/post-pipeline et non le message envoyé par l’adaptateur (c'est-à-dire le message réseau).|  
|BTS.MessageType|Promue par les composants du pipeline Désassembleur lors de l'analyse du message.|xs:string|Indique le type du message. Le type de message est défini comme une concaténation de l’espace de noms de schéma document et le nœud racine du document : http://\<*MyNamespace*>#\<*MaRacine*>.|  
|BTS.OutboundTransportLocation|Si cette propriété est définie dans le contexte du message, elle est promue par le moteur de messagerie. Cette propriété est définie implicitement dans un contexte de message lorsqu'une orchestration envoie un message à un port d'envoi. Elle peut également être définie explicitement à partir d'un pipeline ou d'une orchestration.|xs:string|Indique l'URI de l'emplacement de destination auquel le message est envoyé. L’URI peut contenir le préfixe d’adaptateur, tel que **http://**. Le préfixe d'adaptateur est utilisé par le moteur de messagerie pour déterminer le type d'adaptateur à utiliser lors de l'envoi du message. Si les deux le préfixe d’adaptateur et le **BTS. OutboundTransportType** sont définies, le type de carte de **BTS. OutboundTransportType** est toujours prioritaire sur le type d’adaptateur déterminé par le préfixe.<br /><br /> Valeurs valides :<br /><br /> Message Queuing BizTalk : **DIRECT =**, **privé =**, et **PUBLIC =**<br /><br /> FICHIER : **file://**<br /><br /> FTP : **FTP : / /**<br /><br /> HTTP : **http://** et **https://**<br /><br /> SMTP : **mailto :**<br /><br /> SOAP : **SOAP : / /**<br /><br /> SQL : **SQL : / /**|  
|BTS.OutboundTransportType|Si cette propriété est définie dans le contexte du message, elle est promue par le moteur de messagerie. Cette propriété est définie implicitement dans un contexte lorsqu'une orchestration envoie un message à un port d'envoi. Cette propriété peut également être définie explicitement dans une orchestration ou un pipeline.|xs:string|Spécifie le type de l'adaptateur utilisé pour envoyer le message. Les types d’adaptateur disponibles sont **fichier**, **FTP**, **HTTP**, **SMTP**, **SOAP**et **SQL**.<br /><br /> Les valeurs indiquées pour cette propriété, de même que les préfixes d'adaptateur spécifiés dans l'adresse ne respectent pas la casse.|  
|BTS.PropertiesToUpdate|Un adaptateur définit cette propriété lorsqu'il a besoin de préserver certaines valeurs de propriété d'un message ayant échoué qui est soumis à nouveau ou suspendu.<br /><br /> Cela signifie que lorsque le message sera à nouveau soumis ou repris, il sera doté des propriétés définies sur le contexte.|xs:string|Contient une chaîne XML avec des éléments qui représentent les valeurs, les espaces de noms et les noms de propriété.|  
|BTS.ReceivePortID|Promue par le moteur de messagerie après la réception d'un message en provenance d'un adaptateur de réception et avant sa publication dans la base de données MessageBox.|xs:int|Identifie le port de réception sur lequel le message a été reçu.|  
|BTS.ReceivePortName|Promue par le moteur de messagerie après la réception d'un message en provenance d'un adaptateur de réception et avant sa publication dans la base de données MessageBox.|xs:string|Nom convivial du port de réception sur lequel le message a été reçu.|  
|BTS.RouteDirectToTP|Promue par le moteur de messagerie sur les messages de bouclage ou exécution de requête-réponse. Cette propriété est promue avant que les messages ne soient soumis dans la base de données MessageBox.|xs:boolean|Utilisée en interne par le moteur de messagerie pour activer les scénarios de bouclage et de requête-réponse.|  
|BTS.SPGroupID|Promue par le moteur de messagerie lorsque le message est envoyé à un port d'envoi à partir d'une orchestration.|xs:string|Spécifie l'ID du groupe de ports d'envoi.|  
|BTS.SPID|Promue par le moteur de messagerie lorsqu'un message est envoyé à un port d'envoi à partir d'une orchestration.|xs:string|Spécifie l'ID du port d'envoi.|  
|BTS.SPName|Promue par le moteur de messagerie lors de la publication d'une réponse à partir d'un port d'envoi de sollicitation-réponse.|xs:string|Permet de s'abonner aux réponses d'un port d'envoi de sollicitation-réponse. La valeur correspond au nom du port d'envoi.|  
|BTS.SPTransportBackupID|Promue par le moteur de messagerie lorsqu’un message est envoyé à un port d’envoi à partir d’une orchestration.|xs:string|Spécifie l'ID de l'adaptateur de secours dans le port d'envoi.|  
|BTS.SPTransportID|Promue par le moteur de messagerie lorsqu’un message est envoyé à un port d’envoi à partir d’une orchestration.|xs:string|Spécifie l'ID de l'adaptateur principal dans le port d'envoi.|  
|BTS.SuspendAsNonResumable|Cette propriété peut être définie par un adaptateur avant d'appeler SubmitMessage() ou dans une orchestration avant d'envoyer un message à un port d'envoi. **Remarque :** SubmitRequestMessage() ignore cette propriété ; messages bidirectionnels sont toujours suspendus comme non-pouvant être repris.|xs:boolean|Détermine si le moteur de messagerie doit suspendre un message comme ne pouvant être repris en cas d'échec du message. En général, les messages sont suspendus comme pouvant être repris mais cela est parfois inapproprié : par exemple, la reprise d'un message pour un port d'envoi ou de réception chronologique aurait pour effet de rompre la chronologie.<br /><br /> Valeurs valides :<br /><br /> -La valeur est false. Le message est suspendu comme pouvant être repris (valeur par défaut).<br />-La valeur est true. Le message est suspendu comme ne pouvant être repris.|  
|BTS.SuspendMessageOnRoutingFailure|Promue par le moteur de messagerie après la réception d'un message en provenance d'un adaptateur de réception et avant sa publication dans la base de données MessageBox.|xs:boolean|Spécifie le comportement en cas d'échec du routage pour un message entrant.<br /><br /> Valeurs valides :<br /><br /> -Par défaut / False. Si la propriété n'existe pas ou est définie sur False, le moteur signale l'erreur à l'adaptateur en cas d'échec du routage.<br />-La valeur est true. Le moteur de routage suspend automatiquement le message en cas d'échec du routage. **Remarque :** le message suspendu sera le message post-mappage/post-pipeline et non le message envoyé par l’adaptateur (c'est-à-dire le message réseau).|  
  
 Un certain nombre d'autres propriétés de cet espace de noms transportent des informations qui peuvent être utiles pour certaines applications BizTalk.  
  
|Propriété|Moment et emplacement de la promotion|Type| Description|  
|--------------|-----------------------------------|----------|-----------------|  
|BTS.AckDescription|Définie par le moteur de messagerie avant la publication d'un accusé de réception dans la base de données MessageBox.|xs:string|Identifie la **ErrorDescription**, ce qui donne le lieu et la raison de l’interruption.|  
|BTS.EncryptionCert|Ne peut être promue.|xs:int|Identifie l'empreinte correspondant au certificat de chiffrement. Définissez cette propriété dans une orchestration ou un composant de pipeline personnalisé placé avant le composant de pipeline Encodeur MIME/SMIME dans un pipeline afin de réaliser le chiffrement de la réponse sur un port de requête-réponse recevant un message chiffré et signé.|  
|BTS.InterchangeID|Défini par le moteur de messagerie pour chaque message arrivant sur le serveur.|xs:string|Définit l'ID unique utilisé pour grouper les documents provenant du même message d'échange.|  
|BTS.Loopback|Défini par un adaptateur lors de la soumission du message de requête pour l'exécution de la boucle.|xs:boolean|Détermine si le message doit être soumis au serveur pour l'exécution de la boucle. Lors de l'exécution de la boucle, le message de requête est publié dans la base de données MessageBox où il est acheminé directement vers l'adaptateur de réception sous forme de réponse.|  
|BTS.SignatureCertificate|Défini par certains adaptateurs lors de la soumission d'un message dans le serveur. Cette propriété est utilisée par le composant de pipeline Résolution du tiers.|xs:string|Identifie l'empreinte du certificat de signature utilisé pour signer le message reçu par BizTalk Server.|  
|BTS.SourcePartyID|Défini par le composant de pipeline Résolution du tiers une fois que le tiers a été identifié pour le message entrant.|xs:string|ID du tiers BizTalk.|  
|BTS.SSOTicket|Si l'adaptateur de réception prend en charge cette propriété, elle est définie lors de la publication du message sur un serveur.|xs:string|Un ticket contient des informations chiffrées sur le nom d'utilisateur et le domaine de l'utilisateur actuel, ainsi que sur le délai d'expiration du ticket. Le ticket est utilisé par les adaptateurs SSO afin d'obtenir les informations d'identification pour l'utilisateur lors de l'authentification auprès des points de terminaison de destination.|  
|BTS.WindowsUser|Défini par certains adaptateurs lors de la soumission d'un message dans le serveur. Cette propriété est utilisée par le composant de pipeline Résolution du tiers.|xs:string|Spécifie le compte d'un utilisateur au nom duquel le message est soumis au serveur.|  
  
 Pour plus d'informations sur les propriétés et schémas de propriétés associés aux composants de pipeline et adaptateurs, voir les rubriques suivantes :  
  
-   [Propriétés et schéma de propriété de l’adaptateur de fichier](../core/file-adapter-property-schema-and-properties.md)
  
-   [Propriétés et schéma de propriété de l’adaptateur FTP](../core/ftp-adapter-property-schema-and-properties.md)  
  
-   [Propriétés et schéma de propriété de l’adaptateur HTTP](../core/http-adapter-property-schema-and-properties.md)  
  
-   [Propriétés et schéma de propriété d’adaptateur MSMQ](../core/msmq-adapter-property-schema-and-properties.md)  
  
-   [Propriétés et schéma de propriété de l’adaptateur SMTP](../core/smtp-adapter-property-schema-and-properties.md)  
  
-   [Propriétés et schéma de propriété de l’adaptateur SOAP](../core/soap-adapter-property-schema-and-properties.md)  
  
-   [Propriétés et schéma BizTalk Framework](../core/biztalk-framework-schema-and-properties.md)  
  
-   [Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md)  
  
-   [POP3 Propriétés et le schéma de propriété de l’adaptateur](../core/pop3-adapter-property-schema-and-properties.md)  
  
-   [Référence des propriétés de l’adaptateur Windows SharePoint Services](../core/windows-sharepoint-services-adapter-properties-reference.md)  
  
-   [Propriétés et schéma de propriété MIME/SMIME](../core/mime-smime-property-schema-and-properties.md)  
  
-   [Propriétés et schéma de propriété de fichier plat et XML](../core/xml-and-flat-file-property-schema-and-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des propriétés de contexte de Message BizTalk](../core/about-biztalk-message-context-properties.md)   
 [Comment utiliser des Expressions pour affecter des valeurs à des Ports dynamiques](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)