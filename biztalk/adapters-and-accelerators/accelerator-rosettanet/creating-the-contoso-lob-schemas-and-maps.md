---
title: "Création des mappages et schémas LOB Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, LOB
- LOBs, schemas
- private process tutorial, creating LOB schemas
- private process tutorial, creating maps
- maps
ms.assetid: fda8852a-51d8-4987-a187-834883a06d9b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f204efd00858f3f4204848f4fb4a0dcef5233b3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-contoso-lob-schemas-and-maps"></a><span data-ttu-id="d55df-102">Création de mappages et de schémas LOB Contoso</span><span class="sxs-lookup"><span data-stu-id="d55df-102">Creating the Contoso LOB Schemas and Maps</span></span>
<span data-ttu-id="d55df-103">Dans cette section, vous allez créer des schémas métier (LOB, Line-of-Business) que l'organisation Contoso utilise dans son système ERP.</span><span class="sxs-lookup"><span data-stu-id="d55df-103">In this section, you create the line-of-business (LOB) schemas that the Contoso organization uses in their ERP system.</span></span> <span data-ttu-id="d55df-104">Vous utilisez la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] outil Mappeur pour créer des transformations de données entre les messages Contoso internes et les types de messages RosettaNet entrants et sortants.</span><span class="sxs-lookup"><span data-stu-id="d55df-104">You use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Mapper tool to create data transformations between the internal Contoso messages and the inbound and outbound RosettaNet message types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d55df-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d55df-105">In This Section</span></span>  
  
-   [<span data-ttu-id="d55df-106">Étape 1 : Création d’une Solution BizTalk pour la requête de la disponibilité et le prix de Contoso</span><span class="sxs-lookup"><span data-stu-id="d55df-106">Step 1: Creating a New BizTalk Solution for the Contoso Price and Availability Request</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md)  
  
-   [<span data-ttu-id="d55df-107">Étape 2 : Création de schémas Application LOB Contoso pour le prix et le projet de disponibilité à l’aide de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="d55df-107">Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-contoso-lob-application-schema-for-price-and-availability.md)  
  
-   [<span data-ttu-id="d55df-108">Étape 3 : Créer les mappages d’applications métier Contoso pour le prix et le projet de disponibilité à l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="d55df-108">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)