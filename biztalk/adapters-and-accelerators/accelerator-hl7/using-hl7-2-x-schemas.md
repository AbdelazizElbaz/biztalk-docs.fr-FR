---
title: "L’utilisation des schémas 2.X HL7 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas
- HL7, 2.X schemas
- schemas, 2.X schemas
ms.assetid: 7f2d7dd4-76f1-463e-b579-9839a74b9631
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 934ca60bb3d89e08c9e803813f3548f196c3d56d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-hl7-2x-schemas"></a><span data-ttu-id="cbedb-102">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="cbedb-102">Using HL7 2.X Schemas</span></span>
<span data-ttu-id="cbedb-103">Cette section décrit les versions 2.X de la norme sept de niveau d’intégrité (HL7) pris en charge par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cbedb-103">This section discusses the 2.X versions of the Health Level Seven (HL7) standard supported by [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cbedb-104">Vous devrez peut-être mettre à jour les schémas installés avec BTAHL7 pour se conformer à la HL7 standard.</span><span class="sxs-lookup"><span data-stu-id="cbedb-104">You may need to update the schemas installed with BTAHL7 to conform to the HL7 standard.</span></span> <span data-ttu-id="cbedb-105">Pour ce faire, consultez [résolution des erreurs de base de données](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).</span><span class="sxs-lookup"><span data-stu-id="cbedb-105">To do so, see [Resolving Database Errors](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbedb-106">Le moteur de BTAHL7 ne peut pas traiter les instances de message conforme aux schémas HL7 qui ont une structure de schéma ambigu.</span><span class="sxs-lookup"><span data-stu-id="cbedb-106">The BTAHL7 engine cannot process message instances conforming to HL7 schemas that have an ambiguous schema structure.</span></span> <span data-ttu-id="cbedb-107">Une structure de schéma ambigu est celle qui la norme HL7 n’a pas complètement défini.</span><span class="sxs-lookup"><span data-stu-id="cbedb-107">An ambiguous schema structure is one that the HL7 standard has not completely defined.</span></span> <span data-ttu-id="cbedb-108">Ces schémas incluent ceux pour les types de messages CSU et SUR.</span><span class="sxs-lookup"><span data-stu-id="cbedb-108">Such schemas include those for message types CSU and SUR.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cbedb-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="cbedb-109">In This Section</span></span>  
  
-   [<span data-ttu-id="cbedb-110">Versions 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="cbedb-110">HL7 2.X Versions</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-versions.md)  
  
-   [<span data-ttu-id="cbedb-111">Les événements et les sous-dossiers 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="cbedb-111">HL7 2.X Subfolders and Events</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-subfolders-and-events.md)  
  
-   [<span data-ttu-id="cbedb-112">Fichiers de schéma HL7 2.X communs</span><span class="sxs-lookup"><span data-stu-id="cbedb-112">HL7 2.X Common Schema Files</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)  
  
-   [<span data-ttu-id="cbedb-113">Extension des schémas 2.X HL7 avec des objets Z</span><span class="sxs-lookup"><span data-stu-id="cbedb-113">Extending HL7 2.X Schemas with Z Objects</span></span>](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)  
  
-   [<span data-ttu-id="cbedb-114">Résolution des erreurs de base de données</span><span class="sxs-lookup"><span data-stu-id="cbedb-114">Resolving Database Errors</span></span>](../../adapters-and-accelerators/accelerator-hl7/resolving-database-errors.md)  
  
-   [<span data-ttu-id="cbedb-115">« X » et « Y » Optionality</span><span class="sxs-lookup"><span data-stu-id="cbedb-115">'X' and 'Y' Optionality</span></span>](../../adapters-and-accelerators/accelerator-hl7/x-and-y-optionality.md)  
  
-   [<span data-ttu-id="cbedb-116">Segments répétitifs</span><span class="sxs-lookup"><span data-stu-id="cbedb-116">Repeatable Field Segments</span></span>](../../adapters-and-accelerators/accelerator-hl7/repeatable-field-segments.md)