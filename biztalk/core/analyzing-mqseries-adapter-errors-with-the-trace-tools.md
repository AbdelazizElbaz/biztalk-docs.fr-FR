---
title: "Analyse des erreurs de l’adaptateur MQSeries avec les outils de Trace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, about Adapter Trace Utility
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- errors, MQSeries adapters
- MQSeries adapters, Adapter Trace Utility
- Adapter Trace Utility, running
- MQSeries adapters, errors
- Adapter Trace Utility
ms.assetid: fdc73d99-3b73-491d-9b2f-7064364fefa7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8880197e58f6a499cc63e8b6ec89f67af9f0086
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="analyzing-mqseries-adapter-errors-with-the-trace-tools"></a><span data-ttu-id="c4271-102">Analyse des erreurs de l’adaptateur MQSeries avec les outils de Trace</span><span class="sxs-lookup"><span data-stu-id="c4271-102">Analyzing MQSeries Adapter Errors with the Trace Tools</span></span>
<span data-ttu-id="c4271-103">Les outils de suivi permettent d'analyser les échecs relatifs à la messagerie lors de l'exécution d'une application.</span><span class="sxs-lookup"><span data-stu-id="c4271-103">You use the trace tools to analyze messaging failures when you run your application.</span></span> <span data-ttu-id="c4271-104">Avec l'adaptateur MQSeries, vous devez utiliser deux outils : trace.cmd pour l'adaptateur et l'application BizTalk application, et MQSTrace.cmd pour MQSAgent.</span><span class="sxs-lookup"><span data-stu-id="c4271-104">With the MQSeries adapter you must use two tools, one for the adapter and your BizTalk application (trace.cmd), and the other for the MQSAgent (MQSTrace.cmd).</span></span> <span data-ttu-id="c4271-105">Les deux outils utilisent tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="c4271-105">Both tools use tracelog.exe.</span></span> <span data-ttu-id="c4271-106">Vous devez installer tracelog.exe si vous ne l’avez pas déjà.</span><span class="sxs-lookup"><span data-stu-id="c4271-106">You have to install tracelog.exe if you do not already have it.</span></span>  
  
 <span data-ttu-id="c4271-107">Trace.cmd et MQSTrace.cmd, vous devez définir une option (**-outils**) afin que ces outils peuvent trouver le fichier tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="c4271-107">With both trace.cmd and MQSTrace.cmd you have to set an option (**-tools**) so that these tools can find the tracelog.exe file.</span></span>  
  
## <a name="install-the-trace-utility"></a><span data-ttu-id="c4271-108">Installation de l'utilitaire de suivi</span><span class="sxs-lookup"><span data-stu-id="c4271-108">Install the Trace Utility</span></span>  
 <span data-ttu-id="c4271-109">Pour installer l'utilitaire de suivi de l'adaptateur BizTalk, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4271-109">To install the BizTalk Adapter Trace Utility, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c4271-110">Pour télécharger le fichier Tracelog.exe, visitez le site Web de téléchargement Microsoft Platform SDK à [http://go.microsoft.com/fwlink/?LinkId=21975](http://go.microsoft.com/fwlink/?LinkId=21975).</span><span class="sxs-lookup"><span data-stu-id="c4271-110">To download the Tracelog.exe file, visit the Microsoft Platform SDK download Web site at [http://go.microsoft.com/fwlink/?LinkId=21975](http://go.microsoft.com/fwlink/?LinkId=21975).</span></span>  
  
2.  <span data-ttu-id="c4271-111">Démarrer le programme d’installation Web du Kit de développement logiciel Platform en cliquant sur le lien pour le **PSDK-x86.exe** fichier au bas de la page Web.</span><span class="sxs-lookup"><span data-stu-id="c4271-111">Start the Platform SDK Web installation program by clicking the link for the **PSDK-x86.exe** file at the bottom of the Web page.</span></span>  
  
3.  <span data-ttu-id="c4271-112">Lorsque vous y êtes invité, choisissez de procéder à une installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c4271-112">When you are prompted, choose the option for a custom installation.</span></span>  
  
4.  <span data-ttu-id="c4271-113">Dans la boîte de dialogue **Installation personnalisée** , désactivez toutes les cases à cocher relatives aux composants disponibles.</span><span class="sxs-lookup"><span data-stu-id="c4271-113">In the **Custom Installation** dialog box, click to clear all the available features.</span></span>  
  
5.  <span data-ttu-id="c4271-114">Développez le composant de **kit de développement SDK principal Microsoft Windows** , puis le composant **Outils** .</span><span class="sxs-lookup"><span data-stu-id="c4271-114">Expand the **Microsoft Windows Core SDK** feature, and then expand the **Tools** feature.</span></span>  
  
6.  <span data-ttu-id="c4271-115">Choisissez le composant **Outils (Intel 64 bits)** et cliquez sur **Installation sur le disque dur local**.</span><span class="sxs-lookup"><span data-stu-id="c4271-115">Choose the **Tools (Intel 64-bit)** feature, and then click **Will be installed on local hard drive**.</span></span>  
  
7.  <span data-ttu-id="c4271-116">Cliquez sur **Suivant**, puis de nouveau sur **Suivant** pour démarrer l'installation.</span><span class="sxs-lookup"><span data-stu-id="c4271-116">Click **Next**, and then click **Next** again to start the installation.</span></span>  
  
8.  <span data-ttu-id="c4271-117">Recherchez le *lecteur*:\\*MicrosoftPlatformSDKInstallationFolder\bin* dossier, puis copiez le fichier Tracelog.exe dans le dossier d’installation de Microsoft BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c4271-117">Locate the *drive*:\\*MicrosoftPlatformSDKInstallationFolder\bin* folder, and then copy the Tracelog.exe file to the Microsoft BizTalk Server installation folder.</span></span> <span data-ttu-id="c4271-118">qui inclut également le fichier Trace.cmd.</span><span class="sxs-lookup"><span data-stu-id="c4271-118">The BizTalk Server installation folder also contains the Trace.cmd file.</span></span>  
  
## <a name="enable-the-trace-utility"></a><span data-ttu-id="c4271-119">Activation de l'utilitaire de suivi</span><span class="sxs-lookup"><span data-stu-id="c4271-119">Enable the Trace Utility</span></span>  
 <span data-ttu-id="c4271-120">Pour activer l'utilitaire de suivi de l'adaptateur BizTalk dans BizTalk Server, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4271-120">To enable the BizTalk Adapter Trace Utility in BizTalk Server, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c4271-121">Déplacer vers le répertoire contenant trace.cmd.</span><span class="sxs-lookup"><span data-stu-id="c4271-121">Move to the directory that contains trace.cmd.</span></span> <span data-ttu-id="c4271-122">L’emplacement par défaut est Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] active.</span><span class="sxs-lookup"><span data-stu-id="c4271-122">The default location is the Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] directory.</span></span>  
  
2.  <span data-ttu-id="c4271-123">Tapez la commande suivante, en remplaçant le répertoire contenant le fichier tracelog.exe sur votre ordinateur par le répertoire entre guillemets, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="c4271-123">Type the following command, substituting the directory that contains the tracelog.exe file on your computer for the directory in quotes, and then press ENTER:</span></span>  
  
     <span data-ttu-id="c4271-124">**trace - tools « c:\Program Files\Microsoft SDK\Bin »**</span><span class="sxs-lookup"><span data-stu-id="c4271-124">**trace -tools "c:\Program Files\Microsoft SDK\Bin"**</span></span>  
  
3.  <span data-ttu-id="c4271-125">Accédez au répertoire contenant MQSTrace.cmd.</span><span class="sxs-lookup"><span data-stu-id="c4271-125">Move to the directory that contains MQSTrace.cmd.</span></span>  
  
4.  <span data-ttu-id="c4271-126">Tapez la commande suivante, en remplaçant le répertoire contenant le fichier tracelog.exe sur votre ordinateur par le répertoire entre guillemets, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="c4271-126">Type the following command, substituting the directory that contains the tracelog.exe file on your computer for the directory in quotes, and then press ENTER:</span></span>  
  
     <span data-ttu-id="c4271-127">**MQSTrace-« c:\Program Files\Microsoft SDK\Bin » des outils**</span><span class="sxs-lookup"><span data-stu-id="c4271-127">**MQSTrace -tools "c:\Program Files\Microsoft SDK\Bin"**</span></span>  
  
## <a name="run-the-trace-utility"></a><span data-ttu-id="c4271-128">Exécution de l'utilitaire de suivi</span><span class="sxs-lookup"><span data-stu-id="c4271-128">Run the Trace Utility</span></span>  
 <span data-ttu-id="c4271-129">Pour exécuter l'utilitaire de suivi de l'adaptateur BizTalk, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4271-129">To run the BizTalk Adapter Trace Utility, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c4271-130">À l’invite de commandes, tapez **trace.cmd-start - high**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c4271-130">At the command prompt, type **trace.cmd -start -high**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="c4271-131">Exécutez le scénario d'échec.</span><span class="sxs-lookup"><span data-stu-id="c4271-131">Run your failure scenario.</span></span>  
  
3.  <span data-ttu-id="c4271-132">À l’invite de commandes, tapez **trace.cmd-stop**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c4271-132">At the command prompt, type **trace.cmd -stop**, and then press ENTER.</span></span>  
  
4.  <span data-ttu-id="c4271-133">Le fichier bts2006.bin contient la sortie de l'outil de suivi.</span><span class="sxs-lookup"><span data-stu-id="c4271-133">The bts2006.bin file contains the output of the trace tool.</span></span> <span data-ttu-id="c4271-134">Contactez les Services de support technique Microsoft à des fins d'analyse.</span><span class="sxs-lookup"><span data-stu-id="c4271-134">Contact Microsoft Product Support Services for analysis.</span></span> <span data-ttu-id="c4271-135">Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).</span><span class="sxs-lookup"><span data-stu-id="c4271-135">For more information, see [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).</span></span>  
  
 <span data-ttu-id="c4271-136">Pour exécuter l'utilitaire de suivi MQSAgent, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c4271-136">To run the MQSAgent Trace Utility, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c4271-137">À l’invite de commandes, tapez **MQSTrace.cmd-start - high**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="c4271-137">At the command prompt, type **MQSTrace.cmd -start -high**, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="c4271-138">Exécutez le scénario d'échec.</span><span class="sxs-lookup"><span data-stu-id="c4271-138">Run your failure scenario.</span></span>  
  
3.  <span data-ttu-id="c4271-139">À l’invite de commandes, tapez **MQSTrace.cmd-stop**.</span><span class="sxs-lookup"><span data-stu-id="c4271-139">At the command prompt, type **MQSTrace.cmd -stop**.</span></span>  
  
4.  <span data-ttu-id="c4271-140">Le fichier MQSAdapterTrace.bin contient la sortie de l'outil de suivi.</span><span class="sxs-lookup"><span data-stu-id="c4271-140">The MQSAdapterTrace.bin file contains the output of the trace tool.</span></span> <span data-ttu-id="c4271-141">Contactez les Services de support technique Microsoft à des fins d'analyse.</span><span class="sxs-lookup"><span data-stu-id="c4271-141">Contact Microsoft Product Support Services for analysis.</span></span> <span data-ttu-id="c4271-142">Pour plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).</span><span class="sxs-lookup"><span data-stu-id="c4271-142">For more information see [http://go.microsoft.com/fwlink/?LinkId=41645](http://go.microsoft.com/fwlink/?LinkId=41645).</span></span>