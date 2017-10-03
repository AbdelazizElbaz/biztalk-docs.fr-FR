---
title: "Propriétés de contexte MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQCIH_TaskEndStatus property [MQSeries adapters]
- MQIIH_SecurityScope property [MQSeries adapters]
- MQCIH_AbendCode property [MQSeries adapters]
- filters, MQSeries adapters
- MQCIH_ReturnCode property [MQSeries adapters]
- MQCIH_TransactionId property [MQSeries adapters]
- MQCIH_ReplyToFormat property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- MQMD_PutTime property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQMD_PutApplName property [MQSeries adapters]
- configuring [MQSeries adapters], filtering
- MQCIH_UOWControl property [MQSeries adapters]
- MQCIH_ErrorOffset property [MQSeries adapters]
- MQMD_Priority property [MQSeries adapters]
- MQMD_MsgSeqNumber property [MQSeries adapters]
- MQMD_Format property [MQSeries adapters]
- MQCIH_ConversationalTask property [MQSeries adapters]
- Message Descriptor table [MQSeries adapters]
- MQMD_Feedback property [MQSeries adapters]
- MQCIH_Authenticator property [MQSeries adapters]
- MQIIH_TranState property [MQSeries adapters]
- MQCIH_AttentionId property [MQSeries adapters]
- MQMD_UserIdentifier property [MQSeries adapters]
- MQCIH_Flags property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQIIH_Format property [MQSeries adapters]
- MQMD_Offset property [MQSeries adapters]
- MQMD_BackoutCount property [MQSeries adapters]
- MQMD_Report property [MQSeries adapters]
- MQMD_MsgFlags property [MQSeries adapters]
- MQSeries adapters, filtering
- MQMD_ApplIdentityData property [MQSeries adapters]
- MQIIH_Authenticator property [MQSeries adapters]
- MQIIH_MFSMapName property [MQSeries adapters]
- MQCIH_LinkType property [MQSeries adapters]
- MQMD_Persistence property [MQSeries adapters]
- MQCIH_CursorPosition property [MQSeries adapters]
- MQCIH_Format property [MQSeries adapters]
- MQCIH_Facility property [MQSeries adapters]
- MQCIH_CancelCode property [MQSeries adapters]
- MQMD_PutDate property [MQSeries adapters]
- MQCIH_NextTransactionId property [MQSeries adapters]
- MQIIH_CommitMode property [MQSeries adapters]
- MQIIH_ReplyToFormat property [MQSeries adapters]
- MQCIH_Function property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- MQCIH_StartCode property [MQSeries adapters]
- MQMD_Expiry property [MQSeries adapters]
- MQMD_PutApplType property [MQSeries adapters]
- MQCIH_FacilityLike property [MQSeries adapters]
- MQIIH_Flags property [MQSeries adapters]
- MQCIH_CompCode property [MQSeries adapters]
- MQSeries adapters, properties
- MQCIH_FacilityKeepTime property [MQSeries adapters]
- MQMD_ApplOriginData property [MQSeries adapters]
- MQCIH_Reason property [MQSeries adapters]
- MQIIH_LTermOverride property [MQSeries adapters]
- MQMD_CodedCharSetId property [MQSeries adapters]
- MQMD_GroupID property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgType property [MQSeries adapters]
- MQMD_OriginalLength property [MQSeries adapters]
- MQMD_Encoding property [MQSeries adapters]
- MQMD_AccountingToken property [MQSeries adapters]
- MQCIH_OutputDataLength property [MQSeries adapters]
- MQIIH_TranInstanceId property [MQSeries adapters]
- MQCIH_GetWaitInterval property [MQSeries adapters]
- MQCIH_ADSDescriptor property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: 1b22b7d7-432b-4ec5-938c-c43077ce3e0f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d27309379fac2c4821251f27fd2aa5a6e9d59418
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-context-properties"></a>Propriétés de contexte MQSeries
L'adaptateur MQSeries offre un ensemble de propriétés de contexte spécifiques à MQSeries que vous pouvez utiliser dans vos applications, notamment au niveau des expressions de filtre et des orchestrations.  
  
 Pour assigner des propriétés de contexte MQSeries à un message destiné à un port d'envoi lié à l'adaptateur MQSeries, utilisez l'opérateur d'assignation du message et spécifiez l'une des propriétés de contexte disponibles dans l'espace de noms MQSeries.  
  
 Voici un exemple de définition de la MQSeries **MQMD_UserIdentifier** propriété :  
  
```  
Message_2(MQSeries.MQMD_UserIdentifier) = "MeMyselfAndI";  
```  
  
 Vous devez obtenir des valeurs énumérées à partir des fichiers d'en-tête en langage de programmation C, lesquels sont inclus dans le kit de développement IBM MQSeries. Ces fichiers sont accessibles dans le dossier Program Files\IBM\WebSphere MQ\Tools\c\include. Ils définissent les valeurs à utiliser lors de la configuration ou de la lecture des valeurs des propriétés de contexte MQSeries.  
  
 Les valeurs de chaîne hexadécimales constituent des chaînes de caractères représentant des valeurs binaires. Elles ne disposent pas de préfixe tel que 0x. Elles sont constituées de chiffres compris entre 0 et 9 ainsi que de lettres comprises entre « a » et « f » ou « A » et « F ». L'adaptateur ignore les espaces intermédiaires.  
  
 Pour plus d'informations sur ces propriétés, consultez la documentation d'IBM WebSphere MQ.  
  
 Le tableau suivant répertorie l'intégralité des propriétés du descripteur de message (structure MQMD) ainsi que les types et les valeurs qui leur correspondent.  
  
|Nom|Type|Longueur|Valeur|  
|----------|----------|------------|-----------|  
|**MQMD_AccountingToken**|chaîne|64|Chaîne hexadécimale|  
|**MQMD_ApplIdentityData**|chaîne|32|Chaîne hexadécimale|  
|**MQMD_ApplOriginData**|chaîne|4|Chaîne<br /><br /> **Valeur par défaut :** espace|  
|**MQMD_BackoutCount**|nombre entier non signé|4|Number<br /><br /> En lecture seule<br /><br /> **Valeur par défaut :** 0|  
|**MQMD_CodedCharSetId**|nombre entier non signé|4|Number<br /><br /> **Valeur par défaut :** 0|  
|**MQMD_CorrelId**|chaîne|48|Chaîne hexadécimale|  
|**MQMD_Encoding**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête. **Valeur par défaut :** 0|  
|**MQMD_Expiry**|nombre entier non signé|4|Number|  
|**MQMD_Feedback**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête. **Valeur par défaut :** 0|  
|**MQMD_Format**|chaîne|8|Chaîne<br /><br /> Lorsque la propriété est définie sur MQXMIT, vérifiez que les propriétés MQXQH possèdent des valeurs.|  
|**MQMD_GroupID**|chaîne|48|Chaîne hexadécimale|  
|**MQMD_MsgFlags**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête. **Valeur par défaut :** 0|  
|**MQMD_MsgId**|chaîne|48|Chaîne hexadécimale|  
|**MQMD_MsgSeqNumber**|nombre entier non signé|4||  
|**MQMD_MsgType**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête.|  
|**MQMD_Offset**|nombre entier non signé|4||  
|**MQMD_OriginalLength**|nombre entier non signé|4||  
|**MQMD_Persistence**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête.|  
|**MQMD_Priority**|nombre entier non signé|4|Number|  
|**MQMD_PutApplName**|chaîne|28|Chaîne<br /><br /> **Valeur par défaut :** espace|  
|**MQMD_PutApplType**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête. **Valeur par défaut :** 0|  
|**MQMD_PutDate**|chaîne|8|Date|  
|**MQMD_PutTime**|chaîne|8|Time|  
|**MQMD_ReplyToQ**|chaîne|48|Chaîne<br /><br /> **Valeur par défaut :** espace|  
|**MQMD_ReplyToQMgr**|chaîne|48|Chaîne<br /><br /> **Valeur par défaut :** espace|  
|**MQMD_Report**|nombre entier non signé|4|Number<br /><br /> Utilisez la valeur du fichier d'en-tête.|  
|**MQMD_UserIdentifier**|chaîne|12|Chaîne<br /><br /> Contient l’identificateur d’utilisateur lorsque vous utilisez la **SSOAffiliateApplication** propriété.|  
  
 Lors de la réception de messages directement à partir des files d'attente de transmission MQSeries, l'adaptateur MQSeries formate les propriétés d'en-tête d'une file d'attente de transmission (la structure de données MQXQH) et les place dans les propriétés de contexte qui leur correspondent. Lors de l’envoi des messages directement à des files d’attente de transmission MQSeries, les propriétés d’en-tête sont formatées et assignées de valeurs à partir de la correspondant contexte propriétés uniquement si le **MQMD_Format** propriété a la valeur MQXMIT. Le tableau suivant décrit les propriétés.  
  
|Nom|Type|Longueur|Valeur|  
|----------|----------|------------|-----------|  
|**MQXQH_RemoteQMgrName**|chaîne|48|chaîne|  
|**MQXQH_RemoteQName**|chaîne|48|chaîne|  
  
 L'adaptateur renseigne les valeurs du descripteur de message conjointement avec les propriétés décrites précédemment dans cette rubrique d'après les mêmes règles. Il ajoute le préfixe MQXQH_ (au lieu de MQMD_) aux noms des propriétés, car autrement elles mappent directement vers les propriétés définies dans le tableau du descripteur de message :  
  
-   **MQXQH_MsgDesc_AccountingToken**  
  
-   **MQXQH_MsgDesc_ApplIdentityData**  
  
-   **MQXQH_MsgDesc_ApplOriginData**  
  
-   **MQXQH_MsgDesc_BackoutCount**  
  
-   **MQXQH_MsgDesc_CodedCharSetId**  
  
-   **MQXQH_MsgDesc_CorrelId**  
  
-   **MQXQH_MsgDesc_Encoding**  
  
-   **MQXQH_MsgDesc_Expiry**  
  
-   **MQXQH_MsgDesc_Feedback**  
  
-   **MQXQH_MsgDesc_Format**  
  
-   **MQXQH_MsgDesc_MsgId**  
  
-   **MQXQH_MsgDesc_MsgType**  
  
-   **MQXQH_MsgDesc_Persistence**  
  
-   **MQXQH_MsgDesc_Priority**  
  
-   **MQXQH_MsgDesc_PutApplName**  
  
-   **MQXQH_MsgDesc_PutApplType**  
  
-   **MQXQH_MsgDesc_PutDate**  
  
-   **MQXQH_MsgDesc_PutTime**  
  
-   **MQXQH_MsgDesc_ReplyToQ**  
  
-   **MQXQH_MsgDesc_ReplyToQMgr**  
  
-   **MQXQH_MsgDesc_Report**  
  
-   **MQXQH_MsgDesc_UserIdentifier**  
  
 Il existe d'autres propriétés associées à MQSeries qui sont incluses dans le schéma de propriété et qui peuvent être utilisées dans les expressions de filtre. Celles-ci sont décrites dans le tableau suivant.  
  
|Nom|Type|Longueur|Valeur|  
|----------|----------|------------|-----------|  
|**MQCIH_AbendCode**|chaîne|4||  
|**MQCIH_ADSDescriptor**|nombre entier non signé|4||  
|**MQCIH_AttentionId**|chaîne|4||  
|**MQCIH_Authenticator**|chaîne|8|Définir le mot de passe de l’authentification unique lorsque vous utilisez la **SSOAffiliateApplication** propriété. **Remarque :** cette valeur est fixée à vide par l’adaptateur MQSeries si la longueur du mot de passe SSO dépasse 8 caractères.|  
|**MQCIH_CancelCode**|chaîne|4||  
|**MQCIH_CompCode**|nombre entier non signé|4||  
|**MQCIH_ConversationalTask**|nombre entier non signé|4||  
|**MQCIH_CursorPosition**|nombre entier non signé|4||  
|**MQCIH_ErrorOffset**|nombre entier non signé|4||  
|**MQCIH_Facility**|chaîne|16|Chaîne hexadécimale|  
|**MQCIH_FacilityKeepTime**|nombre entier non signé|4||  
|**MQCIH_FacilityLike**|chaîne|4||  
|**MQCIH_Flags**|nombre entier non signé|4||  
|**MQCIH_Format**|chaîne|||  
|**MQCIH_Function**|chaîne|4||  
|**MQCIH_GetWaitInterval**|nombre entier non signé|4||  
|**MQCIH_LinkType**|nombre entier non signé|4||  
|**MQCIH_NextTransactionId**|chaîne|4||  
|**MQCIH_OutputDataLength**|nombre entier non signé|4||  
|**MQCIH_Reason**|nombre entier non signé|4||  
|**MQCIH_ReplyToFormat**|chaîne|||  
|**MQCIH_ReturnCode**|nombre entier non signé|4||  
|**MQCIH_StartCode**|chaîne|4||  
|**MQCIH_TaskEndStatus**|nombre entier non signé|4||  
|**MQCIH_TransactionId**|chaîne|4||  
|**MQCIH_UOWControl**|nombre entier non signé|4||  
|**MQIIH_Authenticator**|chaîne|8|Définir le mot de passe de l’authentification unique lorsque vous utilisez la **SSOAffiliateApplication** propriété. **Remarque :** cette valeur est fixée à vide par l’adaptateur MQSeries si la longueur du mot de passe SSO dépasse 8 caractères.|  
|**MQIIH_CommitMode**|chaîne|||  
|**MQIIH_Flags**|nombre entier non signé|4||  
|**MQIIH_Format**|chaîne|||  
|**MQIIH_LTermOverride**|chaîne|8||  
|**MQIIH_MFSMapName**|chaîne|8||  
|**MQIIH_ReplyToFormat**|chaîne|||  
|**MQIIH_SecurityScope**|chaîne|||  
|**MQIIH_TranInstanceId**|chaîne|32|Chaîne hexadécimale|  
|**MQIIH_TranState**|chaîne|||  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md)   
 [Propriétés relatives à BizTalk Server](../core/properties-related-to-biztalk-server.md)   
 [Conversion de Type de données de propriétés](../core/data-type-conversion-of-properties.md)