---
title: "Modèle (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, examples
- scripts, deploying
- deploying, scripts
- examples, deploying
ms.assetid: 7e77ff8e-b2bc-4d38-b5fd-329d6d54221f
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 315a685f0e289d60e3db9dfbe77bae5a7e2b19f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="template-application-deployment-sample"></a><span data-ttu-id="03e46-102">Modèle (exemple de déploiement d'une application)</span><span class="sxs-lookup"><span data-stu-id="03e46-102">Template (Application Deployment Sample)</span></span>
<span data-ttu-id="03e46-103">Cette rubrique décrit l'utilisation de l'exemple de modèle pour le déploiement d'une application.</span><span class="sxs-lookup"><span data-stu-id="03e46-103">This topic describes how to use the Template sample for application deployment.</span></span>  
  
 <span data-ttu-id="03e46-104">Vous pouvez créer et utiliser les deux types de scripts de déploiement pour personnaliser le déploiement d’applications BizTalk : scripts de pré-traitement et de scripts de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="03e46-104">You can create and use two types of deployment scripts to customize BizTalk application deployment: pre-processing scripts and post-processing scripts.</span></span> <span data-ttu-id="03e46-105">Les scripts de pré-traitement sont appelés avant le début de l'installation et de l'importation de l'application, ainsi qu'une fois la désinstallation terminée.</span><span class="sxs-lookup"><span data-stu-id="03e46-105">Pre-processing scripts are invoked before application installation and import begins and after uninstallation completes.</span></span> <span data-ttu-id="03e46-106">Les scripts de post-traitement sont appelés après la fin de l'installation et de l'importation de l'application, ainsi qu'avant le début de la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="03e46-106">Post-processing scripts are invoked after application installation and import completes and before uninstallation begins.</span></span>  
  
 <span data-ttu-id="03e46-107">Vous pouvez écrire de tels scripts pour qu'ils soient appelés pour chacune de ces opérations.</span><span class="sxs-lookup"><span data-stu-id="03e46-107">You can write pre- and post- processing scripts so that they are invoked for each of these operations.</span></span> <span data-ttu-id="03e46-108">Vous pouvez également les configurer de manière à ce qu'ils soient exécutés uniquement après l'une d'entre elles.</span><span class="sxs-lookup"><span data-stu-id="03e46-108">Alternatively, you can configure scripts to execute after only one of them.</span></span> <span data-ttu-id="03e46-109">Pour plus d’informations sur l’écriture de scripts, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="03e46-109">For more information about writing scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
 <span data-ttu-id="03e46-110">Cette rubrique illustre l'écriture et le déploiement d'un script de façon à ce qu'il soit appelé avant ou après une seule opération.</span><span class="sxs-lookup"><span data-stu-id="03e46-110">This topic demonstrates how to write and deploy a script so that it is invoked before or after only one operation.</span></span> <span data-ttu-id="03e46-111">Pour ce faire, écrivez un script chargé de vérifier les valeurs de trois variables d'environnement pour déterminer le contexte de l'opération au sein duquel le script est appelé.</span><span class="sxs-lookup"><span data-stu-id="03e46-111">You do this by writing a script that checks the values of three environment variables to determine the operation in the context of which it is being called.</span></span> <span data-ttu-id="03e46-112">En fonction de ce contexte, le script continue ou interrompt l'exécution.</span><span class="sxs-lookup"><span data-stu-id="03e46-112">Based on this context, the script either continues or discontinues execution.</span></span>  
  
 <span data-ttu-id="03e46-113">Cette rubrique présente les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="03e46-113">This topic describes how to take the following steps:</span></span>  
  
1.  <span data-ttu-id="03e46-114">Définition de l'emplacement du fichier journal, de manière à pouvoir générer un fichier journal des opérations du script.</span><span class="sxs-lookup"><span data-stu-id="03e46-114">Set the log file location, so that you can generate a log file of the script operations.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="03e46-115">Il est recommandé de toujours générer un fichier journal pour vérifier les opérations de script et résoudre les problèmes éventuels.</span><span class="sxs-lookup"><span data-stu-id="03e46-115">As a best practice, you should always generate a log file so that you can verify script operations and troubleshoot any problems.</span></span>  
  
2.  <span data-ttu-id="03e46-116">Création d'une application BizTalk et ajout des exemples de scripts à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="03e46-116">Create a new BizTalk application and add the sample scripts to it.</span></span>  
  
3.  <span data-ttu-id="03e46-117">Export d'un fichier .msi contenant les artefacts de l'application.</span><span class="sxs-lookup"><span data-stu-id="03e46-117">Export an .msi file containing the application artifacts.</span></span>  
  
4.  <span data-ttu-id="03e46-118">Suppression de l'application dans le groupe BizTalk, de manière à y importer de nouveau le fichier .msi et l'installer à partir de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="03e46-118">Delete the application from the BizTalk group, so that you can import the .msi file back into the same group as well as install it from the .msi file.</span></span>  
  
5.  <span data-ttu-id="03e46-119">Importation de l'application et vérification du fichier journal pour s'assurer de la réussite de l'opération.</span><span class="sxs-lookup"><span data-stu-id="03e46-119">Import the application, and check the log file to see that the import operation was logged.</span></span>  
  
6.  <span data-ttu-id="03e46-120">Installation de l'application et vérification du fichier journal pour s'assurer que le journal d'installation y a bien été ajouté.</span><span class="sxs-lookup"><span data-stu-id="03e46-120">Install the application, and check the log file to see that the installation log was appended to the log file.</span></span>  
  
7.  <span data-ttu-id="03e46-121">Affichage des fichiers journaux et consignation de la nature et de l'heure des opérations réalisées par les scripts.</span><span class="sxs-lookup"><span data-stu-id="03e46-121">View the log files and note what operations the scripts performed and when they were performed.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="03e46-122">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="03e46-122">What This Sample Does</span></span>  
 <span data-ttu-id="03e46-123">Deux fichiers .bat fournis avec cet exemple contiennent les valeurs des variables d'environnement pour les opérations d'importation, d'installation et de désinstallation.</span><span class="sxs-lookup"><span data-stu-id="03e46-123">Two .bat files provided for this sample contain the values of the environment variables for import, installation, and uninstallation.</span></span> <span data-ttu-id="03e46-124">Le fichier SamplePreProcessing.bat inclut les variables d'un script de pré-traitement.</span><span class="sxs-lookup"><span data-stu-id="03e46-124">SamplePreProcessing.bat contains variables for a pre-processing script.</span></span> <span data-ttu-id="03e46-125">Le fichier SamplePostProcessing.bat inclut les variables d'un script de post-traitement.</span><span class="sxs-lookup"><span data-stu-id="03e46-125">SamplePostProcessing.bat contains variables for a post-processing script.</span></span> <span data-ttu-id="03e46-126">Les fichiers présentent également la méthode d'enregistrement des messages à partir de scripts.</span><span class="sxs-lookup"><span data-stu-id="03e46-126">The files also demonstrate how to log messages from scripts.</span></span> <span data-ttu-id="03e46-127">Vous pouvez copier les sections appropriées dans vos scripts.</span><span class="sxs-lookup"><span data-stu-id="03e46-127">You can copy the relevant sections of these files into your scripts.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03e46-128">Certains commentaires contenus dans les fichiers de script sont incorrects, à savoir :</span><span class="sxs-lookup"><span data-stu-id="03e46-128">Some of the comments within the script files are incorrect, as follows:</span></span>  
>   
>  <span data-ttu-id="03e46-129">Dans le fichier SamplePreProcessing.bat, le commentaire de script « Pré-désinstallation du script appelée pour une application existante » devrait plutôt afficher « Post-désinstallation du script appelée pour une application existante ».</span><span class="sxs-lookup"><span data-stu-id="03e46-129">In SamplePreProcessing.bat, the script comment, “Pre uninstall part of the script called for an existing application” should read "Post uninstall part of the script called for an existing application."</span></span>  
>   
>  <span data-ttu-id="03e46-130">Dans le fichier SamplePostProcessing.bat, le commentaire de script « Post-désinstallation du script appelée pour une application existante » devrait plutôt afficher « Pré-désinstallation du script appelée pour une application existante ».</span><span class="sxs-lookup"><span data-stu-id="03e46-130">In SamplePostProcessing.bat, the script comment, “Post uninstall part of the script called for an existing application” should read "Pre uninstall part of the script called for an existing application."</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="03e46-131">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="03e46-131">Where to Find This Sample</span></span>  
 <span data-ttu-id="03e46-132">L'exemple se trouve dans le dossier d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], comme suit :</span><span class="sxs-lookup"><span data-stu-id="03e46-132">The sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder, as follows:</span></span>  
  
 <span data-ttu-id="03e46-133">*\<Exemples de chemin d’accès\>*\Application Deployment\Template</span><span class="sxs-lookup"><span data-stu-id="03e46-133">*\<Samples Path\>*\Application Deployment\Template</span></span>  
  
 <span data-ttu-id="03e46-134">Comme indiqué précédemment, l'exemple inclut les deux fichiers suivants :</span><span class="sxs-lookup"><span data-stu-id="03e46-134">As previously mentioned, the sample includes the following two files:</span></span>  
  
-   <span data-ttu-id="03e46-135">SamplePreProcessing.bat</span><span class="sxs-lookup"><span data-stu-id="03e46-135">SamplePreProcessing.bat</span></span>  
  
-   <span data-ttu-id="03e46-136">SamplePostProcessing.bat</span><span class="sxs-lookup"><span data-stu-id="03e46-136">SamplePostProcessing.bat</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="03e46-137">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="03e46-137">How to Use This Sample</span></span>  
 <span data-ttu-id="03e46-138">Pour exécuter l'exemple, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="03e46-138">To run the sample, take the following steps.</span></span>  
  
### <a name="to-set-the-logging-location"></a><span data-ttu-id="03e46-139">Pour définir l'emplacement des journaux</span><span class="sxs-lookup"><span data-stu-id="03e46-139">To set the logging location</span></span>  
  
-   <span data-ttu-id="03e46-140">Ouvrez les exemples de scripts et modifiez la variable LogFile de sorte qu'elle renvoie à l'emplacement dans lequel les fichiers journaux doivent être générés.</span><span class="sxs-lookup"><span data-stu-id="03e46-140">Open both the script samples and change the LogFile variable to point to the location where the log files are to be written.</span></span> <span data-ttu-id="03e46-141">Vous devez indiquer le chemin d'accès complet, y compris le nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="03e46-141">You must provide the full path including the file name.</span></span> <span data-ttu-id="03e46-142">Si elle comprend des espaces, vous devez placer le chemin d’accès entre guillemets doubles («).</span><span class="sxs-lookup"><span data-stu-id="03e46-142">If it includes spaces, you must enclose the path in double quotation marks (").</span></span>  
  
     <span data-ttu-id="03e46-143">Exemple :</span><span class="sxs-lookup"><span data-stu-id="03e46-143">Example:</span></span>  
  
     <span data-ttu-id="03e46-144">définir le fichier journal = «*\<exemples de chemin\>*\ApplicationDeployment\Templates\SampleLogOut.txt »</span><span class="sxs-lookup"><span data-stu-id="03e46-144">set LogFile="*\<Samples Path\>*\ApplicationDeployment\Templates\SampleLogOut.txt"</span></span>  
  
### <a name="to-create-a-new-application"></a><span data-ttu-id="03e46-145">Pour créer une application</span><span class="sxs-lookup"><span data-stu-id="03e46-145">To create a new application</span></span>  
  
1.  <span data-ttu-id="03e46-146">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="03e46-146">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="03e46-147">Dans l'arborescence de la console, développez successivement la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="03e46-147">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and expand the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="03e46-148">Avec le bouton droit **Applications** puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="03e46-148">Right-click **Applications** and then click **New**.</span></span>  
  
4.  <span data-ttu-id="03e46-149">Dans **nom de l’Application**, type `SamplesTemplate`, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="03e46-149">In **Application name**, type `SamplesTemplate`, and then click **OK**.</span></span>  
  
### <a name="to-add-the-scripts-to-the-application"></a><span data-ttu-id="03e46-150">Pour ajouter les scripts à l'application</span><span class="sxs-lookup"><span data-stu-id="03e46-150">To add the scripts to the application</span></span>  
  
1.  <span data-ttu-id="03e46-151">Développez le dossier de l’application SamplesTemplate que vous venez de créer et cliquez sur **ressources** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="03e46-151">Expand the folder of the SamplesTemplate application that you just created and right-click **Resources** in the left pane.</span></span>  
  
2.  <span data-ttu-id="03e46-152">Pointez sur **ajouter** et cliquez sur **Scripts de pré-traitement**.</span><span class="sxs-lookup"><span data-stu-id="03e46-152">Point to **Add** and click **Pre-processing Scripts**.</span></span>  
  
3.  <span data-ttu-id="03e46-153">Cliquez sur **ajouter** et accédez au fichier SamplePreProcessing.bat.</span><span class="sxs-lookup"><span data-stu-id="03e46-153">Click **Add** and browse to SamplePreProcessing.bat.</span></span>  
  
4.  <span data-ttu-id="03e46-154">Sélectionnez le fichier et cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="03e46-154">Select the file and click **Open**.</span></span>  
  
5.  <span data-ttu-id="03e46-155">Dans **type de fichier**, cliquez sur **System.BizTalk : preprocessingscript**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="03e46-155">In **File type**, click **System.BizTalk:PreprocessingScript**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="03e46-156">Le fichier SamplePreProcessing.bat est ajouté à l'application, et affiché dans le dossier Ressources associé.</span><span class="sxs-lookup"><span data-stu-id="03e46-156">SamplePreProcessing.bat is added to the application and is displayed in the Resources folder of the application.</span></span>  
  
6.  <span data-ttu-id="03e46-157">Ressources avec le bouton droit à nouveau, pointez sur **ajouter**, puis cliquez sur **Scripts de post-traitement**.</span><span class="sxs-lookup"><span data-stu-id="03e46-157">Right-click Resources again, point to **Add**, and then click **Post-processing Scripts**.</span></span>  
  
7.  <span data-ttu-id="03e46-158">Cliquez sur **ajouter** et accédez au fichier SamplePostProcessing.bat.</span><span class="sxs-lookup"><span data-stu-id="03e46-158">Click **Add** and browse to SamplePostProcessing.bat.</span></span>  
  
8.  <span data-ttu-id="03e46-159">Sélectionnez le fichier et cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="03e46-159">Select the file and click **Open**.</span></span>  
  
9. <span data-ttu-id="03e46-160">Dans **type de fichier**, cliquez sur **System.BizTalk : postprocessingscript**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="03e46-160">In **File type**, click **System.BizTalk:PostprocessingScript**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="03e46-161">Le fichier SamplePostProcessing.bat est ajouté à l'application, et affiché dans le dossier Ressources associé.</span><span class="sxs-lookup"><span data-stu-id="03e46-161">SamplePostProcessing.bat is added to the application and is displayed in the Resources folder of the application.</span></span>  
  
### <a name="to-export-an-msi-file"></a><span data-ttu-id="03e46-162">Pour exporter un fichier .msi</span><span class="sxs-lookup"><span data-stu-id="03e46-162">To export an .msi file</span></span>  
  
1.  <span data-ttu-id="03e46-163">Dans la console Administration de BizTalk Server, cliquez sur l’application SamplesTemplate, pointez sur **exporter**, puis cliquez sur **fichier MSI**.</span><span class="sxs-lookup"><span data-stu-id="03e46-163">In the BizTalk Server Administration console, right-click the SamplesTemplate application, point to **Export**, and then click **MSI file**.</span></span>  
  
2.  <span data-ttu-id="03e46-164">Dans la page d’accueil de l’Assistant Exportation, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-164">On the Welcome to the Export Wizard page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="03e46-165">Dans la page Sélectionner les ressources, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-165">On the Select Resources page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="03e46-166">Dans la page spécifier les hôtes IIS, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-166">On the Specify IIS Hosts page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="03e46-167">Dans la page dépendances, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-167">On the Dependencies page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="03e46-168">Dans la page de Destination, dans **nom de l’application Destination**, tapez le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="03e46-168">On the Destination page, in **Destination application name**, type the application name.</span></span>  
  
7.  <span data-ttu-id="03e46-169">Dans **fichier MSI à générer**, tapez le chemin d’accès complet pour le fichier MSI, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="03e46-169">In **MSI file to generate**, type the full path for the MSI file, and then click **Export**.</span></span> <span data-ttu-id="03e46-170">Exemple : C:\MSI\SamplesTemplate.msi</span><span class="sxs-lookup"><span data-stu-id="03e46-170">Example: C:\MSI\SamplesTemplate.msi</span></span>  
  
8.  <span data-ttu-id="03e46-171">Dans la page Résumé, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="03e46-171">On the Summary page, click **Finish**.</span></span>  
  
### <a name="delete-the-application"></a><span data-ttu-id="03e46-172">Pour supprimer l'application</span><span class="sxs-lookup"><span data-stu-id="03e46-172">Delete the application</span></span>  
  
-   <span data-ttu-id="03e46-173">Dans la console Administration de BizTalk Server, cliquez sur l’application SamplesTemplate, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="03e46-173">In the BizTalk Server Administration console, right-click the SamplesTemplate application, and then click **Delete**.</span></span>  
  
### <a name="to-import-the-msi-file"></a><span data-ttu-id="03e46-174">Pour importer le fichier .msi</span><span class="sxs-lookup"><span data-stu-id="03e46-174">To import the .msi file</span></span>  
  
1.  <span data-ttu-id="03e46-175">Dans la console Administration de BizTalk Server, cliquez sur **Applications**, pointez sur **importation**, puis cliquez sur **fichier MSI**.</span><span class="sxs-lookup"><span data-stu-id="03e46-175">In the BizTalk Server Administration console, right-click **Applications**, point to **Import**, and then click **MSI file**.</span></span>  
  
2.  <span data-ttu-id="03e46-176">Sur la page d’accueil de l’Assistant Importation, dans **fichier MSI à importer**, tapez le chemin d’accès du fichier .msi que vous exportées, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-176">On the Welcome to the Import Wizard page, in **MSI file to import**, type the path of the .msi file that you previously exported, and then click **Next**.</span></span> <span data-ttu-id="03e46-177">Si nécessaire, vous pouvez rechercher le fichier MSI en cliquant sur le **(...)** bouton.</span><span class="sxs-lookup"><span data-stu-id="03e46-177">If necessary, you can browse for the MSI file by clicking the **(….)** button.</span></span>  
  
3.  <span data-ttu-id="03e46-178">Dans la page Paramètres de l’Application, dans le **nom de l’Application** liste déroulante, sélectionnez le nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="03e46-178">On the Application Settings page, in the **Application name** drop-down list, select the application name.</span></span>  
  
4.  <span data-ttu-id="03e46-179">Dans **applications disponibles auxquelles ajouter des références aux**, sélectionnez les applications auxquelles ajouter des références, éventuellement, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-179">In **Available applications to add references to**, select the applications to which to add references, if any, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="03e46-180">Dans la page Paramètres d’environnement Application cible, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="03e46-180">On the Application Target Environment Settings page, click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="03e46-181">Il est inutile de spécifier un environnement cible dans le cadre de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="03e46-181">You do not need to specify a target environment for the purposes of this sample.</span></span> <span data-ttu-id="03e46-182">Pour plus d’informations sur cette fonctionnalité, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="03e46-182">For background information on this feature, see [Binding Files and Application Deployment](../core/binding-files-and-application-deployment.md).</span></span> <span data-ttu-id="03e46-183">Pour obtenir des instructions sur l’ajout de fichiers de liaison, consultez [l’ajout d’un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span><span class="sxs-lookup"><span data-stu-id="03e46-183">For instructions on adding binding files, see [How to Add a Binding File to an Application](../core/how-to-add-a-binding-file-to-an-application2.md).</span></span>  
  
6.  <span data-ttu-id="03e46-184">Dans la page Résumé d’importation, vérifiez que les informations de résumé sont correctes, puis cliquez sur **importation**.</span><span class="sxs-lookup"><span data-stu-id="03e46-184">On the Import Summary page, confirm that the summary information is correct, and then click **Import**.</span></span>  
  
7.  <span data-ttu-id="03e46-185">Dans la page de résultats, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="03e46-185">On the Results page, click **Finish**.</span></span>  
  
8.  <span data-ttu-id="03e46-186">Ouvrez le fichier journal créé lors de l'exécution des scripts, puis vérifiez que l'opération d'importation y a été consignée.</span><span class="sxs-lookup"><span data-stu-id="03e46-186">Open the log file that was created when the scripts executed, and verify that import operation was logged.</span></span>  
  
### <a name="to-install-the-application"></a><span data-ttu-id="03e46-187">Pour installer l'application</span><span class="sxs-lookup"><span data-stu-id="03e46-187">To install the application</span></span>  
  
1.  <span data-ttu-id="03e46-188">Double-cliquez sur le fichier .msi, puis exécutez l'Assistant Installation.</span><span class="sxs-lookup"><span data-stu-id="03e46-188">Double-click the .msi file and run the Installation Wizard.</span></span>  
  
2.  <span data-ttu-id="03e46-189">Ouvrez le fichier journal, puis vérifiez que l'opération d'installation y a été consignée.</span><span class="sxs-lookup"><span data-stu-id="03e46-189">Open the log file and verify that installation operation was added to the logging information.</span></span>  
  
### <a name="to-verify-that-the-scripts-functioned-correctly"></a><span data-ttu-id="03e46-190">Pour vérifier le bon fonctionnement des scripts</span><span class="sxs-lookup"><span data-stu-id="03e46-190">To verify that the scripts functioned correctly</span></span>  
  
-   <span data-ttu-id="03e46-191">Ouvrez les fichiers journaux, puis vérifiez qu'ils ont été exécutés lors des opérations spécifiées.</span><span class="sxs-lookup"><span data-stu-id="03e46-191">Open the log files and verify that they executed during the specified operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e46-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03e46-192">See Also</span></span>  
 <span data-ttu-id="03e46-193">[Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="03e46-193">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="03e46-194">Déploiement des applications BizTalk</span><span class="sxs-lookup"><span data-stu-id="03e46-194">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)