---
title: Modes de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message modes, about message modes
- messages, message modes
- message modes, HL7 messages
ms.assetid: 2d832b67-6f0e-45e1-95ac-cb80b74a7831
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b09a610d000ae6beaef75b1ed0144d1597d517b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-modes"></a><span data-ttu-id="7d727-102">Modes de messages</span><span class="sxs-lookup"><span data-stu-id="7d727-102">Message Modes</span></span>
<span data-ttu-id="7d727-103">Il existe deux concepts de base qui sous-tendent tous les messages HL7.</span><span class="sxs-lookup"><span data-stu-id="7d727-103">There are two basic concepts that underlie all HL7 messages.</span></span> <span data-ttu-id="7d727-104">Ces concepts d’adresses différentes façons dans lequel des systèmes indépendants qui échangent des données peuvent interagir et fournissent une structure qui prend en charge les exigences d’interopérabilité dans le temps au sein d’un système de soins de santé distribué.</span><span class="sxs-lookup"><span data-stu-id="7d727-104">These concepts address different ways in which independent systems that exchange data can interact, and provide a structure that supports the requirements of interoperability over time within a distributed health care system.</span></span> <span data-ttu-id="7d727-105">Les concepts ci-dessous définissent les thèmes sous-jacent derrière la conception HL7 :</span><span class="sxs-lookup"><span data-stu-id="7d727-105">The concepts listed below define the underlying themes behind the HL7 design:</span></span>  
  
-   <span data-ttu-id="7d727-106">**Mode de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="7d727-106">**Messaging Mode**.</span></span> <span data-ttu-id="7d727-107">La reconnaissance des trois objectifs fondamentaux pour l’échange d’informations : diffusion des informations (déclaratives), pour demander des informations (interrogative) et vous demande que le système entreprendre une action (impératif).</span><span class="sxs-lookup"><span data-stu-id="7d727-107">The recognition of three fundamental purposes for information exchange: to broadcast information (declarative), to request information (interrogative), and to request that the system take an action (imperative).</span></span> <span data-ttu-id="7d727-108">Chacun de ces objectifs a ses besoins et le modèle de flux de messages.</span><span class="sxs-lookup"><span data-stu-id="7d727-108">Each of these purposes has its particular requirements and pattern of message flow.</span></span>  
  
-   <span data-ttu-id="7d727-109">**Mode d’accusé de réception**.</span><span class="sxs-lookup"><span data-stu-id="7d727-109">**Acknowledgment Mode**.</span></span> <span data-ttu-id="7d727-110">La nécessité de prendre en charge étroitement et faiblement couplées styles de messagerie.</span><span class="sxs-lookup"><span data-stu-id="7d727-110">The need to support tightly and loosely coupled styles of messaging.</span></span> <span data-ttu-id="7d727-111">Les modes d’accusé de réception pour HL7 permettent à une application émettrice pour demander une réponse du récepteur, ou pour activer le réseau sous-jacent garantir la remise des messages.</span><span class="sxs-lookup"><span data-stu-id="7d727-111">The acknowledgment modes for HL7 enable a sending application either to require a response from the receiver, or to enable the underlying network to guarantee message delivery.</span></span>  
  
-   <span data-ttu-id="7d727-112">**Localisation**.</span><span class="sxs-lookup"><span data-stu-id="7d727-112">**Localization**.</span></span> <span data-ttu-id="7d727-113">La nécessité de prendre en charge des exigences spécifiques en permettant aux entités introduire des documents spécifiques au site dans les spécifications de message.</span><span class="sxs-lookup"><span data-stu-id="7d727-113">The need to support specific local requirements by allowing entities to introduce site-specific material into message specifications.</span></span>  
  
-   <span data-ttu-id="7d727-114">**Évolution**.</span><span class="sxs-lookup"><span data-stu-id="7d727-114">**Evolution**.</span></span> <span data-ttu-id="7d727-115">La nécessité de prendre en charge des sites avec nombreuses interfaces et de nombreuses applications en activant l’interopérabilité entre les versions standards.</span><span class="sxs-lookup"><span data-stu-id="7d727-115">The need to support sites with many interfaces and many applications by enabling interoperability between standard versions.</span></span> <span data-ttu-id="7d727-116">Ainsi, les entités à l’étape interface les mises à niveau, sans nécessiter des mises à niveau simultanées de toutes les interfaces.</span><span class="sxs-lookup"><span data-stu-id="7d727-116">This enables entities to stage interface upgrades, as opposed to requiring simultaneous upgrades of all interfaces.</span></span>  
  
 <span data-ttu-id="7d727-117">Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge les spécifications ci-dessus :</span><span class="sxs-lookup"><span data-stu-id="7d727-117">The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support the above requirements:</span></span>  
  
-   <span data-ttu-id="7d727-118">Modes d’accusé de réception HL7.</span><span class="sxs-lookup"><span data-stu-id="7d727-118">HL7 acknowledgment modes.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="7d727-119">prend en charge le mode d’accusé de réception d’origine en passant des accusés de réception application à l’expéditeur du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="7d727-119"> supports the original acknowledgment mode by passing application acknowledgments back to the original message sender.</span></span>  
  
-   <span data-ttu-id="7d727-120">Différents modes de messagerie.</span><span class="sxs-lookup"><span data-stu-id="7d727-120">Different messaging modes.</span></span> <span data-ttu-id="7d727-121">Cela permet la diffusion vers plusieurs destinations et relie les requêtes à la réponse de la requête associée.</span><span class="sxs-lookup"><span data-stu-id="7d727-121">This enables broadcast to multiple destinations, and ties together queries to the associated query response.</span></span>  
  
-   <span data-ttu-id="7d727-122">Prise en charge de plusieurs versions, y compris XML et encodages de délimitée par des canaux.</span><span class="sxs-lookup"><span data-stu-id="7d727-122">Support for multiple versions, including XML and pipe-delimited encodings.</span></span>  
  
-   <span data-ttu-id="7d727-123">Le mappage entre les mises à niveau et les versions HL7 activer divers environnements.</span><span class="sxs-lookup"><span data-stu-id="7d727-123">Mapping between HL7 versions to enable diverse environments and upgrades.</span></span>  
  
-   <span data-ttu-id="7d727-124">Localisation (personnalisation) au sein de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="7d727-124">Localization (customization) within orchestration.</span></span>  
  
-   <span data-ttu-id="7d727-125">Outils pour prendre en charge le débogage et l’évaluation des nouvelles interfaces.</span><span class="sxs-lookup"><span data-stu-id="7d727-125">Tools to support debugging and evaluation of new interfaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d727-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d727-126">See Also</span></span>  
 <span data-ttu-id="7d727-127">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="7d727-127">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="7d727-128">[L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7d727-128">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="7d727-129">[Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="7d727-129">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="7d727-130">[Les événements et les Types de messages](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md) </span><span class="sxs-lookup"><span data-stu-id="7d727-130">[Message Types and Events](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md) </span></span>  
 [<span data-ttu-id="7d727-131">La messagerie HL7</span><span class="sxs-lookup"><span data-stu-id="7d727-131">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)