---
title: Comment faire pour configurer la DTA Purge et archivage du projet | Documents Microsoft
ms.custom: 
ms.date: 2015-11-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- purging, configuring
- DTA Purge and Archive job, configuring
- archiving [Tracking database], DTA Purge and Archive job
- archiving [Tracking database], configuring
- purging, DTA Purge and Archive job
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f4985e657f26945aa2fdc168b273dbfdb159efc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="f9144-102">Configuration du travail de purge et d'archivage DTA</span><span class="sxs-lookup"><span data-stu-id="f9144-102">How to Configure the DTA Purge and Archive Job</span></span>
<span data-ttu-id="f9144-103">Avant d'archiver ou de purger des données de la base de données des suivis BizTalk (BizTalkDTADb), vous devez configurer le travail de purge et d'archivage DTA (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="f9144-103">Before you can archive or purge data from the BizTalk Tracking (BizTalkDTADb) database, you must configure the DTA Purge and Archive (BizTalkDTADb) job.</span></span> <span data-ttu-id="f9144-104">Cette tâche est configurée pour appeler la procédure stockée dtasp_BackupAndPurgeTrackingDatabase, qui utilise les six paramètres que vous devez configurer.</span><span class="sxs-lookup"><span data-stu-id="f9144-104">This job is configured to call the dtasp_BackupAndPurgeTrackingDatabase store procedure, which uses six parameters you must configure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f9144-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f9144-105">Prerequisites</span></span>  
 <span data-ttu-id="f9144-106">Vous devez être connecté avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server comme suit.</span><span class="sxs-lookup"><span data-stu-id="f9144-106">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to follow these steps.</span></span>  
  
### <a name="to-configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="f9144-107">Pour configurer le travail de purge et d'archivage DTA</span><span class="sxs-lookup"><span data-stu-id="f9144-107">To configure the DTA purge and archive job</span></span>  
  
1.  <span data-ttu-id="f9144-108">Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="f9144-108">On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="f9144-109">Dans **se connecter au serveur**, entrez le nom du serveur SQL server où le suivi BizTalk (BizTalkDTADb) de base de données réside, entrez le type d’authentification, puis sélectionnez **connexion** pour se connecter à SQL server.</span><span class="sxs-lookup"><span data-stu-id="f9144-109">In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.</span></span>  
  
3.  <span data-ttu-id="f9144-110">Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.</span><span class="sxs-lookup"><span data-stu-id="f9144-110">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
4.  <span data-ttu-id="f9144-111">Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f9144-111">In the **Object Explorer Details** pane, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f9144-112">Dans le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.</span><span class="sxs-lookup"><span data-stu-id="f9144-112">In the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
6.  <span data-ttu-id="f9144-113">Dans le **liste des étapes du travail**, cliquez sur **archiver et purger**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="f9144-113">In the **Job step list**, click **Archive and Purge**, and then click **Edit**.</span></span>  
  
7.  <span data-ttu-id="f9144-114">Sur le **général** page, dans le **commande** zone, modifiez les paramètres ci-dessous comme il convient, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9144-114">On the **General** page, in the **Command** box, edit the following parameters as appropriate, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="f9144-115">@nLiveHourstinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="f9144-115">@nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="f9144-116">Il s’agit d’un paramètre obligatoire sans valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9144-116">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="f9144-117">@nLiveDaystinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="f9144-117">@nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="f9144-118">Intervalle par défaut est 0 jour.</span><span class="sxs-lookup"><span data-stu-id="f9144-118">Default interval is 0 days.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f9144-119">Pour les besoins de la base de données des suivis BizTalk (BizTalkDTADb), la somme du nombre d'heures et du nombre de jours d'activité est égale aux données de la fenêtre active que vous souhaitez conserver dans votre environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f9144-119">For the purposes of the BizTalk Tracking (BizTalkDTADb) database, the sum of LiveHours plus LiveDays is the live window of data you want to maintain in your BizTalk Server environment.</span></span> <span data-ttu-id="f9144-120">Les données associées à une instance achevée et antérieures aux données de la fenêtre active sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="f9144-120">All data associated with a completed instance older than the live window of data is deleted.</span></span>  
  
    -   <span data-ttu-id="f9144-121">@nHardDeleteDaystinyint : toutes les données (même si elle est incomplète) antérieurs à cela sera supprimé.</span><span class="sxs-lookup"><span data-stu-id="f9144-121">@nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted.</span></span> <span data-ttu-id="f9144-122">L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="f9144-122">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="f9144-123">Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="f9144-123">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="f9144-124">Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.</span><span class="sxs-lookup"><span data-stu-id="f9144-124">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span> <span data-ttu-id="f9144-125">Valeur par défaut est 0 jour.</span><span class="sxs-lookup"><span data-stu-id="f9144-125">Default is 0 days.</span></span>  
  
    -   <span data-ttu-id="f9144-126">@nvcFoldernvarchar (1024) : dossier dans lequel placer les fichiers de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="f9144-126">@nvcFolder nvarchar(1024) — Folder in which to put the backup files.</span></span> <span data-ttu-id="f9144-127">Il s’agit d’un paramètre obligatoire sans valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f9144-127">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="f9144-128">@nvcValidatingServersysname : serveur sur lequel la validation est exécutée.</span><span class="sxs-lookup"><span data-stu-id="f9144-128">@nvcValidatingServer sysname — Server on which validation will be done.</span></span> <span data-ttu-id="f9144-129">La valeur NULL indique qu'aucune validation n'est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="f9144-129">NULL value indicates no validation is being done.</span></span> <span data-ttu-id="f9144-130">La valeur par défaut est NULL.</span><span class="sxs-lookup"><span data-stu-id="f9144-130">Default is NULL.</span></span>  
  
    -   <span data-ttu-id="f9144-131">@fForceBackupint, valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="f9144-131">@fForceBackup int — Default is 0.</span></span> <span data-ttu-id="f9144-132">Elle est réservée à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="f9144-132">This is reserved for future use.</span></span>  
  
     <span data-ttu-id="f9144-133">La commande modifiée doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="f9144-133">The edited command should look similar to the following.</span></span> <span data-ttu-id="f9144-134">Dans l’exemple suivant, il est de 1 heure, une fenêtre active et de purge de 1 jour :</span><span class="sxs-lookup"><span data-stu-id="f9144-134">In the following example, there is a live window of 1 hour and a hard purge of 1 day:</span></span>  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0  
    ```  
  
8.  <span data-ttu-id="f9144-135">Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **général**, sélectionnez le **activé**case à cocher, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f9144-135">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, click **General**, select the **Enabled** check box, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9144-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9144-136">See Also</span></span>  
 [<span data-ttu-id="f9144-137">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="f9144-137">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)