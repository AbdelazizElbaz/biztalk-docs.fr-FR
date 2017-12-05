---
title: "Commandes de gestion des activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34db54f3-4116-49de-880b-c9891a38d2e7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18caccaf5207b5a63d0272c5d9e0277270c3e04c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="activity-management-commands"></a><span data-ttu-id="38250-102">Commandes de gestion des activités</span><span class="sxs-lookup"><span data-stu-id="38250-102">Activity Management Commands</span></span>
<span data-ttu-id="38250-103">Les commandes de gestion des activités de l'utilitaire de gestion de l'analyse BAM permettent de travailler avec des activités déployées.</span><span class="sxs-lookup"><span data-stu-id="38250-103">The BAM Management utility activity management commands allow you to work with deployed activities.</span></span>  
  
-   <span data-ttu-id="38250-104">Get-activities : Obtient une liste des activités déployées.</span><span class="sxs-lookup"><span data-stu-id="38250-104">get-activities: Gets a list of deployed activities.</span></span>  
  
-   <span data-ttu-id="38250-105">Remove-activity : supprime une activité.</span><span class="sxs-lookup"><span data-stu-id="38250-105">remove-activity: Removes an activity.</span></span>  
  
-   <span data-ttu-id="38250-106">Get-activitywindow : Obtient la durée d’une activité.</span><span class="sxs-lookup"><span data-stu-id="38250-106">get-activitywindow: Gets the duration for an activity.</span></span>  
  
-   <span data-ttu-id="38250-107">Set-activitywindow : définit la durée d’une activité.</span><span class="sxs-lookup"><span data-stu-id="38250-107">set-activitywindow: Sets the activity duration for an activity.</span></span>  
  
-   <span data-ttu-id="38250-108">Get-index : Obtient la liste des index.</span><span class="sxs-lookup"><span data-stu-id="38250-108">get-index: Gets the list of indexes.</span></span>  
  
-   <span data-ttu-id="38250-109">créer des index : crée un nouvel index.</span><span class="sxs-lookup"><span data-stu-id="38250-109">create-index: Creates a new index.</span></span>  
  
-   <span data-ttu-id="38250-110">index de la suppression : supprime un index.</span><span class="sxs-lookup"><span data-stu-id="38250-110">delete-index: Deletes an index.</span></span>  
  
-   <span data-ttu-id="38250-111">Get-archive : Obtient le comportement de l’activité archivée.</span><span class="sxs-lookup"><span data-stu-id="38250-111">get-archive: Gets the behavior of archived activity.</span></span>  
  
-   <span data-ttu-id="38250-112">Set-archive : définit le comportement de l’activité archivée.</span><span class="sxs-lookup"><span data-stu-id="38250-112">set-archive: Sets the behavior of archived activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38250-113">Vous pouvez activer le suivi de n’importe quelle commande d’utilitaire BAM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="38250-113">You can enable tracing on any BAM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="38250-114">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="38250-114">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="38250-115">L'option peut être utilisée conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="38250-115">The switch can be used in conjunction with any normal BAM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38250-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="38250-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-activities-command"></a><span data-ttu-id="38250-117">Commande get-activities</span><span class="sxs-lookup"><span data-stu-id="38250-117">get-activities Command</span></span>  
 <span data-ttu-id="38250-118">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-118">**Usage**</span></span>  
  
 <span data-ttu-id="38250-119">**BM.exe get-activities [-View :\<nom de la vue\> ] [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-119">**bm.exe get-activities [ -View:\<view name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-120">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-120">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-121">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-121">Parameter</span></span>|<span data-ttu-id="38250-122"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-123">Nom :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-123">Name:\<activity name\></span></span>|<span data-ttu-id="38250-124">Nom de l'activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="38250-124">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="38250-125">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-125">Server:\<server\></span></span>|<span data-ttu-id="38250-126">Facultatif : Le nom du serveur à partir duquel obtenir la liste des activités.</span><span class="sxs-lookup"><span data-stu-id="38250-126">Optional: The name of the server from which to get the list of activities.</span></span> <span data-ttu-id="38250-127">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-127">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-128">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-128">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-129">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-129">Database:\<database\></span></span>|<span data-ttu-id="38250-130">Facultatif : Le nom de la base de données à partir duquel obtenir la liste des activités.</span><span class="sxs-lookup"><span data-stu-id="38250-130">Optional: The name of the database from which to get the list of activities.</span></span> <span data-ttu-id="38250-131">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-131">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-132">Répertorie les activités déployées sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="38250-132">Lists the activities deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="38250-133">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-133">**Examples**</span></span>  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-activity-command"></a><span data-ttu-id="38250-134">Commande remove-activity</span><span class="sxs-lookup"><span data-stu-id="38250-134">remove-activity Command</span></span>  
 <span data-ttu-id="38250-135">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-135">**Usage**</span></span>  
  
 <span data-ttu-id="38250-136">**BM.exe remove-activity-nom :\<nom de l’activité\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-136">**bm.exe remove-activity -Name:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-137">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-137">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-138">Parameter</span></span>|<span data-ttu-id="38250-139"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-140">Nom :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-140">Name:\<activity name\></span></span>|<span data-ttu-id="38250-141">Nom de l'activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="38250-141">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="38250-142">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-142">Server:\<server\></span></span>|<span data-ttu-id="38250-143">Facultatif : Le nom du serveur à partir duquel l’activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="38250-143">Optional: The name of the server from which to remove the activity.</span></span> <span data-ttu-id="38250-144">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-144">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-145">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-145">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-146">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-146">Database:\<database\></span></span>|<span data-ttu-id="38250-147">Facultatif : Le nom de la base de données à partir duquel l’activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="38250-147">Optional: The name of the database from which to remove the activity.</span></span> <span data-ttu-id="38250-148">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-148">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-149">Supprime l'activité spécifiée de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="38250-149">Removes the specified activity from the BAM Primary Import database.</span></span> <span data-ttu-id="38250-150">Si l'activité comporte des vues dépendantes, la commande échoue et renvoie une erreur.</span><span class="sxs-lookup"><span data-stu-id="38250-150">If the activity has dependent views, the command will fail and report an error.</span></span> <span data-ttu-id="38250-151">Utilisez alors la commande remove-view pour supprimer toutes les vues dépendantes, puis réexécutez la commande remove-activity.</span><span class="sxs-lookup"><span data-stu-id="38250-151">Use the remove-view command to remove all the dependent views and execute the remove-activity command again.</span></span>  
  
 <span data-ttu-id="38250-152">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-152">**Examples**</span></span>  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-activitywindow-command"></a><span data-ttu-id="38250-153">Commande get-activitywindow</span><span class="sxs-lookup"><span data-stu-id="38250-153">get-activitywindow Command</span></span>  
 <span data-ttu-id="38250-154">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-154">**Usage**</span></span>  
  
 <span data-ttu-id="38250-155">**BM.exe get-activitywindow-activité :\<nom de l’activité\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-155">**bm.exe get-activitywindow -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-156">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-156">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-157">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-157">Parameter</span></span>|<span data-ttu-id="38250-158"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-158">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-159">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-159">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-160">Le nom de la .activity.</span><span class="sxs-lookup"><span data-stu-id="38250-160">The name of the .activity.</span></span>|  
|<span data-ttu-id="38250-161">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-161">Server:\<server\></span></span>|<span data-ttu-id="38250-162">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-162">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-163">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-163">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-164">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-164">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-165">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-165">Database:\<database\></span></span>|<span data-ttu-id="38250-166">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-166">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-167">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-167">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-168">Affiche la durée pour l'activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38250-168">Displays the duration for the specified activity.</span></span> <span data-ttu-id="38250-169">Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="38250-169">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="38250-170">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-170">**Examples**</span></span>  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="set-activitywindow-command"></a><span data-ttu-id="38250-171">Commande set-activitywindow</span><span class="sxs-lookup"><span data-stu-id="38250-171">set-activitywindow Command</span></span>  
 <span data-ttu-id="38250-172">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-172">**Usage**</span></span>  
  
 <span data-ttu-id="38250-173">**BM.exe set-activitywindow-activité :\<nom de l’activité\> - TimeLength :\<nombre entier\> - TimeUnit : mois &#124; jour &#124; Heure &#124; Minute [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-173">**bm.exe set-activitywindow -Activity:\<activity name\> -TimeLength:\<integer number\> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-174">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-174">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-175">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-175">Parameter</span></span>|<span data-ttu-id="38250-176"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-176">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-177">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-177">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-178">Nom de l'activité.</span><span class="sxs-lookup"><span data-stu-id="38250-178">The name of the activity.</span></span>|  
|<span data-ttu-id="38250-179">TimeLength :\<nombre entier\></span><span class="sxs-lookup"><span data-stu-id="38250-179">TimeLength:\<integer number\></span></span>|<span data-ttu-id="38250-180">Durée de l'activité.</span><span class="sxs-lookup"><span data-stu-id="38250-180">The duration for the activity.</span></span>|  
|<span data-ttu-id="38250-181">TimeUnit:Month &#124; jour &#124; Heure &#124; Minute</span><span class="sxs-lookup"><span data-stu-id="38250-181">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="38250-182">Unité de mesure de la durée.</span><span class="sxs-lookup"><span data-stu-id="38250-182">The unit measure for the duration.</span></span>|  
|<span data-ttu-id="38250-183">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-183">Server:\<server\></span></span>|<span data-ttu-id="38250-184">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-184">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-185">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-185">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-186">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-186">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-187">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-187">Database:\<database\></span></span>|<span data-ttu-id="38250-188">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-188">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-189">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-189">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-190">Définit la durée pour l'activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38250-190">Sets the duration for the specified activity.</span></span>  
  
 <span data-ttu-id="38250-191">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-191">**Examples**</span></span>  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## <a name="get-index-command"></a><span data-ttu-id="38250-192">Commande get-index</span><span class="sxs-lookup"><span data-stu-id="38250-192">get-index Command</span></span>  
 <span data-ttu-id="38250-193">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-193">**Usage**</span></span>  
  
 <span data-ttu-id="38250-194">**BM.exe get-index-activité :\<nom de l’activité\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-194">**bm.exe get-index -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-195">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-195">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-196">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-196">Parameter</span></span>|<span data-ttu-id="38250-197"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-197">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-198">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-198">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-199">Nom de l'activité.</span><span class="sxs-lookup"><span data-stu-id="38250-199">The name of the activity.</span></span>|  
|<span data-ttu-id="38250-200">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-200">Server:\<server\></span></span>|<span data-ttu-id="38250-201">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-201">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-202">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-202">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-203">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-203">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-204">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-204">Database:\<database\></span></span>|<span data-ttu-id="38250-205">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-205">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-206">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-206">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-207">Répertorie tous les index qui ont été créés pour l'activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38250-207">Lists all the indexes that have been created for the specified activity.</span></span>  
  
 <span data-ttu-id="38250-208">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-208">**Examples**</span></span>  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="create-index-command"></a><span data-ttu-id="38250-209">Commande create-index</span><span class="sxs-lookup"><span data-stu-id="38250-209">create-index Command</span></span>  
 <span data-ttu-id="38250-210">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-210">**Usage**</span></span>  
  
 <span data-ttu-id="38250-211">**BM.exe create-index - IndexName :\<nom de l’index\> -activité :\<nom de l’activité\> -point de contrôle :\<point de contrôle 1\>[,\<point de contrôle 2\>...] [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-211">**bm.exe create-index -IndexName:\<index name\> -Activity:\<activity name\> -Checkpoint:\<checkpoint1\>[,\<checkpoint2\>...][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-212">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-212">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-213">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-213">Parameter</span></span>|<span data-ttu-id="38250-214"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-214">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-215">IndexName :\<nom de l’index\></span><span class="sxs-lookup"><span data-stu-id="38250-215">IndexName:\<index name\></span></span>|<span data-ttu-id="38250-216">Nom du nouvel index.</span><span class="sxs-lookup"><span data-stu-id="38250-216">The name of the new index.</span></span>|  
|<span data-ttu-id="38250-217">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-217">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-218">Nom de l'activité pour laquelle l'index est créé.</span><span class="sxs-lookup"><span data-stu-id="38250-218">The name of the activity for which the index is created.</span></span>|  
|<span data-ttu-id="38250-219">Point de contrôle :\<point de contrôle 1\>[,\<point de contrôle 2\>...]</span><span class="sxs-lookup"><span data-stu-id="38250-219">Checkpoint:\<checkpoint1\>[,\<checkpoint2\>...]</span></span>|<span data-ttu-id="38250-220">Liste de points de contrôle délimités par des virgules pour l'index.</span><span class="sxs-lookup"><span data-stu-id="38250-220">A comma-delimited list of checkpoints for the index.</span></span>|  
|<span data-ttu-id="38250-221">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-221">Server:\<server\></span></span>|<span data-ttu-id="38250-222">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-222">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-223">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-223">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-224">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-224">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-225">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-225">Database:\<database\></span></span>|<span data-ttu-id="38250-226">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-226">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-227">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-227">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-228">Crée un index pour l'activité spécifiée en utilisant les points de contrôle spécifiés.</span><span class="sxs-lookup"><span data-stu-id="38250-228">Creates an index for the specified activity using the specified checkpoints.</span></span>  
  
 <span data-ttu-id="38250-229">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-229">**Examples**</span></span>  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## <a name="delete-index-command"></a><span data-ttu-id="38250-230">Commande delete-index</span><span class="sxs-lookup"><span data-stu-id="38250-230">delete-index Command</span></span>  
 <span data-ttu-id="38250-231">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-231">**Usage**</span></span>  
  
 <span data-ttu-id="38250-232">**BM.exe delete-index - IndexName :\<nom de l’index\> -activité :\<nom de l’activité\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="38250-232">**bm.exe delete-index -IndexName:\<index name\> -Activity:\<activity name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="38250-233">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-233">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-234">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-234">Parameter</span></span>|<span data-ttu-id="38250-235"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-235">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-236">IndexName :\<nom de l’index\></span><span class="sxs-lookup"><span data-stu-id="38250-236">IndexName:\<index name\></span></span>|<span data-ttu-id="38250-237">Le nom de l’index à supprimer.</span><span class="sxs-lookup"><span data-stu-id="38250-237">The name of the index to delete.</span></span>|  
|<span data-ttu-id="38250-238">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-238">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-239">Nom de l'activité pour laquelle l'index est supprimé.</span><span class="sxs-lookup"><span data-stu-id="38250-239">The name of the activity for which the index is deleted.</span></span>|  
|<span data-ttu-id="38250-240">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-240">Server:\<server\></span></span>|<span data-ttu-id="38250-241">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-241">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-242">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-242">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-243">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-243">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-244">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-244">Database:\<database\></span></span>|<span data-ttu-id="38250-245">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-245">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-246">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-246">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-247">Supprime de l'activité indiquée l'index spécifié à l'aide du nom indiqué.</span><span class="sxs-lookup"><span data-stu-id="38250-247">Deletes the specified index with the given name from the specified activity.</span></span>  
  
 <span data-ttu-id="38250-248">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-248">**Examples**</span></span>  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="38250-249">Commande set-archive</span><span class="sxs-lookup"><span data-stu-id="38250-249">set-archive Command</span></span>  
 <span data-ttu-id="38250-250">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-250">**Usage**</span></span>  
  
 <span data-ttu-id="38250-251">**BM.exe get-archive-activité :\<activité\> [-Server :\<server\>] [-base de données :\<base de données\>]**</span><span class="sxs-lookup"><span data-stu-id="38250-251">**bm.exe get-archive -Activity:\<activity\> [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="38250-252">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-252">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-253">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-253">Parameter</span></span>|<span data-ttu-id="38250-254"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-254">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-255">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-255">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-256">Nom de l’activité pour laquelle le comportement doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="38250-256">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="38250-257">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-257">Server:\<server\></span></span>|<span data-ttu-id="38250-258">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-258">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-259">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-259">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-260">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-260">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-261">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-261">Database:\<database\></span></span>|<span data-ttu-id="38250-262">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-262">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-263">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-263">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-264">Obtient le comportement du package d’archivage de l’activité spécifiée, qu’il archive ou qu’il supprime les données de l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-264">Gets the behavior of the archiving package for the specified activity, whether the archiving package will archive orpurge activity data.</span></span>  
  
 <span data-ttu-id="38250-265">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-265">**Examples**</span></span>  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="38250-266">Commande set-archive</span><span class="sxs-lookup"><span data-stu-id="38250-266">set-archive Command</span></span>  
 <span data-ttu-id="38250-267">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="38250-267">**Usage**</span></span>  
  
 <span data-ttu-id="38250-268">**BM.exe set-archive - activité :\<activité\> - ShouldArchive : True [-Server :\<server\>] [-base de données :\<base de données\>]**</span><span class="sxs-lookup"><span data-stu-id="38250-268">**bm.exe set-archive -Activity:\<activity\> -ShouldArchive:True [-Server:\<server\>] [-Database:\<database\>]**</span></span>  
  
 <span data-ttu-id="38250-269">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="38250-269">**Parameters**</span></span>  
  
|<span data-ttu-id="38250-270">Paramètre</span><span class="sxs-lookup"><span data-stu-id="38250-270">Parameter</span></span>|<span data-ttu-id="38250-271"> Description</span><span class="sxs-lookup"><span data-stu-id="38250-271">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38250-272">Activité :\<nom de l’activité\></span><span class="sxs-lookup"><span data-stu-id="38250-272">Activity:\<activity name\></span></span>|<span data-ttu-id="38250-273">Nom de l’activité pour laquelle le comportement doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="38250-273">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="38250-274">ShouldArchive : True</span><span class="sxs-lookup"><span data-stu-id="38250-274">ShouldArchive: True</span></span>|<span data-ttu-id="38250-275">Si ce paramètre a la valeur True, l’activité est déplacée dans la base de données d’archivage.</span><span class="sxs-lookup"><span data-stu-id="38250-275">If set to True, the activity is moved to Archive DB.</span></span> <span data-ttu-id="38250-276">En revanche, s’il a la valeur False, l’activité est supprimée.</span><span class="sxs-lookup"><span data-stu-id="38250-276">If set to False, the activity is purged.</span></span>|  
|<span data-ttu-id="38250-277">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="38250-277">Server:\<server\></span></span>|<span data-ttu-id="38250-278">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-278">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="38250-279">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="38250-279">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="38250-280">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="38250-280">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="38250-281">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="38250-281">Database:\<database\></span></span>|<span data-ttu-id="38250-282">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="38250-282">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="38250-283">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="38250-283">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="38250-284">Définit le comportement du package d’archivage de l’activité spécifiée pour que les données de cette dernière soient déplacées dans la base de donnés d’archivage.</span><span class="sxs-lookup"><span data-stu-id="38250-284">Sets the behavior of the archiving package for the activity specified so that activity data is moved into the Archive DB.</span></span> <span data-ttu-id="38250-285">Par défaut, ce comportement est défini pour les nouvelles activités déployées.</span><span class="sxs-lookup"><span data-stu-id="38250-285">By default, this behavior is set for new activities that are deployed.</span></span>  
  
 <span data-ttu-id="38250-286">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="38250-286">**Examples**</span></span>  
  
 <span data-ttu-id="38250-287">Pour purger les données de l’activité BAM, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="38250-287">To purge the BAM activity data, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 <span data-ttu-id="38250-288">Pour déplacer les données de l’activité BAM vers la base de données d’archivage BAM, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="38250-288">To move the BAM activity data to the BAMArchive database, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## <a name="see-also"></a><span data-ttu-id="38250-289">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38250-289">See Also</span></span>  
 [<span data-ttu-id="38250-290">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="38250-290">BAM Management Utility</span></span>](../core/bam-management-utility.md)