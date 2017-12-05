---
title: "À l’aide du suivi des adaptateurs BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- Adapter Trace Utility, running
- enabling, Adapter Trace Utility
ms.assetid: ddc6b2c7-9dee-43c1-950b-8fd580bfcb26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1e14234363ace4b953fa4766a97502753572e6f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-biztalk-adapter-tracing"></a><span data-ttu-id="ab6d3-102">Utilisation du suivi des adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="ab6d3-102">Using BizTalk Adapter Tracing</span></span>
<span data-ttu-id="ab6d3-103">Cette rubrique décrit la procédure d'installation de l'outil Trace Log (Journal de suivi) et d'activation du suivi des adaptateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-103">This topic describes how to install the Trace Log tool and how to enable BizTalk adapter tracing.</span></span>  
  
## <a name="install-the-trace-log-tool"></a><span data-ttu-id="ab6d3-104">Installation de l'outil Trace Log</span><span class="sxs-lookup"><span data-stu-id="ab6d3-104">Install the Trace Log Tool</span></span>  
  
#### <a name="to-install-the-trace-log-tool-tracelogexe"></a><span data-ttu-id="ab6d3-105">Pour installer l'outil de journal de suivi (tracelog.exe)</span><span class="sxs-lookup"><span data-stu-id="ab6d3-105">To install the Trace Log tool (tracelog.exe)</span></span>  
  
1.  <span data-ttu-id="ab6d3-106">Téléchargez l'outil Trace Log sur le site Web [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) (en anglais).</span><span class="sxs-lookup"><span data-stu-id="ab6d3-106">Download the Trace Log tool from the [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) Web site.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab6d3-107">Installez cette version (6.0) du Kit de développement logiciel même si vous exécutez [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab6d3-107">Install this version (6.0) of the SDK even if you are running [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span></span> <span data-ttu-id="ab6d3-108">Si vous installez le **Kit de développement logiciel Windows pour Windows Server 2008 et .NET Framework 3.5** version (v.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-108">If you install the **Windows SDK for Windows Server 2008 and .NET Framework 3.5** version (v.</span></span> <span data-ttu-id="ab6d3-109">6.1), l’outil Trace Log n’est pas installé.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-109">6.1), it will not install the Trace Log tool.</span></span>  
  
2.  <span data-ttu-id="ab6d3-110">Lancez le programme d'installation Web de la **mise à jour du Kit de développement logiciel Microsoft® Windows® pour Windows Vista** en cliquant, au bas de la page Web, sur le lien correspondant au fichier **PSDK-x86.exe** .</span><span class="sxs-lookup"><span data-stu-id="ab6d3-110">Start the **Microsoft® Windows® Software Development Kit Update for Windows Vista** Web installation program by clicking the link for the **PSDK-x86.exe** file at the bottom of the Web page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab6d3-111">Si vous utilisez une version 64 bits de Windows, téléchargez les fichiers adaptés à votre système.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-111">If you are using a 64-bit version of Windows choose the correct files to download for your system.</span></span>  
  
3.  <span data-ttu-id="ab6d3-112">Dans la boîte de dialogue **Sélectionner un type d'installation** , choisissez l'installation **personnalisée** , puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-112">In the **Select an Installation Type** dialog box, choose the option for a **Custom** installation, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="ab6d3-113">Acceptez l'emplacement d'installation par défaut, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-113">Accept the default installation location and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="ab6d3-114">Dans la boîte de dialogue **Installation personnalisée** , désactivez toutes les cases à cocher relatives aux composants disponibles.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-114">In the **Custom Installation** dialog box, click to clear all the available features.</span></span>  
  
6.  <span data-ttu-id="ab6d3-115">Développez le composant de **kit de développement SDK principal Microsoft Windows** , puis le composant **Outils** .</span><span class="sxs-lookup"><span data-stu-id="ab6d3-115">Expand the **Microsoft Windows Core SDK** feature, and then expand the **Tools** feature.</span></span>  
  
7.  <span data-ttu-id="ab6d3-116">Choisissez le composant **Outils (Intel 64 bits)** et cliquez sur **Installation sur le disque dur local**.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-116">Choose the **Tools (Intel 64-bit)** feature, and then click **Will be installed on local hard drive**.</span></span>  
  
8.  <span data-ttu-id="ab6d3-117">Cliquez sur **Suivant**, puis de nouveau sur **Suivant** pour démarrer l'installation.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-117">Click **Next**, and then click **Next** again to start the installation.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab6d3-118">Après l'installation de la **mise à jour du Kit de développement logiciel Microsoft® Windows® pour Windows Vista** , vous pouvez être invité à redémarrer selon les fonctionnalités que vous avez choisi d'installer en plus de l'outil Trace Log.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-118">After installing the **Microsoft® Windows® Software Development Kit Update for Windows Vista** you may be prompted to reboot depending upon what other features you chose to install along with the Trace Log tool.</span></span> <span data-ttu-id="ab6d3-119">En effet, certains composants de la **mise à jour du Kit de développement logiciel Microsoft® Windows® pour Windows Vista** ne fonctionneront pas correctement sans un redémarrage.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-119">This is because certain components of the **Microsoft® Windows® Software Development Kit Update for Windows Vista** will not function correctly until the reboot has been completed.</span></span> <span data-ttu-id="ab6d3-120">Vous pouvez utiliser l'outil Trace Log sans redémarrer.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-120">You do not need to reboot to use the Trace Log tool.</span></span>  
  
## <a name="enable-biztalk-adapter-tracing-with-tracecmd"></a><span data-ttu-id="ab6d3-121">Activation du suivi des adaptateurs BizTalk avec trace.cmd</span><span class="sxs-lookup"><span data-stu-id="ab6d3-121">Enable BizTalk Adapter Tracing with trace.cmd</span></span>  
  
#### <a name="to-enable-biztalk-adapter-tracing"></a><span data-ttu-id="ab6d3-122">Pour activer le suivi des adaptateurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="ab6d3-122">To enable BizTalk adapter tracing</span></span>  
  
1.  <span data-ttu-id="ab6d3-123">À l’invite de commandes, accédez au répertoire en cours le répertoire d’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-123">At a command prompt, change the current directory to the directory where BizTalk Server is installed.</span></span> <span data-ttu-id="ab6d3-124">Par défaut, BizTalk Server est installé dans le [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] active.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-124">By default, BizTalk Server is installed in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] directory.</span></span>  <span data-ttu-id="ab6d3-125">Si vous utilisez une version 64 bits de Windows et BizTalk Server, le chemin d’installation est [!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ab6d3-125">If using a 64-bit version of Windows and BizTalk Server, the installation path is [!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)].</span></span>  
  
2.  <span data-ttu-id="ab6d3-126">Tapez la commande suivante et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ab6d3-126">Type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="ab6d3-127">**trace - tools « Chemin d’accès de l’outil Trace Log »**</span><span class="sxs-lookup"><span data-stu-id="ab6d3-127">**trace -tools "Path of the Trace Log tool"**</span></span>  
  
     <span data-ttu-id="ab6d3-128">Par défaut, l'outil Trace Log (tracelog.exe) se trouve dans le répertoire **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** .</span><span class="sxs-lookup"><span data-stu-id="ab6d3-128">By default, the Trace Log tool (tracelog.exe) is located in the **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** directory.</span></span> <span data-ttu-id="ab6d3-129">Si vous utilisez une version 64 bits de Windows, il se trouve dans le répertoire **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-129">If using a 64-bit version of Windows the Trace Log tool is located at **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**.</span></span>  <span data-ttu-id="ab6d3-130">Vous devez indiquer le chemin d'accès à cet outil entre guillemets.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-130">You must enclose the path of the Trace Log tool in quotation marks.</span></span>  
  
     <span data-ttu-id="ab6d3-131">Par exemple, tapez la commande suivante et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ab6d3-131">For example, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="ab6d3-132">**trace - tools « C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin »**</span><span class="sxs-lookup"><span data-stu-id="ab6d3-132">**trace -tools "C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab6d3-133">Le commutateur **-tools** indique au fichier Trace.cmd l'emplacement du fichier Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-133">The **-tools** switch indicates to the Trace.cmd file the location of the Tracelog.exe file.</span></span>  
    >   
    >  <span data-ttu-id="ab6d3-134">Si la commande fonctionne, la sortie doit correspondre à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="ab6d3-134">If the command successfully runs, the output will be like below:</span></span>  
    >   
    >  <span data-ttu-id="ab6d3-135">**2.0 - gérer BizTalk 2006 version Bits le suivi de trace.**</span><span class="sxs-lookup"><span data-stu-id="ab6d3-135">**trace 2.0 - Manage BizTalk 2006 Release Bits Tracing.**</span></span>  
    >   
    >  <span data-ttu-id="ab6d3-136">**Paramètre TRACE_TOOL_SEARCH_PATH à « C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin »**</span><span class="sxs-lookup"><span data-stu-id="ab6d3-136">**Setting TRACE_TOOL_SEARCH_PATH to "C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin "**</span></span>  
  
## <a name="capture-trace-output-with-tracecmd"></a><span data-ttu-id="ab6d3-137">Capture de la sortie de traçage avec trace.cmd</span><span class="sxs-lookup"><span data-stu-id="ab6d3-137">Capture Trace output with trace.cmd</span></span>  
  
#### <a name="to-capture-trace-output"></a><span data-ttu-id="ab6d3-138">Pour capturer la sortie de traçage</span><span class="sxs-lookup"><span data-stu-id="ab6d3-138">To capture trace output</span></span>  
  
1.  <span data-ttu-id="ab6d3-139">À l’invite de commandes, accédez au répertoire en cours le répertoire d’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-139">At a command prompt, change the current directory to the directory where BizTalk Server is installed.</span></span>  
  
2.  <span data-ttu-id="ab6d3-140">Au niveau d'une invite de commande, tapez la commande ci-après, puis appuyez sur la touche ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ab6d3-140">At a command prompt, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="ab6d3-141">**trace - Démarrer**</span><span class="sxs-lookup"><span data-stu-id="ab6d3-141">**trace -start**</span></span>  
  
3.  <span data-ttu-id="ab6d3-142">Reproduisez le scénario dont vous voulez capturer la sortie de traçage.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-142">Reproduce the scenario for which you want to capture trace output.</span></span>  
  
4.  <span data-ttu-id="ab6d3-143">Au niveau d'une invite de commande, tapez la commande ci-après, puis appuyez sur la touche ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ab6d3-143">At a command prompt, type the following command, and then press ENTER:</span></span>  
  
     <span data-ttu-id="ab6d3-144">**trace - arrêter**</span><span class="sxs-lookup"><span data-stu-id="ab6d3-144">**trace -stop**</span></span>  
  
5.  <span data-ttu-id="ab6d3-145">Après l’arrêt de la trace, un fichier binaire nommé **Btstrace.bin** est généré dans le dossier dans lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-145">After you stop the trace, a binary file that is named **Btstrace.bin** is generated in the folder where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed.</span></span>  
  
6.  <span data-ttu-id="ab6d3-146">Envoyez le fichier **Btstrace.bin** pour analyse aux Services de support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ab6d3-146">Send the **Btstrace.bin** file to Microsoft Product Support Services for analysis.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6d3-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab6d3-147">See Also</span></span>  
 <span data-ttu-id="ab6d3-148">[À l’aide des adaptateurs](../core/using-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="ab6d3-148">[Using Adapters](../core/using-adapters.md) </span></span>  
 [<span data-ttu-id="ab6d3-149">Résolution des problèmes de l’adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="ab6d3-149">Troubleshooting the Windows SharePoint Services Adapter</span></span>](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)