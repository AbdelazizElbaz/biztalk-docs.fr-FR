---
title: "Leçon 2 : Réception et filtrer les Notifications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5ec679c-1c67-4bf4-aa88-0787373343f5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f28d0479510078b3717d68f99976808ee19aa7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-2-receive-and-filter-notifications"></a>Leçon 2 : Réception et filtrer les Notifications
Dans cette leçon, vous commencez à créer une orchestration qui reçoit les notifications de modifications apportées à la **employé** table. Une fois que l’orchestration reçoit la notification, il extrait le type de notification et si le type de notification pour une opération d’insertion sur la **employé** table, une condition « if » est utilisée pour effectuer les tâches suivantes. Dans cette leçon, vous allez effectuer les tâches suivantes :  
  
1.  Ajouter un unidirectionnel port de réception et un **réception** forme à l’orchestration pour recevoir le message de notification.  
  
2.  Ajouter un **Expression** forme qui contient une requête xpath pour extraire le type de notification.  
  
3.  Une fois le type de notification est connu, ajouter un filtre à l’orchestration en incluant un **décider** forme. Cette forme décide si la notification est d’une notification d’insertion et puis effectue les opérations suivantes. Si la notification n’est pas pour une opération d’insertion, l’orchestration ne fait rien.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Ajouter des formes d’Orchestration pour recevoir une Notification](../../adapters-and-accelerators/adapter-sql/step-1-add-orchestration-shapes-to-receive-notification.md)  
  
-   [Étape 2 : Extraire le Type de Notification de Message de Notification](../../adapters-and-accelerators/adapter-sql/step-2-extract-notification-type-from-notification-message.md)  
  
-   [Étape 3 : Ajouter un filtre pour les Notifications d’insertion](../../adapters-and-accelerators/adapter-sql/step-3-add-a-filter-for-insert-notifications.md)