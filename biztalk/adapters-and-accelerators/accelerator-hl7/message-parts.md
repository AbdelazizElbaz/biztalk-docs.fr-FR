---
title: Parties de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- messages, message parts
- segments, messages
ms.assetid: 2bb6557e-cd4a-42b7-8bc2-f8b53a59517e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9b6b02096a0cc75460552a6cd1dd56ef9e6c4e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-parts"></a><span data-ttu-id="d031e-102">Parties du message</span><span class="sxs-lookup"><span data-stu-id="d031e-102">Message Parts</span></span>
<span data-ttu-id="d031e-103">Un message HL7 contienne les éléments suivants : segments, les champs de données, les composants et éventuellement sous-composants.</span><span class="sxs-lookup"><span data-stu-id="d031e-103">An HL7 message contains the following parts: segments, data fields, components, and optionally subcomponents.</span></span> <span data-ttu-id="d031e-104">Les messages de HL7 ont la structure hiérarchique suivante :</span><span class="sxs-lookup"><span data-stu-id="d031e-104">HL7 messages have the following hierarchical structure:</span></span>  
  
 <span data-ttu-id="d031e-105">Segment</span><span class="sxs-lookup"><span data-stu-id="d031e-105">Segment</span></span>  
  
 <span data-ttu-id="d031e-106">Champ de données</span><span class="sxs-lookup"><span data-stu-id="d031e-106">Data Field</span></span>  
  
 <span data-ttu-id="d031e-107">Composant</span><span class="sxs-lookup"><span data-stu-id="d031e-107">Component</span></span>  
  
 <span data-ttu-id="d031e-108">Sous-composant (facultatif)</span><span class="sxs-lookup"><span data-stu-id="d031e-108">Subcomponent (optional)</span></span>  
  
 <span data-ttu-id="d031e-109">**Segments**</span><span class="sxs-lookup"><span data-stu-id="d031e-109">**Segments**</span></span>  
  
 <span data-ttu-id="d031e-110">Un segment est un regroupement logique des champs de données.</span><span class="sxs-lookup"><span data-stu-id="d031e-110">A segment is a logical grouping of data fields.</span></span> <span data-ttu-id="d031e-111">Les segments sont au niveau plus élevé (profondeur 1) de la hiérarchie de message.</span><span class="sxs-lookup"><span data-stu-id="d031e-111">Segments are at the highest level (depth 1) of the message hierarchy.</span></span> <span data-ttu-id="d031e-112">Chaque segment possède un nom qui inclut une valeur littérale de trois caractères.</span><span class="sxs-lookup"><span data-stu-id="d031e-112">Each segment has a name that includes a three-character literal value.</span></span> <span data-ttu-id="d031e-113">Le tableau suivant présente des exemples de noms de segment contenus dans les types de message ADT.</span><span class="sxs-lookup"><span data-stu-id="d031e-113">The following table shows examples of segment names contained by ADT message types.</span></span>  
  
|<span data-ttu-id="d031e-114">Segment de code</span><span class="sxs-lookup"><span data-stu-id="d031e-114">Segment code</span></span>|<span data-ttu-id="d031e-115"> Description</span><span class="sxs-lookup"><span data-stu-id="d031e-115">Description</span></span>|  
|------------------|-----------------|  
|<span data-ttu-id="d031e-116">MSH</span><span class="sxs-lookup"><span data-stu-id="d031e-116">MSH</span></span>|<span data-ttu-id="d031e-117">En-tête de message</span><span class="sxs-lookup"><span data-stu-id="d031e-117">Message Header</span></span>|  
|<span data-ttu-id="d031e-118">EVN</span><span class="sxs-lookup"><span data-stu-id="d031e-118">EVN</span></span>|<span data-ttu-id="d031e-119">Type d’événement</span><span class="sxs-lookup"><span data-stu-id="d031e-119">Event Type</span></span>|  
|<span data-ttu-id="d031e-120">PID</span><span class="sxs-lookup"><span data-stu-id="d031e-120">PID</span></span>|<span data-ttu-id="d031e-121">Informations sur les patients</span><span class="sxs-lookup"><span data-stu-id="d031e-121">Patient Information</span></span>|  
  
 <span data-ttu-id="d031e-122">Les messages HL7 ont un *en-tête de message* et *corps*.</span><span class="sxs-lookup"><span data-stu-id="d031e-122">HL7 messages have a *message header* and *body*.</span></span> <span data-ttu-id="d031e-123">Les segments MSH définissent l’en-tête du message et tous les autres types de segments forment le corps du message.</span><span class="sxs-lookup"><span data-stu-id="d031e-123">The MSH segments define the header of the message and all other types of segments form the body of the message.</span></span>  
  
 <span data-ttu-id="d031e-124">**Champs de données**</span><span class="sxs-lookup"><span data-stu-id="d031e-124">**Data Fields**</span></span>  
  
 <span data-ttu-id="d031e-125">Un champ de données est une chaîne de caractères qui se produisent au niveau de profondeur 2 de la hiérarchie de message.</span><span class="sxs-lookup"><span data-stu-id="d031e-125">A data field is a string of characters that occur at depth 2 of the message hierarchy.</span></span> <span data-ttu-id="d031e-126">Types de données définissent les champs de données : Simple et complexe.</span><span class="sxs-lookup"><span data-stu-id="d031e-126">Data types define data fields: Simple and Complex.</span></span>  
  
 <span data-ttu-id="d031e-127">L’exemple suivant illustre la structure de message hiérarchique des segments MSH et EVN qui contient les champs de données MSH.1 et EVN.1 :</span><span class="sxs-lookup"><span data-stu-id="d031e-127">The following example shows the hierarchical message structure of the MSH and EVN segments containing the MSH.1 and EVN.1 data fields:</span></span>  
  
 <span data-ttu-id="d031e-128">MSH</span><span class="sxs-lookup"><span data-stu-id="d031e-128">MSH</span></span>  
  
 <span data-ttu-id="d031e-129">MSH.1</span><span class="sxs-lookup"><span data-stu-id="d031e-129">MSH.1</span></span>  
  
 <span data-ttu-id="d031e-130">EVN</span><span class="sxs-lookup"><span data-stu-id="d031e-130">EVN</span></span>  
  
 <span data-ttu-id="d031e-131">EVN.1</span><span class="sxs-lookup"><span data-stu-id="d031e-131">EVN.1</span></span>  
  
 <span data-ttu-id="d031e-132">**Composants et les sous-composants**</span><span class="sxs-lookup"><span data-stu-id="d031e-132">**Components and Subcomponents**</span></span>  
  
 <span data-ttu-id="d031e-133">Composants et les sous-composants davantage contiennent les données dans les champs de données.</span><span class="sxs-lookup"><span data-stu-id="d031e-133">Components and subcomponents further contain the data within data fields.</span></span> <span data-ttu-id="d031e-134">Composants et les sous-composants peuvent répéter dans le même champ.</span><span class="sxs-lookup"><span data-stu-id="d031e-134">Components and subcomponents can repeat within the same field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d031e-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d031e-135">See Also</span></span>  
 <span data-ttu-id="d031e-136">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="d031e-136">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="d031e-137">[Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="d031e-137">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="d031e-138">L’utilisation des schémas 2.X HL7</span><span class="sxs-lookup"><span data-stu-id="d031e-138">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)