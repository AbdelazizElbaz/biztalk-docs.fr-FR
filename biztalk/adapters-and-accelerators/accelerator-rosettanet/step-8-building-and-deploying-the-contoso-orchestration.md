---
title: "Étape 8 : Création et déploiement de l’Orchestration Contoso | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- private process tutorial, building solutions
- private process tutorial, deploying solutions
ms.assetid: d350b87a-0e4e-4837-ad39-fb5b1fdc1532
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 706c5ab2b52d30aeedfba7b3e002dc637fcece93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-8-building-and-deploying-the-contoso-orchestration"></a><span data-ttu-id="5e1db-102">Étape 8 : Création et déploiement de l’Orchestration Contoso</span><span class="sxs-lookup"><span data-stu-id="5e1db-102">Step 8: Building and Deploying the Contoso Orchestration</span></span>
<span data-ttu-id="5e1db-103">Au cours de cette étape, vous allez générer le projet Orchestration et le déployer à l'aide de l'Assistant Déploiement BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5e1db-103">In this step, you build the Orchestration project and deploy it using the BizTalk Deployment Wizard.</span></span> <span data-ttu-id="5e1db-104">Ces opérations ajoutent l'assembly à la base de données de configuration et l'installent dans le GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="5e1db-104">This adds the assembly to the Configuration database and installs the assembly in the Global Assembly Cache (GAC).</span></span>  
  
### <a name="to-assign-a-strong-name-to-your-assembly"></a><span data-ttu-id="5e1db-105">Pour affecter un nom fort à votre assembly</span><span class="sxs-lookup"><span data-stu-id="5e1db-105">To assign a strong name to your assembly</span></span>  
  
1.  <span data-ttu-id="5e1db-106">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **PrivateResponder** , puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5e1db-106">In Solution Explorer, right-click the **PrivateResponder** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="5e1db-107">Dans la boîte de dialogue Pages de propriétés de PrivateResponder, sélectionnez **Assembly** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="5e1db-107">In the PrivateResponder Property Pages dialog box, select **Assembly** from the left pane.</span></span>  
  
3.  <span data-ttu-id="5e1db-108">Dans le volet droit, faites défiler l'affichage jusqu'à la section **Nom fort** , cliquez sur le champ situé à droite de **Fichier de clé de l'assembly**, puis cliquez sur le bouton de sélection (**...**).</span><span class="sxs-lookup"><span data-stu-id="5e1db-108">In the right pane, scroll down to the **Strong name** section, click the field to the right of the **Assembly Key File**, and then click the ellipsis button (**…**).</span></span>  
  
4.  <span data-ttu-id="5e1db-109">Recherchez votre dossier de projet, sélectionnez le fichier **FabConPriceAvail.snk** , puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="5e1db-109">Locate your project folder, select the **FabConPriceAvail.snk** file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="5e1db-110">Dans le volet droit, sélectionnez **Faux** dans la liste déroulante **Temporisation de la signature de l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="5e1db-110">In the right pane, select **False** from the **Assembly Delay Sign** drop down list.</span></span>  
  
6.  <span data-ttu-id="5e1db-111">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="5e1db-111">Click **OK** to save the changes.</span></span>  
  
### <a name="to-build-and-deploy-the-orchestration-project"></a><span data-ttu-id="5e1db-112">Pour créer et déployer le projet d'orchestration</span><span class="sxs-lookup"><span data-stu-id="5e1db-112">To build and deploy the orchestration project</span></span>  
  
1.  <span data-ttu-id="5e1db-113">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet **PrivateResponder** , puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="5e1db-113">In Solution Explorer, right-click the **PrivateResponder** project, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5e1db-114">Vous pouvez ignorer sans risque les avertissements qui se produisent pendant le processus de génération.</span><span class="sxs-lookup"><span data-stu-id="5e1db-114">You can safely ignore any warnings that occur during the build process.</span></span>  
  
2.  <span data-ttu-id="5e1db-115">Une fois la génération réussie, cliquez à nouveau avec le bouton droit sur le projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="5e1db-115">After the build has succeeded, right-click the project again, and then click **Deploy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e1db-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e1db-116">See Also</span></span>  
 [<span data-ttu-id="5e1db-117">Étape 9 : Démarrer l’Orchestration Contoso</span><span class="sxs-lookup"><span data-stu-id="5e1db-117">Step 9: Starting the Contoso Orchestration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-9-starting-the-contoso-orchestration.md)