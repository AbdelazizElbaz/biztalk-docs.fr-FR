---
title: "SelectiveBindingImport (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- examples, applications
- binding files, examples
- examples, importing
- applications, binding files
- applications, examples
- applications, importing
- deploying, scripts
- examples, binding files
ms.assetid: 963bfc80-8cc4-4d90-96b4-e85ae04405cf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88e6a2aa02decf1e4ed9c4a9838077be0c3b97b2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="selectivebindingimport-application-deployment-sample"></a><span data-ttu-id="7968a-102">SelectiveBindingImport (exemple de déploiement d'application)</span><span class="sxs-lookup"><span data-stu-id="7968a-102">SelectiveBindingImport (Application Deployment Sample)</span></span>
<span data-ttu-id="7968a-103">Cette rubrique décrit l'utilisation de l'exemple SelectiveBindingImport.</span><span class="sxs-lookup"><span data-stu-id="7968a-103">This topic explains how to use the SelectiveBindingImport sample.</span></span> <span data-ttu-id="7968a-104">Cet exemple de script permet d'appliquer plusieurs liaisons à une application lorsque vous importez celle-ci dans différents environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="7968a-104">You can use this sample script to apply different bindings to an application when you import the application into different destination environments.</span></span> <span data-ttu-id="7968a-105">Vous pouvez utiliser cette approche pour importer les liaisons des fichiers de liaison stockés sur un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="7968a-105">You can use this approach when you want to import the bindings from binding files that are stored on a network share.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7968a-106">Si vous ne devez pas importer automatiquement les fichiers de liaison d'un partage réseau lors de l'importation de l'application, vous pouvez ajouter à l'application plusieurs fichiers de liaison dans lesquels différents environnements de destination sont spécifiés.</span><span class="sxs-lookup"><span data-stu-id="7968a-106">If you do not need to automatically import binding files from a network share during application import, you can add to the application different binding files that have different destination environments specified.</span></span> <span data-ttu-id="7968a-107">Lorsque vous importez l'application, vous pouvez spécifier l'environnement, de sorte que les liaisons pour cet environnement sont appliquées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="7968a-107">When you import the application, you can specify the environment, and the bindings for that environment will be applied automatically.</span></span> <span data-ttu-id="7968a-108">Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-108">For more information, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span>  
  
 <span data-ttu-id="7968a-109">Les applications BizTalk sont généralement déplacées entre les environnements de développement, de test, intermédiaire et de production.</span><span class="sxs-lookup"><span data-stu-id="7968a-109">BizTalk applications are typically moved from development to testing to staging and then to production environments.</span></span> <span data-ttu-id="7968a-110">Les liaisons utilisées au sein de ces environnements sont généralement différentes.</span><span class="sxs-lookup"><span data-stu-id="7968a-110">The bindings used in different environments are typically different.</span></span> <span data-ttu-id="7968a-111">Cet exemple permet d'appliquer les liaisons pour différents environnements comme suit :</span><span class="sxs-lookup"><span data-stu-id="7968a-111">Using this sample, you can apply bindings for different environments as follows:</span></span>  
  
1.  <span data-ttu-id="7968a-112">en plaçant les fichiers de liaison à utiliser dans un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="7968a-112">Placing all the binding files that you want to use on a network share.</span></span>  
  
2.  <span data-ttu-id="7968a-113">en ajoutant un script de post-traitement à l'application qui importera depuis cet emplacement le fichier de liaison correct pour l'environnement de destination particulier lors de l'importation de l'application.</span><span class="sxs-lookup"><span data-stu-id="7968a-113">Adding a post-processing script to the application that will import from this location the correct binding file for the particular destination environment during application import.</span></span> <span data-ttu-id="7968a-114">Le script détecte l'environnement en lisant la variable d'environnement %ENVIRONMENT% que vous définissez sur l'ordinateur local,</span><span class="sxs-lookup"><span data-stu-id="7968a-114">The script detects the environment by reading an environment variable named %ENVIRONMENT% that you set on the local computer,</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="7968a-115">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="7968a-115">What This Sample Does</span></span>  
 <span data-ttu-id="7968a-116">Cet exemple illustre l'importation sélective de fichiers de liaison d'un partage réseau à l'aide d'un script de post-traitement contenu dans un fichier .msi d'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7968a-116">This sample illustrates how to selectively import binding files from a network share by using a post-processing script contained in a BizTalk application .msi file.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="7968a-117">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="7968a-117">Where to Find This Sample</span></span>  
 <span data-ttu-id="7968a-118">Vous pouvez rechercher les dossiers et les fichiers sous  *\<exemples de chemin\>*\Application Deployment\SelectiveBindingImport :</span><span class="sxs-lookup"><span data-stu-id="7968a-118">You can find the following sample folders and files under *\<Samples Path\>*\Application Deployment\SelectiveBindingImport:</span></span>  
  
-   <span data-ttu-id="7968a-119">Develop (dossier)</span><span class="sxs-lookup"><span data-stu-id="7968a-119">Develop (Folder)</span></span>  
  
    -   <span data-ttu-id="7968a-120">Dev.xml</span><span class="sxs-lookup"><span data-stu-id="7968a-120">Dev.xml</span></span>  
  
-   <span data-ttu-id="7968a-121">Production (dossier)</span><span class="sxs-lookup"><span data-stu-id="7968a-121">Production (Folder)</span></span>  
  
    -   <span data-ttu-id="7968a-122">Production.xml</span><span class="sxs-lookup"><span data-stu-id="7968a-122">Production.xml</span></span>  
  
-   <span data-ttu-id="7968a-123">Staging (dossier)</span><span class="sxs-lookup"><span data-stu-id="7968a-123">Staging (Folder)</span></span>  
  
    -   <span data-ttu-id="7968a-124">Staging.xml</span><span class="sxs-lookup"><span data-stu-id="7968a-124">Staging.xml</span></span>  
  
-   <span data-ttu-id="7968a-125">Test (dossier)</span><span class="sxs-lookup"><span data-stu-id="7968a-125">Test (Folder)</span></span>  
  
    -   <span data-ttu-id="7968a-126">Test.xml</span><span class="sxs-lookup"><span data-stu-id="7968a-126">Test.xml</span></span>  
  
-   <span data-ttu-id="7968a-127">SelectiveBindings.bat</span><span class="sxs-lookup"><span data-stu-id="7968a-127">SelectiveBindings.bat</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="7968a-128">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="7968a-128">How to Use This Sample</span></span>  
 <span data-ttu-id="7968a-129">Les procédures suivantes permettent d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="7968a-129">Use the following procedures to run this sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7968a-130">Pour exécuter l’exemple</span><span class="sxs-lookup"><span data-stu-id="7968a-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="7968a-131">Exécutez **Build.Bat à partir de la  *\<exemples de chemin\>*\Application Deployment\CreateApp** active.</span><span class="sxs-lookup"><span data-stu-id="7968a-131">Run **Build.Bat from the *\<Samples Path\>*\Application Deployment\CreateApp** directory.</span></span> <span data-ttu-id="7968a-132">Cette opération crée les fichiers suivants dans le  *\<exemples de chemin\>*\Application Deployment\CreateApp\Dlls dossier : Schemas.dll, Maps.dll et Orchestrations.dll.</span><span class="sxs-lookup"><span data-stu-id="7968a-132">This creates the following files in the *\<Samples Path\>*\Application Deployment\CreateApp\Dlls folder: Schemas.dll, Maps.dll, and Orchestrations.dll.</span></span>  
  
2.  <span data-ttu-id="7968a-133">**Créer l’application.**</span><span class="sxs-lookup"><span data-stu-id="7968a-133">**Create the application.**</span></span> <span data-ttu-id="7968a-134">Dans la console Administration de BizTalk Server, créez une application, comme décrit dans [la création d’une Application](../core/how-to-create-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-134">In the BizTalk Server Administration console, create an application, as described in [How to Create an Application](../core/how-to-create-an-application.md).</span></span>  
  
3.  <span data-ttu-id="7968a-135">**Ajouter à l’application les fichiers .dll créés dans la première étape.**</span><span class="sxs-lookup"><span data-stu-id="7968a-135">**Add to the application the .dll files created in the first step.**</span></span> <span data-ttu-id="7968a-136">Pour obtenir des instructions, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-136">For instructions, see [How to Add a BizTalk Assembly to an Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).</span></span>  
  
4.  <span data-ttu-id="7968a-137">**Créez la variable d’environnement, comme suit :**</span><span class="sxs-lookup"><span data-stu-id="7968a-137">**Create the ENVIRONMENT variable, as follows:**</span></span>  
  
    1.  <span data-ttu-id="7968a-138">Dans le menu Démarrer, cliquez sur **poste** et cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7968a-138">On the Start menu, right-click **My Computer** and click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="7968a-139">Sur le **avancé** , cliquez sur **Variables d’environnement**.</span><span class="sxs-lookup"><span data-stu-id="7968a-139">On the **Advanced** tab, click **Environment Variables**.</span></span>  
  
    3.  <span data-ttu-id="7968a-140">Dans le **variables utilisateur** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="7968a-140">In the **User variables** section, click **New**.</span></span>  
  
    4.  <span data-ttu-id="7968a-141">Dans **nom de la Variable**, type **environnement**.</span><span class="sxs-lookup"><span data-stu-id="7968a-141">In **Variable name**, type **ENVIRONMENT**.</span></span>  
  
    5.  <span data-ttu-id="7968a-142">Dans **valeur de la Variable**, type sur des valeurs suivantes pour l’environnement : **développer**, **Production**, **intermédiaire**, ou **Test**.</span><span class="sxs-lookup"><span data-stu-id="7968a-142">In **Variable value**, type on of the following values for the environment: **Develop**, **Production**, **Staging**, or **Test**.</span></span> <span data-ttu-id="7968a-143">Ces valeurs respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="7968a-143">These values are case sensitive.</span></span>  
  
5.  <span data-ttu-id="7968a-144">Cliquez sur **OK** trois fois.</span><span class="sxs-lookup"><span data-stu-id="7968a-144">Click **OK** three times.</span></span>  
  
6.  <span data-ttu-id="7968a-145">**Copiez les fichiers de liaison vers un emplacement sur votre système de fichiers.**</span><span class="sxs-lookup"><span data-stu-id="7968a-145">**Copy the binding files to a location on your file system.**</span></span> <span data-ttu-id="7968a-146">Copiez les fichiers .xml de liaison des dossiers Develop, Test, Staging et Production dans un emplacement de votre système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="7968a-146">Copy the binding .xml files from the Develop, Test, Staging, and Production folders to a location on your file system.</span></span>  
  
7.  <span data-ttu-id="7968a-147">**Modifiez le script de post-traitement.**</span><span class="sxs-lookup"><span data-stu-id="7968a-147">**Edit the post-processing script.**</span></span> <span data-ttu-id="7968a-148">Modifiez le fichier SelectiveBindings.bat comme suit :</span><span class="sxs-lookup"><span data-stu-id="7968a-148">Edit SelectiveBindings.bat as follows:</span></span>  
  
    1.  <span data-ttu-id="7968a-149">**Spécifiez l’emplacement de fichier de liaison.**</span><span class="sxs-lookup"><span data-stu-id="7968a-149">**Specify the binding file location.**</span></span> <span data-ttu-id="7968a-150">Dans la ligne contenant BINDINGS_LOC, supprimez REM et indiquez le chemin d'accès à l'emplacement dans lequel vous avez copié les fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="7968a-150">In the line containing BINDINGS_LOC, delete REM, and provide the path to the location where you copied the binding files.</span></span>  
  
         <span data-ttu-id="7968a-151">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7968a-151">Example:</span></span>  
  
         <span data-ttu-id="7968a-152">BINDINGS_LOC=C:\MyBindings</span><span class="sxs-lookup"><span data-stu-id="7968a-152">BINDINGS_LOC=C:\MyBindings</span></span>  
  
    2.  <span data-ttu-id="7968a-153">**Spécifiez le nom de l’application.**</span><span class="sxs-lookup"><span data-stu-id="7968a-153">**Specify the application name.**</span></span> <span data-ttu-id="7968a-154">Dans la ligne contenant APPLICATION_NAME, supprimez REM et indiquez le nom de l'application dans laquelle importer les liaisons.</span><span class="sxs-lookup"><span data-stu-id="7968a-154">In the line containing APPLICATION_NAME, delete REM, and provide the name of the application into which you want to import the bindings.</span></span>  
  
         <span data-ttu-id="7968a-155">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7968a-155">Example:</span></span>  
  
         <span data-ttu-id="7968a-156">APPLICATION_Name=SelectiveBindingImport</span><span class="sxs-lookup"><span data-stu-id="7968a-156">APPLICATION_Name=SelectiveBindingImport</span></span>  
  
8.  <span data-ttu-id="7968a-157">**Ajoutez le script à l’application en tant que script de post-traitement.**</span><span class="sxs-lookup"><span data-stu-id="7968a-157">**Add the script to the application as a post-processing script.**</span></span> <span data-ttu-id="7968a-158">Pour obtenir des instructions, consultez [Ajout antérieur à la version ou un Script de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-158">For instructions, see [How to Add a Pre- or Post-processing Script to an Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).</span></span>  
  
9. <span data-ttu-id="7968a-159">**Exportez l’application.**</span><span class="sxs-lookup"><span data-stu-id="7968a-159">**Export the application.**</span></span> <span data-ttu-id="7968a-160">Pour obtenir des instructions, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-160">For instructions, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
10. <span data-ttu-id="7968a-161">**Supprimer l’application.**</span><span class="sxs-lookup"><span data-stu-id="7968a-161">**Delete the application.**</span></span> <span data-ttu-id="7968a-162">Pour obtenir des instructions, consultez [comment supprimer une Application BizTalk du groupe BizTalk](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-162">For instructions, see [How to Delete a BizTalk Application from the BizTalk Group](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).</span></span>  
  
11. <span data-ttu-id="7968a-163">**Importez l’application.**</span><span class="sxs-lookup"><span data-stu-id="7968a-163">**Import the application.**</span></span> <span data-ttu-id="7968a-164">Pour obtenir des instructions, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-164">For instructions, see [How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md).</span></span> <span data-ttu-id="7968a-165">Il n'est pas nécessaire de spécifier un environnement de destination.</span><span class="sxs-lookup"><span data-stu-id="7968a-165">You do not need to specify a destination environment.</span></span>  
  
12. <span data-ttu-id="7968a-166">**Vérifiez que le fichier de liaison approprié a été appliqué.**</span><span class="sxs-lookup"><span data-stu-id="7968a-166">**Verify that the right binding file was applied.**</span></span> <span data-ttu-id="7968a-167">Pour ce faire, vérifiez le champ de description des emplacements de réception comme suit :</span><span class="sxs-lookup"><span data-stu-id="7968a-167">You can do this by checking the description field of the receive locations, as follows:</span></span>  
  
    1.  <span data-ttu-id="7968a-168">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="7968a-168">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    2.  <span data-ttu-id="7968a-169">Dans l'arborescence de la console, développez successivement le groupe BizTalk, l'application BizTalk, puis le dossier Emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="7968a-169">In the console tree, expand the BizTalk group, the BizTalk application, and the Receive Locations folder.</span></span>  
  
    3.  <span data-ttu-id="7968a-170">Dans le volet droit, consultez la description des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="7968a-170">In the right pane, view the description of the receive locations.</span></span>  
  
13. <span data-ttu-id="7968a-171">**Installer l’application.**</span><span class="sxs-lookup"><span data-stu-id="7968a-171">**Install the application.**</span></span> <span data-ttu-id="7968a-172">Pour obtenir des instructions, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="7968a-172">For instructions, see [How to Install a BizTalk Application](../core/how-to-install-a-biztalk-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7968a-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7968a-173">See Also</span></span>  
 <span data-ttu-id="7968a-174">[Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="7968a-174">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="7968a-175">Déploiement des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="7968a-175">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)