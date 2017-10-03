---
title: "Mise en corrélation des Messages à l’aide de la demande-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MQSeries adapters
- messages, correlating
- MQSeries adapters, correlating messages
ms.assetid: 4615b586-663b-41d8-949c-fefb6143c590
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2f13d8dea9192e982f597311ca3ea13fa213ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlating-messages-using-request-reply"></a>Corrélation de messages dans un scénario de requête-réponse
Les messages peuvent être corrélés de deux manières dans les orchestrations BizTalk pour le composant IBM WebSphere MQ Server dans les scénarios de requête-réponse de plateformes Windows. La première consiste à fournir l’identificateur de corrélation en définissant l’identificateur de message (**MQMD_MSGID**) et l’identificateur de corrélation (**MQMD_CorrelId**) sur la même valeur. La seconde consiste à utiliser le **BizTalk_CorrelationId** propriété de contexte.  
  
## <a name="setting-mqmdmsgid-and-mqmdcorrelid-to-the-same-value"></a>Définition de MQMD_MsgId et MQMD_CorrelId sur la même valeur  
 Lorsque vous envoyez le message à un gestionnaire de file d’attente IBM WebSphere MQ, vous pouvez définir l’identificateur de message (**MQMD_MSGID**) et l’identificateur de corrélation (**MQMD_CorrelId**) sur la même valeur dans le message sortant . Le gestionnaire de file d'attente IBM WebSphere MQ copie l'identificateur de message dans l'identificateur de corrélation pour le message de réponse. La figure suivante illustre le processus.  
  
 ![Corrélation simple](../core/media/bts-dev-mqsimplecorrelation.gif "BTS_Dev_MQSimpleCorrelation")  
  
 Vous pouvez initialiser les ensembles de corrélations pour le message sortant et suivre les ensembles de corrélations pour le message entrant à l’aide de la valeur de **MQMD_CorrelId**.  
  
## <a name="using-the-mqseriesbiztalkcorrelationid-context-property"></a>Utilisation de la propriété de contexte MQSeries.BizTalk_CorrelationId  
 Au lieu de définir le message et corrélation sur la même valeur dans le message sortant, vous pouvez utiliser la **BizTalk_CorrelationID** port de l’adaptateur MQSeries d’envoi de propriété de contexte avec une sollicitation-réponse. Ce processus est représenté dans la figure suivante.  
  
 ![À l’aide de sollicitation &#45; Réponse pour générer CorrelationID](../core/media/bts-dev-mqgeneratedcorrelation.gif "BTS_Dev_MQGeneratedCorrelation")  
  
 Pour utiliser les identificateurs fournis par IBM WebSphere MQ Server pour les corrélations dans votre orchestration BizTalk, BizTalk Server doit d'abord obtenir l'identificateur. Pour ce faire, votre application utilise une demande de sollicitation-réponse. BizTalk Server envoie une demande de sollicitation-réponse au serveur IBM WebSphere MQ Server à l'aide de l'adaptateur MQSeries. En retour, il reçoit une réponse avec l’identificateur de message (**MQMD_MSGId**) et l’identificateur de corrélation (**MQMD_CorrelId**).  
  
 Pour le message sortant dans un port d’envoi de sollicitation-réponse, l’adaptateur copie le **MQMD_MSGID** généré par IBM WebSphere MQ Server dans le **MQSeries.BizTalk_CorrelationId** propriété de contexte.  
  
 Lors de la réception des messages, l’adaptateur copie le **MQMD_CorrelId** à la **MQSeries.BizTalk_CorrelationId**. Dans ce cas, à l’aide des ensembles de corrélations, vous pouvez initialiser les ensembles de corrélations pour le message sortant et suivre les ensembles de corrélations pour le message entrant à l’aide du **MQSeries.BizTalk_CorrelationId**.  
  
## <a name="see-also"></a>Voir aussi  
 [MQSCorrelationSetOrchestrationWithSolicitResponse (exemple BizTalk Server)](../core/mqscorrelationsetorchestrationwithsolicitresponse-biztalk-server-sample.md)