---
title: Prise en charge des transactions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataConnection object
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: 84faac2f-6229-4692-9d1a-bf62d87d69bb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57fc1d7a1edd18663cb21a85037cf3e662948fc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-support"></a>Prise en charge des transactions
En règle générale, le moteur de règles ne prend pas en charge les transactions. Toutefois, vous pouvez mettre à jour une base de données de façon transactionnelle à l’aide de la **DataConnection** de l’objet comme indiqué dans les étapes suivantes :  
  
1.  Créer un **SqlConnection** de l’objet à l’aide d’une chaîne de connexion, puis ouvrez la connexion.  
  
    ```  
    SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
    connection.Open();  
    ```  
  
2.  Créer un **SqlTransaction** objet en appelant le **BeginTransaction** méthode sur l’objet de connexion que vous avez créé à l’étape 1.  
  
    ```  
    SqlTransaction transaction = connection.BeginTransaction();  
    ```  
  
3.  Créer un **DataConnection** objet en utilisant les objets de connexion et de transaction que vous avez créé dans les étapes 1 et 2.  
  
    ```  
    DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
    ```  
  
4.  Passez le **DataConnection** objet en tant que fait avec les autres faits vous souhaitez passer à la stratégie et d’exécuter la stratégie.  
  
    ```  
    //Passing a .NET object as a fact along with the data connection  
    MyClass obj = new MyClass();  
    object[] facts = new object[2];  
    facts[0] = dc;  
    facts[1] = obj;  
    Policy pol = new Policy(policyName);  
    policy.Execute(facts);    
    ```  
  
5.  Appeler le **mise à jour** méthode sur l’objet de connexion de données. Toutes les mises à jour effectuées pendant l'exécution de la stratégie sont uniquement apportées dans la mémoire. Vous devez appeler la **mettre à jour** méthode sur l’objet de connexion de données pour mettre à jour la base de données.  
  
    ```  
    dc.Update();  
    ```  
  
6.  Appelez la méthode **valider** ou **restauration** sur l’objet de connexion de données en fonction de votre propre logique.  
  
    ```  
    //Checking the value of PropertyA in .net object   
    //to decide whether to commit or rollback  
    if (obj.PropertyA == true)  
    transaction.Commit();  
    else  
    transaction.Rollback();  
  
    ```  
  
7.  Fermez la connexion, puis supprimez l'objet stratégie.  
  
    ```  
    sqlCon.Close();  
    policy.Dispose();  
    ```  
  
 Code complet de l'ensemble de la procédure :  
  
```  
SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
connection.Open();  
SqlTransaction transaction = connection.BeginTransaction();  
DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
MyClass obj = new MyClass();  
object[] facts = new object[2];  
facts[0] = dc;  
facts[1] = obj;  
Policy pol = new Policy(policyName);  
policy.Execute(facts);    
dc.Update();  
if (obj.PropertyA == true)  
transaction.Commit();  
else  
transaction.Rollback();  
sqlCon.Close();  
policy.Dispose();  
```  
  
## <a name="comments"></a>Commentaires  
  
-   Vous pouvez également utiliser le **OleDbConnection** et **OleDbTransaction** objets au lieu d’utiliser le **SqlConnection** et **SqlTransaction** objets pour effectuer des mises à jour de la base de données de manière transactionnelle.  
  
-   Toutes les modifications effectuées à partir de la stratégie sont uniquement apportées dans la mémoire. Vous devez appeler la **mettre à jour** méthode sur le **DataConnection** objet à mettre à jour la base de données.  
  
-   Vous pouvez valider ou restaurer la transaction en appelant le **validation** ou **restauration** méthode de la **DataConnection** objets respectivement.