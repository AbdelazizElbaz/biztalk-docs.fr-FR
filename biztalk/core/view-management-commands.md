---
title: Afficher les commandes de gestion | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f25ee3-9bb3-4682-a9ff-cac8c25f58c3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ced7a9ac58fa0375e3eaefa49832e6c23ba1a73
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="view-management-commands"></a><span data-ttu-id="aba47-102">Commandes de gestion des vues</span><span class="sxs-lookup"><span data-stu-id="aba47-102">View Management Commands</span></span>
<span data-ttu-id="aba47-103">Les commandes de gestion des vues de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser des vues déployées.</span><span class="sxs-lookup"><span data-stu-id="aba47-103">The BAM Management utility view management commands allow you to work with deployed views.</span></span>  
  
-   <span data-ttu-id="aba47-104">Get-views : répertorie toutes les vues déployées.</span><span class="sxs-lookup"><span data-stu-id="aba47-104">get-views: Lists all the deployed views.</span></span>  
  
-   <span data-ttu-id="aba47-105">Remove-view : supprime une vue déployée.</span><span class="sxs-lookup"><span data-stu-id="aba47-105">remove-view: Removes a deployed view.</span></span>  
  
-   <span data-ttu-id="aba47-106">Get-rtawindow : Obtient la durée d’une vue.</span><span class="sxs-lookup"><span data-stu-id="aba47-106">get-rtawindow: Gets the duration on a view.</span></span>  
  
-   <span data-ttu-id="aba47-107">Set-rtawindow : définit la durée d’une vue.</span><span class="sxs-lookup"><span data-stu-id="aba47-107">set-rtawindow: Sets the duration on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aba47-108">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aba47-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="aba47-109">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="aba47-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="aba47-110">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="aba47-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aba47-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="aba47-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-views-command"></a><span data-ttu-id="aba47-112">Commande get-views</span><span class="sxs-lookup"><span data-stu-id="aba47-112">get-views Command</span></span>  
 <span data-ttu-id="aba47-113">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aba47-113">**Usage**</span></span>  
  
 <span data-ttu-id="aba47-114">**BM.exe get-views [-activité :\<nom de l’activité\> ] [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aba47-114">**bm.exe get-views [ -Activity:\<activity name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aba47-115">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aba47-115">**Parameters**</span></span>  
  
|<span data-ttu-id="aba47-116">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aba47-116">Parameter</span></span>|<span data-ttu-id="aba47-117"> Description</span><span class="sxs-lookup"><span data-stu-id="aba47-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aba47-118">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="aba47-118">Activity:\<activity name\></span></span>|<span data-ttu-id="aba47-119">Nom de l'activité à partir de laquelle répertorier les vues.</span><span class="sxs-lookup"><span data-stu-id="aba47-119">The name of the activity from which to list the views.</span></span>|  
|<span data-ttu-id="aba47-120">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aba47-120">Server:\<server\></span></span>|<span data-ttu-id="aba47-121">Facultatif : Le nom du serveur à partir duquel obtenir la liste des vues.</span><span class="sxs-lookup"><span data-stu-id="aba47-121">Optional: The name of the server from which to get the list of views.</span></span> <span data-ttu-id="aba47-122">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="aba47-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="aba47-123">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aba47-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aba47-124">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aba47-124">Database:\<database\></span></span>|<span data-ttu-id="aba47-125">Facultatif : Le nom de la base de données à partir duquel obtenir la liste des vues.</span><span class="sxs-lookup"><span data-stu-id="aba47-125">Optional: The name of the database from which to get the list of views.</span></span> <span data-ttu-id="aba47-126">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aba47-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aba47-127">Répertorie les vues déployées sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="aba47-127">Lists the views deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="aba47-128">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aba47-128">**Examples**</span></span>  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-view-command"></a><span data-ttu-id="aba47-129">Commande remove-view</span><span class="sxs-lookup"><span data-stu-id="aba47-129">remove-view Command</span></span>  
 <span data-ttu-id="aba47-130">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aba47-130">**Usage**</span></span>  
  
 <span data-ttu-id="aba47-131">**BM.exe remove-view-nom :\<nom de la vue\> [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aba47-131">**bm.exe remove-view -Name:\<view name\> [ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aba47-132">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aba47-132">**Parameters**</span></span>  
  
|<span data-ttu-id="aba47-133">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aba47-133">Parameter</span></span>|<span data-ttu-id="aba47-134"> Description</span><span class="sxs-lookup"><span data-stu-id="aba47-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aba47-135">Nom :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="aba47-135">Name:\<view name\></span></span>|<span data-ttu-id="aba47-136">Nom de la vue à supprimer.</span><span class="sxs-lookup"><span data-stu-id="aba47-136">The name of the view to remove.</span></span>|  
|<span data-ttu-id="aba47-137">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aba47-137">Server:\<server\></span></span>|<span data-ttu-id="aba47-138">Facultatif : Le nom du serveur à partir duquel supprimer la vue.</span><span class="sxs-lookup"><span data-stu-id="aba47-138">Optional: The name of the server from which to remove the view.</span></span> <span data-ttu-id="aba47-139">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="aba47-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="aba47-140">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aba47-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aba47-141">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aba47-141">Database:\<database\></span></span>|<span data-ttu-id="aba47-142">Facultatif : Le nom de la base de données à partir duquel supprimer la vue.</span><span class="sxs-lookup"><span data-stu-id="aba47-142">Optional: The name of the database from which to remove the view.</span></span> <span data-ttu-id="aba47-143">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aba47-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aba47-144">Supprime la vue spécifiée de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="aba47-144">Removes the specified view from the BAM Primary Import database.</span></span> <span data-ttu-id="aba47-145">Si la vue présente des alertes dépendantes, elles sont supprimées par la même opération.</span><span class="sxs-lookup"><span data-stu-id="aba47-145">If the view has dependent alerts, they are removed at the same time.</span></span>  
  
 <span data-ttu-id="aba47-146">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aba47-146">**Examples**</span></span>  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-rtawindow-command"></a><span data-ttu-id="aba47-147">Commande get-rtawindow</span><span class="sxs-lookup"><span data-stu-id="aba47-147">get-rtawindow Command</span></span>  
 <span data-ttu-id="aba47-148">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aba47-148">**Usage**</span></span>  
  
 <span data-ttu-id="aba47-149">**BM.exe get-rtawindow-View :\<nom de la vue\> -activité :\<nom de l’activité\> -Rta :\<nom RTA\>[-Server :\<server\> ] [-base de données :\< base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aba47-149">**bm.exe get-rtawindow -View:\<view name\> -Activity:\<activity name\> -Rta:\<RTA name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aba47-150">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aba47-150">**Parameters**</span></span>  
  
|<span data-ttu-id="aba47-151">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aba47-151">Parameter</span></span>|<span data-ttu-id="aba47-152"> Description</span><span class="sxs-lookup"><span data-stu-id="aba47-152">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aba47-153">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="aba47-153">View:\<view name\></span></span>|<span data-ttu-id="aba47-154">Le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="aba47-154">The view name.</span></span>|  
|<span data-ttu-id="aba47-155">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="aba47-155">Activity:\<activity name\></span></span>|<span data-ttu-id="aba47-156">Le nom de l’activité.</span><span class="sxs-lookup"><span data-stu-id="aba47-156">The activity name.</span></span>|  
|<span data-ttu-id="aba47-157">RTA :\<nom RTA\></span><span class="sxs-lookup"><span data-stu-id="aba47-157">Rta:\<RTA name\></span></span>|<span data-ttu-id="aba47-158">Nom de l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="aba47-158">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="aba47-159">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aba47-159">Server:\<server\></span></span>|<span data-ttu-id="aba47-160">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="aba47-160">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="aba47-161">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="aba47-161">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="aba47-162">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aba47-162">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aba47-163">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aba47-163">Database:\<database\></span></span>|<span data-ttu-id="aba47-164">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="aba47-164">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="aba47-165">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aba47-165">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aba47-166">Affiche la durée de l'agrégation en temps réel spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aba47-166">Displays the duration of the specified real-time aggregation.</span></span> <span data-ttu-id="aba47-167">Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="aba47-167">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="aba47-168">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aba47-168">**Examples**</span></span>  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## <a name="set-rtawindow-command"></a><span data-ttu-id="aba47-169">Commande set-rtawindow</span><span class="sxs-lookup"><span data-stu-id="aba47-169">set-rtawindow Command</span></span>  
 <span data-ttu-id="aba47-170">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aba47-170">**Usage**</span></span>  
  
 <span data-ttu-id="aba47-171">**BM.exe set-rtawindow-View :\<nom de la vue\> -activité :\<nom de l’activité\> -nom :\<nom RTA\> - TimeLength :\<nombre entier\>- TimeUnit:Day &#124; Heure &#124; Minute [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aba47-171">**bm.exe set-rtawindow -View:\<view name\> -Activity:\<activity name\> -Name:\<RTA name\> -TimeLength:\<integer number\>-TimeUnit:Day&#124;Hour&#124;Minute[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aba47-172">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aba47-172">**Parameters**</span></span>  
  
|<span data-ttu-id="aba47-173">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aba47-173">Parameter</span></span>|<span data-ttu-id="aba47-174"> Description</span><span class="sxs-lookup"><span data-stu-id="aba47-174">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aba47-175">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="aba47-175">View:\<view name\></span></span>|<span data-ttu-id="aba47-176">Le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="aba47-176">The view name.</span></span>|  
|<span data-ttu-id="aba47-177">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="aba47-177">Activity:\<activity name\></span></span>|<span data-ttu-id="aba47-178">Le nom de l’activité.</span><span class="sxs-lookup"><span data-stu-id="aba47-178">The activity name.</span></span>|  
|<span data-ttu-id="aba47-179">Nom :\<nom RTA\></span><span class="sxs-lookup"><span data-stu-id="aba47-179">Name:\<RTA name\></span></span>|<span data-ttu-id="aba47-180">Nom de l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="aba47-180">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="aba47-181">TimeLength :\<nombre entier\></span><span class="sxs-lookup"><span data-stu-id="aba47-181">TimeLength:\<integer number\></span></span>|<span data-ttu-id="aba47-182">Durée de l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="aba47-182">The duration for the real-time aggregation.</span></span>|  
|<span data-ttu-id="aba47-183">TimeUnit:Month &#124; jour &#124; Heure &#124; Minute</span><span class="sxs-lookup"><span data-stu-id="aba47-183">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="aba47-184">Unité de mesure pour la durée de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="aba47-184">The unit measure for the window duration.</span></span>|  
|<span data-ttu-id="aba47-185">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aba47-185">Server:\<server\></span></span>|<span data-ttu-id="aba47-186">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="aba47-186">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="aba47-187">Le serveur doit être dans le même domaine que l’ordinateur à partir duquel vous exécutez bm.exe.</span><span class="sxs-lookup"><span data-stu-id="aba47-187">The server must be in the same domain as the machine from which you are running bm.exe.</span></span> <span data-ttu-id="aba47-188">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aba47-188">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aba47-189">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aba47-189">Database:\<database\></span></span>|<span data-ttu-id="aba47-190">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="aba47-190">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="aba47-191">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aba47-191">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aba47-192">Définit la durée pour l'agrégation en temps réel spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aba47-192">Sets the duration for the specified real-time aggregation.</span></span>  
  
 <span data-ttu-id="aba47-193">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aba47-193">**Examples**</span></span>  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## <a name="see-also"></a><span data-ttu-id="aba47-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aba47-194">See Also</span></span>  
 [<span data-ttu-id="aba47-195">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="aba47-195">BAM Management Utility</span></span>](../core/bam-management-utility.md)