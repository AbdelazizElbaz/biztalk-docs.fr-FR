---
title: "Mise à niveau de BizTalk Accelerator pour RosettaNet (BTARN) dans BizTalk Server | Documents Microsoft »"
description: "Suivez les étapes de mise à niveau pour mettre à jour BTARN vers la version actuelle de BizTalk Server"
author: MandiOhlinger
manager: anneta
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 
ms.author: mandia
ms.openlocfilehash: 16e6083f3e5fb1778d77536cd602ee2208c0005f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="upgrade-the-rosettanet-accelerator"></a><span data-ttu-id="74bcf-103">Mise à niveau de l’accélérateur RosettaNet</span><span class="sxs-lookup"><span data-stu-id="74bcf-103">Upgrade the RosettaNet accelerator</span></span>

## <a name="upgrade-overview"></a><span data-ttu-id="74bcf-104">Vue d’ensemble de la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="74bcf-104">Upgrade overview</span></span>
<span data-ttu-id="74bcf-105">Vous pouvez mettre à niveau la version précédente de BizTalk Accelerator pour l’installation de RosettaNet (BTARN) vers la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="74bcf-105">You can upgrade the previous version of the BizTalk Accelerator for RosettaNet (BTARN) installation to the current version.</span></span> <span data-ttu-id="74bcf-106">Le processus de mise à niveau implique la mise à niveau de BizTalk Server et puis mise à niveau de BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-106">The upgrade process involves upgrading BizTalk Server, and then upgrading BTARN.</span></span>  
  
 <span data-ttu-id="74bcf-107">Vous pouvez mettre à niveau à partir de la version précédente de BTARN à un en exécutant le programme d’installation de BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-107">You can upgrade from the previous version of BTARN to a by running the BTARN installation program.</span></span> <span data-ttu-id="74bcf-108">Le programme d’installation migre les informations de configuration de BTRAN vers la version actuelle.</span><span class="sxs-lookup"><span data-stu-id="74bcf-108">The setup migrates the BTRAN configuration information to the current version.</span></span>  
  
 <span data-ttu-id="74bcf-109">Dans un environnement de BTARN multiserveur, vous devez mettre à niveau tous les serveurs BizTalk tout d’abord, puis à BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-109">In a multi-server BTARN environment, you should upgrade all BizTalk Servers first, and then to BTARN.</span></span> <span data-ttu-id="74bcf-110">Migrez vos serveur dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="74bcf-110">Migrate your servers in the following order:</span></span>  
  
-   <span data-ttu-id="74bcf-111">Le serveur hébergeant le groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="74bcf-111">The server hosting the BizTalk Group</span></span>  
  
-   <span data-ttu-id="74bcf-112">Chaque nœud de traitement</span><span class="sxs-lookup"><span data-stu-id="74bcf-112">Each processing node</span></span>  
  
-   <span data-ttu-id="74bcf-113">Le serveur du portail BAM</span><span class="sxs-lookup"><span data-stu-id="74bcf-113">The BAM portal server</span></span>  
  
 <span data-ttu-id="74bcf-114">Dans la BTARN mise à niveau, assurez-vous de que procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="74bcf-114">In the BTARN upgrade process, ensure you do the following:</span></span>  
  
-   <span data-ttu-id="74bcf-115">Vérifiez que le service SQL Server (MSSQLSERVER) est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="74bcf-115">Check if the SQL Server (MSSQLSERVER) service is running.</span></span>  
  
-   <span data-ttu-id="74bcf-116">N'exécutez pas une installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="74bcf-116">Do not run a silent installation.</span></span>  
  
## <a name="upgrade-steps"></a><span data-ttu-id="74bcf-117">Étapes de la mise à niveau</span><span class="sxs-lookup"><span data-stu-id="74bcf-117">Upgrade steps</span></span>  
  
1.  <span data-ttu-id="74bcf-118">Mise à niveau de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="74bcf-118">Upgrade BizTalk Server.</span></span> <span data-ttu-id="74bcf-119">Consultez [BizTalk Server quelles sont les nouveautés, Installation, Configuration et mise à niveau](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="74bcf-119">See [BizTalk Server What's New, Installation, Configuration, and Upgrade](../../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
  
2.  <span data-ttu-id="74bcf-120">Sauvegardez la base de données BTARN et les schémas de message BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-120">Back up the BTARN database and BTARN message schemas.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="74bcf-121">Vous devez sauvegarder la base de données BTARN pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="74bcf-121">You should back up the BTARN database for safety reasons.</span></span> <span data-ttu-id="74bcf-122">Le programme d’installation migre la base de données BTRAN vers une version plus récente.</span><span class="sxs-lookup"><span data-stu-id="74bcf-122">The installation program migrates the BTRAN database to the newer version.</span></span>  
  
3.  <span data-ttu-id="74bcf-123">Sauvegardez tous les fichiers sous le *< lecteur\>*: \Program Files\\Microsoft BizTalk Accelerator pour RosettaNet dossier que vous avez apporté des modifications, par exemple, les fichiers dans le Kit de développement.</span><span class="sxs-lookup"><span data-stu-id="74bcf-123">Back up any files under the *<drive\>*:\Program Files\\Microsoft BizTalk Accelerator for RosettaNet folder that you have made changes to, for example, files in the SDK.</span></span>  
  
4.  <span data-ttu-id="74bcf-124">Annulez le déploiement des projets ou assemblys qui contiennent des références à une ou plusieurs versions des assemblys de BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-124">Undeploy any projects or assemblies that have references to one or more of the previous versions of BTARN assemblies.</span></span>  
  
5.  <span data-ttu-id="74bcf-125">Dans Visual Studio, annulez manuellement le déploiement de tous les assemblys BTARN, dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="74bcf-125">In Visual Studio, manually undeploy all BTARN assemblies, in the following order:</span></span>  
  
    -   <span data-ttu-id="74bcf-126">Microsoft.Solutions.BTARN.CommonTypes</span><span class="sxs-lookup"><span data-stu-id="74bcf-126">Microsoft.Solutions.BTARN.CommonTypes</span></span>  
  
    -   <span data-ttu-id="74bcf-127">Microsoft.Solutions.BTARN.GlobalSchemas</span><span class="sxs-lookup"><span data-stu-id="74bcf-127">Microsoft.Solutions.BTARN.GlobalSchemas</span></span>  
  
    -   <span data-ttu-id="74bcf-128">Microsoft.Solutions.BTARN.PipelineReceive</span><span class="sxs-lookup"><span data-stu-id="74bcf-128">Microsoft.Solutions.BTARN.PipelineReceive</span></span>  
  
    -   <span data-ttu-id="74bcf-129">Microsoft.Solutions.BTARN.PipelineSend</span><span class="sxs-lookup"><span data-stu-id="74bcf-129">Microsoft.Solutions.BTARN.PipelineSend</span></span>  
  
    -   <span data-ttu-id="74bcf-130">Microsoft.Solutions.BTARN.PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="74bcf-130">Microsoft.Solutions.BTARN.PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="74bcf-131">Microsoft.Solutions.BTARN.PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="74bcf-131">Microsoft.Solutions.BTARN.PrivateResponder</span></span>  
  
    -   <span data-ttu-id="74bcf-132">Microsoft.Solutions.BTARN.PublicInitiator</span><span class="sxs-lookup"><span data-stu-id="74bcf-132">Microsoft.Solutions.BTARN.PublicInitiator</span></span>  
  
    -   <span data-ttu-id="74bcf-133">Microsoft.Solutions.BTARN.PublicResponder</span><span class="sxs-lookup"><span data-stu-id="74bcf-133">Microsoft.Solutions.BTARN.PublicResponder</span></span>  
  
    -   <span data-ttu-id="74bcf-134">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span><span class="sxs-lookup"><span data-stu-id="74bcf-134">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span></span>  
  
    -   <span data-ttu-id="74bcf-135">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span><span class="sxs-lookup"><span data-stu-id="74bcf-135">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span></span>  
  
    -   <span data-ttu-id="74bcf-136">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span><span class="sxs-lookup"><span data-stu-id="74bcf-136">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span></span>  
  
6.  <span data-ttu-id="74bcf-137">Exécutez l’installation de BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-137">Run the BTARN installation.</span></span> <span data-ttu-id="74bcf-138">Consultez [installer et configurer l’accélérateur RosettaNet](install-configure-biztalk-accelerator-for-rosettanet.md).</span><span class="sxs-lookup"><span data-stu-id="74bcf-138">See [Install and configure the RosettaNet accelerator](install-configure-biztalk-accelerator-for-rosettanet.md).</span></span>
  
7.  <span data-ttu-id="74bcf-139">Utilisez **BTSTask.exe** (\Program Files\Microsoft BizTalk Server) à redéployer manuellement les assemblys BTARN dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="74bcf-139">Use **BTSTask.exe** (\Program Files\Microsoft BizTalk Server) to manually redeploy the BTARN assemblies in the following order:</span></span>  
  
    -   <span data-ttu-id="74bcf-140">Microsoft.Solutions.BTARN.CommonTypes</span><span class="sxs-lookup"><span data-stu-id="74bcf-140">Microsoft.Solutions.BTARN.CommonTypes</span></span>  
  
    -   <span data-ttu-id="74bcf-141">Microsoft.Solutions.BTARN.GlobalSchemas</span><span class="sxs-lookup"><span data-stu-id="74bcf-141">Microsoft.Solutions.BTARN.GlobalSchemas</span></span>  
  
    -   <span data-ttu-id="74bcf-142">Microsoft.Solutions.BTARN.PipelineReceive</span><span class="sxs-lookup"><span data-stu-id="74bcf-142">Microsoft.Solutions.BTARN.PipelineReceive</span></span>  
  
    -   <span data-ttu-id="74bcf-143">Microsoft.Solutions.BTARN.PipelineSend</span><span class="sxs-lookup"><span data-stu-id="74bcf-143">Microsoft.Solutions.BTARN.PipelineSend</span></span>  
  
    -   <span data-ttu-id="74bcf-144">Microsoft.Solutions.BTARN.PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="74bcf-144">Microsoft.Solutions.BTARN.PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="74bcf-145">Microsoft.Solutions.BTARN.PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="74bcf-145">Microsoft.Solutions.BTARN.PrivateResponder</span></span>  
  
    -   <span data-ttu-id="74bcf-146">Microsoft.Solutions.BTARN.PublicInitiator</span><span class="sxs-lookup"><span data-stu-id="74bcf-146">Microsoft.Solutions.BTARN.PublicInitiator</span></span>  
  
    -   <span data-ttu-id="74bcf-147">Microsoft.Solutions.BTARN.PublicResponder</span><span class="sxs-lookup"><span data-stu-id="74bcf-147">Microsoft.Solutions.BTARN.PublicResponder</span></span>  
  
    -   <span data-ttu-id="74bcf-148">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span><span class="sxs-lookup"><span data-stu-id="74bcf-148">Microsoft.Solutions.BTARN.Schemas.RNIFv11</span></span>  
  
    -   <span data-ttu-id="74bcf-149">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span><span class="sxs-lookup"><span data-stu-id="74bcf-149">Microsoft.Solutions.BTARN.Schemas.RNIFv20</span></span>  
  
    -   <span data-ttu-id="74bcf-150">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span><span class="sxs-lookup"><span data-stu-id="74bcf-150">Microsoft.Solutions.BTARN.Schemas.RNPIPs</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="74bcf-151">Pour plus d’informations sur **BTSTask.exe**, consultez la rubrique « Référence de ligne de commande BTSTask » dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="74bcf-151">For more information about **BTSTask.exe**, see the "BTSTask Command-line Reference" topic in BizTalk Server Help.</span></span>  
  
8.  <span data-ttu-id="74bcf-152">Regénérez les projets ou les assemblys qui contiennent une référence à un ou plusieurs des [assemblys BTARN.</span><span class="sxs-lookup"><span data-stu-id="74bcf-152">Rebuild any projects or assemblies that have a reference to one or more of the [BTARN assemblies.</span></span> <span data-ttu-id="74bcf-153">Utilisez **BTSTask.exe** à redéployer manuellement ces projets.</span><span class="sxs-lookup"><span data-stu-id="74bcf-153">Use **BTSTask.exe** to manually redeploy these projects.</span></span>  
  
9. <span data-ttu-id="74bcf-154">Mettez à niveau les dossiers virtuels dans IIS à partir de ASP.NET 2.0 vers ASP.NET 4.0 pour ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="74bcf-154">Upgrade the virtual folders in IIS from ASP.NET 2.0 to ASP.NET 4.0 for the following:</span></span>  
  
    -   <span data-ttu-id="74bcf-155">BTARNApp</span><span class="sxs-lookup"><span data-stu-id="74bcf-155">BTARNApp</span></span>  
  
    -   <span data-ttu-id="74bcf-156">BTARNHttpReceive</span><span class="sxs-lookup"><span data-stu-id="74bcf-156">BTARNHttpReceive</span></span>  
  
10. <span data-ttu-id="74bcf-157">Redémarrez l'ordinateur pour appliquer les modifications éventuellement effectuées.</span><span class="sxs-lookup"><span data-stu-id="74bcf-157">Restart the computer to apply any modifications done.</span></span>  
  
