---
title: "Propriétés de contexte de message pour recevoir des IDOC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDOCs, message context properties for receiving
ms.assetid: fadb2284-2f55-49c2-bae9-95325f1be539
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca289e37cac15972e75c69d7ad20928b72911963
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-context-properties-for-receiving-idocs"></a><span data-ttu-id="279bf-102">Propriétés de contexte de message pour recevoir des IDOC</span><span class="sxs-lookup"><span data-stu-id="279bf-102">Message Context Properties for Receiving IDOCs</span></span>
<span data-ttu-id="279bf-103">Pour la réception d’un IDOC à l’aide de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les propriétés de contexte de message suivant.</span><span class="sxs-lookup"><span data-stu-id="279bf-103">For receiving an IDOC using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] supports the following message context properties.</span></span>  
  
 <span data-ttu-id="279bf-104">**Propriétés de l’enregistrement de contrôle IDOC.**</span><span class="sxs-lookup"><span data-stu-id="279bf-104">**IDOC Control Record properties.**</span></span>  
  
-   <span data-ttu-id="279bf-105">**TABNAM** -nom de la structure de table</span><span class="sxs-lookup"><span data-stu-id="279bf-105">**TABNAM** - Name of table structure</span></span>  
  
-   <span data-ttu-id="279bf-106">**SITUATION** -Client</span><span class="sxs-lookup"><span data-stu-id="279bf-106">**MANDT** - Client</span></span>  
  
-   <span data-ttu-id="279bf-107">**DOCNUM** -numéro IDOC</span><span class="sxs-lookup"><span data-stu-id="279bf-107">**DOCNUM** - IDOC number</span></span>  
  
-   <span data-ttu-id="279bf-108">**DOCREL** -version SAP pour IDOC</span><span class="sxs-lookup"><span data-stu-id="279bf-108">**DOCREL** - SAP Release for IDOC</span></span>  
  
-   <span data-ttu-id="279bf-109">**ÉTAT** -état de IDOC</span><span class="sxs-lookup"><span data-stu-id="279bf-109">**STATUS** - Status of IDOC</span></span>  
  
-   <span data-ttu-id="279bf-110">**DIRECT** -Direction</span><span class="sxs-lookup"><span data-stu-id="279bf-110">**DIRECT** - Direction</span></span>  
  
-   <span data-ttu-id="279bf-111">**OUTMOD** -mode de sortie</span><span class="sxs-lookup"><span data-stu-id="279bf-111">**OUTMOD** - Output mode</span></span>  
  
-   <span data-ttu-id="279bf-112">**EXPRSS** - substitution dans le traitement entrant</span><span class="sxs-lookup"><span data-stu-id="279bf-112">**EXPRSS** - Overriding in inbound processing</span></span>  
  
-   <span data-ttu-id="279bf-113">**TEST** -indicateur de Test</span><span class="sxs-lookup"><span data-stu-id="279bf-113">**TEST** - Test flag</span></span>  
  
-   <span data-ttu-id="279bf-114">**IDOCTYP** -nom du type de base</span><span class="sxs-lookup"><span data-stu-id="279bf-114">**IDOCTYP** - Name of basic type</span></span>  
  
-   <span data-ttu-id="279bf-115">**CIMTYP** -Extension (défini par le client)</span><span class="sxs-lookup"><span data-stu-id="279bf-115">**CIMTYP** - Extension (defined by customer)</span></span>  
  
-   <span data-ttu-id="279bf-116">**MESTYP** -type de Message</span><span class="sxs-lookup"><span data-stu-id="279bf-116">**MESTYP** - Message type</span></span>  
  
-   <span data-ttu-id="279bf-117">**MESCOD** -code de Message</span><span class="sxs-lookup"><span data-stu-id="279bf-117">**MESCOD** - Message code</span></span>  
  
-   <span data-ttu-id="279bf-118">**MESFCT** -Message (fonction)</span><span class="sxs-lookup"><span data-stu-id="279bf-118">**MESFCT** - Message function</span></span>  
  
-   <span data-ttu-id="279bf-119">**STD** -indicateur de standard, EDI</span><span class="sxs-lookup"><span data-stu-id="279bf-119">**STD** - EDI standard, flag</span></span>  
  
-   <span data-ttu-id="279bf-120">**STDVRS** -EDI standard, version et mise en production</span><span class="sxs-lookup"><span data-stu-id="279bf-120">**STDVRS** - EDI standard, version and release</span></span>  
  
-   <span data-ttu-id="279bf-121">**STDMES** -type de message EDI</span><span class="sxs-lookup"><span data-stu-id="279bf-121">**STDMES** - EDI message type</span></span>  
  
-   <span data-ttu-id="279bf-122">**SNDPOR** -port de l’expéditeur (système SAP, sous-système externe)</span><span class="sxs-lookup"><span data-stu-id="279bf-122">**SNDPOR** - Sender port (SAP System, external subsystem)</span></span>  
  
-   <span data-ttu-id="279bf-123">**SNDPRT** -type d’expéditeur du partenaire</span><span class="sxs-lookup"><span data-stu-id="279bf-123">**SNDPRT** - Partner type of sender</span></span>  
  
-   <span data-ttu-id="279bf-124">**SNDPFC** -partenaire de l’expéditeur (fonction)</span><span class="sxs-lookup"><span data-stu-id="279bf-124">**SNDPFC** - Partner Function of Sender</span></span>  
  
-   <span data-ttu-id="279bf-125">**SNDPRN** -nombre de l’expéditeur du partenaire</span><span class="sxs-lookup"><span data-stu-id="279bf-125">**SNDPRN** - Partner Number of Sender</span></span>  
  
-   <span data-ttu-id="279bf-126">**SNDSAD** -adresse d’expéditeur (SADR)</span><span class="sxs-lookup"><span data-stu-id="279bf-126">**SNDSAD** - Sender address (SADR)</span></span>  
  
-   <span data-ttu-id="279bf-127">**SNDLAD** -adresse logique d’expéditeur</span><span class="sxs-lookup"><span data-stu-id="279bf-127">**SNDLAD** - Logical address of sender</span></span>  
  
-   <span data-ttu-id="279bf-128">**RCVPOR** -port de réception</span><span class="sxs-lookup"><span data-stu-id="279bf-128">**RCVPOR** - Receiver port</span></span>  
  
-   <span data-ttu-id="279bf-129">**RCVPRT** -Type de partenaire du récepteur</span><span class="sxs-lookup"><span data-stu-id="279bf-129">**RCVPRT** - Partner Type of receiver</span></span>  
  
-   <span data-ttu-id="279bf-130">**RCVPFC** -partenaire du destinataire (fonction)</span><span class="sxs-lookup"><span data-stu-id="279bf-130">**RCVPFC** - Partner function of recipient</span></span>  
  
-   <span data-ttu-id="279bf-131">**RCVPRN** -numéro du destinataire de partenaire</span><span class="sxs-lookup"><span data-stu-id="279bf-131">**RCVPRN** - Partner number of recipient</span></span>  
  
-   <span data-ttu-id="279bf-132">**RCVSAD** -l’adresse du destinataire (SADR)</span><span class="sxs-lookup"><span data-stu-id="279bf-132">**RCVSAD** - Recipient address (SADR)</span></span>  
  
-   <span data-ttu-id="279bf-133">**RCVLAD** -adresse logique du destinataire</span><span class="sxs-lookup"><span data-stu-id="279bf-133">**RCVLAD** - Logical address of recipient</span></span>  
  
-   <span data-ttu-id="279bf-134">**CREDAT** - créé sur</span><span class="sxs-lookup"><span data-stu-id="279bf-134">**CREDAT** - Created on</span></span>  
  
-   <span data-ttu-id="279bf-135">**CRETIM** -heure de création</span><span class="sxs-lookup"><span data-stu-id="279bf-135">**CRETIM** - Time Created</span></span>  
  
-   <span data-ttu-id="279bf-136">**REFINT** -fichier de Transmission (échange EDI)</span><span class="sxs-lookup"><span data-stu-id="279bf-136">**REFINT** - Transmission file (EDI Interchange)</span></span>  
  
-   <span data-ttu-id="279bf-137">**REFGRP** -groupe de messages (groupe de messages EDI)</span><span class="sxs-lookup"><span data-stu-id="279bf-137">**REFGRP** - Message group (EDI Message Group)</span></span>  
  
-   <span data-ttu-id="279bf-138">**REFMES** -Message (Message EDI)</span><span class="sxs-lookup"><span data-stu-id="279bf-138">**REFMES** - Message (EDI Message)</span></span>  
  
-   <span data-ttu-id="279bf-139">**ARCKEY** - Key pour l’archivage de message externe</span><span class="sxs-lookup"><span data-stu-id="279bf-139">**ARCKEY** - Key for external message archive</span></span>  
  
-   <span data-ttu-id="279bf-140">**SÉRIE** -sérialisation</span><span class="sxs-lookup"><span data-stu-id="279bf-140">**SERIAL** - Serialization</span></span>  
  
-   <span data-ttu-id="279bf-141">**DOCTYP** -type IDOC (il est disponible dans EDI_DC uniquement.</span><span class="sxs-lookup"><span data-stu-id="279bf-141">**DOCTYP** - IDOC type (This is available in EDI_DC only.</span></span> <span data-ttu-id="279bf-142">Doit être présent dans la propriété de contexte, mais doit être promu uniquement pour la Version 2 IDOC)</span><span class="sxs-lookup"><span data-stu-id="279bf-142">Should be present in the context property but should be promoted for Version 2 IDOCs only)</span></span>  
  
 <span data-ttu-id="279bf-143">**TID** – représente le TID envoyé par le système SAP pour l’appel entrant TRFC.</span><span class="sxs-lookup"><span data-stu-id="279bf-143">**TID** – Represents the TID sent by the SAP system for the incoming TRFC call.</span></span>  
  
 <span data-ttu-id="279bf-144">**GUID** – représente le GUID qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise en interne.</span><span class="sxs-lookup"><span data-stu-id="279bf-144">**GUID** – Represents the GUID which the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses internally.</span></span> <span data-ttu-id="279bf-145">Cela a un mappage avec le TID qui a été reçu à partir du système SAP.</span><span class="sxs-lookup"><span data-stu-id="279bf-145">This has a one-to-one mapping with the TID which was received from the SAP system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="279bf-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="279bf-146">See Also</span></span>  
 [<span data-ttu-id="279bf-147">Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="279bf-147">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)