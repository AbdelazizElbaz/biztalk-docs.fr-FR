---
title: Validation des messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, messages
- messages, validating
ms.assetid: 720ab16a-7ab4-4741-9951-9ab10a2c4c24
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 940b6aa811cbee845b287c09a66c4b9753313ee0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-validation"></a><span data-ttu-id="918aa-102">Validation de message</span><span class="sxs-lookup"><span data-stu-id="918aa-102">Message Validation</span></span>
<span data-ttu-id="918aa-103">Message de validation se produit pour les messages HL7 entrants et sortants avec HL7 2.X de réception et pipelines d’envoi.</span><span class="sxs-lookup"><span data-stu-id="918aa-103">Message validation occurs for incoming and outgoing HL7 messages with HL7 2.X receive and send pipelines.</span></span> <span data-ttu-id="918aa-104">Vous pouvez configurer la validation pour seulement le segment MSH (en-tête), ou pour l’ensemble du message.</span><span class="sxs-lookup"><span data-stu-id="918aa-104">You can configure validation for only the MSH (header) segment, or for the entire message body.</span></span> <span data-ttu-id="918aa-105">En outre, il est possible pour la validation des versions localisées uniques du schéma.</span><span class="sxs-lookup"><span data-stu-id="918aa-105">In addition, it is possible to validate against unique localized versions of the schema.</span></span> <span data-ttu-id="918aa-106">Pour cela, en définissant une valeur de l’espace de noms unique et à l’aide de cette valeur de l’espace de noms dans la configuration de messagerie HL7 (au niveau du tiers) et la propriété d’espace de noms cible du schéma qui définit le message.</span><span class="sxs-lookup"><span data-stu-id="918aa-106">You accomplish this by defining a unique namespace value, and using this namespace value within both the HL7 messaging configuration (at the party level) and the target namespace property of the actual schema that defines the message.</span></span> <span data-ttu-id="918aa-107">Au moment de l’exécution [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise la combinaison de l’espace de noms et la propriété de référence de racine du schéma pour sélectionner le schéma approprié pour l’analyse et la validation.</span><span class="sxs-lookup"><span data-stu-id="918aa-107">At run time, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the combination of namespace and the root reference property for the schema to select the appropriate schema for message parsing and validation.</span></span>  
  
 <span data-ttu-id="918aa-108">L’analyseur et le sérialiseur exécutent une validation basée sur les paramètres pour le tiers associé à un message.</span><span class="sxs-lookup"><span data-stu-id="918aa-108">The parser and serializer perform validation based on the settings for the party associated with a message.</span></span> <span data-ttu-id="918aa-109">Autres paramètres du tiers, y compris le remplacement de traitement par lot, d’accusé de réception et en-tête de message affectent comment l’analyseur ou au sérialiseur effectue la validation.</span><span class="sxs-lookup"><span data-stu-id="918aa-109">Other party settings, including batching, acknowledgment, and message-header override affect how the parser or serializer performs validation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="918aa-110">Le sérialiseur effectue une série d’étapes, y compris (le cas échéant) effectuer des substitutions d’en-tête à partir d’une carte MSH et effectuer la validation XML.</span><span class="sxs-lookup"><span data-stu-id="918aa-110">The serializer performs a series of steps, including (if applicable) performing header overrides from an MSH map, and performing XML validation.</span></span> <span data-ttu-id="918aa-111">Si les processus de remplacement et la validation en-tête sont toutes deux activées, et le processus de remplacement d’en-tête entre une valeur incorrecte dans un champ d’en-tête, le message de validation échoue, même si le message a été pour passer la validation du corps.</span><span class="sxs-lookup"><span data-stu-id="918aa-111">If the header override and validation processes are both enabled, and the header override process enters an incorrect value into a header field, the message will fail validation, even if the message were to pass body validation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="918aa-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="918aa-112">See Also</span></span>  
 [<span data-ttu-id="918aa-113">Remplacement de MSH</span><span class="sxs-lookup"><span data-stu-id="918aa-113">MSH Override</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-override.md)