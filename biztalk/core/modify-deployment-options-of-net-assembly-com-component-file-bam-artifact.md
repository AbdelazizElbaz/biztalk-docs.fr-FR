---
title: "Comment modifier les Options de déploiement d’un Assembly .NET, un composant COM, un fichier ou un artefact BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [.NET assemblies], deploying
- deploying, virtual directories
- managing [applications], deploying
- managing [applications], modifying
- definition files [BAM], modifying
- modifying, artifacts
- deploying, artifacts
- managing [certificates], deploying
- deploying, .NET assemblies
- COM components, deploying
- definition files [BAM], deploying
- virtual directories, deploying
- deploying, certificates
- modifying, deployment options
- virtual directories, modifying
- deploying, COM components
ms.assetid: 4955d420-d9ff-4d5a-82f4-fb16477a828c
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6469f06b7b42ae1f8b45419fa0214682bd9fa67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-the-deployment-options-of-a-net-assembly-com-component-file-or-bam-artifact"></a><span data-ttu-id="c6680-102">Modification des options de déploiement d'un assembly .NET, d'un composant COM, d'un fichier ou d'un artefact BAM</span><span class="sxs-lookup"><span data-stu-id="c6680-102">How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact</span></span>
<span data-ttu-id="c6680-103">Cette rubrique explique comment modifier les options de déploiement des artefacts de ressource suivants dans la console Administration de BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="c6680-103">This topic describes how to use the BizTalk Server Administration console to modify the deployment options of the following resource artifacts:</span></span>  
  
-   <span data-ttu-id="c6680-104">assemblys .NET</span><span class="sxs-lookup"><span data-stu-id="c6680-104">.NET assemblies</span></span>  
  
-   <span data-ttu-id="c6680-105">composants des services COM</span><span class="sxs-lookup"><span data-stu-id="c6680-105">COM components</span></span>  
  
-   <span data-ttu-id="c6680-106">Fichiers ad hoc</span><span class="sxs-lookup"><span data-stu-id="c6680-106">Ad hoc files</span></span>  
  
-   <span data-ttu-id="c6680-107">Artefacts BAM</span><span class="sxs-lookup"><span data-stu-id="c6680-107">BAM artifacts</span></span>  
  
 <span data-ttu-id="c6680-108">La modification des propriétés de déploiement peut vous permettre de modifier l'emplacement de destination dans lequel est copié le fichier d'artefact lorsque l'application est installée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="c6680-108">You might want to modify the deployment properties to change the destination location to which the artifact file will be copied when the application is installed on the local computer.</span></span> <span data-ttu-id="c6680-109">Le fichier n'est pas copié sur l'ordinateur local lors de l'installation si vous n'indiquez pas de chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="c6680-109">If you do not provide a path, the file will not be copied to the local computer on installation.</span></span>  
  
 <span data-ttu-id="c6680-110">En outre, vous pouvez souhaiter modifier les options suivantes d'un assembly .NET :</span><span class="sxs-lookup"><span data-stu-id="c6680-110">In addition, you might want to modify the following options for a .NET assembly:</span></span>  
  
-   <span data-ttu-id="c6680-111">**Ajouter au global assembly cache sur Ajouter une ressource (gacutil).**</span><span class="sxs-lookup"><span data-stu-id="c6680-111">**Add to the global assembly cache on add resource (gacutil).**</span></span> <span data-ttu-id="c6680-112">si vous sélectionnez cette option, l'assembly est ajouté dans le GAC sur l'ordinateur local lors de son ajout dans l'application.</span><span class="sxs-lookup"><span data-stu-id="c6680-112">When you select this option, the assembly is added to the global assembly cache (GAC) on the local computer when the assembly is added to the application.</span></span> <span data-ttu-id="c6680-113">En outre, si vous mettez ensuite à jour l’assembly (faites un clic droit et cliquez sur **Actualiser**), l’assembly est ajouté au GAC.</span><span class="sxs-lookup"><span data-stu-id="c6680-113">In addition, if you later refresh the assembly (right-click it and click **Refresh**), the assembly is added to the GAC.</span></span> <span data-ttu-id="c6680-114">La désactivation de cette option ne supprime pas l'assembly du GAC.</span><span class="sxs-lookup"><span data-stu-id="c6680-114">Clearing the check box for this option does not remove the assembly from the GAC, if it currently exists there.</span></span>  
  
-   <span data-ttu-id="c6680-115">**Ajouter au global assembly cache lors de l’importation du fichier MSI (gacutil).**</span><span class="sxs-lookup"><span data-stu-id="c6680-115">**Add to the global assembly cache on MSI file import (gacutil).**</span></span> <span data-ttu-id="c6680-116">Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que le fichier .msi est importé dans un groupe BizTalk, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'importation.</span><span class="sxs-lookup"><span data-stu-id="c6680-116">When you select this option, if the application is exported to an .msi file, and the .msi file is imported into a BizTalk group, the assembly is installed in the GAC on the local computer as part of the import process.</span></span>  
  
-   <span data-ttu-id="c6680-117">**Ajoutez dans le global assembly cache lors de l’installation du fichier MSI (gacutil).**</span><span class="sxs-lookup"><span data-stu-id="c6680-117">**Add to the global assembly cache on MSI file install (gacutil).**</span></span> <span data-ttu-id="c6680-118">Lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, l'assembly est installé dans le GAC sur l'ordinateur local au cours de la procédure d'installation.</span><span class="sxs-lookup"><span data-stu-id="c6680-118">When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, the assembly is installed in the GAC on the local computer as part of the installation process.</span></span>  
  
-   <span data-ttu-id="c6680-119">**Rendre visible pour les composants COM (regasm).**</span><span class="sxs-lookup"><span data-stu-id="c6680-119">**Make visible to COM components (regasm).**</span></span> <span data-ttu-id="c6680-120">lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, un assembly COM géré est ajouté au Registre Windows sur l'ordinateur local au cours de la procédure d'installation.</span><span class="sxs-lookup"><span data-stu-id="c6680-120">When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM assembly is added to the Windows registry on the local computer as part of the installation process.</span></span> <span data-ttu-id="c6680-121">Si vous spécifiez cette option, vous devez également préciser un emplacement pour le fichier dans Destination.</span><span class="sxs-lookup"><span data-stu-id="c6680-121">If you specify this option, you must also specify a location for the file in Destination.</span></span>  
  
-   <span data-ttu-id="c6680-122">**Inscrire les composants traités (regsvcs).**</span><span class="sxs-lookup"><span data-stu-id="c6680-122">**Register serviced components (regsvcs).**</span></span> <span data-ttu-id="c6680-123">lorsque vous sélectionnez cette option, si l'application est exportée vers un fichier .msi et que l'application est installée sur un ordinateur à partir du fichier .msi, un assembly COM+ géré est ajouté au Registre Windows sur l'ordinateur local au cours de la procédure d'installation.</span><span class="sxs-lookup"><span data-stu-id="c6680-123">When you select this option, if the application is exported to an .msi file, and the application is installed on a computer from the .msi file, a managed COM+ assembly is added to the Windows registry on the local computer as part of the installation process.</span></span> <span data-ttu-id="c6680-124">Si vous spécifiez cette option, vous devez également préciser un emplacement pour le fichier dans Destination.</span><span class="sxs-lookup"><span data-stu-id="c6680-124">If you specify this option, you must also specify a location for the file in Destination.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c6680-125">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="c6680-125">Prerequisites</span></span>  
 <span data-ttu-id="c6680-126">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c6680-126">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="c6680-127">Vous devez en outre être membre du groupe des administrateurs locaux pour sélectionner une option qui ajoute immédiatement l'assembly au GAC.</span><span class="sxs-lookup"><span data-stu-id="c6680-127">In addition, if you select an option that immediately adds the assembly to the GAC, your account must also be a member of the local Administrator's group.</span></span> <span data-ttu-id="c6680-128">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="c6680-128">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-modify-the-deployment-properties-of-a-resource-artifact"></a><span data-ttu-id="c6680-129">Pour modifier les propriétés de déploiement d'un artefact de ressource</span><span class="sxs-lookup"><span data-stu-id="c6680-129">To modify the deployment properties of a resource artifact</span></span>  
  
1.  <span data-ttu-id="c6680-130">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="c6680-130">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c6680-131">Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant l'artefact pour lequel modifier les options de déploiement, puis l'application contenant l'artefact.</span><span class="sxs-lookup"><span data-stu-id="c6680-131">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the artifact for which to modify deployment options, and then expand the application containing the artifact.</span></span>  
  
3.  <span data-ttu-id="c6680-132">Cliquez sur le **ressources** dossier, cliquez sur l’artefact, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="c6680-132">Click the **Resources** folder, right-click the artifact, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="c6680-133">Sur le **Options** onglet, modifier les options de déploiement si nécessaire, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6680-133">On the **Options** tab, modify the deployment options as necessary, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6680-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6680-134">See Also</span></span>  
 [<span data-ttu-id="c6680-135">La gestion des assemblys .NET, certificats et autres ressources</span><span class="sxs-lookup"><span data-stu-id="c6680-135">Managing .NET Assemblies, Certificates, and Other Resources</span></span>](../core/managing-net-assemblies-certificates-and-other-resources.md)