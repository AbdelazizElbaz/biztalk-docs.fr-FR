---
title: "Schémas de message pour la Notification de requête à l’aide de l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "Utilisez l’adaptateur SQL pour recevoir des notifications de requête à partir d’une base de données SQL Server dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5183655-64d4-4767-a923-0a575e3708cd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f662f34a9ac31dd5ce200d776bc8b542008e98e1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-query-notification"></a>Schémas de message de notification de requête
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] met en évidence l’opération de Notification pour recevoir des notifications de requête à partir de la base de données SQL Server.  
  
 Vous configurez l’opération de Notification en définissant des propriétés de liaison dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur les propriétés liées à la Notification de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Vous définissez la **NotificationStatement** liaison de propriété pour spécifier une instruction SQL (SELECT ou EXEC \<procédure stockée\>) pour la notification de requête. Le jeu de résultats de cette requête est retourné en tant que données fortement typées à votre code dans l’opération de Notification.  
  
## <a name="message-structure-for-the-notification-operation"></a>Structure de message pour l’opération de Notification  
 Le tableau suivant montre la structure de message XML pour l’opération de Notification.  

**Opération**:`Notification`

**Message XML**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Notification xmlns="http://schemas.microsoft.com/Sql/2008/05/Notification">
    <Info>Value</Info>
    <Source>Value</Source>
    <Type>Value</Type>
 </Notification>
```

**Description**: c’est le message entrant envoyé par le serveur SQL Server pour les clients de la carte. Dans le message :

- Le `<Info>` balise indique la raison de la notification. Par exemple, une valeur de « insert » dans cette balise indique que les données a été insérées dans une ou plusieurs des tables référencées dans l’instruction de notification.
- Le `<Source>` balise indique la source de la notification. Par exemple, une valeur de « données » dans cette balise indique une modification de données dans un objet référencé. De même, une valeur de « objet » dans cette balise indique une modification dans un objet référencé.
- Le `<Type>` étiquette indique le type de modification des données. Les messages de notification de requête sont de deux types : modifier et de s’abonner. Un « modifier » la valeur dans la `<Type>` balise indique que les résultats de la requête ont changé, tandis qu’une valeur « s’abonner » dans la `<Type>` balise indique qu’une demande d’abonnement a échoué.

  
## <a name="message-action-for-the-notification-operation"></a>Action de message pour l’opération de Notification  
 L’action du message pour l’opération de notification est « Notification ».  
  