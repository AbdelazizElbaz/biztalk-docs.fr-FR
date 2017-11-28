---
title: "Commandes de gestion d’infrastructure | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2f1a88c-19fc-4384-b6bb-f95962a32921
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae58ea03f394b0fe8b7223bdd810dbc72ccb2472
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="infrastructure-management-commands"></a><span data-ttu-id="6022f-102">Commandes de gestion d'infrastructure</span><span class="sxs-lookup"><span data-stu-id="6022f-102">Infrastructure Management Commands</span></span>
<span data-ttu-id="6022f-103">Les commandes de configuration de l'utilitaire de gestion de l'analyse BAM (BM) vous permettent d'obtenir et de mettre à jour la configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-103">The BAM Management (BM) utility configuration commands allow you get and update the BAM configuration.</span></span>  
  
-   <span data-ttu-id="6022f-104">Get-config : Obtient le fichier de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-104">get-config: Gets the BAM configuration file.</span></span>  
  
-   <span data-ttu-id="6022f-105">configuration de la mise à jour : met à jour la configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-105">update-config: Updates the BAM configuration.</span></span>  
  
-   <span data-ttu-id="6022f-106">Get-changes : répertorie les modifications de l’infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-106">get-changes: Lists changes to the BAM infrastructure.</span></span>  
  
-   <span data-ttu-id="6022f-107">Get-defxml : Obtient un fichier qui contient tous les artefacts dans la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-107">get-defxml: Gets a file containing all the artifacts in the BAM Primary Import database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6022f-108">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="6022f-108">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="6022f-109">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6022f-109">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="6022f-110">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="6022f-110">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6022f-111">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="6022f-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="get-config-command"></a><span data-ttu-id="6022f-112">Commande get-config</span><span class="sxs-lookup"><span data-stu-id="6022f-112">get-config Command</span></span>  
 <span data-ttu-id="6022f-113">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="6022f-113">**Usage**</span></span>  
  
 <span data-ttu-id="6022f-114">**BM.exe get-config - FileName :\<fichier de sortie > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="6022f-114">**bm.exe get-config -FileName:\<output file> [ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="6022f-115">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="6022f-115">**Parameters**</span></span>  
  
|<span data-ttu-id="6022f-116">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6022f-116">Parameter</span></span>|<span data-ttu-id="6022f-117"> Description</span><span class="sxs-lookup"><span data-stu-id="6022f-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6022f-118">Nom de fichier :\<fichier de sortie ></span><span class="sxs-lookup"><span data-stu-id="6022f-118">FileName:\<output file></span></span>|<span data-ttu-id="6022f-119">Chemin d'accès et nom de fichier à utiliser pour enregistrer le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6022f-119">The path and name to which to save the configuration file.</span></span>|  
|<span data-ttu-id="6022f-120">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="6022f-120">Server:\<server></span></span>|<span data-ttu-id="6022f-121">Facultatif : Le nom du serveur à partir duquel obtenir la configuration.</span><span class="sxs-lookup"><span data-stu-id="6022f-121">Optional: The name of the server from which to get the configuration.</span></span> <span data-ttu-id="6022f-122">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="6022f-122">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="6022f-123">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="6022f-123">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="6022f-124">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="6022f-124">Database:\<database></span></span>|<span data-ttu-id="6022f-125">Facultatif : Le nom de la base de données à partir duquel obtenir la configuration.</span><span class="sxs-lookup"><span data-stu-id="6022f-125">Optional: The name of the database from which to get the configuration.</span></span> <span data-ttu-id="6022f-126">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="6022f-126">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="6022f-127">Récupère le fichier XML de configuration BAM et l'enregistre dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="6022f-127">Retrieves the BAM configuration XML and saves it in the specified file.</span></span> <span data-ttu-id="6022f-128">Le **get-config** commande n’écrase pas le fichier existant.</span><span class="sxs-lookup"><span data-stu-id="6022f-128">The **get-config** command will not overwrite the existing file.</span></span>  
  
 <span data-ttu-id="6022f-129">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="6022f-129">**Examples**</span></span>  
  
```  
bm.exe get-config -FileName:MyConfig.xml  
bm.exe get-config -FileName:BAMConfiguration.xml -Server:OrdersServer  
```  
  
## <a name="update-config-command"></a><span data-ttu-id="6022f-130">Commande update-config</span><span class="sxs-lookup"><span data-stu-id="6022f-130">update-config Command</span></span>  
 <span data-ttu-id="6022f-131">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="6022f-131">**Usage**</span></span>  
  
 <span data-ttu-id="6022f-132">**BM.exe update-config - FileName :\<le fichier de configuration >**</span><span class="sxs-lookup"><span data-stu-id="6022f-132">**bm.exe update-config -FileName:\<config file>**</span></span>  
  
 <span data-ttu-id="6022f-133">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="6022f-133">**Parameters**</span></span>  
  
|<span data-ttu-id="6022f-134">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6022f-134">Parameter</span></span>|<span data-ttu-id="6022f-135"> Description</span><span class="sxs-lookup"><span data-stu-id="6022f-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6022f-136">Nom de fichier :\<le fichier de configuration ></span><span class="sxs-lookup"><span data-stu-id="6022f-136">FileName:\<config file></span></span>|<span data-ttu-id="6022f-137">Chemin d'accès et nom du fichier de configuration à l'aide duquel mettre à jour l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-137">The path and name of the configuration file from which to update the BAM infrastructure.</span></span>|  
  
 <span data-ttu-id="6022f-138">Met à jour la configuration de l'ordinateur local à partir d'un fichier XML de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-138">Updates the configuration on the local computer from a file containing BAM configuration XML.</span></span> <span data-ttu-id="6022f-139">Vous pouvez ajouter des noms de serveur et de base de données qui n'existent pas encore dans la configuration actuelle.</span><span class="sxs-lookup"><span data-stu-id="6022f-139">You can add server and database names that do not already exist in the current configuration.</span></span> <span data-ttu-id="6022f-140">La modification des noms de serveur ou de base de données disposant déjà d'une infrastructure dynamique déployée se soldera par un échec et bm.exe signalera une erreur.</span><span class="sxs-lookup"><span data-stu-id="6022f-140">Changing server or database names that already have dynamic infrastructure deployed in will fail and bm.exe will report an error.</span></span>  
  
 <span data-ttu-id="6022f-141">Si vous modifiez l'emplacement de dépôt du fichier pour les alertes envoyées sous forme de fichier,</span><span class="sxs-lookup"><span data-stu-id="6022f-141">If you modify the file drop location for alerts delivered by file.</span></span> <span data-ttu-id="6022f-142">vous devez redémarrer les services de notification SQL.</span><span class="sxs-lookup"><span data-stu-id="6022f-142">You must restart the SQL Notifications Services.</span></span> <span data-ttu-id="6022f-143">Si ces services ne sont pas redémarrés, les alertes continueront à être envoyées à l'emplacement d'origine destiné au dépôt du fichier.</span><span class="sxs-lookup"><span data-stu-id="6022f-143">If the NS service is not restarted, alerts will continue being delivered to the original file drop location.</span></span>  
  
 <span data-ttu-id="6022f-144">L'emplacement de dépôt du fichier se modifie en changeant la ligne suivante du fichier de configuration BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-144">The file drop location is changed by modifying the following line of the BAM configuration file.</span></span>  
  
 <span data-ttu-id="6022f-145">\<Nom de la propriété = « FileDropUNC » >\\\\< nom de l’ordinateur\>\alerts\<cette propriété ></span><span class="sxs-lookup"><span data-stu-id="6022f-145">\<Property Name="FileDropUNC">\\\\<computer name\>\alerts\</Property></span></span>  
  
 <span data-ttu-id="6022f-146">Pour connaître la procédure mettre à jour les références, consultez [sauvegarde et restauration de BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="6022f-146">For appropriate steps to update the references, see [Backing Up and Restoring BizTalk Server](../core/backing-up-and-restoring-biztalk-server.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6022f-147">Si vous exécutez une commande update-database, avec un fichier de configuration BAM ne contenant pas de section d'alertes, et que vous avez déjà configuré des alertes BAM, bm.exe écrasera la configuration de sorte que les alertes ne fonctionneront plus.</span><span class="sxs-lookup"><span data-stu-id="6022f-147">If you execute an update-database command, using a BAM configuration file that does not contain an alerts section, and you have already configured BAM Alerts, bm.exe will overwrite the configuration such that alerts will no longer function.</span></span>  
  
 <span data-ttu-id="6022f-148">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="6022f-148">**Examples**</span></span>  
  
```  
bm.exe update-config -FileName:MyConfig.xml  
```  
  
## <a name="get-changes-command"></a><span data-ttu-id="6022f-149">Commande get-changes</span><span class="sxs-lookup"><span data-stu-id="6022f-149">get-changes Command</span></span>  
 <span data-ttu-id="6022f-150">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="6022f-150">**Usage**</span></span>  
  
 <span data-ttu-id="6022f-151">**BM.exe get-changes [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="6022f-151">**bm.exe get-changes [ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="6022f-152">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="6022f-152">**Parameters**</span></span>  
  
|<span data-ttu-id="6022f-153">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6022f-153">Parameter</span></span>|<span data-ttu-id="6022f-154"> Description</span><span class="sxs-lookup"><span data-stu-id="6022f-154">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6022f-155">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="6022f-155">Server:\<server></span></span>|<span data-ttu-id="6022f-156">Facultatif : Le nom du serveur sur lequel réside la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-156">Optional: The name of the server on which the BAM Primary Import database resides.</span></span> <span data-ttu-id="6022f-157">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="6022f-157">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="6022f-158">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="6022f-158">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="6022f-159">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="6022f-159">Database:\<database></span></span>|<span data-ttu-id="6022f-160">Facultatif : Si le nom n’est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="6022f-160">Optional: If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="6022f-161">Obtient une liste de modifications appliquées à la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-161">Gets a list of changes applied to the BAM Primary Import database.</span></span> <span data-ttu-id="6022f-162">Vous pouvez utiliser cette commande pour vérifier les modifications de l'infrastructure de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="6022f-162">You can use this command to audit changes to the BAM Infrastructure.</span></span> <span data-ttu-id="6022f-163">La commande renvoie les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6022f-163">The command returns the following information:</span></span>  
  
 <span data-ttu-id="6022f-164">Le type de commande de la modification et le fichier à partir duquel la modification a été appliquée.</span><span class="sxs-lookup"><span data-stu-id="6022f-164">The command type of the change and the file from which the change was applied.</span></span>  
  
 <span data-ttu-id="6022f-165">L'utilisateur ayant appliqué la modification.</span><span class="sxs-lookup"><span data-stu-id="6022f-165">Who applied the change.</span></span>  
  
 <span data-ttu-id="6022f-166">Les activités qui ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="6022f-166">Which activities were changed.</span></span>  
  
 <span data-ttu-id="6022f-167">Les vues qui ont été modifiées.</span><span class="sxs-lookup"><span data-stu-id="6022f-167">Which views were changed.</span></span>  
  
 <span data-ttu-id="6022f-168">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="6022f-168">**Examples**</span></span>  
  
```  
bm.exe get-changes  
```  
  
 <span data-ttu-id="6022f-169">Résultat de la commande</span><span class="sxs-lookup"><span data-stu-id="6022f-169">Output of command</span></span>  
  
 <span data-ttu-id="6022f-170">\#1 : déployer c:\bam\ordermanagement.xml</span><span class="sxs-lookup"><span data-stu-id="6022f-170">\#1: Deploy c:\bam\ordermanagement.xml</span></span>  
  
 <span data-ttu-id="6022f-171">By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).</span><span class="sxs-lookup"><span data-stu-id="6022f-171">By domain\user at 12/30/2005 8:17:08 PM (v3.5.1536.0).</span></span>  
  
 <span data-ttu-id="6022f-172">Activités : OrderMgmt</span><span class="sxs-lookup"><span data-stu-id="6022f-172">Activities: OrderMgmt</span></span>  
  
 <span data-ttu-id="6022f-173">Vues : SalesManager</span><span class="sxs-lookup"><span data-stu-id="6022f-173">Views: SalesManager</span></span>  
  
## <a name="get-defxml-command"></a><span data-ttu-id="6022f-174">Commande get-defxml</span><span class="sxs-lookup"><span data-stu-id="6022f-174">get-defxml Command</span></span>  
 <span data-ttu-id="6022f-175">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="6022f-175">**Usage**</span></span>  
  
 <span data-ttu-id="6022f-176">**BM.exe get-defxml - FileName :\<fichier de sortie > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="6022f-176">**bm.exe get-defxml -FileName:\<output file>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="6022f-177">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="6022f-177">**Parameters**</span></span>  
  
|<span data-ttu-id="6022f-178">Paramètre</span><span class="sxs-lookup"><span data-stu-id="6022f-178">Parameter</span></span>|<span data-ttu-id="6022f-179"> Description</span><span class="sxs-lookup"><span data-stu-id="6022f-179">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6022f-180">Nom de fichier :\<fichier de sortie ></span><span class="sxs-lookup"><span data-stu-id="6022f-180">FileName:\<output file></span></span>|<span data-ttu-id="6022f-181">Chemin d'accès et nom du fichier dans lequel enregistrer les définitions.</span><span class="sxs-lookup"><span data-stu-id="6022f-181">The path and name of the file to which to save the definitions.</span></span>|  
|<span data-ttu-id="6022f-182">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="6022f-182">Server:\<server></span></span>|<span data-ttu-id="6022f-183">Facultatif : Le nom du serveur à partir duquel obtenir les définitions.</span><span class="sxs-lookup"><span data-stu-id="6022f-183">Optional: The name of the server from which to get the definitions.</span></span> <span data-ttu-id="6022f-184">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="6022f-184">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="6022f-185">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="6022f-185">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="6022f-186">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="6022f-186">Database:\<database></span></span>|<span data-ttu-id="6022f-187">Facultatif : Le nom de la base de données à partir duquel obtenir les définitions.</span><span class="sxs-lookup"><span data-stu-id="6022f-187">Optional: The name of the database from which to get the definitions.</span></span> <span data-ttu-id="6022f-188">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="6022f-188">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="6022f-189">Extrait tous les artefacts de la base de données d'importation principale BAM et les enregistre dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="6022f-189">Retrieves all artifacts on from the BAM Primary Import database and saves them in a file as XML.</span></span> <span data-ttu-id="6022f-190">La commande n'écrase pas les fichiers existants.</span><span class="sxs-lookup"><span data-stu-id="6022f-190">The command will not overwrite existing files.</span></span>  
  
 <span data-ttu-id="6022f-191">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="6022f-191">**Examples**</span></span>  
  
```  
bm.exe get-defxml -FileName:BAMDefinition.xml  
bm.exe get-defxml -FileName:MyDef.xml -Server:MyServer -Database:MyPI  
```  
  
## <a name="see-also"></a><span data-ttu-id="6022f-192">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6022f-192">See Also</span></span>  
 [<span data-ttu-id="6022f-193">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="6022f-193">BAM Management Utility</span></span>](../core/bam-management-utility.md)