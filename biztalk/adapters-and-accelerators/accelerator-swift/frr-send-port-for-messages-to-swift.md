---
title: "FRR Port d’envoi de Messages SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- send ports, FRR
ms.assetid: 905c69a3-dff3-4a60-803d-dd617ffb6896
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a442b45f57009b839b4e184ef9662b253ba32b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-send-port-for-messages-to-swift"></a><span data-ttu-id="9322e-102">FRR Port d’envoi de Messages SWIFT</span><span class="sxs-lookup"><span data-stu-id="9322e-102">FRR Send Port for Messages to SWIFT</span></span>
<span data-ttu-id="9322e-103">Pour activer le rapprochement de réponse FIN (FRR), vous devez configurer un port d’envoi FRR qui envoie un message à SAA via l’adaptateur BizTalk pour MQSeries.</span><span class="sxs-lookup"><span data-stu-id="9322e-103">To enable FIN response reconciliation (FRR), you must set up an FRR send port that sends a message to SAA through the BizTalk Adapter for MQSeries.</span></span> <span data-ttu-id="9322e-104">Cette itinéraires de port d’envoi un message via un FRR personnalisé envoyer composant de pipeline que vous devez créer avec les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="9322e-104">This send port routes a message through a custom FRR send pipeline component that you must create with the following pipeline components:</span></span>  
  
-   <span data-ttu-id="9322e-105">L’assembleur SWIFT dans la phase d’assemblage</span><span class="sxs-lookup"><span data-stu-id="9322e-105">The SWIFT assembler in the Assemble stage</span></span>  
  
-   <span data-ttu-id="9322e-106">Le composant de pipeline SWIFTAsmFrrMQSeriesHelper dans la phase de codage</span><span class="sxs-lookup"><span data-stu-id="9322e-106">The SWIFTAsmFrrMQSeriesHelper pipeline component in the Encode stage</span></span>  
  
 <span data-ttu-id="9322e-107">Le composant de pipeline SWIFTAsmFrrMQSeriesHelper définit la propriété MQMD_MsgID du message sortant à la valeur de la propriété FRRCorrelationToken.</span><span class="sxs-lookup"><span data-stu-id="9322e-107">The SWIFTAsmFrrMQSeriesHelper pipeline component sets the MQMD_MsgID property of the outgoing message to the value of the FRRCorrelationToken property.</span></span> <span data-ttu-id="9322e-108">Aussi, il assigne et promeut d’autres propriétés de contexte requis commençant par « MQ » avec les valeurs définies au moment du design du pipeline.</span><span class="sxs-lookup"><span data-stu-id="9322e-108">It also assigns and promotes any other required context properties starting with "MQ" with values set at the pipeline design time.</span></span> <span data-ttu-id="9322e-109">Le pipeline d’envoi inclut chaque propriété définie pour MQSeries comme une propriété configurable.</span><span class="sxs-lookup"><span data-stu-id="9322e-109">The send pipeline includes each property defined for MQSeries as a configurable property.</span></span> <span data-ttu-id="9322e-110">Chaque valeur par défaut est « Non utilisé ».</span><span class="sxs-lookup"><span data-stu-id="9322e-110">Each value defaults to "Not Used".</span></span>  
  
 <span data-ttu-id="9322e-111">Le port d’envoi traite les messages qui ont [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed == False et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND == True.</span><span class="sxs-lookup"><span data-stu-id="9322e-111">The send port handles messages that have [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed==False and [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_SWIFTBOUND==True.</span></span> <span data-ttu-id="9322e-112">Le mécanisme de transport est de l’adaptateur BizTalk pour MQSeries.</span><span class="sxs-lookup"><span data-stu-id="9322e-112">The transport mechanism is the BizTalk Adapter for MQSeries.</span></span> <span data-ttu-id="9322e-113">Pour plus d’informations sur les propriétés de transport, telles que la taille de la fragmentation, consultez la documentation de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="9322e-113">For information about the transport properties, such as the fragmentation size, see the MQSeries documentation.</span></span>