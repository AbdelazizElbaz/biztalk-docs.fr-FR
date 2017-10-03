---
title: Installer BizTalk Adapter Pack 2016 | Documents Microsoft
description: "Une installation standard ou personnalisée de 2016 BAP, éditions 32 bits et 64 bits, installez en mode silencieux"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f3e1717-8063-4460-bfdc-a933cd58a5c1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0939ddaa11e409ec42989062e28314c14277549
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="install-the-biztalk-adapter-pack-2016"></a><span data-ttu-id="eb0ef-103">Installer BizTalk Adapter Pack 2016</span><span class="sxs-lookup"><span data-stu-id="eb0ef-103">Install the BizTalk Adapter Pack 2016</span></span>
<span data-ttu-id="eb0ef-104">Installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] des deux manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-104">Install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in the following two ways:</span></span>  
  
-   <span data-ttu-id="eb0ef-105">**En mode interactif**: exécuter l’Assistant Installation</span><span class="sxs-lookup"><span data-stu-id="eb0ef-105">**In interactive mode**: Run the setup wizard</span></span>  
  
-   <span data-ttu-id="eb0ef-106">**En mode silencieux**: utiliser la ligne de commande</span><span class="sxs-lookup"><span data-stu-id="eb0ef-106">**In silent mode**: Use the command line</span></span>  
  
> [!IMPORTANT]
> - <span data-ttu-id="eb0ef-107">Vous devez disposer des privilèges d’administrateur sur l’ordinateur sur lequel vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], indépendamment de si vous installez à l’aide de l’Assistant, ou la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-107">You must have administrative privileges on the computer where you install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)], irrespective of whether you are installing using the wizard, or the command line.</span></span>  
> - <span data-ttu-id="eb0ef-108">Être que toutes les le [les composants logiciels requis](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) sont installés avant d’installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-108">Be sure all the [software prerequisites](../adapters-and-accelerators/software-prerequisites-for-biztalk-adapter-pack-2016.md) are installed before installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>

## <a name="typical-vs-custom-installation"></a><span data-ttu-id="eb0ef-109">Installation personnalisée d’installation par défaut et</span><span class="sxs-lookup"><span data-stu-id="eb0ef-109">Typical vs custom installation</span></span>  
<span data-ttu-id="eb0ef-110">Répertorie les types d’installation, ainsi que les fonctionnalités qui sont installées avec chaque option :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-110">Lists the installation types, and the features that are installed with each option:</span></span>  
  
-   <span data-ttu-id="eb0ef-111">Le **standard** et **Complete** options installer toutes les cartes, avec les fournisseurs de données associé.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-111">The **Typical** and **Complete** options install all the adapters, with the associated data providers.</span></span> <span data-ttu-id="eb0ef-112">Vous n’avez pas de l’option de choix d’une carte spécifique d’installation.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-112">You do not have the option of choosing a specific adapter to install.</span></span>  
  
-   <span data-ttu-id="eb0ef-113">Le **personnalisé** option installe une ou plusieurs cartes, avec les fournisseurs de données associé.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-113">The **Custom** option installs one or more adapters, with the associated data providers.</span></span> <span data-ttu-id="eb0ef-114">Vous pouvez choisir les adaptateurs à installer.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-114">You can choose which adapters to install.</span></span> <span data-ttu-id="eb0ef-115">Si vous choisissez d’installer un fournisseur de données, vous devez également installer l’adaptateur correspondant.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-115">If you choose to install a data provider, you must also install the corresponding adapter.</span></span> <span data-ttu-id="eb0ef-116">Toutefois, vous pouvez installer un adaptateur sans installer le fournisseur de données correspondant.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-116">However, you can install an adapter without installing the corresponding data provider.</span></span> <span data-ttu-id="eb0ef-117">Cela en développant le **ADO fournisseurs** nœud, puis en sélectionnant les fournisseurs que vous ne souhaitez pas installer.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-117">Do this by expanding the **ADO Providers** node, and then selecting the providers that you don't want to install.</span></span> <span data-ttu-id="eb0ef-118">Consultez **installer à l’aide de l’Assistant Installation** (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="eb0ef-118">See **Install using the setup wizard** (in this topic).</span></span>  
  
     <span data-ttu-id="eb0ef-119">Par exemple, si vous installez le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], vous devez également installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-119">For example, if you install the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], you must also install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="eb0ef-120">Toutefois, vous pouvez installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] sans installer le [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-120">However, you can install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] without installing the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)].</span></span>  
  
## <a name="32-bit-and-64-bit-install-scenarios"></a><span data-ttu-id="eb0ef-121">scénarios d’installation de 32 bits et 64 bits</span><span class="sxs-lookup"><span data-stu-id="eb0ef-121">32-bit and 64-bit install scenarios</span></span>
 <span data-ttu-id="eb0ef-122">Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peut être utilisé pour :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-122">With [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] can be used for:</span></span> 
  
-   [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="eb0ef-123">au moment du design (lors de la génération des métadonnées pour les opérations sur les applications métiers)</span><span class="sxs-lookup"><span data-stu-id="eb0ef-123"> design time (when generating metadata for operations on LOB applications)</span></span>
  
-   <span data-ttu-id="eb0ef-124">Moment du design console Administration de BizTalk Server (pour créer des ports physiques)</span><span class="sxs-lookup"><span data-stu-id="eb0ef-124">BizTalk Server Administration console design time (for creating physical ports)</span></span>
  
    > [!NOTE]
    >  <span data-ttu-id="eb0ef-125">Console d’Administration de BizTalk Server s’exécute comme une application de la Console MMC (Microsoft Management Console) 32 bits.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-125">BizTalk Server Administration console runs as a 32-bit Microsoft Management Console (MMC) application.</span></span>  
  
-   <span data-ttu-id="eb0ef-126">Durée d’exécution BizTalk (pendant l’envoi et réception de messages à partir d’applications métier)</span><span class="sxs-lookup"><span data-stu-id="eb0ef-126">BizTalk run time (when sending and receiving messages from LOB applications)</span></span>

<span data-ttu-id="eb0ef-127">Vous pouvez utiliser un ordinateur unique pour toutes ces tâches, ou utiliser des ordinateurs distincts.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-127">You can use a single computer for all these taks, or use different computers.</span></span> <span data-ttu-id="eb0ef-128">Étant donné que les deux [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] et MMC de BizTalk sont des processus 32 bits, vous devez installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sur l’ordinateur où vous effectuez les tâches de conception.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-128">Because both [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and BizTalk MMC are 32-bit processes, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on the computer where you complete the design-time tasks.</span></span> 

### <a name="32-bit-install-scenario"></a><span data-ttu-id="eb0ef-129">scénario d’installation 32 bits</span><span class="sxs-lookup"><span data-stu-id="eb0ef-129">32-bit install scenario</span></span>
<span data-ttu-id="eb0ef-130">Installer les logiciels suivants sur chaque ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-130">Install the following software on each computer.</span></span> <span data-ttu-id="eb0ef-131">Si vous utilisez un seul ordinateur, tous les logiciels doivent être installé sur cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-131">If you are using a single computer, all the software must be installed on that computer.</span></span> 
 
1. <span data-ttu-id="eb0ef-132">Installer 32 bits[!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb0ef-132">Install 32-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]</span></span>
2. <span data-ttu-id="eb0ef-133">Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-133">Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>
3. <span data-ttu-id="eb0ef-134">Client d’installation 32 bits métier et d’autres requis DLL.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-134">Install 32-bit LOB client and other required DLLs.</span></span>  
  
### <a name="64-bit-install-scenarios"></a><span data-ttu-id="eb0ef-135">scénarios d’installation 64 bits</span><span class="sxs-lookup"><span data-stu-id="eb0ef-135">64-bit install scenarios</span></span>
  
|<span data-ttu-id="eb0ef-136">Pour le moment du design Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eb0ef-136">For Visual Studio design time</span></span>|<span data-ttu-id="eb0ef-137">Moment du design pour la console MMC de BizTalk</span><span class="sxs-lookup"><span data-stu-id="eb0ef-137">For BizTalk MMC design time</span></span>|<span data-ttu-id="eb0ef-138">Pour le moment de l’exécution de BizTalk</span><span class="sxs-lookup"><span data-stu-id="eb0ef-138">For BizTalk run time</span></span>|<span data-ttu-id="eb0ef-139">Pour la conception de Visual Studio heure et/ou de conception BizTalk MMC + BizTalk moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="eb0ef-139">For Visual Studio design time and/or BizTalk MMC design time + BizTalk run time</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="eb0ef-140">-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-140">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-141">-Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-141">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-142">-Installer le client LOB de 32 bits et d’autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-142">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="eb0ef-143">-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-143">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-144">-Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-144">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-145">-Installer le client LOB de 32 bits et d’autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-145">- Install 32-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="eb0ef-146">**Pour un processus de BizTalk 32 bits**:</span><span class="sxs-lookup"><span data-stu-id="eb0ef-146">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="eb0ef-147">-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-147">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-148">-Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-148">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-149">-Installer le client LOB de 32 bits et d’autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-149">- Install 32-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="eb0ef-150">**Pour un processus BizTalk de 64 bits**:</span><span class="sxs-lookup"><span data-stu-id="eb0ef-150">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="eb0ef-151">-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-151">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-152">-Installer 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-152">- Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-153">-Installer 64 bits LOB client et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-153">- Install 64-bit LOB client and other required DLLs.</span></span>|<span data-ttu-id="eb0ef-154">**Pour un processus de BizTalk 32 bits**:</span><span class="sxs-lookup"><span data-stu-id="eb0ef-154">**For a 32-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="eb0ef-155">-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-155">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-156">-Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-156">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-157">-Installer le client LOB de 32 bits et d’autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-157">- Install 32-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="eb0ef-158">**Pour un processus BizTalk de 64 bits**:</span><span class="sxs-lookup"><span data-stu-id="eb0ef-158">**For a 64-bit BizTalk process**:</span></span><br /><br /> <span data-ttu-id="eb0ef-159">-Installer 64 bits [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-159">- Install 64-bit [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-160">-Installer 64 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-160">- Install 64-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-161">-Installer 64 bits LOB client et autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-161">- Install 64-bit LOB client and other required DLLs.</span></span><br /><br /> <span data-ttu-id="eb0ef-162">-Installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-162">- Install 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span><br /><br /> <span data-ttu-id="eb0ef-163">-Installer le client LOB de 32 bits et d’autres DLL requise.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-163">- Install 32-bit LOB client and other required DLLs.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="eb0ef-164">Sur n’importe quel ordinateur où vous souhaitez effectuer des tâches de conception, à l’aide [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] ou MMC de BizTalk, vous devez installer 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-164">On any computer where you want to do design-time tasks, using either [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] or BizTalk MMC, you must install the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
## <a name="install-using-the-setup-wizard"></a><span data-ttu-id="eb0ef-165">Installer à l’aide de l’Assistant Installation</span><span class="sxs-lookup"><span data-stu-id="eb0ef-165">Install using the setup wizard</span></span>  
<span data-ttu-id="eb0ef-166">Étapes pour installer le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] en mode interactif.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-166">Steps to install the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] in interactive mode.</span></span>  
  
1.  <span data-ttu-id="eb0ef-167">Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-167">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] **setup.exe**.</span></span>  
  
2.  <span data-ttu-id="eb0ef-168">Sélectionnez **installer des adaptateurs Microsoft BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-168">Select **Install Microsoft BizTalk Adapters**.</span></span> <span data-ttu-id="eb0ef-169">Dans la fenêtre suivante, un programme requis manquant est répertorié.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-169">In the next window, any missing prerequisite programs are listed.</span></span> <span data-ttu-id="eb0ef-170">Si un est manquant, puis sélectionnez le programme manquant et le programme d’installation l’installe pour vous.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-170">If any are missing, then select the missing program, and setup installs it for you.</span></span> 

    <span data-ttu-id="eb0ef-171">Par exemple, sélectionnez **étape 2 : installer Microsoft BizTalk Adapter Pack** ou **étape 3 : installer Microsoft BizTalk Adapter Pack (x64)**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-171">For example, select **Step 2: Install Microsoft BizTalk Adapter Pack** or **Step 3: Install Microsoft BizTalk Adapter Pack (x64)**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb0ef-172">Si vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sur un ordinateur virtuel, l’Assistant installation peut afficher un message qu’elle vérifie l’espace disque disponible.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-172">If you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] on a virtual machine, the setup wizard may display a message that it's checking for available disk space.</span></span> <span data-ttu-id="eb0ef-173">Si ce message apparaît se bloque ou restez, nous vous recommandons **installer en mode silencieux** (dans cette rubrique).</span><span class="sxs-lookup"><span data-stu-id="eb0ef-173">If this message appears to hang or just sit there, then we recommend you **Install in silent mode** (in this topic).</span></span>  
  
3.  <span data-ttu-id="eb0ef-174">Dans l’écran de bienvenue, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-174">On the Welcome screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="eb0ef-175">Acceptez le contrat de licence utilisateur final (CLUF), puis sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-175">Accept the end-user license agreement (EULA), and then select **Next**.</span></span>  
  
5.  <span data-ttu-id="eb0ef-176">Dans **choisir le Type d’installation**:</span><span class="sxs-lookup"><span data-stu-id="eb0ef-176">In **Choose Setup Type**:</span></span>  
  
    -   <span data-ttu-id="eb0ef-177">Pour installer les fonctionnalités les plus courantes, sélectionnez **standard**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-177">To install the most common features, select **Typical**.</span></span>  
  
    -   <span data-ttu-id="eb0ef-178">Pour sélectionner les cartes que vous souhaitez installer, sélectionnez **personnalisé**, puis passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-178">To select the adapters you want to install, select **Custom**, and then proceed to the next step.</span></span>  
  
    -   <span data-ttu-id="eb0ef-179">Pour installer toutes les fonctionnalités, sélectionnez **Complete**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-179">To install all the features, select **Complete**.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="eb0ef-180">Pour installer uniquement l’adaptateur que vous utilisez pour interagir avec votre application d’entreprise, sélectionnez le **personnalisé** installation.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-180">To install only the adapter that you use to interface with your enterprise application, select the **Custom** installation.</span></span>  
  
6. <span data-ttu-id="eb0ef-181">**Requis** uniquement si vous choisissez l’installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-181">**Required** only if you chose the Custom installation.</span></span> <span data-ttu-id="eb0ef-182">Si vous avez choisi le **standard** ou **Complete** installation, puis ignorez cette étape et passez à l’étape 7.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-182">If you chose the **Typical** or **Complete** installation, then skip this step, and go to step 7.</span></span>  
  
    1.  <span data-ttu-id="eb0ef-183">Dans **installation personnalisée**, développez **Base adaptateurs** pour voir les adaptateurs disponibles.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-183">In **Custom Setup**, expand **Base Adapters** to see the available adapters.</span></span>  
  
    2.  <span data-ttu-id="eb0ef-184">Pour les cartes que vous ne souhaitez pas, sélectionnez l’icône en regard de la carte, puis **totalité de cette fonctionnalité n’est pas disponible**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-184">For the adapters that you don't want, select the icon next to the adapter, and then select **Entire feature will be unavailable**.</span></span>  
  
    3.  <span data-ttu-id="eb0ef-185">Développez **ADO fournisseurs**, puis sélectionnez les fournisseurs que vous ne souhaitez pas installer.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-185">Expand **ADO Providers**, and then select the providers that you don't want to install.</span></span>  
  
    4.  <span data-ttu-id="eb0ef-186">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-186">Select **Next**.</span></span>  
  
7.  <span data-ttu-id="eb0ef-187">Sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-187">Select **Install**.</span></span>  
  
8.  <span data-ttu-id="eb0ef-188">Dans **Customer Experience Improvement Program**, vous pouvez choisir de les inscrire.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-188">In **Customer Experience Improvement Program**, you can choose to enroll.</span></span> <span data-ttu-id="eb0ef-189">Si vous inscrivez, vous pouvez partager les données suivantes avec Microsoft :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-189">If you enroll, you can share the following data with Microsoft:</span></span>  
  
    -   <span data-ttu-id="eb0ef-190">Les données relatives au matériel de l’ordinateur sur lequel vous installez le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-190">Data related to the computer hardware on which you are installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="eb0ef-191">Les données relatives aux versions enterprise application vous utilisez avec le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-191">Data related to the enterprise application versions you are using with the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
     <span data-ttu-id="eb0ef-192">[CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) fournit plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-192">[CEIP](http://go.microsoft.com/fwlink/p/?LinkId=144699) provides more information.</span></span>  
     
     <span data-ttu-id="eb0ef-193">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-193">Select **OK**.</span></span> 
  
    > [!NOTE]
    >  <span data-ttu-id="eb0ef-194">Vous pouvez toujours modifier ce paramètre en exécutant le programme d’installation en mode de réparation à partir de **programmes**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-194">You can always change this setting by running the Setup in Repair mode from **Programs**.</span></span>  
  
9. <span data-ttu-id="eb0ef-195">Sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-195">Select **Finish**.</span></span>  
  
<a name="BKMK_SilentInst"></a>   
## <a name="install-in-silent-mode"></a><span data-ttu-id="eb0ef-196">Installer en mode silencieux</span><span class="sxs-lookup"><span data-stu-id="eb0ef-196">Install in silent mode</span></span>  
 <span data-ttu-id="eb0ef-197">Utilisez le **msiexec** commande pour effectuer une installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-197">Use the **msiexec** command to do a silent installation.</span></span> <span data-ttu-id="eb0ef-198">Dans le cadre de la commande msiexec, entrez les composants individuels que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-198">As part of the msiexec command, enter the individual components that you want to install.</span></span> <span data-ttu-id="eb0ef-199">Le tableau suivant répertorie les valeurs pour chaque composant dans le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb0ef-199">The following table lists the values for each component in the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="eb0ef-200">Utilisez ces valeurs pour installer (ou supprimer) des composants spécifiques.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-200">Use these values to install (or remove) specific components.</span></span> <span data-ttu-id="eb0ef-201">Pour installer (ou supprimer) plusieurs composants, vous pouvez utiliser une combinaison de ces valeurs séparées par une virgule.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-201">To install (or remove) more than one component, you can use a combination of these values separated by a comma.</span></span>  
  
|<span data-ttu-id="eb0ef-202">Nom du composant</span><span class="sxs-lookup"><span data-stu-id="eb0ef-202">Component name</span></span>|<span data-ttu-id="eb0ef-203">Valeur correspondante pour les propriétés de ligne de commande</span><span class="sxs-lookup"><span data-stu-id="eb0ef-203">Corresponding value for command-line properties</span></span>|  
|---|---|  
|[!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)]|<span data-ttu-id="eb0ef-204">DbFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-204">DbFeature</span></span>|  
|[!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)]|<span data-ttu-id="eb0ef-205">OracleEBSFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-205">OracleEBSFeature</span></span>|  
|[!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)]|<span data-ttu-id="eb0ef-206">SapBaseAdapterFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-206">SapBaseAdapterFeature</span></span>|  
|[!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)]|<span data-ttu-id="eb0ef-207">SiebelBaseAdapterFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-207">SiebelBaseAdapterFeature</span></span>|  
|[!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)]|<span data-ttu-id="eb0ef-208">SqlFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-208">SqlFeature</span></span>|  
|[!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]|<span data-ttu-id="eb0ef-209">SapAdoFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-209">SapAdoFeature</span></span><br /><br /> <span data-ttu-id="eb0ef-210">**Remarque**: vous devez fournir cette valeur uniquement si vous installez le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] également.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-210">**Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] also.</span></span>|  
|[!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)]|<span data-ttu-id="eb0ef-211">SiebelAdoFeature</span><span class="sxs-lookup"><span data-stu-id="eb0ef-211">SiebelAdoFeature</span></span><br /><br /> <span data-ttu-id="eb0ef-212">**Remarque**: vous devez fournir cette valeur uniquement si vous installez le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] également.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-212">**Note**: You must provide this value only if you are installing the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] also.</span></span>|  
|<span data-ttu-id="eb0ef-213">Tous les composants</span><span class="sxs-lookup"><span data-stu-id="eb0ef-213">All components</span></span>|<span data-ttu-id="eb0ef-214">ALL</span><span class="sxs-lookup"><span data-stu-id="eb0ef-214">ALL</span></span>|  
  
> [!IMPORTANT]
>  <span data-ttu-id="eb0ef-215">Les noms de fonctionnalités respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-215">The feature names are case-sensitive.</span></span>  
  
 <span data-ttu-id="eb0ef-216">Les étapes suivantes vous montrent comment effectuer une installation silencieuse de [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] pour les différents composants.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-216">The following steps show you how to complete a silent installation of [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] for different components.</span></span>  
  
### <a name="silent-mode-steps"></a><span data-ttu-id="eb0ef-217">Étapes de mode silencieux</span><span class="sxs-lookup"><span data-stu-id="eb0ef-217">Silent mode steps</span></span>
  
1.  <span data-ttu-id="eb0ef-218">Ouvrez une invite de commandes et accédez à la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] racine dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-218">Open a command prompt, and go to the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] root in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation.</span></span>  
  
2.  <span data-ttu-id="eb0ef-219">Exécutez les commandes suivantes, selon ce que vous souhaitez installer :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-219">Run the following commands based on what you want to install:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eb0ef-220">Pour effectuer une installation sans assistance sur une plateforme x64 64, remplacez `AdaptersSetup.msi` avec `AdaptersSetup64.msi` dans les commandes suivantes.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-220">To do silent installation on an x64-based platform, replace `AdaptersSetup.msi` with `AdaptersSetup64.msi` in the following commands.</span></span>  
  
    -   <span data-ttu-id="eb0ef-221">Pour effectuer une installation complète, qui installe tous les adaptateurs, y compris les fournisseurs de données .NET Framework, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-221">To perform a complete installation, which installs all the adapters including the .NET Framework Data Providers, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=ALL  
        ```  
  
    -   <span data-ttu-id="eb0ef-222">Pour installer uniquement le [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-222">To install only the [!INCLUDE[adapteroracle_short](../includes/adapteroracle-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=DbFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-223">Pour installer uniquement le [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-223">To install only the [!INCLUDE[adapteroraclebusinessshort](../includes/adapteroraclebusinessshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=OracleEBSFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-224">Pour installer uniquement le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-224">To install only the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-225">Pour installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] avec [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-225">To install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] along with [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-226">Pour installer uniquement le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-226">To install only the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-227">Pour installer le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-227">To install the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] along with [!INCLUDE[adoprovidersiebelshort](../includes/adoprovidersiebelshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SiebelBaseAdapterFeature,SiebelAdoFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-228">Pour installer uniquement le [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-228">To install only the [!INCLUDE[adaptersqlshort](../includes/adaptersqlshort-md.md)], type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SqlFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-229">Pour installer tous les adaptateurs de base, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-229">To install all the base adapters, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SiebelBaseAdapterFeature,DbFeature,OracleEBSFeature,SqlFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-230">Pour installer les deux fournisseurs de données .NET Framework, tapez :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-230">To install the two .NET Framework Data Providers, type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapAdoFeature,SiebelAdoFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-231">N’importe quel type d’installation personnalisée en répartissant les composants par une virgule.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-231">Any type of custom installation by separating the components by a comma.</span></span> <span data-ttu-id="eb0ef-232">Par exemple, pour installer le [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] avec la [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)]et le [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-232">For example, to install the [!INCLUDE[adaptersap_short](../includes/adaptersap-short-md.md)] with the [!INCLUDE[adoprovidersapshort](../includes/adoprovidersapshort-md.md)], and the [!INCLUDE[adaptersiebel_short](../includes/adaptersiebel-short-md.md)] type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn ADDLOCAL=SapBaseAdapterFeature,SapAdoFeature,SiebelBaseAdapterFeature  
        ```  
  
    -   <span data-ttu-id="eb0ef-233">Vous pouvez également choisir d’inscrire pour CEIP dans le cadre de l’installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-233">You can also opt to enroll for CEIP as part of the silent installation.</span></span> <span data-ttu-id="eb0ef-234">Type :</span><span class="sxs-lookup"><span data-stu-id="eb0ef-234">Type:</span></span>  
  
        ```  
        msiexec /i AdaptersSetup.msi /qn CEIP_OPTIN=true  
        ```  
  
         <span data-ttu-id="eb0ef-235">Par défaut, l’option est false.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-235">By default the option is false.</span></span> 
  
        > [!IMPORTANT]
        >  <span data-ttu-id="eb0ef-236">Lors de l’installation du [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] version d’évaluation en mode silencieux, l’option par défaut pour CEIP est true.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-236">While installing the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] Evaluation version in silent mode, the default option for CEIP is true.</span></span>  
  
     <span data-ttu-id="eb0ef-237">Pour plus d’informations sur la **msiexec** de commandes, tapez `msiexec` sur la ligne de commande, puis appuyez sur `ENTER`.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-237">For more information about the **msiexec** command, type `msiexec` on the command line, and press `ENTER`.</span></span> <span data-ttu-id="eb0ef-238">Ou accédez à [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span><span class="sxs-lookup"><span data-stu-id="eb0ef-238">Or go to [http://go.microsoft.com/fwlink/p/?LinkId=103199](http://go.microsoft.com/fwlink/p/?LinkId=103199).</span></span>
     
## <a name="known-install-issue"></a><span data-ttu-id="eb0ef-239">Problème d’installation connus</span><span class="sxs-lookup"><span data-stu-id="eb0ef-239">Known install issue</span></span>
<span data-ttu-id="eb0ef-240">Pour une liste complète des problèmes d’installation, consultez **dépannage** rubriques pour chaque adaptateur.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-240">For a comprehensive list of installation-related issues, refer to **Troubleshooting** topics for each adapter.</span></span>  
  
<span data-ttu-id="eb0ef-241">**Le programme d’installation en cours d’exécution sur un ordinateur 64 bits peut lever une erreur lors de l’accès au fichier de schéma**</span><span class="sxs-lookup"><span data-stu-id="eb0ef-241">**Running setup on a 64-bit computer may throw an error while accessing schema file**</span></span>  
  
<span data-ttu-id="eb0ef-242">Le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] le programme d’installation génère une erreur lors de l’accès à la Microsoft.Adapters. *\<AdapterName >*_schema.xml fichier, mais se poursuit avec l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-242">The [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] setup throws an error while accessing the Microsoft.Adapters.*\<AdapterName>*_schema.xml file, but proceeds with the adapter installation.</span></span>  
  
<span data-ttu-id="eb0ef-243">**Cause**</span><span class="sxs-lookup"><span data-stu-id="eb0ef-243">**Cause**</span></span>  
  
<span data-ttu-id="eb0ef-244">Si les versions 32 bits et 64 bits de la [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] sont installés sur le même ordinateur, le fichier de schéma cible utilisé par les deux est la même.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-244">If both 32-bit and 64-bit versions of the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] are installed on the same computer, the target schema file used by both is the same.</span></span> <span data-ttu-id="eb0ef-245">Par conséquent, le fichier est installé par 32 bits [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] peut être utilisé par IIS lorsque le programme d’installation 64 bits tente d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="eb0ef-245">As a result, the file installed by the 32-bit [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] might be in use by IIS when the 64-bit installer tries to access it.</span></span>  
  
<span data-ttu-id="eb0ef-246">**Résolution**</span><span class="sxs-lookup"><span data-stu-id="eb0ef-246">**Resolution**</span></span>  
  
<span data-ttu-id="eb0ef-247">Copiez manuellement le Microsoft.Adapters.  *\<AdapterName >*fichier _schema.xml *C:\Program Files\Microsoft BizTalk Pack (x64) \IIS schémas* à *C:\Windows\System32\inetsrv\config\schema* .</span><span class="sxs-lookup"><span data-stu-id="eb0ef-247">Manually copy the Microsoft.Adapters.*\<AdapterName>*_schema.xml file from *C:\Program Files\Microsoft BizTalk Adapter Pack(x64)\IIS Schemas* to *C:\Windows\System32\inetsrv\config\schema*.</span></span> 
  
## <a name="next-step"></a><span data-ttu-id="eb0ef-248">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="eb0ef-248">Next step</span></span>
[<span data-ttu-id="eb0ef-249">Valider les étapes d’installation</span><span class="sxs-lookup"><span data-stu-id="eb0ef-249">Post installation steps</span></span>](../adapters-and-accelerators/post-installation-steps-for-biztalk-adapter-pack-2016.md)