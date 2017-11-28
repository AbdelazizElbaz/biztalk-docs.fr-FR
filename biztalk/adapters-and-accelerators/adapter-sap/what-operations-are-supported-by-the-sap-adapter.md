---
title: "Les opérations sont prises en charge par l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: adapters, performing operations
ms.assetid: 4b676336-526d-42b9-9ff2-1a4f27df1a78
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee217572e0bf56e7a4f7e4810421befeb08bfc3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-sap-adapter"></a><span data-ttu-id="a6b42-102">Les opérations sont prises en charge par l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="a6b42-102">What operations are supported by the SAP adapter</span></span>
<span data-ttu-id="a6b42-103">Les clients de l’adaptateur peuvent effectuer des opérations sur le système SAP en créant les projets BizTalk, en utilisant le modèle de canal WCF ou en utilisant le modèle de service WCF.</span><span class="sxs-lookup"><span data-stu-id="a6b42-103">Adapter clients can perform operations on the SAP system by creating BizTalk projects, by using the WCF channel model, or by using the WCF service model.</span></span> <span data-ttu-id="a6b42-104">Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications.</span><span class="sxs-lookup"><span data-stu-id="a6b42-104">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exposes operations that applications can invoke on it and that it can, in turn, invoke on applications.</span></span> <span data-ttu-id="a6b42-105">Ces opérations sont appelées en envoyant des messages SOAP sur un canal.</span><span class="sxs-lookup"><span data-stu-id="a6b42-105">These operations are invoked by sending SOAP messages over a channel.</span></span> <span data-ttu-id="a6b42-106">Si une réponse est requise, il est retourné dans un message SOAP sur le même canal.</span><span class="sxs-lookup"><span data-stu-id="a6b42-106">If a response is required, it is returned in a SOAP message over the same channel.</span></span> <span data-ttu-id="a6b42-107">Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span><span class="sxs-lookup"><span data-stu-id="a6b42-107">For information about the message structure and the SOAP action associated with each operation, see [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>  
  
 <span data-ttu-id="a6b42-108">Cette section fournit des informations sur les opérations prises en charge sur le système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6b42-108">This section provides information about the operations supported on the SAP system using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6b42-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a6b42-109">In This Section</span></span>  
  
-   [<span data-ttu-id="a6b42-110">Opérations sur les documents RFC dans SAP</span><span class="sxs-lookup"><span data-stu-id="a6b42-110">Operations on RFCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md)  
  
-   [<span data-ttu-id="a6b42-111">Opérations sur tRFCs dans SAP</span><span class="sxs-lookup"><span data-stu-id="a6b42-111">Operations on tRFCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md)  
  
-   [<span data-ttu-id="a6b42-112">Opérations sur les BAPI dans SAP</span><span class="sxs-lookup"><span data-stu-id="a6b42-112">Operations on BAPIs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md)  
  
-   [<span data-ttu-id="a6b42-113">Opérations sur IDOC dans SAP</span><span class="sxs-lookup"><span data-stu-id="a6b42-113">Operations on IDOCs in SAP</span></span>](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md)