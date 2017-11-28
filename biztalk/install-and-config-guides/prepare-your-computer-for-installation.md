---
title: "Préparer votre ordinateur pour l’Installation | Documents Microsoft"
ms.custom: 
ms.date: 2016-03-15
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a493c1a0ef38e9be5e229ff82f8773211adfe765
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prepare-your-computer-for-installation"></a><span data-ttu-id="bf999-102">Préparation de votre ordinateur pour l'installation</span><span class="sxs-lookup"><span data-stu-id="bf999-102">Prepare Your Computer for Installation</span></span>
<span data-ttu-id="bf999-103">Cette rubrique présente les étapes nécessaires pour préparer votre ordinateur en installant et en configurant tous les composants logiciels requis, puis en créant des comptes et en définissant les autorisations.</span><span class="sxs-lookup"><span data-stu-id="bf999-103">This topic lists the steps to prepare your computer by installing and configuring all software prerequisites, and then creating accounts and setting permissions.</span></span>  

> [!TIP] 
> <span data-ttu-id="bf999-104">Un MVP d’intégration a préparé un guide pas à pas très détaillé pour installer les prérequis et BizTalk Server : [Installation et configuration de BizTalk 2013, partie 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).</span><span class="sxs-lookup"><span data-stu-id="bf999-104">An integration MVP prepared a very detailed step-by-step guide to install the prerequisites, and BizTalk Server:  [BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).</span></span>  
> 
> <span data-ttu-id="bf999-105">Certaines étapes ne sont pas recommandées par Microsoft, telles que la désactivation du contrôle d’accès d’utilisateur ou du Pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="bf999-105">Some steps are not recommended by Microsoft, such as disabling User Access Control (UAC) or Windows Firewall.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="bf999-106">Effectuez ces tâches dans l’ordre indiqué.</span><span class="sxs-lookup"><span data-stu-id="bf999-106">Complete these tasks in the order listed.</span></span>  
  
##  <span data-ttu-id="bf999-107"><a name="BKMK_InstUpdates"></a> Installation des mises à jour Windows</span><span class="sxs-lookup"><span data-stu-id="bf999-107"><a name="BKMK_InstUpdates"></a> Install Windows Updates</span></span>  
  
-   <span data-ttu-id="bf999-108">**Windows 7** : Cliquez sur Démarrer.</span><span class="sxs-lookup"><span data-stu-id="bf999-108">**Windows 7**: Click Start.</span></span> <span data-ttu-id="bf999-109">Dans la zone de texte **Rechercher**, tapez **Windows Update**.</span><span class="sxs-lookup"><span data-stu-id="bf999-109">In the **Search** text box, type **Windows Update**.</span></span>  
  
-   <span data-ttu-id="bf999-110">**Windows 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2** : Appuyez sur le bouton Windows du clavier et tapez **Windows Update**.</span><span class="sxs-lookup"><span data-stu-id="bf999-110">**Windows 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2**: Click the Windows button on the keyboard and type **Windows Update**.</span></span> <span data-ttu-id="bf999-111">À partir des résultats de la recherche, cliquez sur **Windows Update**.</span><span class="sxs-lookup"><span data-stu-id="bf999-111">From the search results, click **Windows Update**.</span></span>  
  
 <span data-ttu-id="bf999-112">Après avoir installé les mises à jour, vous devrez peut-être redémarrer l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bf999-112">After installing updates, you may need to restart the computer.</span></span>  
  
##  <span data-ttu-id="bf999-113"><a name="BKMK_IIS"></a> Activation d’Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="bf999-113"><a name="BKMK_IIS"></a> Enable Internet Information Services</span></span>  
 <span data-ttu-id="bf999-114">Microsoft Internet Information Services (IIS) offre une infrastructure d'applications Web pour de nombreuses fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], notamment :</span><span class="sxs-lookup"><span data-stu-id="bf999-114">Microsoft Internet Information Services (IIS) provides a Web application infrastructure for many [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features, including:</span></span>  
  
-   <span data-ttu-id="bf999-115">adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="bf999-115">HTTP adapter</span></span>  
  
-   <span data-ttu-id="bf999-116">adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="bf999-116">SOAP adapter</span></span>  
  
-   <span data-ttu-id="bf999-117">Adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="bf999-117">Windows SharePoint Services adapter</span></span>  
  
-   <span data-ttu-id="bf999-118">Chiffrement SSL (Secure Sockets Layer)</span><span class="sxs-lookup"><span data-stu-id="bf999-118">Secure Sockets Layer (SSL) encryption</span></span>  
  
-   <span data-ttu-id="bf999-119">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="bf999-119">BAM Portal</span></span>  
  
#### <a name="install-iis-75-on-windows-7-sp1"></a><span data-ttu-id="bf999-120">Installation d'IIS 7.5 sur Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="bf999-120">Install IIS 7.5 on Windows 7 SP1</span></span>  
  
1.  <span data-ttu-id="bf999-121">Sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-121">Select **Start**.</span></span> <span data-ttu-id="bf999-122">Dans la zone de texte **Rechercher**, tapez **Programmes et fonctionnalités** et ouvrez la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="bf999-122">In the **Search** text box, type **Programs and Features**, and open it.</span></span>  
  
2.  <span data-ttu-id="bf999-123">Sélectionnez **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="bf999-123">Select**Turn Windows features on or off**.</span></span>  
  
3.  <span data-ttu-id="bf999-124">Sélectionnez **Internet Information Services** et développez **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="bf999-124">Select**Internet Information Services** and expand **Internet Information Services**.</span></span> <span data-ttu-id="bf999-125">En plus des options activées par défaut, sélectionnez également ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bf999-125">In addition to the default checked options, also check the following:</span></span>  
  
    -   <span data-ttu-id="bf999-126">**Outils d’administration Web** : Cochez également :</span><span class="sxs-lookup"><span data-stu-id="bf999-126">**Web Management Tools**: Also check:</span></span>  
  
        -   <span data-ttu-id="bf999-127">Compatibilité avec la gestion IIS 6 :</span><span class="sxs-lookup"><span data-stu-id="bf999-127">IIS 6 Management Compatibility:</span></span>  
  
            -   <span data-ttu-id="bf999-128">Console de gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="bf999-128">IIS 6 Management Console</span></span>  
  
            -   <span data-ttu-id="bf999-129">Compatibilité avec la métabase IIS et la configuration IIS 6</span><span class="sxs-lookup"><span data-stu-id="bf999-129">IIS Metabase and IIS 6 configuration compatibility</span></span>  
  
        -   <span data-ttu-id="bf999-130">Console de gestion IIS</span><span class="sxs-lookup"><span data-stu-id="bf999-130">IIS Management Console</span></span>  
  
    -   <span data-ttu-id="bf999-131">**Services World Wide Web** : Développez **Sécurité** et sélectionnez également :</span><span class="sxs-lookup"><span data-stu-id="bf999-131">**World Wide Web Services**: Expand **Security** and also select:</span></span>  
  
        -   <span data-ttu-id="bf999-132">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="bf999-132">Basic Authentication</span></span>  
  
        -   <span data-ttu-id="bf999-133">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bf999-133">Windows Authentication</span></span>  
  
4.  <span data-ttu-id="bf999-134">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf999-134">Select **OK**.</span></span> <span data-ttu-id="bf999-135">Une fois terminé, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-135">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="bf999-136">L’article [http://go.microsoft.com/fwlink/p/?LinkID=257033](http://go.microsoft.com/fwlink/p/?LinkId=257033) présente aussi les étapes permettant d’activer IIS sur Windows 7.</span><span class="sxs-lookup"><span data-stu-id="bf999-136">[http://go.microsoft.com/fwlink/p/?LinkId=257033](http://go.microsoft.com/fwlink/p/?LinkId=257033) also lists the steps to enable IIS on Windows 7.</span></span>  
  
#### <a name="install-iis-80-on-windows-8"></a><span data-ttu-id="bf999-137">Installation d’IIS 8.0 sur Windows 8</span><span class="sxs-lookup"><span data-stu-id="bf999-137">Install IIS 8.0 on Windows 8</span></span>  
  
1.  <span data-ttu-id="bf999-138">Sélectionnez le bouton Windows de votre clavier.</span><span class="sxs-lookup"><span data-stu-id="bf999-138">Select the Windows button on your keyboard.</span></span> <span data-ttu-id="bf999-139">Tapez **Programmes et fonctionnalités**, puis sélectionnez **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="bf999-139">Type **Programs and Features** and select**Settings**.</span></span> <span data-ttu-id="bf999-140">Dans la fenêtre des résultats, sélectionnez **Programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="bf999-140">In the Results window, select **Programs and Features**.</span></span>  
  
2.  <span data-ttu-id="bf999-141">Sélectionnez **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="bf999-141">Select **Turn Windows features on or off**.</span></span>  
  
3.  <span data-ttu-id="bf999-142">Sélectionnez **Internet Information Services** et développez **Internet Information Services**.</span><span class="sxs-lookup"><span data-stu-id="bf999-142">Select **Internet Information Services** and expand **Internet Information Services**.</span></span> <span data-ttu-id="bf999-143">En plus des options activées par défaut, sélectionnez également :</span><span class="sxs-lookup"><span data-stu-id="bf999-143">In addition to the default checked options, also select the following:</span></span>  
  
    -   <span data-ttu-id="bf999-144">**Outils d’administration Web** : Cochez également :</span><span class="sxs-lookup"><span data-stu-id="bf999-144">**Web Management Tools**: Also check:</span></span>  
  
        -   <span data-ttu-id="bf999-145">Compatibilité avec la gestion IIS 6 :</span><span class="sxs-lookup"><span data-stu-id="bf999-145">IIS 6 Management Compatibility:</span></span>  
  
            -   <span data-ttu-id="bf999-146">Console de gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="bf999-146">IIS 6 Management Console</span></span>  
  
            -   <span data-ttu-id="bf999-147">Compatibilité avec la métabase IIS et la configuration IIS 6</span><span class="sxs-lookup"><span data-stu-id="bf999-147">IIS Metabase and IIS 6 configuration compatibility</span></span>  
  
        -   <span data-ttu-id="bf999-148">Console de gestion IIS</span><span class="sxs-lookup"><span data-stu-id="bf999-148">IIS Management Console</span></span>  
  
    -   <span data-ttu-id="bf999-149">**Services World Wide Web** : Développez **Sécurité** et cochez également :</span><span class="sxs-lookup"><span data-stu-id="bf999-149">**World Wide Web Services**: Expand **Security** and also check:</span></span>  
  
        -   <span data-ttu-id="bf999-150">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="bf999-150">Basic Authentication</span></span>  
  
        -   <span data-ttu-id="bf999-151">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bf999-151">Windows Authentication</span></span>  
  
4.  <span data-ttu-id="bf999-152">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf999-152">Click **OK**.</span></span> <span data-ttu-id="bf999-153">Une fois terminé, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-153">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="bf999-154">L’article [http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) présente aussi les étapes permettant d’activer IIS sur Windows 8.</span><span class="sxs-lookup"><span data-stu-id="bf999-154">[http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) also lists the steps to enable IIS on Windows 8.</span></span>  
  
#### <a name="install-iis-80-on-windows-server-2012"></a><span data-ttu-id="bf999-155">Installation d'IIS 8.0 sur Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="bf999-155">Install IIS 8.0 on Windows Server 2012</span></span>  
  
1.  <span data-ttu-id="bf999-156">Ouvrez le **Gestionnaire de serveur**, puis cliquez sur **Tableau de bord** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="bf999-156">Open **Server Manager** and click **Dashboard** in the left pane.</span></span>  
  
2.  <span data-ttu-id="bf999-157">Cliquez sur **Ajouter des rôles et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="bf999-157">Click **Add roles and features**.</span></span> <span data-ttu-id="bf999-158">Vous pouvez aussi ouvrir **Ajouter des rôles et fonctionnalités** à partir du menu **Gérer** en haut à droite.</span><span class="sxs-lookup"><span data-stu-id="bf999-158">**Add Roles and Features** can also be opened from the **Manage** menu in the top right-hand corner.</span></span>  
  
3.  <span data-ttu-id="bf999-159">Dans la fenêtre **Avant de commencer**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-159">On the **Before You Begin** window, click **Next**.</span></span>  
  
4.  <span data-ttu-id="bf999-160">Dans la fenêtre **Type d’installation**, cliquez sur **Installation basée sur un rôle ou une fonctionnalité**, puis sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-160">On the **Installation Type** window, click **Role-based or feature-based installation**, and click **Next**.</span></span>  
  
5.  <span data-ttu-id="bf999-161">Dans la fenêtre **Sélection du serveur**, cliquez sur **Sélectionner un serveur du pool de serveurs**, cliquez sur le serveur voulu, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-161">On the **Server Selection** window, click **Select a server from the server pool**, click the desired server, and click **Next**.</span></span>  
  
     <span data-ttu-id="bf999-162">La fenêtre **Sélection du serveur** répertorie les serveurs qui ont été ajoutés avec **Ajouter un serveur** dans le **Gestionnaire de serveur**.</span><span class="sxs-lookup"><span data-stu-id="bf999-162">The **Server Selection** window lists the servers that have been added using **Add Server** in **Server Manager**.</span></span> <span data-ttu-id="bf999-163">Le serveur local est sélectionné par défaut.</span><span class="sxs-lookup"><span data-stu-id="bf999-163">By default, it selects the local server.</span></span> <span data-ttu-id="bf999-164">[Ajouter des serveurs au Gestionnaire de serveur](http://go.microsoft.com/fwlink/p/?LinkID=241353) répertorie les étapes permettant d’utiliser **Ajouter un serveur** sur [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-164">[Add Servers to Server Manager](http://go.microsoft.com/fwlink/p/?LinkID=241353) lists the steps to use **Add Server** on [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].</span></span>  
  
6.  <span data-ttu-id="bf999-165">Dans la fenêtre **Rôles du serveur**, cliquez sur **Serveur Web (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="bf999-165">On the **Server Roles** window, click **Web Server (IIS)**.</span></span> <span data-ttu-id="bf999-166">Si vous y êtes invité, cliquez sur **Ajouter des fonctionnalités**, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-166">If prompted, click **Add Features**, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="bf999-167">Dans la fenêtre **Fonctionnalités**, laissez les options par défaut activées et tenez également compte de ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bf999-167">On the **Features** window, keep the default options enabled and also consider the following:</span></span>  
  
     <span data-ttu-id="bf999-168">**Fonctionnalités de .NET Framework 3.5** : [!INCLUDE[dotnet45](../includes/dotnet45-md.md)] et [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] peuvent être utilisés pour développer des applications .NET impliquant le [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-168">**.Net Framework 3.5 Features**: [!INCLUDE[dotnet45](../includes/dotnet45-md.md)] and [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] can be used to develop .Net applications involving the [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span> <span data-ttu-id="bf999-169">En règle générale, les **fonctionnalités de [!INCLUDE[dotnet45](../includes/dotnet45-md.md)]** sont déjà installées.</span><span class="sxs-lookup"><span data-stu-id="bf999-169">Typically, **[!INCLUDE[dotnet45](../includes/dotnet45-md.md)] Features** is already installed.</span></span> <span data-ttu-id="bf999-170">Si vous envisagez d’utiliser [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] pour créer des applications sur cet ordinateur, vous pouvez également installer les **fonctionnalités de .NET Framework 3.5**.</span><span class="sxs-lookup"><span data-stu-id="bf999-170">If you will use [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] to create applications on this computer, then **.Net Framework 3.5 Features** can also be installed.</span></span>  
  
     <span data-ttu-id="bf999-171">**Message Queuing** : Si vous utilisez l’adaptateur MSMQ, vous pouvez créer un magasin MSMQ local en cochant **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="bf999-171">**Message Queuing**: If you are using the MSMQ adapter, you can create a local MSMQ store by checking **Message Queuing**.</span></span>  
  
     <span data-ttu-id="bf999-172">**Serveur SMTP** : Si vous utilisez l’adaptateur SMTP, vous pouvez créer un serveur SMTP local en cochant **Serveur SMTP**.</span><span class="sxs-lookup"><span data-stu-id="bf999-172">**SMTP Server**: If you are using the SMTP adapter, you can create a local SMTP Server by checking **SMTP Server**.</span></span>  
  
     <span data-ttu-id="bf999-173">**Windows Identity Foundation (WIF) 3.5** : Windows Identity Foundation (WIF) est requis par l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] lors de l’utilisation de l’option d’installation CSOM.</span><span class="sxs-lookup"><span data-stu-id="bf999-173">**Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) is required by the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] adapter when using the CSOM installation option.</span></span> <span data-ttu-id="bf999-174">L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit l’option d’installation CSOM pour l’adaptateur [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-174">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the CSOM installation option for the [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] adapter.</span></span>  
  
     <span data-ttu-id="bf999-175">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-175">Click **Next**.</span></span>  
  
8.  <span data-ttu-id="bf999-176">Dans la fenêtre **Rôle Serveur Web (IIS)**, cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-176">On the **Web Server Role (IIS)** window, click **Next**.</span></span>  
  
9. <span data-ttu-id="bf999-177">Dans la fenêtre **Services de rôle** (sous **Rôle Serveur Web (IIS)**), cliquez sur les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf999-177">On the **Role Services** window (under **Web Server Role (IIS)**), click the following options:</span></span>  
  
     <span data-ttu-id="bf999-178">**Sécurité** : Outre les options par défaut, cliquez également sur ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bf999-178">**Security**: In addition to the default options, also click:</span></span>  
  
    -   <span data-ttu-id="bf999-179">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="bf999-179">Basic Authentication</span></span>  
  
    -   <span data-ttu-id="bf999-180">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="bf999-180">Windows Authentication</span></span>  
  
     <span data-ttu-id="bf999-181">**Développement d’applications** : Les options par défaut sont suffisantes pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-181">**Application Development**: The default options are sufficient for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bf999-182">Si vous hébergez d'autres applications IIS basées sur cet ordinateur, sélectionnez les rôles nécessaires.</span><span class="sxs-lookup"><span data-stu-id="bf999-182">If you host other IIS-based applications on this computer, check the needed roles.</span></span>  
  
     <span data-ttu-id="bf999-183">**Outils de gestion** : Outre les options par défaut, cliquez également sur :</span><span class="sxs-lookup"><span data-stu-id="bf999-183">**Management Tools**: In addition to the default options, also click:</span></span>  
  
    -   <span data-ttu-id="bf999-184">Console de gestion IIS</span><span class="sxs-lookup"><span data-stu-id="bf999-184">IIS Management Console</span></span>  
  
    -   <span data-ttu-id="bf999-185">Compatibilité avec la gestion IIS 6 :</span><span class="sxs-lookup"><span data-stu-id="bf999-185">IIS 6 Management Compatibility:</span></span>  
  
        -   <span data-ttu-id="bf999-186">Compatibilité avec la métabase IIS 6</span><span class="sxs-lookup"><span data-stu-id="bf999-186">IIS 6 Metabase Compatibility</span></span>  
  
        -   <span data-ttu-id="bf999-187">Console de gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="bf999-187">IIS 6 Management Console</span></span>  
  
     <span data-ttu-id="bf999-188">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-188">Click **Next**.</span></span>  
  
10. <span data-ttu-id="bf999-189">Dans la fenêtre **Confirmation**, cliquez sur **Installer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-189">On the **Confirmation** window, click **Install**.</span></span> <span data-ttu-id="bf999-190">Une fois terminé, cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-190">When complete, click **Close**.</span></span>  
  
 <span data-ttu-id="bf999-191">L’article [http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) présente aussi les étapes permettant d’activer IIS sur [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-191">[http://go.microsoft.com/fwlink/p/?LinkID=291297](http://go.microsoft.com/fwlink/p/?LinkID=291297) also lists the steps to enable IIS on [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)].</span></span>  
  
##  <span data-ttu-id="bf999-192"><a name="BKMK_XLS"></a> Installation de Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="bf999-192"><a name="BKMK_XLS"></a> Install Microsoft Office Excel</span></span>  
  
1.  <span data-ttu-id="bf999-193">Exécutez le programme d'installation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="bf999-193">Run the Microsoft Office setup.</span></span>  
  
2.  <span data-ttu-id="bf999-194">Dans la page **Type d’installation**, sélectionnez **Installation personnalisée**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-194">When you reach the **Type of Installation** screen, select **Custom Install**, and then select **Next**.</span></span>  
  
3.  <span data-ttu-id="bf999-195">Dans la page **Installation personnalisée**, sélectionnez **Excel**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-195">On the **Custom Setup** screen, select **Excel**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="bf999-196">Sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-196">Select **Install**.</span></span>  
  
5.  <span data-ttu-id="bf999-197">Dans **Fin de l’installation**, sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-197">In **Setup Completed**, select **Finish**.</span></span>  
  
 <span data-ttu-id="bf999-198">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-198">**Additional**</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bf999-199"> prend uniquement en charge la version 32 bits de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="bf999-199"> supports only 32-bit version of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="bf999-200">Microsoft Office Excel est requis par BAM (Business Activity Monitoring) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-200">Microsoft Office Excel is required by Business Activity Monitoring (BAM) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bf999-201">Le classeur BAM Office Excel définit les processus d'entreprise que vous souhaitez analyser.</span><span class="sxs-lookup"><span data-stu-id="bf999-201">The BAM Office Excel Workbook defines the business processes you want to monitor.</span></span> <span data-ttu-id="bf999-202">Vous utilisez également le classeur Excel BAM pour définir la manière dont les utilisateurs des activités visualisent les données collectées par l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="bf999-202">You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.</span></span>  
  
-   <span data-ttu-id="bf999-203">Pour charger correctement le fichier BAM.xla dans Excel, installez **Visual Basic pour Applications** sous **Composants partagés d’Office**.</span><span class="sxs-lookup"><span data-stu-id="bf999-203">To successfully load BAM.xla into Excel, install **Visual Basic for Applications** under **Office Shared Features**.</span></span> <span data-ttu-id="bf999-204">Dans le cas contraire, vous risquez de recevoir l’erreur « Ce classeur a perdu son projet VBA, ses contrôles ActiveX et d’autres fonctionnalités liées à la programmabilité ».</span><span class="sxs-lookup"><span data-stu-id="bf999-204">Otherwise, you may get error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”</span></span>  
  
##  <span data-ttu-id="bf999-205"><a name="BKMK_VS"></a> Installation de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bf999-205"><a name="BKMK_VS"></a> Install Visual Studio</span></span>  
  
1.  <span data-ttu-id="bf999-206">Exécutez l'installation de Visual Studio en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="bf999-206">Run the Visual Studio setup as Administrator.</span></span>  
  
2.  <span data-ttu-id="bf999-207">Acceptez le contrat de licence et cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="bf999-207">Accept the license agreement and click **Next**.</span></span>  
  
3.  <span data-ttu-id="bf999-208">Dans **Fonctionnalités facultatives à installer**, sélectionnez les options dont vous avez besoin, puis sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-208">In **Optional features to install**, select the options you need and then select **Install**.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bf999-209"> ne nécessite aucune des fonctionnalités facultatives.</span><span class="sxs-lookup"><span data-stu-id="bf999-209"> does not require any of the optional features.</span></span>  
  
4.  <span data-ttu-id="bf999-210">Dans la page **Terminer**, fermez la fenêtre ou cliquez sur **Lancer** pour ouvrir Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bf999-210">On the **Finish** page, close the window or click **Launch** to open Visual Studio.</span></span>  
  
 <span data-ttu-id="bf999-211">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-211">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-212">Si vous installez Visual Studio avant d’installer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis effectuez une mise à niveau vers Visual Studio Team Explorer, vous devrez peut-être réparer votre installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir de l’option **Panneau de configuration** / **Programmes**.</span><span class="sxs-lookup"><span data-stu-id="bf999-212">If you install Visual Studio before installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and then upgrade to Visual Studio Team Explorer, you may need to repair your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation from the **Control Panel** / **Programs** option.</span></span>  
  
-   <span data-ttu-id="bf999-213">Visual Studio installe automatiquement Microsoft SQL Server Express, qui n'est pas utilisé par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-213">Visual Studio automatically installs Microsoft SQL Server Express; which is not used by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="bf999-214">La bonne pratique est de désinstaller Microsoft SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="bf999-214">As a best practice, uninstall Microsoft SQL Server Express.</span></span>  
  
-   <span data-ttu-id="bf999-215">Les outils de développement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont en effet basés sur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bf999-215">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] development tools are based on Visual Studio.</span></span> <span data-ttu-id="bf999-216">Au minimum, vous devez installer le composant Microsoft Visual C#® .NET de Visual Studio avant d’installer le composant **Outils et kit de développement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**.</span><span class="sxs-lookup"><span data-stu-id="bf999-216">At a minimum, you must install the Microsoft Visual C#® .NET component of Visual Studio before you install the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**Developer Tools and SDK**.</span></span>  
  
-   <span data-ttu-id="bf999-217">Visual Studio n’est *pas* nécessaire si vous installez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur de production (d’exécution uniquement) sur lequel aucun débogage ni développement d’application n’est requis.</span><span class="sxs-lookup"><span data-stu-id="bf999-217">Visual Studio is *not* required if you are installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on a production computer (runtime only), on which no application development or debugging is required.</span></span>  
  
-   <span data-ttu-id="bf999-218">Le composant d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exige [!INCLUDE[dotnet45](../includes/dotnet45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-218">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime requires [!INCLUDE[dotnet45](../includes/dotnet45-md.md)].</span></span> <span data-ttu-id="bf999-219">.NET Framework 3.0 est indispensable si l’adaptateur ou l’intercepteur WCF (Windows Communication Foundation) est installé.</span><span class="sxs-lookup"><span data-stu-id="bf999-219">The .NET Framework 3.0 is required if the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed.</span></span>  
  
##  <span data-ttu-id="bf999-220"><a name="BKMK_SQL"></a> Installation de SQL Server</span><span class="sxs-lookup"><span data-stu-id="bf999-220"><a name="BKMK_SQL"></a> Install SQL Server</span></span>  
 <span data-ttu-id="bf999-221">Installation de [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-221">Install [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span></span>  
  
 <span data-ttu-id="bf999-222">Installation de [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-222">Install [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span></span>  
  
 <span data-ttu-id="bf999-223">Installation de [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-223">Install [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span></span>  
  
 <span data-ttu-id="bf999-224">Lors de l'installation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], sélectionnez les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf999-224">When you install [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], select the following features:</span></span>  
  
-   <span data-ttu-id="bf999-225">Services Moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="bf999-225">Database Engine Services</span></span>  
  
    -   <span data-ttu-id="bf999-226">Réplication SQL Server</span><span class="sxs-lookup"><span data-stu-id="bf999-226">SQL Server Replication</span></span>  
  
    -   <span data-ttu-id="bf999-227">Recherche en texte intégral</span><span class="sxs-lookup"><span data-stu-id="bf999-227">Full-Text Search</span></span>  
  
-   <span data-ttu-id="bf999-228">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="bf999-228">Analysis Services</span></span>  
  
-   <span data-ttu-id="bf999-229">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="bf999-229">Reporting Services</span></span>  
  
-   <span data-ttu-id="bf999-230">Fonctionnalités partagées</span><span class="sxs-lookup"><span data-stu-id="bf999-230">Shared Features</span></span>  
  
    -   <span data-ttu-id="bf999-231">SQL Server Data Tools (SQL Server 2014/SQL Server 2012) ou Business Intelligence Development Studio (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="bf999-231">SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) or Business Intelligence Development Studio (SQL Server 2008 R2)</span></span>  
  
         [<span data-ttu-id="bf999-232">Téléchargez SQL Server 2014 Data Tools</span><span class="sxs-lookup"><span data-stu-id="bf999-232">Download SQL Server 2014 Data Tools</span></span>](http://www.microsoft.com/download/details.aspx?id=42313)  
  
    -   <span data-ttu-id="bf999-233">Connectivité des outils clients</span><span class="sxs-lookup"><span data-stu-id="bf999-233">Client Tools Connectivity</span></span>  
  
    -   <span data-ttu-id="bf999-234">Integration Services</span><span class="sxs-lookup"><span data-stu-id="bf999-234">Integration Services</span></span>  
  
    -   <span data-ttu-id="bf999-235">Outils de gestion - Base</span><span class="sxs-lookup"><span data-stu-id="bf999-235">Management Tools - Basic</span></span>  
  
        -   <span data-ttu-id="bf999-236">Outils de gestion - Complet</span><span class="sxs-lookup"><span data-stu-id="bf999-236">Management Tools - Complete</span></span>  
  
 <span data-ttu-id="bf999-237">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-237">**Additional**</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="bf999-238"> prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l'exception des classements binaires.</span><span class="sxs-lookup"><span data-stu-id="bf999-238"> supports all case-sensitive and case-insensitive SQL Server collations except for binary collations.</span></span> <span data-ttu-id="bf999-239">Les classements binaires ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bf999-239">Binary collations are not supported.</span></span>  
  
-   <span data-ttu-id="bf999-240">Pour des performances optimales, Microsoft recommande d’utiliser SQL Server Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="bf999-240">For optimal performance, Microsoft recommends using the Enterprise Edition of SQL Server.</span></span> <span data-ttu-id="bf999-241">Consultez les [éditions SQL Server 2008 R2](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), les [éditions SQL Server 2012](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx) ou les [éditions SQL Server 2014](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).</span><span class="sxs-lookup"><span data-stu-id="bf999-241">See [SQL Server 2008 R2 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), [SQL Server 2012 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx), or [SQL Server 2014 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="bf999-242">Les Service Packs et mises à jour Windows sont pris en charge et doivent être installés.</span><span class="sxs-lookup"><span data-stu-id="bf999-242">Service packs and Windows Updates are supported and should be installed.</span></span>  
  
-   <span data-ttu-id="bf999-243">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts, MS DTC (Microsoft Distributed Transaction Coordinator) gère les transactions entre les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="bf999-243">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.</span></span> <span data-ttu-id="bf999-244">La fonctionnalité [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn ne prend pas en charge les transactions MSDTC.</span><span class="sxs-lookup"><span data-stu-id="bf999-244">The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn feature does not support MSDTC transactions.</span></span> <span data-ttu-id="bf999-245">La fonctionnalité AlwaysOn [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="bf999-245">The [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] AlwaysOn feature is not supported.</span></span>  
  
##  <span data-ttu-id="bf999-246"><a name="BKMK_MQSeries"></a> Installation des composants requis pour MQSeries</span><span class="sxs-lookup"><span data-stu-id="bf999-246"><a name="BKMK_MQSeries"></a> Install MQSeries Prerequisites</span></span>  
 <span data-ttu-id="bf999-247">**Adaptateur MQSeries** : Installé automatiquement avec l’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bf999-247">**MQSeries adapter**: Automatically installed with the BizTalk Server installation.</span></span>  
  
 <span data-ttu-id="bf999-248">**Adaptateur MQSeries Client (MQSC)** :</span><span class="sxs-lookup"><span data-stu-id="bf999-248">**MQSeries Client (MQSC) adapter**:</span></span>  
  
1.  <span data-ttu-id="bf999-249">Exécuter l'installation de HIS (Host Integration Server)</span><span class="sxs-lookup"><span data-stu-id="bf999-249">Run the Host Integration Server (HIS) installation</span></span>  
  
2.  <span data-ttu-id="bf999-250">Dans l’installation des composants, développez **Adaptateurs BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="bf999-250">In component installation, expand **BizTalk Adapters**.</span></span>  
  
3.  <span data-ttu-id="bf999-251">Sélectionnez **Adaptateur BizTalk pour WebSphere MQ (basé sur le client)**.</span><span class="sxs-lookup"><span data-stu-id="bf999-251">Select **BizTalk Adapter for WebSphere MQ (Client-Based)**.</span></span>  
  
 <span data-ttu-id="bf999-252">**Versions prises en charge d’IBM WebSphere MQ** :</span><span class="sxs-lookup"><span data-stu-id="bf999-252">**Supported IBM WebSphere MQ versions**:</span></span>  
  
-   <span data-ttu-id="bf999-253">IBM WebSphere MQ 6.0.2.12 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bf999-253">IBM WebSphere MQ 6.0.2.12 and later</span></span>  
  
-   <span data-ttu-id="bf999-254">IBM WebSphere MQ 7.0.1.9 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bf999-254">IBM WebSphere MQ 7.0.1.9 and later</span></span>  
  
-   <span data-ttu-id="bf999-255">IBM WebSphere MQ 7.1.0.5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bf999-255">IBM WebSphere MQ 7.1.0.5 and later</span></span>  
  
-   <span data-ttu-id="bf999-256">IBM WebSphere MQ 7.5.0.3 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="bf999-256">IBM WebSphere MQ 7.5.0.3 and later</span></span>  
  
-   <span data-ttu-id="bf999-257">IBM WebSphere MQ 8 (limité à l’exécution, aucune API d’administration)</span><span class="sxs-lookup"><span data-stu-id="bf999-257">IBM WebSphere MQ 8 (limited to runtime; no administration APIs)</span></span>  
  
     <span data-ttu-id="bf999-258">La prise en charge de MQ version 8 est incluse avec [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).</span><span class="sxs-lookup"><span data-stu-id="bf999-258">MQ version 8 support is included with [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf999-259">Si une version WebSphere MQ spécifique n'est pas répertoriée, comme MQ 5.x, c'est qu'elle n'est pas prise en charge par cette version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-259">If a specific WebSphere MQ version is not listed, like MQ 5.x, then it is not supported with this [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] version.</span></span>  
  
 <span data-ttu-id="bf999-260">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-260">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-261">Il est recommandé de toujours installer le dernier pack de correctifs WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="bf999-261">As a best practice, always install the latest WebSphere MQ fix pack.</span></span> <span data-ttu-id="bf999-262">Consultez [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).</span><span class="sxs-lookup"><span data-stu-id="bf999-262">See [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).</span></span>  
  
-   <span data-ttu-id="bf999-263">Si IBM WebSphere MQ est installé sur un ordinateur non-Windows, installez l’**application MQSAgent COM+** (MQSConfigWiz.exe) et **MQSeries Server for Windows** sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="bf999-263">If IBM WebSphere MQ is installed on a non-Windows computer, install the **MQSAgent COM+ application** (MQSConfigWiz.exe) and **MQSeries Server for Windows** on the same computer.</span></span> <span data-ttu-id="bf999-264">Si IBM WebSphere MQ est installé sur un ordinateur Windows, l’**application MQSAgent COM+** et le programme **MQSeries Server for Windows** ne sont ni utilisés ni nécessaires.</span><span class="sxs-lookup"><span data-stu-id="bf999-264">If IBM WebSphere MQ is installed on a Windows computer, then the **MQSAgent COM+ application** and **MQSeries Server for Windows** program are not used or needed.</span></span>  
  
     <span data-ttu-id="bf999-265">**MQSConfigWiz.exe** est inclus dans les fichiers d’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-265">**MQSConfigWiz.exe** is included in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation files.</span></span>  
  
     <span data-ttu-id="bf999-266">**MQSeries Server pour Windows** n’est pas un programme Microsoft et doit être obtenu avec votre programme IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="bf999-266">**MQSeries Server for Windows** is not a Microsoft program and must be obtained with your IBM WebSphere MQ program.</span></span>  
  
-   <span data-ttu-id="bf999-267">L’article [Adaptateur MQSeries](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) fournit plus d’informations sur l’adaptateur MQSeries, y compris la configuration des différents composants.</span><span class="sxs-lookup"><span data-stu-id="bf999-267">[MQSeries Adapter](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) provides more information on the MQSeries adapter, including configuring the different components.</span></span> <span data-ttu-id="bf999-268">La page [BizTalk Server : Adaptateurs MQSeries et MQSeries Client (MQSC)](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) fournit des détails supplémentaires sur les adaptateurs MQSeries et MQSC.</span><span class="sxs-lookup"><span data-stu-id="bf999-268">[BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) provides additional details on the MQSeries and MQSC adapters.</span></span>  
  
-   <span data-ttu-id="bf999-269">IBM WebSphere n'est pas un produit Microsoft et n'est pas pris en charge par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bf999-269">IBM WebSphere is not a Microsoft product and is not supported by Microsoft.</span></span> <span data-ttu-id="bf999-270">Microsoft ne donne aucune garantie quant à la pertinence de ce programme.</span><span class="sxs-lookup"><span data-stu-id="bf999-270">Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="bf999-271">Pour plus d'informations sur IBM WebSphere MQ, y compris les instructions de téléchargement, consultez www.ibm.com.</span><span class="sxs-lookup"><span data-stu-id="bf999-271">For more information about IBM WebSphere MQ, including download instructions, see www.ibm.com.</span></span>  
  
##  <span data-ttu-id="bf999-272"><a name="BKMK_BAMAlerts"></a> Alertes BAM</span><span class="sxs-lookup"><span data-stu-id="bf999-272"><a name="BKMK_BAMAlerts"></a> BAM Alerts</span></span>  
 <span data-ttu-id="bf999-273">Les alertes BAM avec [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] ou [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] utilisent la fonctionnalité Messagerie de base de données dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-273">BAM Alerts with [!INCLUDE[sqlserver2014](../includes/sqlserver2014-md.md)] or [!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)] uses Database Mail in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="bf999-274">Alertes BAM avec [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] utilise SQL Notification Services.</span><span class="sxs-lookup"><span data-stu-id="bf999-274">BAM Alerts with [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] uses SQL Notification Services.</span></span> <span data-ttu-id="bf999-275">Avant d'installer ou de configurer les alertes BAM, vous devez configurer les services de notification Services ou la messagerie de base de données dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-275">Before installing or configuring BAM Alerts, you must configure the Notification Services or Database Mail in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
###  <span data-ttu-id="bf999-276"><a name="BKMK_DBMail"></a> Alertes BAM utilisant SQL Server 2012/2014</span><span class="sxs-lookup"><span data-stu-id="bf999-276"><a name="BKMK_DBMail"></a> BAM Alerts using SQL Server 2012/2014</span></span>  
 <span data-ttu-id="bf999-277">Configurez la [messagerie de base de données SQL Server 2012](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="bf999-277">Configure [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).</span></span>  
  
 <span data-ttu-id="bf999-278">Configurez la [messagerie de base de données SQL Server 2014](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).</span><span class="sxs-lookup"><span data-stu-id="bf999-278">Configure [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="bf999-279">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-279">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-280">La fonctionnalité Messagerie de base de données utilise un serveur SMTP pour envoyer les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="bf999-280">Database Mail uses an SMTP server to send the BAM Alerts.</span></span> <span data-ttu-id="bf999-281">Le serveur SMTP peut être installé localement sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou un autre serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="bf999-281">SMTP Server can be installed locally on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or on another IIS server.</span></span> <span data-ttu-id="bf999-282">L’[annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md) répertorie les étapes de l’installation et de la configuration d’un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="bf999-282">[Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md) lists the steps to install and configure a SMTP Server.</span></span>  
  
###  <span data-ttu-id="bf999-283"><a name="BKMK_SSNS"></a> Alertes BAM utilisant SQL Server 2008 R2 – Installation de SQL Server 2005 Notification Services</span><span class="sxs-lookup"><span data-stu-id="bf999-283"><a name="BKMK_SSNS"></a> BAM Alerts using SQL Server 2008 R2 – Install SQL Server 2005 Notification Services</span></span>  
  
1.  <span data-ttu-id="bf999-284">Consultez [Feature Pack pour Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).</span><span class="sxs-lookup"><span data-stu-id="bf999-284">Go to [Feature Pack for Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).</span></span>  
  
2.  <span data-ttu-id="bf999-285">Téléchargez et installez le package de plate-forme approprié pour les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="bf999-285">Download and install the appropriate platform package for the following components:</span></span>  
  
     <span data-ttu-id="bf999-286">**Microsoft SQL Server Native Client**</span><span class="sxs-lookup"><span data-stu-id="bf999-286">**Microsoft SQL Server Native Client**</span></span>  
  
    -   <span data-ttu-id="bf999-287">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" Package X86 (sqlncli.msi)</span><span class="sxs-lookup"><span data-stu-id="bf999-287">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" X86 Package (sqlncli.msi)</span></span>  
  
    -   <span data-ttu-id="bf999-288">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" Package X64 (sqlncli_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="bf999-288">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" X64 Package (sqlncli_x64.msi)</span></span>  
  
     <span data-ttu-id="bf999-289">**Collection d’objets de gestion de Microsoft SQL Server 2005**</span><span class="sxs-lookup"><span data-stu-id="bf999-289">**Microsoft SQL Server 2005 Management Objects Collection**</span></span>  
  
    -   <span data-ttu-id="bf999-290">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" Package X86 (SQLServer2005_XMO.msi)</span><span class="sxs-lookup"><span data-stu-id="bf999-290">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" X86 Package (SQLServer2005_XMO.msi)</span></span>  
  
    -   <span data-ttu-id="bf999-291">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" Package X64 (SQLServer2005_XMO_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="bf999-291">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" X64 Package (SQLServer2005_XMO_x64.msi)</span></span>  
  
     <span data-ttu-id="bf999-292">**Composants clients Notification Services de Microsoft SQL Server 2005**</span><span class="sxs-lookup"><span data-stu-id="bf999-292">**Microsoft SQL Server 2005 Notification Services Client Components**</span></span>  
  
    -   <span data-ttu-id="bf999-293">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" Package X86 (SQLServer2005_NS.msi)</span><span class="sxs-lookup"><span data-stu-id="bf999-293">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" X86 Package (SQLServer2005_NS.msi)</span></span>  
  
    -   <span data-ttu-id="bf999-294">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" Package X64 (SQLServer2005_NS_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="bf999-294">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" X64 Package (SQLServer2005_NS_x64.msi)</span></span>  
  
 <span data-ttu-id="bf999-295">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-295">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-296">Il n'est pas nécessaire de configurer SQL Notification Services ; installez-le seulement sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-296">SQL Notification Services does not need to be configured; only installed on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
##  <span data-ttu-id="bf999-297"><a name="BKMK_WIF"></a> Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="bf999-297"><a name="BKMK_WIF"></a> Windows Identity Foundation</span></span>  
  
|||  
|-|-|  
|[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]<span data-ttu-id="bf999-298"> 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] et [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2</span><span class="sxs-lookup"><span data-stu-id="bf999-298"> 8.1, [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)], and [!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)] R2</span></span>|<span data-ttu-id="bf999-299">Windows Identity Foundation est inclus dans le système d’exploitation comme fonctionnalité dans **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="bf999-299">Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.</span></span>|  
|[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]<span data-ttu-id="bf999-300"> SP1</span><span class="sxs-lookup"><span data-stu-id="bf999-300"> SP1</span></span>|<span data-ttu-id="bf999-301">Téléchargement disponible sur la page [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) LIEN HYPERTEXTE "http://www.microsoft.com/download/details.aspx?id=17331".</span><span class="sxs-lookup"><span data-stu-id="bf999-301">Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "http://www.microsoft.com/download/details.aspx?id=17331" .</span></span>|  
  
 <span data-ttu-id="bf999-302">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-302">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-303">Windows Identity Foundation (WIF) est requis pour l’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ou SharePoint Online lorsque celui-ci est utilisé avec le modèle CSOM (Client Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-303">Windows Identity Foundation (WIF) is required for the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] adapter or SharePoint Online when used with [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Client Side Object Model (CSOM).</span></span> <span data-ttu-id="bf999-304">Plus précisément :</span><span class="sxs-lookup"><span data-stu-id="bf999-304">Specifically:</span></span>  
  
    |<span data-ttu-id="bf999-305">Option d’installation</span><span class="sxs-lookup"><span data-stu-id="bf999-305">Installation Option</span></span>|<span data-ttu-id="bf999-306">WIF requis</span><span class="sxs-lookup"><span data-stu-id="bf999-306">WIF Required</span></span>|  
    |-------------------------|------------------|  
    |<span data-ttu-id="bf999-307">Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] avec CSOM</span><span class="sxs-lookup"><span data-stu-id="bf999-307">[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter with CSOM</span></span>|<span data-ttu-id="bf999-308">Oui</span><span class="sxs-lookup"><span data-stu-id="bf999-308">Yes</span></span>|  
    |<span data-ttu-id="bf999-309">SharePoint Online avec CSOM</span><span class="sxs-lookup"><span data-stu-id="bf999-309">SharePoint Online with CSOM</span></span>|<span data-ttu-id="bf999-310">Oui</span><span class="sxs-lookup"><span data-stu-id="bf999-310">Yes</span></span>|  
    |<span data-ttu-id="bf999-311">Service Web Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] (supprimé)</span><span class="sxs-lookup"><span data-stu-id="bf999-311">[!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] Adapter Web Service (deprecated)</span></span>|<span data-ttu-id="bf999-312">Non</span><span class="sxs-lookup"><span data-stu-id="bf999-312">No</span></span>|  
    |<span data-ttu-id="bf999-313">Pas de SharePoint</span><span class="sxs-lookup"><span data-stu-id="bf999-313">No SharePoint</span></span>|<span data-ttu-id="bf999-314">Non</span><span class="sxs-lookup"><span data-stu-id="bf999-314">No</span></span>|  
  
-   <span data-ttu-id="bf999-315">L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations spécifiques sur les options d’installation de [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-315">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides specific information on the [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation options.</span></span>  
  
##  <span data-ttu-id="bf999-316"><a name="BKMK_WSS"></a> Installation et configuration de Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="bf999-316"><a name="BKMK_WSS"></a> Install and Configure Microsoft SharePoint</span></span>  
 <span data-ttu-id="bf999-317">Installation de [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-317">Install [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span></span>  
  
 <span data-ttu-id="bf999-318">Installation de [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-318">Install [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)</span></span>  
  
 <span data-ttu-id="bf999-319">Installation de [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-319">Install [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span></span>  
  
 <span data-ttu-id="bf999-320">Installation de [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-320">Install [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span></span>  
  
 <span data-ttu-id="bf999-321">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-321">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-322">Si vous installez SharePoint, vous devez le faire avant de continuer avec le reste de la configuration requise de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-322">If you are installing SharePoint, you must do so before continuing with the remaining [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prerequisites.</span></span>  
  
-   <span data-ttu-id="bf999-323">L’installation et la configuration de SharePoint s’effectuent comme suit :</span><span class="sxs-lookup"><span data-stu-id="bf999-323">Installing and configuring SharePoint consists of the following procedures:</span></span>  
  
    -   <span data-ttu-id="bf999-324">installation de SharePoint ;</span><span class="sxs-lookup"><span data-stu-id="bf999-324">Install SharePoint</span></span>  
  
    -   <span data-ttu-id="bf999-325">configuration de SharePoint ;</span><span class="sxs-lookup"><span data-stu-id="bf999-325">Configure SharePoint</span></span>  
  
    -   <span data-ttu-id="bf999-326">extension du site Web par défaut en tant que serveur virtuel.</span><span class="sxs-lookup"><span data-stu-id="bf999-326">Extend the default Web site as a virtual server</span></span>  
  
-   <span data-ttu-id="bf999-327">L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit les options d’installation de l’adaptateur SharePoint pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="bf999-327">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the SharePoint adapter installation options for BizTalk Server.</span></span>  
  
-   <span data-ttu-id="bf999-328">Lorsque vous utilisez l’adaptateur SharePoint, il est recommandé d’installer la nouvelle option CSOM à la place du service web SharePoint Service, qui est décrite dans l’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="bf999-328">When using the SharePoint adapter, it is recommended to install the new CSOM option instead of the SharePoint Service Web Service; described at [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).</span></span>  
  
##  <span data-ttu-id="bf999-329"><a name="BKMK_SharedMem"></a> Désactivation du protocole de mémoire partagée</span><span class="sxs-lookup"><span data-stu-id="bf999-329"><a name="BKMK_SharedMem"></a> Disable the Shared Memory Protocol</span></span>  
  
1.  <span data-ttu-id="bf999-330">Ouvrez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="bf999-330">Open **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="bf999-331">Dans le **Gestionnaire de configuration SQL Server**, développez **Configuration du réseau SQL Server**, puis sélectionnez **Protocoles pour MSSQLSERVER**.</span><span class="sxs-lookup"><span data-stu-id="bf999-331">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.</span></span>  
  
3.  <span data-ttu-id="bf999-332">Cliquez avec le bouton droit sur **Mémoire partagée**, puis sélectionnez **Désactiver**.</span><span class="sxs-lookup"><span data-stu-id="bf999-332">Right-click **Shared Memory**, and then select **Disable**.</span></span>  
  
4.  <span data-ttu-id="bf999-333">Sélectionnez **Services SQL Server**, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="bf999-333">Select **SQL Server Services**, right-click **SQL Server (MSSQLSERVER)**, and then select **Stop**.</span></span> <span data-ttu-id="bf999-334">Une fois le service arrêté, cliquez de nouveau avec le bouton droit sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="bf999-334">After the service has stopped, right-click **SQL Server (MSSQLSERVER)** again, and then select **Start**.</span></span>  
  
5.  <span data-ttu-id="bf999-335">Fermez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="bf999-335">Close **SQL Server Configuration Manager**.</span></span>  
  
 <span data-ttu-id="bf999-336">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-336">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-337">Sous certaines conditions de surcharge (telles que l’accès à un serveur SQL Server par des clients à partir du même ordinateur), le protocole de mémoire partagée du serveur SQL Server risque de réduire les performances de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-337">Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performance.</span></span> <span data-ttu-id="bf999-338">Vous pouvez corriger ce comportement en désactivant le protocole de réseau de la mémoire partagée dans la configuration du réseau SQL Server.</span><span class="sxs-lookup"><span data-stu-id="bf999-338">You can resolve this behavior by disabling the Shared Memory network protocol in SQL Server Network Configuration.</span></span>  
  
-   <span data-ttu-id="bf999-339">ReplaceThisText</span><span class="sxs-lookup"><span data-stu-id="bf999-339">ReplaceThisText</span></span>  
  
##  <span data-ttu-id="bf999-340"><a name="BKMK_LocalAdmin"></a> Adhésion au groupe Administrateurs local</span><span class="sxs-lookup"><span data-stu-id="bf999-340"><a name="BKMK_LocalAdmin"></a> Join the Local Administrators Group</span></span>  
 <span data-ttu-id="bf999-341">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : [Windows Server 2012 : Guide pratique pour ajouter un compte dans un groupe Administrateurs local](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span><span class="sxs-lookup"><span data-stu-id="bf999-341">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : [Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span></span>  
  
 <span data-ttu-id="bf999-342">**Windows 8.1** : Pour ouvrir Utilisateurs et groupes locaux sur Windows 8.1, appuyez sur le bouton Windows du clavier et tapez **groupes**.</span><span class="sxs-lookup"><span data-stu-id="bf999-342">**Windows 8.1**: To open Local Users and Groups on Windows 8, click the Windows button on the keyboard and type **groups**.</span></span> <span data-ttu-id="bf999-343">Dans la fenêtre de recherche, cliquez sur **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="bf999-343">In the Search window, click **Settings**.</span></span> <span data-ttu-id="bf999-344">Dans la fenêtre des résultats, cliquez sur **Modifier les utilisateurs et les groupes locaux**.</span><span class="sxs-lookup"><span data-stu-id="bf999-344">In the Results window, click **Edit local users and groups**.</span></span> <span data-ttu-id="bf999-345">Cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.</span><span class="sxs-lookup"><span data-stu-id="bf999-345">Click **Groups** and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="bf999-346">**Windows 7 SP1** : Cliquez sur Démarrer.</span><span class="sxs-lookup"><span data-stu-id="bf999-346">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="bf999-347">Dans la zone de texte **Rechercher**, tapez **Gestion de l’ordinateur** et cliquez dessus pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="bf999-347">In the **Search** text box, type **Computer Management**, and click it to open.</span></span> <span data-ttu-id="bf999-348">Développez **Utilisateurs et groupes locaux**, cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.</span><span class="sxs-lookup"><span data-stu-id="bf999-348">Expand **Local Users and Groups**, click **Groups**, and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="bf999-349">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-349">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-350">Vous devez être connecté en tant que membre du groupe Administrateurs pour installer et configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-350">You must be a member of the local Administrators group to install and configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
##  <span data-ttu-id="bf999-351"><a name="BKMK_AppLog"></a> Configuration du journal des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="bf999-351"><a name="BKMK_AppLog"></a> Configure the Application Event Log</span></span>  
  
1.  <span data-ttu-id="bf999-352">Cliquez sur **Observateur d’événements** :</span><span class="sxs-lookup"><span data-stu-id="bf999-352">Open **Event Viewer**:</span></span>  
  
     <span data-ttu-id="bf999-353">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Appuyez sur le bouton Windows du clavier et tapez **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="bf999-353">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="bf999-354">Dans la fenêtre des résultats, cliquez sur **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="bf999-354">In the Results window, click **Event Viewer**.</span></span>  
  
     <span data-ttu-id="bf999-355">**Windows 8.1** : Appuyez sur le bouton Windows du clavier et tapez **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="bf999-355">**Windows 8.1**: Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="bf999-356">Dans la fenêtre de recherche, cliquez sur **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="bf999-356">In the Search window, click **Settings**.</span></span> <span data-ttu-id="bf999-357">Dans la fenêtre des résultats, cliquez sur **Afficher les journaux d’événements**.</span><span class="sxs-lookup"><span data-stu-id="bf999-357">In the Results window, click **View event logs**.</span></span>  
  
     <span data-ttu-id="bf999-358">**Windows 7 SP1** : Cliquez sur Démarrer.</span><span class="sxs-lookup"><span data-stu-id="bf999-358">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="bf999-359">Dans la zone de texte **Rechercher**, tapez **Observateur d’événements**, et cliquez dessus pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="bf999-359">In the **Search** text box, type **Event Viewer**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="bf999-360">Développez **Journaux Windows**, cliquez avec le bouton droit sur **Application**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bf999-360">Expand **Windows Logs**, right-click **Application**, and then click **Properties**.</span></span> <span data-ttu-id="bf999-361">Dans **Propriétés du journal** :</span><span class="sxs-lookup"><span data-stu-id="bf999-361">In **Log Properties**:</span></span>  
  
    -   <span data-ttu-id="bf999-362">Pour déterminer l’espace disponible, comparez les propriétés **Taille du journal** et **Taille maximale du journal**.</span><span class="sxs-lookup"><span data-stu-id="bf999-362">To determine the available space, compare the **Log Size** and the **Maximum log size** properties.</span></span>  
  
    -   <span data-ttu-id="bf999-363">Pour fournir plus d’espace, entrez un numéro supérieur dans **Taille maximale du journal**.</span><span class="sxs-lookup"><span data-stu-id="bf999-363">To provide more space, enter a higher number in **Maximum log size**.</span></span>  
  
    -   <span data-ttu-id="bf999-364">Pour activer le remplacement des anciens événements lorsque le journal est plein, sélectionnez **Remplacer les événements si nécessaire**.</span><span class="sxs-lookup"><span data-stu-id="bf999-364">To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.</span></span>  
  
    -   <span data-ttu-id="bf999-365">Pour effacer les événements du journal, sélectionnez **Effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="bf999-365">To clear the log events, select **Clear log**.</span></span>  
  
3.  <span data-ttu-id="bf999-366">Cliquez sur **OK** pour fermer l’**Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="bf999-366">Click **OK** to close the **Event Viewer**.</span></span>  
  
 <span data-ttu-id="bf999-367">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="bf999-367">**Additional**</span></span>  
  
-   <span data-ttu-id="bf999-368">Le programme d’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve un enregistrement des événements dans le journal des événements de l’application.</span><span class="sxs-lookup"><span data-stu-id="bf999-368">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup keeps a record of events in the Application Event Log.</span></span> <span data-ttu-id="bf999-369">Selon les fonctionnalités de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installées, il se peut que la limite d’espace requis dans le journal soit dépassée.</span><span class="sxs-lookup"><span data-stu-id="bf999-369">Depending on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features installed, the amount of space required in the log may exceed its limit.</span></span> <span data-ttu-id="bf999-370">L'installation échoue si le journal des événements de l'application ne dispose plus de suffisamment d'espace lors de l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf999-370">If the application event log runs out of space during [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] setup, the installation fails.</span></span> <span data-ttu-id="bf999-371">Le fait de modifier les paramètres du journal d'événements d'applications permet d'empêcher cet échec.</span><span class="sxs-lookup"><span data-stu-id="bf999-371">Changing the Application Event Log settings prevents this failure.</span></span>  
  
## <a name="next"></a><span data-ttu-id="bf999-372">Suivant</span><span class="sxs-lookup"><span data-stu-id="bf999-372">Next</span></span>  
 [<span data-ttu-id="bf999-373">Choix des fonctionnalités et composants de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bf999-373">Choose BizTalk Server Features and Components</span></span>](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a><span data-ttu-id="bf999-374">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf999-374">See Also</span></span>  
 <span data-ttu-id="bf999-375">[Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span><span class="sxs-lookup"><span data-stu-id="bf999-375">[Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span></span>  
 <span data-ttu-id="bf999-376">[Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md) </span><span class="sxs-lookup"><span data-stu-id="bf999-376">[Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md) </span></span>  
 <span data-ttu-id="bf999-377">[Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="bf999-377">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span></span>  
 <span data-ttu-id="bf999-378">[Annexe C : Fichiers CAB redistribuables](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span><span class="sxs-lookup"><span data-stu-id="bf999-378">[Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span></span>  
 [<span data-ttu-id="bf999-379">Annexe D : Création du serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="bf999-379">Appendix D: Create the SMTP Server</span></span>](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
