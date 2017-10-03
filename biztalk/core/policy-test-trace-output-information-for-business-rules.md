---
title: "Informations de sortie de Trace de Test de stratégie pour des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, business rules
- testing, policies
- business rules, testing
- policies, testing
ms.assetid: 26ff584e-97a1-4d76-a8a9-a55b4c99231f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c223e8bddae1ff68e77cdf881ea22e6be4cdab9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-information-for-business-rules"></a>Informations concernant le résultat du suivi du test de stratégies pour les règles d'entreprise
Cette section propose des informations sur les informations de suivi affichées lors du test d'une stratégie dans l'Éditeur des règles d’entreprise. Des informations similaires sont visibles lorsque vous affichez les résultats du suivi de l'exécution des stratégies à l'aide des requêtes de suivi des événements de messages et des instances de service dans la page Hub du groupe.  
  
 Quatre types d’instructions sont affichés dans le résultat de suivi :  
  
-   Activité des faits  
  
-   Évaluation de condition  
  
-   Mise à jour de l'agenda  
  
-   Règle déclenchée  
  
 Chaque type d’instruction est décrit ci-dessous.  
  
## <a name="fact-activity"></a>Activité des faits  
 Cette instruction indique les modifications apportées aux faits présents dans la mémoire de travail du moteur. L’exemple suivant illustre une entrée d’activité des faits :  
  
```  
FACT ACTIVITY 3/16/2004 9:50:28 AM  
Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
Ruleset Name: LoanProcessing  
Operation: Assert  
Object Type: MyTest.test  
Object Instance Identifier: 872  
```  
  
### <a name="rule-engine-instance-identifier"></a>Identificateur de l'instance du moteur de règles  
 Identificateur unique pour le **RuleEngine** instance qui fournit l’environnement d’exécution pour l’activation de règle.  
  
### <a name="ruleset-name"></a>Nom de l'ensemble des règles  
 Nom de l’ensemble de règles (stratégie).  
  
### <a name="operation"></a>Opération  
 Il existe trois types d’opérations pouvant intervenir dans une activité de faits :  
  
 Assert  
  
 Le fait est ajouté à la mémoire de travail.  
  
 Update  
  
 Le fait est mis à jour par une règle et doit être redéclaré dans le moteur pour être ré-évalué, à partir des nouvelles données et du nouvel état.  
  
 Retract  
  
 Le fait est supprimé de la mémoire de travail.  
  
> [!NOTE]
>  Si un fait est déclaré dont le type ne correspond pas à un des types utilisés dans la stratégie, l’opération déclarer affiche « Déclarer-fait non reconnu ».  
  
### <a name="object-type"></a>Type d'objet  
 Type de fait d'une activité particulière :  
  
-   DataConnection  
  
-   TypedDataTable  
  
-   TypedDataRow  
  
     Lorsqu’un TypedDataTable est déclaré, toutes les lignes contenues sont déclarées en tant que TypedDataRows.  Les TypedDataRows associés à une DataConnection ne sont pas déclarés, jusqu’à ce qu’une condition soit évaluée et que la requête qui en résulte soit exécutée.  
  
-   TypedXmlDocument  
  
     Les assertions sont affichées à la fois pour les instances TypedXmlDocument parentes et enfants.  
  
### <a name="object-instance-identifier"></a>Identificateur de l'instance d'objet  
 ID d'instance unique de la référence de fait.  
  
## <a name="condition-evaluation"></a>Évaluation de condition  
 Cette activité indique le résultat de l’évaluation des prédicats individuels. L’exemple suivant illustre une évaluation de condition :  
  
```  
CONDITION EVALUATION TEST (MATCH) 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:Root.EmploymentType/TimeInMonths >= 18  
Left Operand Value: 31  
Right Operand Value: 18  
Test Result: True  
```  
  
 Voici la description de certains des termes de l'exemple précédent :  
  
-   **Expression de test.** expression simple (unaire ou binaire) au sein d’un règle.  
  
-   **Valeur de l’opérande de gauche.** valeur du terme situé à gauche d’une expression.  
  
-   **Valeur de l’opérande de droite.** valeur du terme situé à droite d’une expression.  
  
-   **Résultat de test.** résultat de l’évaluation, True ou False.  
  
## <a name="agenda-update"></a>Mise à jour de l'agenda  
 Cette activité indique les règles qui sont ajoutées à l’agenda du moteur de règles pour être exécutées ultérieurement. L’exemple suivant illustre une entrée de mise à jour d’agenda :  
  
```  
AGENDA UPDATE 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Operation: Add  
Rule Name: Employment Status Rule  
Conflict Resolution Criteria: 0  
```  
  
 Voici la description de certains des termes de l'exemple précédent :  
  
-   **Opération.** des règles peuvent être ajoutées ou supprimées d'un agenda.  
  
-   **Nom de la règle.** nom de la règle qui est ajoutée à l’agenda.  
  
-   **Critères de résolution des conflits.** priorité d'une règle, qui détermine l'ordre relatif dans lequel les actions sont exécutées (les actions avec la priorité la plus élevée sont exécutées en premier).  
  
## <a name="rule-fired"></a>Règle déclenchée  
 Cette activité indique l’exécution des actions d’une règle. L’exemple suivant illustre une entrée de règle déclenchée :  
  
```  
RULE FIRED 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Rule Name: Residency Status Rule  
Conflict Resolution Criteria: 10  
```