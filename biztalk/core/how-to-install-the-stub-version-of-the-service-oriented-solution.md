---
title: "Comment installer la Version Stub du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IIS, installing virtual directories [service solutions]
- service solution tutorial, IIS virtual directories
- service solution tutorial, stub version
- deploying, BAM solutions [service solutions]
- service solution tutorial, solutions [BAM]
- service solution tutorial, service solutions
- SSO, configuring
- IBM WebSphere MQ Client
- service solution tutorial, IBM WebSphere MQ Client
- installing, tutorials
- service solutions, deploying
- service solution tutorial, SSO
- BAM, deploying solutions
- service solution tutorial, building solutions
- service solution tutorial, installing
ms.assetid: 45de7681-4df0-47a4-a02c-509140423a1e
caps.latest.revision: "53"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c000c733097bffa58f652801b459c429df149e56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-stub-version-of-the-service-oriented-solution"></a><span data-ttu-id="ba3ba-102">Installation de la version stub du service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="ba3ba-102">How to Install the Stub Version of the Service Oriented Solution</span></span>
<span data-ttu-id="ba3ba-103">La procédure suivante décrit la préparation de votre ordinateur avant l'installation de la version stub de la solution orientée services, puis l'installation de la solution sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-103">The following steps describe how to prepare your computer before you install the stub version of the service oriented solution, and then how to install the solution on your computer.</span></span>  
  
-   [<span data-ttu-id="ba3ba-104">Préparer l’ordinateur pour l’installation de la version stub de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-104">Prepare the computer for installing the stub version of the Service Oriented Solution</span></span>](#step1)  
  
-   [<span data-ttu-id="ba3ba-105">Installer le Client IBM WebSphere MQ pour Windows</span><span class="sxs-lookup"><span data-stu-id="ba3ba-105">Install the IBM WebSphere MQ Client for Windows</span></span>](#step3)  
  
-   [<span data-ttu-id="ba3ba-106">Créer les répertoires virtuels dans IIS pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-106">Create the virtual directories in IIS for the Service Oriented Solution</span></span>](#step5)  
  
-   [<span data-ttu-id="ba3ba-107">Générez la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-107">Build the Service Oriented Solution</span></span>](#step7)  
  
-   [<span data-ttu-id="ba3ba-108">Créer les entrées de Enterprise Single Sign-On (SSO) et les valeurs dans la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="ba3ba-108">Create the Enterprise Single Sign-On (SSO) entries and values in the SSO database</span></span>](#step9)  
  
-   [<span data-ttu-id="ba3ba-109">Déployer la définition BAM pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-109">Deploy the BAM definition for the Service Oriented Solution</span></span>](#step11)  
  
-   [<span data-ttu-id="ba3ba-110">Déployer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-110">Deploy the Service Oriented Solution</span></span>](#step13)  
  
##  <span data-ttu-id="ba3ba-111"><a name="step1"></a>Préparer l’ordinateur pour l’installation de la version stub de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-111"><a name="step1"></a> Prepare the computer for installing the stub version of the Service Oriented Solution</span></span>  
  
#### <a name="to-prepare-the-computer-for-installing-the-stub-version-of-the-service-oriented-solution"></a><span data-ttu-id="ba3ba-112">Pour préparer l'ordinateur pour l'installation de la version stub de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-112">To prepare the computer for installing the stub version of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="ba3ba-113">Assurez-vous que le **Site Web par défaut** est configuré pour utiliser ASP.NET 2.X.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-113">Make sure that the **Default Web Site** is configured to use ASP.NET 2.X.</span></span>  
  
    1.  <span data-ttu-id="ba3ba-114">Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-114">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-115">Dans le **Gestionnaire des Services Internet (IIS)**, le nom de l’ordinateur, développez **Sites**, développez **Site Web par défaut**, développez **aspnet_client**, développez **system_web**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-115">In the **Internet Information Services (IIS) Manager**, the machine name, expand  **Sites**, expand **Default Web Site**, expand **aspnet_client**, expand **system_web**.</span></span>  
  
    3.  <span data-ttu-id="ba3ba-116">Vérifiez que le sous-dossier est 2.X.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-116">Make sure that the sub-folder is 2.X.</span></span>  
  
2.  <span data-ttu-id="ba3ba-117">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Services**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-117">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**.</span></span> <span data-ttu-id="ba3ba-118">À l’aide de la **Services** de la console, assurez-vous que les services suivants sont en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-118">Using the **Services** console, make sure that the following services are running:</span></span>  
  
    -   <span data-ttu-id="ba3ba-119">**Publication du World Wide Web**</span><span class="sxs-lookup"><span data-stu-id="ba3ba-119">**World Wide Web Publishing**</span></span>  
  
3.  <span data-ttu-id="ba3ba-120">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-120">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
4.  <span data-ttu-id="ba3ba-121">Si vous avez installé Windows SharePoint Services, excluez la (racine) de la **Site Web par défaut** à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes** , pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-121">If you installed Windows SharePoint Services, exclude the (root) of the **Default Web Site** from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="ba3ba-122">Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-122">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-123">Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-123">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="ba3ba-124">Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-124">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="ba3ba-125">Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-125">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="ba3ba-126">Ouvrez une invite de commandes, puis exécutez IISReset.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-126">At a command prompt, perform an IISReset.</span></span>  
  
5.  <span data-ttu-id="ba3ba-127">Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-127">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
6.  <span data-ttu-id="ba3ba-128">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir l'environnement %BTSSolutionsPath%.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-128">Open a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment.</span></span> <span data-ttu-id="ba3ba-129">Fermez ensuite l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-129">Then, exit the command prompt.</span></span>  
  
    -   <span data-ttu-id="ba3ba-130">setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span><span class="sxs-lookup"><span data-stu-id="ba3ba-130">setx BTSSolutionsPath "[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ba3ba-131">Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-131">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ba3ba-132">Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span><span class="sxs-lookup"><span data-stu-id="ba3ba-132">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
##  <span data-ttu-id="ba3ba-133"><a name="step3"></a>Installer le Client IBM WebSphere MQ pour Windows</span><span class="sxs-lookup"><span data-stu-id="ba3ba-133"><a name="step3"></a> Install the IBM WebSphere MQ Client for Windows</span></span>  
  
#### <a name="to-install-the-ibm-websphere-mq-client-for-windows"></a><span data-ttu-id="ba3ba-134">Pour installer le client IBM WebSphere MQ pour Windows</span><span class="sxs-lookup"><span data-stu-id="ba3ba-134">To install the IBM WebSphere MQ Client for Windows</span></span>  
  
1.  <span data-ttu-id="ba3ba-135">Téléchargez la dernière version du client IBM WebSphere MQ pour Windows.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-135">Download the latest version of IBM WebSphere MQ Client for Windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-136">Même si la version stub de la solution ne requiert pas IBM WebSphere Server, l'application cliente référence le fichier amqmdnet.dll fourni par le client IBM WebSphere MQ pour Windows, de sorte que vous devez installer ce dernier.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-136">Even if the stub version of the solution doesn't require IBM WebSphere Server, the client application references the amqmdnet.dll file provided by IBM WebSphere MQ Client for Windows, so you must install it.</span></span> <span data-ttu-id="ba3ba-137">Le client de la version stub n'appelle pas réellement une API dans la DLL.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-137">The client of the stub version does not actually call an API in the DLL.</span></span> <span data-ttu-id="ba3ba-138">Il n'est requis que pour la compilation et l'exécution de l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-138">It is required only for compiling and running the client application.</span></span> <span data-ttu-id="ba3ba-139">Vous pouvez télécharger le client IBM WebSphere MQ pour Windows depuis le site Web d'IBM.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-139">You can download IBM WebSphere MQ Client for Windows from the IBM Web site.</span></span>  
  
2.  <span data-ttu-id="ba3ba-140">Installez le client IBM WebSphere MQ pour Windows</span><span class="sxs-lookup"><span data-stu-id="ba3ba-140">Install IBM WebSphere MQ Client for Windows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-141">Il n'est pas utile de configurer le client IBM WebSphere MQ pour Windows.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-141">You don't need to configure IBM WebSphere MQ Client for Windows.</span></span> <span data-ttu-id="ba3ba-142">Conservez les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-142">Keep all of the default settings.</span></span>  
  
3.  <span data-ttu-id="ba3ba-143">Ajoutez les classes WebSphere MQ pour l'assembly .NET au Global Assembly Cache (GAC).</span><span class="sxs-lookup"><span data-stu-id="ba3ba-143">Add WebSphere MQ classes for the .NET assembly to the global assembly cache (GAC).</span></span>  
  
    1.  <span data-ttu-id="ba3ba-144">À la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire \<répertoire d’Installation IBM MQSeries > \bin.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-144">At the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command prompt, navigate to the directory \<IBM MQSeries Installation Directory>\bin.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-145">Exécutez la commande suivante (vérifiez que gacutil.exe est inclus dans l'environnement PATH) :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-145">Run the following command (make sure gacutil.exe is in the path environment):</span></span>  
  
         `gacutil.exe /i amqmdnet.dll`  
  
##  <span data-ttu-id="ba3ba-146"><a name="step5"></a>Créer les répertoires virtuels dans IIS pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-146"><a name="step5"></a> Create the virtual directories in IIS for the Service Oriented Solution</span></span>  
  
#### <a name="to-create-the-virtual-directories-in-iis-for-the-service-oriented-solution"></a><span data-ttu-id="ba3ba-147">Pour créer les répertoires virtuels dans IIS pour la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-147">To create the virtual directories in IIS for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="ba3ba-148">Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **ajouter un Pool d’applications**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-148">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **Add Application Pool**.</span></span>  
  
     <span data-ttu-id="ba3ba-149">Sur le **ajouter un Pool d’applications** boîte de dialogue, tapez `SSOStubAppPool` dans les **nom** zone de texte, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-149">On the **Add Application Pool** dialog box, type `SSOStubAppPool` in the **Name** text box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ba3ba-150">Les répertoires virtuels utilisés par la solution orientée services incluent le service Web publié pour la version stub des orchestrations, le service Web SAP stub, le service Web Payment Tracker stub et le service Web Pending Transaction stub.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-150">The virtual directories that service-oriented solution uses include the published Web service for the stub version of orchestrations, the stub SAP Web service, the stub Payment Tracker Web service, and the stub Pending Transaction Web service.</span></span>  
  
2.  <span data-ttu-id="ba3ba-151">Dans le **Gestionnaire des Services Internet (IIS)**, cliquez sur le pool d’applications que vous venez de créée, puis cliquez sur **paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-151">In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then click **Advanced Settings**.</span></span>  
  
3.  <span data-ttu-id="ba3ba-152">Cliquez dans la colonne à droite de la **identité** propriété, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-152">Click in the column to the right of the **Identity** property, and then click the ellipsis (**…**) button.</span></span>  
  
4.  <span data-ttu-id="ba3ba-153">Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez le **compte personnalisé** option, puis cliquez sur **définir**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-153">In the **Application Pool Identity** dialog box, select the **Custom Account** option, and then click **Set**.</span></span>  
  
5.  <span data-ttu-id="ba3ba-154">Dans le **définir les informations d’identification** boîte de dialogue, spécifiez un nom d’utilisateur et un mot de passe, confirmez le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-154">In the **Set Credentials** dialog box, specify a username and password, confirm the password, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-155">Cet utilisateur doit être autorisé à exécuter le service Web Orchestration Proxy et être ajouté au groupe Administrateurs BizTalk Server, Administrateurs de l'authentification unique ou Administrateurs d'applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-155">This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups</span></span>  
  
6.  <span data-ttu-id="ba3ba-156">Cliquez sur **OK** pour fermer la **identité du Pool d’applications** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-156">Click **OK** to close the **Application Pool Identity** dialog box.</span></span>  
  
7.  <span data-ttu-id="ba3ba-157">Cliquez sur **OK** pour fermer la boîte de dialogue **Paramètres avancés** .</span><span class="sxs-lookup"><span data-stu-id="ba3ba-157">Click **OK** to close the **Advanced Settings** dialog box.</span></span>  
  
8.  <span data-ttu-id="ba3ba-158">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-158">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
    1.  <span data-ttu-id="ba3ba-159">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-159">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="ba3ba-160">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub</span><span class="sxs-lookup"><span data-stu-id="ba3ba-160">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub</span></span>  
  
         <span data-ttu-id="ba3ba-161">Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub</span><span class="sxs-lookup"><span data-stu-id="ba3ba-161">PATH = \<BizTalk Install Directory>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Stub</span></span>  
  
         <span data-ttu-id="ba3ba-162">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="ba3ba-162">Access Permissions = Read, Run scripts</span></span>  
  
    2.  <span data-ttu-id="ba3ba-163">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-163">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="ba3ba-164">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span><span class="sxs-lookup"><span data-stu-id="ba3ba-164">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span></span>  
  
         <span data-ttu-id="ba3ba-165">Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span><span class="sxs-lookup"><span data-stu-id="ba3ba-165">PATH = \<BizTalk Install Directory>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span></span>  
  
         <span data-ttu-id="ba3ba-166">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="ba3ba-166">Access Permissions = Read, Run scripts</span></span>  
  
    3.  <span data-ttu-id="ba3ba-167">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-167">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="ba3ba-168">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="ba3ba-168">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
         <span data-ttu-id="ba3ba-169">Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="ba3ba-169">PATH = \<BizTalk Install Directory>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
         <span data-ttu-id="ba3ba-170">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="ba3ba-170">Access Permissions = Read, Run scripts</span></span>  
  
    4.  <span data-ttu-id="ba3ba-171">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-171">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
         <span data-ttu-id="ba3ba-172">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker</span><span class="sxs-lookup"><span data-stu-id="ba3ba-172">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker</span></span>  
  
         <span data-ttu-id="ba3ba-173">Chemin d’accès = \<répertoire d’installation de BizTalk > \SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack</span><span class="sxs-lookup"><span data-stu-id="ba3ba-173">PATH = \<BizTalk Install Directory>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PaymentTrack</span></span>  
  
         <span data-ttu-id="ba3ba-174">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="ba3ba-174">Access Permissions = Read, Run scripts</span></span>  
  
9. <span data-ttu-id="ba3ba-175">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-175">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="ba3ba-176">Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-176">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-177">Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-177">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="ba3ba-178">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-178">Click **OK** to exit.</span></span>  
  
10. <span data-ttu-id="ba3ba-179">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-179">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="ba3ba-180">Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-180">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-181">Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-181">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**.</span></span> <span data-ttu-id="ba3ba-182">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-182">Click **OK** to exit.</span></span>  
  
11. <span data-ttu-id="ba3ba-183">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-183">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="ba3ba-184">Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-184">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-185">Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-185">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**.</span></span> <span data-ttu-id="ba3ba-186">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-186">Click **OK** to exit.</span></span>  
  
12. <span data-ttu-id="ba3ba-187">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-187">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="ba3ba-188">Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à **SSOStubAppPool** vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-188">On the **Virtual directory** tab, set the **Application Pool** to **SSOStubAppPool** you just created.</span></span>  
  
    2.  <span data-ttu-id="ba3ba-189">Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-189">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable Anonymous Access**.</span></span> <span data-ttu-id="ba3ba-190">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-190">Click **OK** to exit.</span></span>  
  
##  <span data-ttu-id="ba3ba-191"><a name="step7"></a>Générez la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-191"><a name="step7"></a> Build the Service Oriented Solution</span></span>  
  
#### <a name="to-build-the-service-oriented-solution"></a><span data-ttu-id="ba3ba-192">Pour générer la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-192">To build the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="ba3ba-193">Démarrer **invite de commandes Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-193">Start **Visual Studio Command Prompt**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-194">Dans les fichiers **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs** et **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\ customerserviceport.asmx.cs**, remplacez toutes les instances de 17f20caea2afcc8c par a1054514fc67bded.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-194">In the files **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Inline\app_code\customerserviceport.asmx.cs** and **%BTSInstallPath%\Scenarios\SO\BTSSoln\OrchProxy\Stub\app_code\customerserviceport.asmx.cs**, replace all the instances of 17f20caea2afcc8c with a1054514fc67bded.</span></span>  
  
2.  <span data-ttu-id="ba3ba-195">À l'invite de commandes Visual Studio, accédez au dossier %BTSSolutionsPath%\SO\BTSSoln, puis exécutez la commande suivante pour générer la version stub de la solution orientée services.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-195">At the Visual Studio Command Prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln folder, and then run the following command to build the stub version of service-oriented solution.</span></span>  
  
    -   `SetupBTSSoln.bat`  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-196">Dans les fichiers répertoriés ci-dessous, remplacez toutes les instances de 17f20caea2afcc8c par le jeton de clé publique actuel.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-196">In the files listed below, replace all the instances of 17f20caea2afcc8c with the current public key token.</span></span>  
    >   
    >  -   <span data-ttu-id="ba3ba-197">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="ba3ba-197">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_CustomerServiceResponse.btm.cs</span></span>  
    > -   <span data-ttu-id="ba3ba-198">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="ba3ba-198">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\Aggregate_To_ErrorResponse.btm.cs</span></span>  
    > -   <span data-ttu-id="ba3ba-199">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="ba3ba-199">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CreditLimitResponse.btm.cs</span></span>  
    > -   <span data-ttu-id="ba3ba-200">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs</span><span class="sxs-lookup"><span data-stu-id="ba3ba-200">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_CustomerServiceResponseDenied.btm.cs</span></span>  
    > -   <span data-ttu-id="ba3ba-201">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs</span><span class="sxs-lookup"><span data-stu-id="ba3ba-201">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_LastPaymentResponseTimeout.btm.cs</span></span>  
    > -   <span data-ttu-id="ba3ba-202">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs</span><span class="sxs-lookup"><span data-stu-id="ba3ba-202">%BTSInstallPath%\Scenarios\SO\BTSSoln\Maps\CustomerServiceRequest_To_PendingTransactionResponse.btm.cs</span></span>  
  
##  <span data-ttu-id="ba3ba-203"><a name="step9"></a>Créer les entrées de Enterprise Single Sign-On (SSO) et les valeurs dans la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="ba3ba-203"><a name="step9"></a> Create the Enterprise Single Sign-On (SSO) entries and values in the SSO database</span></span>  
  
#### <a name="to-create-the-enterprise-single-sign-on-sso-entries-and-values-in-the-sso-database"></a><span data-ttu-id="ba3ba-204">Pour créer les entrées et valeurs de l'authentification unique de l'entreprise (SSO) dans la base de données SSO</span><span class="sxs-lookup"><span data-stu-id="ba3ba-204">To create the Enterprise Single Sign-On (SSO) entries and values in the SSO database</span></span>  
  
1.  <span data-ttu-id="ba3ba-205">Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, puis exécutez les commandes suivantes pour définir l'environnement PATH pour le dossier Authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-205">Open a command prompt, change the current directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts, and then run the following command to set the PATH environment for the Enterprise Single Sign-On folder.</span></span>  
  
    -   `Set PATH=%PATH%;%ProgramFiles%\"Common Files\Enterprise Single Sign-On"`  
  
2.  <span data-ttu-id="ba3ba-206">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, ouvrez le fichier ConfigStoreApp.xml à l'aide du Bloc-notes, puis examinez le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-206">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open ConfigStoreApp.xml using Notepad, and then review the contents of the file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-207">Ce fichier définit l'application de magasin de configuration dans SSO que le scénario utilise pour stocker les paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-207">This file defines the configuration store application in SSO that the scenario uses to store configuration parameters.</span></span> <span data-ttu-id="ba3ba-208">Voici quelques-uns des paramètres de configuration le **délai d’attente** valeur utilisée pour communiquer avec SAP (pour les trois versions).</span><span class="sxs-lookup"><span data-stu-id="ba3ba-208">Some of the configuration parameters include the **Timeout** value used to communicate with SAP (for all three versions).</span></span> <span data-ttu-id="ba3ba-209">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-209">No changes to this file are necessary.</span></span>  
  
3.  <span data-ttu-id="ba3ba-210">À l'invite de commandes, exécutez la commande suivante pour créer l'application de magasin de configuration SSO.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-210">At the command prompt, run the following command to create the SSO configuration store application.</span></span>  
  
    -   `ssomanage -createapps ConfigStoreApp.xml`  
  
4.  <span data-ttu-id="ba3ba-211">À l'invite de commandes, ouvrez SetConfigValuesInSSO.cmd à l'aide du Bloc-notes, puis examinez le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-211">At the command prompt, open SetConfigValuesInSSO.cmd using Notepad, and then review the contents of the file</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ba3ba-212">Ce fichier de commandes définit les valeurs des paramètres de configuration dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-212">This command file sets the values of the configuration parameters in the SSO database.</span></span> <span data-ttu-id="ba3ba-213">Il contient plusieurs instructions Set qui définissent les valeurs dans les variables locales au début du fichier de commandes.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-213">It contains several set statements that set the values in local variables in the beginning of the command file.</span></span> <span data-ttu-id="ba3ba-214">Le **SAPAdapterTimeout**, **PendingTransactionsAdapterTimeout**, et **PaymentTrackingAdapterTimeout** valeurs sont utilisées dans la version stub et d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-214">The **SAPAdapterTimeout**, **PendingTransactionsAdapterTimeout**, and **PaymentTrackingAdapterTimeout** values are used in the stub and adapter version.</span></span> <span data-ttu-id="ba3ba-215">Les valeurs restantes sont utilisées dans la version Inline.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-215">The remaining values are used in the inline version.</span></span> <span data-ttu-id="ba3ba-216">Il n'est pas nécessaire de modifier ce fichier pour la version stub.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-216">No changes to this file are necessary for stub version.</span></span>  
  
5.  <span data-ttu-id="ba3ba-217">À l’invite de commandes, tapez `SetConfigValuesInSSO.cmd`, puis appuyez sur ENTRÉE pour stocker les valeurs dans l’application de magasin de configuration de l’authentification unique.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-217">At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER to store the values in the SSO configuration store application.</span></span>  
  
6.  <span data-ttu-id="ba3ba-218">À l'invite de commandes, exécutez la commande suivante pour activer les tickets dans SSO :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-218">At the command prompt, run the following command to enable tickets in SSO:</span></span>  
  
    -   `ssomanage -tickets yes yes`  
  
##  <span data-ttu-id="ba3ba-219"><a name="step11"></a>Déployer la définition BAM pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-219"><a name="step11"></a> Deploy the BAM definition for the Service Oriented Solution</span></span>  
  
#### <a name="to-deploy-the-bam-definition-for-the-service-oriented-solution"></a><span data-ttu-id="ba3ba-220">Pour déployer la définition BAM pour la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-220">To deploy the BAM definition for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="ba3ba-221">À l’invite de commandes, tapez la commande suivante et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-221">At a command prompt, type the following command, and then press ENTER.</span></span> <span data-ttu-id="ba3ba-222">Cela permet de définir le chemin d'accès de l'utilitaire BAM :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-222">This sets the path to find the BAM utility:</span></span>  
  
    -   <span data-ttu-id="ba3ba-223">SET PATH=%PATH%;%programfiles%\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\Tracking</span><span class="sxs-lookup"><span data-stu-id="ba3ba-223">SET PATH=%PATH%;%programfiles%\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]\Tracking</span></span>  
  
2.  <span data-ttu-id="ba3ba-224">À l’invite de commandes, accédez au répertoire du dossier %BTSSolutionsPath%\SO\BTSSoln\BAM et tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-224">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM folder, and type the following command, and then press ENTER:</span></span>  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
        > [!NOTE]
        >  <span data-ttu-id="ba3ba-225">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-225">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
##  <span data-ttu-id="ba3ba-226"><a name="step13"></a>Déployer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-226"><a name="step13"></a> Deploy the Service Oriented Solution</span></span>  
  
#### <a name="to-deploy-the-service-oriented-solution"></a><span data-ttu-id="ba3ba-227">Pour déployer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="ba3ba-227">To deploy the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="ba3ba-228">Ouvrez une invite de commandes, puis accédez au dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-228">Open a command prompt and change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="ba3ba-229">Modifier la **DeployStubBinding.cmd** fichier en remplaçant toutes les instances de « debug » et « development » par « release ».</span><span class="sxs-lookup"><span data-stu-id="ba3ba-229">Modify the **DeployStubBinding.cmd** file by replacing all the instances of “debug” and “development” with “release”.</span></span>  
  
3.  <span data-ttu-id="ba3ba-230">Ouvrez une invite de commandes, puis accédez au dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-230">Open a command prompt and change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span> <span data-ttu-id="ba3ba-231">Tapez la commande suivante et appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="ba3ba-231">Type the following command, and then press ENTER:</span></span>  
  
    -   `DeployStubBinding.cmd`  
  
4.  <span data-ttu-id="ba3ba-232">À l'invite de commandes, exécutez la commande suivante pour démarrer les orchestrations de la version stub.</span><span class="sxs-lookup"><span data-stu-id="ba3ba-232">At the command prompt, run the following command to start the orchestrations for the stub version</span></span>  
  
    -   `Startstub.vbs`  
  
## <a name="next-steps"></a><span data-ttu-id="ba3ba-233">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="ba3ba-233">Next Steps</span></span>  
 <span data-ttu-id="ba3ba-234">Tester le fonctionne de la version stub de la solution orientée services dans [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="ba3ba-234">You test how the stub version of the service-oriented solution works in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba3ba-235">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba3ba-235">See Also</span></span>  
 <span data-ttu-id="ba3ba-236">[Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="ba3ba-236">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="ba3ba-237">[Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="ba3ba-237">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="ba3ba-238">Installation d’ordinateur de développeur pour le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="ba3ba-238">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)