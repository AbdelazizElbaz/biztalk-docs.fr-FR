---
title: "Phase 3 : Préparation de l’évaluation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d153ed62-f2cc-4080-8912-c98ecdd329f5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 890047f6a13352d89d33d9514883dc20eacd4001
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="phase-3-preparing-for-the-assessment"></a><span data-ttu-id="60b1b-102">Phase 3 : Préparation de l’évaluation</span><span class="sxs-lookup"><span data-stu-id="60b1b-102">Phase 3: Preparing for the Assessment</span></span>
<span data-ttu-id="60b1b-103">La phase d’une évaluation des performances peut être considéré comme « comment » à la phase de portée « que se passe-t-il » et la phase de planification de préparation 's « lorsque. »</span><span class="sxs-lookup"><span data-stu-id="60b1b-103">The Prepare phase of a performance assessment can be thought of as the “how” to the Scope phase’s “what” and the Plan phase’s “when.”</span></span> <span data-ttu-id="60b1b-104">À ce stade dans l’évaluation des performances, toutes les parties prenantes doivent ont convenu l’étendue de l’engagement et les plans d’effectuer le laboratoire.</span><span class="sxs-lookup"><span data-stu-id="60b1b-104">At this point in the performance assessment, all stakeholders should have agreed upon the scope of the engagement and the plans for conducting the lab.</span></span> <span data-ttu-id="60b1b-105">Il est dans la phase de préparation de l’évaluation des performances où les plans sont exécutées et les étapes pour préparer l’exécution des procédures du laboratoire de performances.</span><span class="sxs-lookup"><span data-stu-id="60b1b-105">It is in the Prepare phase of the performance assessment where the plans are executed and steps are taken to get ready for execution of the performance lab.</span></span>  
  
 <span data-ttu-id="60b1b-106">Cette rubrique décrit les différents aspects de la phase de préparation d’une évaluation de performances de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="60b1b-106">This topic describes the various aspects of the Prepare phase of a BizTalk Server performance assessment.</span></span>  
  
## <a name="detailed-design-of-the-solution-platform"></a><span data-ttu-id="60b1b-107">Conception détaillée de la plateforme de solution</span><span class="sxs-lookup"><span data-stu-id="60b1b-107">Detailed design of the solution platform</span></span>  
 <span data-ttu-id="60b1b-108">Conception d’une solution détaillées facilite les communications et évite les hypothèses, afin d’amélioreront la flexibilité et l’efficacité de toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="60b1b-108">A detailed solution design facilitates communications and avoids assumptions, which will improve the agility and effectiveness of all activities.</span></span> <span data-ttu-id="60b1b-109">Vous devez entièrement documenter les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="60b1b-109">You should fully document the following elements:</span></span>  
  
-   <span data-ttu-id="60b1b-110">**Bases de données BizTalk Server et comment elles seront distribuées sur plusieurs ordinateurs** -performances de SQL Server sont un des principaux facteurs de performances globales de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="60b1b-110">**BizTalk Server databases and how they will be distributed across computers** - SQL Server performance is one of the key factors in overall BizTalk Server performance.</span></span> <span data-ttu-id="60b1b-111">Si SQL Server rencontre des contraintes de ressources, cela aura un impact sur la capacité de BizTalk Server pour traiter les messages.</span><span class="sxs-lookup"><span data-stu-id="60b1b-111">If SQL Server is experiencing resource constraints, this will impact the ability of BizTalk Server to process messages.</span></span> <span data-ttu-id="60b1b-112">Le principal facteur qui influencent les performances de base de données BizTalk est la vitesse de qu’ils sont hébergés sur des disques.</span><span class="sxs-lookup"><span data-stu-id="60b1b-112">The main factor that influences BizTalk database performance is the speed of disks that they are hosted on.</span></span> <span data-ttu-id="60b1b-113">Séparer les fichiers de base de données et du journal des transactions pour chaque BizTalk base de données sur des lecteurs distincts ou l’unité logique de réseau SAN a démontré considérablement améliorer les performances globales de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="60b1b-113">Separating the transaction log and database files for each BizTalk database onto separate drives or SAN LUN’s has been shown to remarkably improve the overall performance of BizTalk Server.</span></span> <span data-ttu-id="60b1b-114">Par conséquent, il est important que ces informations soient enregistrés de façon facilement accessible.</span><span class="sxs-lookup"><span data-stu-id="60b1b-114">Therefore, it is important that this information be recorded in an easily accessible manner.</span></span> <span data-ttu-id="60b1b-115">Les valeurs qui seront utilisés dans l’environnement de production doivent être documentées dans la conception de solution détaillées.</span><span class="sxs-lookup"><span data-stu-id="60b1b-115">The values that will be used in the production environment should be documented in the detailed solution design.</span></span> <span data-ttu-id="60b1b-116">Le tableau suivant fournit un exemple de la manière dont cela est possible.</span><span class="sxs-lookup"><span data-stu-id="60b1b-116">The following table provides an example of how this can be done.</span></span>  
  
    |<span data-ttu-id="60b1b-117">Base de données BizTalk</span><span class="sxs-lookup"><span data-stu-id="60b1b-117">BizTalk Database</span></span>|<span data-ttu-id="60b1b-118">Nom de volume</span><span class="sxs-lookup"><span data-stu-id="60b1b-118">Volume Name</span></span>|<span data-ttu-id="60b1b-119">Fichiers</span><span class="sxs-lookup"><span data-stu-id="60b1b-119">Files</span></span>|<span data-ttu-id="60b1b-120">Numéro d’unité logique # ou ML_ #</span><span class="sxs-lookup"><span data-stu-id="60b1b-120">LUN# or ML_#</span></span>|<span data-ttu-id="60b1b-121">Taille LUN physique (Go)</span><span class="sxs-lookup"><span data-stu-id="60b1b-121">Physical LUN Size (GB)</span></span>|  
    |----------------------|-----------------|-----------|---------------------|------------------------------|  
    |<span data-ttu-id="60b1b-122">MessageBox</span><span class="sxs-lookup"><span data-stu-id="60b1b-122">MessageBox</span></span>|<span data-ttu-id="60b1b-123">Data_TempDb_1</span><span class="sxs-lookup"><span data-stu-id="60b1b-123">Data_TempDb_1</span></span>|<span data-ttu-id="60b1b-124">Fichiers de données TEMPDB, MASTER et MSDB</span><span class="sxs-lookup"><span data-stu-id="60b1b-124">TEMPDB,  MASTER, and MSDB data files</span></span>|<span data-ttu-id="60b1b-125">1</span><span class="sxs-lookup"><span data-stu-id="60b1b-125">1</span></span>|<span data-ttu-id="60b1b-126">134</span><span class="sxs-lookup"><span data-stu-id="60b1b-126">134</span></span>|  
    ||<span data-ttu-id="60b1b-127">Logs_TempDb_1</span><span class="sxs-lookup"><span data-stu-id="60b1b-127">Logs_TempDb_1</span></span>|<span data-ttu-id="60b1b-128">Fichiers journaux des transactions TEMPDB, MASTER et MSDB</span><span class="sxs-lookup"><span data-stu-id="60b1b-128">TEMPDB,  MASTER, and MSDB transaction log files</span></span>|<span data-ttu-id="60b1b-129">2</span><span class="sxs-lookup"><span data-stu-id="60b1b-129">2</span></span>|<span data-ttu-id="60b1b-130">134</span><span class="sxs-lookup"><span data-stu-id="60b1b-130">134</span></span>|  
    ||<span data-ttu-id="60b1b-131">Data_BtsMsgBox</span><span class="sxs-lookup"><span data-stu-id="60b1b-131">Data_BtsMsgBox</span></span>|<span data-ttu-id="60b1b-132">Fichier de données BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="60b1b-132">BizTalkMsgBoxDb data file</span></span>|<span data-ttu-id="60b1b-133">3</span><span class="sxs-lookup"><span data-stu-id="60b1b-133">3</span></span>|<span data-ttu-id="60b1b-134">134</span><span class="sxs-lookup"><span data-stu-id="60b1b-134">134</span></span>|  
    ||<span data-ttu-id="60b1b-135">Logs_BtsMsgBox</span><span class="sxs-lookup"><span data-stu-id="60b1b-135">Logs_BtsMsgBox</span></span>|<span data-ttu-id="60b1b-136">Fichier journal des transactions BizTalkMsgBoxDb</span><span class="sxs-lookup"><span data-stu-id="60b1b-136">BizTalkMsgBoxDb transaction log file</span></span>|<span data-ttu-id="60b1b-137">4</span><span class="sxs-lookup"><span data-stu-id="60b1b-137">4</span></span>|<span data-ttu-id="60b1b-138">134</span><span class="sxs-lookup"><span data-stu-id="60b1b-138">134</span></span>|  
    |<span data-ttu-id="60b1b-139">BAM</span><span class="sxs-lookup"><span data-stu-id="60b1b-139">BAM</span></span>|<span data-ttu-id="60b1b-140">Data_TempDb_2</span><span class="sxs-lookup"><span data-stu-id="60b1b-140">Data_TempDb_2</span></span>|<span data-ttu-id="60b1b-141">Fichiers de données TEMPDB, MASTER et MSDB</span><span class="sxs-lookup"><span data-stu-id="60b1b-141">TEMPDB, MASTER, and MSDB data files</span></span>|<span data-ttu-id="60b1b-142">5</span><span class="sxs-lookup"><span data-stu-id="60b1b-142">5</span></span>|<span data-ttu-id="60b1b-143">67</span><span class="sxs-lookup"><span data-stu-id="60b1b-143">67</span></span>|  
    ||<span data-ttu-id="60b1b-144">Logs_TempDb_2</span><span class="sxs-lookup"><span data-stu-id="60b1b-144">Logs_TempDb_2</span></span>|<span data-ttu-id="60b1b-145">Fichiers journaux des transactions TEMPDB, MASTER et MSDB</span><span class="sxs-lookup"><span data-stu-id="60b1b-145">TEMPDB, MASTER, and MSDB transaction log files</span></span>|<span data-ttu-id="60b1b-146">6</span><span class="sxs-lookup"><span data-stu-id="60b1b-146">6</span></span>|<span data-ttu-id="60b1b-147">67</span><span class="sxs-lookup"><span data-stu-id="60b1b-147">67</span></span>|  
    ||<span data-ttu-id="60b1b-148">Data_BAM</span><span class="sxs-lookup"><span data-stu-id="60b1b-148">Data_BAM</span></span>|<span data-ttu-id="60b1b-149">Fichier de données BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="60b1b-149">BAMPrimaryImport data file</span></span>|<span data-ttu-id="60b1b-150">7</span><span class="sxs-lookup"><span data-stu-id="60b1b-150">7</span></span>|<span data-ttu-id="60b1b-151">134</span><span class="sxs-lookup"><span data-stu-id="60b1b-151">134</span></span>|  
    ||<span data-ttu-id="60b1b-152">Logs_BAM</span><span class="sxs-lookup"><span data-stu-id="60b1b-152">Logs_BAM</span></span>|<span data-ttu-id="60b1b-153">Fichier journal des transactions BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="60b1b-153">BAMPrimaryImport transaction log file</span></span>|<span data-ttu-id="60b1b-154">8</span><span class="sxs-lookup"><span data-stu-id="60b1b-154">8</span></span>|<span data-ttu-id="60b1b-155">134</span><span class="sxs-lookup"><span data-stu-id="60b1b-155">134</span></span>|  
    |<span data-ttu-id="60b1b-156">Bases de données des suivis BizTalk, la gestion, l’authentification unique et du moteur de règles</span><span class="sxs-lookup"><span data-stu-id="60b1b-156">BizTalk Tracking, Management, Single Sign-On, and Rule Engine databases</span></span>|<span data-ttu-id="60b1b-157">Data_TempDb_3</span><span class="sxs-lookup"><span data-stu-id="60b1b-157">Data_TempDb_3</span></span>|<span data-ttu-id="60b1b-158">Fichiers de données TEMPDB, MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO et BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="60b1b-158">TEMPDB,  MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO, and BizTalkRuleEngineDb data files</span></span>|<span data-ttu-id="60b1b-159">9</span><span class="sxs-lookup"><span data-stu-id="60b1b-159">9</span></span>|<span data-ttu-id="60b1b-160">67</span><span class="sxs-lookup"><span data-stu-id="60b1b-160">67</span></span>|  
    ||<span data-ttu-id="60b1b-161">Logs_TempDb_3</span><span class="sxs-lookup"><span data-stu-id="60b1b-161">Logs_TempDb_3</span></span>|<span data-ttu-id="60b1b-162">Fichiers journaux des transactions TEMPDB, MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO et BizTalkRuleEngineDb</span><span class="sxs-lookup"><span data-stu-id="60b1b-162">TEMPDB,  MASTER, MSDB, BizTalkDTADb, BizTalkMgmtDb, ENTSSO, and BizTalkRuleEngineDb transaction log files</span></span>|<span data-ttu-id="60b1b-163">10</span><span class="sxs-lookup"><span data-stu-id="60b1b-163">10</span></span>|<span data-ttu-id="60b1b-164">67</span><span class="sxs-lookup"><span data-stu-id="60b1b-164">67</span></span>|  
  
-   <span data-ttu-id="60b1b-165">**Conception de l’hôte BizTalk et les descriptions de chaque ordinateur hôte et leurs instances.**</span><span class="sxs-lookup"><span data-stu-id="60b1b-165">**BizTalk Host design and descriptions of each host and their instances.**</span></span>  
  
-   <span data-ttu-id="60b1b-166">**Description de chaque orchestration.**</span><span class="sxs-lookup"><span data-stu-id="60b1b-166">**Description of each orchestration.**</span></span>  
  
-   <span data-ttu-id="60b1b-167">**Description de chaque pipeline.**</span><span class="sxs-lookup"><span data-stu-id="60b1b-167">**Description of each pipeline.**</span></span>  
  
-   <span data-ttu-id="60b1b-168">**Description des composants personnalisés tels que des assemblys .NET et des composants COM +.**</span><span class="sxs-lookup"><span data-stu-id="60b1b-168">**Description of custom components such as .NET assemblies and COM+ components.**</span></span>  
  
## <a name="detailed-architecture-diagram"></a><span data-ttu-id="60b1b-169">Diagramme d’architecture détaillée</span><span class="sxs-lookup"><span data-stu-id="60b1b-169">Detailed architecture diagram</span></span>  
 <span data-ttu-id="60b1b-170">Le diagramme suivant illustre un diagramme d’architecture qui peut être utilisé pour une évaluation des performances.</span><span class="sxs-lookup"><span data-stu-id="60b1b-170">The following diagram illustrates an architecture diagram that could be used for a performance assessment.</span></span>  
  
 <span data-ttu-id="60b1b-171">![Diagramme d’Architecture BizTalk](../technical-guides/media/architecturediagram.gif "ArchitectureDiagram")</span><span class="sxs-lookup"><span data-stu-id="60b1b-171">![BizTalk Architecture Diagram](../technical-guides/media/architecturediagram.gif "ArchitectureDiagram")</span></span>  
<span data-ttu-id="60b1b-172">Diagramme de l'architecture BizTalk</span><span class="sxs-lookup"><span data-stu-id="60b1b-172">BizTalk Architecture Diagram</span></span>  
  
## <a name="message-flow-diagrams"></a><span data-ttu-id="60b1b-173">Diagrammes de flux de message</span><span class="sxs-lookup"><span data-stu-id="60b1b-173">Message flow diagrams</span></span>  
 <span data-ttu-id="60b1b-174">Créer des diagrammes de flux de message détaillé pour éviter toute confusion ou false hypothèses concernant ce qui doit pour se produire pour les messages au cours du traitement.</span><span class="sxs-lookup"><span data-stu-id="60b1b-174">Create detailed message flow diagrams to help prevent confusion or false assumptions regarding what is supposed to be happening to messages during processing.</span></span>  
  
 <span data-ttu-id="60b1b-175">En matière de guidage une solution BizTalk, nous avons tendance à considérer que le flux de messages via le système.</span><span class="sxs-lookup"><span data-stu-id="60b1b-175">When thinking about a BizTalk solution holistically, we tend to think of the message flow through the system.</span></span> <span data-ttu-id="60b1b-176">Cette perspective de flux de messages est particulièrement importante lors de la tester les performances car toutes les parties du flux doivent être considérées comme des goulots d’étranglement potentiels.</span><span class="sxs-lookup"><span data-stu-id="60b1b-176">This Message Flow perspective is especially important when doing performance testing because all parts of the flow must be considered as potential bottlenecks.</span></span> <span data-ttu-id="60b1b-177">Avoir un diagramme de flux de message empêche toute confusion ou fausses hypothèses concernant ce qui doit pour se produire pour les messages au cours de chaque test exécuté.</span><span class="sxs-lookup"><span data-stu-id="60b1b-177">Having a message flow diagram prevents any confusion or false assumptions regarding what is supposed to be happening to messages during each test run.</span></span>  
  
 <span data-ttu-id="60b1b-178">Dans l’exemple suivant, créé à l’aide de formes Visio, tout le monde sur le projet, quelle que soit l’arrière-plan peut comprendre rapidement comment un message atteint dans le système, quelles parties des solutions interagissent avec le message, et enfin sur lequel le message arrive après lors du traitement.</span><span class="sxs-lookup"><span data-stu-id="60b1b-178">In the following example, created using simple Visio shapes, everyone on the project regardless of background can quickly understand how a message gets into the system, what parts of the solutions interact with the message, and finally where the message lands after processing.</span></span>  
  
 <span data-ttu-id="60b1b-179">![Diagramme de flux de message](../technical-guides/media/11c5afac-5c1b-42a5-8947-7c6d0ca4e2df.gif "11c5afac-5c1b-42a5-8947-7c6d0ca4e2df")</span><span class="sxs-lookup"><span data-stu-id="60b1b-179">![Message Flow Diagram](../technical-guides/media/11c5afac-5c1b-42a5-8947-7c6d0ca4e2df.gif "11c5afac-5c1b-42a5-8947-7c6d0ca4e2df")</span></span>  
<span data-ttu-id="60b1b-180">Diagramme du flux de message</span><span class="sxs-lookup"><span data-stu-id="60b1b-180">Message Flow Diagram</span></span>  
  
 <span data-ttu-id="60b1b-181">Les détails suivants doivent être pris en compte lors de la création de diagrammes de flux de message :</span><span class="sxs-lookup"><span data-stu-id="60b1b-181">The following details should be considered when creating the message flow diagrams:</span></span>  
  
-   <span data-ttu-id="60b1b-182">Décrire le cycle de vie de chaque type de message à partir du moment qu’il arrive à un emplacement de réception jusqu'à ce que tous les messages résultants sont envoyés et toutes les liés au traitement est terminé.</span><span class="sxs-lookup"><span data-stu-id="60b1b-182">Describe the lifecycle of each type of message from the time it arrives at a receive location until all resulting messages are sent and all related processing is completed.</span></span>  
  
-   <span data-ttu-id="60b1b-183">Décrire le traitement des modifications des conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="60b1b-183">Describe how processing changes for error conditions.</span></span>  
  
-   <span data-ttu-id="60b1b-184">Inclure des détails sur la corrélation, les accusés de réception et les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="60b1b-184">Include details about correlation, delivery notifications, and acknowledgements.</span></span>  
  
-   <span data-ttu-id="60b1b-185">Inclure des détails sur la dépendance sur des systèmes externes.</span><span class="sxs-lookup"><span data-stu-id="60b1b-185">Include details about dependence on external systems.</span></span>  
  
-   <span data-ttu-id="60b1b-186">Incluent des informations de condition de performances concernant la latence et le débit.</span><span class="sxs-lookup"><span data-stu-id="60b1b-186">Include performance requirement information regarding latency and throughput.</span></span>  
  
## <a name="third-party-software-details"></a><span data-ttu-id="60b1b-187">Détails des logiciels tiers</span><span class="sxs-lookup"><span data-stu-id="60b1b-187">Third-party software details</span></span>  
 <span data-ttu-id="60b1b-188">Tous les logiciels non Microsoft sont utilisé doivent être entièrement documentée dans le cadre de la conception de solution détaillées.</span><span class="sxs-lookup"><span data-stu-id="60b1b-188">All non-Microsoft software that is used should be fully documented as part of the detailed solution design.</span></span>  
  
## <a name="detailed-lab-hardware-stack"></a><span data-ttu-id="60b1b-189">Pile de matériel de laboratoire détaillées</span><span class="sxs-lookup"><span data-stu-id="60b1b-189">Detailed lab hardware stack</span></span>  
 <span data-ttu-id="60b1b-190">S’appuyant sur le diagramme de matériel de niveau supérieur créé précédemment, les informations matérielles suivantes doivent être entièrement documentées :</span><span class="sxs-lookup"><span data-stu-id="60b1b-190">Building on the previously created high-level hardware diagram, the following hardware information should be fully documented:</span></span>  
  
-   <span data-ttu-id="60b1b-191">Processeurs</span><span class="sxs-lookup"><span data-stu-id="60b1b-191">Processors</span></span>  
  
    -   <span data-ttu-id="60b1b-192">Type</span><span class="sxs-lookup"><span data-stu-id="60b1b-192">Type</span></span>  
  
    -   <span data-ttu-id="60b1b-193">Vitesse</span><span class="sxs-lookup"><span data-stu-id="60b1b-193">Speed</span></span>  
  
    -   <span data-ttu-id="60b1b-194">Nombre de cœurs</span><span class="sxs-lookup"><span data-stu-id="60b1b-194">Number of cores</span></span>  
  
    -   <span data-ttu-id="60b1b-195">Hyperthreading</span><span class="sxs-lookup"><span data-stu-id="60b1b-195">Hyperthreading</span></span>  
  
-   <span data-ttu-id="60b1b-196">Mémoire</span><span class="sxs-lookup"><span data-stu-id="60b1b-196">Memory</span></span>  
  
    -   <span data-ttu-id="60b1b-197">Montant</span><span class="sxs-lookup"><span data-stu-id="60b1b-197">Amount</span></span>  
  
    -   <span data-ttu-id="60b1b-198">Vitesse</span><span class="sxs-lookup"><span data-stu-id="60b1b-198">Speed</span></span>  
  
    -   <span data-ttu-id="60b1b-199">Parité</span><span class="sxs-lookup"><span data-stu-id="60b1b-199">Parity</span></span>  
  
-   <span data-ttu-id="60b1b-200">Réseau</span><span class="sxs-lookup"><span data-stu-id="60b1b-200">Network</span></span>  
  
    -   <span data-ttu-id="60b1b-201">Nombre de cartes d’interface réseau (NIC)</span><span class="sxs-lookup"><span data-stu-id="60b1b-201">Number of network interface cards (NICs)</span></span>  
  
    -   <span data-ttu-id="60b1b-202">Vitesse du réseau</span><span class="sxs-lookup"><span data-stu-id="60b1b-202">Speed of network</span></span>  
  
-   <span data-ttu-id="60b1b-203">RÉSEAU SAN</span><span class="sxs-lookup"><span data-stu-id="60b1b-203">SAN</span></span>  
  
    -   <span data-ttu-id="60b1b-204">Nombre de cartes réseau SAN de chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="60b1b-204">Number of SAN cards in each computer</span></span>  
  
    -   <span data-ttu-id="60b1b-205">Nombre de numéros d’unité logique (LUN) pour chaque ordinateur et l’objectif de chaque numéro d’unité logique</span><span class="sxs-lookup"><span data-stu-id="60b1b-205">Number of logical unit numbers (LUNs) for each computer and purpose for each LUN</span></span>  
  
    -   <span data-ttu-id="60b1b-206">Vitesse de zone de stockage (SAN) cartes du réseau</span><span class="sxs-lookup"><span data-stu-id="60b1b-206">Speed of storage area network (SAN) Cards</span></span>  
  
    -   <span data-ttu-id="60b1b-207">Détails de configuration de carte réseau SAN</span><span class="sxs-lookup"><span data-stu-id="60b1b-207">SAN card configuration details</span></span>  
  
    -   <span data-ttu-id="60b1b-208">Allocation de disque SAN, mise en forme et le partitionnement</span><span class="sxs-lookup"><span data-stu-id="60b1b-208">SAN disk allocation, formatting, and partitioning</span></span>  
  
-   <span data-ttu-id="60b1b-209">Disque</span><span class="sxs-lookup"><span data-stu-id="60b1b-209">Disk</span></span>  
  
    -   <span data-ttu-id="60b1b-210">Détails du disque local pour chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="60b1b-210">Local disk details for each computer</span></span>  
  
    -   <span data-ttu-id="60b1b-211">Mise en forme utilisée pour les disques locaux</span><span class="sxs-lookup"><span data-stu-id="60b1b-211">Formatting used for local disks</span></span>  
  
    -   <span data-ttu-id="60b1b-212">Partitionnement des détails pour les disques locaux</span><span class="sxs-lookup"><span data-stu-id="60b1b-212">Partitioning details for local disks</span></span>  
  
-   <span data-ttu-id="60b1b-213">Cache</span><span class="sxs-lookup"><span data-stu-id="60b1b-213">Cache</span></span>  
  
    -   <span data-ttu-id="60b1b-214">Quantité de mémoire Cache L2</span><span class="sxs-lookup"><span data-stu-id="60b1b-214">L2 Cache amount</span></span>  
  
    -   <span data-ttu-id="60b1b-215">Quantité de mémoire Cache L3</span><span class="sxs-lookup"><span data-stu-id="60b1b-215">L3 Cache amount</span></span>  
  
## <a name="detailed-lab-software-stack"></a><span data-ttu-id="60b1b-216">Pile de logiciels détaillées de laboratoire</span><span class="sxs-lookup"><span data-stu-id="60b1b-216">Detailed lab software stack</span></span>  
 <span data-ttu-id="60b1b-217">Les logiciels suivants doivent être documentées :</span><span class="sxs-lookup"><span data-stu-id="60b1b-217">The following software information should be documented:</span></span>  
  
-   <span data-ttu-id="60b1b-218">Architecture, les éditions et versions de système d’exploitation spécifique</span><span class="sxs-lookup"><span data-stu-id="60b1b-218">Specific operating system versions, editions, and architecture</span></span>  
  
-   <span data-ttu-id="60b1b-219">Fonctionnalités du système d’exploitation spécifique</span><span class="sxs-lookup"><span data-stu-id="60b1b-219">Specific operating system features</span></span>  
  
-   <span data-ttu-id="60b1b-220">Logiciel spécifique installé sur chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="60b1b-220">Specific software installed on each computer</span></span>  
  
-   <span data-ttu-id="60b1b-221">Pilotes spécifiques</span><span class="sxs-lookup"><span data-stu-id="60b1b-221">Specific drivers</span></span>  
  
-   <span data-ttu-id="60b1b-222">Service Packs et autres mises à jour</span><span class="sxs-lookup"><span data-stu-id="60b1b-222">Service Packs and other updates</span></span>  
  
-   <span data-ttu-id="60b1b-223">Valeurs de configuration pour toutes les fonctionnalités de système d’exploitation et les logiciels utilisées si elles diffèrent des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="60b1b-223">Configuration values for all software and operating system features used if they vary from default values</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b1b-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60b1b-224">See Also</span></span>  
 [<span data-ttu-id="60b1b-225">Phases d’une évaluation des performances</span><span class="sxs-lookup"><span data-stu-id="60b1b-225">Phases of a Performance Assessment</span></span>](../technical-guides/phases-of-a-performance-assessment.md)