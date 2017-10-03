---
title: "Déploiement des commandes de définition (modèle d’Observation) BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7914f3-7a92-4ab2-bd0e-94a2eed4825e
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 847dd40bc7d0e8fe9ec225ad8af45d06c92d7b63
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deployment-of-bam-definition-observation-model-commands"></a><span data-ttu-id="89e65-102">Commandes de déploiement de définitions BAM (modèle d'observation)</span><span class="sxs-lookup"><span data-stu-id="89e65-102">Deployment of BAM Definition (Observation Model) Commands</span></span>
<span data-ttu-id="89e65-103">Les commandes de déploiement de l'utilitaire de gestion de l'analyse BAM vous permettent d'appliquer, de modifier et de supprimer des définitions.</span><span class="sxs-lookup"><span data-stu-id="89e65-103">The BAM management utility deployment commands allow you to apply, modify, and remove definitions.</span></span>  
  
-   <span data-ttu-id="89e65-104">déployer-all : déploie une définition BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-104">deploy-all: Deploys a BAM definition.</span></span>  
  
-   <span data-ttu-id="89e65-105">mise à jour-all : met à jour une définition BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-105">update-all: Updates a BAM definition.</span></span>  
  
-   <span data-ttu-id="89e65-106">Remove-all : supprime une définition BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-106">remove-all: Removes a BAM definition.</span></span>  
  
-   <span data-ttu-id="89e65-107">mise à jour-livedataworkbook : met à jour les informations de connexion de base de données dans un classeur de données actives.</span><span class="sxs-lookup"><span data-stu-id="89e65-107">update-livedataworkbook: Updates the database connection information in a live data workbook.</span></span>  
  
-   <span data-ttu-id="89e65-108">Regenerate-livedataworkbook : régénère le classeur de données actives sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="89e65-108">regenerate-livedataworkbook: Regenerates the live data workbook on the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e65-109">Vous pouvez activer le traçage sur n’importe quelle commande d’utilitaire BM en incluant le **-Trace : sur &#124; off** commutateur de paramètre.</span><span class="sxs-lookup"><span data-stu-id="89e65-109">You can enable tracing on any BM utility command by including the **-Trace:on&#124;off** parameter switch.</span></span> <span data-ttu-id="89e65-110">L'utilisation du commutateur de suivi remplace les paramètres de suivi du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="89e65-110">Using the Trace switch overrides the tracing settings in the configuration file.</span></span> <span data-ttu-id="89e65-111">Le commutateur peut être utilisé conjointement avec toute commande BAM classique.</span><span class="sxs-lookup"><span data-stu-id="89e65-111">The switch can be used in conjunction with any normal BM command.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e65-112">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="89e65-112">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
## <a name="deploy-all-command"></a><span data-ttu-id="89e65-113">Commande deploy-all</span><span class="sxs-lookup"><span data-stu-id="89e65-113">deploy-all Command</span></span>  
 <span data-ttu-id="89e65-114">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="89e65-114">**Usage**</span></span>  
  
 <span data-ttu-id="89e65-115">**BM.exe déployer-all - DefinitionFile :\<fichier def > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="89e65-115">**bm.exe deploy-all -DefinitionFile:\<def file>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="89e65-116">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="89e65-116">**Parameters**</span></span>  
  
|<span data-ttu-id="89e65-117">Paramètre</span><span class="sxs-lookup"><span data-stu-id="89e65-117">Parameter</span></span>|<span data-ttu-id="89e65-118"> Description</span><span class="sxs-lookup"><span data-stu-id="89e65-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89e65-119">DefinitionFile :\<fichier def ></span><span class="sxs-lookup"><span data-stu-id="89e65-119">DefinitionFile:\<def file></span></span>|<span data-ttu-id="89e65-120">Chemin d'accès et nom du fichier contenant les définitions à déployer.</span><span class="sxs-lookup"><span data-stu-id="89e65-120">The path and name of the file containing the definitions to deploy.</span></span>|  
|<span data-ttu-id="89e65-121">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="89e65-121">Server:\<server></span></span>|<span data-ttu-id="89e65-122">Facultatif : Le nom du serveur auquel vous souhaitez déployer les définitions.</span><span class="sxs-lookup"><span data-stu-id="89e65-122">Optional: The name of the server to which to deploy the definitions.</span></span> <span data-ttu-id="89e65-123">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="89e65-123">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="89e65-124">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="89e65-124">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="89e65-125">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="89e65-125">Database:\<database></span></span>|<span data-ttu-id="89e65-126">Facultatif : Le nom de la base de données auquel vous souhaitez déployer les définitions.</span><span class="sxs-lookup"><span data-stu-id="89e65-126">Optional: The name of the database to which to deploy the definitions.</span></span> <span data-ttu-id="89e65-127">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="89e65-127">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="89e65-128">Déploie tous les artefacts du fichier XML de définitions BAM sur le serveur et la base de données spécifiés.</span><span class="sxs-lookup"><span data-stu-id="89e65-128">Deploys all artifacts from the specified BAM definition XML file to the specified server and database.</span></span> <span data-ttu-id="89e65-129">Le fichier peut être un fichier texte contenant les instructions XML de définition BAM ou un classeur Excel BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-129">The file can be a text file containing the BAM definition XML or a BAM Excel workbook.</span></span> <span data-ttu-id="89e65-130">Le fichier de définitions doit comporter des nouveaux artefacts exclusivement.</span><span class="sxs-lookup"><span data-stu-id="89e65-130">The definition file must include only new artifacts.</span></span> <span data-ttu-id="89e65-131">Si le fichier contient des artefacts déjà déployés, le déploiement échouera et génèrera une erreur.</span><span class="sxs-lookup"><span data-stu-id="89e65-131">If the file contains artifacts that have already been deployed, the deployment will fail and report an error.</span></span>  
  
 <span data-ttu-id="89e65-132">**Considérations relatives au déploiement de définitions BAM**</span><span class="sxs-lookup"><span data-stu-id="89e65-132">**Considerations for deploying BAM definitions**</span></span>  
  
 <span data-ttu-id="89e65-133">Lors du déploiement d'abonnements aux alertes, les ID utilisateur des abonnés doivent être spécifiés selon le format domaine\utilisateur.</span><span class="sxs-lookup"><span data-stu-id="89e65-133">When deploying alert subscriptions, user IDs of the subscribers must be specified in a domain\user format.</span></span>  
  
 <span data-ttu-id="89e65-134">Distributed transaction coordinator (DTC) service doit être en cours d’exécution sur l’ordinateur sur lequel le **déployer-all** commande est émise.</span><span class="sxs-lookup"><span data-stu-id="89e65-134">The distributed transaction coordinator (DTC) service must be running on the computer on which the **deploy-all** command is issued.</span></span>  
  
 <span data-ttu-id="89e65-135">Dans le cadre du déploiement d'une définition, l'utilitaire de gestion de l'analyse BAM ne prend en charge que 14 niveaux de dimension dans la vue RTA.</span><span class="sxs-lookup"><span data-stu-id="89e65-135">When deploying a definition the BAM Management utility only supports 14 dimension levels in Real-Time Aggregation (RTA) view.</span></span> <span data-ttu-id="89e65-136">Le déploiement de niveaux supplémentaires entraîne l'échec du déploiement.</span><span class="sxs-lookup"><span data-stu-id="89e65-136">Deploying additional levels returns a Deployment failed error.</span></span>  
  
 <span data-ttu-id="89e65-137">Si vous définissez plusieurs vues utilisant des paramètres de langue différents et que vous déployez votre solution sur un serveur utilisant une seule langue, les vues ne pourront pas être déployées.</span><span class="sxs-lookup"><span data-stu-id="89e65-137">If you define multiple views that use different language settings and deploy your solution to a server that uses a single language, the views will be undeployable.</span></span> <span data-ttu-id="89e65-138">Ce scénario n'est pris en charge que s'il n'existe aucune agrégation planifiée nécessitant OLAP dans le cadre de la définition BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-138">This scenario is supported only in a case where you don't have scheduled aggregations that require OLAP as part of the BAM definition.</span></span>  
  
 <span data-ttu-id="89e65-139">L'utilitaire de gestion de l'analyse BAM vous impose une limite de 49 vues d'activité déployées lorsque les alertes BAM sont activées.</span><span class="sxs-lookup"><span data-stu-id="89e65-139">The BAM management utility limits you to 49 deployed activity views when BAM Alerts are enabled.</span></span> <span data-ttu-id="89e65-140">Le nombre de vues d'activité est calculé de la manière suivante : somme de 1 à N vue(s) multipliée par le nombre d'activités parentes.</span><span class="sxs-lookup"><span data-stu-id="89e65-140">The number of activity views is calculated as the Summation 1..N of View(n) multiplied by the number of parent activities.</span></span>  <span data-ttu-id="89e65-141">Par exemple, si vous déployez une vue basée sur deux activités, vous obtenez deux vues d'activité.</span><span class="sxs-lookup"><span data-stu-id="89e65-141">For example, if you deploy a view that is based on two activities, you get two activity views.</span></span>  <span data-ttu-id="89e65-142">Si vous déployez deux vues, l'une concernant deux activités et l'autre, une seule activité, vous disposez de 3 vues d'activité.</span><span class="sxs-lookup"><span data-stu-id="89e65-142">If you deploy two views, one of which spans two activities and the other based on a single activity, you have 3 activity views.</span></span>  
  
 <span data-ttu-id="89e65-143">L'utilitaire de gestion de l'analyse BAM bloque le déploiement des définitions BAM comprenant plusieurs rapports de tableau croisé dynamique définis sur la même combinaison RTA et nom de cube.</span><span class="sxs-lookup"><span data-stu-id="89e65-143">The BAM Management utility blocks deployment of BAM definitions which have multiple PivotTable reports which are defined on the same RTA and cube name combination.</span></span> <span data-ttu-id="89e65-144">Bm.exe met fin au déploiement et génère l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="89e65-144">Bm.exe will terminate the deployment and return the following error:</span></span>  
  
 <span data-ttu-id="89e65-145">Déploiement de vue... Erreur : Échec du déploiement de l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-145">Deploying View... ERROR: The BAM deployment failed.</span></span>  
  
 <span data-ttu-id="89e65-146">Seule une vue de tableau croisé dynamique peut être définie sur une valeur RTA et un cube donnés.</span><span class="sxs-lookup"><span data-stu-id="89e65-146">Only one PivotTable view can be defined on a given RTA and cube.</span></span>  
  
 <span data-ttu-id="89e65-147">Les noms suivants sont réservés et entraîneront l'échec du déploiement de la définition :</span><span class="sxs-lookup"><span data-stu-id="89e65-147">The following list of names are reserved and will cause the definition deployment to fail:</span></span>  
  
-   <span data-ttu-id="89e65-148">RecordID</span><span class="sxs-lookup"><span data-stu-id="89e65-148">RecordID</span></span>  
  
-   <span data-ttu-id="89e65-149">ActivityID</span><span class="sxs-lookup"><span data-stu-id="89e65-149">ActivityID</span></span>  
  
-   <span data-ttu-id="89e65-150">EstVisible</span><span class="sxs-lookup"><span data-stu-id="89e65-150">IsVisible</span></span>  
  
-   <span data-ttu-id="89e65-151">IsComplete</span><span class="sxs-lookup"><span data-stu-id="89e65-151">IsComplete</span></span>  
  
-   <span data-ttu-id="89e65-152">LastModified</span><span class="sxs-lookup"><span data-stu-id="89e65-152">LastModified</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e65-153">Si bm.exe rencontre une erreur lors du déploiement, celui-ci est interrompu et les modifications apportées aux vues et activités sont annulées.</span><span class="sxs-lookup"><span data-stu-id="89e65-153">If bm.exe encounters an error during the deployment, the deployment is terminated and changes to the views and activities are rolled back.</span></span> <span data-ttu-id="89e65-154">Les modifications apportées aux cubes OLAP ne sont pas annulées car OLAP ne prend pas en charge le déploiement transactionnel.</span><span class="sxs-lookup"><span data-stu-id="89e65-154">Changes to OLAP cubes are not rolled back since OLAP does not support transactional deployment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e65-155">Les définitions BAM créées sur un ordinateur utilisant des paramètres régionaux particuliers ne peuvent être déployées sur un ordinateur présentant une configuration de paramètres régionaux différente.</span><span class="sxs-lookup"><span data-stu-id="89e65-155">BAM definitions created on a computer using one locale setting cannot be deployed to a computer configured with a different locale setting.</span></span> <span data-ttu-id="89e65-156">Par exemple, une définition BAM générée à l'aide d'une version en anglais de Microsoft Excel sur un ordinateur configuré avec un paramètre régional EN ne peut être déployée sur un ordinateur configuré pour le japonais à l'aide du paramètre régional JA.</span><span class="sxs-lookup"><span data-stu-id="89e65-156">For example, a BAM definition generated using an English language version of Microsoft Excel on a computer configured with a EN locale setting cannot be deployed on a computer configured for Japanese using a JA locale setting.</span></span>  
  
 <span data-ttu-id="89e65-157">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="89e65-157">**Examples**</span></span>  
  
```  
bm.exe deploy-all -DefinitionFile:MyDef.xml  
bm.exe deploy-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-all-command"></a><span data-ttu-id="89e65-158">Commande update-all</span><span class="sxs-lookup"><span data-stu-id="89e65-158">update-all Command</span></span>  
 <span data-ttu-id="89e65-159">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="89e65-159">**Usage**</span></span>  
  
 <span data-ttu-id="89e65-160">**BM.exe update-all - DefinitionFile :\<fichier def > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="89e65-160">**bm.exe update-all -DefinitionFile:\<def file>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="89e65-161">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="89e65-161">**Parameters**</span></span>  
  
|<span data-ttu-id="89e65-162">Paramètre</span><span class="sxs-lookup"><span data-stu-id="89e65-162">Parameter</span></span>|<span data-ttu-id="89e65-163"> Description</span><span class="sxs-lookup"><span data-stu-id="89e65-163">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89e65-164">DefinitionFile :\<fichier def ></span><span class="sxs-lookup"><span data-stu-id="89e65-164">DefinitionFile:\<def file></span></span>|<span data-ttu-id="89e65-165">Chemin d'accès et nom du fichier contenant les définitions à partir desquelles effectuer la mise à jour.</span><span class="sxs-lookup"><span data-stu-id="89e65-165">The path and name of the file containing the definitions from which to perform the update.</span></span>|  
|<span data-ttu-id="89e65-166">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="89e65-166">Server:\<server></span></span>|<span data-ttu-id="89e65-167">Facultatif : Le nom du serveur sur lequel déployer les mises à jour de définition.</span><span class="sxs-lookup"><span data-stu-id="89e65-167">Optional: The name of the server to which to deploy the definition updates.</span></span> <span data-ttu-id="89e65-168">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="89e65-168">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="89e65-169">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="89e65-169">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="89e65-170">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="89e65-170">Database:\<database></span></span>|<span data-ttu-id="89e65-171">Facultatif : Le nom de la base de données auquel vous souhaitez déployer les mises à jour de définition.</span><span class="sxs-lookup"><span data-stu-id="89e65-171">Optional: The name of the database to which to deploy the definition updates.</span></span> <span data-ttu-id="89e65-172">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="89e65-172">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="89e65-173">Met à jour certains artefacts du fichier XML de définition BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-173">Updates certain artifacts from the BAM definition XML.</span></span> <span data-ttu-id="89e65-174">Le fichier peut être un fichier texte contenant les instructions XML de définition BAM ou un classeur Excel BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-174">The file can be a text file containing the BAM definition XML or a BAM Excel workbook.</span></span> <span data-ttu-id="89e65-175">La mise à jour ne supprime pas les artefacts non décrits dans le fichier de définitions actuel.</span><span class="sxs-lookup"><span data-stu-id="89e65-175">The update does not delete artifacts that are not described in the current definition file.</span></span> <span data-ttu-id="89e65-176">Elle peut ajouter de nouveaux points de contrôle aux activités, mais ne peut pas supprimer des points de contrôle sur les activités déployées.</span><span class="sxs-lookup"><span data-stu-id="89e65-176">It can add new checkpoints to activities, but cannot drop checkpoints from deployed activities.</span></span> <span data-ttu-id="89e65-177">La mise à jour ne peut pas non plus renommer les points de contrôle ni modifier leurs propriétés.</span><span class="sxs-lookup"><span data-stu-id="89e65-177">The update can neither rename checkpoints nor change checkpoint properties.</span></span>  
  
 <span data-ttu-id="89e65-178">Une fois qu'une activité a été déployée, les actions que vous pouvez effectuer sur celle-ci sont restreintes.</span><span class="sxs-lookup"><span data-stu-id="89e65-178">Once an activity has been deployed, the actions you can take on an activity become restricted.</span></span> <span data-ttu-id="89e65-179">Par exemple, vous pouvez supprimer des éléments d'une activité mais dans ce cas, votre administrateur devra annuler le déploiement de tous les ensembles des activités et des vues BAM, puis les redéployer.</span><span class="sxs-lookup"><span data-stu-id="89e65-179">Specifically, you cannot delete items from an activity unless you are prepared to have your administrator undeploy the entire BAM activity and view sets and then redeploy them.</span></span> <span data-ttu-id="89e65-180">Ceci peut causer une interruption de l'affichage et une perte de données si l'administrateur n'effectue pas de sauvegarde et de restauration des données.</span><span class="sxs-lookup"><span data-stu-id="89e65-180">This can cause an interruption of visibility and loss of data unless the administrator does a backup and restore of the data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e65-181">Vous ne pouvez pas recourir à cette commande pour ajouter de nouvelles activités à une vue existante.</span><span class="sxs-lookup"><span data-stu-id="89e65-181">You cannot use this command to add new activities to an existing view.</span></span> <span data-ttu-id="89e65-182">Pour ajouter une vue à une activité, vous devez créer une nouvelle vue comprenant cette activité.</span><span class="sxs-lookup"><span data-stu-id="89e65-182">To add a view to an activity you must create a new view that includes the new activity.</span></span> <span data-ttu-id="89e65-183">Vous pouvez ensuite annuler le déploiement de l'ancienne vue, mais rappelez-vous que vous perdrez alors votre historique de données OLAP.</span><span class="sxs-lookup"><span data-stu-id="89e65-183">You can then undeploy the old view, but be aware that you will then lose your OLAP data history.</span></span>  
  
 <span data-ttu-id="89e65-184">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="89e65-184">**Examples**</span></span>  
  
```  
bm.exe update-all -DefinitionFile:MyDef.xml  
bm.exe update-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="remove-all-command"></a><span data-ttu-id="89e65-185">Commande remove-all</span><span class="sxs-lookup"><span data-stu-id="89e65-185">remove-all Command</span></span>  
 <span data-ttu-id="89e65-186">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="89e65-186">**Usage**</span></span>  
  
 <span data-ttu-id="89e65-187">**BM.exe remove-all DefinitionFile :\<fichier def > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="89e65-187">**bm.exe remove-all DefinitionFile:\<def file> [ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="89e65-188">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="89e65-188">**Parameters**</span></span>  
  
|<span data-ttu-id="89e65-189">Paramètre</span><span class="sxs-lookup"><span data-stu-id="89e65-189">Parameter</span></span>|<span data-ttu-id="89e65-190"> Description</span><span class="sxs-lookup"><span data-stu-id="89e65-190">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89e65-191">DefinitionFile :\<fichier def ></span><span class="sxs-lookup"><span data-stu-id="89e65-191">DefinitionFile:\<def file></span></span>|<span data-ttu-id="89e65-192">Chemin d'accès et nom du fichier contenant les définitions à supprimer.</span><span class="sxs-lookup"><span data-stu-id="89e65-192">The path and name of the file containing the definitions to remove.</span></span>|  
|<span data-ttu-id="89e65-193">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="89e65-193">Server:\<server></span></span>|<span data-ttu-id="89e65-194">Facultatif : Le nom du serveur à partir de laquelle les définitions doivent être supprimées.</span><span class="sxs-lookup"><span data-stu-id="89e65-194">Optional: The name of the server from which the definitions will be removed.</span></span> <span data-ttu-id="89e65-195">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="89e65-195">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="89e65-196">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="89e65-196">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="89e65-197">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="89e65-197">Database:\<database></span></span>|<span data-ttu-id="89e65-198">Facultatif : Le nom de la base de données à partir de laquelle les définitions doivent être supprimées.</span><span class="sxs-lookup"><span data-stu-id="89e65-198">Optional: The name of the database from which the definitions will be removed.</span></span> <span data-ttu-id="89e65-199">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="89e65-199">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="89e65-200">Supprime tous les artefacts spécifiés dans le fichier XML de définition BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-200">Removes all artifacts specified in the BAM definition XML file.</span></span> <span data-ttu-id="89e65-201">Le fichier peut être un fichier texte contenant les instructions XML de définition BAM ou un classeur Excel BAM.</span><span class="sxs-lookup"><span data-stu-id="89e65-201">The file can be a text file containing the BAM definition XML or a BAM Excel workbook.</span></span> <span data-ttu-id="89e65-202">La définition de chaque artefact doit correspondre exactement à la définition d'origine utilisée pour le déploiement.</span><span class="sxs-lookup"><span data-stu-id="89e65-202">The definition for each artifact must exactly match the original definition that was used for deployment.</span></span>  
  
 <span data-ttu-id="89e65-203">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="89e65-203">**Examples**</span></span>  
  
```  
bm.exe remove-all -DefinitionFile:MyDef.xml  
bm.exe remove-all -DefinitionFile:MyWorkbook.xls -Server:machine1  
```  
  
## <a name="update-livedataworkbook-command"></a><span data-ttu-id="89e65-204">Commande update-livedataworkbook</span><span class="sxs-lookup"><span data-stu-id="89e65-204">update-livedataworkbook Command</span></span>  
 <span data-ttu-id="89e65-205">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="89e65-205">**Usage**</span></span>  
  
 <span data-ttu-id="89e65-206">**BM.exe update-livedataworkbook-nom :\<nom de fichier de classeur de données actives > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="89e65-206">**bm.exe update-livedataworkbook -Name:\<livedata workbook file name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="89e65-207">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="89e65-207">**Parameters**</span></span>  
  
|<span data-ttu-id="89e65-208">Paramètre</span><span class="sxs-lookup"><span data-stu-id="89e65-208">Parameter</span></span>|<span data-ttu-id="89e65-209"> Description</span><span class="sxs-lookup"><span data-stu-id="89e65-209">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89e65-210">Nom :\<classeur des données actives ></span><span class="sxs-lookup"><span data-stu-id="89e65-210">Name:\<livedata workbook></span></span>|<span data-ttu-id="89e65-211">Nom du classeur de données actives à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="89e65-211">The name of the existing live workbook to update.</span></span>|  
|<span data-ttu-id="89e65-212">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="89e65-212">Server:\<server></span></span>|<span data-ttu-id="89e65-213">Facultatif : Le nom du serveur sur lequel réside le classeur.</span><span class="sxs-lookup"><span data-stu-id="89e65-213">Optional: The name of the server on which the workbook resides.</span></span> <span data-ttu-id="89e65-214">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="89e65-214">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="89e65-215">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="89e65-215">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="89e65-216">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="89e65-216">Database:\<database></span></span>|<span data-ttu-id="89e65-217">Facultatif : Le nom de la base de données sur lequel réside le classeur.</span><span class="sxs-lookup"><span data-stu-id="89e65-217">Optional: The name of the database on which the workbook resides.</span></span> <span data-ttu-id="89e65-218">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="89e65-218">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="89e65-219">Met à jour les informations de connexion à la base de données d'importation principale BAM du classeur de données actives BAM spécifié.</span><span class="sxs-lookup"><span data-stu-id="89e65-219">Updates the BAM Primary Import database connection information in the specified BAM live data workbook.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89e65-220">Lorsque vous configurez une nouvelle chaîne de connexion, vous devez redémarrer le service TDDS pour vous assurer que ce service reconnaît le changement.</span><span class="sxs-lookup"><span data-stu-id="89e65-220">When configuring new connection string, you must restart the TDDS service to ensure that the service recognizes the change.</span></span> <span data-ttu-id="89e65-221">Pour plus d’informations sur le service TDDS, consultez [procédures stockées BAM événement Bus Service](../core/bam-event-bus-service-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="89e65-221">For more information on the TDDS service, see [BAM Event Bus Service Stored Procedures](../core/bam-event-bus-service-stored-procedures.md).</span></span>  
  
 <span data-ttu-id="89e65-222">**Exemples**</span><span class="sxs-lookup"><span data-stu-id="89e65-222">**Examples**</span></span>  
  
```  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls  
bm.exe update-livedataworkbook -Name:SalesManager_Live.xls -Server:SalesSrv  
```  
  
## <a name="regenerate-livedataworkbook-command"></a><span data-ttu-id="89e65-223">Commande regenerate-livedataworkbook</span><span class="sxs-lookup"><span data-stu-id="89e65-223">regenerate-livedataworkbook Command</span></span>  
 <span data-ttu-id="89e65-224">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="89e65-224">**Usage**</span></span>  
  
 <span data-ttu-id="89e65-225">**BM.exe regenerate-livedataworkbook - WorkbookName :\<nom de fichier de classeur de données actives > [-Server :\<serveur >] [-base de données :\<base de données >]**</span><span class="sxs-lookup"><span data-stu-id="89e65-225">**bm.exe regenerate-livedataworkbook -WorkbookName:\<livedata workbook file name>[ -Server:\<server> ][ -Database:\<database> ]**</span></span>  
  
 <span data-ttu-id="89e65-226">**Paramètres**</span><span class="sxs-lookup"><span data-stu-id="89e65-226">**Parameters**</span></span>  
  
|<span data-ttu-id="89e65-227">Paramètre</span><span class="sxs-lookup"><span data-stu-id="89e65-227">Parameter</span></span>|<span data-ttu-id="89e65-228"> Description</span><span class="sxs-lookup"><span data-stu-id="89e65-228">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="89e65-229">WorkbookName :\<nom de fichier de classeur de données actives ></span><span class="sxs-lookup"><span data-stu-id="89e65-229">WorkbookName:\<livedata workbook file name></span></span>|<span data-ttu-id="89e65-230">Nom du classeur à mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="89e65-230">The name of the workbook to update.</span></span>|  
|<span data-ttu-id="89e65-231">Serveur :\<server ></span><span class="sxs-lookup"><span data-stu-id="89e65-231">Server:\<server></span></span>|<span data-ttu-id="89e65-232">Facultatif : Le nom du serveur sur lequel réside le classeur.</span><span class="sxs-lookup"><span data-stu-id="89e65-232">Optional: The name of the server on which the workbook resides.</span></span> <span data-ttu-id="89e65-233">Le serveur doit se trouver dans le même domaine que l'ordinateur à partir duquel bm.exe est exécuté.</span><span class="sxs-lookup"><span data-stu-id="89e65-233">The server must be in the same domain as the computer from which you are running bm.exe.</span></span> <span data-ttu-id="89e65-234">Si le nom du serveur n'est pas spécifié, bm.exe utilise le nom par défaut de l'hôte local.</span><span class="sxs-lookup"><span data-stu-id="89e65-234">If the server name is not specified, bm.exe uses the default name of localhost.</span></span>|  
|<span data-ttu-id="89e65-235">Base de données :\<base de données ></span><span class="sxs-lookup"><span data-stu-id="89e65-235">Database:\<database></span></span>|<span data-ttu-id="89e65-236">Facultatif : Le nom de la base de données sur lequel réside le classeur.</span><span class="sxs-lookup"><span data-stu-id="89e65-236">Optional: The name of the database on which the workbook resides.</span></span> <span data-ttu-id="89e65-237">Si le nom n'est pas spécifié, bm.exe utilise le nom par défaut BamPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="89e65-237">If the name is not specified, bm.exe uses the default name BamPrimaryImport.</span></span>|  
  
 <span data-ttu-id="89e65-238">Génère un classeur BAM de données actives, mais sans le déployer.</span><span class="sxs-lookup"><span data-stu-id="89e65-238">Generates a BAM live data workbook but does not deploy the workbook.</span></span>  
  
 <span data-ttu-id="89e65-239">Exemples</span><span class="sxs-lookup"><span data-stu-id="89e65-239">Examples</span></span>  
  
```  
bm.exe regenerate-livedataworkbook -WorkbookName:SalesManager_Live.xls  
bm.exe regenerate-livedataworkbook -WorkbookName:SM_Live.xls -Server:S1  
```  
  
## <a name="see-also"></a><span data-ttu-id="89e65-240">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89e65-240">See Also</span></span>  
 [<span data-ttu-id="89e65-241">Utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="89e65-241">BAM Management Utility</span></span>](../core/bam-management-utility.md)