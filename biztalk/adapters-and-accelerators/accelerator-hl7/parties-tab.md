---
title: "Onglet de parties de l’accélérateur HL7 dans BizTalk Server | Documents Microsoft"
description: "Utilisez l’Explorateur de Configuration de BTAHL7 pour afficher des parties existantes et configurer des accusés de réception dans BizTalk Server"
ms.custom: 
ms.date: 08/14/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e01052c8-25c5-4736-8403-33f16fbd3fb7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d8572da051d046d46b6e895f11f07d3f9d9771c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="parties-in-btahl7-configuration-explorer"></a><span data-ttu-id="26b4b-103">Parties dans l’Explorateur de Configuration BTAHL7</span><span class="sxs-lookup"><span data-stu-id="26b4b-103">Parties in BTAHL7 Configuration Explorer</span></span>
<span data-ttu-id="26b4b-104">Vous utilisez la **Parties** onglet pour afficher les parties disponibles et spécifier [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration d’un tiers spécifique que vous choisissez et pour configurer les propriétés pour les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="26b4b-104">You use the **Parties** tab to view the available parties and specify [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration for a particular party that you choose, and to configure properties for acknowledgments.</span></span> 

## <a name="parties-ui-explained"></a><span data-ttu-id="26b4b-105">Expliqué des parties de l’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="26b4b-105">Parties UI explained</span></span>
<span data-ttu-id="26b4b-106">Le **Parties** onglet contient un volet de gauche et droit.</span><span class="sxs-lookup"><span data-stu-id="26b4b-106">The **Parties** tab contains both a left and right pane.</span></span> <span data-ttu-id="26b4b-107">Les parties disponibles s’affichent dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="26b4b-107">The available parties appear in the left pane.</span></span> <span data-ttu-id="26b4b-108">Le volet de droite contient les onglets suivants pour la partie sélectionnée :</span><span class="sxs-lookup"><span data-stu-id="26b4b-108">The right pane contains the following tabs for the selected party:</span></span>  
  
-   <span data-ttu-id="26b4b-109">**Alias de tiers**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-109">**Party Aliases**.</span></span> <span data-ttu-id="26b4b-110">Utilisez cet onglet pour afficher des informations sur le tiers que vous avez sélectionné dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="26b4b-110">Use this tab to view information about the party you have selected from the left pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26b4b-111">Vous utilisez l’Explorateur BizTalk pour créer des parties.</span><span class="sxs-lookup"><span data-stu-id="26b4b-111">You use BizTalk Explorer to create parties.</span></span>  
  
-   <span data-ttu-id="26b4b-112">**Définition du lot**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-112">**Batch Definition**.</span></span> <span data-ttu-id="26b4b-113">Utilisez cet onglet pour configurer [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="26b4b-113">Use this tab to configure [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batching.</span></span>  
  
-   <span data-ttu-id="26b4b-114">**Planification du lot**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-114">**Batch Schedule**.</span></span> <span data-ttu-id="26b4b-115">Utilisez cet onglet pour activer les lots sortants.</span><span class="sxs-lookup"><span data-stu-id="26b4b-115">Use this tab to activate outbound batches.</span></span>  
  
-   <span data-ttu-id="26b4b-116">**Accusé de réception**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-116">**Acknowledgment**.</span></span> <span data-ttu-id="26b4b-117">Utilisez cet onglet pour spécifier les propriétés pour les accusés de réception entrants et générés.</span><span class="sxs-lookup"><span data-stu-id="26b4b-117">Use this tab to specify the properties for inbound and generated acknowledgments.</span></span>  
  
-   <span data-ttu-id="26b4b-118">**Validation**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-118">**Validation**.</span></span> <span data-ttu-id="26b4b-119">Utilisez cet onglet pour sélectionner les options de validation de message pour les messages entrants et générés.</span><span class="sxs-lookup"><span data-stu-id="26b4b-119">Use this tab to select the message validation options for inbound and generated messages.</span></span>  
  
-   <span data-ttu-id="26b4b-120">**Mappage de MSH**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-120">**MSH Map**.</span></span> <span data-ttu-id="26b4b-121">Utilisez cet onglet pour activer les transformations d’en-tête de message pour les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="26b4b-121">Use this tab to enable message header transformations for inbound messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="26b4b-122">Vous devez configurer les alias des tiers, définitions de traitement par lots, les planifications de traitement par lots et les informations d’accusé de réception pour tous les partenaires commerciaux.</span><span class="sxs-lookup"><span data-stu-id="26b4b-122">You must configure party aliases, batch definitions, batch schedules, and acknowledgment information for all trading parties.</span></span>  
    > 
    >  <span data-ttu-id="26b4b-123">Vous pouvez actualiser la liste des parties en appuyant sur F5 ou en cliquant sur la liste de parties et sélectionnez **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="26b4b-123">You can refresh the parties list by pressing F5, or by right-clicking the parties list, and select **Refresh**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="26b4b-124">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="26b4b-124">Next steps</span></span>  
  
-   [<span data-ttu-id="26b4b-125">Onglet alias de tiers</span><span class="sxs-lookup"><span data-stu-id="26b4b-125">Party Aliases Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/party-aliases-tab.md)  
  
-   [<span data-ttu-id="26b4b-126">Onglet de définition de lot</span><span class="sxs-lookup"><span data-stu-id="26b4b-126">Batch Definition Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/batch-definition-tab.md)  
  
-   [<span data-ttu-id="26b4b-127">Onglet Planification de traitement par lots</span><span class="sxs-lookup"><span data-stu-id="26b4b-127">Batch Schedule Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/batch-schedule-tab.md)  
  
-   [<span data-ttu-id="26b4b-128">Onglet d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="26b4b-128">Acknowledgment Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-tab.md)  
  
-   [<span data-ttu-id="26b4b-129">Onglet validation</span><span class="sxs-lookup"><span data-stu-id="26b4b-129">Validation Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/validation-tab.md)  
  
-   [<span data-ttu-id="26b4b-130">Onglet MSH</span><span class="sxs-lookup"><span data-stu-id="26b4b-130">MSH Map Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-map-tab.md)