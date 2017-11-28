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
ms.openlocfilehash: 4b0a641c6d461d02f8db3e0fb0112321e0657e44
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="view-management-commands"></a><span data-ttu-id="b41de-102">Commandes de gestion des vues</span><span class="sxs-lookup"><span data-stu-id="b41de-102">View Management Commands</span></span>
<span data-ttu-id="b41de-103">Les commandes de gestion des vues de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser des vues déployées.</span><span class="sxs-lookup"><span data-stu-id="b41de-103">The BAM Management utility view management commands allow you to work with deployed views.</span></span>  
  
-   <span data-ttu-id="b41de-104">Get-views : répertorie toutes les vues déployées.</span><span class="sxs-lookup"><span data-stu-id="b41de-104">get-views: Lists all the deployed views.</span></span>  
  
-   <span data-ttu-id="b41de-105">Remove-view : supprime une vue déployée.</span><span class="sxs-lookup"><span data-stu-id="b41de-105">remove-view: Removes a deployed view.</span></span>  
  
-   <span data-ttu-id="b41de-106">Get-rtawindow : Obtient la durée d’une vue.</span><span class="sxs-lookup"><span data-stu-id="b41de-106">get-rtawindow: Gets the duration on a view.</span></span>  
  
-   <span data-ttu-id="b41de-107">Set-rtawindow : définit la durée d’une vue.</span><span class="sxs-lookup"><span data-stu-id="b41de-107">set-rtawindow: Sets the duration on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b41de-108">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b41de-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="b41de-109">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b41de-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="b41de-110">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="b41de-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b41de-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b41de-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-views-command"></a><span data-ttu-id="b41de-112">Commande get-views</span><span class="sxs-lookup"><span data-stu-id="b41de-112">get-views Command</span></span>  
 <span data-ttu-id="b41de-113">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b41de-113">**Usage**</span></span>  
  
 <span data-ttu-id="b41de-114">**BM.exe get-views [-activité :\<nom de l’activité >] [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="b41de-114">**bm.exe get-views [ -Activity:\<activity name> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b41de-115">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b41de-115">**Parameters**</span></span>  
  
|<span data-ttu-id="b41de-116">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b41de-116">Parameter</span></span>|<span data-ttu-id="b41de-117"> Description</span><span class="sxs-lookup"><span data-stu-id="b41de-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b41de-118">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="b41de-118">Activity:\<activity name></span></span>|<span data-ttu-id="b41de-119">Nom de l'activité à partir de laquelle répertorier les vues.</span><span class="sxs-lookup"><span data-stu-id="b41de-119">The name of the activity from which to list the views.</span></span>|  
|<span data-ttu-id="b41de-120">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="b41de-120">Server:\<server></span></span>|<span data-ttu-id="b41de-121">Facultatif : Le nom du serveur à partir duquel obtenir la liste des vues.</span><span class="sxs-lookup"><span data-stu-id="b41de-121">Optional: The name of the server from which to get the list of views.</span></span> <span data-ttu-id="b41de-122">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b41de-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b41de-123">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b41de-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b41de-124">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="b41de-124">Database:\<database></span></span>|<span data-ttu-id="b41de-125">Facultatif : Le nom de la base de données à partir duquel obtenir la liste des vues.</span><span class="sxs-lookup"><span data-stu-id="b41de-125">Optional: The name of the database from which to get the list of views.</span></span> <span data-ttu-id="b41de-126">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b41de-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b41de-127">Répertorie les vues déployées sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="b41de-127">Lists the views deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="b41de-128">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b41de-128">**Examples**</span></span>  
  
```  
bm.exe get-views -Activity:PO1  
bm.exe get-views -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-view-command"></a><span data-ttu-id="b41de-129">Commande remove-view</span><span class="sxs-lookup"><span data-stu-id="b41de-129">remove-view Command</span></span>  
 <span data-ttu-id="b41de-130">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b41de-130">**Usage**</span></span>  
  
 <span data-ttu-id="b41de-131">**BM.exe remove-view-nom :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="b41de-131">**bm.exe remove-view -Name:\<view name> [ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b41de-132">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b41de-132">**Parameters**</span></span>  
  
|<span data-ttu-id="b41de-133">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b41de-133">Parameter</span></span>|<span data-ttu-id="b41de-134"> Description</span><span class="sxs-lookup"><span data-stu-id="b41de-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b41de-135">Nom :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="b41de-135">Name:\<view name></span></span>|<span data-ttu-id="b41de-136">Nom de la vue à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b41de-136">The name of the view to remove.</span></span>|  
|<span data-ttu-id="b41de-137">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="b41de-137">Server:\<server></span></span>|<span data-ttu-id="b41de-138">Facultatif : Le nom du serveur à partir duquel supprimer la vue.</span><span class="sxs-lookup"><span data-stu-id="b41de-138">Optional: The name of the server from which to remove the view.</span></span> <span data-ttu-id="b41de-139">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b41de-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b41de-140">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b41de-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b41de-141">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="b41de-141">Database:\<database></span></span>|<span data-ttu-id="b41de-142">Facultatif : Le nom de la base de données à partir duquel supprimer la vue.</span><span class="sxs-lookup"><span data-stu-id="b41de-142">Optional: The name of the database from which to remove the view.</span></span> <span data-ttu-id="b41de-143">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b41de-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b41de-144">Supprime la vue spécifiée de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="b41de-144">Removes the specified view from the BAM Primary Import database.</span></span> <span data-ttu-id="b41de-145">Si la vue présente des alertes dépendantes, elles sont supprimées par la même opération.</span><span class="sxs-lookup"><span data-stu-id="b41de-145">If the view has dependent alerts, they are removed at the same time.</span></span>  
  
 <span data-ttu-id="b41de-146">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b41de-146">**Examples**</span></span>  
  
```  
bm.exe remove-view -Name:POView  
bm.exe remove-view -Name:MyView -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-rtawindow-command"></a><span data-ttu-id="b41de-147">Commande get-rtawindow</span><span class="sxs-lookup"><span data-stu-id="b41de-147">get-rtawindow Command</span></span>  
 <span data-ttu-id="b41de-148">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b41de-148">**Usage**</span></span>  
  
 <span data-ttu-id="b41de-149">**BM.exe get-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité > -Rta :\<nom RTA > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="b41de-149">**bm.exe get-rtawindow -View:\<view name> -Activity:\<activity name> -Rta:\<RTA name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b41de-150">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b41de-150">**Parameters**</span></span>  
  
|<span data-ttu-id="b41de-151">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b41de-151">Parameter</span></span>|<span data-ttu-id="b41de-152"> Description</span><span class="sxs-lookup"><span data-stu-id="b41de-152">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b41de-153">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="b41de-153">View:\<view name></span></span>|<span data-ttu-id="b41de-154">Le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="b41de-154">The view name.</span></span>|  
|<span data-ttu-id="b41de-155">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="b41de-155">Activity:\<activity name></span></span>|<span data-ttu-id="b41de-156">Le nom de l’activité.</span><span class="sxs-lookup"><span data-stu-id="b41de-156">The activity name.</span></span>|  
|<span data-ttu-id="b41de-157">RTA :\<nom RTA ></span><span class="sxs-lookup"><span data-stu-id="b41de-157">Rta:\<RTA name></span></span>|<span data-ttu-id="b41de-158">Nom de l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="b41de-158">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="b41de-159">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="b41de-159">Server:\<server></span></span>|<span data-ttu-id="b41de-160">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="b41de-160">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="b41de-161">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b41de-161">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b41de-162">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b41de-162">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b41de-163">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="b41de-163">Database:\<database></span></span>|<span data-ttu-id="b41de-164">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="b41de-164">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="b41de-165">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b41de-165">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b41de-166">Affiche la durée de l'agrégation en temps réel spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b41de-166">Displays the duration of the specified real-time aggregation.</span></span> <span data-ttu-id="b41de-167">Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="b41de-167">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="b41de-168">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b41de-168">**Examples**</span></span>  
  
```  
bm.exe get-rtawindow -View:ManagerView -Activity:PO -Rta:Rta1  
bm.exe get-rtawindow -View:V1 -Activity:A2 -Rta:R3 -Server:S1 -Database:BamPI  
```  
  
## <a name="set-rtawindow-command"></a><span data-ttu-id="b41de-169">Commande set-rtawindow</span><span class="sxs-lookup"><span data-stu-id="b41de-169">set-rtawindow Command</span></span>  
 <span data-ttu-id="b41de-170">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b41de-170">**Usage**</span></span>  
  
 <span data-ttu-id="b41de-171">**BM.exe set-rtawindow-View :\<nom de la vue >-activité :\<nom de l’activité >-nom :\<nom RTA > - TimeLength :\<nombre entier >-TimeUnit:Day &#124; Heure &#124; Minute [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="b41de-171">**bm.exe set-rtawindow -View:\<view name> -Activity:\<activity name> -Name:\<RTA name> -TimeLength:\<integer number>-TimeUnit:Day&#124;Hour&#124;Minute[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="b41de-172">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b41de-172">**Parameters**</span></span>  
  
|<span data-ttu-id="b41de-173">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b41de-173">Parameter</span></span>|<span data-ttu-id="b41de-174"> Description</span><span class="sxs-lookup"><span data-stu-id="b41de-174">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b41de-175">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="b41de-175">View:\<view name></span></span>|<span data-ttu-id="b41de-176">Le nom de la vue.</span><span class="sxs-lookup"><span data-stu-id="b41de-176">The view name.</span></span>|  
|<span data-ttu-id="b41de-177">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="b41de-177">Activity:\<activity name></span></span>|<span data-ttu-id="b41de-178">Le nom de l’activité.</span><span class="sxs-lookup"><span data-stu-id="b41de-178">The activity name.</span></span>|  
|<span data-ttu-id="b41de-179">Nom :\<nom RTA ></span><span class="sxs-lookup"><span data-stu-id="b41de-179">Name:\<RTA name></span></span>|<span data-ttu-id="b41de-180">Nom de l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="b41de-180">The real-time aggregation name.</span></span>|  
|<span data-ttu-id="b41de-181">TimeLength :\<nombre entier ></span><span class="sxs-lookup"><span data-stu-id="b41de-181">TimeLength:\<integer number></span></span>|<span data-ttu-id="b41de-182">Durée de l'agrégation en temps réel.</span><span class="sxs-lookup"><span data-stu-id="b41de-182">The duration for the real-time aggregation.</span></span>|  
|<span data-ttu-id="b41de-183">TimeUnit:Month &#124; jour &#124; Heure &#124; Minute</span><span class="sxs-lookup"><span data-stu-id="b41de-183">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="b41de-184">Unité de mesure pour la durée de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b41de-184">The unit measure for the window duration.</span></span>|  
|<span data-ttu-id="b41de-185">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="b41de-185">Server:\<server></span></span>|<span data-ttu-id="b41de-186">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="b41de-186">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="b41de-187">Le serveur doit être dans le même domaine que l’ordinateur à partir duquel vous exécutez bm.exe.</span><span class="sxs-lookup"><span data-stu-id="b41de-187">The server must be in the same domain as the machine from which you are running bm.exe.</span></span> <span data-ttu-id="b41de-188">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b41de-188">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b41de-189">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="b41de-189">Database:\<database></span></span>|<span data-ttu-id="b41de-190">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="b41de-190">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="b41de-191">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b41de-191">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b41de-192">Définit la durée pour l'agrégation en temps réel spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b41de-192">Sets the duration for the specified real-time aggregation.</span></span>  
  
 <span data-ttu-id="b41de-193">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b41de-193">**Examples**</span></span>  
  
```  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:5 -TimeUnit:Minute  
bm.exe set-rtawindow -View:V -Activity:A -Name:R -TimeLength:1 -TimeUnit:Hour  
```  
  
## <a name="see-also"></a><span data-ttu-id="b41de-194">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b41de-194">See Also</span></span>  
 [<span data-ttu-id="b41de-195">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="b41de-195">BAM Management Utility</span></span>](../core/bam-management-utility.md)