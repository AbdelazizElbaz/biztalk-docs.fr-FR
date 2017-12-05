---
title: "Considérations relatives à la réception de Notifications de requête à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0142f385-3d55-41a7-a50e-dda94b96d0a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02d7aa9eadc5e639e56cc526bfd5763abc432a4f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="considerations-for-receiving-query-notifications-using-the-sql-adapter"></a>Considérations relatives à la réception de Notifications de requête à l’aide de l’adaptateur SQL
Cette rubrique fournit quelques considérations et les meilleures pratiques à prendre en compte lors de l’utilisation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des notifications de requête à partir d’une base de données SQL Server.  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a>Considérations lors de l’utilisation de l’adaptateur pour recevoir des Notifications  
 Vous devez prendre en compte les éléments suivants lors de l’utilisation du [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des notifications de requête :  
  
-   Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] reçoit la notification de requête à partir de SQL Server, puis transmet simplement sur la notification pour les clients de la carte. L’adaptateur ne distingue pas les notifications pour différentes opérations (par exemple, l’adaptateur n’a pas d’informations si une notification spécifique s’applique à une opération d’insertion ou d’une opération de mise à jour).  
  
-   Le message de notification pour une opération n’est pas affecté par le nombre d’enregistrements concernés par cette opération. Par exemple, quel que soit le nombre d’enregistrements insérés, mis à jour ou supprimées dans une table de base de données SQL Server, le client de l’adaptateur ne reçoit qu’un seul message de notification.  
  
-   Nous recommandons que l’application cliente de carte contiennent la logique pour interpréter le type de notification reçue de SQL Server. Le type de notification peut être déterminé en extrayant les informations à partir, le  **\<Info\>**  élément du message de notification a été reçue. Voici un exemple d’un message de notification reçu pour une opération d’insertion :  
  
    ```  
    <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification/">  
      <Info>Insert</Info>  
      <Source>Data</Source>  
      <Type>Change</Type>  
    </Notification>  
    ```  
  
     Notez la valeur dans la  **\<Info\>**  élément. Cette valeur fournit des informations sur l’opération pour laquelle le message de notification a été reçu. Votre application doit avoir les fonctionnalités pour extraire la valeur dans la  **\<Info\>**  élément, puis en fonction de la valeur, effectuez les tâches suivantes. La rubrique [traiter les Messages de Notification pour effectuer des tâches spécifiques dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md) contient des instructions sur la façon d’extraire la valeur dans la  **\<Info\>**  élément . Un didacticiel détaillé qui effectue des tâches similaires est également disponible à l’adresse [didacticiel 2 : employé - processus de bon de commande à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).  
  
-   Dans l’idéal, une fois que l’application cliente reçoit une notification pour un enregistrement spécifique, cet enregistrement doit être mis à jour afin que les notifications supplémentaires ne sont pas reçues. Par exemple, considérez un **employé** table qui a un **état** colonne. Pour tous les nouveaux enregistrements insérés dans le **employé** table, la valeur de la **état** colonne est toujours « 0 » et la table ressemblera à ce qui suit :  
  
    |Nom de l’employé|État|  
    |-------------------|------------|  
    |John|0|  
  
     Pour recevoir des notifications pour l’enregistrement inséré, le client de carte définira la **NotificatonStatement** de la propriété de liaison :  
  
    ```  
    SELECT Employee_ID, Name FROM dbo.Employee WHERE Status=0  
    ```  
  
    > [!NOTE]
    >  Vous devez spécifiquement spécifier les noms de colonnes dans l’instruction comme indiqué dans cette instruction de sélection. En outre, vous devez toujours spécifier le nom de table, ainsi que le nom du schéma. Par exemple, dbo. Employé.  
  
     Après avoir reçu la notification, l’application cliente doit réinitialiser la valeur de la **état** colonne sur « 1 » afin que l’instruction de notification ne fonctionne pas à nouveau sur l’enregistrement. Pour ce faire, l’application cliente doit effectuer une opération de mise à jour sur le **employé** table. Après l’opération de mise à jour, le même enregistrement dans le **employé** table doit ressembler à ce qui suit :  
  
    |Nom de l’employé|État|  
    |-------------------|------------|  
    |John|1|  
  
     Chose intéressante, l’opération de mise à jour à nouveau envoie une notification au client de carte et l’ensemble du processus est répété à nouveau, par conséquent, l’application cliente doit avoir la logique nécessaire pour ignorer ces notifications inutiles.  
  
-   Si le **NotifyOnListenerStart** liaison de la propriété a la valeur true, le client de l’adaptateur reçoit un message de notification chaque fois que l’emplacement de réception démarre. Pour plus d’informations sur la façon d’utiliser la propriété de liaison et d’interpréter le message de notification, consultez [de réception requête Notifications après une réception emplacement répartition dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-query-notifications-after-a-sql-receive-location-stops-in-biztalk.md).  
  
## <a name="typical-orchestration-for-receiving-notifications"></a>Orchestration classique pour recevoir des Notifications  
 Cette section décrit le flux typique d’orchestration pour recevoir des notifications à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
1.  La première chose que l’orchestration doit effectuer consiste à déterminer le type de notification reçue, y compris :  
  
    -   Indique si la notification a été reçue après redémarrage d’un emplacement de réception.  
  
    -   Si la notification a été reçue pour une opération sur une table de base de données, telles que Insert, Update ou Delete.  
  
     L’orchestration doit inclure un **Expression** forme et dans laquelle une requête xpath pour déterminer le type de message est reçu.  
  
2.  Après la notification de type est déterminé, l’orchestration doit inclure un bloc de décision pour effectuer des actions spécifiques en fonction du type de notification reçue. Pour ce faire, l’orchestration doit inclure un **décider** forme, qui inclut un **règle** bloc et un **Else** bloc :  
  
    -   Dans le **règle** bloc, vous devez spécifier la condition et ensuite inclure des formes d’orchestration pour effectuer certaines opérations si la condition est remplie.  
  
    -   Dans le **Else** bloc, vous devez inclure des formes d’orchestration pour effectuer certaines opérations si la condition est *pas* remplie.  
  
 Détails de la configuration requise ci-dessus sont décrits dans [traiter les Messages de Notification pour effectuer des tâches spécifiques dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/process-notification-messages-to-complete-specific-tasks-in-sql-using-biztalk.md). Un didacticiel détaillé est également disponible dans [didacticiel 2 : employé - processus de bon de commande à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/tutorial-2-employee-purchase-order-process-using-the-sql-adapter.md).