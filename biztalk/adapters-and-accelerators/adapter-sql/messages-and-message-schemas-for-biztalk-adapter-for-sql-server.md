---
title: "Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server | Documents Microsoft"
description: "Structure XML de messages et types de données utilisé par l’adaptateur de SQL Server pour BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e95c6342-5420-4fb8-9b41-7c87d27b5b68
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b1e45f0a20500253e2ca831138a21efa24df3c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-sql-server"></a>Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Il expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications. Ces opérations sont appelées en envoyant des messages SOAP sur un canal. Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.  
  
 Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes. Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de données de base de SQL Server](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md)  
  
-   [Schémas de message pour insérer, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [Schémas de message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)  
  
-   [Schémas de message pour l’interrogation et les opérations de TypedPolling](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)  
  
-   [Schémas de message de notification de requête](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)  
  
-   [Schémas de message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)  
  
-   [Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar](../../adapters-and-accelerators/adapter-sql/executenonquery-executereader-and-executescalar-message-schemas-in-sql.md)  
  
