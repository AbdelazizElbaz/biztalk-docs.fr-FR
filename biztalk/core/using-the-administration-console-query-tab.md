---
title: "À l’aide de l’onglet requête de la Console Administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Administration Console [BizTalk Server], Query tab
- Query tab [Administration Console]
ms.assetid: 7655f0b6-9217-46c4-88e0-ca2e661ce7a6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f20046580913ee8ea3ccb4a742ab693bcaa08d38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-administration-console-query-tab"></a>Utilisation de l'onglet Requête de la console Administration
L'onglet Requête de la page Hub du groupe dans la console Administration de BizTalk Server permet de rechercher et de localiser des abonnements, des messages ou des instances de service spécifiques en cours d'exécution ou interrompus. Les requêtes exécutées à l'aide de la console Administration localisent des éléments actifs, qui sont stockés dans la base de données MessageBox. Un onglet de requête vierge apparaît à chaque fois que vous lancez une nouvelle requête.  
  
 Le suivi des instances de service et des événements de message permet de localiser des instances de service ou des messages archivés ou suivis. Pour plus d’informations, consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).  
  
> [!NOTE]
>  Lorsque vous exécutez une requête pour les instances de service, le jeu de résultats retourné affiche la valeur de  **\<nom n’est pas disponible >** pour le **ServiceName** champ d’un service de l’instance si le correspondant port d’envoi, l’emplacement de réception ou l’orchestration a été supprimée.  Le **ServiceName** champ d’une instance de service est rempli par une recherche dans la base de données de gestion BizTalk pour le nom convivial du port d’envoi, l’emplacement de réception, ou orchestration.  Si le port d’envoi, emplacement de réception, ou d’orchestration a été supprimé puis de la recherche du nom convivial échoue et  **\<nom n’est pas disponible >** s’affiche.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment ouvrir une requête enregistrée](../core/how-to-open-a-saved-query.md)  
  
-   [Comment rechercher toutes les Instances de Service](../core/how-to-search-for-all-service-instances.md)  
  
-   [Comment rechercher des Instances de Service en cours d’exécution](../core/how-to-search-for-running-service-instances.md)  
  
-   [Comment rechercher des Instances de Service suspendues](../core/how-to-search-for-suspended-service-instances.md)  
  
-   [Comment rechercher des Messages](../core/how-to-search-for-messages.md)  
  
-   [Comment rechercher des abonnements](../core/how-to-search-for-subscriptions.md)  
  
-   [Comment enregistrer une requête](../core/how-to-save-a-query.md)  
  
-   [Comment rechercher des événements de Message suivis](../core/how-to-search-for-tracked-message-events.md)  
  
-   [Comment rechercher des Instances de Service suivies](../core/how-to-search-for-tracked-service-instances.md)