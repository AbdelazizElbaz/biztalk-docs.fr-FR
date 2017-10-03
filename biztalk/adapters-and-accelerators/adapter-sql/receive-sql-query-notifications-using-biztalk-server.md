---
title: "Recevoir des Notifications de requête SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69444df7-f2ae-4d1a-9b49-817b437517d8
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1632bde50a0daf9df22b9c1cfb7aaca8d59fbce7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-sql-query-notifications-using-biztalk-server"></a>Recevoir des Notifications de requête SQL à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de notification pour les tables SQL Server ou des vues. Vous pouvez spécifier une instruction SQL que l’adaptateur utilise pour inscrire pour les notifications avec SQL Server. L’instruction de notification peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats. Pour plus d’informations sur les notifications de requête, consultez « À l’aide de Notifications de requête » à [http://go.microsoft.com/fwlink/?LinkId=122159](http://go.microsoft.com/fwlink/?LinkId=122159). Pour plus d’informations sur les requêtes qui peut être utilisé pour les notifications de requête, consultez « Création d’une requête pour Notification » à [http://go.microsoft.com/fwlink/?LinkId=122160](http://go.microsoft.com/fwlink/?LinkId=122160).  
  
 Recevoir des notifications de requête de SQL Server est similaire à l’interrogation de SQL Server, avec quelques différences importantes. Pour obtenir la liste des différences, consultez [considérations relatives à la réception de requête des Notifications à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md).  
  
 Voici quelques scénarios dans lesquels vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des notifications à partir de SQL Server :  
  
-   Les clients de carte obtiennent seule la notification « incrémentielle », par exemple, uniquement pour les modifications qui ont été apportées à une table de base de données depuis la dernière notification.  
  
-   Si le nombre de lignes est insérée dans une table de base de données, les clients de l’adaptateur peuvent configurer plusieurs emplacements à recevoir des notifications d’équilibrer la charge de réception.  
  
-   Si l’emplacement de réception sur lequel l’adaptateur les clients reçoivent des notifications tombe en panne, les clients de l’adaptateur peuvent configurer l’adaptateur pour recevoir une notification dès que l’emplacement de réception est de nouveau. Les clients doivent également implémenter la logique dans leur application pour traiter les enregistrements qui peuvent ont été insérées, mises à jour ou supprimés lors de l’emplacement de réception vers le bas.  
  
 Une fois que les clients de l’adaptateur de réception un message de notification, ils peuvent effectuer des tâches spécifiques en fonction du type de notification reçue. Par exemple, une orchestration BizTalk peut être conçue de telle sorte qu’elle s’exécute un ensemble de tâches si une insertion notification est reçue et un autre ensemble de tâches si une notification de mise à jour est reçue.  
  
 Les rubriques de cette section fournissent des informations sur la configuration de l’adaptateur pour chacun de ces scénarios. Pour démarrer la mise en route de notifications à partir de SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez spécifier certaines propriétés de liaison. Pour plus d’informations sur comment l’adaptateur prend en charge la réception de messages, consultez [considérations relatives à la réception de requête des Notifications à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md). Pour plus d’informations sur les propriétés de liaison aux notifications, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Pour plus d’informations sur la structure des messages de notification, consultez [schémas de Message de notification de requête](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md).  
  
 Vous devez également effectuer les tâches suivantes sur SQL Server pour activer les notifications de requête.  
  
-   Vous devez activer Service Broker pour la base de données SQL Server.  
  
-   Vous devez vous assurer que le client de carte dispose des autorisations nécessaires pour exécuter des commandes pour notification de la demande.  
  
 Pour plus d’informations sur ces tâches, consultez « Activation des Notifications de requête » à [http://go.microsoft.com/fwlink/?LinkID=122323](http://go.microsoft.com/fwlink/?LinkID=122323).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Considérations relatives à la réception de requête des Notifications à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/considerations-for-receiving-query-notifications-using-the-sql-adapter.md)  
  
-   [Traiter les Messages de Notification pour effectuer des tâches spécifiques dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md)  
  
-   [Recevoir des Notifications de requête par incréments de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-incrementally-from-sql-using-biztalk-server.md)  
  
-   [Réception de requête des Notifications sur plusieurs emplacements de réception à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-on-receive-locations-from-sql-server-using-biztalk.md)  
  
-   [Réception de requête Notifications après une réception emplacement répartition dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)