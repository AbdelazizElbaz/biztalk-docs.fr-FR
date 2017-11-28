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
# <a name="support-for-class-inheritance-in-the-business-rule-engine"></a><span data-ttu-id="d8f10-102">Prise en charge de l'héritage de classe au sein du moteur de règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="d8f10-102">Support for Class Inheritance in the Business Rule Engine</span></span>
<span data-ttu-id="d8f10-103">L'héritage constitue l'une des fonctionnalités principales des langages de la programmation orientée objet.</span><span class="sxs-lookup"><span data-stu-id="d8f10-103">One of the key features of Object Oriented Programming (OOP) languages is inheritance.</span></span> <span data-ttu-id="d8f10-104">Il s'agit de la capacité à utiliser toute la fonctionnalité d'une classe et à étendre ces capacités sans réécrire la classe d'origine.</span><span class="sxs-lookup"><span data-stu-id="d8f10-104">Inheritance is the ability to use all of the functionality of an existing class, and extend those capabilities without rewriting the original class.</span></span>  
  
 <span data-ttu-id="d8f10-105">L’infrastructure des règles d’entreprise prend en charge deux types d’héritage de classe : implémentation et l’interface.</span><span class="sxs-lookup"><span data-stu-id="d8f10-105">The Business Rules Framework supports two types of class inheritance: implementation and interface.</span></span> <span data-ttu-id="d8f10-106">L'héritage de l'implémentation se réfère à la capacité à utiliser les propriétés et les méthodes d'une classe de base sans codage supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d8f10-106">Implementation inheritance refers to the ability to use a base class's properties and methods with no additional coding.</span></span> <span data-ttu-id="d8f10-107">L'héritage de l'interface, quant à lui, se réfère à la capacité à utiliser seulement le nom des propriétés et des méthodes. La classe enfant doit cependant fournir l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="d8f10-107">Interface inheritance refers to the ability to use just the names of the properties and methods, but the child class must provide the implementation.</span></span>  
  
 <span data-ttu-id="d8f10-108">Les règles peuvent être écrites dans une classe de base commune, mais les objets déclarés dans le moteur peuvent provenir de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="d8f10-108">The rules can be written in terms of a common base class, but the objects asserted into the engine can be from derived classes.</span></span> <span data-ttu-id="d8f10-109">Dans l’exemple suivant, **RegularEmployee** et **ContractEmployee** sont des classes dérivées de la classe de base **employé**.</span><span class="sxs-lookup"><span data-stu-id="d8f10-109">In the following example, **RegularEmployee** and **ContractEmployee** are derived classes of the base class **Employee**.</span></span>  
  
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
  
 <span data-ttu-id="d8f10-110">Supposons que la règle suivante existe.</span><span class="sxs-lookup"><span data-stu-id="d8f10-110">Assume you have the following rule.</span></span>  
  
## <a name="rule-1"></a><span data-ttu-id="d8f10-111">Règle 1</span><span class="sxs-lookup"><span data-stu-id="d8f10-111">Rule 1</span></span>  
  
```  
IF Employee.TimeInMonths < 12  
THEN Employee.Status = "New"  
```  
  
 <span data-ttu-id="d8f10-112">Au moment de l’exécution, si l’utilisateur déclare deux objets, un est une instance de **ContractEmployee** et l’autre une instance de **RegularEmployee**, les instances d’objet sont évaluées par rapport à la règle décrite plus haut.</span><span class="sxs-lookup"><span data-stu-id="d8f10-112">At run time, if the user asserts two objects, one an instance of **ContractEmployee** and the other an instance of **RegularEmployee**, both the object instances are evaluated against the rule described earlier.</span></span>  
  
 <span data-ttu-id="d8f10-113">L’utilisateur peut également déclarer des objets de classe dérivés dans des actions en utilisant un **Assert**.</span><span class="sxs-lookup"><span data-stu-id="d8f10-113">The user can also assert derived class objects in actions by using an **Assert**.</span></span> <span data-ttu-id="d8f10-114">Cela provoque une nouvelle évaluation des règles qui contiennent l'objet dérivé et son type de base dans leur condition, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="d8f10-114">This causes the rules that contain the derived object and its base type in their conditions to be re-evaluated, as shown in the following example.</span></span>  
  
## <a name="rule-2"></a><span data-ttu-id="d8f10-115">Règle 2</span><span class="sxs-lookup"><span data-stu-id="d8f10-115">Rule 2</span></span>  
  
```  
IF Employee.Status = "Contract"   
THEN Employee.Bonus = false  
Assert(new ContractEmployee())  
```  
  
 <span data-ttu-id="d8f10-116">Toutes les règles contenant le **employé** type ou le **ContractEmployee** type dans leurs conditions réévaluées après l’assertion.</span><span class="sxs-lookup"><span data-stu-id="d8f10-116">All rules containing the **Employee** type or the **ContractEmployee** type in their conditions get re-evaluated after the assertion.</span></span> <span data-ttu-id="d8f10-117">Le type d'héritage dans cet exemple est l'implémentation.</span><span class="sxs-lookup"><span data-stu-id="d8f10-117">The type of inheritance in this example is implementation.</span></span> <span data-ttu-id="d8f10-118">Bien que seule la classe dérivée soit déclarée, la classe de base est également déclarée si les règles sont écrites à l'aide des méthodes dans la classe de base au lieu de la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="d8f10-118">Even though only the derived class is asserted, the base class also gets asserted if rules are written using methods in the base instead of the derived class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f10-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f10-119">See Also</span></span>  
 [<span data-ttu-id="d8f10-120">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="d8f10-120">Rule Engine</span></span>](../core/rule-engine.md)