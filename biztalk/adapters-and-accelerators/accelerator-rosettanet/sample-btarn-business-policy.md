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
ms.openlocfilehash: bfe0bd746894106fc7ac9ebeaae600fe7344ba18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sample-btarn-business-policy"></a><span data-ttu-id="579da-102">Exemple de stratégie d'entreprise BTARN</span><span class="sxs-lookup"><span data-stu-id="579da-102">Sample BTARN Business Policy</span></span>
<span data-ttu-id="579da-103">Cet exemple est le code XML associé à un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stratégie de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="579da-103">This sample is the XML code associated with a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] business-rules policy.</span></span>  
  
 <span data-ttu-id="579da-104">L’exemple de fichier est samplebtarnpolicy.xml dans \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\PIPAutomation\3A4.</span><span class="sxs-lookup"><span data-stu-id="579da-104">The sample file is samplebtarnpolicy.xml in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\PIPAutomation\3A4.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="579da-105">Montre</span><span class="sxs-lookup"><span data-stu-id="579da-105">Demonstrates</span></span>  
 <span data-ttu-id="579da-106">Ce code illustre une stratégie de règles d'entreprise avec la règle suivante :</span><span class="sxs-lookup"><span data-stu-id="579da-106">This code shows a business-rule policy with the following rule:</span></span>  
  
 <span data-ttu-id="579da-107">IF (AccountNumber dans le message de bon de commande entrant 3A4 = « 111111111 ») et (MonetaryAmount de la commande < 500) THEN envoyer automatiquement un message de réponse</span><span class="sxs-lookup"><span data-stu-id="579da-107">IF (AccountNumber in the incoming 3A4 Purchase Order message = "111111111") and (MonetaryAmount of the Order < 500) THEN automatically send a response message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="579da-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="579da-108">See Also</span></span>  
 [<span data-ttu-id="579da-109">Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise</span><span class="sxs-lookup"><span data-stu-id="579da-109">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)