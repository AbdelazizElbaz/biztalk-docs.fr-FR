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
ms.openlocfilehash: 0b73129d884fea81bdb64609de5e95570275a344
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="alert-management-commands"></a><span data-ttu-id="c54f0-102">Commandes de gestion des alertes</span><span class="sxs-lookup"><span data-stu-id="c54f0-102">Alert Management Commands</span></span>
<span data-ttu-id="c54f0-103">Les commandes de gestion des alertes de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser des alertes déployées.</span><span class="sxs-lookup"><span data-stu-id="c54f0-103">The BAM management utility alert management commands allow you to work with deployed alerts.</span></span>  
  
-   <span data-ttu-id="c54f0-104">Get-alerts : obtenir la liste des alertes déployées.</span><span class="sxs-lookup"><span data-stu-id="c54f0-104">get-alerts: Get a list of deployed alerts.</span></span>  
  
-   <span data-ttu-id="c54f0-105">supprimer les alertes : supprime une alerte.</span><span class="sxs-lookup"><span data-stu-id="c54f0-105">remove-alerts: Removes an alert.</span></span>  
  
-   <span data-ttu-id="c54f0-106">Enable-alerts : Active les alertes sur une vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-106">enable-alerts: Enables alerts on a view.</span></span>  
  
-   <span data-ttu-id="c54f0-107">Disable-alerts : désactive les alertes sur une vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-107">disable-alerts: Disables alerts on a view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c54f0-108">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="c54f0-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="c54f0-109">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="c54f0-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="c54f0-110">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="c54f0-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c54f0-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="c54f0-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-alerts-command"></a><span data-ttu-id="c54f0-112">Commande get-alerts</span><span class="sxs-lookup"><span data-stu-id="c54f0-112">get-alerts Command</span></span>  
 <span data-ttu-id="c54f0-113">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="c54f0-113">**Usage**</span></span>  
  
 <span data-ttu-id="c54f0-114">**BM.exe get-alerts [-View :\<nom de la vue >] [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="c54f0-114">**bm.exe get-alerts [ -View:\<view name> ][ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="c54f0-115">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="c54f0-115">**Parameters**</span></span>  
  
|<span data-ttu-id="c54f0-116">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c54f0-116">Parameter</span></span>|<span data-ttu-id="c54f0-117"> Description</span><span class="sxs-lookup"><span data-stu-id="c54f0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c54f0-118">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="c54f0-118">View:\<view name></span></span>|<span data-ttu-id="c54f0-119">Nom de la vue à partir de laquelle obtenir la liste des alertes.</span><span class="sxs-lookup"><span data-stu-id="c54f0-119">The name of the view from which to get the list of alerts.</span></span>|  
|<span data-ttu-id="c54f0-120">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="c54f0-120">Server:\<server></span></span>|<span data-ttu-id="c54f0-121">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-121">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="c54f0-122">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="c54f0-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="c54f0-123">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="c54f0-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="c54f0-124">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="c54f0-124">Database:\<database></span></span>|<span data-ttu-id="c54f0-125">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-125">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="c54f0-126">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="c54f0-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="c54f0-127">Répertorie les alertes définies sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="c54f0-127">Lists the alerts defined on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="c54f0-128">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="c54f0-128">**Examples**</span></span>  
  
```  
bm.exe get-alerts -View:ManagerView  
bm.exe get-alerts -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="remove-alerts-command"></a><span data-ttu-id="c54f0-129">Commande remove-alerts</span><span class="sxs-lookup"><span data-stu-id="c54f0-129">remove-alerts Command</span></span>  
 <span data-ttu-id="c54f0-130">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="c54f0-130">**Usage**</span></span>  
  
 <span data-ttu-id="c54f0-131">**BM.exe remove-alerts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="c54f0-131">**bm.exe remove-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="c54f0-132">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="c54f0-132">**Parameters**</span></span>  
  
|<span data-ttu-id="c54f0-133">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c54f0-133">Parameter</span></span>|<span data-ttu-id="c54f0-134"> Description</span><span class="sxs-lookup"><span data-stu-id="c54f0-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c54f0-135">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="c54f0-135">View:\<view name></span></span>|<span data-ttu-id="c54f0-136">Nom de la vue à partir de laquelle supprimer les alertes.</span><span class="sxs-lookup"><span data-stu-id="c54f0-136">The name of the view from which to remove alerts.</span></span>|  
|<span data-ttu-id="c54f0-137">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="c54f0-137">Server:\<server></span></span>|<span data-ttu-id="c54f0-138">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-138">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="c54f0-139">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="c54f0-139">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="c54f0-140">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="c54f0-140">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="c54f0-141">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="c54f0-141">Database:\<database></span></span>|<span data-ttu-id="c54f0-142">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-142">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="c54f0-143">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="c54f0-143">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="c54f0-144">Supprime toutes les alertes sur la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c54f0-144">Removes all alerts on the specified view.</span></span>  
  
 <span data-ttu-id="c54f0-145">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="c54f0-145">**Examples**</span></span>  
  
```  
bm.exe remove-alerts -View:SalesManagerView  
bm.exe remove-alerts -View:Shipments -Server:Ship1  
```  
  
## <a name="enable-alerts-command"></a><span data-ttu-id="c54f0-146">Commande enable-alerts </span><span class="sxs-lookup"><span data-stu-id="c54f0-146">enable-alerts Command</span></span>  
 <span data-ttu-id="c54f0-147">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="c54f0-147">**Usage**</span></span>  
  
 <span data-ttu-id="c54f0-148">**BM.exe enable-alerts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="c54f0-148">**bm.exe enable-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="c54f0-149">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="c54f0-149">**Parameters**</span></span>  
  
|<span data-ttu-id="c54f0-150">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c54f0-150">Parameter</span></span>|<span data-ttu-id="c54f0-151"> Description</span><span class="sxs-lookup"><span data-stu-id="c54f0-151">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c54f0-152">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="c54f0-152">View:\<view name></span></span>|<span data-ttu-id="c54f0-153">Nom de la vue sur laquelle activer les alertes.</span><span class="sxs-lookup"><span data-stu-id="c54f0-153">The name of the view on which to enable alerts.</span></span>|  
|<span data-ttu-id="c54f0-154">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="c54f0-154">Server:\<server></span></span>|<span data-ttu-id="c54f0-155">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-155">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="c54f0-156">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="c54f0-156">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="c54f0-157">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="c54f0-157">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="c54f0-158">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="c54f0-158">Database:\<database></span></span>|<span data-ttu-id="c54f0-159">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-159">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="c54f0-160">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="c54f0-160">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="c54f0-161">Active les alertes sur la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c54f0-161">Enables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="c54f0-162">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="c54f0-162">**Examples**</span></span>  
  
```  
bm.exe enable-alerts -View:SalesManagerView  
bm.exe enable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="disable-alerts-command"></a><span data-ttu-id="c54f0-163">Commande disable-alerts</span><span class="sxs-lookup"><span data-stu-id="c54f0-163">disable-alerts Command</span></span>  
 <span data-ttu-id="c54f0-164">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="c54f0-164">**Usage**</span></span>  
  
 <span data-ttu-id="c54f0-165">**BM.exe disable-alerts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="c54f0-165">**bm.exe disable-alerts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="c54f0-166">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="c54f0-166">**Parameters**</span></span>  
  
|<span data-ttu-id="c54f0-167">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c54f0-167">Parameter</span></span>|<span data-ttu-id="c54f0-168"> Description</span><span class="sxs-lookup"><span data-stu-id="c54f0-168">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c54f0-169">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="c54f0-169">View:\<view name></span></span>|<span data-ttu-id="c54f0-170">Nom de la vue sur laquelle désactiver les alertes.</span><span class="sxs-lookup"><span data-stu-id="c54f0-170">The name of the view on which to disable alerts.</span></span>|  
|<span data-ttu-id="c54f0-171">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="c54f0-171">Server:\<server></span></span>|<span data-ttu-id="c54f0-172">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-172">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="c54f0-173">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="c54f0-173">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="c54f0-174">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="c54f0-174">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="c54f0-175">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="c54f0-175">Database:\<database></span></span>|<span data-ttu-id="c54f0-176">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="c54f0-176">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="c54f0-177">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="c54f0-177">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="c54f0-178">Désactive les alertes sur la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c54f0-178">Disables alerts on the specified view.</span></span>  
  
 <span data-ttu-id="c54f0-179">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="c54f0-179">**Examples**</span></span>  
  
```  
bm.exe disable-alerts -View:SalesManagerView  
bm.exe disable-alerts -View:SalesManagerView -Server:s1 -Database:db2  
```  
  
## <a name="see-also"></a><span data-ttu-id="c54f0-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c54f0-180">See Also</span></span>  
 [<span data-ttu-id="c54f0-181">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="c54f0-181">BAM Management Utility</span></span>](../core/bam-management-utility.md)