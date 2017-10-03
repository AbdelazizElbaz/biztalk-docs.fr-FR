---
title: Appel de Back-end incorporation (inlining) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MessageBox database, performance
- service solution tutorial, performance
- performance, in-line invocation
- Inline Invocation of Back-End Processes [service solutions], performance
- performance, MessageBox database
ms.assetid: 991d080f-a4cc-4f14-bab3-3b8b74636daf
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7300429e9f74abc7bc10569c653bdaa0a4c13b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="inlining-back-end-invocation"></a>Appel de Back-end incorporation (inlining)
La version d'appel Inline des solutions complètes offre la durée de traitement la plus courte. Elle élimine la charge de stockage des messages de requête et de réponse vers et à partir des systèmes principaux dans la base de données MessageBox. Dans la version d'adaptateur, le message est acheminé d'une orchestration d'expédition vers MessageBox. L'hôte exécutant l'adaptateur récupère le message, puis l'envoie au processus principal par l'intermédiaire de MessageBox.  
  
 L'efficacité de la version Inline est atteinte en liant l'orchestration directement aux protocoles de transport des systèmes principaux. Dans cette version, l'orchestration ne communique pas par l'intermédiaire de ports logiques : elle appelle les systèmes principaux via trois assemblys personnalisés. Si le transport d'un système principal est modifié, un assembly doit être réécrit puis recompilé. Le tableau suivant décrit ces assemblys et leurs fonctions :  
  
|Nom de l'assembly|Connexion au système principal|  
|-------------------|--------------------------|  
|Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall|Fait appel à MQSeries **obtenir** et **put** fonctions de message.|  
|Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall|Appelle le service Web associé au système de transactions.|  
|Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall|Appelle les services Web simulant un système SAP.|  
  
## <a name="see-also"></a>Voir aussi  
 [Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md)   
 [Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md)   
 [Conversion des modèles de Service, la Solution orientée services](../core/translating-the-patterns-of-the-service-oriented-solution.md)   
 [Le Service d’analyse de la Solution avec BAM orientée services](../core/monitoring-the-service-oriented-solution-with-bam.md)