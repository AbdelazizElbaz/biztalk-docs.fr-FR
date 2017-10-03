---
title: "Création et déploiement des Pipelines d’A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- deploying, pipelines
- pipelines, deploying
- pipelines, creating
ms.assetid: 2a614510-7e15-4e88-9012-fc019d3aefee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bec21ebd5a3b32986969676a78109cad55d870cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-deploying-a4swift-pipelines"></a><span data-ttu-id="63b0e-102">Création et déploiement des Pipelines d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="63b0e-102">Creating and Deploying A4SWIFT Pipelines</span></span>
<span data-ttu-id="63b0e-103">Procédez comme suit pour créer et déployer des pipelines SWIFT pour message repair et nouvelle soumission, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="63b0e-103">Perform the following steps to create and deploy SWIFT pipelines for message repair and new submission, as shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-pipeline-configuration.gif "A4SWIFT_Pipeline_Configuration")  
  
 <span data-ttu-id="63b0e-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="63b0e-104">**Summary**</span></span>  
  
 <span data-ttu-id="63b0e-105">Déployer les schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="63b0e-105">Deploy the following schemas:</span></span>  
  
-   <span data-ttu-id="63b0e-106">Pipeline avec le désassembleur SWIFT de réception personnalisé.</span><span class="sxs-lookup"><span data-stu-id="63b0e-106">Custom receive pipeline with the SWIFT Disassembler.</span></span> <span data-ttu-id="63b0e-107">Définir les propriétés BRE Validation et de Validation XML sur True et la propriété de schéma d’en-tête SWIFT (None).</span><span class="sxs-lookup"><span data-stu-id="63b0e-107">Set BRE Validation and XML Validation properties to True, and the SWIFT Header Schema property to (None).</span></span>  
  
-   <span data-ttu-id="63b0e-108">Pipeline avec l’assembleur SWIFT d’envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="63b0e-108">Custom send pipeline with the SWIFT Assembler</span></span>  
  
### <a name="to-create-a-pipeline-project"></a><span data-ttu-id="63b0e-109">Pour créer un projet de pipeline</span><span class="sxs-lookup"><span data-stu-id="63b0e-109">To create a pipeline project</span></span>  
  
1.  <span data-ttu-id="63b0e-110">Dans Visual Studio, cliquez sur **fichier**, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-110">In Visual Studio, click **File**, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="63b0e-111">Dans la boîte de dialogue Nouveau projet, dans le **types de projet** volet, sélectionnez le **projets BizTalk** dossier.</span><span class="sxs-lookup"><span data-stu-id="63b0e-111">In the New Project dialog box, in the **Project types** pane, select the **BizTalk Projects** folder.</span></span>  
  
3.  <span data-ttu-id="63b0e-112">Dans le **modèles** volet, sélectionnez **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-112">In the **Templates** pane, select **Empty BizTalk Server Project**.</span></span>  
  
4.  <span data-ttu-id="63b0e-113">Dans le **nom** , tapez le nom souhaité pour le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="63b0e-113">In the **Name** box, type the name you want for the project name.</span></span>  
  
5.  <span data-ttu-id="63b0e-114">Dans le **Solution** boîte, sélectionnez **ajouter à la Solution**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-114">In the **Solution** box, select **Add to Solution**.</span></span> <span data-ttu-id="63b0e-115">Dans le **emplacement** , entrez l’emplacement du projet de schéma que vous avez créé dans la zone [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="63b0e-115">In the **Location** box, enter the location of the schema project that you created in [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span></span>  
  
6.  <span data-ttu-id="63b0e-116">Cliquez sur **OK** pour ouvrir le nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="63b0e-116">Click **OK** to open the new project.</span></span>  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="63b0e-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]Ajoute un nouveau projet à l’Explorateur de solutions et crée le dossier du projet et les fichiers dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="63b0e-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] adds a new project to Solution Explorer, and creates the project folder and files in the folder specified.</span></span>  
  
7.  <span data-ttu-id="63b0e-118">Créez et affectez un fichier de clé fort au projet.</span><span class="sxs-lookup"><span data-stu-id="63b0e-118">Create and assign a strong key file to the project.</span></span> <span data-ttu-id="63b0e-119">Pour plus d’informations, consultez « pour créer un projet SWIFT fort » dans [déploiement des schémas A4SWIFT](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="63b0e-119">For more information, see "To create a strong-named SWIFT project" in [Deploying A4SWIFT Schemas](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-schemas.md).</span></span>  
  
### <a name="to-add-a-custom-receive-pipeline"></a><span data-ttu-id="63b0e-120">Pour ajouter un pipeline de réception personnalisé</span><span class="sxs-lookup"><span data-stu-id="63b0e-120">To add a custom receive pipeline</span></span>  
  
1.  <span data-ttu-id="63b0e-121">Dans l’Explorateur de solutions, votre projet de pipeline avec le bouton droit, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-121">In Solution Explorer, right-click your pipeline project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="63b0e-122">Dans la boîte de dialogue Ajouter un nouvel élément, cliquez sur **fichiers de Pipeline** dans le volet des catégories, puis sélectionnez **Pipeline de réception** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="63b0e-122">In the Add New Item dialog box, click **Pipeline Files** in the Categories pane, and then select **Receive Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="63b0e-123">Dans le **nom** , tapez un nom pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="63b0e-123">In the **Name** box, type a name for the pipeline.</span></span>  
  
4.  <span data-ttu-id="63b0e-124">Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="63b0e-124">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
5.  <span data-ttu-id="63b0e-125">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** , puis **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-125">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.</span></span>  
  
6.  <span data-ttu-id="63b0e-126">À partir de la **boîte à outils des composants de Pipeline BizTalk**, faites glisser le **SWIFT désassembleur** à la **Déposer ici** zone ci-dessous le **désassembler** étape mettre en forme **le Concepteur de Pipeline BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-126">From the **BizTalk Pipeline Components Toolbox**, drag the **SWIFT Disassembler** to the **Drop Here** box below the **Disassemble** stage shape in **BizTalk Pipeline Designer**.</span></span> <span data-ttu-id="63b0e-127">Laissez le **SWIFT désassembleur** sélectionné dans le **le Concepteur de Pipeline BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-127">Leave the **SWIFT Disassembler** as selected in the **BizTalk Pipeline Designer**.</span></span>  
  
7.  <span data-ttu-id="63b0e-128">Dans **propriétés**, vérifiez que le **BRE Validation** et **Validation XML** propriétés sont définies sur **True**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-128">In **Properties**, verify that the **BRE Validation** and **XML Validation** properties are set to **True**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b0e-129">La propriété de schéma d’en-tête SWIFT doit être définie **(aucun)**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-129">The SWIFT Header Schema property should be set to **(None)**.</span></span>  
  
8.  <span data-ttu-id="63b0e-130">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **fichier**, puis **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-130">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then **Save All**.</span></span>  
  
### <a name="to-add-a-custom-send-pipeline"></a><span data-ttu-id="63b0e-131">Pour ajouter un pipeline d’envoi personnalisé</span><span class="sxs-lookup"><span data-stu-id="63b0e-131">To add a custom send pipeline</span></span>  
  
1.  <span data-ttu-id="63b0e-132">Dans l’Explorateur de solutions, cliquez sur le **SWIFTPipelines** de projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-132">In Solution Explorer, right-click the **SWIFTPipelines** project, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="63b0e-133">Dans la boîte de dialogue Ajouter un nouvel élément, vérifiez que **fichiers de Pipeline** est sélectionné dans le volet des catégories, puis sélectionnez **Pipeline d’envoi** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="63b0e-133">In the Add New Item dialog box, verify that **Pipeline Files** is selected in the Categories pane, and then select **Send Pipeline** from the Templates pane.</span></span>  
  
3.  <span data-ttu-id="63b0e-134">Dans le **nom** , tapez un nom pour le pipeline.</span><span class="sxs-lookup"><span data-stu-id="63b0e-134">In the **Name** box, type a name for the pipeline.</span></span>  
  
4.  <span data-ttu-id="63b0e-135">Cliquez sur **ajouter** pour ouvrir le pipeline vide dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="63b0e-135">Click **Add** to open the blank pipeline in BizTalk Pipeline Designer.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b0e-136">Un pipeline vide apparaît dans le Concepteur de Pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="63b0e-136">An empty pipeline appears in the BizTalk Pipeline Designer.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="63b0e-137">Ajoute le nouveau pipeline à l’Explorateur de solutions sous le projet SWIFTPipelines.</span><span class="sxs-lookup"><span data-stu-id="63b0e-137"> adds the new pipeline to Solution Explorer under the SWIFTPipelines project.</span></span>  
  
5.  <span data-ttu-id="63b0e-138">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **vue** , puis **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-138">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **View** and then **Toolbox**.</span></span>  
  
6.  <span data-ttu-id="63b0e-139">Dans le **boîte à outils des composants de Pipeline BizTalk**, faites glisser **SWIFT assembleur** à la **Déposer ici** zone ci-dessous le **assemblage** forme dans l’étape **Le Concepteur de Pipeline BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-139">In the **BizTalk Pipeline Components Toolbox**, drag **SWIFT Assembler** to the **Drop Here** box below the **Assemble** stage shape in **BizTalk Pipeline Designer**.</span></span>  
  
7.  <span data-ttu-id="63b0e-140">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur **fichier**, puis **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-140">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **File**, and then **Save All**.</span></span>  
  
8.  <span data-ttu-id="63b0e-141">Cliquez avec le bouton droit sur le projet de pipelines, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-141">Right click the pipelines project, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63b0e-142">Pendant le processus de compilation, vous ne devez pas voir les erreurs.</span><span class="sxs-lookup"><span data-stu-id="63b0e-142">During the compilation process, you should not see any failures.</span></span> <span data-ttu-id="63b0e-143">Si vous le faites, vérifiez la source de l’erreur, corrigez-la et puis générez à nouveau le projet.</span><span class="sxs-lookup"><span data-stu-id="63b0e-143">If you do, check the source of the error, correct it and then re-build the project.</span></span> <span data-ttu-id="63b0e-144">Toutefois, vous voyez les avertissements.</span><span class="sxs-lookup"><span data-stu-id="63b0e-144">You may, however, see warnings.</span></span> <span data-ttu-id="63b0e-145">Vous pouvez corriger la condition des avertissements.</span><span class="sxs-lookup"><span data-stu-id="63b0e-145">You can correct the condition leading to the warnings.</span></span> <span data-ttu-id="63b0e-146">Pour plus d’informations, consultez « Création d’un projet de pipeline peut générer des avertissements » dans [divers problèmes connus](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).</span><span class="sxs-lookup"><span data-stu-id="63b0e-146">For more information, see "Building a pipeline project may result in warnings" in [Miscellaneous Known Issues](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).</span></span>  
  
9. <span data-ttu-id="63b0e-147">Cliquez avec le bouton droit sur le projet de pipelines, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="63b0e-147">Right click the pipelines project, and then click **Deploy**.</span></span>