---
title: "Schémas de message pour la Notification Operation1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f98d76d0-6084-4de7-b6ff-124202ca92ab
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dd0d7513a0a439d34d5bfb4722fec2b9025e676b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-notification-operation"></a>Schémas de message pour l’opération de Notification
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence l’opération de Notification pour recevoir des notifications de modification de base de données à partir de la base de données Oracle.  
  
 Vous configurez l’opération de Notification en définissant des propriétés de liaison dans le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Pour plus d’informations sur les propriétés liées à la Notification de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). Vous définissez la **NotificationStatement** liaison de propriété pour spécifier une instruction SELECT pour la notification de requête.  
  
## <a name="message-structure-for-the-notification-operation"></a>Structure de message pour l’opération de Notification  
 Le tableau suivant montre la structure de message XML pour l’opération de Notification.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|Notification|`<?xml version="1.0" encoding="utf-8" ?>  <Notification xmlns="http://Microsoft.LobServices.OracleDB/2007/03/Notification">    <Info>Value</Info>    <Source>Value</Source>    <Type>Value</Type> </Notification>`|Il s’agit du message entrant envoyé par la base de données Oracle pour les clients de la carte. Dans le message :<br /><br /> -La `<Info>` balise indique la raison de la notification. Par exemple, une valeur de « insert » dans cette balise indique que les données a été insérées dans une ou plusieurs des tables référencées dans l’instruction de notification.<br /><br /> -La `<Source>` balise indique la source de la notification. Par exemple, une valeur de « données » dans cette balise indique une modification de données dans un objet référencé. De même, une valeur de « objet » dans cette balise indique une modification dans un objet référencé.<br /><br /> -La `<Type>` étiquette indique le type de modification des données. Par exemple, un « Update » valeur dans la `<Type>` balise indique que les résultats de la requête ont été mis à jour.|  
  
## <a name="message-action-for-the-notification-operation"></a>Action de message pour l’opération de Notification  
 L’action du message pour l’opération de notification est « http://Microsoft.LobServices.OracleDB/2007/03/Notification ».  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)