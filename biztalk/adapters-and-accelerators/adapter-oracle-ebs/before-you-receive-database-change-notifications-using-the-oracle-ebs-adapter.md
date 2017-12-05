---
title: "Considérations relatives à la base de données de réception modifier des notifications à l’aide de l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95bbb19e-8d31-4b27-8cfe-6760e4bb0808
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3157b8ab7a706203d3b9475de890fb2a8f8dd3a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="considerations-for-receiving-database-change-notifications-using-the-oracle-e-business-suite-adapter"></a>Considérations relatives à la base de données réceptrice modifier des notifications à l’aide de l’adaptateur Oracle E-Business Suite
Cette rubrique fournit quelques considérations et les meilleures pratiques que vous devez garder à l’esprit lors de l’utilisation du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des notifications de la base de données à partir d’une base de données Oracle.  
  
## <a name="considerations-while-using-the-adapter-to-receive-notifications"></a>Considérations lors de l’utilisation de l’adaptateur pour recevoir des Notifications  
 Vous devez prendre en compte les éléments suivants lors de l’utilisation du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des notifications de requête.  
  
-   Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] transmet simplement sur la notification, il reçoit à partir de la base de données Oracle pour les clients de la carte. L’adaptateur ne distingue pas les notifications pour les différentes opérations, c'est-à-dire, l’adaptateur n’a pas d’informations si une notification spécifique s’applique à une opération d’insertion ou d’une opération de mise à jour.  
  
-   Le message de notification pour une opération n’est pas affecté par le nombre d’enregistrements concernés par cette opération. Par exemple, quel que soit le nombre d’enregistrements insérés dans une table de base de données Oracle, les clients de l’adaptateur de réception qu’un seul message de notification.  
  
-   Nous recommandons que l’application cliente de carte contiennent la logique pour interpréter le type de notification reçue à partir de la base de données Oracle. Les applications clientes d’adaptateur peuvent se faire en extrayant les informations contenues dans le  **\<Info\>**  élément du message de notification a été reçue. Voici un exemple d’un message de notification reçu pour une opération d’insertion.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Notification xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/Notification/">  
      <Details>  
        <NotificationDetails>  
          <ResourceName>SCOTT.ACCOUNTACTIVITY</ResourceName>   
          <Info>1</Info>   
          <QueryId>0</QueryId>   
        </NotificationDetails>  
      </Details>  
      <Info>Insert</Info>   
      <ResourceNames>  
        <string xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">SCOTT.ACCOUNTACTIVITY</string>   
      </ResourceNames>  
      <Source>Data</Source>   
      <Type>Change</Type>   
    </Notification>  
    ```  
  
     Notez la valeur dans la  **\<Info\>**  élément. Cette valeur fournit des informations sur l’opération pour laquelle le message de notification a été reçu. Votre application doit avoir les fonctionnalités pour extraire la valeur dans la  **\<Info\>**  élément, puis en fonction de la valeur, effectuez les tâches suivantes. La rubrique [traiter les Messages de Notification pour effectuer des tâches spécifiques dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md) contient des instructions sur la façon d’extraire la valeur dans la  **\<Info\>**  élément .  
  
-   Dans l’idéal, une fois que l’application cliente reçoit une notification, elle doit mettre à jour l’enregistrement pour lequel la notification est déjà reçue afin que les notifications suivantes ne sont pas pour un même enregistrement. Par exemple, considérez un **ACCOUNTACTIVITY** table qui a un **traités** colonne. Pour tous les nouveaux enregistrements insérés dans le **ACCOUNTACTIVITY** table, la valeur de la **traités** colonne est toujours n '. Par exemple, après une opération d’insertion, les enregistrements dans la **ACCOUNTACTIVITY** table doit ressembler à ce qui suit :  
  
    |ID de Transaction de compte|Traités|  
    |----------------------------|---------------|  
    |10001|n|  
  
     Pour obtenir des notifications pour l’enregistrement inséré, le client de carte définira la **NotificaitonStatement** de la propriété de liaison :  
  
    ```  
    SELECT * FROM SCOTT.ACCOUNTACTIVITY WHERE PROCESSED = ‘n’  
    ```  
  
     Après réception de la notification, l’application cliente doit définir la valeur de la **traités** colonne à 'y' afin que l’instruction de notification ne fonctionne pas sur l’enregistrement qui a été déjà informé pour. Par conséquent, pour ce faire, l’application cliente doit effectuer une opération de mise à jour sur le **ACCOUNTACTIVITY** table. Après l’opération de mise à jour, le même enregistrement dans le **ACCOUNTACTIVITY** table doit ressembler à ce qui suit :  
  
    |ID de Transaction de compte|Traités|  
    |----------------------------|---------------|  
    |10001|y|  
  
     Chose intéressante, l’opération de mise à jour à nouveau envoie une notification au client de carte et l’ensemble du processus est répété à nouveau. Par conséquent, l’application cliente doit avoir la logique nécessaire pour ignorer ces notifications inutiles.  
  
-   Si le **NotifyOnListenerStart** liaison de la propriété a la valeur true, l’adaptateur envoie une notification au client de carte chaque fois que l’emplacement de réception démarre. Pour plus d’informations sur la façon d’utiliser la propriété de liaison et d’interpréter le message de notification, consultez [réception Oracle E-Business Suite de base de données modification Notifications après une réception emplacement répartition](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-after-a-receive-location-stops.md).  
  
## <a name="typical-orchestration-for-receiving-notifications"></a>Orchestration classique pour recevoir des Notifications  
 Cette section décrit le flux typique d’orchestration pour recevoir des notifications à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
1.  La première chose que l’orchestration doit faire est de vérifier le type de notification reçue. Les éléments à vérifier sont :  
  
    -   Indique si la notification a été reçue pour le redémarrage d’emplacement de réception.  
  
    -   Si la notification a été reçue pour une opération sur une table de base de données, telles que Insert, Update ou Delete.  
  
     L’orchestration doit inclure un **Expression** forme, et dans laquelle une requête xpath, pour décider quel type de message est reçue.  
  
2.  Une fois que le type de notification n’est disponible, l’orchestration doit inclure un bloc de décision pour effectuer des actions spécifiques en fonction du type de notification reçue. Pour ce faire, l’orchestration doit inclure un **décider** forme. Le **décider** forme se compose d’un **règle** bloc et un **Else** bloc. Dans le **règle** bloc, vous devez spécifier la condition et ensuite inclure des formes d’orchestration pour effectuer certaines opérations si la condition est remplie. Dans le **Else** bloc, vous devez inclure des formes d’orchestration pour effectuer certaines opérations si la condition est *pas* remplie.  
  
 Ces recommandations sont décrites en détail dans [traiter les Messages de Notification pour effectuer des tâches spécifiques dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/process-notification-messages-to-complete-specific-tasks-in-oracle-ebs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Recevoir des Notifications de la modification de base de données Oracle E-Business Suite à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-ebs/receive-oracle-ebs-database-change-notifications-using-biztalk-server.md)