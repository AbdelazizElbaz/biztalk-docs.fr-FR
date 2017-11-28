---
title: "Conditions d’erreur d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, errors
- errors, acknowledgements
ms.assetid: 605c7fa0-2365-4cb6-92fb-6df570905ca8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15b481f4cdb60822841021f7f708a6caea021b8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgment-error-conditions"></a><span data-ttu-id="f7743-102">Conditions d’erreur d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="f7743-102">Acknowledgment Error Conditions</span></span>
<span data-ttu-id="f7743-103">Les conditions suivantes provoque une erreur irrécupérable quand la condition [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) est accusé de réception de traitement des messages (ACK) :</span><span class="sxs-lookup"><span data-stu-id="f7743-103">The following conditions will result in a fatal error condition when [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) is processing acknowledgment (ACK) messages:</span></span>  
  
-   <span data-ttu-id="f7743-104">Les champs requis dans MSH9 manquants</span><span class="sxs-lookup"><span data-stu-id="f7743-104">Missing required fields in MSH9</span></span>  
  
-   <span data-ttu-id="f7743-105">Les champs requis dans MSH12 manquants</span><span class="sxs-lookup"><span data-stu-id="f7743-105">Missing required fields in MSH12</span></span>  
  
 <span data-ttu-id="f7743-106">Les conditions suivantes génèrent dans une condition d’erreur non fatale.</span><span class="sxs-lookup"><span data-stu-id="f7743-106">The following conditions result in a non-fatal error condition.</span></span> <span data-ttu-id="f7743-107">Dans ce cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère l’accusé de réception, mais également suspend l’accusé de réception :</span><span class="sxs-lookup"><span data-stu-id="f7743-107">In this situation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates the ACK, but also suspends the ACK:</span></span>  
  
-   <span data-ttu-id="f7743-108">Un champ obligatoire dans MSH11 manquant</span><span class="sxs-lookup"><span data-stu-id="f7743-108">Missing a required field in MSH11</span></span>  
  
-   <span data-ttu-id="f7743-109">Valeur MSH10 manquante</span><span class="sxs-lookup"><span data-stu-id="f7743-109">Missing a MSH10 value</span></span>  
  
-   <span data-ttu-id="f7743-110">Erreurs de type énumération pour les champs facultatifs dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="f7743-110">Enumeration type errors for optional fields in the header.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7743-111">Pour les erreurs de type énumération trouvés dans l’en-tête lorsque MSH 15 est définie sur AL ou ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère une validation de l’accusé de réception avec l’état **MSA_1 = CR**.</span><span class="sxs-lookup"><span data-stu-id="f7743-111">For enumeration type errors found in the header when MSH 15 is set to AL or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] generates a commit ACK with the status **MSA_1=CR**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7743-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7743-112">See Also</span></span>  
 <span data-ttu-id="f7743-113">[Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="f7743-113">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="f7743-114">[Types de schémas de Message de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="f7743-114">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="f7743-115">[Segment de message d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="f7743-115">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 [<span data-ttu-id="f7743-116">Configuration d’un Port d’envoi pour recevoir des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="f7743-116">Setting Up a Send Port for Receiving ACKs</span></span>](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)