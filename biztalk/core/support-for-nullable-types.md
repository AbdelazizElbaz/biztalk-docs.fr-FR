---
title: Prise en charge des Types Nullable | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a5ea191-09d5-47ab-a197-390fbbcf6306
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abd277db970a00e9d7d8f20de65e85c607c2a861
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="support-for-nullable-types"></a>Prise en charge des types nullables
Le moteur de règles prend en charge l'utilisation des types nullables dans une règle d'entreprise. Vous pouvez utiliser des types nullables dans les liaisons de classe .NET, les liaisons XML et les liaisons de base de données. À l'heure actuelle, l'outil Éditeur des règles d'entreprise ne prend pas en charge l'utilisation des types nullables dans une règle d'entreprise. Vous pouvez utiliser des types nullables lors de la création des règles par programme.  
  
## <a name="using-nullable-types-in-net-class-bindings"></a>Utilisation des types nullables dans les liaisons de classe .NET  
 Vous pouvez créer une liaison du membre de classe vers une propriété ou un champ de type nullable. Vous pouvez également créer une liaison de membre de classe vers une méthode qui prend un paramètre de type nullable et/ou retourne une valeur de type nullable. L'exemple de code suivant montre comment accéder à un champ et à une valeur renvoyée de type nullable à partir d'une méthode dans une règle d'entreprise. Si vous exécutez une application de console avec le code suivant car il s’agit, vous verrez que la valeur de la **prop** champ est défini sur 5. Si vous n’initialisez pas le **prop** champ dans la classe ou de l’initialisation pour la valeur null et exécutez le code, vous verrez que la valeur de la **prop** champ est défini sur 1.  
  
```  
using Microsoft.RuleEngine;  
namespace UseNullableAsm  
{  
    class Program  
    {  
        public class Class1  
        {  
            public int? prop = 1;  
            private int? prop2 = 4;  
            public int? GetProp2()  
            {  
                return prop2;  
            }  
        }  
  
        static void Main(string[] args)  
        {  
            //Create the class binding for the Class1 class  
            ClassBinding cbCls1 = new ClassBinding(typeof(Class1));  
  
            //Create the class member binding to the GetProp2 method of Cls1 class  
            ClassMemberBinding cmGetProp2 = new ClassMemberBinding("GetProp2", cbCls1);  
  
            //Create the class member binding to the to GET the value of prop  
            ClassMemberBinding cmGetProp = new ClassMemberBinding("prop", cbCls1);  
  
            //Create arguments for the prop1 field, which is prop1 + GetProp2()  
            UserFunction ufGetProp = new UserFunction(cmGetProp);  
            Add addArg = new Add(ufGetProp, new UserFunction(cmGetProp2));  
            ArgumentCollection al1 = new ArgumentCollection();  
            al1.Add(addArg);  
  
            //Set the value of prop to prop1 + cmGetPro2()  
            ClassMemberBinding cmProp = new ClassMemberBinding("prop", cbCls1, al1);  
  
            //Create a userfunction based on cmProp and add to the action collection  
            UserFunction ufProp = new UserFunction(cmProp);  
            ActionCollection ac = new ActionCollection();  
            ac.Add(ufProp);  
  
            //Create the condition list IF prop == 1  
            Equal eq = new Equal(ufGetProp, new Constant(1));  
  
            //Create the rule   
            // If (prop == 1)  
            // Then prop = prop + GetProp2()  
            Rule rl = new Rule("NullableTestRule", eq, ac);  
  
            //Create the condition list IF prop != 1  
            NotEqual neq = new NotEqual(ufGetProp, new Constant(1));  
  
            //Set the value of prop to prop to 1  
            Constant ct = new Constant(1);  
            ArgumentCollection al2 = new ArgumentCollection();  
            al2.Add(ct);  
  
            //Create class member binding to prop field with argument value 1  
            ClassMemberBinding cmSetProp = new ClassMemberBinding("prop", cbCls1, al2);  
  
            //Create a userfunction based on cmSetProp and add to the action collection  
            UserFunction ufSetProp = new UserFunction(cmSetProp);  
            ActionCollection ac2 = new ActionCollection();  
            ac2.Add(ufSetProp);  
  
            //Create the second rule   
            // If (prop != 1)  
            // Then prop = 1  
            Rule rl2 = new Rule("NullableTestRule2", neq, ac2);  
  
            //Create the policy and add both the rules to the policy  
            RuleSet rs = new RuleSet("NulableTestPolicy");  
            rs.Rules.Add(rl);  
            rs.Rules.Add(rl2);  
  
            //Create the .NET object fact  
            Class1 cls1Obj = new Class1();  
  
            //Print the value of the field prop before executing the policy  
            Console.WriteLine("Value of the prop field is " + cls1Obj.prop);  
  
            //Execute the policy  
            PolicyTester pt = new PolicyTester(rs);  
            pt.Execute(cls1Obj);  
  
            //Print the value of the field prop after executing the policy  
            Console.WriteLine("Value of the prop field is " + cls1Obj.prop);  
        }  
    }  
}  
```  
  
## <a name="using-nullable-types-in-database-bindings"></a>Utilisation des types nullables dans les liaisons de base de données  
 Vous pouvez également utiliser des types nullables dans les liaisons de base de données. L'extrait de code suivant montre comment utiliser un type nullable dans des liaisons de base de données.  
  
```  
DataColumnBinding dcBinding = new DataColumnBinding(“col”, typeof(int?), dbBinding);  
```  
  
 Supposez que vous avez une règle avec une condition qui vérifie la valeur d’une colonne de base de données pour voir si est égal à 3. Si la valeur de la colonne est null, l’expression a la valeur false. Cela ne génère pas d'exception.  
  
## <a name="using-nullable-types-in-xml-bindings"></a>Utilisation des types nullables dans les liaisons XML  
 Vous pouvez également utiliser des types nullables dans les liaisons XML. L'extrait de code suivant montre comment utiliser un type nullable dans des liaisons XML.  
  
```  
XMLDocumentFieldBinding xfb1 = new XMLDocumentFieldBinding(typeof(int?),"ID",xdb);  
```