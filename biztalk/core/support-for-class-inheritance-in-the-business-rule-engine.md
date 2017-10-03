---
title: "Prise en charge de l’héritage de classes dans le moteur de règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code samples, Business Rules Engine
- Business Rules Engine, inheritance
- Business Rules Engine, code samples
- Business Rules Engine, examples
- examples, Business Rules Engine
ms.assetid: 50871f34-ccbe-4f77-8feb-5694e1b14837
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 930fc5591ce55f1a2ec988b307203a4154e85c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-class-inheritance-in-the-business-rule-engine"></a>Prise en charge de l'héritage de classe au sein du moteur de règles d'entreprise
L'héritage constitue l'une des fonctionnalités principales des langages de la programmation orientée objet. Il s'agit de la capacité à utiliser toute la fonctionnalité d'une classe et à étendre ces capacités sans réécrire la classe d'origine.  
  
 L’infrastructure des règles d’entreprise prend en charge deux types d’héritage de classe : implémentation et l’interface. L'héritage de l'implémentation se réfère à la capacité à utiliser les propriétés et les méthodes d'une classe de base sans codage supplémentaire. L'héritage de l'interface, quant à lui, se réfère à la capacité à utiliser seulement le nom des propriétés et des méthodes. La classe enfant doit cependant fournir l'implémentation.  
  
 Les règles peuvent être écrites dans une classe de base commune, mais les objets déclarés dans le moteur peuvent provenir de classes dérivées. Dans l’exemple suivant, **RegularEmployee** et **ContractEmployee** sont des classes dérivées de la classe de base **employé**.  
  
```  
class Employee  
   {  
      public string Status()  
      {   
         // member definition  
      }  
      public string TimeInMonths()        
      {   
         // member definition  
      }  
   }  
  
class ContractEmployee : Employee  
{  
   // class definition  
}  
class RegularEmployee : Employee  
{  
   // class definition  
}  
```  
  
 Supposons que la règle suivante existe.  
  
## <a name="rule-1"></a>Règle 1  
  
```  
IF Employee.TimeInMonths < 12  
THEN Employee.Status = "New"  
```  
  
 Au moment de l’exécution, si l’utilisateur déclare deux objets, un est une instance de **ContractEmployee** et l’autre une instance de **RegularEmployee**, les instances d’objet sont évaluées par rapport à la règle décrite plus haut.  
  
 L’utilisateur peut également déclarer des objets de classe dérivés dans des actions en utilisant un **Assert**. Cela provoque une nouvelle évaluation des règles qui contiennent l'objet dérivé et son type de base dans leur condition, comme le montre l'exemple suivant.  
  
## <a name="rule-2"></a>Règle 2  
  
```  
IF Employee.Status = "Contract"   
THEN Employee.Bonus = false  
Assert(new ContractEmployee())  
```  
  
 Toutes les règles contenant le **employé** type ou le **ContractEmployee** type dans leurs conditions réévaluées après l’assertion. Le type d'héritage dans cet exemple est l'implémentation. Bien que seule la classe dérivée soit déclarée, la classe de base est également déclarée si les règles sont écrites à l'aide des méthodes dans la classe de base au lieu de la classe dérivée.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de règles](../core/rule-engine.md)