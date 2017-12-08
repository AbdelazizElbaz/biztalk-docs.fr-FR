---
title: "Étapes de post-installation pour BizTalk Server 2013 et 2013 R2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c3b47843-9da5-4144-8b84-135494b8ab43
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b86d8c4c1e1a22dad349c2cc8c2be5ca4b206b2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="post-installation-steps-for-biztalk-server-2013-and-2013-r2"></a><span data-ttu-id="2f2a9-102">Étapes de post-installation pour BizTalk Server 2013 et 2013 R2</span><span class="sxs-lookup"><span data-stu-id="2f2a9-102">Post-installation Steps for BizTalk Server 2013 and 2013 R2</span></span>
  
##  <a name="BKMK_NamedPipes"></a> <span data-ttu-id="2f2a9-103">Activation du protocole TCP/IP et des canaux nommés</span><span class="sxs-lookup"><span data-stu-id="2f2a9-103">Enable TCP/IP and Named Pipes</span></span>  
  
1.  <span data-ttu-id="2f2a9-104">Ouvrez le **Gestionnaire de configuration SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-104">Open **SQL Server Configuration Manager**.</span></span>  
  
2.  <span data-ttu-id="2f2a9-105">Développez **Configuration du réseau SQL Server** et sélectionnez **Protocoles pour MSSQLSERVER**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-105">Expand **SQL Server Network Configuration**, and select **Protocols for MSSQLSERVER**.</span></span>  
  
4.  <span data-ttu-id="2f2a9-106">Vérifiez que les options **TCP/IP** et **Canaux nommés** sont activées.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-106">Verify that both **TCP/IP** and **Named Pipes** are enabled.</span></span> <span data-ttu-id="2f2a9-107">Si elles sont activées, passez à l’étape suivante.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-107">If enabled, proceed to the next step.</span></span>  
  
     <span data-ttu-id="2f2a9-108">Sinon :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-108">If not enabled:</span></span>  
  
    -   <span data-ttu-id="2f2a9-109">Cliquez avec le bouton droit sur le protocole, puis cliquez sur **Activer**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-109">Right-click the protocol, and then click **Enable**.</span></span>  
  
    -   <span data-ttu-id="2f2a9-110">Répétez l'opération pour activer l'autre protocole, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-110">Repeat to enable the other protocol if necessary.</span></span>  
  
    -   <span data-ttu-id="2f2a9-111">Dans le volet gauche, cliquez sur **Services SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-111">In the left-hand pane, click **SQL Server Services**.</span></span>  
  
    -   <span data-ttu-id="2f2a9-112">Dans le volet droit, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)** et cliquez sur **Arrêter**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-112">In the right-hand pane, right-click **SQL Server (MSSQLSERVER)**, and click **Stop**.</span></span>  
  
    -   <span data-ttu-id="2f2a9-113">Une fois le service arrêté, cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)** et cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-113">When the service has stopped, right-click **SQL Server (MSSQLSERVER)**, and click **Start**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2f2a9-114">Si vous utilisez [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], le service **NS$BAMAlerts** peut être arrêté.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-114">If you are using [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], the **NS$BAMAlerts** service may be stopped.</span></span> <span data-ttu-id="2f2a9-115">Redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-115">Restart the service.</span></span>  
  
5.  <span data-ttu-id="2f2a9-116">Fermez le **Gestionnaire de configuration**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-116">Close the **Configuration Manager**.</span></span>  
  
##  <a name="BKMK_DTC"></a> <span data-ttu-id="2f2a9-117">Activation de DTC (Distributed Transaction Coordinator) sur le serveur hôte local</span><span class="sxs-lookup"><span data-stu-id="2f2a9-117">Enable DTC on the Local Host Server</span></span>  
  
1.  <span data-ttu-id="2f2a9-118">Ouvrez Services de composants :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-118">Open Component Services:</span></span>  
  
     <span data-ttu-id="2f2a9-119">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Sélectionnez le bouton Windows et tapez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-119">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Select the Windows button, and type **Component Services**.</span></span> <span data-ttu-id="2f2a9-120">Dans la fenêtre des résultats, sélectionnez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-120">In the Results window, select **Component Services**.</span></span>  
  
     <span data-ttu-id="2f2a9-121">**Windows 8.1** : Sélectionnez le bouton Windows et tapez **Outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-121">**Windows 8.1**: Select the Windows button, and type **Administrative Tools**.</span></span> <span data-ttu-id="2f2a9-122">Dans la fenêtre de recherche, sélectionnez **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-122">In the Search window, select **Settings**.</span></span> <span data-ttu-id="2f2a9-123">Dans la fenêtre des résultats, cliquez sur **Outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-123">In the Results window, click **Administrative Tools**.</span></span> <span data-ttu-id="2f2a9-124">Double-cliquez sur **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-124">Double-click **Component Services**.</span></span>  
  
     <span data-ttu-id="2f2a9-125">**Windows 7 SP1** : Sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-125">**Windows 7 SP1**: Select **Start**.</span></span> <span data-ttu-id="2f2a9-126">Dans la zone de texte **Rechercher**, tapez **Services de composants** et cliquez dessus pour les ouvrir.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-126">In the **Search** text box, type **Component Services**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="2f2a9-127">Dans l’arborescence de la console, développez **Services de composants**, **Ordinateurs**, **Poste de travail**, **Distributed Transaction Coordinator**, puis cliquez sur **DTC local**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-127">In the console tree, expand **Component Services**, expand **Computers**, expand **My Computer**, expand **Distributed Transaction Coordinator**, and then click **Local DTC**.</span></span>  
  
3.  <span data-ttu-id="2f2a9-128">Cliquez avec le bouton droit sur **DTC local** et sélectionnez **Propriétés** pour afficher la boîte de dialogue **Propriétés DTC locales**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-128">Right-click **Local DTC** and select **Properties** to open the **Local DTC Properties**.</span></span>  
  
4.  <span data-ttu-id="2f2a9-129">Sélectionnez l’onglet **Sécurité**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-129">Select the **Security** tab.</span></span>  
  
5.  <span data-ttu-id="2f2a9-130">Veiller à activer les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-130">Confirm the following options are checked:</span></span>  
  
    -   <span data-ttu-id="2f2a9-131">**Accès DTC réseau**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-131">**Network DTC Access**</span></span>  
  
    -   <span data-ttu-id="2f2a9-132">**Autoriser les transactions entrantes**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-132">**Allow Inbound**</span></span>  
  
    -   <span data-ttu-id="2f2a9-133">**Autoriser les transactions sortantes**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-133">**Allow Outbound**</span></span>  
  
    -   <span data-ttu-id="2f2a9-134">**Aucune authentification requise**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-134">**No Authentication Required**</span></span>  
  
     <span data-ttu-id="2f2a9-135">Pour obtenir des paramètres supplémentaires qui peuvent être nécessaires, consultez [Résolution des problèmes liés à MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span><span class="sxs-lookup"><span data-stu-id="2f2a9-135">For additional settings that may be needed, see [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).</span></span>  
  
6.  <span data-ttu-id="2f2a9-136">Sélectionnez **OK** pour fermer la boîte de dialogue **Propriétés DTC locales**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-136">Select **OK** to close the **Local DTC Properties** dialog box.</span></span> <span data-ttu-id="2f2a9-137">Redémarrez le service MSDTC, si vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-137">Restart the MSDTC service if prompted.</span></span>  
  
7.  <span data-ttu-id="2f2a9-138">Fermez **Services de composants**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-138">Close **Component Services**.</span></span>  
  
##  <a name="BKMK_Firewall"></a> <span data-ttu-id="2f2a9-139">Configuration du Pare-feu Windows pour activer DTC</span><span class="sxs-lookup"><span data-stu-id="2f2a9-139">Configure Windows Firewall to Enable DTC</span></span>  
  
1.  <span data-ttu-id="2f2a9-140">Ouvrez le **Pare-feu Windows** :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-140">Open **Windows Firewall**:</span></span>  
  
     <span data-ttu-id="2f2a9-141">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : appuyez sur le bouton Windows du clavier et tapez **Pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-141">**[!INCLUDE[btsWinSrv2k12](../includes/btswinsrv2k12-md.md)]** : Click the Windows button, and type **Windows Firewall**.</span></span> <span data-ttu-id="2f2a9-142">Dans la fenêtre des résultats, cliquez sur **Pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-142">In the Results window, click **Windows Firewall**.</span></span>  
  
     <span data-ttu-id="2f2a9-143">**Windows 8.1**: appuyez sur le bouton Windows et tapez **Pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-143">**Windows 8.1**: Click the Windows button, and type **Windows Firewall**.</span></span> <span data-ttu-id="2f2a9-144">Dans la fenêtre de recherche, cliquez sur **Paramètres**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-144">In the Search window, click **Settings**.</span></span> <span data-ttu-id="2f2a9-145">Dans la fenêtre des résultats, cliquez sur **Pare-feu Windows**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-145">In the Results window, click **Windows Firewall**.</span></span>  
  
     <span data-ttu-id="2f2a9-146">**Windows 7 SP1** : cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-146">**Windows 7 SP1**: Click **Start**.</span></span> <span data-ttu-id="2f2a9-147">Dans la zone de texte **Rechercher**, tapez **Pare-feu Windows** et cliquez dessus pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-147">In the **Search** text box, type **Windows Firewall**, and click it to open.</span></span>  
  
2.  <span data-ttu-id="2f2a9-148">Cliquez sur **Paramètres avancés**, puis sur **Règles de trafic entrant**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-148">Click **Advanced Settings** and click **Inbound Rules**.</span></span>  
  
3.  <span data-ttu-id="2f2a9-149">Dans le volet **Règles entrantes**, cliquez avec le bouton droit sur **Distributed Transaction Coordinator** \* (selon le cas), puis cliquez sur **Activer la règle**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-149">In the **Inbound Rules** pane, right-click **Distributed Transaction Coordinator** \* (as appropriate), and then click **Enable Rule**.</span></span>  
  
4.  <span data-ttu-id="2f2a9-150">Cliquez sur **Règles sortantes**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-150">Click **Outbound Rules**.</span></span>  
  
5.  <span data-ttu-id="2f2a9-151">Dans le volet **Règles sortantes**, cliquez avec le bouton droit sur **Distributed Transaction Coordinator** \* (selon le cas), puis cliquez sur **Activer la règle**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-151">In the **Outbound Rules** pane, right-click **Distributed Transaction Coordinator** \* (as appropriate), and then click **Enable Rule**.</span></span>  
  
6.  <span data-ttu-id="2f2a9-152">Dans le **Panneau de configuration**, modifiez l’affichage des listes en affichant des icônes, puis double-cliquez sur **Outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-152">On the **Control Panel**, change the view to list by icons, and then double-click **Administrative Tools**.</span></span>  
  
7.  <span data-ttu-id="2f2a9-153">Double-cliquez sur **Services**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-153">Double-click **Services**.</span></span>  
  
8.  <span data-ttu-id="2f2a9-154">Cliquez avec le bouton droit sur **Application système COM+**, cliquez sur **Redémarrer** et attendez que le service redémarre.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-154">Right-click **COM+ System Application**, click **Restart**, and wait for the service to restart.</span></span>  
  
9. <span data-ttu-id="2f2a9-155">Effectuez un clic droit et redémarrez le service **Distributed Transaction Coordinator**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-155">Right-click and restart the **Distributed Transaction Coordinator** service.</span></span>  
  
10. <span data-ttu-id="2f2a9-156">Effectuez un clic droit et redémarrez le service **SQL Server (MSSQLSERVER)**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-156">Right-click and restart the **SQL Server (MSSQLSERVER)** service.</span></span>  
  
11. <span data-ttu-id="2f2a9-157">Fermez la page **Services (local)**, puis la page **Outils d’administration**.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-157">Close **Services (Local)**, and then close **Administrative Tools**.</span></span>  
  
##  <a name="BKMK_SQLAgent"></a> <span data-ttu-id="2f2a9-158">Configuration des travaux de l’Agent SQL</span><span class="sxs-lookup"><span data-stu-id="2f2a9-158">Configure SQL Agent Jobs</span></span>  
  
|<span data-ttu-id="2f2a9-159">Travail</span><span class="sxs-lookup"><span data-stu-id="2f2a9-159">Job</span></span>|<span data-ttu-id="2f2a9-160">Description</span><span class="sxs-lookup"><span data-stu-id="2f2a9-160">Description</span></span>|<span data-ttu-id="2f2a9-161">Raisons</span><span class="sxs-lookup"><span data-stu-id="2f2a9-161">Why configure</span></span>|  
|---------|-----------------|-------------------|  
|<span data-ttu-id="2f2a9-162">**Sauvegarde de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-162">**Backup BizTalk Server**</span></span>|<span data-ttu-id="2f2a9-163">Ce travail de l’Agent SQL sauvegarde les bases de données et les fichiers journaux de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f2a9-163">This SQL Agent job backs up the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the log files.</span></span> <span data-ttu-id="2f2a9-164">Dans le cadre de la configuration de ce travail, vous déterminez divers paramètres tels que la fréquence et l’emplacement de fichier.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-164">When configuring the job, you determine parameters like frequency and file location.</span></span><br /><br /> <span data-ttu-id="2f2a9-165">Les liens suivants décrivent le travail de l’Agent SQL et ses paramètres :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-165">The following links describe the SQL Agent job and its parameters:</span></span><br /><br /> <span data-ttu-id="2f2a9-166">[Sauvegarde et restauration des bases de données BizTalk Server](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f2a9-166">[Backing Up and Restoring BizTalk Server Databases](http://msdn.microsoft.com/library/aa561125\(v=bts.80\).aspx)</span></span><br /><br /> <span data-ttu-id="2f2a9-167">[Configuration du travail de sauvegarde de BizTalk Server](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f2a9-167">[How to Configure the Backup BizTalk Server Job](http://msdn.microsoft.com/library/aa546765\(v=bts.80\).aspx)</span></span>|<span data-ttu-id="2f2a9-168">Ce travail de l’Agent SQL tronque par ailleurs les journaux des transactions, ce qui permet d’améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-168">This SQL Agent job also truncates the transaction logs, which helps improve performance.</span></span><br /><br /> <span data-ttu-id="2f2a9-169">Le travail **Sauvegarde de BizTalk Server** ne supprime pas les fichiers de sauvegarde, même les fichiers plus anciens.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-169">The **Backup BizTalk Server** job does not remove or delete backup files, including older files.</span></span> <span data-ttu-id="2f2a9-170">Pour supprimer les fichiers de sauvegarde, consultez la rubrique [Échec du travail « Sauvegarde de BizTalk Server » suite à l’accumulation de fichiers sur le serveur de base de données Microsoft BizTalk Server](http://support.microsoft.com/kb/982546).</span><span class="sxs-lookup"><span data-stu-id="2f2a9-170">To delete backup files, refer to [The "Backup BizTalk Server" job fails when backup files accumulate over time in the Microsoft BizTalk Server database server](http://support.microsoft.com/kb/982546).</span></span>|  
|<span data-ttu-id="2f2a9-171">**Purge et archivage DTA**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-171">**DTA Purge and Archive**</span></span>|<span data-ttu-id="2f2a9-172">Ce travail de l’Agent SQL tronque et archive la base de données des suivis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="2f2a9-172">This SQL Agent job truncates and archives the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Tracking database (BizTalkDTADb).</span></span> <span data-ttu-id="2f2a9-173">Dans le cadre de la configuration du travail, vous déterminez les paramètres tels que le délai de conservation des instances terminées et de toutes les données.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-173">When configuring the job, you determine parameters like how many days to keep completed instances and how many to days to keep all data.</span></span><br /><br /> <span data-ttu-id="2f2a9-174">Les liens suivants décrivent le travail de l’Agent SQL et ses paramètres :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-174">The following links describe the SQL Agent job and its parameters:</span></span><br /><br /> <span data-ttu-id="2f2a9-175">[Archivage et purge de la base de données de suivi BizTalk](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f2a9-175">[Archiving and Purging the BizTalk Tracking Database](http://msdn.microsoft.com/library/aa560754\(v=bts.80\).aspx)</span></span><br /><br /> <span data-ttu-id="2f2a9-176">[Configuration du travail de purge et d’archivage DTA](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f2a9-176">[How to Configure the DTA Purge and Archive Job](http://msdn.microsoft.com/library/aa558715\(v=bts.80\).aspx)</span></span>|<span data-ttu-id="2f2a9-177">Ce travail de l’Agent SQL affecte directement les performances en conservant les événements de l’hôte de suivi et de purge du suivi.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-177">This SQL Agent job directly impacts performance by maintaining the Tracking host and purging tracking events.</span></span><br /><br /> <span data-ttu-id="2f2a9-178">Les rubriques suivantes ont trait aux performances :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-178">Performance topics include:</span></span><br /><br /> [<span data-ttu-id="2f2a9-179">Gestion et dépannage des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2f2a9-179">How to maintain and troubleshoot BizTalk Server databases</span></span>](http://support.microsoft.com/kb/952555)<br /><br /> <span data-ttu-id="2f2a9-180">[Instructions pour le dimensionnement de la base de données de suivi](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f2a9-180">[Tracking Database Sizing Guidelines](http://msdn.microsoft.com/library/aa559162\(v=bts.80\).aspx)</span></span>|  
  
 <span data-ttu-id="2f2a9-181">**Supplément**</span><span class="sxs-lookup"><span data-stu-id="2f2a9-181">**Additional**</span></span>  
  
-   <span data-ttu-id="2f2a9-182">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé, plusieurs travaux de l’Agent SQL sont créés automatiquement, comme décrit dans les liens suivants :</span><span class="sxs-lookup"><span data-stu-id="2f2a9-182">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed, several SQL Agent jobs are automatically created, as described in the following links:</span></span>  
  
     [<span data-ttu-id="2f2a9-183">Description des travaux de l’Agent SQL Server dans BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2f2a9-183">Description of the SQL Server Agent jobs in BizTalk Server</span></span>](http://support.microsoft.com/kb/919776)  
  
     <span data-ttu-id="2f2a9-184">[Structure et travaux de base de données](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2f2a9-184">[Database Structure and Jobs](http://msdn.microsoft.com/library/aa561960\(v=bts.80\).aspx)</span></span>  
  
##  <a name="BKMK_InstallCU"></a> <span data-ttu-id="2f2a9-185">Installation des mises à jour cumulatives</span><span class="sxs-lookup"><span data-stu-id="2f2a9-185">Install Cumulative Updates</span></span>  
 <span data-ttu-id="2f2a9-186">Après avoir installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], installez les éventuelles mises à jour cumulatives de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] répertoriées dans Windows Update.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-186">After you install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], install any [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cumulative updates listed in Windows Update.</span></span> <span data-ttu-id="2f2a9-187">L’[article 2555976 de la Base de connaissances](http://support.microsoft.com/kb/2555976) répertorie les Services Pack et les mises à jour cumulatives disponibles.</span><span class="sxs-lookup"><span data-stu-id="2f2a9-187">[KB article 2555976](http://support.microsoft.com/kb/2555976) lists available service packs and cumulative updates.</span></span>  
  
## <a name="next"></a><span data-ttu-id="2f2a9-188">Suivant</span><span class="sxs-lookup"><span data-stu-id="2f2a9-188">Next</span></span>  
[<span data-ttu-id="2f2a9-189">Configuration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2f2a9-189">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)
  
## <a name="see-also"></a><span data-ttu-id="2f2a9-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f2a9-190">See Also</span></span>  
 [<span data-ttu-id="2f2a9-191">Annexe A : Installation sans assistance</span><span class="sxs-lookup"><span data-stu-id="2f2a9-191">Appendix A: Silent Installation</span></span>](../install-and-config-guides/appendix-a-silent-installation.md) 
 
[<span data-ttu-id="2f2a9-192">Annexe B : Installation de l’adaptateur Microsoft SharePoint</span><span class="sxs-lookup"><span data-stu-id="2f2a9-192">Appendix B: Install the Microsoft SharePoint Adapter</span></span>](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md)  

[<span data-ttu-id="2f2a9-193">Annexe C : Fichiers CAB redistribuables</span><span class="sxs-lookup"><span data-stu-id="2f2a9-193">Appendix C: Redistributable CAB Files</span></span>](../install-and-config-guides/appendix-c-redistributable-cab-files.md)  

[<span data-ttu-id="2f2a9-194">Annexe D : Création du serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="2f2a9-194">Appendix D: Create the SMTP Server</span></span>](../install-and-config-guides/appendix-d-create-the-smtp-server.md)

[<span data-ttu-id="2f2a9-195">Désinstallation et annulation de la configuration de BizTalk Server pour le supprimer</span><span class="sxs-lookup"><span data-stu-id="2f2a9-195">Uninstall and unconfigure BizTalk Server to remove it</span></span>](../install-and-config-guides/uninstall-and-unconfigure-biztalk-server-to-remove-it.md)
