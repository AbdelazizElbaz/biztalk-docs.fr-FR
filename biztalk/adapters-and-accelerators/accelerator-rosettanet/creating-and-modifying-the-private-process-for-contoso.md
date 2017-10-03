---
title: "Création et modification du processus privé pour Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private processes, creating
- configuring, private processes
- private processes, configuring
- private process tutorial, creating private processes
- creating, private processes
- private process tutorial, configuring private processes
ms.assetid: 0690aaef-cd9e-46aa-8bd5-22744d5aec4c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9b1749c941e78963abd4768afbb5ce0668ee3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-modifying-the-private-process-for-contoso"></a><span data-ttu-id="9e115-102">Création et modification du processus privé pour Contoso</span><span class="sxs-lookup"><span data-stu-id="9e115-102">Creating and Modifying the Private Process for Contoso</span></span>
<span data-ttu-id="9e115-103">Vous pouvez effectuer des tâches supplémentaires avec les messages RosettaNet lors de l’implémentation de votre solution en personnalisant le processus privé dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9e115-103">You can perform additional tasks with RosettaNet-based messages when implementing your solution by customizing the private process within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="9e115-104">Cette section montre comment personnaliser le processus privé à l’aide du moteur de règles d’entreprise (BRE) pour créer des stratégies et l’Éditeur BizTalk pour personnaliser l’orchestration de processus privé.</span><span class="sxs-lookup"><span data-stu-id="9e115-104">This section demonstrates how to customize the private process by using the Business Rule Engine (BRE) to create policies and BizTalk Editor to customize the private process orchestration.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e115-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9e115-105">In This Section</span></span>  
  
-   [<span data-ttu-id="9e115-106">Étape 1 : Ajout d’un projet BizTalk existant à la Solution Contoso existante</span><span class="sxs-lookup"><span data-stu-id="9e115-106">Step 1: Adding an Existing BizTalk Project to the Existing Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-adding-an-existing-biztalk-project-to-the-existing-contoso-solution.md)  
  
-   [<span data-ttu-id="9e115-107">Étape 2 : Définition et publication du vocabulaire pour Contoso</span><span class="sxs-lookup"><span data-stu-id="9e115-107">Step 2: Defining and Publishing the Vocabulary for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-defining-and-publishing-the-vocabulary-for-contoso.md)  
  
-   [<span data-ttu-id="9e115-108">Étape 3 : Définition, la publication et le déploiement de la stratégie d’entreprise pour Contoso</span><span class="sxs-lookup"><span data-stu-id="9e115-108">Step 3: Defining, Publishing, and Deploying the Business Policy for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-defining-publishing-and-deploying-the-business-policy-for-contoso.md)  
  
-   [<span data-ttu-id="9e115-109">Étape 4 : Création du projet de HeaderHelper</span><span class="sxs-lookup"><span data-stu-id="9e115-109">Step 4: Creating the HeaderHelper Project</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-headerhelper-project.md)  
  
-   [<span data-ttu-id="9e115-110">Étape 5 : Modification de l’Orchestration de processus de privé de Contoso</span><span class="sxs-lookup"><span data-stu-id="9e115-110">Step 5: Modifying the Contoso Private Process Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-modifying-the-contoso-private-process-orchestration.md)  
  
-   [<span data-ttu-id="9e115-111">Étape 6 : Configuration des formes d’Orchestration (Contoso)</span><span class="sxs-lookup"><span data-stu-id="9e115-111">Step 6: Configuring Orchestration Shapes (Contoso)</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-configuring-orchestration-shapes-contoso.md)  
  
-   [<span data-ttu-id="9e115-112">Étape 7 : Création et configuration des Ports</span><span class="sxs-lookup"><span data-stu-id="9e115-112">Step 7: Creating and Configuring Ports</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md)  
  
-   [<span data-ttu-id="9e115-113">Étape 8 : Création et déploiement de l’Orchestration Contoso</span><span class="sxs-lookup"><span data-stu-id="9e115-113">Step 8: Building and Deploying the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-8-building-and-deploying-the-contoso-orchestration.md)  
  
-   [<span data-ttu-id="9e115-114">Étape 9 : Démarrer l’Orchestration Contoso</span><span class="sxs-lookup"><span data-stu-id="9e115-114">Step 9: Starting the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)