---
title: Prise en charge EDI | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d4f50a9-fc55-400c-a63c-40b697425fea
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04cd9c14b9c3663bdf332155cc9824e1681ca7a6
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="edi-support-in-biztalk-server"></a><span data-ttu-id="e1110-102">Prise en charge d'EDI dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="e1110-102">EDI Support in BizTalk Server</span></span>
<span data-ttu-id="e1110-103">EDI est intégré à BizTalk Server et est un composant facultatif lorsque vous installez et configurez BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e1110-103">EDI is built-in to BizTalk Server, and is an optional component when you install and configure BizTalk Server.</span></span> 
  
## <a name="feature-set-comparison-chart"></a><span data-ttu-id="e1110-104">Tableau comparatif des fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="e1110-104">Feature Set Comparison Chart</span></span>  
 <span data-ttu-id="e1110-105">Le tableau suivant présente la prise en charge EDI inclus dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e1110-105">The following table shows the EDI support included with BizTalk Server.</span></span>
  
|<span data-ttu-id="e1110-106">Fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="e1110-106">Feature</span></span>|<span data-ttu-id="e1110-107">Commentaire</span><span class="sxs-lookup"><span data-stu-id="e1110-107">Comment</span></span>|  
|---|---|
|<span data-ttu-id="e1110-108">Modification du Segment ISA au jeu de transactions</span><span class="sxs-lookup"><span data-stu-id="e1110-108">ISA    Segment modification at transaction set</span></span>| <span data-ttu-id="e1110-109">Créer des accords spécifiques</span><span class="sxs-lookup"><span data-stu-id="e1110-109">Create TransactionSet-specific agreements</span></span>|  
|<span data-ttu-id="e1110-110">ISA11 : US ou autre type de standard</span><span class="sxs-lookup"><span data-stu-id="e1110-110">ISA11:    US or other standard type</span></span>| |  
|<span data-ttu-id="e1110-111">ISA12 : Version de contrôle d’échange</span><span class="sxs-lookup"><span data-stu-id="e1110-111">ISA12:    Interchange Control Version</span></span>| |  
|<span data-ttu-id="e1110-112">ISA13 : Numéro de contrôle d’échange (incrémentation d’un nombre)</span><span class="sxs-lookup"><span data-stu-id="e1110-112">ISA13:    Interchange Control Number (incrementing number)</span></span>| |  
|<span data-ttu-id="e1110-113">ISA15 : Test ou Production</span><span class="sxs-lookup"><span data-stu-id="e1110-113">ISA15:    Test or Production</span></span>| |  
|<span data-ttu-id="e1110-114">Modification du Segment GS au niveau du document/de la transaction</span><span class="sxs-lookup"><span data-stu-id="e1110-114">GS    Segment modification at document/transaction level</span></span>| |  
|<span data-ttu-id="e1110-115">GS expéditeur/destinataire GS différents de ISA</span><span class="sxs-lookup"><span data-stu-id="e1110-115">GS    sender/receiver IDs allowed to be different than ISA</span></span>| |  
|<span data-ttu-id="e1110-116">ID de Document entrants différents ISA et GS sortants</span><span class="sxs-lookup"><span data-stu-id="e1110-116">Inbound    Document IDs different than ISA & GS Outbound IDs</span></span>| |  
|<span data-ttu-id="e1110-117">GS01 : Possibilité de modifier le type de document</span><span class="sxs-lookup"><span data-stu-id="e1110-117">GS01:    Ability to change type of document</span></span>| |  
|<span data-ttu-id="e1110-118">GS04 : Date (possibilité de modifier le format)</span><span class="sxs-lookup"><span data-stu-id="e1110-118">GS04:    Date (Ability to change format)</span></span>|<span data-ttu-id="e1110-119">Contient l’interface utilisateur pour sélectionner les formats SSAAMMJJ et aammjj</span><span class="sxs-lookup"><span data-stu-id="e1110-119">Contains UI to select format as CCYYMMDD and YYMMDD</span></span>|  
|<span data-ttu-id="e1110-120">GS05 : Heure (possibilité de modifier le format)</span><span class="sxs-lookup"><span data-stu-id="e1110-120">GS05:    Time (Ability to change format)</span></span>|<span data-ttu-id="e1110-121">Contient l’interface utilisateur pour sélectionner les formats HHMM, HHMMSS et Hhmmssjj</span><span class="sxs-lookup"><span data-stu-id="e1110-121">Contains UI to select format as HHMM, HHMMSS, and HHMMSSdd</span></span>|  
|<span data-ttu-id="e1110-122">GS06 : Modifier le numéro de contrôle</span><span class="sxs-lookup"><span data-stu-id="e1110-122">GS06:    Change the control number</span></span>| |  
|<span data-ttu-id="e1110-123">GS07 : Code d’agence</span><span class="sxs-lookup"><span data-stu-id="e1110-123">GS07:    Agency Code</span></span>| |  
|<span data-ttu-id="e1110-124">GS08 : Peut placer dans la version de norme</span><span class="sxs-lookup"><span data-stu-id="e1110-124">GS08:    Able to put in standards version</span></span>| |  
|<span data-ttu-id="e1110-125">possibilité de remplacer l'enveloppe EDI au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="e1110-125">Ability to override EDI envelope at runtime</span></span>| |  
|<span data-ttu-id="e1110-126">Schémas EDI personnalisés</span><span class="sxs-lookup"><span data-stu-id="e1110-126">Custom    EDI Schemas</span></span>| |  
|<span data-ttu-id="e1110-127">Paramètre organisation/tiers</span><span class="sxs-lookup"><span data-stu-id="e1110-127">Organization/Party Setting</span></span>|<span data-ttu-id="e1110-128">Créer des tiers distinct des accords.</span><span class="sxs-lookup"><span data-stu-id="e1110-128">Create separate party and agreements.</span></span> <span data-ttu-id="e1110-129">Également créer des modèles d’accords.</span><span class="sxs-lookup"><span data-stu-id="e1110-129">Also create agreements based off templates.</span></span>|  
|<span data-ttu-id="e1110-130">Document EDI routage via la définition de document</span><span class="sxs-lookup"><span data-stu-id="e1110-130">EDI    document routing via document definition</span></span>| |  
|<span data-ttu-id="e1110-131">Automatique 997 aux partenaires commerciaux</span><span class="sxs-lookup"><span data-stu-id="e1110-131">Automatic 997’s to trading partners</span></span>|<span data-ttu-id="e1110-132">Configuration spécifique des profils d’entreprise</span><span class="sxs-lookup"><span data-stu-id="e1110-132">Configuration specific to business profiles</span></span>|  
|<span data-ttu-id="e1110-133">Sortant EDI fiables sortants via 997</span><span class="sxs-lookup"><span data-stu-id="e1110-133">Outbound    EDI reliable messaging via 997’s</span></span>| |  
|<span data-ttu-id="e1110-134">Prise en charge d’EDIFACT</span><span class="sxs-lookup"><span data-stu-id="e1110-134">EDIFACT    Support</span></span>|<span data-ttu-id="e1110-135">Prend en charge D93 à D05 par ISO 9735 v4.1</span><span class="sxs-lookup"><span data-stu-id="e1110-135">Supports D93 to D05 per ISO 9735 v4.1</span></span>|  
|<span data-ttu-id="e1110-136">X12    Support</span><span class="sxs-lookup"><span data-stu-id="e1110-136">X12    Support</span></span>|<span data-ttu-id="e1110-137">2040 à 5030</span><span class="sxs-lookup"><span data-stu-id="e1110-137">2040 to 5030</span></span>|  
|<span data-ttu-id="e1110-138">Prise en charge de HIPAA</span><span class="sxs-lookup"><span data-stu-id="e1110-138">HIPAA support</span></span>| <span data-ttu-id="e1110-139">Microsoft BizTalk Accelerator pour HIPAA (BTAHIPAA) dans le cadre de la fonctionnalité EDI native</span><span class="sxs-lookup"><span data-stu-id="e1110-139">Microsoft BizTalk Accelerator for HIPAA (BTAHIPAA) as  part of native EDI functionality</span></span>|  
|<span data-ttu-id="e1110-140">Possibilité de supprimer les énumérateurs/CodeList</span><span class="sxs-lookup"><span data-stu-id="e1110-140">Ability to remove enumerators/codelists</span></span>|<span data-ttu-id="e1110-141">Utilisez Visual Studio / l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e1110-141">Use Visual Studio/BizTalk Editor</span></span>|  
|<span data-ttu-id="e1110-142">AS2 Envoi/réception</span><span class="sxs-lookup"><span data-stu-id="e1110-142">AS2    Send/Receive</span></span>| <span data-ttu-id="e1110-143">AS2 est certifiée par Drummond pour la prise en charge des pièces jointes, support de conservation de nom de fichier et l’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="e1110-143">AS2 is Drummond Certified for multi-file attachment support, file name preservation support and interoperability.</span></span>|  
|<span data-ttu-id="e1110-144">Conservation des noms de fichier AS2</span><span class="sxs-lookup"><span data-stu-id="e1110-144">AS2 file name preservation</span></span>| |  
|<span data-ttu-id="e1110-145">Messages fiables AS2</span><span class="sxs-lookup"><span data-stu-id="e1110-145">AS2 reliable messaging</span></span>| |  
|<span data-ttu-id="e1110-146">Traitement par lot sortant (accumulation de plusieurs types de transactions dans une transaction unique)</span><span class="sxs-lookup"><span data-stu-id="e1110-146">Outbound    Batching (accumulating multiple transaction types in a single transaction)</span></span>|<span data-ttu-id="e1110-147">Prend en charge plusieurs configurations de lot pour chaque profil d’entreprise</span><span class="sxs-lookup"><span data-stu-id="e1110-147">Supports multiple batch configurations for each business profile</span></span>|  
|<span data-ttu-id="e1110-148">Trafic entrant de traitement par lot : échange XML (en conservant un échange « traité par lot » entrant) ou XML de document informatisé basée sur les options de configuration</span><span class="sxs-lookup"><span data-stu-id="e1110-148">Inbound    Batching – Interchange XML (preserving an incoming ‘batched’ interchange) or Transaction Set XML based off configuration options</span></span>|<span data-ttu-id="e1110-149">Prend également en charge le trafic entrant décomposition, fractionner l’échange en individuels XML de document informatisé</span><span class="sxs-lookup"><span data-stu-id="e1110-149">Also supports inbound-debatching, i.e., splitting interchange into individual Transaction Set Xml</span></span>|  
|<span data-ttu-id="e1110-150">Échange et Transaction défini génération et Validation au moment du Design dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e1110-150">Interchange    and Transaction Set Generation and Validation in Design Time in Visual Studio</span></span>| |  
|<span data-ttu-id="e1110-151">Rapprochement et la génération TA1 (accusé de réception technique)</span><span class="sxs-lookup"><span data-stu-id="e1110-151">TA1    (Technical ACK) Generation and Reconciliation</span></span>| |  
|<span data-ttu-id="e1110-152">Indicateurs de Validation facultatif EDI et XSD</span><span class="sxs-lookup"><span data-stu-id="e1110-152">Optional    EDI and XSD Validation flags</span></span>| |  
|<span data-ttu-id="e1110-153">Format de document/définition au niveau GS</span><span class="sxs-lookup"><span data-stu-id="e1110-153">Document    format/definition at GS level</span></span>| |  
  
## <a name="see-also"></a><span data-ttu-id="e1110-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1110-154">See Also</span></span>  
 <span data-ttu-id="e1110-155">[Prise en charge des normes EDI](../core/edi-standards-support.md) </span><span class="sxs-lookup"><span data-stu-id="e1110-155">[EDI Standards Support](../core/edi-standards-support.md) </span></span>  
 <span data-ttu-id="e1110-156">[Prise en charge des schémas de Document EDI](../core/edi-document-schema-support.md) </span><span class="sxs-lookup"><span data-stu-id="e1110-156">[EDI Document Schema Support](../core/edi-document-schema-support.md) </span></span>  
 [<span data-ttu-id="e1110-157">Prise en charge du jeu de caractères EDI</span><span class="sxs-lookup"><span data-stu-id="e1110-157">EDI Character Set Support</span></span>](../core/edi-character-set-support.md)