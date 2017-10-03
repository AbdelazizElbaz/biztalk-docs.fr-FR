---
title: "Conversion des propriétés de Type de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, data type conversion
- MQBYTE property [MQSeries adapters]
- MQLONG property [MQSeries adapters]
- MQCHAR property [MQSeries adapters]
- configuring [MQSeries adapters], data type conversion
ms.assetid: 5b81eab0-f7a1-42f3-b212-a211b2893fd5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3705f1d0a20a48f0683a15588891ef3fe60889cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-conversion-of-properties"></a>Conversion de Type de données de propriétés
Les propriétés d'en-tête d'un message MQSeries constituent des structures de données contenues dans le message lui-même. L'adaptateur MQSeries valide et convertit automatiquement certaines valeurs d'en-têtes de message MQSeries lors de l'envoi et de la réception de messages.  
  
 Le tableau suivant décrit les types de données MQSeries, leur validation et leur conversion.  
  
|Type de données MQSeries|Validation et conversion|  
|------------------------|-------------------------------|  
|MQLONG|MQSeries effectue la validation. Convertit en un nombre entier long. Les valeurs non valides empêchent le placement du message dans la file d'attente MQSeries.|  
|MQCHAR|Convertit en une chaîne.|  
|MQBYTE|Convertit en une chaîne contenant les caractères 0-9 et a-f ou A-F qui représente la valeur hexadécimale du nombre.|  
  
 Un grand nombre de propriétés MQSeries sont des entiers non signés 32 bits (4 octets). Étant donné que **uint** n’est pas une spécification de langage commun (CLS)-type conforme, vous devez les assigner à **objet** types avant de les utiliser dans les méthodes .NET.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md)   
 [Propriétés relatives à BizTalk Server](../core/properties-related-to-biztalk-server.md)   
 [Propriétés de contexte MQSeries](../core/mqseries-context-properties.md)