---
title: Comment installer un Assembly dans le GAC | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6afc2f81-fa28-4144-b4bd-21c8f35f2270
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80e3a5126a56b945b2aa7b53aec71fbe83d678a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-install-an-assembly-in-the-gac"></a><span data-ttu-id="e5024-102">Installation d'un assembly dans le GAC</span><span class="sxs-lookup"><span data-stu-id="e5024-102">How to Install an Assembly in the GAC</span></span>
<span data-ttu-id="e5024-103">Installer et désinstaller un assembly BizTalk dans le global assembly cache (GAC) à l’aide de l’outil Gacutil fourni avec manuellement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5024-103">Manually install and uninstall a BizTalk assembly in the global assembly cache (GAC) using the Gacutil tool included with [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e5024-104">À l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], vous pouvez avoir des assemblys BizTalk automatiquement installés dans le GAC lorsqu’ils sont déployés à partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5024-104">Using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], you can have BizTalk assemblies automatically installed in the GAC when they are deployed from [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="e5024-105">Définir cette option dans les propriétés de déploiement du projet BizTalk ; consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="e5024-105">Set this this option in the Deployment Properties of the BizTalk project; see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span></span> <span data-ttu-id="e5024-106">Vous ne pouvez pas utiliser cette méthode pour installer des assemblys .NET non - BizTalk dans le GAC ; Vous devez les installer manuellement, comme décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e5024-106">You cannot, use this method to install non-BizTalk .NET assemblies in the GAC; you must install them manually, as described in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5024-107">Vous pouvez également spécifier des options de déploiement pour les assemblys après leur déploiement dans une application BizTalk, à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5024-107">You can also specify deployment options for assemblies after they are deployed into a BizTalk application by using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="e5024-108">Consultez [comment modifier les Options de déploiement d’un Assembly BizTalk](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md), et [comment modifier les Options de déploiement d’un Assembly .NET, un composant COM, un fichier ou un artefact BAM](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md).</span><span class="sxs-lookup"><span data-stu-id="e5024-108">See [How to Modify the Deployment Options of a BizTalk Assembly](../core/how-to-modify-the-deployment-options-of-a-biztalk-assembly.md), and [How to Modify the Deployment Options of a .NET Assembly, COM Component, File, or BAM Artifact](../core/modify-deployment-options-of-net-assembly-com-component-file-bam-artifact.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e5024-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e5024-109">Prerequisites</span></span>  
<span data-ttu-id="e5024-110">Connectez-vous avec un compte qui a l’autorisation d’écriture dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="e5024-110">Sign in with an account that has Write permission to the GAC.</span></span> <span data-ttu-id="e5024-111">Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="e5024-111">The Administrators account on the local computer has this permission.</span></span>  

  
## <a name="install-using-gacutil"></a><span data-ttu-id="e5024-112">Installer à l’aide de gacutil</span><span class="sxs-lookup"><span data-stu-id="e5024-112">Install using gacutil</span></span>
  
1.  <span data-ttu-id="e5024-113">Copiez l’assembly BizTalk sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e5024-113">Copy the BizTalk assembly to your local computer.</span></span>  
  
2.  <span data-ttu-id="e5024-114">Ouvrez **invite de commandes développeur pour Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="e5024-114">Open **Developer Command Prompt for Visual Studio** as administrator.</span></span>  
  
3.  <span data-ttu-id="e5024-115">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e5024-115">Type the following:</span></span>  
  
     `gacutil /i path_to_assembly_file /f`

    <span data-ttu-id="e5024-116">Par exemple, tapez :</span><span class="sxs-lookup"><span data-stu-id="e5024-116">For example, type:</span></span>  
    `gacutil /i c:\temp\filename.dll /f`
    
<span data-ttu-id="e5024-117">Le `/f` option remplace tout assembly existant qui porte le même nom d’assembly.</span><span class="sxs-lookup"><span data-stu-id="e5024-117">The `/f` option overwrites any existing assembly that has the same assembly name.</span></span> <span data-ttu-id="e5024-118">Pour plus d’informations sur les options et les commandes de gacutil, tapez `gacutil /?`.</span><span class="sxs-lookup"><span data-stu-id="e5024-118">For more info on the gacutil commands and options, type `gacutil /?`.</span></span> 

## <a name="uninstall-using-gacutil"></a><span data-ttu-id="e5024-119">Désinstallation à l’aide de gacutil</span><span class="sxs-lookup"><span data-stu-id="e5024-119">Uninstall using gacutil</span></span>
<span data-ttu-id="e5024-120">Désinstallation d’un assembly à partir du global assembly cache (GAC) est nécessaire pour annuler complètement le déploiement d’une application.</span><span class="sxs-lookup"><span data-stu-id="e5024-120">Uninstalling an assembly from the global assembly cache (GAC) is necessary to completely undeploy an application.</span></span> <span data-ttu-id="e5024-121">Vous pouvez automatiser ce processus.</span><span class="sxs-lookup"><span data-stu-id="e5024-121">You can automate this process.</span></span> <span data-ttu-id="e5024-122">Avant de déployer l’application dans un environnement de production, écrivez un script de pré-traitement qui désinstalle automatiquement l’assembly du GAC lors de la désinstallation de l’application.</span><span class="sxs-lookup"><span data-stu-id="e5024-122">Before deploying the application into a production environment, write a pre-processing script that uninstalls the assembly from the GAC automatically when the application is uninstalled.</span></span> <span data-ttu-id="e5024-123">Consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement de l’Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span><span class="sxs-lookup"><span data-stu-id="e5024-123">See [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
 <span data-ttu-id="e5024-124">Vous pouvez également utiliser un script pour supprimer des paramètres et des fichiers supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="e5024-124">You can also use a script to remove additional files and settings.</span></span> <span data-ttu-id="e5024-125">Consultez [comment supprimer les autres fichiers et paramètres d’une Application BizTalk](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="e5024-125">See [How to Remove Other Files and Settings for a BizTalk Application](../core/how-to-remove-other-files-and-settings-for-a-biztalk-application.md).</span></span>  
 
#### <a name="using-the-windows-interface"></a><span data-ttu-id="e5024-126">Utilisation de l'interface Windows</span><span class="sxs-lookup"><span data-stu-id="e5024-126">Using the Windows interface</span></span>  
  
1.  <span data-ttu-id="e5024-127">Ouvrez à % systemdrive%\Windows\Assembly.</span><span class="sxs-lookup"><span data-stu-id="e5024-127">Open to %systemdrive%\Windows\Assembly.</span></span>  
  
2.  <span data-ttu-id="e5024-128">Avec le bouton droit de chaque fichier d’assembly inclus dans votre application, sélectionnez **désinstallation**, puis sélectionnez **Oui** pour confirmer.</span><span class="sxs-lookup"><span data-stu-id="e5024-128">Right-click each assembly file included in your application, select **Uninstall**, and then select **Yes** to confirm.</span></span>  
  
#### <a name="using-the-command-line"></a><span data-ttu-id="e5024-129">À l’aide de la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="e5024-129">Using the command line</span></span>  
  
1.  <span data-ttu-id="e5024-130">Ouvrez **invite de commandes développeur pour Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="e5024-130">Open **Developer Command Prompt for Visual Studio** as administrator.</span></span> 
  
2.  <span data-ttu-id="e5024-131">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e5024-131">Type the following:</span></span>  
  
     <span data-ttu-id="e5024-132">`gacutil /u`\< *nom d’assembly qualifié complet*\></span><span class="sxs-lookup"><span data-stu-id="e5024-132">`gacutil /u` \<*fully qualified assembly name*\></span></span>  
  
     <span data-ttu-id="e5024-133">Par exemple, tapez :</span><span class="sxs-lookup"><span data-stu-id="e5024-133">For example, type:</span></span>  
     `gacutil /u "hello,Version=1.0.0.0, Culture=neutral, PublicKeyToken=0123456789ABCDEF"`
       
## <a name="see-also"></a><span data-ttu-id="e5024-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5024-134">See Also</span></span>  
 [<span data-ttu-id="e5024-135">Déploiement des assemblys BizTalk à partir de Visual Studio dans une application BizTalk</span><span class="sxs-lookup"><span data-stu-id="e5024-135">Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application</span></span>](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)  
<span data-ttu-id="e5024-136">[Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="e5024-136">[Undeploying BizTalk Applications](../core/undeploying-biztalk-applications.md) </span></span>  
 <span data-ttu-id="e5024-137">[Comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="e5024-137">[How to Uninstall a BizTalk Application](../core/how-to-uninstall-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="e5024-138">Comment supprimer une Application BizTalk du groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="e5024-138">How to Delete a BizTalk Application from the BizTalk Group</span></span>](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md)
 