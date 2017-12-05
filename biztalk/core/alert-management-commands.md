---
title: Commandes de gestion des alertes | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a96d8de7-a918-4737-aa35-4e1abf6bb08f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f419e7a0019287383080c319961b8a3831d27bb4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="alert-management-commands"></a><span data-ttu-id="cecd2-102">Commandes de gestion des alertes</span><span class="sxs-lookup"><span data-stu-id="cecd2-102">Alert Management Commands</span></span>
<span data-ttu-id="cecd2-103">Les commandes de gestion des alertes de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser des alertes déployées.</span><span class="sxs-lookup"><span data-stu-id="cecd2-103">The BAM management utility alert management commands allow you to work with deployed alerts.</span></span>  
  
-   <span data-ttu-id="cecd2-104">Get-alerts : obtenir la liste des alertes déployées.</span><span class="sxs-lookup"><span data-stu-id="cecd2-104">get-alerts: Get a list of deployed alerts.</span></span>  
  
-   <span data-ttu-id="cecd2-105">supprimer les alertes : supprime une alerte.</span><span class="sxs-lookup"><span data-stu-id="cecd2-105">remove-alerts: Removes an alert.</span></span>  
  
-   <span data-ttu-id="cecd2-106">Enable-alerts : Active les alertes sur une vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-106">enable-alerts: Enables alerts on a view.</span></span>  
  
-   <span data-ttu-id="cecd2-107">Disable-alerts : désactive les alertes sur une vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-107">disable-alerts: Disables alerts on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cecd2-108">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="cecd2-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="cecd2-109">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="cecd2-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="cecd2-110">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="cecd2-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cecd2-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="cecd2-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-alerts-command"></a><span data-ttu-id="cecd2-112">Commande get-alerts</span><span class="sxs-lookup"><span data-stu-id="cecd2-112">get-alerts Command</span></span>  
 <span data-ttu-id="cecd2-113">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="cecd2-113">**Usage**</span></span>  
  
 <span data-ttu-id="cecd2-114">**BM.exe get-alerts [-View :\<nom de la vue\> ] [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="cecd2-114">**bm.exe get-alerts [ -View:\<view name\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="cecd2-115">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="cecd2-115">**Parameters**</span></span>  
  
|<span data-ttu-id="cecd2-116">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cecd2-116">Parameter</span></span>|<span data-ttu-id="cecd2-117"> Description</span><span class="sxs-lookup"><span data-stu-id="cecd2-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cecd2-118">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="cecd2-118">View:\<view name\></span></span>|<span data-ttu-id="cecd2-119">Nom de la vue à partir de laquelle obtenir la liste des alertes.</span><span class="sxs-lookup"><span data-stu-id="cecd2-119">The name of the view from which to get the list of alerts.</span></span>|  
|<span data-ttu-id="cecd2-120">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="cecd2-120">Server:\<server\></span></span>|<span data-ttu-id="cecd2-121">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-121">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="cecd2-122">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="cecd2-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="cecd2-123">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="cecd2-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="cecd2-124">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="cecd2-124">Database:\<database\></span></span>|<span data-ttu-id="cecd2-125">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-125">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="cecd2-126">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="cecd2-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="cecd2-127">Répertorie les alertes définies sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="cecd2-127">Lists the alerts defined on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="cecd2-128">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="cecd2-128">**Examples**</span></span>  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-alerts-command"></a><span data-ttu-id="cecd2-129">Commande remove-alerts</span><span class="sxs-lookup"><span data-stu-id="cecd2-129">remove-alerts Command</span></span>  
 <span data-ttu-id="cecd2-130">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="cecd2-130">**Usage**</span></span>  
  
 <span data-ttu-id="cecd2-131">**BM.exe remove-alerts-View :\<nom de la vue\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="cecd2-131">**bm.exe remove-alerts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="cecd2-132">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="cecd2-132">**Parameters**</span></span>  
  
|<span data-ttu-id="cecd2-133">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cecd2-133">Parameter</span></span>|<span data-ttu-id="cecd2-134"> Description</span><span class="sxs-lookup"><span data-stu-id="cecd2-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cecd2-135">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="cecd2-135">View:\<view name\></span></span>|<span data-ttu-id="cecd2-136">Nom de la vue à partir de laquelle supprimer les alertes.</span><span class="sxs-lookup"><span data-stu-id="cecd2-136">The name of the view from which to remove alerts.</span></span>|  
|<span data-ttu-id="cecd2-137">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="cecd2-137">Server:\<server\></span></span>|<span data-ttu-id="cecd2-138">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-138">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="cecd2-139">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="cecd2-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="cecd2-140">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="cecd2-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="cecd2-141">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="cecd2-141">Database:\<database\></span></span>|<span data-ttu-id="cecd2-142">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-142">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="cecd2-143">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="cecd2-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="cecd2-144">Supprime toutes les alertes sur la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cecd2-144">Removes all alerts on the specified view.</span></span>  
  
 <span data-ttu-id="cecd2-145">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="cecd2-145">**Examples**</span></span>  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## <a name="enable-alerts-command"></a><span data-ttu-id="cecd2-146">Commande enable-alerts </span><span class="sxs-lookup"><span data-stu-id="cecd2-146">enable-alerts Command</span></span>  
 <span data-ttu-id="cecd2-147">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="cecd2-147">**Usage**</span></span>  
  
 <span data-ttu-id="cecd2-148">**BM.exe enable-alerts-View :\<nom de la vue\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="cecd2-148">**bm.exe enable-alerts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="cecd2-149">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="cecd2-149">**Parameters**</span></span>  
  
|<span data-ttu-id="cecd2-150">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cecd2-150">Parameter</span></span>|<span data-ttu-id="cecd2-151"> Description</span><span class="sxs-lookup"><span data-stu-id="cecd2-151">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cecd2-152">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="cecd2-152">View:\<view name\></span></span>|<span data-ttu-id="cecd2-153">Nom de la vue sur laquelle activer les alertes.</span><span class="sxs-lookup"><span data-stu-id="cecd2-153">The name of the view on which to enable alerts.</span></span>|  
|<span data-ttu-id="cecd2-154">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="cecd2-154">Server:\<server\></span></span>|<span data-ttu-id="cecd2-155">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-155">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="cecd2-156">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="cecd2-156">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="cecd2-157">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="cecd2-157">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="cecd2-158">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="cecd2-158">Database:\<database\></span></span>|<span data-ttu-id="cecd2-159">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-159">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="cecd2-160">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="cecd2-160">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="cecd2-161">Active les alertes sur la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cecd2-161">Enables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="cecd2-162">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="cecd2-162">**Examples**</span></span>  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="disable-alerts-command"></a><span data-ttu-id="cecd2-163">Commande disable-alerts</span><span class="sxs-lookup"><span data-stu-id="cecd2-163">disable-alerts Command</span></span>  
 <span data-ttu-id="cecd2-164">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="cecd2-164">**Usage**</span></span>  
  
 <span data-ttu-id="cecd2-165">**BM.exe disable-alerts-View :\<nom de la vue\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="cecd2-165">**bm.exe disable-alerts -View:\<view name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="cecd2-166">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="cecd2-166">**Parameters**</span></span>  
  
|<span data-ttu-id="cecd2-167">Paramètre</span><span class="sxs-lookup"><span data-stu-id="cecd2-167">Parameter</span></span>|<span data-ttu-id="cecd2-168"> Description</span><span class="sxs-lookup"><span data-stu-id="cecd2-168">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cecd2-169">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="cecd2-169">View:\<view name\></span></span>|<span data-ttu-id="cecd2-170">Nom de la vue sur laquelle désactiver les alertes.</span><span class="sxs-lookup"><span data-stu-id="cecd2-170">The name of the view on which to disable alerts.</span></span>|  
|<span data-ttu-id="cecd2-171">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="cecd2-171">Server:\<server\></span></span>|<span data-ttu-id="cecd2-172">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-172">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="cecd2-173">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="cecd2-173">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="cecd2-174">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="cecd2-174">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="cecd2-175">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="cecd2-175">Database:\<database\></span></span>|<span data-ttu-id="cecd2-176">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="cecd2-176">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="cecd2-177">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="cecd2-177">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="cecd2-178">Désactive les alertes sur la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="cecd2-178">Disables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="cecd2-179">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="cecd2-179">**Examples**</span></span>  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="see-also"></a><span data-ttu-id="cecd2-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cecd2-180">See Also</span></span>  
 [<span data-ttu-id="cecd2-181">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="cecd2-181">BAM Management Utility</span></span>](../core/bam-management-utility.md)