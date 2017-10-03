---
title: "Résolution des problèmes d’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e63299a8-5c74-4337-ba20-3213e0c6ea1f
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d47932ffd9f7843d0b3d95073ca54bce987b8f75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-bam"></a><span data-ttu-id="e8633-102">Résolution des problèmes d’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e8633-102">Troubleshooting BAM</span></span>
<span data-ttu-id="e8633-103">Cette rubrique fournit des informations permettant de faciliter la résolution des problèmes que vous pouvez rencontrer lors de l'utilisation de l'analyse BAM (Business Activity Monitoring).</span><span class="sxs-lookup"><span data-stu-id="e8633-103">This topic provides information to help you troubleshoot problems you might encounter when using Business Activity Monitoring (BAM).</span></span>  
  
## <a name="bam-deployment-failed"></a><span data-ttu-id="e8633-104">Échec du déploiement de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e8633-104">BAM deployment failed</span></span>  
 <span data-ttu-id="e8633-105">Si vous tentez de déployer une définition BAM qui inclut une agrégation RTA lorsque SQL Server Analysis Services n'est pas disponible, la commande Bm.exe affiche le message suivant :</span><span class="sxs-lookup"><span data-stu-id="e8633-105">If you attempt to deploy a BAM definition that includes a real-time aggregation (RTA) when SQL Server Analysis Services is not available, the Bm.exe command will display the following message:</span></span>  
  
 <span data-ttu-id="e8633-106">Erreur : Échec du déploiement de l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="e8633-106">ERROR: BAM deployment failed.</span></span> <span data-ttu-id="e8633-107">Impossible d'établir une connexion.</span><span class="sxs-lookup"><span data-stu-id="e8633-107">A connection cannot be made.</span></span> <span data-ttu-id="e8633-108">Vérifiez que le serveur fonctionne.</span><span class="sxs-lookup"><span data-stu-id="e8633-108">Ensure that the server is running.</span></span> <span data-ttu-id="e8633-109">Aucune connexion n’a pu être établie, car l’ordinateur cible l’a activement refusée  *\<adresse IP >*.</span><span class="sxs-lookup"><span data-stu-id="e8633-109">No connection could be made because the target machine actively refused it *\<IP address>*.</span></span>  
  
 <span data-ttu-id="e8633-110">Cette erreur se produit car SQL Server Analysis Services doit avoir été installé et configuré, et doit être en cours d'exécution afin de déployer une définition BAM qui inclut une valeur RTA.</span><span class="sxs-lookup"><span data-stu-id="e8633-110">This occurs because SQL Server Analysis Services must have been installed and configured, and must be running in order to deploy a BAM definition that includes an RTA.</span></span>  
  
## <a name="cannot-refresh-the-live-data-workbook"></a><span data-ttu-id="e8633-111">Impossible d'actualiser le classeur de données actives</span><span class="sxs-lookup"><span data-stu-id="e8633-111">Cannot refresh the live data workbook</span></span>  
 <span data-ttu-id="e8633-112">Lorsque vous tentez d'actualiser les données d'un classeur de données actives, Microsoft Office Excel risque d'afficher l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="e8633-112">When you try to refresh the data in a live data workbook, Microsoft Office Excel might display the following error:</span></span>  
  
 `XML for Analysis parser: The CurrentCatalog XML/A property was not specified.`  
  
 <span data-ttu-id="e8633-113">Cette erreur se produit car le complément BAM n'a pas été ajouté à Excel.</span><span class="sxs-lookup"><span data-stu-id="e8633-113">This occurs because the BAM add-in has not been added to Excel.</span></span>  
  
#### <a name="to-add-the-bam-add-in-to-excel"></a><span data-ttu-id="e8633-114">Pour ajouter le complément BAM à Excel</span><span class="sxs-lookup"><span data-stu-id="e8633-114">To add the BAM add-in to Excel</span></span>  
  
1.  <span data-ttu-id="e8633-115">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft Office**, puis cliquez sur **Microsoft Office Excel**.</span><span class="sxs-lookup"><span data-stu-id="e8633-115">Click **Start**, point to **All Programs**, point to **Microsoft Office**, and then click **Microsoft Office Excel**.</span></span>  
  
2.  <span data-ttu-id="e8633-116">Cliquez sur le **bouton Microsoft Office**, puis cliquez sur **Options Excel**.</span><span class="sxs-lookup"><span data-stu-id="e8633-116">Click the **Microsoft Office Button**, and then click **Excel Options**.</span></span>  
  
3.  <span data-ttu-id="e8633-117">Dans le **Options Excel** boîte de dialogue, cliquez sur **compléments**.</span><span class="sxs-lookup"><span data-stu-id="e8633-117">In the **Excel Options** dialog box, click **Add-Ins**.</span></span>  
  
4.  <span data-ttu-id="e8633-118">Dans le **compléments** volet, cliquez sur **accédez**.</span><span class="sxs-lookup"><span data-stu-id="e8633-118">In the **Add-Ins** pane, click **Go**.</span></span>  
  
5.  <span data-ttu-id="e8633-119">Dans le **compléments** boîte de dialogue, sélectionnez le **Business Activity Monitoring** case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e8633-119">In the **Add-Ins** dialog box, select the **Business Activity Monitoring** check box, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e8633-120">![Ajouter &#45; boîte de dialogue complémentaires](../core/media/addins.gif "AddIns")</span><span class="sxs-lookup"><span data-stu-id="e8633-120">![Add&#45;Ins dialog box](../core/media/addins.gif "AddIns")</span></span>  
  
## <a name="errorobject-library-invalid-or-contains-references-to-object-definitions-that-could-not-be-found-with-bam-excel-add-in-in-office"></a><span data-ttu-id="e8633-121">Erreur : « Bibliothèque d’objets incorrecte ou contenant des références à des définitions d’objets introuvables » avec le complément BAM pour Excel dans Office</span><span class="sxs-lookup"><span data-stu-id="e8633-121">Error:"Object library invalid or contains references to object definitions that could not be found" with BAM Excel Add-In in Office</span></span>  
 <span data-ttu-id="e8633-122">Vous pouvez recevoir cette erreur lorsque vous tentez d’utiliser le complément BAM pour Excel après la mise à niveau de Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="e8633-122">You may receive this error, when you try use the BAM Excel Add-In after you upgrade Microsoft Excel.</span></span>  
  
 <span data-ttu-id="e8633-123">**Résolution :** étant donné que le complément BAM utilise des contrôles ActiveX, vous devez supprimer tous les fichiers .exd mis en cache dans les répertoires suivants :</span><span class="sxs-lookup"><span data-stu-id="e8633-123">**Resolution:** Since the BAM Add-In uses ActiveX controls, you have to delete any cached .exd files from the following directories:</span></span>  
  
-   <span data-ttu-id="e8633-124">C:\Documents and Settings\\< nom d’utilisateur\>\Application Data\Microsoft\Forms</span><span class="sxs-lookup"><span data-stu-id="e8633-124">C:\Documents and Settings\\<username\>\Application Data\Microsoft\Forms</span></span>  
  
-   <span data-ttu-id="e8633-125">C:\Documents and Settings\\< nom d’utilisateur\>\AppData\Local\Temp\VBE</span><span class="sxs-lookup"><span data-stu-id="e8633-125">C:\Documents and Settings\\<username\>\AppData\Local\Temp\VBE</span></span>  
  
## <a name="bam-portal-cannot-connect"></a><span data-ttu-id="e8633-126">Le portail BAM ne parvient pas à se connecter</span><span class="sxs-lookup"><span data-stu-id="e8633-126">BAM portal cannot connect</span></span>  
 <span data-ttu-id="e8633-127">Dans [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], vous devez exécuter le portail BAM en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e8633-127">In [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)], you must run the BAM portal as an administrator.</span></span>  
  
#### <a name="to-run-the-bam-portal-on-windows-server-2008-r2-or-windows-7"></a><span data-ttu-id="e8633-128">Pour exécuter le portail BAM sur Windows Server 2008 R2 ou Windows 7</span><span class="sxs-lookup"><span data-stu-id="e8633-128">To run the BAM portal on Windows Server 2008 R2 or Windows 7</span></span>  
  
1.  <span data-ttu-id="e8633-129">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, avec le bouton droit **Internet Explorer**, puis cliquez sur **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="e8633-129">Click **Start**, point to **All Programs**, right-click **Internet Explorer**, and then click **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="e8633-130">Dans le **contrôle de compte d’utilisateur** boîte de dialogue, cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="e8633-130">In the **User Account Control** dialog box, click **Continue**.</span></span>  
  
3.  <span data-ttu-id="e8633-131">Dans la barre d’adresses Internet Explorer, tapez `http://<server>/BAM`, où  *\<server >* est le nom de l’ordinateur qui exécute le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="e8633-131">In the Internet Explorer address bar, type `http://<server>/BAM`, where *\<server>* is the name of the computer that is running the BAM portal.</span></span>  
  
## <a name="bam-portal-does-not-work-if-invalid-users-are-granted-permissions"></a><span data-ttu-id="e8633-132">Le portail BAM ne fonctionne pas si des autorisations sont accordées à des utilisateurs non valides</span><span class="sxs-lookup"><span data-stu-id="e8633-132">BAM portal does not work if invalid users are granted permissions</span></span>  
 <span data-ttu-id="e8633-133">Si un utilisateur Active Directory disposant des autorisations Vue BAM est retiré d'AD, le portail BAM ne se charge pas correctement pour tous les utilisateurs (à l'exception des DBO).</span><span class="sxs-lookup"><span data-stu-id="e8633-133">If an AD user who has the BAM view permissions is removed from the AD, then the BAM portal does not load properly for any user (except DBO).</span></span>  
  
 <span data-ttu-id="e8633-134">Pour résoudre ce problème, supprimez l'utilisateur non valide du rôle de sécurité bam_{viewname}view correspondant.</span><span class="sxs-lookup"><span data-stu-id="e8633-134">To resolve this issue, remove the invalid user from the corresponding bam_{viewname}view security role.</span></span>  
  
## <a name="cannot-export-or-import-a-bam-definition-to-localhost"></a><span data-ttu-id="e8633-135">Impossible d'exporter une définition BAM vers localhost ou d'en importer une depuis localhost</span><span class="sxs-lookup"><span data-stu-id="e8633-135">Cannot export or import a BAM definition to localhost</span></span>  
 <span data-ttu-id="e8633-136">Lorsque vous exportez une définition BAM dans un fichier XML, le message d'erreur suivant s'affiche si vous tentez de le faire vers localhost :</span><span class="sxs-lookup"><span data-stu-id="e8633-136">When you export a BAM definition as XML, you will see the following error message if you try to export to localhost:</span></span>  
  
 `The system cannot find the path specified.`  
  
 <span data-ttu-id="e8633-137">L'exportation d'une définition BAM vers localhost n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e8633-137">Exporting a BAM definition to localhost is not supported.</span></span> <span data-ttu-id="e8633-138">De même, l'importation d'une définition BAM à partir de localhost n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e8633-138">Similarly, importing a BAM definition from localhost is not supported.</span></span>  
  
## <a name="alerts-do-not-work-after-upgrading-sql-server-editions"></a><span data-ttu-id="e8633-139">Les alertes ne fonctionnent plus après la mise à niveau des différentes éditions de SQL Server</span><span class="sxs-lookup"><span data-stu-id="e8633-139">Alerts do not work after upgrading SQL Server editions</span></span>  
 <span data-ttu-id="e8633-140">Si vous avez mis à niveau une édition de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] vers une autre (par exemple, une édition Standard vers une édition Entreprise), les alertes BAM ne démarreront plus.</span><span class="sxs-lookup"><span data-stu-id="e8633-140">If you have upgraded from one edition of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to another edition (for example, from Standard Edition to Enterprise Edition), BAM alerts will not restart.</span></span> <span data-ttu-id="e8633-141">Pour résoudre ce problème, supprimez les alertes BAM, puis recréez-les ou mettez à niveau [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Service.</span><span class="sxs-lookup"><span data-stu-id="e8633-141">To fix this problem, either delete the BAM alerts and re-create them, or upgrade the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Service.</span></span>  
  
#### <a name="to-upgrade-the-sql-server-notification-service"></a><span data-ttu-id="e8633-142">Pour mettre à niveau SQL Server Notification Service</span><span class="sxs-lookup"><span data-stu-id="e8633-142">To upgrade the SQL Server Notification Service</span></span>  
  
1.  <span data-ttu-id="e8633-143">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2005**, puis cliquez sur **invite de commandes de Service de Notification**.</span><span class="sxs-lookup"><span data-stu-id="e8633-143">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2005**, and then click **Notification Service Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="e8633-144">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e8633-144">Type the following command at the command prompt:</span></span>  
  
     `nscontrol.exe upgrade -name <instanceName>`  
  
## <a name="objectdisposedexception-exception"></a><span data-ttu-id="e8633-145">ObjectDisposedException Exception</span><span class="sxs-lookup"><span data-stu-id="e8633-145">ObjectDisposedException Exception</span></span>  
 <span data-ttu-id="e8633-146">Si votre application utilise l’intercepteur WF BAM 3.5, vous pouvez recevoir le message d’erreur suivant : **System.ObjectDisposedException : Impossible d’accéder à un objet supprimé**.</span><span class="sxs-lookup"><span data-stu-id="e8633-146">If your application is using BAM WF 3.5 interceptor, you may receive the following error message: **System.ObjectDisposedException: Cannot access a disposed object**.</span></span> <span data-ttu-id="e8633-147">Pour plus d’informations sur ce message d’erreur, consultez [ObjectDisposedException Exception](http://go.microsoft.com/fwlink/?LinkID=195338) (http://go.microsoft.com/fwlink/?LinkID=195338).</span><span class="sxs-lookup"><span data-stu-id="e8633-147">For more information about this error message, see [ObjectDisposedException Exception](http://go.microsoft.com/fwlink/?LinkID=195338) (http://go.microsoft.com/fwlink/?LinkID=195338).</span></span>   
<span data-ttu-id="e8633-148">Pour résoudre ce problème, installez le correctif 960754 disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkID=195339](http://go.microsoft.com/fwlink/?LinkID=195339).</span><span class="sxs-lookup"><span data-stu-id="e8633-148">To resolve this issue, install the hotfix 960754 available at [http://go.microsoft.com/fwlink/?LinkID=195339](http://go.microsoft.com/fwlink/?LinkID=195339).</span></span>  
  
## <a name="workbook-has-lost-its-vba-project-activex-controls-and-other-programmability-related-features"></a><span data-ttu-id="e8633-149">Un classeur a perdu son projet VBA, ses contrôles ActiveX ainsi que d'autres fonctionnalités de programmabilité</span><span class="sxs-lookup"><span data-stu-id="e8633-149">Workbook has lost its VBA project, ActiveX controls and other programmability-related features</span></span>  
 <span data-ttu-id="e8633-150">Lorsque vous tentez d’utiliser BAM.xla dans Microsoft Excel, vous pouvez recevoir l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="e8633-150">When attempting to use BAM.xla in Microsoft Excel, you may get the following error:</span></span>  
  
 `This workbook has lost its VBA project, ActiveX controls and any other programmability-related features.`  
  
 <span data-ttu-id="e8633-151">Pour résoudre ce problème, installez le **Visual Basic pour Applications** sous **composants partagés d’Office** avec Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="e8633-151">To resolve this issue, install the **Visual Basic for Applications** option under **Office Shared Features** with Microsoft Office.</span></span>  
  
## <a name="pivot-table-fails-to-get-the-data"></a><span data-ttu-id="e8633-152">Le tableau croisé dynamique ne parvient pas à récupérer les données</span><span class="sxs-lookup"><span data-stu-id="e8633-152">Pivot table fails to get the data</span></span>  
 <span data-ttu-id="e8633-153">Vous avez reçu les autorisations pour accéder aux bases de données BAM ainsi qu'un rôle et des autorisations sur les vues déployées.</span><span class="sxs-lookup"><span data-stu-id="e8633-153">You have permissions to access BAM databases, and also role and permissions on the views which are deployed.</span></span> <span data-ttu-id="e8633-154">La page Recherche d'activité fonctionne normalement et vous pouvez consulter les données.</span><span class="sxs-lookup"><span data-stu-id="e8633-154">The Activity Search page works as expected and you can see the data.</span></span> <span data-ttu-id="e8633-155">Cependant, dans le tableau croisé dynamique, l'erreur suivante s'affiche :</span><span class="sxs-lookup"><span data-stu-id="e8633-155">But, in the Pivot table, the following error is displayed:</span></span>  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* The following system error occurred:  No connection could be made because the target machine actively refused it.  
```  
  
 <span data-ttu-id="e8633-156">Pour résoudre ce problème, ajoutez les paramètres DNS correspondants comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8633-156">To resolve this issue, add the respective DNS settings as follows:</span></span>  
  
1.  <span data-ttu-id="e8633-157">Cliquez sur **Démarrer** et accédez à **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="e8633-157">Click **Start** and go to **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="e8633-158">Cliquez sur **réseau et Internet** puis cliquez sur **connexions réseau**.</span><span class="sxs-lookup"><span data-stu-id="e8633-158">Click **Network and Internet** and then click **Network Connections**.</span></span>  
  
3.  <span data-ttu-id="e8633-159">Avec le bouton droit sur la connexion réseau (par exemple, la connexion au réseau Local), puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e8633-159">Right-click on the network connection (like Local Area Connection), and select **Properties**.</span></span>  
  
4.  <span data-ttu-id="e8633-160">Sur le **connexion au réseau Local** page, sélectionnez **Internet Protocol Version 4 (TCP/IPv4)**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e8633-160">On the **Local Area Connection** page, select **Internet Protocol Version 4 (TCP/IPv4)**, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="e8633-161">Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="e8633-161">Click **Advanced**.</span></span> <span data-ttu-id="e8633-162">Sur le **paramètres TCP/IP avancés** , cliquez sur le **DNS** onglet.</span><span class="sxs-lookup"><span data-stu-id="e8633-162">On the **Advance TCP/IP Settings** page, click the **DNS** tab.</span></span>  
  
6.  <span data-ttu-id="e8633-163">Sélectionnez **ajouter ces suffixes DNS** , puis ajoutez les suffixes DNS nécessaires.</span><span class="sxs-lookup"><span data-stu-id="e8633-163">Select **Append these DNS suffixes** and then add the required DNS suffixes.</span></span>  
  
7.  <span data-ttu-id="e8633-164">Cliquez sur **OK** et fermez toutes les fenêtres ouvertes.</span><span class="sxs-lookup"><span data-stu-id="e8633-164">Click **OK** and close all the open windows.</span></span>  
  
## <a name="pivot-table-view-shows-all-values-as-0"></a><span data-ttu-id="e8633-165">La vue du tableau croisé dynamique affiche toutes les valeurs comme étant égales à « 0 »</span><span class="sxs-lookup"><span data-stu-id="e8633-165">Pivot table view shows all values as “0”</span></span>  
 <span data-ttu-id="e8633-166">Lorsque vous déployez le portail BAM, la page Recherche d'activité affiche les résultats attendus.</span><span class="sxs-lookup"><span data-stu-id="e8633-166">When you deploy the BAM portal, the Activity Search page displays expected results.</span></span> <span data-ttu-id="e8633-167">Cependant, la vue du tableau croisé dynamique affiche toutes les valeurs comme étant égales à « 0 ».</span><span class="sxs-lookup"><span data-stu-id="e8633-167">But, the Pivot table view displays all values as “0”.</span></span> <span data-ttu-id="e8633-168">Le message d'erreur suivant s'affiche :</span><span class="sxs-lookup"><span data-stu-id="e8633-168">The following error is displayed:</span></span>  
  
```  
Failed to get data.  If available, errors returned from the provider are listed below.  
* Safety settings on this machine prohibit accessing a data source on another domain.  
```  
  
 <span data-ttu-id="e8633-169">Pour résoudre ce problème, ajoutez le site à la zone, comme suit :</span><span class="sxs-lookup"><span data-stu-id="e8633-169">To resolve this issue, add the site to the zone as follows:</span></span>  
  
1.  <span data-ttu-id="e8633-170">Dans la fenêtre Internet Explorer, cliquez sur **outils**, puis cliquez sur **Options Internet**.</span><span class="sxs-lookup"><span data-stu-id="e8633-170">In the Internet Explorer window, click **Tools**, then click **Internet Options**.</span></span> <span data-ttu-id="e8633-171">Cliquez sur le **sécurité** onglet, puis sélectionnez le **sites de confiance** zone.</span><span class="sxs-lookup"><span data-stu-id="e8633-171">Click the **Security** tab, and then select the **Trusted sites** zone.</span></span>  
  
2.  <span data-ttu-id="e8633-172">Cliquez sur **niveau personnalisé** pour définir le niveau de sécurité pour la zone.</span><span class="sxs-lookup"><span data-stu-id="e8633-172">Click **Custom level** to set the security level for the zone.</span></span>  
  
3.  <span data-ttu-id="e8633-173">Sur le **paramètres** sous le **accéder aux sources de données sur plusieurs domaines** , cliquez sur **invite**.</span><span class="sxs-lookup"><span data-stu-id="e8633-173">On the **Settings** page, under the **Access data sources across domains** option, click **Prompt**.</span></span> <span data-ttu-id="e8633-174">Une invite s'affichera lorsqu'un composant nécessite cette autorisation.</span><span class="sxs-lookup"><span data-stu-id="e8633-174">You will be prompted when a component requires this permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8633-175">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e8633-175">See Also</span></span>  
 [<span data-ttu-id="e8633-176">À l’aide de Business Activity Monitoring</span><span class="sxs-lookup"><span data-stu-id="e8633-176">Using Business Activity Monitoring</span></span>](../core/using-business-activity-monitoring.md)