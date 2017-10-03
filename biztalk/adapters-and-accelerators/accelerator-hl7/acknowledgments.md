---
title: "Accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, acknowledgements
- parties, acknowledgements
- acknowledgements, about acknowledgements
- acknowledgements, messages
- acknowledgements, parties
ms.assetid: d25352a4-bae9-4de9-a504-2339bea25c4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c519ec4649ee1fbcfbc51edb7e3e8fe6ba6b5871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgments"></a><span data-ttu-id="9104b-102">Accusés de réception</span><span class="sxs-lookup"><span data-stu-id="9104b-102">Acknowledgments</span></span>
<span data-ttu-id="9104b-103">Configurer des accusés de réception HL7 sur le niveau de tiers à l’aide [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="9104b-103">You configure HL7 acknowledgments at the party level using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Configuration Explorer.</span></span> <span data-ttu-id="9104b-104">Accusés de réception s’appliquent aux parties qui envoient des messages via un emplacement de réception (et éventuellement l’adaptateur MLLP) et le HL7 HL7 pipeline de réception 2.X.</span><span class="sxs-lookup"><span data-stu-id="9104b-104">Acknowledgments apply to parties that are sending HL7 messages through a receive location (possibly the MLLP adapter) and the HL7 2.X receive pipeline.</span></span> <span data-ttu-id="9104b-105">Quand un message termine, l’analyse et la validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peut créer un message d’accusé de réception qui contient le résultat (succès ou erreur) du processus de validation.</span><span class="sxs-lookup"><span data-stu-id="9104b-105">When a message completes parsing and validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] can create an acknowledgment message that contains the result (success or error) of the validation process.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="9104b-106">peut retourner des messages d’accusé de réception de l’une des deux façons.</span><span class="sxs-lookup"><span data-stu-id="9104b-106"> can return acknowledgment messages in one of two ways.</span></span> <span data-ttu-id="9104b-107">Si le tiers expéditeur d’origine envoyé le message d’origine via bidirectionnel recevoir la configuration du port, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] renvoie le message d’accusé de réception via cet emplacement de port d’origine.</span><span class="sxs-lookup"><span data-stu-id="9104b-107">If the original sending party submitted the original message through a two-way receive port configuration, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] returns the acknowledgment message through that original port location.</span></span> <span data-ttu-id="9104b-108">Si le port d’envoi d’origine envoyé le message d’origine via unidirectionnel port de réception, puis [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie le message d’accusé de réception dans la base de données MessageBox et l’achemine à l’aide du modèle d’abonnement.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9104b-108">If the original sending port submitted the original message through a one-way receive port, then [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] submits the acknowledgment message into the MessageBox database and routes it using the subscription model.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]</span></span> <span data-ttu-id="9104b-109">effectue l’association de partie pour le traitement du message de réception automatiquement en fonction de la valeur dans le champ d’application émettrice du message HL7 (MSH 3.1).</span><span class="sxs-lookup"><span data-stu-id="9104b-109">performs party association for receive message processing automatically based on the value within the sending application field of the HL7 message (MSH 3.1).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9104b-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9104b-110">See Also</span></span>  
 [<span data-ttu-id="9104b-111">Flux de messages</span><span class="sxs-lookup"><span data-stu-id="9104b-111">Message Flow</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-flow.md)