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
ms.openlocfilehash: d90c5f394ed32b68f4f9b747c580fac02e22a8ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-management-commands"></a><span data-ttu-id="d0457-102">Commandes de gestion des activités</span><span class="sxs-lookup"><span data-stu-id="d0457-102">Activity Management Commands</span></span>
<span data-ttu-id="d0457-103">Les commandes de gestion des activités de l'utilitaire de gestion de l'analyse BAM permettent de travailler avec des activités déployées.</span><span class="sxs-lookup"><span data-stu-id="d0457-103">The BAM Management utility activity management commands allow you to work with deployed activities.</span></span>  
  
-   <span data-ttu-id="d0457-104">Get-activities : Obtient une liste des activités déployées.</span><span class="sxs-lookup"><span data-stu-id="d0457-104">get-activities: Gets a list of deployed activities.</span></span>  
  
-   <span data-ttu-id="d0457-105">Remove-activity : supprime une activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-105">remove-activity: Removes an activity.</span></span>  
  
-   <span data-ttu-id="d0457-106">Get-activitywindow : Obtient la durée d’une activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-106">get-activitywindow: Gets the duration for an activity.</span></span>  
  
-   <span data-ttu-id="d0457-107">Set-activitywindow : définit la durée d’une activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-107">set-activitywindow: Sets the activity duration for an activity.</span></span>  
  
-   <span data-ttu-id="d0457-108">Get-index : Obtient la liste des index.</span><span class="sxs-lookup"><span data-stu-id="d0457-108">get-index: Gets the list of indexes.</span></span>  
  
-   <span data-ttu-id="d0457-109">créer des index : crée un nouvel index.</span><span class="sxs-lookup"><span data-stu-id="d0457-109">create-index: Creates a new index.</span></span>  
  
-   <span data-ttu-id="d0457-110">index de la suppression : supprime un index.</span><span class="sxs-lookup"><span data-stu-id="d0457-110">delete-index: Deletes an index.</span></span>  
  
-   <span data-ttu-id="d0457-111">Get-archive : Obtient le comportement de l’activité archivée.</span><span class="sxs-lookup"><span data-stu-id="d0457-111">get-archive: Gets the behavior of archived activity.</span></span>  
  
-   <span data-ttu-id="d0457-112">Set-archive : définit le comportement de l’activité archivée.</span><span class="sxs-lookup"><span data-stu-id="d0457-112">set-archive: Sets the behavior of archived activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0457-113">Vous pouvez activer le suivi de n’importe quelle commande d’utilitaire BAM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="d0457-113">You can enable tracing on any BAM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="d0457-114">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d0457-114">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="d0457-115">L'option peut être utilisée conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="d0457-115">The switch can be used in conjunction with any normal BAM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d0457-116">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="d0457-116">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-activities-command"></a><span data-ttu-id="d0457-117">Commande get-activities</span><span class="sxs-lookup"><span data-stu-id="d0457-117">get-activities Command</span></span>  
 <span data-ttu-id="d0457-118">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-118">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-119">**BM.exe get-activities [-View :\<nom de la vue >] [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-119">**bm.exe get-activities [ -View:\<view name> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-120">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-120">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-121">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-121">Parameter</span></span>|<span data-ttu-id="d0457-122"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-123">Nom :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-123">Name:\<activity name></span></span>|<span data-ttu-id="d0457-124">Nom de l'activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d0457-124">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="d0457-125">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-125">Server:\<server></span></span>|<span data-ttu-id="d0457-126">Facultatif : Le nom du serveur à partir duquel obtenir la liste des activités.</span><span class="sxs-lookup"><span data-stu-id="d0457-126">Optional: The name of the server from which to get the list of activities.</span></span> <span data-ttu-id="d0457-127">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-127">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-128">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-128">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-129">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-129">Database:\<database></span></span>|<span data-ttu-id="d0457-130">Facultatif : Le nom de la base de données à partir duquel obtenir la liste des activités.</span><span class="sxs-lookup"><span data-stu-id="d0457-130">Optional: The name of the database from which to get the list of activities.</span></span> <span data-ttu-id="d0457-131">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-131">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-132">Répertorie les activités déployées sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="d0457-132">Lists the activities deployed on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="d0457-133">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-133">**Examples**</span></span>  
  
```  
bm.exe get-activities -View:SalesManagerView  
bm.exe get-activities -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-activity-command"></a><span data-ttu-id="d0457-134">Commande remove-activity</span><span class="sxs-lookup"><span data-stu-id="d0457-134">remove-activity Command</span></span>  
 <span data-ttu-id="d0457-135">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-135">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-136">**BM.exe remove-activity-nom :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-136">**bm.exe remove-activity -Name:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-137">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-137">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-138">Parameter</span></span>|<span data-ttu-id="d0457-139"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-139">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-140">Nom :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-140">Name:\<activity name></span></span>|<span data-ttu-id="d0457-141">Nom de l'activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d0457-141">The name of the activity to remove.</span></span>|  
|<span data-ttu-id="d0457-142">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-142">Server:\<server></span></span>|<span data-ttu-id="d0457-143">Facultatif : Le nom du serveur à partir duquel l’activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d0457-143">Optional: The name of the server from which to remove the activity.</span></span> <span data-ttu-id="d0457-144">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-144">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-145">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-145">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-146">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-146">Database:\<database></span></span>|<span data-ttu-id="d0457-147">Facultatif : Le nom de la base de données à partir duquel l’activité à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d0457-147">Optional: The name of the database from which to remove the activity.</span></span> <span data-ttu-id="d0457-148">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-148">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-149">Supprime l'activité spécifiée de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="d0457-149">Removes the specified activity from the BAM Primary Import database.</span></span> <span data-ttu-id="d0457-150">Si l'activité comporte des vues dépendantes, la commande échoue et renvoie une erreur.</span><span class="sxs-lookup"><span data-stu-id="d0457-150">If the activity has dependent views, the command will fail and report an error.</span></span> <span data-ttu-id="d0457-151">Utilisez alors la commande remove-view pour supprimer toutes les vues dépendantes, puis réexécutez la commande remove-activity.</span><span class="sxs-lookup"><span data-stu-id="d0457-151">Use the remove-view command to remove all the dependent views and execute the remove-activity command again.</span></span>  
  
 <span data-ttu-id="d0457-152">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-152">**Examples**</span></span>  
  
```  
bm.exe remove-activity -Name:PurchaseOrder  
bm.exe remove-activity -Name:PO -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="get-activitywindow-command"></a><span data-ttu-id="d0457-153">Commande get-activitywindow</span><span class="sxs-lookup"><span data-stu-id="d0457-153">get-activitywindow Command</span></span>  
 <span data-ttu-id="d0457-154">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-154">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-155">**BM.exe get-activitywindow-activité :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-155">**bm.exe get-activitywindow -Activity:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-156">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-156">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-157">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-157">Parameter</span></span>|<span data-ttu-id="d0457-158"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-158">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-159">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-159">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-160">Le nom de la .activity.</span><span class="sxs-lookup"><span data-stu-id="d0457-160">The name of the .activity.</span></span>|  
|<span data-ttu-id="d0457-161">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-161">Server:\<server></span></span>|<span data-ttu-id="d0457-162">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-162">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-163">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-163">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-164">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-164">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-165">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-165">Database:\<database></span></span>|<span data-ttu-id="d0457-166">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-166">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-167">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-167">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-168">Affiche la durée pour l'activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d0457-168">Displays the duration for the specified activity.</span></span> <span data-ttu-id="d0457-169">Cette commande renvoie la valeur de la durée ainsi que son unité de mesure.</span><span class="sxs-lookup"><span data-stu-id="d0457-169">The command returns the length of the duration and the units by which the duration is measured.</span></span>  
  
 <span data-ttu-id="d0457-170">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-170">**Examples**</span></span>  
  
```  
bm.exe get-activitywindow -Activity:PurchaseOrder  
bm.exe get-activitywindow -Activity:PO -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="set-activitywindow-command"></a><span data-ttu-id="d0457-171">Commande set-activitywindow</span><span class="sxs-lookup"><span data-stu-id="d0457-171">set-activitywindow Command</span></span>  
 <span data-ttu-id="d0457-172">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-172">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-173">**BM.exe set-activitywindow-activité :\<nom de l’activité > - TimeLength :\<nombre entier > - TimeUnit : mois &#124; jour &#124; Heure &#124; Minute [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-173">**bm.exe set-activitywindow -Activity:\<activity name> -TimeLength:\<integer number> -TimeUnit:Month&#124;Day&#124;Hour&#124;Minute[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-174">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-174">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-175">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-175">Parameter</span></span>|<span data-ttu-id="d0457-176"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-176">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-177">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-177">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-178">Nom de l'activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-178">The name of the activity.</span></span>|  
|<span data-ttu-id="d0457-179">TimeLength :\<nombre entier ></span><span class="sxs-lookup"><span data-stu-id="d0457-179">TimeLength:\<integer number></span></span>|<span data-ttu-id="d0457-180">Durée de l'activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-180">The duration for the activity.</span></span>|  
|<span data-ttu-id="d0457-181">TimeUnit:Month &#124; jour &#124; Heure &#124; Minute</span><span class="sxs-lookup"><span data-stu-id="d0457-181">TimeUnit:Month&#124;Day&#124;Hour&#124;Minute</span></span>|<span data-ttu-id="d0457-182">Unité de mesure de la durée.</span><span class="sxs-lookup"><span data-stu-id="d0457-182">The unit measure for the duration.</span></span>|  
|<span data-ttu-id="d0457-183">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-183">Server:\<server></span></span>|<span data-ttu-id="d0457-184">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-184">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-185">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-185">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-186">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-186">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-187">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-187">Database:\<database></span></span>|<span data-ttu-id="d0457-188">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-188">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-189">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-189">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-190">Définit la durée pour l'activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d0457-190">Sets the duration for the specified activity.</span></span>  
  
 <span data-ttu-id="d0457-191">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-191">**Examples**</span></span>  
  
```  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:6 -TimeUnit:Day  
bm.exe set-activitywindow -Activity:PurchaseOrder -TimeLength:1 -TimeUnit:Month  
```  
  
## <a name="get-index-command"></a><span data-ttu-id="d0457-192">Commande get-index</span><span class="sxs-lookup"><span data-stu-id="d0457-192">get-index Command</span></span>  
 <span data-ttu-id="d0457-193">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-193">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-194">**BM.exe get-index-activité :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-194">**bm.exe get-index -Activity:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-195">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-195">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-196">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-196">Parameter</span></span>|<span data-ttu-id="d0457-197"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-197">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-198">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-198">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-199">Nom de l'activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-199">The name of the activity.</span></span>|  
|<span data-ttu-id="d0457-200">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-200">Server:\<server></span></span>|<span data-ttu-id="d0457-201">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-201">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-202">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-202">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-203">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-203">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-204">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-204">Database:\<database></span></span>|<span data-ttu-id="d0457-205">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-205">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-206">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-206">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-207">Répertorie tous les index qui ont été créés pour l'activité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d0457-207">Lists all the indexes that have been created for the specified activity.</span></span>  
  
 <span data-ttu-id="d0457-208">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-208">**Examples**</span></span>  
  
```  
bm.exe get-index -Activity:PurchaseOrder  
bm.exe get-index -Activity:PurchaseOrder -Server:Ship -Database:ShipDatabase  
```  
  
## <a name="create-index-command"></a><span data-ttu-id="d0457-209">Commande create-index</span><span class="sxs-lookup"><span data-stu-id="d0457-209">create-index Command</span></span>  
 <span data-ttu-id="d0457-210">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-210">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-211">**BM.exe create-index - IndexName :\<nom de l’index >-activité :\<nom de l’activité >-point de contrôle :\<point de contrôle 1 > [,\<point de contrôle 2 >...] [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-211">**bm.exe create-index -IndexName:\<index name> -Activity:\<activity name> -Checkpoint:\<checkpoint1>[,\<checkpoint2>...][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-212">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-212">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-213">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-213">Parameter</span></span>|<span data-ttu-id="d0457-214"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-214">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-215">IndexName :\<nom de l’index ></span><span class="sxs-lookup"><span data-stu-id="d0457-215">IndexName:\<index name></span></span>|<span data-ttu-id="d0457-216">Nom du nouvel index.</span><span class="sxs-lookup"><span data-stu-id="d0457-216">The name of the new index.</span></span>|  
|<span data-ttu-id="d0457-217">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-217">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-218">Nom de l'activité pour laquelle l'index est créé.</span><span class="sxs-lookup"><span data-stu-id="d0457-218">The name of the activity for which the index is created.</span></span>|  
|<span data-ttu-id="d0457-219">Point de contrôle :\<point de contrôle 1 > [,\<point de contrôle 2 >...]</span><span class="sxs-lookup"><span data-stu-id="d0457-219">Checkpoint:\<checkpoint1>[,\<checkpoint2>...]</span></span>|<span data-ttu-id="d0457-220">Liste de points de contrôle délimités par des virgules pour l'index.</span><span class="sxs-lookup"><span data-stu-id="d0457-220">A comma-delimited list of checkpoints for the index.</span></span>|  
|<span data-ttu-id="d0457-221">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-221">Server:\<server></span></span>|<span data-ttu-id="d0457-222">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-222">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-223">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-223">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-224">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-224">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-225">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-225">Database:\<database></span></span>|<span data-ttu-id="d0457-226">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-226">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-227">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-227">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-228">Crée un index pour l'activité spécifiée en utilisant les points de contrôle spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d0457-228">Creates an index for the specified activity using the specified checkpoints.</span></span>  
  
 <span data-ttu-id="d0457-229">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-229">**Examples**</span></span>  
  
```  
bm.exe create-index -IndexName:Idx1 -Activity:PO -Checkpoint:State,City  
bm.exe create-index -IndexName:Idx2 -Activity:PO -Checkpoint:Amount -Server:S1  
```  
  
## <a name="delete-index-command"></a><span data-ttu-id="d0457-230">Commande delete-index</span><span class="sxs-lookup"><span data-stu-id="d0457-230">delete-index Command</span></span>  
 <span data-ttu-id="d0457-231">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-231">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-232">**BM.exe delete-index - IndexName :\<nom de l’index >-activité :\<nom de l’activité > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-232">**bm.exe delete-index -IndexName:\<index name> -Activity:\<activity name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="d0457-233">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-233">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-234">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-234">Parameter</span></span>|<span data-ttu-id="d0457-235"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-235">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-236">IndexName :\<nom de l’index ></span><span class="sxs-lookup"><span data-stu-id="d0457-236">IndexName:\<index name></span></span>|<span data-ttu-id="d0457-237">Le nom de l’index à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d0457-237">The name of the index to delete.</span></span>|  
|<span data-ttu-id="d0457-238">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-238">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-239">Nom de l'activité pour laquelle l'index est supprimé.</span><span class="sxs-lookup"><span data-stu-id="d0457-239">The name of the activity for which the index is deleted.</span></span>|  
|<span data-ttu-id="d0457-240">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-240">Server:\<server></span></span>|<span data-ttu-id="d0457-241">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-241">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-242">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-242">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-243">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-243">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-244">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-244">Database:\<database></span></span>|<span data-ttu-id="d0457-245">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-245">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-246">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-246">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-247">Supprime de l'activité indiquée l'index spécifié à l'aide du nom indiqué.</span><span class="sxs-lookup"><span data-stu-id="d0457-247">Deletes the specified index with the given name from the specified activity.</span></span>  
  
 <span data-ttu-id="d0457-248">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-248">**Examples**</span></span>  
  
```  
bm.exe delete-index -IndexName:Idx1 -Activity:PO  
bm.exe delete-index -IndexName:Idx2 -Activity:PO -Server:S1 -Database:BamPI1  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="d0457-249">Commande set-archive</span><span class="sxs-lookup"><span data-stu-id="d0457-249">set-archive Command</span></span>  
 <span data-ttu-id="d0457-250">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-250">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-251">**BM.exe get-archive-activité :\<activité > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-251">**bm.exe get-archive -Activity:\<activity> [-Server:\<server>] [-Database:\<database>]**</span></span>  
  
 <span data-ttu-id="d0457-252">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-252">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-253">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-253">Parameter</span></span>|<span data-ttu-id="d0457-254"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-254">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-255">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-255">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-256">Nom de l’activité pour laquelle le comportement doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="d0457-256">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="d0457-257">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-257">Server:\<server></span></span>|<span data-ttu-id="d0457-258">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-258">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-259">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-259">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-260">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-260">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-261">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-261">Database:\<database></span></span>|<span data-ttu-id="d0457-262">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-262">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-263">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-263">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-264">Obtient le comportement du package d’archivage de l’activité spécifiée, qu’il archive ou qu’il supprime les données de l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-264">Gets the behavior of the archiving package for the specified activity, whether the archiving package will archive orpurge activity data.</span></span>  
  
 <span data-ttu-id="d0457-265">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-265">**Examples**</span></span>  
  
```  
bm.exe get-archive -Activity:PurchaseOrder  
```  
  
## <a name="set-archive-command"></a><span data-ttu-id="d0457-266">Commande set-archive</span><span class="sxs-lookup"><span data-stu-id="d0457-266">set-archive Command</span></span>  
 <span data-ttu-id="d0457-267">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="d0457-267">**Usage**</span></span>  
  
 <span data-ttu-id="d0457-268">**BM.exe set-archive - activité :\<activité > - ShouldArchive : True [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="d0457-268">**bm.exe set-archive -Activity:\<activity> -ShouldArchive:True [-Server:\<server>] [-Database:\<database>]**</span></span>  
  
 <span data-ttu-id="d0457-269">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="d0457-269">**Parameters**</span></span>  
  
|<span data-ttu-id="d0457-270">Paramètre</span><span class="sxs-lookup"><span data-stu-id="d0457-270">Parameter</span></span>|<span data-ttu-id="d0457-271"> Description</span><span class="sxs-lookup"><span data-stu-id="d0457-271">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0457-272">Activité :\<nom de l’activité ></span><span class="sxs-lookup"><span data-stu-id="d0457-272">Activity:\<activity name></span></span>|<span data-ttu-id="d0457-273">Nom de l’activité pour laquelle le comportement doit être affiché.</span><span class="sxs-lookup"><span data-stu-id="d0457-273">The name of the activity for which the behavior is to be displayed.</span></span>|  
|<span data-ttu-id="d0457-274">ShouldArchive : True</span><span class="sxs-lookup"><span data-stu-id="d0457-274">ShouldArchive: True</span></span>|<span data-ttu-id="d0457-275">Si ce paramètre a la valeur True, l’activité est déplacée dans la base de données d’archivage.</span><span class="sxs-lookup"><span data-stu-id="d0457-275">If set to True, the activity is moved to Archive DB.</span></span> <span data-ttu-id="d0457-276">En revanche, s’il a la valeur False, l’activité est supprimée.</span><span class="sxs-lookup"><span data-stu-id="d0457-276">If set to False, the activity is purged.</span></span>|  
|<span data-ttu-id="d0457-277">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="d0457-277">Server:\<server></span></span>|<span data-ttu-id="d0457-278">Facultatif : Le nom du serveur sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-278">Optional: The name of the server on which the activity resides.</span></span> <span data-ttu-id="d0457-279">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="d0457-279">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="d0457-280">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="d0457-280">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="d0457-281">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="d0457-281">Database:\<database></span></span>|<span data-ttu-id="d0457-282">Facultatif : Le nom de la base de données sur lequel réside l’activité.</span><span class="sxs-lookup"><span data-stu-id="d0457-282">Optional: The name of the database on which the activity resides.</span></span> <span data-ttu-id="d0457-283">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="d0457-283">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="d0457-284">Définit le comportement du package d’archivage de l’activité spécifiée pour que les données de cette dernière soient déplacées dans la base de donnés d’archivage.</span><span class="sxs-lookup"><span data-stu-id="d0457-284">Sets the behavior of the archiving package for the activity specified so that activity data is moved into the Archive DB.</span></span> <span data-ttu-id="d0457-285">Par défaut, ce comportement est défini pour les nouvelles activités déployées.</span><span class="sxs-lookup"><span data-stu-id="d0457-285">By default, this behavior is set for new activities that are deployed.</span></span>  
  
 <span data-ttu-id="d0457-286">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="d0457-286">**Examples**</span></span>  
  
 <span data-ttu-id="d0457-287">Pour purger les données de l’activité BAM, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d0457-287">To purge the BAM activity data, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:False  
```  
  
 <span data-ttu-id="d0457-288">Pour déplacer les données de l’activité BAM vers la base de données d’archivage BAM, exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="d0457-288">To move the BAM activity data to the BAMArchive database, execute the following:</span></span>  
  
```  
bm.exe set-archive -Activity:PurchaseOrder -ShouldArchive:True  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0457-289">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0457-289">See Also</span></span>  
 [<span data-ttu-id="d0457-290">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="d0457-290">BAM Management Utility</span></span>](../core/bam-management-utility.md)