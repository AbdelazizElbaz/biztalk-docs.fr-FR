---
title: "Moteur de règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RuleEngine object
- Business Rules Engine, ruleset executor
- Business Rules Engine, ruleset translator
- Business Rules Engine, ruleset tracking interceptor
- Business Rules Engine, Business Rules Engine
ms.assetid: c4043a1f-357f-47bc-84e1-5e4bd9f8b5b8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0dc2d293697ccbb64851591037440d0371c1346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rule-engine"></a>Moteur de règles
Cette section décrit plusieurs composants, fonctionnalités et fonctionnements du moteur de règles d'entreprise. Le moteur de règles fournit le contexte d'exécution d'un ensemble de règles. Le **RuleEngine** objet pour l’implémentation utilise les composants plug-in suivants :  
  
-   **Exécuteur d’ensemble de règles (moteur d’inférence)**. Implémente l'algorithme responsable de l'évaluation des conditions de règle et de l'exécution des actions. L'exécuteur d'ensemble de règles par défaut est un moteur d'inférence de discrimination en réseau à chaînage avant qui est conçu pour optimiser les opérations en mémoire.  
  
-   **Convertisseur d’ensemble de règles**. Prend comme entrée un **RuleSet** de l’objet et produit une représentation exécutable de l’ensemble de règles. Le convertisseur en mémoire par défaut crée un réseau de discrimination compilé à partir de la définition de l'ensemble de règles.  
  
-   **L’intercepteur de suivi d’ensemble de règles**. reçoit le résultat de l'exécuteur de l'ensemble de règles (moteur d'inférence) et le transmet aux outils de suivi et de contrôle de l'ensemble de règles.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md)  
  
-   [Agenda et priorité](../core/agenda-and-priority.md)  
  
-   [Fonctions de contrôle du moteur](../core/engine-control-functions.md)  
  
-   [Accès aux données dans le moteur de règles d’entreprise](../core/data-access-in-the-business-rule-engine.md)  
  
-   [Action de règle effets](../core/rule-action-side-effects.md)  
  
-   [Prise en charge de l’héritage de classes dans le moteur de règles d’entreprise](../core/support-for-class-inheritance-in-the-business-rule-engine.md)  
  
-   [Paramètres de réglage et de Configuration du moteur de règles](../core/rule-engine-configuration-and-tuning-parameters.md)  
  
-   [Considérations sur les performances lors de l’utilisation du moteur de règles](../core/performance-considerations-when-using-the-rule-engine.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur des règles d’entreprise](../core/business-rules-engine.md)