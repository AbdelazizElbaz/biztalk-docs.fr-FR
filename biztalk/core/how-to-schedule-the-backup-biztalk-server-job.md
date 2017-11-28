---
title: Planifier le travail de sauvegarde de BizTalk Server | Documents Microsoft
description: "Configurez les paramètres de la tâche de sauvegarde de BizTalk Server, définissez une planification de l’exécution mensuelle, hebdomadaire, quotidienne ou toutes les heures"
ms.custom: 
ms.date: 11/02/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f09ca97f65605ac3bf427d1c1fcc322a14feb53
ms.sourcegitcommit: 9aaed443492b74729171fef79c634bff561af929
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2017
---
# <a name="schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="64946-103">Planifier le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="64946-103">Schedule the Backup BizTalk Server Job</span></span>
<span data-ttu-id="64946-104">Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté selon la planification du service SQL Server Agent.</span><span class="sxs-lookup"><span data-stu-id="64946-104">The Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job runs as scheduled by the SQL Server Agent service.</span></span> <span data-ttu-id="64946-105">Si vous souhaitez varier la fréquence des sauvegardes, vous pouvez modifier la planification du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="64946-105">If you want to create more frequent or less frequent backups, you can change the schedule of the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job by using SQL Server Management Studio.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="64946-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="64946-106">Prerequisites</span></span>  
<span data-ttu-id="64946-107">Connectez-vous avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="64946-107">Sign in with an account that is a member of the SQL Server sysadmin fixed server role.</span></span>  
  
## <a name="schedule-the-backup-biztalk-server-job"></a><span data-ttu-id="64946-108">Planifier le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="64946-108">Schedule the Backup BizTalk Server job</span></span>
  
1.  <span data-ttu-id="64946-109">Sur le serveur SQL qui héberge la base de données de gestion BizTalk, ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="64946-109">On the SQL Server that hosts the BizTalk Management database, open **SQL Server Management Studio**.</span></span>

2.  <span data-ttu-id="64946-110">Dans **se connecter au serveur**, entrez le nom du serveur SQL sur lequel le serveur BizTalk Server résident des bases de données, sélectionnez le type d’authentification, puis **connexion**.</span><span class="sxs-lookup"><span data-stu-id="64946-110">In **Connect to Server**, enter the name of the SQL Server where the BizTalk Server databases reside, select the authentication type, and then **Connect**.</span></span>  
  
3.  <span data-ttu-id="64946-111">Dans l’Explorateur d’objets, double-cliquez sur **l’Agent SQL Server**, puis sélectionnez **travaux**.</span><span class="sxs-lookup"><span data-stu-id="64946-111">In the Object Explorer, double-click **SQL Server Agent**, and then select **Jobs**.</span></span>  
  
4.  <span data-ttu-id="64946-112">Dans le volet détails, cliquez sur **sauvegarde de BizTalk Server (BizTalkMgmtDb)**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="64946-112">In the details pane, right-click **Backup BizTalk Server (BizTalkMgmtDb)**, and then select **Properties**.</span></span>  
  
5.  <span data-ttu-id="64946-113">Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)**, sous **sélectionner une page**, sélectionnez **étapes**.</span><span class="sxs-lookup"><span data-stu-id="64946-113">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="64946-114">Dans le **liste des étapes du travail**, sélectionnez **BackupFull**, puis sélectionnez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="64946-114">In the **Job step list**, select **BackupFull**, and then select **Edit**.</span></span>  
  
7.  <span data-ttu-id="64946-115">Dans le **propriétés étape du travail - BackupFull**, dans le **commande** zone, de mise à jour de la commande en changeant la fréquence pour exécuter une sauvegarde complète : **'h'** (horaire), **avait '**  (quotidienne), **« w »** (hebdomadaire), **suis '** (mensuelle), **'y'** (annuelle).</span><span class="sxs-lookup"><span data-stu-id="64946-115">In the **Job Step Properties - BackupFull**, in the **Command** box, update the command by changing the frequency to run a full backup: **'h'** (hourly), **'d'** (daily), **'w'** (weekly), **'m'** (monthly), **'y'** (yearly).</span></span> <span data-ttu-id="64946-116">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="64946-116">Select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64946-117">La première fois que le travail de sauvegarde de BizTalk Server s’exécute, il réalise une sauvegarde complète.</span><span class="sxs-lookup"><span data-stu-id="64946-117">The first time the Backup BizTalk Server job runs, it completes a full backup.</span></span>  
    
8.  <span data-ttu-id="64946-118">Configurer d’autres  **@frequency**  paramètres :</span><span class="sxs-lookup"><span data-stu-id="64946-118">Configure additional **@frequency** parameters:</span></span>  
  
    - <span data-ttu-id="64946-119">**@ForceFullBackupAfterPartialSetFailure**: La valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="64946-119">**@ForceFullBackupAfterPartialSetFailure**: The default value is **false**.</span></span> <span data-ttu-id="64946-120">Lorsque **false**, si la sauvegarde complète échoue, le système attend que le prochain cycle jusqu'à ce que la sauvegarde complète est effectuée.</span><span class="sxs-lookup"><span data-stu-id="64946-120">When **false**, if the full backup fails, the system waits for the next cycle until the full backup is made.</span></span>  
    
        > [!NOTE]
        >  <span data-ttu-id="64946-121">Si votre  **@frequency**  paramètre est long (par exemple, hebdomadaire, mensuelle, annuelle), puis à ce paramètre **false** peut être dangereuse.</span><span class="sxs-lookup"><span data-stu-id="64946-121">If your **@frequency** setting is long (like weekly, monthly, yearly), then setting this parameter to **false** could be dangerous.</span></span> <span data-ttu-id="64946-122">Dans ce scénario, il peut être préférable de définir cet indicateur **true**.</span><span class="sxs-lookup"><span data-stu-id="64946-122">In this scenario, it may be best to set this flag to **true**.</span></span> <span data-ttu-id="64946-123">Lorsque **true**, chaque fois une défaillance, le système force lui-même pour créer une sauvegarde complète.</span><span class="sxs-lookup"><span data-stu-id="64946-123">When **true**, every time there is a failure, the system forces itself to create a full backup.</span></span> <span data-ttu-id="64946-124">Il peut y avoir un impact sur les performances, mais il est safter d’un système récupérable.</span><span class="sxs-lookup"><span data-stu-id="64946-124">There may be a small performance impact, but it’s safter to have a recoverable system.</span></span>
  
    - <span data-ttu-id="64946-125">**@BackupHour**: La valeur par défaut NULL.</span><span class="sxs-lookup"><span data-stu-id="64946-125">**@BackupHour**: The default valueis NULL.</span></span> <span data-ttu-id="64946-126">Ce paramètre est directement lié à  **@Frequency** .</span><span class="sxs-lookup"><span data-stu-id="64946-126">This parameter is directly related to **@Frequency**.</span></span> <span data-ttu-id="64946-127">Lorsque vous définissez la fréquence **h** (horaire), vous définissez les heures du jour que vous souhaitez que la sauvegarde complète à exécuter.</span><span class="sxs-lookup"><span data-stu-id="64946-127">When you set the frequency to **h** (hourly), you set which hour of the day you want the full backup to run.</span></span> <span data-ttu-id="64946-128">Vous pouvez choisir une valeur comprise entre 0 (minuit) et 23 (11 PM).</span><span class="sxs-lookup"><span data-stu-id="64946-128">You can choose a value between 0 (midnight) to 23 (11 PM).</span></span> <span data-ttu-id="64946-129">Si ce champ est vide, la sauvegarde complète s’exécute toutes les heures.</span><span class="sxs-lookup"><span data-stu-id="64946-129">If left blank, the full backup runs every hour.</span></span>  
    
       > [!NOTE]
        >  <span data-ttu-id="64946-130">Si vous définissez ce paramètre avec une valeur en dehors de la plage comprise entre 0 et 23 (par exemple, 100 ou -1), le système force ce dernier à 0.</span><span class="sxs-lookup"><span data-stu-id="64946-130">If you set this parameter with a number outside the 0 to 23 range (for example, 100 or -1), the system forces it to 0.</span></span>
  
    - <span data-ttu-id="64946-131">**@UseLocalTime**: Un paramètre supplémentaire qui stipule pour utiliser l’heure locale.</span><span class="sxs-lookup"><span data-stu-id="64946-131">**@UseLocalTime**: An extra parameter that states to use local time.</span></span> <span data-ttu-id="64946-132">Par défaut, la tâche fonctionne avec l’heure UTC.</span><span class="sxs-lookup"><span data-stu-id="64946-132">By default, the job works with UTC time.</span></span> <span data-ttu-id="64946-133">Par conséquent, si vous résidez en Australie (qui est UTC + 10 heures), votre sauvegarde s’exécute au lieu de 10 à minuit.</span><span class="sxs-lookup"><span data-stu-id="64946-133">So if you live in Australia (which is UTC + 10 hours), your backup runs at 10am rather than midnight.</span></span> <span data-ttu-id="64946-134">Comme meilleure pratique, il est recommandé d’affecter à ce **1** (true).</span><span class="sxs-lookup"><span data-stu-id="64946-134">As a best practice, it is recommended to set this to **1** (true).</span></span>  
  
9.  <span data-ttu-id="64946-135">Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)**, sous **sélectionner une page**, cliquez sur **planifications**.</span><span class="sxs-lookup"><span data-stu-id="64946-135">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, under **Select a page**, click **Schedules**.</span></span>  
  
10. <span data-ttu-id="64946-136">Dans le **liste planification**, cliquez sur **MarkAndBackupLogSched**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="64946-136">In the **Schedule list**, click **MarkAndBackupLogSched**, and then click **Edit**.</span></span>  
  
11. <span data-ttu-id="64946-137">Dans le **propriétés de planification du travail - MarkAndBackupLogSched**, type de planification, sélectionnez **périodique** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="64946-137">In the **Job Schedule Properties - MarkAndBackupLogSched**, in Schedule type, select **Recurring** from the drop-down list.</span></span>  
  
     <span data-ttu-id="64946-138">Par défaut, l'exécution du travail est planifiée toutes les 15 minutes.</span><span class="sxs-lookup"><span data-stu-id="64946-138">By default, the job is scheduled to run every 15 minutes.</span></span>  
     
    > [!NOTE]
    >  <span data-ttu-id="64946-139">Vous pouvez modifier cette valeur en fonction de vos exigences, mais le premier test dans un environnement hors production.</span><span class="sxs-lookup"><span data-stu-id="64946-139">You can change this value according to your requirements, but first test in non-production environment.</span></span> <span data-ttu-id="64946-140">La valeur des résultats trop faibles dans des sauvegardes fréquentes et l’ajoute à la charge de l’arrière-plan de votre environnement SQL.</span><span class="sxs-lookup"><span data-stu-id="64946-140">Setting this value too low results in frequent backups, and adds to the background load in your SQL environment.</span></span> <span data-ttu-id="64946-141">Une valeur trop élevée peut augmenter la taille des journaux de transactions et affecter les performances.</span><span class="sxs-lookup"><span data-stu-id="64946-141">Setting this value too high may increase the size of transaction logs, and impact performance.</span></span> <span data-ttu-id="64946-142">Dans certaines situations, il est recommandé de laisser la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="64946-142">In some situations, it is recommended to leave the default value.</span></span>    
  
12. <span data-ttu-id="64946-143">Mettre à jour la planification si vous le souhaitez, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="64946-143">Update the schedule if desired, and then select **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="64946-144">[Planification de travaux](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job) fournit plus de détails.</span><span class="sxs-lookup"><span data-stu-id="64946-144">[Scheduling Jobs](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job) provides more details.</span></span>
  
13. <span data-ttu-id="64946-145">Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)**, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="64946-145">In the **Job Properties - Backup BizTalk Server (BizTalkMgmtDb)**, click **OK**.</span></span>  
  
## <a name="more-good-stuff"></a><span data-ttu-id="64946-146">Autre contenu intéressant</span><span class="sxs-lookup"><span data-stu-id="64946-146">More good stuff</span></span>  
 <span data-ttu-id="64946-147">[Configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="64946-147">[Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="64946-148">[Configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span><span class="sxs-lookup"><span data-stu-id="64946-148">[Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) </span></span>  
 <span data-ttu-id="64946-149">[Restaurer vos bases de données](../core/how-to-restore-your-databases.md) </span><span class="sxs-lookup"><span data-stu-id="64946-149">[Restore Your Databases](../core/how-to-restore-your-databases.md) </span></span>  
 [<span data-ttu-id="64946-150">Informations avancées sur la sauvegarde et la restauration</span><span class="sxs-lookup"><span data-stu-id="64946-150">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)
