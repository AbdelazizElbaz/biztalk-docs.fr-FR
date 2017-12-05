---
title: "Commandes de gestion d’abonnement d’alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd6ad27-6217-466a-b616-4b26fb31b0af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02234637e38bb59e71c0f435ee24feef39e09e91
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="alert-subscription-management-commands"></a><span data-ttu-id="aab5b-102">Commandes de gestion des abonnements relatifs aux alertes</span><span class="sxs-lookup"><span data-stu-id="aab5b-102">Alert Subscription Management Commands</span></span>
<span data-ttu-id="aab5b-103">Les commandes de gestion des abonnements de l'utilitaire de gestion BAM vous permettent de travailler avec les abonnements relatifs aux alertes.</span><span class="sxs-lookup"><span data-stu-id="aab5b-103">The BAM management utility subscription management commands allow you to work with alert subscriptions.</span></span>  
  
-   <span data-ttu-id="aab5b-104">get-subscription : Obtient une liste d’abonnés à une alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-104">get-subscription: Gets a list of subscribers to an alert.</span></span>  
  
-   <span data-ttu-id="aab5b-105">Ajouter un abonnement : ajoute un abonné à une alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-105">add-subscription: Adds a subscriber to an alert.</span></span>  
  
-   <span data-ttu-id="aab5b-106">Remove-subscription : supprime un abonné à partir d’une alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-106">remove-subscription: Removes a subscriber from an alert.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aab5b-107">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="aab5b-107">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="aab5b-108">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="aab5b-108">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="aab5b-109">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="aab5b-109">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aab5b-110">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="aab5b-110">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-subscription-command"></a><span data-ttu-id="aab5b-111">Commande get-subscription</span><span class="sxs-lookup"><span data-stu-id="aab5b-111">get-subscription Command</span></span>  
 <span data-ttu-id="aab5b-112">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aab5b-112">**Usage**</span></span>  
  
 <span data-ttu-id="aab5b-113">**BM.exe get-subscriptions-View :\<nom de la vue\> -alerte :\<nom de l’alerte\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aab5b-113">**bm.exe get-subscriptions -View:\<view name\> -Alert:\<alert name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aab5b-114">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aab5b-114">**Parameters**</span></span>  
  
|<span data-ttu-id="aab5b-115">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aab5b-115">Parameter</span></span>|<span data-ttu-id="aab5b-116"> Description</span><span class="sxs-lookup"><span data-stu-id="aab5b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aab5b-117">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="aab5b-117">View:\<view name\></span></span>|<span data-ttu-id="aab5b-118">Nom de la vue sur laquelle l'alerte doit être spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aab5b-118">The name of the view on which the alert is to be specified.</span></span>|  
|<span data-ttu-id="aab5b-119">Alerte :\<nom de l’alerte\></span><span class="sxs-lookup"><span data-stu-id="aab5b-119">Alert:\<alert name\></span></span>|<span data-ttu-id="aab5b-120">Nom de l'alerte à partir de laquelle obtenir l'abonnement.</span><span class="sxs-lookup"><span data-stu-id="aab5b-120">The name of the alert from which to get the subscription.</span></span>|  
|<span data-ttu-id="aab5b-121">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aab5b-121">Server:\<server\></span></span>|<span data-ttu-id="aab5b-122">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="aab5b-122">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="aab5b-123">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="aab5b-123">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="aab5b-124">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aab5b-124">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aab5b-125">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aab5b-125">Database:\<database\></span></span>|<span data-ttu-id="aab5b-126">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="aab5b-126">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="aab5b-127">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aab5b-127">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aab5b-128">Répertorie tous les abonnés à l'alerte spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aab5b-128">Lists all the subscribers to the specified alert.</span></span>  
  
 <span data-ttu-id="aab5b-129">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aab5b-129">**Examples**</span></span>  
  
```  
bm.exe get-subscriptions -View:SalesManagerView -Alert:SalesTooLow  
bm.exe get-subscriptions -View:Shipments -Alert:SlowShipment -Server:Ship1  
```  
  
## <a name="add-subscription-command"></a><span data-ttu-id="aab5b-130">Commande add-subscription</span><span class="sxs-lookup"><span data-stu-id="aab5b-130">add-subscription Command</span></span>  
 <span data-ttu-id="aab5b-131">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aab5b-131">**Usage**</span></span>  
  
 <span data-ttu-id="aab5b-132">**BM.exe ajouter-subscription-View :\<nom de la vue\> -alerte :\<nom de l’alerte\> - AccountName :\<nom de compte\> -Type : [fichier &#124; Email] [-messagerie :\<adresse de messagerie\> ] [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aab5b-132">**bm.exe add-subscription -View:\<view name\> -Alert:\<alert name\> -AccountName:\<account name\> -Type: [ File &#124; Email ][ -Email:\<e-mail address\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aab5b-133">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aab5b-133">**Parameters**</span></span>  
  
|<span data-ttu-id="aab5b-134">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aab5b-134">Parameter</span></span>|<span data-ttu-id="aab5b-135"> Description</span><span class="sxs-lookup"><span data-stu-id="aab5b-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aab5b-136">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="aab5b-136">View:\<view name\></span></span>|<span data-ttu-id="aab5b-137">Nom de la vue sur laquelle l'alerte est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aab5b-137">The name of the view on which the alert is specified.</span></span>|  
|<span data-ttu-id="aab5b-138">Alerte :\<nom de l’alerte\></span><span class="sxs-lookup"><span data-stu-id="aab5b-138">Alert:\<alert name\></span></span>|<span data-ttu-id="aab5b-139">Nom de l'alerte à laquelle s'abonner.</span><span class="sxs-lookup"><span data-stu-id="aab5b-139">The name of the alert to which to subscribe.</span></span>|  
|<span data-ttu-id="aab5b-140">AccountName :\<nom du compte\></span><span class="sxs-lookup"><span data-stu-id="aab5b-140">AccountName:\<account name\></span></span>|<span data-ttu-id="aab5b-141">Compte, au format domaine\utilisateur, à abonner à l'alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-141">The account, in domain\user format, to subscribe to the alert.</span></span>|  
|<span data-ttu-id="aab5b-142">Type : [Fichier &#124; Messagerie]</span><span class="sxs-lookup"><span data-stu-id="aab5b-142">Type: [ File &#124; Email ]</span></span>|<span data-ttu-id="aab5b-143">Type de livraison de l'alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-143">The delivery type of the alert.</span></span> <span data-ttu-id="aab5b-144">Si vous spécifiez un type de livraison par message électronique, vous devez inclure le paramètre de messagerie sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="aab5b-144">If you specify a delivery type of e-mail, you must include the e-mail parameter on the command line.</span></span>|  
|<span data-ttu-id="aab5b-145">Adresse de messagerie :\<adresse de messagerie\></span><span class="sxs-lookup"><span data-stu-id="aab5b-145">Email:\<e-mail address\></span></span>|<span data-ttu-id="aab5b-146">Facultatif : L’adresse de messagerie à laquelle la notification d’alerte soient remise.</span><span class="sxs-lookup"><span data-stu-id="aab5b-146">Optional: The email address to which the alert notification will be delivered.</span></span>|  
|<span data-ttu-id="aab5b-147">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aab5b-147">Server:\<server\></span></span>|<span data-ttu-id="aab5b-148">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="aab5b-148">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="aab5b-149">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="aab5b-149">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="aab5b-150">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aab5b-150">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aab5b-151">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aab5b-151">Database:\<database\></span></span>|<span data-ttu-id="aab5b-152">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="aab5b-152">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="aab5b-153">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aab5b-153">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aab5b-154">Ajoute au compte spécifié un abonnement à l'alerte spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aab5b-154">Adds a subscription for the specified account to the specified alert.</span></span>  
  
 <span data-ttu-id="aab5b-155">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aab5b-155">**Examples**</span></span>  
  
```  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:File  
bm.exe add-subscription -View:v1 -Alert:a2 -AccountName:domain\user -Type:Email -Email:useremail@domain.com  
```  
  
## <a name="remove-subscription-command"></a><span data-ttu-id="aab5b-156">Commande remove-subscription</span><span class="sxs-lookup"><span data-stu-id="aab5b-156">remove-subscription Command</span></span>  
 <span data-ttu-id="aab5b-157">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="aab5b-157">**Usage**</span></span>  
  
 <span data-ttu-id="aab5b-158">**BM.exe remove-subscription-View :\<nom de la vue\> -alerte :\<nom de l’alerte\> - AccountName :\<nom de compte\>[-Server :\<server\> ] [- Base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="aab5b-158">**bm.exe remove-subscription -View:\<view name\> -Alert:\<alert name\> -AccountName:\<account name\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="aab5b-159">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="aab5b-159">**Parameters**</span></span>  
  
|<span data-ttu-id="aab5b-160">Paramètre</span><span class="sxs-lookup"><span data-stu-id="aab5b-160">Parameter</span></span>|<span data-ttu-id="aab5b-161"> Description</span><span class="sxs-lookup"><span data-stu-id="aab5b-161">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aab5b-162">Affichage :\<nom de la vue\></span><span class="sxs-lookup"><span data-stu-id="aab5b-162">View:\<view name\></span></span>|<span data-ttu-id="aab5b-163">Nom de la vue sur laquelle l'alerte est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aab5b-163">The name of the view on which the alert is specified.</span></span>|  
|<span data-ttu-id="aab5b-164">Alerte :\<nom de l’alerte\></span><span class="sxs-lookup"><span data-stu-id="aab5b-164">Alert:\<alert name\></span></span>|<span data-ttu-id="aab5b-165">Le nom de l'alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-165">The name of the alert.</span></span>|  
|<span data-ttu-id="aab5b-166">AccountName :\<nom du compte\></span><span class="sxs-lookup"><span data-stu-id="aab5b-166">AccountName:\<account name\></span></span>|<span data-ttu-id="aab5b-167">Compte, au format domaine\utilisateur, à supprimer de l'alerte.</span><span class="sxs-lookup"><span data-stu-id="aab5b-167">The account, in domain\user format, to remove from the alert.</span></span>|  
|<span data-ttu-id="aab5b-168">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="aab5b-168">Server:\<server\></span></span>|<span data-ttu-id="aab5b-169">Facultatif : Le nom du serveur sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="aab5b-169">Optional: The name of the server on which the view resides.</span></span> <span data-ttu-id="aab5b-170">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="aab5b-170">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="aab5b-171">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="aab5b-171">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="aab5b-172">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="aab5b-172">Database:\<database\></span></span>|<span data-ttu-id="aab5b-173">Facultatif : Le nom de la base de données sur lequel réside la vue.</span><span class="sxs-lookup"><span data-stu-id="aab5b-173">Optional: The name of the database on which the view resides.</span></span> <span data-ttu-id="aab5b-174">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="aab5b-174">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="aab5b-175">Supprime l'abonnement du compte spécifié à l'alerte indiquée.</span><span class="sxs-lookup"><span data-stu-id="aab5b-175">Removes the subscription of the specified account from the specified alert.</span></span> <span data-ttu-id="aab5b-176">Tous les abonnements du compte spécifié sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="aab5b-176">All subscriptions for the specified account are removed.</span></span>  
  
 <span data-ttu-id="aab5b-177">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="aab5b-177">**Examples**</span></span>  
  
```  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:domain\user  
bm.exe remove-subscription -View:v1 -Alert:a2 -AccountName:user -Server:s1  
```  
  
## <a name="see-also"></a><span data-ttu-id="aab5b-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aab5b-178">See Also</span></span>  
 [<span data-ttu-id="aab5b-179">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="aab5b-179">BAM Management Utility</span></span>](../core/bam-management-utility.md)