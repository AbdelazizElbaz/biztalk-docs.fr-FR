---
title: "Purge des données de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging
- DTA Purge and Archive job, purging data
- purging, DTA Purge and Archive job
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01c56629aaa0934010ba79637b4e4a134bf29f26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="37e64-102">Purge des données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="37e64-102">How to Purge Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="37e64-103">Lors de la purge des données de la base de données des suivis BizTalk (BizTalkDTADb), le travail de purge et d'archivage DTA implique l'élimination de divers types d'informations de suivi de cette base de données, comme les données de suivi du moteur de règles, les données relatives aux instances de service et de message ou relatives aux événements d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="37e64-103">When you purge data from the BizTalk Tracking (BizTalkDTADb) database, the DTA Purge and Archive job purges different types of tracking information such as message and service instance information, orchestration event information, and rules engine tracking data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37e64-104">Cette procédure ne permet pas d'archiver la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="37e64-104">The BizTalk Tracking (BizTalkDTADb) database is not archived using this procedure.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="37e64-105">Si une exception est interceptée et traitée dans une orchestration alors que le suivi n'est pas activé, une instance de suivi orpheline dotée d'un état Démarré et d'informations sur l'exception peut être insérée dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="37e64-105">If an exception is caught and handled in an orchestration without tracking turned on, an orphaned tracking instance with a Started state and exception information may be inserted into the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="37e64-106">Cet enregistrement demeure après la purge de la base de données.</span><span class="sxs-lookup"><span data-stu-id="37e64-106">This record will remain after purging the database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="37e64-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="37e64-107">Prerequisites</span></span>  
 <span data-ttu-id="37e64-108">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="37e64-108">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="37e64-109">Pour purger les données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="37e64-109">To purge data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="37e64-110">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="37e64-110">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="37e64-111">Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="37e64-111">In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the SQL Server.</span></span>  
  
3.  <span data-ttu-id="37e64-112">Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.</span><span class="sxs-lookup"><span data-stu-id="37e64-112">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="37e64-113">Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="37e64-113">In the **Object Explorer Details** pane, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="37e64-114">Dans le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.</span><span class="sxs-lookup"><span data-stu-id="37e64-114">In the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="37e64-115">Dans le **liste des étapes du travail**, cliquez sur **archiver et purger**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="37e64-115">In the **Job step list**, click **Archive and Purge**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="37e64-116">Dans le **propriétés étape du travail - Archive and Purge** boîte de dialogue le **général** page, dans le **commande** , changez **exec dtasp_ BackupAndPurgeTrackingDatabase** à **exec dtasp_PurgeTrackingDatabase**.</span><span class="sxs-lookup"><span data-stu-id="37e64-116">In the **Job Step Properties - Archive and Purge** dialog box, on the **General** page, in the **Command** box, change **exec dtasp_BackupAndPurgeTrackingDatabase** to **exec dtasp_PurgeTrackingDatabase**.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="37e64-117">Le **exec dtasp_PurgeTrackingDatabase** procédure stockée n’archive pas la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="37e64-117">The **exec dtasp_PurgeTrackingDatabase** stored procedure does not archive the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="37e64-118">N'ayez recours à cette option que si vous êtes sûr de ne plus avoir besoin des données de suivi archivées.</span><span class="sxs-lookup"><span data-stu-id="37e64-118">Before using this option, be certain that you no longer require archived tracking data.</span></span>  
  
8.  <span data-ttu-id="37e64-119">Dans le **commande** zone, modifiez les paramètres ci-dessous comme il convient, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="37e64-119">In the **Command** box, edit the following parameters as appropriate, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="37e64-120">@nHourstinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="37e64-120">@nHours tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.</span></span>  
  
    -   <span data-ttu-id="37e64-121">@nDaystinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="37e64-121">@nDays tinyint — Any completed instance older than (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="37e64-122">Le délai par défaut est de 1 jour.</span><span class="sxs-lookup"><span data-stu-id="37e64-122">Default interval is 1 day.</span></span>  
  
    -   <span data-ttu-id="37e64-123">@nHardDaystinyint : toutes les données antérieures à cette date seront supprimées, même si les données sont incomplètes.</span><span class="sxs-lookup"><span data-stu-id="37e64-123">@nHardDays tinyint — All data older than this day will be deleted, even if the data is incomplete.</span></span> <span data-ttu-id="37e64-124">L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="37e64-124">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="37e64-125">Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="37e64-125">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="37e64-126">Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.</span><span class="sxs-lookup"><span data-stu-id="37e64-126">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span>  
  
    -   <span data-ttu-id="37e64-127">@dtLastBackup: Affectez la valeur **GetUTCDate()** pour purger les données à partir de la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="37e64-127">@dtLastBackup — Set this to **GetUTCDate()** to purge data from the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="37e64-128">Lorsque la valeur **NULL**, données ne sont pas purgées à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="37e64-128">When set to **NULL**, data is not purged from the database.</span></span>  
  
     <span data-ttu-id="37e64-129">Le script modifié doit être similaire à ceci :</span><span class="sxs-lookup"><span data-stu-id="37e64-129">Your edited script should look similar to this:</span></span>  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup  
    ```  
  
9. <span data-ttu-id="37e64-130">Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **général**, sélectionnez le **activé**case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="37e64-130">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **General**, select the **Enabled** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e64-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37e64-131">See Also</span></span>  
 [<span data-ttu-id="37e64-132">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="37e64-132">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)