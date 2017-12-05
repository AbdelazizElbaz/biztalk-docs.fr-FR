---
title: Les Pipelines RNIF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RNIF, pipelines
- pipelines, RNIF
ms.assetid: 6cf480fe-6b54-4b13-8318-617f3bba71d0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cfdc50906f356a7eceeea50dd716c903720f785
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="rnif-pipelines"></a><span data-ttu-id="340b0-102">Pipelines RNIF</span><span class="sxs-lookup"><span data-stu-id="340b0-102">RNIF Pipelines</span></span>
<span data-ttu-id="340b0-103">Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] recevoir et envoyer les pipelines effectuent le traitement nécessaire pour recevoir ou envoyer des messages de Framework RNIF (RosettaNet Implementation).</span><span class="sxs-lookup"><span data-stu-id="340b0-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] receive and send pipelines perform the processing required for receive or send RosettaNet Implementation Framework (RNIF) messages.</span></span> <span data-ttu-id="340b0-104">Ce traitement inclut le prétraitement, codage/décodage, déchiffrement et le cryptage, montage/démontage et l’authentification de tiers.</span><span class="sxs-lookup"><span data-stu-id="340b0-104">This processing includes preprocessing, decoding/encoding, decrypting/encrypting, disassembly/assembly, and party authentication.</span></span>  
  
## <a name="pipeline-files"></a><span data-ttu-id="340b0-105">Fichiers de pipeline</span><span class="sxs-lookup"><span data-stu-id="340b0-105">Pipeline Files</span></span>  
 <span data-ttu-id="340b0-106">Standard [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] recevoir et envoyer des pipelines ne traitent pas les messages RNIF en mode natif.</span><span class="sxs-lookup"><span data-stu-id="340b0-106">Standard [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] receive and send pipelines do not process RNIF messages natively.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="340b0-107">a ajouté personnalisée de réception et pipelines d’envoi à cet effet.</span><span class="sxs-lookup"><span data-stu-id="340b0-107"> has added custom receive and send pipelines for this purpose.</span></span> <span data-ttu-id="340b0-108">Ces pipelines sont construits sur la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines, mais ajouter [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]-les capacités de traitement spécifique.</span><span class="sxs-lookup"><span data-stu-id="340b0-108">These pipelines are built on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines, but add [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]-specific processing capability.</span></span> <span data-ttu-id="340b0-109">Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipelines (RNIFReceive.btp et RNIFSend.btp) sont disponibles dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK à l’adresse \< *lecteur*\>: \Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span><span class="sxs-lookup"><span data-stu-id="340b0-109">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipelines (RNIFReceive.btp and RNIFSend.btp) are available in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK at \<*drive*\>:\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines.</span></span> <span data-ttu-id="340b0-110">Cela vous permet de les personnaliser selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="340b0-110">This lets you customize them for your own purposes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="340b0-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="340b0-111">See Also</span></span>  
 <span data-ttu-id="340b0-112">[Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="340b0-112">[BTARN Receive Pipeline](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md) </span></span>  
 [<span data-ttu-id="340b0-113">Pipeline d’envoi BTARN</span><span class="sxs-lookup"><span data-stu-id="340b0-113">BTARN Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)