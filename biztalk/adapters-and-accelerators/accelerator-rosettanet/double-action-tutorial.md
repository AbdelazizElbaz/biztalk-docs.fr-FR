---
title: Didacticiel double Action | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, PIPs
- double action tutorial, about the tutorial
- trading partners, tutorials
- double action tutorial
- tutorials, trading partners
- PIPs, tutorials
- tutorials, double action tutorial
ms.assetid: b692c043-82ef-46f4-8683-7ae1fd6e4421
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5243fb2547f27b113e3096d6c93d233e22aae3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="double-action-tutorial"></a><span data-ttu-id="46fc0-102">Didacticiel double Action</span><span class="sxs-lookup"><span data-stu-id="46fc0-102">Double Action Tutorial</span></span>
<span data-ttu-id="46fc0-103">Ce didacticiel décrit une solution de bout en bout à l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46fc0-103">This tutorial covers an end-to-end solution using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="46fc0-104">Le didacticiel détaille les étapes à suivre pour implémenter une solution compatible avec RosettaNet en créant un scénario de partenaire commercial entre deux entreprises fictives : Contoso, l’organisation du fournisseur et Fabrikam, l’organisation de l’acheteur.</span><span class="sxs-lookup"><span data-stu-id="46fc0-104">The tutorial details the steps that you have to follow to implement a RosettaNet-compliant solution by creating a trading partner scenario between two fictitious companies: Contoso, the supplier organization, and Fabrikam, the buyer organization.</span></span>  
  
 <span data-ttu-id="46fc0-105">Ce didacticiel utilise quatre différents processus Partner Interface (PIP) :</span><span class="sxs-lookup"><span data-stu-id="46fc0-105">This tutorial uses four different Partner Interface Processes (PIPs):</span></span>  
  
-   <span data-ttu-id="46fc0-106">0, C 2 - demande de Test asynchrone</span><span class="sxs-lookup"><span data-stu-id="46fc0-106">0C2 - Asynchronous Test Request</span></span>  
  
-   <span data-ttu-id="46fc0-107">-Test synchrone requête 0c4</span><span class="sxs-lookup"><span data-stu-id="46fc0-107">0C4 - Synchronous Test Query</span></span>  
  
-   <span data-ttu-id="46fc0-108">3A2 - demande de prix et disponibilité</span><span class="sxs-lookup"><span data-stu-id="46fc0-108">3A2 - Request Price and Availability</span></span>  
  
-   <span data-ttu-id="46fc0-109">3 a 4 - demande de bon de commande</span><span class="sxs-lookup"><span data-stu-id="46fc0-109">3A4 - Request Purchase Order</span></span>  
  
 <span data-ttu-id="46fc0-110">Ce didacticiel traite plusieurs zones distinctes d’une solution RosettaNet, notamment l’utilisation de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion, créer des applications line of business (LOB) et la création d’orchestrations personnalisées que vous pouvez utiliser pour intégrer Systèmes de planification ERP (Enterprise Resource).</span><span class="sxs-lookup"><span data-stu-id="46fc0-110">This tutorial addresses several distinct areas of a RosettaNet-based solution, including working with the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, creating line-of-business (LOB) applications, and creating custom orchestrations that you can use to integrate Enterprise Resource Planning (ERP) systems.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46fc0-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="46fc0-111">In This Section</span></span>  
  
-   [<span data-ttu-id="46fc0-112">Préparation pour le didacticiel Double Action</span><span class="sxs-lookup"><span data-stu-id="46fc0-112">Preparing for the Double Action Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/preparing-for-the-double-action-tutorial.md)  
  
-   [<span data-ttu-id="46fc0-113">Création et configuration de la Solution de Contoso</span><span class="sxs-lookup"><span data-stu-id="46fc0-113">Creating and Configuring the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)  
  
-   [<span data-ttu-id="46fc0-114">Création et configuration de la Solution Fabrikam</span><span class="sxs-lookup"><span data-stu-id="46fc0-114">Creating and Configuring the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-fabrikam-solution.md)  
  
-   [<span data-ttu-id="46fc0-115">Test du didacticiel Double Action</span><span class="sxs-lookup"><span data-stu-id="46fc0-115">Testing the Double Action Tutorial</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/testing-the-double-action-tutorial.md)