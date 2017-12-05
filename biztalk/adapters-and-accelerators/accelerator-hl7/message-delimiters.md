---
title: "Délimiteurs de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, events
- messages, XML messages
- events
- delimiters
- messages, delimiters
- flat files
- XML messages
- messages, flat files
ms.assetid: d25bf6db-5512-4c82-be0e-00da024c55d1
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e25e4fad2eb9e32c87f8a395bd924fc4a1f2eb5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-delimiters"></a><span data-ttu-id="ddf45-102">Délimiteurs de message</span><span class="sxs-lookup"><span data-stu-id="ddf45-102">Message Delimiters</span></span>
<span data-ttu-id="ddf45-103">Les événements de message définis par les normes HL7 prennent la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="ddf45-103">Message events defined by HL7 standards take the following form:</span></span>  
  
-   <span data-ttu-id="ddf45-104">**Fichiers plats**.</span><span class="sxs-lookup"><span data-stu-id="ddf45-104">**Flat files**.</span></span> <span data-ttu-id="ddf45-105">Les événements de message définis par les versions HL7 2.4 et versions antérieures prennent la forme de fichiers plats.</span><span class="sxs-lookup"><span data-stu-id="ddf45-105">Message events defined by HL7 versions 2.4 and earlier take the form of flat files.</span></span>  
  
-   <span data-ttu-id="ddf45-106">**XML**.</span><span class="sxs-lookup"><span data-stu-id="ddf45-106">**XML**.</span></span> <span data-ttu-id="ddf45-107">Les événements de message définis par HL7 versions 2 XML et la version 3 prennent la forme de fichiers XML.</span><span class="sxs-lookup"><span data-stu-id="ddf45-107">Message events defined by HL7 versions 2.XML and version 3 take the form of XML files.</span></span>  
  
 <span data-ttu-id="ddf45-108">Étant donné que le HL7 standard ne suit pas le format de position, elle utilise des délimiteurs pour définir le segment, champ, composant et les niveaux de sous-composant de fichiers plats.</span><span class="sxs-lookup"><span data-stu-id="ddf45-108">Since the HL7 standard does not follow positional format, it uses delimiters to define the segment, field, component, and subcomponent levels of flat files.</span></span> <span data-ttu-id="ddf45-109">Le tableau suivant répertorie les séparateurs par défaut utilisés par les fichiers plats HL7.</span><span class="sxs-lookup"><span data-stu-id="ddf45-109">The following table lists the default delimiters used by HL7 flat files.</span></span>  
  
|<span data-ttu-id="ddf45-110">Délimiteur</span><span class="sxs-lookup"><span data-stu-id="ddf45-110">Delimiter</span></span>|<span data-ttu-id="ddf45-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="ddf45-111">Value</span></span>|<span data-ttu-id="ddf45-112">Utilisation</span><span class="sxs-lookup"><span data-stu-id="ddf45-112">Usage</span></span>|  
|---------------|-----------|-----------|  
|<span data-ttu-id="ddf45-113">Terminateur de segment</span><span class="sxs-lookup"><span data-stu-id="ddf45-113">Segment terminator</span></span>|<span data-ttu-id="ddf45-114">\<retour chariot\></span><span class="sxs-lookup"><span data-stu-id="ddf45-114">\<cr\></span></span>|<span data-ttu-id="ddf45-115">Un retour chariot met fin à un enregistrement de segment.</span><span class="sxs-lookup"><span data-stu-id="ddf45-115">A carriage return terminates a segment record.</span></span> <span data-ttu-id="ddf45-116">Vous ne pouvez pas modifier cette valeur.</span><span class="sxs-lookup"><span data-stu-id="ddf45-116">You cannot change this value.</span></span>|  
|<span data-ttu-id="ddf45-117">Séparateur de champs</span><span class="sxs-lookup"><span data-stu-id="ddf45-117">Field separator</span></span>|<span data-ttu-id="ddf45-118">&#124;</span><span class="sxs-lookup"><span data-stu-id="ddf45-118">&#124;</span></span>|<span data-ttu-id="ddf45-119">Une barre verticale sépare les deux champs de données adjacents dans un segment.</span><span class="sxs-lookup"><span data-stu-id="ddf45-119">A pipe character separates two adjacent data fields within a segment.</span></span> <span data-ttu-id="ddf45-120">Ce caractère sépare également l’ID de segment du premier champ de données dans chaque segment.</span><span class="sxs-lookup"><span data-stu-id="ddf45-120">This character also separates the segment ID from the first data field in each segment.</span></span>|  
|<span data-ttu-id="ddf45-121">Séparateur de composants</span><span class="sxs-lookup"><span data-stu-id="ddf45-121">Component separator</span></span>|^|<span data-ttu-id="ddf45-122">Un caractère hat sépare les composants adjacents de données des champs où autorisée par la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="ddf45-122">A hat character separates adjacent components of data fields where allowed by the HL7 standard.</span></span>|  
|<span data-ttu-id="ddf45-123">Séparateur de sous-composant</span><span class="sxs-lookup"><span data-stu-id="ddf45-123">Subcomponent separator</span></span>|&|<span data-ttu-id="ddf45-124">Une esperluette sépare les sous-composants adjacents de données des champs où autorisée par la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="ddf45-124">An ampersand character separates adjacent subcomponents of data fields where allowed by the HL7 standard.</span></span> <span data-ttu-id="ddf45-125">S’il n’y a aucun sous-composant, vous pouvez omettre ce caractère.</span><span class="sxs-lookup"><span data-stu-id="ddf45-125">If there are no subcomponents, then you can omit this character.</span></span>|  
|<span data-ttu-id="ddf45-126">Séparateur de répétition</span><span class="sxs-lookup"><span data-stu-id="ddf45-126">Repetition separator</span></span>|~|<span data-ttu-id="ddf45-127">Un tilde sépare les occurrences multiples de composants ou des sous-composants d’un champ où autorisée par la norme HL7.</span><span class="sxs-lookup"><span data-stu-id="ddf45-127">A tilde character separates multiple occurrences of components or subcomponents in a field where allowed by the HL7 standard.</span></span>|  
|<span data-ttu-id="ddf45-128">Caractère d’échappement</span><span class="sxs-lookup"><span data-stu-id="ddf45-128">Escape character</span></span>|\|<span data-ttu-id="ddf45-129">Vous utilisez un caractère d’échappement avec n’importe quel champ conforme à un type de données ST, TX ou FT, ou avec le composant (quatrième) de données du type de données ED.</span><span class="sxs-lookup"><span data-stu-id="ddf45-129">You use an escape character with any field that conforms to an ST, TX, or FT data type, or with the data (fourth) component of the ED data type.</span></span> <span data-ttu-id="ddf45-130">Si aucun caractère d’échappement n’existe dans un message, vous pouvez omettre ce caractère.</span><span class="sxs-lookup"><span data-stu-id="ddf45-130">If no escape characters exist in a message, you can omit this character.</span></span> <span data-ttu-id="ddf45-131">Toutefois, vous devez l’inclure si vous utilisez des sous-composants dans le message.</span><span class="sxs-lookup"><span data-stu-id="ddf45-131">However, you must include it if you use subcomponents in the message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddf45-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddf45-132">See Also</span></span>  
 <span data-ttu-id="ddf45-133">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="ddf45-133">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="ddf45-134">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="ddf45-134">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="ddf45-135">Utilisation des schémas HL7 2.X</span><span class="sxs-lookup"><span data-stu-id="ddf45-135">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)