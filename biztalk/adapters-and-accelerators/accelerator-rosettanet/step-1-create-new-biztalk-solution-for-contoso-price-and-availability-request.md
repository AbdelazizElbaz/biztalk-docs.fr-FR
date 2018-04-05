---
title: 'Étape 1 : Création d’une Solution BizTalk pour la requête de la disponibilité et le prix de Contoso | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating solutions
ms.assetid: e323ce26-2031-4293-95bd-a3bf02e535a5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee09981b11be8892eefe8d73d526e5712145c9c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-a-new-biztalk-solution-for-the-contoso-price-and-availability-request"></a><span data-ttu-id="d0b68-102">Étape 1 : Création d’une Solution BizTalk pour la requête de la disponibilité et le prix de Contoso</span><span class="sxs-lookup"><span data-stu-id="d0b68-102">Step 1: Creating a New BizTalk Solution for the Contoso Price and Availability Request</span></span>
<span data-ttu-id="d0b68-103">Dans cette étape, vous allez créer un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] solution pour le projet de Contoso Price et demandes de disponibilité.</span><span class="sxs-lookup"><span data-stu-id="d0b68-103">In this step, you create a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] solution for the Contoso Price and Availability Request project.</span></span> <span data-ttu-id="d0b68-104">Ce projet contient les schémas et mappages des requêtes et réponses pour les messages 3A2 relatifs au prix et à la disponibilité.</span><span class="sxs-lookup"><span data-stu-id="d0b68-104">This project will contain the schemas and maps for the requests and responses for the 3A2 Price and Availability messages.</span></span>  
  
### <a name="to-create-a-blank-solution"></a><span data-ttu-id="d0b68-105">Pour créer une solution vide</span><span class="sxs-lookup"><span data-stu-id="d0b68-105">To create a blank solution</span></span>  
  
1.  <span data-ttu-id="d0b68-106">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="d0b68-106">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="d0b68-107">Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="d0b68-107">On the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="d0b68-108">Dans la boîte de dialogue Nouveau projet, dans la section **Types de projets** , développez **Autres types de projets**, sélectionnez **Solutions Visual Studio**, puis dans la section **Modèles** , sélectionnez **Nouvelle solution**.</span><span class="sxs-lookup"><span data-stu-id="d0b68-108">In the New Project dialog box, in the **Project Types** section, expand **Other Project Types**, select **Visual Studio Solutions**, and then in the **Templates** section, select **Blank Solution**.</span></span>  
  
4.  <span data-ttu-id="d0b68-109">Dans la zone **Nom** , tapez **Contoso** en tant que nom de la solution, puis cliquez sur **OK** pour ouvrir la nouvelle solution.</span><span class="sxs-lookup"><span data-stu-id="d0b68-109">In the **Name** box, type **Contoso** as the solution name, and then click **OK** to open the new solution.</span></span>  
  
### <a name="to-create-the-price-and-availability-project"></a><span data-ttu-id="d0b68-110">Pour créer le projet relatif au prix et à la disponibilité</span><span class="sxs-lookup"><span data-stu-id="d0b68-110">To create the Price and Availability project</span></span>  
  
1.  <span data-ttu-id="d0b68-111">Dans le menu **Fichier** de Visual Studio, pointez sur **Nouveau**, puis cliquez sur **Projet**.</span><span class="sxs-lookup"><span data-stu-id="d0b68-111">In Visual Studio, on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="d0b68-112">Dans la boîte de dialogue Nouveau projet, dans la section **Types de projets** , sélectionnez **Projets BizTalk**, puis, dans la section **Modèles** , cliquez sur **Projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="d0b68-112">In the New Project dialog box, in the **Project Types** section, select **BizTalk Projects**, and then in the **Templates** section, select **Empty BizTalk Server Project**.</span></span>  
  
3.  <span data-ttu-id="d0b68-113">Dans la zone **Nom** , tapez **ContosoPriceAndAvailability** comme nom de projet.</span><span class="sxs-lookup"><span data-stu-id="d0b68-113">In the **Name** box, type **ContosoPriceAndAvailability** as the project name.</span></span> <span data-ttu-id="d0b68-114">Pour **Solution**, sélectionnez **Ajouter à la solution**.</span><span class="sxs-lookup"><span data-stu-id="d0b68-114">For **Solution**, select **Add to Solution**.</span></span> <span data-ttu-id="d0b68-115">Cliquez sur **OK** pour ouvrir le nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="d0b68-115">Click **OK** to open the new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0b68-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0b68-116">See Also</span></span>  
 [<span data-ttu-id="d0b68-117">Étape 2 : Création de schémas Application LOB Contoso pour le prix et le projet de disponibilité à l’aide de l’Éditeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="d0b68-117">Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-contoso-lob-application-schema-for-price-and-availability.md)