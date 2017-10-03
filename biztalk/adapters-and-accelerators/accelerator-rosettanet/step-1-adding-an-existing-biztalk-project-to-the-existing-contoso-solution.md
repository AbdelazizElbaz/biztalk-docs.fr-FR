---
title: "Étape 1 : Ajout d’un projet BizTalk existant à la Solution Contoso existante | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects, adding to solutions
- private process tutorial, adding projects to solutions
ms.assetid: 9e84d282-01aa-4611-8462-c1acef234042
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34c6a6bd5807702cb01c4c7cbc13780b95cc3da2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-adding-an-existing-biztalk-project-to-the-existing-contoso-solution"></a><span data-ttu-id="a8bff-102">Étape 1 : Ajout d’un projet BizTalk existant à la Solution Contoso existante</span><span class="sxs-lookup"><span data-stu-id="a8bff-102">Step 1: Adding an Existing BizTalk Project to the Existing Contoso Solution</span></span>
<span data-ttu-id="a8bff-103">Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK contient une orchestration de processus privé qui sert d’un bon point de départ lors de la personnalisation de votre propre processus privé.</span><span class="sxs-lookup"><span data-stu-id="a8bff-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK contains a private process orchestration that serves as a good starting point when customizing your own private process.</span></span> <span data-ttu-id="a8bff-104">Dans cette étape, vous ajoutez cette orchestration à votre solution et modifiez le nom de l’assembly pour éviter tout conflit avec l’orchestration PrivateResponder installée lors de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="a8bff-104">In this step, you add that orchestration to your solution and change the assembly name to avoid conflict with the PrivateResponder orchestration installed during the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] installation.</span></span> <span data-ttu-id="a8bff-105">Avant de commencer, ouvrez la solution de Contoso que vous avez créé dans [étape 1 : création d’une BizTalk Solution pour Contoso Price les demandes de disponibilité](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md).</span><span class="sxs-lookup"><span data-stu-id="a8bff-105">Before you start, open the Contoso solution you created in [Step 1: Creating a New BizTalk Solution for the Contoso Price and Availability Request](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md).</span></span>  
  
### <a name="to-add-the-privateresponder-project-to-the-contoso-solution"></a><span data-ttu-id="a8bff-106">Pour ajouter le projet de PrivateResponder à la solution Contoso</span><span class="sxs-lookup"><span data-stu-id="a8bff-106">To add the PrivateResponder project to the Contoso solution</span></span>  
  
1.  <span data-ttu-id="a8bff-107">Copiez l’exemple de PrivateResponder SDK dans votre dossier de solution de Contoso.</span><span class="sxs-lookup"><span data-stu-id="a8bff-107">Copy the PrivateResponder SDK sample to your Contoso solution folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a8bff-108">Par défaut, l’exemple de PrivateResponder SDK se trouve dans C:\Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\PrivateResponder dossier.</span><span class="sxs-lookup"><span data-stu-id="a8bff-108">By default, the PrivateResponder SDK sample is located in the C:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\PrivateResponder folder.</span></span>  
  
2.  <span data-ttu-id="a8bff-109">Dans Visual Studio, cliquez sur **fichier**, pointez sur **ajouter**, puis cliquez sur **projet existant**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-109">In Visual Studio, click **File**, point to **Add**, and then click **Existing Project**.</span></span>  
  
3.  <span data-ttu-id="a8bff-110">Dans la boîte de dialogue Ajouter un projet existant, recherchez le dossier de votre solution, sélectionnez le **PrivateResponder.btproj** fichier de projet, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-110">In the Add Existing Project dialog box, locate the folder for your solution, select the **PrivateResponder.btproj** project file, and then click **Open**.</span></span>  
  
### <a name="to-change-the-privateresponder-assembly-name-and-default-namespace"></a><span data-ttu-id="a8bff-111">Pour modifier le nom de l’assembly PrivateResponder et par défaut d’espace de noms</span><span class="sxs-lookup"><span data-stu-id="a8bff-111">To change the PrivateResponder assembly name and default namespace</span></span>  
  
1.  <span data-ttu-id="a8bff-112">Dans l’Explorateur de solutions, avec le bouton droit sur le **PrivateResponder** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-112">In Solution Explorer, right click the **PrivateResponder** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="a8bff-113">Dans la boîte de dialogue Pages de propriétés de PrivateResponder, dans l’arborescence de la console, cliquez sur **général**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-113">In the PrivateResponder Property Pages dialog box, in the console tree, click **General**.</span></span> <span data-ttu-id="a8bff-114">Dans le volet d’informations, dans le **nom de l’Assembly** , tapez **ContosoPriceAndAvailability.PrivateResponder**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-114">In the details pane, in the **Assembly Name** box, type **ContosoPriceAndAvailability.PrivateResponder**.</span></span>  
  
3.  <span data-ttu-id="a8bff-115">Dans le **par défaut de Namespace** , tapez **ContosoPriceAndAvailability**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-115">In the **Default Namespace** box, type **ContosoPriceAndAvailability**.</span></span>  
  
4.  <span data-ttu-id="a8bff-116">Cliquez sur **OK** pour fermer la boîte de dialogue Pages de propriétés de PrivateResponder.</span><span class="sxs-lookup"><span data-stu-id="a8bff-116">Click **OK** to close the PrivateResponder Property Pages dialog box.</span></span>  
  
5.  <span data-ttu-id="a8bff-117">Dans l'Explorateur de solutions, double-cliquez sur **PrivateResponder.odx**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-117">In Solution Explorer, double-click **PrivateResponder.odx**.</span></span>  
  
6.  <span data-ttu-id="a8bff-118">Dans le **Vue Orchestration** fenêtre, vérifiez que **propriétés d’Orchestration** (sous **PrivateResponderProcess**) est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a8bff-118">In the **Orchestration View** window, ensure that **Orchestration Properties** (under **PrivateResponderProcess**) is selected.</span></span>  
  
7.  <span data-ttu-id="a8bff-119">Dans le **propriétés** fenêtre, dans le **Namespace** , tapez **ContosoPriceAndAvailability**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="a8bff-119">In the **Properties** window, in the **Namespace** field, type **ContosoPriceAndAvailability**, and then press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8bff-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8bff-120">See Also</span></span>  
 [<span data-ttu-id="a8bff-121">Étape 2 : Définition et publication du vocabulaire pour Contoso</span><span class="sxs-lookup"><span data-stu-id="a8bff-121">Step 2: Defining and Publishing the Vocabulary for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-defining-and-publishing-the-vocabulary-for-contoso.md)