---
title: "Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications | Documents Microsoft"
description: "Structure XML de messages et types de données utilisé par l’adaptateur Siebel dans le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b4da884-89b0-4ab1-a728-c5569088a993
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 294662793fc8103813b582d1b0d84db4447b0e7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-siebel-ebusiness-applications"></a><span data-ttu-id="49fa1-103">Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications</span><span class="sxs-lookup"><span data-stu-id="49fa1-103">Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications</span></span>

## <a name="overview"></a><span data-ttu-id="49fa1-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="49fa1-104">Overview</span></span>
<span data-ttu-id="49fa1-105">Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="49fa1-105">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="49fa1-106">Il expose les opérations que les applications peuvent appeler sur un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="49fa1-106">It exposes operations that applications can invoke on a Siebel system.</span></span> <span data-ttu-id="49fa1-107">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="49fa1-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="49fa1-108">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="49fa1-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="49fa1-109">Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes.</span><span class="sxs-lookup"><span data-stu-id="49fa1-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="49fa1-110">Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="49fa1-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49fa1-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="49fa1-111">In This Section</span></span>  
  
-   [<span data-ttu-id="49fa1-112">Types de données de base Siebel</span><span class="sxs-lookup"><span data-stu-id="49fa1-112">Basic Siebel Data Types</span></span>](basic-siebel-data-types.md)  
  
-   [<span data-ttu-id="49fa1-113">Schémas de message pour les opérations de composant d’entreprise</span><span class="sxs-lookup"><span data-stu-id="49fa1-113">Message Schemas for Business Component Operations</span></span>](message-schemas-for-business-component-operations.md)  
  
-   [<span data-ttu-id="49fa1-114">Schémas de message pour les opérations de Service d’entreprise</span><span class="sxs-lookup"><span data-stu-id="49fa1-114">Message Schemas for Business Service Operations</span></span>](message-schemas-for-business-service-operations.md)  
  
-   [<span data-ttu-id="49fa1-115">Schéma de message pour les opérations de liste de choix</span><span class="sxs-lookup"><span data-stu-id="49fa1-115">Message Schema for Picklist Operations</span></span>](message-schema-for-picklist-operations.md)  
  
-   [<span data-ttu-id="49fa1-116">Prise en charge du Versioning de message</span><span class="sxs-lookup"><span data-stu-id="49fa1-116">Message Versioning Support</span></span>](message-versioning-support2.md)  
  
