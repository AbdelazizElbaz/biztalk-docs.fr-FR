---
title: Traitement de BTAHL72XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.XML messages, processing
- acknowledgements, 2.XML messages
- 2.XML messages, message modes
- message modes, 2.XML message
- 2.XML messages
- validating, 2.XML messages
- 2.XML messages, acknowledgements
- 2.XML messages, validating
ms.assetid: 2f12cb44-816c-4773-9db0-9cbc3d1b1aee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e86697884c28d71fa9fb91c8b276293f7d36a588
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btahl72xml-processing"></a><span data-ttu-id="43c88-102">Traitement de BTAHL72XML</span><span class="sxs-lookup"><span data-stu-id="43c88-102">BTAHL72XML Processing</span></span>
<span data-ttu-id="43c88-103">Les composants suivants dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) traiter les messages HL7 2 XML (codé en XML) :</span><span class="sxs-lookup"><span data-stu-id="43c88-103">The following components in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) process HL7 2.XML (XML-encoded) messages:</span></span>  
  
-   <span data-ttu-id="43c88-104">Pipelines et les bibliothèques principales : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineCommon.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineMessageCore.dll</span><span class="sxs-lookup"><span data-stu-id="43c88-104">Pipelines and core libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineCommon.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].PipelineMessageCore.dll</span></span>  
  
-   <span data-ttu-id="43c88-105">Bibliothèques d’assembleur et désassembleur : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72XmlAsm.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72XmlDAsm.dll</span><span class="sxs-lookup"><span data-stu-id="43c88-105">Assembler and disassembler libraries: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72XmlAsm.dll and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL72XmlDAsm.dll</span></span>  
  
-   <span data-ttu-id="43c88-106">Adaptateur d’envoi de la bibliothèque de validation d’accusé de réception (ACK) utilisée pour le MLLP bidirectionnelle : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL7ACKHelper.dll</span><span class="sxs-lookup"><span data-stu-id="43c88-106">The acknowledgment (ACK) validation library used for the two-way MLLP send adapter: [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].HL7ACKHelper.dll</span></span>  
  
## <a name="xml-message-modes"></a><span data-ttu-id="43c88-107">Modes de Message XML</span><span class="sxs-lookup"><span data-stu-id="43c88-107">XML Message Modes</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="43c88-108">prend en charge les modes de message suivants pour les messages XML de 2 :</span><span class="sxs-lookup"><span data-stu-id="43c88-108"> supports the following message modes for 2.XML messages:</span></span>  
  
-   <span data-ttu-id="43c88-109">Mode éditeur-abonné (pub-sub)</span><span class="sxs-lookup"><span data-stu-id="43c88-109">Publisher-subscriber (pub-sub) mode</span></span>  
  
     <span data-ttu-id="43c88-110">Le serveur de publication diffuse à un tiers d’abonnés, comme déclaratives ou une non sollicité mise à jour.</span><span class="sxs-lookup"><span data-stu-id="43c88-110">The publisher broadcasts to a party of subscribers, either as declarative or an unsolicited update.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="43c88-111">et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournissent une grande souplesse pour ce mode, étant donné que vous pouvez gérer les abonnements et les parties après le moment du design.</span><span class="sxs-lookup"><span data-stu-id="43c88-111"> and [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] provide flexibility to this mode, since you can manage subscriptions and parties after design time.</span></span>  
  
-   <span data-ttu-id="43c88-112">Mode de requête-réponse</span><span class="sxs-lookup"><span data-stu-id="43c88-112">Request-response mode</span></span>  
  
     <span data-ttu-id="43c88-113">Un échange de messages interrogative ou d’une requête dans lequel une demande spécifique à partir d’une entité spécifique génère un message de répond.</span><span class="sxs-lookup"><span data-stu-id="43c88-113">An interrogative or query message exchange in which a specific request from a specific entity results in a responding message.</span></span>  
  
## <a name="xml-validation"></a><span data-ttu-id="43c88-114">Validation XML</span><span class="sxs-lookup"><span data-stu-id="43c88-114">XML Validation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="43c88-115">Fournit la validation suivante de 2. des messages XML :</span><span class="sxs-lookup"><span data-stu-id="43c88-115"> provides the following validation of 2.XML messages:</span></span>  
  
-   <span data-ttu-id="43c88-116">Lecteur XML</span><span class="sxs-lookup"><span data-stu-id="43c88-116">XML reader</span></span>  
  
-   <span data-ttu-id="43c88-117">Schéma</span><span class="sxs-lookup"><span data-stu-id="43c88-117">Schematic</span></span>  
  
     <span data-ttu-id="43c88-118">Pour activer ou désactiver la validation de schéma par le tiers.</span><span class="sxs-lookup"><span data-stu-id="43c88-118">You enable or disable schematic validation by the party.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="43c88-119">utilise les schémas XML de 2 HL7 directement lors du traitement, de déterminée par le champ d’en-tête MSH9.3 structure de message et le champ d’ID de Version MSH12 (2.3.1, 2.4 ou 2.5).</span><span class="sxs-lookup"><span data-stu-id="43c88-119"> uses the HL7 2.XML schemas directly for this processing, as determined by the MSH9.3 message-structure header field and the MSH12 Version ID field (2.3.1, 2.4, or 2.5).</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="43c88-120">utilise les fonctions de traitement XML standards dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="43c88-120"> uses the standard XML processing capabilities in [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="43c88-121">Segment de Z</span><span class="sxs-lookup"><span data-stu-id="43c88-121">Z segment</span></span>  
  
     [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="43c88-122">valide qu’aucun segment déclarée n’est inclus dans un segment Z non déclaré.</span><span class="sxs-lookup"><span data-stu-id="43c88-122"> validates that no declared segments are included in an undeclared Z segment.</span></span>  
  
## <a name="ack-generation"></a><span data-ttu-id="43c88-123">Génération de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="43c88-123">ACK Generation</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="43c88-124">prend en charge les types d’accusés de réception (ACK) suivants pour les messages XML de 2.</span><span class="sxs-lookup"><span data-stu-id="43c88-124"> supports the following types of acknowledgments (ACKs) for 2.XML messages.</span></span> <span data-ttu-id="43c88-125">Les deux le type d’erreur HL7 et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] type d’erreur (secondaire) sont utilisées :</span><span class="sxs-lookup"><span data-stu-id="43c88-125">Both the HL7 error type and the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] (alternate) error type are used:</span></span>  
  
-   <span data-ttu-id="43c88-126">Accusés de réception d’origine HL7</span><span class="sxs-lookup"><span data-stu-id="43c88-126">HL7 original ACKs</span></span>  
  
-   <span data-ttu-id="43c88-127">HL7 améliorée des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="43c88-127">HL7 enhanced ACKs</span></span>  
  
     <span data-ttu-id="43c88-128">Validation acceptent et Application</span><span class="sxs-lookup"><span data-stu-id="43c88-128">Commit Accept and Application Accept</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43c88-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43c88-129">See Also</span></span>  
 <span data-ttu-id="43c88-130">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="43c88-130">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="43c88-131">Utilisation de schémas XML de 2 HL7</span><span class="sxs-lookup"><span data-stu-id="43c88-131">Using HL7 2.XML Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)