---
title: "Création de schémas d’en-tête personnalisé pour la découverte de Type dynamique Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, dynamic resolution
- schemas, message types
- schemas, custom headers
- header schemas
ms.assetid: 0c936c57-b533-47ca-9258-576b021fd016
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c87ba83961b9daac07028a994d7c01add0c11a73
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="creating-custom-header-schemas-for-dynamic-message-type-discovery"></a><span data-ttu-id="d624f-102">Création de schémas d’en-tête personnalisé pour la détection de Type de Message dynamique</span><span class="sxs-lookup"><span data-stu-id="d624f-102">Creating Custom Header Schemas for Dynamic Message Type Discovery</span></span>
<span data-ttu-id="d624f-103">Dans la plupart des scénarios, vous devez spécifier le schéma d’en-tête SWIFT par défaut (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) pour la propriété de configuration de schéma d’en-tête SWIFT désassembleur SWIFT de.</span><span class="sxs-lookup"><span data-stu-id="d624f-103">In most scenarios, you should specify the default SWIFT header schema (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) for the SWIFT Header Schema configuration property of the SWIFT disassembler.</span></span> <span data-ttu-id="d624f-104">Le désassembleur SWIFT utilise le schéma d’en-tête SWIFT par défaut pour analyser les en-têtes de message qui se conforment à la spécification standard SWIFT et a nécessaires promu des propriétés pour faciliter la résolution de schéma dynamique (et la résolution de sous-type de « type double » Messages SWIFT tels que MT574_IRSLST et MT574_W8BENO).</span><span class="sxs-lookup"><span data-stu-id="d624f-104">The SWIFT disassembler uses the default SWIFT header schema to parse message headers that conform to the SWIFT standard specification, and has the necessary promoted properties to facilitate dynamic schema resolution (and sub-type resolution for "dual type" SWIFT messages like MT574_IRSLST and MT574_W8BENO).</span></span> <span data-ttu-id="d624f-105">Pour plus d’informations sur le schéma d’en-tête SWIFT par défaut et pour comprendre comment le désassembleur SWIFT effectue la résolution de schéma, consultez [dynamique découverte de Type de Message et la résolution de schéma](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).</span><span class="sxs-lookup"><span data-stu-id="d624f-105">For more information about the default SWIFT header schema and to understand how the SWIFT disassembler performs schema resolution, see [Dynamic Message Type Discovery and Schema Resolution](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).</span></span>  
  
 <span data-ttu-id="d624f-106">Pour d’autres scénarios où les messages contiennent les données d’en-tête standard de non-SWIFT, vous pouvez utiliser un schéma d’en-tête personnalisé pour l’analyse des en-têtes et la découverte de type de message dynamique.</span><span class="sxs-lookup"><span data-stu-id="d624f-106">For other scenarios where messages contain non-SWIFT standard header data, you can use a custom header schema for header parsing and dynamic message type discovery.</span></span> <span data-ttu-id="d624f-107">Pour créer et utiliser un schéma d’en-tête personnalisé pour la résolution de schéma dynamique, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d624f-107">To create and use a custom header schema for dynamic schema resolution, do the following:</span></span>  
  
1.  <span data-ttu-id="d624f-108">Créer un schéma personnalisé qui permet le désassembleur SWIFT structurellement analyser le format de données d’en-tête attendue.</span><span class="sxs-lookup"><span data-stu-id="d624f-108">Create a custom schema that the SWIFT disassembler can use to structurally parse the expected header data format.</span></span>  
  
2.  <span data-ttu-id="d624f-109">Identifiez les champs dans le schéma contiendront les valeurs indiquant le type de message.</span><span class="sxs-lookup"><span data-stu-id="d624f-109">Identify which fields in the schema will hold the value(s) indicating message type.</span></span>  
  
3.  <span data-ttu-id="d624f-110">Ajoutez le schéma de propriété A4SWIFT (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) à la « liste de schémas de propriété » du schéma d’en-tête personnalisé et promouvoir les champs appropriés qui indiquent le type de message à l’aide de ce qui suit [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] propriétés :</span><span class="sxs-lookup"><span data-stu-id="d624f-110">Add the A4SWIFT Property Schema (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) to the "Property schemas list" of the custom header schema and promote the appropriate fields that indicate message type using the following [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] properties:</span></span>  
  
    -   <span data-ttu-id="d624f-111">**A4SWIFT_MessageType**</span><span class="sxs-lookup"><span data-stu-id="d624f-111">**A4SWIFT_MessageType**</span></span>  
  
    -   <span data-ttu-id="d624f-112">**A4SWIFT_MessageType2** (facultatif si **A4SWIFT_MessageTypes** est utilisé)</span><span class="sxs-lookup"><span data-stu-id="d624f-112">**A4SWIFT_MessageType2** (optional if **A4SWIFT_MessageTypes** is used)</span></span>  
  
    -   <span data-ttu-id="d624f-113">**A4SWIFT_SecondaryMessageType** (facultatif)</span><span class="sxs-lookup"><span data-stu-id="d624f-113">**A4SWIFT_SecondaryMessageType** (optional)</span></span>  
  
4.  <span data-ttu-id="d624f-114">Générez et déployez le schéma d’en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d624f-114">Build and deploy the custom header schema.</span></span>  
  
5.  <span data-ttu-id="d624f-115">La propriété de configuration de schéma d’en-tête SWIFT désassembleur SWIFT (dans votre projet de pipeline de réception) de la valeur du schéma d’en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="d624f-115">Set the SWIFT Header Schema configuration property of the SWIFT disassembler (in your receive pipeline project) to the custom header schema.</span></span>  
  
 <span data-ttu-id="d624f-116">Pour plus d’informations sur ces autres propriétés promues et, consultez [propriétés promues A4SWIFT_ *](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d624f-116">For more information about these and other promoted properties, see [A4SWIFT_* Promoted Properties](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md).</span></span> <span data-ttu-id="d624f-117">Pour plus d’informations sur l’utilisation de l’Éditeur BizTalk pour créer et modifier des schémas, promouvoir des propriétés à l’aide d’un schéma de propriété, générer et déployer des projets de schéma, consultez l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d624f-117">For more information about using BizTalk Editor to create and edit schemas, promote properties using a property schema, and build and deploy schema projects, see BizTalk Server Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d624f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d624f-118">See Also</span></span>  
 [<span data-ttu-id="d624f-119">Utilisation du désassembleur et de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="d624f-119">Working with the SWIFT Disassembler and Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)