---
title: "Propriétés du descripteur Message TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message descriptor properties
ms.assetid: fc164c12-6dc3-4b74-9aa9-024e18faf80a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80c75875c44c4d082089fc9394fef390a0f91571
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-message-descriptor-properties"></a>Propriétés du descripteur de message TIBCO Enterprise Message Service
Le tableau suivant répertorie l'intégralité des propriétés du descripteur de message (structure TibcoEMSMD), ainsi que les types et les valeurs qui leur correspondent.  
  
|Nom|Type|Valeur|Remarques|  
|----------|----------|-----------|-----------|  
|TibcoEMS .CorrelationID|chaîne|||  
|TibcoEMS .DelieveryMode|chaîne|PERSISENT ou NON-PERSISTENT||  
|TibcoEMS .Destination|chaîne||Lecture seule|  
|TibcoEMS .Expiration|long|||  
|TibcoEMS .MessageID|chaîne||Lecture seule|  
|TibcoEMS .Priority|entier|De 0 à 9||  
|TibcoEMS .Redelivered|boolean||Lecture seule|  
|TibcoEMS .ReplyTo|chaîne|Semblable à la valeur de la propriété Destination||  
|TibcoEMS .Timestamp|long||Lecture seule|  
  
 Les propriétés en lecture seule sont définies par TIBCO Enterprise Message Service lors de la remise du message à l'adaptateur Microsoft BizTalk pour TIBCO EMS. La modification de la valeur (possible dans l'expression de la forme Assignation du message) n'affecte pas le message.  
  
 Pour les autres propriétés qui doivent être déplacées du message EMS vers le message BizTalk Server, vous devez créer un fichier DLL de propriétés à utiliser dans le projet.  
  
 L'exemple de schéma de propriété suivant permet à l'orchestration d'utiliser la propriété de message `JMSXDeliveryCount`.  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://schemas.microsoft.com/BizTalk/TibcoEMS-properties" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
        <xs:appinfo>  
            <b:schemaInfo schema_type="property" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" />  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="JMSXDeliveryCount" type="xs:long">  
        <xs:annotation>  
            <xs:appinfo>  
                <b:fieldInfo propertyGuid="f62f1a4b-a528-45fb-b1f8-bd880e9f46db" />  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>   
```  
  
 Vérifiez que l'espace de noms cible est utilisé. Seules les propriétés qui utilisent cet espace de noms sont copiées dans le message BizTalk Server ou le message EMS. Pour plus d'informations sur les propriétés de contexte de message, consultez la documentation de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de contexte de message](../core/message-context-properties2.md)