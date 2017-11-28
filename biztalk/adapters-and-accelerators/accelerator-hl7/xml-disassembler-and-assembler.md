---
title: "Désassembleur XML et assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, XML
- assembler, XML
ms.assetid: 242a7a96-2342-4ab5-9d3f-1acbcc7ffd14
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4978484f888290377986ee4ae8bf049c14a1b31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-disassembler-and-assembler"></a><span data-ttu-id="caba4-102">Assembleur et désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="caba4-102">XML Disassembler and Assembler</span></span>
<span data-ttu-id="caba4-103">Le désassembleur XML et l’assembleur de s’assurer que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge non seulement les messages encodés HL7, mais prend également en charge les messages XML entrants et/ou sortants.</span><span class="sxs-lookup"><span data-stu-id="caba4-103">The XML disassembler and assembler ensure that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) not only supports HL7-encoded messages, but also supports incoming and/or outgoing XML messages.</span></span>  
  
## <a name="xml-disassembler"></a><span data-ttu-id="caba4-104">Désassembleur XML</span><span class="sxs-lookup"><span data-stu-id="caba4-104">XML Disassembler</span></span>  
 <span data-ttu-id="caba4-105">Le désassembleur XML traite les messages XML entrants en segments XML pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="caba4-105">The XML disassembler parses incoming XML messages into XML segments for processing.</span></span> <span data-ttu-id="caba4-106">Comme il traite les messages, le désassembleur effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="caba4-106">As it parses the messages, the disassembler performs the following tasks:</span></span>  
  
-   <span data-ttu-id="caba4-107">Gère les séquences d’échappement</span><span class="sxs-lookup"><span data-stu-id="caba4-107">Handles escape sequences</span></span>  
  
-   <span data-ttu-id="caba4-108">Gère les vérifications des propriétés obligatoire ou facultatif</span><span class="sxs-lookup"><span data-stu-id="caba4-108">Handles checks of required/optional properties</span></span>  
  
-   <span data-ttu-id="caba4-109">Handles déclarés de segments de Z</span><span class="sxs-lookup"><span data-stu-id="caba4-109">Handles declared Z segments</span></span>  
  
 <span data-ttu-id="caba4-110">Comme il traite les messages, le désassembleur effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="caba4-110">As it parses the messages, the dissassembler performs the following:</span></span>  
  
-   <span data-ttu-id="caba4-111">Validation syntaxique</span><span class="sxs-lookup"><span data-stu-id="caba4-111">Syntactic validation</span></span>  
  
-   <span data-ttu-id="caba4-112">Validation de schéma (si activé)</span><span class="sxs-lookup"><span data-stu-id="caba4-112">Schema validation (if enabled)</span></span>  
  
## <a name="xml-assembler"></a><span data-ttu-id="caba4-113">Assembleur XML</span><span class="sxs-lookup"><span data-stu-id="caba4-113">XML Assembler</span></span>  
 <span data-ttu-id="caba4-114">L’assembleur XML sérialise les segments XML dans un message XML sortant.</span><span class="sxs-lookup"><span data-stu-id="caba4-114">The XML assembler serializes XML segments into an outgoing XML message.</span></span> <span data-ttu-id="caba4-115">L’assembleur XML prend en charge et crée des messages (ACK) de l’accusé de réception suivant :</span><span class="sxs-lookup"><span data-stu-id="caba4-115">The XML assembler supports and creates the following acknowledgment (ACK) messages:</span></span>  
  
-   <span data-ttu-id="caba4-116">Statique</span><span class="sxs-lookup"><span data-stu-id="caba4-116">Static</span></span>  
  
-   <span data-ttu-id="caba4-117">Mode d’origine</span><span class="sxs-lookup"><span data-stu-id="caba4-117">Original mode</span></span>  
  
-   <span data-ttu-id="caba4-118">Mode étendu</span><span class="sxs-lookup"><span data-stu-id="caba4-118">Enhanced mode</span></span>  
  
 <span data-ttu-id="caba4-119">L’assembleur XML a également la possibilité de router les messages d’accusé de réception différés.</span><span class="sxs-lookup"><span data-stu-id="caba4-119">The XML assembler also has the ability to route deferred ACK messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caba4-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="caba4-120">See Also</span></span>  
 <span data-ttu-id="caba4-121">[Traitement de BTAHL72XML](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md) </span><span class="sxs-lookup"><span data-stu-id="caba4-121">[BTAHL72XML Processing](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md) </span></span>  
 [<span data-ttu-id="caba4-122">BizTalk Accelerator pour HL7 composants</span><span class="sxs-lookup"><span data-stu-id="caba4-122">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)