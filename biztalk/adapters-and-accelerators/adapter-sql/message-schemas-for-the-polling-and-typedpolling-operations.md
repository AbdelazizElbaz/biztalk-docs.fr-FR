---
title: "Schémas de message pour l’interrogation et les opérations de TypedPolling de l’adaptateur SQL dans BizTalk | Documents Microsoft"
description: "L’interrogation et TypedPolling message structure utilisée par l’adaptateur SQL dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e900307-2c9c-493b-81c9-67af3e143eeb
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cd6a281bfca73e74f23ce25bb9fa08761a07789
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-the-polling-and-typedpolling-operations"></a>Schémas de message pour l’interrogation et les opérations de TypedPolling
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] surfaces d’interrogation et de TypedPolling entrant operations pour retourner le jeu de résultats de la requête d’interrogation à un client de carte.  
  
 Vous configurez les opérations d’interrogation et TypedPolling en définissant les propriétés de liaison dans le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Pour plus d’informations sur ces propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md). Vous définissez la **PollingStatement** liaison de propriété pour spécifier une instruction SQL (SELECT ou EXEC \<procédure stockée\>) pour la requête d’interrogation. Le jeu de résultats de cette requête est retourné sous forme de données à votre code dans l’opération d’interrogation et en tant que données fortement typées dans l’opération TypedPolling. La structure du jeu de résultats est déterminée par les métadonnées que l’adaptateur met en évidence pour la requête spécifiée.  
  
## <a name="polling-message-structure"></a>Structure des messages d’interrogation 
  
**Opération**:`Polling`

**Message XML**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <Polling xmlns="http://schemas.microsoft.com/Sql/2008/05/Polling">
    <PolledData>
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">
        <any>[Value]</any>
        <any>[Value]</any>
        …
        </DataSet>
    </PolledData>
 </Polling>
```

**Description**: le message entrant envoyé par le serveur SQL Server pour les clients de la carte.  


## <a name="typedpolling-message-structure"></a>Structure de message TypedPolling 

**Opération**:`TypedPolling`

**Message XML**:  
```xml
<?xml version="1.0" encoding="utf-8" ?>
  <TypedPollingResultSet xmlns="http://schemas.microsoft.com/Sql/2008/05/TypedPolling">
    <COLUMN1>[Value]</Column1>
    <COLUMN2>[Value]</Column2>
    …
  </TypedPollingResultSet>
```

**Description**: le message entrant fortement typée qui est envoyé par le serveur SQL Server pour les clients de la carte.
  
## <a name="message-action-for-the-polling-and-typedpolling-operations"></a>Action du message pour l’interrogation et les opérations de TypedPolling  
 L’action du message pour le :  
  
-   Opération d’interrogation est « interrogation ».  
  
-   L’opération TypedPolling est « TypedPolling. »  
  
