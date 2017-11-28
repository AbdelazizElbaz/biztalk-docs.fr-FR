---
title: ExpenseReportSubmission | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
ms.assetid: d0bacab3-7092-44b8-a1c6-6f574a2db8bd
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 993d1874a95da2501636f941f1436fec894e87f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="expensereportsubmission"></a><span data-ttu-id="87d90-102">ExpenseReportSubmission</span><span class="sxs-lookup"><span data-stu-id="87d90-102">ExpenseReportSubmission</span></span>
<span data-ttu-id="87d90-103">L'exemple ExpenseReportSubmission montre comment soumettre un document à une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une application client riche comme Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="87d90-103">The ExpenseReportSubmission sample demonstrates how to submit a document to a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration from a rich client such as Microsoft Excel.</span></span>  
  
 <span data-ttu-id="87d90-104">Les applications client riche vous permettent d'effectuer un certain nombre d'actions, telles que des validations et des calculs préliminaires, sur le client.</span><span class="sxs-lookup"><span data-stu-id="87d90-104">Rich clients enable you to perform a number of actions, such as data validation and preliminary calculations, on the client.</span></span> <span data-ttu-id="87d90-105">Cela contribue à réduire au minimum les interactions avec le serveur principal, ce qui peut être utile lorsque seules des connections à faible bande passante sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="87d90-105">This helps to minimize interactions with the back-end server, which can be useful when only low bandwidth connections are available.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="87d90-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="87d90-106">Prerequisites</span></span>  
 <span data-ttu-id="87d90-107">Vous devez vous assurer que votre environnement de développement est configuré et activé pour fonctionner avec les services Web [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87d90-107">You must ensure that your development environment is configured and enabled to work with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web services.</span></span> <span data-ttu-id="87d90-108">Pour plus d’informations, consultez [activation des Services Web](../core/enabling-web-services.md).</span><span class="sxs-lookup"><span data-stu-id="87d90-108">For more information, see [Enabling Web Services](../core/enabling-web-services.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="87d90-109">Fonctions de l'exemple</span><span class="sxs-lookup"><span data-stu-id="87d90-109">What This Sample Does</span></span>  
 <span data-ttu-id="87d90-110">Cet exemple montre comment vous pouvez soumettre une note de frais à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directement à partir d'Excel, en respectant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d90-110">This sample shows how you can submit an expense report to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directly from Excel, using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="87d90-111">L'utilisateur effectue les étapes manuelles de l'exemple fournies dans le tableur Excel.</span><span class="sxs-lookup"><span data-stu-id="87d90-111">The user performs the manual sample steps provided in the Excel spreadsheet.</span></span>  
  
2.  <span data-ttu-id="87d90-112">Le code macro du tableur convertit les données de tableur au format Extensible Markup Language (XML), et soumet le message XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en utilisant une connection HTTP.</span><span class="sxs-lookup"><span data-stu-id="87d90-112">Macro code in the spreadsheet converts the spreadsheet data to Extensible Markup Language (XML) format, and submits the XML message to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] using an HTTP connection.</span></span>  
  
3.  <span data-ttu-id="87d90-113">L'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère le message XML de note de frais, valide son format en utilisant le schéma fourni, puis le range dans un dossier différent.</span><span class="sxs-lookup"><span data-stu-id="87d90-113">The computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] retrieves the XML expense report message, validates its format using the provided schema, and then drops it into a different folder.</span></span>  
  
4.  <span data-ttu-id="87d90-114">En pratique, au delà de cet exemple, une autre application, comme un système planification des ressources de l'entreprise (ERP), récupère ensuite le fichier de tableur pour un traitement ultérieur.</span><span class="sxs-lookup"><span data-stu-id="87d90-114">In practice, beyond the scope of this sample, another application such as an Enterprise Resource Planning (ERP) system would then retrieve the spreadsheet file for further processing.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="87d90-115">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="87d90-115">Where to Find This Sample</span></span>  
 <span data-ttu-id="87d90-116">\<*Exemples de chemin d’accès*> \AdaptersUsage\ExpenseReportSubmission\\</span><span class="sxs-lookup"><span data-stu-id="87d90-116">\<*Samples Path*>\AdaptersUsage\ExpenseReportSubmission\\</span></span>  
  
 <span data-ttu-id="87d90-117">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="87d90-117">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="87d90-118">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="87d90-118">File(s)</span></span>|<span data-ttu-id="87d90-119"> Description</span><span class="sxs-lookup"><span data-stu-id="87d90-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87d90-120">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="87d90-120">Cleanup.bat</span></span>|<span data-ttu-id="87d90-121">Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.</span><span class="sxs-lookup"><span data-stu-id="87d90-121">Undeploys assemblies and removes them from the global assembly cache (GAC); removes send and receive ports; removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="87d90-122">ExpenseReport.15.3.xls</span><span class="sxs-lookup"><span data-stu-id="87d90-122">ExpenseReport.15.3.xls</span></span>|<span data-ttu-id="87d90-123">Tableur Excel avec la mise en page de la note de frais, les macros associées, et des boutons pour appeler les macros.</span><span class="sxs-lookup"><span data-stu-id="87d90-123">Excel spreadsheet with the expense report layout, associated macros, and buttons to invoke the macros.</span></span>|  
|<span data-ttu-id="87d90-124">MessageExample.xml</span><span class="sxs-lookup"><span data-stu-id="87d90-124">MessageExample.xml</span></span>|<span data-ttu-id="87d90-125">Exemple de note de frais au format XML.</span><span class="sxs-lookup"><span data-stu-id="87d90-125">Example of the XML expense report format.</span></span>|  
|<span data-ttu-id="87d90-126">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="87d90-126">Setup.bat</span></span>|<span data-ttu-id="87d90-127">Crée et initialise l'exemple.</span><span class="sxs-lookup"><span data-stu-id="87d90-127">Builds and initializes this sample.</span></span>|  
|<span data-ttu-id="87d90-128">Dans le dossier \BTSExpenseDemo :</span><span class="sxs-lookup"><span data-stu-id="87d90-128">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="87d90-129">AssemblyInfo.cs,</span><span class="sxs-lookup"><span data-stu-id="87d90-129">AssemblyInfo.cs,</span></span><br /><br /> <span data-ttu-id="87d90-130">BTSExpenseDemo.btproj,</span><span class="sxs-lookup"><span data-stu-id="87d90-130">BTSExpenseDemo.btproj,</span></span><br /><br /> <span data-ttu-id="87d90-131">BTSExpenseDemo.sln</span><span class="sxs-lookup"><span data-stu-id="87d90-131">BTSExpenseDemo.sln</span></span>|<span data-ttu-id="87d90-132">Fournit un projet, une solution, et des fichiers associés pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="87d90-132">Provides project, solution, and related files for this sample.</span></span>|  
|<span data-ttu-id="87d90-133">Dans le dossier \BTSExpenseDemo :</span><span class="sxs-lookup"><span data-stu-id="87d90-133">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="87d90-134">BTSExpenseDemoBinding.xml</span><span class="sxs-lookup"><span data-stu-id="87d90-134">BTSExpenseDemoBinding.xml</span></span>|<span data-ttu-id="87d90-135">Utilisé pour une installation automatique, comme une liaison de port.</span><span class="sxs-lookup"><span data-stu-id="87d90-135">Used for automated setup, such as port binding.</span></span>|  
|<span data-ttu-id="87d90-136">Dans le dossier \BTSExpenseDemo :</span><span class="sxs-lookup"><span data-stu-id="87d90-136">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="87d90-137">BTSExpenseOrchestration.odx</span><span class="sxs-lookup"><span data-stu-id="87d90-137">BTSExpenseOrchestration.odx</span></span>|<span data-ttu-id="87d90-138">Fournit une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="87d90-138">Provides a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration for this sample.</span></span>|  
|<span data-ttu-id="87d90-139">Dans le dossier \BTSExpenseDemo :</span><span class="sxs-lookup"><span data-stu-id="87d90-139">In the \BTSExpenseDemo folder:</span></span><br /><br /> <span data-ttu-id="87d90-140">SchemaExpenseReport.xsd</span><span class="sxs-lookup"><span data-stu-id="87d90-140">SchemaExpenseReport.xsd</span></span>|<span data-ttu-id="87d90-141">Fournit un schéma pour la note de frais au format XML.</span><span class="sxs-lookup"><span data-stu-id="87d90-141">Provides a schema for the XML expense report format.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="87d90-142">Pour créer et initialiser l'exemple</span><span class="sxs-lookup"><span data-stu-id="87d90-142">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="87d90-143">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="87d90-143">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="87d90-144">\<*Exemples de chemin d’accès*> \AdaptersUsage\ExpenseReportSubmission</span><span class="sxs-lookup"><span data-stu-id="87d90-144">\<*Samples Path*>\AdaptersUsage\ExpenseReportSubmission</span></span>  
  
2.  <span data-ttu-id="87d90-145">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d90-145">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="87d90-146">Compile le projet Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, et déploie l'assembly résultant.</span><span class="sxs-lookup"><span data-stu-id="87d90-146">Compiles the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project for this sample, and deploys the resulting assembly.</span></span>  
  
    -   <span data-ttu-id="87d90-147">Crée et lie les ports d'envoi et de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87d90-147">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] send and receive ports.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="87d90-148">Cet exemple affiche les avertissements suivants lors de la création et de la liaison des ports :</span><span class="sxs-lookup"><span data-stu-id="87d90-148">This sample displays the following warnings when creating and binding the ports:</span></span>  
        >   
        >  `Warning: Receive handler not specified for receive location "BTSExpenseReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  <span data-ttu-id="87d90-149">`Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`.</span><span class="sxs-lookup"><span data-stu-id="87d90-149">`Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`.</span></span>  
        >   
        >  <span data-ttu-id="87d90-150">Vous pouvez ignorer ces avertissements sans problème.</span><span class="sxs-lookup"><span data-stu-id="87d90-150">You can safely ignore these warnings.</span></span> <span data-ttu-id="87d90-151">(Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)</span><span class="sxs-lookup"><span data-stu-id="87d90-151">(To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)</span></span>  
  
    -   <span data-ttu-id="87d90-152">Active l'emplacement de réception, et démarre le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="87d90-152">Enables the receive location, and starts the send port.</span></span>  
  
    -   <span data-ttu-id="87d90-153">Configure IIS.</span><span class="sxs-lookup"><span data-stu-id="87d90-153">Configures IIS.</span></span>  
  
    -   <span data-ttu-id="87d90-154">Lie et démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="87d90-154">Binds and starts the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration.</span></span>  
  
    -   <span data-ttu-id="87d90-155">Définit l'adresse HTTP à l'emplacement prévu par le tableur Excel.</span><span class="sxs-lookup"><span data-stu-id="87d90-155">Sets the HTTP address to the location expected by the Excel spreadsheet.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87d90-156">Pour plus d’informations sur le filtre ISAPI de BizTalk, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="87d90-156">For more information about the BizTalk ISAPI filter, see [How to Configure IIS for an HTTP Receive Location](../core/how-to-configure-iis-for-an-http-receive-location.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87d90-157">Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.</span><span class="sxs-lookup"><span data-stu-id="87d90-157">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87d90-158">Si vous choisissez d'ouvrir et de créer le projet dans cet exemple sans exécuter le fichier Setup.bat, vous devez d'abord créer une paire de clés de nom fort en utilisant l'utilitaire .NET Framework Strong Name Utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="87d90-158">If you choose to open and build the project in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="87d90-159">Utilisez cette paire de clés pour signer l'assembly obtenu.</span><span class="sxs-lookup"><span data-stu-id="87d90-159">Use this key pair to sign the resulting assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87d90-160">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="87d90-160">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="87d90-161">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="87d90-161">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
3.  <span data-ttu-id="87d90-162">Le fichier setup.bat configure le répertoire virtuel pour que cet exemple soit exécuté dans le pool d'applications IIS associé au site Web par défaut.</span><span class="sxs-lookup"><span data-stu-id="87d90-162">The setup.bat file configures the virtual directory for this sample to run in the IIS application pool associated with the default web site.</span></span>  <span data-ttu-id="87d90-163">Pour configurer le répertoire virtuel pour cet exemple soit exécuté sous le contexte d’un utilisateur dans le **utilisateurs d’hôtes BizTalk isolés** et **IIS_WPG** groupes d’utilisateurs, vous devez configurer le répertoire virtuel pour s’exécuter dans un nouveau Pool d’applications IIS.</span><span class="sxs-lookup"><span data-stu-id="87d90-163">To configure the virtual directory for this sample to run under the context of a user in the **BizTalk Isolated Host Users** and **IIS_WPG** user groups, you should configure the virtual directory to run in a new IIS application pool.</span></span>  <span data-ttu-id="87d90-164">Configurez le répertoire virtuel à exécuter dans un nouveau pool d’applications IIS en effectuant les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="87d90-164">Configure the virtual directory to run in a new IIS application pool by completing the following steps:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="87d90-165">Si vous avez déjà créé un nouveau pool d'applications pour un autre exemple SDK, alors vous pouvez passer au dernier élément ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="87d90-165">If you have already created a new application pool for another SDK sample then you can proceed to the last bullet item below.</span></span>  
  
    1.  <span data-ttu-id="87d90-166">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="87d90-166">Click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    2.  <span data-ttu-id="87d90-167">Dans le **Gestionnaire des Services Internet (IIS)**, accédez à la **Pools d’applications** dossier.</span><span class="sxs-lookup"><span data-stu-id="87d90-167">In the **Internet Information Services (IIS) Manager**, navigate to the **Application Pools** folder.</span></span>  
  
    3.  <span data-ttu-id="87d90-168">Cliquez sur le **Pools d’applications** dossier puis cliquez sur **nouveau**, **Pool d’applications...**</span><span class="sxs-lookup"><span data-stu-id="87d90-168">Right-click the **Application Pools** folder and click **New**, **Application Pool...**</span></span>  
  
    4.  <span data-ttu-id="87d90-169">Entrez un nom pour le **ID du Pool d’applications :** tel que BizTalkSDKSamples, vérifiez que le **utiliser les paramètres par défaut pour le nouveau pool d’applications** option est sélectionnée, puis cliquez sur **OK** à créer le pool d’applications.</span><span class="sxs-lookup"><span data-stu-id="87d90-169">Enter a name for the **Application Pool ID:** such as BizTalkSDKSamples, verify that the **Use default settings for new application pool** option is selected and click **OK** to create the new application pool.</span></span>  
  
    5.  <span data-ttu-id="87d90-170">Cliquez sur le pool d’applications, puis sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="87d90-170">Right-click the new application pool and then click **Properties**.</span></span>  
  
    6.  <span data-ttu-id="87d90-171">Cliquez sur le **identité** onglet de la boîte de dialogue Propriétés zone et de modifier l’identité sous laquelle ce pool d’applications s’exécute à un utilisateur qui est membre de la **utilisateurs d’hôtes BizTalk isolés** groupe d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="87d90-171">Click the **Identity** tab of the properties dialog box and change the identity under which this application pool runs to a user that is a member of the **BizTalk Isolated Host Users** user group.</span></span>  <span data-ttu-id="87d90-172">Cet utilisateur doit également être un membre de la variable locale **IIS_WPG** groupe d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="87d90-172">This user should also be a member of the local **IIS_WPG** user group.</span></span>  
  
    7.  <span data-ttu-id="87d90-173">Configurez le répertoire virtuel pour que cet exemple de Kit de développement logiciel soit exécuté sous le nouveau pool d'applications.</span><span class="sxs-lookup"><span data-stu-id="87d90-173">Configure the virtual directory for this SDK sample to run under the new application pool.</span></span> <span data-ttu-id="87d90-174">Le **pool d’applications :** paramètre n’est disponible sur le **répertoire virtuel** onglet de la boîte de dialogue Propriétés du répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="87d90-174">The **Application pool:** setting is available on the **Virtual Directory** tab of the Virtual Directory properties dialog box.</span></span> <span data-ttu-id="87d90-175">Le répertoire virtuel créé pour cet exemple est **ExpenseReportSubmission**.</span><span class="sxs-lookup"><span data-stu-id="87d90-175">The virtual directory created for this sample is **ExpenseReportSubmission**.</span></span>  
  
4.  <span data-ttu-id="87d90-176">Ajout d'une extension de service web aux IIS pour HTTPReceive.dll</span><span class="sxs-lookup"><span data-stu-id="87d90-176">Add a web service extension to IIS for HTTPReceive.dll</span></span>  
  
    1.  <span data-ttu-id="87d90-177">Dans le **Gestionnaire des Services Internet (IIS)**, accédez à la **Extensions du Service Web** dossier.</span><span class="sxs-lookup"><span data-stu-id="87d90-177">In the **Internet Information Services (IIS) Manager**, navigate to the **Web Service Extensions** folder.</span></span>  
  
    2.  <span data-ttu-id="87d90-178">Avec le bouton droit le **Extensions du Service Web** et sélectionnez **ajouter une nouvelle extension de service Web** pour afficher les **nouvelle Extension de Service Web** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="87d90-178">Right-click the **Web Service Extensions** folder and select **Add a new Web service extension** to display the **New Web Service Extension** dialog box.</span></span>  
  
    3.  <span data-ttu-id="87d90-179">Entrez **ExpenseReportSubmission** pour **nom d’Extension :**</span><span class="sxs-lookup"><span data-stu-id="87d90-179">Enter **ExpenseReportSubmission** for **Extension name:**</span></span>  
  
    4.  <span data-ttu-id="87d90-180">Cliquez sur **ajouter** pour afficher les **ajouter le fichier** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="87d90-180">Click **Add** to display the **Add file** dialog box.</span></span>  
  
    5.  <span data-ttu-id="87d90-181">Cliquez sur **Parcourir** pour afficher les **ouvrir** boîte de dialogue zone et accédez à  *\<dossier d’Installation de BizTalk Server >*\HttpReceive\BTSHTTPReceive.dll et Cliquez sur **ouvrir**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87d90-181">Click **Browse** to display the **Open** dialog box and navigate to *\<BizTalk Server Installation folder>*\HttpReceive\BTSHTTPReceive.dll and click **Open**, then click **OK**.</span></span>  
  
    6.  <span data-ttu-id="87d90-182">Activer l’option pour **définir l’état de l’extension à autorisée** et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="87d90-182">Enable the option to **Set extension status to Allowed** and click **OK**.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="87d90-183">Cet exemple en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="87d90-183">Running This Sample</span></span>  
 <span data-ttu-id="87d90-184">Utilisez la procédure suivante pour exécuter l'exemple ExpenseReportSubmission.</span><span class="sxs-lookup"><span data-stu-id="87d90-184">Use the following procedure to run the ExpenseReportSubmission sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87d90-185">Si vous utilisez les composants de sécurité avancée de Microsoft Excel, les macros du tableur peuvent être désactivées.</span><span class="sxs-lookup"><span data-stu-id="87d90-185">If you are using the enhanced security features of Microsoft Excel, the macros in the spreadsheet may be disabled.</span></span> <span data-ttu-id="87d90-186">Suivez les instructions fournies par Excel sur la manière d'exécuter des macros non-signées provenant d'une source approuvée.</span><span class="sxs-lookup"><span data-stu-id="87d90-186">Follow the instructions provided by Excel about how to run unsigned macros from a trusted source.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="87d90-187">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="87d90-187">To run this sample</span></span>  
  
1.  <span data-ttu-id="87d90-188">Ouvrez le fichier Excel ExpenseReport.15.3.xls inclus dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="87d90-188">Open the Excel file ExpenseReport.15.3.xls included with this sample.</span></span>  
  
2.  <span data-ttu-id="87d90-189">Eventuellement, modifiez les données d'exemple dans le tableur sans changer son format.</span><span class="sxs-lookup"><span data-stu-id="87d90-189">Optionally, change the sample data in the spreadsheet without changing its format.</span></span>  
  
3.  <span data-ttu-id="87d90-190">Dans la feuille de calcul, cliquez sur **Démarrer** pour effectuer des calculs locaux.</span><span class="sxs-lookup"><span data-stu-id="87d90-190">In the spreadsheet, click **Start** to perform local calculations.</span></span>  
  
     <span data-ttu-id="87d90-191">Le texte du bouton passe de **Démarrer** à **Submit**.</span><span class="sxs-lookup"><span data-stu-id="87d90-191">The text of the button changes from **Start** to **Submit**.</span></span>  
  
4.  <span data-ttu-id="87d90-192">Dans la feuille de calcul, cliquez sur **Submit**.</span><span class="sxs-lookup"><span data-stu-id="87d90-192">In the spreadsheet, click **Submit**.</span></span>  
  
5.  <span data-ttu-id="87d90-193">Observez le texte du message soumis, le résultat au-dessus du tableau avec l'arrière-plan jaune (cellule C7), ainsi que le code de retour et la description de texte en dessous et à droite (cellule G23).</span><span class="sxs-lookup"><span data-stu-id="87d90-193">Observe the text of the submitted message, the result above the table with yellow background (cell C7), and the actual return code and text description below and to the right (cell G23).</span></span>  
  
     <span data-ttu-id="87d90-194">Si la soumission échoue, essayez à nouveau.</span><span class="sxs-lookup"><span data-stu-id="87d90-194">If submission fails, try again.</span></span> <span data-ttu-id="87d90-195">Consultez également le tableau de résolution des problèmes dans la section Commentaires.</span><span class="sxs-lookup"><span data-stu-id="87d90-195">Also, refer to the troubleshooting table in the Comments section.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="87d90-196">Commentaires</span><span class="sxs-lookup"><span data-stu-id="87d90-196">Comments</span></span>  
 <span data-ttu-id="87d90-197">Des scénarios comme celui-ci peuvent se produire lorsqu'une force de vente sur le terrain est par exemple équipée de versions plus anciennes de Microsoft Windows, qui ne supportent pas le .NET Framework, et pour lesquelles une mise à jour vers une version plus récente de Windows ne serait pas une option viable.</span><span class="sxs-lookup"><span data-stu-id="87d90-197">Scenarios such as this can occur when, for example, a field sales force is equipped with older versions of Microsoft Windows that do not support the .NET Framework, and for which the requirement to upgrade to a more current version of Windows is not a viable option.</span></span>  
  
 <span data-ttu-id="87d90-198">Les principaux composants présentés dans cet exemple sont :</span><span class="sxs-lookup"><span data-stu-id="87d90-198">Essential features demonstrated in this sample are:</span></span>  
  
-   <span data-ttu-id="87d90-199">Soumission à partir d'une application client riche (non basée sur .NET)</span><span class="sxs-lookup"><span data-stu-id="87d90-199">Submission from a rich client (not .NET-based)</span></span>  
  
-   <span data-ttu-id="87d90-200">Intégration de Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="87d90-200">Microsoft Office integration</span></span>  
  
-   <span data-ttu-id="87d90-201">Connections de réception HTTP</span><span class="sxs-lookup"><span data-stu-id="87d90-201">HTTP receive connections</span></span>  
  
-   <span data-ttu-id="87d90-202">Orchestration simple</span><span class="sxs-lookup"><span data-stu-id="87d90-202">Simple orchestration</span></span>  
  
-   <span data-ttu-id="87d90-203">Adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="87d90-203">File adapter</span></span>  
  
 <span data-ttu-id="87d90-204">Le tableau suivant montre les éventuelles erreurs de soumission et leurs solutions.</span><span class="sxs-lookup"><span data-stu-id="87d90-204">The following table shows some possible submission errors and their solutions.</span></span>  
  
|<span data-ttu-id="87d90-205">Code d'erreur HTTP</span><span class="sxs-lookup"><span data-stu-id="87d90-205">HTTP error code</span></span>|<span data-ttu-id="87d90-206">Action possible</span><span class="sxs-lookup"><span data-stu-id="87d90-206">Possible action</span></span>|  
|---------------------|---------------------|  
|<span data-ttu-id="87d90-207">401 Non autorisé</span><span class="sxs-lookup"><span data-stu-id="87d90-207">401 Unauthorized</span></span>|<span data-ttu-id="87d90-208">Activez l'accès anonyme sur le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="87d90-208">Enable anonymous access on the virtual directory.</span></span>|  
|<span data-ttu-id="87d90-209">503 Service non disponible, et la plupart des autres codes HTTP dans les plages 400 et 500</span><span class="sxs-lookup"><span data-stu-id="87d90-209">503 Service Unavailable, and most other HTTP codes in the 400 and 500 ranges</span></span>|<span data-ttu-id="87d90-210">Assurez-vous que l'hôte est en cours d'exécution et que le service est déployé, relié au bon port, et démarré.</span><span class="sxs-lookup"><span data-stu-id="87d90-210">Ensure that the host runs and that the service is deployed, bound to the correct port, and started.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87d90-211">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87d90-211">See Also</span></span>  
 [<span data-ttu-id="87d90-212">Exemples d’adaptateurs - utilisation</span><span class="sxs-lookup"><span data-stu-id="87d90-212">Adapter Samples - Usage</span></span>](../core/adapter-samples-usage.md)