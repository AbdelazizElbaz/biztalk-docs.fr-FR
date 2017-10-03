---
title: "Partie 2 : Dans lot scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, outbound batches
- batching, inbound batches
ms.assetid: 36b9d927-f5b7-4c1a-9163-9e79d17c3e9e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56ffac38676fe6b163a39ff06be5fe0538800d2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="part-2-batch-inbatch-out-scenario"></a><span data-ttu-id="faf1d-102">Partie 2 : Traitement par lots de dans / lots scénario</span><span class="sxs-lookup"><span data-stu-id="faf1d-102">Part 2: Batch In/Batch Out Scenario</span></span>
<span data-ttu-id="faf1d-103">Dans cette partie du didacticiel, vous recevez un fichier de commandes de HL7 encodé, transmettre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sans fragmentation et envoyez le fichier de commandes intactes à la destination.</span><span class="sxs-lookup"><span data-stu-id="faf1d-103">In this part of the tutorial, you receive an HL7-encoded batch file, pass it through [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] without fragmentation, and send the intact batch file to the destination.</span></span> <span data-ttu-id="faf1d-104">La figure suivante illustre le flux de ce processus, et la sous-section ci-dessous décrit le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="faf1d-104">The following figure shows the flow of this process, and the subsection below describes the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="faf1d-105">Avant de commencer cette partie du didacticiel, désactivez les outils MllpReceive et MllpSend que vous avez utilisé dans la partie 1, en fermant les invites de commandes.</span><span class="sxs-lookup"><span data-stu-id="faf1d-105">Before starting this part of the tutorial, turn off the MllpReceive and MllpSend tools that you used in Part 1, by closing the command prompts.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")  
  
 <span data-ttu-id="faf1d-106">**Le flux des messages dans le lot dans / lots scénario**</span><span class="sxs-lookup"><span data-stu-id="faf1d-106">**How messages flow in the Batch In/Batch Out scenario**</span></span>  
  
 <span data-ttu-id="faf1d-107">Ce scénario inclut le workflow suivant :</span><span class="sxs-lookup"><span data-stu-id="faf1d-107">This scenario includes the following workflow:</span></span>  
  
1.  <span data-ttu-id="faf1d-108">Le flux de travail commence quand une application métier-envoie un lot de messages à la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) en utilisant le protocole de fichier moteur d’intégration.</span><span class="sxs-lookup"><span data-stu-id="faf1d-108">The workflow begins when a line-of-business application sends a message batch to the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) Integration Engine using the FILE protocol.</span></span> <span data-ttu-id="faf1d-109">Le lot contient deux versions d’un ADT ^ A03 message.</span><span class="sxs-lookup"><span data-stu-id="faf1d-109">The batch contains two versions of an ADT^A03 message.</span></span> <span data-ttu-id="faf1d-110">L’application source appartient au tiers Tutorial_BatchSource.</span><span class="sxs-lookup"><span data-stu-id="faf1d-110">The source application belongs to the Tutorial_BatchSource party.</span></span>  
  
2.  <span data-ttu-id="faf1d-111">Le moteur d’intégration reçoit le lot sur un fichier de port de réception et valide le lot de messages.</span><span class="sxs-lookup"><span data-stu-id="faf1d-111">The Integration Engine receives the batch on a FILE receive port, and validates the message batch.</span></span> <span data-ttu-id="faf1d-112">(Le niveau de validation dépend des paramètres sélectionnés pour la partie de la source de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.)</span><span class="sxs-lookup"><span data-stu-id="faf1d-112">(The level of validation depends on settings selected for the source party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.)</span></span>  
  
3.  <span data-ttu-id="faf1d-113">Basé sur un paramètre dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Explorer de Configuration qui désactive la fragmentation de lot pour le tiers, le moteur d’Interface n’analyse pas le lot en messages individuels, mais laisse le lot en tant que lot.</span><span class="sxs-lookup"><span data-stu-id="faf1d-113">Based on a setting in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer that disables batch fragmentation for the party, the Interface Engine does not parse the batch into individual messages, but leaves the batch as a batch.</span></span> <span data-ttu-id="faf1d-114">Il valide les messages individuels, en fonction de paramètres sélectionnés pour le tiers source dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.</span><span class="sxs-lookup"><span data-stu-id="faf1d-114">It validates the individual messages, again based on settings selected for the source party in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer.</span></span>  
  
4.  <span data-ttu-id="faf1d-115">Le moteur de l’Interface génère un accusé de réception pour le message de lot, selon les paramètres de la définition d’accusé de réception dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] éditeur de Configuration pour le tiers.</span><span class="sxs-lookup"><span data-stu-id="faf1d-115">The Interface Engine generates an acknowledgment for the batch message, based on the acknowledgment definition settings in the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Editor for the party.</span></span> <span data-ttu-id="faf1d-116">Dans ce cas, vous sélectionnez le mode d’accusé de réception d’origine, afin du moteur de l’Interface génère un accusé de réception de Application accepter unique pour le lot de messages après la validation de l’en-tête de message et le corps.</span><span class="sxs-lookup"><span data-stu-id="faf1d-116">In this case, you select Original Acknowledgment mode, so the Interface Engine generates a single Application Accept acknowledgment for the message batch after validating both the message header and body.</span></span> <span data-ttu-id="faf1d-117">Le moteur génère l’accusé de réception en fonction du schéma ACK_024_GLO_DEF, passe à « AA » dans le champ MSA2 de l’accusé de réception, passe à des tiers de destination dans MSH3 et passe à la partie source dans MSH5.</span><span class="sxs-lookup"><span data-stu-id="faf1d-117">The engine builds the acknowledgment based on the ACK_024_GLO_DEF schema, enters "AA" in field MSA2 of the acknowledgment, enters the destination party in MSH3, and enters the source party in MSH5.</span></span>  
  
5.  <span data-ttu-id="faf1d-118">Les itinéraires de moteur d’Interface que le traitement de l’accusé de réception à la source de tiers via un fichier de l’adaptateur configuré pour traiter les accusés de réception d’envoi.</span><span class="sxs-lookup"><span data-stu-id="faf1d-118">The Interface Engine routes the acknowledgment batch to the source party through a FILE send adapter set up to process acknowledgments.</span></span> <span data-ttu-id="faf1d-119">Dans ce cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] achemine le lot dans le dossier \Tutorial_BatchACKDrop.</span><span class="sxs-lookup"><span data-stu-id="faf1d-119">In this case, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] routes the batch to the \Tutorial_BatchACKDrop folder.</span></span>  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="faf1d-120">envoie que le lot de messages à la destination spécifiée pour le tiers de destination, dans ce cas, le dossier \Tutorial_BTAHL7Drop.</span><span class="sxs-lookup"><span data-stu-id="faf1d-120"> sends the message batch to the destination specified for the destination party, in this case the folder \Tutorial_BTAHL7Drop.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="faf1d-121">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="faf1d-121">In This Section</span></span>  
  
-   [<span data-ttu-id="faf1d-122">Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans / hors du lot</span><span class="sxs-lookup"><span data-stu-id="faf1d-122">Step 1: Configure Party Information for Batch In/Batch Out</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-party-information-for-batch-in-batch-out.md)  
  
-   [<span data-ttu-id="faf1d-123">Étape 2 : Modifier ou créer l’envoi et Ports de réception</span><span class="sxs-lookup"><span data-stu-id="faf1d-123">Step 2: Modify or Create the Send and Receive Ports</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)  
  
-   [<span data-ttu-id="faf1d-124">Étape 3 : Tester le lot dans / lots scénario</span><span class="sxs-lookup"><span data-stu-id="faf1d-124">Step 3: Test the Batch In/Batch Out Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)