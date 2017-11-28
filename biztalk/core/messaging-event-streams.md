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
# <a name="messaging-event-streams"></a><span data-ttu-id="9cfc5-102">Flux d’événements de messagerie</span><span class="sxs-lookup"><span data-stu-id="9cfc5-102">Messaging Event Streams</span></span>
<span data-ttu-id="9cfc5-103">Vous utilisez les flux d’événements de messagerie (MES) lorsque votre application s’exécute sur un ordinateur sur lequel BizTalk Server est installé et que vous assurez le suivi d'éléments qui font partie de transactions de pipelines BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9cfc5-103">You use Messaging Event Streams (MES) when your application runs on a computer on which BizTalk Server is installed and you are you are tracking items that are part of BizTalk pipeline transactions.</span></span> <span data-ttu-id="9cfc5-104">Grâce aux flux d'événements de messagerie, la persistance de votre événement BAM reste synchronisée avec les transactions de pipelines BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9cfc5-104">Using MES ensures that your BAM event persistence remains in sync with the BizTalk pipeline transactions.</span></span>  
  
 <span data-ttu-id="9cfc5-105">Flux d’événements de messagerie sont des instances d’objets EventStream renvoyés par le [Microsoft.BizTalk.Component.Interop.IPipelineContext.GetEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.ipipelinecontext.geteventstream.aspx) (méthode).</span><span class="sxs-lookup"><span data-stu-id="9cfc5-105">Messaging Event Streams are instances of EventStream objects returned by the [Microsoft.BizTalk.Component.Interop.IPipelineContext.GetEventStream](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.ipipelinecontext.geteventstream.aspx) method.</span></span>  
  
 <span data-ttu-id="9cfc5-106">Les flux d’événements de messagerie sont asynchrones et conservent d’abord les données de suivi dans la base de données BizTalk MessageBox.</span><span class="sxs-lookup"><span data-stu-id="9cfc5-106">Messaging Event Streams are asynchronous and store tracking data first in the BizTalk MessageBox database.</span></span> <span data-ttu-id="9cfc5-107">Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).</span><span class="sxs-lookup"><span data-stu-id="9cfc5-107">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
 <span data-ttu-id="9cfc5-108">IPipelineContext figure dans le [Microsoft.BizTalk.Component.Interop](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx) espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9cfc5-108">IPipelineContext is found in the [Microsoft.BizTalk.Component.Interop](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx) namespace.</span></span> <span data-ttu-id="9cfc5-109">Pour utiliser l’API, vous devez ajouter Microsoft.BizTalk.Pipeline (dans microsoft.biztalk.pipeline.dll) à votre projet.</span><span class="sxs-lookup"><span data-stu-id="9cfc5-109">To use the API you must add the Microsoft.BizTalk.Pipeline (in microsoft.biztalk.pipeline.dll) to your project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cfc5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9cfc5-110">See Also</span></span>  
 <span data-ttu-id="9cfc5-111">[OrchestrationEventStream](../core/orchestrationeventstream.md) </span><span class="sxs-lookup"><span data-stu-id="9cfc5-111">[OrchestrationEventStream](../core/orchestrationeventstream.md) </span></span>  
 <span data-ttu-id="9cfc5-112">[Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) </span><span class="sxs-lookup"><span data-stu-id="9cfc5-112">[Microsoft.BizTalk.Bam.EventObservation.EventStream](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.aspx) </span></span>  
 [<span data-ttu-id="9cfc5-113">Microsoft.BizTalk.Component.Interop</span><span class="sxs-lookup"><span data-stu-id="9cfc5-113">Microsoft.BizTalk.Component.Interop</span></span>](http://msdn.microsoft.com/library/microsoft.biztalk.component.interop.aspx)