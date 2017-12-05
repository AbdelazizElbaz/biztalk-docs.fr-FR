---
title: "Utilisation de SWIFT désassembleur et assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, assembler
- developing, disassembler
- assembler, developing
- disassembler, developing
ms.assetid: cc88ed4c-baed-4efa-b54f-9fe079df9ba4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a63b27e3c89ac59c698098b09e2f6565980e363
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="working-with-the-swift-disassembler-and-assembler"></a><span data-ttu-id="30696-102">Utilisation de SWIFT désassembleur et assembleur</span><span class="sxs-lookup"><span data-stu-id="30696-102">Working with the SWIFT Disassembler and Assembler</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="30696-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit des composants de pipeline personnalisés, SWIFT désassembleur et assembleur SWIFT qui disposent de fonctionnalités conçues spécifiquement pour le traitement des messages de fichier plat SWIFT.</span><span class="sxs-lookup"><span data-stu-id="30696-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides custom pipeline components, the SWIFT disassembler, and SWIFT assembler that have features designed specifically for processing SWIFT flat-file messages.</span></span> <span data-ttu-id="30696-104">Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] envoyer et recevoir des composants de pipeline pipelines utilisez le A4SWIFT pour effectuer des tâches spécifiques au cours des étapes définies de trafic entrant (réception) et le traitement de sortant (envoi).</span><span class="sxs-lookup"><span data-stu-id="30696-104">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send and receive pipelines use the A4SWIFT pipeline components to perform specific tasks during defined stages of inbound (receive) and outbound (send) processing.</span></span> <span data-ttu-id="30696-105">Pour plus d’informations sur le traitement des messages, pipelines et les composants de pipeline, consultez l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="30696-105">For further details about message processing, pipelines, and pipeline components, see BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="30696-106">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="30696-106">This section contains:</span></span>  
  
-   [<span data-ttu-id="30696-107">Fonctionnalités du désassembleur et de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="30696-107">SWIFT Disassembler and Assembler Functionality</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-and-assembler-functionality.md)  
  
-   [<span data-ttu-id="30696-108">Ajout du désassembleur ou de l’assembleur SWIFT à un pipeline</span><span class="sxs-lookup"><span data-stu-id="30696-108">Adding the SWIFT Disassembler or Assembler to a Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-the-swift-disassembler-or-assembler-to-a-pipeline.md)  
  
-   [<span data-ttu-id="30696-109">Configuration du désassembleur ou de l’assembleur SWIFT</span><span class="sxs-lookup"><span data-stu-id="30696-109">Configuring the SWIFT Disassembler or Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler-or-assembler.md)  
  
-   [<span data-ttu-id="30696-110">Détection dynamique des types de messages et résolution dynamique des schémas</span><span class="sxs-lookup"><span data-stu-id="30696-110">Dynamic Message Type Discovery and Schema Resolution</span></span>](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)  
  
-   [<span data-ttu-id="30696-111">Création de schémas d’en-tête personnalisés pour la détection dynamique des types de messages</span><span class="sxs-lookup"><span data-stu-id="30696-111">Creating Custom Header Schemas for Dynamic Message Type Discovery</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-custom-header-schemas-for-dynamic-message-type-discovery.md)  
  
-   [<span data-ttu-id="30696-112">Désassemblage des lots entrants</span><span class="sxs-lookup"><span data-stu-id="30696-112">Disassembling Inbound Batches</span></span>](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)