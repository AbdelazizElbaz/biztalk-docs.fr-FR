---
title: "Considérations relatives à la création de plat fichier schémas de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52271b17-4f0b-4286-a462-cd5951ae49aa
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d0cbe19b85fc65c492f1e0ae377da94dad75baf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-creating-flat-file-message-schemas"></a><span data-ttu-id="2f2ff-102">Considérations relatives à la création de plat fichier schémas de Message</span><span class="sxs-lookup"><span data-stu-id="2f2ff-102">Considerations When Creating Flat File Message Schemas</span></span>
<span data-ttu-id="2f2ff-103">Il faut tenir compte d'un certain nombre de considérations lorsque vous utilisez des schémas de message de fichier plat.</span><span class="sxs-lookup"><span data-stu-id="2f2ff-103">There are a number of considerations when working with flat file message schemas.</span></span> <span data-ttu-id="2f2ff-104">Certaines concernent l'ensemble des schémas de fichier plat tandis que d'autres ont trait spécifiquement aux enregistrements positionnels, aux enregistrements délimités, aux champs positionnels ou aux champs délimités.</span><span class="sxs-lookup"><span data-stu-id="2f2ff-104">This includes considerations that apply to all flat file schemas, as well as considerations that apply specifically to positional records, delimited records, positional fields, or delimited fields.</span></span> <span data-ttu-id="2f2ff-105">Il existe également des considérations sur la façon d'interpréter des caractères considérés généralement comme spéciaux en tant que données normales.</span><span class="sxs-lookup"><span data-stu-id="2f2ff-105">There are also considerations about how to interpret otherwise special characters as regular data.</span></span> <span data-ttu-id="2f2ff-106">Cette section contient des informations sur ces points :</span><span class="sxs-lookup"><span data-stu-id="2f2ff-106">This section provides information about these considerations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2f2ff-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2f2ff-107">In This Section</span></span>  
  
-   [<span data-ttu-id="2f2ff-108">Spécification de Page de codes pour les schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="2f2ff-108">Code Page Specification for Flat File Schemas</span></span>](../core/code-page-specification-for-flat-file-schemas.md)  
  
-   [<span data-ttu-id="2f2ff-109">Cas de gestion des schémas de fichier plat</span><span class="sxs-lookup"><span data-stu-id="2f2ff-109">Case Handling in Flat File Schemas</span></span>](../core/case-handling-in-flat-file-schemas.md)  
  
-   [<span data-ttu-id="2f2ff-110">Plages de caractères restreintes</span><span class="sxs-lookup"><span data-stu-id="2f2ff-110">Restricted Character Ranges</span></span>](../core/restricted-character-ranges.md)  
  
-   [<span data-ttu-id="2f2ff-111">Enregistrements positionnels et délimités imbriqués</span><span class="sxs-lookup"><span data-stu-id="2f2ff-111">Nested Positional and Delimited Records</span></span>](../core/nested-positional-and-delimited-records.md)  
  
-   [<span data-ttu-id="2f2ff-112">Considérations concernant les enregistrements positionnels</span><span class="sxs-lookup"><span data-stu-id="2f2ff-112">Positional Record Considerations</span></span>](../core/positional-record-considerations.md)  
  
-   [<span data-ttu-id="2f2ff-113">Considérations concernant les enregistrements délimités</span><span class="sxs-lookup"><span data-stu-id="2f2ff-113">Delimited Record Considerations</span></span>](../core/delimited-record-considerations.md)  
  
-   [<span data-ttu-id="2f2ff-114">Considérations relatives aux champs</span><span class="sxs-lookup"><span data-stu-id="2f2ff-114">Field Considerations</span></span>](../core/field-considerations.md)  
  
-   [<span data-ttu-id="2f2ff-115">Comment interpréter les caractères spéciaux dans le cadre d’une valeur de champ</span><span class="sxs-lookup"><span data-stu-id="2f2ff-115">Ways to Interpret Special Characters as Part of a Field Value</span></span>](../core/ways-to-interpret-special-characters-as-part-of-a-field-value.md)