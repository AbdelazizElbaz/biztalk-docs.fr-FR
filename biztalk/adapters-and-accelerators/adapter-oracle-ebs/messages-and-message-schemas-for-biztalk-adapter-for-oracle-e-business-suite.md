---
title: "Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite | Documents Microsoft"
description: "Structure XML des types de messages et les données utilisées par l’adaptateur Oracle eBusiness Suite pour BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4434b4d4-fbe0-4692-81a5-9883c9a77cf6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9069e5bf83f323726da7c8b08b9f5cc7ca6ccd85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite"></a><span data-ttu-id="5f1c3-103">Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite</span><span class="sxs-lookup"><span data-stu-id="5f1c3-103">Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite</span></span>

## <a name="overview"></a><span data-ttu-id="5f1c3-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="5f1c3-104">Overview</span></span>
<span data-ttu-id="5f1c3-105">Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="5f1c3-105">The [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="5f1c3-106">Il expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="5f1c3-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="5f1c3-107">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="5f1c3-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="5f1c3-108">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="5f1c3-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="5f1c3-109">Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes.</span><span class="sxs-lookup"><span data-stu-id="5f1c3-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="5f1c3-110">Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="5f1c3-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f1c3-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5f1c3-111">In This Section</span></span>  
  
-   [<span data-ttu-id="5f1c3-112">Types de données Oracle de base</span><span class="sxs-lookup"><span data-stu-id="5f1c3-112">Basic Oracle Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/basic-oracle-data-types2.md)  
  
-   [<span data-ttu-id="5f1c3-113">Schémas de message pour insérer, mettre à jour, supprimer et sélectionner des opérations</span><span class="sxs-lookup"><span data-stu-id="5f1c3-113">Message Schemas for Insert, Update, Delete, and Select Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-insert-update-delete-and-select-operations.md)  
  
-   [<span data-ttu-id="5f1c3-114">Schémas de message pour les procédures stockées, fonctions et API PL/SQL</span><span class="sxs-lookup"><span data-stu-id="5f1c3-114">Message Schemas for Stored Procedures, Functions, and PL/SQL APIs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-stored-procedures-functions-and-pl-sql-apis.md)  
  
-   [<span data-ttu-id="5f1c3-115">Schémas de message pour les programmes simultanés</span><span class="sxs-lookup"><span data-stu-id="5f1c3-115">Message Schemas for Concurrent Programs</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md)  
  
-   [<span data-ttu-id="5f1c3-116">Schémas de message pour les ensembles de requêtes</span><span class="sxs-lookup"><span data-stu-id="5f1c3-116">Message Schemas for Request Sets</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md)  
  
-   [<span data-ttu-id="5f1c3-117">Schémas de message pour les opérations métier spéciaux</span><span class="sxs-lookup"><span data-stu-id="5f1c3-117">Message Schemas for Special LOB Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md)  
  
-   [<span data-ttu-id="5f1c3-118">Schémas de message pour les opérations d’interrogation</span><span class="sxs-lookup"><span data-stu-id="5f1c3-118">Message Schemas for the Polling Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-polling-operations1.md)  
  
-   [<span data-ttu-id="5f1c3-119">Schémas de message pour l’opération de Notification</span><span class="sxs-lookup"><span data-stu-id="5f1c3-119">Message Schemas for the Notification Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-notification-operation2.md)  
  
-   [<span data-ttu-id="5f1c3-120">Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar</span><span class="sxs-lookup"><span data-stu-id="5f1c3-120">Message Schemas for the ExecuteNonQuery, ExecuteReader, and ExecuteScalar Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/executenonquery-executereader-and-executescalar-message-schemas.md)  
  
-   [<span data-ttu-id="5f1c3-121">Schémas de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="5f1c3-121">Message Schemas for the Composite Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-the-composite-operation1.md)  
  