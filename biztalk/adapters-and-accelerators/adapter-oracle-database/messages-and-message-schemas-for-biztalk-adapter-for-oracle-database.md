---
title: "Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle | Documents Microsoft"
description: "Structure XML de messages et types de données utilisé par l’adaptateur de base de données Oracle pour BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fee0a531-b1e6-4b99-bb79-45368c401395
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bda5ed06470e051dc1f0bdf4595a1539aab6e6bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-database"></a>Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Il expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications. Ces opérations sont appelées en envoyant des messages SOAP sur un canal. Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.  
  
 Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes. Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Types de données Oracle de base](../../adapters-and-accelerators/adapter-oracle-database/basic-oracle-data-types1.md)  
  
-   [Schémas de message pour l’insertion de base, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [Schémas de message pour les opérations métier spéciaux](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)  
  
-   [Schémas de message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)  
  
-   [Schémas de message pour REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)  
  
-   [Schémas de message pour les Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)  
  
-   [Schémas de message pour l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)  
  
-   [Schémas de message pour les opérations d’interrogation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)  
  
-   [Schémas de message pour l’opération Composite](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)  
  
-   [Schémas de message pour l’opération de Notification](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)  
  
