---
title: "Flux d’événements de messagerie | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2dc56aff-c093-4c79-9cc7-f72079ee927f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d955dbc2b50d1d9c40b54736762fcbaa2bfe536
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messaging-event-streams"></a>Flux d’événements de messagerie
Vous utilisez les flux d’événements de messagerie (MES) lorsque votre application s’exécute sur un ordinateur sur lequel BizTalk Server est installé et que vous assurez le suivi d'éléments qui font partie de transactions de pipelines BizTalk. Grâce aux flux d'événements de messagerie, la persistance de votre événement BAM reste synchronisée avec les transactions de pipelines BizTalk.  
  
 Flux d’événements de messagerie sont des instances d’objets EventStream renvoyés par le [Microsoft.BizTalk.Component.Interop.IPipelineContext.GetEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.ipipelinecontext.geteventstream.aspx) (méthode).  
  
 Les flux d’événements de messagerie sont asynchrones et conservent d’abord les données de suivi dans la base de données BizTalk MessageBox. Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).  
  
 IPipelineContext figure dans le [Microsoft.BizTalk.Component.Interop](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx) espace de noms. Pour utiliser l’API, vous devez ajouter Microsoft.BizTalk.Pipeline (dans microsoft.biztalk.pipeline.dll) à votre projet.  
  
## <a name="see-also"></a>Voir aussi  
 [OrchestrationEventStream](../core/orchestrationeventstream.md)   
 [Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx)   
 [Microsoft.BizTalk.Component.Interop](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx)