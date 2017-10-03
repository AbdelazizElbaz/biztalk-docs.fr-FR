---
title: "Comment installer le Inline et les Versions d’adaptateur du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificate services
- service solution tutorial, affiliat applications [SSO]
- service solution tutorial, adapter version
- service solution tutorial, Web services
- service solution tutorial, definition files [BAM]
- service solution tutorial, COM+ applications
- service solution tutorial, virtual directories
- service solution tutorial, testing connectivity
- TI components
- MQSeries queues, creating
- service solution tutorial, deploying
- service solution tutorial, MQSeries adapters
- service solution tutorial, mainframe CICS applications
- service solution tutorial, certificate services
- service solution tutorial, back-end systems
- service solution tutorial, MQSeries queues
- service solution tutorial, remote environments
- certificates, creating requests
- service solution tutorial, starting service
- service solution tutorial, TI components
- service solution tutorial, inline version
- CICS application
- service solution tutorial, installing
- service solution tutorial, deleting stub version
- service solution tutorial, certificates
ms.assetid: 6050cfe9-4e94-4a55-8b24-fbcc74d9e8f4
caps.latest.revision: "97"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb7de8939037f9e7647c62c1164e3c3de3ab378c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution"></a><span data-ttu-id="8f698-102">Installation des versions Inline et d'adaptateur de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-102">How to Install the Inline and Adapter Versions of the Service Oriented Solution</span></span>
<span data-ttu-id="8f698-103">La procédure suivante décrit la préparation de votre ordinateur pour l'installation des versions d'adaptateur et Inline de la solution orientée services, puis l'installation de la solution sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-103">The following steps describe how to prepare the computer for installing the inline and adapter versions of the service oriented solution, and how to install the solution on this computer.</span></span>  
  
-   [<span data-ttu-id="8f698-104">Préparer l’ordinateur pour l’installation des versions d’adaptateur et inline de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-104">Prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>](#step1)  
  
-   [<span data-ttu-id="8f698-105">Supprimer la version stub de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-105">Remove the stub version of the Service Oriented Solution</span></span>](#step3)  
  
-   [<span data-ttu-id="8f698-106">Préparation des systèmes principaux pour la Solution orientée services pour accéder à</span><span class="sxs-lookup"><span data-stu-id="8f698-106">Prepare the back-end systems for the Service Oriented Solution to access</span></span>](#step5)  
  
-   [<span data-ttu-id="8f698-107">Configurer le serveur Web pour SSL Secure Socket Layers)</span><span class="sxs-lookup"><span data-stu-id="8f698-107">Configure the Web server for Secure Socket Layers (SSL)</span></span>](#step7)  
  
-   [<span data-ttu-id="8f698-108">Créer des services Web pour les systèmes back-end</span><span class="sxs-lookup"><span data-stu-id="8f698-108">Create the Web services for the back-end systems</span></span>](#step9)  
  
-   [<span data-ttu-id="8f698-109">Créer le composant TI pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-109">Create the TI component for the Service Oriented Solution</span></span>](#step11)  
  
-   [<span data-ttu-id="8f698-110">Créer les répertoires virtuels pour l’orchestration des services Web</span><span class="sxs-lookup"><span data-stu-id="8f698-110">Create the virtual directories for the orchestration Web services</span></span>](#step13)  
  
-   [<span data-ttu-id="8f698-111">Générez la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-111">Build the Service Oriented Solution</span></span>](#step15)  
  
-   [<span data-ttu-id="8f698-112">Créer des applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="8f698-112">Create the SSO affiliate applications</span></span>](#step17)  
  
-   [<span data-ttu-id="8f698-113">Déployer le fichier de définition BAM pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-113">Deploy the BAM definition file for the Service Oriented Solution</span></span>](#step19)  
  
-   [<span data-ttu-id="8f698-114">Déployer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-114">Deploy the Service Oriented Solution</span></span>](#step21)  
  
-   [<span data-ttu-id="8f698-115">Configurer le Services Web Pending Transactions stub lorsqu’un macroordinateur n’est pas disponible</span><span class="sxs-lookup"><span data-stu-id="8f698-115">Configure the stub Pending Transactions Web Services when a mainframe is not available</span></span>](#step23)  
  
-   [<span data-ttu-id="8f698-116">Démarrer le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="8f698-116">Start the Service Oriented Solution</span></span>](#step25)  
  
> [!NOTE]
>  <span data-ttu-id="8f698-117">Le service de solution orientée services se trouve dans le dossier \< *dossier d’Installation de BizTalk Server*> \SDK\Scenarios\SO.</span><span class="sxs-lookup"><span data-stu-id="8f698-117">The service oriented solution is located in the folder \<*BizTalk Server Installation Folder*>\SDK\Scenarios\SO.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f698-118">Si vous ne disposez pas d'un macroordinateur pour la solution, vous pouvez modifier la liaison du port de manière à utiliser le service Web Pending Transactions stub.</span><span class="sxs-lookup"><span data-stu-id="8f698-118">If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions.</span></span> <span data-ttu-id="8f698-119">Le service Web génère des transactions localement pour émuler celles du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-119">The Web service generates transactions locally to emulate the mainframe transactions.</span></span>  
  
##  <span data-ttu-id="8f698-120"><a name="step1"></a>Préparer l’ordinateur pour l’installation des versions d’adaptateur et inline de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-120"><a name="step1"></a> Prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>  
  
#### <a name="to-prepare-the-computer-for-installing-the-adapter-and-inline-versions-of-the-service-oriented-solution"></a><span data-ttu-id="8f698-121">Pour préparer l'ordinateur pour l'installation des versions d'adaptateur et Inline de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-121">To prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="8f698-122">Si vous avez installé Windows SharePoint Services, excluez la (racine) du Site Web par défaut à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **Outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="8f698-122">If you installed Windows SharePoint Services, exclude the (root) of the Default Web Site from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="8f698-123">Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-123">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="8f698-124">Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="8f698-124">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="8f698-125">Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-125">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="8f698-126">Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-126">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="8f698-127">Ouvrez une invite de commandes, puis exécutez IISReset.</span><span class="sxs-lookup"><span data-stu-id="8f698-127">At a command prompt, perform an IISReset.</span></span>  
  
2.  <span data-ttu-id="8f698-128">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="8f698-128">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
3.  <span data-ttu-id="8f698-129">Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-129">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
4.  <span data-ttu-id="8f698-130">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir la variable d'environnement %BTSSolutionsPath%.</span><span class="sxs-lookup"><span data-stu-id="8f698-130">At a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable.</span></span> <span data-ttu-id="8f698-131">Fermez ensuite l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="8f698-131">Then, exit the command prompt.</span></span>  
  
    -   <span data-ttu-id="8f698-132">setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span><span class="sxs-lookup"><span data-stu-id="8f698-132">setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8f698-133">Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="8f698-133">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8f698-134">Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span><span class="sxs-lookup"><span data-stu-id="8f698-134">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
##  <span data-ttu-id="8f698-135"><a name="step3"></a>Supprimer la version stub de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-135"><a name="step3"></a> Remove the stub version of the Service Oriented Solution</span></span>  
  
#### <a name="to-remove-the-stub-version-of-the-service-oriented-solution"></a><span data-ttu-id="8f698-136">Pour supprimer la version stub de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-136">To remove the stub version of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="8f698-137">Ouvrez le **Console d’Administration de BizTalk Server** comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur  **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8f698-137">Open the **BizTalk Server Administration Console** as follows: Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="8f698-138">Dans le **Console d’Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **BTSScn.SO.CustomerService**, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="8f698-138">In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, right-click **BTSScn.SO.CustomerService**, and then click **Stop**.</span></span> <span data-ttu-id="8f698-139">Dans le **arrêter l’Application** boîte de dialogue, sélectionnez **arrêt complet - arrêter les Instances**, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="8f698-139">In the **Stop Application** dialog box, select **Full Stop - Terminate Instances**, and then click **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-140">Il n'est pas nécessaire de supprimer la version stub pour installer les versions d'adaptateur et Inline.</span><span class="sxs-lookup"><span data-stu-id="8f698-140">You don't need to remove the stub version for installing the inline and adapter versions.</span></span> <span data-ttu-id="8f698-141">Si vous souhaitez rassembler toutes les versions, ignorez cette étape.</span><span class="sxs-lookup"><span data-stu-id="8f698-141">If you want to put all the versions together, you should skip this step.</span></span>  
  
3.  <span data-ttu-id="8f698-142">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8f698-142">Open a command prompt, type the following command, and then press ENTER.</span></span> <span data-ttu-id="8f698-143">Cette commande définit l'environnement d'exécution de scripts par défaut sur CScript.exe :</span><span class="sxs-lookup"><span data-stu-id="8f698-143">This command changes the default script host to CScript.exe:</span></span>  
  
    -   `cscript /H:CScript`  
  
4.  <span data-ttu-id="8f698-144">À l'invite de commandes, accédez au répertoire %BTSSolutonsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="8f698-144">At the command prompt, change the current directory to %BTSSolutonsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER:</span></span>  
  
    -   `UnEnlistStub.vbs`  
  
5.  <span data-ttu-id="8f698-145">À l'invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="8f698-145">At the command prompt, type the following command, and then press ENTER:</span></span>  
  
    -   `UndeployStub.vbs`  
  
6.  <span data-ttu-id="8f698-146">À l'invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8f698-146">At the command prompt, run the following command</span></span>  
  
     <span data-ttu-id="8f698-147">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span><span class="sxs-lookup"><span data-stu-id="8f698-147">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span></span>  
  
     <span data-ttu-id="8f698-148">Cette opération définit le chemin d'accès des utilitaires BAM.</span><span class="sxs-lookup"><span data-stu-id="8f698-148">This sets the path to find the BAM utilities.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-149">Si vous utilisez un ordinateur 64 bits, tapez `%ProgramFiles(x86)%` au lieu de `%ProgramFiles%`.</span><span class="sxs-lookup"><span data-stu-id="8f698-149">If you are using a 64-bit computer, type `%ProgramFiles(x86)%` instead of `%ProgramFiles%`.</span></span>  
  
7.  <span data-ttu-id="8f698-150">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\BAM, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8f698-150">At the command prompt, change the directory to %BTSSolutionsPath%\SO\BTSSoln\BAM, and then run the following command:</span></span>  
  
    -   `bm remove-all -DefinitionFile:ServiceLevelTracking.xml`  
  
8.  <span data-ttu-id="8f698-151">À l’invite de commandes, accédez au répertoire \< *unique Sign-On installer annuaire d’entreprise*>, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8f698-151">At the command prompt, change the directory to \<*Enterprise Single Sign-On Install Directory*>, and then run the following command:</span></span>  
  
    -   `ssomanage -tickets no no`  
  
9. <span data-ttu-id="8f698-152">À l'invite de commandes, exécutez la commande suivante pour supprimer l'application associée SSO WoodgroveBank.CustomerService :</span><span class="sxs-lookup"><span data-stu-id="8f698-152">At the command prompt, run the following command to delete the WoodgroveBank.CustomerService SSO Affiliated application:</span></span>  
  
    -   `ssomanage -deleteapp WoodgroveBank.CustomerService`  
  
10. <span data-ttu-id="8f698-153">À l'invite de commandes, exécutez les commandes suivantes pour supprimer les sites Web utilisés par la version stub.</span><span class="sxs-lookup"><span data-stu-id="8f698-153">At the command prompt, run the following commands to delete the Web sites used by the stub version.</span></span> <span data-ttu-id="8f698-154">Pour plus d’informations sur iisvdir.vbs, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span><span class="sxs-lookup"><span data-stu-id="8f698-154">For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span></span>  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker`  
  
11. <span data-ttu-id="8f698-155">Démarrez le Gestionnaire des Services Internet (IIS) comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **les outils d’Administration**, puis cliquez sur **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="8f698-155">Start Internet Information Services (IIS) Manager as follows: Click **Start**, point to **All Programs**, point to **Administration Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    -   <span data-ttu-id="8f698-156">Développez le **Pools d’applications**, cliquez sur le pool d’applications que vous avez créé pour les applications Web précédentes, cliquez sur **supprimer**, puis cliquez sur **OK** dans la confirmation boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8f698-156">Expand the **Application Pools**, right-click the application pool you crated for the previous Web applications, click **Delete**, and then click **OK** in the confirmation dialog box.</span></span>  
  
12. <span data-ttu-id="8f698-157">Cliquez sur **Démarrer**, pointez sur **le panneau de configuration**, cliquez sur **Ajout / Suppression de programmes**, puis désinstallez le Client IBM WebSphere MQ pour Windows.</span><span class="sxs-lookup"><span data-stu-id="8f698-157">Click **Start**, point to **Control Panel**, click **Add or Remove Programs**, and then uninstall the IBM WebSphere MQ Client for Windows.</span></span>  
  
13. <span data-ttu-id="8f698-158">Démarrer **invite de commandes Visual Studio** , puis exécutez la commande suivante pour supprimer le fichier amqmdnet.dll que vous avez installé pour la version stub.</span><span class="sxs-lookup"><span data-stu-id="8f698-158">Start **Visual Studio Command Prompt** and then run the following command to delete the amqmdnet.dll you installed for the stub version.</span></span>  
  
    -   `gacutil /u amqmdnet`  
  
##  <span data-ttu-id="8f698-159"><a name="step5"></a>Préparation des systèmes principaux pour la Solution orientée services pour accéder à</span><span class="sxs-lookup"><span data-stu-id="8f698-159"><a name="step5"></a> Prepare the back-end systems for the Service Oriented Solution to access</span></span>  
  
#### <a name="to-install-the-required-applications-for-the-back-end-systems-for-the-service-oriented-solution-to-access"></a><span data-ttu-id="8f698-160">Pour installer les applications requises par les systèmes principaux pour l'accès de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-160">To install the required applications for the back-end systems for the Service Oriented Solution to access</span></span>  
  
1.  <span data-ttu-id="8f698-161">Installez IBM WebSphere MQ pour Windows Version 5.3 Server sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="8f698-161">Install IBM WebSphere MQ for Windows Version 5.3 Server on the local computer.</span></span>  
  
    1.  <span data-ttu-id="8f698-162">Conservez tous les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f698-162">Keep all the default settings.</span></span> <span data-ttu-id="8f698-163">Configurer le **Configuration par défaut** à la fin de la **préparation de WebSphere MQ Assistant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-163">Set up the **Default Configuration** at the end of the **Prepare WebSphere MQ Wizard**.</span></span> <span data-ttu-id="8f698-164">Le Gestionnaire de file d’attente est nommé QM_\<*nom de votre ordinateur*>.</span><span class="sxs-lookup"><span data-stu-id="8f698-164">The queue manager is named as QM_\<*your computer name*>.</span></span>  
  
    2.  <span data-ttu-id="8f698-165">Installez le Fix Pack 10 (CSD10).</span><span class="sxs-lookup"><span data-stu-id="8f698-165">Install the Fix Pack 10 (CSD10).</span></span> <span data-ttu-id="8f698-166">Conservez tous les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f698-166">Keep all the default settings.</span></span>  
  
2.  <span data-ttu-id="8f698-167">Installez MQSeries Agent.</span><span class="sxs-lookup"><span data-stu-id="8f698-167">Install the MQSeries Agent.</span></span>  
  
    1.  <span data-ttu-id="8f698-168">Réexécutez le programme d'installation de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f698-168">Rerun the [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] setup program.</span></span>  
  
    2.  <span data-ttu-id="8f698-169">Sur le **Maintenance du programme** page, sélectionnez **modifier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-169">On the **Program Maintenance** page, select **Modify**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="8f698-170">Sur le **Installation des composants** page, développez le **des logiciels supplémentaires** nœud et sélectionnez **MQSeries Agent**.</span><span class="sxs-lookup"><span data-stu-id="8f698-170">On the **Component Installation** page, expand the **Additional Software** node, and then select **MQSeries Agent**.</span></span>  
  
    4.  <span data-ttu-id="8f698-171">Sur le **achèvement** , assurez-vous que **lancer l’Assistant de Configuration de BizTalk MQSeries Agent** n’est pas sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="8f698-171">On the **Completion** page, make sure that **Launch BizTalk MQSeries Agent Configuration Wizard** is not selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-172">Le **MQSeries Agent** case à cocher est activée uniquement après l’IBM WebSphere MQ pour Windows est installé.</span><span class="sxs-lookup"><span data-stu-id="8f698-172">The **MQSeries Agent** check box is activated only after the IBM WebSphere MQ for Windows is installed.</span></span>  
  
3.  <span data-ttu-id="8f698-173">Ouvrir un **invite de commandes Visual Studio**, remplacez le répertoire par le \< *répertoire d’Installation IBM MQSeries*> dossier \bin, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="8f698-173">Open a **Visual Studio Command Prompt**, change the directory to the \<*IBM MQSeries Installation Directory*>\bin folder, and then run the following command:</span></span>  
  
    -   `gacutil /i amqmdnet.dll`  
  
4.  <span data-ttu-id="8f698-174">Installez Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] si vous souhaitez installer Microsoft Host Integration Server 2004 pour accéder au macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-174">Install Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] if you want to install Microsoft Host Integration Server 2004 to access the mainframe.</span></span> <span data-ttu-id="8f698-175">Le programme d’installation, sur le **Options** page, sélectionnez **Visual c# .NET**, puis désactivez les autres cases à cocher des composants.</span><span class="sxs-lookup"><span data-stu-id="8f698-175">In the setup program, on the **Options** page, select **Visual C# .NET**, and then clear other components checkboxes.</span></span> <span data-ttu-id="8f698-176">Vous n’avez pas besoin d’installer les autres composants que le **Visual c# .NET**.</span><span class="sxs-lookup"><span data-stu-id="8f698-176">You don't need to install other components than the **Visual C# .NET**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-177">Le Concepteur TI inclus dans Host Integration Server 2004 requiert [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f698-177">The TI Designer in Host Integration Server 2004 requires [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].</span></span>  
  
5.  <span data-ttu-id="8f698-178">Installez et configurez Microsoft Host Integration Server 2004 si vous avez un macroordinateur accessible.</span><span class="sxs-lookup"><span data-stu-id="8f698-178">Install and configure Microsoft Host Integration Server 2004 if you have a mainframe to be accessed.</span></span> <span data-ttu-id="8f698-179">Conservez tous les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="8f698-179">Keep all the default settings.</span></span>  
  
#### <a name="to-create-the-mqseries-queues"></a><span data-ttu-id="8f698-180">Pour créer les files d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="8f698-180">To create the MQSeries queues</span></span>  
  
1.  <span data-ttu-id="8f698-181">Ouvrez WebSphere MQ Explorer, développez **gestionnaires de file d’attente**, puis développez le Gestionnaire de file d’attente dans laquelle vous souhaitez créer les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="8f698-181">Open the WebSphere MQ Explorer, expand **Queue Managers**, and then expand the queue manager in which you want to create the queues.</span></span> <span data-ttu-id="8f698-182">En règle générale, un gestionnaire de file d’attente est nommé QM_\<*nom de votre ordinateur*>.</span><span class="sxs-lookup"><span data-stu-id="8f698-182">Typically, a queue manager is named as QM_\<*your computer name*>.</span></span>  
  
2.  <span data-ttu-id="8f698-183">Dans WebSphere MQ Explorer, cliquez sur **les files d’attente**, pointez sur **nouveau**, cliquez sur **file d’attente locale**, puis créer les files d’attente locales suivantes pour la version de l’adaptateur de le solution :</span><span class="sxs-lookup"><span data-stu-id="8f698-183">In the WebSphere MQ Explorer, right-click **Queues**, point to **New**, click **Local Queue**, and then create the following local queues for the adapter version of the solution:</span></span>  
  
    -   <span data-ttu-id="8f698-184">AdapterSOAInputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-184">AdapterSOAInputQueue</span></span>  
  
    -   <span data-ttu-id="8f698-185">AdapterSOAOutputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-185">AdapterSOAOutputQueue</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-186">Les files d'attente peuvent partager un cluster MQSeries (facultatif).</span><span class="sxs-lookup"><span data-stu-id="8f698-186">The queues can share an MQSeries cluster, but they are not required to do so.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-187">Les noms des gestionnaires de file d'attente MQSeries et les noms des files d'attente respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="8f698-187">MQSeries queue manager names and queue names are case sensitive.</span></span>  
  
3.  <span data-ttu-id="8f698-188">Répétez l'étape précédente pour créer les files d'attente locales suivantes pour la version Inline :</span><span class="sxs-lookup"><span data-stu-id="8f698-188">Repeat the previous step to create the following local queues for the inline version:</span></span>  
  
    -   <span data-ttu-id="8f698-189">InlineSOAOutputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-189">InlineSOAOutputQueue</span></span>  
  
    -   <span data-ttu-id="8f698-190">InlineSOAInputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-190">InlineSOAInputQueue</span></span>  
  
4.  <span data-ttu-id="8f698-191">Répétez l'étape précédente pour créer les files d'attente locales suivantes pour le simulateur Payment Tracker</span><span class="sxs-lookup"><span data-stu-id="8f698-191">Repeat the previous step to create the following local queues for the Payment Tracker simulator.</span></span> <span data-ttu-id="8f698-192">(ce dispositif est utilisé à la fois dans la version d'adaptateur et dans la version Inline) :</span><span class="sxs-lookup"><span data-stu-id="8f698-192">(The Payment Tracker simulator is used in both the adapter and inline versions):</span></span>  
  
    -   <span data-ttu-id="8f698-193">LastPaymentsInputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-193">LastPaymentsInputQueue</span></span>  
  
    -   <span data-ttu-id="8f698-194">LastPaymentsOutputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-194">LastPaymentsOutputQueue</span></span>  
  
#### <a name="to-complete-configuration-of-the-mqseries-adapter"></a><span data-ttu-id="8f698-195">Pour terminer la configuration de l'adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="8f698-195">To complete configuration of the MQSeries adapter</span></span>  
  
1.  <span data-ttu-id="8f698-196">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Configuration de BizTalk MQSeries Agent**.</span><span class="sxs-lookup"><span data-stu-id="8f698-196">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk MQSeries Agent Configuration Wizard**.</span></span>  
  
2.  <span data-ttu-id="8f698-197">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-197">On the **Welcome** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="8f698-198">Sur le **identité de l’Application** page, sélectionnez **cet utilisateur**, puis entrez le nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="8f698-198">On the **Application Identity** page, select **This User**, and then enter the user name and password.</span></span> <span data-ttu-id="8f698-199">L'application COM+ pour MQSeries Agent est exécutée sous ce compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-199">The COM+ application for the MQSeries Agent will run under this user account.</span></span> <span data-ttu-id="8f698-200">Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-200">For this walkthrough, use the same user account that the BizTalk service is using.</span></span> <span data-ttu-id="8f698-201">S’il n’est pas, les comptes d’utilisateur pour les services BizTalk hébergeant l’adaptateur MQSeries doivent être ajoutés à la **CreatorOwner** rôle de l’application COM +.</span><span class="sxs-lookup"><span data-stu-id="8f698-201">If it is not, the user accounts for BizTalk services hosting the MQSeries Adapter must be added to the **CreatorOwner** role of the COM+ application.</span></span>  
  
4.  <span data-ttu-id="8f698-202">Cliquez sur **Oui** sur la **MQSConfigWiz** boîte de dialogue, si vous y êtes invité que le compte d’utilisateur que vous avez entré à l’étape précédente a des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-202">Click **Yes** on the **MQSConfigWiz** dialog box, if prompted that the user account that you entered in the previous step has the administrative privilege.</span></span>  
  
5.  <span data-ttu-id="8f698-203">Sur le **nom du rôle** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-203">On the **Name of Role** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="8f698-204">Sur le **création de l’Application MQSAgent COM +** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.</span><span class="sxs-lookup"><span data-stu-id="8f698-204">On the **Creating the MQSAgent COM+ Application** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="to-configure-the-mainframe-cics-application"></a><span data-ttu-id="8f698-205">Pour configurer l'application CICS du macroordinateur</span><span class="sxs-lookup"><span data-stu-id="8f698-205">To configure the mainframe CICS application</span></span>  
  
1.  <span data-ttu-id="8f698-206">À l'aide du Bloc-notes, ouvrez le fichier bizcbl.txt, ainsi que le fichier associé MainFrameProgramVTCS2Description.txt, dans le dossier %BTSSolutionsPath%\SO\MFAccess\HISTIComponent, puis passez en revue leur contenu.</span><span class="sxs-lookup"><span data-stu-id="8f698-206">Using Notepad, open the bizcbl.txt and its "copy book" (MainFrameProgramVTCS2Description.txt) in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then review the contents.</span></span>  
  
    -   <span data-ttu-id="8f698-207">Bizcbl.txt inclut la procédure COBOL qui renvoie les relevés de compte aléatoires d'après une entrée de numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="8f698-207">Bizcbl.txt includes the COBOL procedure returning the randomized account statements from account number input.</span></span>  
  
    -   <span data-ttu-id="8f698-208">Le fichier MainFrameProgramVTCS2Description.txt contient la COMMAREA qui décrit les informations des données d'entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="8f698-208">MainFrameProgramVTCS2Descriptoin.txt contains COMMAREA which describes the input and output data information.</span></span> <span data-ttu-id="8f698-209">La COMMAREA constitue un bloc de mémoire contiguë servant à échanger des données entre les programmes appelés et les programmes appelants.</span><span class="sxs-lookup"><span data-stu-id="8f698-209">COMMAREA is a block of contiguous memory used to pass data back and forth between called and calling programs.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-210">Vous pouvez également utiliser le fichier associé pour générer le fichier de métadonnées de l'intégrateur de transactions (TI) à l'aide du plug-in Concepteur TI de [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f698-210">You can also use the copy book to generate the Transaction Integrator (TI) metadata file using [!INCLUDE[vs2010](../includes/vs2010-md.md)] with the TI Designer plug-in.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-211">Bien que les étapes suivantes soient essentielles à la réussite du déploiement, elles ne sont généralement pas effectuées par un développeur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8f698-211">Although the following steps are crucial to the successful deployment, they are not usually performed by the BizTalk Server developer.</span></span> <span data-ttu-id="8f698-212">Il revient au personnel chargé de l'administration du macroordinateur de configurer correctement l'environnement du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-212">You must rely on the mainframe personnel to properly configure the mainframe environment.</span></span> <span data-ttu-id="8f698-213">Les logiciels requis dans le cadre de cette procédure pas à pas sont généralement installés dans la plupart des environnements de macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-213">The software required for this walkthrough is usually installed in the most mainframe environments.</span></span> <span data-ttu-id="8f698-214">Pour plus d’informations sur l’environnement de système d’exploitation minimale macroordinateur, consultez la documentation de Host Integration Server.</span><span class="sxs-lookup"><span data-stu-id="8f698-214">For more information about the minimum mainframe operating system environment, see the Host Integration Server documentation.</span></span>  
  
2.  <span data-ttu-id="8f698-215">Copiez le code COBOL sur l'ordinateur hôte via FTP par exemple.</span><span class="sxs-lookup"><span data-stu-id="8f698-215">Copy the COBOL code to the host by method like FTP.</span></span>  
  
3.  <span data-ttu-id="8f698-216">Compilez le code COBOL et le fichier associé.</span><span class="sxs-lookup"><span data-stu-id="8f698-216">Compile the COBOL code and copy book.</span></span> <span data-ttu-id="8f698-217">Le code suivant illustre un exemple de langage JCL (Job Control Language) utilisé par le compilateur COBOL.</span><span class="sxs-lookup"><span data-stu-id="8f698-217">The following code shows a sample of Job Control Language (JCL) for the COBOL compiler.</span></span>  
  
    ```  
    //COB      EXEC PGM=IGYCRCTL,  
    //            PARM=&COBPARM,  
    //            REGION=&REG  
    //STEPLIB  DD DSN=&COMPINDX..SIGYCOMP,DISP=SHR  
    //SYSLIB   DD DSN=&INDEX..SDFHCOB,DISP=SHR  
    //         DD DSN=&INDEX..SDFHMAC,DISP=SHR  
    //         DD DSN=&HLQ..&COMP..COBCOPY,DISP=SHR  
    //SYSPRINT DD SYSOUT=&OUTC  
    //*SYSPRINT DD DSN=&&INPUT,DISP=(,PASS),UNIT=SYSDA,  
    //*         SPACE=(TRK,(100,50)),  
    //*         DCB=(DSORG=PS,LRECL=121,BLKSIZE=2420,RECFM=FBA)  
    //SYSIN    DD DSN=&&SYSCIN,DISP=(OLD,DELETE)  
    //SYSLIN   DD DSN=&&LOADSET,  
    //            DISP=(MOD,PASS),  
    //            UNIT=&WORK,  
    //            SPACE=(80,(250,100))  
    //SYSUT1   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT2   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT3   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT4   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT5   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT6   DD UNIT=&WORK,SPACE=(460,(350,150))  
    //SYSUT7   DD UNIT=&WORK,SPACE=(460,(350,150))  
    ```  
  
4.  <span data-ttu-id="8f698-218">Éditez les liens de la source compilée pour créer l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="8f698-218">Link edit the compiled source to create the executable.</span></span> <span data-ttu-id="8f698-219">Le code suivant montre un exemple de langage JCL pour l'édition de liens COBOL.</span><span class="sxs-lookup"><span data-stu-id="8f698-219">The following code shows a sample of JCL for COBOL link edit.</span></span>  
  
    ```  
    //LKED     EXEC PGM=IEWL,REGION=&REG,  
    //            PARM=&LNKPARM,COND=(5,LT,COB)  
    //SYSLIB   DD DSN=&INDEX..SDFHLOAD,DISP=SHR  
    //         DD DSN=CEE.SCEELKED,DISP=SHR  
    //         DD DSN=&TCPINDX..SEZATCP,DISP=SHR  
    //SYSLMOD  DD DSN=&LMINDX..&COMP..LOADLIB,DISP=SHR  
    //SYSUT1   DD UNIT=&WORK,  
    //            DCB=BLKSIZE=1024,  
    //            SPACE=(1024,(200,20))  
    //SYSPRINT DD SYSOUT=&OUTC  
    //SYSLIN   DD DSN=&&LOADSET,DISP=(OLD,DELETE)  
    //         DD DSN=&&COPYLINK,DISP=(OLD,DELETE)  
    ```  
  
5.  <span data-ttu-id="8f698-220">Configurez l'application de macroordinateur CICS.</span><span class="sxs-lookup"><span data-stu-id="8f698-220">Configure the CICS mainframe application.</span></span>  
  
    -   <span data-ttu-id="8f698-221">Au cours de cette étape, le programmateur système du macroordinateur ou le développeur CICS doit installer les définitions de ressource relatives au service TCP/IP, aux sessions, aux connexions, aux transactions et aux programmes.</span><span class="sxs-lookup"><span data-stu-id="8f698-221">In this step, the mainframe systems programmer or CICS developer must install TCPIPSERVICE, Session, Connection, Transaction, and Program resource definitions.</span></span>  
  
    -   <span data-ttu-id="8f698-222">Consultez les administrateurs du macroordinateur pour obtenir l'adresse IP, le numéro de port et le nom de lien au programme auxquels accéder.</span><span class="sxs-lookup"><span data-stu-id="8f698-222">You should consult with mainframe administrators to get an IP address, port number, and a Link to Program name that you can access.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8f698-223">Cette procédure pas à pas implique que le macroordinateur exploite un serveur d'applications CICS et que le modèle de programmation de la transaction soit TCP/IP (lien ELM [Enhanced Listener Mode]).</span><span class="sxs-lookup"><span data-stu-id="8f698-223">This walkthrough assumes that the mainframe uses a CICS application server and that the programming model for the transaction is TCP/IP (Enhanced Listener Mode (ELM) Link).</span></span>  
  
##  <span data-ttu-id="8f698-224"><a name="step7"></a>Configurer le serveur Web pour SSL Secure Socket Layers)</span><span class="sxs-lookup"><span data-stu-id="8f698-224"><a name="step7"></a> Configure the Web server for Secure Socket Layers (SSL)</span></span>  
  
#### <a name="to-install-certificate-services"></a><span data-ttu-id="8f698-225">Pour installer les services de certificats</span><span class="sxs-lookup"><span data-stu-id="8f698-225">To install Certificate Services</span></span>  
  
1.  <span data-ttu-id="8f698-226">Cliquez sur **Démarrer**, pointez sur **le panneau de configuration**, puis cliquez sur **Ajout / Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="8f698-226">Click **Start**, point to **Control Panel**, and then click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="8f698-227">Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="8f698-227">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="8f698-228">Dans le **Assistant Composants de Windows**, sélectionnez le **les Services de certificats**, cliquez sur **suivant**, puis suivez l’à l’écran des instructions pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="8f698-228">In the **Windows Components Wizard**, select the **Certificate Services**, click **Next**, and then follow the on-screen instructions to complete the installation.</span></span>  
  
#### <a name="to-create-a-certificate-request"></a><span data-ttu-id="8f698-229">Pour créer une demande de certificat</span><span class="sxs-lookup"><span data-stu-id="8f698-229">To create a certificate request</span></span>  
  
1.  <span data-ttu-id="8f698-230">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, cliquez sur **propriétés** , cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **certificat de serveur**.</span><span class="sxs-lookup"><span data-stu-id="8f698-230">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, click **Properties**, click the **Directory Security** tab, and then click **Server Certificate**.</span></span>  
  
2.  <span data-ttu-id="8f698-231">Sur le **Bienvenue** page de la **Assistant certificat de serveur Web**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-231">On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="8f698-232">Sur le **certificat de Service** page, sélectionnez **créer un nouveau certificat**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-232">On the **Service Certificate** page, select **Create a new certificate**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="8f698-233">Sur le **demande ultérieure ou immédiate** , cliquez sur **préparer la demande maintenant, mais l’envoyer ultérieurement**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-233">On the **Delayed or Immediate Request** page, click **Prepare the request now, but send it later**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="8f698-234">Sur le **nom et les paramètres de sécurité** page, conservez tous les paramètres par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-234">On the **Name and Security Settings** page, keep all the default settings, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="8f698-235">Sur le **informations de l’organisation** page, tapez votre organisation et noms de l’unité d’organisation, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-235">On the **Organization Information** page, type your company's organization and organizational unit names, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="8f698-236">Sur le **nom commun de votre Site** , tapez le nom de votre ordinateur dans le **nom commun** zone, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-236">On the **Your Site's Common Name** page, type your computer name in the **Common name** box, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="8f698-237">Sur le **informations géographiques** page, remplir vos informations géographiques, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-237">On the **Geographical Information** page, fill out your geographical information, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="8f698-238">Sur le **nom du fichier de demande de certificat** , tapez `c:\certreq.txt` dans les **nom de fichier** zone, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-238">On the **Certificate Request File Name** page, type `c:\certreq.txt` in the **File name** box, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="8f698-239">Sur le **résumé du fichier de demande** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.</span><span class="sxs-lookup"><span data-stu-id="8f698-239">On the **Request File Summary** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="to-submit-the-certificate-request-to-the-certification-authority"></a><span data-ttu-id="8f698-240">Pour transmettre la demande de certificat à l'Autorité de certification</span><span class="sxs-lookup"><span data-stu-id="8f698-240">To submit the certificate request to the Certification Authority</span></span>  
  
1.  <span data-ttu-id="8f698-241">Dans Internet Explorer, dans la zone Adresse, tapez `http://localhost/certsrvt`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8f698-241">In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="8f698-242">Sur le **Bienvenue** , cliquez sur **demander un certificat**, puis cliquez sur **demande de certificat avancée** sur la **demander un certificat** page.</span><span class="sxs-lookup"><span data-stu-id="8f698-242">On the **Welcome** page, click **Request a Certificate**, and then click **Advanced certificate request** on the **Request a Certificate** page.</span></span>  
  
3.  <span data-ttu-id="8f698-243">Sur le **demande de certificat avancée** , cliquez sur **soumettre une demande de certificat à l’aide de base64 encodé PKCS #10 ou une demande de renouvellement à l’aide d’un fichier de PKCS #7 codé en base64**.</span><span class="sxs-lookup"><span data-stu-id="8f698-243">On the **Advanced Certificate Request** page, click **Submit a certificate request using a base64 encoded PKCS #10 file or a renewal request using a base64 encoded PKCS #7 file**.</span></span>  
  
4.  <span data-ttu-id="8f698-244">Copiez le texte à partir de la c:\certreq.txt que vous avez créé dans la procédure « pour créer d’une demande de certificat », collez-le dans le **demande enregistrée** zone sur le **soumettre une demande de certificat ou une demande de renouvellement** page, puis cliquez sur **Submit**.</span><span class="sxs-lookup"><span data-stu-id="8f698-244">Copy all the text from the c:\certreq.txt that you created in the procedure "To create a certificate request", paste it to the **Saved Request** box on the **Submit a Certificate Request or Renewal Request** page, and then click **Submit**.</span></span>  
  
#### <a name="to-issue-a-certificate-using-certification-authority-management-tool"></a><span data-ttu-id="8f698-245">Pour émettre un certificat à l'aide de l'outil de gestion de l'Autorité de certification</span><span class="sxs-lookup"><span data-stu-id="8f698-245">To issue a certificate using Certification Authority management tool</span></span>  
  
1.  <span data-ttu-id="8f698-246">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **autorité de Certification**.</span><span class="sxs-lookup"><span data-stu-id="8f698-246">Click **Start**, point to **Administrative Tools**, and then click **Certification Authority**.</span></span>  
  
2.  <span data-ttu-id="8f698-247">Dans le **autorité de Certification** de la console, développez le nom de votre autorité de certification, le **demande en attente**, avec le bouton droit de la demande de certificat que vous avez envoyé à l’étape précédente, le point pour **toutes les tâches**, puis cliquez sur **problème**.</span><span class="sxs-lookup"><span data-stu-id="8f698-247">In the **Certification Authority** console, expand your certification authority's name, expand the **Pending Request**, right-click the certificate request that you submitted in the previous step, point to **All Tasks**, and then click **Issue**.</span></span>  
  
3.  <span data-ttu-id="8f698-248">Fermer le **autorité de Certification** console.</span><span class="sxs-lookup"><span data-stu-id="8f698-248">Close the **Certification Authority** console.</span></span>  
  
#### <a name="to-download-the-certificate-to-the-web-server"></a><span data-ttu-id="8f698-249">Pour télécharger le certificat sur le serveur Web</span><span class="sxs-lookup"><span data-stu-id="8f698-249">To download the certificate to the Web server</span></span>  
  
1.  <span data-ttu-id="8f698-250">Dans Internet Explorer, dans la zone Adresse, tapez `http://localhost/certsrvt`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8f698-250">In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="8f698-251">Sur le **Bienvenue** , cliquez sur **afficher l’état d’une demande de certificat en attente**.</span><span class="sxs-lookup"><span data-stu-id="8f698-251">On the **Welcome** page, click **View the status of a pending certificate request**.</span></span>  
  
3.  <span data-ttu-id="8f698-252">Sur le **afficher l’état d’une demande de certificat en attente** , cliquez sur le certificat **demande** que vous avez créé dans la procédure « pour créer une demande de certificat ».</span><span class="sxs-lookup"><span data-stu-id="8f698-252">On the **View the Status of a Pending Certificate Request** page, click the certificate **request** that you created in the procedure "To create a certificate request".</span></span>  
  
4.  <span data-ttu-id="8f698-253">Sur le **délivré** page, sélectionnez un des schémas d’encodage, puis cliquez sur **télécharger le certificat**.</span><span class="sxs-lookup"><span data-stu-id="8f698-253">On the **Certificate Issued** page, select either of the encoding schemes, and then click **Download certificate**.</span></span>  
  
5.  <span data-ttu-id="8f698-254">Sur le **avertissement de sécurité** boîte de dialogue, cliquez sur **enregistrer**, puis enregistrez le certificat sous c:\certnew.cer.</span><span class="sxs-lookup"><span data-stu-id="8f698-254">On the **Security Warning** dialog box, click **Save**, and then save the certificate as c:\certnew.cer.</span></span>  
  
#### <a name="to-install-the-certificate-to-the-web-server"></a><span data-ttu-id="8f698-255">Pour installer le certificat sur le serveur Web</span><span class="sxs-lookup"><span data-stu-id="8f698-255">To install the certificate to the Web server</span></span>  
  
1.  <span data-ttu-id="8f698-256">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut** pour lequel vous avez créé la demande de certificat, puis Cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-256">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site** for which you created the certificate request, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="8f698-257">Sur le **propriétés** boîte de dialogue, cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **certificat de serveur**.</span><span class="sxs-lookup"><span data-stu-id="8f698-257">On the **Properties** dialog box, click the **Directory Security** tab, and then click **Server Certificate**.</span></span>  
  
3.  <span data-ttu-id="8f698-258">Sur le **Bienvenue** page de la **Assistant certificat de serveur Web**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-258">On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="8f698-259">Sur le **demande de certificat en attente** page, sélectionnez **traiter la demande en attente et installer le certificat**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-259">On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="8f698-260">Sur le **traiter une demande en attente** , tapez `c:\certnew.cer` dans les **chemin d’accès et nom de fichier** zone de texte, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-260">On the **Process a Pending Request** page, type `c:\certnew.cer` in the **Path and file name** text box, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="8f698-261">Cliquez sur **suivant** sur la **Port SSL** , cliquez sur **suivant** sur la **résumé du certificat** page, puis cliquez sur **Terminer** sur la **Confirmation** page.</span><span class="sxs-lookup"><span data-stu-id="8f698-261">Click **Next** on the **SSL Port** page, click **Next** on the **Certificate Summery** page, and then click **Finish** on the **Confirmation** page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-262">Au cours de cette procédure pas à pas, il n'est pas nécessaire d'installer le certificat de serveur dans le magasin d'autorités de certification de racine de confiance de l'ordinateur local car les services de certificats et le serveur Web sont installés sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-262">In this walkthrough you don't need to install the server certificate to the Trusted Root Certification Authorities store on the local computer because both Certificate Services and Web server are installed on the same computer.</span></span>  
  
##  <span data-ttu-id="8f698-263"><a name="step9"></a>Créer des services Web pour les systèmes back-end</span><span class="sxs-lookup"><span data-stu-id="8f698-263"><a name="step9"></a> Create the Web services for the back-end systems</span></span>  
  
#### <a name="to-create-a-new-iis-application-pool-for-the-pending-transaction-web-services"></a><span data-ttu-id="8f698-264">Pour créer un pool d'applications IIS pour les services Web Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="8f698-264">To create a new IIS application pool for the Pending Transaction Web services</span></span>  
  
1.  <span data-ttu-id="8f698-265">Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Poold’applications**.</span><span class="sxs-lookup"><span data-stu-id="8f698-265">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-266">La solution orientée services accède au macroordinateur via ce service Web.</span><span class="sxs-lookup"><span data-stu-id="8f698-266">The service oriented solution accesses the mainframe through this Web service.</span></span>  
  
2.  <span data-ttu-id="8f698-267">Sur le **Ajouter nouveau Pool d’applications** boîte de dialogue, entrez le **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f698-267">On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="8f698-268">Dans le **Gestionnaire des Services Internet (IIS)**, cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-268">In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="8f698-269">Sur le **propriétés** , cliquez sur le **identité** onglet, sélectionnez **Configurable**, entrez la **nom d’utilisateur** et **mot de passe** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f698-269">On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**.</span></span> <span data-ttu-id="8f698-270">Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-270">For this walkthrough, use the same user account that the BizTalk service is using.</span></span>  
  
#### <a name="to-create-the-pendingtransactions-web-service-for-runtime"></a><span data-ttu-id="8f698-271">Pour créer le service Web PendingTransactions à des fins d'exécution</span><span class="sxs-lookup"><span data-stu-id="8f698-271">To create the PendingTransactions Web service for runtime</span></span>  
  
1.  <span data-ttu-id="8f698-272">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-272">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-273">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :</span><span class="sxs-lookup"><span data-stu-id="8f698-273">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="8f698-274">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-274">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions</span></span>  
  
     <span data-ttu-id="8f698-275">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\MFAccess\PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-275">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span></span>  
  
     <span data-ttu-id="8f698-276">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-276">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="8f698-277">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-277">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="8f698-278">Dans le **sécurité du répertoire** , cliquez sur **modifier** modifier **d’authentification et contrôle d’accès**.</span><span class="sxs-lookup"><span data-stu-id="8f698-278">In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**.</span></span> <span data-ttu-id="8f698-279">Sélectionnez **l’authentification de base (mot de passe est envoyé en texte clair)**et désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="8f698-279">Select **Basic authentication (password is sent in clear text)**, and clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="8f698-280">Cliquez sur **OK** pour fermer la **les méthodes d’authentification** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8f698-280">Click **OK** to close the **Authentication Methods** dialog box.</span></span>  
  
    2.  <span data-ttu-id="8f698-281">Dans le **sécurité du répertoire** , cliquez sur **modifier** sous le **une Communication sécurisée** zone de groupe, puis vérifiez **requérir un canal sécurisé (SSL)**dans les **Communications sécurisées** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8f698-281">In the **Directory Security** tab, click **Edit** under the **Secure Communication** group box, and then check **Require secure channel (SSL)** in the **Secure Communications** dialog box.</span></span>  
  
    3.  <span data-ttu-id="8f698-282">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** au pool d’applications que vous avez créé dans la procédure « pour créer un nouveau pool d’applications IIS pour les services Web Pending transactions ».</span><span class="sxs-lookup"><span data-stu-id="8f698-282">In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
#### <a name="to-create-the-pendingtransactions-web-service-for-development-environment"></a><span data-ttu-id="8f698-283">Pour créer le service Web PendingTransactions pour l'environnement de développement</span><span class="sxs-lookup"><span data-stu-id="8f698-283">To create the PendingTransactions Web service for development environment</span></span>  
  
1.  <span data-ttu-id="8f698-284">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-284">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-285">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :</span><span class="sxs-lookup"><span data-stu-id="8f698-285">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="8f698-286">Alias = PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-286">Alias = PendingTransactions</span></span>  
  
     <span data-ttu-id="8f698-287">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\MFAccess\PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-287">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span></span>  
  
     <span data-ttu-id="8f698-288">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-288">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="8f698-289">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, cliquez sur PendingTransactions, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-289">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click PendingTransactions, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="8f698-290">Dans le **sécurité du répertoire** , cliquez sur **modifier** modifier **d’authentification et contrôle d’accès**.</span><span class="sxs-lookup"><span data-stu-id="8f698-290">In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**.</span></span> <span data-ttu-id="8f698-291">Sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="8f698-291">Select **Enable anonymous access**.</span></span> <span data-ttu-id="8f698-292">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8f698-292">Click **OK** to exit.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8f698-293">L'application Web PendingTransactions pour l'environnement de développement sera utilisée par [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f698-293">The PendingTransactions Web application for development environment will be used by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="8f698-294">Cette application Web n'est pas requise pour l'environnement de production.</span><span class="sxs-lookup"><span data-stu-id="8f698-294">You don't need this Web application for production environment.</span></span>  
  
    2.  <span data-ttu-id="8f698-295">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** au pool d’applications que vous avez créé dans la procédure « pour créer un nouveau pool d’applications IIS pour les services Web Pending transactions ».</span><span class="sxs-lookup"><span data-stu-id="8f698-295">In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
#### <a name="to-create-the-stub-sap-web-service"></a><span data-ttu-id="8f698-296">Pour créer le service Web SAP stub</span><span class="sxs-lookup"><span data-stu-id="8f698-296">To create the Stub SAP Web service</span></span>  
  
1.  <span data-ttu-id="8f698-297">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-297">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-298">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :</span><span class="sxs-lookup"><span data-stu-id="8f698-298">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="8f698-299">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span><span class="sxs-lookup"><span data-stu-id="8f698-299">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span></span>  
  
     <span data-ttu-id="8f698-300">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-300">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span></span>  
  
     <span data-ttu-id="8f698-301">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-301">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="8f698-302">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f698-302">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="8f698-303">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool*> que vous avez créé dans la procédure « pour créer une nouvelle application IIS pool pour les services Web Pending transactions ».</span><span class="sxs-lookup"><span data-stu-id="8f698-303">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
    2.  <span data-ttu-id="8f698-304">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="8f698-304">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="8f698-305">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8f698-305">Click **OK** to exit.</span></span>  
  
##  <span data-ttu-id="8f698-306"><a name="step11"></a>Créer le composant TI pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-306"><a name="step11"></a> Create the TI component for the Service Oriented Solution</span></span>  
  
#### <a name="to-create-a-com-application-for-the-ti-component"></a><span data-ttu-id="8f698-307">Pour créer une application COM+ pour le composant TI</span><span class="sxs-lookup"><span data-stu-id="8f698-307">To create a COM+ application for the TI component</span></span>  
  
1.  <span data-ttu-id="8f698-308">Ouvrez une invite de commandes, puis exécutez %systemroot%\system32\com\comexp.msc.</span><span class="sxs-lookup"><span data-stu-id="8f698-308">At a command prompt, run %systemroot%\system32\com\comexp.msc.</span></span>  
  
2.  <span data-ttu-id="8f698-309">Dans **Services de composants** de la console, développez **Services de composants**, développez **ordinateurs**, développez **poste**, avec le bouton droit  **L’Application COM +**, pointez sur **nouveau**, puis cliquez sur **Application**.</span><span class="sxs-lookup"><span data-stu-id="8f698-309">In **Component Services** console, expand **Component Services**, expand **Computers**, expand **My Computer**, right-click **COM+ Application**, point to **New**, and then click **Application**.</span></span>  
  
    1.  <span data-ttu-id="8f698-310">Sur le **Bienvenue** , cliquez sur **suivant**, puis cliquez sur **créer une application vide** sur la **installer ou créer une nouvelle Application** page.</span><span class="sxs-lookup"><span data-stu-id="8f698-310">On the **Welcome** page, click **Next**, and then click **Create an empty application** on the **Install or Create a New Application** page.</span></span>  
  
    2.  <span data-ttu-id="8f698-311">Type `BTSScn SO TI Component` dans les **Entrez un nom pour la nouvelle application** boîte, sélectionnez **application serveur** en tant que **type d’Activation**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-311">Type `BTSScn SO TI Component` in the **Enter a name for the new application** box, select **Server application** as **Activation type**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="8f698-312">Dans le **compte** zone de groupe de la **définir l’identité Application** page, sélectionnez **cet utilisateur**, puis tapez le nom d’utilisateur et un mot de passe dans la **utilisateur**et **mot de passe** cases.</span><span class="sxs-lookup"><span data-stu-id="8f698-312">In the **Account** group box of the **Set Application Identity** page, select **This user**, and then type the user name and password in the **User** and **Password** boxes.</span></span> <span data-ttu-id="8f698-313">La nouvelle application COM+ sera exécutée sous ce compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-313">The new COM+ application will run under this user account.</span></span> <span data-ttu-id="8f698-314">Celui-ci doit appartenir au groupe d'utilisateurs HIS Runtime locaux.</span><span class="sxs-lookup"><span data-stu-id="8f698-314">This user account must be a member of local HIS Runtime Users group.</span></span> <span data-ttu-id="8f698-315">Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-315">For this walkthrough, use the same user account that the BizTalk service is using.</span></span>  
  
    4.  <span data-ttu-id="8f698-316">Sur le **ajouter des rôles d’Application** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-316">On the **Add Application Roles** page, click **Next**.</span></span>  
  
    5.  <span data-ttu-id="8f698-317">Sur le **ajouter des utilisateurs aux rôles** page, développez **CreatorOwner**, cliquez sur **utilisateurs**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8f698-317">On the **Add Users to Roles** page, expand **CreatorOwner**, click **Users**, and then click **Add**.</span></span>  
  
    6.  <span data-ttu-id="8f698-318">Sur le **sélectionner des utilisateurs ou groupes** boîte de dialogue, sélectionnez un compte d’utilisateur qui sera utilisé pour accéder au macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-318">On the **Select Users or Groups** dialog box, select a user account that will be used for accessing the mainframe.</span></span> <span data-ttu-id="8f698-319">Dans le cadre de cette procédure pas à pas, ajoutez le compte local UserID.</span><span class="sxs-lookup"><span data-stu-id="8f698-319">For this walkthrough, add UserID local account.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8f698-320">Pour accéder à la transaction CICS via le composant TI, vous pouvez utiliser l'application COM+ ou l'application Web hébergeant le composant d'accès à distance .NET.</span><span class="sxs-lookup"><span data-stu-id="8f698-320">To access the CICS transaction through the TI component, you can use the COM+ application or the Web application hosting the .NET Remoting component.</span></span> <span data-ttu-id="8f698-321">Cette procédure pas à pas utilise l'application COM+ et COM Interop pour permettre aux composants TI d'accéder au macroordinateur à des fins d'amélioration des performances.</span><span class="sxs-lookup"><span data-stu-id="8f698-321">This walkthrough uses the COM+ application and COM Interop for TI components to access the mainframe to improve performance.</span></span>  
  
    7.  <span data-ttu-id="8f698-322">Sur le **achèvement** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8f698-322">On the **Completion** page, click **Finish**.</span></span>  
  
#### <a name="to-create-a-remote-environment-to-access-the-mainframe"></a><span data-ttu-id="8f698-323">Pour créer un environnement distant permettant d'accéder au macroordinateur</span><span class="sxs-lookup"><span data-stu-id="8f698-323">To create a Remote Environment to access the mainframe</span></span>  
  
1.  <span data-ttu-id="8f698-324">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Host Integration Server 2004**, puis cliquez sur **Gestionnaire TI**.</span><span class="sxs-lookup"><span data-stu-id="8f698-324">Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.</span></span>  
  
2.  <span data-ttu-id="8f698-325">Dans le **Gestionnaire TI** de la console, cliquez sur **intégrateur de transactions (Configuration)**, développez **traitement initié par Windows**, avec le bouton droit **à distance Environnements**, pointez sur **nouveau**, puis cliquez sur **environnement distant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-325">In the **TI Manager** console, click **Transaction Integrator (Configuration)**, expand **Windows Initiated Processing**, right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.</span></span>  
  
    1.  <span data-ttu-id="8f698-326">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-326">On the **Welcome** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="8f698-327">Sur le **configurer un nouvel environnement distant** , tapez le **nom de l’Application à distance**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-327">On the **Configure a New Remote Environment** page, type the **Remote Application Name**, and then click **Next**.</span></span> <span data-ttu-id="8f698-328">Dans le cadre de cette procédure pas à pas, utilisez le nom Mainframe_TCP.</span><span class="sxs-lookup"><span data-stu-id="8f698-328">For this walkthrough, use Mainframe_TCP for the name.</span></span>  
  
    3.  <span data-ttu-id="8f698-329">Sur le **configurer l’environnement hôte et le modèle de programmation** page, sélectionnez **CICS** pour le **hôte cible** et **lien ELM** pour la  **Modèle de programmation**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-329">On the **Configure Host Environment and Programming Model** page, select **CICS** for the **Target host** and **ELM Link** for the **Programming model**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="8f698-330">Sur **le point de terminaison configurer TCP/IP** , tapez l’adresse IP du macroordinateur dans le **adresse IP/DNS** zone, puis cliquez sur **modifier** pour ajouter le numéro de port.</span><span class="sxs-lookup"><span data-stu-id="8f698-330">On **the Configure Endpoint TCP/IP** page, type the IP address for your mainframe in the **IP/DNS address** box, and then click **Edit** to add the port number.</span></span> <span data-ttu-id="8f698-331">Le HIS COM accèdera aux transactions via l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="8f698-331">Your HIS COM will access the transactions through the endpoint address.</span></span>  
  
    5.  <span data-ttu-id="8f698-332">Sur le **achèvement** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="8f698-332">On the **Completion** page, click **Finish**.</span></span>  
  
#### <a name="to-create-the-ti-component-for-the-service-oriented-solution"></a><span data-ttu-id="8f698-333">Pour créer le composant TI de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-333">To create the TI Component for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="8f698-334">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Host Integration Server 2004**, puis cliquez sur **Gestionnaire TI**.</span><span class="sxs-lookup"><span data-stu-id="8f698-334">Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.</span></span>  
  
2.  <span data-ttu-id="8f698-335">Dans le **Gestionnaire TI** de la console, cliquez sur **intégrateur de transactions (Configuration)**, cliquez sur **traitement initié par Windows**, puis cliquez sur **objets**.</span><span class="sxs-lookup"><span data-stu-id="8f698-335">In the **TI Manager** console, click **Transaction Integrator (Configuration)**, click **Windows Initiated Processing**, and then click **Objects**.</span></span> <span data-ttu-id="8f698-336">Avec le bouton droit **objets**, cliquez sur **nouveau**, puis cliquez sur **objet**.</span><span class="sxs-lookup"><span data-stu-id="8f698-336">Right-click **Objects**, click **New**, and then click **Object**.</span></span>  
  
    1.  <span data-ttu-id="8f698-337">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-337">On the **Welcome** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="8f698-338">Sur le **spécifier ou rechercher un objet** , cliquez sur **Parcourir**, choisissez l’objet SOHISTIUsingCOM.TLB dans le dossier %BTSSolutionsPath%\SO\MFAccess\HISTIComponent, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="8f698-338">On the **Specify Or Locate An Object** page, click **Browse**, choose the SOHISTIUsingCOM.TLB in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="8f698-339">Sur le **caractéristiques de l’environnement définir pour l’objet COM** page, sélectionnez **BTSScn SO TI Component** pour le **l’application COM +**, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="8f698-339">On the **Define Environment Characteristics for The COM Object** page, select **BTSScn SO TI Component** for the **COM+ application**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="8f698-340">Sur le **définir l’environnement distant** , sélectionnez l’environnement distant que vous avez créé dans la procédure précédente pour le **environnement distant, puis cliquez sur Suivant.**</span><span class="sxs-lookup"><span data-stu-id="8f698-340">On the **Define Remote Environment** page, select the remote environment that you created in the previous procedure for the **Remote environment, and then click Next.**</span></span>  
  
    5.  <span data-ttu-id="8f698-341">Sur le **création d’objets WIP** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.</span><span class="sxs-lookup"><span data-stu-id="8f698-341">On the **Creation of WIP Objects** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="to-test-the-connectivity-to-the-mainframe"></a><span data-ttu-id="8f698-342">Pour tester la connectivité au macroordinateur</span><span class="sxs-lookup"><span data-stu-id="8f698-342">To test the connectivity to the mainframe</span></span>  
  
1.  <span data-ttu-id="8f698-343">Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester, puis double-cliquez sur le fichier Interop.SOHISTIUsingCOM.dll.reg.</span><span class="sxs-lookup"><span data-stu-id="8f698-343">In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester folder, and then double-click the Interop.SOHISTIUsingCOM.dll.reg file.</span></span> <span data-ttu-id="8f698-344">Cette action a pour effet d'ajouter des valeurs correspondant à l'application HISTISimpleTester au Registre afin d'appeler le composant TI via le wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="8f698-344">This adds registry values for the HISTISimpleTester application to call the TI component through the Runtime Callable Wrapper (RCW).</span></span>  
  
2.  <span data-ttu-id="8f698-345">Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\, puis exécutez SetupMFAccess.bat.</span><span class="sxs-lookup"><span data-stu-id="8f698-345">In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\ folder, and then run SetupMFAccess.bat.</span></span>  
  
3.  <span data-ttu-id="8f698-346">Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug, puis exécutez BTSScnSOHISTIComponentSimpleTester.exe.</span><span class="sxs-lookup"><span data-stu-id="8f698-346">In Windows Explorer, navigate to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug folder, and then run BTSScnSOHISTIComponentSimpleTester.exe.</span></span>  
  
    -   <span data-ttu-id="8f698-347">Dans l’application HISTISimpleTester, cliquez sur **appeler le programme du macroordinateur - utiliser COM**.</span><span class="sxs-lookup"><span data-stu-id="8f698-347">In the HISTISimpleTester application, click **Call Mainframe Program - Using COM**.</span></span> <span data-ttu-id="8f698-348">Cinq enregistrements sont renvoyés de l'application COBOL exécutée sur le macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-348">It returns five records from the COBOL application running on the mainframe.</span></span>  
  
##  <span data-ttu-id="8f698-349"><a name="step13"></a>Créer les répertoires virtuels pour l’orchestration des services Web</span><span class="sxs-lookup"><span data-stu-id="8f698-349"><a name="step13"></a> Create the virtual directories for the orchestration Web services</span></span>  
  
#### <a name="to-create-the-virtual-directories-for-the-orchestration-web-services"></a><span data-ttu-id="8f698-350">Pour créer les répertoires virtuels des services Web d'orchestration</span><span class="sxs-lookup"><span data-stu-id="8f698-350">To create the virtual directories for the orchestration Web services</span></span>  
  
1.  <span data-ttu-id="8f698-351">Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Poold’applications**.</span><span class="sxs-lookup"><span data-stu-id="8f698-351">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    1.  <span data-ttu-id="8f698-352">Sur le **Ajouter nouveau Pool d’applications** boîte de dialogue, entrez le **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f698-352">On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="8f698-353">Cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-353">Right-click the application pool that you just created, and then select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="8f698-354">Sur le **propriétés** , cliquez sur le **identité** onglet, sélectionnez **Configurable**, entrez la **nom d’utilisateur** et **mot de passe** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8f698-354">On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**.</span></span> <span data-ttu-id="8f698-355">Pour cette procédure pas à pas utiliser le même compte d’utilisateur qui utilise le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-355">For this walkthrough use the same user account that the BizTalk service is using.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-356">Cet utilisateur doit être autorisé à exécuter le service Web Orchestration Proxy et être ajouté au groupe Administrateurs BizTalk Server, Administrateurs de l'authentification unique ou Administrateurs d'applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="8f698-356">This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups</span></span>  
  
2.  <span data-ttu-id="8f698-357">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-357">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-358">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="8f698-358">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="8f698-359">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter</span><span class="sxs-lookup"><span data-stu-id="8f698-359">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter</span></span>  
  
     <span data-ttu-id="8f698-360">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter</span><span class="sxs-lookup"><span data-stu-id="8f698-360">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter</span></span>  
  
     <span data-ttu-id="8f698-361">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-361">Access Permissions = Read, Run scripts</span></span>  
  
3.  <span data-ttu-id="8f698-362">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f698-362">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="8f698-363">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool*> que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="8f698-363">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> that you created in the previous step.</span></span>  
  
    2.  <span data-ttu-id="8f698-364">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="8f698-364">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="8f698-365">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8f698-365">Click **OK** to exit.</span></span>  
  
4.  <span data-ttu-id="8f698-366">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-366">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-367">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version inline :</span><span class="sxs-lookup"><span data-stu-id="8f698-367">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the inline version:</span></span>  
  
     <span data-ttu-id="8f698-368">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline</span><span class="sxs-lookup"><span data-stu-id="8f698-368">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline</span></span>  
  
     <span data-ttu-id="8f698-369">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline</span><span class="sxs-lookup"><span data-stu-id="8f698-369">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline</span></span>  
  
     <span data-ttu-id="8f698-370">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-370">Access Permissions = Read, Run scripts</span></span>  
  
5.  <span data-ttu-id="8f698-371">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f698-371">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="8f698-372">Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool*> vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="8f698-372">On the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> you just created.</span></span>  
  
    2.  <span data-ttu-id="8f698-373">Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="8f698-373">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="8f698-374">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8f698-374">Click **OK** to exit.</span></span>  
  
##  <span data-ttu-id="8f698-375"><a name="step15"></a>Générez la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-375"><a name="step15"></a> Build the Service Oriented Solution</span></span>  
  
#### <a name="to-build-the-service-oriented-solution"></a><span data-ttu-id="8f698-376">Pour créer la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-376">To build the Service Oriented solution</span></span>  
  
-   <span data-ttu-id="8f698-377">À l’invite de commandes, accédez au répertoire % BTSSolutionsPath%\SO\BTSSoln, tapez `SetupBTSSoln.bat`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8f698-377">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln, type `SetupBTSSoln.bat`, and then press ENTER.</span></span> <span data-ttu-id="8f698-378">La commande SetupBTSSoln.bat effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f698-378">The SetupBTSSoln.bat performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="8f698-379">Crée une clé de nom fort unique (SNK) pour signer les assemblys de la solution orientée services.</span><span class="sxs-lookup"><span data-stu-id="8f698-379">Creates a unique strong name key (SNK) for signing the assemblies of the SO Solution.</span></span>  
  
    -   <span data-ttu-id="8f698-380">extraction du jeton de clé publique de la clé de nom fort et mise à jour des fichiers de liaison avec le jeton public ;</span><span class="sxs-lookup"><span data-stu-id="8f698-380">Extracts the public key token from the SNK and updates the binding files with the public token.</span></span>  
  
    -   <span data-ttu-id="8f698-381">création de la solution orientée services ;</span><span class="sxs-lookup"><span data-stu-id="8f698-381">Builds the SO solution.</span></span>  
  
    -   <span data-ttu-id="8f698-382">création de SSOApplicationConfig dans le dossier %BTSSolutionsPath%\Common.</span><span class="sxs-lookup"><span data-stu-id="8f698-382">Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.</span></span>  
  
##  <span data-ttu-id="8f698-383"><a name="step17"></a>Créer des applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="8f698-383"><a name="step17"></a> Create the SSO affiliate applications</span></span>  
  
#### <a name="to-create-the-sso-affiliate-applications"></a><span data-ttu-id="8f698-384">Pour créer les applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="8f698-384">To create the SSO affiliate applications</span></span>  
  
1.  <span data-ttu-id="8f698-385">Ouvrez une invite de commandes, puis accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts.</span><span class="sxs-lookup"><span data-stu-id="8f698-385">Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="8f698-386">À l'invite de commandes, ouvrez le fichier PendTransAffApp.xml à l'aide du Bloc-notes, puis passez-le en revue.</span><span class="sxs-lookup"><span data-stu-id="8f698-386">At the command prompt, open the PendTransAffApp.xml using Notepad, and review it.</span></span> <span data-ttu-id="8f698-387">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="8f698-387">No changes to this file are necessary.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-388">Le fichier PendTransAffApp.xml définit l'application associée SSO (WoodgroveBank.PendingTransactions) pour le système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-388">The PendTransAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PendingTransactions, for the Pending Transactions back-end system.</span></span> <span data-ttu-id="8f698-389">Il définit également les groupes d'utilisateurs et les groupes d'administration pour l'application associée SSO.</span><span class="sxs-lookup"><span data-stu-id="8f698-389">It also defines the user and administrative groups for the SSO affiliate application.</span></span> <span data-ttu-id="8f698-390">Pour cette procédure pas à pas, utilisez **utilisateurs d’applications BizTalk** et **administrateurs de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="8f698-390">For this walkthrough, use **BizTalk Application Users** and **BizTalk Server Administrators**.</span></span>  
    >   
    >  <span data-ttu-id="8f698-391">Si vous souhaitez utiliser d’autres groupes pour l’application associée SSO, vous devez créer des groupes Windows (avec n’importe quel nom) dans Active Directory et modifier le **appAdminAccount** et **appUserAccount** nœuds dans le fichier PendTransAffApp.xml.</span><span class="sxs-lookup"><span data-stu-id="8f698-391">If you want to use different groups for the SSO affiliate application, you need to create Windows groups (with any name) in the Active Directory, and then change the **appAdminAccount** and **appUserAccount** nodes in the PendTransAffApp.xml.</span></span> <span data-ttu-id="8f698-392">Si vous faites cela, vous devez définir la valeur de **groupApp** attribut de **indicateurs** nœud sur « yes ».</span><span class="sxs-lookup"><span data-stu-id="8f698-392">If you do this, you should set the value for **groupApp** attribute of **flags** node to "yes".</span></span>  
    >   
    >  <span data-ttu-id="8f698-393">Pour plus d’informations sur les applications associées SSO, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).</span><span class="sxs-lookup"><span data-stu-id="8f698-393">For more information about SSO affiliate applications, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>  
  
3.  <span data-ttu-id="8f698-394">À l'invite de commandes, ouvrez le fichier PendTransUserMap.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f698-394">At the command prompt, open the PendTransUserMap.xml file using Notepad, and then make the following edits:</span></span>  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-395">Le fichier PendTransUserMap.xml contient les mappages utilisateur du système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-395">The PendTransUserMap.xml file contains the user mappings for the Pending Transactions back-end system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-396">Pour le **externalUserId** nœud, utilisez l’ID utilisateur externe pour le système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-396">For the **externalUserId** node, use the external user ID for the Pending Transactions back-end system.</span></span> <span data-ttu-id="8f698-397">Dans le cadre de cette procédure pas à pas, utilisez l'ID externe UserID.</span><span class="sxs-lookup"><span data-stu-id="8f698-397">For this walkthrough, use UserID for the external ID.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-398">Pour le **windowsUserId** nœud, entrez le nom d’utilisateur nom qui le **externalUserId** sont mappés à.</span><span class="sxs-lookup"><span data-stu-id="8f698-398">For the **windowsUserId** node, enter the user name which the **externalUserId** will map to.</span></span> <span data-ttu-id="8f698-399">Vous pouvez utiliser un groupe de domaine et un compte d'utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="8f698-399">You can use both a domain group and a domain user account.</span></span> <span data-ttu-id="8f698-400">L'utilisateur doit faire partie d'un groupe autorisé à utiliser le système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-400">This user must be a member of the group that will be allowed to use the Pending Transactions back-end system.</span></span> <span data-ttu-id="8f698-401">Dans le cadre de cette procédure pas à pas, utilisez le nom d'utilisateur du service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-401">For this walkthrough, use the user name of the BizTalk service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-402">Pour le **windowsDomain** nœud, entrez le nom de domaine de la **windowsUserId**.</span><span class="sxs-lookup"><span data-stu-id="8f698-402">For the **windowsDomain** node, enter the domain name of the **windowsUserId**.</span></span>  
  
4.  <span data-ttu-id="8f698-403">À l'invite de commandes, ouvrez le fichier PmntTrckAffApp.xml à l'aide du Bloc-notes, puis passez en revue le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="8f698-403">At the command prompt, open the PmntTrckAffApp.xml file using Notepad, and review the contents of the file.</span></span> <span data-ttu-id="8f698-404">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="8f698-404">No changes to this file are necessary.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-405">Le fichier PmntTrckAffApp.xml définit l'application associée SSO (WoodgroveBank.PaymentTracker) pour le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="8f698-405">The PmntTrckAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PaymentTracker, for the Payment Tracker back-end system.</span></span>  
  
5.  <span data-ttu-id="8f698-406">À l'invite de commandes, ouvrez le fichier PmntTrckUserMap.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f698-406">At the command prompt, open the PmntTrckUserMap.xml file using Notepad, and then make the following edits:</span></span>  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-407">L'application associée SSO Payment Tracker sera utilisée pour l'adaptateur MQSeries. L'ID utilisateur externe/le mot de passe mappés sont envoyés via les propriétés d'en-tête de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8f698-407">The Payment Tracker SSO affiliated application will be used for the MQSeries Adapter and the mapped external user ID/password are sent through MQSeries header properties.</span></span> <span data-ttu-id="8f698-408">Le serveur MQSeries valide uniquement le compte de service BizTalk, sous lequel l'adaptateur MQSeries est exécuté.</span><span class="sxs-lookup"><span data-stu-id="8f698-408">The MQSeries Server validates only the BizTalk service account, under which MQSeries Adapter is running.</span></span> <span data-ttu-id="8f698-409">Il ne valide pas les informations d'identification de l'utilisateur externe.</span><span class="sxs-lookup"><span data-stu-id="8f698-409">It doesn't validate any external user credential.</span></span>  
    >   
    >  <span data-ttu-id="8f698-410">Pour plus d’informations sur l’authentification unique applications associées pour l’adaptateur MQSeries, consultez [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span><span class="sxs-lookup"><span data-stu-id="8f698-410">For more information about SSO affiliated applications for the MQSeries Adapter, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-411">Le fichier PmntTrckUserMap.xml contient les mappages utilisateur SSO pour le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="8f698-411">The PmntTrckUserMap.xml file contains the SSO user mappings for the Payment Tracker back-end system.</span></span> <span data-ttu-id="8f698-412">Le programme de simulation Payment Tracker permet de recréer les conditions de réussite et d'échec de l'authentification des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="8f698-412">The Payment Tracker simulator program simulates both success and failure conditions for user authentication.</span></span>  
    >   
    >  <span data-ttu-id="8f698-413">Le programme authentifie correctement tous les ID d’utilisateur qui commencent par les lettres **PT** (par exemple, **PTUserID**) et ne parvient pas à authentifier les ID d’utilisateur qui ne commencent pas par **PT**.</span><span class="sxs-lookup"><span data-stu-id="8f698-413">The program successfully authenticates all user IDs that begin with the letters **PT** (for example, **PTUserID**), and fails to authenticate any user IDs that do not begin with **PT**.</span></span> <span data-ttu-id="8f698-414">Vous pouvez ainsi choisir l'ID utilisateur approprié en fonction de la condition que vous voulez tester.</span><span class="sxs-lookup"><span data-stu-id="8f698-414">This enables you to choose the appropriate user ID depending on the condition that you would like to test.</span></span> <span data-ttu-id="8f698-415">Vous pouvez également répéter l’intégralité **mappage** nœud pour chaque ID d’utilisateur et définir plusieurs mappages dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="8f698-415">You can also repeat the entire **mapping** node for each user ID and define multiple mappings in the same file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-416">Pour le **externalUserId** nœud, entrez l’ID utilisateur externe pour le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="8f698-416">For the **externalUserId** node, enter the external user ID for the Payment Tracker back-end system.</span></span> <span data-ttu-id="8f698-417">Dans le cadre de cette procédure pas à pas, utilisez l'ID externe PTUserID.</span><span class="sxs-lookup"><span data-stu-id="8f698-417">For this walkthrough, use PTUserID for the external ID.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-418">Pour le **windowsUserId** nœud, entrez le nom d’utilisateur nom qui le **externalUserId** sont mappés à.</span><span class="sxs-lookup"><span data-stu-id="8f698-418">For the **windowsUserId** node, enter the user name which the **externalUserId** will map to.</span></span> <span data-ttu-id="8f698-419">L'utilisateur doit faire partie d'un groupe qui est autorisé à utiliser le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="8f698-419">This user must be a member of the group that will be allowed to use the Payment Tracker back-end system.</span></span> <span data-ttu-id="8f698-420">Dans le cadre de cette procédure pas à pas, utilisez le nom d'utilisateur du service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8f698-420">For this walkthrough, use the user name of the BizTalk service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-421">Pour le **windowsDomain** nœud, entrez le nom de domaine de la **windowsUserId**.</span><span class="sxs-lookup"><span data-stu-id="8f698-421">For the **windowsDomain** node, enter the domain name of the **windowsUserId**.</span></span>  
  
6.  <span data-ttu-id="8f698-422">À l'invite de commandes, ouvrez le fichier ConfigStoreApp.xml à l'aide du Bloc-notes, puis passez en revue le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="8f698-422">At the command prompt, open the ConfigStoreApp.xml file using Notepad, and then review the contents of the file.</span></span>  
  
     <span data-ttu-id="8f698-423">Ce fichier définit l'application de magasin de configuration dans SSO que le scénario utilise pour conserver les paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="8f698-423">This file defines the configuration store application in SSO that the scenario uses to keep configuration parameters.</span></span> <span data-ttu-id="8f698-424">Certains de ces paramètres incluent une valeur de délai d'expiration lors de la communication avec SAP (à la fois pour la version d'adaptateur et pour la version Inline), le nom du gestionnaire de file d'attente, ainsi que les files d'attente à utiliser avec la version Inline.</span><span class="sxs-lookup"><span data-stu-id="8f698-424">Some of the configuration parameters include the Timeout value when communicating with SAP (for both the adapter and inline versions) and the name of the queue manager and queues to use when using the inline version.</span></span> <span data-ttu-id="8f698-425">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="8f698-425">No changes to this file are necessary.</span></span>  
  
7.  <span data-ttu-id="8f698-426">À l'invite de commandes, ouvrez le fichier SetConfigValuesInSSO.cmd à l'aide du Bloc-notes, puis examinez et modifiez son contenu selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8f698-426">At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, review and change the contents of the file as the following table.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-427">Ce fichier de commande définit les valeurs des paramètres de configuration dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="8f698-427">This command file sets the values for the configuration parameters in the SSO database.</span></span> <span data-ttu-id="8f698-428">Il contient plusieurs commandes Set qui attribuent les valeurs à des variables locales au début du fichier de commande.</span><span class="sxs-lookup"><span data-stu-id="8f698-428">It contains several set commands that assign the values to local variables in the beginning of the command file.</span></span>  
    >   
    >  <span data-ttu-id="8f698-429">Les valeurs SAPAdapterTimeout, PendingTransactionsAdapterTimeout et PaymentTrackingAdapterTimeout sont utilisées dans la version d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-429">The SAPAdapterTimeout, PendingTransactionsAdapterTimeout, and PaymentTrackingAdapterTimeout values are used in the adapter version.</span></span> <span data-ttu-id="8f698-430">Les valeurs restantes sont utilisées dans la version Inline.</span><span class="sxs-lookup"><span data-stu-id="8f698-430">The remaining values are used in the inline version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-431">Vous pouvez entrer « » (deux guillemets doubles) pour les valeurs par défaut marquées \<spécifié par l’utilisateur > dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="8f698-431">You can enter " " (two double quotes) for the default values marked \<User Specified> in the following table.</span></span>  
  
    |<span data-ttu-id="8f698-432">Paramètre</span><span class="sxs-lookup"><span data-stu-id="8f698-432">Parameter</span></span>|<span data-ttu-id="8f698-433">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="8f698-433">Default Value</span></span>|<span data-ttu-id="8f698-434"> Description</span><span class="sxs-lookup"><span data-stu-id="8f698-434">Description</span></span>|  
    |---------------|-------------------|-----------------|  
    |<span data-ttu-id="8f698-435">SAPAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="8f698-435">SAPAdapterTimeout</span></span>|<span data-ttu-id="8f698-436">20000</span><span class="sxs-lookup"><span data-stu-id="8f698-436">20000</span></span>|<span data-ttu-id="8f698-437">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système principal SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-437">Max timeout (millisecond) for a request to the SAP back-end</span></span>|  
    |<span data-ttu-id="8f698-438">SAPInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="8f698-438">SAPInlineTimeout</span></span>|<span data-ttu-id="8f698-439">20000</span><span class="sxs-lookup"><span data-stu-id="8f698-439">20000</span></span>|<span data-ttu-id="8f698-440">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système principal SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-440">Max timeout (millisecond) for a request to the SAP back-end</span></span>|  
    |<span data-ttu-id="8f698-441">SAPInlineHostName</span><span class="sxs-lookup"><span data-stu-id="8f698-441">SAPInlineHostName</span></span>|<span data-ttu-id="8f698-442">\<Utilisateur spécifié ></span><span class="sxs-lookup"><span data-stu-id="8f698-442">\<User Specified></span></span>|<span data-ttu-id="8f698-443">Identificateur principal SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-443">SAP back-end identifier</span></span>|  
    |<span data-ttu-id="8f698-444">SAPInlineClientNumber</span><span class="sxs-lookup"><span data-stu-id="8f698-444">SAPInlineClientNumber</span></span>|<span data-ttu-id="8f698-445">\<Utilisateur spécifié ></span><span class="sxs-lookup"><span data-stu-id="8f698-445">\<User Specified></span></span>|<span data-ttu-id="8f698-446">Numéro de client SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-446">SAP Client number</span></span>|  
    |<span data-ttu-id="8f698-447">SAPInlineSystemNumber</span><span class="sxs-lookup"><span data-stu-id="8f698-447">SAPInlineSystemNumber</span></span>|<span data-ttu-id="8f698-448">\<Utilisateur spécifié ></span><span class="sxs-lookup"><span data-stu-id="8f698-448">\<User Specified></span></span>|<span data-ttu-id="8f698-449">Numéro de système SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-449">SAP System number</span></span>|  
    |<span data-ttu-id="8f698-450">SAPInlineUserName</span><span class="sxs-lookup"><span data-stu-id="8f698-450">SAPInlineUserName</span></span>|<span data-ttu-id="8f698-451">\<Utilisateur spécifié ></span><span class="sxs-lookup"><span data-stu-id="8f698-451">\<User Specified></span></span>|<span data-ttu-id="8f698-452">Nom d'utilisateur permettant de se connecter au système principal SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-452">The user name used to connect to the SAP back-end</span></span>|  
    |<span data-ttu-id="8f698-453">SAPInlinePassword</span><span class="sxs-lookup"><span data-stu-id="8f698-453">SAPInlinePassword</span></span>|<span data-ttu-id="8f698-454">\<Utilisateur spécifié ></span><span class="sxs-lookup"><span data-stu-id="8f698-454">\<User Specified></span></span>|<span data-ttu-id="8f698-455">Mot de passe permettant de se connecter au système principal SAP</span><span class="sxs-lookup"><span data-stu-id="8f698-455">The password used to connect to the SAP back-end</span></span>|  
    |<span data-ttu-id="8f698-456">PendingTransactionsAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="8f698-456">PendingTransactionsAdapterTimeout</span></span>|<span data-ttu-id="8f698-457">20000</span><span class="sxs-lookup"><span data-stu-id="8f698-457">20000</span></span>|<span data-ttu-id="8f698-458">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du serveur Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="8f698-458">Max timeout (millisecond) for a request to the Pending Transactions server</span></span>|  
    |<span data-ttu-id="8f698-459">PendingTransactionsInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="8f698-459">PendingTransactionsInlineTimeout</span></span>|<span data-ttu-id="8f698-460">20000</span><span class="sxs-lookup"><span data-stu-id="8f698-460">20000</span></span>|<span data-ttu-id="8f698-461">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du serveur Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="8f698-461">Max timeout (millisecond) for a request to the Pending Transactions server</span></span>|  
    |<span data-ttu-id="8f698-462">PendingTransactionsInlineURL</span><span class="sxs-lookup"><span data-stu-id="8f698-462">PendingTransactionsInlineURL</span></span>|<span data-ttu-id="8f698-463">https://\<*nom de votre ordinateur*> /Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx</span><span class="sxs-lookup"><span data-stu-id="8f698-463">https://\<*your computer name*>/Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx</span></span>|<span data-ttu-id="8f698-464">URL du service Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-464">URL of the Pending Transactions service.</span></span> <span data-ttu-id="8f698-465">\<*Nom de votre ordinateur*> doit correspondre à la **nom commun** dans la procédure « pour créer une demande de certificat ».</span><span class="sxs-lookup"><span data-stu-id="8f698-465">\<*Your computer name*> must match the **common name** in the procedure "To create a certificate request".</span></span> <span data-ttu-id="8f698-466">Vous ne devez pas utiliser « localhost » pour \< *nom de votre ordinateur*>.</span><span class="sxs-lookup"><span data-stu-id="8f698-466">You must not use "localhost" for \<*Your computer name*>.</span></span>|  
    |<span data-ttu-id="8f698-467">PendingTransactionsInlineSSOAffiliateApp</span><span class="sxs-lookup"><span data-stu-id="8f698-467">PendingTransactionsInlineSSOAffiliateApp</span></span>|<span data-ttu-id="8f698-468">WoodgroveBank.PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-468">WoodgroveBank.PendingTransactions</span></span>|<span data-ttu-id="8f698-469">Nom de l'application SSO Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="8f698-469">Pending Transactions SSO application name</span></span>|  
    |<span data-ttu-id="8f698-470">PaymentTrackingAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="8f698-470">PaymentTrackingAdapterTimeout</span></span>|<span data-ttu-id="8f698-471">20000</span><span class="sxs-lookup"><span data-stu-id="8f698-471">20000</span></span>|<span data-ttu-id="8f698-472">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="8f698-472">Max timeout (millisecond) for a request to the Payment Tracking system</span></span>|  
    |<span data-ttu-id="8f698-473">PaymentTrackingInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="8f698-473">PaymentTrackingInlineTimeout</span></span>|<span data-ttu-id="8f698-474">20000</span><span class="sxs-lookup"><span data-stu-id="8f698-474">20000</span></span>|<span data-ttu-id="8f698-475">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="8f698-475">Max timeout (millisecond) for a request to the Payment Tracking system</span></span>|  
    |<span data-ttu-id="8f698-476">PaymentTrackingInlineQManager</span><span class="sxs-lookup"><span data-stu-id="8f698-476">PaymentTrackingInlineQManager</span></span>|<span data-ttu-id="8f698-477">\<Utilisateur spécifié > (généralement QM_\<*nom de votre ordinateur*>).</span><span class="sxs-lookup"><span data-stu-id="8f698-477">\<User Specified> (Typically QM_\<*your computer name*>).</span></span>|<span data-ttu-id="8f698-478">Nom du gestionnaire de file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="8f698-478">MQSeries Queue Manager name</span></span>|  
    |<span data-ttu-id="8f698-479">PaymentTrackingInlineMQChannelDefinition</span><span class="sxs-lookup"><span data-stu-id="8f698-479">PaymentTrackingInlineMQChannelDefinition</span></span>|<span data-ttu-id="8f698-480">" " (vous devez entrer deux guillemets doubles).</span><span class="sxs-lookup"><span data-stu-id="8f698-480">" " (need to enter the two double quotes).</span></span>|<span data-ttu-id="8f698-481">Chaîne vide si local, ou nom de chaîne formaté du serveur MQ distant.</span><span class="sxs-lookup"><span data-stu-id="8f698-481">Empty string if local, or formatted channel name of the remote MQ server.</span></span> <span data-ttu-id="8f698-482">Si vous conservez tous les paramètres par défaut de la configuration d’IBM WebSphere MQ, la définition de la chaîne sera S__\<*nom de votre ordinateur*> /TCP/\<*nom de votre ordinateur*> (1414).</span><span class="sxs-lookup"><span data-stu-id="8f698-482">If you keep all default settings in configuring IBM WebSphere MQ, the channel definition will be S__\<*your computer name*>/TCP/\<*your computer name*>(1414).</span></span>|  
    |<span data-ttu-id="8f698-483">PaymentTrackingInlineRequestQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-483">PaymentTrackingInlineRequestQueue</span></span>|<span data-ttu-id="8f698-484">LastPaymentsInputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-484">LastPaymentsInputQueue</span></span>|<span data-ttu-id="8f698-485">Nom de la file d'attente MQ pour les demandes de Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="8f698-485">The MQ Queue name for payment tracking requests</span></span>|  
    |<span data-ttu-id="8f698-486">PaymentTrackingInlineResponseQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-486">PaymentTrackingInlineResponseQueue</span></span>|<span data-ttu-id="8f698-487">LastPaymentsOutputQueue</span><span class="sxs-lookup"><span data-stu-id="8f698-487">LastPaymentsOutputQueue</span></span>|<span data-ttu-id="8f698-488">Nom de la file d'attente MQ pour les réponses de Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="8f698-488">The MQ Queue name for payment tracking responses</span></span>|  
    |<span data-ttu-id="8f698-489">PaymentTrackingInlineSSOAffiliateApp</span><span class="sxs-lookup"><span data-stu-id="8f698-489">PaymentTrackingInlineSSOAffiliateApp</span></span>|<span data-ttu-id="8f698-490">WoodgroveBank.PaymentTracker</span><span class="sxs-lookup"><span data-stu-id="8f698-490">WoodgroveBank.PaymentTracker</span></span>|<span data-ttu-id="8f698-491">Nom de l'application SSO Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="8f698-491">Payment tracking SSO application name</span></span>|  
    |<span data-ttu-id="8f698-492">StubSAPWebServiceURL</span><span class="sxs-lookup"><span data-stu-id="8f698-492">StubSAPWebServiceURL</span></span>|<span data-ttu-id="8f698-493">http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx</span><span class="sxs-lookup"><span data-stu-id="8f698-493">http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx</span></span>|<span data-ttu-id="8f698-494">URL du service Web stub du système SAP Credit Limit</span><span class="sxs-lookup"><span data-stu-id="8f698-494">The stub Web service URL of the Credit Limit SAP system</span></span>|  
  
8.  <span data-ttu-id="8f698-495">À l'invite de commandes, exécutez la commande suivante pour définir l'environnement PATH :</span><span class="sxs-lookup"><span data-stu-id="8f698-495">At the command prompt, run the following command to set the PATH environment:</span></span>  
  
    -   `SET PATH=%PATH%;"%CommonProgramFiles%\Enterprise Single Sign-On"`  
  
9. <span data-ttu-id="8f698-496">À l'invite de commandes, exécutez la commande CreateInitialConfigInSSO.cmd.</span><span class="sxs-lookup"><span data-stu-id="8f698-496">At the command prompt, run the CreateInitialConfigInSSO.cmd.</span></span> <span data-ttu-id="8f698-497">Celle-ci crée les applications associées SSO, l'application de magasin de configuration SSO et les mappages utilisateur des applications associées.</span><span class="sxs-lookup"><span data-stu-id="8f698-497">It creates the SSO Affiliate Applications, the SSO configuration store application, and the user mappings for the affiliate applications.</span></span> <span data-ttu-id="8f698-498">Elle exécute ensuite SetConfigValuesInSSO.cmd pour stocker les valeurs de configuration dans l'application de magasin de configuration SSO.</span><span class="sxs-lookup"><span data-stu-id="8f698-498">Then, it executes the SetConfigValuesInSSO.cmd to store configuration values in the SSO configuration store application.</span></span>  
  
10. <span data-ttu-id="8f698-499">À l'invite de commandes, exécutez la commande suivante pour définir les informations d'identification de l'utilisateur de l'application associée Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-499">At the command prompt, run the following command to set the user credential for the Pending Transactions affiliate application.</span></span> <span data-ttu-id="8f698-500">Utilisez le \< **DomainName**> et \< **UserID**> définis dans le fichier PendTransUserMap.xml pour la \<WindowsDomain >\\< WindowsUserId\>.</span><span class="sxs-lookup"><span data-stu-id="8f698-500">Use the \<**DomainName**> and \<**UserID**> defined in the PendTransUserMap.xml for the \<WindowsDomain>\\<WindowsUserId\>.</span></span> <span data-ttu-id="8f698-501">Cette commande vous invite à entrer le mot de passe de l'utilisateur externe (UserID dans le cadre de cette procédure).</span><span class="sxs-lookup"><span data-stu-id="8f698-501">This command asks you to enter the password of the external user, UserID, used in this walkthrough.</span></span>  
  
    -   `ssomanage -setcredentials <WindowsDomain>\<WindowsUserId> WoodgroveBank.PendingTransactions`  
  
11. <span data-ttu-id="8f698-502">À l'invite de commandes, exécutez la commande suivante pour définir les informations d'identification de l'utilisateur de l'application associée Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="8f698-502">At the command prompt, run the following command to set the user credential for the Payment Tracker affiliate application.</span></span> <span data-ttu-id="8f698-503">Utilisez le \< **DomainName**> et \< **UserID**> définis dans le fichier PmntTrckUserMap.xml pour la \<WindowsDomain >\\< WindowsUserId \>.</span><span class="sxs-lookup"><span data-stu-id="8f698-503">Use the \<**DomainName**> and \<**UserID**> defined in the PmntTrckUserMap.xml for the \<WindowsDomain>\\<WindowsUserId\>.</span></span> <span data-ttu-id="8f698-504">Cette commande vous invite à entrer le mot de passe de l'utilisateur externe (PTUserID dans le cadre de cette procédure).</span><span class="sxs-lookup"><span data-stu-id="8f698-504">This command asks you to enter the password of the external user, PTUserID, used in this walkthrough.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-505">Le simulateur Payment Tracker ne valide pas les informations d'identification de l'utilisateur externe.</span><span class="sxs-lookup"><span data-stu-id="8f698-505">The Payment Tracker simulator doesn't validate the external user credential.</span></span> <span data-ttu-id="8f698-506">Vous pouvez entrer n'importe quel mot de passe pour l'utilisateur PTUserID.</span><span class="sxs-lookup"><span data-stu-id="8f698-506">You can enter any password for the PTUserID.</span></span>  
  
    -   `ssomanage -setcredentials < WindowsDomain >\< WindowsUserId > WoodgroveBank.PaymentTracker`  
  
##  <span data-ttu-id="8f698-507"><a name="step19"></a>Déployer le fichier de définition BAM pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-507"><a name="step19"></a> Deploy the BAM definition file for the Service Oriented Solution</span></span>  
  
#### <a name="to-deploy-the-bam-definition-file-for-the-service-oriented-solution"></a><span data-ttu-id="8f698-508">Pour déployer le fichier de définition BAM pour la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-508">To deploy the BAM definition file for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="8f698-509">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir le chemin d'accès des utilitaires BAM :</span><span class="sxs-lookup"><span data-stu-id="8f698-509">Open a command prompt, type the following command, and then press ENTER to set the path to find the BAM utilities:</span></span>  
  
    -   <span data-ttu-id="8f698-510">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span><span class="sxs-lookup"><span data-stu-id="8f698-510">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span></span>  
  
2.  <span data-ttu-id="8f698-511">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\BAM, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="8f698-511">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM, type the following command, and then press ENTER:</span></span>  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
##  <span data-ttu-id="8f698-512"><a name="step21"></a>Déployer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-512"><a name="step21"></a> Deploy the Service Oriented Solution</span></span>  
  
#### <a name="to-edit-the-binding-files-for-the-service-oriented-solution"></a><span data-ttu-id="8f698-513">Pour modifier les fichiers de liaison de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-513">To edit the binding files for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="8f698-514">Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, ouvrez le fichier Deployallbinding.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f698-514">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open the Deployallbinding.xml using Notepad, and then make the following edits:</span></span>  
  
    -   <span data-ttu-id="8f698-515">Remplacez le nom du serveur dans les variables SET MGMT_DB_SERVER et MBMT_DB par les noms du serveur et de la base de données utilisés par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8f698-515">Change the name of the server in the SET MGMT_DB_SERVER and MBMT_DB to the name of the server and database that BizTalk Server is using.</span></span>  
  
    -   <span data-ttu-id="8f698-516">Remplacez la valeur de la variable SOLNDIR par "%BTSSolutionsPath%\SO\BTSSoln".</span><span class="sxs-lookup"><span data-stu-id="8f698-516">Change the value of the SOLNDIR variable to "%BTSSolutionsPath%\SO\BTSSoln".</span></span>  
  
2.  <span data-ttu-id="8f698-517">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Bindings.</span><span class="sxs-lookup"><span data-stu-id="8f698-517">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Bindings folder.</span></span>  
  
3.  <span data-ttu-id="8f698-518">Pour la version d'adaptateur, ouvrez le fichier AdapterSOAOrchBindings.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f698-518">For the adapter version, open the AdapterSOAOrchBindings.xml using Notepad, and then edit as follows:</span></span>  
  
    -   <span data-ttu-id="8f698-519">Remplacez toutes les occurrences de __MQ_SERVER_NAME\_ \_ avec le nom du serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8f698-519">Replace all occurrences of __MQ_SERVER_NAME\_\_ with the MQSeries Server name.</span></span>  
  
    -   <span data-ttu-id="8f698-520">Remplacez toutes les occurrences de __MQ_QMANAGER_NAME\_ \_ avec le nom du Gestionnaire de file d’attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8f698-520">Replace all occurrences of __MQ_QMANAGER_NAME\_\_ with the MQSeries Queue Manager name.</span></span>  
  
    -   <span data-ttu-id="8f698-521">Remplacez toutes les occurrences de __PT_WS_SERVER_NAME\_ \_ dans la chaîne «\<adresse > https://\__PT_WS_SERVER_NAME\_\_» avec le nom du serveur où les Transactions en attente Service Web est déployé.</span><span class="sxs-lookup"><span data-stu-id="8f698-521">Replace all occurrences of __PT_WS_SERVER_NAME\_\_ in the string "\<Address>https://\__PT_WS_SERVER_NAME\_\_" with the server name where the Pending Transactions Web service is deployed.</span></span> <span data-ttu-id="8f698-522">Le nom du serveur doit correspondre à la **nom commun** à l’étape, « pour configurer le serveur Web pour SSL ».</span><span class="sxs-lookup"><span data-stu-id="8f698-522">The server name must match the **common name** in the step, "To configure the Web server for SSL".</span></span> <span data-ttu-id="8f698-523">Vous ne devez pas utiliser « localhost ».</span><span class="sxs-lookup"><span data-stu-id="8f698-523">You shouldn't use localhost.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-524">Le fichier de liaison, AdapterSOAOrchBindings.xml, utilise le service Web stub pour :</span><span class="sxs-lookup"><span data-stu-id="8f698-524">The binding file, AdapterSOAOrchBindings.xml, uses the stub Web service for:</span></span>  
    >   
    >  1.  <span data-ttu-id="8f698-525">le système principal SAP Credit Limit ;</span><span class="sxs-lookup"><span data-stu-id="8f698-525">The Credit Limit back-end SAP system.</span></span>  
    > 2.  <span data-ttu-id="8f698-526">l'adaptateur MQSeries à des fins d'intégration au système principal Payment Tracking ;</span><span class="sxs-lookup"><span data-stu-id="8f698-526">The MQSeries adapter to integrate with the Payment Tracking back-end system.</span></span>  
    > 3.  <span data-ttu-id="8f698-527">le service Web Pending Transactions pour appeler le composant .NET TI HIS à des fins d'intégration au système principal du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="8f698-527">The Pending Transactions Web service to call the HIS TI .NET component to integrate with the mainframe back-end system.</span></span>  
    >   
    >  <span data-ttu-id="8f698-528">Si vous ne disposez d'aucun macroordinateur, vous devez utiliser le service Web stub pour générer des données dans le système Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="8f698-528">If you aren’t using the mainframe, you must use the stub Web service to generate data for the Pending Transactions system.</span></span>  
  
4.  <span data-ttu-id="8f698-529">Pour la version Inline, ouvrez le fichier InlineSOAOrchBindings.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="8f698-529">For the inline version, open the InlineSOAOrchBindings.xml using Notepad, and then edit as follows:</span></span>  
  
    -   <span data-ttu-id="8f698-530">Remplacez toutes les occurrences de __MQ_SERVER_NAME\_ \_ avec le nom du serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8f698-530">Replace all occurrences of __MQ_SERVER_NAME\_\_ with the MQSeries Server name.</span></span>  
  
    -   <span data-ttu-id="8f698-531">Remplacez toutes les occurrences de __MQ_QMANAGER_NAME\_ \_ avec le nom du Gestionnaire de file d’attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="8f698-531">Replace all occurrences of __MQ_QMANAGER_NAME\_\_ with the MQSeries Queue Manager name.</span></span>  
  
#### <a name="to-deploy-the-service-oriented-solution"></a><span data-ttu-id="8f698-532">Pour déployer la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-532">To deploy the Service Oriented solution</span></span>  
  
-   <span data-ttu-id="8f698-533">À l’invite de commandes, accédez au répertoire dans le dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8f698-533">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER.</span></span>  
  
    -   `Deployallbinding.cmd`  
  
    > [!NOTE]
    >  <span data-ttu-id="8f698-534">La commande Deployallbinding.cmd crée l'application BizTalk appelée BTSScn.SO.CustomerService et importe les fichiers de liaison pour les versions d'adaptateur et Inline.</span><span class="sxs-lookup"><span data-stu-id="8f698-534">The Deployallbinding.cmd creates the BizTalk application named BTSScn.SO.CustomerService and imports binding files for the adapter and inline versions.</span></span>  
  
##  <span data-ttu-id="8f698-535"><a name="step23"></a>Configurer le Services Web Pending Transactions stub lorsqu’un macroordinateur n’est pas disponible</span><span class="sxs-lookup"><span data-stu-id="8f698-535"><a name="step23"></a> Configure the stub Pending Transactions Web Services when a mainframe is not available</span></span>  
  
#### <a name="to-configure-the-stub-pending-transactions-web-service-for-using-the-adapter-version-without-a-mainframe"></a><span data-ttu-id="8f698-536">Pour configurer le service Web Pending Transactions stub (pour utiliser la version d'adaptateur sans macroordinateur)</span><span class="sxs-lookup"><span data-stu-id="8f698-536">To configure the stub Pending Transactions Web service (for using the adapter version without a mainframe)</span></span>  
  
1.  <span data-ttu-id="8f698-537">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-537">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-538">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web Pending Transactions pour la version d’adaptateur stub :</span><span class="sxs-lookup"><span data-stu-id="8f698-538">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="8f698-539">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-539">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
     <span data-ttu-id="8f698-540">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="8f698-540">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
     <span data-ttu-id="8f698-541">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-541">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="8f698-542">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit à l’aide de la **propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8f698-542">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows using the **Properties** dialog box.</span></span>  
  
    1.  <span data-ttu-id="8f698-543">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool*> vous avez créé à l’étape, « pour créer les répertoires virtuels dans IIS pour la solution ».</span><span class="sxs-lookup"><span data-stu-id="8f698-543">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> you created in the step, "To create the virtual directories in IIS for the solution".</span></span>  
  
    2.  <span data-ttu-id="8f698-544">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="8f698-544">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="8f698-545">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8f698-545">Click **OK** to exit.</span></span>  
  
3.  <span data-ttu-id="8f698-546">Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, btsscn.so.CustomerService, puis **envoyer Ports**, avec le bouton droit **PendingTransactionSolicitResponsePort**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="8f698-546">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand BTSScn.SO.CustomerService, expand **Send Ports**, right-click **PendingTransactionSolicitResponsePort**, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="8f698-547">Dans le **général** , cliquez sur **configurer** pour afficher les **propriétés du Transport** boîte de dialogue zone, puis modifiez le **URL du Service Web** à le stub Web en attente de Transaction de service, par exemple :</span><span class="sxs-lookup"><span data-stu-id="8f698-547">In the **General** page, click **Configure** to display the **Transport Properties** dialog box, and then modify the **Web Service URL** to the stub Pending Transaction Web service, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
    2.  <span data-ttu-id="8f698-548">Fermez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="8f698-548">Close all of the dialog boxes.</span></span>  
  
#### <a name="to-configure-the-stub-pending-transactions-web-service-for-using-the-inline-version-without-a-mainframe"></a><span data-ttu-id="8f698-549">Pour configurer le service Web Pending Transactions stub (pour utiliser la version Inline sans macroordinateur)</span><span class="sxs-lookup"><span data-stu-id="8f698-549">To configure the stub Pending Transactions Web service (for using the inline version without a mainframe)</span></span>  
  
1.  <span data-ttu-id="8f698-550">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="8f698-550">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="8f698-551">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web Pending Transactions pour la version d’adaptateur stub :</span><span class="sxs-lookup"><span data-stu-id="8f698-551">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="8f698-552">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="8f698-552">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
     <span data-ttu-id="8f698-553">Chemin d’accès = \< *répertoire d’installation de BizTalk*> \SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="8f698-553">PATH = \<*BizTalk Install Directory*>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
     <span data-ttu-id="8f698-554">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="8f698-554">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="8f698-555">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="8f698-555">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="8f698-556">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool*> vous avez créé à l’étape, « pour créer les répertoires virtuels dans IIS pour la solution ».</span><span class="sxs-lookup"><span data-stu-id="8f698-556">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*> you created in the step, "To create the virtual directories in IIS for the solution".</span></span>  
  
    2.  <span data-ttu-id="8f698-557">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="8f698-557">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="8f698-558">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="8f698-558">Click **OK** to exit.</span></span>  
  
3.  <span data-ttu-id="8f698-559">Ouvrez une invite de commandes, puis accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts.</span><span class="sxs-lookup"><span data-stu-id="8f698-559">Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
4.  <span data-ttu-id="8f698-560">À l’invite de commandes, ouvrez le fichier SetConfigValuesInSSO.cmd à l’aide du bloc-notes, puis définissez la valeur de la **PendingTransactionsInlineURL** à l’URL du Service Web Pending transactions stub.</span><span class="sxs-lookup"><span data-stu-id="8f698-560">At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, and then set the value of the **PendingTransactionsInlineURL** to the URL of the stub Pending Transaction Web Service.</span></span>  
  
    -   `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
5.  <span data-ttu-id="8f698-561">À l'invite de commandes, tapez `SetConfigValuesInSSO.cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="8f698-561">At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER.</span></span>  
  
##  <span data-ttu-id="8f698-562"><a name="step25"></a>Démarrer le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="8f698-562"><a name="step25"></a> Start the Service Oriented Solution</span></span>  
  
#### <a name="to-start-the-service-oriented-solution"></a><span data-ttu-id="8f698-563">Pour démarrer la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="8f698-563">To start the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="8f698-564">Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE pour démarrer toutes les orchestrations des versions d'adaptateur et Inline.</span><span class="sxs-lookup"><span data-stu-id="8f698-564">Open a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER to start all orchestrations for the inline and adapter versions.</span></span>  
  
    -   `startAll.vbs`  
  
2.  <span data-ttu-id="8f698-565">Exécutez la solution orientée services.</span><span class="sxs-lookup"><span data-stu-id="8f698-565">Run the service-oriented solution.</span></span> <span data-ttu-id="8f698-566">Pour plus d’informations sur l’exécution de la solution, consultez [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="8f698-566">For more information about running the solution, see [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8f698-567">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8f698-567">Next Steps</span></span>  
 <span data-ttu-id="8f698-568">Test de la version d’adaptateur et inline de la solution orientée services dans [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="8f698-568">You test the inline and adapter version of the service-oriented solution in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f698-569">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f698-569">See Also</span></span>  
 <span data-ttu-id="8f698-570">[Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="8f698-570">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="8f698-571">[Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="8f698-571">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="8f698-572">Installation d’ordinateur de développeur pour le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="8f698-572">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)