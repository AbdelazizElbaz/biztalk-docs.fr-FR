---
title: "FRR des Ports d’envoi des Messages aux gestionnaires personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, send ports
- custom handlers
- FRR, custom handlers
- send ports, FRR
- send ports, custom handlers
ms.assetid: 486d7410-fde1-4a9b-a9c2-64c1ed85ebc0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6babc312ddad7d77a96e29bc9e59ec9298aa6ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-send-ports-for-messages-to-the-custom-handlers"></a><span data-ttu-id="a6953-102">FRR des Ports d’envoi des Messages aux gestionnaires personnalisés</span><span class="sxs-lookup"><span data-stu-id="a6953-102">FRR Send Ports for Messages to the Custom Handlers</span></span>
<span data-ttu-id="a6953-103">Pour activer des gestionnaires personnalisés pour FRR, vous devez créer une série de ports d’envoi FRR, chacun d’eux qui achemine une copie d’un message d’origine d’un certain type aux gestionnaires personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a6953-103">To enable custom handlers for FRR, you must create a series of FRR send ports, each one of which routes a copy of an original message of a certain type to the custom handlers.</span></span> <span data-ttu-id="a6953-104">Ces ports d’envoi doivent doivent les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="a6953-104">These send ports must have the following pipeline components:</span></span>  
  
-   <span data-ttu-id="a6953-105">L’assembleur SWIFT dans la phase d’assemblage</span><span class="sxs-lookup"><span data-stu-id="a6953-105">The SWIFT assembler in the Assemble stage</span></span>  
  
-   <span data-ttu-id="a6953-106">Le composant de pipeline SWIFTSendFrrComponent dans la phase de codage</span><span class="sxs-lookup"><span data-stu-id="a6953-106">The SWIFTSendFrrComponent pipeline component in the Encode stage</span></span>  
  
 <span data-ttu-id="a6953-107">Pour tous les messages à l’exception des messages SWIFT FIN catégorie 0 à 9 qui ne sont pas envoyés avec succès, le port d’envoi doit avoir les filtres suivants :</span><span class="sxs-lookup"><span data-stu-id="a6953-107">For all messages except Category 0 to 9 SWIFT FIN messages that are not successfully sent, the send port must have the following filters:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="a6953-108">_SendingServiceType == [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="a6953-108">_SendingServiceType == [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
-   <span data-ttu-id="a6953-109">BIZTALK SERVER. La valeur requise pour chaque type de message de l’opération.</span><span class="sxs-lookup"><span data-stu-id="a6953-109">BTS.Operation set to the value required for each message type.</span></span> <span data-ttu-id="a6953-110">Les valeurs possibles pour le BTS. Propriété de l’opération, consultez le tableau dans [créer les Ports d’envoi FRR à envoyer aux gestionnaires personnalisé](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="a6953-110">For the possible values for the BTS.Operation property, see the table in [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>  
  
 <span data-ttu-id="a6953-111">Pour les messages de la catégorie de 0 à 9 SWIFT FIN qui ne sont pas envoyés avec succès, le port d’envoi doit avoir les filtres suivants :</span><span class="sxs-lookup"><span data-stu-id="a6953-111">For Category 0 to 9 SWIFT FIN messages that are not successfully sent, the send port must have the following filters:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="a6953-112">_SendingServiceTyp ==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="a6953-112">_SendingServiceTyp==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="a6953-113">_FrrFailed == true</span><span class="sxs-lookup"><span data-stu-id="a6953-113">_FrrFailed==True</span></span>  
  
-   <span data-ttu-id="a6953-114">BIZTALK SERVER. Opération ==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg</span><span class="sxs-lookup"><span data-stu-id="a6953-114">BTS.Operation==[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrSendMTMsg</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="a6953-115">_FRRFailedReason défini sur la valeur requise pour chaque type de message.</span><span class="sxs-lookup"><span data-stu-id="a6953-115">_FRRFailedReason set to the value required for each message type.</span></span> <span data-ttu-id="a6953-116">Les valeurs possibles pour le BTS. Propriété de l’opération, consultez le tableau dans [créer les Ports d’envoi FRR à envoyer aux gestionnaires personnalisé](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="a6953-116">For the possible values for the BTS.Operation property, see the table in [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>