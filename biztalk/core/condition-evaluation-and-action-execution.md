---
title: "Condition d’évaluation et d’exécution d’Action | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Action stage [Business Rules Engine]
- examples, business rules
- Business Rules Engine, policies
- Match stage [Business Rules Engine]
- business rules, examples
- Business Rules Engine, algorithm
- Business Rules Engine, examples
- conflict resolution [Business Rules Engine]
- Business Rules Engine, stages
ms.assetid: dcaa32c2-3403-4f54-92e2-128686bfc193
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2814a97c1907b1bb29eee2a718d04d14cfe901a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="condition-evaluation-and-action-execution"></a>Évaluation de condition et exécution d'action
L'infrastructure des règles d'entreprise fournit un moteur d'inférence très performant, capable de lier des règles à des documents XML, des tables de base de données ou des objets .NET.  
  
 Le moteur des règles d'entreprise utilise un algorithme en trois étapes pour l'exécution des stratégies. Ces trois étapes sont les suivantes :  
  
-   **Correspondance**. À cette étape, les faits sont mis en correspondance avec les prédicats qui utilisent le type de fait (références d'objet conservées dans la mémoire de travail du moteur des règles) en se servant des prédicats définis dans les conditions de règle. Pour des raisons d'efficacité, la mise correspondance avec un modèle est appliquée à toutes les règles de la stratégie et les conditions partagées par ces règles ne sont mises en correspondance qu'une seule fois. Des correspondances de condition partielles peuvent être stockées dans la mémoire de travail pour accélérer les opérations ultérieures de mise en correspondance avec un modèle. Le résultat de la phase de mise en correspondance avec un modèle consiste en des mises à jour de l'agenda du moteur des règles.  
  
-   **Résolution des conflits**. Dans la phase de résolution de conflit, les règles qui sont des candidats pour l’exécution sont examinées pour déterminer l’ensemble suivant de l’exécution des actions de règle basée sur un schéma de résolution prédéterminé. Toutes les règles candidates trouvées lors de l'étape de mise en correspondance sont ajoutées à l'agenda du moteur des règles.  
  
     Le schéma de résolution des conflits par défaut est basé sur des priorités de règle dans une stratégie. La priorité est une propriété configurable d'une règle dans l'Éditeur des règles d'entreprise. Plus le nombre est grand, plus la priorité est élevée. Par conséquent, si plusieurs règles sont déclenchées, les actions ayant la priorité la plus élevée sont exécutées en premier.  
  
-   **Action**. Dans cette étape, les actions de la règle résolue sont exécutées. Notez que des actions de règle peuvent déclarer de nouveaux faits dans le moteur des règles, ce qui engendre la poursuite du cycle. Ceci est également connu sous le nom de chaînage avant. Il est important de noter que l'algorithme ne prévaut jamais sur la règle en cours d'exécution. Toutes les actions de la règle actuellement en cours seront exécutées avant que la phase de correspondance soit répétée. Toutefois, les autres règles de l'agenda ne seront pas déclenchées tant que la phase de correspondance n'aura pas recommencé. La phase de correspondance peut provoquer la suppression des règles de l'agenda avant même leur déclenchement.  
  
 L'exemple suivant illustre l'algorithme en trois étapes (correspondance, résolution des conflits, action).  
  
 **Règle 1 : Évaluation des revenus**  
  
-   Représentation déclarative :  
  
     Un client ne peut prétendre à des conditions de crédit que si son taux de solvabilité est inférieur à 0,2.  
  
-   Représentation IF—THEN à l'aide d'objets métier :  
  
    ```  
    IF Application.Income / Property.Price < 0.2    
    THEN Assert new CreditRating( Application)   
    ```  
  
 **Règle 2 : Évaluer les conditions de crédit**  
  
-   Représentation déclarative :  
  
     Un candidat ne peut être approuvé que si ses conditions de crédit sont supérieures à 725.  
  
-   IF, puis la représentation sous forme de l’utilisation des objets métier :  
  
    ```  
    IF Application.SSN = CreditRating.SSN AND CreditRating.Value > 725    
    THEN SendApprovalLetter(Application)    
    ```  
  
 Les faits sont synthétisés dans le tableau suivant.  
  
|Fait|Champs|  
|----------|------------|  
|Application – Document XML représentant une demande de prêt immobilier|-Income = $65,000<br />-SSN = XXX-XX-XXXX|  
|Property – Document XML représentant le bien acheté|-Prix = $225,000|  
|CreditRating –Document XML contenant les conditions de crédit du candidat|-Valeur = 0-800<br />-SSN = XXX-XX-XXXX|  
  
 L'agenda et la mémoire de travail du moteur de règles sont initialement vides. Une fois que l'application a ajouté les faits Application et Property, l'agenda et la mémoire de travail du moteur de règles sont mis à jour comme suit.  
  
|Mémoire de travail|Agenda|  
|--------------------|------------|  
|-Application<br />-Propriété|Règle 1|  
  
 Règle 1 est ajoutée à l’agenda car sa condition (application.Income/Property.Price / considérée comme < 0,2) évaluée à **true** pendant la phase de correspondance. Aucun fait CreditRating n'est dans la mémoire de travail. La condition de Règle 2 n'a donc pas été évaluée. Dans la mesure où la seule règle présente dans l'agenda est Règle 1, la règle est exécutée, puis disparaît de l'agenda. La seule action définie pour Règle 1 entraîne l'ajout d'un nouveau fait (document CreditRating pour le candidat) dans la mémoire de travail. Lorsque l'exécution de Règle 1 est terminée, le contrôle revient à la phase de correspondance. Dans la mesure où le seul nouvel objet correspondant est le fait CreditRating, le résultat de la phase de correspondance est le suivant.  
  
|Mémoire de travail|Agenda|  
|--------------------|------------|  
|-Application<br />-Propriété<br />-CreditRating|Règle 2|  
  
 À ce stade, Règle 2 est exécutée, ce qui entraîne l'appel d'une fonction qui envoie une lettre d'approbation au candidat. Une fois Règle 2 terminée, l'exécution de l'algorithme à chaînage avant revient à la phase de correspondance. Comme il n'existe plus aucun nouveau fait à mettre en correspondance et que l'agenda est vide, le chaînage avant s'arrête et l'exécution de la stratégie se termine.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de règles](../core/rule-engine.md)