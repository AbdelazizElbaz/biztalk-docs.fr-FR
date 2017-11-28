---
title: Guide de Configuration de composants A4SWIFT | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: A4SWIFT, configuration guide
ms.assetid: ff4a3ee7-2fd9-44e7-8aa3-c3d214a6ce68
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 396e28d49b3e6a43e188e8358a045c3c91a627cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a4swift-component-configuration-guide"></a><span data-ttu-id="1f10e-102">Guide de Configuration de composants A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="1f10e-102">A4SWIFT Component Configuration Guide</span></span>
<span data-ttu-id="1f10e-103">Ce guide fournit des informations sur la configuration [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1f10e-103">This guide provides information about configuring [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="1f10e-104">Effectuer les étapes de ce guide de configuration après avoir installé A4SWIFT et terminé l’Assistant de Configuration d’A4SWIFT (comme décrit dans le Guide d’Installation).</span><span class="sxs-lookup"><span data-stu-id="1f10e-104">Perform the steps in this configuration guide after you have installed A4SWIFT and completed the A4SWIFT Configuration Wizard (as described in the Installation Guide).</span></span> <span data-ttu-id="1f10e-105">Ce guide de configuration comprend les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f10e-105">This configuration guide includes the following instructions:</span></span>  
  
-   <span data-ttu-id="1f10e-106">Étapes de post-installation pour la configuration de l’exécution de A4SWIFT pour les scénarios de messagerie.</span><span class="sxs-lookup"><span data-stu-id="1f10e-106">Post-installation steps for configuring the A4SWIFT runtime for messaging scenarios.</span></span>  
  
-   <span data-ttu-id="1f10e-107">Comment configurer Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="1f10e-107">How to configure Message Repair and New Submission.</span></span> <span data-ttu-id="1f10e-108">Pour ce faire, vous devez tout d’abord configurer manuellement l’exécution d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="1f10e-108">To do so, you must first manually configure the A4SWIFT runtime.</span></span> <span data-ttu-id="1f10e-109">Cela ne nécessite pas que vous configurez le rapprochement de réponse de FIN.</span><span class="sxs-lookup"><span data-stu-id="1f10e-109">This does not require that you configure FIN Response Reconciliation.</span></span>  
  
-   <span data-ttu-id="1f10e-110">Comment configurer le rapprochement de réponse de FIN.</span><span class="sxs-lookup"><span data-stu-id="1f10e-110">How to configure FIN Response Reconciliation.</span></span> <span data-ttu-id="1f10e-111">Pour ce faire, vous devez tout d’abord configurer manuellement l’exécution d’A4SWIFT.</span><span class="sxs-lookup"><span data-stu-id="1f10e-111">To do so, you must first manually configure the A4SWIFT runtime.</span></span> <span data-ttu-id="1f10e-112">Cela ne nécessite pas que vous configurez Message Repair et New Submission.</span><span class="sxs-lookup"><span data-stu-id="1f10e-112">This does not require that you configure Message Repair and New Submission.</span></span>  
  
 <span data-ttu-id="1f10e-113">L’illustration suivante montre les composants A4SWIFT que vous configurez.</span><span class="sxs-lookup"><span data-stu-id="1f10e-113">The following figure shows the A4SWIFT components that you will configure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-component-configuration.gif "A4SWIFT_Component_Configuration")  
  
 <span data-ttu-id="1f10e-114">Contenu de cette section :</span><span class="sxs-lookup"><span data-stu-id="1f10e-114">This section contains:</span></span>  
  
-   [<span data-ttu-id="1f10e-115">Configuration de l’exécution A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="1f10e-115">Configuring the A4SWIFT Runtime</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-the-a4swift-runtime.md)  
  
-   [<span data-ttu-id="1f10e-116">Configuration de Message Repair et New Submission</span><span class="sxs-lookup"><span data-stu-id="1f10e-116">Configuring Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="1f10e-117">Configuration de rapprochement de réponse FIN</span><span class="sxs-lookup"><span data-stu-id="1f10e-117">Configuring FIN Response Reconciliation</span></span>](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md)