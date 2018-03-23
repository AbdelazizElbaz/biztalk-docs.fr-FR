---
title: Propriétés et schéma de l’infrastructure de BizTalk | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8986e4a7-0c0a-415f-8a74-4fca71d3f1b5
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 992f0fb9c66ee00cf425609db4231a57bf5782c4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="biztalk-framework-schema-and-properties"></a>Schéma et propriétés BizTalk Framework
Le **http://schemas.microsoft.com/BizTalk/2003/btf2-properties** espace de noms contient les propriétés que vous pouvez utiliser pour définir les propriétés de contexte de message et de partie pour le composant de pipeline Désassembleur BizTalk Framework. Le composant de pipeline Désassembleur BizTalk Framework utilise ces propriétés pour générer les en-têtes appropriés dans le message qui est créé. Le tableau suivant décrit les propriétés BizTalk Framework.  

## <a name="properties-list"></a>Liste Propriétés  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**IsReliable**|xs:boolean|Indique si le message BizTalk Framework doit être de nouveau envoyé jusqu'à ce qu'un accusé de réception soit reçu d'une destination. Cette propriété est définie de façon interne par les composants BizTalk Framework et est utilisée par le moteur. Ne faites pas varier la valeur de cette propriété par rapport à votre code.|  
|**PassAckThrough**|xs:boolean|Indique si un message d'accusé de réception doit être transmis par un composant de pipeline Désassembleur BizTalk Framework au lieu d'être utilisé.|  
|**eps_to_address**|xs:string|Spécifie l'adresse de destination.|  
|**eps_to_address_type**|xs:string|Spécifie le type de l'adresse de destination.|  
|**eps_from_address**|xs:string|Spécifie l'adresse source.|  
|**eps_from_address_type**|xs:string|Spécifie le type de l'adresse source.|  
|**prop_identity**|xs:string|Référence URI qui identifie de façon unique le document BizTalk Framework à des fins de journalisation, de suivi, de gestion des erreurs et d'autres critères de corrélation et de traitement des documents.|  
|**prop_sentAt**|xs:string|L'horodatage d'envoi du document BizTalk Framework.|  
|**prop_topic**|xs:string|Référence URI qui identifie de façon unique la finalité globale du document BizTalk Framework.|  
|**svc_deliveryRctRqt_sendTo_address**|xs:string|Spécifie l'adresse à laquelle l'accusé de réception du document BizTalk Framework sera envoyé.|  
|**svc_deliveryRctRqt_sendTo_address_type**|xs:string|Spécifie le type de l'adresse à laquelle l'accusé de réception du document BizTalk Framework devra être envoyé.|  
|**svc_deliveryRctRqt_sendBy**|xs:dateTime|Spécifie la durée (en minutes) passée laquelle l'accusé de réception du document BizTalk Framework doit être reçu.|  
|**svc_commitmentRctRqt_sendTo_address**|xs:string|Spécifie l'adresse à laquelle la notification de la décision du destinataire concernant le traitement de la requête de l'expéditeur doit être envoyée.|  
|**svc_commitmentRctRqt_sendTo_address_type**|xs:string|Spécifie le type d'adresse à laquelle la notification de la décision du destinataire concernant le traitement de la requête de l'expéditeur doit être envoyée.|  
|**svc_commitmentRctRqt_sendBy**|xs:dateTime|Spécifie la durée (en minutes) passée laquelle l'accusé d'engagement du document BizTalk Framework doit être reçu par l'expéditeur.|  
|**prc_type**|xs:string|Fournit une référence URI qui spécifie le type de processus d'entreprise impliqué par le traitement des messages BizTalk Framework.|  
|**prc_instance**|xs:string|Fournit une référence URI qui identifie de façon unique une instance spécifique du processus d'entreprise auquel le document BizTalk Framework est associé.|  
|**deliveryRct_receivedAt**|xs:dateTime|Spécifie l'horodatage de réception du document dont la réception a été accusée par ce reçu. L'horodatage de réception peut refléter soit l'heure à laquelle la première copie a été reçue, soit l'heure à laquelle la copie dont la réception est accusée a été reçue.|  
|**deliveryRct_identity**|xs:string|Spécifie une identité du document BizTalk Framework dont la réception est accusée par l'accusé de réception.|  
|**commitmentRct_identity**|xs:string|Spécifie l'identité d'un document BizTalk Framework dont la réception est accusée par l'accusé d'engagement.|  
|**commitmentRct_decidedAt**|xs:string|Spécifie l'horodatage de décision de traitement du document dont la réception a été accusée par ce reçu.|  
|**commitmentRct_decision**|xs:string|Spécifie la décision actuelle avec des valeurs qui peuvent être aussi bien positives que négatives.|  
|**commitmentRct_commitmentCode**|xs:QName|Spécifie le nom complet (dans XSD) qui spécifie un état plus spécifique concernant la décision de traitement.|  
  
## <a name="see-also"></a>Voir aussi  
-  **Propriétés de contexte de message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]   
-  [Configuration des composants de pipeline natifs](../core/configuring-native-pipeline-components.md)