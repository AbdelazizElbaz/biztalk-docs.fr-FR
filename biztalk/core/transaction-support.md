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
# <a name="transaction-support"></a><span data-ttu-id="3e77a-102">Prise en charge des transactions</span><span class="sxs-lookup"><span data-stu-id="3e77a-102">Transaction Support</span></span>
<span data-ttu-id="3e77a-103">En règle générale, le moteur de règles ne prend pas en charge les transactions.</span><span class="sxs-lookup"><span data-stu-id="3e77a-103">The rule engine does not support transactions in general.</span></span> <span data-ttu-id="3e77a-104">Toutefois, vous pouvez mettre à jour une base de données de façon transactionnelle à l’aide de la **DataConnection** de l’objet comme indiqué dans les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="3e77a-104">However, you can update a database in a transactional manner by using the **DataConnection** object as shown in the following steps:</span></span>  
  
1.  <span data-ttu-id="3e77a-105">Créer un **SqlConnection** de l’objet à l’aide d’une chaîne de connexion, puis ouvrez la connexion.</span><span class="sxs-lookup"><span data-stu-id="3e77a-105">Create a **SqlConnection** object by using a connection string, and open the connection.</span></span>  
  
    ```  
    SqlConnection connection = new SqlConnection("Initial Catalog=Northwind;Data Source=(local);Integrated Security=SSPI;");  
    connection.Open();  
    ```  
  
2.  <span data-ttu-id="3e77a-106">Créer un **SqlTransaction** objet en appelant le **BeginTransaction** méthode sur l’objet de connexion que vous avez créé à l’étape 1.</span><span class="sxs-lookup"><span data-stu-id="3e77a-106">Create a **SqlTransaction** object by calling the **BeginTransaction** method on the connection object you created in step 1.</span></span>  
  
    ```  
    SqlTransaction transaction = connection.BeginTransaction();  
    ```  
  
3.  <span data-ttu-id="3e77a-107">Créer un **DataConnection** objet en utilisant les objets de connexion et de transaction que vous avez créé dans les étapes 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="3e77a-107">Create a **DataConnection** object by using the connection and transaction objects you created in steps 1 and 2.</span></span>  
  
    ```  
    DataConnection dc = new DataConnection(datasetName, tableName, connection, transaction);  
    ```  
  
4.  <span data-ttu-id="3e77a-108">Passez le **DataConnection** objet en tant que fait avec les autres faits vous souhaitez passer à la stratégie et d’exécuter la stratégie.</span><span class="sxs-lookup"><span data-stu-id="3e77a-108">Pass the **DataConnection** object as a fact along with any other facts you want to pass to the policy, and execute the policy.</span></span>  
  
    ```  
    //Passing a .NET object as a fact along with the data connection  
    MyClass obj = new MyClass();  
    object[] facts = new object[2];  
    facts[0] = dc;  
    facts[1] = obj;  
    Policy pol = new Policy(policyName);  
    policy.Execute(facts);    
    ```  
  
5.  <span data-ttu-id="3e77a-109">Appeler le **mise à jour** méthode sur l’objet de connexion de données.</span><span class="sxs-lookup"><span data-stu-id="3e77a-109">Invoke the **Update** method on the data connection object.</span></span> <span data-ttu-id="3e77a-110">Toutes les mises à jour effectuées pendant l'exécution de la stratégie sont uniquement apportées dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="3e77a-110">All the updates done while executing the policy are done only in memory.</span></span> <span data-ttu-id="3e77a-111">Vous devez appeler la **mettre à jour** méthode sur l’objet de connexion de données pour mettre à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="3e77a-111">You must call the **Update** method on the data connection object to update the database.</span></span>  
  
    ```  
    dc.Update();  
    ```  
  
6.  <span data-ttu-id="3e77a-112">Appelez la méthode **valider** ou **restauration** sur l’objet de connexion de données en fonction de votre propre logique.</span><span class="sxs-lookup"><span data-stu-id="3e77a-112">Now, invoke **Commit** or **Rollback** on the data connection object based on your own logic.</span></span>  
  
    ```  
    //Checking the value of PropertyA in .net object   
    //to decide whether to commit or rollback  
    if (obj.PropertyA == true)  
    transaction.Commit();  
    else  
    transaction.Rollback();  
  
    ```  
  
7.  <span data-ttu-id="3e77a-113">Fermez la connexion, puis supprimez l'objet stratégie.</span><span class="sxs-lookup"><span data-stu-id="3e77a-113">Close the connection, and dispose the policy object.</span></span>  
  
    ```  
    sqlCon.Close();  
    policy.Dispose();  
    ```  
  
 <span data-ttu-id="3e77a-114">Code complet de l'ensemble de la procédure :</span><span class="sxs-lookup"><span data-stu-id="3e77a-114">The following code is the complete code with all the steps:</span></span>  
  
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
  
## <a name="comments"></a><span data-ttu-id="3e77a-115">Commentaires</span><span class="sxs-lookup"><span data-stu-id="3e77a-115">Comments</span></span>  
  
-   <span data-ttu-id="3e77a-116">Vous pouvez également utiliser le **OleDbConnection** et **OleDbTransaction** objets au lieu d’utiliser le **SqlConnection** et **SqlTransaction** objets pour effectuer des mises à jour de la base de données de manière transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="3e77a-116">You can also use the **OleDbConnection** and **OleDbTransaction** objects instead of using the **SqlConnection** and **SqlTransaction** objects to perform database updates in a transactional manner.</span></span>  
  
-   <span data-ttu-id="3e77a-117">Toutes les modifications effectuées à partir de la stratégie sont uniquement apportées dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="3e77a-117">All the modifications done from the policy are done in memory.</span></span> <span data-ttu-id="3e77a-118">Vous devez appeler la **mettre à jour** méthode sur le **DataConnection** objet à mettre à jour la base de données.</span><span class="sxs-lookup"><span data-stu-id="3e77a-118">You must invoke the **Update** method on the **DataConnection** object to update the database.</span></span>  
  
-   <span data-ttu-id="3e77a-119">Vous pouvez valider ou restaurer la transaction en appelant le **validation** ou **restauration** méthode de la **DataConnection** objets respectivement.</span><span class="sxs-lookup"><span data-stu-id="3e77a-119">You can either commit or roll back the transaction by invoking the **Commit** or **Rollback** method of the **DataConnection** objects respectively.</span></span>