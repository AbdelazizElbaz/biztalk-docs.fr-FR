---
title: Flux de travail BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring business activities [BAM], collecting business data
- XML files
- orchestrations, XML files
- business activities, business data
- infrastructure, managing [BAM]
- business activities, monitoring
- monitoring business activities [BAM], monitoring flow
- managing [BAM], infrastructure
- monitoring business activities [BAM], viewing business data
- managing [orchestrations], mapping XML to orchestrations
ms.assetid: 8b4ae145-3e16-4bb8-bfba-09b9f666218d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 19356d6191963ec441f0b85c0e987c8515dcf1f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-workflow"></a><span data-ttu-id="c6117-102">Workflow BAM</span><span class="sxs-lookup"><span data-stu-id="c6117-102">BAM Workflow</span></span>
<span data-ttu-id="c6117-103">L'illustration suivante représente les quatre rôles d'utilisateur qui interviennent dans le cadre de l'analyse BAM, ainsi que les outils qu'ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="c6117-103">The following figure shows the four user roles who work with Business Activity Monitoring, and the tools that they use.</span></span>  
  
 ![](../core/media/ebiz-tut-bamworkflow.gif "ebiz_tut_bamworkflow")  
<span data-ttu-id="c6117-104">Rôles BAM</span><span class="sxs-lookup"><span data-stu-id="c6117-104">BAM Roles</span></span>  
  
 <span data-ttu-id="c6117-105">Les étapes ci-après constituent une présentation détaillée du workflow de l'utilisation de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="c6117-105">The following steps provide a high-level overview of the workflow for using Business Activity Monitoring.</span></span>  
  
## <a name="specifying-the-business-data-to-collect"></a><span data-ttu-id="c6117-106">Spécification des données de l'entreprise à collecter</span><span class="sxs-lookup"><span data-stu-id="c6117-106">Specifying the business data to collect</span></span>  
 <span data-ttu-id="c6117-107">Les données de l'entreprise sont collectées de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="c6117-107">Business data is collected in the following manner:</span></span>  
  
-   <span data-ttu-id="c6117-108">L'analyste d'entreprise utilise l'Assistant Activité BAM pour spécifier les données à collecter pour tous les utilisateurs des activités.</span><span class="sxs-lookup"><span data-stu-id="c6117-108">The business analyst uses the BAM Activity Wizard to specify what data to collect for all business users.</span></span>  
  
-   <span data-ttu-id="c6117-109">L'analyste d'entreprise utilise l'Assistant Vue BAM pour définir la vue de chaque catégorie d'utilisateur des activités.</span><span class="sxs-lookup"><span data-stu-id="c6117-109">The business analyst uses the BAM View Wizard to define the view for each category of business user.</span></span>  
  
-   <span data-ttu-id="c6117-110">Ensuite, il enregistre les activités et les vues dans un classeur Microsoft® Excel appelé le Classeur de définitions BAM.</span><span class="sxs-lookup"><span data-stu-id="c6117-110">When finished, he saves the activities and views in a Microsoft® Excel Workbook called the BAM Definition Workbook.</span></span>  
  
-   <span data-ttu-id="c6117-111">L'analyste d'entreprise exporte le Classeur de définitions BAM au format XML.</span><span class="sxs-lookup"><span data-stu-id="c6117-111">The business analyst exports the BAM Definition Workbook to XML.</span></span>  
  
-   <span data-ttu-id="c6117-112">L'administrateur système et le développeur utilisent le fichier XML dans le cadre de leurs rôles.</span><span class="sxs-lookup"><span data-stu-id="c6117-112">The system administrator and developer use the XML to perform their roles.</span></span>  
  
-   <span data-ttu-id="c6117-113">Les instructions relatives à l’aide du classeur de définition BAM se trouvent dans [définition des activités d’entreprise et les vues dans Excel](../core/defining-business-activities-and-views-in-excel.md).</span><span class="sxs-lookup"><span data-stu-id="c6117-113">Instructions for using the BAM Definition Workbook are located in [Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md).</span></span>  
  
## <a name="managing-the-bam-infrastructure"></a><span data-ttu-id="c6117-114">Gestion de l'infrastructure BAM</span><span class="sxs-lookup"><span data-stu-id="c6117-114">Managing the BAM Infrastructure</span></span>  
 <span data-ttu-id="c6117-115">Une fois que l'analyste d'entreprise a défini la vue BAM voulue, l'administrateur système utilise l'utilitaire de gestion de l'analyse BAM (BM.EXE), un outil de ligne de commande, pour déployer l'infrastructure BAM à partir du Classeur de définitions BAM ou du fichier XML exporté depuis celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c6117-115">After the business analyst has defined the BAM view he wants, the system administrator uses the BAM management utility (BM.EXE), a command-line tool, to deploy the BAM infrastructure from the BAM Definition Workbook or the XML exported from the workbook.</span></span>  
  
 <span data-ttu-id="c6117-116">L'utilitaire de gestion de l'analyse BAM crée de manière dynamique les tables, les déclencheurs, les packages DTS et les cubes OLAP nécessaires à la prise en charge de la vue BAM.</span><span class="sxs-lookup"><span data-stu-id="c6117-116">The BAM management utility dynamically creates the tables, triggers, DTS packages, and OLAP cubes necessary to support the BAM view.</span></span>  
  
 <span data-ttu-id="c6117-117">Chaque fois que l'analyste d'entreprise définit une vue BAM différentes ou modifie une vue BAM, l'administrateur système doit redéployer le Classeur de définitions BAM.</span><span class="sxs-lookup"><span data-stu-id="c6117-117">Each time the business analyst defines a different BAM view, or changes an existing BAM view, the system administrator must redeploy the BAM Definition Workbook.</span></span>  
  
## <a name="mapping-the-xml-to-an-orchestration"></a><span data-ttu-id="c6117-118">Mappage du fichier XML vers une orchestration</span><span class="sxs-lookup"><span data-stu-id="c6117-118">Mapping the XML to an orchestration</span></span>  
 <span data-ttu-id="c6117-119">Après que l'analyste d'entreprise a exporté le Classeur de définitions BAM au format XML, le développeur importe le fichier XML dans l'Éditeur de modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="c6117-119">After the business analyst exports the BAM Definition Workbook to XML, the developer imports the XML file into the Tracking Profile Editor.</span></span> <span data-ttu-id="c6117-120">Le développeur implémente les demandes d'information de l'analyste d'entreprise en mappant le fichier XML vers une orchestration.</span><span class="sxs-lookup"><span data-stu-id="c6117-120">The developer implements the business analyst's information requirements, mapping the XML to an orchestration.</span></span>  
  
 <span data-ttu-id="c6117-121">À l'aide de l'Éditeur de modèle de suivi, le développeur exécute la procédure suivante pour mapper le fichier XML vers une orchestration :</span><span class="sxs-lookup"><span data-stu-id="c6117-121">Using the Tracking Profile Editor, the developer performs the following steps to map the XML to an orchestration:</span></span>  
  
-   <span data-ttu-id="c6117-122">Il charge l'assembly déployé qui est stocké dans la base de données de gestion BizTalk (également appelée « base de données de configuration »).</span><span class="sxs-lookup"><span data-stu-id="c6117-122">Loads the deployed assembly that is stored in the BizTalk Management database (also known as the Configuration database).</span></span> <span data-ttu-id="c6117-123">L'assembly déployé contient une ou plusieurs orchestrations correspondant aux exigences spécifiées par l'analyste d'entreprise à l'étape 1 ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="c6117-123">The deployed assembly contains one or more orchestrations corresponding to the requirements that the business analyst specified in Step 1 above.</span></span>  
  
-   <span data-ttu-id="c6117-124">Il définit les données à extraire d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="c6117-124">Defines the data to be extracted from an orchestration.</span></span> <span data-ttu-id="c6117-125">Pour ce faire, il fait glisser des éléments issus des schémas des messages et des formes Orchestration dans les dossiers d'étapes majeures commerciales (événement) et d'éléments de données appropriés.</span><span class="sxs-lookup"><span data-stu-id="c6117-125">You do this by dropping items from the message schemas and orchestration shapes into the appropriate business milestone (event) and data item folders.</span></span>  
  
-   <span data-ttu-id="c6117-126">Lorsqu'il a terminé, il enregistre le profil en tant que fichier de suivi BizTalk® Server (.btt) dans une base de données de stockage telle que Visual SourceSafe.</span><span class="sxs-lookup"><span data-stu-id="c6117-126">When he is finished, he saves the profile as a BizTalk® Server tracking (.btt) file, to a storage database such as Visual SourceSafe.</span></span>  
  
 <span data-ttu-id="c6117-127">Le développeur déploie le fichier .btt dans une base de données de test et vérifie le résultat par des tests d'intégration.</span><span class="sxs-lookup"><span data-stu-id="c6117-127">The developer deploys the .btt file to a testing database, and verifies the result through integration testing.</span></span>  
  
## <a name="deploying-the-tracking-profile"></a><span data-ttu-id="c6117-128">Déploiement du modèle de suivi</span><span class="sxs-lookup"><span data-stu-id="c6117-128">Deploying the Tracking Profile</span></span>  
 <span data-ttu-id="c6117-129">À l'aide de l'Éditeur de modèle de suivi, l'administrateur système déploie le profil vers une ou plusieurs bases de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c6117-129">Using the Tracking Profile Editor, the system administrator deploys the profile to one or more BizTalk Management databases.</span></span>  
  
 <span data-ttu-id="c6117-130">Chaque fois que le développeur modifie l'orchestration ou que les exigences des utilisateurs des activités changent et qu'ils souhaitent effectuer le suivi d'un plus grand nombre de données, l'administrateur système doit redéployer le modèle de suivi à l'aide de l'utilitaire de ligne de commande bttdeploy.exe.</span><span class="sxs-lookup"><span data-stu-id="c6117-130">Each time the developer changes the orchestration, or the requirements of the business users change and they want to track more data, the system administrator needs to redeploy the tracking profile using the bttdeploy.exe command line utility.</span></span>  
  
## <a name="viewing-the-business-data"></a><span data-ttu-id="c6117-131">Affichage des données de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="c6117-131">Viewing the business data</span></span>  
 <span data-ttu-id="c6117-132">L'utilisateur des activités fait appel au classeur _LiveData généré par l'utilitaire BM.exe.</span><span class="sxs-lookup"><span data-stu-id="c6117-132">The business user uses the _LiveData workbook, which is produced by the BM.exe utility.</span></span> <span data-ttu-id="c6117-133">Chaque fois que l'utilisateur des activités ouvre ce classeur, il reçoit une nouvelle version à jour des données collectées pour surveiller un aspect spécifique du processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="c6117-133">Each time the business user opens the _LiveData workbook, he receives a new live version of the data that is collected to monitor a specific aspect of the business process.</span></span>  
  
-   <span data-ttu-id="c6117-134">Pour afficher les données qui sont définies comme une agrégation en temps réel, l’utilisateur doit simplement cliquer sur **Actualiser** dans le classeur pour afficher les données.</span><span class="sxs-lookup"><span data-stu-id="c6117-134">To view data that is defined as real-time aggregation, the business user just needs to click **Refresh** in the workbook to view the data.</span></span>  
  
-   <span data-ttu-id="c6117-135">Si les données d'agrégation ne sont pas en temps réel, l'utilisateur des activités affiche un instantané des données de l'entreprise pris au moment de l'exécution du lot DTS planifié.</span><span class="sxs-lookup"><span data-stu-id="c6117-135">If the aggregation data is not real-time, the business user views a snapshot of the business data that is taken at the time that the scheduled DTS package runs.</span></span>  
  
-   <span data-ttu-id="c6117-136">Si votre organisation a défini des exigences concernant la collaboration, l'utilisateur des activités peut accéder aux données actives à partir du site Web BAS.</span><span class="sxs-lookup"><span data-stu-id="c6117-136">If your organization has collaboration requirements, the business user can access the live data from the BAS Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6117-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6117-137">See Also</span></span>  
 <span data-ttu-id="c6117-138">[Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md) </span><span class="sxs-lookup"><span data-stu-id="c6117-138">[Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md) </span></span>  
 [<span data-ttu-id="c6117-139">Analyse des activités d’entreprise avec BAM</span><span class="sxs-lookup"><span data-stu-id="c6117-139">Monitoring Business Activities with BAM</span></span>](../core/monitoring-business-activities-with-bam.md)