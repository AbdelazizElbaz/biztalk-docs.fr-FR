---
title: "Étape 3 : Ajouter un filtre pour les Notifications d’insertion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a1e9ef-a179-42a7-b4ae-b1170181053b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97fc32fe7dd657bb45edca91fda0eddaa537b32a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-add-a-filter-for-insert-notifications"></a>Étape 3 : Ajouter un filtre pour les Notifications d’insertion
![Étape 3 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez une forme décider à l’orchestration pour filtrer les messages de notification pour l’opération d’insertion. Les opérations suivantes dans l’orchestration sont effectuées uniquement si la notification reçue est de type de l’insertion.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 2 : extraction de Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).  
  
### <a name="to-filter-for-notification-messages"></a>Pour filtrer les messages de notification  
  
1.  Ajouter un **décider** mettre en forme à l’orchestration, après le **Expression** forme. Dans la boîte à outils, faites glisser le **décider** forme sur la ligne de connexion directement sous la **Expression** forme.  
  
     Le **décider** forme se développe pour afficher une branche pour le **si** instruction **(Rule_1)** et une branche pour le **Else** instruction.  
  
2.  Sur l’aire de conception, cliquez sur le **décider** mettre en forme, puis cliquez sur **fenêtre Propriétés**.  
  
3.  Dans le **propriétés** volet pour le **décider** mettre en forme, dans le **nom** , tapez `CheckNotification`.  
  
4.  Sur l’aire de conception, cliquez sur le **Rule_1** forme (à l’intérieur de la **décider** forme), puis cliquez sur **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Rule_1**, dans le **nom** , tapez **insérer**.  
  
6.  Cliquez sur le **insérer** mettre en forme, puis cliquez sur **modifier l’Expression booléenne**.  
  
7.  Dans l’éditeur d’Expression BizTalk, tapez le texte suivant :  
  
    ```  
    NotificationType.Equals("Insert")  
    ```  
  
     Cette condition indique à l’orchestration permettant d’effectuer les opérations suivantes uniquement si la valeur de la **NotificationType** variable est **insérer**.  
  
    > [!NOTE]
    >  Vous avez ajouté cette variable dans [étape 2 : extraction de Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md) pour extraire le type de notification à partir du message de notification reçu à partir de la base de données SQL Server.  
  
8.  L’illustration suivante montre l’orchestration en cours avec le **décider** forme inclus.  
  
     ![Ajouter une forme décider à l’orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-03-add-filter-orch.gif "sql_adap_tut_03_add_filter_orch")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez ajouté un **décider** forme pour filtrer les messages de notification pour effectuer les opérations suivantes uniquement si la notification reçue est pour les opérations d’insertion.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans l’étape suivante, vous ajoutez des formes d’orchestration à appeler le UPDATE_EMPLOYE de procédure stockée dans la table Employee, comme décrit dans [leçon 3 : exécuter une procédure stockée pour sélectionnez Nouveau employés ajouté](../../adapters-and-accelerators/adapter-sql/lesson-3-execute-a-stored-procedure-to-select-new-employees-added.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Extraire le Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)   
 [Leçon 2 : Réception et filtrer les Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)