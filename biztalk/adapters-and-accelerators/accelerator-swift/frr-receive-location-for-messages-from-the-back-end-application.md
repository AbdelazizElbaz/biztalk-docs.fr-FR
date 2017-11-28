---
title: "FRR emplacement de réception pour les Messages à partir de l’Application Back-End | Documents Microsoft"
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
ms.assetid: da0ad616-800f-493f-822f-eca1224722ab
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41d50f83feceac0238742cd474f70ecc1449f906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-receive-location-for-messages-from-the-back-end-application"></a><span data-ttu-id="e13e7-102">FRR emplacement de réception pour les Messages à partir de l’Application Back-End.</span><span class="sxs-lookup"><span data-stu-id="e13e7-102">FRR Receive Location for Messages from the Back-End Application</span></span>
<span data-ttu-id="e13e7-103">Pour activer le rapprochement de réponse FIN (FRR), vous devez configurer un FRR emplacement de réception qui reçoit les messages de l’application principale et de les achemine vers la MessageBox de BizTalk pour la consommation par l’orchestration FRR.</span><span class="sxs-lookup"><span data-stu-id="e13e7-103">To enable FIN response reconciliation (FRR), you must set up an FRR receive location that receives messages from the back-end application and routes them to the BizTalk MessageBox for consumption by the FRR orchestration.</span></span> <span data-ttu-id="e13e7-104">L’emplacement de réception achemine un message via un pipeline de réception FRR personnalisé que vous devez créer avec les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="e13e7-104">The receive location routes a message through a custom FRR receive pipeline that you must create with the following pipeline components:</span></span>  
  
-   <span data-ttu-id="e13e7-105">Le désassembleur SWIFT dans la phase de désassemblage</span><span class="sxs-lookup"><span data-stu-id="e13e7-105">The SWIFT disassembler in the Disassemble stage</span></span>  
  
-   <span data-ttu-id="e13e7-106">Le composant de pipeline décodeur de FRR SWIFT à l’étape de décodeur</span><span class="sxs-lookup"><span data-stu-id="e13e7-106">The SWIFT FRR Decoder pipeline component in the Decoder stage</span></span>  
  
-   <span data-ttu-id="e13e7-107">Le composant de pipeline Résolution de l’ensemblecorrélations FRR SWIFT dans la phase de résolution de tiers</span><span class="sxs-lookup"><span data-stu-id="e13e7-107">The SWIFT FRR CorrelationSet Resolver pipeline component in the Party Resolution stage</span></span>  
  
 <span data-ttu-id="e13e7-108">Le port de réception traite les messages qui ont [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed == False et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND == True.</span><span class="sxs-lookup"><span data-stu-id="e13e7-108">The receive port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True.</span></span> <span data-ttu-id="e13e7-109">Le mécanisme de transport est tout ce qui détermine l’application principale.</span><span class="sxs-lookup"><span data-stu-id="e13e7-109">The transport mechanism is whatever the back-end application dictates.</span></span>  
  
 <span data-ttu-id="e13e7-110">Ce port de réception utilise le même pipeline de réception personnalisé qui est utilisé par l’emplacement de réception pour les messages SWIFT.</span><span class="sxs-lookup"><span data-stu-id="e13e7-110">This receive port uses the same custom receive pipeline that is used by the receive location for messages from SWIFT.</span></span> <span data-ttu-id="e13e7-111">Toutefois, le pipeline effectue des fonctions différentes pour les deux emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="e13e7-111">However, the pipeline performs different functions for the two receive locations.</span></span> <span data-ttu-id="e13e7-112">Dans l’emplacement de réception des messages à partir de l’application principale, le composant de pipeline Résolution de l’ensemblecorrélations SWIFT FRR initialise le jeton de corrélation.</span><span class="sxs-lookup"><span data-stu-id="e13e7-112">In the receive location for messages from the back-end application, the SWIFT FRR CorrelationSet Resolver pipeline component initializes the correlation token.</span></span>