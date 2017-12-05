---
title: "Exemple de stratégie d’entreprise BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db932c17-8e8f-4f7a-b165-d1d7d749cdb6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c85cbb7894f0d8bd1b61b7e7856865b49fd33859
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sample-btarn-business-policy"></a><span data-ttu-id="f6363-102">Exemple de stratégie d'entreprise BTARN</span><span class="sxs-lookup"><span data-stu-id="f6363-102">Sample BTARN Business Policy</span></span>
<span data-ttu-id="f6363-103">Cet exemple est le code XML associé à un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stratégie de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f6363-103">This sample is the XML code associated with a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] business-rules policy.</span></span>  
  
 <span data-ttu-id="f6363-104">L’exemple de fichier est samplebtarnpolicy.xml dans \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\ PIPAutomation\3A4.</span><span class="sxs-lookup"><span data-stu-id="f6363-104">The sample file is samplebtarnpolicy.xml in \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PIPAutomation\3A4.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f6363-105">Montre</span><span class="sxs-lookup"><span data-stu-id="f6363-105">Demonstrates</span></span>  
 <span data-ttu-id="f6363-106">Ce code illustre une stratégie de règles d'entreprise avec la règle suivante :</span><span class="sxs-lookup"><span data-stu-id="f6363-106">This code shows a business-rule policy with the following rule:</span></span>  
  
 <span data-ttu-id="f6363-107">IF (AccountNumber dans le message de bon de commande entrant 3A4 = « 111111111 ») et (MonetaryAmount de la commande < 500) THEN envoyer automatiquement un message de réponse</span><span class="sxs-lookup"><span data-stu-id="f6363-107">IF (AccountNumber in the incoming 3A4 Purchase Order message = "111111111") and (MonetaryAmount of the Order < 500) THEN automatically send a response message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6363-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6363-108">See Also</span></span>  
 [<span data-ttu-id="f6363-109">Orchestration de répondeur privé 3A4 avec une règle d’entreprise</span><span class="sxs-lookup"><span data-stu-id="f6363-109">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)