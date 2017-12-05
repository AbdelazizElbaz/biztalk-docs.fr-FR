---
title: Traitement SQL dans BTARN | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- line-of-business applications (LOBs)
- LOBs
- SQL processing
- messages, message flow
- BTARN, SQL processing
ms.assetid: cfaf804f-3803-438e-a22e-50f487fe21c3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24798038ef7110a87efef2850c7787c066ae9511
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="sql-processing-in-btarn"></a><span data-ttu-id="20c0b-102">Traitement SQL dans BTARN</span><span class="sxs-lookup"><span data-stu-id="20c0b-102">SQL Processing in BTARN</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="20c0b-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise un adaptateur SQL pour router un message à partir de l’application de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="20c0b-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses a SQL adapter to route a message from the line-of-business (LOB) application.</span></span> <span data-ttu-id="20c0b-104">Il utilise un port d'envoi SQL pour acheminer un message vers l'application métier.</span><span class="sxs-lookup"><span data-stu-id="20c0b-104">It uses a SQL send port to route a message to the LOB application.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="20c0b-105">Flux de messages</span><span class="sxs-lookup"><span data-stu-id="20c0b-105">Message Flow</span></span>  
 <span data-ttu-id="20c0b-106">Sur soit l’initiateur ou répondeur, l’application métier principale achemine un message à la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données.</span><span class="sxs-lookup"><span data-stu-id="20c0b-106">On either the initiator or responder computer, the back-end LOB application routes a message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="20c0b-107">utilise un adaptateur SQL pour déplacer le message de la table MessagesFromLOB vers le processus privé.</span><span class="sxs-lookup"><span data-stu-id="20c0b-107"> uses a SQL adapter to move the message from the MessagesFromLOB table to the private process.</span></span> <span data-ttu-id="20c0b-108">Pour plus d’informations, consultez « Adaptateur SQL » dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="20c0b-108">For more information, see "SQL Adapter" in BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="20c0b-109">Vous pouvez choisir d’utiliser un adaptateur de fichier pour envoyer du contenu de service à [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], au lieu d’utiliser l’adaptateur SQL par défaut.</span><span class="sxs-lookup"><span data-stu-id="20c0b-109">You can choose to use a File adapter to submit service content to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], instead of using the default SQL adapter.</span></span> <span data-ttu-id="20c0b-110">Si vous choisissez d’utiliser un adaptateur File, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge les pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="20c0b-110">If you choose to use a File adapter, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support attachments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20c0b-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20c0b-111">See Also</span></span>  
 [<span data-ttu-id="20c0b-112">Traitement de messages dans BTARN</span><span class="sxs-lookup"><span data-stu-id="20c0b-112">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)