---
title: MQSSendPipelineComponent (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, MQSeries adapters
- pipelines, examples
- MQSeries adapters, examples
- examples, pipelines
ms.assetid: ac709e45-524b-45ab-9673-060790ecbed2
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 256731dbb6194aa1962d62ec9fdbe58a0fd60e03
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqssendpipelinecomponent-biztalk-server-sample"></a><span data-ttu-id="1ae57-102">MQSSendPipelineComponent (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="1ae57-102">MQSSendPipelineComponent (BizTalk Server Sample)</span></span>
<span data-ttu-id="1ae57-103">Cet exemple montre comment écrire un composant de pipeline capable de lire un ensemble de valeurs de propriétés MQSeries à partir d'un fichier XML et de les appliquer à un message.</span><span class="sxs-lookup"><span data-stu-id="1ae57-103">This sample demonstrates how to write a pipeline component that reads a set of MQSeries property values from an XML file and applies them to a message.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="1ae57-104">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="1ae57-104">What This Sample Does</span></span>  
 <span data-ttu-id="1ae57-105">Cet exemple est constitué de deux projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] : un projet de composant de pipeline et un projet de pipeline utilisant le composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-105">This sample is composed of two [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] projects, a pipeline component project and a pipeline project that makes use of the pipeline component.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="1ae57-106">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="1ae57-106">Where to Find This Sample</span></span>  
  
-   <span data-ttu-id="1ae57-107">*\<Cheminaccèsexemples >*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent</span><span class="sxs-lookup"><span data-stu-id="1ae57-107">*\<SamplesPath>*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyComponent</span></span>  
  
-   <span data-ttu-id="1ae57-108">*\<Cheminaccèsexemples >*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline</span><span class="sxs-lookup"><span data-stu-id="1ae57-108">*\<SamplesPath>*\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\SetMQSeriesHeaderPropertyPipeline</span></span>  
  
 <span data-ttu-id="1ae57-109">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="1ae57-109">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="1ae57-110">**Fichier**</span><span class="sxs-lookup"><span data-stu-id="1ae57-110">**File**</span></span>|<span data-ttu-id="1ae57-111">**Description**</span><span class="sxs-lookup"><span data-stu-id="1ae57-111">**Description**</span></span>|  
|--------------|---------------------|  
|<span data-ttu-id="1ae57-112">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,</span><span class="sxs-lookup"><span data-stu-id="1ae57-112">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln,</span></span><br /><br /> <span data-ttu-id="1ae57-113">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj</span><span class="sxs-lookup"><span data-stu-id="1ae57-113">SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.csproj</span></span>|<span data-ttu-id="1ae57-114">Fichiers projet et solution du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-114">The project and solution files for the pipeline component.</span></span>|  
|<span data-ttu-id="1ae57-115">SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs</span><span class="sxs-lookup"><span data-stu-id="1ae57-115">SetMQSeriesHeaderPropertyComponent\CSetMQSeriesHeaderPropertyComponent.cs</span></span>|<span data-ttu-id="1ae57-116">Fichier source Visual C#® du composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-116">The Visual C#® source file for the pipeline component.</span></span>|  
|<span data-ttu-id="1ae57-117">SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml</span><span class="sxs-lookup"><span data-stu-id="1ae57-117">SetMQSeriesHeaderPropertyComponent\SetMQSMQMDHdrProps.xml</span></span>|<span data-ttu-id="1ae57-118">Propriétés MQSeries lues et utilisées par le composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-118">The MQSeries properties read and used by the pipeline component.</span></span>|  
|<span data-ttu-id="1ae57-119">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,</span><span class="sxs-lookup"><span data-stu-id="1ae57-119">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btproj,</span></span><br /><br /> <span data-ttu-id="1ae57-120">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln</span><span class="sxs-lookup"><span data-stu-id="1ae57-120">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln</span></span>|<span data-ttu-id="1ae57-121">Fichiers projet et solution du pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1ae57-121">The project and solution files for the BizTalk pipeline.</span></span>|  
|<span data-ttu-id="1ae57-122">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk</span><span class="sxs-lookup"><span data-stu-id="1ae57-122">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.snk</span></span>|<span data-ttu-id="1ae57-123">Fichier de clé de nom fort du projet de pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1ae57-123">The strong naming key file for the BizTalk pipeline project.</span></span>|  
|<span data-ttu-id="1ae57-124">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp</span><span class="sxs-lookup"><span data-stu-id="1ae57-124">SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.btp</span></span>|<span data-ttu-id="1ae57-125">Pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-125">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="1ae57-126">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="1ae57-126">How to Use This Sample</span></span>  
 <span data-ttu-id="1ae57-127">Pour créer l'application, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ae57-127">To create the application, you must complete the following steps:</span></span>  
  
1.  <span data-ttu-id="1ae57-128">Créez les dossiers pour l'application.</span><span class="sxs-lookup"><span data-stu-id="1ae57-128">Create the folders for the application.</span></span>  
  
2.  <span data-ttu-id="1ae57-129">Modifiez et compilez le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-129">Modify and compile the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the pipeline component.</span></span>  
  
3.  <span data-ttu-id="1ae57-130">Copiez l'assembly compilé et le fichier d'en-tête dans les dossiers appropriés.</span><span class="sxs-lookup"><span data-stu-id="1ae57-130">Copy the compiled assembly and the header file to the appropriate folders.</span></span>  
  
4.  <span data-ttu-id="1ae57-131">Modifiez le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-131">Modify the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.</span></span>  
  
5.  <span data-ttu-id="1ae57-132">Compilez et déployez le projet de pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-132">Compile and deploy the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline project.</span></span>  
  
6.  <span data-ttu-id="1ae57-133">Configurez un emplacement de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-133">Set up a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location.</span></span>  
  
7.  <span data-ttu-id="1ae57-134">Créez une file d'attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="1ae57-134">Create a MQSeries queue.</span></span>  
  
8.  <span data-ttu-id="1ae57-135">Configurez un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1ae57-135">Set up a send port.</span></span>  
  
9. <span data-ttu-id="1ae57-136">Activez l'emplacement de réception et démarrez le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1ae57-136">Enable the receive location and start the send port.</span></span>  
  
## <a name="creating-the-folders-for-the-application"></a><span data-ttu-id="1ae57-137">Création des dossiers pour l'application</span><span class="sxs-lookup"><span data-stu-id="1ae57-137">Creating the Folders for the Application</span></span>  
 <span data-ttu-id="1ae57-138">Cette procédure permet de créer les dossiers appropriés pour l'application.</span><span class="sxs-lookup"><span data-stu-id="1ae57-138">This procedure creates the appropriate folders for the application.</span></span>  
  
#### <a name="to-create-the-folders-for-the-application"></a><span data-ttu-id="1ae57-139">Pour créer les dossiers pour l'application</span><span class="sxs-lookup"><span data-stu-id="1ae57-139">To create the folders for the application</span></span>  
  
1.  <span data-ttu-id="1ae57-140">Créez un dossier nommé **temp** sur votre lecteur C:\ si elle n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="1ae57-140">Create a folder named **temp** on your C:\ drive if it does not already exist.</span></span>  
  
2.  <span data-ttu-id="1ae57-141">Créez un dossier sous le **C:\temp** répertoire nommé **Pickup3**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-141">Create a folder under the **C:\temp** directory named **Pickup3**.</span></span>  
  
## <a name="modifying-and-compiling-the-project-for-the-pipeline-component"></a><span data-ttu-id="1ae57-142">Modification et compilation du projet pour le composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="1ae57-142">Modifying and Compiling the Project for the Pipeline Component</span></span>  
 <span data-ttu-id="1ae57-143">Cette procédure permet de modifier et de compiler le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-143">This procedure modifies and compiles the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the pipeline component.</span></span>  
  
#### <a name="to-modify-and-compile-the-project-for-the-pipeline-component"></a><span data-ttu-id="1ae57-144">Pour modifier et compiler le projet pour le composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="1ae57-144">To modify and compile the project for the pipeline component</span></span>  
  
1.  <span data-ttu-id="1ae57-145">Double-cliquez sur le fichier solution **setmqseriesheaderpropertycomponent\setmqseriesheaderpropertycomponent.sln** pour ouvrir la solution dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-145">Double-click the solution file, **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent.sln** to open the solution in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="1ae57-146">Double-cliquez sur le fichier de classe **CSetMQSeriesHeaderPropertyComponent.cs** pour ouvrir le fichier de classe dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-146">Double-click the class file **CSetMQSeriesHeaderPropertyComponent.cs** to open the class file in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
3.  <span data-ttu-id="1ae57-147">Recherchez la variable **samplesDir**, vérifiez que cette variable est définie à l’emplacement **C:\temp**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-147">Locate the variable **samplesDir**, verify that this variable is set to the location **C:\temp**.</span></span>  
  
4.  <span data-ttu-id="1ae57-148">Avec le bouton droit de la solution dans l’Explorateur de solutions, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-148">Right-click the solution in the Solution Explorer and click **Build**.</span></span> <span data-ttu-id="1ae57-149">Cela sera compilé le projet dans une dll située dans le **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\**  active.</span><span class="sxs-lookup"><span data-stu-id="1ae57-149">This will compile the project into a dll located in the **SetMQSeriesHeaderPropertyComponent\SetMQSeriesHeaderPropertyComponent\bin\Debug\\** directory.</span></span>  
  
## <a name="copying-the-assembly-and-header-file-to-appropriate-folders"></a><span data-ttu-id="1ae57-150">Copie de l'assembly et du fichier d'en-tête dans les dossiers appropriés</span><span class="sxs-lookup"><span data-stu-id="1ae57-150">Copying the Assembly and Header File to Appropriate Folders</span></span>  
 <span data-ttu-id="1ae57-151">Cette procédure permet de copier l'assembly compilé et le fichier d'en-tête dans les dossiers appropriés.</span><span class="sxs-lookup"><span data-stu-id="1ae57-151">This procedure copies the compiled assembly and the header file to the appropriate folders.</span></span>  
  
#### <a name="to-copy-the-compiled-assembly-and-header-file-to-the-appropriate-folders"></a><span data-ttu-id="1ae57-152">Pour copier l'assembly compilé et le fichier d'en-tête dans les dossiers appropriés</span><span class="sxs-lookup"><span data-stu-id="1ae57-152">To copy the compiled assembly and header file to the appropriate folders</span></span>  
  
1.  <span data-ttu-id="1ae57-153">Copiez l’assembly compilé **SetMQSeriesHeaderPropertyComponent.dll** dans le dossier composants de pipeline BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1ae57-153">Copy the compiled assembly **SetMQSeriesHeaderPropertyComponent.dll** to the BizTalk pipeline components folder.</span></span> <span data-ttu-id="1ae57-154">Par défaut, le dossier des composants de pipeline BizTalk se trouve à l'emplacement suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-154">The default location for the BizTalk pipeline components folder is [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Pipeline Components.</span></span>  
  
2.  <span data-ttu-id="1ae57-155">Copiez le fichier de propriétés MQHeader **SetMQSMQMDHdrProps.xml** à la **C:\temp** active.</span><span class="sxs-lookup"><span data-stu-id="1ae57-155">Copy the MQHeader properties file **SetMQSMQMDHdrProps.xml** to the **C:\temp** directory.</span></span>  
  
## <a name="modifying-the-project-for-the-biztalk-server-pipeline"></a><span data-ttu-id="1ae57-156">Modification du projet pour le pipeline BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1ae57-156">Modifying the Project for the BizTalk Server Pipeline</span></span>  
 <span data-ttu-id="1ae57-157">Cette procédure permet de modifier le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour le pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-157">This procedure modifies the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline.</span></span>  
  
#### <a name="to-modify-the-project-for-the-biztalk-server-pipeline"></a><span data-ttu-id="1ae57-158">Pour modifier le projet pour le pipeline BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="1ae57-158">To modify the project for the BizTalk Server pipeline</span></span>  
  
1.  <span data-ttu-id="1ae57-159">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez la solution en double-cliquant sur le fichier solution **setmqseriesheaderpropertypipeline\setmqseriesheaderpropertypipeline.sln**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-159">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution by double-clicking the solution file, **SetMQSeriesHeaderPropertyPipeline\SetMQSeriesHeaderPropertyPipeline.sln**.</span></span>  
  
2.  <span data-ttu-id="1ae57-160">Créez un fichier de clé de nom fort pour le projet.</span><span class="sxs-lookup"><span data-stu-id="1ae57-160">Create a strong name key file for the project.</span></span> <span data-ttu-id="1ae57-161">Pour ce faire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ae57-161">To do that, do the following:</span></span>  
  
    1.  <span data-ttu-id="1ae57-162">Ouvrez une invite de commandes [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-162">Open a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Command prompt.</span></span>  
  
    2.  <span data-ttu-id="1ae57-163">Remplacez les répertoires par \<Cheminaccèsexemples > \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent.</span><span class="sxs-lookup"><span data-stu-id="1ae57-163">Change directories to \<SamplesPath>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent.</span></span>  
  
    3.  <span data-ttu-id="1ae57-164">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="1ae57-164">Type the following:</span></span>  
  
         `sn -k MQSSendPipelineComponent.snk`  
  
    4.  <span data-ttu-id="1ae57-165">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="1ae57-165">Press ENTER.</span></span> <span data-ttu-id="1ae57-166">Le fichier de clé sera ainsi créé.</span><span class="sxs-lookup"><span data-stu-id="1ae57-166">This will create the key file.</span></span>  
  
3.  <span data-ttu-id="1ae57-167">Dans **l’Explorateur de solutions**, cliquez sur le projet, cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet (dans le centre de la fenêtre).</span><span class="sxs-lookup"><span data-stu-id="1ae57-167">In **Solution Explorer**, right-click the project and click **Properties** to launch Project Designer for the project (in the center window).</span></span>  
  
    1.  <span data-ttu-id="1ae57-168">Dans le Concepteur de projets, cliquez sur **signature** onglet.</span><span class="sxs-lookup"><span data-stu-id="1ae57-168">In the Project Designer, click **Signing** tab.</span></span>  
  
    2.  <span data-ttu-id="1ae57-169">Dans le volet droit, sélectionnez le **signer l’assembly** option...</span><span class="sxs-lookup"><span data-stu-id="1ae57-169">In the right-hand pane, select the **Sign the assembly** option..</span></span>  
  
    3.  <span data-ttu-id="1ae57-170">Cliquez sur la liste déroulante pour le **choisir un fichier de clé de nom fort** option, puis cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-170">Click drop-down list for the **Choose a strong name key file** option, and click **Browse**.</span></span>  
  
    4.  <span data-ttu-id="1ae57-171">Accédez à \<Cheminaccèsexemples > \AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-171">Browse to \<SamplesPath>\AdaptersUsage\MQSeriesAdapter\MQSSendPipelineComponent\MQSSendPipelineComponent.snk, click **Open**.</span></span>  
  
4.  <span data-ttu-id="1ae57-172">Le composant de pipeline que vous avez créé précédemment est déjà ajouté à la **préassembler** stade de ce projet de pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-172">The pipeline component that you created earlier is already added to the **Pre-Assemble** stage of this pipeline project.</span></span> <span data-ttu-id="1ae57-173">Si ce composant n'était pas déjà ajouté, vous devriez procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ae57-173">If this component was not already added you would need to complete the following steps to add it:</span></span>  
  
    1.  <span data-ttu-id="1ae57-174">Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE, cliquez sur le **boîte à outils** onglet sur le côté gauche.</span><span class="sxs-lookup"><span data-stu-id="1ae57-174">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] IDE, click the **Toolbox** tab on the left side.</span></span>  
  
    2.  <span data-ttu-id="1ae57-175">Cliquez sur le **boîte à outils**, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-175">Right-click the **Toolbox**, and click **Choose Items**.</span></span>  
  
    3.  <span data-ttu-id="1ae57-176">Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** onglet, sélectionnez le **Custom Component to Set MQseries propriétés d’en-tête**composant, et puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-176">In the **Choose Toolbox Items** dialog box, click the **BizTalk Pipeline Components** tab, select the **Custom Component to Set MQseries header properties**component, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="1ae57-177">Faites glisser le **Custom Component to Set MQseries propriétés d’en-tête**composant le **préassembler** stade de ce pipeline.</span><span class="sxs-lookup"><span data-stu-id="1ae57-177">Drag the **Custom Component to Set MQseries header properties**component to the **Pre-Assemble** stage of this pipeline.</span></span>  
  
## <a name="compiling-and-deploying-the-pipeline-project"></a><span data-ttu-id="1ae57-178">Compilation et déploiement du projet de pipeline</span><span class="sxs-lookup"><span data-stu-id="1ae57-178">Compiling and Deploying the Pipeline Project</span></span>  
 <span data-ttu-id="1ae57-179">Cette procédure permet de compiler et de déployer le projet de pipeline [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-179">This procedure compiles and deploys the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipeline project.</span></span>  
  
#### <a name="to-compile-and-deploy-the-pipeline-project"></a><span data-ttu-id="1ae57-180">Pour compiler et déployer le projet de pipeline</span><span class="sxs-lookup"><span data-stu-id="1ae57-180">To compile and deploy the pipeline project</span></span>  
  
1.  <span data-ttu-id="1ae57-181">Dans la fenêtre Explorateur de solutions, cliquez sur la solution, puis cliquez sur **déployer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-181">In the Solution Explorer window, right-click the solution, and then click **Deploy Solution**.</span></span> <span data-ttu-id="1ae57-182">La solution est alors générée et l'assembly est déployé dans la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1ae57-182">This builds the solution and deploys the assembly to the BizTalk Management database.</span></span>  
  
2.  <span data-ttu-id="1ae57-183">Vérifiez que l'assembly a été déployé dans la base de données de gestion BizTalk :</span><span class="sxs-lookup"><span data-stu-id="1ae57-183">Verify the Assembly was deployed to the BizTalk Management database:</span></span>  
  
    1.  <span data-ttu-id="1ae57-184">Ouvrez la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1ae57-184">Open the BizTalk Administration Console.</span></span>  
  
    2.  <span data-ttu-id="1ae57-185">Cliquez pour développer **groupe BizTalk [\<nom_serveur > :\<base de données de gestion >]**, puis cliquez pour développer le **assemblys** dossier.</span><span class="sxs-lookup"><span data-stu-id="1ae57-185">Click to expand **BizTalk Group [\<servername>:\<management database>]**, and then click to expand the **Assemblies** folder.</span></span>  
  
         <span data-ttu-id="1ae57-186">L’assembly de pipeline déployé doit être visible sous le **assemblys** dossier.</span><span class="sxs-lookup"><span data-stu-id="1ae57-186">The deployed pipeline assembly should be visible under the **Assemblies** folder.</span></span>  
  
## <a name="creating-the-receive-location"></a><span data-ttu-id="1ae57-187">Création de l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="1ae57-187">Creating the Receive Location</span></span>  
 <span data-ttu-id="1ae57-188">Cette procédure permet de créer un emplacement de réception [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1ae57-188">This procedure creates a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location.</span></span>  
  
#### <a name="to-create-the-receive-location"></a><span data-ttu-id="1ae57-189">Pour créer l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="1ae57-189">To create the receive location</span></span>  
  
1.  <span data-ttu-id="1ae57-190">Dans la Console Administration de BizTalk Server, cliquez sur **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-190">In the BizTalk Server Administration Console, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="1ae57-191">Dans le **propriétés du Port de réception unidirectionnel** boîte de dialogue le **nom** tapez « MQReply », puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-191">In the **One-way Receive Port Properties** dialog box, in the **Name** box type "MQReply" and click **OK**.</span></span>  
  
3.  <span data-ttu-id="1ae57-192">Dans le volet gauche, cliquez sur **emplacements de réception** onglet, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-192">In the left pane, click **Receive Locations** tab, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="1ae57-193">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **nom** , tapez « ReceiveFile ».</span><span class="sxs-lookup"><span data-stu-id="1ae57-193">In the **Receive Location Properties** dialog box, in the **Name** field, type "ReceiveFile".</span></span>  
  
5.  <span data-ttu-id="1ae57-194">Dans le **Type de Transport** boîte, sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-194">In the **Transport Type** box, select **FILE**.</span></span>  
  
6.  <span data-ttu-id="1ae57-195">Dans le **Gestionnaire de réception** champ, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-195">In the **Receive Handler** field, select **BizTalkServerApplication**.</span></span>  
  
7.  <span data-ttu-id="1ae57-196">Dans le **pipeline de réception** champ, sélectionnez **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-196">In the **Receive pipeline** field, select **Microsoft.BizTalk.DefaultPipelines.PassThruReceive**.</span></span>  
  
8.  <span data-ttu-id="1ae57-197">Dans le **dossier de réception** , tapez « C:\temp\Pickup3 ».</span><span class="sxs-lookup"><span data-stu-id="1ae57-197">In the **Receive folder** field, type "C:\temp\Pickup3".</span></span>  
  
9. <span data-ttu-id="1ae57-198">Dans le **masque de fichier** , tapez « *.\*».</span><span class="sxs-lookup"><span data-stu-id="1ae57-198">In the **File mask** field, type "*.\*".</span></span>  
  
10. <span data-ttu-id="1ae57-199">Cliquez sur **OK**, puis cliquez sur **OK** pour quitter le **propriétés de l’emplacement de réception** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1ae57-199">Click **OK**, and then click **OK** again to exit the **Receive Location Properties** dialog box.</span></span>  
  
## <a name="creating-a-mqseries-queue-through-the-mqseries-explorer"></a><span data-ttu-id="1ae57-200">Création d'une file d'attente MQSeries à l'aide de MQSeries Explorer</span><span class="sxs-lookup"><span data-stu-id="1ae57-200">Creating a MQSeries Queue Through the MQSeries Explorer</span></span>  
 <span data-ttu-id="1ae57-201">Si vous avez les autorisations requises pour le serveur MQSeries pour l’installation de Windows, vous pouvez créer la file d’attente MQSeries via les boîtes de dialogue de l’adaptateur et ignorez cette procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="1ae57-201">If you have the required permissions to the MQSeries Server for Windows installation, you can create the MQSeries queue through the adapter dialog boxes, and can skip this next procedure.</span></span>  
  
 <span data-ttu-id="1ae57-202">Sinon, vous pouvez utiliser la procédure suivante pour créer les files d'attente à l'aide d'IBM WebSphere MQ Explorer.</span><span class="sxs-lookup"><span data-stu-id="1ae57-202">If you do not have such access, you can use the following procedure to create the queue using the IBM WebSphere MQ Explorer.</span></span>  
  
#### <a name="to-create-a-mqseries-queue-through-the-mqseries-explorer"></a><span data-ttu-id="1ae57-203">Pour créer une file d'attente MQSeries à l'aide de MQSeries Explorer</span><span class="sxs-lookup"><span data-stu-id="1ae57-203">To create a MQSeries queue through the MQSeries Explorer</span></span>  
  
1.  <span data-ttu-id="1ae57-204">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **IBM WebSphere MQ**, puis cliquez sur **WebSphere MQ Explorer**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-204">Click **Start**, point to **Programs**, point to **IBM WebSphere MQ**, and then click **WebSphere MQ Explorer**.</span></span>  
  
2.  <span data-ttu-id="1ae57-205">Double-cliquez sur **gestionnaires de file d’attente**, puis double-cliquez sur le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ae57-205">Double-click **Queue Managers**, and then double-click the default queue manager.</span></span> <span data-ttu-id="1ae57-206">Le Gestionnaire de file d’attente par défaut est généralement nommé **QM_**\<*Nom_Ordinateur*> où *Nom_Ordinateur* est le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1ae57-206">The default queue manager is typically named **QM_**\<*machine_name*> where *machine_name* is the name of your computer.</span></span>  
  
3.  <span data-ttu-id="1ae57-207">Avec le bouton droit **les files d’attente**, pointez sur **nouveau**, puis cliquez sur **file d’attente locale**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-207">Right-click **Queues**, point to **New**, and then click **Local Queue**.</span></span>  
  
4.  <span data-ttu-id="1ae57-208">Dans **créer une file d’attente locale** boîte de dialogue **nom de la file d’attente**, type **SETHEADER**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-208">In **Create Local Queue** dialog box, in **Queue Name**, type **SETHEADER**, and then click **OK**.</span></span>  
  
## <a name="creating-the-send-port-and-mqseries-queue"></a><span data-ttu-id="1ae57-209">Création du port d'envoi et de la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="1ae57-209">Creating the Send Port and MQSeries Queue</span></span>  
 <span data-ttu-id="1ae57-210">Cette procédure permet de créer le port d'envoi pour le message sortant.</span><span class="sxs-lookup"><span data-stu-id="1ae57-210">This procedure creates the send port for the output message.</span></span> <span data-ttu-id="1ae57-211">Le cas échéant, la file d'attente MQSeries est également créée lorsque vous créez le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1ae57-211">The MQSeries queue is also created when you create the send port if you have not already created it.</span></span>  
  
#### <a name="to-create-the-send-port-and-mqseries-queue"></a><span data-ttu-id="1ae57-212">Pour créer le port d'envoi et la file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="1ae57-212">To create the send port and MQSeries queue</span></span>  
  
1.  <span data-ttu-id="1ae57-213">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-213">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="1ae57-214">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez « MQSolicitResponse ».</span><span class="sxs-lookup"><span data-stu-id="1ae57-214">In the **Send Port Properties** dialog box, in the **Name** box, type "MQSolicitResponse".</span></span>  
  
3.  <span data-ttu-id="1ae57-215">Dans le **Type de Transport** boîte, sélectionnez **MQSeries**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-215">In the **Transport Type** box, select **MQSeries**.</span></span>  
  
4.  <span data-ttu-id="1ae57-216">Dans le **pipeline d’envoi** boîte, sélectionnez **SetMQSeriesHeaderPropertyPipeline.SetMQSeriesHeadersSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-216">In the **Send pipeline** box, select **SetMQSeriesHeaderPropertyPipeline.SetMQSeriesHeadersSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="1ae57-217">Dans **filtres**, ajouter une nouvelle entrée avec les paires nom/valeur suivantes :</span><span class="sxs-lookup"><span data-stu-id="1ae57-217">In **Filters**, add a new entry with the following name/value pairs:</span></span>  
  
    -   <span data-ttu-id="1ae57-218">Définissez **propriété** à « BizTalk Server. ReceivePortName ».</span><span class="sxs-lookup"><span data-stu-id="1ae57-218">Set **Property** to "BTS.ReceivePortName".</span></span>  
  
    -   <span data-ttu-id="1ae57-219">Définissez **opérateur** à « == ».</span><span class="sxs-lookup"><span data-stu-id="1ae57-219">Set **Operator** to "==".</span></span>  
  
    -   <span data-ttu-id="1ae57-220">Définissez **valeur** sur « ReceiveFile ».</span><span class="sxs-lookup"><span data-stu-id="1ae57-220">Set **Value** to "ReceiveFile".</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="1ae57-221">Le port d'envoi sera ainsi configuré pour s'abonner aux messages qui arrivent sur le port de réception ReceiveFile.</span><span class="sxs-lookup"><span data-stu-id="1ae57-221">This sets the send port to subscribe to messages that arrive on the ReceiveFile receive port.</span></span>  
  
6.  <span data-ttu-id="1ae57-222">Cliquez sur **Transport**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-222">Click **Transport**.</span></span>  
  
7.  <span data-ttu-id="1ae57-223">Dans le **adresse (URI)** , cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="1ae57-223">In the **Address (URI)** field, click the ellipsis (…) button.</span></span>  
  
8.  <span data-ttu-id="1ae57-224">Dans le **propriétés du Transport MQSeries** boîte de dialogue le **définition file d’attente** , cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="1ae57-224">In the **MQSeries Transport Properties** dialog box, in the **Queue Definition** field, click the ellipsis (…) button.</span></span>  
  
9. <span data-ttu-id="1ae57-225">Dans le **définition file d’attente** boîte de dialogue le **nom du serveur** , tapez le nom de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1ae57-225">In the **Queue Definition** dialog box, in the **Server Name** field, type your computer name.</span></span>  
  
10. <span data-ttu-id="1ae57-226">Dans le **Gestionnaire de file d’attente** , sélectionnez le Gestionnaire de file d’attente par défaut.</span><span class="sxs-lookup"><span data-stu-id="1ae57-226">In the **Queue Manager** field, select the default queue manager.</span></span>  
  
11. <span data-ttu-id="1ae57-227">Dans le champ de la file d’attente, tapez « SETHEADER », puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-227">In the Queue field, type "SETHEADER", and then click **Export**.</span></span>  
  
12. <span data-ttu-id="1ae57-228">Dans le **exporter** boîte de dialogue, cliquez sur **créer une file d’attente**, puis cliquez sur **OK** ou **fait** jusqu'à ce que vous avez quitté la boîte de dialogue tous les.</span><span class="sxs-lookup"><span data-stu-id="1ae57-228">In the **Export** dialog box, click **Create Queue**, and then click **OK** or **Done** until you have exited all dialog.</span></span>  
  
## <a name="enabling-the-receive-location-and-starting-the-send-port"></a><span data-ttu-id="1ae57-229">L’activation de l’emplacement de réception et démarrer le Port d’envoi</span><span class="sxs-lookup"><span data-stu-id="1ae57-229">Enabling the Receive Location and Starting the Send Port</span></span>  
 <span data-ttu-id="1ae57-230">Cette procédure permet d'activer l'emplacement de réception et de démarrer le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="1ae57-230">This procedure enables the receive location and start the send port.</span></span>  
  
#### <a name="to-enable-the-receive-location-and-start-the-send-port"></a><span data-ttu-id="1ae57-231">Activation de l'emplacement de réception et démarrage du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="1ae57-231">To enable the receive location and start the send port</span></span>  
  
1.  <span data-ttu-id="1ae57-232">Dans la console Administration de BizTalk Server, cliquez sur **Ports de réception**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-232">In the BizTalk Server Administration console, click **Receive Ports**.</span></span>  
  
2.  <span data-ttu-id="1ae57-233">Dans le volet détails, cliquez sur le **MQIn** emplacement de réception et cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-233">In the details pane, right-click the **MQIn** receive location and click **Enable**.</span></span>  
  
3.  <span data-ttu-id="1ae57-234">Dans le volet détails, cliquez sur le **SetMQHeader** port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-234">In the details pane, right-click the **SetMQHeader** send port and click **Start**.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="1ae57-235">Test de l'application</span><span class="sxs-lookup"><span data-stu-id="1ae57-235">Testing the Application</span></span>  
 <span data-ttu-id="1ae57-236">Cette procédure permet de tester l'application.</span><span class="sxs-lookup"><span data-stu-id="1ae57-236">This procedure tests the application.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="1ae57-237">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="1ae57-237">To test the application</span></span>  
  
1.  <span data-ttu-id="1ae57-238">Placez un fichier dans le **C:\Temp\Pickup3** dossier.</span><span class="sxs-lookup"><span data-stu-id="1ae57-238">Put a file into the **C:\Temp\Pickup3** folder.</span></span>  
  
2.  <span data-ttu-id="1ae57-239">Lancez WebSphere MQ Explorer et double-cliquez sur la file d'attente SETHEADER pour examiner le ou les messages dans la file d'attente SETHEADER.</span><span class="sxs-lookup"><span data-stu-id="1ae57-239">Launch the WebSphere MQ Explorer and double-click the SETHEADER queue to examine the message(s) in the SETHEADER queue.</span></span>  
  
     <span data-ttu-id="1ae57-240">Pour afficher toutes les propriétés de contexte des messages dans la file d'attente SETHEADER, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="1ae57-240">To see all of the context properties for the messages in the SETHEADER queue, complete the following steps:</span></span>  
  
    1.  <span data-ttu-id="1ae57-241">Double-cliquez sur le **SETHEADER** file d’attente pour afficher les **Message Browser** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1ae57-241">Double-click the **SETHEADER** queue to display the **Message Browser** dialog box.</span></span>  
  
    2.  <span data-ttu-id="1ae57-242">Dans le **Message Browser** boîte de dialogue, cliquez sur **colonnes** pour afficher les **afficher/masquer les colonnes de Messages** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1ae57-242">In the **Message Browser** dialog box, click **Columns** to display the **Show/Hide Columns for Messages** dialog box.</span></span>  
  
    3.  <span data-ttu-id="1ae57-243">Sous **colonnes disponibles**, double-cliquez sur chaque entrée pour le rendre visible dans le **Message Browser** boîte de dialogue, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1ae57-243">Under **Available Columns**, double-click each entry to make it visible in the **Message Browser** dialog box, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="1ae57-244">Les propriétés de contexte de message pour chaque message doivent être visibles dans le **Message Browser** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1ae57-244">The message context properties for each message should be visible in the **Message Browser** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae57-245">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1ae57-245">See Also</span></span>  
 [<span data-ttu-id="1ae57-246">Exemples d’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="1ae57-246">MQSeries Adapter Samples</span></span>](../core/mqseries-adapter-samples.md)