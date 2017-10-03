---
title: "Recevoir des Notifications de modification de base de données Oracle à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 495a29bc-72f6-4140-8160-0b917d935503
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 69d4b4b3a0b528109caac60ecec3c3614e5d7a5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-database-change-notifications-using-biztalk-server"></a>Recevoir des Notifications de modification de base de données Oracle à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour recevoir des messages de notification de modification de base de données à partir de la base de données Oracle. Vous pouvez spécifier une instruction SELECT qui l’adaptateur utilise pour inscrire pour les notifications avec la base de données Oracle. L’adaptateur reçoit un message de notification lorsque le jeu de résultats de l’instruction SELECT, inscrite pour les notifications, change. Pour plus d’informations sur la façon dont l’adaptateur prend en charge la notification, consultez [considérations relatives à la réception de base de données des Notifications de modification à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md).  
  
 Voici quelques scénarios dans lesquels vous pouvez configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des notifications à partir de la base de données Oracle :  
  
-   Les clients de carte obtiennent seule la notification « incrémentielle », par exemple, uniquement pour les modifications qui ont été apportées à une table de base de données depuis la dernière notification.  
  
-   Si de nombreuses lignes sont insérées dans une table de base de données, les clients de l’adaptateur peuvent configurer plusieurs emplacements à recevoir des notifications d’équilibrer la charge de réception.  
  
 Une fois que les clients de l’adaptateur de réception un message de notification, ils peuvent effectuer des tâches spécifiques en fonction du type de notification reçue. Par exemple, une orchestration BizTalk peut être conçue de telle sorte qu’elle s’exécute un ensemble de tâches si une insertion notification est reçue et un autre ensemble de tâches si une notification de mise à jour est reçue.  
  
> [!CAUTION]
>  S’il existe une panne réseau entre la base de données Oracle et le client de carte, les notifications de n’être envoyées aux clients de la carte pour que les modifications effectuées sur la base de données Oracle pendant la période d’indisponibilité du réseau et par la suite. Par conséquent, vous devez utiliser l’opération d’interrogation au lieu de l’opération de Notification pour des scénarios critiques.  
  
 Les rubriques de cette section fournissent des informations sur la façon de configurer l’adaptateur pour chacun de ces scénarios. Pour démarrer la mise en route de notifications à partir de la base de données Oracle à l’aide du [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], vous devez spécifier certaines propriétés de liaison. Pour plus d’informations sur les propriétés de liaison aux notifications, consultez [fonctionne avec les propriétés de liaison](https://msdn.microsoft.com/library/dd788467.aspx). Pour plus d’informations sur la structure des messages de notification, consultez [des schémas de Message pour l’opération de Notification](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md).  
  
 Pour recevoir des notifications de la base de données Oracle, assurez-vous que :  
  
-   Vous utilisez l’adaptateur pour se connecter à la version de base de données Oracle 10.2 ou version ultérieure. Versions de base de données Oracle avant 10.2 ne gèrent pas les notifications.  
  
-   Les informations d’identification que vous utilisez pour vous connecter à Oracle pour les notifications a `change notification` privilège. Ce privilège est nécessaire pour recevoir des notifications de modification de base de données. Pour ce faire, vous connecter à la base de données Oracle à l’aide des privilèges d’administrateur et tapez la commande suivante sur l’invite de commandes SQL.  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   Choisir un port TCP à utiliser pour recevoir des notifications de modification de base de données à partir de la base de données Oracle ODP.NET. Ajoutez ce port à la liste des exceptions du pare-feu Windows. Pour obtenir des instructions sur la façon d’ajouter des ports à la liste des exceptions du pare-feu Windows, consultez [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). Vous devez fournir le numéro de port pour le **NotificationPort** propriété de liaison. Pour plus d’informations sur la propriété de liaison, consultez [fonctionne avec les propriétés de liaison](https://msdn.microsoft.com/library/dd788467.aspx).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Considérations pour recevoir des Notifications de modification de base de données à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [Le traitement des Messages de Notification pour effectuer des tâches spécifiques dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/process-notification-messages-to-run-specific-tasks-in-oracle-db-using-biztalk.md)  
  
-   [Recevoir des Notifications de modification de base de données Oracle incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [Réception Notifications de modification de la base de données Oracle sur plusieurs emplacements de réception](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [Recevoir des Notifications de modification de base de données Oracle après une panne de l’emplacement de réception](../../adapters-and-accelerators/adapter-oracle-database/receive-oracle-database-change-notifications-after-a-receive-location-breakdown.md)  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)