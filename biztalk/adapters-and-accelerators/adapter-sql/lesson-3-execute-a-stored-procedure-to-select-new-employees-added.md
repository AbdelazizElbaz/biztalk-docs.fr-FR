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
# <a name="lesson-3-execute-a-stored-procedure-to-select-new-employees-added"></a>Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés
Avant de comprendre les tâches effectuées dans cette leçon, vous devez d’abord comprendre pourquoi ces tâches sont obligatoires. Le **employé** table à laquelle les enregistrements sont insérés pour ajouter un nouvel employé est définie de telle sorte qu’un **état** colonne a toujours la valeur « 0 » chaque fois qu’un nouvel employé est ajouté. Cela afin que vous pouvez utiliser cette colonne pour rechercher des employés nouvellement ajoutées et obtenir des notifications. Dans SQL Server, vous devez interroger en exécutant l’instruction SQL suivante :  
  
```  
SELECT Employee_ID, Name, Designation FROM Employee WHERE Status = 0  
```  
  
 Après réception de la liste des nouvellement ajouté employés, vous devez également mettre à jour le **état** colonne sur « 1 » afin que la prochaine fois que les nouveaux employés sont ajoutés et que vous exécutez la même requête, vous n’obtenez pas les enregistrements pour les anciens employés également. Pour vous assurer que l’instruction Select ci-dessus donne uniquement les employés qui vient d’être ajoutés, vous mettrez à jour la **employé** de table à l’aide de l’instruction SQL suivante :  
  
```  
UPDATE Employee SET Status = 1 WHERE Status = 0  
```  
  
 Par conséquent, le **état** colonne pour les anciens employés est définie sur « 1 », alors que les nouveaux employés seront toujours égal à « 0 ».  
  
 Dans cette leçon, vous allez exécuter une procédure stockée, **UPDATE_EMPLOYEE**, qui exécute ensuite les instructions Select et Update. Une fois que vous avez terminé cette leçon, l’orchestration effectue les opérations suivantes :  
  
1.  Reçoit une notification pour toute modification apportée à la **employé** table.  
  
2.  Extrait le type de notification à partir du message de notification reçu.  
  
3.  Si le message de notification est pour une opération d’insertion, l’orchestration exécute la **UPDATE_EMPLOYEE** procédure stockée.  
  
4.  La procédure stockée lit les enregistrements qui vient d’être entrés dans le **employé** table. Après avoir lu les nouveaux enregistrements, la procédure stockée définit également la **état** colonne pour les enregistrements sur « 1 ».  
  
 Maintenant, vous savez Pourquoi vous avez besoin d’exécuter la procédure stockée. Maintenant, vous devez réfléchir à exécuter dans le cadre de l’orchestration. L’orchestration a besoin d’un message de demande pour le **UPDATE_EMPLOYEE** procédure stockée. Dans ce didacticiel, vous allez créer une bibliothèque de classes personnalisées qui créent le message à la volée et puis la fournir à l’orchestration. Une fois que l’orchestration reçoit le message, il envoie le message à SQL Server à l’aide de l’adaptateur SQL et recevoir la réponse.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Créer le Message de demande pour UPDATE_EMPLOYEE procédure stockée](../../adapters-and-accelerators/adapter-sql/step-1-create-the-request-message-for-update-employee-stored-procedure.md)  
  
-   [Étape 2 : Envoyer le Message de demande à SQL Server et recevoir la réponse](../../adapters-and-accelerators/adapter-sql/step-2-send-the-request-message-to-sql-server-and-receive-response.md)