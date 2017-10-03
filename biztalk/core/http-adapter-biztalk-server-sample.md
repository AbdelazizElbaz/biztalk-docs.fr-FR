---
title: "L’adaptateur HTTP (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: f3bd8172-15c4-42fa-aa17-e4bed9d4aba4
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4f443bf0b60f0bb90a914824b3922110ee1b300
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-biztalk-server-sample"></a><span data-ttu-id="30782-102">Adaptateur HTTP (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="30782-102">HTTP Adapter (BizTalk Server Sample)</span></span>
<span data-ttu-id="30782-103">L'exemple d'adaptateur HTTP illustre l'implémentation des paradigmes de communication de requête/réponse et de sollicitation/réponse utilisés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30782-103">The HTTP Adapter sample demonstrates how to implement the request/response and solicit/response communication paradigms used in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="30782-104">Accès à l'exemple</span><span class="sxs-lookup"><span data-stu-id="30782-104">Where to Find This Sample</span></span>  
 <span data-ttu-id="30782-105">*\<Exemples de chemin d’accès >*\AdaptersDevelopment\HttpAdapter\\</span><span class="sxs-lookup"><span data-stu-id="30782-105">*\<Samples Path>*\AdaptersDevelopment\HttpAdapter\\</span></span>  
  
 <span data-ttu-id="30782-106">Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.</span><span class="sxs-lookup"><span data-stu-id="30782-106">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="30782-107">Fichier(s)</span><span class="sxs-lookup"><span data-stu-id="30782-107">File(s)</span></span>|<span data-ttu-id="30782-108"> Description</span><span class="sxs-lookup"><span data-stu-id="30782-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30782-109">\Design-Time\Adapter Management</span><span class="sxs-lookup"><span data-stu-id="30782-109">\Design-Time\Adapter Management</span></span>|<span data-ttu-id="30782-110">Contient le projet qui implémente la phase de conception de cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="30782-110">Contains the project that implements the design time portion of this adapter.</span></span>|  
|<span data-ttu-id="30782-111">\Run-Time\HttpReceive</span><span class="sxs-lookup"><span data-stu-id="30782-111">\Run-Time\HttpReceive</span></span>|<span data-ttu-id="30782-112">Contient le projet qui implémente le modèle de communication de l'adaptateur de requête/réponse.</span><span class="sxs-lookup"><span data-stu-id="30782-112">Contains the project that implements the request/response adapter communication pattern.</span></span> <span data-ttu-id="30782-113">Il s'agit d'un récepteur isolé.</span><span class="sxs-lookup"><span data-stu-id="30782-113">This is an isolated receiver.</span></span>|  
|<span data-ttu-id="30782-114">\Run-Time\HttpSend</span><span class="sxs-lookup"><span data-stu-id="30782-114">\Run-Time\HttpSend</span></span>|<span data-ttu-id="30782-115">Contient le projet qui implémente le modèle de communication de l'adaptateur de type sollicitation/réponse.</span><span class="sxs-lookup"><span data-stu-id="30782-115">Contains the project that implements the solicit/response adapter communication pattern.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="30782-116">L’utilisation de cet exemple</span><span class="sxs-lookup"><span data-stu-id="30782-116">How to Use This Sample</span></span>  
 <span data-ttu-id="30782-117">Cet exemple est conçu comme une infrastructure que vous utilisez pour développer des adaptateurs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="30782-117">This sample is meant as a framework for you to use in developing custom adapters.</span></span> <span data-ttu-id="30782-118">Il peut arriver que BizTalk Server doive acheminer des messages vers une application personnalisée ou utiliser un protocole pour lequel aucun adaptateur natif n'est prévu.</span><span class="sxs-lookup"><span data-stu-id="30782-118">In some cases BizTalk Server may need to transport messages to a specific custom application or use a protocol for which a native adapter that does not exist.</span></span> <span data-ttu-id="30782-119">Des entreprises tierces ont élaboré des adaptateurs qui prennent en charge des protocoles supplémentaires,</span><span class="sxs-lookup"><span data-stu-id="30782-119">Third-party companies have written adapters to support additional protocols.</span></span> <span data-ttu-id="30782-120">et vous souhaitez peut-être savoir s'il existe un adaptateur adapté à votre protocole avant d'écrire le vôtre.</span><span class="sxs-lookup"><span data-stu-id="30782-120">You may want to determine if there is an adapter for your protocol before deciding to write a custom adapter.</span></span> <span data-ttu-id="30782-121">Si vous ne parvenez pas à trouver un adaptateur qui prenne en charge vos conditions de communication, il vous reste la possibilité de développer votre propre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="30782-121">If you are unable to locate an adapter to support your communication requirements, you can develop your own custom adapter.</span></span>  
  
 <span data-ttu-id="30782-122">L'écriture d'un adaptateur personnalisé peut se révéler difficile.</span><span class="sxs-lookup"><span data-stu-id="30782-122">Writing a custom adapter can be a challenging exercise.</span></span> <span data-ttu-id="30782-123">Pour vous faciliter la tâche, Microsoft a développé une structure de base appelée Infrastructure d'adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="30782-123">To simplify this process Microsoft has developed a foundation called the Adapter Framework.</span></span> <span data-ttu-id="30782-124">Vous pouvez vous baser sur cette infrastructure, de même que vous pouvez utiliser l'exemple de code source fourni dans le kit SDK de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="30782-124">You can use this framework as a basis for your development along with sample adapter source code in the BizTalk Server SDK.</span></span>  <span data-ttu-id="30782-125">Pour plus d’informations sur les adaptateurs personnalisés et l’infrastructure d’adaptateurs, reportez-vous à la **Voir aussi** section à la fin de ce document.</span><span class="sxs-lookup"><span data-stu-id="30782-125">For more information on custom adapters, and the Adapter Framework, please refer to the **See Also** section at the end of this document.</span></span>  
  
## <a name="building-and-initializing-the-sample-adapter"></a><span data-ttu-id="30782-126">Création et initialisation de l'exemple d'adaptateur</span><span class="sxs-lookup"><span data-stu-id="30782-126">Building and Initializing the Sample Adapter</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="30782-127">Si l'installation BizTalk est 64 bits ou si son emplacement a été modifié, les valeurs OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath doivent être modifiées en conséquence.</span><span class="sxs-lookup"><span data-stu-id="30782-127">If the BizTalk installation is 64-bit or the location of installation is modified, OutboundAssemblyPath, InboundAssemblyPath, AdapterMgmtAssemblyPath would need to be changed accordingly.</span></span>  
  
#### <a name="to-build-and-initialize-the-http-adapter-sample"></a><span data-ttu-id="30782-128">Pour créer et initialiser l'exemple d'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="30782-128">To build and initialize the HTTP Adapter sample</span></span>  
  
1.  <span data-ttu-id="30782-129">Dans une fenêtre de commande, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="30782-129">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="30782-130">\<*Exemples de chemin d’accès*> \AdaptersDevelopment\HttpAdapter</span><span class="sxs-lookup"><span data-stu-id="30782-130">\<*Samples Path*>\AdaptersDevelopment\HttpAdapter</span></span>  
  
2.  <span data-ttu-id="30782-131">Exécutez le fichier Setup.bat, qui effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="30782-131">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="30782-132">Compile HTTPAdapter et toutes ses dépendances.</span><span class="sxs-lookup"><span data-stu-id="30782-132">Compiles the HTTPAdapter and all of its dependencies.</span></span>  
  
    -   <span data-ttu-id="30782-133">Crée une application IIS utilisée par le côté récepteur de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="30782-133">Creates an Internet Information Services (IIS) application used by the receiver side of the adapter.</span></span>  
  
 <span data-ttu-id="30782-134">Sous IIS port d'envoi, vous devez vérifier que l'identité du pool d'applications exécutant cette application IIS est membre des groupes suivants :</span><span class="sxs-lookup"><span data-stu-id="30782-134">On IIS 7.0, you must ensure the identity of the application pool running this IIS application is a member of the following groups:</span></span>  
  
-   <span data-ttu-id="30782-135">groupe Utilisateurs d'hôtes BizTalk isolés ;</span><span class="sxs-lookup"><span data-stu-id="30782-135">BizTalk Isolated Host Users group.</span></span>  
  
-   <span data-ttu-id="30782-136">groupe IIS_WPG.</span><span class="sxs-lookup"><span data-stu-id="30782-136">IIS_WPG group.</span></span>  
  
-   <span data-ttu-id="30782-137">Sous IIS 7.0, vous devez migrer l’application fonctionne avec le mode .NET intégré.</span><span class="sxs-lookup"><span data-stu-id="30782-137">On IIS 7.0, you must migrate the application to work with the Integrated .NET mode.</span></span> <span data-ttu-id="30782-138">Vous pouvez migrer la configuration d’application, y compris le contenu de la \<httpHandlers > section de configuration, à l’aide de ce qui suit à partir d’une fenêtre de ligne de commande (la fenêtre doit être en cours d’exécution en tant qu’administrateur) :</span><span class="sxs-lookup"><span data-stu-id="30782-138">You can migrate the application configuration, including the contents of the \<httpHandlers> configuration section, by using the following from a command line window (the window must be running as Administrator):</span></span>  
  
    ```  
    %systemroot%\system32\inetsrv\APPCMD.EXE migrate config "Default Web Site/HttpReceive"  
    ```  
  
-   <span data-ttu-id="30782-139">Après avoir migré votre application, elle sera exécutée en mode classique et en mode .NET intégré, tout comme sur les plateformes de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="30782-139">After you migrate your application, it will run in both Classic and Integrated .NET modes, as well as on downlevel platforms.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30782-140">Avant de tenter d'exécuter cet exemple, vous devez vérifier qu'aucune erreur n'a été signalée durant le processus de création et d'initialisation.</span><span class="sxs-lookup"><span data-stu-id="30782-140">You should confirm that no errors were reported during the build and initialization process before attempting to run this sample.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30782-141">Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe).</span><span class="sxs-lookup"><span data-stu-id="30782-141">If you choose to open and build the projects in this sample without running the file Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name Utility (sn.exe).</span></span> <span data-ttu-id="30782-142">Celle-ci permet de signer les assemblys obtenus.</span><span class="sxs-lookup"><span data-stu-id="30782-142">Use this key pair to sign the resulting assemblies.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30782-143">Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="30782-143">To undo changes made by Setup.bat, run Cleanup.bat.</span></span> <span data-ttu-id="30782-144">Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.</span><span class="sxs-lookup"><span data-stu-id="30782-144">You must run Cleanup.bat before running Setup.bat a second time.</span></span>  
  
## <a name="registering-the-sample-adapter"></a><span data-ttu-id="30782-145">Enregistrement de l'exemple d'adaptateur</span><span class="sxs-lookup"><span data-stu-id="30782-145">Registering the Sample Adapter</span></span>  
  
#### <a name="to-register-the-http-adapter-sample"></a><span data-ttu-id="30782-146">Pour enregistrer l'exemple d'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="30782-146">To register the HTTP Adapter sample</span></span>  
  
1.  <span data-ttu-id="30782-147">Dans l’Explorateur Windows, accédez au lecteur d’installation pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis accédez à \<chemin d’accès des exemples > \AdaptersDevelopment\HTTPAdapter.</span><span class="sxs-lookup"><span data-stu-id="30782-147">In Windows Explorer, navigate to the installation drive for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then navigate to \<Samples Path>\AdaptersDevelopment\HTTPAdapter.</span></span>  
  
2.  <span data-ttu-id="30782-148">Pour ajouter l’exemple d’adaptateur au Registre, double-cliquez sur **HTTP.NET.reg**.</span><span class="sxs-lookup"><span data-stu-id="30782-148">To add the sample adapter to the registry, double-click **HTTP.NET.reg**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30782-149">HTTP.NET.reg inclut des chemins d'accès codés en dur vers le répertoire d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30782-149">HTTP.NET.reg includes hard-coded paths to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation directory.</span></span> <span data-ttu-id="30782-150">Si vous n'avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'emplacement par défaut ou si vous avez mis à niveau votre installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une version antérieure de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez modifier le fichier HTTP.NET.reg en y indiquant les chemins d'accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="30782-150">If you did not install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the default location or if you upgraded your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from a previous version of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you must modify the file HTTP.NET.reg with the appropriate paths.</span></span> <span data-ttu-id="30782-151">Mettez à jour les chemins d'accès associés aux valeurs « OutboundAssemblyPath » et « AdapterMgmtAssemblyPath » afin qu'ils pointent vers l'emplacement exact des fichiers spécifiés.</span><span class="sxs-lookup"><span data-stu-id="30782-151">Update the paths associated with the "OutboundAssemblyPath" and "AdapterMgmtAssemblyPath" values to point to the correct location of the specified files.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="30782-152">Si vous installez BizTalk sur un ordinateur 64 bits, modifiez toutes les instances de l’entrée de Registre HKEY_CLASSES_ROOT\CLSID\ à HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ dans le **HTTP.NET.reg** fichier de Registre.</span><span class="sxs-lookup"><span data-stu-id="30782-152">If you install BizTalk on a 64 bit machine, change all instances of the HKEY_CLASSES_ROOT\CLSID\ registry entry to HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ in the **HTTP.NET.reg** registry file.</span></span>  
  
3.  <span data-ttu-id="30782-153">Dans le **Éditeur du Registre** boîte de dialogue, cliquez sur **Oui** à ajouter l’exemple d’adaptateur au Registre, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="30782-153">In the **Registry Editor** dialog box, click **Yes** to add the sample adapter to the registry, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="30782-154">Pour fermer l’Explorateur Windows, dans le **fichier** menu, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="30782-154">To close Windows Explorer, on the **File** menu, click **Close**.</span></span>  
  
## <a name="installing-the-sample-adapter"></a><span data-ttu-id="30782-155">Installation de l'exemple d'adaptateur</span><span class="sxs-lookup"><span data-stu-id="30782-155">Installing the Sample Adapter</span></span>  
  
#### <a name="to-install-the-http-adapter-sample"></a><span data-ttu-id="30782-156">Pour installer l'exemple d'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="30782-156">To install the HTTP Adapter sample</span></span>  
  
1.  <span data-ttu-id="30782-157">Cliquez sur le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="30782-157">Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then select **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="30782-158">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] d’arborescence, puis développez le **groupe BizTalk** d’arborescence, puis développez le **paramètres de plateforme** arborescence.</span><span class="sxs-lookup"><span data-stu-id="30782-158">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] tree, then expand the **BizTalk Group** tree, then expand the **Platform Settings** tree.</span></span>  
  
3.  <span data-ttu-id="30782-159">Avec le bouton droit **cartes**, cliquez sur **nouveau**, puis cliquez sur **carte**.</span><span class="sxs-lookup"><span data-stu-id="30782-159">Right-click **Adapters**, click **New**, and then click **Adapter**.</span></span>  
  
4.  <span data-ttu-id="30782-160">Dans le **propriétés de l’adaptateur** boîte de dialogue zone, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="30782-160">In the **Adapter Properties** dialog box, do the following.</span></span>  
  
    |<span data-ttu-id="30782-161">Utiliser</span><span class="sxs-lookup"><span data-stu-id="30782-161">Use this</span></span>|<span data-ttu-id="30782-162">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="30782-162">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="30782-163">Nom</span><span class="sxs-lookup"><span data-stu-id="30782-163">Name</span></span>|<span data-ttu-id="30782-164">Type **HTTP.NET**.</span><span class="sxs-lookup"><span data-stu-id="30782-164">Type **HTTP.NET**.</span></span>|  
    |<span data-ttu-id="30782-165">Adaptateur</span><span class="sxs-lookup"><span data-stu-id="30782-165">Adapter</span></span>|<span data-ttu-id="30782-166">Sélectionnez **HTTP.NET** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="30782-166">Select **HTTP.NET** from the drop-down list.</span></span>|  
    |<span data-ttu-id="30782-167"> Description</span><span class="sxs-lookup"><span data-stu-id="30782-167">Description</span></span>|<span data-ttu-id="30782-168">Type **exemple d’adaptateur HTTP.NET**.</span><span class="sxs-lookup"><span data-stu-id="30782-168">Type **Sample HTTP.NET Adapter**.</span></span>|  
  
5.  <span data-ttu-id="30782-169">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="30782-169">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="30782-170">L'adaptateur apparaît dans la liste des adaptateurs, dans la fenêtre droite de la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="30782-170">The adapter now appears in the list of adapters in the right window of the BizTalk Administration console.</span></span>  
  
## <a name="stopping-and-restarting-the-host-instance"></a><span data-ttu-id="30782-171">Arrêt et redémarrage de l'instance de l'hôte</span><span class="sxs-lookup"><span data-stu-id="30782-171">Stopping and Restarting the Host Instance</span></span>  
  
#### <a name="to-stop-and-restart-the-host-instance-for-the-http-adapter-sample"></a><span data-ttu-id="30782-172">Pour arrêter et redémarrer l'instance de l'hôte pour l'exemple d'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="30782-172">To stop and restart the host instance for the HTTP Adapter sample</span></span>  
  
1.  <span data-ttu-id="30782-173">Cliquez sur le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis sélectionnez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30782-173">Click the **Start** menu, select **All Programs**, select [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and select [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="30782-174">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez le [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] , puis **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="30782-174">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] tree, then expand **Platform Settings**, and click **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="30782-175">Dans le volet de résultats, cliquez sur l’instance d’hôte (en règle générale, le nom d’ordinateur), puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="30782-175">In the results pane, right-click the host instance (typically, the computer name), and then click **Stop**.</span></span>  
  
     <span data-ttu-id="30782-176">L’état de l’instance d’hôte devient **arrêté**.</span><span class="sxs-lookup"><span data-stu-id="30782-176">The status of the host instance changes to **Stopped**.</span></span>  
  
4.  <span data-ttu-id="30782-177">Dans le volet de résultats, cliquez sur l’instance d’hôte, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="30782-177">In the results pane, right-click the host instance, and then click **Start**.</span></span>  
  
 <span data-ttu-id="30782-178">L'adaptateur HTTP.NET peut maintenant être utilisé par votre application.</span><span class="sxs-lookup"><span data-stu-id="30782-178">The HTTP.NET adapter is now ready to be used by your application.</span></span> <span data-ttu-id="30782-179">Lors de la configuration de l’adaptateur, le format de la **répertoire virtuel** propriété du transport est au format : /httpreceive/httpreceive.aspx?optionalQueryString.</span><span class="sxs-lookup"><span data-stu-id="30782-179">When configuring the adapter, the format for the **Virtual Directory** transport property is of the form: /httpreceive/httpreceive.aspx?optionalQueryString.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="30782-180">Commentaires</span><span class="sxs-lookup"><span data-stu-id="30782-180">Comments</span></span>  
 <span data-ttu-id="30782-181">Le fait de l’adaptateur HTTP.NET utilisation des classes BaseAdapter fournie dans  *\<exemples de chemin >*\AdaptersDevelopment\BaseAdapter\v1.0... 2\\.</span><span class="sxs-lookup"><span data-stu-id="30782-181">The HTTP.NET adapter makes use of the BaseAdapter classes provided in *\<Samples Path>*\AdaptersDevelopment\BaseAdapter\v1.0..2\\.</span></span> <span data-ttu-id="30782-182">Les classes fournies dans le projet BaseAdapter sont conçues pour accélérer le développement de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="30782-182">The classes provided in the BaseAdapter project are intended to accelerate adapter development.</span></span> <span data-ttu-id="30782-183">Pour plus d'informations sur les classes fournies, consultez les commentaires du code BaseAdapter.</span><span class="sxs-lookup"><span data-stu-id="30782-183">Refer to the BaseAdapter code comments for details about the classes provided.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30782-184">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30782-184">See Also</span></span>  
 <span data-ttu-id="30782-185">[Inscription d’un adaptateur](../core/registering-an-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="30782-185">[Registering an Adapter](../core/registering-an-adapter.md) </span></span>  
 <span data-ttu-id="30782-186">[Exemples d’adaptateurs - utilisation](../core/adapter-samples-usage.md) </span><span class="sxs-lookup"><span data-stu-id="30782-186">[Adapter Samples - Usage](../core/adapter-samples-usage.md) </span></span>  
 <span data-ttu-id="30782-187">[Développement d’adaptateurs personnalisés](../core/developing-custom-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="30782-187">[Developing Custom Adapters](../core/developing-custom-adapters.md) </span></span>  
 <span data-ttu-id="30782-188">[Quelle est l’infrastructure d’adaptateurs ?](../core/what-is-the-adapter-framework.md) </span><span class="sxs-lookup"><span data-stu-id="30782-188">[What Is the Adapter Framework?](../core/what-is-the-adapter-framework.md) </span></span>  
 <span data-ttu-id="30782-189">[L’utilisation des outils de Framework adaptateur](../core/using-the-adapter-framework-tools.md) </span><span class="sxs-lookup"><span data-stu-id="30782-189">[Using the Adapter Framework Tools](../core/using-the-adapter-framework-tools.md) </span></span>  
 <span data-ttu-id="30782-190">[Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="30782-190">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="30782-191">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="30782-191">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="30782-192">[Comment déployer un adaptateur personnalisé](../core/how-to-deploy-a-custom-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="30782-192">[How to Deploy a Custom Adapter](../core/how-to-deploy-a-custom-adapter.md) </span></span>  
 <span data-ttu-id="30782-193">[Conseils pour la conception de votre adaptateur.](../core/tips-for-designing-your-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="30782-193">[Tips for Designing Your Adapter](../core/tips-for-designing-your-adapter.md) </span></span>  
 [<span data-ttu-id="30782-194">Configuration de l’adaptateur au moment du Design</span><span class="sxs-lookup"><span data-stu-id="30782-194">Adapter Design-Time Configuration</span></span>](../core/adapter-design-time-configuration.md)