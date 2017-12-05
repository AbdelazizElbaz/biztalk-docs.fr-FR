---
title: "Comment activer la Validation de l’archivage automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, archives [Tracking database]
- archiving [Tracking database], validating archive
ms.assetid: 406ca54a-6b1f-4bdb-9bad-bea5ea0f6e66
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e654d22a08a7b07210ded9c319953c288065927a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-automatic-archive-validation"></a><span data-ttu-id="08192-102">Activation de la validation automatique de l'archivage</span><span class="sxs-lookup"><span data-stu-id="08192-102">How to Enable Automatic Archive Validation</span></span>
<span data-ttu-id="08192-103">La validation d'archivage permet de valider les archives lors de leur création.</span><span class="sxs-lookup"><span data-stu-id="08192-103">Archive validation enables you to validate the archives as they are created.</span></span> <span data-ttu-id="08192-104">Avant de pouvoir activer la validation d'archivage automatique, vous devez configurer un serveur de base de données secondaire, également appelé « serveur de validation ».</span><span class="sxs-lookup"><span data-stu-id="08192-104">Before you can enable automatic archive validation, you must set up a secondary database server, also called a validation server.</span></span> <span data-ttu-id="08192-105">Le processus d'archivage consistant en une simple sauvegarde, l'image réelle stockée sur le disque peut être altérée suite à une défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="08192-105">Because the archiving process is a simple backup, it is possible that the actual image stored on the disk can be corrupted due to a hardware issue.</span></span>  
  
 <span data-ttu-id="08192-106">La fonction de validation d'archivage vous permet de vous assurer que l'archive (la sauvegarde) a été correctement créée et peut être restaurée.</span><span class="sxs-lookup"><span data-stu-id="08192-106">Using the archive validation feature, you can ensure the archive (backup) was successful and can be restored.</span></span> <span data-ttu-id="08192-107">Chaque nouvelle création d'archive est notifiée au serveur de validation.</span><span class="sxs-lookup"><span data-stu-id="08192-107">After an archive is created, the validation server is notified that a new archive has been created.</span></span> <span data-ttu-id="08192-108">Le serveur de validation tente de restaurer l'archive.</span><span class="sxs-lookup"><span data-stu-id="08192-108">The validation server attempts to restore the archive.</span></span> <span data-ttu-id="08192-109">Le serveur de validation doit être une autre instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], différente de celle dans laquelle le travail s'exécute.</span><span class="sxs-lookup"><span data-stu-id="08192-109">A validation server must be another instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] different from the one in which the job is running.</span></span> <span data-ttu-id="08192-110">La version de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur la validation de serveur doit être la même version que le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] utilisé pour héberger les bases de données.</span><span class="sxs-lookup"><span data-stu-id="08192-110">The version of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] on the validation server must be the same version as the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] used to host the databases.</span></span>  
  
 <span data-ttu-id="08192-111">Si la restauration s'effectue correctement, le serveur de validation communique cette information à la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="08192-111">If the restore is successful, the validation server communicates this information back to the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="08192-112">La purge des données n'a lieu qu'une fois la restauration correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="08192-112">Until a successful restore is completed, the purge job will not purge any more data.</span></span>  
  
 <span data-ttu-id="08192-113">Si la restauration ne s'effectue pas correctement, le serveur de validation communique cette information à la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="08192-113">If the restore is not successful, the validation server communicates this information back to the BizTalk Tracking database.</span></span> <span data-ttu-id="08192-114">Le travail de purge crée une autre archive et attend la validation de la nouvelle archive.</span><span class="sxs-lookup"><span data-stu-id="08192-114">The purge job creates another archive and awaits validation of the new archive.</span></span> <span data-ttu-id="08192-115">Ceci vous évite toute perte de données de suivi due à une archive endommagée.</span><span class="sxs-lookup"><span data-stu-id="08192-115">This prevents the possibility of a corrupted archive causing you to lose tracking data.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="08192-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="08192-116">Prerequisites</span></span>  
 <span data-ttu-id="08192-117">Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08192-117">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-enable-automatic-archive-validation"></a><span data-ttu-id="08192-118">Activation de la validation de l'archivage automatique</span><span class="sxs-lookup"><span data-stu-id="08192-118">To enable automatic archive validation</span></span>  
  
1.  <span data-ttu-id="08192-119">Sur le serveur de validation, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio** .</span><span class="sxs-lookup"><span data-stu-id="08192-119">On the validation server, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="08192-120">Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] où vous pouvez valider l’archive en effectuant un test du processus de restauration, puis cliquez sur **connexion** pour se connecter à la serveur SQL Server approprié.</span><span class="sxs-lookup"><span data-stu-id="08192-120">In the **Connect to Server** dialog box, specify the name of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] where you can validate the archive by performing a test of the restore process, and then click **Connect** to connect to the appropriate SQL Server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="08192-121">Ce serveur ne doit pas être un autre serveur de base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], car cela réduit les performances du système lors de la validation de l'archivage.</span><span class="sxs-lookup"><span data-stu-id="08192-121">This server should not be another [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database server as it reduces system performance when validating the archive.</span></span>  
  
3.  <span data-ttu-id="08192-122">Dans **Microsoft SQL Server Management Studio**, cliquez sur **fichier**, cliquez sur **ouvrir**, puis cliquez sur **fichier**.</span><span class="sxs-lookup"><span data-stu-id="08192-122">In **Microsoft SQL Server Management Studio**, click **File**, click **Open**, and then click **File**.</span></span>  
  
4.  <span data-ttu-id="08192-123">Dans le **ouvrir le fichier** boîte de dialogue, cliquez sur Parcourir pour le script SQL suivant :</span><span class="sxs-lookup"><span data-stu-id="08192-123">In the **Open File** dialog box, browse to the following SQL script:</span></span>  
  
    ```  
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\BTS_Tracking_ValidateArchive.sql  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="08192-124">Vous aurez peut-être besoin de copier le script de l'ordinateur qui exécute [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur le serveur de validation.</span><span class="sxs-lookup"><span data-stu-id="08192-124">You might need to copy the script from the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the validation server.</span></span>  
  
5.  <span data-ttu-id="08192-125">Cliquez sur le **requête** menu, puis sur **Execute**.</span><span class="sxs-lookup"><span data-stu-id="08192-125">Click the **Query** menu, and then click **Execute**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="08192-126">Le script BTS_Tracking_ValidateArchive.sql fonctionne uniquement si le dossier dans lequel vous archivez votre base de données des suivis BizTalk (BizTalkDTADb) est un partage réseau.</span><span class="sxs-lookup"><span data-stu-id="08192-126">The BTS_Tracking_ValidateArchive.sql script only works if the folder where you are archiving your BizTalk Tracking (BizTalkDTADb) database is a network share.</span></span>  
  
     <span data-ttu-id="08192-127">Le script BTS_Tracking_ValidateArchive.sql crée un travail SQL Server Agent nommé ValidateArchive.</span><span class="sxs-lookup"><span data-stu-id="08192-127">The BTS_Tracking_ValidateArchive.sql script creates a SQL Server Agent job called ValidateArchive.</span></span>  
  
6.  <span data-ttu-id="08192-128">Le processus d’archivage et de purge pouvant utiliser ou met à jour des bases de données de différents serveurs SQL Server, vous devez donc définir des serveurs liés entre les instances de SQL Server concernées.</span><span class="sxs-lookup"><span data-stu-id="08192-128">The archiving and purging process potentially accesses and/or updates databases in different SQL Servers, so you must set up linked servers between the involved SQL Server instances.</span></span> <span data-ttu-id="08192-129">Dans **SQL Server Management Studio**, double-cliquez sur **objets serveur**, avec le bouton droit **des serveurs liés**, puis cliquez sur **nouveau serveur lié**.</span><span class="sxs-lookup"><span data-stu-id="08192-129">In **SQL Server Management Studio**, double-click **Server Objects**, right-click **Linked Servers**, and then click **New Linked Server**.</span></span>  
  
     <span data-ttu-id="08192-130">Vous devez configurer un serveur lié entre :</span><span class="sxs-lookup"><span data-stu-id="08192-130">You must set up linked server between:</span></span>  
  
    -   <span data-ttu-id="08192-131">chacune de vos bases de données MessageBox BizTalk (BizTalkMsgBoxDb) et la base de données des suivis BizTalk (BizTalkDTADb) si celles-ci résident sur des serveurs différents ;</span><span class="sxs-lookup"><span data-stu-id="08192-131">Each of your BizTalk MessageBox (BizTalkMsgBoxDb) databases and the BizTalk Tracking (BizTalkDTADb) database if they reside on different servers.</span></span>  
  
    -   <span data-ttu-id="08192-132">la base de données des suivis BizTalk (BizTalkDTADb) et le serveur de validation pour la validation de l'archivage.</span><span class="sxs-lookup"><span data-stu-id="08192-132">The BizTalk Tracking (BizTalkDTADb) database and the validating server for archive validation.</span></span>  
  
    -   <span data-ttu-id="08192-133">Les comptes de service de l'Agent SQL Server sur l'ordinateur qui héberge la base de données MessageBox BizTalk (BizTalkMsgBoxDb) doivent disposer des autorisations db_datareader et db_datawriter pour la base de données des suivis BizTalk (BizTalkDTADb) qui réside sur le serveur lié.</span><span class="sxs-lookup"><span data-stu-id="08192-133">The service accounts for the SQL Server Agent on the computer hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database must have the db_datareader and db_datawriter permissions for the BizTalk Tracking (BizTalkDTADb) database on the linked server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="08192-134">Le compte utilisé pour exécuter le travail doit disposer des privilèges de l'opérateur de base de données (DBO, Database Operator) sur les deux bases de données.</span><span class="sxs-lookup"><span data-stu-id="08192-134">The account used for running the job should have Database Operator (DBO) privileges on both the databases.</span></span>  
  
7.  <span data-ttu-id="08192-135">Dans le **nouveau serveur lié** boîte de dialogue le **général** page **serveur lié**, entrez le nom du serveur que vous voulez lier à.</span><span class="sxs-lookup"><span data-stu-id="08192-135">In the **New Linked Server** dialog box, on the **General** page, in **Linked server**, enter the name of the server you want to link to.</span></span>  
  
     <span data-ttu-id="08192-136">Il peut s'agir, par exemple, du serveur hébergeant la base de données MessageBox BizTalk (BizTalkMsgBoxDb), la base de données des suivis BizTalk (BizTalkDTADb) ou le serveur de validation.</span><span class="sxs-lookup"><span data-stu-id="08192-136">For example, the server hosting the BizTalk MessageBox (BizTalkMsgBoxDb) database, BizTalk Tracking (BizTalkDTADb) database, or the validation server.</span></span>  
  
8.  <span data-ttu-id="08192-137">Sous **type de serveur**, cliquez sur **SQL Server**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="08192-137">Under **Server type**, click **SQL Server**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="08192-138">Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.</span><span class="sxs-lookup"><span data-stu-id="08192-138">In **Microsoft SQL Server Management Studio**, double-click **SQL Server Agent**, and then click **Jobs**.</span></span>  
  
10. <span data-ttu-id="08192-139">Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **ValidateArchive**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="08192-139">In the **Object Explorer Details** pane, right-click **ValidateArchive**, and then click **Properties**.</span></span>  
  
11. <span data-ttu-id="08192-140">Dans le **propriétés du travail - ValidateArchive** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.</span><span class="sxs-lookup"><span data-stu-id="08192-140">In the **Job Properties - ValidateArchive** dialog box, under **Select a page**, click **Steps**.</span></span>  
  
12. <span data-ttu-id="08192-141">Dans le **liste des étapes du travail**, cliquez sur **valider**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="08192-141">In the **Job step list**, click **validate**, and then click **Edit**.</span></span>  
  
13. <span data-ttu-id="08192-142">Sur le **général** page, dans le **commande** zone, dans la commande, **exec dtasp_ValidateArchive null null**, remplacez null, null avec le nom du serveur hébergeant le BizTalk Suivi de base de données, entouré de guillemets, suivis du nom de la base de données des suivis BizTalk, entouré de guillemets, simples, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="08192-142">On the **General** page, in the **Command** box, in the command, **exec dtasp_ValidateArchive null, null**, replace null, null with the name of the server hosting the BizTalk Tracking database, surrounded by single quotes, followed by the name of the BizTalk Tracking database, surrounded by quotes, and then click **OK**.</span></span> <span data-ttu-id="08192-143">Exemple :</span><span class="sxs-lookup"><span data-stu-id="08192-143">For example:</span></span>  
  
     <span data-ttu-id="08192-144">**EXEC dtasp_ValidateArchive '**  *\<TrackingServerName\>*  **','**  *\<TrackingDatabaseName\>*  **'**</span><span class="sxs-lookup"><span data-stu-id="08192-144">**exec dtasp_ValidateArchive '** *\<TrackingServerName\>* **', '** *\<TrackingDatabaseName\>* **'**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="08192-145">Le travail ValidateArchive ne comporte pas de planification et vous ne devez pas configurer de planification pour ce travail.</span><span class="sxs-lookup"><span data-stu-id="08192-145">The ValidateArchive job does not have a schedule and you should not configure a schedule for it.</span></span> <span data-ttu-id="08192-146">Le travail de purge et d'archivage de la base de données des suivis (BizTalkDTADb) démarre ce travail automatiquement lors de la création d'une archive.</span><span class="sxs-lookup"><span data-stu-id="08192-146">Instead, the DTA Purge and Archive (BizTalkDTADb) job starts this job automatically when an archive is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08192-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08192-147">See Also</span></span>  
 [<span data-ttu-id="08192-148">Archivage et purge de la base de données de suivi BizTalk</span><span class="sxs-lookup"><span data-stu-id="08192-148">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)