---
title: "HL7 Désassembleur et assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, HL7
- disassembler, HL7
ms.assetid: 54e83a04-86c8-482f-bea3-dbbdeb4584d6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e81d621656fc678196f7f6fb709b29de87a3aaf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-disassembler-and-assembler"></a><span data-ttu-id="dbbd2-102">HL7 Désassembleur et assembleur</span><span class="sxs-lookup"><span data-stu-id="dbbd2-102">HL7 Disassembler and Assembler</span></span>
<span data-ttu-id="dbbd2-103">Le HL7 désassembleur et assembleur prennent en charge les messages à encodage HL7.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-103">The HL7 disassembler and assembler provide support for HL7-encoded messages.</span></span> <span data-ttu-id="dbbd2-104">Étant donné que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] traite les messages en mode natif au format XML, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise le HL7 désassembleur et assembleur pour faire [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] un moteur d’intégration HL7.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-104">Since [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processes messages natively in XML format, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) uses the HL7 disassembler and assembler to make [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] an HL7 integration engine.</span></span>  
  
## <a name="hl7-disassembler"></a><span data-ttu-id="dbbd2-105">Désassembleur de HL7</span><span class="sxs-lookup"><span data-stu-id="dbbd2-105">HL7 Disassembler</span></span>  
 <span data-ttu-id="dbbd2-106">Le désassembleur de HL7 analyse les messages entrants HL7 encodé en segments XML pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-106">The HL7 disassembler parses incoming HL7-encoded messages into XML segments for processing.</span></span> <span data-ttu-id="dbbd2-107">Il effectue la validation de l’en-tête de message et du corps de la validation de base.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-107">It performs validation of the message header, and basic validation of the body.</span></span> <span data-ttu-id="dbbd2-108">Il détermine le schéma qu’il utilise pour analyser le message HL7 (consultez [détermination du schéma dans le HL7 2.X désassembleur](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)), détermine la partie de la source du message et effectue une validation supplémentaire du corps (s’il est activé pour le tiers).</span><span class="sxs-lookup"><span data-stu-id="dbbd2-108">It determines the schema that it uses to parse the HL7 message (see [Schema Determination in the HL7 2.X Disassembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)), determines the source party for the message, and performs additional validation of the body (if enabled for the party).</span></span>  
  
## <a name="hl7-assembler"></a><span data-ttu-id="dbbd2-109">HL7 assembleur</span><span class="sxs-lookup"><span data-stu-id="dbbd2-109">HL7 Assembler</span></span>  
 <span data-ttu-id="dbbd2-110">L’assembleur HL7 sérialise les segments XML dans un message HL7 sortant.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-110">The HL7 assembler serializes XML segments into an outgoing HL7 message.</span></span> <span data-ttu-id="dbbd2-111">Il détermine le schéma qu’il utilise pour sérialiser le message HL7 (consultez [détermination du schéma dans le HL7 2.X assembleur](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)), détermine le tiers de destination pour le message et effectue la validation du corps (si activé pour le tiers).</span><span class="sxs-lookup"><span data-stu-id="dbbd2-111">It determines the schema that it uses to serialize the HL7 message (see [Schema Determination in the HL7 2.X Assembler](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)), determines the destination party for the message, and performs validation of the body (if enabled for the party).</span></span>  
  
 <span data-ttu-id="dbbd2-112">L’assembleur peut sérialiser les messages d’accusé de réception (ACK) suivants :</span><span class="sxs-lookup"><span data-stu-id="dbbd2-112">The assembler can serialize the following acknowledgment (ACK) messages:</span></span>  
  
-   <span data-ttu-id="dbbd2-113">Statique</span><span class="sxs-lookup"><span data-stu-id="dbbd2-113">Static</span></span>  
  
-   <span data-ttu-id="dbbd2-114">Mode d’origine</span><span class="sxs-lookup"><span data-stu-id="dbbd2-114">Original mode</span></span>  
  
-   <span data-ttu-id="dbbd2-115">Mode étendu</span><span class="sxs-lookup"><span data-stu-id="dbbd2-115">Enhanced mode</span></span>  
  
 <span data-ttu-id="dbbd2-116">L’assembleur HL7 a également la possibilité de router les messages d’accusé de réception différés.</span><span class="sxs-lookup"><span data-stu-id="dbbd2-116">The HL7 assembler also has the ability to route deferred ACK messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbbd2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbbd2-117">See Also</span></span>  
 <span data-ttu-id="dbbd2-118">[Traitement des fichiers plats BTAHL72X](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) </span><span class="sxs-lookup"><span data-stu-id="dbbd2-118">[BTAHL72X Flat File Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md) </span></span>  
 [<span data-ttu-id="dbbd2-119">BizTalk Accelerator pour HL7 composants</span><span class="sxs-lookup"><span data-stu-id="dbbd2-119">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)