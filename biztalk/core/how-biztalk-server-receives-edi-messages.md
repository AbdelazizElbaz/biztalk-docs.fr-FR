---
title: "Réception des Messages EDI dans BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f3bb88c-9226-4791-b100-ba68dea45278
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb7cdda6a54db06c0388d8c72dcb65a2c8f21f02
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-receives-edi-messages"></a><span data-ttu-id="7e99d-102">Réception des messages EDI par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="7e99d-102">How BizTalk Server Receives EDI Messages</span></span>
<span data-ttu-id="7e99d-103">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message EDI, il recherche l'accord de partenariat commercial, identifie le schéma, valide le message, envoie un accusé de réception (le cas échéant) et analyse le lot EDI.</span><span class="sxs-lookup"><span data-stu-id="7e99d-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI message, it performs trading partner agreement lookup and schema discovery, validates the message, sends an acknowledgment (if appropriate), and parses the EDI batch.</span></span> <span data-ttu-id="7e99d-104">Ce traitement est effectué par le Désassembleur EDI dans le pipeline de réception EDI.</span><span class="sxs-lookup"><span data-stu-id="7e99d-104">This processing is performed by the EDI disassembler in the EDI Receive Pipeline.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e99d-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7e99d-105">In This Section</span></span>  
  
-   [<span data-ttu-id="7e99d-106">Composants de réception EDI</span><span class="sxs-lookup"><span data-stu-id="7e99d-106">EDI Receive Components</span></span>](../core/edi-receive-components.md)  
  
-   [<span data-ttu-id="7e99d-107">Résolution de l’accord, détection de schéma et l’autorisation des Messages EDI reçus</span><span class="sxs-lookup"><span data-stu-id="7e99d-107">Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages</span></span>](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)  
  
-   [<span data-ttu-id="7e99d-108">Fonctionne du désassembleur EDI</span><span class="sxs-lookup"><span data-stu-id="7e99d-108">How the EDI Disassembler Works</span></span>](../core/how-the-edi-disassembler-works.md)  
  
-   [<span data-ttu-id="7e99d-109">Validation des Messages EDI reçus</span><span class="sxs-lookup"><span data-stu-id="7e99d-109">Validation of Received EDI Messages</span></span>](../core/validation-of-received-edi-messages.md)  
  
-   [<span data-ttu-id="7e99d-110">Envoi d’un accusé de réception EDI</span><span class="sxs-lookup"><span data-stu-id="7e99d-110">Sending an EDI Acknowledgment</span></span>](../core/sending-an-edi-acknowledgment.md)  
  
-   [<span data-ttu-id="7e99d-111">Traitement des lots entrants</span><span class="sxs-lookup"><span data-stu-id="7e99d-111">Processing Incoming Batches</span></span>](../core/processing-incoming-batches.md)