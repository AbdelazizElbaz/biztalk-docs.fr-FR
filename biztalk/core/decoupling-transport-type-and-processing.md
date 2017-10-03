---
title: Dissocation du Type de Transport et traitement | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transport types, decoupling processing
- processing, decoupling transport types
- transport types
- transport types, service solutions
- service solution tutorial, MQSeries adapters
- processing, service solutions
- service solution tutorial, decoupling transport type and processing
- correlations, MQSeries adapters
- MQSeries adapters, correlations
- MQSeries adapters, service solutions
ms.assetid: 0b2c733a-e2c7-42ff-a733-f712fde38f7e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b14522c6bbf9393bc22f632c4db5eeb5e4a22a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="decoupling-transport-type-and-processing"></a>Dissocation du type de transport et du traitement
Dans une solution orientée services, le processus d'entreprise et les spécificités de transmission ou de réception des messages ont souvent un fonctionnement bien distinct. Ceci permet de modifier le processus d'entreprise ou la fonctionnalité de messagerie de la solution de façon indépendante.  
  
 La solution orientée services respecte ce principe de conception, à une exception près. Cette section décrit l'exception en question, les alternatives possibles et la structure sélectionnée.  
  
## <a name="correlation-and-the-mqseries-adapter"></a>Corrélation et adaptateur MQSeries  
 Afin d'utiliser l'adaptateur MQSeries, vous ne pouvez pas utiliser les identificateurs de corrélation BizTalk Server standard. En effet, l'identificateur de corrélation est envoyé à un système IBM principal qui possède son propre système d'identificateurs de corrélation. Au lieu de cela, vous devez utiliser le **MQSeries.MQMD_CorrelId** et **MQSeries.MQMD_MsgID** propriétés. afin de placer les informations spécifiques au transport dans l'orchestration et donc, dans le processus d'entreprise.  
  
 Pour gérer cette dépendance, vous pouvez utiliser l'identificateur de corrélation BizTalk Server, ainsi qu'un composant de pipeline personnalisé pour convertir l'identificateur de corrélation pour MQSeries. Cet ajout complexifie le scénario. En outre, si le transport est modifié, deux composants du pipeline doivent l'être également. Enfin, cette opération déplace la dépendance (dans le composant du pipeline) sans la résoudre.  
  
 Une autre option consiste à isoler la gestion de la corrélation spécifique à MQSeries dans une orchestration distincte et d'appeler cette dernière. De cette manière, l'indépendance du processus d'entreprise est préservée. Toutefois, cela provoque une dépendance de compilation entre les orchestrations. La modification du transport nécessite une recompilation des deux orchestrations (par exemple, du stub vers la version de l'adaptateur de la solution). L'appel s'ajoute également au temps de réponse de la solution.  
  
 Étant donné la complexité supplémentaire et la réduction éventuelle des performances, il semble plus simple d'utiliser la corrélation MQSeries directement dans l'orchestration.  
  
 Pour plus d’informations sur la carte et les corrélations dans les orchestrations, consultez [MQSCorrelationSetOrchestration (exemple BizTalk Server)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md)   
 [MQSCorrelationSetOrchestration (exemple BizTalk Server)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)