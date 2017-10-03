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
ms.openlocfilehash: 9cf1aba9f2d4d2ea77f369e76c277160739f7f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sql-processing-in-btarn"></a><span data-ttu-id="ee4f3-102">Traitement SQL dans BTARN</span><span class="sxs-lookup"><span data-stu-id="ee4f3-102">SQL Processing in BTARN</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="ee4f3-103">[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise un adaptateur SQL pour router un message à partir de l’application de métier (LOB).</span><span class="sxs-lookup"><span data-stu-id="ee4f3-103"> [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses a SQL adapter to route a message from the line-of-business (LOB) application.</span></span> <span data-ttu-id="ee4f3-104">Il utilise un port d'envoi SQL pour acheminer un message vers l'application métier.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-104">It uses a SQL send port to route a message to the LOB application.</span></span>  
  
## <a name="message-flow"></a><span data-ttu-id="ee4f3-105">Flux de messages</span><span class="sxs-lookup"><span data-stu-id="ee4f3-105">Message Flow</span></span>  
 <span data-ttu-id="ee4f3-106">Sur soit l’initiateur ou répondeur, l’application métier principale achemine un message à la table MessagesFromLOB de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]données [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-106">On either the initiator or responder computer, the back-end LOB application routes a message to the MessagesFromLOB table of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]DATA [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="ee4f3-107">utilise un adaptateur SQL pour déplacer le message de la table MessagesFromLOB vers le processus privé.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-107"> uses a SQL adapter to move the message from the MessagesFromLOB table to the private process.</span></span> <span data-ttu-id="ee4f3-108">Pour plus d’informations, consultez « Adaptateur SQL » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-108">For more information, see "SQL Adapter" in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="ee4f3-109">Vous pouvez choisir d’utiliser un adaptateur de fichier pour envoyer du contenu de service à [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], au lieu d’utiliser l’adaptateur SQL par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-109">You can choose to use a File adapter to submit service content to [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], instead of using the default SQL adapter.</span></span> <span data-ttu-id="ee4f3-110">Si vous choisissez d’utiliser un adaptateur File, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge les pièces jointes.</span><span class="sxs-lookup"><span data-stu-id="ee4f3-110">If you choose to use a File adapter, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support attachments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4f3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee4f3-111">See Also</span></span>  
 [<span data-ttu-id="ee4f3-112">Traitement des messages dans BTARN</span><span class="sxs-lookup"><span data-stu-id="ee4f3-112">Message Processing in BTARN</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)