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
# <a name="using-an-activity"></a>Utilisation d'une activité
La façon la plus aisée d'utiliser l'analyse BAM consiste à envoyer des étapes majeures ou des données explicites à l'aide de l'API BAM. Vous pouvez vous représenter l'activité BAM comme un enregistrement d'une table SQL que vous maintiendriez en synchronisation avec l'unité de travail en cours.  
  
-   Appelez `BeginActivity` pour chaque nouvelle unité de travail.  
  
-   Appelez `EndActivity` lorsque le travail est terminé et que vous ne prévoyez plus aucun événement dans le contexte de l’unité de travail.  
  
-   Appelez [Microsoft.BizTalk.Bam.EventObservation.EventStream.UpdateActivity](http://msdn.microsoft.com/library/microsoft.biztalk.bam.eventobservation.eventstream.updateactivity.aspx) à des endroits critiques de l’implémentation, pour envoyer des données et étapes majeures qui peuvent être utiles à l’information.  
  
> [!IMPORTANT]
>  Le flux d’événements doit être vidé avant suppression. L'objet EventStream n'effectue pas de vidage automatique des données lorsqu'il est supprimé. Cela signifie que le code que vous écririez normalement, dans lequel vous videz le flux uniquement après avoir terminé de traiter vos activités, peut entraîner une perte de données si une exception se produit préalablement à un appel de vidage.  
>   
>  Pour éviter la perte de données, il est recommandé d'encapsuler le traitement et le vidage dans un bloc try/finally tel qu'illustré dans le pseudo-code ci-dessous :  
  
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
  
 L'exemple de code suivant indique comment vous servir des événements BeginActivity, UpdateActivity et EndActivity lorsque l'unité de travail correspond à un bon de commande. Dans l’exemple, nous supposons que la variable de chaîne **poid** identifie le bon de commande dans le processus actuel :  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’activités BAM avec les flux d’événements](../core/implementing-bam-activities-with-event-streams.md)   
 [Continuation d’activités](../core/activity-continuation.md)   
 [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md)   
 [API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md)