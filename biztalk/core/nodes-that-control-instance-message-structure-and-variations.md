---
title: "Nœuds contrôlant l’Instance de Structure et les Variations de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af8e6ce-282d-4318-a538-046b423ef033
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: baa82def3f62c6a603ef67e098e53b48a49013a3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="nodes-that-control-instance-message-structure-and-variations"></a>Nœuds contrôlant la structure et les variations de message d'instance
Certains types de nœuds que vous utilisez pour créer des schémas dans l’Éditeur BizTalk contrôlent la structure des messages d’instance et leurs variations. Vous utilisez **groupe séquence** nœuds pour spécifier qu’une séquence d’éléments doit se produire dans un ordre spécifique dans l’emplacement correspondant dans un message d’instance. Vous utilisez **groupe choix** nœuds pour spécifier qu’un élément d’une collection d’éléments peuvent se produire dans l’emplacement correspondant dans un message d’instance. Vous utilisez **groupe tous** nœuds pour spécifier que tous les éléments spécifiés peuvent se produire dans n’importe quel ordre, mais une seule fois, à l’emplacement correspondant dans un message d’instance. **\<Équivalent\>**  nœuds et leurs nœuds enfants sont affichés dans l’arborescence du schéma pour indiquer les emplacements dans les messages de l’instance où le polymorphisme par dérivation est en vigueur, celle qui permet de nombreuses données complexes connexes types se produire dans les emplacement correspondant dans un message d’instance.  
  
 Le reste de cette section propose des informations supplémentaires concernant cette classe de nœuds.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Nœuds Groupe Séquence](../core/sequence-group-nodes.md)  
  
-   [Nœuds Groupe Choix](../core/choice-group-nodes.md)  
  
-   [Nœuds Groupe Tous](../core/all-group-nodes.md)  
  
-   [\<Équivalent\> nœuds et leurs nœuds enfants](../core/equivalent-nodes-and-their-child-nodes.md)