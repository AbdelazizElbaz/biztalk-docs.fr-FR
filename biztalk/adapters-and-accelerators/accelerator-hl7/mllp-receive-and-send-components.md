---
title: MLLP recevoir et envoyer des composants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send components
- Minimal Lower Layer Protocol (MLLP)
- MLLP adapters
- MLLP adapters, wrappers
- wrappers [MLLP adapters]
- receive components
ms.assetid: 2f1c4099-8f52-437a-bdc1-efe707fbf347
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e135b98c04531aa6200f3b79c5b6d5153bf299a7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mllp-receive-and-send-components"></a><span data-ttu-id="704fb-102">MLLP recevoir et envoyer des composants</span><span class="sxs-lookup"><span data-stu-id="704fb-102">MLLP Receive and Send Components</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="704fb-103">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge tous les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] types d’adaptateur natif, y compris le fichier, HTTP, SQL et FTP.</span><span class="sxs-lookup"><span data-stu-id="704fb-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) supports all [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] native adapter types, including File, HTTP, SQL, and FTP.</span></span> <span data-ttu-id="704fb-104">Pour HL7-message réception et l’envoi, toutefois, vous utilisez généralement l’adaptateur MLLP.</span><span class="sxs-lookup"><span data-stu-id="704fb-104">For HL7-encoded message receiving and sending, however, you typically use the MLLP adapter.</span></span> <span data-ttu-id="704fb-105">Cet adaptateur est un adaptateur de socket TCP/IP qui utilise le protocole minimale de couche inférieure (MLLP).</span><span class="sxs-lookup"><span data-stu-id="704fb-105">This adapter is a TCP/IP socket adapter that uses the Minimal Lower Layer Protocol (MLLP).</span></span> <span data-ttu-id="704fb-106">Ce protocole permet à des messages bidirectionnels prise en charge et bout en bout de soins de santé intégration d’application.</span><span class="sxs-lookup"><span data-stu-id="704fb-106">This protocol provides bi-directional message support and end-to-end health care application integration.</span></span>  
  
 <span data-ttu-id="704fb-107">Vous pouvez configurer le MLLP comme une carte bidirectionnelle ou une carte à sens unique : adaptateur de réception.</span><span class="sxs-lookup"><span data-stu-id="704fb-107">You can configure the MLLP receive adapter as either a two-way adapter or a one-way adapter.</span></span> <span data-ttu-id="704fb-108">Vous pouvez configurer l’adaptateur d’envoi MLLP que l’adaptateur d’envoi une bidirectionnelle avec sollicitation-réponse, unidirectionnel l’adaptateur d’envoi configuré pour recevoir des accusés de réception (ACK) sur la même connexion de socket ou adaptateur qui ne retourne pas les messages d’envoi unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="704fb-108">You can configure the MLLP send adapter as a two-way solicit-response send adapter, a one-way send adapter configured to receive acknowledgments (ACKs) on the same socket connection, or a one-way send adapter that does not return any messages.</span></span> <span data-ttu-id="704fb-109">Lorsque vous utilisez bidirectionnel adaptateur MLLP d’envoi de sollicitation-réponse, vous pouvez configurer le port de réception pour renvoyer des accusés de réception ou de messages de réponse.</span><span class="sxs-lookup"><span data-stu-id="704fb-109">When you use the two-way solicit-response send MLLP adapter, you can configure the receive port to return either ACKs or response messages.</span></span> <span data-ttu-id="704fb-110">Pour obtenir des exemples de MLLP envoyer et recevoir des adaptateurs, consultez [Interrogative didacticiel](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="704fb-110">For examples of MLLP send and receive adapters, see [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).</span></span>  
  
 <span data-ttu-id="704fb-111">Les messages [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit ou envoie sur un adaptateur MLLP requièrent les wrappers suivantes :</span><span class="sxs-lookup"><span data-stu-id="704fb-111">Messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives or sends on an MLLP adapter require the following wrappers:</span></span>  
  
-   <span data-ttu-id="704fb-112">\<Service bus\> caractère de début de bloc</span><span class="sxs-lookup"><span data-stu-id="704fb-112">\<SB\> Start Block character</span></span>  
  
-   <span data-ttu-id="704fb-113">\<EB\> caractère du bloc de fin</span><span class="sxs-lookup"><span data-stu-id="704fb-113">\<EB\> End Block character</span></span>  
  
-   <span data-ttu-id="704fb-114">\<CR\> chariot retourner octets (facultatif)</span><span class="sxs-lookup"><span data-stu-id="704fb-114">\<CR\> Carriage Return Byte (optional)</span></span>  
  
 <span data-ttu-id="704fb-115">Les adaptateurs MLLP fournissent manquantes de gestion des erreurs \<SB\> ou \<EB\> wrappers, les pertes de connexion ou les délais.</span><span class="sxs-lookup"><span data-stu-id="704fb-115">MLLP adapters provide error handling for missing \<SB\> or \<EB\> wrappers, dropped connections, or timeouts.</span></span> <span data-ttu-id="704fb-116">Avec un adaptateur MLLP, vous pouvez configurer une limitation du nombre de connexions.</span><span class="sxs-lookup"><span data-stu-id="704fb-116">With an MLLP adapter, you can configure a limitation on the number of connections.</span></span> <span data-ttu-id="704fb-117">Vous pouvez utiliser un vaste choix d’accusés de réception avec un adaptateur MLLP.</span><span class="sxs-lookup"><span data-stu-id="704fb-117">You can use an assortment of acknowledgments with an MLLP adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704fb-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="704fb-118">See Also</span></span>  
 <span data-ttu-id="704fb-119">[Le traitement des Messages encodés en MLLP](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span><span class="sxs-lookup"><span data-stu-id="704fb-119">[Processing MLLP-encoded Messages](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md) </span></span>  
 [<span data-ttu-id="704fb-120">Composants de BizTalk Accelerator pour HL7</span><span class="sxs-lookup"><span data-stu-id="704fb-120">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)