---
title: "Instructions pour la résolution des problèmes d’autorisations SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c24512-5f65-4363-b806-8dd52b22f179
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db02fd2a981d3f1dc34924e680caf5926f67871a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-resolving-sql-server-permissions-problems"></a><span data-ttu-id="211a5-102">Instructions pour la résolution des problèmes d'autorisation liés à SQL Server</span><span class="sxs-lookup"><span data-stu-id="211a5-102">Guidelines for Resolving SQL Server Permissions Problems</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="211a5-103"> exploite pleinement les bases de données Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour les opérations d'exécution. Il est par conséquent important que les autorisations [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] soient définies correctement.</span><span class="sxs-lookup"><span data-stu-id="211a5-103"> makes extensive use of Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] databases for run-time operations and as such, it is important that the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permissions are set correctly.</span></span> <span data-ttu-id="211a5-104">Cette rubrique fournit des indications générales pour minimiser [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des problèmes d’autorisation et les étapes que vous pouvez suivre pour résoudre les problèmes [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des problèmes d’autorisation qui affectent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="211a5-104">This topic provides some general guidelines for minimizing [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permissions problems and steps that you can follow to troubleshoot [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] permissions problems that affect [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="general-guidelines"></a><span data-ttu-id="211a5-105">Règles générales</span><span class="sxs-lookup"><span data-stu-id="211a5-105">General Guidelines</span></span>  
  
-   <span data-ttu-id="211a5-106">**Utiliser des utilisateurs et des groupes pour une installation multiserveur de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="211a5-106">**Use domain users and groups for a multicomputer installation of BizTalk Server**</span></span>  
  
     <span data-ttu-id="211a5-107">Vous devez utiliser des groupes d'utilisateurs et des comptes de domaine lors de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour une exécution sur plusieurs ordinateurs, par exemple, lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts.</span><span class="sxs-lookup"><span data-stu-id="211a5-107">You must use domain user groups and accounts when configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to run in a multicomputer scenario, for example, where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] are installed on separate computers.</span></span> <span data-ttu-id="211a5-108">N’essayez pas de configurer ou exécutez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un *pass-through* scénario d’authentification par laquelle des paires nom d’utilisateur et mots de passe sont créés sur chaque ordinateur pour éviter d’utiliser des comptes et groupes de domaine.</span><span class="sxs-lookup"><span data-stu-id="211a5-108">Do not attempt to configure or run [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a *pass-through* authentication scenario whereby matching pairs of usernames and passwords are created on each computer to avoid using domain groups and accounts.</span></span> <span data-ttu-id="211a5-109">Bien qu'un tel scénario puisse fonctionner correctement dans certains cas, il entraînera l'échec de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans d'autres scénarios. De plus, ce n'est pas une configuration prise en charge.</span><span class="sxs-lookup"><span data-stu-id="211a5-109">While such a pass-through scenario may appear to function correctly in some scenarios, this will cause [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to fail in other scenarios and is not a supported configuration.</span></span>  
  
     <span data-ttu-id="211a5-110">Pour plus d’informations sur l’installation et la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement multiserveurs, téléchargez le Guide d’Installation à [Installation Guides Related to BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582).</span><span class="sxs-lookup"><span data-stu-id="211a5-110">For more information about installing and configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in a multicomputer configuration, download the Installation Guide at [Installation Guides Related to BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582).</span></span>  
  
-   <span data-ttu-id="211a5-111">**Assurez-vous que les utilisateurs Windows et les groupes appropriés sont définis dans les rôles SQL Server appropriés**</span><span class="sxs-lookup"><span data-stu-id="211a5-111">**Ensure that the appropriate Windows users and groups are defined in the appropriate SQL Server roles**</span></span>  
  
     <span data-ttu-id="211a5-112">Vérifiez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] l’appartenance au rôle tel qu’il figure dans la table dans la rubrique [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="211a5-112">Verify correct [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] role membership as listed in the table in the topic [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="211a5-113">**Utilisateur SQL Server Profiler pour diagnostiquer les problèmes d’autorisations**</span><span class="sxs-lookup"><span data-stu-id="211a5-113">**User SQL Server Profiler to diagnose permissions problems**</span></span>  
  
     <span data-ttu-id="211a5-114">Configurer un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] trace Profiler pour surveiller le **événement d’échec de la connexion d’Audit** pour recueillir des informations détaillées sur les échecs d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="211a5-114">Set up a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler trace to monitor the **Audit Login Failed Event** to gather detailed information about permissions failures.</span></span> <span data-ttu-id="211a5-115">Pour plus d'informations sur l'utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, consultez la documentation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="211a5-115">For information about how to use [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, see the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="211a5-116">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="211a5-116">Known Issues</span></span>  
  
#### <a name="the-sql-server-jobs-that-are-installed-with-biztalk-server-fail-to-execute"></a><span data-ttu-id="211a5-117">Les travaux SQL Server installés avec BizTalk Server ne peuvent pas être exécutés</span><span class="sxs-lookup"><span data-stu-id="211a5-117">The SQL Server jobs that are installed with BizTalk Server fail to execute</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="211a5-118">Problème</span><span class="sxs-lookup"><span data-stu-id="211a5-118">Problem</span></span>  
 <span data-ttu-id="211a5-119">Les travaux SQL Server installés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] échouent et des erreurs similaires aux erreurs suivantes sont générées dans le journal de l'application [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] :</span><span class="sxs-lookup"><span data-stu-id="211a5-119">The SQL Server jobs that are installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fail and errors similar to the following are generated in the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Application log:</span></span>  
  
 <span data-ttu-id="211a5-120">Type d'événement : Avertissement</span><span class="sxs-lookup"><span data-stu-id="211a5-120">Event Type: Warning</span></span>  
  
 <span data-ttu-id="211a5-121">Source d'événement : SQLSERVERAGENT</span><span class="sxs-lookup"><span data-stu-id="211a5-121">Event Source: SQLSERVERAGENT</span></span>  
  
 <span data-ttu-id="211a5-122">Catégorie d'événement : Moteur de travail</span><span class="sxs-lookup"><span data-stu-id="211a5-122">Event Category: Job Engine</span></span>  
  
 <span data-ttu-id="211a5-123">ID d’événement : 208</span><span class="sxs-lookup"><span data-stu-id="211a5-123">Event ID: 208</span></span>  
  
 <span data-ttu-id="211a5-124">Date : 29/06/2008</span><span class="sxs-lookup"><span data-stu-id="211a5-124">Date: 6/29/2008</span></span>  
  
 <span data-ttu-id="211a5-125">Heure : 16:45:01</span><span class="sxs-lookup"><span data-stu-id="211a5-125">Time: 4:45:01 PM</span></span>  
  
 <span data-ttu-id="211a5-126">Utilisateur : n/a</span><span class="sxs-lookup"><span data-stu-id="211a5-126">User: N/A</span></span>  
  
 <span data-ttu-id="211a5-127">Ordinateur : *SQLServer*</span><span class="sxs-lookup"><span data-stu-id="211a5-127">Computer: *SQLServer*</span></span>  
  
 <span data-ttu-id="211a5-128">Description :</span><span class="sxs-lookup"><span data-stu-id="211a5-128">Description:</span></span>  
  
 <span data-ttu-id="211a5-129">Travail planifié de SQL Server « Backup BizTalk Server »</span><span class="sxs-lookup"><span data-stu-id="211a5-129">SQL Server Scheduled Job 'Backup BizTalk Server'</span></span>  
  
 <span data-ttu-id="211a5-130">(0x4AC7C44A48541443927A56C5C6699ECF) - État : Échec - Appelé le : 29-6-2008 13:45:01 - Message : Le travail a échoué.</span><span class="sxs-lookup"><span data-stu-id="211a5-130">(0x4AC7C44A48541443927A56C5C6699ECF) - Status: Failed - Invoked on: 2008-6-29 13:45:01 - Message: The job failed.</span></span>  <span data-ttu-id="211a5-131">Le travail a été appelé par Planification 305 (MarkAndBackupLogSched).</span><span class="sxs-lookup"><span data-stu-id="211a5-131">The Job was invoked by Schedule 305 (MarkAndBackupLogSched).</span></span> <span data-ttu-id="211a5-132">La dernière étape exécutée est l'étape 1 (BackupFull).</span><span class="sxs-lookup"><span data-stu-id="211a5-132">The last step to run was step 1 (BackupFull).</span></span>  
  
 <span data-ttu-id="211a5-133">**- et -**</span><span class="sxs-lookup"><span data-stu-id="211a5-133">**- and -**</span></span>  
  
 <span data-ttu-id="211a5-134">Type d'événement : Informations</span><span class="sxs-lookup"><span data-stu-id="211a5-134">Event Type: Information</span></span>  
  
 <span data-ttu-id="211a5-135">Source d'événement : MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="211a5-135">Event Source: MSSQLSERVER</span></span>  
  
 <span data-ttu-id="211a5-136">Catégorie d'événement : (4)</span><span class="sxs-lookup"><span data-stu-id="211a5-136">Event Category: (4)</span></span>  
  
 <span data-ttu-id="211a5-137">ID de l'événement : 17055</span><span class="sxs-lookup"><span data-stu-id="211a5-137">Event ID: 17055</span></span>  
  
 <span data-ttu-id="211a5-138">Date : 29/06/2008</span><span class="sxs-lookup"><span data-stu-id="211a5-138">Date: 6/29/2008</span></span>  
  
 <span data-ttu-id="211a5-139">Heure : 16:45:01</span><span class="sxs-lookup"><span data-stu-id="211a5-139">Time: 4:45:01 PM</span></span>  
  
 <span data-ttu-id="211a5-140">Utilisateur : n/a</span><span class="sxs-lookup"><span data-stu-id="211a5-140">User: N/A</span></span>  
  
 <span data-ttu-id="211a5-141">Ordinateur : *SQLServer*</span><span class="sxs-lookup"><span data-stu-id="211a5-141">Computer: *SQLServer*</span></span>  
  
 <span data-ttu-id="211a5-142">Description :</span><span class="sxs-lookup"><span data-stu-id="211a5-142">Description:</span></span>  
  
 <span data-ttu-id="211a5-143">18456 : Échec de l'ouverture de session pour l'utilisateur 'NT AUTHORITY\SYSTEM'</span><span class="sxs-lookup"><span data-stu-id="211a5-143">18456: Login failed for user 'NT AUTHORITY\SYSTEM'.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="211a5-144">Cause</span><span class="sxs-lookup"><span data-stu-id="211a5-144">Cause</span></span>  
 <span data-ttu-id="211a5-145">Cette erreur peut se produire si la connexion BUILTIN\Administrators a été supprimée de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="211a5-145">This error can occur if the BUILTIN\Administrators login has been removed from [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="211a5-146">Si cette connexion est supprimée, sqlmaint.exe ne pourra pas se connecter à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], ce qui empêchera les travaux SQL d'être exécutés.</span><span class="sxs-lookup"><span data-stu-id="211a5-146">If the BUILTIN\Administrators login is deleted, sqlmaint.exe will be unable to logon to [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] which will prevent SQL jobs from running.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="211a5-147">Résolution</span><span class="sxs-lookup"><span data-stu-id="211a5-147">Resolution</span></span>  
 <span data-ttu-id="211a5-148">Pour résoudre ce problème, recréez la connexion BUILTIN\Administrators et ajoutez-la au rôle db_owner des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de la base de données Master.</span><span class="sxs-lookup"><span data-stu-id="211a5-148">To resolve this issue, re-create the BUILTIN\Administrators Login and add it to the db_owner role for the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and the Master database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="211a5-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="211a5-149">See Also</span></span>  
 <span data-ttu-id="211a5-150">[Dépannage de SQL Server](../core/troubleshooting-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="211a5-150">[Troubleshooting SQL Server](../core/troubleshooting-sql-server.md) </span></span>  
 [<span data-ttu-id="211a5-151">Résolution des problèmes d’autorisations BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="211a5-151">Troubleshooting BizTalk Server Permissions</span></span>](../core/troubleshooting-biztalk-server-permissions.md)