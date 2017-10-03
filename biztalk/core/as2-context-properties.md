---
title: "AS2 Propriétés de contexte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4d63104-f31e-4ed2-b294-ba3ea8a39ae6
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f66fa78b1efb8bd6850e64ba002ecd8e1cb91f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="as2-context-properties"></a>Propriétés de contexte AS2
Dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], cinq types de propriétés de contexte s'appliquent aux messages AS2 :  
  
-   les propriétés de contexte du schéma EdiIntProperties.xsd ;  
  
-   les propriétés de contexte internes à [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ;  
  
-   les propriétés de contexte internes à MIME BizTalk ;  
  
-   les propriétés de contexte internes à AS2 ;  
  
-   les propriétés de contexte internes au rapport d'état AS2.  
  
## <a name="context-properties-in-the-ediintpropertiesxsd-schema"></a>Propriétés de contexte du schéma EdiIntProperties.xsd  
 Les propriétés de contexte de message du schéma de propriété global EDI/INT étant exposées publiquement, vous pouvez les utiliser pour l'acheminement des messages. Elles sont définies dans le fichier EdiIntProperties.xsd dans l'assembly `Microsoft.BizTalk.Edi.BaseArtifacts`. L'espace de noms de ces propriétés est `http://schemas.microsoft.com/BizTalk/2006/as2-properties`. Si elles sont promues, ces propriétés de contexte du message sont disponibles en tant que `EdiIntAS.<Property Name>` dans les **filtres** page de la **propriétés de Port d’envoi** boîte de dialogue.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|AS2From|chaîne|Contient la valeur d’en-tête AS2 AS2-From représentant le nom de l’expéditeur.|  
|AS2PayloadContentType|chaîne|Renferme le type de contenu de la charge du message.|  
|AS2To|chaîne|Contient la valeur d’en-tête AS2 AS2-To représentant le nom du récepteur.|  
|DispositionMode|chaîne|Contient la valeur du mode de disposition du MDN.<br /><br /> Pour qu'un MDN soit généré, vous devez promouvoir les propriétés de contexte DispositionType et celle-ci.|  
|DispositionType|chaîne|Contient la valeur du type de disposition du MDN.<br /><br /> Pour qu'un MDN soit généré, vous devez promouvoir les propriétés de contexte DispositionMode et celle-ci.|  
|IsAS2AsynchronousMdn|boolean|Indique que le message est un MDN asynchrone.|  
|IsAS2FailedMessage|boolean|Indique que le traitement AS2 du message AS2 entrant a échoué, entraînant l'interruption du message de charge.|  
|IsAS2Http200OKResponse|boolean|Définie pour un message qui sera généré en tant que message de réponse HTTP 200 OK. Elle est utilisée lorsqu'aucun MDN n'est généré pour un message AS2 ou lorsque le MDN est envoyé de manière asynchrone.|  
|IsAS2MdnResponseMessage|boolean|Indique que le message est un message de réponse MDN.|  
|IsAS2MessageDuplicate|boolean|Indique que le message AS2 entrant a déjà été reçu précédemment.|  
|IsAS2MessageCompressed|boolean|Indique que le message AS2 entrant a été compressé.|  
|IsAS2MessageEncrypted|boolean|Indique que le message AS2 entrant a été chiffré.|  
|IsAS2MessageSigned|boolean|Indique que le message AS2 entrant a été signé.|  
|IsAS2PayloadMessage|boolean|Indique que le message contient le contenu de message AS2 décodé et qu'il doit donc être traité en tant que charge.|  
|MDNAsyncURI|chaîne|Contient le **Receipt-Delivery-Option** valeur utilisée lors de l’envoi des messages de réponse MDN asynchrones.|  
|MessageId|chaîne|Contient l'ID de message AS2 inclus dans les en-têtes du message AS2.|  
|OriginalMessageId|chaîne|Contient l'ID de message du message AS2 d'origine. Cette propriété de contexte fait partie d'un message MDN et est utilisée à des fins de mise en corrélation des messages AS2 avec leur réponse MDN.|  
|PreservedFileName|chaîne|Contient le nom du fichier d'origine du message. Cette propriété de contexte est uniquement renseignée si le message entrant inclut des informations sur le nom de fichier dans l'en-tête MIME Content-Disposition.|  
|SendMDN|boolean|Cette propriété est définie sur true si un message MDN doit être généré.|  
  
## <a name="context-properties-internal-to-biztalk-server"></a>Propriétés de contexte internes à BizTalk Server  
 Les propriétés de contexte de message suivantes n'étant pas exposées publiquement, vous ne pouvez pas les utiliser pour l'acheminement des messages. Toutefois, elles peuvent être consultées dans les messages interrompus et suivis. L'espace de noms de ces propriétés de contexte est `http://schemas.microsoft.com/BizTalk/2006/system-properties`.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|IgnoreSslCertificateNameMismatchErrors|boolean|Indique au traitement HTTP de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'ignorer les erreurs relatives à l'absence de correspondance dans le nom SSL lors du traitement.|  
|KeepAlive|Booléen|Contrôle le comportement de la fonctionnalité de persistance HTTP.|  
|TreatEPMSuspendAsSuccess|boolean|Indique à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de considérer un message interrompu en tant que message traité correctement lors de son traitement sur une connexion d'entrée HTTP bidirectionnelle.|  
|IsSolicitResponse|boolean|Définie par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ; indique que le message est du type sollicitation-réponse.|  
  
## <a name="context-properties-internal-to-biztalk-mime"></a>Propriétés de contexte internes à BizTalk MIME  
 Les propriétés de contexte de message suivantes n'étant pas exposées publiquement, vous ne pouvez pas les utiliser pour l'acheminement des messages. Toutefois, elles peuvent être consultées dans les messages interrompus et suivis. L'espace de noms de ces propriétés de contexte est `http://schemas.microsoft.com/BizTalk/2006/system-properties`.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|IsMultipartReport|boolean|Provoque la création d'un message de rapport/à parties multiples par l'encodeur MIME [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|SuppressMimeVersionFromMultiPartMessage|boolean|Provoque la suppression de l'en-tête MIME Version de chaque partie d'un message à parties multiples par l'encodeur MIME [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
  
## <a name="context-properties-internal-to-as2"></a>Propriétés de contexte internes à AS2  
 Les propriétés de contexte de message suivantes n'étant pas exposées publiquement, vous ne pouvez pas les utiliser pour l'acheminement des messages. Toutefois, elles peuvent être consultées dans les messages interrompus et suivis. L'espace de noms de ces propriétés de contexte est `http://schemas.microsoft.com/BizTalk/2006/as2-properties`.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|MicHashAlgorithm|chaîne|Contient l'algorithme de hachage utilisé lors du calcul de la valeur de hachage MIC.|  
|ReceivedContentMic|chaîne|Contient la valeur de hachage MIC calculée.|  
  
## <a name="context-properties-internal-to-as2-status-reporting"></a>Propriétés de contexte internes au rapport d'état AS2  
 Les propriétés de contexte de message suivantes n'étant pas exposées publiquement, vous ne pouvez pas les utiliser pour l'acheminement des messages. Toutefois, elles peuvent être consultées dans les messages interrompus et suivis. L'espace de noms de ces propriétés de contexte est `http://schemas.microsoft.com/BizTalk/2006/edi-properties`.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|InterchangeControlNo|chaîne|Numéro de contrôle d'un échange EDI. Cette propriété est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
|InterchangeDate|chaîne|Date d'échange d'un échange EDI. Cette propriété est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
|InterchangeTime|chaîne|Heure d'échange d'un échange EDI. Cette propriété de contexte est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
|ReceiverID|chaîne|ID du récepteur d'un échange EDI. Cette propriété est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
|ReceiverQualifier|chaîne|Qualificateur du récepteur d'un échange EDI. Cette propriété est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
|SenderID|chaîne|ID de l'expéditeur d'un échange EDI. Cette propriété est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
|SenderQualifier|chaîne|Qualificateur d’expéditeur des échanges d’un échange EDI. Cette propriété est lue dans un message lors du codage AS2 ; elle est utilisée pour signaler une activité d'échange AS2.|  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions AS2 BizTalk Server](../core/developing-and-configuring-biztalk-server-as2-solutions.md)