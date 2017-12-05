---
title: "Commandes de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c54131-0793-45a9-822a-554cd4fc05a2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2232602ec5a91768f4b9dbde5f6c63a79de0c332
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="database-commands"></a><span data-ttu-id="b8d9d-102">Commandes de base de données</span><span class="sxs-lookup"><span data-stu-id="b8d9d-102">Database Commands</span></span>
<span data-ttu-id="b8d9d-103">Les commandes de la base de données de l'utilitaire de gestion de l'analyse BAM vous permettent d'utiliser les bases de données BAM :</span><span class="sxs-lookup"><span data-stu-id="b8d9d-103">The BAM Management utility database commands allow you to work with the BAM databases:</span></span>  
  
-   <span data-ttu-id="b8d9d-104">bases de données de configuration : crée les bases de données BAM spécifique.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-104">setup-databases: Creates the BAM-specific databases.</span></span>  
  
-   <span data-ttu-id="b8d9d-105">sql migration : migration de vos bases de données BAM à partir de :</span><span class="sxs-lookup"><span data-stu-id="b8d9d-105">migrate-sql: Migrates your BAM databases from:</span></span>  
  
    -   <span data-ttu-id="b8d9d-106">Microsoft SQL Server 2000 vers Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="b8d9d-106">Microsoft SQL Server 2000 to Microsoft SQL Server 2008</span></span>  
  
    -   <span data-ttu-id="b8d9d-107">Microsoft SQL Server 2005 vers Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="b8d9d-107">Microsoft SQL Server 2005 to Microsoft SQL Server 2008</span></span>  
  
-   <span data-ttu-id="b8d9d-108">Enable-reference : active une référence à une base de données d’importation principale BAM distribuée.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-108">enable-reference: Enables a reference to a distributed BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="b8d9d-109">Get-references : Obtient une liste de références aux bases de données importation principale BAM distribuées.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-109">get-references: Gets a list of references to distributed BAM Primary Import databases.</span></span>  
  
-   <span data-ttu-id="b8d9d-110">Disable-reference : désactive une référence à une base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-110">disable-reference: Disables a reference to a BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9d-111">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-111">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="b8d9d-112">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-112">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="b8d9d-113">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-113">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9d-114">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-114">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="setup-databases-command"></a><span data-ttu-id="b8d9d-115">Commande setup-databases</span><span class="sxs-lookup"><span data-stu-id="b8d9d-115">setup-databases Command</span></span>  
 <span data-ttu-id="b8d9d-116">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-116">**Usage**</span></span>  
  
 <span data-ttu-id="b8d9d-117">**le programme d’installation-bases de données-ConfigFile BM.exe :\<fichier de configuration\>[- NSUser :\<nom d’utilisateur du service de notifications\> ] [- NSUserPassword :\<motdepasseduservicedenotifications\> ]**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-117">**bm.exe setup-databases-ConfigFile:\<configuration file\>[ -NSUser:\<notifications service user name\> ][ -NSUserPassword:\<notifications service user password\> ]**</span></span>  
  
 <span data-ttu-id="b8d9d-118">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-118">**Parameters**</span></span>  
  
|<span data-ttu-id="b8d9d-119">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b8d9d-119">Parameter</span></span>|<span data-ttu-id="b8d9d-120"> Description</span><span class="sxs-lookup"><span data-stu-id="b8d9d-120">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8d9d-121">ConfigFile :\<fichier de configuration\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-121">ConfigFile:\<configuration file\></span></span>|<span data-ttu-id="b8d9d-122">Fichier de configuration BAM à partir duquel créer la base de données.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-122">The BAM configuration file from which to create the database.</span></span>|  
|<span data-ttu-id="b8d9d-123">NSUser :\<nom d’utilisateur du service de notifications\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-123">NSUser:\<notifications service user name\></span></span>|<span data-ttu-id="b8d9d-124">Facultatif : L’ID utilisateur d’un utilisateur de services de notifications autorisé à créer des bases de données.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-124">Optional: The user ID of a notifications services user with permissions to create databases.</span></span>|  
|<span data-ttu-id="b8d9d-125">NSUserPassword</span><span class="sxs-lookup"><span data-stu-id="b8d9d-125">NSUserPassword</span></span>|<span data-ttu-id="b8d9d-126">Facultatif : Le mot de passe pour l’utilisateur de services de notifications spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-126">Optional: The password for the specified notifications services user.</span></span>|  
  
 <span data-ttu-id="b8d9d-127">Crée les bases de données décrites dans le fichier de configuration (Importation principale BAM, Schémas en étoile BAM, Archives de l'analyse BAM, Analyse BAM et alertes) si elles n'existent pas déjà.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-127">Creates the databases described in the configuration file (BAM Primary Import, BAM Star Schema, BAM Archive, BAM Analysis, and alerts) if they do not already exist.</span></span> <span data-ttu-id="b8d9d-128">Une fois les bases de données créées, la commande génère les procédures stockées et les tables de métadonnées BAM associées.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-128">Once the databases are created, the command creates the associated BAM metadata tables and stored procedures.</span></span>  
  
 <span data-ttu-id="b8d9d-129">Les paramètres NSUser et NSUserPassword sont obligatoires si vous configurez des alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-129">The NSUser and NSUserPassword parameters are required if you are setting up BAM alerts.</span></span> <span data-ttu-id="b8d9d-130">Si NSUserPassword n'est pas spécifié sur la ligne de commande, bm.exe vous invite à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-130">If the NSUserPassword is not specified on the command line, bm.exe prompts you for the password.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9d-131">À l'issue de l'exécution de la commande, il est possible qu'une exception en provenance d'AlertModule figure dans le journal de suivi :</span><span class="sxs-lookup"><span data-stu-id="b8d9d-131">After the completion of the command, you may note an exception from the AlertModule in the trace log:</span></span>  
>   
>  <span data-ttu-id="b8d9d-132">« Le compte spécifié correspond au propriétaire de la base de données.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-132">"The specified account is the Database Owner.</span></span> <span data-ttu-id="b8d9d-133">Celui-ci peut toujours accéder à la vue, il ne peut être ajouté à la vue ou supprimé de celle-ci. »</span><span class="sxs-lookup"><span data-stu-id="b8d9d-133">The Database owner always has access to the view and cannot be added to or removed from the view."</span></span>  
>   
>  <span data-ttu-id="b8d9d-134">En outre, vous pouvez voir un avertissement dans l'événement provenant de NotificationServices#19001.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-134">In addition, you may see a warning in the event from NotificationServices #19001.</span></span>  
>   
>  <span data-ttu-id="b8d9d-135">Si aucune erreur n'a été signalée lors de l'exécution de la commande, vous pouvez ignorer ces avertissements.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-135">If no errors were reported during the execution of the command, you can safely disregard these notices.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8d9d-136">Si vous exécutez une commande setup-database, avec un fichier de configuration BAM ne contenant pas de section d'alertes, et que vous avez déjà configuré des alertes BAM, bm.exe écrasera la configuration de sorte que les alertes ne fonctionneront plus.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-136">If you execute a setup-database command, using a BAM configuration file that does not contain an alerts section, and you have already configured BAM Alerts, bm.exe will overwrite the configuration such that alerts will no longer function.</span></span>  
  
 <span data-ttu-id="b8d9d-137">Pour configurer les bases de données BAM, vous devez disposer des autorisations d'administrateur sur le serveur Microsoft SQL hébergeant les bases de données BAMPrimaryImport, BAMStarSchema et BAMArchive.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-137">To set up the BAM databases you must have administrator permissions on the Microsoft SQL server hosting the BAMPrimaryImport, BAMStarSchema, and BAMArchive databases.</span></span> <span data-ttu-id="b8d9d-138">Pour configurer les bases de données des services de notification SQL, vous devez disposer des autorisations d'administrateur et être membre du groupe des administrateurs locaux et de tout autre groupe d'administration ayant été configuré, par exemple le groupe des administrateurs BTS.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-138">To set up SQL Notification Services databases, you must have administrator permissions and be a member of the local administrators group, as well as be a member of any other additional administrative groups that have been configured, such as the BTS Admins group.</span></span>  
  
 <span data-ttu-id="b8d9d-139">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-139">**Examples**</span></span>  
  
```  
bm.exe setup-databases -ConfigFile:BamConfiguration.xml  
bm.exe setup-databases -ConfigFile:cfg.xml -NSUser:domain\user1  
```  
  
## <a name="migrate-sql-command"></a><span data-ttu-id="b8d9d-140">Commande migrate-sql</span><span class="sxs-lookup"><span data-stu-id="b8d9d-140">migrate-sql Command</span></span>  
 <span data-ttu-id="b8d9d-141">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-141">**Usage**</span></span>  
  
 <span data-ttu-id="b8d9d-142">**BM.exe migrer-sql-à partir de : sql2000-pour : sql2008 [- NSUser :\<nom d’utilisateur du service de notifications\> ] [- NSUserPassword :\<mot de passe utilisateur du service de notifications\> ] [-Server :\<server\> ] [-Base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-142">**bm.exe migrate-sql -From:sql2000 -To:sql2008 [ -NSUser:\<notifications service user name\> ][ -NSUserPassword:\<notifications service user password\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="b8d9d-143">\- Ou -</span><span class="sxs-lookup"><span data-stu-id="b8d9d-143">\- Or -</span></span>  
  
 <span data-ttu-id="b8d9d-144">**BM.exe migrer-sql-à partir de : sql2005-pour : sql2008 [- NSUser :\<nom d’utilisateur du service de notifications\> ] [- NSUserPassword :\<mot de passe utilisateur du service de notifications\> ] [-Server :\<server\> ] [-Base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-144">**bm.exe migrate-sql -From:sql2005 -To:sql2008 [ -NSUser:\<notifications service user name\> ][ -NSUserPassword:\<notifications service user password\> ][ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="b8d9d-145">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-145">**Parameters**</span></span>  
  
|<span data-ttu-id="b8d9d-146">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b8d9d-146">Parameter</span></span>|<span data-ttu-id="b8d9d-147"> Description</span><span class="sxs-lookup"><span data-stu-id="b8d9d-147">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8d9d-148">À partir de : sql2000</span><span class="sxs-lookup"><span data-stu-id="b8d9d-148">From: sql2000</span></span>|<span data-ttu-id="b8d9d-149">Spécifie que vous convertissez des données d'une base de données Microsoft SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-149">Specifies that you are converting from a Microsoft SQL Server 2000 database.</span></span>|  
|<span data-ttu-id="b8d9d-150">To:sql2008</span><span class="sxs-lookup"><span data-stu-id="b8d9d-150">To:sql2008</span></span>|<span data-ttu-id="b8d9d-151">Spécifie que vous convertissez une base de données Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-151">Specifies that you are converting to a Microsoft SQL Server 2008 database.</span></span>|  
|<span data-ttu-id="b8d9d-152">À partir de : sql2005</span><span class="sxs-lookup"><span data-stu-id="b8d9d-152">From: sql2005</span></span>|<span data-ttu-id="b8d9d-153">Spécifie que vous effectuez une conversion à partir d’une base de données Microsoft SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-153">Specifies that you are converting from a Microsoft SQL Server 2005 database.</span></span>|  
|<span data-ttu-id="b8d9d-154">To:sql2008</span><span class="sxs-lookup"><span data-stu-id="b8d9d-154">To:sql2008</span></span>|<span data-ttu-id="b8d9d-155">Spécifie que vous convertissez une base de données Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-155">Specifies that you are converting to a Microsoft SQL Server 2008 database.</span></span>|  
|<span data-ttu-id="b8d9d-156">NSUser :\<nom d’utilisateur du service de notifications\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-156">NSUser:\<notifications service user name\></span></span>|<span data-ttu-id="b8d9d-157">Facultatif : L’ID utilisateur d’un utilisateur des Services de Notifications autorisé à créer des bases de données.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-157">Optional: The user ID of a Notifications Services user with permissions to create databases.</span></span>|  
|<span data-ttu-id="b8d9d-158">NSUserPassword</span><span class="sxs-lookup"><span data-stu-id="b8d9d-158">NSUserPassword</span></span>|<span data-ttu-id="b8d9d-159">Facultatif : Le mot de passe pour l’utilisateur des Services de Notifications spécifié.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-159">Optional: The password for the specified Notifications Services user.</span></span>|  
|<span data-ttu-id="b8d9d-160">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-160">Server:\<server\></span></span>|<span data-ttu-id="b8d9d-161">Facultatif : Le nom du serveur sur lequel réside la base de données convertie.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-161">Optional: The name of the server on which the converted database will reside.</span></span> <span data-ttu-id="b8d9d-162">Le serveur doit être dans le même domaine que l’ordinateur qui héberge la base de données Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-162">The server must be in the same domain as the computer hosting the Microsoft SQL Server 2008 database.</span></span> <span data-ttu-id="b8d9d-163">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-163">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b8d9d-164">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-164">Database:\<database\></span></span>|<span data-ttu-id="b8d9d-165">Facultatif : Tapez le nom de la base de données convertie.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-165">Optional: Then name of the converted database.</span></span> <span data-ttu-id="b8d9d-166">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-166">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b8d9d-167">Fait migrer l’infrastructure BAM à partir de Microsoft SQL Server 2000 ou Microsoft SQL Server 2005 vers Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-167">Migrates the BAM infrastructure from Microsoft SQL Server 2000 or Microsoft SQL Server 2005 to Microsoft SQL Server 2008.</span></span> <span data-ttu-id="b8d9d-168">Utilisez cette commande une fois que vous mettez à niveau votre serveur de base de données et le serveur d’analyse à partir de Microsoft SQL Server 2000 ou Microsoft SQL Server 2005 vers Microsoft SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-168">Use this command after you upgrade your database server and Analysis server from Microsoft SQL Server 2000 or Microsoft SQL Server 2005 to Microsoft SQL Server 2008.</span></span>  
  
 <span data-ttu-id="b8d9d-169">Les paramètres NSUser et NSUserPassword sont requis si les alertes BAM sont configurées.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-169">The NSUser and NSUserPassword parameters are required if BAM alerts are configured.</span></span> <span data-ttu-id="b8d9d-170">Si NSUserPassword n'est pas spécifié sur la ligne de commande, bm.exe vous invite à entrer le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-170">If the NSUserPassword is not specified on the command line, bm.exe prompts you for the password.</span></span>  
  
 <span data-ttu-id="b8d9d-171">Pour faire migrer les bases de données des services de notification SQL Server, vous devez disposer des autorisations d'administrateur et être membre du groupe des administrateurs locaux et de tout autre groupe d'administration ayant été configuré, par exemple le groupe des administrateurs BTS.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-171">To migrate the SQL Server Notification Services databases, you must have administrator permissions and be a member of the local administrators group, as well as be a member of any other additional administrative groups that have been configured, such as the BTS Admins group.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9d-172">Si vous recevez le message d’erreur « Erreur : Impossible de démarrer le service NS$ BAMAlerts sur l’ordinateur '\<nom de l’ordinateur\>'.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-172">If you receive the error message "ERROR: Cannot start service NS$BAMAlerts on computer '\<computer name\>'.</span></span> <span data-ttu-id="b8d9d-173">car le service n'a pas répondu à la demande de démarrage ou de contrôle en temps voulu s'affiche, essayez de redémarrer le service manuellement.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-173">The service did not respond to the start or control request in a timely fashion.", try restarting the service manually.</span></span> <span data-ttu-id="b8d9d-174">Si le serveur SQL est très occupé pendant la migration, le service risque de ne pas redémarrer.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-174">If the SQL Server is extremely busy during a migration, the service may not restart.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8d9d-175">Pour exécuter la commande migrate-sql sur l'ordinateur sur lequel est installé Notification Services, vous devez être membre du groupe des administrateurs locaux de cet ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-175">To run the migrate-sql command on the computer where Notification Services is installed, you must belong to the Local Administrators group on that computer.</span></span>  
  
 <span data-ttu-id="b8d9d-176">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-176">**Examples**</span></span>  
  
```  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2000 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
```  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -NSUser:domain\user1  
bm.exe migrate-sql -From:sql2005 -To:sql2008 -Server:MyServer -Database:db1  
```  
  
## <a name="enable-reference-command"></a><span data-ttu-id="b8d9d-177">Commande enable-reference</span><span class="sxs-lookup"><span data-stu-id="b8d9d-177">enable-reference Command</span></span>  
 <span data-ttu-id="b8d9d-178">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-178">**Usage**</span></span>  
  
 <span data-ttu-id="b8d9d-179">**BM.exe enable-reference - TargetServer :\<serveur cible\> - TargetDatabase :\<base de données cible\>[-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-179">**bm.exe enable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="b8d9d-180">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-180">**Parameters**</span></span>  
  
|<span data-ttu-id="b8d9d-181">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b8d9d-181">Parameter</span></span>|<span data-ttu-id="b8d9d-182"> Description</span><span class="sxs-lookup"><span data-stu-id="b8d9d-182">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8d9d-183">TargetServer :\<serveur cible\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-183">TargetServer:\<target server\></span></span>|<span data-ttu-id="b8d9d-184">Nom du serveur sur lequel la référence est activée.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-184">The name of the server to which the reference is enabled.</span></span> <span data-ttu-id="b8d9d-185">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-185">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="b8d9d-186">TargetDatabase :\<base de données cible\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-186">TargetDatabase:\<target database\></span></span>|<span data-ttu-id="b8d9d-187">Nom de la base de données sur laquelle la référence est activée.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-187">The name of the database to which the reference is enabled.</span></span>|  
|<span data-ttu-id="b8d9d-188">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-188">Server:\<server\></span></span>|<span data-ttu-id="b8d9d-189">Facultatif : Le nom du serveur qui a une référence activée vers le serveur cible et la base de données.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-189">Optional: The name of the server which will have a reference enabled to the target server and database.</span></span> <span data-ttu-id="b8d9d-190">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-190">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b8d9d-191">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-191">Database:\<database\></span></span>|<span data-ttu-id="b8d9d-192">Facultatif : Le nom de la base de données qui ont une référence activée vers le serveur cible et la base de données.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-192">Optional: The name of the database which will have a reference enabled to the target server and database.</span></span> <span data-ttu-id="b8d9d-193">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-193">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b8d9d-194">Active une référence vers une autre base de données d'importation principale BAM distribuée.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-194">Enables a reference to another distributed BAM Primary Import database.</span></span> <span data-ttu-id="b8d9d-195">Ceci autorise les abonnements de la base de données actuelle vers les métadonnées de vue et d'activité sur la base de données d'importation principale BAM cible.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-195">This allows subscriptions from the current database to the view and activity metadata on the target BAM Primary Import database.</span></span> <span data-ttu-id="b8d9d-196">Utilisez cette fonctionnalité pour permettre la navigation entre les activités distribuées.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-196">You use this to enable navigation of the distributed activities.</span></span>  
  
 <span data-ttu-id="b8d9d-197">Vous pouvez spécifier le serveur cible en tant qu'instance du serveur SQL Server, par exemple 'mamachine2\moninstance'.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-197">You can specify the target server as an instance of SQL Server, for example, 'mymachine2\myinstance'.</span></span>  
  
 <span data-ttu-id="b8d9d-198">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-198">**Examples**</span></span>  
  
```  
bm.exe enable-reference -TargetServer:MySrv -TargetDatabase:BamPrimaryImport  
bm.exe enable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="get-references-command"></a><span data-ttu-id="b8d9d-199">Commande get-references</span><span class="sxs-lookup"><span data-stu-id="b8d9d-199">get-references Command</span></span>  
 <span data-ttu-id="b8d9d-200">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-200">**Usage**</span></span>  
  
 <span data-ttu-id="b8d9d-201">**BM.exe get-references [-Server :\<server\> ] [-base de données :\<base de données\> ]**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-201">**bm.exe get-references [ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="b8d9d-202">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-202">**Parameters**</span></span>  
  
|<span data-ttu-id="b8d9d-203">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b8d9d-203">Parameter</span></span>|<span data-ttu-id="b8d9d-204"> Description</span><span class="sxs-lookup"><span data-stu-id="b8d9d-204">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8d9d-205">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-205">Server:\<server\></span></span>|<span data-ttu-id="b8d9d-206">Facultatif : Le nom du serveur sur laquelle obtenir une liste de références.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-206">Optional: The name of the server on which to get a list of references.</span></span> <span data-ttu-id="b8d9d-207">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-207">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b8d9d-208">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-208">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b8d9d-209">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-209">Database:\<database\></span></span>|<span data-ttu-id="b8d9d-210">Facultatif : Le nom de la base de données sur laquelle obtenir une liste de références.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-210">Optional: The name of the database on which to get a list of references.</span></span> <span data-ttu-id="b8d9d-211">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-211">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b8d9d-212">Répertorie les références activées sur l'ordinateur sur lequel la commande est exécutée.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-212">Lists the references enabled on the computer on which the command is executed.</span></span>  
  
 <span data-ttu-id="b8d9d-213">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-213">**Examples**</span></span>  
  
```  
bm.exe get-references  
bm.exe get-references -Server:MyServer -Database:MyPrimaryImport  
```  
  
## <a name="disable-reference-command"></a><span data-ttu-id="b8d9d-214">Commande disable-reference</span><span class="sxs-lookup"><span data-stu-id="b8d9d-214">disable-reference Command</span></span>  
 <span data-ttu-id="b8d9d-215">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-215">**Usage**</span></span>  
  
 <span data-ttu-id="b8d9d-216">**BM.exe disable-reference - TargetServer :\<serveur cible\> - TargetDatabase :\<base de données cible\>[-Server :\<server\> ] [-base de données :\<base de données \> ]**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-216">**bm.exe disable-reference -TargetServer:\<target server\> -TargetDatabase:\<target database\>[ -Server:\<server\> ][ -Database:\<database\> ]**</span></span>  
  
 <span data-ttu-id="b8d9d-217">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-217">**Parameters**</span></span>  
  
|<span data-ttu-id="b8d9d-218">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b8d9d-218">Parameter</span></span>|<span data-ttu-id="b8d9d-219"> Description</span><span class="sxs-lookup"><span data-stu-id="b8d9d-219">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8d9d-220">TargetServer :\<serveur cible\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-220">TargetServer:\<target server\></span></span>|<span data-ttu-id="b8d9d-221">Nom du serveur sur lequel désactiver les références.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-221">The name of the server on which to disable the references.</span></span> <span data-ttu-id="b8d9d-222">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-222">The server must be in the same domain as the computer from which you are running bm.exe.</span></span>|  
|<span data-ttu-id="b8d9d-223">TargetDatabase :\<base de données cible\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-223">TargetDatabase:\<target database\></span></span>|<span data-ttu-id="b8d9d-224">Nom de la base de données sur laquelle désactiver les références.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-224">The name of the database on which to disable the references.</span></span>|  
|<span data-ttu-id="b8d9d-225">Serveur :\<server\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-225">Server:\<server\></span></span>|<span data-ttu-id="b8d9d-226">Facultatif : Le nom du serveur sur lequel les références à la cible de serveur et base de données doivent être désactivées.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-226">Optional: The name of the server on which references to the target server and database are to be disabled.</span></span> <span data-ttu-id="b8d9d-227">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-227">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="b8d9d-228">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-228">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="b8d9d-229">Base de données :\<base de données\></span><span class="sxs-lookup"><span data-stu-id="b8d9d-229">Database:\<database\></span></span>|<span data-ttu-id="b8d9d-230">Facultatif : Le nom de la base de données sur laquelle les références vers le serveur cible et la base de données doivent être désactivées.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-230">Optional: The name of the database on which references to the target server and database are to be disabled.</span></span> <span data-ttu-id="b8d9d-231">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-231">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="b8d9d-232">Désactive une référence vers une autre base de données d'importation principale BAM distribuée sur le serveur cible.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-232">Disables a reference to another distributed BAM Primary Import database on the target server.</span></span>  
  
 <span data-ttu-id="b8d9d-233">Vous pouvez spécifier le serveur cible en tant qu'instance du serveur SQL Server, par exemple 'mamachine2\moninstance'.</span><span class="sxs-lookup"><span data-stu-id="b8d9d-233">You can specify the target server as an instance of SQL Server, for example, 'mymachine2\myinstance'.</span></span>  
  
 <span data-ttu-id="b8d9d-234">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="b8d9d-234">**Examples**</span></span>  
  
```  
bm.exe disable-reference -TargetServer:MySrv -TargetDatabase:BamPI  
bm.exe disable-reference -TargetServer:s2 -TargetDatabase:db1 -Server:s1  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8d9d-235">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8d9d-235">See Also</span></span>  
 [<span data-ttu-id="b8d9d-236">Utilitaire de gestion de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="b8d9d-236">BAM Management Utility</span></span>](../core/bam-management-utility.md)