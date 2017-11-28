---
title: "Déplacer les bases de données BizTalk Server | Documents Microsoft"
description: "Étapes pour déplacer les bases de données BizTalk Server vers un nouveau serveur, y compris l’arrêt des services et à l’aide des travaux de l’Agent SQL Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec302e6d-c89d-4fe7-849f-97b5566e8ba4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12bd1d6bc8a46d4e63dc69166d87f3678a0e3272
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-biztalk-server-databases"></a><span data-ttu-id="70b5f-103">Déplacement des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="70b5f-103">How to Move the BizTalk Server Databases</span></span>

## <a name="overview"></a><span data-ttu-id="70b5f-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="70b5f-104">Overview</span></span>
<span data-ttu-id="70b5f-105">Cette procédure permet de déplacer les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] principales vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="70b5f-105">You can use this procedure to move the primary [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases to another server.</span></span> <span data-ttu-id="70b5f-106">Elle permet également de déplacer les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] local vers un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distant ou vers un cluster [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70b5f-106">This same basic procedure can also be used to move the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases from a local [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] to a remote [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] or to a [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="70b5f-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="70b5f-107">Prerequisites</span></span>  
<span data-ttu-id="70b5f-108">Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] le rôle de serveur fixe sysadmin pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="70b5f-108">Sign in with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
## <a name="move-steps"></a><span data-ttu-id="70b5f-109">Étapes de déplacement</span><span class="sxs-lookup"><span data-stu-id="70b5f-109">Move steps</span></span>
  
1.  <span data-ttu-id="70b5f-110">Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="70b5f-110">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="70b5f-111">Pour plus d’informations, consultez [redémarrer les Services BizTalk Server et arrêt de BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span><span class="sxs-lookup"><span data-stu-id="70b5f-111">For more information, see [Restart BizTalk Server Services, and shut down BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>
  
    > [!IMPORTANT]
    >  <span data-ttu-id="70b5f-112">Il est important de vérifier que tous les services et travaux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont arrêtés avant de déplacer les bases de données.</span><span class="sxs-lookup"><span data-stu-id="70b5f-112">It is critical to make sure that all the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services and jobs are stopped before you move the databases.</span></span>  
  
2.  <span data-ttu-id="70b5f-113">Arrêtez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="70b5f-113">Stop the IIS service.</span></span>  
  
3.  <span data-ttu-id="70b5f-114">Arrêtez le service SQL Server Agent.</span><span class="sxs-lookup"><span data-stu-id="70b5f-114">Stop the SQL Server Agent service.</span></span>  
  
4.  <span data-ttu-id="70b5f-115">Sauvegardez les bases de données BizTalk en suivant les procédures de sauvegarde de base de données comme décrit dans [sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span><span class="sxs-lookup"><span data-stu-id="70b5f-115">Back up the BizTalk databases by following the database backup procedures as described at [Backing Up and Restoring the BizTalk Server Databases](../core/backing-up-and-restoring-the-biztalk-server-databases.md).</span></span>  
  
5.  <span data-ttu-id="70b5f-116">Restauration de bases de données sur le nouveau serveur de la base de données BizTalk restaurer procédures au [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="70b5f-116">Restore the BizTalk databases on the new server following the database restore procedures at [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span>  
  
6.  <span data-ttu-id="70b5f-117">Script de travaux de SQL Server Agent répertoriés ci-dessous pour le transfert vers le nouveau serveur, comme décrit dans [comment sauvegarder et restaurer des travaux de l’Agent SQL](../core/how-to-back-up-and-restore-sql-agent-jobs.md).</span><span class="sxs-lookup"><span data-stu-id="70b5f-117">Script the SQL Server Agent jobs listed below for transfer to the new server, as described at [How to Back Up and Restore SQL Agent Jobs](../core/how-to-back-up-and-restore-sql-agent-jobs.md).</span></span>  <span data-ttu-id="70b5f-118">Exécutez chacun des scripts sur le nouveau serveur pour recréer les travaux.</span><span class="sxs-lookup"><span data-stu-id="70b5f-118">Run each of the scripts on the new server to recreate the jobs.</span></span>  
  
     <span data-ttu-id="70b5f-119">Exécutez chacun des scripts sur le nouveau serveur pour recréer les travaux.</span><span class="sxs-lookup"><span data-stu-id="70b5f-119">Run each of the scripts on the new server to recreate the jobs.</span></span> <span data-ttu-id="70b5f-120">Certains travaux, tels que les **sauvegarde de BizTalk Server (BizTalkMsgBoxDb)** , doivent être reconfigurés sauf si les nouveaux chemins de fichier du serveur et le nom du serveur sont identiques à l’ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="70b5f-120">Certain jobs, such as the **Backup BizTalk Server (BizTalkMsgBoxDb)** job, will have to be reconfigured unless the new server file paths and server name are identical to the old server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70b5f-121">Vous pouvez également utiliser DTS/SSIS **transfert de travaux** de tâches pour déplacer les travaux vers le nouveau serveur, mais la plupart des utilisateurs sera probablement plus facile de générer un script les travaux à l’aide de SQL Management Studio.</span><span class="sxs-lookup"><span data-stu-id="70b5f-121">You can also use the SSIS/DTS **Transfer Jobs** task to move the jobs to the new server, but most users will probably find it easier to script the jobs using SQL Management Studio.</span></span>  
  
7.  <span data-ttu-id="70b5f-122">Outre les travaux de l’Agent SQL Server comme décrit dans l’étape précédente, vous devez également un script connexions comme décrit dans [comment sauvegarder et restaurer les connexions SQL Server](../core/how-to-back-up-and-restore-sql-server-logins.md).</span><span class="sxs-lookup"><span data-stu-id="70b5f-122">In addition to scripting SQL Server Agent jobs as described in the previous step, you must also script logins as described in [How to Back Up and Restore SQL Server Logins](../core/how-to-back-up-and-restore-sql-server-logins.md).</span></span> <span data-ttu-id="70b5f-123">Ces comptes de connexion doivent être restaurés sur le serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="70b5f-123">These logins need to be restored on the destination server.</span></span>  
  
8.  <span data-ttu-id="70b5f-124">Restaurer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données en suivant les étapes 9 à 22 [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="70b5f-124">Restore the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases by following steps 9 through 22 in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="70b5f-125">Cette procédure permet de mettre à jour la base de données de gestion BizTalk (BizTalkMgmtDb) et le Registre avec le nouvel emplacement des bases de données BizTalk.</span><span class="sxs-lookup"><span data-stu-id="70b5f-125">This procedure updates the BizTalk Management (BizTalkMgmtDb) database and registry with the new location of the BizTalk databases.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70b5f-126">Dans le **SampleUpdateInfo.xml** de fichier, commentaire pour toutes les bases de données à l’exception de celles que vous avez déplacé vers le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="70b5f-126">In the **SampleUpdateInfo.xml** file, comment out all of the databases except for those you have moved to the new server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b5f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70b5f-127">See Also</span></span>  
 [<span data-ttu-id="70b5f-128">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="70b5f-128">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)