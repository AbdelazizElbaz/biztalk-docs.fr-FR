---
title: "Convois séquentiels | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- convoy sets
- correlation sets, sequential receive tasks
ms.assetid: f05ff42c-2236-42a3-8166-19700e0c3d97
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 329d0f56d9f092cd146a900c42ed48d5206a6393
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sequential-convoys"></a>Convois séquentiels
Un convoi séquentiel permet à plusieurs messages distincts d'être assemblés afin d'obtenir le résultat souhaité. Il s'agit d'un ensemble de messages associés présentant un ordre prédéfini. Bien que ces messages n'aient pas à être exactement identiques, BizTalk Server doit les recevoir dans un ordre séquentiel.  
  
 Supposons, par exemple, qu'une entreprise de vente au détail en ligne reçoive de nouvelles commandes de la part de clients directs et de revendeurs tout au long de la journée. Toutes les commandes reçues avant 14h doivent être dirigées vers l'entrepôt en un seul lot, et l'ordre de réception de ces commandes doit être respecté. Vous pouvez ainsi accorder la priorité aux premières commandes en cas de rupture de stock d'un produit donné. Vous définissez l'ordre des lots en assemblant toutes les commandes du jour en un seul fichier comportant des informations d'en-tête de lot. À 14h, toutes les commandes du jour partent à l'entrepôt afin d'y être traitées. Toutes les commandes reçues après 14h sont placées dans un nouveau lot de façon à être traitées le jour suivant.  
  
 Ceci est un exemple de processus d'entreprise qui requiert un traitement séquentiel des messages entrants. Ces exigences stipulent que toutes les commandes reçues avant 14h doivent être rassemblées dans un lot. Ceci implique que le premier message reçu démarre une nouvelle instance d'orchestration et initialise un ensemble de corrélations. À ce stade, toutes les autres commandes reçues associées à ce type de message sont acheminées vers l'instance d'orchestration déjà en cours d'exécution. Pour ce faire, vous positionnez un **écouter** forme (contenant une **réception** forme et un **délai** forme) à l’intérieur d’un **boucle** forme. Une fois le délai atteint, la boucle prend fin. Ceci permet la réception d'un nombre inconnu de commandes dans le même processus d'entreprise.  
  
## <a name="implementing-sequential-convoys"></a>Implémentation de convois séquentiels  
 Vous avez la possibilité d'implémenter des convois séquentiels à l'aide du modèle de conception de message « réceptions séquentielles corrélées » dans BizTalk Server. Les réceptions séquentielles corrélées sont des réceptions corrélées à de précédentes réceptions.  
  
 Le traitement en convoi a lieu lorsque les ensembles de corrélations d'une réception sont initialisés par une autre réception.  
  
 Pour les réceptions nécessitant un traitement en convoi, les restrictions suivantes s'appliquent :  
  
-   Les ensembles de corrélations constituant des ensembles de convois séquentiels pour une réception spécifique doivent être initialisés par une réception passée.  
  
-   Le port associé à une réception nécessitant un traitement de convoi séquentiel doit être le port de la réception initialisant l'ensemble de convois. Les convois multiport ne sont pas pris en charge.  
  
-   Le type de message d'une réception nécessitant un traitement en convoi doit correspondre au type de message de la réception initialisant l'ensemble de convois, sauf si l'instruction de réception est exécutée sur un port de livraison chronologique.  
  
-   Toutes les réceptions participant à un convoi séquentiel doivent suivre tous les ensembles de corrélations initialisés (ou suivis) par la réception d'initialisation, sauf si elles sont exécutées sur un port de livraison chronologique.  
  
-   Si un convoi séquentiel est initialisé par une instruction de réception avec activation, cette réception avec activation ne peut pas avoir d'expression de filtre, sauf si elle est exécutée sur un port de livraison chronologique.  
  
-   Si un convoi séquentiel est initialisé par une réception avec activation, les réceptions suivantes ne peuvent pas figurer dans une orchestration imbriquée.  
  
 Pour obtenir un exemple d’implémentation de convoi séquentiel, consultez [Aggregator (exemple BizTalk Server)](../core/aggregator-biztalk-server-sample.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des convois](../core/working-with-convoy-scenarios.md)   
 [Convois parallèles](../core/parallel-convoys.md)