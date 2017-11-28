---
title: Utilitaire de gestion BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c55aabe2-f38b-4917-863c-b408a4eef98e
caps.latest.revision: "50"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be7c36900c39f46f636077c5c9d0cb630265cc80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-management-utility"></a><span data-ttu-id="e76bb-102">Utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-102">BAM Management Utility</span></span>
<span data-ttu-id="e76bb-103">Les administrateurs des définitions BAM utilisent l'utilitaire de gestion de l'analyse BAM pour gérer et conserver tous les aspects de l'infrastructure BAM.</span><span class="sxs-lookup"><span data-stu-id="e76bb-103">Administrators of Business Activity Monitoring (BAM) definitions use the BAM Management utility to manage and maintain all aspects of the BAM infrastructure.</span></span>  
  
 <span data-ttu-id="e76bb-104">L'utilitaire BAM permet d'exécuter les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e76bb-104">You can use the BAM utility to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="e76bb-105">Utiliser les fichiers XML de définition BAM et de configuration BAM en entrée.</span><span class="sxs-lookup"><span data-stu-id="e76bb-105">Consume BAM definition and BAM configuration XML as input.</span></span> <span data-ttu-id="e76bb-106">Les fichiers XML ou XLS de définition d'analyse BAM définissent les données à suivre et à agréger, ainsi que la vue des données de suivi pour les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e76bb-106">The BAM definition XML or XLS files define the data to track and aggregate, as well as the business end user's view on the tracking data.</span></span> <span data-ttu-id="e76bb-107">Le fichier XML de configuration BAM spécifie l'emplacement de déploiement de l'infrastructure, à savoir le nom du serveur, le nom de la base de données, ainsi que d'autres paramètres de base de données.</span><span class="sxs-lookup"><span data-stu-id="e76bb-107">The BAM configuration XML mandates where to deploy the infrastructure, such as the server name, database name, and other database settings.</span></span>  
  
-   <span data-ttu-id="e76bb-108">Déployer l'infrastructure d'exécution sur le serveur, ce qui inclut la base de données d'importation principale BAM, la base de données de schémas en étoile BAM, la base de données Analyse BAM et les lots DTS (Data Transformation Services).</span><span class="sxs-lookup"><span data-stu-id="e76bb-108">Deploy the run-time infrastructure on the server, which includes the BAM Primary Import database, BAM Star Schema database, BAM Analysis database, and corresponding Data Transformation Services (DTS) packages.</span></span> <span data-ttu-id="e76bb-109">Cette étape crée également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e76bb-109">The following items are created during this step:</span></span>  
  
    -   <span data-ttu-id="e76bb-110">Base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-110">BAM Primary Import database</span></span>  
  
    -   <span data-ttu-id="e76bb-111">Base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-111">BAM Star Schema database</span></span>  
  
    -   <span data-ttu-id="e76bb-112">Base de données des archives de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-112">BAM Archive database</span></span>  
  
    -   <span data-ttu-id="e76bb-113">Base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-113">BAM Analysis database</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e76bb-114">Pour que les commandes fonctionnent correctement, les paramètres régionaux de l'ordinateur exécutant l'utilitaire de gestion BAM doivent être identiques à ceux utilisés pour créer la définition BAM déployée.</span><span class="sxs-lookup"><span data-stu-id="e76bb-114">The locale setting of the computer running the BAM Management utility must be the same as the locale used to create the BAM definition being deployed in order for the BAM commands to work properly.</span></span> <span data-ttu-id="e76bb-115">Par exemple, si vous exécutez le **get-views** commande sur un ordinateur configuré avec les paramètres régionaux anglais paramètre par rapport à une base de données sur un ordinateur avec les paramètres régionaux Français pas sera en mesure d’utiliser le nom de vue renvoyé, sauf si vous réinitialisez votre ordinateur paramètres régionaux à Français.</span><span class="sxs-lookup"><span data-stu-id="e76bb-115">For example, if you execute the **get-views** command on a computer configured with an English locale setting against a database on a computer with a French locale you will not be able to use the returned view name unless you reset your computer locale to French.</span></span>  
  
 <span data-ttu-id="e76bb-116">Vous pouvez utiliser l'utilitaire de gestion de l'analyse BAM pour générer et déployer votre configuration de suivi sur un serveur.</span><span class="sxs-lookup"><span data-stu-id="e76bb-116">You can use the BAM Management utility to generate and deploy your tracking configuration on a server.</span></span> <span data-ttu-id="e76bb-117">L’utilitaire de gestion de l’analyse BAM est un outil de ligne de commande situé dans \< *chemin d’installation*> \Program Files\Microsoft BizTalk Server \<version > \Tracking\BM.exe.</span><span class="sxs-lookup"><span data-stu-id="e76bb-117">The BAM Management utility is a command-line tool located at \<*installation path*>\Program Files\Microsoft BizTalk Server \<version>\Tracking\BM.exe.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e76bb-118">Pour exécuter l’utilitaire de gestion BAM, vous devez être membre de la **db_owner** rôle de base de données SQL Server dans les bases de données d’importation principale BAM, schémas en étoile BAM et archives BAM.</span><span class="sxs-lookup"><span data-stu-id="e76bb-118">To run the BAM management utility, you must be member of the **db_owner** SQL Server Database role in the BAM Primary Import, BAM Star Schema, and BAM Archive databases.</span></span> <span data-ttu-id="e76bb-119">Vous devez également disposer des autorisations sysadmin sur les bases de données d'alertes BAM si vous effectuez des mises à jour associées aux alertes BAM.</span><span class="sxs-lookup"><span data-stu-id="e76bb-119">You must also have sysadmin permissions on the BAM Alerts databases if making any updates related to BAM Alerts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e76bb-120">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="e76bb-120">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span> <span data-ttu-id="e76bb-121">Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="e76bb-121">To do this, right-click the application, and then select **Run as administrator**.</span></span>  
  
## <a name="bam-management-utility-commands"></a><span data-ttu-id="e76bb-122">Commandes de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-122">BAM Management Utility Commands</span></span>  
 <span data-ttu-id="e76bb-123">Les descriptions de commande utilisent les conventions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e76bb-123">The command descriptions use these conventions:</span></span>  
  
-   <span data-ttu-id="e76bb-124">Les crochets ([]) signalent un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="e76bb-124">The square brackets ([]) indicate an optional parameter.</span></span>  
  
-   <span data-ttu-id="e76bb-125">Les crochets angulaires (<>) signalent un paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="e76bb-125">The angled brackets (<>) indicate a required parameter.</span></span>  
  
-   <span data-ttu-id="e76bb-126">Les accolades ({}) indiquent qu'un élément doit être sélectionné parmi ceux énumérés dans la liste.</span><span class="sxs-lookup"><span data-stu-id="e76bb-126">The braces ({}) indicate that one item should be selected from the enumerated list.</span></span>  
  
-   <span data-ttu-id="e76bb-127">Un compte de sécurité peut être un groupe NT ou un compte d'utilisateur NT individuel.</span><span class="sxs-lookup"><span data-stu-id="e76bb-127">A security account can be either an NT group or an individual NT user account.</span></span>  
  
-   <span data-ttu-id="e76bb-128">Un fichier de définition d'analyse BAM peut être un fichier XML ou un classeur Excel BAM (.xls).</span><span class="sxs-lookup"><span data-stu-id="e76bb-128">A BAM definition file can be either an XML file or a BAM Excel workbook file (.xls).</span></span>  
  
-   <span data-ttu-id="e76bb-129">Si le fichier de configuration BAM n'est pas fourni, il s'agit par défaut du fichier BamConfiguration.xml figurant dans le dossier en cours.</span><span class="sxs-lookup"><span data-stu-id="e76bb-129">If the BAM configuration file is not supplied, it defaults to BamConfiguration.xml in the current folder.</span></span>  
  
 <span data-ttu-id="e76bb-130">Les rubriques ci-dessous contiennent les descriptions des commandes individuelles :</span><span class="sxs-lookup"><span data-stu-id="e76bb-130">The Individual command descriptions are contained in the following topics:</span></span>  
  
-   [<span data-ttu-id="e76bb-131">Commandes de base de données</span><span class="sxs-lookup"><span data-stu-id="e76bb-131">Database Commands</span></span>](../core/database-commands.md)  
  
-   [<span data-ttu-id="e76bb-132">Déploiement des commandes de définition (modèle d’Observation) BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-132">Deployment of BAM Definition (Observation Model) Commands</span></span>](../core/deployment-of-bam-definition-observation-model-commands.md)  
  
-   [<span data-ttu-id="e76bb-133">Commandes de gestion d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="e76bb-133">Infrastructure Management Commands</span></span>](../core/infrastructure-management-commands.md)  
  
-   [<span data-ttu-id="e76bb-134">Commandes de gestion des activités</span><span class="sxs-lookup"><span data-stu-id="e76bb-134">Activity Management Commands</span></span>](../core/activity-management-commands.md)  
  
-   [<span data-ttu-id="e76bb-135">Afficher les commandes de gestion</span><span class="sxs-lookup"><span data-stu-id="e76bb-135">View Management Commands</span></span>](../core/view-management-commands.md)  
  
-   [<span data-ttu-id="e76bb-136">Commandes de gestion des alertes</span><span class="sxs-lookup"><span data-stu-id="e76bb-136">Alert Management Commands</span></span>](../core/alert-management-commands.md)  
  
-   [<span data-ttu-id="e76bb-137">Commandes de gestion d’utilisateur</span><span class="sxs-lookup"><span data-stu-id="e76bb-137">User Management Commands</span></span>](../core/user-management-commands.md)  
  
-   [<span data-ttu-id="e76bb-138">Commandes de gestion des abonnements aux alertes</span><span class="sxs-lookup"><span data-stu-id="e76bb-138">Alert Subscription Management Commands</span></span>](../core/alert-subscription-management-commands.md)  
  
-   [<span data-ttu-id="e76bb-139">Commandes de gestion de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="e76bb-139">Interceptor Management Commands</span></span>](../core/interceptor-management-commands.md)  
  
## <a name="displaying-the-bam-management-utility-help"></a><span data-ttu-id="e76bb-140">Affichage de l'Aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-140">Displaying the BAM Management Utility Help</span></span>  
 <span data-ttu-id="e76bb-141">Vous utilisez la **/ ?**</span><span class="sxs-lookup"><span data-stu-id="e76bb-141">You use the **/?**</span></span> <span data-ttu-id="e76bb-142">ou le **aide utilitaire BAM Management** commande afin d’afficher le fichier d’aide de l’utilitaire de gestion BAM.</span><span class="sxs-lookup"><span data-stu-id="e76bb-142">or the **help BAM Management utility** command to display the Help file for the BAM Management utility.</span></span>  
  
#### <a name="to-display-the-help-file-for-the-bam-management-utility"></a><span data-ttu-id="e76bb-143">Affichage du fichier d'aide de l'utilitaire de gestion de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="e76bb-143">To display the Help file for the BAM Management utility</span></span>  
  
1.  <span data-ttu-id="e76bb-144">À partir d’une invite de commandes, accédez au répertoire suivant : C:\Program Files\Microsoft BizTalk Server \<version > \Tracking\\.</span><span class="sxs-lookup"><span data-stu-id="e76bb-144">From a command prompt, browse to the following directory: C:\Program Files\Microsoft BizTalk Server \<version>\Tracking\\.</span></span>  
  
2.  <span data-ttu-id="e76bb-145">Type **bm** ou **aide de bm**.</span><span class="sxs-lookup"><span data-stu-id="e76bb-145">Type **bm** or **bm help**.</span></span>  
  
3.  <span data-ttu-id="e76bb-146">Appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="e76bb-146">Press ENTER.</span></span>