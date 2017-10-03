---
title: "Propriétés relatives à BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [MQSeries adapters], properties
- CompleteMessage property [MQSeries adapters]
- SSOAffiliateApplication property [MQSeries adapters]
- Ordered property [MQSeries adapters]
- TransactionSupported property [MQSeries adapters]
- BizTalk_CorrelationID property [MQSeries adapters]
- SegmentationAllowed property [MQSeries adapters]
- DynamicReceive property [MQSeries adapters]
- MQSeries adapters, properties
- DataConversion property [MQSeries adapters]
ms.assetid: c27d7f9c-8198-4624-9952-054ba8ea1c7c
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f729e4ab359471e002029efc04c0c8ad21e0d99b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="properties-related-to-biztalk-server"></a>Propriétés relatives à BizTalk Server
L'adaptateur MQSeries attribue des valeurs à certaines propriétés de contexte qui ne sont pas directement liées à MQSeries mais qui restent utiles dans vos applications.  
  
 Toutes les propriétés reçoivent des valeurs pendant l’envoi et la réception à l’exception de **BizTalk_CorrelationID**. Le **BizTalk_CorrelationID** propriété a une valeur uniquement lors de la réception.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**BizTalk_CorrelationID**|chaîne|Utilisez cette propriété pour que le serveur MQSeries génère un identificateur de corrélation à utiliser avec le message.<br /><br /> Pour plus d’informations, consultez [mise en corrélation de demande-réponse d’à l’aide des Messages](../core/correlating-messages-using-request-reply.md).|  
|**DataConversion**|chaîne|Convertit le message en page de code ANSI du serveur MQSeries pour Windows. Lors de l'envoi, si le format du message est différent de MQFMT_STRING, aucune conversion n'est effectuée.<br /><br /> Sélectionnez **Oui** pour effectuer cette conversion Unicode en ANSI.<br /><br /> **Valeur par défaut :** N°|  
|**Commandée**|chaîne|Définit MQSeries pour qu'il conserve l'ordre des messages au fur et à mesure de leur réception ou de leur envoi depuis la file d'attente MQSeries.<br /><br /> La propriété dispose de différents ensembles de valeurs pour l'envoi et la réception. Pour plus d'informations sur les valeurs, consultez la rubrique [Comment configurer MQSeries adaptateur emplacements de réception et Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).<br /><br /> **Valeur par défaut :** N°|  
|**SegmentationAllowed**|chaîne|Définit MQSeries pour qu'il assemble les messages segmentés ou pour obtenir le message tel quel. La propriété dispose de différents ensembles de valeurs pour l'envoi et la réception.<br /><br /> Lors de la réception, utilisez **No Action** pour lire les messages à partir de la file d’attente MQSeries sans activer la segmentation ; utilisez **Message complet** pour que MQSeries assemble les messages segmentés avant leur transmission à la adaptateur.<br /><br /> **Valeur par défaut :** aucune Action<br /><br /> Lors de l’envoi, sélectionnez **Oui**pour que MQSeries place les messages segmentés dans la file d’attente.<br /><br /> **Valeur par défaut :** N°|  
|**SSOAffiliateApplication**|chaîne|Définir l'application associée à authentification unique. Vous utilisez l’ID utilisateur et un mot de passe de l’authentification unique pour le **MQMD_UserIdentifier**et le **MQIIH_Authenticator** (ou **MQCIH_Authenticator**) propriété respectivement.<br /><br /> Utilisé uniquement lors de l'envoi des messages.<br /><br /> **Valeur par défaut :** vide|  
|**CompleteMessage**|chaîne|Indique s'il faut récupérer les « messages achevés » lors de la récupération des messages segmentés d'une file d'attente.<br /><br /> Affectez la valeur **Oui** pour récupérer les « messages achevés » pour les messages segmentés dans une file d’attente.<br /><br /> **Valeur par défaut :** N°|  
|**DynamicReceive**|chaîne|Indique si les messages doivent être reçus d'une file d'attente de façon dynamique.<br /><br /> Affectez la valeur **Oui** lors de la réception des messages à partir d’une file d’attente dynamique. Cette fonctionnalité est utilisée conjointement avec un port d'envoi de sollicitation-réponse.<br /><br /> Si vous spécifiez les options de correspondance (MessageID, CorrelationID ou GroupID), seuls les messages corrélés aux critères de correspondance seront récupérés.|  
|**TransactionSupported**|chaîne|L'adaptateur commence une transaction DTC (Microsoft Distributed Transaction Coordinator) entre BizTalk Server et le serveur MQSeries. Lorsque la valeur **non**, il n’existe aucune garantie de remise des messages.<br /><br /> **Valeur par défaut :** Oui|  
|**WaitInterval**|chaîne|Indique le délai approximatif (exprimé en secondes) pendant lequel le système MQ attend qu'un message approprié arrive. Si aucun message approprié n'arrive dans ce délai, l'appel échoue. **Remarque :** peut être défini dans une orchestration uniquement. <br /><br /> **Valeur par défaut :** 3|  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md)   
 [Conversion de Type de données de propriétés](../core/data-type-conversion-of-properties.md)   
 [Propriétés de contexte MQSeries](../core/mqseries-context-properties.md)