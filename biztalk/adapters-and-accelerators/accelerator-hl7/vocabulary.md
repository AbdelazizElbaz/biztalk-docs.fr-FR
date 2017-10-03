---
title: Vocabulaire | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, vocabulary
- vocabularies
ms.assetid: c5df05dd-4af8-4e48-8509-e692b04adf3c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c77247054914097131103fe33d86fc78551d8cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="vocabulary"></a><span data-ttu-id="49a19-102">Vocabulaire</span><span class="sxs-lookup"><span data-stu-id="49a19-102">Vocabulary</span></span>
<span data-ttu-id="49a19-103">HL7 Version 2 fournit une prise en charge pour les vocabulaires pour les éléments codés, mais pour l’essentiel, fournit une structure qui transmet les codes dessinées à partir des systèmes de codage locales.</span><span class="sxs-lookup"><span data-stu-id="49a19-103">HL7 Version 2 provides some support for vocabularies for coded elements, but for the most part, provides a structure that transmits codes drawn from local coding systems.</span></span>  
  
 <span data-ttu-id="49a19-104">HL7 Version 2, un segment lie tous les champs codés.</span><span class="sxs-lookup"><span data-stu-id="49a19-104">In HL7 Version 2, a segment table links all coded fields.</span></span> <span data-ttu-id="49a19-105">La table segment inclut l’identificateur de la table par le champ.</span><span class="sxs-lookup"><span data-stu-id="49a19-105">The segment table includes the identifier of the table that the field uses.</span></span> <span data-ttu-id="49a19-106">Il existe trois types de tables : HL7 définies, défini de façon externe et définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="49a19-106">There are three types of tables: HL7 defined, externally defined, and user-defined.</span></span> <span data-ttu-id="49a19-107">Dans certains cas, la norme fournit des exemples de valeurs pour une table définie par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="49a19-107">In some cases, the standard supplies example values for a user-defined table.</span></span> <span data-ttu-id="49a19-108">Vous devez traiter ces comme la norme HL7 a étiqueté les.</span><span class="sxs-lookup"><span data-stu-id="49a19-108">You should treat these as the HL7 standard has labeled them.</span></span>  
  
 <span data-ttu-id="49a19-109">Dans les nouvelles versions, vous ne peut pas supprimer les codes des tables de HL7 défini, mais vous pouvez ajouter de nouveaux codes.</span><span class="sxs-lookup"><span data-stu-id="49a19-109">In new versions, you cannot remove codes from HL7 defined tables, but you can add new codes.</span></span> <span data-ttu-id="49a19-110">Vous pouvez modifier les tables définies par l’utilisateur à volonté.</span><span class="sxs-lookup"><span data-stu-id="49a19-110">You can change user-defined tables at will.</span></span>  
  
 <span data-ttu-id="49a19-111">Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge ces exigences :</span><span class="sxs-lookup"><span data-stu-id="49a19-111">The following functions of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   <span data-ttu-id="49a19-112">Vous pouvez utiliser toutes les tables HL7 défini.</span><span class="sxs-lookup"><span data-stu-id="49a19-112">You can use all of the HL7 defined tables.</span></span>  
  
-   <span data-ttu-id="49a19-113">Vous pouvez importer et ensembles de code tels que ICD9 et LOINC définie par l’utilisation externe.</span><span class="sxs-lookup"><span data-stu-id="49a19-113">You can import and use externally defined code sets such as ICD9 and LOINC.</span></span>  
  
-   <span data-ttu-id="49a19-114">Vous pouvez fournir les valeurs des tables définies par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="49a19-114">You can provide the values for user-defined tables.</span></span>  
  
-   <span data-ttu-id="49a19-115">Dans les cas où les systèmes prennent en charge différents ensembles de codes, vous pouvez définir des mappages qui autorisent des ensembles de code disparates interagir.</span><span class="sxs-lookup"><span data-stu-id="49a19-115">In cases where systems are supporting different sets of codes, you can set up mappings that allow disparate code sets to interoperate.</span></span> <span data-ttu-id="49a19-116">Si nécessaire, vous pouvez définir plusieurs instances d’une table unique défini par l’utilisateur pour accéder en même temps que le mappage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="49a19-116">If necessary, you can define multiple instances of a single user-defined table to go along with the intermediary mapping.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49a19-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49a19-117">See Also</span></span>  
 <span data-ttu-id="49a19-118">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="49a19-118">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="49a19-119">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="49a19-119">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="49a19-120">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="49a19-120">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)