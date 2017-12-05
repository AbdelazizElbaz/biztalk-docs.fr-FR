---
title: "Conditions préalables pour les activités de développement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54c91405-f9a4-4676-b5c5-fe90b3b51b45
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dbc79fd31e78581d98ecad34579958ff90f3b1e1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="prerequisites-for-the-development-activities"></a><span data-ttu-id="7af50-102">Conditions préalables pour les activités de développement</span><span class="sxs-lookup"><span data-stu-id="7af50-102">Prerequisites for the Development Activities</span></span>
<span data-ttu-id="7af50-103">Cette section décrit comment préparer votre environnement pour effectuer les étapes décrites dans les activités de développement qui sont incluses dans le cadre de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7af50-103">This section describes how to prepare your environment to complete the steps in the development activities that are included as part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="7af50-104">Terminer la configuration suivante avant de tenter d’une des procédures dans les activités de développement :</span><span class="sxs-lookup"><span data-stu-id="7af50-104">Complete the following setup before you attempt any of the procedures in the development activities:</span></span>  
  
## <a name="set-up-your-computer-to-perform-the-procedures-in-the-biztalk-esb-toolkit-development-activities"></a><span data-ttu-id="7af50-105">Configurer votre ordinateur pour effectuer les procédures décrites dans les activités de développement de BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="7af50-105">Set up your computer to perform the procedures in the BizTalk ESB Toolkit development activities</span></span>  
  
1.  <span data-ttu-id="7af50-106">Installer et déployer l’application d’exemple de feuille de route, l’exemple d’application de résolution dynamique et l’exemple d’application de plusieurs Services Web.</span><span class="sxs-lookup"><span data-stu-id="7af50-106">Install and deploy the Itinerary sample application, the Dynamic Resolution sample application, and the Multiple Web Services sample application.</span></span> <span data-ttu-id="7af50-107">Pour plus d’informations sur l’installation et le déploiement de ces applications, consultez [exemples d’Applications BizTalk ESB Toolkit](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).</span><span class="sxs-lookup"><span data-stu-id="7af50-107">For more information about installing and deploying these applications, see [BizTalk ESB Toolkit Sample Applications](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md).</span></span>  
  
2.  <span data-ttu-id="7af50-108">Exécutez l’utilitaire de serveur de publication UDDI.</span><span class="sxs-lookup"><span data-stu-id="7af50-108">Run the UDDI Publisher Utility.</span></span>  
  
3.  <span data-ttu-id="7af50-109">Sur votre ordinateur de développement, dans l’Explorateur Windows, créez les chemins d’accès suivants :</span><span class="sxs-lookup"><span data-stu-id="7af50-109">On your development computer, in Windows Explorer, create the following paths:</span></span>  
  
    -   <span data-ttu-id="7af50-110">C:\HowTos</span><span class="sxs-lookup"><span data-stu-id="7af50-110">C:\HowTos</span></span>  
  
    -   <span data-ttu-id="7af50-111">C:\HowTos\Itineraries</span><span class="sxs-lookup"><span data-stu-id="7af50-111">C:\HowTos\Itineraries</span></span>  
  
    -   <span data-ttu-id="7af50-112">C:\HowTos\DropFolder</span><span class="sxs-lookup"><span data-stu-id="7af50-112">C:\HowTos\DropFolder</span></span>  
  
    -   <span data-ttu-id="7af50-113">C:\HowTos\Out</span><span class="sxs-lookup"><span data-stu-id="7af50-113">C:\HowTos\Out</span></span>  
  
4.  <span data-ttu-id="7af50-114">Assurez-vous que votre compte de service BizTalk Server a **contrôle total** des autorisations pour la structure de répertoires C:\HowTos.</span><span class="sxs-lookup"><span data-stu-id="7af50-114">Ensure that your BizTalk Server service account has **Full Control** permissions to the C:\HowTos directory structure.</span></span>  
  
5.  <span data-ttu-id="7af50-115">Assurez-vous que votre compte de service Microsoft BizTalk Server a **écrire** autorisations pour C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out.</span><span class="sxs-lookup"><span data-stu-id="7af50-115">Ensure that your Microsoft BizTalk Server service account has **Write** permissions to C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out.</span></span>  
  
6.  <span data-ttu-id="7af50-116">Dans le dossier C:\HowTos, copiez le message de test suivant :</span><span class="sxs-lookup"><span data-stu-id="7af50-116">Copy the following test message to the C:\HowTos folder:</span></span>  
  
    -   <span data-ttu-id="7af50-117">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.Xml</span><span class="sxs-lookup"><span data-stu-id="7af50-117">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Test\Data\NAOrderDoc.xml</span></span>  
  
7.  <span data-ttu-id="7af50-118">Dans le dossier C:\HowTos, créez un raccourci vers l’application Client de Test d’itinéraire, à l’emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="7af50-118">In the C:\HowTos folder, create a shortcut to the Itinerary Test Client application, found at the following location:</span></span>  
  
    -   <span data-ttu-id="7af50-119">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB. Itinerary.Test\bin\Debug\ESB. Itinerary.Test.exe</span><span class="sxs-lookup"><span data-stu-id="7af50-119">C:\Projects\Microsoft.Practices.ESB\Source\Samples\Itinerary\Source\ESB.Itinerary.Test\bin\Debug\ESB.Itinerary.Test.exe</span></span>  
  
## <a name="create-the-visual-studio-solution"></a><span data-ttu-id="7af50-120">Créer la solution Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7af50-120">Create the Visual Studio solution</span></span>  
  
1.  <span data-ttu-id="7af50-121">Dans Visual Studio, dans le menu fichier, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="7af50-121">In Visual Studio, on the File menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="7af50-122">Dans le **nouveau projet** boîte de dialogue, dans le volet types de projet, cliquez sur **Visual C#**, puis cliquez sur **bibliothèque de classes** dans le volet Modèles.</span><span class="sxs-lookup"><span data-stu-id="7af50-122">In the **New Project** dialog box, in the Project types pane, click **Visual C#**, and then click **Class Library** in the Templates pane.</span></span>  
  
3.  <span data-ttu-id="7af50-123">Dans le **nom** , tapez **ItineraryLibrary**.</span><span class="sxs-lookup"><span data-stu-id="7af50-123">In the **Name** box, type **ItineraryLibrary**.</span></span>  
  
4.  <span data-ttu-id="7af50-124">Dans le **emplacement** , tapez **C:\HowTos**.</span><span class="sxs-lookup"><span data-stu-id="7af50-124">In the **Location** box, type **C:\HowTos**.</span></span>  
  
5.  <span data-ttu-id="7af50-125">Sélectionnez le **créer le répertoire pour la solution** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="7af50-125">Select the **Create directory for solution** check box.</span></span>  
  
6.  <span data-ttu-id="7af50-126">Dans le **nom de la Solution** , tapez **modèles**, puis cliquez sur **OK** pour créer la solution.</span><span class="sxs-lookup"><span data-stu-id="7af50-126">In the **Solution Name** box, type **Patterns**, and then click **OK** to create the solution.</span></span>  
  
7.  <span data-ttu-id="7af50-127">Supprimer le **Class1.cs** de fichiers à partir de la **ItineraryLibrary** projet.</span><span class="sxs-lookup"><span data-stu-id="7af50-127">Delete the **Class1.cs** file from the **ItineraryLibrary** project.</span></span>