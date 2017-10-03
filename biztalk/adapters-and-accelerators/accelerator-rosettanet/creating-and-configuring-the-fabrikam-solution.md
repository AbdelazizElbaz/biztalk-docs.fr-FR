---
title: "Création et configuration de la Solution Fabrikam | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating solutions
- double action tutorial, configuring solutions
ms.assetid: 463d55ef-12b6-49e1-a1b8-9081cfb0abed
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 923e5fb3ba8e50f87538c77b354434cac952d9d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-configuring-the-fabrikam-solution"></a><span data-ttu-id="eedeb-102">Création et configuration de la Solution Fabrikam</span><span class="sxs-lookup"><span data-stu-id="eedeb-102">Creating and Configuring the Fabrikam Solution</span></span>
<span data-ttu-id="eedeb-103">Cette section du didacticiel détaille les étapes à suivre pour l’organisation de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="eedeb-103">This section of the tutorial details the steps that you have to follow for the Fabrikam organization.</span></span> <span data-ttu-id="eedeb-104">L’organisation Fabrikam représente l’acheteur et par conséquent agit en tant que l’initiateur pour toutes les demandes de processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="eedeb-104">The Fabrikam organization represents the buyer and therefore acts as the initiator for all Partner Interface Process (PIP) requests.</span></span> <span data-ttu-id="eedeb-105">Dans ce didacticiel, créer des accords pour quatre PIP, partenaire et générer et déployer un ASP line-of-business (LOB)[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] application d’envoyer une demande à l’ordinateur Contoso basée sur un certain type PIP.</span><span class="sxs-lookup"><span data-stu-id="eedeb-105">In this tutorial, you create partner agreements for four PIPs, and build and deploy a line-of-business (LOB) ASP[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] application to send a request to the Contoso computer based on a certain PIP type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eedeb-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eedeb-106">In This Section</span></span>  
  
-   [<span data-ttu-id="eedeb-107">Étape 1 : Création de l’organisation d’origine Fabrikam</span><span class="sxs-lookup"><span data-stu-id="eedeb-107">Step 1: Creating the Fabrikam Home Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-the-fabrikam-home-organization.md)  
  
-   [<span data-ttu-id="eedeb-108">Étape 2 : Création de l’organisation partenaire Contoso</span><span class="sxs-lookup"><span data-stu-id="eedeb-108">Step 2: Creating the Contoso Partner Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-the-contoso-partner-organization.md)  
  
-   [<span data-ttu-id="eedeb-109">Étape 3 : Création de l’accord de partenariat commercial 2 Fabrikam 0C</span><span class="sxs-lookup"><span data-stu-id="eedeb-109">Step 3: Creating the Fabrikam 0C2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-fabrikam-0c2-trading-partner-agreement.md)  
  
-   [<span data-ttu-id="eedeb-110">Étape 4 : Création de l’accord de partenariat commercial 4 Fabrikam 0C</span><span class="sxs-lookup"><span data-stu-id="eedeb-110">Step 4: Creating the Fabrikam 0C4 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-fabrikam-0c4-trading-partner-agreement.md)  
  
-   [<span data-ttu-id="eedeb-111">Étape 5 : Création de l’accord de partenariat commercial Fabrikam 3A2</span><span class="sxs-lookup"><span data-stu-id="eedeb-111">Step 5: Creating the Fabrikam 3A2 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-5-creating-the-fabrikam-3a2-trading-partner-agreement.md)  
  
-   [<span data-ttu-id="eedeb-112">Étape 6 : Création de l’accord de partenariat commercial Fabrikam 3 a 4</span><span class="sxs-lookup"><span data-stu-id="eedeb-112">Step 6: Creating the Fabrikam 3A4 Trading Partner Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-6-creating-the-fabrikam-3a4-trading-partner-agreement.md)  
  
-   [<span data-ttu-id="eedeb-113">Étape 7 : Création et déploiement de l’exemple du Kit de développement LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="eedeb-113">Step 7: Building and Deploying the LOBWebApplication SDK Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-7-building-and-deploying-the-lobwebapplication-sdk-sample.md)