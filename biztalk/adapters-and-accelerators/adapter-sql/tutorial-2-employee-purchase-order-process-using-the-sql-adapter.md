---
title: "Didacticiel 2 : Employé - processus de bon de commande à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eeb4dd1e-209a-47eb-9c0e-a138e02f0ff2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fca0c11aeb1f84a5e9f05a4df4f995b7c2b52e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-2-employee---purchase-order-process-using-the-sql-adapter"></a>Didacticiel 2 : Employé - processus de bon de commande à l’aide de l’adaptateur SQL
Dans ce didacticiel, vous automatisez le processus dans lequel le service des achats qui place un équipement de commande chaque fois qu’un nouvel employé rejoint l’organisation. Détails de l’employé et purchase order Detail est conservés dans **employé** et **Purchase_Order** tables respectivement, dans une base de données SQL Server. Le service des achats est informé en mettant à jour la table Purchase_Order dans la base de données SQL Server et en envoyant un message électronique. Dans le processus, les actions suivantes se produisent :  
  
1.  L’adaptateur reçoit une notification chaque fois que le **employé** table est mise à jour. Ensuite, l’adaptateur envoie une notification à l’orchestration BizTalk.  
  
2.  L’orchestration BizTalk détermine si la notification est pour un nouvel enregistrement est inséré dans le **employé** table. Si la notification est pour toute autre opération sur le **employé** table, l’orchestration n’effectue aucune opération.  
  
3.  Si la notification est pour une opération d’insertion sur la **employé** table, notification qu’un nouvel enregistrement d’employé a été ajouté, l’orchestration utilise le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour lire les détails du nouvel enregistrement.  
  
4.  L’orchestration reçoit une réponse qui contient les détails du nouvel enregistrement d’employé. Les mappages d’orchestration le **Employee_ID** et **désignation** champs dans la réponse au message de demande pour l’opération d’insertion sur la **Purchase_Order** table.  
  
5.  L’orchestration utilise la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour effectuer une opération d’insertion sur la **Purchase_Order** table. La réponse pour l’opération d’insertion est envoyée au service des achats comme un message électronique.  
  
## <a name="about-the-database-objects-used-in-this-sample"></a>Sur les objets de base de données utilisées dans cet exemple  
 Ce didacticiel utilise les objets de base de données créés par le script SQL inclu dans les exemples. Pour plus d’informations sur le script et les exemples, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md). Les objets de base de données que vous utiliserez dans ce didacticiel sont :  
  
-   **ADAPTER_SAMPLES** base de données.  
  
-   **Employé** et **Purchase_Order** tables.  
  
-   **UPDATE_EMPLOYEE** procédure stockée.  
  
 Tous ces objets de base de données sont créés lorsque vous exécutez le script SQL fourni avec l’exemple. Assurez-vous que vous exécutez le script avant de commencer avec le didacticiel.  
  
## <a name="sample-based-on-this-tutorial"></a>Exemple basé sur ce didacticiel  
 Un exemple, **Employee_PurchaseOrder**, qui est basé sur ce didacticiel est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
 Nous vous recommandons de suivre le didacticiel complètement pour comprendre comment créer des projets BizTalk à l’aide de l’adaptateur puis d’observer l’échantillon sous la forme d’une référence.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Leçon 1 : Générer des schémas et créer des Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md)  
  
-   [Leçon 2 : Réception et filtrer les Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)  
  
-   [Leçon 3 : Exécuter une procédure stockée pour sélectionner les nouveaux employés ajoutés](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md)  
  
-   [Leçon 4 : Effectuer une opération d’insertion sur la Table de commande d’achat](../../adapters-and-accelerators/adapter-sql/lesson-4-perform-an-insert-operation-on-the-purchase-order-table.md)  
  
-   [Leçon 5 : Déployer la Solution](../../adapters-and-accelerators/adapter-sql/lesson-5-deploy-the-solution.md)