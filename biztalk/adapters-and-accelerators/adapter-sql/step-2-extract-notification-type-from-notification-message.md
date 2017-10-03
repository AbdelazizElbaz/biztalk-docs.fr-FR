---
title: "Étape 2 : Extraire le Type de Notification de Message de Notification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72f3e805-0f5f-42fa-8fe3-78ccbb375f74
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51a4fd5e96c3593d3f47ed3c7dfc1875efca7c52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-extract-notification-type-from-notification-message"></a>Étape 2 : Extraire le Type de Notification de Message de Notification
![Étape 2 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez une forme expression pour extraire le type de notification reçue à partir de la base de données SQL Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé [étape 1 : ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).  
  
### <a name="to-extract-the-notification-type-from-the-notification-message"></a>Pour extraire le type de notification à partir du message de notification  
  
1.  Ajouter une variable à l’orchestration BizTalk que vous avez créé dans [étape 1 : ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md).  
  
    1.  À partir de la vue Orchestration, cliquez sur **Variables**, puis cliquez sur **nouvelle Variable**.  
  
    2.  Avec le bouton droit de la nouvelle variable **Variable_1**, puis cliquez sur **fenêtre Propriétés**. Définissez les propriétés suivantes pour la variable.  
  
        |Définissez cette propriété|Cette valeur|  
        |-----------------------|-------------------|  
        |**Identificateur**|NotificationType|  
        |**Type**|System.String|  
  
2.  Ajouter un **Expression** forme à l’orchestration BizTalk. À partir de l’orchestration de boîte à outils, faites glisser le **Expression** forme sur l’aire de conception d’orchestration et déposez-la après le **réception** forme  
  
     Dans le **Expression** forme, vous allez ajouter une requête xpath pour extraire le type de message de notification reçue de SQL Server. Avant de créer une requête xpath, examinons le format d’un message de notification. Un message de notification classique ressemble à ceci :  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>   
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
3.  Comme vous le voir, les informations sur le type de la notification sont disponibles dans le `<info>` balise, au sein du parent `<Notification>` balise. Par conséquent, ajoutez la requête xpath suivante dans le **Expression** forme :  
  
    ```  
    NotificationType = xpath(NotifyReceive,"string(/*[local-name()='Notification']/*[local-name()='Info']/text())");  
    ```  
  
     Ici, **NotificationType** est la variable que vous avez créé pour stocker la valeur extraite par la requête xpath. **NotifyReceive** est le message que vous avez créé dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md) pour recevoir des messages de notification.  
  
4.  L’illustration suivante montre l’orchestration en cours avec le **Expression** forme inclus.  
  
     ![Ajouter une forme Expression à l’orchestration](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-02-add-expression-orch.gif "sql_adap_tut_02_add_expression_orch")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous avez ajouté un **Expression** forme pour extraire le type de notification reçue à partir de la base de données SQL Server.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous ajoutez une forme décider pour filtrer les notifications d’insertion, comme décrit dans [étape 3 : ajouter un filtre pour les Notifications d’insérer](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)   
 [Étape 3 : Ajouter un filtre pour les Notifications d’insertion](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)   
 [Leçon 2 : Réception et filtrer les Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)