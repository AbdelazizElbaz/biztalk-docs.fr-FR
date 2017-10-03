---
title: "POP3 Propriétés et le schéma de propriété de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, POP3 adapters
- Subject properties [POP3 adapters]
- Date properties [POP3 adapters]
- From properties [POP3 adapters]
- To properties [POP3 adapters]
- POP3 adapters, properties
- configuring [POP3 adapters], schemas
- configuring [POP3 adapters], properties
- CC properties [POP3 adapters]
- Headers properties [POP3 adapters]
- ReplyTo properties [POP3 adapters]
- DispositionNotificationTo properties [POP3 adapters]
ms.assetid: 7a10ae1f-dbcf-4c05-9a50-2503895960f9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b976aba7161272ebdc65da2b5bcd2067c8cd3a5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-property-schema-and-properties"></a>POP3 Propriétés et le schéma de propriété de l’adaptateur
Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur POP3.  
  
 **Namespace :** http://schemas.microsoft.com/BizTalk/2003/pop3-properties  
  
|**Nom**|**Type**|**Description**|  
|--------------|--------------|---------------------|  
|**Subject**|xs:string|Spécifie le contenu inséré dans le **sujet** en-tête du message|  
|**From**|xs:string|Spécifie l’adresse de messagerie placé sur le **de** champ d’en-tête du message électronique.|  
|**Pour**|xs:string|Spécifie l’adresse de messagerie ou les adresses placés sur le **à** champ d’en-tête du message électronique.|  
|**ReplyTo**|xs:string|Spécifie l’adresse de messagerie placé sur le **ReplyTo** champ d’en-tête du message électronique.|  
|**CC**|xs:string|Spécifie l’adresse de messagerie ou les adresses placés sur le **CC** champ d’en-tête du message électronique.|  
|**Date**|xs:string|Spécifie le contenu inséré dans le **Date** champ d’en-tête du message électronique.|  
|**DispositionNotificationTo**|xs:string|Spécifie le contenu inséré dans le **DispositionNotificationTo** champ d’en-tête du message électronique.|  
|**En-têtes**|xs:string|Spécifie le contenu de tous les champs d'en-tête du message électronique.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur POP3](../core/configuring-the-pop3-adapter.md)