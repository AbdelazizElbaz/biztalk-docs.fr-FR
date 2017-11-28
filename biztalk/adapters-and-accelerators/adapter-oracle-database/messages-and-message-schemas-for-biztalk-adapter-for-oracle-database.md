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
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-oracle-database"></a><span data-ttu-id="157c6-103">Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="157c6-103">Messages and Message Schemas for BizTalk Adapter for Oracle Database</span></span>

## <a name="overview"></a><span data-ttu-id="157c6-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="157c6-104">Overview</span></span>
<span data-ttu-id="157c6-105">Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="157c6-105">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="157c6-106">Il expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="157c6-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="157c6-107">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="157c6-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="157c6-108">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="157c6-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="157c6-109">Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes.</span><span class="sxs-lookup"><span data-stu-id="157c6-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="157c6-110">Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="157c6-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="157c6-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="157c6-111">In This Section</span></span>  
  
-   [<span data-ttu-id="157c6-112">Types de données Oracle de base</span><span class="sxs-lookup"><span data-stu-id="157c6-112">Basic Oracle Data Types</span></span>](../../adapters-and-accelerators/adapter-oracle-database/basic-oracle-data-types1.md)  
  
-   [<span data-ttu-id="157c6-113">Schémas de message pour l’insertion de base, mettre à jour, supprimer et sélectionner des opérations sur les Tables et vues</span><span class="sxs-lookup"><span data-stu-id="157c6-113">Message Schemas for the Basic Insert, Update, Delete, and Select Operations on Tables and Views</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md)  
  
-   [<span data-ttu-id="157c6-114">Schémas de message pour les opérations métier spéciaux</span><span class="sxs-lookup"><span data-stu-id="157c6-114">Message Schemas for Special LOB Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md)  
  
-   [<span data-ttu-id="157c6-115">Schémas de message pour les fonctions et procédures</span><span class="sxs-lookup"><span data-stu-id="157c6-115">Message Schemas for Functions and Procedures</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md)  
  
-   [<span data-ttu-id="157c6-116">Schémas de message pour REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="157c6-116">Message Schemas for REF CURSORS</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md)  
  
-   [<span data-ttu-id="157c6-117">Schémas de message pour les Types d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="157c6-117">Message Schemas for RECORD Types</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md)  
  
-   [<span data-ttu-id="157c6-118">Schémas de message pour l’opération SQLEXECUTE</span><span class="sxs-lookup"><span data-stu-id="157c6-118">Message Schemas for the SQLEXECUTE Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md)  
  
-   [<span data-ttu-id="157c6-119">Schémas de message pour les opérations d’interrogation</span><span class="sxs-lookup"><span data-stu-id="157c6-119">Message Schemas for the Polling Operations</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)  
  
-   [<span data-ttu-id="157c6-120">Schémas de message pour l’opération Composite</span><span class="sxs-lookup"><span data-stu-id="157c6-120">Message Schemas for the Composite Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md)  
  
-   [<span data-ttu-id="157c6-121">Schémas de message pour l’opération de Notification</span><span class="sxs-lookup"><span data-stu-id="157c6-121">Message Schemas for the Notification Operation</span></span>](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-notification-operation1.md)  
  
