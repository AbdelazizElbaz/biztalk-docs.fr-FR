---
title: "Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec7897e9-0c77-41b2-8cc2-61745bd3b028
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7af49c026b443fb1ca6a0fb7f35b64cdf1e377f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-3-execute-a-stored-procedure-to-select-new-employees-added"></a><span data-ttu-id="8dd57-102">Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés</span><span class="sxs-lookup"><span data-stu-id="8dd57-102">Lesson 3: Execute a Stored Procedure to Select New Employees Added</span></span>
<span data-ttu-id="8dd57-103">Avant de comprendre les tâches effectuées dans cette leçon, vous devez d’abord comprendre pourquoi ces tâches sont obligatoires.</span><span class="sxs-lookup"><span data-stu-id="8dd57-103">Before understanding the tasks performed in this lesson, you must first understand why these tasks are required.</span></span> <span data-ttu-id="8dd57-104">Le **employé** table à laquelle les enregistrements sont insérés pour ajouter un nouvel employé est définie de telle sorte qu’un **état** colonne a toujours la valeur « 0 » chaque fois qu’un nouvel employé est ajouté.</span><span class="sxs-lookup"><span data-stu-id="8dd57-104">The **Employee** table to which the records are inserted to add a new employee is defined in such a way that a **Status** column is always set to “0” every time a new employee is added.</span></span> <span data-ttu-id="8dd57-105">Cela afin que vous pouvez utiliser cette colonne pour rechercher des employés nouvellement ajoutées et obtenir des notifications.</span><span class="sxs-lookup"><span data-stu-id="8dd57-105">This is done so that you can use this column to query for newly added employees and also get notifications.</span></span> <span data-ttu-id="8dd57-106">Dans SQL Server, vous devez interroger en exécutant l’instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="8dd57-106">In SQL Server, you would query this by running the following SQL statement:</span></span>  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 <span data-ttu-id="8dd57-107">Après réception de la liste des nouvellement ajouté employés, vous devez également mettre à jour le **état** colonne sur « 1 » afin que la prochaine fois que les nouveaux employés sont ajoutés et que vous exécutez la même requête, vous n’obtenez pas les enregistrements pour les anciens employés également.</span><span class="sxs-lookup"><span data-stu-id="8dd57-107">After receiving the list of newly added employees, you must also update the **Status** column to “1” so that the next time new employees are added and you run the same query, you do not get records for old employees as well.</span></span> <span data-ttu-id="8dd57-108">Pour vous assurer que l’instruction Select ci-dessus donne uniquement les employés qui vient d’être ajoutés, vous mettrez à jour la **employé** de table à l’aide de l’instruction SQL suivante :</span><span class="sxs-lookup"><span data-stu-id="8dd57-108">To make sure that the above Select statement gives only the newly added employees, you will update the **Employee** table using the following SQL statement:</span></span>  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 <span data-ttu-id="8dd57-109">Par conséquent, le **état** colonne pour les anciens employés est définie sur « 1 », alors que les nouveaux employés seront toujours égal à « 0 ».</span><span class="sxs-lookup"><span data-stu-id="8dd57-109">So, the **Status** column for the old employees is set to “1” while new employees will always be “0.”</span></span>  
  
 <span data-ttu-id="8dd57-110">Dans cette leçon, vous allez exécuter une procédure stockée, **UPDATE_EMPLOYEE**, qui exécute ensuite les instructions Select et Update.</span><span class="sxs-lookup"><span data-stu-id="8dd57-110">In this lesson, you will execute a stored procedure, **UPDATE_EMPLOYEE**, which in turn executes the Select and Update statements.</span></span> <span data-ttu-id="8dd57-111">Une fois que vous avez terminé cette leçon, l’orchestration effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="8dd57-111">After you have finished this lesson, your orchestration will do the following:</span></span>  
  
1.  <span data-ttu-id="8dd57-112">Reçoit une notification pour toute modification apportée à la **employé** table.</span><span class="sxs-lookup"><span data-stu-id="8dd57-112">Receives notification for any changes to the **Employee** table.</span></span>  
  
2.  <span data-ttu-id="8dd57-113">Extrait le type de notification à partir du message de notification reçu.</span><span class="sxs-lookup"><span data-stu-id="8dd57-113">Extracts the type of notification from the notification message received.</span></span>  
  
3.  <span data-ttu-id="8dd57-114">Si le message de notification est pour une opération d’insertion, l’orchestration exécute la **UPDATE_EMPLOYEE** procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="8dd57-114">If the notification message is for an Insert operation, the orchestration executes the **UPDATE_EMPLOYEE** stored procedure.</span></span>  
  
4.  <span data-ttu-id="8dd57-115">La procédure stockée lit les enregistrements qui vient d’être entrés dans le **employé** table.</span><span class="sxs-lookup"><span data-stu-id="8dd57-115">The stored procedure reads the newly entered records in the **Employee** table.</span></span> <span data-ttu-id="8dd57-116">Après avoir lu les nouveaux enregistrements, la procédure stockée définit également la **état** colonne pour les enregistrements sur « 1 ».</span><span class="sxs-lookup"><span data-stu-id="8dd57-116">After reading the new records, the stored procedure also sets the **Status** column for those records to “1.”</span></span>  
  
 <span data-ttu-id="8dd57-117">Maintenant, vous savez Pourquoi vous avez besoin d’exécuter la procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="8dd57-117">Now you know why you need to execute the stored procedure.</span></span> <span data-ttu-id="8dd57-118">Maintenant, vous devez réfléchir à exécuter dans le cadre de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8dd57-118">You now need to think about how to execute this as part of the orchestration.</span></span> <span data-ttu-id="8dd57-119">L’orchestration a besoin d’un message de demande pour le **UPDATE_EMPLOYEE** procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="8dd57-119">The orchestration needs a request message for the **UPDATE_EMPLOYEE** stored procedure.</span></span> <span data-ttu-id="8dd57-120">Dans ce didacticiel, vous allez créer une bibliothèque de classes personnalisées qui créent le message à la volée et puis la fournir à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="8dd57-120">In this tutorial, you will create a custom class library that will create the message on the fly and then provide it to the orchestration.</span></span> <span data-ttu-id="8dd57-121">Une fois que l’orchestration reçoit le message, il envoie le message à SQL Server à l’aide de l’adaptateur SQL et recevoir la réponse.</span><span class="sxs-lookup"><span data-stu-id="8dd57-121">After the orchestration receives the message, it will send the message to the SQL Server using the SQL adapter and receive the response.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8dd57-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8dd57-122">In This Section</span></span>  
  
-   [<span data-ttu-id="8dd57-123">Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée</span><span class="sxs-lookup"><span data-stu-id="8dd57-123">Step 1: Create the Request Message for UPDATE_EMPLOYEE Stored Procedure</span></span>](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [<span data-ttu-id="8dd57-124">Étape 2 : Envoyer le Message de demande à SQL Server et recevoir la réponse</span><span class="sxs-lookup"><span data-stu-id="8dd57-124">Step 2: Send the Request Message to SQL Server and Receive Response</span></span>](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)