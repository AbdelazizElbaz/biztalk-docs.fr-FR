---
title: "À l’aide d’une activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e218e2a-27f8-4df2-a1e0-27392112d369
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13b56424e06bdb8fad043acd92c22a88ca19f478
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-an-activity"></a><span data-ttu-id="b6c1e-102">Utilisation d'une activité</span><span class="sxs-lookup"><span data-stu-id="b6c1e-102">Using an Activity</span></span>
<span data-ttu-id="b6c1e-103">La façon la plus aisée d'utiliser l'analyse BAM consiste à envoyer des étapes majeures ou des données explicites à l'aide de l'API BAM.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-103">The simplest way to use BAM is to send explicit milestones or data using the BAM API.</span></span> <span data-ttu-id="b6c1e-104">Vous pouvez vous représenter l'activité BAM comme un enregistrement d'une table SQL que vous maintiendriez en synchronisation avec l'unité de travail en cours.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-104">You can think of the BAM activity as a record in a SQL table that you are keeping in synchronization with the actual unit of work.</span></span>  
  
-   <span data-ttu-id="b6c1e-105">Appelez `BeginActivity` pour chaque nouvelle unité de travail.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-105">Call `BeginActivity` for each new unit of work.</span></span>  
  
-   <span data-ttu-id="b6c1e-106">Appelez `EndActivity` lorsque le travail est terminé et que vous ne prévoyez plus aucun événement dans le contexte de l’unité de travail.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-106">Call `EndActivity` when the work is complete and you expect no more events in the context of this unit of work.</span></span>  
  
-   <span data-ttu-id="b6c1e-107">Appelez [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) à des endroits critiques de l’implémentation, pour envoyer des données et étapes majeures qui peuvent être utiles à l’information.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-107">Call [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) in critical places of the implementation, to send data and milestones that will be useful to the information worker.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b6c1e-108">Le flux d’événements doit être vidé avant suppression.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-108">The Event Stream must be flushed before disposing.</span></span> <span data-ttu-id="b6c1e-109">L'objet EventStream n'effectue pas de vidage automatique des données lorsqu'il est supprimé.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-109">The EventStream object does not perform an automatic flush of the data when disposed.</span></span> <span data-ttu-id="b6c1e-110">Cela signifie que le code que vous écririez normalement, dans lequel vous videz le flux uniquement après avoir terminé de traiter vos activités, peut entraîner une perte de données si une exception se produit préalablement à un appel de vidage.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-110">This means that code you would typically write in which you flush the stream only after you have finished processing your activities can result in data loss if an exception occurs before a call to flush.</span></span>  
>   
>  <span data-ttu-id="b6c1e-111">Pour éviter la perte de données, il est recommandé d'encapsuler le traitement et le vidage dans un bloc try/finally tel qu'illustré dans le pseudo-code ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="b6c1e-111">To avoid data loss, we recommend that you encapsulate the processing and flush in a try/finally block as shown in the pseudo code below:</span></span>  
  
```  
BufferedEventStream es = new BufferedEventStream(…)  
Try  
{  
   // Do the activity processing here.  
}  
Finally  
{  
   if (es != null ) es.Flush();  
}  
```  
  
 <span data-ttu-id="b6c1e-112">L'exemple de code suivant indique comment vous servir des événements BeginActivity, UpdateActivity et EndActivity lorsque l'unité de travail correspond à un bon de commande.</span><span class="sxs-lookup"><span data-stu-id="b6c1e-112">The following example code shows how to do use BeginActivity, UpdateActivity, and EndActivity when the unit of work is a Purchase Order.</span></span> <span data-ttu-id="b6c1e-113">Dans l’exemple, nous supposons que la variable de chaîne **poid** identifie le bon de commande dans le processus actuel :</span><span class="sxs-lookup"><span data-stu-id="b6c1e-113">In the example, we assume that the string variable **poid** identifies the current Purchase Order in process:</span></span>  
  
```  
using Microsoft.BizTalk.BAM.EventObservation;  
...   
EventStream es=new DirectEventStream(connectionString,1);  
...  
// At the beginning of the processing of a new work:  
//    Here poid is a string variable that has the current   
//    Purchase Order identifier (e.g. PO number)  
es.BeginActivity("PurchaseOrder",poid);  
es.UpdateActivity("PurchaseOrder",poid,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
    "CustomerName",""Joe",  
    "CustomerCity","Seattle");  
...  
// few days later  
es.UpdateActivity("PurchaseOrder",poid,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","Widget");  
...  
// and another few days later  
es. UpdateActivity("PurchaseOrder",poid,  
    "POShipped",DateTime.UtcNow);  
...  
// and finally  
es. UpdateActivity("PurchaseOrder",poid,  
    "Delivered",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",poid);  
```  
  
## <a name="see-also"></a><span data-ttu-id="b6c1e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6c1e-114">See Also</span></span>  
 <span data-ttu-id="b6c1e-115">[Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md) </span><span class="sxs-lookup"><span data-stu-id="b6c1e-115">[Implementing BAM Activities with Event Streams](../core/implementing-bam-activities-with-event-streams.md) </span></span>  
 <span data-ttu-id="b6c1e-116">[Continuation d’activités](../core/activity-continuation.md) </span><span class="sxs-lookup"><span data-stu-id="b6c1e-116">[Activity Continuation](../core/activity-continuation.md) </span></span>  
 <span data-ttu-id="b6c1e-117">[Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="b6c1e-117">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 [<span data-ttu-id="b6c1e-118">API BAM (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="b6c1e-118">BAM API (BizTalk Server Sample)</span></span>](../core/bam-api-biztalk-server-sample.md)