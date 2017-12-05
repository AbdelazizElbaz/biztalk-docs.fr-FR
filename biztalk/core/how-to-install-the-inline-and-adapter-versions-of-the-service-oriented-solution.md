---
title: "Installation en ligne et la Solution orientée services des Versions d’adaptateur du Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6050cfe9-4e94-4a55-8b24-fbcc74d9e8f4
caps.latest.revision: "97"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d648db0f3a7c6ad4dccdbcc7555fc3c0727568c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution"></a><span data-ttu-id="6c662-102">Installation des versions Inline et d'adaptateur de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-102">How to Install the Inline and Adapter Versions of the Service Oriented Solution</span></span>
<span data-ttu-id="6c662-103">La procédure suivante décrit la préparation de votre ordinateur pour l'installation des versions d'adaptateur et Inline de la solution orientée services, puis l'installation de la solution sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-103">The following steps describe how to prepare the computer for installing the inline and adapter versions of the service oriented solution, and how to install the solution on this computer.</span></span>  
  
> [!NOTE]
>  - <span data-ttu-id="6c662-104">Le service de solution orientée services se trouve dans le dossier \< *dossier d’Installation de BizTalk Server*\>\SDK\Scenarios\SO.</span><span class="sxs-lookup"><span data-stu-id="6c662-104">The service oriented solution is located in the folder \<*BizTalk Server Installation Folder*\>\SDK\Scenarios\SO.</span></span>  
>  - <span data-ttu-id="6c662-105">Si vous ne disposez pas d'un macroordinateur pour la solution, vous pouvez modifier la liaison du port de manière à utiliser le service Web Pending Transactions stub.</span><span class="sxs-lookup"><span data-stu-id="6c662-105">If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions.</span></span> <span data-ttu-id="6c662-106">Le service Web génère des transactions localement pour émuler celles du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-106">The Web service generates transactions locally to emulate the mainframe transactions.</span></span>  
  
##  <a name="step1"></a><span data-ttu-id="6c662-107">Préparer l’ordinateur pour l’installation des versions d’adaptateur et inline de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-107">Prepare the computer for installing the adapter and inline versions of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="6c662-108">Si vous avez installé Windows SharePoint Services, excluez la (racine) du Site Web par défaut à partir de Windows SharePoint Services de chemins d’accès gérés comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur  **Outils d’administration**, puis cliquez sur **Administration centrale de SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="6c662-108">If you installed Windows SharePoint Services, exclude the (root) of the Default Web Site from Windows SharePoint Services Managed Paths as follows: Click **Start**, point to **All Programs**, point to **Administrative Tools**, and then click **SharePoint Central Administration**.</span></span>  
  
    1.  <span data-ttu-id="6c662-109">Sous **Configuration du serveur virtuel**, sélectionnez **configurer les paramètres du serveur virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-109">Under **Virtual Server Configuration**, select **Configure virtual server settings**.</span></span>  
  
    2.  <span data-ttu-id="6c662-110">Sur le **liste des serveurs virtuels** , cliquez sur **Site Web par défaut**.</span><span class="sxs-lookup"><span data-stu-id="6c662-110">On the **Virtual Server List** page, click **Default Web Site**.</span></span>  
  
    3.  <span data-ttu-id="6c662-111">Sur le **paramètres du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-111">On the **Virtual Server Settings** page, click **Define managed paths**.</span></span>  
  
    4.  <span data-ttu-id="6c662-112">Dans le **chemins d’accès inclus** section de la **défini par chemin d’accès géré** page, sélectionnez **racine** puis cliquez sur **supprimer des chemins d’accès sélectionnés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-112">In the **Included Paths** section of the **Defined Managed Path** page, select **Root** and then click **Remove selected paths**.</span></span>  
  
    5.  <span data-ttu-id="6c662-113">Ouvrez une invite de commandes, puis exécutez IISReset.</span><span class="sxs-lookup"><span data-stu-id="6c662-113">At a command prompt, perform an IISReset.</span></span>  
  
2.  <span data-ttu-id="6c662-114">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **outils d’administration**, cliquez sur **gestion de l’ordinateur** de la console, puis ajoutez le Compte de service BizTalk au groupe Administrateurs local.</span><span class="sxs-lookup"><span data-stu-id="6c662-114">Click **Start**, point to **All Programs**, point to **Administrative Tools**, click **Computer Management** console, and then add the BizTalk service account to the local Administrators group.</span></span>  
  
3.  <span data-ttu-id="6c662-115">Fermez votre session, puis ouvrez une session sur l'ordinateur à l'aide du compte de service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-115">Log off the computer, and then log on to the computer as the BizTalk service account.</span></span>  
  
4.  <span data-ttu-id="6c662-116">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir la variable d'environnement %BTSSolutionsPath%.</span><span class="sxs-lookup"><span data-stu-id="6c662-116">At a command prompt, type the following command, and then press ENTER to set the %BTSSolutionsPath% environment variable.</span></span> <span data-ttu-id="6c662-117">Fermez ensuite l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6c662-117">Then, exit the command prompt.</span></span>  
  
    -   <span data-ttu-id="6c662-118">setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span><span class="sxs-lookup"><span data-stu-id="6c662-118">setx BTSSolutionsPath [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Scenarios"</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c662-119">Si vous utilisez un ordinateur 64 bits, utilisez %ProgramFiles(x86)% à la place de %ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="6c662-119">If you are using a 64-bit computer, use %ProgramFiles(x86)% instead of %ProgramFiles%.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c662-120">Pour plus d’informations sur la commande SETX, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span><span class="sxs-lookup"><span data-stu-id="6c662-120">For more information about the SETX command, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67831](http://go.microsoft.com/fwlink/?LinkId=67831).</span></span>  
  
##  <a name="step3"></a><span data-ttu-id="6c662-121">Supprimer la version stub de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-121">Remove the stub version of the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="6c662-122">Ouvrez le **Console d’Administration de BizTalk Server** comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur  **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6c662-122">Open the **BizTalk Server Administration Console** as follows: Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6c662-123">Dans le **Console d’Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, avec le bouton droit **BTSScn.SO.CustomerService**, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="6c662-123">In the **BizTalk Server Administration Console**, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, right-click **BTSScn.SO.CustomerService**, and then click **Stop**.</span></span> <span data-ttu-id="6c662-124">Dans le **arrêter l’Application** boîte de dialogue, sélectionnez **arrêt complet - arrêter les Instances**, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="6c662-124">In the **Stop Application** dialog box, select **Full Stop - Terminate Instances**, and then click **Stop**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-125">Il n'est pas nécessaire de supprimer la version stub pour installer les versions d'adaptateur et Inline.</span><span class="sxs-lookup"><span data-stu-id="6c662-125">You don't need to remove the stub version for installing the inline and adapter versions.</span></span> <span data-ttu-id="6c662-126">Si vous souhaitez rassembler toutes les versions, ignorez cette étape.</span><span class="sxs-lookup"><span data-stu-id="6c662-126">If you want to put all the versions together, you should skip this step.</span></span>  
  
3.  <span data-ttu-id="6c662-127">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6c662-127">Open a command prompt, type the following command, and then press ENTER.</span></span> <span data-ttu-id="6c662-128">Cette commande définit l'environnement d'exécution de scripts par défaut sur CScript.exe :</span><span class="sxs-lookup"><span data-stu-id="6c662-128">This command changes the default script host to CScript.exe:</span></span>  
  
    -   `cscript /H:CScript`  
  
4.  <span data-ttu-id="6c662-129">À l'invite de commandes, accédez au répertoire %BTSSolutonsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="6c662-129">At the command prompt, change the current directory to %BTSSolutonsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER:</span></span>  
  
    -   `UnEnlistStub.vbs`  
  
5.  <span data-ttu-id="6c662-130">À l'invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="6c662-130">At the command prompt, type the following command, and then press ENTER:</span></span>  
  
    -   `UndeployStub.vbs`  
  
6.  <span data-ttu-id="6c662-131">À l'invite de commandes, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6c662-131">At the command prompt, run the following command</span></span>  
  
     <span data-ttu-id="6c662-132">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span><span class="sxs-lookup"><span data-stu-id="6c662-132">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span></span>  
  
     <span data-ttu-id="6c662-133">Cette opération définit le chemin d'accès des utilitaires BAM.</span><span class="sxs-lookup"><span data-stu-id="6c662-133">This sets the path to find the BAM utilities.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-134">Si vous utilisez un ordinateur 64 bits, tapez `%ProgramFiles(x86)%` au lieu de `%ProgramFiles%`.</span><span class="sxs-lookup"><span data-stu-id="6c662-134">If you are using a 64-bit computer, type `%ProgramFiles(x86)%` instead of `%ProgramFiles%`.</span></span>  
  
7.  <span data-ttu-id="6c662-135">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\BAM, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6c662-135">At the command prompt, change the directory to %BTSSolutionsPath%\SO\BTSSoln\BAM, and then run the following command:</span></span>  
  
    -   `bm remove-all -DefinitionFile:ServiceLevelTracking.xml`  
  
8.  <span data-ttu-id="6c662-136">À l’invite de commandes, accédez au répertoire \< *unique Sign-On installer annuaire d’entreprise*\>, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6c662-136">At the command prompt, change the directory to \<*Enterprise Single Sign-On Install Directory*\>, and then run the following command:</span></span>  
  
    -   `ssomanage -tickets no no`  
  
9. <span data-ttu-id="6c662-137">À l'invite de commandes, exécutez la commande suivante pour supprimer l'application associée SSO WoodgroveBank.CustomerService :</span><span class="sxs-lookup"><span data-stu-id="6c662-137">At the command prompt, run the following command to delete the WoodgroveBank.CustomerService SSO Affiliated application:</span></span>  
  
    -   `ssomanage -deleteapp WoodgroveBank.CustomerService`  
  
10. <span data-ttu-id="6c662-138">À l'invite de commandes, exécutez les commandes suivantes pour supprimer les sites Web utilisés par la version stub.</span><span class="sxs-lookup"><span data-stu-id="6c662-138">At the command prompt, run the following commands to delete the Web sites used by the stub version.</span></span> <span data-ttu-id="6c662-139">Pour plus d’informations sur iisvdir.vbs, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span><span class="sxs-lookup"><span data-stu-id="6c662-139">For more information about iisvdir.vbs, see the Microsoft TechNet Web site at [http://go.microsoft.com/fwlink/?LinkId=67830](http://go.microsoft.com/fwlink/?LinkId=67830).</span></span>  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Stub`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions`  
  
    -   `iisvdir /delete W3SVC/1/ROOT/Microsoft.Samples.BizTalk.WoodgroveBank.StubPaymentTracker`  
  
11. <span data-ttu-id="6c662-140">Démarrez le Gestionnaire des Services Internet (IIS) comme suit : cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **les outils d’Administration**, puis cliquez sur **Internet Information Services (IIS) Manager**.</span><span class="sxs-lookup"><span data-stu-id="6c662-140">Start Internet Information Services (IIS) Manager as follows: Click **Start**, point to **All Programs**, point to **Administration Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
    -   <span data-ttu-id="6c662-141">Développez le **Pools d’applications**, cliquez sur le pool d’applications que vous avez créé pour les applications Web précédentes, cliquez sur **supprimer**, puis cliquez sur **OK** dans la confirmation boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c662-141">Expand the **Application Pools**, right-click the application pool you crated for the previous Web applications, click **Delete**, and then click **OK** in the confirmation dialog box.</span></span>  
  
12. <span data-ttu-id="6c662-142">Cliquez sur **Démarrer**, pointez sur **le panneau de configuration**, cliquez sur **Ajout / Suppression de programmes**, puis désinstallez le Client IBM WebSphere MQ pour Windows.</span><span class="sxs-lookup"><span data-stu-id="6c662-142">Click **Start**, point to **Control Panel**, click **Add or Remove Programs**, and then uninstall the IBM WebSphere MQ Client for Windows.</span></span>  
  
13. <span data-ttu-id="6c662-143">Démarrer **invite de commandes Visual Studio** , puis exécutez la commande suivante pour supprimer le fichier amqmdnet.dll que vous avez installé pour la version stub.</span><span class="sxs-lookup"><span data-stu-id="6c662-143">Start **Visual Studio Command Prompt** and then run the following command to delete the amqmdnet.dll you installed for the stub version.</span></span>  
  
    -   `gacutil /u amqmdnet`  
  
##  <a name="step5"></a><span data-ttu-id="6c662-144">Préparation des systèmes principaux pour la Solution orientée services pour accéder à</span><span class="sxs-lookup"><span data-stu-id="6c662-144">Prepare the back-end systems for the Service Oriented Solution to access</span></span>  
  
1.  <span data-ttu-id="6c662-145">Installez IBM WebSphere MQ pour Windows Server sur l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="6c662-145">Install IBM WebSphere MQ for Windows Server on the local computer.</span></span>  
  
    1.  <span data-ttu-id="6c662-146">Conservez tous les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c662-146">Keep all the default settings.</span></span> <span data-ttu-id="6c662-147">Configurer le **Configuration par défaut** à la fin de la **préparation de WebSphere MQ Assistant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-147">Set up the **Default Configuration** at the end of the **Prepare WebSphere MQ Wizard**.</span></span> <span data-ttu-id="6c662-148">Le Gestionnaire de file d’attente est nommé QM_\<*nom de votre ordinateur*\>.</span><span class="sxs-lookup"><span data-stu-id="6c662-148">The queue manager is named as QM_\<*your computer name*\>.</span></span>  
  
    2.  <span data-ttu-id="6c662-149">Installez le Fix Pack 10 (CSD10).</span><span class="sxs-lookup"><span data-stu-id="6c662-149">Install the Fix Pack 10 (CSD10).</span></span> <span data-ttu-id="6c662-150">Conservez tous les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c662-150">Keep all the default settings.</span></span>  
  
2.  <span data-ttu-id="6c662-151">Installez MQSeries Agent.</span><span class="sxs-lookup"><span data-stu-id="6c662-151">Install the MQSeries Agent.</span></span>  
  
    1.  <span data-ttu-id="6c662-152">Réexécutez le programme d’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6c662-152">Rerun the BizTalk Server setup program.</span></span>  
  
    2.  <span data-ttu-id="6c662-153">Sur le **Maintenance du programme** page, sélectionnez **modifier**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-153">On the **Program Maintenance** page, select **Modify**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="6c662-154">Sur le **Installation des composants** page, développez le **des logiciels supplémentaires** nœud et sélectionnez **MQSeries Agent**.</span><span class="sxs-lookup"><span data-stu-id="6c662-154">On the **Component Installation** page, expand the **Additional Software** node, and then select **MQSeries Agent**.</span></span>  
  
    4.  <span data-ttu-id="6c662-155">Sur le **achèvement** , assurez-vous que **lancer l’Assistant de Configuration de BizTalk MQSeries Agent** n’est pas sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6c662-155">On the **Completion** page, make sure that **Launch BizTalk MQSeries Agent Configuration Wizard** is not selected.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-156">Le **MQSeries Agent** case à cocher est activée uniquement après l’IBM WebSphere MQ pour Windows est installé.</span><span class="sxs-lookup"><span data-stu-id="6c662-156">The **MQSeries Agent** check box is activated only after the IBM WebSphere MQ for Windows is installed.</span></span>  
  
3.  <span data-ttu-id="6c662-157">Ouvrir un **invite de commandes Visual Studio**, remplacez le répertoire par le \< *répertoire d’Installation IBM MQSeries*\>dossier \bin, puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="6c662-157">Open a **Visual Studio Command Prompt**, change the directory to the \<*IBM MQSeries Installation Directory*\>\bin folder, and then run the following command:</span></span>  
  
    -   `gacutil /i amqmdnet.dll`  
  
4.  <span data-ttu-id="6c662-158">Installez Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] si vous souhaitez installer Microsoft Host Integration Server 2004 pour accéder au macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-158">Install Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] if you want to install Microsoft Host Integration Server 2004 to access the mainframe.</span></span> <span data-ttu-id="6c662-159">Le programme d’installation, sur le **Options** page, sélectionnez **Visual c# .NET**, puis désactivez les autres cases à cocher des composants.</span><span class="sxs-lookup"><span data-stu-id="6c662-159">In the setup program, on the **Options** page, select **Visual C# .NET**, and then clear other components checkboxes.</span></span> <span data-ttu-id="6c662-160">Vous n’avez pas besoin d’installer les autres composants que le **Visual c# .NET**.</span><span class="sxs-lookup"><span data-stu-id="6c662-160">You don't need to install other components than the **Visual C# .NET**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-161">Le Concepteur TI inclus dans Host Integration Server 2004 requiert [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c662-161">The TI Designer in Host Integration Server 2004 requires [!INCLUDE[btsVStudioNet2003](../includes/btsvstudionet2003-md.md)].</span></span>  
  
5.  <span data-ttu-id="6c662-162">Installez et configurez Microsoft Host Integration Server 2004 si vous avez un macroordinateur accessible.</span><span class="sxs-lookup"><span data-stu-id="6c662-162">Install and configure Microsoft Host Integration Server 2004 if you have a mainframe to be accessed.</span></span> <span data-ttu-id="6c662-163">Conservez tous les paramètres par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c662-163">Keep all the default settings.</span></span>  
  
#### <a name="create-the-mqseries-queues"></a><span data-ttu-id="6c662-164">Créer les files d’attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="6c662-164">Create the MQSeries queues</span></span>  
  
1.  <span data-ttu-id="6c662-165">Ouvrez WebSphere MQ Explorer, développez **gestionnaires de file d’attente**, puis développez le Gestionnaire de file d’attente dans laquelle vous souhaitez créer les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="6c662-165">Open the WebSphere MQ Explorer, expand **Queue Managers**, and then expand the queue manager in which you want to create the queues.</span></span> <span data-ttu-id="6c662-166">En règle générale, un gestionnaire de file d’attente est nommé QM_\<*nom de votre ordinateur*\>.</span><span class="sxs-lookup"><span data-stu-id="6c662-166">Typically, a queue manager is named as QM_\<*your computer name*\>.</span></span>  
  
2.  <span data-ttu-id="6c662-167">Dans WebSphere MQ Explorer, cliquez sur **les files d’attente**, pointez sur **nouveau**, cliquez sur **file d’attente locale**, puis créer les files d’attente locales suivantes pour la version de l’adaptateur de le solution :</span><span class="sxs-lookup"><span data-stu-id="6c662-167">In the WebSphere MQ Explorer, right-click **Queues**, point to **New**, click **Local Queue**, and then create the following local queues for the adapter version of the solution:</span></span>  
  
    -   <span data-ttu-id="6c662-168">AdapterSOAInputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-168">AdapterSOAInputQueue</span></span>  
  
    -   <span data-ttu-id="6c662-169">AdapterSOAOutputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-169">AdapterSOAOutputQueue</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-170">Les files d'attente peuvent partager un cluster MQSeries (facultatif).</span><span class="sxs-lookup"><span data-stu-id="6c662-170">The queues can share an MQSeries cluster, but they are not required to do so.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-171">Les noms des gestionnaires de file d'attente MQSeries et les noms des files d'attente respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="6c662-171">MQSeries queue manager names and queue names are case sensitive.</span></span>  
  
3.  <span data-ttu-id="6c662-172">Répétez l'étape précédente pour créer les files d'attente locales suivantes pour la version Inline :</span><span class="sxs-lookup"><span data-stu-id="6c662-172">Repeat the previous step to create the following local queues for the inline version:</span></span>  
  
    -   <span data-ttu-id="6c662-173">InlineSOAOutputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-173">InlineSOAOutputQueue</span></span>  
  
    -   <span data-ttu-id="6c662-174">InlineSOAInputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-174">InlineSOAInputQueue</span></span>  
  
4.  <span data-ttu-id="6c662-175">Répétez l'étape précédente pour créer les files d'attente locales suivantes pour le simulateur Payment Tracker</span><span class="sxs-lookup"><span data-stu-id="6c662-175">Repeat the previous step to create the following local queues for the Payment Tracker simulator.</span></span> <span data-ttu-id="6c662-176">(ce dispositif est utilisé à la fois dans la version d'adaptateur et dans la version Inline) :</span><span class="sxs-lookup"><span data-stu-id="6c662-176">(The Payment Tracker simulator is used in both the adapter and inline versions):</span></span>  
  
    -   <span data-ttu-id="6c662-177">LastPaymentsInputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-177">LastPaymentsInputQueue</span></span>  
  
    -   <span data-ttu-id="6c662-178">LastPaymentsOutputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-178">LastPaymentsOutputQueue</span></span>  
  
#### <a name="complete-configuration-of-the-mqseries-adapter"></a><span data-ttu-id="6c662-179">Terminer la configuration de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="6c662-179">Complete configuration of the MQSeries adapter</span></span>  
  
1.  <span data-ttu-id="6c662-180">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Assistant Configuration de BizTalk MQSeries Agent**.</span><span class="sxs-lookup"><span data-stu-id="6c662-180">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk MQSeries Agent Configuration Wizard**.</span></span>  
  
2.  <span data-ttu-id="6c662-181">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-181">On the **Welcome** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="6c662-182">Sur le **identité de l’Application** page, sélectionnez **cet utilisateur**, puis entrez le nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6c662-182">On the **Application Identity** page, select **This User**, and then enter the user name and password.</span></span> <span data-ttu-id="6c662-183">L'application COM+ pour MQSeries Agent est exécutée sous ce compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-183">The COM+ application for the MQSeries Agent will run under this user account.</span></span> <span data-ttu-id="6c662-184">Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-184">For this walkthrough, use the same user account that the BizTalk service is using.</span></span> <span data-ttu-id="6c662-185">S’il n’est pas, les comptes d’utilisateur pour les services BizTalk hébergeant l’adaptateur MQSeries doivent être ajoutés à la **CreatorOwner** rôle de l’application COM +.</span><span class="sxs-lookup"><span data-stu-id="6c662-185">If it is not, the user accounts for BizTalk services hosting the MQSeries Adapter must be added to the **CreatorOwner** role of the COM+ application.</span></span>  
  
4.  <span data-ttu-id="6c662-186">Cliquez sur **Oui** sur la **MQSConfigWiz** boîte de dialogue, si vous y êtes invité que le compte d’utilisateur que vous avez entré à l’étape précédente a des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-186">Click **Yes** on the **MQSConfigWiz** dialog box, if prompted that the user account that you entered in the previous step has the administrative privilege.</span></span>  
  
5.  <span data-ttu-id="6c662-187">Sur le **nom du rôle** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-187">On the **Name of Role** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="6c662-188">Sur le **création de l’Application MQSAgent COM +** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.</span><span class="sxs-lookup"><span data-stu-id="6c662-188">On the **Creating the MQSAgent COM+ Application** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="configure-the-mainframe-cics-application"></a><span data-ttu-id="6c662-189">Configurer l’application CICS du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-189">Configure the mainframe CICS application</span></span>  
  
1.  <span data-ttu-id="6c662-190">À l'aide du Bloc-notes, ouvrez le fichier bizcbl.txt, ainsi que le fichier associé MainFrameProgramVTCS2Description.txt, dans le dossier %BTSSolutionsPath%\SO\MFAccess\HISTIComponent, puis passez en revue leur contenu.</span><span class="sxs-lookup"><span data-stu-id="6c662-190">Using Notepad, open the bizcbl.txt and its "copy book" (MainFrameProgramVTCS2Description.txt) in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then review the contents.</span></span>  
  
    -   <span data-ttu-id="6c662-191">Bizcbl.txt inclut la procédure COBOL qui renvoie les relevés de compte aléatoires d'après une entrée de numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="6c662-191">Bizcbl.txt includes the COBOL procedure returning the randomized account statements from account number input.</span></span>  
  
    -   <span data-ttu-id="6c662-192">Le fichier MainFrameProgramVTCS2Description.txt contient la COMMAREA qui décrit les informations des données d'entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="6c662-192">MainFrameProgramVTCS2Descriptoin.txt contains COMMAREA which describes the input and output data information.</span></span> <span data-ttu-id="6c662-193">La COMMAREA constitue un bloc de mémoire contiguë servant à échanger des données entre les programmes appelés et les programmes appelants.</span><span class="sxs-lookup"><span data-stu-id="6c662-193">COMMAREA is a block of contiguous memory used to pass data back and forth between called and calling programs.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-194">Vous pouvez également utiliser le livre de copie pour générer le fichier de métadonnées de Transaction Integrator (TI) à l’aide de Visual Studio avec le concepteur TI plug-in.</span><span class="sxs-lookup"><span data-stu-id="6c662-194">You can also use the copy book to generate the Transaction Integrator (TI) metadata file using Visual Studio with the TI Designer plug-in.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-195">Bien que les étapes suivantes soient essentielles à la réussite du déploiement, elles ne sont généralement pas effectuées par un développeur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6c662-195">Although the following steps are crucial to the successful deployment, they are not usually performed by the BizTalk Server developer.</span></span> <span data-ttu-id="6c662-196">Il revient au personnel chargé de l'administration du macroordinateur de configurer correctement l'environnement du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-196">You must rely on the mainframe personnel to properly configure the mainframe environment.</span></span> <span data-ttu-id="6c662-197">Les logiciels requis dans le cadre de cette procédure pas à pas sont généralement installés dans la plupart des environnements de macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-197">The software required for this walkthrough is usually installed in the most mainframe environments.</span></span> <span data-ttu-id="6c662-198">Pour plus d’informations sur l’environnement de système d’exploitation minimale macroordinateur, consultez la documentation de Host Integration Server.</span><span class="sxs-lookup"><span data-stu-id="6c662-198">For more information about the minimum mainframe operating system environment, see the Host Integration Server documentation.</span></span>  
  
2.  <span data-ttu-id="6c662-199">Copiez le code COBOL sur l'ordinateur hôte via FTP par exemple.</span><span class="sxs-lookup"><span data-stu-id="6c662-199">Copy the COBOL code to the host by method like FTP.</span></span>  
  
3.  <span data-ttu-id="6c662-200">Compilez le code COBOL et le fichier associé.</span><span class="sxs-lookup"><span data-stu-id="6c662-200">Compile the COBOL code and copy book.</span></span> <span data-ttu-id="6c662-201">Le code suivant illustre un exemple de langage JCL (Job Control Language) utilisé par le compilateur COBOL.</span><span class="sxs-lookup"><span data-stu-id="6c662-201">The following code shows a sample of Job Control Language (JCL) for the COBOL compiler.</span></span>  
  
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
  
4.  <span data-ttu-id="6c662-202">Éditez les liens de la source compilée pour créer l'exécutable.</span><span class="sxs-lookup"><span data-stu-id="6c662-202">Link edit the compiled source to create the executable.</span></span> <span data-ttu-id="6c662-203">Le code suivant montre un exemple de langage JCL pour l'édition de liens COBOL.</span><span class="sxs-lookup"><span data-stu-id="6c662-203">The following code shows a sample of JCL for COBOL link edit.</span></span>  
  
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
  
5.  <span data-ttu-id="6c662-204">Configurez l'application de macroordinateur CICS.</span><span class="sxs-lookup"><span data-stu-id="6c662-204">Configure the CICS mainframe application.</span></span>  
  
    -   <span data-ttu-id="6c662-205">Au cours de cette étape, le programmateur système du macroordinateur ou le développeur CICS doit installer les définitions de ressource relatives au service TCP/IP, aux sessions, aux connexions, aux transactions et aux programmes.</span><span class="sxs-lookup"><span data-stu-id="6c662-205">In this step, the mainframe systems programmer or CICS developer must install TCPIPSERVICE, Session, Connection, Transaction, and Program resource definitions.</span></span>  
  
    -   <span data-ttu-id="6c662-206">Consultez les administrateurs du macroordinateur pour obtenir l'adresse IP, le numéro de port et le nom de lien au programme auxquels accéder.</span><span class="sxs-lookup"><span data-stu-id="6c662-206">You should consult with mainframe administrators to get an IP address, port number, and a Link to Program name that you can access.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c662-207">Cette procédure pas à pas implique que le macroordinateur exploite un serveur d'applications CICS et que le modèle de programmation de la transaction soit TCP/IP (lien ELM [Enhanced Listener Mode]).</span><span class="sxs-lookup"><span data-stu-id="6c662-207">This walkthrough assumes that the mainframe uses a CICS application server and that the programming model for the transaction is TCP/IP (Enhanced Listener Mode (ELM) Link).</span></span>  
  
##  <a name="step7"></a><span data-ttu-id="6c662-208">Configurer le serveur Web pour SSL Secure Socket Layers)</span><span class="sxs-lookup"><span data-stu-id="6c662-208">Configure the Web server for Secure Socket Layers (SSL)</span></span>  
  
#### <a name="install-certificate-services"></a><span data-ttu-id="6c662-209">Installer les Services de certificats</span><span class="sxs-lookup"><span data-stu-id="6c662-209">Install Certificate Services</span></span>  
  
1.  <span data-ttu-id="6c662-210">Cliquez sur **Démarrer**, pointez sur **le panneau de configuration**, puis cliquez sur **Ajout / Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="6c662-210">Click **Start**, point to **Control Panel**, and then click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="6c662-211">Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="6c662-211">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="6c662-212">Dans le **Assistant Composants de Windows**, sélectionnez le **les Services de certificats**, cliquez sur **suivant**, puis suivez l’à l’écran des instructions pour terminer l’installation.</span><span class="sxs-lookup"><span data-stu-id="6c662-212">In the **Windows Components Wizard**, select the **Certificate Services**, click **Next**, and then follow the on-screen instructions to complete the installation.</span></span>  
  
#### <a name="create-a-certificate-request"></a><span data-ttu-id="6c662-213">Créer une demande de certificat</span><span class="sxs-lookup"><span data-stu-id="6c662-213">Create a certificate request</span></span>  
  
1.  <span data-ttu-id="6c662-214">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, cliquez sur **propriétés** , cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **certificat de serveur**.</span><span class="sxs-lookup"><span data-stu-id="6c662-214">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, click **Properties**, click the **Directory Security** tab, and then click **Server Certificate**.</span></span>  
  
2.  <span data-ttu-id="6c662-215">Sur le **Bienvenue** page de la **Assistant certificat de serveur Web**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-215">On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.</span></span>  
  
3.  <span data-ttu-id="6c662-216">Sur le **certificat de Service** page, sélectionnez **créer un nouveau certificat**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-216">On the **Service Certificate** page, select **Create a new certificate**, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="6c662-217">Sur le **demande ultérieure ou immédiate** , cliquez sur **préparer la demande maintenant, mais l’envoyer ultérieurement**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-217">On the **Delayed or Immediate Request** page, click **Prepare the request now, but send it later**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="6c662-218">Sur le **nom et les paramètres de sécurité** page, conservez tous les paramètres par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-218">On the **Name and Security Settings** page, keep all the default settings, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="6c662-219">Sur le **informations de l’organisation** page, tapez votre organisation et noms de l’unité d’organisation, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-219">On the **Organization Information** page, type your company's organization and organizational unit names, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="6c662-220">Sur le **nom commun de votre Site** , tapez le nom de votre ordinateur dans le **nom commun** zone, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-220">On the **Your Site's Common Name** page, type your computer name in the **Common name** box, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="6c662-221">Sur le **informations géographiques** page, remplir vos informations géographiques, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-221">On the **Geographical Information** page, fill out your geographical information, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="6c662-222">Sur le **nom du fichier de demande de certificat** , tapez `c:\certreq.txt` dans les **nom de fichier** zone, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-222">On the **Certificate Request File Name** page, type `c:\certreq.txt` in the **File name** box, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="6c662-223">Sur le **résumé du fichier de demande** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.</span><span class="sxs-lookup"><span data-stu-id="6c662-223">On the **Request File Summary** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="submit-the-certificate-request-to-the-certification-authority"></a><span data-ttu-id="6c662-224">Soumettre la demande de certificat de l’autorité de Certification</span><span class="sxs-lookup"><span data-stu-id="6c662-224">Submit the certificate request to the Certification Authority</span></span>  
  
1.  <span data-ttu-id="6c662-225">Dans Internet Explorer, dans la zone Adresse, tapez `http://localhost/certsrvt`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6c662-225">In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="6c662-226">Sur le **Bienvenue** , cliquez sur **demander un certificat**, puis cliquez sur **demande de certificat avancée** sur la **demander un certificat** page.</span><span class="sxs-lookup"><span data-stu-id="6c662-226">On the **Welcome** page, click **Request a Certificate**, and then click **Advanced certificate request** on the **Request a Certificate** page.</span></span>  
  
3.  <span data-ttu-id="6c662-227">Sur le **demande de certificat avancée** , cliquez sur **soumettre une demande de certificat à l’aide de base64 encodé PKCS #10 ou une demande de renouvellement à l’aide d’un fichier de PKCS #7 codé en base64**.</span><span class="sxs-lookup"><span data-stu-id="6c662-227">On the **Advanced Certificate Request** page, click **Submit a certificate request using a base64 encoded PKCS #10 file or a renewal request using a base64 encoded PKCS #7 file**.</span></span>  
  
4.  <span data-ttu-id="6c662-228">Copiez le texte à partir de la c:\certreq.txt que vous avez créé dans la procédure « pour créer d’une demande de certificat », collez-le dans le **demande enregistrée** zone sur le **soumettre une demande de certificat ou une demande de renouvellement** page, puis cliquez sur **Submit**.</span><span class="sxs-lookup"><span data-stu-id="6c662-228">Copy all the text from the c:\certreq.txt that you created in the procedure "To create a certificate request", paste it to the **Saved Request** box on the **Submit a Certificate Request or Renewal Request** page, and then click **Submit**.</span></span>  
  
#### <a name="issue-a-certificate-using-certification-authority-management-tool"></a><span data-ttu-id="6c662-229">Émettre un certificat à l’aide d’outil de gestion d’autorité de Certification</span><span class="sxs-lookup"><span data-stu-id="6c662-229">Issue a certificate using Certification Authority management tool</span></span>  
  
1.  <span data-ttu-id="6c662-230">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **autorité de Certification**.</span><span class="sxs-lookup"><span data-stu-id="6c662-230">Click **Start**, point to **Administrative Tools**, and then click **Certification Authority**.</span></span>  
  
2.  <span data-ttu-id="6c662-231">Dans le **autorité de Certification** de la console, développez le nom de votre autorité de certification, le **demande en attente**, avec le bouton droit de la demande de certificat que vous avez envoyé à l’étape précédente, le point pour **toutes les tâches**, puis cliquez sur **problème**.</span><span class="sxs-lookup"><span data-stu-id="6c662-231">In the **Certification Authority** console, expand your certification authority's name, expand the **Pending Request**, right-click the certificate request that you submitted in the previous step, point to **All Tasks**, and then click **Issue**.</span></span>  
  
3.  <span data-ttu-id="6c662-232">Fermer le **autorité de Certification** console.</span><span class="sxs-lookup"><span data-stu-id="6c662-232">Close the **Certification Authority** console.</span></span>  
  
#### <a name="download-the-certificate-to-the-web-server"></a><span data-ttu-id="6c662-233">Téléchargez le certificat sur le serveur Web</span><span class="sxs-lookup"><span data-stu-id="6c662-233">Download the certificate to the Web server</span></span>  
  
1.  <span data-ttu-id="6c662-234">Dans Internet Explorer, dans la zone Adresse, tapez `http://localhost/certsrvt`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6c662-234">In Internet Explorer, in the Address box, type `http://localhost/certsrvt`, and then press ENTER.</span></span>  
  
2.  <span data-ttu-id="6c662-235">Sur le **Bienvenue** , cliquez sur **afficher l’état d’une demande de certificat en attente**.</span><span class="sxs-lookup"><span data-stu-id="6c662-235">On the **Welcome** page, click **View the status of a pending certificate request**.</span></span>  
  
3.  <span data-ttu-id="6c662-236">Sur le **afficher l’état d’une demande de certificat en attente** , cliquez sur le certificat **demande** que vous avez créé dans la procédure « pour créer une demande de certificat ».</span><span class="sxs-lookup"><span data-stu-id="6c662-236">On the **View the Status of a Pending Certificate Request** page, click the certificate **request** that you created in the procedure "To create a certificate request".</span></span>  
  
4.  <span data-ttu-id="6c662-237">Sur le **délivré** page, sélectionnez un des schémas d’encodage, puis cliquez sur **télécharger le certificat**.</span><span class="sxs-lookup"><span data-stu-id="6c662-237">On the **Certificate Issued** page, select either of the encoding schemes, and then click **Download certificate**.</span></span>  
  
5.  <span data-ttu-id="6c662-238">Sur le **avertissement de sécurité** boîte de dialogue, cliquez sur **enregistrer**, puis enregistrez le certificat sous c:\certnew.cer.</span><span class="sxs-lookup"><span data-stu-id="6c662-238">On the **Security Warning** dialog box, click **Save**, and then save the certificate as c:\certnew.cer.</span></span>  
  
#### <a name="install-the-certificate-to-the-web-server"></a><span data-ttu-id="6c662-239">Installez le certificat pour le serveur Web</span><span class="sxs-lookup"><span data-stu-id="6c662-239">Install the certificate to the Web server</span></span>  
  
1.  <span data-ttu-id="6c662-240">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut** pour lequel vous avez créé la demande de certificat, puis Cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-240">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site** for which you created the certificate request, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="6c662-241">Sur le **propriétés** boîte de dialogue, cliquez sur le **sécurité du répertoire** onglet, puis cliquez sur **certificat de serveur**.</span><span class="sxs-lookup"><span data-stu-id="6c662-241">On the **Properties** dialog box, click the **Directory Security** tab, and then click **Server Certificate**.</span></span>  
  
3.  <span data-ttu-id="6c662-242">Sur le **Bienvenue** page de la **Assistant certificat de serveur Web**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-242">On the **Welcome** page of the **Web Server Certificate Wizard**, click **Next**.</span></span>  
  
4.  <span data-ttu-id="6c662-243">Sur le **demande de certificat en attente** page, sélectionnez **traiter la demande en attente et installer le certificat**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-243">On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="6c662-244">Sur le **traiter une demande en attente** , tapez `c:\certnew.cer` dans les **chemin d’accès et nom de fichier** zone de texte, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-244">On the **Process a Pending Request** page, type `c:\certnew.cer` in the **Path and file name** text box, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="6c662-245">Cliquez sur **suivant** sur la **Port SSL** , cliquez sur **suivant** sur la **résumé du certificat** page, puis cliquez sur **Terminer** sur la **Confirmation** page.</span><span class="sxs-lookup"><span data-stu-id="6c662-245">Click **Next** on the **SSL Port** page, click **Next** on the **Certificate Summery** page, and then click **Finish** on the **Confirmation** page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-246">Au cours de cette procédure pas à pas, il n'est pas nécessaire d'installer le certificat de serveur dans le magasin d'autorités de certification de racine de confiance de l'ordinateur local car les services de certificats et le serveur Web sont installés sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-246">In this walkthrough you don't need to install the server certificate to the Trusted Root Certification Authorities store on the local computer because both Certificate Services and Web server are installed on the same computer.</span></span>  
  
##  <a name="step9"></a><span data-ttu-id="6c662-247">Créer des services Web pour les systèmes back-end</span><span class="sxs-lookup"><span data-stu-id="6c662-247">Create the Web services for the back-end systems</span></span>  
  
1.  <span data-ttu-id="6c662-248">Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Poold’applications**.</span><span class="sxs-lookup"><span data-stu-id="6c662-248">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-249">La solution orientée services accède au macroordinateur via ce service Web.</span><span class="sxs-lookup"><span data-stu-id="6c662-249">The service oriented solution accesses the mainframe through this Web service.</span></span>  
  
2.  <span data-ttu-id="6c662-250">Sur le **Ajouter nouveau Pool d’applications** boîte de dialogue, entrez le **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c662-250">On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="6c662-251">Dans le **Gestionnaire des Services Internet (IIS)**, cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-251">In the **Internet Information Services (IIS) Manager**, right-click the application pool that you just created, and then select **Properties**.</span></span>  
  
4.  <span data-ttu-id="6c662-252">Sur le **propriétés** , cliquez sur le **identité** onglet, sélectionnez **Configurable**, entrez la **nom d’utilisateur** et **mot de passe** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c662-252">On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**.</span></span> <span data-ttu-id="6c662-253">Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-253">For this walkthrough, use the same user account that the BizTalk service is using.</span></span>  
  
#### <a name="create-the-pendingtransactions-web-service-for-runtime"></a><span data-ttu-id="6c662-254">Créer le service PendingTransactions Web pour l’exécution</span><span class="sxs-lookup"><span data-stu-id="6c662-254">Create the PendingTransactions Web service for runtime</span></span>  
  
1.  <span data-ttu-id="6c662-255">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-255">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-256">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :</span><span class="sxs-lookup"><span data-stu-id="6c662-256">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="6c662-257">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-257">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions</span></span>  
  
     <span data-ttu-id="6c662-258">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-258">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span></span>  
  
     <span data-ttu-id="6c662-259">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-259">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="6c662-260">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-260">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="6c662-261">Dans le **sécurité du répertoire** , cliquez sur **modifier** modifier **d’authentification et contrôle d’accès**.</span><span class="sxs-lookup"><span data-stu-id="6c662-261">In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**.</span></span> <span data-ttu-id="6c662-262">Sélectionnez **l’authentification de base (mot de passe est envoyé en texte clair)**et désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="6c662-262">Select **Basic authentication (password is sent in clear text)**, and clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="6c662-263">Cliquez sur **OK** pour fermer la **les méthodes d’authentification** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c662-263">Click **OK** to close the **Authentication Methods** dialog box.</span></span>  
  
    2.  <span data-ttu-id="6c662-264">Dans le **sécurité du répertoire** , cliquez sur **modifier** sous le **une Communication sécurisée** zone de groupe, puis vérifiez **requérir un canal sécurisé (SSL)**dans les **Communications sécurisées** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c662-264">In the **Directory Security** tab, click **Edit** under the **Secure Communication** group box, and then check **Require secure channel (SSL)** in the **Secure Communications** dialog box.</span></span>  
  
    3.  <span data-ttu-id="6c662-265">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** au pool d’applications que vous avez créé dans la procédure « pour créer un nouveau pool d’applications IIS pour les services Web Pending transactions ».</span><span class="sxs-lookup"><span data-stu-id="6c662-265">In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
#### <a name="create-the-pendingtransactions-web-service-for-development-environment"></a><span data-ttu-id="6c662-266">Créer le service PendingTransactions Web pour l’environnement de développement</span><span class="sxs-lookup"><span data-stu-id="6c662-266">Create the PendingTransactions Web service for development environment</span></span>  
  
1.  <span data-ttu-id="6c662-267">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-267">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-268">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :</span><span class="sxs-lookup"><span data-stu-id="6c662-268">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="6c662-269">Alias = PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-269">Alias = PendingTransactions</span></span>  
  
     <span data-ttu-id="6c662-270">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-270">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\MFAccess\PendingTransactions</span></span>  
  
     <span data-ttu-id="6c662-271">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-271">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="6c662-272">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, cliquez sur PendingTransactions, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-272">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click PendingTransactions, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="6c662-273">Dans le **sécurité du répertoire** , cliquez sur **modifier** modifier **d’authentification et contrôle d’accès**.</span><span class="sxs-lookup"><span data-stu-id="6c662-273">In the **Directory Security** tab, click **Edit** to modify **Authentication and access control**.</span></span> <span data-ttu-id="6c662-274">Sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="6c662-274">Select **Enable anonymous access**.</span></span> <span data-ttu-id="6c662-275">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="6c662-275">Click **OK** to exit.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c662-276">L'application Web PendingTransactions pour l'environnement de développement sera utilisée par [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6c662-276">The PendingTransactions Web application for development environment will be used by [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="6c662-277">Cette application Web n'est pas requise pour l'environnement de production.</span><span class="sxs-lookup"><span data-stu-id="6c662-277">You don't need this Web application for production environment.</span></span>  
  
    2.  <span data-ttu-id="6c662-278">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** au pool d’applications que vous avez créé dans la procédure « pour créer un nouveau pool d’applications IIS pour les services Web Pending transactions ».</span><span class="sxs-lookup"><span data-stu-id="6c662-278">In the **Virtual Directory** tab, set the **Application Pool** to the application pool that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
#### <a name="create-the-stub-sap-web-service"></a><span data-ttu-id="6c662-279">Créer le service Web SAP Stub</span><span class="sxs-lookup"><span data-stu-id="6c662-279">Create the Stub SAP Web service</span></span>  
  
1.  <span data-ttu-id="6c662-280">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-280">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-281">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web SAP stub :</span><span class="sxs-lookup"><span data-stu-id="6c662-281">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the stub SAP Web service:</span></span>  
  
     <span data-ttu-id="6c662-282">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span><span class="sxs-lookup"><span data-stu-id="6c662-282">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP</span></span>  
  
     <span data-ttu-id="6c662-283">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-283">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\SAP</span></span>  
  
     <span data-ttu-id="6c662-284">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-284">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="6c662-285">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c662-285">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="6c662-286">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> que vous avez créé dans la procédure « pour créer un nouveau serveur IIS pool d’applications pour les services Web Pending transactions ».</span><span class="sxs-lookup"><span data-stu-id="6c662-286">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> that you created in the procedure "To create a new IIS application pool for the Pending Transaction Web services".</span></span>  
  
    2.  <span data-ttu-id="6c662-287">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="6c662-287">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="6c662-288">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="6c662-288">Click **OK** to exit.</span></span>  
  
##  <a name="step11"></a><span data-ttu-id="6c662-289">Créer le composant TI pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-289">Create the TI component for the Service Oriented Solution</span></span>  
  
#### <a name="create-a-com-application-for-the-ti-component"></a><span data-ttu-id="6c662-290">Créer une application COM + pour le composant TI</span><span class="sxs-lookup"><span data-stu-id="6c662-290">Create a COM+ application for the TI component</span></span>  
  
1.  <span data-ttu-id="6c662-291">Ouvrez une invite de commandes, puis exécutez %systemroot%\system32\com\comexp.msc.</span><span class="sxs-lookup"><span data-stu-id="6c662-291">At a command prompt, run %systemroot%\system32\com\comexp.msc.</span></span>  
  
2.  <span data-ttu-id="6c662-292">Dans **Services de composants** de la console, développez **Services de composants**, développez **ordinateurs**, développez **poste**, avec le bouton droit  **L’Application COM +**, pointez sur **nouveau**, puis cliquez sur **Application**.</span><span class="sxs-lookup"><span data-stu-id="6c662-292">In **Component Services** console, expand **Component Services**, expand **Computers**, expand **My Computer**, right-click **COM+ Application**, point to **New**, and then click **Application**.</span></span>  
  
    1.  <span data-ttu-id="6c662-293">Sur le **Bienvenue** , cliquez sur **suivant**, puis cliquez sur **créer une application vide** sur la **installer ou créer une nouvelle Application** page.</span><span class="sxs-lookup"><span data-stu-id="6c662-293">On the **Welcome** page, click **Next**, and then click **Create an empty application** on the **Install or Create a New Application** page.</span></span>  
  
    2.  <span data-ttu-id="6c662-294">Type `BTSScn SO TI Component` dans les **Entrez un nom pour la nouvelle application** boîte, sélectionnez **application serveur** en tant que **type d’Activation**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-294">Type `BTSScn SO TI Component` in the **Enter a name for the new application** box, select **Server application** as **Activation type**, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="6c662-295">Dans le **compte** zone de groupe de la **définir l’identité Application** page, sélectionnez **cet utilisateur**, puis tapez le nom d’utilisateur et un mot de passe dans la **utilisateur**et **mot de passe** cases.</span><span class="sxs-lookup"><span data-stu-id="6c662-295">In the **Account** group box of the **Set Application Identity** page, select **This user**, and then type the user name and password in the **User** and **Password** boxes.</span></span> <span data-ttu-id="6c662-296">La nouvelle application COM+ sera exécutée sous ce compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-296">The new COM+ application will run under this user account.</span></span> <span data-ttu-id="6c662-297">Celui-ci doit appartenir au groupe d'utilisateurs HIS Runtime locaux.</span><span class="sxs-lookup"><span data-stu-id="6c662-297">This user account must be a member of local HIS Runtime Users group.</span></span> <span data-ttu-id="6c662-298">Dans le cadre de cette procédure pas à pas, vous devez utiliser le même compte d'utilisateur que celui utilisé par le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-298">For this walkthrough, use the same user account that the BizTalk service is using.</span></span>  
  
    4.  <span data-ttu-id="6c662-299">Sur le **ajouter des rôles d’Application** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-299">On the **Add Application Roles** page, click **Next**.</span></span>  
  
    5.  <span data-ttu-id="6c662-300">Sur le **ajouter des utilisateurs aux rôles** page, développez **CreatorOwner**, cliquez sur **utilisateurs**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="6c662-300">On the **Add Users to Roles** page, expand **CreatorOwner**, click **Users**, and then click **Add**.</span></span>  
  
    6.  <span data-ttu-id="6c662-301">Sur le **sélectionner des utilisateurs ou groupes** boîte de dialogue, sélectionnez un compte d’utilisateur qui sera utilisé pour accéder au macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-301">On the **Select Users or Groups** dialog box, select a user account that will be used for accessing the mainframe.</span></span> <span data-ttu-id="6c662-302">Dans le cadre de cette procédure pas à pas, ajoutez le compte local UserID.</span><span class="sxs-lookup"><span data-stu-id="6c662-302">For this walkthrough, add UserID local account.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c662-303">Pour accéder à la transaction CICS via le composant TI, vous pouvez utiliser l'application COM+ ou l'application Web hébergeant le composant d'accès à distance .NET.</span><span class="sxs-lookup"><span data-stu-id="6c662-303">To access the CICS transaction through the TI component, you can use the COM+ application or the Web application hosting the .NET Remoting component.</span></span> <span data-ttu-id="6c662-304">Cette procédure pas à pas utilise l'application COM+ et COM Interop pour permettre aux composants TI d'accéder au macroordinateur à des fins d'amélioration des performances.</span><span class="sxs-lookup"><span data-stu-id="6c662-304">This walkthrough uses the COM+ application and COM Interop for TI components to access the mainframe to improve performance.</span></span>  
  
    7.  <span data-ttu-id="6c662-305">Sur le **achèvement** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="6c662-305">On the **Completion** page, click **Finish**.</span></span>  
  
#### <a name="create-a-remote-environment-to-access-the-mainframe"></a><span data-ttu-id="6c662-306">Créer un environnement à distance pour accéder au macroordinateur</span><span class="sxs-lookup"><span data-stu-id="6c662-306">Create a Remote Environment to access the mainframe</span></span>  
  
1.  <span data-ttu-id="6c662-307">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Host Integration Server 2004**, puis cliquez sur **Gestionnaire TI**.</span><span class="sxs-lookup"><span data-stu-id="6c662-307">Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.</span></span>  
  
2.  <span data-ttu-id="6c662-308">Dans le **Gestionnaire TI** de la console, cliquez sur **intégrateur de transactions (Configuration)**, développez **traitement initié par Windows**, avec le bouton droit **à distance Environnements**, pointez sur **nouveau**, puis cliquez sur **environnement distant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-308">In the **TI Manager** console, click **Transaction Integrator (Configuration)**, expand **Windows Initiated Processing**, right-click **Remote Environments**, point to **New**, and then click **Remote Environment**.</span></span>  
  
    1.  <span data-ttu-id="6c662-309">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-309">On the **Welcome** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="6c662-310">Sur le **configurer un nouvel environnement distant** , tapez le **nom de l’Application à distance**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-310">On the **Configure a New Remote Environment** page, type the **Remote Application Name**, and then click **Next**.</span></span> <span data-ttu-id="6c662-311">Dans le cadre de cette procédure pas à pas, utilisez le nom Mainframe_TCP.</span><span class="sxs-lookup"><span data-stu-id="6c662-311">For this walkthrough, use Mainframe_TCP for the name.</span></span>  
  
    3.  <span data-ttu-id="6c662-312">Sur le **configurer l’environnement hôte et le modèle de programmation** page, sélectionnez **CICS** pour le **hôte cible** et **lien ELM** pour la  **Modèle de programmation**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-312">On the **Configure Host Environment and Programming Model** page, select **CICS** for the **Target host** and **ELM Link** for the **Programming model**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="6c662-313">Sur **le point de terminaison configurer TCP/IP** , tapez l’adresse IP du macroordinateur dans le **adresse IP/DNS** zone, puis cliquez sur **modifier** pour ajouter le numéro de port.</span><span class="sxs-lookup"><span data-stu-id="6c662-313">On **the Configure Endpoint TCP/IP** page, type the IP address for your mainframe in the **IP/DNS address** box, and then click **Edit** to add the port number.</span></span> <span data-ttu-id="6c662-314">Le HIS COM accèdera aux transactions via l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6c662-314">Your HIS COM will access the transactions through the endpoint address.</span></span>  
  
    5.  <span data-ttu-id="6c662-315">Sur le **achèvement** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="6c662-315">On the **Completion** page, click **Finish**.</span></span>  
  
#### <a name="create-the-ti-component-for-the-service-oriented-solution"></a><span data-ttu-id="6c662-316">Créer le composant TI pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-316">Create the TI Component for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="6c662-317">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Host Integration Server 2004**, puis cliquez sur **Gestionnaire TI**.</span><span class="sxs-lookup"><span data-stu-id="6c662-317">Click **Start**, point to **All Programs**, point to **Microsoft Host Integration Server 2004**, and then click **TI Manager**.</span></span>  
  
2.  <span data-ttu-id="6c662-318">Dans le **Gestionnaire TI** de la console, cliquez sur **intégrateur de transactions (Configuration)**, cliquez sur **traitement initié par Windows**, puis cliquez sur **objets**.</span><span class="sxs-lookup"><span data-stu-id="6c662-318">In the **TI Manager** console, click **Transaction Integrator (Configuration)**, click **Windows Initiated Processing**, and then click **Objects**.</span></span> <span data-ttu-id="6c662-319">Avec le bouton droit **objets**, cliquez sur **nouveau**, puis cliquez sur **objet**.</span><span class="sxs-lookup"><span data-stu-id="6c662-319">Right-click **Objects**, click **New**, and then click **Object**.</span></span>  
  
    1.  <span data-ttu-id="6c662-320">Sur le **Bienvenue** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-320">On the **Welcome** page, click **Next**.</span></span>  
  
    2.  <span data-ttu-id="6c662-321">Sur le **spécifier ou rechercher un objet** , cliquez sur **Parcourir**, choisissez l’objet SOHISTIUsingCOM.TLB dans le dossier %BTSSolutionsPath%\SO\MFAccess\HISTIComponent, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="6c662-321">On the **Specify Or Locate An Object** page, click **Browse**, choose the SOHISTIUsingCOM.TLB in the %BTSSolutionsPath%\SO\MFAccess\HISTIComponent folder, and then click **Next**.</span></span>  
  
    3.  <span data-ttu-id="6c662-322">Sur le **caractéristiques de l’environnement définir pour l’objet COM** page, sélectionnez **BTSScn SO TI Component** pour le **l’application COM +**, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="6c662-322">On the **Define Environment Characteristics for The COM Object** page, select **BTSScn SO TI Component** for the **COM+ application**, and then click **Next**.</span></span>  
  
    4.  <span data-ttu-id="6c662-323">Sur le **définir l’environnement distant** , sélectionnez l’environnement distant que vous avez créé dans la procédure précédente pour le **environnement distant, puis cliquez sur Suivant.**</span><span class="sxs-lookup"><span data-stu-id="6c662-323">On the **Define Remote Environment** page, select the remote environment that you created in the previous procedure for the **Remote environment, and then click Next.**</span></span>  
  
    5.  <span data-ttu-id="6c662-324">Sur le **création d’objets WIP** , cliquez sur **suivant**, puis cliquez sur **Terminer** sur la **achèvement** page.</span><span class="sxs-lookup"><span data-stu-id="6c662-324">On the **Creation of WIP Objects** page, click **Next**, and then click **Finish** on the **Completion** page.</span></span>  
  
#### <a name="test-the-connectivity-to-the-mainframe"></a><span data-ttu-id="6c662-325">Tester la connectivité au macroordinateur</span><span class="sxs-lookup"><span data-stu-id="6c662-325">Test the connectivity to the mainframe</span></span>  
  
1.  <span data-ttu-id="6c662-326">Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester, puis double-cliquez sur le fichier Interop.SOHISTIUsingCOM.dll.reg.</span><span class="sxs-lookup"><span data-stu-id="6c662-326">In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester folder, and then double-click the Interop.SOHISTIUsingCOM.dll.reg file.</span></span> <span data-ttu-id="6c662-327">Cette action a pour effet d'ajouter des valeurs correspondant à l'application HISTISimpleTester au Registre afin d'appeler le composant TI via le wrapper RCW (Runtime Callable Wrapper).</span><span class="sxs-lookup"><span data-stu-id="6c662-327">This adds registry values for the HISTISimpleTester application to call the TI component through the Runtime Callable Wrapper (RCW).</span></span>  
  
2.  <span data-ttu-id="6c662-328">Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\, puis exécutez SetupMFAccess.bat.</span><span class="sxs-lookup"><span data-stu-id="6c662-328">In Windows Explorer, browse to the %BTSSolutionsPath%\SO\MFAccess\ folder, and then run SetupMFAccess.bat.</span></span>  
  
3.  <span data-ttu-id="6c662-329">Dans l'Explorateur Windows, accédez au dossier %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug, puis exécutez BTSScnSOHISTIComponentSimpleTester.exe.</span><span class="sxs-lookup"><span data-stu-id="6c662-329">In Windows Explorer, navigate to the %BTSSolutionsPath%\SO\MFAccess\HISTISimpleTester\bin\Debug folder, and then run BTSScnSOHISTIComponentSimpleTester.exe.</span></span>  
  
    -   <span data-ttu-id="6c662-330">Dans l’application HISTISimpleTester, cliquez sur **appeler le programme du macroordinateur - utiliser COM**.</span><span class="sxs-lookup"><span data-stu-id="6c662-330">In the HISTISimpleTester application, click **Call Mainframe Program - Using COM**.</span></span> <span data-ttu-id="6c662-331">Cinq enregistrements sont renvoyés de l'application COBOL exécutée sur le macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-331">It returns five records from the COBOL application running on the mainframe.</span></span>  
  
##  <a name="step13"></a><span data-ttu-id="6c662-332">Créer les répertoires virtuels pour l’orchestration des services Web</span><span class="sxs-lookup"><span data-stu-id="6c662-332">Create the virtual directories for the orchestration Web services</span></span>  
  
1.  <span data-ttu-id="6c662-333">Dans le **Gestionnaire des Services Internet (IIS)**, avec le bouton droit **Pools d’applications**, sélectionnez **nouveau**, puis sélectionnez **Poold’applications**.</span><span class="sxs-lookup"><span data-stu-id="6c662-333">In the **Internet Information Services (IIS) Manager**, right-click **Application Pools**, select **New**, and then select **Application Pool**.</span></span>  
  
    1.  <span data-ttu-id="6c662-334">Sur le **Ajouter nouveau Pool d’applications** boîte de dialogue, entrez le **ID du pool d’applications** (toute valeur), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c662-334">On the **Add New Application Pool** dialog box, enter the **Application pool ID** (any value), and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="6c662-335">Cliquez sur le pool d’applications que vous venez de créée, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-335">Right-click the application pool that you just created, and then select **Properties**.</span></span>  
  
    3.  <span data-ttu-id="6c662-336">Sur le **propriétés** , cliquez sur le **identité** onglet, sélectionnez **Configurable**, entrez la **nom d’utilisateur** et **mot de passe** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6c662-336">On the **Properties** page, click the **Identity** tab, select **Configurable**, enter the **User name** and **Password**, and then click **OK**.</span></span> <span data-ttu-id="6c662-337">Pour cette procédure pas à pas utiliser le même compte d’utilisateur qui utilise le service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-337">For this walkthrough use the same user account that the BizTalk service is using.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-338">Cet utilisateur doit être autorisé à exécuter le service Web Orchestration Proxy et être ajouté au groupe Administrateurs BizTalk Server, Administrateurs de l'authentification unique ou Administrateurs d'applications associées à authentification unique.</span><span class="sxs-lookup"><span data-stu-id="6c662-338">This user must have permission to execute the Orchestration Proxy Web service, and must be added to one of the BizTalk Server Administrators, SSO Administrators, or SSO Affiliated Administrators groups</span></span>  
  
2.  <span data-ttu-id="6c662-339">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-339">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-340">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version d’adaptateur :</span><span class="sxs-lookup"><span data-stu-id="6c662-340">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="6c662-341">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter</span><span class="sxs-lookup"><span data-stu-id="6c662-341">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter</span></span>  
  
     <span data-ttu-id="6c662-342">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter</span><span class="sxs-lookup"><span data-stu-id="6c662-342">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Adapter</span></span>  
  
     <span data-ttu-id="6c662-343">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-343">Access Permissions = Read, Run scripts</span></span>  
  
3.  <span data-ttu-id="6c662-344">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web,** développer le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c662-344">In the **Internet Information Services (IIS) Manager**, expand **Web Sites,** expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Adapter, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="6c662-345">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> que vous avez créé à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="6c662-345">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> that you created in the previous step.</span></span>  
  
    2.  <span data-ttu-id="6c662-346">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="6c662-346">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="6c662-347">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="6c662-347">Click **OK** to exit.</span></span>  
  
4.  <span data-ttu-id="6c662-348">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-348">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-349">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le proxy de service Web pour la version inline :</span><span class="sxs-lookup"><span data-stu-id="6c662-349">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for the proxy Web service for the inline version:</span></span>  
  
     <span data-ttu-id="6c662-350">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline</span><span class="sxs-lookup"><span data-stu-id="6c662-350">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline</span></span>  
  
     <span data-ttu-id="6c662-351">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline</span><span class="sxs-lookup"><span data-stu-id="6c662-351">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\OrchProxy\Inline</span></span>  
  
     <span data-ttu-id="6c662-352">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-352">Access Permissions = Read, Run scripts</span></span>  
  
5.  <span data-ttu-id="6c662-353">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c662-353">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.OrchProxy.Inline, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="6c662-354">Sur le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="6c662-354">On the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> you just created.</span></span>  
  
    2.  <span data-ttu-id="6c662-355">Cliquez sur **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, sélectionnez **uniquement l’authentification Windows intégrée activé**, puis désactivez les autres **d’accès d’authentification** cases à cocher.</span><span class="sxs-lookup"><span data-stu-id="6c662-355">Click **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, select **Only Integrated Windows Authentication enabled**, and then clear other **Authentication access** checkboxes.</span></span> <span data-ttu-id="6c662-356">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="6c662-356">Click **OK** to exit.</span></span>  
  
##  <a name="step15"></a><span data-ttu-id="6c662-357">Générez la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-357">Build the Service Oriented Solution</span></span>  
  
-   <span data-ttu-id="6c662-358">À l’invite de commandes, accédez au répertoire % BTSSolutionsPath%\SO\BTSSoln, tapez `SetupBTSSoln.bat`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6c662-358">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln, type `SetupBTSSoln.bat`, and then press ENTER.</span></span> <span data-ttu-id="6c662-359">La commande SetupBTSSoln.bat effectue les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c662-359">The SetupBTSSoln.bat performs the following tasks:</span></span>  
  
    -   <span data-ttu-id="6c662-360">Crée une clé de nom fort unique (SNK) pour signer les assemblys de la solution orientée services.</span><span class="sxs-lookup"><span data-stu-id="6c662-360">Creates a unique strong name key (SNK) for signing the assemblies of the SO Solution.</span></span>  
  
    -   <span data-ttu-id="6c662-361">extraction du jeton de clé publique de la clé de nom fort et mise à jour des fichiers de liaison avec le jeton public ;</span><span class="sxs-lookup"><span data-stu-id="6c662-361">Extracts the public key token from the SNK and updates the binding files with the public token.</span></span>  
  
    -   <span data-ttu-id="6c662-362">création de la solution orientée services ;</span><span class="sxs-lookup"><span data-stu-id="6c662-362">Builds the SO solution.</span></span>  
  
    -   <span data-ttu-id="6c662-363">création de SSOApplicationConfig dans le dossier %BTSSolutionsPath%\Common.</span><span class="sxs-lookup"><span data-stu-id="6c662-363">Builds the SSOApplicationConfig in the %BTSSolutionsPath%\Common folder.</span></span>  
  
##  <a name="step17"></a><span data-ttu-id="6c662-364">Créer des applications associées SSO</span><span class="sxs-lookup"><span data-stu-id="6c662-364">Create the SSO affiliate applications</span></span>  
  
1.  <span data-ttu-id="6c662-365">Ouvrez une invite de commandes, puis accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts.</span><span class="sxs-lookup"><span data-stu-id="6c662-365">Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
2.  <span data-ttu-id="6c662-366">À l'invite de commandes, ouvrez le fichier PendTransAffApp.xml à l'aide du Bloc-notes, puis passez-le en revue.</span><span class="sxs-lookup"><span data-stu-id="6c662-366">At the command prompt, open the PendTransAffApp.xml using Notepad, and review it.</span></span> <span data-ttu-id="6c662-367">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="6c662-367">No changes to this file are necessary.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-368">Le fichier PendTransAffApp.xml définit l'application associée SSO (WoodgroveBank.PendingTransactions) pour le système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-368">The PendTransAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PendingTransactions, for the Pending Transactions back-end system.</span></span> <span data-ttu-id="6c662-369">Il définit également les groupes d'utilisateurs et les groupes d'administration pour l'application associée SSO.</span><span class="sxs-lookup"><span data-stu-id="6c662-369">It also defines the user and administrative groups for the SSO affiliate application.</span></span> <span data-ttu-id="6c662-370">Pour cette procédure pas à pas, utilisez **utilisateurs d’applications BizTalk** et **administrateurs de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6c662-370">For this walkthrough, use **BizTalk Application Users** and **BizTalk Server Administrators**.</span></span>  
    >   
    >  <span data-ttu-id="6c662-371">Si vous souhaitez utiliser d’autres groupes pour l’application associée SSO, vous devez créer des groupes Windows (avec n’importe quel nom) dans Active Directory et modifier le **appAdminAccount** et **appUserAccount** nœuds dans le fichier PendTransAffApp.xml.</span><span class="sxs-lookup"><span data-stu-id="6c662-371">If you want to use different groups for the SSO affiliate application, you need to create Windows groups (with any name) in the Active Directory, and then change the **appAdminAccount** and **appUserAccount** nodes in the PendTransAffApp.xml.</span></span> <span data-ttu-id="6c662-372">Si vous faites cela, vous devez définir la valeur de **groupApp** attribut de **indicateurs** nœud sur « yes ».</span><span class="sxs-lookup"><span data-stu-id="6c662-372">If you do this, you should set the value for **groupApp** attribute of **flags** node to "yes".</span></span>  
    >   
    >  <span data-ttu-id="6c662-373">Pour plus d’informations sur les applications associées SSO, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).</span><span class="sxs-lookup"><span data-stu-id="6c662-373">For more information about SSO affiliate applications, see [SSO Affiliate Applications](../core/sso-affiliate-applications.md).</span></span>  
  
3.  <span data-ttu-id="6c662-374">À l'invite de commandes, ouvrez le fichier PendTransUserMap.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c662-374">At the command prompt, open the PendTransUserMap.xml file using Notepad, and then make the following edits:</span></span>  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-375">Le fichier PendTransUserMap.xml contient les mappages utilisateur du système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-375">The PendTransUserMap.xml file contains the user mappings for the Pending Transactions back-end system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-376">Pour le **externalUserId** nœud, utilisez l’ID utilisateur externe pour le système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-376">For the **externalUserId** node, use the external user ID for the Pending Transactions back-end system.</span></span> <span data-ttu-id="6c662-377">Dans le cadre de cette procédure pas à pas, utilisez l'ID externe UserID.</span><span class="sxs-lookup"><span data-stu-id="6c662-377">For this walkthrough, use UserID for the external ID.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-378">Pour le **windowsUserId** nœud, entrez le nom d’utilisateur nom qui le **externalUserId** sont mappés à.</span><span class="sxs-lookup"><span data-stu-id="6c662-378">For the **windowsUserId** node, enter the user name which the **externalUserId** will map to.</span></span> <span data-ttu-id="6c662-379">Vous pouvez utiliser un groupe de domaine et un compte d'utilisateur de domaine.</span><span class="sxs-lookup"><span data-stu-id="6c662-379">You can use both a domain group and a domain user account.</span></span> <span data-ttu-id="6c662-380">L'utilisateur doit faire partie d'un groupe autorisé à utiliser le système principal Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-380">This user must be a member of the group that will be allowed to use the Pending Transactions back-end system.</span></span> <span data-ttu-id="6c662-381">Dans le cadre de cette procédure pas à pas, utilisez le nom d'utilisateur du service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-381">For this walkthrough, use the user name of the BizTalk service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-382">Pour le **windowsDomain** nœud, entrez le nom de domaine de la **windowsUserId**.</span><span class="sxs-lookup"><span data-stu-id="6c662-382">For the **windowsDomain** node, enter the domain name of the **windowsUserId**.</span></span>  
  
4.  <span data-ttu-id="6c662-383">À l'invite de commandes, ouvrez le fichier PmntTrckAffApp.xml à l'aide du Bloc-notes, puis passez en revue le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="6c662-383">At the command prompt, open the PmntTrckAffApp.xml file using Notepad, and review the contents of the file.</span></span> <span data-ttu-id="6c662-384">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="6c662-384">No changes to this file are necessary.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-385">Le fichier PmntTrckAffApp.xml définit l'application associée SSO (WoodgroveBank.PaymentTracker) pour le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="6c662-385">The PmntTrckAffApp.xml file defines the SSO affiliate application, WoodgroveBank.PaymentTracker, for the Payment Tracker back-end system.</span></span>  
  
5.  <span data-ttu-id="6c662-386">À l'invite de commandes, ouvrez le fichier PmntTrckUserMap.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c662-386">At the command prompt, open the PmntTrckUserMap.xml file using Notepad, and then make the following edits:</span></span>  
  
    ```  
    <mapping>  
      <windowsDomain><DomainName></windowsDomain>  
      <windowsUserId><UserID></windowsUserId>  
      <externalUserId><ExternalUserID></externalUserId>  
    </mapping>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-387">L'application associée SSO Payment Tracker sera utilisée pour l'adaptateur MQSeries. L'ID utilisateur externe/le mot de passe mappés sont envoyés via les propriétés d'en-tête de MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c662-387">The Payment Tracker SSO affiliated application will be used for the MQSeries Adapter and the mapped external user ID/password are sent through MQSeries header properties.</span></span> <span data-ttu-id="6c662-388">Le serveur MQSeries valide uniquement le compte de service BizTalk, sous lequel l'adaptateur MQSeries est exécuté.</span><span class="sxs-lookup"><span data-stu-id="6c662-388">The MQSeries Server validates only the BizTalk service account, under which MQSeries Adapter is running.</span></span> <span data-ttu-id="6c662-389">Il ne valide pas les informations d'identification de l'utilisateur externe.</span><span class="sxs-lookup"><span data-stu-id="6c662-389">It doesn't validate any external user credential.</span></span>  
    >   
    >  <span data-ttu-id="6c662-390">Pour plus d’informations sur l’authentification unique applications associées pour l’adaptateur MQSeries, consultez [comment configurer les emplacements de réception de la carte de MQSeries et les Ports d’envoi](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span><span class="sxs-lookup"><span data-stu-id="6c662-390">For more information about SSO affiliated applications for the MQSeries Adapter, see [How to Configure MQSeries Adapter Receive Locations and Send Ports](../core/how-to-configure-mqseries-adapter-receive-locations-and-send-ports.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-391">Le fichier PmntTrckUserMap.xml contient les mappages utilisateur SSO pour le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="6c662-391">The PmntTrckUserMap.xml file contains the SSO user mappings for the Payment Tracker back-end system.</span></span> <span data-ttu-id="6c662-392">Le programme de simulation Payment Tracker permet de recréer les conditions de réussite et d'échec de l'authentification des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="6c662-392">The Payment Tracker simulator program simulates both success and failure conditions for user authentication.</span></span>  
    >   
    >  <span data-ttu-id="6c662-393">Le programme authentifie correctement tous les ID d’utilisateur qui commencent par les lettres **PT** (par exemple, **PTUserID**) et ne parvient pas à authentifier les ID d’utilisateur qui ne commencent pas par **PT**.</span><span class="sxs-lookup"><span data-stu-id="6c662-393">The program successfully authenticates all user IDs that begin with the letters **PT** (for example, **PTUserID**), and fails to authenticate any user IDs that do not begin with **PT**.</span></span> <span data-ttu-id="6c662-394">Vous pouvez ainsi choisir l'ID utilisateur approprié en fonction de la condition que vous voulez tester.</span><span class="sxs-lookup"><span data-stu-id="6c662-394">This enables you to choose the appropriate user ID depending on the condition that you would like to test.</span></span> <span data-ttu-id="6c662-395">Vous pouvez également répéter l’intégralité **mappage** nœud pour chaque ID d’utilisateur et définir plusieurs mappages dans le même fichier.</span><span class="sxs-lookup"><span data-stu-id="6c662-395">You can also repeat the entire **mapping** node for each user ID and define multiple mappings in the same file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-396">Pour le **externalUserId** nœud, entrez l’ID utilisateur externe pour le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="6c662-396">For the **externalUserId** node, enter the external user ID for the Payment Tracker back-end system.</span></span> <span data-ttu-id="6c662-397">Dans le cadre de cette procédure pas à pas, utilisez l'ID externe PTUserID.</span><span class="sxs-lookup"><span data-stu-id="6c662-397">For this walkthrough, use PTUserID for the external ID.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-398">Pour le **windowsUserId** nœud, entrez le nom d’utilisateur nom qui le **externalUserId** sont mappés à.</span><span class="sxs-lookup"><span data-stu-id="6c662-398">For the **windowsUserId** node, enter the user name which the **externalUserId** will map to.</span></span> <span data-ttu-id="6c662-399">L'utilisateur doit faire partie d'un groupe qui est autorisé à utiliser le système principal Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="6c662-399">This user must be a member of the group that will be allowed to use the Payment Tracker back-end system.</span></span> <span data-ttu-id="6c662-400">Dans le cadre de cette procédure pas à pas, utilisez le nom d'utilisateur du service BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6c662-400">For this walkthrough, use the user name of the BizTalk service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-401">Pour le **windowsDomain** nœud, entrez le nom de domaine de la **windowsUserId**.</span><span class="sxs-lookup"><span data-stu-id="6c662-401">For the **windowsDomain** node, enter the domain name of the **windowsUserId**.</span></span>  
  
6.  <span data-ttu-id="6c662-402">À l'invite de commandes, ouvrez le fichier ConfigStoreApp.xml à l'aide du Bloc-notes, puis passez en revue le contenu du fichier.</span><span class="sxs-lookup"><span data-stu-id="6c662-402">At the command prompt, open the ConfigStoreApp.xml file using Notepad, and then review the contents of the file.</span></span>  
  
     <span data-ttu-id="6c662-403">Ce fichier définit l'application de magasin de configuration dans SSO que le scénario utilise pour conserver les paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="6c662-403">This file defines the configuration store application in SSO that the scenario uses to keep configuration parameters.</span></span> <span data-ttu-id="6c662-404">Certains de ces paramètres incluent une valeur de délai d'expiration lors de la communication avec SAP (à la fois pour la version d'adaptateur et pour la version Inline), le nom du gestionnaire de file d'attente, ainsi que les files d'attente à utiliser avec la version Inline.</span><span class="sxs-lookup"><span data-stu-id="6c662-404">Some of the configuration parameters include the Timeout value when communicating with SAP (for both the adapter and inline versions) and the name of the queue manager and queues to use when using the inline version.</span></span> <span data-ttu-id="6c662-405">Il n'est pas nécessaire de modifier ce fichier.</span><span class="sxs-lookup"><span data-stu-id="6c662-405">No changes to this file are necessary.</span></span>  
  
7.  <span data-ttu-id="6c662-406">À l'invite de commandes, ouvrez le fichier SetConfigValuesInSSO.cmd à l'aide du Bloc-notes, puis examinez et modifiez son contenu selon le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="6c662-406">At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, review and change the contents of the file as the following table.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-407">Ce fichier de commande définit les valeurs des paramètres de configuration dans la base de données SSO.</span><span class="sxs-lookup"><span data-stu-id="6c662-407">This command file sets the values for the configuration parameters in the SSO database.</span></span> <span data-ttu-id="6c662-408">Il contient plusieurs commandes Set qui attribuent les valeurs à des variables locales au début du fichier de commande.</span><span class="sxs-lookup"><span data-stu-id="6c662-408">It contains several set commands that assign the values to local variables in the beginning of the command file.</span></span>  
    >   
    >  <span data-ttu-id="6c662-409">Les valeurs SAPAdapterTimeout, PendingTransactionsAdapterTimeout et PaymentTrackingAdapterTimeout sont utilisées dans la version d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-409">The SAPAdapterTimeout, PendingTransactionsAdapterTimeout, and PaymentTrackingAdapterTimeout values are used in the adapter version.</span></span> <span data-ttu-id="6c662-410">Les valeurs restantes sont utilisées dans la version Inline.</span><span class="sxs-lookup"><span data-stu-id="6c662-410">The remaining values are used in the inline version.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-411">Vous pouvez entrer « » (deux guillemets doubles) pour les valeurs par défaut marquées \<spécifié par l’utilisateur\> dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="6c662-411">You can enter " " (two double quotes) for the default values marked \<User Specified\> in the following table.</span></span>  
  
    |<span data-ttu-id="6c662-412">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6c662-412">Parameter</span></span>|<span data-ttu-id="6c662-413">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="6c662-413">Default Value</span></span>|<span data-ttu-id="6c662-414"> Description</span><span class="sxs-lookup"><span data-stu-id="6c662-414">Description</span></span>|  
    |---------------|-------------------|-----------------|  
    |<span data-ttu-id="6c662-415">SAPAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="6c662-415">SAPAdapterTimeout</span></span>|<span data-ttu-id="6c662-416">20000</span><span class="sxs-lookup"><span data-stu-id="6c662-416">20000</span></span>|<span data-ttu-id="6c662-417">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système principal SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-417">Max timeout (millisecond) for a request to the SAP back-end</span></span>|  
    |<span data-ttu-id="6c662-418">SAPInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="6c662-418">SAPInlineTimeout</span></span>|<span data-ttu-id="6c662-419">20000</span><span class="sxs-lookup"><span data-stu-id="6c662-419">20000</span></span>|<span data-ttu-id="6c662-420">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système principal SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-420">Max timeout (millisecond) for a request to the SAP back-end</span></span>|  
    |<span data-ttu-id="6c662-421">SAPInlineHostName</span><span class="sxs-lookup"><span data-stu-id="6c662-421">SAPInlineHostName</span></span>|<span data-ttu-id="6c662-422">\<Utilisateur spécifié\></span><span class="sxs-lookup"><span data-stu-id="6c662-422">\<User Specified\></span></span>|<span data-ttu-id="6c662-423">Identificateur principal SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-423">SAP back-end identifier</span></span>|  
    |<span data-ttu-id="6c662-424">SAPInlineClientNumber</span><span class="sxs-lookup"><span data-stu-id="6c662-424">SAPInlineClientNumber</span></span>|<span data-ttu-id="6c662-425">\<Utilisateur spécifié\></span><span class="sxs-lookup"><span data-stu-id="6c662-425">\<User Specified\></span></span>|<span data-ttu-id="6c662-426">Numéro de client SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-426">SAP Client number</span></span>|  
    |<span data-ttu-id="6c662-427">SAPInlineSystemNumber</span><span class="sxs-lookup"><span data-stu-id="6c662-427">SAPInlineSystemNumber</span></span>|<span data-ttu-id="6c662-428">\<Utilisateur spécifié\></span><span class="sxs-lookup"><span data-stu-id="6c662-428">\<User Specified\></span></span>|<span data-ttu-id="6c662-429">Numéro de système SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-429">SAP System number</span></span>|  
    |<span data-ttu-id="6c662-430">SAPInlineUserName</span><span class="sxs-lookup"><span data-stu-id="6c662-430">SAPInlineUserName</span></span>|<span data-ttu-id="6c662-431">\<Utilisateur spécifié\></span><span class="sxs-lookup"><span data-stu-id="6c662-431">\<User Specified\></span></span>|<span data-ttu-id="6c662-432">Nom d'utilisateur permettant de se connecter au système principal SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-432">The user name used to connect to the SAP back-end</span></span>|  
    |<span data-ttu-id="6c662-433">SAPInlinePassword</span><span class="sxs-lookup"><span data-stu-id="6c662-433">SAPInlinePassword</span></span>|<span data-ttu-id="6c662-434">\<Utilisateur spécifié\></span><span class="sxs-lookup"><span data-stu-id="6c662-434">\<User Specified\></span></span>|<span data-ttu-id="6c662-435">Mot de passe permettant de se connecter au système principal SAP</span><span class="sxs-lookup"><span data-stu-id="6c662-435">The password used to connect to the SAP back-end</span></span>|  
    |<span data-ttu-id="6c662-436">PendingTransactionsAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="6c662-436">PendingTransactionsAdapterTimeout</span></span>|<span data-ttu-id="6c662-437">20000</span><span class="sxs-lookup"><span data-stu-id="6c662-437">20000</span></span>|<span data-ttu-id="6c662-438">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du serveur Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="6c662-438">Max timeout (millisecond) for a request to the Pending Transactions server</span></span>|  
    |<span data-ttu-id="6c662-439">PendingTransactionsInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="6c662-439">PendingTransactionsInlineTimeout</span></span>|<span data-ttu-id="6c662-440">20000</span><span class="sxs-lookup"><span data-stu-id="6c662-440">20000</span></span>|<span data-ttu-id="6c662-441">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du serveur Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="6c662-441">Max timeout (millisecond) for a request to the Pending Transactions server</span></span>|  
    |<span data-ttu-id="6c662-442">PendingTransactionsInlineURL</span><span class="sxs-lookup"><span data-stu-id="6c662-442">PendingTransactionsInlineURL</span></span>|<span data-ttu-id="6c662-443">https://\<*nom de votre ordinateur*\>/Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx</span><span class="sxs-lookup"><span data-stu-id="6c662-443">https://\<*your computer name*\>/Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactions/PendTransWS.asmx</span></span>|<span data-ttu-id="6c662-444">URL du service Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-444">URL of the Pending Transactions service.</span></span> <span data-ttu-id="6c662-445">\<*Nom de votre ordinateur* \> doit correspondre à la **nom commun** dans la procédure « pour créer une demande de certificat ».</span><span class="sxs-lookup"><span data-stu-id="6c662-445">\<*Your computer name*\> must match the **common name** in the procedure "To create a certificate request".</span></span> <span data-ttu-id="6c662-446">Vous ne devez pas utiliser « localhost » pour \< *nom de votre ordinateur*\>.</span><span class="sxs-lookup"><span data-stu-id="6c662-446">You must not use "localhost" for \<*Your computer name*\>.</span></span>|  
    |<span data-ttu-id="6c662-447">PendingTransactionsInlineSSOAffiliateApp</span><span class="sxs-lookup"><span data-stu-id="6c662-447">PendingTransactionsInlineSSOAffiliateApp</span></span>|<span data-ttu-id="6c662-448">WoodgroveBank.PendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-448">WoodgroveBank.PendingTransactions</span></span>|<span data-ttu-id="6c662-449">Nom de l'application SSO Pending Transactions</span><span class="sxs-lookup"><span data-stu-id="6c662-449">Pending Transactions SSO application name</span></span>|  
    |<span data-ttu-id="6c662-450">PaymentTrackingAdapterTimeout</span><span class="sxs-lookup"><span data-stu-id="6c662-450">PaymentTrackingAdapterTimeout</span></span>|<span data-ttu-id="6c662-451">20000</span><span class="sxs-lookup"><span data-stu-id="6c662-451">20000</span></span>|<span data-ttu-id="6c662-452">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="6c662-452">Max timeout (millisecond) for a request to the Payment Tracking system</span></span>|  
    |<span data-ttu-id="6c662-453">PaymentTrackingInlineTimeout</span><span class="sxs-lookup"><span data-stu-id="6c662-453">PaymentTrackingInlineTimeout</span></span>|<span data-ttu-id="6c662-454">20000</span><span class="sxs-lookup"><span data-stu-id="6c662-454">20000</span></span>|<span data-ttu-id="6c662-455">Délai d'attente maximal (en millisecondes) avant l'expiration d'une demande effectuée auprès du système Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="6c662-455">Max timeout (millisecond) for a request to the Payment Tracking system</span></span>|  
    |<span data-ttu-id="6c662-456">PaymentTrackingInlineQManager</span><span class="sxs-lookup"><span data-stu-id="6c662-456">PaymentTrackingInlineQManager</span></span>|<span data-ttu-id="6c662-457">\<Utilisateur spécifié\> (généralement QM_\<*nom de votre ordinateur*\>).</span><span class="sxs-lookup"><span data-stu-id="6c662-457">\<User Specified\> (Typically QM_\<*your computer name*\>).</span></span>|<span data-ttu-id="6c662-458">Nom du gestionnaire de file d'attente MQSeries</span><span class="sxs-lookup"><span data-stu-id="6c662-458">MQSeries Queue Manager name</span></span>|  
    |<span data-ttu-id="6c662-459">PaymentTrackingInlineMQChannelDefinition</span><span class="sxs-lookup"><span data-stu-id="6c662-459">PaymentTrackingInlineMQChannelDefinition</span></span>|<span data-ttu-id="6c662-460">" " (vous devez entrer deux guillemets doubles).</span><span class="sxs-lookup"><span data-stu-id="6c662-460">" " (need to enter the two double quotes).</span></span>|<span data-ttu-id="6c662-461">Chaîne vide si local, ou nom de chaîne formaté du serveur MQ distant.</span><span class="sxs-lookup"><span data-stu-id="6c662-461">Empty string if local, or formatted channel name of the remote MQ server.</span></span> <span data-ttu-id="6c662-462">Si vous conservez tous les paramètres par défaut de la configuration d’IBM WebSphere MQ, la définition de la chaîne sera S__\<*nom de votre ordinateur*\>/TCP/\<*nom de votre ordinateur* \>(1414).</span><span class="sxs-lookup"><span data-stu-id="6c662-462">If you keep all default settings in configuring IBM WebSphere MQ, the channel definition will be S__\<*your computer name*\>/TCP/\<*your computer name*\>(1414).</span></span>|  
    |<span data-ttu-id="6c662-463">PaymentTrackingInlineRequestQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-463">PaymentTrackingInlineRequestQueue</span></span>|<span data-ttu-id="6c662-464">LastPaymentsInputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-464">LastPaymentsInputQueue</span></span>|<span data-ttu-id="6c662-465">Nom de la file d'attente MQ pour les demandes de Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="6c662-465">The MQ Queue name for payment tracking requests</span></span>|  
    |<span data-ttu-id="6c662-466">PaymentTrackingInlineResponseQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-466">PaymentTrackingInlineResponseQueue</span></span>|<span data-ttu-id="6c662-467">LastPaymentsOutputQueue</span><span class="sxs-lookup"><span data-stu-id="6c662-467">LastPaymentsOutputQueue</span></span>|<span data-ttu-id="6c662-468">Nom de la file d'attente MQ pour les réponses de Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="6c662-468">The MQ Queue name for payment tracking responses</span></span>|  
    |<span data-ttu-id="6c662-469">PaymentTrackingInlineSSOAffiliateApp</span><span class="sxs-lookup"><span data-stu-id="6c662-469">PaymentTrackingInlineSSOAffiliateApp</span></span>|<span data-ttu-id="6c662-470">WoodgroveBank.PaymentTracker</span><span class="sxs-lookup"><span data-stu-id="6c662-470">WoodgroveBank.PaymentTracker</span></span>|<span data-ttu-id="6c662-471">Nom de l'application SSO Payment Tracking</span><span class="sxs-lookup"><span data-stu-id="6c662-471">Payment tracking SSO application name</span></span>|  
    |<span data-ttu-id="6c662-472">StubSAPWebServiceURL</span><span class="sxs-lookup"><span data-stu-id="6c662-472">StubSAPWebServiceURL</span></span>|<span data-ttu-id="6c662-473">http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx</span><span class="sxs-lookup"><span data-stu-id="6c662-473">http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubSAP/StubSAPWS.asmx</span></span>|<span data-ttu-id="6c662-474">URL du service Web stub du système SAP Credit Limit</span><span class="sxs-lookup"><span data-stu-id="6c662-474">The stub Web service URL of the Credit Limit SAP system</span></span>|  
  
8.  <span data-ttu-id="6c662-475">À l'invite de commandes, exécutez la commande suivante pour définir l'environnement PATH :</span><span class="sxs-lookup"><span data-stu-id="6c662-475">At the command prompt, run the following command to set the PATH environment:</span></span>  
  
    -   `SET PATH=%PATH%;"%CommonProgramFiles%\Enterprise Single Sign-On"`  
  
9. <span data-ttu-id="6c662-476">À l'invite de commandes, exécutez la commande CreateInitialConfigInSSO.cmd.</span><span class="sxs-lookup"><span data-stu-id="6c662-476">At the command prompt, run the CreateInitialConfigInSSO.cmd.</span></span> <span data-ttu-id="6c662-477">Celle-ci crée les applications associées SSO, l'application de magasin de configuration SSO et les mappages utilisateur des applications associées.</span><span class="sxs-lookup"><span data-stu-id="6c662-477">It creates the SSO Affiliate Applications, the SSO configuration store application, and the user mappings for the affiliate applications.</span></span> <span data-ttu-id="6c662-478">Elle exécute ensuite SetConfigValuesInSSO.cmd pour stocker les valeurs de configuration dans l'application de magasin de configuration SSO.</span><span class="sxs-lookup"><span data-stu-id="6c662-478">Then, it executes the SetConfigValuesInSSO.cmd to store configuration values in the SSO configuration store application.</span></span>  
  
10. <span data-ttu-id="6c662-479">À l'invite de commandes, exécutez la commande suivante pour définir les informations d'identification de l'utilisateur de l'application associée Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-479">At the command prompt, run the following command to set the user credential for the Pending Transactions affiliate application.</span></span> <span data-ttu-id="6c662-480">Utilisez le \< **DomainName** \> et \< **UserID** \> défini dans le fichier PendTransUserMap.xml pour la \<WindowsDomain\> \\< WindowsUserId\>.</span><span class="sxs-lookup"><span data-stu-id="6c662-480">Use the \<**DomainName**\> and \<**UserID**\> defined in the PendTransUserMap.xml for the \<WindowsDomain\>\\<WindowsUserId\>.</span></span> <span data-ttu-id="6c662-481">Cette commande vous invite à entrer le mot de passe de l'utilisateur externe (UserID dans le cadre de cette procédure).</span><span class="sxs-lookup"><span data-stu-id="6c662-481">This command asks you to enter the password of the external user, UserID, used in this walkthrough.</span></span>  
  
    -   `ssomanage -setcredentials <WindowsDomain>\<WindowsUserId> WoodgroveBank.PendingTransactions`  
  
11. <span data-ttu-id="6c662-482">À l'invite de commandes, exécutez la commande suivante pour définir les informations d'identification de l'utilisateur de l'application associée Payment Tracker.</span><span class="sxs-lookup"><span data-stu-id="6c662-482">At the command prompt, run the following command to set the user credential for the Payment Tracker affiliate application.</span></span> <span data-ttu-id="6c662-483">Utilisez le \< **DomainName** \> et \< **UserID** \> défini dans le fichier PmntTrckUserMap.xml pour la \<WindowsDomain\> \\< WindowsUserId\>.</span><span class="sxs-lookup"><span data-stu-id="6c662-483">Use the \<**DomainName**\> and \<**UserID**\> defined in the PmntTrckUserMap.xml for the \<WindowsDomain\>\\<WindowsUserId\>.</span></span> <span data-ttu-id="6c662-484">Cette commande vous invite à entrer le mot de passe de l'utilisateur externe (PTUserID dans le cadre de cette procédure).</span><span class="sxs-lookup"><span data-stu-id="6c662-484">This command asks you to enter the password of the external user, PTUserID, used in this walkthrough.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-485">Le simulateur Payment Tracker ne valide pas les informations d'identification de l'utilisateur externe.</span><span class="sxs-lookup"><span data-stu-id="6c662-485">The Payment Tracker simulator doesn't validate the external user credential.</span></span> <span data-ttu-id="6c662-486">Vous pouvez entrer n'importe quel mot de passe pour l'utilisateur PTUserID.</span><span class="sxs-lookup"><span data-stu-id="6c662-486">You can enter any password for the PTUserID.</span></span>  
  
    -   `ssomanage -setcredentials < WindowsDomain >\< WindowsUserId > WoodgroveBank.PaymentTracker`  
  
##  <a name="step19"></a><span data-ttu-id="6c662-487">Déployer le fichier de définition BAM pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-487">Deploy the BAM definition file for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="6c662-488">Ouvrez une invite de commandes, tapez la commande suivante, puis appuyez sur ENTRÉE pour définir le chemin d'accès des utilitaires BAM :</span><span class="sxs-lookup"><span data-stu-id="6c662-488">Open a command prompt, type the following command, and then press ENTER to set the path to find the BAM utilities:</span></span>  
  
    -   <span data-ttu-id="6c662-489">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span><span class="sxs-lookup"><span data-stu-id="6c662-489">SET PATH=%PATH%;[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking"</span></span>  
  
2.  <span data-ttu-id="6c662-490">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\BAM, tapez la commande suivante, puis appuyez sur ENTRÉE :</span><span class="sxs-lookup"><span data-stu-id="6c662-490">At the command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\BAM, type the following command, and then press ENTER:</span></span>  
  
    -   `bm deploy-all -DefinitionFile:ServiceLevelTracking.xml`  
  
##  <a name="step21"></a><span data-ttu-id="6c662-491">Déployer la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-491">Deploy the Service Oriented Solution</span></span>  
  
#### <a name="update-the-binding-files-for-the-service-oriented-solution"></a><span data-ttu-id="6c662-492">Mettre à jour les fichiers de liaison pour la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-492">Update the binding files for the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="6c662-493">Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, ouvrez le fichier Deployallbinding.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c662-493">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, open the Deployallbinding.xml using Notepad, and then make the following edits:</span></span>  
  
    -   <span data-ttu-id="6c662-494">Remplacez le nom du serveur dans les variables SET MGMT_DB_SERVER et MBMT_DB par les noms du serveur et de la base de données utilisés par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="6c662-494">Change the name of the server in the SET MGMT_DB_SERVER and MBMT_DB to the name of the server and database that BizTalk Server is using.</span></span>  
  
    -   <span data-ttu-id="6c662-495">Remplacez la valeur de la variable SOLNDIR par "%BTSSolutionsPath%\SO\BTSSoln".</span><span class="sxs-lookup"><span data-stu-id="6c662-495">Change the value of the SOLNDIR variable to "%BTSSolutionsPath%\SO\BTSSoln".</span></span>  
  
2.  <span data-ttu-id="6c662-496">À l'invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Bindings.</span><span class="sxs-lookup"><span data-stu-id="6c662-496">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Bindings folder.</span></span>  
  
3.  <span data-ttu-id="6c662-497">Pour la version d'adaptateur, ouvrez le fichier AdapterSOAOrchBindings.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c662-497">For the adapter version, open the AdapterSOAOrchBindings.xml using Notepad, and then edit as follows:</span></span>  
  
    -   <span data-ttu-id="6c662-498">Remplacez toutes les occurrences de __MQ_SERVER_NAME\_ \_ avec le nom du serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c662-498">Replace all occurrences of __MQ_SERVER_NAME\_\_ with the MQSeries Server name.</span></span>  
  
    -   <span data-ttu-id="6c662-499">Remplacez toutes les occurrences de __MQ_QMANAGER_NAME\_ \_ avec le nom du Gestionnaire de file d’attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c662-499">Replace all occurrences of __MQ_QMANAGER_NAME\_\_ with the MQSeries Queue Manager name.</span></span>  
  
    -   <span data-ttu-id="6c662-500">Remplacez toutes les occurrences de __PT_WS_SERVER_NAME\_ \_ dans la chaîne «\<adresse\>https://\__PT_WS_SERVER_NAME\_\_» avec le nom du serveur où l’en attente Service Web de transactions est déployé.</span><span class="sxs-lookup"><span data-stu-id="6c662-500">Replace all occurrences of __PT_WS_SERVER_NAME\_\_ in the string "\<Address\>https://\__PT_WS_SERVER_NAME\_\_" with the server name where the Pending Transactions Web service is deployed.</span></span> <span data-ttu-id="6c662-501">Le nom du serveur doit correspondre à la **nom commun** à l’étape, « pour configurer le serveur Web pour SSL ».</span><span class="sxs-lookup"><span data-stu-id="6c662-501">The server name must match the **common name** in the step, "To configure the Web server for SSL".</span></span> <span data-ttu-id="6c662-502">Vous ne devez pas utiliser « localhost ».</span><span class="sxs-lookup"><span data-stu-id="6c662-502">You shouldn't use localhost.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-503">Le fichier de liaison, AdapterSOAOrchBindings.xml, utilise le service Web stub pour :</span><span class="sxs-lookup"><span data-stu-id="6c662-503">The binding file, AdapterSOAOrchBindings.xml, uses the stub Web service for:</span></span>  
    >   
    >  1.  <span data-ttu-id="6c662-504">le système principal SAP Credit Limit ;</span><span class="sxs-lookup"><span data-stu-id="6c662-504">The Credit Limit back-end SAP system.</span></span>  
    > 2.  <span data-ttu-id="6c662-505">l'adaptateur MQSeries à des fins d'intégration au système principal Payment Tracking ;</span><span class="sxs-lookup"><span data-stu-id="6c662-505">The MQSeries adapter to integrate with the Payment Tracking back-end system.</span></span>  
    > 3.  <span data-ttu-id="6c662-506">le service Web Pending Transactions pour appeler le composant .NET TI HIS à des fins d'intégration au système principal du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="6c662-506">The Pending Transactions Web service to call the HIS TI .NET component to integrate with the mainframe back-end system.</span></span>  
    >   
    >  <span data-ttu-id="6c662-507">Si vous ne disposez d'aucun macroordinateur, vous devez utiliser le service Web stub pour générer des données dans le système Pending Transactions.</span><span class="sxs-lookup"><span data-stu-id="6c662-507">If you aren’t using the mainframe, you must use the stub Web service to generate data for the Pending Transactions system.</span></span>  
  
4.  <span data-ttu-id="6c662-508">Pour la version Inline, ouvrez le fichier InlineSOAOrchBindings.xml à l'aide du Bloc-notes, puis effectuez les modifications suivantes :</span><span class="sxs-lookup"><span data-stu-id="6c662-508">For the inline version, open the InlineSOAOrchBindings.xml using Notepad, and then edit as follows:</span></span>  
  
    -   <span data-ttu-id="6c662-509">Remplacez toutes les occurrences de __MQ_SERVER_NAME\_ \_ avec le nom du serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c662-509">Replace all occurrences of __MQ_SERVER_NAME\_\_ with the MQSeries Server name.</span></span>  
  
    -   <span data-ttu-id="6c662-510">Remplacez toutes les occurrences de __MQ_QMANAGER_NAME\_ \_ avec le nom du Gestionnaire de file d’attente MQSeries.</span><span class="sxs-lookup"><span data-stu-id="6c662-510">Replace all occurrences of __MQ_QMANAGER_NAME\_\_ with the MQSeries Queue Manager name.</span></span>  
  
#### <a name="deploy-the-service-oriented-solution"></a><span data-ttu-id="6c662-511">Déployer la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-511">Deploy the Service Oriented solution</span></span>  
  
-   <span data-ttu-id="6c662-512">À l’invite de commandes, accédez au répertoire dans le dossier %BTSSolutionsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6c662-512">At a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER.</span></span>  
  
    -   `Deployallbinding.cmd`  
  
    > [!NOTE]
    >  <span data-ttu-id="6c662-513">La commande Deployallbinding.cmd crée l'application BizTalk appelée BTSScn.SO.CustomerService et importe les fichiers de liaison pour les versions d'adaptateur et Inline.</span><span class="sxs-lookup"><span data-stu-id="6c662-513">The Deployallbinding.cmd creates the BizTalk application named BTSScn.SO.CustomerService and imports binding files for the adapter and inline versions.</span></span>  
  
##  <a name="step23"></a><span data-ttu-id="6c662-514">Configurer le Services Web Pending Transactions stub lorsqu’un macroordinateur n’est pas disponible</span><span class="sxs-lookup"><span data-stu-id="6c662-514">Configure the stub Pending Transactions Web Services when a mainframe is not available</span></span>  
  
#### <a name="configure-the-stub-pending-transactions-web-service-for-using-the-adapter-version-without-a-mainframe"></a><span data-ttu-id="6c662-515">Configurer le service Web Pending Transactions (pour utiliser la version d’adaptateur sans macroordinateur) stub</span><span class="sxs-lookup"><span data-stu-id="6c662-515">Configure the stub Pending Transactions Web service (for using the adapter version without a mainframe)</span></span>  
  
1.  <span data-ttu-id="6c662-516">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-516">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-517">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web Pending Transactions pour la version d’adaptateur stub :</span><span class="sxs-lookup"><span data-stu-id="6c662-517">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="6c662-518">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-518">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
     <span data-ttu-id="6c662-519">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="6c662-519">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
     <span data-ttu-id="6c662-520">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-520">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="6c662-521">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit à l’aide de la **propriétés** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c662-521">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows using the **Properties** dialog box.</span></span>  
  
    1.  <span data-ttu-id="6c662-522">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> vous avez créé à l’étape, « pour créer le serveur virtuel répertoires dans IIS pour la solution ».</span><span class="sxs-lookup"><span data-stu-id="6c662-522">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> you created in the step, "To create the virtual directories in IIS for the solution".</span></span>  
  
    2.  <span data-ttu-id="6c662-523">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="6c662-523">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="6c662-524">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="6c662-524">Click **OK** to exit.</span></span>  
  
3.  <span data-ttu-id="6c662-525">Dans le **Console d’Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, btsscn.so.CustomerService, puis **envoyer Ports**, avec le bouton droit **PendingTransactionSolicitResponsePort**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6c662-525">In the **BizTalk Server Administration Console**, expand **BizTalk Group**, expand **Applications**, expand BTSScn.SO.CustomerService, expand **Send Ports**, right-click **PendingTransactionSolicitResponsePort**, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="6c662-526">Dans le **général** , cliquez sur **configurer** pour afficher les **propriétés du Transport** boîte de dialogue zone, puis modifiez le **URL du Service Web** à le stub Web en attente de Transaction de service, par exemple :</span><span class="sxs-lookup"><span data-stu-id="6c662-526">In the **General** page, click **Configure** to display the **Transport Properties** dialog box, and then modify the **Web Service URL** to the stub Pending Transaction Web service, for example:</span></span>  
  
         `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
    2.  <span data-ttu-id="6c662-527">Fermez toutes les boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="6c662-527">Close all of the dialog boxes.</span></span>  
  
#### <a name="configure-the-stub-pending-transactions-web-service-for-using-the-inline-version-without-a-mainframe"></a><span data-ttu-id="6c662-528">Configurer le service Web Pending Transactions (pour utiliser la version inline sans macroordinateur) stub</span><span class="sxs-lookup"><span data-stu-id="6c662-528">Configure the stub Pending Transactions Web service (for using the inline version without a mainframe)</span></span>  
  
1.  <span data-ttu-id="6c662-529">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, avec le bouton droit le **Site Web par défaut**, pointez sur **nouveau**, et puis cliquez sur **répertoire virtuel** pour exécuter **Assistant de création de répertoire virtuel**.</span><span class="sxs-lookup"><span data-stu-id="6c662-529">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, right-click the **Default Web Site**, point to **New**, and then click **Virtual Directory** to run **Virtual Directory Creation Wizard**.</span></span>  
  
     <span data-ttu-id="6c662-530">À l’aide de la **Assistant de création de répertoire virtuel**, créez le répertoire virtuel suivant pour le service Web Pending Transactions pour la version d’adaptateur stub :</span><span class="sxs-lookup"><span data-stu-id="6c662-530">Using the **Virtual Directory Creation Wizard**, create the following virtual directory for stub Pending Transactions Web service for the adapter version:</span></span>  
  
     <span data-ttu-id="6c662-531">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span><span class="sxs-lookup"><span data-stu-id="6c662-531">Alias = Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions</span></span>  
  
     <span data-ttu-id="6c662-532">Chemin d’accès = \< *répertoire d’installation de BizTalk*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span><span class="sxs-lookup"><span data-stu-id="6c662-532">PATH = \<*BizTalk Install Directory*\>\SDK\Scenarios\SO\BTSSoln\StubWebServices\PendingTrans</span></span>  
  
     <span data-ttu-id="6c662-533">Access Permissions = Read, Run scripts</span><span class="sxs-lookup"><span data-stu-id="6c662-533">Access Permissions = Read, Run scripts</span></span>  
  
2.  <span data-ttu-id="6c662-534">Dans le **Gestionnaire des Services Internet (IIS)**, développez **Sites Web**, développez le **Site Web par défaut**, avec le bouton droit Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, cliquez sur **propriétés**, puis modifiez les paramètres comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c662-534">In the **Internet Information Services (IIS) Manager**, expand **Web Sites**, expand the **Default Web Site**, right-click Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions, click **Properties**, and then modify the settings as follows:</span></span>  
  
    1.  <span data-ttu-id="6c662-535">Dans le **répertoire virtuel** onglet, définissez la **Pool d’applications** à \< *YourAppPool* \> vous avez créé à l’étape, « pour créer le serveur virtuel répertoires dans IIS pour la solution ».</span><span class="sxs-lookup"><span data-stu-id="6c662-535">In the **Virtual directory** tab, set the **Application Pool** to \<*YourAppPool*\> you created in the step, "To create the virtual directories in IIS for the solution".</span></span>  
  
    2.  <span data-ttu-id="6c662-536">Dans le **sécurité du répertoire** , cliquez sur **modifier** dans les **d’authentification et contrôle d’accès** zone de groupe, puis sélectionnez **activer l’accès anonyme**.</span><span class="sxs-lookup"><span data-stu-id="6c662-536">In the **Directory Security** tab, click **Edit** in the **Authentication and access control** group box, and then select **Enable anonymous access**.</span></span> <span data-ttu-id="6c662-537">Cliquez sur **OK** pour quitter.</span><span class="sxs-lookup"><span data-stu-id="6c662-537">Click **OK** to exit.</span></span>  
  
3.  <span data-ttu-id="6c662-538">Ouvrez une invite de commandes, puis accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts.</span><span class="sxs-lookup"><span data-stu-id="6c662-538">Open a command prompt, and then change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder.</span></span>  
  
4.  <span data-ttu-id="6c662-539">À l’invite de commandes, ouvrez le fichier SetConfigValuesInSSO.cmd à l’aide du bloc-notes, puis définissez la valeur de la **PendingTransactionsInlineURL** à l’URL du Service Web Pending transactions stub.</span><span class="sxs-lookup"><span data-stu-id="6c662-539">At the command prompt, open the SetConfigValuesInSSO.cmd file using Notepad, and then set the value of the **PendingTransactionsInlineURL** to the URL of the stub Pending Transaction Web Service.</span></span>  
  
    -   `http://localhost/Microsoft.Samples.BizTalk.WoodgroveBank.StubPendingTransactions/StubPendTransWS.asmx`  
  
5.  <span data-ttu-id="6c662-540">À l'invite de commandes, tapez `SetConfigValuesInSSO.cmd`, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="6c662-540">At the command prompt, type `SetConfigValuesInSSO.cmd`, and then press ENTER.</span></span>  
  
##  <a name="step25"></a><span data-ttu-id="6c662-541">Démarrer le Service orienté solutions</span><span class="sxs-lookup"><span data-stu-id="6c662-541">Start the Service Oriented Solution</span></span>  
  
1.  <span data-ttu-id="6c662-542">Ouvrez une invite de commandes, accédez au répertoire %BTSSolutionsPath%\SO\BTSSoln\Scripts, tapez la commande suivante, puis appuyez sur ENTRÉE pour démarrer toutes les orchestrations des versions d'adaptateur et Inline.</span><span class="sxs-lookup"><span data-stu-id="6c662-542">Open a command prompt, change the directory to the %BTSSolutionsPath%\SO\BTSSoln\Scripts folder, type the following command, and then press ENTER to start all orchestrations for the inline and adapter versions.</span></span>  
  
    -   `startAll.vbs`  
  
2.  <span data-ttu-id="6c662-543">Exécutez la solution orientée services.</span><span class="sxs-lookup"><span data-stu-id="6c662-543">Run the service-oriented solution.</span></span> <span data-ttu-id="6c662-544">Pour plus d’informations sur l’exécution de la solution, consultez [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="6c662-544">For more information about running the solution, see [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6c662-545">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="6c662-545">Next Steps</span></span>  
 <span data-ttu-id="6c662-546">Test de la version d’adaptateur et inline de la solution orientée services dans [l’exécution de la Solution orientée services](../core/how-to-run-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="6c662-546">You test the inline and adapter version of the service-oriented solution in [How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c662-547">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c662-547">See Also</span></span>  
 <span data-ttu-id="6c662-548">[Avant d’installer la Solution orientée services](../core/before-installing-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="6c662-548">[Before Installing the Service Oriented Solution](../core/before-installing-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="6c662-549">[Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="6c662-549">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="6c662-550">Configuration de l’ordinateur de développement pour la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="6c662-550">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)