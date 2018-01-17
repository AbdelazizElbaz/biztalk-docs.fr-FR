---
title: "Leçon 2 : Ajout de références de projet | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- references [projects]
- projects, adding references
ms.assetid: ddc2bf49-cddd-4edb-8043-870897879655
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b00fc7d49024cec6f9c300444646da82069e16cc
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="lesson-2-adding-project-references"></a><span data-ttu-id="51d84-102">Leçon 2 : Ajout de références de projet</span><span class="sxs-lookup"><span data-stu-id="51d84-102">Lesson 2: Adding Project References</span></span>
<span data-ttu-id="51d84-103">Vous ajoutez des références de projet pour vos pipelines peuvent accéder aux schémas runtime par défaut situés dans le fichier Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll.</span><span class="sxs-lookup"><span data-stu-id="51d84-103">You add project references so your pipelines can access the default runtime schemas located in the Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll file.</span></span> <span data-ttu-id="51d84-104">Ce fichier d’assembly contient le schéma d’en-tête avec les propriétés promues requises pour la résolution de type de message.</span><span class="sxs-lookup"><span data-stu-id="51d84-104">This assembly file contains the header schema with promoted properties required for message-type resolution.</span></span>  
  
 <span data-ttu-id="51d84-105">Vous référencez les schémas d’en-tête plus tard lorsque vous ajoutez le composant de code machine au pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="51d84-105">You reference the header schemas later when you add the disassembly component to the receive pipeline.</span></span>  
  
### <a name="to-add-a-reference-to-the-default-swift-runtimeschemas-assembly"></a><span data-ttu-id="51d84-106">Pour ajouter une référence à l’assembly de SWIFT RuntimeSchemas par défaut</span><span class="sxs-lookup"><span data-stu-id="51d84-106">To add a reference to the default SWIFT RuntimeSchemas assembly</span></span>  
  
1.  <span data-ttu-id="51d84-107">Dans l’Explorateur de solutions, vérifiez que le **SWIFTPipelines** projet est développé.</span><span class="sxs-lookup"><span data-stu-id="51d84-107">In Solution Explorer, ensure that the **SWIFTPipelines** project is expanded.</span></span> <span data-ttu-id="51d84-108">Avec le bouton droit **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="51d84-108">Right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="51d84-109">Dans la boîte de dialogue Ajouter une référence, cliquez sur le **Parcourir** onglet.</span><span class="sxs-lookup"><span data-stu-id="51d84-109">In the Add Reference dialog box, click the **Browse** tab.</span></span>  
  
3.  <span data-ttu-id="51d84-110">Accédez à  **\< *lecteur*\>: \Program Files\Microsoft BizTalk Accelerator pour SWIFT\Assemblies**.</span><span class="sxs-lookup"><span data-stu-id="51d84-110">Browse to **\<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\Assemblies**.</span></span>  
  
4.  <span data-ttu-id="51d84-111">Sélectionnez le **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** fichier.</span><span class="sxs-lookup"><span data-stu-id="51d84-111">Select the **Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.dll** file.</span></span>  
  
5.  <span data-ttu-id="51d84-112">Cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="51d84-112">Click **Add**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="51d84-113">L’assembly RuntimeSchemas (dll) que vous venez de sélectionner s’affiche dans la collection de références dans le projet SWIFTPipelines.</span><span class="sxs-lookup"><span data-stu-id="51d84-113">The RuntimeSchemas assembly (dll) that you selected now appears in the references collection in the SWIFTPipelines project.</span></span>  
  
#### <a name="to-add-a-reference-to-the-swiftpipelines-schemas-assembly"></a><span data-ttu-id="51d84-114">Pour ajouter une référence à l’assembly de schémas SWIFTPipelines</span><span class="sxs-lookup"><span data-stu-id="51d84-114">To add a reference to the SWIFTPipelines schemas assembly</span></span>  
  
1.  <span data-ttu-id="51d84-115">Dans l’Explorateur de solutions, sous le **SWIFTPipelines** de projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="51d84-115">In Solution Explorer, under the **SWIFTPipelines** project, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="51d84-116">Dans la boîte de dialogue Ajouter une référence sur le **projets** , cliquez sur le **SWIFTSchemas** de projet, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="51d84-116">In the Add Reference dialog box, on the **Projects** tab, click the **SWIFTSchemas** project, click **Add**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="51d84-117">Sur le **fichier** menu, cliquez sur **Enregistrer tout** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="51d84-117">On the **File** menu, click **Save All** to save your changes.</span></span>  
  
 <span data-ttu-id="51d84-118">Passez à [leçon 3 : ajout d’un Pipeline de réception personnalisé](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span><span class="sxs-lookup"><span data-stu-id="51d84-118">Proceed to [Lesson 3: Adding a Custom Receive Pipeline](../../adapters-and-accelerators/accelerator-swift/lesson-3-adding-a-custom-receive-pipeline.md).</span></span>