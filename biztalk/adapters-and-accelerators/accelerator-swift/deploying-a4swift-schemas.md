---
title: "Déploiement de schémas d’A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, A4SWIFT
- deploying, A4SWIFT schemas
- A4SWIFT, deploying schemas
- schemas, deploying
ms.assetid: a6aed2cd-3578-442e-ab1e-8284cc5f7b72
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 331a21c64aa0130b3e110f1da6ca776f0b2c6a49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-a4swift-schemas"></a><span data-ttu-id="4a1b8-102">Déploiement de schémas d’A4SWIFT</span><span class="sxs-lookup"><span data-stu-id="4a1b8-102">Deploying A4SWIFT Schemas</span></span>
<span data-ttu-id="4a1b8-103">Vous devez déployer les schémas des messages SWIFT à échanger.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-103">You must deploy schemas for the SWIFT messages that you want to exchange.</span></span>  
  
 <span data-ttu-id="4a1b8-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="4a1b8-104">**Summary**</span></span>  
  
 <span data-ttu-id="4a1b8-105">Déployer les schémas suivants :</span><span class="sxs-lookup"><span data-stu-id="4a1b8-105">Deploy the following schemas:</span></span>  
  
-   <span data-ttu-id="4a1b8-106">Types.xsd Base SWIFT</span><span class="sxs-lookup"><span data-stu-id="4a1b8-106">SWIFT Base Types.xsd</span></span>  
  
-   <span data-ttu-id="4a1b8-107">SWIFT Types.xsd données communes</span><span class="sxs-lookup"><span data-stu-id="4a1b8-107">SWIFT Common Data Types.xsd</span></span>  
  
-   <span data-ttu-id="4a1b8-108">Schéma spécifique pour un type de message, par exemple, MT103.xsd</span><span class="sxs-lookup"><span data-stu-id="4a1b8-108">Specific schema for a message type, for example, MT103.xsd</span></span>  
  
### <a name="to-create-a-strong-named-swift-project"></a><span data-ttu-id="4a1b8-109">Pour créer un projet SWIFT avec nom fort</span><span class="sxs-lookup"><span data-stu-id="4a1b8-109">To create a strong-named SWIFT project</span></span>  
  
1.  <span data-ttu-id="4a1b8-110">Dans Visual Studio, cliquez sur **fichier**, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-110">In Visual Studio, click **File**, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="4a1b8-111">Dans la boîte de dialogue Nouveau projet, dans le **types de projet** volet, sélectionnez le **projets BizTalk** dossier.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-111">In the New Project dialog box, in the **Project types** pane, select the **BizTalk Projects** folder.</span></span>  
  
3.  <span data-ttu-id="4a1b8-112">Dans le **modèles** volet, sélectionnez **projet BizTalk Server vide**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-112">In the **Templates** pane, select **Empty BizTalk Server Project**.</span></span>  
  
4.  <span data-ttu-id="4a1b8-113">Dans le **nom** , tapez le nom souhaité pour le nom du projet.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-113">In the **Name** box, type the name you want for the project name.</span></span>  
  
5.  <span data-ttu-id="4a1b8-114">Dans le **Solution** boîte, sélectionnez **créer une nouvelle Solution**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-114">In the **Solution** box, select **Create new Solution**.</span></span> <span data-ttu-id="4a1b8-115">Dans le **emplacement** , entrez l’emplacement du projet que vous ajoutez au projet de schéma.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-115">In the **Location** box, enter the location of the project that you are adding the schema project to.</span></span>  
  
6.  <span data-ttu-id="4a1b8-116">Cliquez sur **OK** pour ouvrir le nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-116">Click **OK** to open the new project.</span></span>  
    [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="4a1b8-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]Ajoute un nouveau projet à l’Explorateur de solutions et crée le dossier du projet et les fichiers dans le dossier spécifié.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-117">[!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] adds a new project to Solution Explorer, and creates the project folder and files in the folder specified.</span></span>  
  
7.  <span data-ttu-id="4a1b8-118">Démarrez l’invite de commandes de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-118">Start Visual Studio command prompt.</span></span>  
  
8.  <span data-ttu-id="4a1b8-119">À l’invite de commandes Visual Studio, accédez à  **\<* lecteur*> : \Program Files\Microsoft BizTalk Accelerator pour SWIFT **.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-119">At the Visual Studio command prompt, browse to **\<*drive*>:\Program Files\Microsoft BizTalk Accelerator for SWIFT**.</span></span>  
  
9. <span data-ttu-id="4a1b8-120">À l’invite de commandes, tapez **sn – k key.snk**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-120">At the command prompt, type **sn –k key.snk**, and then press ENTER.</span></span> <span data-ttu-id="4a1b8-121">Vérifiez qu’un message s’affiche dans la fenêtre d’invite de commandes qui indique qu’une paire de clés a été écrite dans key.snk.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-121">Ensure that a message is displayed in the command-prompt window indicating that a key pair was written to key.snk.</span></span>  
  
10. <span data-ttu-id="4a1b8-122">Dans l’Explorateur de solutions, cliquez sur le nom de votre projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-122">In Solution Explorer, right-click your project name, and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="4a1b8-123">Dans le volet gauche de la **Pages de propriétés** boîte de dialogue, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-123">In the left pane of the **Property Pages** dialog box, click **Assembly**.</span></span>  
  
12. <span data-ttu-id="4a1b8-124">Dans le volet droit de la **Pages de propriétés** boîte de dialogue, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le points de suspension ().</span><span class="sxs-lookup"><span data-stu-id="4a1b8-124">In the right pane of the **Property Pages** dialog box, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis () button.</span></span>  
  
13. <span data-ttu-id="4a1b8-125">Dans le **fichier de clé d’Assembly** boîte de dialogue, accédez à  **\<* lecteur*> : \Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)], cliquez sur **key.snk** , puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-125">In the **Assembly Key File** dialog box, browse to **\<*drive*>:\Program Files\Microsoft**[!INCLUDE[btaA4SWIFTNoVersionui](../../includes/btaa4swiftnoversionui-md.md)], click **key.snk**, and then click **Open**.</span></span>  
  
14. <span data-ttu-id="4a1b8-126">Dans le **Pages de propriétés** boîte de dialogue, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-126">In the **Property Pages** dialog box, click **OK** to save your changes.</span></span>  
  
### <a name="to-add-a-swift-schema"></a><span data-ttu-id="4a1b8-127">Pour ajouter un schéma SWIFT</span><span class="sxs-lookup"><span data-stu-id="4a1b8-127">To add a SWIFT schema</span></span>  
  
1.  <span data-ttu-id="4a1b8-128">Dans l’Explorateur de solutions de Visual Studio, ouvrez votre projet.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-128">In Solution Explorer of Visual Studio, open your project.</span></span>  
  
2.  <span data-ttu-id="4a1b8-129">Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-129">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span>  
  
3.  <span data-ttu-id="4a1b8-130">Dans le **ajouter un élément existant** boîte de dialogue du :\\**programme Files\Microsoft BizTalk Accelerator pour SWIFT \<version > Message Pack\SWIFT Messages\A4SWIFT-SRG\< version > \Base schémas**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-130">In the **Add Existing Item** dialog box, in the :\\**Program Files\Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version>\Base Schemas**.</span></span> <span data-ttu-id="4a1b8-131">Sélectionnez le **SWIFT Base Types.xsd** et **Types.xsd de données courantes SWIFT** schémas, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-131">Select the **SWIFT Base Types.xsd** and **SWIFT Common Data Types.xsd** schemas, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="4a1b8-132">Avec le bouton droit de votre projet, pointez sur **ajouter**, puis cliquez sur **ajouter un élément existant**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-132">Right-click your project, point to **Add**, and then click **Add Existing Item**.</span></span>  
  
5.  <span data-ttu-id="4a1b8-133">Dans le **ajouter un élément existant** boîte de dialogue le **Regarder dans** zone déroulante, accédez à  **\<lecteur > : \Program Files\Microsoft BizTalk Accelerator pour SWIFT \< version > Message Pack\SWIFT Messages\A4SWIFT-SRG\<version > \Category n\MTxxx**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-133">In the **Add Existing Item** dialog box, in the **Look in** drop-down box, move to **\<drive>:\Program Files\Microsoft BizTalk Accelerator for SWIFT \<version> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version>\Category n\MTxxx**.</span></span> <span data-ttu-id="4a1b8-134">Sélectionnez un schéma pour un type de message, par exemple **MT103.xsd**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-134">Select a schema for a message type, for instance **MT103.xsd**, and then click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a1b8-135">A4SWIFT ajoute le schéma pour votre projet, comme indiqué dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-135">A4SWIFT adds the schema for your project, as shown in Solution Explorer.</span></span>  
  
6.  <span data-ttu-id="4a1b8-136">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-136">In Solution Explorer, right-click the project name, and then click **Build**.</span></span>  
  
7.  <span data-ttu-id="4a1b8-137">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**.</span><span class="sxs-lookup"><span data-stu-id="4a1b8-137">In Solution Explorer, right-click the project name, and then click **Deploy**.</span></span>