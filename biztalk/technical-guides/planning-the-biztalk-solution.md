---
title: Planification de la Solution BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30d56a04-966a-46b1-861d-f5be4e58b7d2
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 337883ce2ca3b7f28def19898930d872928a8ce4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="plan-for-your-biztalk-solution"></a><span data-ttu-id="6ec97-102">Planifier votre Solution BizTalk</span><span class="sxs-lookup"><span data-stu-id="6ec97-102">Plan for your BizTalk Solution</span></span>
<span data-ttu-id="6ec97-103">Un des principaux objectifs de création de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est d’offrir une flexibilité maximale pour la prise en charge des scénarios de traitement autant que possible.</span><span class="sxs-lookup"><span data-stu-id="6ec97-103">One of the primary design goals of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is to provide maximum flexibility for accommodating as many processing scenarios as possible.</span></span> <span data-ttu-id="6ec97-104">En raison de cette avec une grande souplesse, un des principaux défis aux développeurs d’une solution BizTalk est pour déterminer comment exploiter les fonctionnalités disponibles dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour mieux répondre à leurs besoins.</span><span class="sxs-lookup"><span data-stu-id="6ec97-104">Because of this great flexibility, one of the primary challenges facing developers of a BizTalk solution is to determine how to make best use of the features available in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to best meet their business needs.</span></span> <span data-ttu-id="6ec97-105">Planification de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut être décomposée en plusieurs phases distinctes qui sont résumés ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6ec97-105">Planning the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] can be broken down into distinct phases which are summarized below.</span></span>  
  
## <a name="scoping-the-solution"></a><span data-ttu-id="6ec97-106">L’étendue de la Solution</span><span class="sxs-lookup"><span data-stu-id="6ec97-106">Scoping the Solution</span></span>  
  
### <a name="performance-considerations"></a><span data-ttu-id="6ec97-107">Considérations relatives aux performances</span><span class="sxs-lookup"><span data-stu-id="6ec97-107">Performance Considerations</span></span>  
 <span data-ttu-id="6ec97-108">Considérez les éléments suivants lorsque la portée de votre solution BizTalk :</span><span class="sxs-lookup"><span data-stu-id="6ec97-108">Consider the following when scoping your BizTalk solution:</span></span>  
  
-   <span data-ttu-id="6ec97-109">Les adaptateurs et/ou les accélérateurs sont nécessaires ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-109">Which adapters and/or accelerators are required?</span></span>  
  
-   <span data-ttu-id="6ec97-110">Quelles sont les conditions requises pour implémenter des orchestrations dans la solution ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-110">What are the requirements for implementing orchestrations in the solution?</span></span>  
  
-   <span data-ttu-id="6ec97-111">Documenter les exigences de débit : quelles sont les exigences de débit maximal acceptable pour la solution ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-111">Document throughput requirements: What are the maximum sustainable throughput requirements for the solution?</span></span>  
  
-   <span data-ttu-id="6ec97-112">Conditions de latence : la réactivité la solution doit-elle être pour les scénarios de sollicitation-réponse et requête-réponse ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-112">Latency requirements: How responsive does the solution need to be for solicit-response and request-response scenarios?</span></span>  
  
-   <span data-ttu-id="6ec97-113">Comment la solution permet de récupérer des périodes de pic de charge de document ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-113">How well does the solution recover from periods of peak document load?</span></span>  
  
-   <span data-ttu-id="6ec97-114">Quelles sont les exigences de haute disponibilité de la solution ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-114">What are the high availability requirements of the solution?</span></span>  
  
-   <span data-ttu-id="6ec97-115">Quelles sont les exigences de suivi de document de la solution ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-115">What are the document tracking requirements of the solution?</span></span>  
  
-   <span data-ttu-id="6ec97-116">Quelles sont les caractéristiques de performances de toutes les applications dépendantes telles que l’autre système ou d’un service Web à distance ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-116">What are the performance characteristics of any dependent applications such as a remote Web service or other system?</span></span> <span data-ttu-id="6ec97-117">Si les applications dépendantes ne conservez pas la charge requise les performances globales du système seront altérée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="6ec97-117">If dependent applications do not keep up with the required load then the overall system performance will be degraded accordingly.</span></span>  
  
-   <span data-ttu-id="6ec97-118">Est l’application BizTalk consomme ne pas liées à des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]?</span><span class="sxs-lookup"><span data-stu-id="6ec97-118">Would the BizTalk application be consuming databases not related to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]?</span></span> <span data-ttu-id="6ec97-119">Par exemple, si l’application BizTalk consomme des tables dans une base de données SQL Server à l’aide de l’adaptateur SQL, sont les tables efficacement configurés ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-119">For example, if the BizTalk application is consuming tables in a SQL Server database using the SQL adapter, are the tables efficiently configured?</span></span>  
  
### <a name="hardware-considerations"></a><span data-ttu-id="6ec97-120">Configuration matérielle requise</span><span class="sxs-lookup"><span data-stu-id="6ec97-120">Hardware Considerations</span></span>  
 <span data-ttu-id="6ec97-121">Lorsque la portée de la solution, créez un diagramme de matériel qui inclut les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6ec97-121">When scoping the solution, create a high-level hardware diagram that includes the following:</span></span>  
  
-   <span data-ttu-id="6ec97-122">Architecture de l’ordinateur (par exemple, x86, x64 et IA64)</span><span class="sxs-lookup"><span data-stu-id="6ec97-122">Computer architecture (such as x86, x64, and IA64)</span></span>  
  
-   <span data-ttu-id="6ec97-123">Configuration requise du processeur (par exemple, le type, la vitesse, nombre, cœurs et utilisation de l’hyperthreading)</span><span class="sxs-lookup"><span data-stu-id="6ec97-123">CPU requirements (such as type, speed, number, cores, and use of hyperthreading)</span></span>  
  
-   <span data-ttu-id="6ec97-124">Mémoire RAM requise pour chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="6ec97-124">RAM requirements for each computer</span></span>  
  
-   <span data-ttu-id="6ec97-125">Stockage de disque local (type, taille, vitesse)</span><span class="sxs-lookup"><span data-stu-id="6ec97-125">Local disk storage (type, size, speed)</span></span>  
  
-   <span data-ttu-id="6ec97-126">Réseau SAN (exigences de stockage : nombre de numéros d’unités logiques ; Type de carte réseau SAN)</span><span class="sxs-lookup"><span data-stu-id="6ec97-126">SAN (storage requirements: number of LUNS; SAN card type)</span></span>  
  
-   <span data-ttu-id="6ec97-127">Cartes réseau (numéro de chaque ordinateur, 100 mégabits (Mbit/s) et 1 Gigabit (1 Gbit/s).)</span><span class="sxs-lookup"><span data-stu-id="6ec97-127">Network cards (number in each computer, 100 megabits (Mbps) versus 1 Gigabit (1 Gbps).)</span></span>  
  
-   <span data-ttu-id="6ec97-128">Comment les pare-feux être déployé dans la solution ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-128">How will firewalls be deployed in the solution?</span></span>  
  
-   <span data-ttu-id="6ec97-129">Matériel d’équilibrage de charge réseau servira ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-129">Will Network Load Balancing hardware be used?</span></span>  
  
-   <span data-ttu-id="6ec97-130">Sont des ordinateurs spécifiques à mettre en cluster ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-130">Are specific computers to be clustered?</span></span>  
  
-   <span data-ttu-id="6ec97-131">Vous utilisent un environnement virtuel impliquant Microsoft Hyper-V Server ou autres produits de virtualisation ?</span><span class="sxs-lookup"><span data-stu-id="6ec97-131">Would you be using a virtual environment involving Microsoft Hyper-V Server or any other virtualization products?</span></span>  
  
## <a name="planning-the-solution"></a><span data-ttu-id="6ec97-132">Planification de la Solution</span><span class="sxs-lookup"><span data-stu-id="6ec97-132">Planning the Solution</span></span>  
  
### <a name="solution-milestones-timeline"></a><span data-ttu-id="6ec97-133">Chronologie des jalons de solution</span><span class="sxs-lookup"><span data-stu-id="6ec97-133">Solution Milestones Timeline</span></span>  
 <span data-ttu-id="6ec97-134">Créer une planification avec étapes majeures pour l’achèvement des aspects spécifiques de votre solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6ec97-134">Create a schedule with milestones for completing specific aspects of your BizTalk solution.</span></span> <span data-ttu-id="6ec97-135">Définition des étapes majeures spécifiques augmente la probabilité que la solution sera effectuée en temps voulu.</span><span class="sxs-lookup"><span data-stu-id="6ec97-135">Setting specific milestones will increase the likelihood that the solution will be completed in a timely manner.</span></span>  
  
### <a name="non-microsoft-software-considerations"></a><span data-ttu-id="6ec97-136">Considérations relatives à des logiciels non Microsoft</span><span class="sxs-lookup"><span data-stu-id="6ec97-136">Non-Microsoft Software Considerations</span></span>  
 <span data-ttu-id="6ec97-137">Considérez les éléments suivants lors de logiciels non Microsoft seront utilisé avec la solution :</span><span class="sxs-lookup"><span data-stu-id="6ec97-137">Consider the following when non-Microsoft software will be used with the solution:</span></span>  
  
-   <span data-ttu-id="6ec97-138">Déterminer comment le logiciel ou matériel requis être obtenu.</span><span class="sxs-lookup"><span data-stu-id="6ec97-138">Determine how the software or hardware required be obtained.</span></span>  
  
-   <span data-ttu-id="6ec97-139">Planifier la capacité et de dimensionnement pour vous assurer que des logiciels non Microsoft n’est pas un goulet d’étranglement dans votre solution.</span><span class="sxs-lookup"><span data-stu-id="6ec97-139">Plan for capacity and sizing to ensure that non-Microsoft software does not become a bottleneck in your solution.</span></span>  
  
-   <span data-ttu-id="6ec97-140">Déterminer un plan d’action pour l’installation de logiciels non Microsoft requis.</span><span class="sxs-lookup"><span data-stu-id="6ec97-140">Determine a plan of action for installing required non-Microsoft software.</span></span>  
  
-   <span data-ttu-id="6ec97-141">Créer un plan d’action pour la configuration et l’optimisation des logiciels non Microsoft requis.</span><span class="sxs-lookup"><span data-stu-id="6ec97-141">Create a plan of action for configuring and optimizing required non-Microsoft software.</span></span>  
  
## <a name="preparing-for-the-solution"></a><span data-ttu-id="6ec97-142">Préparation de la Solution</span><span class="sxs-lookup"><span data-stu-id="6ec97-142">Preparing for the Solution</span></span>  
 <span data-ttu-id="6ec97-143">Inclure les éléments suivants dans la phase de préparation :</span><span class="sxs-lookup"><span data-stu-id="6ec97-143">Include the following elements in your preparation phase:</span></span>  
  
### <a name="detailed-design-of-the-solution-platform"></a><span data-ttu-id="6ec97-144">Conception détaillée de la plateforme de Solution</span><span class="sxs-lookup"><span data-stu-id="6ec97-144">Detailed Design of the Solution Platform</span></span>  
 <span data-ttu-id="6ec97-145">Conception d’une solution détaillées facilite les communications et évite les hypothèses, afin d’amélioreront la flexibilité et l’efficacité de toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="6ec97-145">A detailed solution design facilitates communications and avoids assumptions, which will improve the agility and effectiveness of all activities.</span></span> <span data-ttu-id="6ec97-146">Vous devez entièrement documenter les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6ec97-146">You should fully document the following elements:</span></span>  
  
-   <span data-ttu-id="6ec97-147">Bases de données BizTalk Server et comment elles seront distribuées sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="6ec97-147">BizTalk Server databases and how they will be distributed across computers.</span></span>  
  
-   <span data-ttu-id="6ec97-148">Conception de l’hôte BizTalk et les descriptions de chaque ordinateur hôte et leurs instances.</span><span class="sxs-lookup"><span data-stu-id="6ec97-148">BizTalk Host design and descriptions of each host and their instances.</span></span>  
  
-   <span data-ttu-id="6ec97-149">Description de chaque orchestration.</span><span class="sxs-lookup"><span data-stu-id="6ec97-149">Description of each orchestration.</span></span>  
  
-   <span data-ttu-id="6ec97-150">Description de chaque pipeline.</span><span class="sxs-lookup"><span data-stu-id="6ec97-150">Description of each pipeline.</span></span>  
  
-   <span data-ttu-id="6ec97-151">Description des composants personnalisés tels que des assemblys .NET et des composants COM +.</span><span class="sxs-lookup"><span data-stu-id="6ec97-151">Description of custom components such as .NET assemblies and COM+ components.</span></span>  
  
 <span data-ttu-id="6ec97-152">**Diagrammes de flux de message**</span><span class="sxs-lookup"><span data-stu-id="6ec97-152">**Message Flow Diagrams**</span></span>  
  
 <span data-ttu-id="6ec97-153">Créer des diagrammes de flux de message détaillé pour aider à éviter des hypothèses de confusion ou false sur ce qui doit pour se produire pour les messages au cours du traitement.</span><span class="sxs-lookup"><span data-stu-id="6ec97-153">Create detailed message flow diagrams to help avoid any confusion or false assumptions regarding what is supposed to be happening to messages during processing.</span></span> <span data-ttu-id="6ec97-154">Les détails suivants doivent être pris en compte lors de la création de diagrammes de flux de message :</span><span class="sxs-lookup"><span data-stu-id="6ec97-154">The following details should be considered when creating the message flow diagrams:</span></span>  
  
-   <span data-ttu-id="6ec97-155">Décrire le cycle de vie de chaque type de message à partir du moment qu’il arrive à un emplacement de réception jusqu'à ce que tous les messages résultants sont envoyés et toutes les liés au traitement est terminé.</span><span class="sxs-lookup"><span data-stu-id="6ec97-155">Describe the lifecycle of each type of message from the time it arrives at a receive location until all resulting messages are sent and all related processing is completed.</span></span>  
  
-   <span data-ttu-id="6ec97-156">Décrire le traitement des modifications des conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6ec97-156">Describe how processing changes for error conditions.</span></span>  
  
-   <span data-ttu-id="6ec97-157">Inclure des détails sur la corrélation, les accusés de réception et les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="6ec97-157">Include details about correlation, delivery notifications, and acknowledgements.</span></span>  
  
-   <span data-ttu-id="6ec97-158">Incluent des informations de condition de performances concernant la latence et le débit.</span><span class="sxs-lookup"><span data-stu-id="6ec97-158">Include performance requirement information regarding latency and throughput.</span></span>  
  
 <span data-ttu-id="6ec97-159">**Détails des logiciels non Microsoft**</span><span class="sxs-lookup"><span data-stu-id="6ec97-159">**Non-Microsoft Software Details**</span></span>  
  
 <span data-ttu-id="6ec97-160">Tous les logiciels non Microsoft sont utilisé doivent être entièrement documentée dans le cadre de la conception de solution détaillées.</span><span class="sxs-lookup"><span data-stu-id="6ec97-160">All non-Microsoft software that is used should be fully documented as part of the detailed solution design.</span></span>  
  
 <span data-ttu-id="6ec97-161">**Pile de matérielles détaillées**</span><span class="sxs-lookup"><span data-stu-id="6ec97-161">**Detailed Hardware Stack**</span></span>  
  
 <span data-ttu-id="6ec97-162">S’appuyant sur le diagramme de matériel de haut niveau créé précédemment, les informations matérielles suivantes doivent être entièrement documentées :</span><span class="sxs-lookup"><span data-stu-id="6ec97-162">Building on the previously created high level hardware diagram, the following hardware information should be fully documented:</span></span>  
  
-   <span data-ttu-id="6ec97-163">Processeurs</span><span class="sxs-lookup"><span data-stu-id="6ec97-163">Processors</span></span>  
  
    -   <span data-ttu-id="6ec97-164">Type</span><span class="sxs-lookup"><span data-stu-id="6ec97-164">Type</span></span>  
  
    -   <span data-ttu-id="6ec97-165">Vitesse</span><span class="sxs-lookup"><span data-stu-id="6ec97-165">Speed</span></span>  
  
    -   <span data-ttu-id="6ec97-166">Nombre de cœurs</span><span class="sxs-lookup"><span data-stu-id="6ec97-166">Number of cores</span></span>  
  
    -   <span data-ttu-id="6ec97-167">Hyperthreading</span><span class="sxs-lookup"><span data-stu-id="6ec97-167">Hyperthreading</span></span>  
  
-   <span data-ttu-id="6ec97-168">Mémoire</span><span class="sxs-lookup"><span data-stu-id="6ec97-168">Memory</span></span>  
  
    -   <span data-ttu-id="6ec97-169">Montant</span><span class="sxs-lookup"><span data-stu-id="6ec97-169">Amount</span></span>  
  
    -   <span data-ttu-id="6ec97-170">Vitesse</span><span class="sxs-lookup"><span data-stu-id="6ec97-170">Speed</span></span>  
  
    -   <span data-ttu-id="6ec97-171">Parité</span><span class="sxs-lookup"><span data-stu-id="6ec97-171">Parity</span></span>  
  
-   <span data-ttu-id="6ec97-172">Réseau</span><span class="sxs-lookup"><span data-stu-id="6ec97-172">Network</span></span>  
  
    -   <span data-ttu-id="6ec97-173">Nombre de cartes d’interface réseau (NIC)</span><span class="sxs-lookup"><span data-stu-id="6ec97-173">Number of network interface cards (NICs)</span></span>  
  
    -   <span data-ttu-id="6ec97-174">Vitesse du réseau</span><span class="sxs-lookup"><span data-stu-id="6ec97-174">Speed of network</span></span>  
  
-   <span data-ttu-id="6ec97-175">RÉSEAU SAN</span><span class="sxs-lookup"><span data-stu-id="6ec97-175">SAN</span></span>  
  
    -   <span data-ttu-id="6ec97-176">Nombre de cartes réseau SAN de chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="6ec97-176">Number of SAN cards in each computer</span></span>  
  
    -   <span data-ttu-id="6ec97-177">Nombre de numéros d’unité logique (LUN) pour chaque ordinateur et l’objectif de chaque numéro d’unité logique</span><span class="sxs-lookup"><span data-stu-id="6ec97-177">Number of logical unit numbers (LUNs) for each computer and purpose for each LUN</span></span>  
  
    -   <span data-ttu-id="6ec97-178">Vitesse de zone de stockage (SAN) cartes du réseau</span><span class="sxs-lookup"><span data-stu-id="6ec97-178">Speed of storage area network (SAN) Cards</span></span>  
  
    -   <span data-ttu-id="6ec97-179">Détails de configuration de carte réseau SAN</span><span class="sxs-lookup"><span data-stu-id="6ec97-179">SAN card configuration details</span></span>  
  
    -   <span data-ttu-id="6ec97-180">Allocation de disque SAN, mise en forme et le partitionnement</span><span class="sxs-lookup"><span data-stu-id="6ec97-180">SAN disk allocation, formatting, and partitioning</span></span>  
  
-   <span data-ttu-id="6ec97-181">Disque</span><span class="sxs-lookup"><span data-stu-id="6ec97-181">Disk</span></span>  
  
    -   <span data-ttu-id="6ec97-182">Détails du disque local pour chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="6ec97-182">Local disk details for each computer</span></span>  
  
    -   <span data-ttu-id="6ec97-183">Mise en forme utilisée pour les disques locaux</span><span class="sxs-lookup"><span data-stu-id="6ec97-183">Formatting used for local disks</span></span>  
  
    -   <span data-ttu-id="6ec97-184">Partitionnement des détails pour les disques locaux</span><span class="sxs-lookup"><span data-stu-id="6ec97-184">Partitioning details for local disks</span></span>  
  
-   <span data-ttu-id="6ec97-185">Cache</span><span class="sxs-lookup"><span data-stu-id="6ec97-185">Cache</span></span>  
  
    -   <span data-ttu-id="6ec97-186">Quantité de mémoire Cache L2</span><span class="sxs-lookup"><span data-stu-id="6ec97-186">L2 Cache amount</span></span>  
  
    -   <span data-ttu-id="6ec97-187">Quantité de mémoire Cache L3</span><span class="sxs-lookup"><span data-stu-id="6ec97-187">L3 Cache amount</span></span>  
  
 <span data-ttu-id="6ec97-188">**Pile logicielle détaillées**</span><span class="sxs-lookup"><span data-stu-id="6ec97-188">**Detailed Software Stack**</span></span>  
  
 <span data-ttu-id="6ec97-189">Les logiciels suivants doivent être documentées :</span><span class="sxs-lookup"><span data-stu-id="6ec97-189">The following software information should be documented:</span></span>  
  
-   <span data-ttu-id="6ec97-190">Architecture, les éditions et versions de système d’exploitation spécifique</span><span class="sxs-lookup"><span data-stu-id="6ec97-190">Specific operating system versions, editions, and architecture</span></span>  
  
-   <span data-ttu-id="6ec97-191">Fonctionnalités du système d’exploitation spécifique</span><span class="sxs-lookup"><span data-stu-id="6ec97-191">Specific operating system features</span></span>  
  
-   <span data-ttu-id="6ec97-192">Logiciel spécifique installé sur chaque ordinateur</span><span class="sxs-lookup"><span data-stu-id="6ec97-192">Specific software installed on each computer</span></span>  
  
-   <span data-ttu-id="6ec97-193">Pilotes spécifiques</span><span class="sxs-lookup"><span data-stu-id="6ec97-193">Specific drivers</span></span>  
  
-   <span data-ttu-id="6ec97-194">Service Packs et autres mises à jour</span><span class="sxs-lookup"><span data-stu-id="6ec97-194">Service Packs and other updates</span></span>  
  
-   <span data-ttu-id="6ec97-195">Valeurs de configuration pour toutes les fonctionnalités de système d’exploitation et les logiciels utilisées si elles diffèrent des valeurs par défaut</span><span class="sxs-lookup"><span data-stu-id="6ec97-195">Configuration values for all software and operating system features used if they vary from default values</span></span>  
  
## <a name="building-out-the-environment-for-the-solution"></a><span data-ttu-id="6ec97-196">Création de l’environnement de la Solution</span><span class="sxs-lookup"><span data-stu-id="6ec97-196">Building Out the Environment for the Solution</span></span>  
 <span data-ttu-id="6ec97-197">Instructions détaillées pour l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et la configuration logicielle requise est dans le [Guides d’Installation de BizTalk Server](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span><span class="sxs-lookup"><span data-stu-id="6ec97-197">Detailed instructions for installing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the software requirements are in the [BizTalk Server Installation Guides](../install-and-config-guides/biztalk-server-what-s-new-installation-configuration-and-upgrade.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6ec97-198">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ec97-198">See Also</span></span>  
 [<span data-ttu-id="6ec97-199">Planification du niveau BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6ec97-199">Planning the BizTalk Server Tier</span></span>](../technical-guides/planning-the-biztalk-server-tier.md)
