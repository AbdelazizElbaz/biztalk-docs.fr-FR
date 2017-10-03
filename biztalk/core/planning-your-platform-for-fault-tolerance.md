---
title: "Planification de votre plateforme de la tolérance de panne | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- MessageBox database, fault tolerance
- clustering, fault tolerance
- SQL Server RAID
- databases [BAM], fault tolerance
- BizTalk Server, planning
- fault tolerance
- clustering, fail-overs
- planning, fault tolerance
- Primary Import database [BAM]
- BizTalk Server, backing up
- fault tolerance, planning
- planning, BizTalk Server
- Primary Import database [BAM], fault tolerance
- fail-over clustering
ms.assetid: 512ed6b8-db1e-434a-8009-63e952cf5500
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32cb8913ff48ed954e6e57140417966846641f54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-your-platform-for-fault-tolerance"></a><span data-ttu-id="750ac-102">Planification de votre plateforme de la tolérance de panne</span><span class="sxs-lookup"><span data-stu-id="750ac-102">Planning Your Platform for Fault Tolerance</span></span>
<span data-ttu-id="750ac-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est basé sur les plateformes Microsoft Windows et Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="750ac-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is built on the Microsoft Windows and Microsoft SQL Server platforms.</span></span> <span data-ttu-id="750ac-104">Les capacités de résistance et de récupération de BizTalk Server après un sinistre dépendent de celles de la plateforme sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="750ac-104">The ability of BizTalk Server to survive or recover from a disaster depends on the ability of the underlying platform to survive or recover.</span></span>  
  
 <span data-ttu-id="750ac-105">Pour vos bases de données analyse BAM (Business Activity) et votre base de données MessageBox, nous vous recommandons de que procéder comme suit :</span><span class="sxs-lookup"><span data-stu-id="750ac-105">For your Business Activity Monitoring (BAM) databases and your MessageBox database, we recommend you do the following:</span></span>  
  
-   <span data-ttu-id="750ac-106">Définissez un système de clusters avec basculement en cas de sinistre, disponible avec SQL Server Enterprise Edition.</span><span class="sxs-lookup"><span data-stu-id="750ac-106">Set up fail-over clustering, which is available in SQL Server Enterprise Edition.</span></span> <span data-ttu-id="750ac-107">La mise en place de serveurs en cluster avec basculement permet à SQL Server de basculer automatiquement le traitement d'une instance SQL Server entre un serveur défaillant et un serveur opérationnel.</span><span class="sxs-lookup"><span data-stu-id="750ac-107">Fail-over clustering enables SQL Server to automatically switch the processing for an instance of SQL Server from a failed server to a working server.</span></span>  
  
     <span data-ttu-id="750ac-108">La base de données d'importation principale BAM collecte les données d'événement.</span><span class="sxs-lookup"><span data-stu-id="750ac-108">The BAM Primary Import database collects event data.</span></span> <span data-ttu-id="750ac-109">En cas de sinistre, les données ajoutées à cette base de données depuis la dernière sauvegarde seront perdues.</span><span class="sxs-lookup"><span data-stu-id="750ac-109">In the event of a disaster, data that was written to the BAM Primary Import database since the last backup will be lost.</span></span> <span data-ttu-id="750ac-110">Sachant qu'il n'existe aucune solution pour régénérer les événements perdus, il est très important d'activer le système de clusters avec basculement pour la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="750ac-110">Because there is no way to regenerate lost events, it is especially important that you enable fail over clustering on your BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="750ac-111">Utilisez le RAID (redundant array of independent disks) SQL Server, notamment pour la base de données MessageBox et celle d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="750ac-111">Use SQL Server RAID (redundant array of independent disks), especially for the MessageBox database and the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="750ac-112">Servez-vous des ressources ci-dessous pour élaborer les déploiements Windows et SQL Server et les doter d'une tolérance de pannes.</span><span class="sxs-lookup"><span data-stu-id="750ac-112">Use the following resources to design your Windows and SQL Server deployments for fault tolerance.</span></span> <span data-ttu-id="750ac-113">Prenez le temps de vous familiariser avec les technologies de redondance de serveurs et de matériels (mise en cluster et mise en miroir du disque) afin d'éviter les pannes de service et les pertes de données.</span><span class="sxs-lookup"><span data-stu-id="750ac-113">Take time to learn about hardware and server redundancy technologies, such as clustering and disk mirroring, to prevent service outages and data loss.</span></span>  
  
-   [<span data-ttu-id="750ac-114">Livre blanc : Haute disponibilité : Always On Technologies</span><span class="sxs-lookup"><span data-stu-id="750ac-114">White Paper: High Availability—Always On Technologies</span></span>](http://go.microsoft.com/fwlink/?LinkId=130376)  
  
     <span data-ttu-id="750ac-115">Le livre blanc « High Availability – Always On Technologies » présente les fonctionnalités de haute disponibilité disponibles avec SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="750ac-115">The “High Availability – Always On Technologies” whitepaper describes high availability features that are available with SQL Server 2008.</span></span>  
  
-   [<span data-ttu-id="750ac-116">Vue d’ensemble des Solutions de haute disponibilité</span><span class="sxs-lookup"><span data-stu-id="750ac-116">High Availability Solutions Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=130377)  
  
     <span data-ttu-id="750ac-117">Présente plusieurs solutions haute disponibilité SQL Server 2008 qui améliorent la disponibilité des serveurs ou des bases de données.</span><span class="sxs-lookup"><span data-stu-id="750ac-117">Introduces several high-availability solutions for SQL Server 2008 that improve the availability of servers or databases.</span></span>  
  
-   [<span data-ttu-id="750ac-118">Chapitre 15 - Options de haute disponibilité SQL Server Resource Kit</span><span class="sxs-lookup"><span data-stu-id="750ac-118">Chapter 15 - High Availability Options, SQL Server Resource Kit</span></span>](http://go.microsoft.com/fwlink/?LinkId=24431)  
  
     <span data-ttu-id="750ac-119">Ce kit aborde un certain nombre de questions portant sur l'administration et la planification du déploiement.</span><span class="sxs-lookup"><span data-stu-id="750ac-119">The Microsoft SQL Server Resource Kit covers a wide range of administrative and deployment planning areas.</span></span> <span data-ttu-id="750ac-120">Le chapitre 15 traite plus particulièrement de la planification d'une tolérance de pannes et de la récupération.</span><span class="sxs-lookup"><span data-stu-id="750ac-120">Chapter 15 covers planning for fault tolerance and recovery.</span></span>  
  
-   [<span data-ttu-id="750ac-121">Guide pas à pas des Services de déploiement Windows</span><span class="sxs-lookup"><span data-stu-id="750ac-121">Windows Deployment Services Step-by-Step Guide</span></span>](http://go.microsoft.com/fwlink/?LinkId=130379)  
  
     <span data-ttu-id="750ac-122">Contient des instructions détaillées pour savoir comment utiliser le rôle Services de déploiement Windows dans Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="750ac-122">Contains step-by-step guidance for how to use the Windows Deployment Services role in Windows Server 2008</span></span>  
  
-   <span data-ttu-id="750ac-123">[Kit de déploiement de Windows Server 2003 : Planification des déploiements de serveur](http://go.microsoft.com/fwlink/?LinkId=24433).</span><span class="sxs-lookup"><span data-stu-id="750ac-123">[Windows Server 2003 Deployment Kit: Planning Server Deployments](http://go.microsoft.com/fwlink/?LinkId=24433).</span></span>  
  
     <span data-ttu-id="750ac-124">Ce document fournit des informations sur la planification du stockage sur un serveur et sur la conception et le déploiement de serveurs de fichiers, de serveurs d'impression et de Terminal Server dans les moyennes et grandes entreprises.</span><span class="sxs-lookup"><span data-stu-id="750ac-124">This book provides information about planning server storage, and information about designing and deploying file servers, print servers, and terminal servers in medium and large organizations.</span></span>  
  
     <span data-ttu-id="750ac-125">Vous pouvez également vous référer aux instructions de ce document pour accroître la disponibilité et l'évolutivité des serveurs grâce à une planification de la gestion à distance des serveurs et à la conception et au déploiement de clusters de serveurs et de clusters d'équilibrage de la charge réseau.</span><span class="sxs-lookup"><span data-stu-id="750ac-125">You can also use the guidelines in this book to maximize the availability and scalability of your servers by planning for remote server management, designing and deploying server clusters, and designing and deploying Network Load Balancing clusters.</span></span>  
  
## <a name="backing-up-your-platform"></a><span data-ttu-id="750ac-126">Sauvegarde de votre plateforme.</span><span class="sxs-lookup"><span data-stu-id="750ac-126">Backing Up Your Platform</span></span>  
 <span data-ttu-id="750ac-127">Après avoir configuré le système, préparez des sauvegardes complètes des différents serveurs afin de pouvoir rapidement rétablir un serveur à l'identique en cas de perte de données.</span><span class="sxs-lookup"><span data-stu-id="750ac-127">After you have configured your system, prepare full backups of your servers so you can quickly restore an identical server in the event of data loss.</span></span>  
  
 <span data-ttu-id="750ac-128">Pour sauvegarder la plateforme, suivez les procédures des documentations de chacune des technologies suivantes :</span><span class="sxs-lookup"><span data-stu-id="750ac-128">To back up your platform, perform the documented backup procedures for each of the following technologies:</span></span>  
  
-   <span data-ttu-id="750ac-129">Microsoft Windows Server Standard, Enterprise ou Datacenter Edition</span><span class="sxs-lookup"><span data-stu-id="750ac-129">Microsoft Windows Server Standard, Enterprise, or Datacenter Edition</span></span>  
  
-   <span data-ttu-id="750ac-130">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="750ac-130">Internet Information Services (IIS)</span></span>  
  
-   <span data-ttu-id="750ac-131">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="750ac-131">Microsoft SQL Server</span></span>  
  
-   <span data-ttu-id="750ac-132">Windows SharePoint Services, utilisé par l'adaptateur Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="750ac-132">Windows SharePoint Services, which is used by the Windows SharePoint Services adapter.</span></span>  
  
 <span data-ttu-id="750ac-133">Suivez les recommandations de « BizTalk Server Operations Guide » pour « Sauvegarde de BizTalk Server » disponible à l’adresse [Checklist : Increasing Availability with la récupération d’urgence](http://go.microsoft.com/fwlink/?LinkId=130498).</span><span class="sxs-lookup"><span data-stu-id="750ac-133">Follow the recommendations in the “BizTalk Server Operations Guide” for “Backing up BizTalk Server” available at [Checklist: Increasing Availability with Disaster Recovery](http://go.microsoft.com/fwlink/?LinkId=130498).</span></span>  
  
 <span data-ttu-id="750ac-134">Testez minutieusement les procédures de sauvegarde et de restauration et conservez-les sur un emplacement distant et sécurisé.</span><span class="sxs-lookup"><span data-stu-id="750ac-134">Thoroughly test your backup and restore procedures, and put them in a safe, remote location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750ac-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="750ac-135">See Also</span></span>  
 [<span data-ttu-id="750ac-136">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="750ac-136">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)