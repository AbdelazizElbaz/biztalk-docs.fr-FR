---
title: En-têtes personnalisés de l’adaptateur MQSeries | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, custom headers
ms.assetid: b0e18203-a33f-4d50-8483-396699cdff23
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09a05b8c73cd7be84af01eb4465681816e429bc3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-custom-headers"></a>En-têtes personnalisés de l’adaptateur MQSeries
Compte tenu des structures d'en-tête utilisées dans les messages MQSeries, vous devez gérer les en-têtes personnalisés que vous souhaitez utiliser. Les en-têtes personnalisés doivent faire partie du corps d'un message pour éviter toute interférence avec le traitement des en-têtes MQSeries. Veillez à ne pas rétrograder une propriété promue automatiquement. Pour plus d’informations sur les propriétés promues automatiquement, consultez [propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md).  
  
 L'incorporation d'en-têtes personnalisés dans le corps du message nécessite un traitement supplémentaire. Une solution consiste à traiter les en-têtes personnalisés dans les pipelines de l'application. Le pipeline de réception extraie les informations de l'en-tête personnalisé et promeut les informations en tant que propriétés de contexte. De la même manière, le pipeline d'envoi récupère les propriétés de contexte correspondant à l'en-tête personnalisé et rétrograde les propriétés dans le corps du message.  
  
 Pour obtenir un exemple d’utilisation des en-têtes personnalisés dans un composant de pipeline, consultez [MQSSendPipelineComponent (exemple BizTalk Server)](../core/mqssendpipelinecomponent-biztalk-server-sample.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de l’adaptateur MQSeries](../core/mqseries-adapter-properties.md)