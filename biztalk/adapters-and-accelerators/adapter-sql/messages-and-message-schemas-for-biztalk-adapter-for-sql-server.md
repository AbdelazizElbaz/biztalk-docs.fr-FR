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
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-sql-server"></a><span data-ttu-id="0f793-103">Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f793-103">Messages and Message Schemas for BizTalk Adapter for SQL Server</span></span>

## <a name="overview"></a><span data-ttu-id="0f793-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="0f793-104">Overview</span></span>
<span data-ttu-id="0f793-105">Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="0f793-105">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="0f793-106">Il expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="0f793-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="0f793-107">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="0f793-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="0f793-108">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="0f793-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="0f793-109">Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes.</span><span class="sxs-lookup"><span data-stu-id="0f793-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="0f793-110">Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="0f793-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f793-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0f793-111">In This Section</span></span>  
  
-   [<span data-ttu-id="0f793-112">Types de données de base de SQL Server</span><span class="sxs-lookup"><span data-stu-id="0f793-112">Basic SQL Server Data Types</span></span>](../../adapters-and-accelerators/adapter-sql/basic-sql-server-data-types.md)  
  
-   [<span data-ttu-id="0f793-113">Schémas de message pour insérer, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues</span><span class="sxs-lookup"><span data-stu-id="0f793-113">Message Schemas for Insert, Update, Delete, and Select Operations on Tables and Views</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [<span data-ttu-id="0f793-114">Schémas de message pour les procédures et fonctions</span><span class="sxs-lookup"><span data-stu-id="0f793-114">Message Schemas for Procedures and Functions</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md)  
  
-   [<span data-ttu-id="0f793-115">Schémas de message pour l’interrogation et les opérations de TypedPolling</span><span class="sxs-lookup"><span data-stu-id="0f793-115">Message Schemas for the Polling and TypedPolling Operations</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md)  
  
-   [<span data-ttu-id="0f793-116">Schémas de message de notification de requête</span><span class="sxs-lookup"><span data-stu-id="0f793-116">Message Schemas for Query Notification</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-query-notification.md)  
  
-   [<span data-ttu-id="0f793-117">Schémas de message pour des opérations composites</span><span class="sxs-lookup"><span data-stu-id="0f793-117">Message Schemas for Composite Operations</span></span>](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md)  
  
-   [<span data-ttu-id="0f793-118">Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="0f793-118">Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-sql/executenonquery-executereader-and-executescalar-message-schemas-in-sql.md)  
  
