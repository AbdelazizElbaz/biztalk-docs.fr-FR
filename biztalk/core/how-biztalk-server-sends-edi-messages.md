---
title: Envoi des Messages EDI dans BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eaf1085-4244-4df2-9d89-52ebdf6bcbbc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4727a407c28ede98bba67774576d4d43329a946
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-biztalk-server-sends-edi-messages"></a><span data-ttu-id="71df6-102">Envoi des messages EDI par BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="71df6-102">How BizTalk Server Sends EDI Messages</span></span>
<span data-ttu-id="71df6-103">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie un message EDI, il recherche l'accord, identifie le schéma, valide le message, envoie un accusé de réception (le cas échéant) et sérialise le lot EDI.</span><span class="sxs-lookup"><span data-stu-id="71df6-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends an EDI message, it performs agreement lookup and schema discovery, validates the message, sends an acknowledgment (if appropriate), and serializes the EDI batch.</span></span> <span data-ttu-id="71df6-104">Ce traitement est effectué par l'assembleur EDI dans le pipeline d'envoi EDI.</span><span class="sxs-lookup"><span data-stu-id="71df6-104">This processing is performed by the EDI assembler in the EDI Send Pipeline.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71df6-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="71df6-105">In This Section</span></span>  
  
-   [<span data-ttu-id="71df6-106">Composants d’envoi EDI</span><span class="sxs-lookup"><span data-stu-id="71df6-106">EDI Send Components</span></span>](../core/edi-send-components.md)  
  
-   [<span data-ttu-id="71df6-107">Résolution de l’accord et détermination du schéma pour les Messages EDI sortants</span><span class="sxs-lookup"><span data-stu-id="71df6-107">Agreement Resolution and Schema Determination for Outgoing EDI Messages</span></span>](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)  
  
-   [<span data-ttu-id="71df6-108">Fonctionne de l’assembleur EDI</span><span class="sxs-lookup"><span data-stu-id="71df6-108">How the EDI Assembler Works</span></span>](../core/how-the-edi-assembler-works.md)  
  
-   [<span data-ttu-id="71df6-109">Remplacement des en-têtes EDI</span><span class="sxs-lookup"><span data-stu-id="71df6-109">Overriding EDI Headers</span></span>](../core/overriding-edi-headers.md)  
  
-   [<span data-ttu-id="71df6-110">Validation des Messages EDI sortants</span><span class="sxs-lookup"><span data-stu-id="71df6-110">Validation of Outgoing EDI Messages</span></span>](../core/validation-of-outgoing-edi-messages.md)  
  
-   [<span data-ttu-id="71df6-111">Le traitement par lot des Messages EDI sortants</span><span class="sxs-lookup"><span data-stu-id="71df6-111">Batching Outgoing EDI Messages</span></span>](../core/batching-outgoing-edi-messages.md)  
  
-   [<span data-ttu-id="71df6-112">Le traitement d’un accusé de réception</span><span class="sxs-lookup"><span data-stu-id="71df6-112">Processing a Received Acknowledgment</span></span>](../core/processing-a-received-acknowledgment.md)