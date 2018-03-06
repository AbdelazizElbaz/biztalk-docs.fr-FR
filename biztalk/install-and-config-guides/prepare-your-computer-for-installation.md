---
title: "Préparer votre ordinateur pour l’Installation | Documents Microsoft"
ms.custom: 
ms.date: 03/15/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53df7a2f-638b-4921-a97f-736760248526
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c2e732073ccc787cad32984720d7fac422a8cb
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="prepare-your-computer-for-installation"></a><span data-ttu-id="14c08-102">Préparation de votre ordinateur pour l'installation</span><span class="sxs-lookup"><span data-stu-id="14c08-102">Prepare Your Computer for Installation</span></span>
<span data-ttu-id="14c08-103">Cette rubrique présente les étapes nécessaires pour préparer votre ordinateur en installant et en configurant tous les composants logiciels requis, puis en créant des comptes et en définissant les autorisations.</span><span class="sxs-lookup"><span data-stu-id="14c08-103">This topic lists the steps to prepare your computer by installing and configuring all software prerequisites, and then creating accounts and setting permissions.</span></span>  

> [!TIP] 
> <span data-ttu-id="14c08-104">Un MVP d’intégration a préparé un guide pas à pas très détaillé pour installer les prérequis et BizTalk Server : [Installation et configuration de BizTalk 2013, partie 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).</span><span class="sxs-lookup"><span data-stu-id="14c08-104">An integration MVP prepared a very detailed step-by-step guide to install the prerequisites, and BizTalk Server:  [BizTalk 2013 Installation and Configuration part 1](http://sandroaspbiztalkblog.wordpress.com/2013/05/05/biztalk-2013-installation-and-configuration-important-considerations-before-set-up-the-server-part-1/).</span></span>  
> 
> <span data-ttu-id="14c08-105">Certaines étapes ne sont pas recommandées par Microsoft, telles que la désactivation du contrôle d’accès d’utilisateur ou du Pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="14c08-105">Some steps are not recommended by Microsoft, such as disabling User Access Control (UAC) or Windows Firewall.</span></span> 
  
> [!IMPORTANT]
>  <span data-ttu-id="14c08-106">Effectuez ces tâches dans l’ordre indiqué.</span><span class="sxs-lookup"><span data-stu-id="14c08-106">Complete these tasks in the order listed.</span></span>  
  
##  <a name="BKMK_InstUpdates"></a> <span data-ttu-id="14c08-107">Installation des mises à jour Windows</span><span class="sxs-lookup"><span data-stu-id="14c08-107">Install Windows Updates</span></span>  
  
-   <span data-ttu-id="14c08-108">**Windows 7** : Cliquez sur Démarrer.</span><span class="sxs-lookup"><span data-stu-id="14c08-108">**Windows 7**: Click Start.</span></span> <span data-ttu-id="14c08-109">Dans la zone de texte **Rechercher**, tapez **Windows Update**.</span><span class="sxs-lookup"><span data-stu-id="14c08-109">In the **Search** text box, type **Windows Update**.</span></span>  
  
-   <span data-ttu-id="14c08-110">**Windows 8.1, Windows Server 2012 et Windows Server 2012 R2**: cliquez sur le bouton Windows du clavier et tapez **mise à jour Windows**.</span><span class="sxs-lookup"><span data-stu-id="14c08-110">**Windows 8.1, Windows Server 2012, and Windows Server 2012 R2**: Click the Windows button on the keyboard and type **Windows Update**.</span></span> <span data-ttu-id="14c08-111">À partir des résultats de la recherche, cliquez sur **Windows Update**.</span><span class="sxs-lookup"><span data-stu-id="14c08-111">From the search results, click **Windows Update**.</span></span>  
  
 <span data-ttu-id="14c08-112">Après avoir installé les mises à jour, vous devrez peut-être redémarrer l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14c08-112">After installing updates, you may need to restart the computer.</span></span>  
  
##  <a name="BKMK_IIS"></a> <span data-ttu-id="14c08-113">Activation d’Internet Information Services</span><span class="sxs-lookup"><span data-stu-id="14c08-113">Enable Internet Information Services</span></span>  
 <span data-ttu-id="14c08-114">Microsoft Internet Information Services (IIS) fournit une infrastructure d’application Web pour de nombreuses fonctionnalités de BizTalk Server, y compris :</span><span class="sxs-lookup"><span data-stu-id="14c08-114">Microsoft Internet Information Services (IIS) provides a Web application infrastructure for many BizTalk Server features, including:</span></span>  
  
-   <span data-ttu-id="14c08-115">adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="14c08-115">HTTP adapter</span></span>  
  
-   <span data-ttu-id="14c08-116">adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="14c08-116">SOAP adapter</span></span>  
  
-   <span data-ttu-id="14c08-117">Adaptateur Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="14c08-117">Windows SharePoint Services adapter</span></span>  
  
-   <span data-ttu-id="14c08-118">Chiffrement SSL (Secure Sockets Layer)</span><span class="sxs-lookup"><span data-stu-id="14c08-118">Secure Sockets Layer (SSL) encryption</span></span>  
  
-   <span data-ttu-id="14c08-119">Portail BAM</span><span class="sxs-lookup"><span data-stu-id="14c08-119">BAM Portal</span></span>  
  
#### <a name="install-iis"></a><span data-ttu-id="14c08-120">Installer IIS</span><span class="sxs-lookup"><span data-stu-id="14c08-120">Install IIS</span></span>

<span data-ttu-id="14c08-121">Étapes d’installation spécifique, consultez :</span><span class="sxs-lookup"><span data-stu-id="14c08-121">For the specific install steps, see:</span></span> 

[<span data-ttu-id="14c08-122">Installer les services IIS (Windows 8 et Windows Server 2012)</span><span class="sxs-lookup"><span data-stu-id="14c08-122">Install IIS (Windows 8 and Windows Server 2012)</span></span>](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/installing-iis-8-on-windows-server-2012)

[<span data-ttu-id="14c08-123">Installer les services IIS (Windows 7 et Windows Vista)</span><span class="sxs-lookup"><span data-stu-id="14c08-123">Install IIS (Windows 7 and Windows Vista)</span></span>](https://docs.microsoft.com/iis/install/installing-iis-7/installing-iis-on-windows-vista-and-windows-7)


<span data-ttu-id="14c08-124">Lorsque vous installez IIS, en plus des options par défaut activée, vérifiez également les points suivants :</span><span class="sxs-lookup"><span data-stu-id="14c08-124">When you install IIS, in addition to the default checked options, also check the following:</span></span>  
  
- <span data-ttu-id="14c08-125">**Outils d’administration Web** : Cochez également :</span><span class="sxs-lookup"><span data-stu-id="14c08-125">**Web Management Tools**: Also check:</span></span>  
  
    - <span data-ttu-id="14c08-126">Compatibilité avec la gestion IIS 6 :</span><span class="sxs-lookup"><span data-stu-id="14c08-126">IIS 6 Management Compatibility:</span></span>  
  
        - <span data-ttu-id="14c08-127">Console de gestion IIS 6</span><span class="sxs-lookup"><span data-stu-id="14c08-127">IIS 6 Management Console</span></span>  
  
        - <span data-ttu-id="14c08-128">Compatibilité avec la métabase IIS et la configuration IIS 6</span><span class="sxs-lookup"><span data-stu-id="14c08-128">IIS Metabase and IIS 6 configuration compatibility</span></span>  
  
    - <span data-ttu-id="14c08-129">Console de gestion IIS</span><span class="sxs-lookup"><span data-stu-id="14c08-129">IIS Management Console</span></span>  
  
- <span data-ttu-id="14c08-130">**Services World Wide Web** : Développez **Sécurité** et sélectionnez également :</span><span class="sxs-lookup"><span data-stu-id="14c08-130">**World Wide Web Services**: Expand **Security** and also select:</span></span>  
  
    - <span data-ttu-id="14c08-131">Authentification de base</span><span class="sxs-lookup"><span data-stu-id="14c08-131">Basic Authentication</span></span>  
  
    - <span data-ttu-id="14c08-132">Authentification Windows</span><span class="sxs-lookup"><span data-stu-id="14c08-132">Windows Authentication</span></span>  

<span data-ttu-id="14c08-133">Prenez également en considération les points suivants :</span><span class="sxs-lookup"><span data-stu-id="14c08-133">Also consider the following:</span></span>  
  
- <span data-ttu-id="14c08-134">**Fonctionnalités .net framework 3.5**: .NET Framework 4.5 et .NET Framework 3.5 peuvent être utilisé pour développer des applications .net impliquant BizTalk Adapter Pack.</span><span class="sxs-lookup"><span data-stu-id="14c08-134">**.Net Framework 3.5 Features**: .NET Framework 4.5 and .NET Framework 3.5 can be used to develop .Net applications involving the BizTalk Adapter Pack.</span></span> <span data-ttu-id="14c08-135">En règle générale, **fonctionnalités .NET Framework 4.5** est déjà installé.</span><span class="sxs-lookup"><span data-stu-id="14c08-135">Typically, **.NET Framework 4.5 Features** is already installed.</span></span> <span data-ttu-id="14c08-136">Si vous utilisez .NET Framework 3.5 pour créer des applications sur cet ordinateur, puis **fonctionnalités .net Framework 3.5** peut également être installé.</span><span class="sxs-lookup"><span data-stu-id="14c08-136">If you will use .NET Framework 3.5 to create applications on this computer, then **.Net Framework 3.5 Features** can also be installed.</span></span>  
  
- <span data-ttu-id="14c08-137">**Message Queuing** : Si vous utilisez l’adaptateur MSMQ, vous pouvez créer un magasin MSMQ local en cochant **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="14c08-137">**Message Queuing**: If you are using the MSMQ adapter, you can create a local MSMQ store by checking **Message Queuing**.</span></span>  
  
- <span data-ttu-id="14c08-138">**Serveur SMTP** : Si vous utilisez l’adaptateur SMTP, vous pouvez créer un serveur SMTP local en cochant **Serveur SMTP**.</span><span class="sxs-lookup"><span data-stu-id="14c08-138">**SMTP Server**: If you are using the SMTP adapter, you can create a local SMTP Server by checking **SMTP Server**.</span></span>  
  
- <span data-ttu-id="14c08-139">**Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) est requis par l’adaptateur SharePoint lors de l’utilisation de l’option d’installation CSOM.</span><span class="sxs-lookup"><span data-stu-id="14c08-139">**Windows Identity Foundation 3.5**: Windows Identity Foundation (WIF) is required by the SharePoint adapter when using the CSOM installation option.</span></span> <span data-ttu-id="14c08-140">[Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit l’option d’installation CSOM pour l’adaptateur SharePoint.</span><span class="sxs-lookup"><span data-stu-id="14c08-140">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the CSOM installation option for the SharePoint adapter.</span></span>    
  
 
##  <a name="BKMK_XLS"></a> <span data-ttu-id="14c08-141">Installation de Microsoft Office Excel</span><span class="sxs-lookup"><span data-stu-id="14c08-141">Install Microsoft Office Excel</span></span>  
  
1.  <span data-ttu-id="14c08-142">Exécutez le programme d'installation de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="14c08-142">Run the Microsoft Office setup.</span></span>  
  
2.  <span data-ttu-id="14c08-143">Dans la page **Type d’installation**, sélectionnez **Installation personnalisée**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="14c08-143">When you reach the **Type of Installation** screen, select **Custom Install**, and then select **Next**.</span></span>  
  
3.  <span data-ttu-id="14c08-144">Dans la page **Installation personnalisée**, sélectionnez **Excel**, puis **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="14c08-144">On the **Custom Setup** screen, select **Excel**, and then select **Next**.</span></span>  
  
4.  <span data-ttu-id="14c08-145">Sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="14c08-145">Select **Install**.</span></span>  
  
5.  <span data-ttu-id="14c08-146">Dans **Fin de l’installation**, sélectionnez **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="14c08-146">In **Setup Completed**, select **Finish**.</span></span>  
  
 <span data-ttu-id="14c08-147">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-147">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-148">BizTalk Server prend en charge uniquement la version 32 bits de Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="14c08-148">BizTalk Server supports only 32-bit version of Microsoft Office.</span></span>  
  
-   <span data-ttu-id="14c08-149">Microsoft Office Excel est requis par analyse BAM (Business Activity) dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-149">Microsoft Office Excel is required by Business Activity Monitoring (BAM) in BizTalk Server.</span></span> <span data-ttu-id="14c08-150">Le classeur BAM Office Excel définit les processus d'entreprise que vous souhaitez analyser.</span><span class="sxs-lookup"><span data-stu-id="14c08-150">The BAM Office Excel Workbook defines the business processes you want to monitor.</span></span> <span data-ttu-id="14c08-151">Vous utilisez également le classeur Excel BAM pour définir la manière dont les utilisateurs des activités visualisent les données collectées par l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="14c08-151">You also use the BAM Excel Workbook to define the way business users see the data collected by BAM.</span></span>  
  
-   <span data-ttu-id="14c08-152">Pour charger correctement le fichier BAM.xla dans Excel, installez **Visual Basic pour Applications** sous **Composants partagés d’Office**.</span><span class="sxs-lookup"><span data-stu-id="14c08-152">To successfully load BAM.xla into Excel, install **Visual Basic for Applications** under **Office Shared Features**.</span></span> <span data-ttu-id="14c08-153">Dans le cas contraire, vous risquez de recevoir l’erreur « Ce classeur a perdu son projet VBA, ses contrôles ActiveX et d’autres fonctionnalités liées à la programmabilité ».</span><span class="sxs-lookup"><span data-stu-id="14c08-153">Otherwise, you may get error “This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.”</span></span>  
  
##  <a name="BKMK_VS"></a> <span data-ttu-id="14c08-154">Installation de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="14c08-154">Install Visual Studio</span></span>  
  
1.  <span data-ttu-id="14c08-155">Exécutez l'installation de Visual Studio en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="14c08-155">Run the Visual Studio setup as Administrator.</span></span>  
  
2.  <span data-ttu-id="14c08-156">Acceptez le contrat de licence et cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="14c08-156">Accept the license agreement and click **Next**.</span></span>  
  
3.  <span data-ttu-id="14c08-157">Dans **Fonctionnalités facultatives à installer**, sélectionnez les options dont vous avez besoin, puis sélectionnez **Installer**.</span><span class="sxs-lookup"><span data-stu-id="14c08-157">In **Optional features to install**, select the options you need and then select **Install**.</span></span> <span data-ttu-id="14c08-158">BizTalk Server ne nécessite aucune des fonctionnalités facultatives.</span><span class="sxs-lookup"><span data-stu-id="14c08-158">BizTalk Server does not require any of the optional features.</span></span>  
  
4.  <span data-ttu-id="14c08-159">Dans la page **Terminer**, fermez la fenêtre ou cliquez sur **Lancer** pour ouvrir Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14c08-159">On the **Finish** page, close the window or click **Launch** to open Visual Studio.</span></span>  
  
 <span data-ttu-id="14c08-160">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-160">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-161">Si vous installez Visual Studio avant d’installer BizTalk Server, puis mettre à niveau vers Visual Studio Team Explorer, vous devrez peut-être réparer votre installation de BizTalk Server à partir de la **le panneau de configuration** / **programmes**  option.</span><span class="sxs-lookup"><span data-stu-id="14c08-161">If you install Visual Studio before installing BizTalk Server, and then upgrade to Visual Studio Team Explorer, you may need to repair your BizTalk Server installation from the **Control Panel** / **Programs** option.</span></span>  
  
-   <span data-ttu-id="14c08-162">Visual Studio installe automatiquement Microsoft SQL Server Express, qui n’est pas utilisé par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-162">Visual Studio automatically installs Microsoft SQL Server Express; which is not used by BizTalk Server.</span></span> <span data-ttu-id="14c08-163">La bonne pratique est de désinstaller Microsoft SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="14c08-163">As a best practice, uninstall Microsoft SQL Server Express.</span></span>  
  
-   <span data-ttu-id="14c08-164">Les outils de développement de BizTalk Server sont basés sur Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="14c08-164">The BizTalk Server development tools are based on Visual Studio.</span></span> <span data-ttu-id="14c08-165">Au minimum, vous devez installer le composant de Microsoft Visual c#® .NET de Visual Studio avant d’installer BizTalk Server**outils de développement et Kit de développement logiciel**.</span><span class="sxs-lookup"><span data-stu-id="14c08-165">At a minimum, you must install the Microsoft Visual C#® .NET component of Visual Studio before you install the BizTalk Server**Developer Tools and SDK**.</span></span>  
  
-   <span data-ttu-id="14c08-166">Visual Studio est *pas* nécessaire si vous installez BizTalk Server sur un ordinateur de production (exécution uniquement), sur lequel aucune application développement ou débogage n’est requis.</span><span class="sxs-lookup"><span data-stu-id="14c08-166">Visual Studio is *not* required if you are installing BizTalk Server on a production computer (runtime only), on which no application development or debugging is required.</span></span>  
  
-   <span data-ttu-id="14c08-167">L’exécution de BizTalk Server requiert .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="14c08-167">The BizTalk Server runtime requires .NET Framework 4.5.</span></span> <span data-ttu-id="14c08-168">.NET Framework 3.0 est indispensable si l’adaptateur ou l’intercepteur WCF (Windows Communication Foundation) est installé.</span><span class="sxs-lookup"><span data-stu-id="14c08-168">The .NET Framework 3.0 is required if the Windows Communication Foundation (WCF) adapter or WCF Interceptor is installed.</span></span>  
  
##  <a name="BKMK_SQL"></a> <span data-ttu-id="14c08-169">Installation de SQL Server</span><span class="sxs-lookup"><span data-stu-id="14c08-169">Install SQL Server</span></span>  
 <span data-ttu-id="14c08-170">Installation de [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-170">Install [SQL Server 2008 R2](http://msdn.microsoft.com/library/bb500395\(v=sql.105\).aspx)</span></span>  
  
 <span data-ttu-id="14c08-171">Installation de [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-171">Install [SQL Server 2012](http://msdn.microsoft.com/library/bb500469\(v=sql.110\).aspx)</span></span>  
  
 <span data-ttu-id="14c08-172">Installation de [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-172">Install [SQL Server 2014](http://msdn.microsoft.com/library/bb500469\(v=sql.120\).aspx)</span></span>  
  
 <span data-ttu-id="14c08-173">Lorsque vous installez SQL Server, sélectionnez les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="14c08-173">When you install SQL Server, select the following features:</span></span>  
  
-   <span data-ttu-id="14c08-174">Services Moteur de base de données</span><span class="sxs-lookup"><span data-stu-id="14c08-174">Database Engine Services</span></span>  
  
    -   <span data-ttu-id="14c08-175">Réplication SQL Server</span><span class="sxs-lookup"><span data-stu-id="14c08-175">SQL Server Replication</span></span>  
  
    -   <span data-ttu-id="14c08-176">Recherche en texte intégral</span><span class="sxs-lookup"><span data-stu-id="14c08-176">Full-Text Search</span></span>  
  
-   <span data-ttu-id="14c08-177">Analysis Services</span><span class="sxs-lookup"><span data-stu-id="14c08-177">Analysis Services</span></span>  
  
-   <span data-ttu-id="14c08-178">Reporting Services</span><span class="sxs-lookup"><span data-stu-id="14c08-178">Reporting Services</span></span>  
  
-   <span data-ttu-id="14c08-179">Fonctionnalités partagées</span><span class="sxs-lookup"><span data-stu-id="14c08-179">Shared Features</span></span>  
  
    -   <span data-ttu-id="14c08-180">SQL Server Data Tools (SQL Server 2014/SQL Server 2012) ou Business Intelligence Development Studio (SQL Server 2008 R2)</span><span class="sxs-lookup"><span data-stu-id="14c08-180">SQL Server Data Tools (SQL Server 2014 / SQL Server 2012) or Business Intelligence Development Studio (SQL Server 2008 R2)</span></span>  
  
         [<span data-ttu-id="14c08-181">Téléchargez SQL Server 2014 Data Tools</span><span class="sxs-lookup"><span data-stu-id="14c08-181">Download SQL Server 2014 Data Tools</span></span>](http://www.microsoft.com/download/details.aspx?id=42313)  
  
    -   <span data-ttu-id="14c08-182">Connectivité des outils clients</span><span class="sxs-lookup"><span data-stu-id="14c08-182">Client Tools Connectivity</span></span>  
  
    -   <span data-ttu-id="14c08-183">Integration Services</span><span class="sxs-lookup"><span data-stu-id="14c08-183">Integration Services</span></span>  
  
    -   <span data-ttu-id="14c08-184">Outils de gestion - Base</span><span class="sxs-lookup"><span data-stu-id="14c08-184">Management Tools - Basic</span></span>  
  
        -   <span data-ttu-id="14c08-185">Outils de gestion - Complet</span><span class="sxs-lookup"><span data-stu-id="14c08-185">Management Tools - Complete</span></span>  
  
 <span data-ttu-id="14c08-186">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-186">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-187">BizTalk Server prend en charge tous les classements SQL Server qui respectent la casse et qui ne la respectent pas, à l’exception des classements binaires.</span><span class="sxs-lookup"><span data-stu-id="14c08-187">BizTalk Server supports all case-sensitive and case-insensitive SQL Server collations except for binary collations.</span></span> <span data-ttu-id="14c08-188">Les classements binaires ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="14c08-188">Binary collations are not supported.</span></span>  
  
-   <span data-ttu-id="14c08-189">Pour des performances optimales, Microsoft recommande d’utiliser SQL Server Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="14c08-189">For optimal performance, Microsoft recommends using the Enterprise Edition of SQL Server.</span></span> <span data-ttu-id="14c08-190">Consultez les [éditions SQL Server 2008 R2](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), les [éditions SQL Server 2012](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx) ou les [éditions SQL Server 2014](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).</span><span class="sxs-lookup"><span data-stu-id="14c08-190">See [SQL Server 2008 R2 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.105\).aspx), [SQL Server 2012 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.110\).aspx), or [SQL Server 2014 Editions](http://msdn.microsoft.com/library/cc645993\(v=sql.120\).aspx).</span></span>  
  
-   <span data-ttu-id="14c08-191">Les Service Packs et mises à jour Windows sont pris en charge et doivent être installés.</span><span class="sxs-lookup"><span data-stu-id="14c08-191">Service packs and Windows Updates are supported and should be installed.</span></span>  
  
-   <span data-ttu-id="14c08-192">Lorsque BizTalk Server et SQL Server se trouvent sur des ordinateurs distincts, Distributed Transaction Coordinator (MS DTC) gère les transactions entre les ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="14c08-192">When BizTalk Server and SQL Server are on separate computers, Distributed Transaction Coordinator (MS DTC) handles the transactions between the computers.</span></span> <span data-ttu-id="14c08-193">La fonctionnalité AlwaysOn de SQL Server ne prend pas en charge les transactions MSDTC.</span><span class="sxs-lookup"><span data-stu-id="14c08-193">The SQL Server AlwaysOn feature does not support MSDTC transactions.</span></span> <span data-ttu-id="14c08-194">La fonctionnalité AlwaysOn de SQL Server n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="14c08-194">The SQL Server AlwaysOn feature is not supported.</span></span>  
  
##  <a name="BKMK_MQSeries"></a> <span data-ttu-id="14c08-195">Installation des composants requis pour MQSeries</span><span class="sxs-lookup"><span data-stu-id="14c08-195">Install MQSeries Prerequisites</span></span>  
 <span data-ttu-id="14c08-196">**Adaptateur MQSeries** : Installé automatiquement avec l’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-196">**MQSeries adapter**: Automatically installed with the BizTalk Server installation.</span></span>  
  
 <span data-ttu-id="14c08-197">**Adaptateur MQSeries Client (MQSC)** :</span><span class="sxs-lookup"><span data-stu-id="14c08-197">**MQSeries Client (MQSC) adapter**:</span></span>  
  
1.  <span data-ttu-id="14c08-198">Exécuter l'installation de HIS (Host Integration Server)</span><span class="sxs-lookup"><span data-stu-id="14c08-198">Run the Host Integration Server (HIS) installation</span></span>  
  
2.  <span data-ttu-id="14c08-199">Dans l’installation des composants, développez **Adaptateurs BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="14c08-199">In component installation, expand **BizTalk Adapters**.</span></span>  
  
3.  <span data-ttu-id="14c08-200">Sélectionnez **Adaptateur BizTalk pour WebSphere MQ (basé sur le client)**.</span><span class="sxs-lookup"><span data-stu-id="14c08-200">Select **BizTalk Adapter for WebSphere MQ (Client-Based)**.</span></span>  
  
 <span data-ttu-id="14c08-201">**Versions prises en charge d’IBM WebSphere MQ** :</span><span class="sxs-lookup"><span data-stu-id="14c08-201">**Supported IBM WebSphere MQ versions**:</span></span>  
  
-   <span data-ttu-id="14c08-202">IBM WebSphere MQ 6.0.2.12 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="14c08-202">IBM WebSphere MQ 6.0.2.12 and later</span></span>  
  
-   <span data-ttu-id="14c08-203">IBM WebSphere MQ 7.0.1.9 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="14c08-203">IBM WebSphere MQ 7.0.1.9 and later</span></span>  
  
-   <span data-ttu-id="14c08-204">IBM WebSphere MQ 7.1.0.5 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="14c08-204">IBM WebSphere MQ 7.1.0.5 and later</span></span>  
  
-   <span data-ttu-id="14c08-205">IBM WebSphere MQ 7.5.0.3 et versions ultérieures</span><span class="sxs-lookup"><span data-stu-id="14c08-205">IBM WebSphere MQ 7.5.0.3 and later</span></span>  
  
-   <span data-ttu-id="14c08-206">IBM WebSphere MQ 8 (limité à l’exécution, aucune API d’administration)</span><span class="sxs-lookup"><span data-stu-id="14c08-206">IBM WebSphere MQ 8 (limited to runtime; no administration APIs)</span></span>  
  
     <span data-ttu-id="14c08-207">La prise en charge de MQ version 8 est incluse avec [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).</span><span class="sxs-lookup"><span data-stu-id="14c08-207">MQ version 8 support is included with [Host Integration Server CU3](https://support.microsoft.com/kb/3019572).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14c08-208">Si une version WebSphere MQ spécifique n’est pas répertoriée, comme MQ 5.x, puis il n'est pas pris en charge avec cette version de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-208">If a specific WebSphere MQ version is not listed, like MQ 5.x, then it is not supported with this BizTalk Server version.</span></span>  
  
 <span data-ttu-id="14c08-209">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-209">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-210">Il est recommandé de toujours installer le dernier pack de correctifs WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="14c08-210">As a best practice, always install the latest WebSphere MQ fix pack.</span></span> <span data-ttu-id="14c08-211">Consultez [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).</span><span class="sxs-lookup"><span data-stu-id="14c08-211">See [http://www.ibm.com/support/docview.wss?uid=swg27006037](http://www.ibm.com/support/docview.wss?uid=swg27006037).</span></span>  
  
-   <span data-ttu-id="14c08-212">Si IBM WebSphere MQ est installé sur un ordinateur non-Windows, installez l’**application MQSAgent COM+** (MQSConfigWiz.exe) et **MQSeries Server for Windows** sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="14c08-212">If IBM WebSphere MQ is installed on a non-Windows computer, install the **MQSAgent COM+ application** (MQSConfigWiz.exe) and **MQSeries Server for Windows** on the same computer.</span></span> <span data-ttu-id="14c08-213">Si IBM WebSphere MQ est installé sur un ordinateur Windows, l’**application MQSAgent COM+** et le programme **MQSeries Server for Windows** ne sont ni utilisés ni nécessaires.</span><span class="sxs-lookup"><span data-stu-id="14c08-213">If IBM WebSphere MQ is installed on a Windows computer, then the **MQSAgent COM+ application** and **MQSeries Server for Windows** program are not used or needed.</span></span>  
  
     <span data-ttu-id="14c08-214">**MQSConfigWiz.exe** est inclus dans les fichiers d’installation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-214">**MQSConfigWiz.exe** is included in the BizTalk Server installation files.</span></span>  
  
     <span data-ttu-id="14c08-215">**MQSeries Server pour Windows** n’est pas un programme Microsoft et doit être obtenu avec votre programme IBM WebSphere MQ.</span><span class="sxs-lookup"><span data-stu-id="14c08-215">**MQSeries Server for Windows** is not a Microsoft program and must be obtained with your IBM WebSphere MQ program.</span></span>  
  
-   <span data-ttu-id="14c08-216">L’article [Adaptateur MQSeries](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) fournit plus d’informations sur l’adaptateur MQSeries, y compris la configuration des différents composants.</span><span class="sxs-lookup"><span data-stu-id="14c08-216">[MQSeries Adapter](http://technet.microsoft.com/library/aa547973\(v=BTS.80\).aspx) provides more information on the MQSeries adapter, including configuring the different components.</span></span> <span data-ttu-id="14c08-217">La page [BizTalk Server : Adaptateurs MQSeries et MQSeries Client (MQSC)](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) fournit des détails supplémentaires sur les adaptateurs MQSeries et MQSC.</span><span class="sxs-lookup"><span data-stu-id="14c08-217">[BizTalk Server: MQSeries and MQSeries Client (MQSC) adapters](http://social.technet.microsoft.com/wiki/contents/articles/18316.biztalk-server-mqseries-and-mqseries-client-mqsc-adapters.aspx) provides additional details on the MQSeries and MQSC adapters.</span></span>  
  
-   <span data-ttu-id="14c08-218">IBM WebSphere n'est pas un produit Microsoft et n'est pas pris en charge par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="14c08-218">IBM WebSphere is not a Microsoft product and is not supported by Microsoft.</span></span> <span data-ttu-id="14c08-219">Microsoft ne donne aucune garantie quant à la pertinence de ce programme.</span><span class="sxs-lookup"><span data-stu-id="14c08-219">Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="14c08-220">Pour plus d'informations sur IBM WebSphere MQ, y compris les instructions de téléchargement, consultez www.ibm.com.</span><span class="sxs-lookup"><span data-stu-id="14c08-220">For more information about IBM WebSphere MQ, including download instructions, see www.ibm.com.</span></span>  
  
##  <a name="BKMK_BAMAlerts"></a> <span data-ttu-id="14c08-221">Alertes BAM</span><span class="sxs-lookup"><span data-stu-id="14c08-221">BAM Alerts</span></span>  
 <span data-ttu-id="14c08-222">Alertes BAM avec SQL Server 2012 et les versions plus récentes utilisent la messagerie de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-222">BAM Alerts with SQL Server 2012 and newer versions use Database Mail in SQL Server.</span></span> <span data-ttu-id="14c08-223">Alertes BAM avec SQL Server 2008 R2 et versions antérieures utilisent les Services de Notification SQL.</span><span class="sxs-lookup"><span data-stu-id="14c08-223">BAM Alerts with SQL Server 2008 R2 and older versions use SQL Notification Services.</span></span> <span data-ttu-id="14c08-224">Avant d’installer ou de configurer des alertes BAM, vous devez configurer les Services de Notification ou messagerie de base de données dans SQL Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-224">Before installing or configuring BAM Alerts, you must configure the Notification Services or Database Mail in SQL Server.</span></span>  
  
###  <a name="BKMK_DBMail"></a> <span data-ttu-id="14c08-225">Alertes BAM utilisant SQL Server 2012/2014</span><span class="sxs-lookup"><span data-stu-id="14c08-225">BAM Alerts using SQL Server 2012/2014</span></span>  
 <span data-ttu-id="14c08-226">Configurez la [messagerie de base de données SQL Server 2012](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).</span><span class="sxs-lookup"><span data-stu-id="14c08-226">Configure [SQL Server 2012 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.110\).aspx).</span></span>  
  
 <span data-ttu-id="14c08-227">Configurez la [messagerie de base de données SQL Server 2014](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).</span><span class="sxs-lookup"><span data-stu-id="14c08-227">Configure [SQL Server 2014 Database Mail](http://msdn.microsoft.com/library/hh245116\(v=sql.120\).aspx).</span></span>  
  
 <span data-ttu-id="14c08-228">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-228">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-229">La fonctionnalité Messagerie de base de données utilise un serveur SMTP pour envoyer les alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="14c08-229">Database Mail uses an SMTP server to send the BAM Alerts.</span></span> <span data-ttu-id="14c08-230">Serveur SMTP peut être installé localement sur le serveur BizTalk Server ou sur un autre serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="14c08-230">SMTP Server can be installed locally on the BizTalk Server or on another IIS server.</span></span> <span data-ttu-id="14c08-231">L’[annexe D : Création du serveur SMTP](../install-and-config-guides/appendix-d-create-the-smtp-server.md) répertorie les étapes de l’installation et de la configuration d’un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="14c08-231">[Appendix D: Create the SMTP Server](../install-and-config-guides/appendix-d-create-the-smtp-server.md) lists the steps to install and configure a SMTP Server.</span></span>  
  
###  <a name="BKMK_SSNS"></a> <span data-ttu-id="14c08-232">Alertes BAM utilisant SQL Server 2008 R2 – Installation de SQL Server 2005 Notification Services</span><span class="sxs-lookup"><span data-stu-id="14c08-232">BAM Alerts using SQL Server 2008 R2 – Install SQL Server 2005 Notification Services</span></span>  
  
1.  <span data-ttu-id="14c08-233">Consultez [Feature Pack pour Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).</span><span class="sxs-lookup"><span data-stu-id="14c08-233">Go to [Feature Pack for Microsoft SQL Server 2005 SP4](http://go.microsoft.com/fwlink/p/?LinkId=286285).</span></span>  
  
2.  <span data-ttu-id="14c08-234">Téléchargez et installez le package de plate-forme approprié pour les composants suivants :</span><span class="sxs-lookup"><span data-stu-id="14c08-234">Download and install the appropriate platform package for the following components:</span></span>  
  
     <span data-ttu-id="14c08-235">**Microsoft SQL Server Native Client**</span><span class="sxs-lookup"><span data-stu-id="14c08-235">**Microsoft SQL Server Native Client**</span></span>  
  
    -   <span data-ttu-id="14c08-236">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" Package X86 (sqlncli.msi)</span><span class="sxs-lookup"><span data-stu-id="14c08-236">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli.msi" X86 Package (sqlncli.msi)</span></span>  
  
    -   <span data-ttu-id="14c08-237">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" Package X64 (sqlncli_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="14c08-237">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/sqlncli_x64.msi" X64 Package (sqlncli_x64.msi)</span></span>  
  
     <span data-ttu-id="14c08-238">**Collection d’objets de gestion de Microsoft SQL Server 2005**</span><span class="sxs-lookup"><span data-stu-id="14c08-238">**Microsoft SQL Server 2005 Management Objects Collection**</span></span>  
  
    -   <span data-ttu-id="14c08-239">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" Package X86 (SQLServer2005_XMO.msi)</span><span class="sxs-lookup"><span data-stu-id="14c08-239">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO.msi" X86 Package (SQLServer2005_XMO.msi)</span></span>  
  
    -   <span data-ttu-id="14c08-240">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" Package X64 (SQLServer2005_XMO_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="14c08-240">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_XMO_x64.msi" X64 Package (SQLServer2005_XMO_x64.msi)</span></span>  
  
     <span data-ttu-id="14c08-241">**Composants clients Notification Services de Microsoft SQL Server 2005**</span><span class="sxs-lookup"><span data-stu-id="14c08-241">**Microsoft SQL Server 2005 Notification Services Client Components**</span></span>  
  
    -   <span data-ttu-id="14c08-242">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" Package X86 (SQLServer2005_NS.msi)</span><span class="sxs-lookup"><span data-stu-id="14c08-242">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS.msi" X86 Package (SQLServer2005_NS.msi)</span></span>  
  
    -   <span data-ttu-id="14c08-243">LIEN HYPERTEXTE "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" Package X64 (SQLServer2005_NS_x64.msi)</span><span class="sxs-lookup"><span data-stu-id="14c08-243">HYPERLINK "http://download.microsoft.com/download/3/1/6/316FADB2-E703-4351-8E9C-E0B36D9D697E/SQLServer2005_NS_x64.msi" X64 Package (SQLServer2005_NS_x64.msi)</span></span>  
  
 <span data-ttu-id="14c08-244">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-244">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-245">Services de Notification SQL doit-elle pas être configurée ; installé uniquement sur le serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-245">SQL Notification Services does not need to be configured; only installed on the BizTalk Server.</span></span>  
  
##  <a name="BKMK_WIF"></a> <span data-ttu-id="14c08-246">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="14c08-246">Windows Identity Foundation</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14c08-247">Windows 8.1, Windows Server 2012 et Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="14c08-247">Windows 8.1, Windows Server 2012, and Windows Server 2012 R2</span></span>|<span data-ttu-id="14c08-248">Windows Identity Foundation est inclus dans le système d’exploitation comme fonctionnalité dans **Activer ou désactiver des fonctionnalités Windows**.</span><span class="sxs-lookup"><span data-stu-id="14c08-248">Windows Identity Foundation is included with the operating system as a Feature in **Turn Windows features on or off**.</span></span>|  
|<span data-ttu-id="14c08-249">Windows Vista SP1</span><span class="sxs-lookup"><span data-stu-id="14c08-249">Windows Vista SP1</span></span>|<span data-ttu-id="14c08-250">Téléchargement disponible sur la page [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) LIEN HYPERTEXTE "http://www.microsoft.com/download/details.aspx?id=17331".</span><span class="sxs-lookup"><span data-stu-id="14c08-250">Download available at [Windows Identity Foundation](http://www.microsoft.com/download/details.aspx?id=17331) HYPERLINK "http://www.microsoft.com/download/details.aspx?id=17331" .</span></span>|  
  
 <span data-ttu-id="14c08-251">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-251">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-252">Windows Identity Foundation (WIF) est requis pour l’adaptateur SharePoint ou SharePoint Online lorsqu’il est utilisé avec SharePoint objet modèle CSOM (Client Side).</span><span class="sxs-lookup"><span data-stu-id="14c08-252">Windows Identity Foundation (WIF) is required for the SharePoint adapter or SharePoint Online when used with SharePoint Client Side Object Model (CSOM).</span></span> <span data-ttu-id="14c08-253">Plus précisément :</span><span class="sxs-lookup"><span data-stu-id="14c08-253">Specifically:</span></span>  
  
    |<span data-ttu-id="14c08-254">Option d’installation</span><span class="sxs-lookup"><span data-stu-id="14c08-254">Installation Option</span></span>|<span data-ttu-id="14c08-255">WIF requis</span><span class="sxs-lookup"><span data-stu-id="14c08-255">WIF Required</span></span>|  
    |-------------------------|------------------|  
    |<span data-ttu-id="14c08-256">Adaptateur SharePoint avec CSOM</span><span class="sxs-lookup"><span data-stu-id="14c08-256">SharePoint Adapter with CSOM</span></span>|<span data-ttu-id="14c08-257">Oui</span><span class="sxs-lookup"><span data-stu-id="14c08-257">Yes</span></span>|  
    |<span data-ttu-id="14c08-258">SharePoint Online avec CSOM</span><span class="sxs-lookup"><span data-stu-id="14c08-258">SharePoint Online with CSOM</span></span>|<span data-ttu-id="14c08-259">Oui</span><span class="sxs-lookup"><span data-stu-id="14c08-259">Yes</span></span>|  
    |<span data-ttu-id="14c08-260">Service Web de SharePoint adaptateur (déconseillée)</span><span class="sxs-lookup"><span data-stu-id="14c08-260">SharePoint Adapter Web Service (deprecated)</span></span>|<span data-ttu-id="14c08-261">non</span><span class="sxs-lookup"><span data-stu-id="14c08-261">No</span></span>|  
    |<span data-ttu-id="14c08-262">Pas de SharePoint</span><span class="sxs-lookup"><span data-stu-id="14c08-262">No SharePoint</span></span>|<span data-ttu-id="14c08-263">non</span><span class="sxs-lookup"><span data-stu-id="14c08-263">No</span></span>|  
  
-   <span data-ttu-id="14c08-264">[Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations spécifiques sur les options d’installation de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="14c08-264">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) provides specific information on the SharePoint installation options.</span></span>  
  
##  <a name="BKMK_WSS"></a> <span data-ttu-id="14c08-265">Installation et configuration de Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="14c08-265">Install and Configure Microsoft SharePoint</span></span>  
 <span data-ttu-id="14c08-266">Installation de [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-266">Install [SharePoint 2013](http://technet.microsoft.com/library/cc303424.aspx)</span></span>  
  
 <span data-ttu-id="14c08-267">Installation de [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-267">Install [SharePoint Online Service](http://technet.microsoft.com/library/jj819267.aspx)</span></span>  
  
 <span data-ttu-id="14c08-268">Installation de [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-268">Install [SharePoint Server 2010](http://technet.microsoft.com/library/cc303424\(v=office.14\).aspx)</span></span>  
  
 <span data-ttu-id="14c08-269">Installation de [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-269">Install [SharePoint 2007](http://technet.microsoft.com/library/cc303424\(v=office.12\).aspx)</span></span>  
  
 <span data-ttu-id="14c08-270">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-270">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-271">Si vous installez SharePoint, vous devez le faire avant de poursuivre la configuration requise de BizTalk Server restante.</span><span class="sxs-lookup"><span data-stu-id="14c08-271">If you are installing SharePoint, you must do so before continuing with the remaining BizTalk Server prerequisites.</span></span>  
  
-   <span data-ttu-id="14c08-272">L’installation et la configuration de SharePoint s’effectuent comme suit :</span><span class="sxs-lookup"><span data-stu-id="14c08-272">Installing and configuring SharePoint consists of the following procedures:</span></span>  
  
    -   <span data-ttu-id="14c08-273">installation de SharePoint ;</span><span class="sxs-lookup"><span data-stu-id="14c08-273">Install SharePoint</span></span>  
  
    -   <span data-ttu-id="14c08-274">configuration de SharePoint ;</span><span class="sxs-lookup"><span data-stu-id="14c08-274">Configure SharePoint</span></span>  
  
    -   <span data-ttu-id="14c08-275">extension du site Web par défaut en tant que serveur virtuel.</span><span class="sxs-lookup"><span data-stu-id="14c08-275">Extend the default Web site as a virtual server</span></span>  
  
-   <span data-ttu-id="14c08-276">L’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) décrit les options d’installation de l’adaptateur SharePoint pour BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-276">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) describes the SharePoint adapter installation options for BizTalk Server.</span></span>  
  
-   <span data-ttu-id="14c08-277">Lorsque vous utilisez l’adaptateur SharePoint, il est recommandé d’installer la nouvelle option CSOM à la place du service web SharePoint Service, qui est décrite dans l’[annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="14c08-277">When using the SharePoint adapter, it is recommended to install the new CSOM option instead of the SharePoint Service Web Service; described at [Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md).</span></span>  
  
##  <a name="BKMK_SharedMem"></a> <span data-ttu-id="14c08-278">Désactivation du protocole de mémoire partagée</span><span class="sxs-lookup"><span data-stu-id="14c08-278">Disable the Shared Memory Protocol</span></span>  
  
1.  <span data-ttu-id="14c08-279">Ouvrez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="14c08-279">Open **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="14c08-280">Dans le **Gestionnaire de configuration SQL Server**, développez **Configuration du réseau SQL Server**, puis sélectionnez **Protocoles pour MSSQLSERVER**.</span><span class="sxs-lookup"><span data-stu-id="14c08-280">In **SQL Server Configuration Manager**, expand **SQL Server Network Configuration**, and then select **Protocols for MSSQLSERVER**.</span></span>  
  
3.  <span data-ttu-id="14c08-281">Cliquez avec le bouton droit sur **Mémoire partagée**, puis sélectionnez **Désactiver**.</span><span class="sxs-lookup"><span data-stu-id="14c08-281">Right-click **Shared Memory**, and then select **Disable**.</span></span>  
  
4.  <span data-ttu-id="14c08-282">Sélectionnez **Services SQL Server**, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="14c08-282">Select **SQL Server Services**, right-click **SQL Server (MSSQLSERVER)**, and then select **Stop**.</span></span> <span data-ttu-id="14c08-283">Une fois le service arrêté, cliquez de nouveau avec le bouton droit sur **SQL Server (MSSQLSERVER)**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="14c08-283">After the service has stopped, right-click **SQL Server (MSSQLSERVER)** again, and then select **Start**.</span></span>  
  
5.  <span data-ttu-id="14c08-284">Fermez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="14c08-284">Close **SQL Server Configuration Manager**.</span></span>  
  
 <span data-ttu-id="14c08-285">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-285">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-286">Dans certains cas de surcharge (comme des clients accédant à SQL Server à partir d'un seul ordinateur), il est possible que le protocole de mémoire partagée pour SQL Server diminue les performances de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-286">Under certain stress conditions (such as clients accessing SQL Server from the same computer), the SQL Server Shared Memory protocol may lower BizTalk Server performance.</span></span> <span data-ttu-id="14c08-287">Vous pouvez corriger ce comportement en désactivant le protocole de réseau de la mémoire partagée dans la configuration du réseau SQL Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-287">You can resolve this behavior by disabling the Shared Memory network protocol in SQL Server Network Configuration.</span></span>  
  
-   <span data-ttu-id="14c08-288">ReplaceThisText</span><span class="sxs-lookup"><span data-stu-id="14c08-288">ReplaceThisText</span></span>  
  
##  <a name="BKMK_LocalAdmin"></a> <span data-ttu-id="14c08-289">Adhésion au groupe Administrateurs local</span><span class="sxs-lookup"><span data-stu-id="14c08-289">Join the Local Administrators Group</span></span>  
 <span data-ttu-id="14c08-290">**Windows Server 2012** : [Windows Server 2012 : l’ajout d’un compte à un groupe d’administrateurs Local](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span><span class="sxs-lookup"><span data-stu-id="14c08-290">**Windows Server 2012** : [Windows Server 2012: How to Add an Account to a Local Administrator Group](http://social.technet.microsoft.com/wiki/contents/articles/13436.windows-server-2012-how-to-add-an-account-to-a-local-administrator-group.aspx)</span></span>  
  
 <span data-ttu-id="14c08-291">**Windows 8.1** : Pour ouvrir Utilisateurs et groupes locaux sur Windows 8.1, appuyez sur le bouton Windows du clavier et tapez **groupes**.</span><span class="sxs-lookup"><span data-stu-id="14c08-291">**Windows 8.1**: To open Local Users and Groups on Windows 8, click the Windows button on the keyboard and type **groups**.</span></span> <span data-ttu-id="14c08-292">Dans la fenêtre de recherche, cliquez sur **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="14c08-292">In the Search window, click **Settings**.</span></span> <span data-ttu-id="14c08-293">Dans la fenêtre des résultats, cliquez sur **Modifier les utilisateurs et les groupes locaux**.</span><span class="sxs-lookup"><span data-stu-id="14c08-293">In the Results window, click **Edit local users and groups**.</span></span> <span data-ttu-id="14c08-294">Cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.</span><span class="sxs-lookup"><span data-stu-id="14c08-294">Click **Groups** and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="14c08-295">**Windows 7 SP1** : Cliquez sur Démarrer.</span><span class="sxs-lookup"><span data-stu-id="14c08-295">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="14c08-296">Dans la zone de texte **Rechercher**, tapez **Gestion de l’ordinateur** et cliquez dessus pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="14c08-296">In the **Search** text box, type **Computer Management**, and click it to open.</span></span> <span data-ttu-id="14c08-297">Développez **Utilisateurs et groupes locaux**, cliquez sur **Groupes**, puis double-cliquez sur Administrateurs pour ajouter un compte.</span><span class="sxs-lookup"><span data-stu-id="14c08-297">Expand **Local Users and Groups**, click **Groups**, and then double-click Administrators to add an account.</span></span>  
  
 <span data-ttu-id="14c08-298">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-298">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-299">Vous devez être membre du groupe Administrateurs local pour installer et configurer BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="14c08-299">You must be a member of the local Administrators group to install and configure BizTalk Server.</span></span>  
  
##  <a name="BKMK_AppLog"></a> <span data-ttu-id="14c08-300">Configuration du journal des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="14c08-300">Configure the Application Event Log</span></span>  
  
1.  <span data-ttu-id="14c08-301">Cliquez sur **Observateur d’événements** :</span><span class="sxs-lookup"><span data-stu-id="14c08-301">Open **Event Viewer**:</span></span>  
  
     <span data-ttu-id="14c08-302">**Windows Server 2012** : cliquez sur le bouton Windows du clavier et tapez **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="14c08-302">**Windows Server 2012** : Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="14c08-303">Dans la fenêtre des résultats, cliquez sur **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="14c08-303">In the Results window, click **Event Viewer**.</span></span>  
  
     <span data-ttu-id="14c08-304">**Windows 8.1** : Appuyez sur le bouton Windows du clavier et tapez **Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="14c08-304">**Windows 8.1**: Click the Windows button on the keyboard and type **Event Viewer**.</span></span> <span data-ttu-id="14c08-305">Dans la fenêtre de recherche, cliquez sur **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="14c08-305">In the Search window, click **Settings**.</span></span> <span data-ttu-id="14c08-306">Dans la fenêtre des résultats, cliquez sur **Afficher les journaux d’événements**.</span><span class="sxs-lookup"><span data-stu-id="14c08-306">In the Results window, click **View event logs**.</span></span>  
  
     <span data-ttu-id="14c08-307">**Windows 7 SP1** : Cliquez sur Démarrer.</span><span class="sxs-lookup"><span data-stu-id="14c08-307">**Windows 7 SP1**: Click Start.</span></span> <span data-ttu-id="14c08-308">Dans la zone de texte **Rechercher**, tapez **Observateur d’événements**, et cliquez dessus pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="14c08-308">In the **Search** text box, type **Event Viewer**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="14c08-309">Développez **Journaux Windows**, cliquez avec le bouton droit sur **Application**, puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="14c08-309">Expand **Windows Logs**, right-click **Application**, and then click **Properties**.</span></span> <span data-ttu-id="14c08-310">Dans **Propriétés du journal** :</span><span class="sxs-lookup"><span data-stu-id="14c08-310">In **Log Properties**:</span></span>  
  
    -   <span data-ttu-id="14c08-311">Pour déterminer l’espace disponible, comparez les propriétés **Taille du journal** et **Taille maximale du journal**.</span><span class="sxs-lookup"><span data-stu-id="14c08-311">To determine the available space, compare the **Log Size** and the **Maximum log size** properties.</span></span>  
  
    -   <span data-ttu-id="14c08-312">Pour fournir plus d’espace, entrez un numéro supérieur dans **Taille maximale du journal**.</span><span class="sxs-lookup"><span data-stu-id="14c08-312">To provide more space, enter a higher number in **Maximum log size**.</span></span>  
  
    -   <span data-ttu-id="14c08-313">Pour activer le remplacement des anciens événements lorsque le journal est plein, sélectionnez **Remplacer les événements si nécessaire**.</span><span class="sxs-lookup"><span data-stu-id="14c08-313">To enable overwriting of old events when the log becomes full, select **Overwrite events as needed**.</span></span>  
  
    -   <span data-ttu-id="14c08-314">Pour effacer les événements du journal, sélectionnez **Effacer le journal**.</span><span class="sxs-lookup"><span data-stu-id="14c08-314">To clear the log events, select **Clear log**.</span></span>  
  
3.  <span data-ttu-id="14c08-315">Cliquez sur **OK** pour fermer l’**Observateur d’événements**.</span><span class="sxs-lookup"><span data-stu-id="14c08-315">Click **OK** to close the **Event Viewer**.</span></span>  
  
 <span data-ttu-id="14c08-316">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="14c08-316">**Additional**</span></span>  
  
-   <span data-ttu-id="14c08-317">Le programme d'installation de BizTalk Server conserve un enregistrement des événements dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="14c08-317">BizTalk Server setup keeps a record of events in the Application Event Log.</span></span> <span data-ttu-id="14c08-318">Selon les fonctionnalités de BizTalk Server installées, il se peut que la limite d'espace requis dans le journal soit dépassée.</span><span class="sxs-lookup"><span data-stu-id="14c08-318">Depending on the BizTalk Server features installed, the amount of space required in the log may exceed its limit.</span></span> <span data-ttu-id="14c08-319">Si le journal des événements application suffisamment d’espace lors de l’installation de BizTalk Server, l’installation échoue.</span><span class="sxs-lookup"><span data-stu-id="14c08-319">If the application event log runs out of space during BizTalk Server setup, the installation fails.</span></span> <span data-ttu-id="14c08-320">Le fait de modifier les paramètres du journal d'événements d'applications permet d'empêcher cet échec.</span><span class="sxs-lookup"><span data-stu-id="14c08-320">Changing the Application Event Log settings prevents this failure.</span></span>  
  
## <a name="next"></a><span data-ttu-id="14c08-321">Suivant</span><span class="sxs-lookup"><span data-stu-id="14c08-321">Next</span></span>  
 [<span data-ttu-id="14c08-322">Choix des fonctionnalités et composants de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="14c08-322">Choose BizTalk Server Features and Components</span></span>](http://msdn.microsoft.com/library/b8c43fcf-9e5c-48ba-830b-13a5177e30f0)  
  
## <a name="see-also"></a><span data-ttu-id="14c08-323">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14c08-323">See Also</span></span>  
 <span data-ttu-id="14c08-324">[Vue d’ensemble de l’installation de BizTalk Server 2013 et 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span><span class="sxs-lookup"><span data-stu-id="14c08-324">[Installation Overview for BizTalk Server 2013 and 2013 R2](http://msdn.microsoft.com/library/8041926c-cfc9-4eaf-9c28-a2c6e8015bc5) </span></span>  
 <span data-ttu-id="14c08-325">[Annexe A : Installation sans assistance](../install-and-config-guides/appendix-a-silent-installation.md) </span><span class="sxs-lookup"><span data-stu-id="14c08-325">[Appendix A: Silent Installation](../install-and-config-guides/appendix-a-silent-installation.md) </span></span>  
 <span data-ttu-id="14c08-326">[Annexe B : Installation de l’adaptateur Microsoft SharePoint](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="14c08-326">[Appendix B: Install the Microsoft SharePoint Adapter](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) </span></span>  
 <span data-ttu-id="14c08-327">[Annexe C : Fichiers CAB redistribuables](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span><span class="sxs-lookup"><span data-stu-id="14c08-327">[Appendix C: Redistributable CAB Files](../install-and-config-guides/appendix-c-redistributable-cab-files.md) </span></span>  
 [<span data-ttu-id="14c08-328">Annexe D : Création du serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="14c08-328">Appendix D: Create the SMTP Server</span></span>](../install-and-config-guides/appendix-d-create-the-smtp-server.md)
