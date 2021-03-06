---
title: "Prise en charge des Types génériques et les méthodes génériques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc6b5b51-e084-4828-ad25-9209aa74dc6f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65d8a17a9ac1f055312f0f1cdf3bc1231319842d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="support-for-generic-types-and-generic-methods"></a>Prise en charge des types génériques et des méthodes génériques
Le moteur de règles prend en charge l'utilisation de types et méthodes génériques spécialisés dans une règle. En revanche, il ne prend pas en charge l'utilisation des types et méthodes génériques eux-mêmes dans une règle. Par exemple, dans une règle d’entreprise, vous pouvez utiliser **liste**\<*int*\>, mais pas **liste**\<T\> (à partir de la  **System.Collections.Generic** espace de noms dans la bibliothèque de classes .NET). À l'heure actuelle, l'outil Éditeur des règles d'entreprise ne prend pas en charge la création de règles à l'aide de types et de méthodes génériques spécialisés. Pour bénéficier de cette fonctionnalité, vous devez créer les règles par programme en utilisant le modèle d'objet du moteur de règles. L’exemple de code suivant montre comment utiliser le **liste** classe générique dans une règle d’entreprise :  
  
```  
  
// Create the condition list IF 1 == 1  
Equal eq = new Equal(new Constant(1), new Constant(1));  
  
// Create the action list List<int>.Add(3)  
ActionCollection ac = new ActionCollection();  
  
//Create class binding and class member bindings  
ClassBinding lstClass = new ClassBinding(typeof(System.Collections.Generic.List<int>));  
ArgumentCollection argc = new ArgumentCollection();  
argc.Add(new Constant(3));  
ClassMemberBinding add = new ClassMemberBinding("Add", lstClass, argc);  
  
// Wrapping the .NET binding as a user function  
UserFunction uf = new UserFunction(add);  
ac.Add(uf);  
  
// Create the rule  
Rule rl = new Rule("AddToList", eq, ac);  
  
// Create the policy  
RuleSet rs = new RuleSet("GenericTest");  
rs.Rules.Add(rl);  
  
// Create the .NET List object  
List<int> lst = new List<int>();  
lst.Add(1);  
lst.Add(2);  
  
// Print the list before executing the policy  
Console.WriteLine("Contents of the lists before executing the policy");  
foreach (int i in lst)  
    Console.WriteLine(i);  
  
PolicyTester pt = new PolicyTester(rs);  
pt.Execute(lst);  
  
// Print the list after executing the policy  
Console.WriteLine("Contents of the lists before executing the policy");  
foreach (int i in lst)  
    Console.WriteLine(i);  
```