---
title: HL7 Les Versions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HL7, standards
- HL7, versions
ms.assetid: 47299c6f-55c3-4434-8170-5ad73fe9a84c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c7edcfa6c44467c0660efd8a9b4b02df7010de6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-versions"></a><span data-ttu-id="46f8c-102">Versions HL7</span><span class="sxs-lookup"><span data-stu-id="46f8c-102">HL7 Versions</span></span>
<span data-ttu-id="46f8c-103">HL7 Version 2 est une famille de normes étroitement liées au lieu d’un seul standard.</span><span class="sxs-lookup"><span data-stu-id="46f8c-103">HL7 Version 2 is a family of closely related standards rather than a single standard.</span></span> <span data-ttu-id="46f8c-104">L’organisation HL7 vise à ces normes pour être compatible vers le haut dans l’application des règles de compatibilité des versions entre HL7.</span><span class="sxs-lookup"><span data-stu-id="46f8c-104">The HL7 organization has designed these standards to be upwards compatible through the application of the HL7 inter-version compatibility rules.</span></span> <span data-ttu-id="46f8c-105">Ces règles garantissent que, dans les limites de la Version 2, une interface définie selon les règles d’une version HL7 continuera à fonctionner dans la définition des versions de successeur.</span><span class="sxs-lookup"><span data-stu-id="46f8c-105">These rules guarantee that, within the confines of Version 2, an interface defined under the rules of an HL7 version will still function within the definition of successor versions.</span></span> <span data-ttu-id="46f8c-106">Afin qu’un système de réception soit en mesure d’accepter des messages à partir de versions ultérieures sans rompre son implémentation et l’envoi d’un système sera en mesure de continuer à envoyer des messages à des destinataires qui prennent en charge les versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="46f8c-106">So that a receiving system will be able to accept messages from later versions without breaking its implementation and a sending system will be able to continue to send messages to receivers who support later versions.</span></span>  
  
 <span data-ttu-id="46f8c-107">Il est important de noter que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) :</span><span class="sxs-lookup"><span data-stu-id="46f8c-107">It is important to note that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]):</span></span>  
  
-   <span data-ttu-id="46f8c-108">Prend en charge toutes les versions HL7 dynamiques à partir de la Version 2.1 via la Version 2.5</span><span class="sxs-lookup"><span data-stu-id="46f8c-108">Supports all live HL7 versions from Version 2.1 through Version 2.5</span></span>  
  
-   <span data-ttu-id="46f8c-109">Fournit les fonctionnalités requises pour le mappage entre les versions HL7 et permet l’interopérabilité de plusieurs versions sur un seul site</span><span class="sxs-lookup"><span data-stu-id="46f8c-109">Provides the functionality needed to map between HL7 versions, and enables the interoperability of multiple versions at a single site</span></span>  
  
-   <span data-ttu-id="46f8c-110">Prend en charge la localisation en prenant en charge des segments de Z et Active le mappage entre l’interprétation du remplacement ou utilise des messages standards</span><span class="sxs-lookup"><span data-stu-id="46f8c-110">Supports localization by supporting Z segments, and enables mapping between alternate interpretations or uses of the standard messages</span></span>  
  
 <span data-ttu-id="46f8c-111">Il est important de noter la différence entre les versions de la norme de messagerie :</span><span class="sxs-lookup"><span data-stu-id="46f8c-111">It is important to note the difference between the versions of the messaging standard:</span></span>  
  
-   <span data-ttu-id="46f8c-112">Version 1 fonctionnait comme une preuve de concept</span><span class="sxs-lookup"><span data-stu-id="46f8c-112">Version 1 functioned as a proof of concept</span></span>  
  
-   <span data-ttu-id="46f8c-113">Version 2 fournit une collection de spécifications de message pour prendre en charge l’échange de messages entre des applications</span><span class="sxs-lookup"><span data-stu-id="46f8c-113">Version 2 provides a collection of message specifications to support message exchange between applications</span></span>  
  
-   <span data-ttu-id="46f8c-114">Version 3 fournit un ensemble intégré basé sur un modèle de spécifications pour prendre en charge une variété de besoins de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="46f8c-114">Version 3 will provide a model-based integrated set of specifications to support a range of interoperability needs</span></span>  
  
 <span data-ttu-id="46f8c-115">Fondamentalement, Version 2 met l’accent sur une approche pragmatique pour fournir aux utilisateurs les spécifications nécessaires pour mener à bien les tâches spécifiées, tandis que la Version 3 se concentre sur la garantie de cohérence et à long terme d’extensibilité pour le corps de spécifications de message prise comme une dans son ensemble.</span><span class="sxs-lookup"><span data-stu-id="46f8c-115">In essence, Version 2 focuses on a pragmatic approach to providing users with the specifications they need to carry out specified tasks, while Version 3 focuses on assuring consistency and long-term extensibility for the body of message specifications taken as a whole.</span></span>  
  
 <span data-ttu-id="46f8c-116">L’Architecture de Document cliniques fournit une extension significative à la norme HL7 en introduisant des normes pour la représentation sous forme de documents cliniques à l’aide de XML.</span><span class="sxs-lookup"><span data-stu-id="46f8c-116">The Clinical Document Architecture provides a significant extension to the HL7 standard by introducing standards for the representation of clinical documents using XML.</span></span>  
  
 <span data-ttu-id="46f8c-117">Le tableau suivant affiche la progression de développement standard de HL7.</span><span class="sxs-lookup"><span data-stu-id="46f8c-117">The following table shows the HL7 standard development progression.</span></span>  
  
|<span data-ttu-id="46f8c-118">Événement</span><span class="sxs-lookup"><span data-stu-id="46f8c-118">Event</span></span>|<span data-ttu-id="46f8c-119">Année</span><span class="sxs-lookup"><span data-stu-id="46f8c-119">Year</span></span>|<span data-ttu-id="46f8c-120">Détails</span><span class="sxs-lookup"><span data-stu-id="46f8c-120">Details</span></span>|  
|-----------|----------|-------------|  
|<span data-ttu-id="46f8c-121">HL7 fondée</span><span class="sxs-lookup"><span data-stu-id="46f8c-121">HL7 Founded</span></span>|<span data-ttu-id="46f8c-122">1987</span><span class="sxs-lookup"><span data-stu-id="46f8c-122">1987</span></span>|<span data-ttu-id="46f8c-123">La première réunion dans Stanford, autorité de certification, inclus 12 participants.</span><span class="sxs-lookup"><span data-stu-id="46f8c-123">The first meeting, in Stanford, CA, included 12 attendees.</span></span>|  
|<span data-ttu-id="46f8c-124">V1.0</span><span class="sxs-lookup"><span data-stu-id="46f8c-124">V1.0</span></span>|<span data-ttu-id="46f8c-125">1987</span><span class="sxs-lookup"><span data-stu-id="46f8c-125">1987</span></span>|<span data-ttu-id="46f8c-126">Brouillon présenté à la réunion de pleine HL7.</span><span class="sxs-lookup"><span data-stu-id="46f8c-126">Draft presented to HL7 plenary meeting.</span></span>|  
|<span data-ttu-id="46f8c-127">V2.0</span><span class="sxs-lookup"><span data-stu-id="46f8c-127">V2.0</span></span>|<span data-ttu-id="46f8c-128">1988</span><span class="sxs-lookup"><span data-stu-id="46f8c-128">1988</span></span>|<span data-ttu-id="46f8c-129">Brouillon présenté à la réunion de pleine HL7.</span><span class="sxs-lookup"><span data-stu-id="46f8c-129">Draft presented to HL7 plenary meeting.</span></span>|  
|<span data-ttu-id="46f8c-130">V2.1 publié</span><span class="sxs-lookup"><span data-stu-id="46f8c-130">V2.1 published</span></span>|<span data-ttu-id="46f8c-131">1990</span><span class="sxs-lookup"><span data-stu-id="46f8c-131">1990</span></span>|<span data-ttu-id="46f8c-132">La première largement implémenté la version</span><span class="sxs-lookup"><span data-stu-id="46f8c-132">The first widely implemented version</span></span>|  
|<span data-ttu-id="46f8c-133">Version 2.2 publié</span><span class="sxs-lookup"><span data-stu-id="46f8c-133">V2.2 published</span></span>|<span data-ttu-id="46f8c-134">1994</span><span class="sxs-lookup"><span data-stu-id="46f8c-134">1994</span></span>||  
|<span data-ttu-id="46f8c-135">V.2.3 publié</span><span class="sxs-lookup"><span data-stu-id="46f8c-135">V.2.3 published</span></span>|<span data-ttu-id="46f8c-136">1997</span><span class="sxs-lookup"><span data-stu-id="46f8c-136">1997</span></span>|<span data-ttu-id="46f8c-137">ANSI approuvé</span><span class="sxs-lookup"><span data-stu-id="46f8c-137">ANSI approved</span></span>|  
|<span data-ttu-id="46f8c-138">V2.3.1 publié</span><span class="sxs-lookup"><span data-stu-id="46f8c-138">V2.3.1 published</span></span>|<span data-ttu-id="46f8c-139">1999</span><span class="sxs-lookup"><span data-stu-id="46f8c-139">1999</span></span>|<span data-ttu-id="46f8c-140">ANSI approuvé</span><span class="sxs-lookup"><span data-stu-id="46f8c-140">ANSI approved</span></span>|  
|<span data-ttu-id="46f8c-141">V2.4 publié</span><span class="sxs-lookup"><span data-stu-id="46f8c-141">V2.4 published</span></span>|<span data-ttu-id="46f8c-142">2000</span><span class="sxs-lookup"><span data-stu-id="46f8c-142">2000</span></span>|<span data-ttu-id="46f8c-143">ANSI approuvé</span><span class="sxs-lookup"><span data-stu-id="46f8c-143">ANSI approved</span></span>|  
|<span data-ttu-id="46f8c-144">Architecture de Document clinique</span><span class="sxs-lookup"><span data-stu-id="46f8c-144">Clinical Document Architecture</span></span>|<span data-ttu-id="46f8c-145">2000</span><span class="sxs-lookup"><span data-stu-id="46f8c-145">2000</span></span>|<span data-ttu-id="46f8c-146">ANSI approuvé</span><span class="sxs-lookup"><span data-stu-id="46f8c-146">ANSI approved</span></span>|  
|<span data-ttu-id="46f8c-147">2.5 publié</span><span class="sxs-lookup"><span data-stu-id="46f8c-147">V2.5 published</span></span>|<span data-ttu-id="46f8c-148">2003</span><span class="sxs-lookup"><span data-stu-id="46f8c-148">2003</span></span>|<span data-ttu-id="46f8c-149">Terminer l’approbation dans HL7, soumis à la norme ANSI pour approbation.</span><span class="sxs-lookup"><span data-stu-id="46f8c-149">Completed approval within HL7, submitted to ANSI for approval.</span></span>|  
|<span data-ttu-id="46f8c-150">Version 3.0 en cours</span><span class="sxs-lookup"><span data-stu-id="46f8c-150">V3.0 in progress</span></span>|<span data-ttu-id="46f8c-151">2003</span><span class="sxs-lookup"><span data-stu-id="46f8c-151">2003</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="46f8c-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46f8c-152">See Also</span></span>  
 <span data-ttu-id="46f8c-153">[Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="46f8c-153">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="46f8c-154">[L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="46f8c-154">[Using HL7 2.X Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md) </span></span>  
 <span data-ttu-id="46f8c-155">[Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="46f8c-155">[Using HL7 2.XML Schemas](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md) </span></span>  
 <span data-ttu-id="46f8c-156">[Modes de messages](../../adapters-and-accelerators/accelerator-hl7/message-modes.md) </span><span class="sxs-lookup"><span data-stu-id="46f8c-156">[Message Modes](../../adapters-and-accelerators/accelerator-hl7/message-modes.md) </span></span>  
 [<span data-ttu-id="46f8c-157">La messagerie HL7</span><span class="sxs-lookup"><span data-stu-id="46f8c-157">HL7 Messaging</span></span>](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)