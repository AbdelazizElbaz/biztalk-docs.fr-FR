---
title: "Considérations pour l’analyse BAM Code Maintenance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, code maintenance
- BAMInterceptor class
ms.assetid: e1f1d8e0-207c-47e1-b9bd-a473c86922ce
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f7cfdb75a32c23ef5c8dedec3b6a4c783bf089a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-for-bam-code-maintenance"></a>Considérations relatives à la maintenance du code BAM
Lorsque vous choisissez la manière dont votre application utilise l'analyse BAM, vous devez prendre en considération le fait que les exigences en la matière risquent de changer. Si vous appelez des méthodes sur l'une des classes [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) pour écrire les données surveillées, cela correspond à un codage effectué de manière irréversible du modèle d'observation dans l'application. Si vous devez modifier les données surveillées, vous devez déconnecter l'application, changer le code, procéder à une recompilation de l'application, puis la redéployer une fois celle-ci mise à jour.  
  
 Vous pouvez également instrumenter votre application en appelant des méthodes sur la classe [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) . La classe [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) fait référence à un fichier de configuration pour déterminer les événements et les données à surveiller. À l'aide de la classe [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx) , vous pouvez instrumenter votre code, puis changer les données surveillées en mettant à jour les métadonnées, sans déconnecter l'application.  
  
## <a name="instrumenting-your-application-by-using-the-eventstream-object"></a>Instrumentation de votre application à l'aide de l'objet EventStream  
 Cette approche est plus simple et s'applique aux situations dans lesquelles vous générez une application dédiée en tenant compte de spécifications de surveillance connues et spécifiques. Avant d'opter pour cette approche, vous devez pouvoir répondre aux questions suivantes :  
  
-   Quelles sont les étapes majeures de l'analyse BAM et à quel emplacement dans le code surviennent-elles ?  
  
-   Quelles données seront surveillées ? À quel moment et à quel emplacement dans le code ces données sont-elles disponibles ?  
  
 Si la réponse à l'une de ces questions risque de changer, vous devez envisager d'instrumenter votre application à l'aide de l'objet [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx), à la place.  
  
 Quand vous suivez cette approche du codage effectué de manière irréversible, il suffit d'appeler les méthodes sur les classes [Microsoft.BizTalk.Bam.EventObservation.DirectEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.directeventstream.aspx), [Microsoft.BizTalk.Bam.EventObservation.BufferedEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.bufferedeventstream.aspx), **MessagingEventStream** (à partir des implémentations de pipeline) ou **OrchestrationEventStream** (à partir des implémentations d'orchestration), en fonction de vos besoins.  
  
## <a name="instrumenting-your-application-by-using-the-baminterceptor-object"></a>Instrumentation de votre application à l'aide de l'objet BAMInterceptor  
 Cette approche est à privilégier quand :  
  
-   Vous devez trouver un juste équilibre entre la visibilité des données et les performances de l'application. Vous devez également être en mesure de contrôler les données surveillées au moment de l'exécution.  
  
-   L'application traite des messages XML volumineux dans lesquels des données peuvent s'avérer cruciales pour la surveillance.  
  
-   Il est interdit d'arrêter l'application et de modifier le code pour surveiller d'autres données.  
  
 Avec cette approche, vous instrumentez l'application de façon générique à l'aide des méthodes de la classe [Microsoft.BizTalk.Bam.EventObservation.BAMInterceptor](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.baminterceptor.aspx). En transmettant diverses configurations à l'intercepteur, vous pouvez modifier les données surveillées par l'analyse BAM.  
  
 L'Éditeur de modèle de suivi permet de modifier les données que l'analyse BAM collecte à partir d'une orchestration BizTalk.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide d’une activité](../core/using-an-activity.md)   
 [Quelle est l’intercepteur BAM ?](../core/what-is-the-bam-interceptor.md)   
 [API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md)