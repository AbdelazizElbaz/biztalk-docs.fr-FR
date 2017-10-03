---
title: Comment planifier le travail de sauvegarde de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, scheduling
- backing up, backup jobs
- scheduling, backup jobs
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d6b40ae933874e1c25cb3a93dbbeab514ef5dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="70030-102">Planification du travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="70030-102">How to Schedule the Backup BizTalk Server Job</span></span>
<span data-ttu-id="70030-103">Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté selon la planification du service SQL Server Agent.</span><span class="sxs-lookup"><span data-stu-id="70030-103">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service.</span></span> <span data-ttu-id="70030-104">Si vous souhaitez varier la fréquence des sauvegardes, vous pouvez modifier la planification du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="70030-104">If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="70030-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="70030-105">Prerequisites</span></span>  
 <span data-ttu-id="70030-106">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="70030-106">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-schedule-the-backup-biztalk-server-job-sql-server-2008"></a><span data-ttu-id="70030-107">Planification du travail de sauvegarde de BizTalk Server (SQL Server 2008)</span><span class="sxs-lookup"><span data-stu-id="70030-107">To schedule the Backup BizTalk Server job (SQL Server 2008)</span></span>  
  
1.  <span data-ttu-id="70030-108">Sur l’ordinateur qui contient la base de données de gestion BizTalk, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **Microsoft SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="70030-108">On the computer that contains the BizTalk Management database, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **Microsoft SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="70030-109">Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL sur lequel BizTalk Server bases de données résident et l’authentification appropriée, puis tapez **connexion**.</span><span class="sxs-lookup"><span data-stu-id="70030-109">In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Server databases reside and the appropriate authentication type, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="70030-110">Dans l’Explorateur d’objets, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.</span><span class="sxs-lookup"><span data-stu-id="70030-110">In the Object Explorer, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="70030-111">Dans le volet détails, cliquez sur **sauvegarde de BizTalk Server (BizTalkMgmtDb)**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="70030-111">In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="70030-112">Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.</span><span class="sxs-lookup"><span data-stu-id="70030-112">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="70030-113">Dans le **liste des étapes du travail**, cliquez sur **BackupFull**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="70030-113">In the **Job step list**, click **BackupFull**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="70030-114">Dans le **propriétés étape du travail - BackupFull** boîte de dialogue le **commande** , modifiez la commande en changeant la fréquence à laquelle effectuer une sauvegarde complète de l’intervalle souhaité : **'h'** (horaire), **avait '** (quotidienne), **« w »** (hebdomadaire), **suis '** (mensuelle), **'y'** (annuelle), puis cliquez sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="70030-114">In the **Job Step Properties - BackupFull** dialog box, in the **Command** box, edit the command by changing the frequency to the desired interval at which to perform a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly), and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70030-115">Une sauvegarde complète est effectuée à la première exécution du travail de sauvegarde de BizTalk Server lors d'une nouvelle période.</span><span class="sxs-lookup"><span data-stu-id="70030-115">The first time the Backup BizTalk Server job is run during a new period, a full backup is performed.</span></span>  
  
8.  <span data-ttu-id="70030-116">Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)** boîte de dialogue **sélectionner une page**, cliquez sur **planifications**.</span><span class="sxs-lookup"><span data-stu-id="70030-116">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, under **Select a page**, click **Schedules**.</span></span>  
  
9. <span data-ttu-id="70030-117">Dans le **liste planification**, cliquez sur **MarkAndBackupLogSched**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="70030-117">In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.</span></span>  
  
10. <span data-ttu-id="70030-118">Dans le **propriétés de planification du travail - MarkAndBackupLogSched** planification, sélectionnez le type de la boîte de dialogue **périodique** dans la zone de liste déroulante (si elle n’est pas déjà sélectionnée).</span><span class="sxs-lookup"><span data-stu-id="70030-118">In the **Job Schedule Properties - MarkAndBackupLogSched** dialog box, in Schedule type, select **Recurring** from the drop-down list box (if it is not already selected).</span></span>  
  
     <span data-ttu-id="70030-119">Par défaut, l'exécution du travail est planifiée toutes les 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="70030-119">By default, the job is scheduled to run every 15 minutes.</span></span>  
  
11. <span data-ttu-id="70030-120">Mettre à jour la planification comme vous le souhaitez, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70030-120">Update the schedule as desired, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70030-121">Pour plus d’informations sur la planification des travaux de l’Agent SQL Server, consultez «[Scheduling Jobs](http://go.microsoft.com/fwlink/?LinkId=195887). »</span><span class="sxs-lookup"><span data-stu-id="70030-121">For more information about scheduling SQL Server Agent jobs, see "[Scheduling Jobs](http://go.microsoft.com/fwlink/?LinkId=195887)."</span></span>  
  
12. <span data-ttu-id="70030-122">Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="70030-122">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70030-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70030-123">See Also</span></span>  
 <span data-ttu-id="70030-124">[Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="70030-124">[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="70030-125">[Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="70030-125">[How to Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 <span data-ttu-id="70030-126">[Comment faire pour restaurer vos bases de données](../core/how-to-restore-your-databases.md) </span><span class="sxs-lookup"><span data-stu-id="70030-126">[How to Restore Your Databases](../core/how-to-restore-your-databases.md) </span></span>  
 [<span data-ttu-id="70030-127">Informations avancées sur la sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="70030-127">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)