---
title: Les Applications BizTalk ESB Toolkit exemple | Documents Microsoft
description: "Installer les exemples d’applications ESB Toolkit et obtenir des liens rapides sur la façon de les utiliser dans BizTalk Server"
caps.latest.revision: "5"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 188f8e1f-26fb-4ea6-8e2e-f2ae3e46ca20
ms.author: mandia
ms.openlocfilehash: f9d1af5c2bc8c16ec14f8e13109f0edfe13b86cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit-sample-applications"></a><span data-ttu-id="cd83e-103">BizTalk ESB Toolkit exemple Applications</span><span class="sxs-lookup"><span data-stu-id="cd83e-103">BizTalk ESB Toolkit Sample Applications</span></span>
<span data-ttu-id="cd83e-104">La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut plusieurs exemples d’applications que vous pouvez installer et exécuter pour voir comment des composants de pipeline de travaux ESB et comment il utilise certaines l’ESB.</span><span class="sxs-lookup"><span data-stu-id="cd83e-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several sample applications that you can install and run to see how the ESB works and how it uses some of the ESB pipeline components.</span></span> <span data-ttu-id="cd83e-105">Vous pouvez adapter et modifier le code et les techniques utilisées dans les exemples pour vos propres applications.</span><span class="sxs-lookup"><span data-stu-id="cd83e-105">You can adapt and modify the code and techniques used in the samples for your own applications.</span></span>  
  
## <a name="install-the-sample-applications"></a><span data-ttu-id="cd83e-106">Installer les exemples d’applications</span><span class="sxs-lookup"><span data-stu-id="cd83e-106">Install the sample applications</span></span>  
  
1.  <span data-ttu-id="cd83e-107">Créez un dossier nommé projets à la racine de votre lecteur C: et créez un sous-dossier nommé Microsoft.Practices.ESB dans ce dossier.</span><span class="sxs-lookup"><span data-stu-id="cd83e-107">Create a folder named Projects in the root of your C: drive, and create a subfolder named Microsoft.Practices.ESB within this folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cd83e-108">Dans la version actuelle, l’installation de prise en charge est pour les fichiers se trouvent dans le dossier C:\Projects\Microsoft.Practices.ESB.</span><span class="sxs-lookup"><span data-stu-id="cd83e-108">In the current release, the supported installation is for the files to reside in the folder C:\Projects\Microsoft.Practices.ESB.</span></span> <span data-ttu-id="cd83e-109">Les fichiers de liaison BizTalk qui sont fournis avec les exemples dépendent de ce chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="cd83e-109">The BizTalk binding files that ship with the samples depend on this path.</span></span>  
  
2.  <span data-ttu-id="cd83e-110">Lorsque vous installez le [ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md), il inclut un fichier .zip appelé ESBSource.zip dans l’emplacement d’installation que vous avez spécifié (par défaut, C:\Program Files\\[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="cd83e-110">When you install the [ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md), it includes a .zip file called ESBSource.zip in the installation location you specified (by default, C:\Program Files\\[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]).</span></span> <span data-ttu-id="cd83e-111">Décompressez le fichier ESBSource.zip dans le dossier C:\Projects\Microsoft.Practices.ESB.</span><span class="sxs-lookup"><span data-stu-id="cd83e-111">Uncompress the ESBSource.zip file into the C:\Projects\Microsoft.Practices.ESB folder.</span></span> <span data-ttu-id="cd83e-112">Cela crée des dossiers nommés **clés** et **Source** qui contiennent l’exemple de clé et les exemples de code source.</span><span class="sxs-lookup"><span data-stu-id="cd83e-112">This creates folders named **Keys** and **Source** that contain the sample key and the samples with source code.</span></span> <span data-ttu-id="cd83e-113">Le dossier Source contient le code source pour l’exemple d’application, et le dossier des clés contient les clés publiques utilisées pour signer les assemblys dans les exemples d’applications.</span><span class="sxs-lookup"><span data-stu-id="cd83e-113">The Source folder contains the source code for the sample application, and the Keys folder contains the public keys used to sign the assemblies in the sample applications.</span></span>  
  
3.  <span data-ttu-id="cd83e-114">Avant d’exécuter les exemples, supprimez l’attribut en lecture seule sur le dossier C:\Projects\Microsoft.Practices.ESB\ afin que les exemples sont installés correctement.</span><span class="sxs-lookup"><span data-stu-id="cd83e-114">Before you run the samples, remove the read-only attribute on the C:\Projects\Microsoft.Practices.ESB\ folder so that the samples install correctly.</span></span>  
  
4.  <span data-ttu-id="cd83e-115">Si vous n’avez pas utilisé avant de scripts PowerShell, vous devez ouvrir PowerShell en tant qu’administrateur et exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="cd83e-115">If you have not used PowerShell scripts before, you must open PowerShell as an Administrator and run the following command:</span></span>  
  
    ```  
    set-executionpolicy unrestricted  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="cd83e-116">Pour plus d’informations sur PowerShell, consultez le [Blog Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187593) ([http://go.microsoft.com/fwlink/? LinkId = 187593](http://go.microsoft.com/fwlink/?LinkId=187593)) et [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([http://go.microsoft.com/fwlink/? LinkId = 187594](http://go.microsoft.com/fwlink/?LinkId=187594)) sur MSDN.</span><span class="sxs-lookup"><span data-stu-id="cd83e-116">For more information about PowerShell, see the [Windows PowerShell Blog](http://go.microsoft.com/fwlink/?LinkId=187593) ([http://go.microsoft.com/fwlink/?LinkId=187593](http://go.microsoft.com/fwlink/?LinkId=187593)) and [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([http://go.microsoft.com/fwlink/?LinkId=187594](http://go.microsoft.com/fwlink/?LinkId=187594)) on MSDN.</span></span>  
  
5.  <span data-ttu-id="cd83e-117">Ouvrez une invite de commandes en tant qu’administrateur et exécutez la commande suivante pour vérifier les scriptmaps WCF sont enregistrés :</span><span class="sxs-lookup"><span data-stu-id="cd83e-117">Open a command prompt as an administrator and run the following command to ensure WCF script maps are registered:</span></span>  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v3.0\Windows Communication Foundation>ServiceModelReg.exe -r -y  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="cd83e-118">Vous devez ouvrir le fichier ESBSource.zip afin d’obtenir un accès à du code des exemples.</span><span class="sxs-lookup"><span data-stu-id="cd83e-118">You need to open the ESBSource.zip file in order to get an access to the Samples code.</span></span>  

## <a name="sample-applications"></a><span data-ttu-id="cd83e-119">Exemples d’applications</span><span class="sxs-lookup"><span data-stu-id="cd83e-119">Sample applications</span></span>  
 <span data-ttu-id="cd83e-120">Les rubriques suivantes décrivent les exemples d’applications et incluent des instructions d’installation supplémentaires, le cas échéant :</span><span class="sxs-lookup"><span data-stu-id="cd83e-120">The following topics describe the sample applications and include additional installation instructions where applicable:</span></span>  
  
-   [<span data-ttu-id="cd83e-121">Installation des exemples de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="cd83e-121">Installing the Exception Management Samples</span></span>](../esb-toolkit/installing-the-exception-management-samples.md)  
  
-   [<span data-ttu-id="cd83e-122">L’exemple de gestionnaire d’exceptions personnalisée réparation et soumettez à nouveau en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="cd83e-122">Running the Repair and Resubmit Custom Exception Handler Sample</span></span>](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)  
  
-   [<span data-ttu-id="cd83e-123">Le Message de persistance d’exemple de gestionnaire d’exceptions personnalisé en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="cd83e-123">Running the Message Persisting Custom Exception Handler Sample</span></span>](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)  
  
-   [<span data-ttu-id="cd83e-124">Échec de l’exemple de traitement ESB du routage de Message BizTalk en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="cd83e-124">Running the BizTalk Failed Message Routing ESB Processing Sample</span></span>](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)  
  
-   [<span data-ttu-id="cd83e-125">Installer et exécuter l’exemple de rampe d’entrée d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="cd83e-125">Installing and Running the Itinerary On-Ramp Sample</span></span>](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [<span data-ttu-id="cd83e-126">Installer et exécuter l’exemple de composant MQRFH2 JMS</span><span class="sxs-lookup"><span data-stu-id="cd83e-126">Installing and Running the JMS MQRFH2 Component Sample</span></span>](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)  
  
-   [<span data-ttu-id="cd83e-127">Installer et exécuter l’exemple de composant de Namespace</span><span class="sxs-lookup"><span data-stu-id="cd83e-127">Installing and Running the Namespace Component Sample</span></span>](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)  
  
-   [<span data-ttu-id="cd83e-128">Installer et exécuter l’exemple de Service de Transformation</span><span class="sxs-lookup"><span data-stu-id="cd83e-128">Installing and Running the Transformation Service Sample</span></span>](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)  
  
-   [<span data-ttu-id="cd83e-129">Installer et exécuter l’exemple de résolution dynamique</span><span class="sxs-lookup"><span data-stu-id="cd83e-129">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="cd83e-130">Installer et exécuter l’exemple d’opérations BizTalk</span><span class="sxs-lookup"><span data-stu-id="cd83e-130">Installing and Running the BizTalk Operations Sample</span></span>](../esb-toolkit/installing-and-running-the-biztalk-operations-sample.md)  
  
-   [<span data-ttu-id="cd83e-131">Installer et exécuter l’exemple de Service de programme de résolution</span><span class="sxs-lookup"><span data-stu-id="cd83e-131">Installing and Running the Resolver Service Sample</span></span>](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)  
  
-   [<span data-ttu-id="cd83e-132">Installer et exécuter l’exemple de ventilation-regroupement</span><span class="sxs-lookup"><span data-stu-id="cd83e-132">Installing and Running the Scatter-Gather Sample</span></span>](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)  
  
-   [<span data-ttu-id="cd83e-133">Installer et exécuter l’exemple d’enrichissement de Message</span><span class="sxs-lookup"><span data-stu-id="cd83e-133">Installing and Running the Message Enrichment Sample</span></span>](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md)  
  
-   [<span data-ttu-id="cd83e-134">Installer et exécuter l’exemple de Services Web multiples</span><span class="sxs-lookup"><span data-stu-id="cd83e-134">Installing and Running the Multiple Web Services Sample</span></span>](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)  
  
-   [<span data-ttu-id="cd83e-135">Installer et exécuter l’exemple de l’extensibilité du Concepteur</span><span class="sxs-lookup"><span data-stu-id="cd83e-135">Installing and Running the Designer Extensibility Sample</span></span>](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)  
  
-   [<span data-ttu-id="cd83e-136">Exemple de Service de gestion des exceptions en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="cd83e-136">Running the Exception Handling Service Sample</span></span>](../esb-toolkit/running-the-exception-handling-service-sample.md)