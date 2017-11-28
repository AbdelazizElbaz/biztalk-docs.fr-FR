---
title: Configurer la Purge DTA et archiver le travail | Documents Microsoft
description: "Définir les paramètres du travail DTA Purge and Archive dans SQL Server Agent pour maintenir la base de données de suivi dans BizTalk Server"
ms.custom: 
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 149719b7eea50ce53c14298597c94729162d43b0
ms.sourcegitcommit: 1fb633fcf919ce3124405420a5d9faa79d9d508e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="f4fa7-103">Configurer la Purge DTA et les travaux d’archivage</span><span class="sxs-lookup"><span data-stu-id="f4fa7-103">Configure the DTA Purge and Archive Job</span></span>
<span data-ttu-id="f4fa7-104">Avant d'archiver ou de purger des données de la base de données des suivis BizTalk (BizTalkDTADb), vous devez configurer le travail de purge et d'archivage DTA (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="f4fa7-104">Before you can archive or purge data from the BizTalk Tracking (BizTalkDTADb) database, you must configure the DTA Purge and Archive (BizTalkDTADb) job.</span></span> <span data-ttu-id="f4fa7-105">Cette tâche est configurée pour appeler la procédure stockée dtasp_BackupAndPurgeTrackingDatabase, qui utilise les six paramètres que vous devez configurer.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-105">This job is configured to call the dtasp_BackupAndPurgeTrackingDatabase store procedure, which uses six parameters you must configure.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f4fa7-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f4fa7-106">Prerequisites</span></span>  
 <span data-ttu-id="f4fa7-107">Connectez-vous avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-107">Sign in with an account that is a member of the SQL Server sysadmin fixed server role.</span></span>  
  
## <a name="configure-the-dta-purge-and-archive-job"></a><span data-ttu-id="f4fa7-108">Configurer la purge DTA et les travaux d’archivage</span><span class="sxs-lookup"><span data-stu-id="f4fa7-108">Configure the DTA purge and archive job</span></span>  
  
1.  <span data-ttu-id="f4fa7-109">Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), ouvrez **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-109">On the SQL Server that hosts the BizTalk Tracking (BizTalkDTADb) database, open **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="f4fa7-110">Dans **se connecter au serveur**, entrez le nom du serveur SQL server où le suivi BizTalk (BizTalkDTADb) de base de données réside, entrez le type d’authentification, puis sélectionnez **connexion** pour se connecter à SQL server.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-110">In **Connect to Server**, enter the name of the SQL server where the BizTalk Tracking (BizTalkDTADb) database resides, enter the authentication type, and then select **Connect** to connect to the SQL server.</span></span>  
  
3. <span data-ttu-id="f4fa7-111">Double-cliquez sur **l’Agent SQL Server**, puis sélectionnez **travaux**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-111">Double-click **SQL Server Agent**, and then select **Jobs**.</span></span>  
  
4.  <span data-ttu-id="f4fa7-112">Dans **détails de l’Explorateur d’objets**, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-112">In **Object Explorer Details**, right-click **DTA Purge and Archive (BizTalkDTADb)**, and then select **Properties**.</span></span>  
  
5.  <span data-ttu-id="f4fa7-113">Dans **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)**, sous **sélectionner une page**, sélectionnez **étapes**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-113">In **Job Properties - DTA Purge and Archive (BizTalkDTADb)**, under **Select a page**, select **Steps**.</span></span>  
  
6.  <span data-ttu-id="f4fa7-114">Dans le **liste des étapes du travail**, sélectionnez **archiver et purger**, puis sélectionnez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-114">In the **Job step list**, select **Archive and Purge**, and then select **Edit**.</span></span>  
  
7.  <span data-ttu-id="f4fa7-115">Dans **général**, dans le **commande** zone, mettre à jour les paramètres suivants, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-115">In **General**, in the **Command** box, update the following parameters, and then select **OK**.</span></span>  
  
    -   <span data-ttu-id="f4fa7-116">@nLiveHourstinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-116">@nLiveHours tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="f4fa7-117">Il s’agit d’un paramètre obligatoire sans valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-117">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="f4fa7-118">@nLiveDaystinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-118">@nLiveDays tinyint — Any completed instance older than the (live hours) + (live days) will be deleted along with all associated data.</span></span> <span data-ttu-id="f4fa7-119">Intervalle par défaut est 0 jour.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-119">Default interval is 0 days.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f4fa7-120">Pour les besoins de la base de données des suivis BizTalk (BizTalkDTADb), la somme du nombre d'heures et du nombre de jours d'activité est égale aux données de la fenêtre active que vous souhaitez conserver dans votre environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-120">For the purposes of the BizTalk Tracking (BizTalkDTADb) database, the sum of LiveHours plus LiveDays is the live window of data you want to maintain in your BizTalk Server environment.</span></span> <span data-ttu-id="f4fa7-121">Les données associées à une instance achevée et antérieures aux données de la fenêtre active sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-121">All data associated with a completed instance older than the live window of data is deleted.</span></span>  
  
    -   <span data-ttu-id="f4fa7-122">@nHardDeleteDaystinyint : toutes les données (même si elle est incomplète) antérieurs à cela sera supprimé.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-122">@nHardDeleteDays tinyint — All data (even if incomplete) older than this will be deleted.</span></span> <span data-ttu-id="f4fa7-123">L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-123">The time interval specified for HardDeleteDays should be greater than the live window of data.</span></span> <span data-ttu-id="f4fa7-124">Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="f4fa7-124">The live window of data is the interval of time for which you want to maintain tracking data in the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="f4fa7-125">Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-125">Anything older than this interval is eligible to be archived at the next archive and then purged.</span></span> <span data-ttu-id="f4fa7-126">Valeur par défaut est 0 jour.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-126">Default is 0 days.</span></span>  
  
    -   <span data-ttu-id="f4fa7-127">@nvcFoldernvarchar (1024) : dossier dans lequel placer les fichiers de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-127">@nvcFolder nvarchar(1024) — Folder in which to put the backup files.</span></span> <span data-ttu-id="f4fa7-128">Il s’agit d’un paramètre obligatoire sans valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-128">This is a required parameter with no default value.</span></span>  
  
    -   <span data-ttu-id="f4fa7-129">@nvcValidatingServersysname : serveur sur lequel la validation est exécutée.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-129">@nvcValidatingServer sysname — Server on which validation will be done.</span></span> <span data-ttu-id="f4fa7-130">La valeur NULL indique qu'aucune validation n'est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-130">NULL value indicates no validation is being done.</span></span> <span data-ttu-id="f4fa7-131">La valeur par défaut est NULL.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-131">Default is NULL.</span></span>  
  
    -   <span data-ttu-id="f4fa7-132">@fForceBackupint, valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-132">@fForceBackup int — Default is 0.</span></span> <span data-ttu-id="f4fa7-133">Elle est réservée à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-133">This is reserved for future use.</span></span>  
  
    -   <span data-ttu-id="f4fa7-134">@fHardDeleteRunningInstancesint - valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-134">@fHardDeleteRunningInstances int - Default is 0.</span></span> <span data-ttu-id="f4fa7-135">Lorsque cette propriété a la valeur 1, il supprime toutes les exécutant des instances de service antérieures à la @nHardDeleteDays valeur.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-135">When set to 1, it deletes all running service instances older than the @nHardDeleteDays value.</span></span> 
    
        > [!NOTE]
        > <span data-ttu-id="f4fa7-136">Le @fHardDeleteRunningInstances propriété est disponible à partir de [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), et [cumulés de BizTalk Server 2013 Mettre à jour 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).</span><span class="sxs-lookup"><span data-stu-id="f4fa7-136">The @fHardDeleteRunningInstances property is available starting with [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), and [BizTalk Server 2013 Cumulative Update 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).</span></span>  
  
    <span data-ttu-id="f4fa7-137">Votre commande modifiée doit ressembler à ce qui suit.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-137">Your edited command should look similar to the following.</span></span> <span data-ttu-id="f4fa7-138">Dans l’exemple suivant, il est de 1 heure, une fenêtre active, de purge de 1 jour et suppressions en cours d’exécution plus de 1 jour des instances de service :</span><span class="sxs-lookup"><span data-stu-id="f4fa7-138">In the following example, there is a live window of 1 hour, a hard purge of 1 day, and deletes all running service instances older than 1 day:</span></span>  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0, 1  
    ```  
  
8.  <span data-ttu-id="f4fa7-139">Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, sélectionnez **général**, sélectionnez le **activé**case à cocher, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="f4fa7-139">On the **Job Properties - DTA Purge and Archive (BizTalkDTADb)** dialog box, under **Select a page**, select **General**, select the **Enabled** check box, and then select **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4fa7-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f4fa7-140">See Also</span></span>  
 [<span data-ttu-id="f4fa7-141">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="f4fa7-141">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)
