---
title: "Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite | Documents Microsoft"
description: "Structure XML des types de messages et les données utilisées par l’adaptateur mySAP pour BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ea5c27-8297-47bf-bcfd-503870349189
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9db6ec6b0fbea7ce5c8f90158126d52cbc7530ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite"></a><span data-ttu-id="2d170-103">Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="2d170-103">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>

## <a name="overview"></a><span data-ttu-id="2d170-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2d170-104">Overview</span></span>
<span data-ttu-id="2d170-105">Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2d170-105">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="2d170-106">Il expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="2d170-106">It exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="2d170-107">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="2d170-107">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="2d170-108">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="2d170-108">If a response is required, it is returned in a SOAP message over the same channel.</span></span>  
  
 <span data-ttu-id="2d170-109">Comme un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose des métadonnées pour ses types d’opérations et les données à l’aide standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mécanismes.</span><span class="sxs-lookup"><span data-stu-id="2d170-109">As a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes metadata for its operations and data types by using standard [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] mechanisms.</span></span> <span data-ttu-id="2d170-110">Les sections de cette rubrique décrivent la structure XML des messages et les types de données que le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise.</span><span class="sxs-lookup"><span data-stu-id="2d170-110">The sections in this topic describe the XML structure of the messages and data types that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d170-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2d170-111">In This Section</span></span>  
  
-   [<span data-ttu-id="2d170-112">Types de données SAP de base</span><span class="sxs-lookup"><span data-stu-id="2d170-112">Basic SAP Data Types</span></span>](../../adapters-and-accelerators/adapter-sap/basic-sap-data-types.md)  
  
-   [<span data-ttu-id="2d170-113">Mappage de Type de données pour les RFC personnalisés</span><span class="sxs-lookup"><span data-stu-id="2d170-113">Data Type Mapping for Custom RFCs</span></span>](../../adapters-and-accelerators/adapter-sap/data-type-mapping-for-custom-rfcs.md)  
  
-   [<span data-ttu-id="2d170-114">Schémas de message pour des opérations IDOC</span><span class="sxs-lookup"><span data-stu-id="2d170-114">Message Schemas for IDOC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md)  
  
-   [<span data-ttu-id="2d170-115">Propriétés de contexte de message pour recevoir des IDOC</span><span class="sxs-lookup"><span data-stu-id="2d170-115">Message Context Properties for Receiving IDOCs</span></span>](../../adapters-and-accelerators/adapter-sap/message-context-properties-for-receiving-idocs.md)  
  
-   [<span data-ttu-id="2d170-116">Schémas de message pour des opérations RFC</span><span class="sxs-lookup"><span data-stu-id="2d170-116">Message Schemas for RFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md)  
  
-   [<span data-ttu-id="2d170-117">Schémas de message pour des opérations tRFC</span><span class="sxs-lookup"><span data-stu-id="2d170-117">Message Schemas for tRFC Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md)  
  
-   [<span data-ttu-id="2d170-118">Schémas de message pour des opérations BAPI</span><span class="sxs-lookup"><span data-stu-id="2d170-118">Message Schemas for BAPI Operations</span></span>](../../adapters-and-accelerators/adapter-sap/message-schemas-for-bapi-operations.md)  
  
-   [<span data-ttu-id="2d170-119">Opérations spéciales</span><span class="sxs-lookup"><span data-stu-id="2d170-119">Special Operations</span></span>](../../adapters-and-accelerators/adapter-sap/special-operations.md)  
  
-   [<span data-ttu-id="2d170-120">Prise en charge du Versioning de message</span><span class="sxs-lookup"><span data-stu-id="2d170-120">Message Versioning Support</span></span>](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md)  
  
