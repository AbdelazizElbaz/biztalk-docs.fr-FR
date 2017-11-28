---
title: "CreateApp (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, examples
- deploying, .msi file
- deploying, exporting
- .msi files, deploying
- examples, deploying
ms.assetid: 825627ee-21d0-4505-9df4-1dadc51335b6
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 010c574c1c9c799d6235b9d10e3378b46c3d1548
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="createapp-application-deployment-sample"></a><span data-ttu-id="196e6-102">CreateApp (exemple de déploiement d'application)</span><span class="sxs-lookup"><span data-stu-id="196e6-102">CreateApp (Application Deployment Sample)</span></span>
<span data-ttu-id="196e6-103">Cette rubrique explique l'utilisation de l'exemple CreateApp qui illustre l'utilisation de l'outil de ligne de commande BTSTask pour déployer et annuler le déploiement d'une application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="196e6-103">This topic explains how to use the CreateApp sample, which demonstrates using the BTSTask command-line tool to deploy and undeploy a BizTalk application.</span></span> <span data-ttu-id="196e6-104">Vous pouvez utiliser des scripts, tels que ceux inclus dans cet exemple, pour automatiser votre processus de génération nocturne pour déployer et annuler le déploiement d'applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="196e6-104">You could use scripts such as those included in this sample to automate your nightly build process to deploy and undeploy BizTalk applications.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="196e6-105">Vous devez toujours écrire vos scripts de déploiement pour une exécution en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="196e6-105">You should always write your deployment scripts to run in silent mode.</span></span> <span data-ttu-id="196e6-106">Si vous ne le faites pas, des boîtes de dialogue s'affichent et nécessitent des saisies de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="196e6-106">If you do not, dialog boxes will display that require user input.</span></span> <span data-ttu-id="196e6-107">Cela arrête le processus de déploiement jusqu'à la fermeture manuelle de la boîte de dialogue, ce qui peut bloquer le processus d'importation.</span><span class="sxs-lookup"><span data-stu-id="196e6-107">This will stop the deployment process until the dialog box is manually dismissed, which can cause the import process to hang.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="196e6-108">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="196e6-108">What This Sample Does</span></span>  
 <span data-ttu-id="196e6-109">L'exemple inclut des scripts qui automatisent les tâches de déploiement d'applications.</span><span class="sxs-lookup"><span data-stu-id="196e6-109">The sample includes scripts that automate application deployment tasks.</span></span> <span data-ttu-id="196e6-110">Pour effectuer ces tâches, vous exécutez un script qui génère le projet et les fichiers BizTalk.</span><span class="sxs-lookup"><span data-stu-id="196e6-110">To perform these tasks, you run a script that generates the BizTalk project and files.</span></span> <span data-ttu-id="196e6-111">Ensuite, vous exécutez un script qui génère deux fichiers .msi d'application BizTalk : l'un contient tous les artefacts dans une application, l'autre contient uniquement un assembly dans l'application.</span><span class="sxs-lookup"><span data-stu-id="196e6-111">Then you run a script that generates two BizTalk application .msi files – an .msi file that contains all of the artifacts in an application, and another that contains only one assembly in the application.</span></span> <span data-ttu-id="196e6-112">Puis, vous exécutez un script qui utilise un fichier .msi pour importer une application dans un groupe BizTalk et installer l'application sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="196e6-112">Next you run a script that uses an .msi file to import an application into a BizTalk group and install the application onto the local computer.</span></span> <span data-ttu-id="196e6-113">Lors de l'installation, un script de pré-traitement inclus dans l'application crée des dossiers utilisés par l'application et consigne ses actions dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="196e6-113">During installation, a pre-processing script included in the application creates folders used by the application and logs its actions to a file.</span></span> <span data-ttu-id="196e6-114">Enfin, vous exécutez un script qui supprime et désinstalle l'application.</span><span class="sxs-lookup"><span data-stu-id="196e6-114">Finally, you run a script that deletes and uninstalls the application.</span></span> <span data-ttu-id="196e6-115">Lors de la désinstallation, un script de pré-traitement inclus dans l'application supprime les fichiers et dossiers créés durant l'installation et consigne ses actions dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="196e6-115">During uninstallation, a pre-processing script included in the application removes the files and folders that were created during installation and logs its actions to a file.</span></span>  
  
 <span data-ttu-id="196e6-116">Les scripts suivants sont inclus dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="196e6-116">The following are the scripts included with this sample:</span></span>  
  
-   <span data-ttu-id="196e6-117">**Build.bat.**</span><span class="sxs-lookup"><span data-stu-id="196e6-117">**Build.bat.**</span></span> <span data-ttu-id="196e6-118">Génère un fichier de clé, crée le projet dans Visual Studio et signe les fichiers .dll.</span><span class="sxs-lookup"><span data-stu-id="196e6-118">Generates a key file, builds the project in Visual Studio, and signs the .dll files.</span></span>  
  
-   <span data-ttu-id="196e6-119">**CreateFullAndPartialMSI.bat.**</span><span class="sxs-lookup"><span data-stu-id="196e6-119">**CreateFullAndPartialMSI.bat.**</span></span> <span data-ttu-id="196e6-120">Effectue les actions suivantes, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="196e6-120">Takes the following actions, in order:</span></span>  
  
    1.  <span data-ttu-id="196e6-121">Utilise l’outil BTSTask [commande AddApp](../core/addapp-command.md) pour créer une application.</span><span class="sxs-lookup"><span data-stu-id="196e6-121">Uses the BTSTask [AddApp command](../core/addapp-command.md) to create an application.</span></span>  
  
    2.  <span data-ttu-id="196e6-122">Utilise l’outil BTSTask [commande AddResource](../core/addresource-command.md) à ajouter à l’application trois assemblys BizTalk ainsi que d’autres ressources qui ont été générées par Build.bat.</span><span class="sxs-lookup"><span data-stu-id="196e6-122">Uses the BTSTask [AddResource command](../core/addresource-command.md) to add to the application three BizTalk assemblies as well as other resources that were generated by Build.bat.</span></span>  
  
    3.  <span data-ttu-id="196e6-123">Utilise l’outil BTSTask [commande ExportApp](../core/exportapp-command.md) pour exporter les artefacts de l’application dans un fichier .msi nommé CreateApplicationSample.msi.</span><span class="sxs-lookup"><span data-stu-id="196e6-123">Uses the BTSTask [ExportApp command](../core/exportapp-command.md) to export the application's artifacts into an .msi file named CreateApplicationSample.msi.</span></span>  
  
    4.  <span data-ttu-id="196e6-124">Utilise l’outil BTSTask [commande ListApp](../core/listapp-command.md) pour générer un manifeste d’application nommé AppManifest.xml, qui répertorie tous les artefacts contenus dans l’application.</span><span class="sxs-lookup"><span data-stu-id="196e6-124">Uses the BTSTask [ListApp Command](../core/listapp-command.md) to generate an application manifest named AppManifest.xml, which lists all of the artifacts contained in the application.</span></span>  
  
    5.  <span data-ttu-id="196e6-125">Utilise l’outil BTSTask [commande ExportApp](../core/exportapp-command.md) pour exporter uniquement l’assembly d’orchestrations dans un fichier .msi nommé CreateApplicationSamplePartial.msi.</span><span class="sxs-lookup"><span data-stu-id="196e6-125">Uses the BTSTask [ExportApp command](../core/exportapp-command.md) to export only the orchestrations assembly into an .msi file named CreateApplicationSamplePartial.msi.</span></span> <span data-ttu-id="196e6-126">Pour ce faire, ResourceSpecPartial.xml est fourni pour le paramètre ResourceSpec.</span><span class="sxs-lookup"><span data-stu-id="196e6-126">It does this by providing ResourceSpecPartial.xml for the ResourceSpec parameter.</span></span> <span data-ttu-id="196e6-127">ResouceSpecPartial.xml est une version modifiée de ResourceSpecComplete.xml qui a été fourni avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="196e6-127">ResouceSpecPartial.xml is an edited version of ResourceSpecComplete.xml that has been provided with this sample.</span></span> <span data-ttu-id="196e6-128">Ce fichier a été modifié afin de contenir une référence à l'assembly d'orchestrations uniquement.</span><span class="sxs-lookup"><span data-stu-id="196e6-128">This file has been edited so that it contains a reference to the orchestrations assembly only.</span></span> <span data-ttu-id="196e6-129">Lorsqu'il est fourni avec ce paramètre, BTSTask exporte uniquement les artefacts répertoriés dans le fichier ResourceSpecPartial.xml, en l'occurrence l'assembly d'orchestrations.</span><span class="sxs-lookup"><span data-stu-id="196e6-129">When provided with this parameter, BTSTask exports only the artifacts listed in the ResourceSpecPartial.xml file – in this case, the orchestrations assembly.</span></span>  
  
    6.  <span data-ttu-id="196e6-130">Supprime l'application de la base de données de gestion BizTalk pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="196e6-130">Deletes the application from the BizTalk Management database for the group.</span></span>  
  
-   <span data-ttu-id="196e6-131">**CreateNewAppFromMSI.bat.**</span><span class="sxs-lookup"><span data-stu-id="196e6-131">**CreateNewAppFromMSI.bat.**</span></span> <span data-ttu-id="196e6-132">Utilise CreateApplicationSample.msi généré par CreateFullAndPartialMSI.bat pour installer une application nommée CreateApplicationSample sur l’ordinateur local ainsi que pour importer l’application dans le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="196e6-132">Uses CreateApplicationSample.msi generated by CreateFullAndPartialMSI.bat to install an application named CreateApplicationSample on the local computer as well as import the application into the BizTalk group.</span></span> <span data-ttu-id="196e6-133">Pendant l’installation, PreProcScript.bat s’exécute automatiquement, comme décrit plus loin.</span><span class="sxs-lookup"><span data-stu-id="196e6-133">During installation, PreProcScript.bat runs automatically, as described later.</span></span>  
  
-   <span data-ttu-id="196e6-134">**RemoveApp.bat.**</span><span class="sxs-lookup"><span data-stu-id="196e6-134">**RemoveApp.bat.**</span></span> <span data-ttu-id="196e6-135">Effectue les actions suivantes, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="196e6-135">Takes the following actions, in order:</span></span>  
  
    1.  <span data-ttu-id="196e6-136">Utilise l’outil BTSTask [commande RemoveApp](../core/removeapp-command.md) pour supprimer l’application CreateApplicationSample de la base de données de gestion BizTalk pour le groupe.</span><span class="sxs-lookup"><span data-stu-id="196e6-136">Uses the BTSTask [RemoveApp Command](../core/removeapp-command.md) to delete the CreateApplicationSample application from the BizTalk Management database for the group.</span></span>  
  
    2.  <span data-ttu-id="196e6-137">Utilise l’outil BTSTask [commande UninstallApp](../core/uninstallapp-command.md) pour désinstaller l’application CreateApplicationSample de l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="196e6-137">Uses the BTSTask [UninstallApp Command](../core/uninstallapp-command.md) to uninstall the CreateApplicationSample application from the local computer.</span></span> <span data-ttu-id="196e6-138">Pendant l'installation, PreProcScript.bat s'exécute automatiquement, comme décrit ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="196e6-138">During installation, PreProcScript.bat runs automatically, as described next.</span></span>  
  
-   <span data-ttu-id="196e6-139">**PreProcScript.bat.**</span><span class="sxs-lookup"><span data-stu-id="196e6-139">**PreProcScript.bat.**</span></span> <span data-ttu-id="196e6-140">Effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="196e6-140">Takes the following actions:</span></span>  
  
    -   <span data-ttu-id="196e6-141">À chaque exécution, définit le jeton de clé publique pour l'assembly fourni par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="196e6-141">Each time it runs, sets the public key token for the assembly that has been provided by the user.</span></span>  
  
    -   <span data-ttu-id="196e6-142">Lors de l'installation de l'application, crée les dossiers suivants qui sont utilisés par l'application CreateApplicationSample pour contenir des messages :</span><span class="sxs-lookup"><span data-stu-id="196e6-142">During application installation, creates the following folders that will be used by the CreateApplicationSample application to contain messages:</span></span>  
  
         <span data-ttu-id="196e6-143">C:\CreateApplicationSample\Out</span><span class="sxs-lookup"><span data-stu-id="196e6-143">C:\CreateApplicationSample\Out</span></span>  
  
         <span data-ttu-id="196e6-144">C:\CreateApplicationSample\In</span><span class="sxs-lookup"><span data-stu-id="196e6-144">C:\CreateApplicationSample\In</span></span>  
  
    -   <span data-ttu-id="196e6-145">Lors de la désinstallation de l'application, supprime les fichiers et dossiers créés au cours de l'installation.</span><span class="sxs-lookup"><span data-stu-id="196e6-145">During application uninstallation, deletes the files and folders that were created during installation.</span></span> <span data-ttu-id="196e6-146">Désinstalle également du Global Assembly Cache tout assembly installé dans le GAC lors de l'installation et consigne ses actions dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="196e6-146">Also uninstalls from the global assembly cache (GAC) any assemblies that were installed in the GAC during installation and logs its actions to a file.</span></span> <span data-ttu-id="196e6-147">Pour désinstaller les assemblys du Global Assembly Cache, il renvoie au jeton de clé publique fourni par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="196e6-147">To uninstall the assemblies from the GAC, it refers to the public key token provided by the user.</span></span>  
  
    -   <span data-ttu-id="196e6-148">Pendant l'installation et la désinstallation, crée un fichier journal à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="196e6-148">During both installation and uninstallation, creates a log file in the following location:</span></span>  
  
         <span data-ttu-id="196e6-149">C:\ScriptLog.txt</span><span class="sxs-lookup"><span data-stu-id="196e6-149">C:\ScriptLog.txt</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="196e6-150">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="196e6-150">Where to Find This Sample</span></span>  
 <span data-ttu-id="196e6-151">Vous trouverez des exemples de fichiers dans les dossiers suivants sous  *\<exemples de chemin >*\Application déploiement\\:</span><span class="sxs-lookup"><span data-stu-id="196e6-151">You can find the sample files in the following folders under *\<Samples Path>*\Application Deployment\\:</span></span>  
  
-   <span data-ttu-id="196e6-152">CreateApp (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-152">CreateApp (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-153">Build.bat</span><span class="sxs-lookup"><span data-stu-id="196e6-153">Build.bat</span></span>  
  
    -   <span data-ttu-id="196e6-154">CreateFullAndPartialMSI.bat</span><span class="sxs-lookup"><span data-stu-id="196e6-154">CreateFullAndPartialMSI.bat</span></span>  
  
    -   <span data-ttu-id="196e6-155">CreateNewAppFromMSI.bat</span><span class="sxs-lookup"><span data-stu-id="196e6-155">CreateNewAppFromMSI.bat</span></span>  
  
    -   <span data-ttu-id="196e6-156">RemoveApp.bat</span><span class="sxs-lookup"><span data-stu-id="196e6-156">RemoveApp.bat</span></span>  
  
-   <span data-ttu-id="196e6-157">CreateApp\Bindings (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-157">CreateApp\Bindings (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-158">CreateApplicationSampleBindings.xml</span><span class="sxs-lookup"><span data-stu-id="196e6-158">CreateApplicationSampleBindings.xml</span></span>  
  
-   <span data-ttu-id="196e6-159">CreateApp\Dlls (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-159">CreateApp\Dlls (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-160">Vide</span><span class="sxs-lookup"><span data-stu-id="196e6-160">Empty</span></span>  
  
-   <span data-ttu-id="196e6-161">CreateApp\ResourceSpecs (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-161">CreateApp\ResourceSpecs (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-162">ResourceSpecPartial.xml</span><span class="sxs-lookup"><span data-stu-id="196e6-162">ResourceSpecPartial.xml</span></span>  
  
    -   <span data-ttu-id="196e6-163">ResourceSpecComplete.xml</span><span class="sxs-lookup"><span data-stu-id="196e6-163">ResourceSpecComplete.xml</span></span>  
  
-   <span data-ttu-id="196e6-164">CreateApp\Scripts (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-164">CreateApp\Scripts (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-165">PreProcScript.bat</span><span class="sxs-lookup"><span data-stu-id="196e6-165">PreProcScript.bat</span></span>  
  
-   <span data-ttu-id="196e6-166">CreateApp\HelloApplicationDeployment (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-166">CreateApp\HelloApplicationDeployment (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-167">HelloApplicationDeployment.suo</span><span class="sxs-lookup"><span data-stu-id="196e6-167">HelloApplicationDeployment.suo</span></span>  
  
    -   <span data-ttu-id="196e6-168">HelloApplicationDeployment.sln</span><span class="sxs-lookup"><span data-stu-id="196e6-168">HelloApplicationDeployment.sln</span></span>  
  
-   <span data-ttu-id="196e6-169">CreateApp\HelloApplicationDeployment\Maps (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-169">CreateApp\HelloApplicationDeployment\Maps (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-170">POToInvoice.btm</span><span class="sxs-lookup"><span data-stu-id="196e6-170">POToInvoice.btm</span></span>  
  
    -   <span data-ttu-id="196e6-171">Maps.btproj</span><span class="sxs-lookup"><span data-stu-id="196e6-171">Maps.btproj</span></span>  
  
-   <span data-ttu-id="196e6-172">CreateApp\HelloApplicationDeployment\Orchestrations (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-172">CreateApp\HelloApplicationDeployment\Orchestrations (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-173">Orchestrations.btproj</span><span class="sxs-lookup"><span data-stu-id="196e6-173">Orchestrations.btproj</span></span>  
  
    -   <span data-ttu-id="196e6-174">HelloOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="196e6-174">HelloOrchestration.odx</span></span>  
  
-   <span data-ttu-id="196e6-175">CreateApp\HelloApplicationDeployment\Schemas (dossier)</span><span class="sxs-lookup"><span data-stu-id="196e6-175">CreateApp\HelloApplicationDeployment\Schemas (Folder)</span></span>  
  
    -   <span data-ttu-id="196e6-176">Schemas.btproj</span><span class="sxs-lookup"><span data-stu-id="196e6-176">Schemas.btproj</span></span>  
  
    -   <span data-ttu-id="196e6-177">POSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="196e6-177">POSchema.xsd</span></span>  
  
    -   <span data-ttu-id="196e6-178">InvoiceSchema.xsd</span><span class="sxs-lookup"><span data-stu-id="196e6-178">InvoiceSchema.xsd</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="196e6-179">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="196e6-179">How to Use This Sample</span></span>  
 <span data-ttu-id="196e6-180">La procédure suivante permet d'utiliser l'exemple.</span><span class="sxs-lookup"><span data-stu-id="196e6-180">Use the following procedure to use this sample.</span></span>  
  
### <a name="to-use-the-sample"></a><span data-ttu-id="196e6-181">Pour utiliser l'exemple</span><span class="sxs-lookup"><span data-stu-id="196e6-181">To use the sample</span></span>  
  
1.  <span data-ttu-id="196e6-182">Exécutez Build.bat.</span><span class="sxs-lookup"><span data-stu-id="196e6-182">Run Build.bat.</span></span> <span data-ttu-id="196e6-183">Cela génère un fichier de clé, crée les projets sous le dossier HelloApplicationDeployment, signe les fichiers .dll obtenus et met les fichiers .dll dans le dossier Dlls.</span><span class="sxs-lookup"><span data-stu-id="196e6-183">This generates a key file, builds the projects under the folder HelloApplicationDeployment, signs the resulting .dll files, and places the.dll files in the Dlls folder.</span></span>  
  
2.  <span data-ttu-id="196e6-184">Ouvrez le fichier PreProcScript.bat, qui se trouve dans le dossier CreateApp\Scripts.</span><span class="sxs-lookup"><span data-stu-id="196e6-184">Open the PreProcScript.bat file, which is located in the CreateApp\Scripts folder.</span></span> <span data-ttu-id="196e6-185">Dans la ligne de code suivante, supprimez REM et indiquez le jeton de clé publique pour l'assembly :</span><span class="sxs-lookup"><span data-stu-id="196e6-185">In the following line of code, remove REM and provide the public key token for the assembly:</span></span>  
  
     <span data-ttu-id="196e6-186">**REM définie PublicKeyToken =**</span><span class="sxs-lookup"><span data-stu-id="196e6-186">**REM set PublicKeyToken=**</span></span>  
  
     <span data-ttu-id="196e6-187">Exemple :</span><span class="sxs-lookup"><span data-stu-id="196e6-187">Example:</span></span>  
  
     <span data-ttu-id="196e6-188">**définir PublicKeyToken = 1234a5b6c1234567**</span><span class="sxs-lookup"><span data-stu-id="196e6-188">**set PublicKeyToken=1234a5b6c1234567**</span></span>  
  
3.  <span data-ttu-id="196e6-189">Exécutez CreateFullAndPartialMSI.bat.</span><span class="sxs-lookup"><span data-stu-id="196e6-189">Run CreateFullAndPartialMSI.bat.</span></span> <span data-ttu-id="196e6-190">Cela crée deux fichiers .msi d'application, CreateApplicationSample.msi et CreateApplicationSamplePartial.msi.</span><span class="sxs-lookup"><span data-stu-id="196e6-190">This creates two application .msi files, CreateApplicationSample.msi and CreateApplicationSamplePartial.msi.</span></span>  
  
4.  <span data-ttu-id="196e6-191">Exécutez CreateNewAppFromMSI.bat.</span><span class="sxs-lookup"><span data-stu-id="196e6-191">Run CreateNewAppFromMSI.bat.</span></span> <span data-ttu-id="196e6-192">Cela importe l'application CreateApplicationSample dans le groupe BizTalk et l'installe sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="196e6-192">This imports the CreateApplicationSample application into the BizTalk group and installs it on the local computer.</span></span>  
  
5.  <span data-ttu-id="196e6-193">Consultez le fichier journal du script (C:\ScriptLog.txt) pour vérifier que le script a bien consigné ses actions d'installation.</span><span class="sxs-lookup"><span data-stu-id="196e6-193">Check the script log file, located at C:\ScriptLog.txt to verify that the script logged its installation actions.</span></span>  
  
6.  <span data-ttu-id="196e6-194">Assurez-vous que l'application CreateApplicationSample apparaît bien dans la console Administration de BizTalk Server et dans Ajout/Suppression de programmes.</span><span class="sxs-lookup"><span data-stu-id="196e6-194">Verify that the CreateApplicationSample application appears both in the BizTalk Server Administration console and Add or Remove Programs.</span></span>  
  
7.  <span data-ttu-id="196e6-195">Exécutez RemoveApp.bat.</span><span class="sxs-lookup"><span data-stu-id="196e6-195">Run RemoveApp.bat.</span></span> <span data-ttu-id="196e6-196">Cela supprime CreateApplicationSample de la base de données de gestion BizTalk et le désinstalle de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="196e6-196">This deletes the CreateApplicationSample from the BizTalk Management database and uninstalls it from the local computer.</span></span>  
  
8.  <span data-ttu-id="196e6-197">Consultez le fichier journal du script (C:\ScriptLog.txt) pour vérifier que le script a bien consigné ses actions de désinstallation.</span><span class="sxs-lookup"><span data-stu-id="196e6-197">Check the script log file, located at C:\ScriptLog.txt to verify that the script logged its uninstallation actions.</span></span> <span data-ttu-id="196e6-198">Elles doivent figurer après les actions d'installation consignées précédemment, au cours de l'installation.</span><span class="sxs-lookup"><span data-stu-id="196e6-198">They should appear after the installation actions logged earlier, during installation.</span></span>  
  
9. <span data-ttu-id="196e6-199">Assurez-vous que l'application CreateApplicationSample n'apparaît plus dans la console Administration de BizTalk Server ni dans Ajout/Suppression de programmes.</span><span class="sxs-lookup"><span data-stu-id="196e6-199">Verify that the CreateApplicationSample application no longer appears in either the BizTalk Server Administration console or Add or Remove Programs.</span></span>  
  
10. <span data-ttu-id="196e6-200">Vérifiez que les dossiers créés pendant l'installation ont été supprimés.</span><span class="sxs-lookup"><span data-stu-id="196e6-200">Verify that the folders that were created during installation have been deleted.</span></span>  
  
11. <span data-ttu-id="196e6-201">Vérifiez que les assemblys ont été désinstallés du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="196e6-201">Verify that the assemblies have been uninstalled from the GAC.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="196e6-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="196e6-202">See Also</span></span>  
 <span data-ttu-id="196e6-203">[Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="196e6-203">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="196e6-204">Déploiement d’Applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="196e6-204">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)