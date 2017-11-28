---
title: "FRR emplacement de réception pour les Messages à partir de SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, receive locations
- receive locations, FRR
ms.assetid: d15989de-56f9-4d62-8394-f4fd6e971495
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d609cfc8c5177581f32ee0957a6a7ae7c1fe9a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-receive-location-for-messages-from-swift"></a><span data-ttu-id="c0e76-102">FRR emplacement de réception pour les Messages à partir de SWIFT</span><span class="sxs-lookup"><span data-stu-id="c0e76-102">FRR Receive Location for Messages from SWIFT</span></span>
<span data-ttu-id="c0e76-103">Pour activer le rapprochement de réponse FIN (FRR), vous devez configurer un FRR composant de pipeline pour recevoir un message de SAA et la préparer pour le traitement par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0e76-103">To enable FIN response reconciliation (FRR), you must set up an FRR receive pipeline component to receive a message from SAA and prepare it for processing by [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span> <span data-ttu-id="c0e76-104">Le pipeline de réception contient les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="c0e76-104">The receive pipeline contains the following components:</span></span>  
  
-   <span data-ttu-id="c0e76-105">Le désassembleur SWIFT dans la phase de désassemblage</span><span class="sxs-lookup"><span data-stu-id="c0e76-105">The SWIFT disassembler in the Disassemble stage</span></span>  
  
-   <span data-ttu-id="c0e76-106">Le composant de pipeline décodeur de FRR SWIFT à l’étape de décodeur</span><span class="sxs-lookup"><span data-stu-id="c0e76-106">The SWIFT FRR Decoder pipeline component in the Decoder stage</span></span>  
  
-   <span data-ttu-id="c0e76-107">Le composant de pipeline Résolution de l’ensemblecorrélations FRR SWIFT dans la phase de résolution de tiers</span><span class="sxs-lookup"><span data-stu-id="c0e76-107">The SWIFT FRR CorrelationSet Resolver pipeline component in the Party Resolution stage</span></span>  
  
 <span data-ttu-id="c0e76-108">Lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] reçoit une panoramique/NAN, SWIFT FRR décodeur lit la propriété de contexte MQ commentaires pour déterminer si la réponse est un panoramique ou une valeur NAN.</span><span class="sxs-lookup"><span data-stu-id="c0e76-108">When [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives a PAN/NAN, SWIFT FRR Decoder reads the MQ Feedback context property to determine whether the response is a PAN or a NAN.</span></span> <span data-ttu-id="c0e76-109">Il définit le transport indépendant [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRTransportLevelAck booléen valeurs True pour un panoramique ou la valeur false pour une valeur NAN.</span><span class="sxs-lookup"><span data-stu-id="c0e76-109">It sets the transport-agnostic [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRTransportLevelAck Boolean values to true for a PAN or false for a NAN.</span></span>  
  
 <span data-ttu-id="c0e76-110">Le composant de pipeline Résolution de l’ensemblecorrélations SWIFT FRR remplace la propriété du message de réponse FRRCorrelationToken, qui utilise de l’orchestration FRR, avec la valeur dans la MQMD. Propriété de CorrelId.</span><span class="sxs-lookup"><span data-stu-id="c0e76-110">The SWIFT FRR CorrelationSet Resolver pipeline component overwrites the response message's FRRCorrelationToken property, which the FRR orchestration uses, with the value in the MQMD.CorrelId property.</span></span>