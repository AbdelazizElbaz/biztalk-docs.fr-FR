---
title: "Comment sauvegarder des bases de données personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom databases
- customizing, custom databases
- backing up, custom databases
ms.assetid: 86bebf3c-968e-4fad-9dab-ced1b04aaac7
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2993de90de3f7b768cc5368012d1f27f8940a99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-custom-databases"></a><span data-ttu-id="b1704-102">Sauvegarde des bases de données personnalisées</span><span class="sxs-lookup"><span data-stu-id="b1704-102">How to Back Up Custom Databases</span></span>
<span data-ttu-id="b1704-103">Comme vos bases de données personnalisées ne sont pas installées avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], elles ne sont pas incluses dans la liste par défaut des bases de données que le travail de sauvegarde de BizTalk Server doit marquer et sauvegarder.</span><span class="sxs-lookup"><span data-stu-id="b1704-103">Because your custom databases are not installed with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], they are not included in the default list of databases to be marked and backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="b1704-104">Si vous souhaitez que ce travail sauvegarde vos bases de données personnalisées, vous devez les y ajouter manuellement.</span><span class="sxs-lookup"><span data-stu-id="b1704-104">If you want the Backup BizTalk Server job to back up your custom databases, you must manually add the databases to the Backup BizTalk Server job.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b1704-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="b1704-105">Prerequisites</span></span>  
  
1.  <span data-ttu-id="b1704-106">SQL Server doit être configuré pour utiliser le modèle de récupération complète afin de garantir l'intégrité des données dans les jeux de sauvegarde de bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1704-106">SQL Server must be configured to use the full recovery model to ensure the integrity of data in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] database backup sets.</span></span>  <span data-ttu-id="b1704-107">Pour plus d’informations, consultez [journaux](../core/log-shipping.md).</span><span class="sxs-lookup"><span data-stu-id="b1704-107">For more information see [Log Shipping](../core/log-shipping.md).</span></span>  
  
2.  <span data-ttu-id="b1704-108">Pour sauvegarder vos bases de données personnalisées, vous devez ouvrir une session à l'aide d'un compte d'utilisateur ayant accès à chacune des bases données en cours de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="b1704-108">To back up your custom databases, you must be logged on with a user account that has access to each of the databases you are backing up.</span></span>  
  
     <span data-ttu-id="b1704-109">Grâce au rôle SQL Server BTS_BACKUP_USERS inclus dans BizTalk Server, le compte d'utilisateur utilisé pour sauvegarder vos bases de données n'a pas besoin d'autorisations d'administrateur dans SQL Server, sauf pour le serveur principal contrôlant le processus de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="b1704-109">BizTalk Server includes a SQL Server role named BTS_BACKUP_USERS so that the user account you use to back up your databases does not require System Administrator permissions within SQL Server, except for the primary server controlling the backup process.</span></span>  
  
     <span data-ttu-id="b1704-110">Notez les points suivants relatifs à la configuration du compte d'utilisateur utilisé pour la sauvegarde des bases de données :</span><span class="sxs-lookup"><span data-stu-id="b1704-110">When setting up the user account that you are using to back up your databases, note the following:</span></span>  
  
    -   <span data-ttu-id="b1704-111">Vous devez créer un compte de connexion SQL Server pour cet utilisateur et affecter ce dernier au rôle BTS_BACKUP_USERS sur chaque serveur.</span><span class="sxs-lookup"><span data-stu-id="b1704-111">You must create a SQL Server logon account for this user, and assign this user to the BizTalk BTS_BACKUP_USERS role on each server.</span></span>  
  
    -   <span data-ttu-id="b1704-112">Les travaux de sauvegarde de BizTalk Server peuvent être configurés pour une exécution sous un compte d'utilisateur différent de celui utilisé pour le service SQL Server Agent.</span><span class="sxs-lookup"><span data-stu-id="b1704-112">The BizTalk Server backup jobs can be configured to run under a user account that is different than the one used for the SQL Server Agent service.</span></span>  
  
    -   <span data-ttu-id="b1704-113">Vous devez configurer l'exécution du service SQL Server Agent sous un compte de domaine.</span><span class="sxs-lookup"><span data-stu-id="b1704-113">You must configure the SQL Server Agent service to run under a domain account.</span></span> <span data-ttu-id="b1704-114">Si toutes les bases de données sont situées sur le même ordinateur, vous pouvez configurer le service SQL Server Agent pour utiliser un compte local.</span><span class="sxs-lookup"><span data-stu-id="b1704-114">If all databases are on the same computer, you can configure SQL Server Agent to use a local account.</span></span>  
  
### <a name="to-back-up-custom-databases"></a><span data-ttu-id="b1704-115">Pour sauvegarder les bases de données personnalisées</span><span class="sxs-lookup"><span data-stu-id="b1704-115">To back up custom databases</span></span>  
  
1.  <span data-ttu-id="b1704-116">Créez les objets dans la nouvelle base de données :</span><span class="sxs-lookup"><span data-stu-id="b1704-116">Build the objects in the new database:</span></span>  
  
    -   <span data-ttu-id="b1704-117">Accédez au répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema, puis exécutez Backup_Setup_All_Procs.sql et Backup_Setup_All_Tables.sql sur toutes les bases de données personnalisées que vous souhaitez sauvegarder.</span><span class="sxs-lookup"><span data-stu-id="b1704-117">Browse to the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema directory, and then run Backup_Setup_All_Procs.sql and Backup_Setup_All_Tables.sql against all your custom databases that you want to back up.</span></span> <span data-ttu-id="b1704-118">Ceci permet de créer les procédures, la table et le rôle nécessaires, et d'affecter les autorisations aux procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="b1704-118">This creates the necessary procedures, table, and role and assigns permissions to the stored procedures.</span></span>  
  
2.  <span data-ttu-id="b1704-119">Configurez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b1704-119">Perform the following configurations:</span></span>  
  
    -   <span data-ttu-id="b1704-120">Liez le serveur SQL Server hébergeant la base de données de gestion BizTalk au serveur SQL Server hébergeant la nouvelle base de données.</span><span class="sxs-lookup"><span data-stu-id="b1704-120">Link the SQL server that is hosting the BizTalk Management database to the SQL server hosting the new database.</span></span> <span data-ttu-id="b1704-121">Le compte utilisé pour exécuter le service SQL Server Agent sur le serveur SQL Server de gestion doit être un compte de domaine mappé à chaque ordinateur hébergeant une base de données à sauvegarder.</span><span class="sxs-lookup"><span data-stu-id="b1704-121">The account used to run the SQL Server Agent service on the management SQL Server must be a domain account that is mapped to each computer holding a database to be backed up.</span></span> <span data-ttu-id="b1704-122">Si les bases de données se trouvent sur le même ordinateur, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="b1704-122">If the databases are on the same computer you can skip this step.</span></span> <span data-ttu-id="b1704-123">Cette opération est effectuée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b1704-123">This is done automatically.</span></span>  
  
    -   <span data-ttu-id="b1704-124">Ajoutez un compte de connexion au serveur SQL Server hébergeant la nouvelle base de données pour le compte exécutant le service SQL Server Agent sur la base de données de gestion SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b1704-124">Add a login on the SQL server hosting the new database for the account running the SQL Server Agent service on the Mgmt SQL Server.</span></span> <span data-ttu-id="b1704-125">Si les bases de données se trouvent sur le même ordinateur, vous pouvez ignorer cette étape.</span><span class="sxs-lookup"><span data-stu-id="b1704-125">If the databases are on the same computer you can skip this step.</span></span>  
  
    -   <span data-ttu-id="b1704-126">Ajoutez un utilisateur dans la nouvelle base de données pour le compte de connexion que vous venez de créer, puis ajoutez-le au rôle BTS_BACKUP_USERS.</span><span class="sxs-lookup"><span data-stu-id="b1704-126">Add a user in the new database for the login created in the previous step and add them to the BTS_BACKUP_USERS role.</span></span> <span data-ttu-id="b1704-127">Les scripts créent ce rôle et octroient à celui-ci les autorisations d'exécution sur les procédures nécessaires lors de la première étape.</span><span class="sxs-lookup"><span data-stu-id="b1704-127">This role is created and granted Execute permissions on the necessary procedures by the scripts in step 1.</span></span>  
  
3.  <span data-ttu-id="b1704-128">À l’aide de SQL Server Enterprise Manager ou SQL Server Management Studio, dans la base de données de gestion BizTalk (BizTalkMgmtDb), modifiez le **adm_OtherBackupDatabases** table pour inclure une ligne pour chacun de vos bases de données personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b1704-128">Using SQL Server Enterprise Manager or SQL Server Management Studio, in the BizTalk Management (BizTalkMgmtDb) database, modify the **adm_OtherBackupDatabases** table to include a row for each of your custom databases.</span></span>  
  
4.  <span data-ttu-id="b1704-129">Tapez les noms des nouveaux serveur et base de données dans les colonnes correspondantes, comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="b1704-129">Type the new server and database names in the corresponding columns, as shown in the following table.</span></span>  
  
    |<span data-ttu-id="b1704-130">Colonne</span><span class="sxs-lookup"><span data-stu-id="b1704-130">Column</span></span>|<span data-ttu-id="b1704-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="b1704-131">Value</span></span>|  
    |------------|-----------|  
    |<span data-ttu-id="b1704-132">DefaultDatabaseName</span><span class="sxs-lookup"><span data-stu-id="b1704-132">DefaultDatabaseName</span></span>|<span data-ttu-id="b1704-133">Nom convivial de votre base de données personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1704-133">The friendly name of your custom database.</span></span>|  
    |<span data-ttu-id="b1704-134">DatabaseName</span><span class="sxs-lookup"><span data-stu-id="b1704-134">DatabaseName</span></span>|<span data-ttu-id="b1704-135">Nom de votre base de données personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b1704-135">The name of your custom database.</span></span>|  
    |<span data-ttu-id="b1704-136">ServerName</span><span class="sxs-lookup"><span data-stu-id="b1704-136">ServerName</span></span>|<span data-ttu-id="b1704-137">Nom de l'ordinateur exécutant SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b1704-137">The name of the computer running SQL Server.</span></span>|  
    |<span data-ttu-id="b1704-138">BTSServerName</span><span class="sxs-lookup"><span data-stu-id="b1704-138">BTSServerName</span></span>|<span data-ttu-id="b1704-139">Nom du serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b1704-139">The name of the BizTalk Server.</span></span> <span data-ttu-id="b1704-140">Cette valeur n'est pas utilisée mais doit tout de même être renseignée.</span><span class="sxs-lookup"><span data-stu-id="b1704-140">This value is not used, but it must contain a value nonetheless.</span></span>|  
  
 <span data-ttu-id="b1704-141">Le travail de sauvegarde de BizTalk Server sauvegarde vos bases de données personnalisées lors de sa prochaine exécution.</span><span class="sxs-lookup"><span data-stu-id="b1704-141">The next time you run the Backup BizTalk Server job, it will back up your custom databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1704-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1704-142">See Also</span></span>  
 <span data-ttu-id="b1704-143">[Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="b1704-143">[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="b1704-144">Informations avancées sur la sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="b1704-144">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)