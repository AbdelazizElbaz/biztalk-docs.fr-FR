---
title: "Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e4c6fa5-81b7-4928-84d5-39533535f862
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a33693a09d89acc5d1ad9e4514c7907b789cc75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-add-orchestration-shapes-to-receive-notification"></a>Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification
![Étape 1 sur 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **Durée :** 5 minutes  
  
 **Objectif :** dans cette étape, vous ajoutez des formes d’orchestration pour recevoir une notification pour les modifications apportées à la **employé** table.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé les étapes de [leçon 1 : générer les schémas et créer des Messages](../../adapters-and-accelerators/adapter-sql/lesson-1-generate-schemas-and-create-messages.md).  
  
### <a name="to-receive-notification-messages"></a>Pour recevoir des messages de notification  
  
1.  Ouvrez l’orchestration BizTalk, **EmployeeOrch.odx**, vous avez ajouté dans [étape 2 : créer des Messages pour les Orchestrations BizTalk](../../adapters-and-accelerators/adapter-sql/step-2-create-messages-for-biztalk-orchestrations.md).  
  
2.  Ajouter un **réception** forme à l’orchestration. À partir de l’orchestration de boîte à outils, faites glisser le **réception** forme sur l’aire de conception d’orchestration et déposez-la dans l’emplacement indiqué entre le **commencer** (cercle vert) et **fin**les formes (octogone rouge).  
  
    |Définissez cette propriété|Cette valeur|  
    |-----------------------|-------------------|  
    |**Activate**|True|  
    |**Message**|NotifyReceive|  
    |**Nom**|ReceiveNotification|  
  
3.  Ajouter un unidirectionnel port de réception pour l’orchestration. Vous allez utiliser ce port pour recevoir des messages de notification à partir de la base de données SQL Server. Définissez les propriétés suivantes pour le port.  
  
    |Définissez cette propriété|Cette valeur|  
    |-----------------------|-------------------|  
    |**Direction de communication**|Recevoir|  
    |**Modèle de communication**|Unidirectionnel|  
    |**Identificateur**|ReceiveNotification|  
  
     En outre, modifier le nom de l’opération à partir de Operation_1 pour **Notification**.  
  
4.  Connecter le **ReceiveNotification** port pour le **ReceiveNotification** forme action. Dans le Concepteur d’Orchestration, faites glisser la poignée verte en forme de flèche pour le handle de port correspondant verte de la forme action sur l’aire de conception.  
  
    > [!NOTE]
    >  Au cours de cette étape, vous utilisez la méthode glisser-déplacer pour relier les ports aux formes Action. Vous pouvez également utiliser la propriété Opération d'une forme Action pour les relier.  
  
5.  L’illustration suivante montre l’orchestration en cours.  
  
     ![Orchestration permettant de recevoir des messages de notification](../../adapters-and-accelerators/adapter-sql/media/sql-adap-tut-01-receive-notification-orch.gif "sql_adap_tut_01_receive_notification_orch")  
  
## <a name="what-did-i-just-do"></a>Actions effectuées  
 Dans cette étape, vous ajouté des formes d’orchestration et port de réception pour recevoir une notification à partir de la base de données SQL Server.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous ajoutez une forme expression à l’orchestration d’extraire le type de notification reçue à partir de la base de données SQL Server, comme décrit dans [étape 2 : extraction de Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Extraire le Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)   
 [Leçon 2 : Réception et filtrer les Notifications](../../adapters-and-accelerators/adapter-sql/lesson-2-receive-and-filter-notifications.md)