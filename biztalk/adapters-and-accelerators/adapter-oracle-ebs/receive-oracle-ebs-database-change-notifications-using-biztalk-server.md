---
title: "Recevoir des notifications de modification de base de données Oracle E-Business Suite à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e92520cf-c552-4225-abba-8e03f73ecf70
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24ac132f599256c2051763ed849e4e5329563201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-oracle-e-business-suite-database-change-notifications-using-biztalk-server"></a>Recevoir des notifications de modification de base de données Oracle E-Business Suite à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages de notification de modification de base de données à partir d’Oracle E-Business Suite. Vous pouvez spécifier une instruction SELECT qui l’adaptateur utilise pour inscrire pour les notifications avec Oracle E-Business Suite. L’adaptateur reçoit un message de notification lorsque le jeu de résultats de l’instruction SELECT, inscrite pour les notifications, change. Pour plus d’informations sur la façon dont l’adaptateur prend en charge la notification, consultez [considérations relatives à la réception de base de données des Notifications de modification à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md).  
  
 Voici quelques scénarios dans lesquels vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des notifications à partir d’Oracle E-Business Suite :  
  
-   Les clients de carte obtiennent seule la notification « incrémentielle », par exemple, uniquement pour les modifications qui ont été apportées à une table de base de données depuis la dernière notification.  
  
-   Si un grand nombre de lignes est inséré dans une table de base de données, les clients de l’adaptateur peuvent configurer plusieurs emplacements à recevoir des notifications d’équilibrer la charge de réception.  
  
 Une fois que les clients de l’adaptateur de réception un message de notification, ils peuvent effectuer des tâches spécifiques en fonction du type de notification reçue. Par exemple, une orchestration BizTalk peut être conçue de telle sorte qu’elle s’exécute un ensemble de tâches si une insertion notification est reçue et un autre ensemble de tâches si une notification de mise à jour est reçue.  
  
> [!CAUTION]
>  S’il existe une panne réseau entre la base de données Oracle et le client de carte, les notifications de n’être envoyées aux clients de la carte pour que les modifications effectuées sur la base de données Oracle pendant la période d’indisponibilité du réseau et par la suite. Par conséquent, vous devez utiliser l’opération d’interrogation au lieu de l’opération de Notification pour des scénarios critiques.  
  
 Les rubriques de cette section fournissent des informations sur la façon de configurer l’adaptateur pour chacun de ces scénarios. Pour démarrer la mise en route de notifications à partir d’Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez spécifier certaines propriétés de liaison. Pour plus d’informations sur les propriétés de liaison aux notifications, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour plus d’informations sur la structure des messages de notification, consultez [des schémas de Message pour l’opération de Notification](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md).  
  
 Pour recevoir des notifications à partir d’Oracle E-Business Suite, assurez-vous que :  
  
-   Vous utilisez l’adaptateur pour se connecter à une version de base de données Oracle prises en charge. Versions de base de données Oracle avant 10.2 ne gèrent pas les notifications.  
  
-   Le **notification de modification** privilège est nécessaire pour recevoir des notifications de modification de base de données.  Pour configurer ce privilège, se connecter à la base de données Oracle à l’aide des privilèges d’administrateur, puis tapez la commande suivante sur l’invite de commandes SQL.  
  
    ```  
    grant change notification to <user name>  
    ```  
  
-   Choisir un port TCP à utiliser pour recevoir des notifications de modification de base de données à partir de la base de données Oracle ODP.NET. Ajoutez ce port à la liste des exceptions du pare-feu Windows. Pour obtenir des instructions sur la façon d’ajouter des ports à la liste des exceptions du pare-feu Windows, consultez [http://go.microsoft.com/fwlink/?LinkID=196959](http://go.microsoft.com/fwlink/?LinkID=196959). Vous devez fournir le numéro de port pour le **NotificationPort** propriété de liaison. Pour plus d’informations sur la propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Considérations relatives à la réception de base de données des Notifications de modification à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/before-you-receive-database-change-notifications-using-the-oracle-ebs-adapter.md)  
  
-   [Traiter les Messages de Notification pour effectuer des tâches spécifiques dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md)  
  
-   [Recevoir des Notifications de modification Oracle E-Business Suite incrémentielle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-change-notifications-incrementally-using-biztalk-server.md)  
  
-   [Réception d’Oracle E-Business Suite de base de données modifiées des Notifications sur plusieurs emplacements de réception](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-on-multiple-receive-locations.md)  
  
-   [Recevoir des Notifications de modification de base de données Oracle E-Business Suite après une panne de l’emplacement de réception](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)