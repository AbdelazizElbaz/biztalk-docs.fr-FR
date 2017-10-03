---
title: "Comment importer une Application à partir d’un fichier .msi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5472df9-9f1e-42d5-82e0-cc559caf56b3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ea38086ea98923b05b23ed8c594175e1ce09e4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-import-an-application-from-an-msi-file"></a><span data-ttu-id="af94b-102">Comment importer une Application à partir d’un fichier .msi</span><span class="sxs-lookup"><span data-stu-id="af94b-102">How to Import an Application from an .msi File</span></span>
<span data-ttu-id="af94b-103">Vous pouvez utiliser l’Assistant MSI d’importation dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Console d’Administration ou de BTSTask pour importer une application BizTalk à partir d’un fichier .msi dans un groupe BizTalk dans l’environnement cible et installer l’application sur les instances d’hôte individuel dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="af94b-103">You can use the Import MSI Wizard in the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Administration Console or BTSTask to import a BizTalk application from an .msi file into a BizTalk group in the target environment and install the application on individual host instances in the group.</span></span> <span data-ttu-id="af94b-104">Le processus d’importation complète effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="af94b-104">The full import process performs the following operations:</span></span>  
  
-   <span data-ttu-id="af94b-105">Un déploiement au niveau du groupe de l’application</span><span class="sxs-lookup"><span data-stu-id="af94b-105">A group-level deployment of the application</span></span>  
  
-   <span data-ttu-id="af94b-106">Une installation au niveau du serveur de l’application.</span><span class="sxs-lookup"><span data-stu-id="af94b-106">A server-level installation of the application.</span></span>  
  
 <span data-ttu-id="af94b-107">**Déploiement d’applications au niveau du groupe**</span><span class="sxs-lookup"><span data-stu-id="af94b-107">**Group-Level Application Deployment**</span></span>  
  
 <span data-ttu-id="af94b-108">Vous effectuez un déploiement de groupe au niveau d’une application sur un serveur dans le groupe en exécutant l’Assistant Importation de MIS à partir de la console Administration de BizTalk Server ou en exécutant l’outil BTSTask.</span><span class="sxs-lookup"><span data-stu-id="af94b-108">You perform a group-level deployment of an application on a server in the group by running the Import MIS Wizard from the BizTalk Server Administration console or by running BTSTask.</span></span> <span data-ttu-id="af94b-109">Le déploiement au niveau du groupe effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="af94b-109">The group-level deployment does the following:</span></span>  
  
-   <span data-ttu-id="af94b-110">Crée l’application et ses artefacts dans le groupe</span><span class="sxs-lookup"><span data-stu-id="af94b-110">Creates the application and its artifacts in the group</span></span>  
  
-   <span data-ttu-id="af94b-111">Importent les liaisons qui se trouvent dans le package .msi</span><span class="sxs-lookup"><span data-stu-id="af94b-111">Imports bindings resident in the .msi package</span></span>  
  
-   <span data-ttu-id="af94b-112">Déploie tous les assemblys BizTalk Server avec leurs artefacts pour la base de données de gestion BizTalk pour le groupe</span><span class="sxs-lookup"><span data-stu-id="af94b-112">Deploys all BizTalk Server assemblies with their artifacts to the BizTalk Management database for the group</span></span>  
  
-   <span data-ttu-id="af94b-113">Exécute des scripts pour s’exécuter au moment de l’importation.</span><span class="sxs-lookup"><span data-stu-id="af94b-113">Runs scripts specified to run at import time.</span></span>  
  
 <span data-ttu-id="af94b-114">Si vous avez ajouté des fichiers de liaison propres à l’environnement à l’application, vous devrez sélectionner les liaisons que vous souhaitez appliquer lors de l’importation.</span><span class="sxs-lookup"><span data-stu-id="af94b-114">If you have added environment-specific binding files to the application, you will have to select the bindings that you want to apply on import.</span></span>  
  
 <span data-ttu-id="af94b-115">**Installation de l’Application de niveau serveur**</span><span class="sxs-lookup"><span data-stu-id="af94b-115">**Server-Level Application Installation**</span></span>  
  
 <span data-ttu-id="af94b-116">Vous effectuez une installation au niveau du serveur d’une application sur chaque serveur dans un groupe en double-cliquant sur le fichier .msi lui-même ou en effectuant le processus d’installation à la fin de l’Assistant MSI d’importation.</span><span class="sxs-lookup"><span data-stu-id="af94b-116">You perform a server-level installation of an application on each server in a group by double-clicking the .msi file itself, or performing the install process at the end of the Import MSI Wizard.</span></span> <span data-ttu-id="af94b-117">Au lieu d’être réalisée une fois par groupe, il est généralement réalisée sur chaque serveur BizTalk server qui est membre du groupe.</span><span class="sxs-lookup"><span data-stu-id="af94b-117">Instead of being done once per group, it is typically done on each BizTalk server that is a member of the group.</span></span> <span data-ttu-id="af94b-118">L’installation au niveau du serveur effectue les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="af94b-118">The server-level installation does the following:</span></span>  
  
-   <span data-ttu-id="af94b-119">Installe tous les assemblys BizTalk Server et les assemblys de dépendance dans le global assembly cache du serveur, afin que cet ordinateur dispose de tous les fichiers binaires dont il a besoin pour l’exécution</span><span class="sxs-lookup"><span data-stu-id="af94b-119">Installs all BizTalk Server assemblies and dependency assemblies into the global assembly cache of the server, so that this computer has all of the binaries that it needs for runtime</span></span>  
  
-   <span data-ttu-id="af94b-120">Présente les services Web associés qui peuvent faire partie de la solution, par exemple, orchestrations publiées en tant que services Web.</span><span class="sxs-lookup"><span data-stu-id="af94b-120">Rolls out related Web services that might be part of the solution, for example, orchestrations published as Web services.</span></span>  
  
-   <span data-ttu-id="af94b-121">Applique les modifications spécifiques à l’ordinateur, telles que la création préalable des files d’attente MSMQ ou en créant des structures de dossiers de dépôt de fichiers et les autorisations, ce qui peuvent être effectuées à l’aide de scripts.</span><span class="sxs-lookup"><span data-stu-id="af94b-121">Applies computer-specific changes, such as pre-creating MSMQ queues or creating FILE drop folder structures and permissions, which can be done with the help of scripts.</span></span>  
  
 <span data-ttu-id="af94b-122">Lorsque vous exécutez un fichier .msi pour installer une application, le fichier .msi crée des entrées d’inscription dans la liste Ajouter ou supprimer des programmes et accélère le déploiement en automatisant le déploiement des artefacts et leurs dépendances dans le bon ordre.</span><span class="sxs-lookup"><span data-stu-id="af94b-122">When you execute an .msi file to install an application, the .msi file creates registration entries in the Add or Remove Programs list, and accelerates deployment by automating deployment of artifacts and their dependencies in the correct order.</span></span>  
  
 <span data-ttu-id="af94b-123">Pour plus d’informations sur l’installation d’une application BizTalk, consultez [comment installer une Application](../technical-guides/how-to-install-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="af94b-123">For more information on installing a BizTalk application, see [How to Install an Application](../technical-guides/how-to-install-an-application.md).</span></span>  
  
 <span data-ttu-id="af94b-124">**Le déploiement de l’Application terminée et le processus d’Installation**</span><span class="sxs-lookup"><span data-stu-id="af94b-124">**The Complete Application Deployment and Installation Process**</span></span>  
  
 <span data-ttu-id="af94b-125">L’Assistant MSI d’importation déploie l’application sur le groupe.</span><span class="sxs-lookup"><span data-stu-id="af94b-125">The Import MSI Wizard deploys the application on the group.</span></span> <span data-ttu-id="af94b-126">Il n’installe pas l’application sur des serveurs individuels dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="af94b-126">It does not install the application on the individual servers in the group.</span></span> <span data-ttu-id="af94b-127">Si l’application inclut des artefacts basés sur un fichier, vous devez installer l’application sur chaque instance d’hôte qui exécutera les assemblys dans l’application (et tous les ordinateurs exécutant les applications qui dépendent de cette application).</span><span class="sxs-lookup"><span data-stu-id="af94b-127">If the application includes file-based artifacts, you need to install the application on each host instance that will run the assemblies in the application (and any computers running applications that depend on this application).</span></span> <span data-ttu-id="af94b-128">Vous pouvez faire sur le serveur vous avez exécuté l’Assistant MSI d’importation, toutefois, en sélectionnant le **exécuter l’Assistant Installation de Application pour installer l’application sur l’ordinateur local** case à cocher sur la page Importation réussie est affichée par le Assistant MSI d’importation.</span><span class="sxs-lookup"><span data-stu-id="af94b-128">You can do so on the server you ran the Import MSI Wizard on, however, by selecting the **Run the Application Installation Wizard to install the application on the local computer** check box on the Import Succeeded page displayed by the Import MSI Wizard.</span></span> <span data-ttu-id="af94b-129">Vous pouvez le faire sur les autres serveurs dans le groupe en double-cliquant sur le fichier .msi sur chacun de ces serveurs.</span><span class="sxs-lookup"><span data-stu-id="af94b-129">You can do so on the other servers in the group by double-clicking the .msi file on each of those servers.</span></span>  
  
 <span data-ttu-id="af94b-130">Si vous êtes prêt à tester l’application, vous pouvez l’importer dans un groupe BizTalk dans un environnement de test.</span><span class="sxs-lookup"><span data-stu-id="af94b-130">If you are ready to test the application, you can import it into a BizTalk group in a test environment.</span></span> <span data-ttu-id="af94b-131">Si votre application est prête pour la production ou intermédiaire, vous pouvez l’importer dans un de ces environnements.</span><span class="sxs-lookup"><span data-stu-id="af94b-131">If your application is ready for staging or production, you can import it into one of those environments.</span></span>  
  
## <a name="important-considerations"></a><span data-ttu-id="af94b-132">Éléments importants à prendre en considération</span><span class="sxs-lookup"><span data-stu-id="af94b-132">Important Considerations</span></span>  
 <span data-ttu-id="af94b-133">Lorsque vous importez une application BizTalk à partir d’un fichier .msi, tenez compte les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="af94b-133">When importing a BizTalk application from an .msi file, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="af94b-134">**Vous devez spécifier que les artefacts doivent être remplacées dans un processus d’importation standard.**</span><span class="sxs-lookup"><span data-stu-id="af94b-134">**You must specify that you want artifacts to be overwritten in a standard import process.**</span></span> <span data-ttu-id="af94b-135">Si vous souhaitez remplacer les artefacts existants, sélectionnez l’option de remplacement des artefacts existants lors de l’importation du fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="af94b-135">If you want to overwrite existing artifacts, select the option to overwrite existing artifacts when importing the .msi file.</span></span>  
  
-   <span data-ttu-id="af94b-136">**Les liaisons importées remplacent les liaisons existantes.**</span><span class="sxs-lookup"><span data-stu-id="af94b-136">**Imported bindings overwrite existing bindings.**</span></span> <span data-ttu-id="af94b-137">Lorsque vous importez un fichier .msi contenant des liaisons dans une application existante, les liaisons existantes sont remplacées par celles importées portant le même nom,</span><span class="sxs-lookup"><span data-stu-id="af94b-137">When you import an .msi file that contains bindings into an existing application, the existing bindings are overwritten by imported bindings that have the same name.</span></span> <span data-ttu-id="af94b-138">et ce même si vous n'avez pas sélectionné l'option de remplacement des artefacts existants lors de l'importation du fichier .msi.</span><span class="sxs-lookup"><span data-stu-id="af94b-138">This is the case even when you have not selected the option to overwrite existing artifacts when importing the .msi file.</span></span> <span data-ttu-id="af94b-139">Pour éviter que les liaisons de l'application exportée ne remplacent les liaisons de l'application dans laquelle vous importez le fichier .msi, ne sélectionnez pas le fichier de liaison en tant que ressource à exporter pendant l'opération d'exportation.</span><span class="sxs-lookup"><span data-stu-id="af94b-139">If you do not want the bindings in the application you are exporting to overwrite the bindings in an application into which you are importing the .msi file, then you should not select the binding file as a resource to export during the export operation.</span></span> <span data-ttu-id="af94b-140">Pour plus d’informations sur les ressources pour une exportation, consultez [comment exporter une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).</span><span class="sxs-lookup"><span data-stu-id="af94b-140">For more information about setting the resources for an export, see [How to Export a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154848) (http://go.microsoft.com/fwlink/?LinkID=154848).</span></span>  
  
 <span data-ttu-id="af94b-141">À mesure que des liaisons sont appliquées au cours du processus d'importation, les liaisons déjà appliquées sont remplacées par de nouvelles liaisons qui portent le même nom.</span><span class="sxs-lookup"><span data-stu-id="af94b-141">As bindings are applied during the import process, bindings that have already been applied are overwritten by new bindings that have the same name.</span></span> <span data-ttu-id="af94b-142">Autrement dit, la liaison d'un nom donné la plus récente est celle qui est effectivement appliquée.</span><span class="sxs-lookup"><span data-stu-id="af94b-142">In other words, the last binding of a particular name to be applied takes effect.</span></span> <span data-ttu-id="af94b-143">Lorsque vous importez une application, les liaisons sont appliquées dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="af94b-143">When you import an application, bindings are applied in the following order:</span></span>  
  
1.  <span data-ttu-id="af94b-144">Liaisons d'application générées par BizTalk Server, n'ayant pas été explicitement ajoutées à l'application au moyen d'un fichier de liaison, mais ayant été sélectionnées par l'utilisateur pour leur exportation dans le fichier .msi de l'application.</span><span class="sxs-lookup"><span data-stu-id="af94b-144">Application bindings generated by BizTalk Server that were not explicitly added to the application via a binding file, but that were explicitly selected by the user for export into the application .msi file.</span></span>  
  
2.  <span data-ttu-id="af94b-145">Fichiers de liaison ajoutés de manière explicite mais pour lesquels aucun environnement de déploiement cible n'a été défini.</span><span class="sxs-lookup"><span data-stu-id="af94b-145">Binding files that have been explicitly added, and do not have a target deployment environment specified.</span></span> <span data-ttu-id="af94b-146">À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="af94b-146">Bindings in this set are applied in no specific order.</span></span>  
  
3.  <span data-ttu-id="af94b-147">Liaisons ajoutées de manière explicite auxquelles est associé un environnement de déploiement cible correspondant à l'environnement de déploiement sélectionné pour l'importation de l'application.</span><span class="sxs-lookup"><span data-stu-id="af94b-147">Bindings that have been explicitly added, and that have an associated target deployment environment that matches the deployment environment selected for application import.</span></span> <span data-ttu-id="af94b-148">À l'intérieur de cet ensemble, l'application des liaisons ne respecte pas d'ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="af94b-148">Bindings in this set are applied in no specific order.</span></span>  
  
-   <span data-ttu-id="af94b-149">**L’hôte spécifié doit exister.**</span><span class="sxs-lookup"><span data-stu-id="af94b-149">**The host specified must exist.**</span></span> <span data-ttu-id="af94b-150">Pour importer une application à partir d’un fichier .msi, un hôte correspondant à l’hôte spécifié dans les liaisons d’application contenues dans le fichier .msi doit déjà exister dans le groupe BizTalk ou l’opération d’importation échoue.</span><span class="sxs-lookup"><span data-stu-id="af94b-150">To import an application from an .msi file, a host corresponding to the host specified in the application bindings contained in the .msi file must already exist in the BizTalk group or the import operation will fail.</span></span> <span data-ttu-id="af94b-151">En outre, le niveau de confiance de l'hôte doit correspondre.</span><span class="sxs-lookup"><span data-stu-id="af94b-151">In addition, the host trust level must match.</span></span>  
  
-   <span data-ttu-id="af94b-152">**Dépendances peuvent avoir des effets significatifs sur les opérations d’importation.**</span><span class="sxs-lookup"><span data-stu-id="af94b-152">**Dependencies can have significant effects upon import operations.**</span></span> <span data-ttu-id="af94b-153">Lorsque vous importez une application qui a une dépendance sur une autre application, les règles suivantes s’appliquent :</span><span class="sxs-lookup"><span data-stu-id="af94b-153">When you import an application that has a dependency on another application, the following rules apply:</span></span>  
  
    -   <span data-ttu-id="af94b-154">Si une application que vous importez est dépendante d’un artefact dans une autre application, vous devez ajouter une référence à partir de la première application à l’autre application.</span><span class="sxs-lookup"><span data-stu-id="af94b-154">If an application that you are importing depends on an artifact in another application, you must add a reference from the first application to the second application.</span></span> <span data-ttu-id="af94b-155">L’application et l’artefact requis doivent déjà exister dans le groupe de destination.</span><span class="sxs-lookup"><span data-stu-id="af94b-155">The application and the required artifact must already exist in the destination group.</span></span> <span data-ttu-id="af94b-156">L’Assistant Importation vous permet de vous permet d’ajouter la référence.</span><span class="sxs-lookup"><span data-stu-id="af94b-156">The Import Wizard enables you to add the reference.</span></span> <span data-ttu-id="af94b-157">Toutefois, si vous utilisez la commande ImportApp de BTSTask, vous devez ajouter la référence à l’application après l’importation.</span><span class="sxs-lookup"><span data-stu-id="af94b-157">However, if you are using the ImportApp command of BTSTask, you must add the reference to the application after import.</span></span> <span data-ttu-id="af94b-158">Pour plus d’informations, consultez [comment ajouter une référence à une autre Application](http://go.microsoft.com/fwlink/?LinkId=155011) (http://go.microsoft.com/fwlink/?LinkId=155011).</span><span class="sxs-lookup"><span data-stu-id="af94b-158">For more information, see [How to Add a Reference to Another Application](http://go.microsoft.com/fwlink/?LinkId=155011) (http://go.microsoft.com/fwlink/?LinkId=155011).</span></span> <span data-ttu-id="af94b-159">L'Assistant Importation établit des correspondances entre les références et les applications existantes du groupe et vous permet d'ajouter ou de modifier une référence.</span><span class="sxs-lookup"><span data-stu-id="af94b-159">The Import Wizard matches the references to existing applications in the group and gives you the option to add a new reference or change an existing reference.</span></span> <span data-ttu-id="af94b-160">Même si BizTalk Server vérifie que l'application référencée existe, nous vous recommandons de vérifier également que l'application référencée contient l'artefact requis.</span><span class="sxs-lookup"><span data-stu-id="af94b-160">While BizTalk Server verifies that the referenced application exists, we recommend that you take the additional step of verifying that the referenced application contains the required artifact.</span></span>  
  
    -   <span data-ttu-id="af94b-161">Lorsque vous installez une application, vous devez également installer les applications dont elle dépend.</span><span class="sxs-lookup"><span data-stu-id="af94b-161">When you install an application, you must also install any applications on which it depends.</span></span> <span data-ttu-id="af94b-162">Lorsque vous installez une application dépendant d'un artefact, tel qu'un assembly BizTalk, contenu dans une autre application, vous devez installer au préalable l'application contenant cet artefact.</span><span class="sxs-lookup"><span data-stu-id="af94b-162">When you install an application that has a dependency on an artifact, such as a BizTalk assembly, which is contained in another application, you must first install the application that contains the artifact.</span></span> <span data-ttu-id="af94b-163">Par exemple, si vous souhaitez installer l'application A, et que celle-ci dépend d'un assembly contenu dans l'application B, vous devez installer au préalable l'application B.</span><span class="sxs-lookup"><span data-stu-id="af94b-163">For example, if you want to install Application A, and it depends on an assembly in Application B, you must install Application B first.</span></span> <span data-ttu-id="af94b-164">Vous pouvez ensuite installer l’Application a Pour plus d’informations sur l’installation d’une application BizTalk, consultez [comment installer une Application](../technical-guides/how-to-install-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="af94b-164">Then you can install Application A. For more information about installing a BizTalk application, see [How to Install an Application](../technical-guides/how-to-install-an-application.md).</span></span>  
  
    -   <span data-ttu-id="af94b-165">Pour importer une application dans un autre groupe BizTalk et l'exécuter dans celui-ci, vous devez également importer les artefacts dont cette application dépend.</span><span class="sxs-lookup"><span data-stu-id="af94b-165">If you want to import an application into a different BizTalk group and run it in that group, you must also import any artifacts on which this application depends.</span></span> <span data-ttu-id="af94b-166">Faire cela en premier l’importation d’une application qui contient l’artefact référencé, ou en ajoutant l’artefact nécessaire à l’application qui le requiert.</span><span class="sxs-lookup"><span data-stu-id="af94b-166">You can do this by first importing an application that contains the referenced artifact, or by adding the needed artifact to the application that requires it.</span></span> <span data-ttu-id="af94b-167">Pour plus d’informations sur l’importation d’une application BizTalk, consultez [comment importer une Application à partir d’un fichier .msi](../technical-guides/how-to-import-an-application-from-an-msi-file.md).</span><span class="sxs-lookup"><span data-stu-id="af94b-167">For more information about importing a BizTalk application, see [How to Import an Application from an .msi File](../technical-guides/how-to-import-an-application-from-an-msi-file.md).</span></span>  
  
 <span data-ttu-id="af94b-168">Pour plus des considérations et des informations sur l’importation d’une application BizTalk à partir d’un fichier .msi, consultez [comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).</span><span class="sxs-lookup"><span data-stu-id="af94b-168">For more considerations and information about importing a BizTalk application from an .msi file, see [How to Import a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).</span></span>  
  
## <a name="how-to-import-an-application"></a><span data-ttu-id="af94b-169">Comment importer une Application</span><span class="sxs-lookup"><span data-stu-id="af94b-169">How to Import an Application</span></span>  
 <span data-ttu-id="af94b-170">Pour obtenir des instructions sur l’importation d’une application BizTalk à partir d’un fichier .msi, consultez [comment importer une Application BizTalk](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).</span><span class="sxs-lookup"><span data-stu-id="af94b-170">For instructions on importing a BizTalk application from an .msi file, see [How to Import a BizTalk Application](http://go.microsoft.com/fwlink/?LinkID=154827) (http://go.microsoft.com/fwlink/?LinkID=154827).</span></span>