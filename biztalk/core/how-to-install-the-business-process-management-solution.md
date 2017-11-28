---
title: "Comment installer la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, examples
- process management solution tutorial, installing
- process management solution tutorial, deployment prerequisites
ms.assetid: 930f3bb1-05e6-4b02-852d-6139aaf341f0
caps.latest.revision: "61"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22b16e8c33dfdbf44b000cc9a048e86a5869d616
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-business-process-management-solution"></a><span data-ttu-id="67bd0-102">Installation de la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-102">How to Install the Business Process Management Solution</span></span>
<span data-ttu-id="67bd0-103">La procédure suivante décrit la préparation de votre ordinateur pour l'installation de la solution de gestion des processus d'entreprise, puis l'installation de la solution sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="67bd0-103">The following steps describe how to prepare the computer for installing the Business Process Management (BPM) solution, and how to install the solution on this computer.</span></span>  
  
-   [<span data-ttu-id="67bd0-104">Préparer l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-104">Prepare the computer for installing the Business Process Management Solution</span></span>](#step1)  
  
     <span data-ttu-id="67bd0-105">Dans le cadre de la préparation, vous êtes amené à créer des dossiers, des files d'attente et une base de données SQL qui seront utilisés par les ports de réception et d'envoi.</span><span class="sxs-lookup"><span data-stu-id="67bd0-105">In the preparation step, you create the folders, queues, and SQL database that will be used by the receive and send ports.</span></span> <span data-ttu-id="67bd0-106">Vous devez également créer deux répertoires virtuels pour l'application cliente (CSRWebApp) et le service Web proxy OrderBroker.</span><span class="sxs-lookup"><span data-stu-id="67bd0-106">You also create the two virtual directories for the client application, CSRWebApp, and the OrderBroker proxy Web Service.</span></span>  
  
-   [<span data-ttu-id="67bd0-107">Configurez l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-107">Configure the computer for installing the Business Process Management Solution</span></span>](#step3)  
  
-   [<span data-ttu-id="67bd0-108">Installer la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-108">Install the Business Process Management Solution</span></span>](#step5)  
  
> [!NOTE]
>  <span data-ttu-id="67bd0-109">Vous devez exécuter des fichiers de commandes pour déployer la solution.</span><span class="sxs-lookup"><span data-stu-id="67bd0-109">You will run some batch files to deploy the solution.</span></span> <span data-ttu-id="67bd0-110">Il est recommandé de rediriger la sortie des fichiers de commandes vers un fichier texte pour vérifier l'exécution correcte du script.</span><span class="sxs-lookup"><span data-stu-id="67bd0-110">We recommend that you redirect the output of the batch files to a text file to verify that the script completed successfully.</span></span>  
  
##  <span data-ttu-id="67bd0-111"><a name="step1"></a>Préparer l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-111"><a name="step1"></a> Prepare the computer for installing the Business Process Management Solution</span></span>  
  
#### <a name="to-prepare-the-computer-for-installing-the-business-process-management-solution"></a><span data-ttu-id="67bd0-112">Pour préparer l'ordinateur pour l'installation de la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-112">To prepare the computer for installing the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="67bd0-113">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, puis cliquez sur **Services**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-113">Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **Services**.</span></span> <span data-ttu-id="67bd0-114">À l’aide de la **Services** de la console, assurez-vous que les services suivants sont en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="67bd0-114">Using the **Services** console, make sure that the following services are running:</span></span>  
  
    -   <span data-ttu-id="67bd0-115">**Publication FTP**</span><span class="sxs-lookup"><span data-stu-id="67bd0-115">**FTP Publishing**</span></span>  
  
    -   <span data-ttu-id="67bd0-116">**Message Queuing**</span><span class="sxs-lookup"><span data-stu-id="67bd0-116">**Message Queuing**</span></span>  
  
    -   <span data-ttu-id="67bd0-117">**Publication du World Wide Web**</span><span class="sxs-lookup"><span data-stu-id="67bd0-117">**World Wide Web Publishing**</span></span>  
  
2.  <span data-ttu-id="67bd0-118">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="67bd0-118">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
3.  <span data-ttu-id="67bd0-119">Si vous avez installé Windows SharePoint Services, excluez la (racine) de la **Site Web par défaut** à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes** , pointez sur **outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-119">If you installed Windows SharePoint Services, exclude the (root) of the **Default Web Site** from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="67bd0-120">Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-120">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="67bd0-121">Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-121">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="67bd0-122">Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-122">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="67bd0-123">Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-123">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="67bd0-124">Ouvrez une invite de commandes, puis exécutez IISReset.</span><span class="sxs-lookup"><span data-stu-id="67bd0-124">At a command prompt, perform an IISReset.</span></span>  
  
##  <span data-ttu-id="67bd0-125"><a name="step3"></a>Configurez l’ordinateur pour l’installation de la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-125"><a name="step3"></a> Configure the computer for installing the Business Process Management Solution</span></span>  
  
#### <a name="to-configure-the-computer-for-installing-the-business-process-management-solution"></a><span data-ttu-id="67bd0-126">Pour configurer l'ordinateur pour l'installation de la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-126">To configure the computer for installing the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="67bd0-127">Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="67bd0-127">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
2.  <span data-ttu-id="67bd0-128">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir la variable d'environnement %BTSSolutionsPath% et indiquer le dossier de base pour les solutions E2E.</span><span class="sxs-lookup"><span data-stu-id="67bd0-128">Open a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable to indicate the base folder for the E2E solutions.</span></span> <span data-ttu-id="67bd0-129">Fermez ensuite l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="67bd0-129">Then, exit the command prompt.</span></span>  
  
    -   `setx BTSSolutionsPath "%ProgramFiles%\Microsoft BizTalk Server 2009\SDK\Scenarios"`  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-130">Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="67bd0-130">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-131">Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span><span class="sxs-lookup"><span data-stu-id="67bd0-131">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
3.  <span data-ttu-id="67bd0-132">Ouvrez une invite de commandes, accédez au répertoire en cours %BTSSolutionsPath%\BPM\HistoryDB dossier, tapez `CreateDatabase.cmd`, puis appuyez sur ENTRÉE pour créer la base de données de l’historique.</span><span class="sxs-lookup"><span data-stu-id="67bd0-132">Open a command prompt, change the current directory to %BTSSolutionsPath%\BPM\HistoryDB folder, type `CreateDatabase.cmd`, and press ENTER to create the history database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67bd0-133">L'utilisateur exécutant l'hôte spécifié comme gestionnaire pour l'adaptateur d'envoi SQL doit être autorisé à exécuter les procédures stockées dans la base de données SouthridgeVideoHistory.</span><span class="sxs-lookup"><span data-stu-id="67bd0-133">The user running the host specified as the handler for the SQL send adapter must have permissions to execute stored procedures on the SouthridgeVideoHistory database.</span></span>  
  
4.  <span data-ttu-id="67bd0-134">Ouvrez une invite de commandes, puis exécutez la commande suivante pour définir l'environnement d'exécution de scripts par défaut sur CScript.exe.</span><span class="sxs-lookup"><span data-stu-id="67bd0-134">At a command prompt, run the following command to change the default script host to CScript.exe</span></span>  
  
    -   `CScript /H:CScript`  
  
5.  <span data-ttu-id="67bd0-135">Ouvrez une invite de commandes, puis exécutez la commande suivante pour créer l'application Web CSRWebApp.</span><span class="sxs-lookup"><span data-stu-id="67bd0-135">At a command prompt, run the following command to create the CSRWebApp Web application</span></span>  
  
    -   `iisvdir /create "Default Web Site" CSRWebApp "%BTSSolutionsPath%\BPM\CSRWebApp"`  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-136">Pour plus d’informations sur iisvdir.vbs, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span><span class="sxs-lookup"><span data-stu-id="67bd0-136">For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span></span>  
  
6.  <span data-ttu-id="67bd0-137">Ouvrez une invite de commandes, puis exécutez la commande suivante pour créer le répertoire virtuel IIS OrderBroker_Proxy.</span><span class="sxs-lookup"><span data-stu-id="67bd0-137">At a command prompt, run the following command to create a new IIS virtual directory for OrderBroker_Proxy.</span></span>  
  
    -   `iisvdir /create "Default Web Site" BTSScn.BPM.OrderBroker_Proxy "%BTSSolutionsPath%\BPM\OrderBroker_Proxy"`  
  
    > [!NOTE]
    >  <span data-ttu-id="67bd0-138">Vous pouvez utiliser le Gestionnaire des Services Internet (IIS) pour créer l'application Web.</span><span class="sxs-lookup"><span data-stu-id="67bd0-138">You can use Internet Information Services (IIS) Manager to create the Web Application.</span></span> <span data-ttu-id="67bd0-139">Pour plus d’informations sur la création d’applications dans IIS 7.0, consultez la Documentation d’IIS 7.0 à [http://go.microsoft.com/fwlink/?LinkId=59263](http://go.microsoft.com/fwlink/?LinkId=59263).</span><span class="sxs-lookup"><span data-stu-id="67bd0-139">For more information about how to create applications in IIS 7.0, see the IIS 7.0 Documentation at [http://go.microsoft.com/fwlink/?LinkId=59263](http://go.microsoft.com/fwlink/?LinkId=59263).</span></span>  
  
7.  <span data-ttu-id="67bd0-140">Créez un pool d'applications IIS et définissez son identité en tant qu'utilisateur membre du groupe Utilisateurs d'hôtes BizTalk isolés et du groupe IIS_WPG, comme suit :</span><span class="sxs-lookup"><span data-stu-id="67bd0-140">Create a new IIS application pool and set its identity as a user that is a member of the BizTalk Isolated Host Users group and the IIS_WPG group, as follows:</span></span>  
  
    1.  <span data-ttu-id="67bd0-141">Dans le Gestionnaire des Services Internet (IIS), cliquez sur **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Pool d’applications**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-141">In Internet Information Services (IIS) Manager, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    2.  <span data-ttu-id="67bd0-142">Type de la **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-142">Type the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
    3.  <span data-ttu-id="67bd0-143">Cliquez sur le pool d’applications que vous avez créé, puis sélectionnez **paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-143">Right-click the application pool that you created, and then select **Advanced Settings**.</span></span>  
  
    4.  <span data-ttu-id="67bd0-144">Développez **modèle de processus**, cliquez dans la colonne de droite pour le **identité** définition, puis cliquez sur **...**</span><span class="sxs-lookup"><span data-stu-id="67bd0-144">Expand **Process Model**, click in the right-column for the **Identity** setting, and then click **…**</span></span>  
  
    5.  <span data-ttu-id="67bd0-145">Sélectionnez un compte d’utilisateur (soit un **compte** ou **compte personnalisé** ) qui dispose des autorisations pour créer et exécuter des fichiers dans le répertoire Windows\Temp.</span><span class="sxs-lookup"><span data-stu-id="67bd0-145">Select a user account (either a **Build-in account** or **Custom account** ) that has permissions to create and execute files in the Windows\Temp directory.</span></span> <span data-ttu-id="67bd0-146">Lorsque vous avez configuré BizTalk, le processus de configuration a déjà défini ces autorisations pour l'utilisateur ajouté au groupe Utilisateurs d'hôtes BizTalk isolés.</span><span class="sxs-lookup"><span data-stu-id="67bd0-146">When you configured BizTalk, the configuration process already set these permissions for the user it added to the BizTalk Isolated Host Users group.</span></span> <span data-ttu-id="67bd0-147">Spécifier le même utilisateur constitue une bonne option.</span><span class="sxs-lookup"><span data-stu-id="67bd0-147">Specifying the same user is a good choice.</span></span>  
  
8.  <span data-ttu-id="67bd0-148">Dans le Gestionnaire des Services Internet (IIS), développez **Sites Web**, développez **Site Web par défaut**, avec le bouton droit **BTSScn.BPM.OrderBroker_Proxy**, pointez sur **Gérer l’Application**, puis cliquez sur **paramètres avancés**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-148">In Internet Information Services (IIS) Manager, expand **Web Sites**, expand **Default Web Site**, right-click **BTSScn.BPM.OrderBroker_Proxy**, point to **Manage Application**, and then click **Advanced Settings**.</span></span>  
  
9. <span data-ttu-id="67bd0-149">Définissez **Pool d’applications** au pool d’applications que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="67bd0-149">Set **Application Pool** to the application pool that you  created in the previous step.</span></span>  
  
10. <span data-ttu-id="67bd0-150">Répétez les deux étapes précédentes pour le **CSRWebApp** application.</span><span class="sxs-lookup"><span data-stu-id="67bd0-150">Repeat the previous two steps for the **CSRWebApp** application.</span></span>  
  
11. <span data-ttu-id="67bd0-151">Réinitialisez IIS pour que ces modifications prennent effet immédiatement.</span><span class="sxs-lookup"><span data-stu-id="67bd0-151">Reset IIS to make sure all these changes take effect immediately.</span></span> <span data-ttu-id="67bd0-152">Pour ce faire, exécutez **iisreset** à une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="67bd0-152">To do this, run **iisreset** at a command prompt.</span></span>  
  
12. <span data-ttu-id="67bd0-153">À l’invite de commandes, remplacer le dossier actuel par le répertoire % BTSSolutionsPath%\BPM\Scripts, tapez `CreateQueues.vbs`, puis appuyez sur ENTRÉE pour créer les files d’attente privées suivantes.</span><span class="sxs-lookup"><span data-stu-id="67bd0-153">At a command prompt, change the current folder to the %BTSSolutionsPath%\BPM\Scripts, type `CreateQueues.vbs`, and then press ENTER to create the following private queues.</span></span>  
  
    |<span data-ttu-id="67bd0-154">Nom</span><span class="sxs-lookup"><span data-stu-id="67bd0-154">Name</span></span>|<span data-ttu-id="67bd0-155">Transactionnelle</span><span class="sxs-lookup"><span data-stu-id="67bd0-155">Transactional</span></span>|<span data-ttu-id="67bd0-156">Protocole de transaction</span><span class="sxs-lookup"><span data-stu-id="67bd0-156">Transaction protocol</span></span>|  
    |----------|-------------------|--------------------------|  
    |<span data-ttu-id="67bd0-157">ToFacilitiesQ</span><span class="sxs-lookup"><span data-stu-id="67bd0-157">ToFacilitiesQ</span></span>|<span data-ttu-id="67bd0-158">Oui</span><span class="sxs-lookup"><span data-stu-id="67bd0-158">Yes</span></span>|<span data-ttu-id="67bd0-159">Natif</span><span class="sxs-lookup"><span data-stu-id="67bd0-159">Native</span></span>|  
    |<span data-ttu-id="67bd0-160">FromFacilitiesQ</span><span class="sxs-lookup"><span data-stu-id="67bd0-160">FromFacilitiesQ</span></span>|<span data-ttu-id="67bd0-161">Oui</span><span class="sxs-lookup"><span data-stu-id="67bd0-161">Yes</span></span>|<span data-ttu-id="67bd0-162">Natif</span><span class="sxs-lookup"><span data-stu-id="67bd0-162">Native</span></span>|  
    |<span data-ttu-id="67bd0-163">FromFixedOrdersQ</span><span class="sxs-lookup"><span data-stu-id="67bd0-163">FromFixedOrdersQ</span></span>|<span data-ttu-id="67bd0-164">Oui</span><span class="sxs-lookup"><span data-stu-id="67bd0-164">Yes</span></span>|<span data-ttu-id="67bd0-165">Natif</span><span class="sxs-lookup"><span data-stu-id="67bd0-165">Native</span></span>|  
    |<span data-ttu-id="67bd0-166">ToServicingSystemQ</span><span class="sxs-lookup"><span data-stu-id="67bd0-166">ToServicingSystemQ</span></span>|<span data-ttu-id="67bd0-167">Oui</span><span class="sxs-lookup"><span data-stu-id="67bd0-167">Yes</span></span>|<span data-ttu-id="67bd0-168">Natif</span><span class="sxs-lookup"><span data-stu-id="67bd0-168">Native</span></span>|  
    |<span data-ttu-id="67bd0-169">ToCSRSystemQ</span><span class="sxs-lookup"><span data-stu-id="67bd0-169">ToCSRSystemQ</span></span>|<span data-ttu-id="67bd0-170">Non</span><span class="sxs-lookup"><span data-stu-id="67bd0-170">No</span></span>|<span data-ttu-id="67bd0-171">HTTP</span><span class="sxs-lookup"><span data-stu-id="67bd0-171">HTTP</span></span>|  
    |<span data-ttu-id="67bd0-172">ToVendorSystemQ</span><span class="sxs-lookup"><span data-stu-id="67bd0-172">ToVendorSystemQ</span></span>|<span data-ttu-id="67bd0-173">Non</span><span class="sxs-lookup"><span data-stu-id="67bd0-173">No</span></span>|<span data-ttu-id="67bd0-174">HTTP</span><span class="sxs-lookup"><span data-stu-id="67bd0-174">HTTP</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="67bd0-175">Vous pouvez utiliser **gestion de l’ordinateur** -composant logiciel enfichable pour créer les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="67bd0-175">You can use **Computer Management** snap-in to create the queues.</span></span> <span data-ttu-id="67bd0-176">Pour plus d’informations sur la création d’une file d’attente privée, consultez la documentation de Message Queuing à [http://go.microsoft.com/fwlink/?LinkId=59264](http://go.microsoft.com/fwlink/?LinkId=59264).</span><span class="sxs-lookup"><span data-stu-id="67bd0-176">For more information about how to create a private queue, see the Message Queuing documentation at [http://go.microsoft.com/fwlink/?LinkId=59264](http://go.microsoft.com/fwlink/?LinkId=59264).</span></span> <span data-ttu-id="67bd0-177">Pour plus d’informations sur l’installation de MSMQ 3.0, consultez la documentation de Message Queuing à [http://go.microsoft.com/fwlink/?LinkId=59265](http://go.microsoft.com/fwlink/?LinkId=59265).</span><span class="sxs-lookup"><span data-stu-id="67bd0-177">For more information about how to install MSMQ 3.0, see the Message Queuing documentation at [http://go.microsoft.com/fwlink/?LinkId=59265](http://go.microsoft.com/fwlink/?LinkId=59265).</span></span>  
  
13. <span data-ttu-id="67bd0-178">À l’invite de commandes, remplacer le dossier actuel par le répertoire % BTSSolutionsPath%\BPM\Scripts, tapez `CreateTestDirectories.cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="67bd0-178">At a command prompt, change the current folder to the %BTSSolutionsPath%\BPM\Scripts, type `CreateTestDirectories.cmd`, and then press ENTER.</span></span>  
  
    -   <span data-ttu-id="67bd0-179">Les dossiers suivants sont créés dans le dossier %SystemDrive%\BPMTest</span><span class="sxs-lookup"><span data-stu-id="67bd0-179">The following folders are crated in %SystemDrive%\BPMTest folder</span></span>  
  
         <span data-ttu-id="67bd0-180">CSRResponse-DSP</span><span class="sxs-lookup"><span data-stu-id="67bd0-180">CSRResponse-DSP</span></span>  
  
         <span data-ttu-id="67bd0-181">VendorResponse-DSP</span><span class="sxs-lookup"><span data-stu-id="67bd0-181">VendorResponse-DSP</span></span>  
  
         <span data-ttu-id="67bd0-182">OrderErrors-SP</span><span class="sxs-lookup"><span data-stu-id="67bd0-182">OrderErrors-SP</span></span>  
  
         <span data-ttu-id="67bd0-183">ErrorResponse-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="67bd0-183">ErrorResponse-RP-TestRL</span></span>  
  
         <span data-ttu-id="67bd0-184">Facilities-SP</span><span class="sxs-lookup"><span data-stu-id="67bd0-184">Facilities-SP</span></span>  
  
         <span data-ttu-id="67bd0-185">Facilities-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="67bd0-185">Facilities-RP-TestRL</span></span>  
  
         <span data-ttu-id="67bd0-186">HistoryInsert-SP</span><span class="sxs-lookup"><span data-stu-id="67bd0-186">HistoryInsert-SP</span></span>  
  
         <span data-ttu-id="67bd0-187">HistoryUpdate-SP</span><span class="sxs-lookup"><span data-stu-id="67bd0-187">HistoryUpdate-SP</span></span>  
  
         <span data-ttu-id="67bd0-188">Order-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="67bd0-188">Order-RP-TestRL</span></span>  
  
         <span data-ttu-id="67bd0-189">ServicingSystem-SP</span><span class="sxs-lookup"><span data-stu-id="67bd0-189">ServicingSystem-SP</span></span>  
  
         <span data-ttu-id="67bd0-190">Vendor-RP-TestRL</span><span class="sxs-lookup"><span data-stu-id="67bd0-190">Vendor-RP-TestRL</span></span>  
  
         <span data-ttu-id="67bd0-191">BizTalkErrors-SP</span><span class="sxs-lookup"><span data-stu-id="67bd0-191">BizTalkErrors-SP</span></span>  
  
    -   <span data-ttu-id="67bd0-192">Le dossier FromVendor est créé dans le dossier %SystemDrive%\Inetpub\ftproot.</span><span class="sxs-lookup"><span data-stu-id="67bd0-192">FromVendor folder is created in the %SystemDrive%\Inetpub\ftproot folder.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-193">Si le système Windows n'est pas installé sur le lecteur C, vous devez remplacer %SystemDrive% par C:.</span><span class="sxs-lookup"><span data-stu-id="67bd0-193">If the Windows system is not installed on the C drive, you should replace %SystemDrive% with C:.</span></span> <span data-ttu-id="67bd0-194">Les noms de dossier doivent correspondre à l'adresse figurant dans les fichiers de liaison fournis par la solution de gestion des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="67bd0-194">You have to match the folder names to the address in the binding files that the BPM solution provides.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-195">Le compte de service BizTalk doit avoir l'autorisation de lecture/écriture sur le dossier FromVendor.</span><span class="sxs-lookup"><span data-stu-id="67bd0-195">The BizTalk service account must have read/write permission to the FromVendor folder.</span></span>  
  
##  <span data-ttu-id="67bd0-196"><a name="step5"></a>Installer la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-196"><a name="step5"></a> Install the Business Process Management Solution</span></span>  
  
#### <a name="to-install-the-business-process-management-solution"></a><span data-ttu-id="67bd0-197">Pour installer la solution de gestion des processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-197">To install the Business Process Management Solution</span></span>  
  
1.  <span data-ttu-id="67bd0-198">À l’invite de commandes, remplacer le dossier actif à % BTSSolutionsPath%\BPM, tapez `SetupBPM.bat`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="67bd0-198">At a command prompt, change the current folder to %BTSSolutionsPath%\BPM, type `SetupBPM.bat`, and then press ENTER.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="67bd0-199">Avant d’exécuter SetupBPM.bat, dans les fichiers **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.WSDL** et **%BTSInstallPath%/SDK/ Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**, remplacez toutes les instances de 8f8bbebbb3fb375a with XXXXXXXXXXXXXXXX.</span><span class="sxs-lookup"><span data-stu-id="67bd0-199">Before running SetupBPM.bat, in the files **%BTSInstallPath%/SDK/Scenarios/BPM/CSDWebApp/App_WebReferences/SouthridgeVideo_OrderBroker/OrderBrokerOrch_OrderPort.wsdl** and **%BTSInstallPath%/SDK/Scenarios/BPM/OrderBroker_Proxy/App_Code/OrderBrokerOrch_OrderPort.asmx.cs**, replace all instances of 8f8bbebbb3fb375a with XXXXXXXXXXXXXXXX.</span></span>  
  
     <span data-ttu-id="67bd0-200">La commande SetupBPM.bat effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="67bd0-200">The SetupBPM.bat performs the following tasks:</span></span>  
  
    1.  <span data-ttu-id="67bd0-201">création d'une clé de nom fort unique (SNK) pour signer les assemblys de la solution de gestion des processus d'entreprise ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-201">Creates a unique strong name key (SNK) for signing the assemblies of the BPM Solution.</span></span>  
  
    2.  <span data-ttu-id="67bd0-202">extraction du jeton de clé publique de la clé de nom fort ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-202">Extracts the public key token from the SNK.</span></span>  
  
    3.  <span data-ttu-id="67bd0-203">mise à jour des fichiers de liaison à l'aide du jeton de clé publique ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-203">Updates the binding files with the public token.</span></span>  
  
    4.  <span data-ttu-id="67bd0-204">création de la solution de gestion des processus d'entreprise et installation d'OpsAdapter ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-204">Builds the BPM solution, and installs OpsAdapter.</span></span>  
  
    5.  <span data-ttu-id="67bd0-205">création de SSOApplicationConfig dans le dossier %BTSSolutionsPath%\Common.</span><span class="sxs-lookup"><span data-stu-id="67bd0-205">Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.</span></span>  
  
2.  <span data-ttu-id="67bd0-206">Déployez les règles d'entreprise de Southridge Video à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise :</span><span class="sxs-lookup"><span data-stu-id="67bd0-206">Deploy the Southridge Video business rules using the Business Rule Engine Deployment Wizard:</span></span>  
  
    1.  <span data-ttu-id="67bd0-207">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Assistant de déploiement du moteur de règles d’entreprise**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-207">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rules Engine Deployment Wizard**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-208">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="67bd0-208">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="67bd0-209">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-209">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
    2.  <span data-ttu-id="67bd0-210">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-210">On the **Welcome** page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="67bd0-211">Sur le **la tâche de déploiement** page, sélectionnez **importer et publier la stratégie/vocabulaire à base de données à partir du fichier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-211">On the **Deployment Task** page, select **Import and publish Policy/Vocabulary to database from file**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="67bd0-212">Sur le **magasin de stratégies** page, conservez tous les autres paramètres par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-212">On the **Policy Store** page, keep all other default settings, and then click **Next**.</span></span>  
  
    5.  <span data-ttu-id="67bd0-213">Sur le **fichier du moteur de règles d’importation stratégie/vocabulaire** , cliquez sur **Parcourir**, sélectionnez le fichier DecodeAndValidateOrderRules.xml dans le dossier %BTSSolutionsPath%\BPM\Rules, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-213">On the **Import Rules Engine Policy/Vocabulary file** page, click **Browse**, select the DecodeAndValidateOrderRules.xml file in the %BTSSolutionsPath%\BPM\Rules folder, and then click **Next**.</span></span>  
  
    6.  <span data-ttu-id="67bd0-214">Sur le **prêt** , cliquez sur **suivant**, puis, dans le **l’importation de la stratégie/le vocabulaire** , cliquez sur **suivant**</span><span class="sxs-lookup"><span data-stu-id="67bd0-214">On the **Ready** page, click **Next**, and then on the **Importing Policy/Vocabulary** page, click **Next**</span></span>  
  
    7.  <span data-ttu-id="67bd0-215">Sur la page de fin, sélectionnez **réexécuter l’Assistant** pour ouvrir l’Assistant à nouveau, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-215">On the Completion page, select **Run the wizard again** to open the Wizard again, and then click **Finish**.</span></span>  
  
    8.  <span data-ttu-id="67bd0-216">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-216">On the **Welcome** page, click **Next**.</span></span>  
  
    9. <span data-ttu-id="67bd0-217">Sur le **la tâche de déploiement** page, sélectionnez **déployer la stratégie**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-217">On the **Deployment Task** page, select **DeployPolicy**, and then click **Next**.</span></span>  
  
    10. <span data-ttu-id="67bd0-218">Sur le **magasin de stratégies** page, conservez tous les autres paramètres par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-218">On the **Policy Store** page, keep all other default settings, and then click **Next**.</span></span>  
  
    11. <span data-ttu-id="67bd0-219">Sur le **déployer la stratégie de** page, sélectionnez **DecodeAndValidateOrder 1.0** dans les **stratégie du moteur de règles** liste déroulante, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="67bd0-219">On the **Deploy Policy** page, select **DecodeAndValidateOrder 1.0** in the **Rule Engine Policy** drop-down list, and then click **Next**.</span></span>  
  
    12. <span data-ttu-id="67bd0-220">Sur le **prêt** , cliquez sur **suivant**, puis, dans le **déploiement de la stratégie** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-220">On the **Ready** page, click **Next**, and then on the **Deploying Policy** page, click **Next**.</span></span>  
  
    13. <span data-ttu-id="67bd0-221">Dans la page de fin, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-221">On the Completion page, click **Finish**.</span></span>  
  
3.  <span data-ttu-id="67bd0-222">Si vous installez la solution de gestion des processus d'entreprise sur un ordinateur 64 bits,</span><span class="sxs-lookup"><span data-stu-id="67bd0-222">If you install the BPM solution on a 64-bit computer, then</span></span>  
  
    1.  <span data-ttu-id="67bd0-223">Ouvrez une invite de commandes 32 bits comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type `%SYSTEMROOT%\SYSWOW64\CMD.EXE`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="67bd0-223">Open a 32-bit command prompt as follow: Click **Start**, click **Run**, type `%SYSTEMROOT%\SYSWOW64\CMD.EXE`, and then press ENTER.</span></span>  
  
    2.  <span data-ttu-id="67bd0-224">À l'invite de commandes 32 bits, accédez au répertoire %BTSSolutionsPath%\BPM\Scripts.</span><span class="sxs-lookup"><span data-stu-id="67bd0-224">At the 32-bit command prompt, change the directory to the %BTSSolutionsPath%\BPM\Scripts folder.</span></span>  
  
    3.  <span data-ttu-id="67bd0-225">À l'aide du Bloc-notes, ouvrez CreateSouthridgeVideoApplication.cmd, puis remplacez « %CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe » par « %SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe ».</span><span class="sxs-lookup"><span data-stu-id="67bd0-225">Using Notepad, open the CreateSouthridgeVideoApplication.cmd, and then replace "%CommonProgramFiles%\Enterprise Single Sign-On\ssomanage.exe" with "%SystemDrive%\Program Files\Common Files\Enterprise Single Sign-On\ssomanage.exe".</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-226">À l'invite de commandes 32 bits, la variable %CommonProgramFiles est modifiée en « % ProgramFiles(x86) %\Common files ».</span><span class="sxs-lookup"><span data-stu-id="67bd0-226">At a 32-bit command prompt, the %CommonProgramFiles% variable is changed to "%ProgramFiles(x86)%\Common Files".</span></span> <span data-ttu-id="67bd0-227">L'utilitaire d'administration SSO étant installé dans %ProgramFiles% même sur un ordinateur 64 bits, vous devez modifier le chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="67bd0-227">Because the SSO administrative utility is installed in the %ProgramFiles% even on a 64-bit computer, you must fix the path.</span></span> <span data-ttu-id="67bd0-228">DeployBPM.cmd appelle CreateSouthridgeVideoApplication.cmd.</span><span class="sxs-lookup"><span data-stu-id="67bd0-228">The DeployBPM.cmd calls CreateSouthridgeVideoApplication.cmd.</span></span>  
  
    4.  <span data-ttu-id="67bd0-229">À l’invite de commandes 32 bits, tapez type `DeployBPM.cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="67bd0-229">At the 32-bit command prompt, type type `DeployBPM.cmd`, and then press ENTER.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="67bd0-230">DeployBPM.cmd doit être exécuté dans une invite de commandes 32 bits car cette commande inclut le script VB d'évaluation des objets x86 nécessitant la version x86 de cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="67bd0-230">The DeployBPM.cmd must be run at a 32-bit command prompt because it includes the VB Script accessing x86 objects that requires the x86 version of cscript.exe.</span></span>  
  
4.  <span data-ttu-id="67bd0-231">À l’invite de commandes, remplacer le dossier actif pour le répertoire % BTSSolutionsPath%\BPM\Scripts, tapez `DeployBPM.cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="67bd0-231">At a command prompt, change the current folder to %BTSSolutionsPath%\BPM\Scripts, type `DeployBPM.cmd`, and then press ENTER.</span></span> <span data-ttu-id="67bd0-232">DeployBPM.cmd effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="67bd0-232">The DeployBPM.cmd performs the following tasks:</span></span>  
  
    1.  <span data-ttu-id="67bd0-233">création d'applications BizTalk pour la solution de gestion des processus d'entreprise ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-233">Creates BizTalk Applications for the BPM Solution.</span></span>  
  
    2.  <span data-ttu-id="67bd0-234">ajout de références entre les applications ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-234">Adds references between the applications.</span></span>  
  
    3.  <span data-ttu-id="67bd0-235">importation des fichiers de liaison ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-235">Imports the binding files.</span></span>  
  
    4.  <span data-ttu-id="67bd0-236">déploiement des fichiers de définition BAM ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-236">Deploys the BAM definition files.</span></span>  
  
    5.  <span data-ttu-id="67bd0-237">enregistrement de la source d'événements SouthridgeVideo ;</span><span class="sxs-lookup"><span data-stu-id="67bd0-237">Registers the SouthridgeVideo event source.</span></span>  
  
    6.  <span data-ttu-id="67bd0-238">création d'une application associée à authentification unique (SSO) et enregistrement des valeurs de configuration dans l'application SSO.</span><span class="sxs-lookup"><span data-stu-id="67bd0-238">Creates a Single Sign-On (SSO) affiliated application, and saves configuration values to the SSO application.</span></span>  
  
5.  <span data-ttu-id="67bd0-239">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="67bd0-239">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
    1.  <span data-ttu-id="67bd0-240">Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, développez **BTSScn.BPM.OrderBrokerApp**, développez **emplacements de réception**, avec le bouton droit **fournisseur-RP-RL**, puis cliquez sur Propriétés.</span><span class="sxs-lookup"><span data-stu-id="67bd0-240">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand **BTSScn.BPM.OrderBrokerApp**, expand **Receive Locations**, right-click **Vendor-RP-RL**, and then click Properties.</span></span>  
  
    2.  <span data-ttu-id="67bd0-241">Sur le **propriétés** boîte de dialogue, cliquez sur **configurer**, puis entrez les valeurs dans le tableau suivant le **propriétés du Transport** boîte de dialogue :</span><span class="sxs-lookup"><span data-stu-id="67bd0-241">On the **Properties** dialog box, click **Configure**, and then enter values as the following table on the **Transport Properties** dialog box:</span></span>  
  
        |<span data-ttu-id="67bd0-242">Nom de la propriété</span><span class="sxs-lookup"><span data-stu-id="67bd0-242">Property Name</span></span>|<span data-ttu-id="67bd0-243">Valeur</span><span class="sxs-lookup"><span data-stu-id="67bd0-243">Value</span></span>|  
        |-------------------|-----------|  
        |<span data-ttu-id="67bd0-244">**Server**</span><span class="sxs-lookup"><span data-stu-id="67bd0-244">**Server**</span></span>|`localhost`|  
        |<span data-ttu-id="67bd0-245">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="67bd0-245">**User Name**</span></span>|<span data-ttu-id="67bd0-246">\<*Nom de compte de service BizTalk*></span><span class="sxs-lookup"><span data-stu-id="67bd0-246">\<*BizTalk service account name*></span></span>|  
        |<span data-ttu-id="67bd0-247">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="67bd0-247">**Password**</span></span>|<span data-ttu-id="67bd0-248">\<*Mot de passe du compte de service BizTalk*></span><span class="sxs-lookup"><span data-stu-id="67bd0-248">\<*BizTalk service account password*></span></span>|  
  
6.  <span data-ttu-id="67bd0-249">Exécutez la solution de gestion des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="67bd0-249">Run the BPM Solution.</span></span> <span data-ttu-id="67bd0-250">Pour plus d’informations sur l’exécution de la solution, consultez [l’exécution de la Solution de gestion des processus métier](../core/how-to-run-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="67bd0-250">For more information about running the solution, see [How to Run the Business Process Management Solution](../core/how-to-run-the-business-process-management-solution.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="67bd0-251">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="67bd0-251">Next Steps</span></span>  
 <span data-ttu-id="67bd0-252">Tester le fonctionnement de la Solution de gestion d’entreprise dans [l’exécution de la Solution de gestion des processus métier](../core/how-to-run-the-business-process-management-solution.md).</span><span class="sxs-lookup"><span data-stu-id="67bd0-252">You test how the Business Management Solution works in [How to Run the Business Process Management Solution](../core/how-to-run-the-business-process-management-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67bd0-253">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67bd0-253">See Also</span></span>  
 <span data-ttu-id="67bd0-254">[Avant d’installer la Solution gestion des processus d’entreprise](../core/before-installing-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="67bd0-254">[Before Installing the Business Process Management Solution](../core/before-installing-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="67bd0-255">Programme d’installation de développeur Machine pour la Solution gestion des processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="67bd0-255">Developer Machine Setup for the Business Process Management Solution</span></span>](../core/developer-machine-setup-for-the-business-process-management-solution.md)