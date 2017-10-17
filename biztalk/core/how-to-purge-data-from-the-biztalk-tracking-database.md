---
title: "Purger les données de la base de données de suivi de BizTalk | Documents Microsoft"
description: "Configurer la procédure stockée dtasp_PurgeTrackingDatabase pour purger la base de données de suivi (BizTalkDTADB) dans BizTalk Server"
ms.custom: 
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06217a7d5012eb402698ad35e76ccfc886952f6e
ms.sourcegitcommit: 5e6ef63416e8885a5ee91bd65618a842b3a0cc54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2017
---
# <a name="purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="2ca73-103">Purge des données de base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="2ca73-103">Purge Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="2ca73-104">Lors de la purge des données de la base de données des suivis BizTalk (BizTalkDTADb), le travail de purge et d'archivage DTA implique l'élimination de divers types d'informations de suivi de cette base de données, comme les données de suivi du moteur de règles, les données relatives aux instances de service et de message ou relatives aux événements d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="2ca73-104">When you purge data from the BizTalk Tracking (BizTalkDTADb) database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ca73-105">Cette procédure ne permet pas d'archiver la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="2ca73-105">The BizTalk Tracking (BizTalkDTADb) database is not archived using this procedure.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="2ca73-106">Si une exception est interceptée et traitée dans une orchestration alors que le suivi n'est pas activé, une instance de suivi orpheline dotée d'un état Démarré et d'informations sur l'exception peut être insérée dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="2ca73-106">If an exception is caught and handled in an orchestration without tracking turned on, an orphaned tracking instance with a Started state and exception information may be inserted into the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="2ca73-107">Cet enregistrement demeure après la purge de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2ca73-107">This record will remain after purging the database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2ca73-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2ca73-108">Prerequisites</span></span>  
<span data-ttu-id="2ca73-109">Connectez-vous avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="2ca73-109">Sign in with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
## <a name="purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="2ca73-110">Purge des données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="2ca73-110">Purge data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="2ca73-111">Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-111">On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.</span></span> 
  
2.  <span data-ttu-id="2ca73-112">Dans **se connecter au serveur**, entrez le nom du serveur SQL server où le suivi BizTalk (BizTalkDTADb) de base de données réside, entrez le type d’authentification, puis sélectionnez **connexion** pour se connecter à SQL server.</span><span class="sxs-lookup"><span data-stu-id="2ca73-112">In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.</span></span> 
  
3.  <span data-ttu-id="2ca73-113">Double-cliquez sur **l’Agent SQL Server**, puis sélectionnez **travaux**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-113">Double-click **SQL Server Agent**, and then select **Jobs**.</span></span>  
  
4.  <span data-ttu-id="2ca73-114">Dans **détails de l’Explorateur d’objets**, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-114">In **Object Explorer Details**, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then select **Properties**.</span></span>  
  
5.  <span data-ttu-id="2ca73-115">Dans **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)**, sous **sélectionner une page**, sélectionnez **étapes**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-115">In **Job Properties - DTA Purge and Archive (BizTalkDTADb)**, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="2ca73-116">Dans **liste des étapes du travail**, sélectionnez **archiver et purger**, puis sélectionnez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-116">In **Job step list**, select **Archive and Purge**, and then select **Edit**.</span></span>  
  
7.  <span data-ttu-id="2ca73-117">Dans **propriétés étape du travail - Archive and Purge**, dans le **général** page, dans le **commande** , changez **exec dtasp_BackupAndPurgeTrackingDatabase** à **exec dtasp_PurgeTrackingDatabase**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-117">In **Job Step Properties - Archive and Purge**, on the **General** page, in the **Command** box, change **exec dtasp_BackupAndPurgeTrackingDatabase** to **exec dtasp_PurgeTrackingDatabase**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="2ca73-118">Le **exec dtasp_PurgeTrackingDatabase** procédure stockée n’archive pas la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="2ca73-118">The **exec dtasp_PurgeTrackingDatabase** stored procedure does not archive the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="2ca73-119">N'ayez recours à cette option que si vous êtes sûr de ne plus avoir besoin des données de suivi archivées.</span><span class="sxs-lookup"><span data-stu-id="2ca73-119">Before using this option, be certain that you no longer require archived tracking data.</span></span>  
  
8.  <span data-ttu-id="2ca73-120">Dans le **commande** zone, mettre à jour les paramètres suivants, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-120">In the **Command** box, update the following parameters, and then select **OK**.</span></span>  
  
    -   <span data-ttu-id="2ca73-121">@nHourstinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="2ca73-121">@nHours tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.</span></span>  
  
    -   <span data-ttu-id="2ca73-122">@nDaystinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="2ca73-122">@nDays tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="2ca73-123">Le délai par défaut est de 1 jour.</span><span class="sxs-lookup"><span data-stu-id="2ca73-123">Default interval is 1 day.</span></span>  
  
    -   <span data-ttu-id="2ca73-124">@nHardDaystinyint : toutes les données antérieures à cette date seront supprimées, même si les données sont incomplètes.</span><span class="sxs-lookup"><span data-stu-id="2ca73-124">@nHardDays tinyint — All data older than this day will be deleted, even if the data is incomplete.</span></span> <span data-ttu-id="2ca73-125">L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="2ca73-125">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="2ca73-126">Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="2ca73-126">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="2ca73-127">Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.</span><span class="sxs-lookup"><span data-stu-id="2ca73-127">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span>  
  
    -   <span data-ttu-id="2ca73-128">@dtLastBackup: Affectez la valeur **GetUTCDate()** pour purger les données à partir de la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="2ca73-128">@dtLastBackup — Set this to **GetUTCDate()** to purge data from the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="2ca73-129">Lorsque la valeur **NULL**, données ne sont pas purgées à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="2ca73-129">When set to **NULL**, data is not purged from the database.</span></span>  

    -  <span data-ttu-id="2ca73-130">@fHardDeleteRunningInstancesint - valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="2ca73-130">@fHardDeleteRunningInstances int - Default is 0.</span></span> <span data-ttu-id="2ca73-131">Lorsque cette propriété a la valeur 1, il supprime toutes les exécutant des instances de service antérieures à la @nHardDeleteDays valeur.</span><span class="sxs-lookup"><span data-stu-id="2ca73-131">When set to 1, it deletes all running service instances older than the @nHardDeleteDays value.</span></span>  
    
        > [!NOTE] 
        > <span data-ttu-id="2ca73-132">Le @fHardDeleteRunningInstances propriété est disponible à partir de [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), et [cumulés de BizTalk Server 2013 Mettre à jour 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).</span><span class="sxs-lookup"><span data-stu-id="2ca73-132">The @fHardDeleteRunningInstances property is available starting with [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), and [BizTalk Server 2013 Cumulative Update 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).</span></span>   

    <span data-ttu-id="2ca73-133">Le script modifié ressemble à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="2ca73-133">Your edited script looks similar to the following:</span></span>  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup, 1  
    ```  
    
9. <span data-ttu-id="2ca73-134">Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, sélectionnez **général**, sélectionnez le **activé**case à cocher, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="2ca73-134">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, select **General**, select the **Enabled** check box, and then select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ca73-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ca73-135">See Also</span></span>  
 [<span data-ttu-id="2ca73-136">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="2ca73-136">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)
