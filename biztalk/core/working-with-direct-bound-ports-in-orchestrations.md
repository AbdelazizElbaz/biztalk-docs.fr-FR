---
title: "Utilisation de Ports à liaison directe dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a37ac0-5131-4d37-b60b-56763c460463
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e7b2b59ccdaa23271ee0707f19f4fd2cddc0508
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-direct-bound-ports-in-orchestrations"></a>Utilisation de ports à liaison directe dans les orchestrations
Il existe trois types de ports à liaison directe : MessageBox, autocorrélation et orchestration partenaire.  
  
 Les ports à liaison directe MessageBox permettent des modèles de conception publication/abonnement. Les messages envoyés sur un port à liaison directe MessageBox sont publiés dans la base de données MessageBox, où les destinataires les récupèrent en fonction des abonnements. Les ports logiques de réception configurés en tant que ports à liaison directe récupèrent les messages directement de la base de donnés MessageBox. Pour l’activation **réception** formes, MessageBox direct lié ports get les messages via des abonnements pour le type de message et l’expression de filtre. Pour l’activation non **réception** formes, MessageBox direct lié ports get les messages via des abonnements pour le type de message et l’ensemble de corrélations.  
  
 Les ports à liaison directe d'autocorrélation vous aident à concevoir une communication asynchrone entre orchestrations. Les messages envoyés à un port à liaison directe d'autocorrélation sont acheminés vers l'instance de l'orchestration qui a créé le point de réception du port à liaison directe autocorrélé.  
  
 Les ports à liaison directe d'orchestration partenaire proposent une communication entre orchestrations. Les messages envoyés sur un port à liaison directe d'orchestration partenaire peuvent être envoyés à une orchestration destinataire prévue, et les messages reçus sur un port à liaison directe d'orchestration partenaire peuvent l'être à partir d'une orchestration d'expédition prévue.  
  
 Même avec une liaison directe, le message semble aller directement d'une orchestration à l'autre. En fait, tout message envoyé par n'importe quel type de port logique transite toujours par la base de données MessageBox. De plus, les ports à liaison directe sont les seuls ports logiques, par conséquent, la liaison logique n'est qu'une fonction de configuration de la conception. Un port à liaison directe ne peut pas être lié à un port physique, et vous pouvez modifier uniquement la configuration de liaison directe au moment de la conception.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment utiliser des Ports à liaison directe MessageBox](../core/how-to-use-messagebox-direct-bound-ports.md)  
  
-   [Ports de liaison de l’utilisation directe d’autocorrélation](../core/how-to-use-self-correlating-direct-bound-ports.md)  
  
-   [Ports de liaison de l’utilisation directe de Orchestration du partenaire](../core/how-to-use-partner-orchestration-direct-bound-ports.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Liaisons de port](../core/port-bindings.md)