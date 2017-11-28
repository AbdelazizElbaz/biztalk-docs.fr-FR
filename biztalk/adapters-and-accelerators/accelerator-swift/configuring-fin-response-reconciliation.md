---
title: "Configuration de rapprochement de réponse FIN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FIN Response Reconciliation, configuring
- configuring, FIN Response Reconciliation
ms.assetid: dc934530-76ff-4cdb-b182-46f9ea0343b7
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 384a2ea27e3d208864c8b16ec52562e6e1cfa28e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fin-response-reconciliation"></a><span data-ttu-id="89fbb-102">Configuration de rapprochement de réponse FIN</span><span class="sxs-lookup"><span data-stu-id="89fbb-102">Configuring FIN Response Reconciliation</span></span>
<span data-ttu-id="89fbb-103">Vous devez effectuer les étapes dans les sections suivantes pour configurer le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fonctionnalité rapprochement de réponse de FIN (FRR), comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="89fbb-103">You must perform the steps in the following sections to configure the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] FIN Response Reconciliation (FRR) feature, as shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-frr-configuration.jpg "A4SWIFT_FRR_Configuration")  
  
 <span data-ttu-id="89fbb-104">Dans l’Assistant Installation d’A4SWIFT, vous pouvez choisir d’installer Message Repair et New Submission et FRR, ou Message Repair et New Submission sans FRR ou FRR sans Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="89fbb-104">In the A4SWIFT Installation Wizard, you can choose to install Message Repair and New Submission and FRR, or Message Repair and New Submission without FRR, or FRR without Message Repair and New Submission.</span></span> <span data-ttu-id="89fbb-105">Par conséquent, les instructions de cette section ne supposent pas que vous installez et configurez Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="89fbb-105">As a result, the instructions in this section do not assume that you are installing and configuring Message Repair and New Submission.</span></span> <span data-ttu-id="89fbb-106">Ils, toutefois, supposez que vous avez effectué les étapes décrites dans le [configuration de l’exécution de A4SWIFT](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md).</span><span class="sxs-lookup"><span data-stu-id="89fbb-106">They do, however, assume that you have performed the steps in the [Configuring the A4SWIFT Runtime](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md).</span></span>  
  
 <span data-ttu-id="89fbb-107">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="89fbb-107">This section contains:</span></span>  
  
-   [<span data-ttu-id="89fbb-108">Liaison et démarrage de l’Orchestration FRR</span><span class="sxs-lookup"><span data-stu-id="89fbb-108">Binding and Starting the FRR Orchestration</span></span>](../../adapters-and-accelerators/accelerator-swift/binding-and-starting-the-frr-orchestration.md)  
  
-   [<span data-ttu-id="89fbb-109">Création de la FRR le Pipeline de réception</span><span class="sxs-lookup"><span data-stu-id="89fbb-109">Creating the FRR Receive Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-pipeline.md)  
  
-   [<span data-ttu-id="89fbb-110">Création de la FRR emplacement de réception pour la réception de l’Application Back-End</span><span class="sxs-lookup"><span data-stu-id="89fbb-110">Creating the FRR Receive Location for Receiving from the Back-End Application</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-the-back-end-application.md)  
  
-   [<span data-ttu-id="89fbb-111">Création de la FRR emplacement de réception pour recevoir des SWIFT</span><span class="sxs-lookup"><span data-stu-id="89fbb-111">Creating the FRR Receive Location for Receiving from SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-receive-location-for-receiving-from-swift.md)  
  
-   [<span data-ttu-id="89fbb-112">Créer le Pipeline d’envoi FRR</span><span class="sxs-lookup"><span data-stu-id="89fbb-112">Creating the FRR Send Pipeline</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-pipeline.md)  
  
-   [<span data-ttu-id="89fbb-113">Création du Port d’envoi FRR pour l’envoi à SWIFT</span><span class="sxs-lookup"><span data-stu-id="89fbb-113">Creating the FRR Send Port for Sending to SWIFT</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-port-for-sending-to-swift.md)  
  
-   [<span data-ttu-id="89fbb-114">Création de Ports d’envoi pour envoyer aux gestionnaires personnalisés FRR</span><span class="sxs-lookup"><span data-stu-id="89fbb-114">Creating the FRR Send Ports for Sending to the Custom Handlers</span></span>](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md)