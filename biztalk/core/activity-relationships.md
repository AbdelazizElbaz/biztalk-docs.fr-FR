---
title: Relations d’activité | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], relationships
ms.assetid: da7c7205-18c6-44df-af03-3140214c84e6
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3709ad02ed082595665c68485502847b52e5a1d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-relationships"></a>Relations d'activité
On parle de relation d'activité quand une activité est associée à une ou plusieurs autres activités. C'est par exemple le cas lorsque plusieurs activités d'expédition sont associées à une activité unique de bon de commande ou quand une activité d'expédition contient des éléments issus de deux activités de bon de commande.  
  
 Pour indiquer que deux activités sont associées, vous devez connaître leurs noms respectifs et avoir les ActivityID correspondants en mémoire pour pouvoir appeler AddRelatedActivity. Cette API crée le lien entre les enregistrements d'activité correspondants.  
  
 Dans le schéma ci-dessous, les lignes de code en surbrillance montrent comment établir une relation entre l'instance d'activité de bon de commande n°123 et les activités d'expédition n°1549, 1550 et 1551.  
  
 ![](../core/media/activity-relationships-example.gif "activity_relationships_example")  
  
 L'utilisateur final du processus d'entreprise voit une page Web où figure l'historique d'un bon de commande. Il peut indiquer qu’à 10 du matin Il arrive, deux jours plus tard, il reçoit l’approbation et la page fournit un lien vers les documents correspondants. En raison du code du schéma ci-dessus, la page indique également des liens hypertexte qui renvoient l'utilisateur final du processus d'entreprise aux pages Web correspondant à l'expédition.  
  
> [!NOTE]
>  Tous les appels à `AddRelatedActivity` doit se produire entre `BeginActivity` et `EndActivity`.  
  
## <a name="see-also"></a>Voir aussi  
  
 [Continuation d’activités](../core/activity-continuation.md)   
 [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md)   
 [API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md)   
 [API BAM à partir d’une Expression d’Orchestration (exemple BizTalk Server)](../core/bam-api-from-an-orchestration-expression-biztalk-server-sample.md)