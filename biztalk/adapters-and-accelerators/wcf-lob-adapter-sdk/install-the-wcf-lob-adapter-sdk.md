---
title: "Installer le Kit de développement logiciel de l’adaptateur LOB WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41b9b34b-3fbb-480f-a335-a218eab33693
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e9d4dfe5818e28e1ccd73b077c19c9d45ecb8cc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="install-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="60dc7-102">Installer le Kit de développement logiciel de l’adaptateur LOB WCF</span><span class="sxs-lookup"><span data-stu-id="60dc7-102">Install the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="60dc7-103">Installer et configurer le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60dc7-103">Install and configure the [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)].</span></span> 
  
## <a name="requirements"></a><span data-ttu-id="60dc7-104">Spécifications</span><span class="sxs-lookup"><span data-stu-id="60dc7-104">Requirements</span></span> 
<span data-ttu-id="60dc7-105">Installer les composants sur le système sur lequel vous installez la suite la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60dc7-105">Install following components on the system where you install the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> 

> [!NOTE]
> <span data-ttu-id="60dc7-106">**Pour obtenir la liste des versions prises en charge**, consultez :</span><span class="sxs-lookup"><span data-stu-id="60dc7-106">**For a list of the supported versions**, see:</span></span> 
> 
> [<span data-ttu-id="60dc7-107">Configurations logicielle et matérielle pour BizTalk Server 2016</span><span class="sxs-lookup"><span data-stu-id="60dc7-107">Hardware and Software Requirements for BizTalk Server 2016</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2016.md)  
> [<span data-ttu-id="60dc7-108">Configuration matérielle et logicielle requise pour BizTalk Server 2013 et 2013 R2</span><span class="sxs-lookup"><span data-stu-id="60dc7-108">Hardware and Software Requirements for BizTalk Server 2013 and 2013 R2</span></span>](../../install-and-config-guides/hardware-and-software-requirements-for-biztalk-server-2013-and-2013-r2.md)
 
 | | | 
 | --- | --- |
 | <span data-ttu-id="60dc7-109">Windows</span><span class="sxs-lookup"><span data-stu-id="60dc7-109">Windows</span></span> | <span data-ttu-id="60dc7-110">x86 ou x64</span><span class="sxs-lookup"><span data-stu-id="60dc7-110">x86 or x64</span></span> <br/><br/><span data-ttu-id="60dc7-111">Les ressources du système d’exploitation requises sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="60dc7-111">Required OS resources include:</span></span><br/> <ul><li><span data-ttu-id="60dc7-112">Microsoft Distributed Transaction Coordinator (MSDTC) : Requis pour prendre en charge les transactions OleTx</span><span class="sxs-lookup"><span data-stu-id="60dc7-112">Microsoft Distributed Transaction Coordinator (MSDTC) : Required to support OleTx transactions</span></span></li><li><span data-ttu-id="60dc7-113">Message Queuing (MSMQ) : Requis pour prendre en charge la messagerie fiable</span><span class="sxs-lookup"><span data-stu-id="60dc7-113">Message Queuing (MSMQ) : Required to support reliable messaging</span></span></li><li><span data-ttu-id="60dc7-114">Internet Information Services (IIS) : Requis si vous souhaitez héberger votre application dans IIS</span><span class="sxs-lookup"><span data-stu-id="60dc7-114">Internet Information Services (IIS) : Required if you want to host your application in IIS</span></span></li><li><span data-ttu-id="60dc7-115">Windows Process Activation Service (WAS) : Requis si vous souhaitez héberger votre application dans WAS</span><span class="sxs-lookup"><span data-stu-id="60dc7-115">Windows Process Activation Service (WAS) : Required if you want to host your application in WAS</span></span></li></ul> |
 |<span data-ttu-id="60dc7-116">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="60dc7-116">Windows Communication Foundation</span></span>| | 
 | [!INCLUDE[btsDotNetFramework_md](../../includes/btsdotnetframework-md.md)] | | 
 | [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] | <span data-ttu-id="60dc7-117">Requis si vous générez des adaptateurs personnalisés ou développer des solutions qui utilisent les adaptateurs générée à l’aide du [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60dc7-117">Required if you are building custom adapters, or developing solutions that use the adapters built with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)].</span></span> |
| [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] | <span data-ttu-id="60dc7-118">Requis si vous utilisez les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="60dc7-118">Required if you use the adapters with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  |


  
## <a name="install"></a><span data-ttu-id="60dc7-119">Install</span><span class="sxs-lookup"><span data-stu-id="60dc7-119">Install</span></span>

> [!IMPORTANT]
> * <span data-ttu-id="60dc7-120">Fermez toutes les instances de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="60dc7-120">Close all instances of Visual Studio</span></span>
> * <span data-ttu-id="60dc7-121">Pour effectuer un **terminé** le programme d’installation, vérifiez que BizTalk Server est installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60dc7-121">To do a **Complete** setup, confirm that BizTalk Server is installed on the computer.</span></span>  
  
1.  <span data-ttu-id="60dc7-122">Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="60dc7-122">Run the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] **Setup.exe** as Administrator.</span></span>
  
2.  <span data-ttu-id="60dc7-123">Sélectionnez **installer des adaptateurs Microsoft BizTalk**, puis sélectionnez **installer Microsoft WCF LOB Adapter SDK**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-123">Select **Install Microsoft BizTalk Adapters**, and then select **Install Microsoft WCF LOB Adapter SDK**.</span></span>  
  
3.  <span data-ttu-id="60dc7-124">Sur le **Bienvenue** écran, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-124">On the **Welcome** screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="60dc7-125">Acceptez le contrat de licence et sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-125">Accept the license agreement, and select **Next**.</span></span>  
  
5.  <span data-ttu-id="60dc7-126">Dans **choisir le Type de programme d’installation**, sélectionnez le type d’installation :</span><span class="sxs-lookup"><span data-stu-id="60dc7-126">In **Choose Setup Type**, select the type of installation:</span></span>  
  
    -   <span data-ttu-id="60dc7-127">Pour installer les outils et le moment de l’exécution courantes, sélectionnez **standard**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-127">To install the common run time and tools, select **Typical**.</span></span>  
  
    -   <span data-ttu-id="60dc7-128">Pour sélectionner les fonctionnalités que vous souhaitez installer et l’emplacement d’installation, sélectionnez **personnalisé**, puis sélectionnez les fonctionnalités que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="60dc7-128">To select the features that you want to install and the installation location, select **Custom**, and then select the features you want to install.</span></span>  
  
    -   <span data-ttu-id="60dc7-129">Pour installer toutes les fonctionnalités, sélectionnez **Complete**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-129">To install all the features, select **Complete**.</span></span>  
  
6.  <span data-ttu-id="60dc7-130">Sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-130">Select **Install**.</span></span>  
  
## <a name="update-or-remove"></a><span data-ttu-id="60dc7-131">Mise à jour ou supprimer</span><span class="sxs-lookup"><span data-stu-id="60dc7-131">Update or remove</span></span>
  
1.  <span data-ttu-id="60dc7-132">Ouvrez **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-132">Open **Programs and Feature**.</span></span> 
  
2.  <span data-ttu-id="60dc7-133">Dans la liste, sélectionnez **Windows Communication Foundation LOB Adapter SDK**, puis sélectionnez **modification**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-133">In the list, select **Windows Communication Foundation LOB Adapter SDK**, and then select **Change**.</span></span>  
  
3.  <span data-ttu-id="60dc7-134">Sur le **Bienvenue** écran, sélectionnez **suivant**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-134">On the **Welcome** screen, select **Next**.</span></span>  
  
4.  <span data-ttu-id="60dc7-135">Procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="60dc7-135">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="60dc7-136">Pour sélectionner les composants que vous souhaitez installer, sélectionnez **modification**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-136">To select the components that you want to install, select **Change**.</span></span>  
  
    -   <span data-ttu-id="60dc7-137">Pour réparer les erreurs dans l’installation la plus récente, sélectionnez **réparer**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-137">To repair errors in the most recent installation, select **Repair**.</span></span>  
  
    -   <span data-ttu-id="60dc7-138">Pour supprimer la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] à partir de l’ordinateur, sélectionnez **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-138">To remove the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] from the computer, select **Remove**.</span></span>  
  
5.  <span data-ttu-id="60dc7-139">Si vous choisissez de modifier l’installation :</span><span class="sxs-lookup"><span data-stu-id="60dc7-139">If you choose to modify the installation:</span></span>  
  
    1.  <span data-ttu-id="60dc7-140">Sélectionnez **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-140">Select **Next**.</span></span>  
  
    2.  <span data-ttu-id="60dc7-141">Sélectionnez **modification**, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-141">Select **Change**, and then select **Finish**.</span></span>  
  
6.  <span data-ttu-id="60dc7-142">Si vous choisissez de réparer l’installation, dans le **prêt à réparer WCF LOB Adapter SDK** boîte de dialogue, sélectionnez **réparer**, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-142">If you choose to repair the installation, in the **Ready to repair WCF LOB Adapter SDK** dialog box, select **Repair**, and then select **Finish**.</span></span>  
  
7.  <span data-ttu-id="60dc7-143">Si vous choisissez de supprimer les adaptateurs, dans le **prêt à supprimer WCF LOB Adapter SDK** boîte de dialogue, sélectionnez **supprimer**, puis sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-143">If you choose to remove the adapters, in the **Ready to remove WCF LOB Adapter SDK** dialog box, select **Remove**, and then select **Finish**.</span></span>  
  
  
#### <a name="remove-custom-adapters-after-uninstalling-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="60dc7-144">Supprimer les cartes personnalisées après la désinstallation de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="60dc7-144">Remove custom adapters after uninstalling the WCF LOB Adapter SDK</span></span>  

 <span data-ttu-id="60dc7-145">Si vous avez développé des adaptateurs personnalisés à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]et que vous avez enregistré ces adaptateurs sur votre ordinateur, vous devez également effectuer la procédure suivante.</span><span class="sxs-lookup"><span data-stu-id="60dc7-145">If you have developed any custom adapters using the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], and you have registered these adapters on your computer, you must also complete the following procedure.</span></span>  
  
1.  <span data-ttu-id="60dc7-146">Supprimer l’adaptateur personnalisé dans le global assembly cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="60dc7-146">Remove the custom adapter from the global assembly cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="60dc7-147">Ouvrir un **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-147">Open a **Visual Studio command prompt**.</span></span>  
  
    2.  <span data-ttu-id="60dc7-148">Supprimer personnalisé **.dll de l’adaptateur** à partir du GAC avec **commande gacutil /u**.</span><span class="sxs-lookup"><span data-stu-id="60dc7-148">Remove the custom **adapter .dll** from the GAC using **command gacutil /u**.</span></span>  
  
2.  <span data-ttu-id="60dc7-149">Supprimez les références à la liaison de l’adaptateur personnalisé à partir de machine.config</span><span class="sxs-lookup"><span data-stu-id="60dc7-149">Remove the references to the custom adapter binding from machine.config</span></span>  
  
    1.  <span data-ttu-id="60dc7-150">Accédez au fichier machine.config sous \< *lecteur système*\>: \WINDOWS\Microsoft.NET\Framework\\< version\>\CONFIG.</span><span class="sxs-lookup"><span data-stu-id="60dc7-150">Go to the machine.config file under \<*system drive*\>:\WINDOWS\Microsoft.NET\Framework\\<version\>\CONFIG.</span></span>  
  
    2.  <span data-ttu-id="60dc7-151">Ouvrez le fichier à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="60dc7-151">Open the file by using a text editor.</span></span>  
  
    3.  <span data-ttu-id="60dc7-152">Recherche de l’élément bindingExtensions client et bindingElementExtensions sous system.serviceModel\extensions.</span><span class="sxs-lookup"><span data-stu-id="60dc7-152">Search for the element bindingExtensions, client and bindingElementExtensions under system.serviceModel\extensions.</span></span>  
  
    4.  <span data-ttu-id="60dc7-153">Supprimez la liaison WCF qui se rapporte à votre adaptateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="60dc7-153">Remove the WCF binding that pertains to your custom adapter.</span></span>  
  
## <a name="do-a-silent-installation"></a><span data-ttu-id="60dc7-154">Effectuez une installation sans assistance</span><span class="sxs-lookup"><span data-stu-id="60dc7-154">Do a silent installation</span></span>  
 <span data-ttu-id="60dc7-155">Une installation sans assistance est idéale pour les scénarios de test ou dans le cadre d’un déploiement d’entreprise à grande échelle.</span><span class="sxs-lookup"><span data-stu-id="60dc7-155">A silent installation is ideal for test scenarios or as part of a large-scale enterprise deployment.</span></span> [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]<span data-ttu-id="60dc7-156">Fournit des paramètres de ligne de commande que vous pouvez utiliser avec AdapterFramework.msi pour effectuer une installation sans assistance.</span><span class="sxs-lookup"><span data-stu-id="60dc7-156"> provides command line parameters that you can use with AdapterFramework.msi to perform a silent installation.</span></span>  
 
> [!NOTE]
>  <span data-ttu-id="60dc7-157">Pour effectuer une installation sans assistance, vous devez être un administrateur sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="60dc7-157">To perform silent installation, you should be an Administrator on the computer.</span></span> 

  
1.  <span data-ttu-id="60dc7-158">Ouvrez une invite de commandes comme administrateur.</span><span class="sxs-lookup"><span data-stu-id="60dc7-158">Open a command prompt as administrator.</span></span>  
  
2.  <span data-ttu-id="60dc7-159">Tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="60dc7-159">Type the following:</span></span>
  
    ```  
    AdapterFramework.msi /quiet MUOPTIN=”Yes”  
    ```  
  
    <span data-ttu-id="60dc7-160">Utilisez les options de ligne de commande suivantes conjointement avec AdapterFramework.msi :</span><span class="sxs-lookup"><span data-stu-id="60dc7-160">Use the following command line options in conjunction with AdapterFramework.msi:</span></span>  
  
    * <span data-ttu-id="60dc7-161">Utilisez `/quiet` pour installer [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] en mode silencieux.</span><span class="sxs-lookup"><span data-stu-id="60dc7-161">Use `/quiet` to install [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] silently.</span></span>  
  
    * <span data-ttu-id="60dc7-162">Utilisez MUOPTIN = « Yes » &#124; » Non » pour indiquer si le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] doit rechercher des mises à jour avec Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="60dc7-162">Use MUOPTIN=”Yes”&#124;”No” to indicate if the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] should check for updates with Microsoft Update.</span></span>  
    
        <span data-ttu-id="60dc7-163">Lorsque la valeur Oui, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] vérifie les mises à jour via Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="60dc7-163">When set to Yes, [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] checks for updates through Microsoft Update.</span></span> <span data-ttu-id="60dc7-164">Lorsque la valeur non [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] ne vérifie pas les mises à jour avec Microsoft Update.</span><span class="sxs-lookup"><span data-stu-id="60dc7-164">When set to no [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] does not check for updates with Microsoft Update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60dc7-165">Pour afficher des options supplémentaires pour l’installation de ligne de commande, tapez `AdapterFramework.msi /?`à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="60dc7-165">To display additional options for command line installation, type `AdapterFramework.msi /?`at the command prompt.</span></span>  
  
