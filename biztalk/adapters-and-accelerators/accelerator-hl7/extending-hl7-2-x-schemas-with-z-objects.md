---
title: "Extension des schémas 2.X HL7 avec des objets Z | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, Z objects
- Z objects, extending 2.X schemas
ms.assetid: 0980d919-eb81-4c65-b0f7-f17f7cfef6b3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27ef2bea3e13904f04449a5b77d05672c2b2d94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-hl7-2x-schemas-with-z-objects"></a><span data-ttu-id="d5c38-102">Extension des schémas 2.X HL7 avec des objets Z</span><span class="sxs-lookup"><span data-stu-id="d5c38-102">Extending HL7 2.X Schemas with Z Objects</span></span>
<span data-ttu-id="d5c38-103">L’organisation HL7 définit HL7 2.X, schémas et attend que tous les expéditeurs et destinataires de reconnaître et utiliser ces schémas comme les définit par l’organisation.</span><span class="sxs-lookup"><span data-stu-id="d5c38-103">The HL7 organization defines HL7 2.X schemas, and expects all senders and receivers to recognize and use these schemas as the organization defines them.</span></span> <span data-ttu-id="d5c38-104">Conformes aux schémas garantit l’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="d5c38-104">Conforming to the schemas ensures for interoperability.</span></span> <span data-ttu-id="d5c38-105">Toutefois, la norme HL7 permet de personnaliser HL7 existant schémas 2.X à vos besoins locales spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d5c38-105">However, the HL7 standard enables you to customize existing HL7 2.X schemas for your specific local purposes.</span></span> <span data-ttu-id="d5c38-106">Vous pouvez également définir des objets et des schémas entièrement nouvelles.</span><span class="sxs-lookup"><span data-stu-id="d5c38-106">You can also define entirely new schemas and objects.</span></span> <span data-ttu-id="d5c38-107">Pour ce faire avec ce que le HL7 standard appelle les objets Z.</span><span class="sxs-lookup"><span data-stu-id="d5c38-107">You do so with what the HL7 standard calls Z objects.</span></span>  
  
 <span data-ttu-id="d5c38-108">Le HL7 standard ne définit pas la valeur des objets de Z.</span><span class="sxs-lookup"><span data-stu-id="d5c38-108">The HL7 standard does not define the value of Z objects.</span></span> <span data-ttu-id="d5c38-109">Les schémas HL7 publiées n’incluent pas les.</span><span class="sxs-lookup"><span data-stu-id="d5c38-109">The published HL7 schemas do not include them.</span></span> <span data-ttu-id="d5c38-110">Vous les définissez localement et que vous les utilisez en accord avec toutes les parties locales.</span><span class="sxs-lookup"><span data-stu-id="d5c38-110">You define them locally, and use them by agreement with all local parties.</span></span> <span data-ttu-id="d5c38-111">L’organisation HL7 réserve tous les type de message, d’événements déclencheurs, segment, type de données et les noms de tables commençant par « Z » pour cet usage local.</span><span class="sxs-lookup"><span data-stu-id="d5c38-111">The HL7 organization reserves all message type, trigger event, segment, data type, and table names beginning with "Z" for this local use.</span></span> <span data-ttu-id="d5c38-112">En raison du préfixe, la norme HL7 appelle ces objets objets définis par site Z.</span><span class="sxs-lookup"><span data-stu-id="d5c38-112">Because of the prefix, the HL7 standard calls these site-defined objects Z objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5c38-113">Lorsque vous ajoutez un objet de Z à un schéma HL7 existant, vous risquez de plusieurs versions de ce schéma.</span><span class="sxs-lookup"><span data-stu-id="d5c38-113">When you add a Z object to an existing HL7-defined schema, you may end up with multiple versions of that schema.</span></span> <span data-ttu-id="d5c38-114">La meilleure façon de gérer ces versions multiples consiste à utiliser la fonctionnalité de Namespace dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5c38-114">The best way to handle these multiple versions is to use the Namespace feature in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="d5c38-115">Vous pouvez trouver cette fonctionnalité sur le **Validation** onglet [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration (au niveau du tiers).</span><span class="sxs-lookup"><span data-stu-id="d5c38-115">You can find this feature on the **Validation** tab in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (at the party level).</span></span> <span data-ttu-id="d5c38-116">Vous devez également modifier la propriété de l’espace de noms du schéma que vous déployez pour ce projet.</span><span class="sxs-lookup"><span data-stu-id="d5c38-116">You will also need to change the namespace property within the schema that you deploy for that project.</span></span>  
  
 <span data-ttu-id="d5c38-117">Dans la création ou le traitement Z des objets, vous devez suivre les règles de l’organisation HL7 a établi pour les objets Z...</span><span class="sxs-lookup"><span data-stu-id="d5c38-117">In creating or processing Z objects, you should follow the rules that the HL7 organization has established for Z objects..</span></span>  
  
 <span data-ttu-id="d5c38-118">Lorsque vous ajoutez un objet de Z à un schéma existant ou créer un nouveau schéma de message Z, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] utilise le schéma avec l’ou les objets Z pour traiter le message encodé HL7.</span><span class="sxs-lookup"><span data-stu-id="d5c38-118">When you add a Z object to an existing schema or create a new Z message schema, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] will use the schema with the Z object(s) to process the HL7-encoded message.</span></span> <span data-ttu-id="d5c38-119">Ce type d’objet de Z est un objet Z déclaré.</span><span class="sxs-lookup"><span data-stu-id="d5c38-119">This type of Z object is a declared Z object.</span></span> <span data-ttu-id="d5c38-120">Vous pouvez également utiliser un segment Z non déclaré, le moteur d’intégration ne traitera pas selon le schéma de message.</span><span class="sxs-lookup"><span data-stu-id="d5c38-120">You can also use an undeclared Z segment, which the integration engine will not process according to the message schema.</span></span> <span data-ttu-id="d5c38-121">Pour plus d’informations sur ce type de segment de Z, consultez [gestion des Segments de Z non déclaré](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md).</span><span class="sxs-lookup"><span data-stu-id="d5c38-121">For more information about this type of Z segment, see [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5c38-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d5c38-122">In This Section</span></span>  
  
-   [<span data-ttu-id="d5c38-123">Création de Segments de Z déclaré</span><span class="sxs-lookup"><span data-stu-id="d5c38-123">Creating Declared Z Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)  
  
-   [<span data-ttu-id="d5c38-124">Création de Types de données personnalisés dans les schémas</span><span class="sxs-lookup"><span data-stu-id="d5c38-124">Creating Custom Data Types in Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)  
  
-   [<span data-ttu-id="d5c38-125">Création de Tables personnalisées dans les schémas</span><span class="sxs-lookup"><span data-stu-id="d5c38-125">Creating Custom Tables in Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-custom-tables-in-schemas.md)  
  
-   [<span data-ttu-id="d5c38-126">Extension des énumérations</span><span class="sxs-lookup"><span data-stu-id="d5c38-126">Extending Enumerations</span></span>](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)  
  
-   [<span data-ttu-id="d5c38-127">Personnalisation des Messages via des objets de plan</span><span class="sxs-lookup"><span data-stu-id="d5c38-127">Customizing Messages through Z Objects</span></span>](../../adapters-and-accelerators/accelerator-hl7/customizing-messages-through-z-objects.md)