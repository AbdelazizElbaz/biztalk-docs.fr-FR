---
title: "Commandes de gestion d’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feb12226-a4da-4fc5-93a1-aced239f60a9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79f908933015fa07e2ecf77a2e61d31227f73e62
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="user-management-commands"></a><span data-ttu-id="dd5b6-102">Commandes de gestion des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="dd5b6-102">User Management Commands</span></span>
<span data-ttu-id="dd5b6-103">Les commandes de gestion de l’utilisateur d’alerte de l'utilitaire de gestion BAM vous permettent d'obtenir, d'ajouter ou de supprimer des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-103">The BAM Management utility alert user management commands allow you to get, add, and remove users.</span></span>  
  
-   <span data-ttu-id="dd5b6-104">Get-accounts : Obtient une liste de tous les utilisateurs et groupes qui peuvent accéder à une vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-104">get-accounts: Gets a list of all users and groups that can access a specified view.</span></span>  
  
-   <span data-ttu-id="dd5b6-105">Ajouter un compte : allocations de droits d’accès pour l’utilisateur spécifié ou le groupe à la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-105">add-account: Grants access rights for the specified user or group to the specified view.</span></span>  
  
-   <span data-ttu-id="dd5b6-106">compte de suppression : supprime les droits pour un utilisateur ou un groupe d’accès d’une vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-106">remove-account: Removes access rights for a user or group from a specified view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd5b6-107">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-107">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="dd5b6-108">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-108">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="dd5b6-109">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-109">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd5b6-110">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-110">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-accounts-command"></a><span data-ttu-id="dd5b6-111">Commande get-accounts</span><span class="sxs-lookup"><span data-stu-id="dd5b6-111">get-accounts Command</span></span>  
 <span data-ttu-id="dd5b6-112">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-112">**Usage**</span></span>  
  
 <span data-ttu-id="dd5b6-113">**BM.exe get-accounts-View :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-113">**bm.exe get-accounts -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="dd5b6-114">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-114">**Parameters**</span></span>  
  
|<span data-ttu-id="dd5b6-115">Paramètre</span><span class="sxs-lookup"><span data-stu-id="dd5b6-115">Parameter</span></span>|<span data-ttu-id="dd5b6-116"> Description</span><span class="sxs-lookup"><span data-stu-id="dd5b6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd5b6-117">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-117">View:\<view name></span></span>|<span data-ttu-id="dd5b6-118">Nom de la vue pour laquelle répertorier les comptes.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-118">The name of the view for which to list accounts.</span></span>|  
|<span data-ttu-id="dd5b6-119">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-119">Server:\<server></span></span>|<span data-ttu-id="dd5b6-120">Facultatif : Le nom du serveur à partir duquel récupérer les comptes.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-120">Optional: The name of the server from which to retrieve the accounts.</span></span> <span data-ttu-id="dd5b6-121">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-121">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="dd5b6-122">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-122">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="dd5b6-123">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-123">Database:\<database></span></span>|<span data-ttu-id="dd5b6-124">Facultatif : Le nom de la base de données à partir duquel récupérer les comptes.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-124">Optional: The name of the database from which to retrieve the accounts.</span></span> <span data-ttu-id="dd5b6-125">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-125">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="dd5b6-126">Répertorie tous les utilisateurs et les groupes qui peuvent accéder à la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-126">Lists all users and groups that can access the specified view.</span></span>  
  
 <span data-ttu-id="dd5b6-127">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-127">**Examples**</span></span>  
  
 `bm.exe get-accounts -View:PurchaseOrder`  
  
 `bm.exe get-accounts -View:ShipmentOrder -Server:Ship -Database:ShipDatabase`  
  
## <a name="add-account-command"></a><span data-ttu-id="dd5b6-128">Commande add-account</span><span class="sxs-lookup"><span data-stu-id="dd5b6-128">add-account Command</span></span>  
 <span data-ttu-id="dd5b6-129">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-129">**Usage**</span></span>  
  
 <span data-ttu-id="dd5b6-130">**BM.exe ajouter-account - AccountName :\<nom du compte >-affichage :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-130">**bm.exe add-account -AccountName:\<account name> -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="dd5b6-131">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-131">**Parameters**</span></span>  
  
|<span data-ttu-id="dd5b6-132">Paramètre</span><span class="sxs-lookup"><span data-stu-id="dd5b6-132">Parameter</span></span>|<span data-ttu-id="dd5b6-133"> Description</span><span class="sxs-lookup"><span data-stu-id="dd5b6-133">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd5b6-134">AccountName:<nom du compte</span><span class="sxs-lookup"><span data-stu-id="dd5b6-134">AccountName:<account name</span></span>|<span data-ttu-id="dd5b6-135">Nom du compte auquel les droits sont accordés.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-135">The name of the account to which rights are granted.</span></span>|  
|<span data-ttu-id="dd5b6-136">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-136">View:\<view name></span></span>|<span data-ttu-id="dd5b6-137">Nom de la vue à laquelle les droits sont accordés.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-137">The name of the view to which rights are granted.</span></span>|  
|<span data-ttu-id="dd5b6-138">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-138">Server:\<server></span></span>|<span data-ttu-id="dd5b6-139">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-139">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="dd5b6-140">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-140">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="dd5b6-141">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-141">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="dd5b6-142">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-142">Database:\<database></span></span>|<span data-ttu-id="dd5b6-143">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-143">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="dd5b6-144">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-144">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="dd5b6-145">Accorde les droits d'accès à l'utilisateur ou au groupe spécifiés pour la vue indiquée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-145">Grants the specified user or group access rights to the specified view.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dd5b6-146">Si vous utilisez les agrégations en temps réel (RTA), les utilisateurs ajoutés à **-ajouter un compte** commande ne sont pas accordées automatiquement les droits d’ouverture de session sur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-146">If you are using Real Time Aggregations (RTAs), users added with **add-account** command are not automatically granted logon rights to SQL Server.</span></span> <span data-ttu-id="dd5b6-147">Dans ce cas, prévoyez d'établir un groupe d'utilisateurs Windows contenant tous les utilisateurs qui ont besoin d'afficher des vues d'agrégations RTA.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-147">If you are using RTAs, consider establishing a Windows user group that contains all of the users that need to see views of the RTAs.</span></span> <span data-ttu-id="dd5b6-148">Accordez à ce groupe des droits de connexion SQL Server explicites au serveur SQL Server hébergeant les bases de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-148">Grant that group explicit SQL Server logon rights on the SQL server hosting the BAM Primary Import databases.</span></span>  
  
 <span data-ttu-id="dd5b6-149">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-149">**Examples**</span></span>  
  
```  
bm.exe add-account -AccountName:john -View:PurchaseOrder  
bm.exe add-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="remove-account-command"></a><span data-ttu-id="dd5b6-150">Commande remove-account</span><span class="sxs-lookup"><span data-stu-id="dd5b6-150">remove-account Command</span></span>  
 <span data-ttu-id="dd5b6-151">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-151">**Usage**</span></span>  
  
 <span data-ttu-id="dd5b6-152">**BM.exe remove-account - AccountName :\<nom du compte >-affichage :\<nom de la vue > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-152">**bm.exe remove-account -AccountName:\<account name> -View:\<view name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="dd5b6-153">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-153">**Parameters**</span></span>  
  
|<span data-ttu-id="dd5b6-154">Paramètre</span><span class="sxs-lookup"><span data-stu-id="dd5b6-154">Parameter</span></span>|<span data-ttu-id="dd5b6-155"> Description</span><span class="sxs-lookup"><span data-stu-id="dd5b6-155">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd5b6-156">AccountName :\<nom du compte ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-156">AccountName:\<account name></span></span>|<span data-ttu-id="dd5b6-157">Nom du compte à partir duquel supprimer les droits sur la vue.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-157">The name of the account from which to remove rights to the view.</span></span>|  
|<span data-ttu-id="dd5b6-158">Affichage :\<nom de la vue ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-158">View:\<view name></span></span>|<span data-ttu-id="dd5b6-159">Nom de la vue à partir de laquelle les droits sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-159">The name of the view to which rights are removed.</span></span>|  
|<span data-ttu-id="dd5b6-160">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-160">Server:\<server></span></span>|<span data-ttu-id="dd5b6-161">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-161">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="dd5b6-162">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-162">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="dd5b6-163">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-163">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="dd5b6-164">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="dd5b6-164">Database:\<database></span></span>|<span data-ttu-id="dd5b6-165">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-165">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="dd5b6-166">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-166">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="dd5b6-167">Supprime les droits d'accès d’un utilisateur ou d'un groupe d’une vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-167">Removes access rights for a user or group from a specified view.</span></span> <span data-ttu-id="dd5b6-168">La suppression d'un compte à partir d'une vue supprime le compte et tous ses membres des alertes définies pour la vue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-168">Removing an account from a view removes that account and all of its members from alerts defined for the specified view.</span></span> <span data-ttu-id="dd5b6-169">Si le compte est l'unique propriétaire d'une alerte, l'utilisateur actuel (admin) devient le nouveau propriétaire de l'alerte.</span><span class="sxs-lookup"><span data-stu-id="dd5b6-169">If that account is the sole owner of an alert, the current user (admin) becomes the new owner of the alert.</span></span>  
  
 <span data-ttu-id="dd5b6-170">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="dd5b6-170">**Examples**</span></span>  
  
```  
bm.exe remove-account -AccountName:john -View:PurchaseOrder  
bm.exe remove-account -AccountName:Agents -View:PO -Server:Srv1 -Database:Db2  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd5b6-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd5b6-171">See Also</span></span>  
 [<span data-ttu-id="dd5b6-172">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="dd5b6-172">BAM Management Utility</span></span>](../core/bam-management-utility.md)