---
title: "Nœuds continuation et ContinuationID | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- continuation tokens
- Continuation nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- BAM, correlating activities
- activities, linking
- activities, continuation tokens
- ContinuationID nodes [Tracking Profile Editor]
ms.assetid: aa050660-66f7-4084-b6bf-b9319ce625af
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8aa8956721d4a44b51b8d2c7776560aaa878f864
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="continuation-and-continuationid-nodes"></a>Nœuds Continuation et ContinuationID
Les continuations assistent l'infrastructure BAM quant aux informations suivantes :  
  
-   L'ordre dans lequel les événements sont censés se produire  
  
-   Une manière de traiter toute modification de l'ID unique avec lequel les éléments d'événement sont corrélés  
  
 Autrement dit, les continuations définissent le transfert de ces informations entre les contributeurs d'une activité. Ce transfert a lieu dans les situations suivantes :  
  
-   Une modification se produit dans l'ActivityID entre le moment où l'activité commence et celui où elle s'achève. Par exemple vous avez deux messages associés tels qu'un numéro de bon de commande et un numéro d'ordre d'achat. Ces numéros sont uniques, par exemple 123456 pour le bon de commande et 987654 pour l'ordre d'achat. Vous utilisez ici une continuation pour mettre en équation les identificateurs uniques du bon de commande et de l'ordre d'achat de sorte que les événements puissent être mis en corrélation avec l'activité commune, quel que soit l'identificateur unique associé aux événements entrants.  
  
-   Il existe une transition d'un environnement d'exécution à l'autre. Par exemple, dans un scénario où vous disposez d’une application qui fournit un bon de commande à un pipeline de messagerie BizTalk Server, qui appelle une orchestration et l’orchestration, puis passe le contrôle à une application qui envoie un avis d’expédition, vous avez deux transitions d’environnement : à partir d’un pipeline de messagerie à un une orchestration et d’une orchestration à un pipeline de messagerie.  
  
 L'un des points importants à retenir lors de la sélection d'une propriété à utiliser pour votre continuation est que les propriétés doivent être mappées à partir du même contexte.  
  
 Par exemple, si vous disposez des propriétés Message.InterchangeID et servicecontext.InterchangeID, vous pourrez probablement utiliser InterchangeID pour créer votre continuation. Si les messages proviennent de contextes différents, vous ne pourrez pas utiliser InterchangeID (ou une autre propriété) pour créer une continuation de manière fiable.  
  
## <a name="working-with-continuation-nodes"></a>Utilisation des nœuds Continuation  
 Le nœud Continuation contient des éléments de données qui indiquent un ID d’instance unique, également appelé un *jeton de continuation*. Grâce au jeton de liaison, les développeurs peuvent établir des liens avec d'autres activités utilisant le nœud ContinuationID.  
  
 On dénombre trois scénarios de base d'utilisation des nœuds Continuation et ContinuationID :  
  
-   Orchestration vers orchestration  
  
-   Orchestration vers solution BizTalk  
  
-   Solution BizTalk vers orchestration  
  
 Dans le scénario « orchestration », l'Éditeur de modèle de suivi doit définir un nœud Continuation et un nœud ContinuationID, et les nœuds doivent porter le même nom afin que l'analyse BAM puisse mettre les activités en corrélation.  
  
 Dans le scénario « orchestration vers solution BizTalk », vous utilisez l'Éditeur de modèle de suivi (TPE) pour définir un nœud Continuation et le développeur crée une solution qui utilise l'API BAM pour gérer la partie destinataire de la continuation.  
  
 Dans « solution BizTalk vers orchestration », le développeur utilise l'API BAM pour fournir l'origine de la paire de continuation et vous utilisez l'Éditeur de modèle de suivi pour définir un nœud ContinuationID.  
  
> [!NOTE]
>  Les ports bidirectionnels peuvent opérer dans les deux sens, ce qui signifie que l'interception des données qui transitent via les ports peut, en fonction du comportement de la solution BizTalk, requérir l'activation d'une continuation. Par exemple, si l'activité enregistre « PortEndTime » pour l'activation d'un port de messagerie BizTalk Server dans les deux sens (si les noms d'élément sont par exemple « MessageReceived » et « MessageSent », dans cet ordre), vous devez créer une continuation entre eux. Une continuation est nécessaire dès que plus d'un flux d'événements contribue à une activité BAM, et on distingue des flux d'événements différents pour chaque point de contact d'implémentation (entrée de la messagerie de BizTalk Server, sortie de la messagerie de BizTalk Server, orchestration, applications personnalisées et services Web).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer une Continuation](../core/how-to-create-a-continuation.md)   
 [Nœuds de l’activité TPE](../core/tpe-activity-view-nodes.md)