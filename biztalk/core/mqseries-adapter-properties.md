---
title: "Propriétés de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQXQH_MsgDesc_ReplyToQMgr property [MQSeries adapters]
- UserHttpHeaders property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQXQH_MsgDesc_MsgId property [MQSeries adapters]
- MQXQH_MsgDesc_ReplyToQ property [MQSeries adapters]
- SubmissionHandle property [MQSeries adapters]
- BizTalk_CorrelationID property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- EnableChunkedEncoding property [MQSeries adapters]
- MQSeries adapters, properties
- MQXQH_MsgDesc_CorrelId property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: c3cfbc8c-4c9b-431e-b0b6-4c065a69ce6b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fae8cc1ed67f077b6ae12945da10c58cf0f147da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-properties"></a>Propriétés de l’adaptateur MQSeries
Pour accéder aux propriétés d'en-tête MQSeries depuis une orchestration BizTalk, vous devez ajouter une référence à l'assembly MQSeries.dll dans votre projet. Cet assembly est situé à l'emplacement d'installation de l'adaptateur MQSeries (par exemple, [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).  
  
 Une fois le schéma de propriété MQSeries référencé, les propriétés de contexte supplémentaires sont disponibles pour les divers outils de développement BizTalk Server (par exemple, le **assignation du Message** forme dans le Concepteur d’Orchestration).  
  
> [!NOTE]
>  Veillez à suivre les instructions de la documentation IBM WebSphere MQ lorsque vous utilisez les propriétés d'en-tête MQSeries.  
  
 L'adaptateur promeut automatiquement certaines propriétés MQSeries. Vos applications et composants personnalisés doivent éviter de rétrograder ces propriétés. Vous pouvez promouvoir d'autres propriétés à l'aide de composants de pipeline personnalisés. Les propriétés suivantes sont promues automatiquement :  
  
-   **BizTalk_CorrelationID**  
  
-   **MQMD_CorrelId**  
  
-   **MQMD_MsgId**  
  
-   **MQMD_ReplyToQ**  
  
-   **MQMD_ReplyToQMgr**  
  
-   **MQXQH_RemoteQMgrName**  
  
-   **MQXQH_RemoteQName**  
  
-   **MQXQH_MsgDesc_CorrelId**  
  
-   **MQXQH_MsgDesc_MsgId**  
  
-   **MQXQH_MsgDesc_ReplyToQ**  
  
-   **MQXQH_MsgDesc_ReplyToQMgr**  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Conversion de Type de données de propriétés](../core/data-type-conversion-of-properties.md)  
  
-   [Propriétés relatives à BizTalk Server](../core/properties-related-to-biztalk-server.md)  
  
-   [Propriétés de contexte MQSeries](../core/mqseries-context-properties.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur MQSeries](../core/configuring-the-mqseries-adapter.md)