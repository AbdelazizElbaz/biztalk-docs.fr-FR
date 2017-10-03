---
title: "Types de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data types, messages
- messages, data types
ms.assetid: 7a758289-1629-48a0-843d-6f6773bd5ba6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8580b4f6c2a3f1a9f461b112bb4125f1a11ebbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-types"></a><span data-ttu-id="ed8e8-102">Types de données</span><span class="sxs-lookup"><span data-stu-id="ed8e8-102">Data Types</span></span>
<span data-ttu-id="ed8e8-103">La spécification de type de données est un outil important pour le partitionnement de la complexité de la norme HL7 et il est essentielle de comprendre le contenu des données d’un champ HL7.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-103">The data type specification is an important tool for partitioning the complexity of the HL7 standard, and is critical to understanding the data contents of an HL7 field.</span></span> <span data-ttu-id="ed8e8-104">Certains types de données sont simples et contient uniquement un composant, et certains contiennent de nombreux composants et les sous-composants.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-104">Some data types are simple and contain only one component, and some contain many components and subcomponents.</span></span> <span data-ttu-id="ed8e8-105">Par exemple, nom du Patient PID.5 a les type de données XPN dans la Version 2.4.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-105">For example, PID.5 Patient Name has the data type XPN in Version 2.4.</span></span> <span data-ttu-id="ed8e8-106">Ce type de données prend en charge les subdivisions courantes d’un nom de langue anglaise, par exemple, nom de famille, prénom, deuxième prénom, ainsi que suffixe, préfixe, nom de code de type et plage de validité (date) de nom.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-106">This data type supports the common subdivisions of an English language name, for example, surname, first name, middle name, as well as suffix, prefix, name type code, and name validity (date) range.</span></span>  
  
 <span data-ttu-id="ed8e8-107">Dans les nouvelles versions HL7, vous pouvez ajouter, mais pas supprimer les types de données.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-107">In new HL7 versions, you can add but not remove data types.</span></span> <span data-ttu-id="ed8e8-108">Si vous ajoutez un contenu à un type de données, en ajoutant de nouveaux composants ou des sous-composants, vous pouvez uniquement les ajouter à la fin de la structure dans laquelle elles sont imbriquées.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-108">If you add content to a data type, by adding new components or subcomponents, you can only add them at the end of the structure within which they are nested.</span></span> <span data-ttu-id="ed8e8-109">Dans certains cas, l’organisation HL7 fusionnée existante pour former de nouveaux types de données.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-109">In some cases, the HL7 organization merged existing data types to form new ones.</span></span> <span data-ttu-id="ed8e8-110">Cela conduit à la nécessité de prendre en charge les éléments qui ont été précédemment sous-composants dans les types de données d’origine.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-110">This led to the need to support items that were formerly subcomponents within the original data types.</span></span>  
  
 <span data-ttu-id="ed8e8-111">Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :</span><span class="sxs-lookup"><span data-stu-id="ed8e8-111">The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="ed8e8-112">prend en charge les types de données standard pour toutes les versions de HL7 à partir de la version 2.1.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-112"> supports standard data types for all HL7 versions from V2.1 on.</span></span>  
  
-   <span data-ttu-id="ed8e8-113">Vous pouvez limiter les types de données lorsque cela est approprié lorsque vous développez des interfaces.</span><span class="sxs-lookup"><span data-stu-id="ed8e8-113">You can restrict data types where appropriate when developing interfaces.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed8e8-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ed8e8-114">In This Section</span></span>  
  
-   [<span data-ttu-id="ed8e8-115">ID de Type de données dans HL7 2.1</span><span class="sxs-lookup"><span data-stu-id="ed8e8-115">Data Type ID in HL7 2.1</span></span>](../../adapters-and-accelerators/accelerator-hl7/data-type-id-in-hl7.md)