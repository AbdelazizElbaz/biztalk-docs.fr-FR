---
title: "Accès aux membres imbriqués d’une classe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 358e1edf-ae0b-4916-b8db-7277f39e36f4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110244f9f007a417450b5bbfdce831d5f255cfe5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-nested-members-of-a-class"></a><span data-ttu-id="4f91f-102">Accès aux membres imbriqués d'une classe</span><span class="sxs-lookup"><span data-stu-id="4f91f-102">Accessing Nested Members of a Class</span></span>
<span data-ttu-id="4f91f-103">Le moteur de règles vous permet d'utiliser une méthode ou une propriété imbriquée d'un objet dans une règle.</span><span class="sxs-lookup"><span data-stu-id="4f91f-103">The rule engine allows you to use a nested property or method of an object in a rule.</span></span> <span data-ttu-id="4f91f-104">Par exemple, supposons qu'il existe une classe nommée AClass, comportant une propriété nommée B de type BClass, qui possède un champ nommé C. Le moteur de règles vous permet de créer des règles d'accès au champ C à l'aide de la syntaxe A.B.C.</span><span class="sxs-lookup"><span data-stu-id="4f91f-104">For example, suppose you have a class named AClass, which has a property named B of type BClass, which has a field named C. The rule engine allows you to build rules accessing the field C by using the A.B.C syntax.</span></span> <span data-ttu-id="4f91f-105">Pour utiliser cette syntaxe, cependant, les règles doivent être créées par programme et non par le biais de l'outil Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="4f91f-105">However, it is possible to use this syntax only when building the rules programmatically, not when using the Business Rule Composer tool.</span></span> <span data-ttu-id="4f91f-106">L'exemple de code suivant montre comment utiliser la propriété imbriquée d'un objet :</span><span class="sxs-lookup"><span data-stu-id="4f91f-106">The following sample code demonstrates how to use a property of an object, which is a property of another object:</span></span>  
  
```  
// Create the condition list IF 1 == 1  
Equal eq = new Equal(new Constant(1), new Constant(1));  
  
// Create the action collection  
ActionCollection ac = new ActionCollection();  
  
// Create class binding and class member binding to cField  
// Set the value of cField to "Changed"  
Constant chg = new Constant("Changed");  
ArgumentCollection argCol = new ArgumentCollection();  
argCol.Add(chg);  
ClassBinding lstClass = new ClassBinding(typeof(AClass));  
ClassMemberBinding bBinding = new ClassMemberBinding("bObj", lstClass);  
ClassMemberBinding CBinding = new ClassMemberBinding("cField", bBinding,argCol);  
UserFunction uf_C = new UserFunction(CBinding);  
ac.Add(uf_C);  
  
// Create the rule  
Rule rl = new Rule("ChangeCField", eq, ac);  
  
// Create the policy  
RuleSet rs = new RuleSet("NestedNodeTest");  
rs.Rules.Add(rl);  
  
//Create the facts  
AClass aObj = new AClass();  
Console.WriteLine("The value of aObj.bObj.cField BEFORE executing the policy");  
Console.WriteLine(aObj.bObj.cField);  
  
//Execute the policy  
PolicyTester tester = new PolicyTester(rs);  
tester.Execute(aObj);  
  
Console.WriteLine("The value of aObj.bObj.cField AFTER executing the policy");  
Console.WriteLine(aObj.bObj.cField);  
```