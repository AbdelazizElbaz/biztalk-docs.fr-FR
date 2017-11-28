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
ms.openlocfilehash: d1ae6acb6239821362ad5f488e9b95b9ffcc43d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-the-swift-disassembler-and-assembler"></a><span data-ttu-id="cfa3b-102">Utilisation de SWIFT désassembleur et assembleur</span><span class="sxs-lookup"><span data-stu-id="cfa3b-102">Working with the SWIFT Disassembler and Assembler</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="cfa3b-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit des composants de pipeline personnalisés, SWIFT désassembleur et assembleur SWIFT qui disposent de fonctionnalités conçues spécifiquement pour le traitement des messages de fichier plat SWIFT.</span><span class="sxs-lookup"><span data-stu-id="cfa3b-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] provides custom pipeline components, the SWIFT disassembler, and SWIFT assembler that have features designed specifically for processing SWIFT flat-file messages.</span></span> <span data-ttu-id="cfa3b-104">Le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] envoyer et recevoir des composants de pipeline pipelines utilisez le A4SWIFT pour effectuer des tâches spécifiques au cours des étapes définies de trafic entrant (réception) et le traitement de sortant (envoi).</span><span class="sxs-lookup"><span data-stu-id="cfa3b-104">The [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] send and receive pipelines use the A4SWIFT pipeline components to perform specific tasks during defined stages of inbound (receive) and outbound (send) processing.</span></span> <span data-ttu-id="cfa3b-105">Pour plus d’informations sur le traitement des messages, pipelines et les composants de pipeline, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="cfa3b-105">For further details about message processing, pipelines, and pipeline components, see [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
 <span data-ttu-id="cfa3b-106">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="cfa3b-106">This section contains:</span></span>  
  
-   [<span data-ttu-id="cfa3b-107">SWIFT désassembleur et assembleur fonctionnalités</span><span class="sxs-lookup"><span data-stu-id="cfa3b-107">SWIFT Disassembler and Assembler Functionality</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-disassembler-and-assembler-functionality.md)  
  
-   [<span data-ttu-id="cfa3b-108">Ajout du désassembleur SWIFT ou l’assembleur de pipeline</span><span class="sxs-lookup"><span data-stu-id="cfa3b-108">Adding the SWIFT Disassembler or Assembler to a Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-the-swift-disassembler-or-assembler-to-a-pipeline.md)  
  
-   [<span data-ttu-id="cfa3b-109">Configuration du désassembleur SWIFT ou l’assembleur</span><span class="sxs-lookup"><span data-stu-id="cfa3b-109">Configuring the SWIFT Disassembler or Assembler</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-swift-disassembler-or-assembler.md)  
  
-   [<span data-ttu-id="cfa3b-110">Découverte de Type dynamique des messages et la résolution de schéma</span><span class="sxs-lookup"><span data-stu-id="cfa3b-110">Dynamic Message Type Discovery and Schema Resolution</span></span>](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md)  
  
-   [<span data-ttu-id="cfa3b-111">Création de schémas d’en-tête personnalisé pour la détection de Type de Message dynamique</span><span class="sxs-lookup"><span data-stu-id="cfa3b-111">Creating Custom Header Schemas for Dynamic Message Type Discovery</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-custom-header-schemas-for-dynamic-message-type-discovery.md)  
  
-   [<span data-ttu-id="cfa3b-112">Désassemblage de lots entrants</span><span class="sxs-lookup"><span data-stu-id="cfa3b-112">Disassembling Inbound Batches</span></span>](../../adapters-and-accelerators/accelerator-swift/disassembling-inbound-batches.md)