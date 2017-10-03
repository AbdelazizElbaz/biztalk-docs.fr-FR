---
title: "Comment supprimer une base de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, MessageBox database
- managing [MessageBox database], deleting
- MessageBox database, deleting
ms.assetid: 51f91fcb-8b97-4b00-9056-6d216c8ccb58
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a12c74bfef8d6afec15b0c83f520eb4be43696c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-a-messagebox-database"></a><span data-ttu-id="91690-102">Suppression d'une base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="91690-102">How to Delete a MessageBox Database</span></span>
<span data-ttu-id="91690-103">Utilisez la console Administration de BizTalk ou Windows Management Instrumentation (WMI) pour supprimer une base de données MessageBox d'un groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="91690-103">You use the BizTalk Administration Console or Windows Management Instrumentation (WMI) to remove a MessageBox database from a BizTalk group.</span></span> <span data-ttu-id="91690-104">Vous pouvez la supprimer d'un groupe BizTalk, ou la supprimer complètement de votre déploiement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="91690-104">You can remove a MessageBox database from a BizTalk group, or you can delete it from your BizTalk Server deployment entirely.</span></span>  
  
 <span data-ttu-id="91690-105">Vous pouvez ainsi supprimer une base de données MessageBox dont vous n'avez plus besoin, telle qu'une base de données utilisée à des fins de test.</span><span class="sxs-lookup"><span data-stu-id="91690-105">For example, you can delete a MessageBox database you are no longer using, such as a database used for testing purposes.</span></span>  
  
 <span data-ttu-id="91690-106">Huit étapes sont nécessaires afin de supprimer de manière définitive une base de données MessageBox de votre déploiement BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="91690-106">There are eight steps to permanently and completely removing MessageBox databases from your BizTalk Server deployment:</span></span>  
  
1.  <span data-ttu-id="91690-107">Désactivez la publication des nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="91690-107">Disable new message publication.</span></span>  
  
     <span data-ttu-id="91690-108">Pour pouvoir supprimer une base de données MessageBox, vous devez désactiver la publication des nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="91690-108">You must disable the publication of new messages before you delete a MessageBox database.</span></span> <span data-ttu-id="91690-109">Pour plus d’informations sur la désactivation de publication des nouveaux messages, consultez [comment désactiver la Publication de nouveaux messages](../core/how-to-disable-new-message-publication.md).</span><span class="sxs-lookup"><span data-stu-id="91690-109">For information about disabling new message publication, see [How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md).</span></span>  
  
2.  <span data-ttu-id="91690-110">Attendez que l'intervalle d'actualisation du cache expire.</span><span class="sxs-lookup"><span data-stu-id="91690-110">Wait for the cache refresh interval to expire.</span></span>  
  
     <span data-ttu-id="91690-111">Après la désactivation de la publication des nouveaux messages, vous devez patienter quelques instants avant de supprimer la base de données.</span><span class="sxs-lookup"><span data-stu-id="91690-111">After you disable the publication of new messages, you must wait before you delete the database.</span></span> <span data-ttu-id="91690-112">Le temps d'attente correspond à deux fois la durée de l'intervalle CacheRefreshInterval.</span><span class="sxs-lookup"><span data-stu-id="91690-112">The wait time is defined as twice the length of the CacheRefreshInterval.</span></span> <span data-ttu-id="91690-113">La valeur par défaut de CacheRefreshInterval est de 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="91690-113">The default value of CacheRefreshInterval is 60 seconds.</span></span> <span data-ttu-id="91690-114">Vous utilisez la **propriétés du groupe** boîte de dialogue pour modifier l’actualisation du Cache.</span><span class="sxs-lookup"><span data-stu-id="91690-114">You use the **Group Properties** dialog box to change the Cache Refresh.</span></span>  
  
3.  <span data-ttu-id="91690-115">Supprimez la base de données MessageBox du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="91690-115">Remove the MessageBox database from the BizTalk Group.</span></span>  
  
     <span data-ttu-id="91690-116">La suppression de la base de données MessageBox du groupe BizTalk supprime également sa référence de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="91690-116">Removing the MessageBox database from the BizTalk Group removes the MessageBox reference from the BizTalk Management database.</span></span>  
  
4.  <span data-ttu-id="91690-117">Redémarrez les instances d'hôte contenant les connexions en mémoire cache de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="91690-117">Restart host instances that contain cached connections to the MessageBox database.</span></span>  
  
     <span data-ttu-id="91690-118">Vous devez redémarrer l'instance d'hôte avant de supprimer physiquement la base de données du serveur SQL Server si des connexions à la base de données du moteur d'exécution existent dans le cache.</span><span class="sxs-lookup"><span data-stu-id="91690-118">You must restart the host instance before physically deleting the database from SQL Server if cached database connections from the run-time engine are present.</span></span> <span data-ttu-id="91690-119">Pour plus d’informations sur le démarrage d’une instance d’hôte, consultez [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="91690-119">For information about starting a host instance, see [How to Start a Host Instance](../core/how-to-start-a-host-instance.md).</span></span>  
  
5.  <span data-ttu-id="91690-120">Arrêtez toutes les instances d'hôte en cours ayant accès à la base de données.</span><span class="sxs-lookup"><span data-stu-id="91690-120">Stop all in-progress host instances that access the database.</span></span> <span data-ttu-id="91690-121">Pour plus d’informations sur l’arrêt d’une instance d’hôte en cours, consultez [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md).</span><span class="sxs-lookup"><span data-stu-id="91690-121">For information about stopping an in-progress host instance, see [How to Stop a Host Instance](../core/how-to-stop-a-host-instance.md).</span></span>  
  
     <span data-ttu-id="91690-122">Si vous supprimez une base de données MessageBox autre que principale, avant d'arrêter l'instance d'hôte en cours, désactivez la publication des nouveaux messages vers cette base de données et vérifiez les points suivants : </span><span class="sxs-lookup"><span data-stu-id="91690-122">If you are removing a non-primary MessageBox database, before stopping an in-progress host instance, you should first disable publication of new messages to that message box and make sure that:</span></span>  
  
    -   <span data-ttu-id="91690-123">Il ne reste aucune instance de service en cours d'exécution dans la base MessageBox.</span><span class="sxs-lookup"><span data-stu-id="91690-123">There are no running service instances remaining in the message box.</span></span>  
  
    -   <span data-ttu-id="91690-124">Il ne reste aucune instance suspendue (ou autres) dans la base MessageBox.</span><span class="sxs-lookup"><span data-stu-id="91690-124">There are no suspended (or any other remaining) instances left in the message box.</span></span>  
  
    -   <span data-ttu-id="91690-125">Les données de suivi BAM ont été transférées vers la base de données des suivis BizTalk (BizTalkDTADb). La table TrackingData doit être vide.</span><span class="sxs-lookup"><span data-stu-id="91690-125">BAM tracked data has been moved to the BizTalk Tracking (BizTalkDTADb) database (TrackingData table should be empty).</span></span>  
  
    -   <span data-ttu-id="91690-126">Les corps de message suivis ont été transférés vers la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="91690-126">Tracked message bodies have been moved to the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
6.  <span data-ttu-id="91690-127">Vérifiez que le travail de l'agent SQL Server Agent en arrière-plan est terminé.</span><span class="sxs-lookup"><span data-stu-id="91690-127">Ensure that the background SQL Server Agent job is finished.</span></span>  
  
     <span data-ttu-id="91690-128">Avant de supprimer définitivement une base de données MessageBox de votre déploiement BizTalk Server, assurez-vous que le travail de l'agent SQL Server Agent en arrière-plan a bien terminé de transférer tous les corps de messages suivis dans la table TrackingSpool, et que les tables TrackingSpool ont été sauvegardées.</span><span class="sxs-lookup"><span data-stu-id="91690-128">Before you permanently delete a MessageBox database from your BizTalk Server deployment, you should first ensure that the background SQL Server Agent job has finished transferring all tracked message bodies to the TrackingSpool table, and then back up the TrackingSpool tables.</span></span> <span data-ttu-id="91690-129">Pour plus d'informations sur la vérification de l'état d'un travail SQL Server Agent en arrière-plan, consultez la documentation en ligne de SQL Server. </span><span class="sxs-lookup"><span data-stu-id="91690-129">For information about checking the status of a background SQL Server Agent job, see SQL Server Books Online.</span></span>  
  
7.  <span data-ttu-id="91690-130">Sauvegardez les tables TrackingSpool.</span><span class="sxs-lookup"><span data-stu-id="91690-130">Back up the TrackingSpool tables.</span></span>  
  
     <span data-ttu-id="91690-131">Les corps de messages suivis demeurent dans la base de données MessageBox jusqu'à ce que vous sauvegardiez manuellement les tables TrackingSpool dans un périphérique de stockage externe.</span><span class="sxs-lookup"><span data-stu-id="91690-131">Tracked message bodies remain in the MessageBox database until you manually back up the TrackingSpool tables into external storage.</span></span> <span data-ttu-id="91690-132">Avant la sauvegarde, un travail de l'agent SQL Server Agent en arrière-plan transfère les corps de message de la table Spool vers la table TrackingSpool.</span><span class="sxs-lookup"><span data-stu-id="91690-132">Before the backup happens, a background SQL Server Agent job transfers the message bodies from the Spool table to the TrackingSpool table.</span></span> <span data-ttu-id="91690-133">Pour plus d'informations sur la sauvegarde manuelle des tables SQL Server, consultez la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="91690-133">For information about manually backing up SQL Server tables, see SQL Server Books Online.</span></span>  
  
8.  <span data-ttu-id="91690-134">Supprimez la base de données du serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="91690-134">Remove the database from SQL Server.</span></span>  
  
     <span data-ttu-id="91690-135">La suppression d'une base de données MessageBox d'un groupe BizTalk n'entraîne pas sa suppression physique du serveur Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="91690-135">Deleting a MessageBox database from a BizTalk Group does not physically remove the database from Microsoft SQL Server.</span></span> <span data-ttu-id="91690-136">Pour une suppression définitive de la base de données, vous devez la supprimer à l'aide de SQL Server Enterprise Manager ou de SQL Server Management Studio après sa suppression du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="91690-136">To permanently delete the MessageBox database, you must remove it by using SQL Server Enterprise Manager or SQL Server Management Studio after it is removed from the BizTalk Group.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="91690-137">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="91690-137">Prerequisites</span></span>  
 <span data-ttu-id="91690-138">Les administrateurs qui gèrent les bases de données MessageBox doivent disposer des droits d'utilisateur nécessaires.</span><span class="sxs-lookup"><span data-stu-id="91690-138">Administrators who manage MessageBox databases must have the required user rights.</span></span> <span data-ttu-id="91690-139">Pour gérer ces bases de données et désactiver la publication des nouveaux messages, vous devez :</span><span class="sxs-lookup"><span data-stu-id="91690-139">You must have the following user rights to manage MessageBox databases and disable new message publication:</span></span>  
  
-   <span data-ttu-id="91690-140">Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="91690-140">You must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
-   <span data-ttu-id="91690-141">être un administrateur SQL Server sur l'ordinateur sur lequel se trouve la base de données.</span><span class="sxs-lookup"><span data-stu-id="91690-141">You must be a SQL Server Administrator on the computer where the database exists.</span></span>  
  
### <a name="to-delete-a-messagebox-database-from-a-biztalk-group"></a><span data-ttu-id="91690-142">Pour supprimer une base de données MessageBox d'un groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="91690-142">To delete a MessageBox database from a BizTalk Group</span></span>  
  
1.  <span data-ttu-id="91690-143">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="91690-143">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="91690-144">Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **boîtes de Message**.</span><span class="sxs-lookup"><span data-stu-id="91690-144">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group, click **Platform Settings**, and then click **Message Boxes**.</span></span>  
  
3.  <span data-ttu-id="91690-145">Dans le volet de détails, cliquez sur la base de données MessageBox vous souhaitez supprimer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="91690-145">In the details pane, right-click the message box database you want to remove, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="91690-146">Dans le **propriétés de MessageBox** boîte de dialogue, sélectionnez le **désactiver la publication des nouveaux messages** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="91690-146">In the **Message Box Properties** dialog box, select the **Disable new message publication** check box.</span></span>  
  
5.  <span data-ttu-id="91690-147">Ouvrez la page Hub du groupe dans la console Administration de BizTalk Server pour vérifier qu'aucune instance de message n'est mise en attente ou suspendue dans la base de données que vous supprimez.</span><span class="sxs-lookup"><span data-stu-id="91690-147">Use the Group Hub page in the BizTalk Server Administration Console to verify that no message instances are dehydrated or suspended on the MessageBox database you are deleting.</span></span>  
  
6.  <span data-ttu-id="91690-148">Laissez passer un laps de temps correspondant à deux fois la durée de l'intervalle CacheRefreshInterval.</span><span class="sxs-lookup"><span data-stu-id="91690-148">Wait for a period of time twice the length of the CacheRefreshInterval.</span></span> <span data-ttu-id="91690-149">La valeur par défaut de CacheRefreshInterval est de 60 secondes.</span><span class="sxs-lookup"><span data-stu-id="91690-149">The default value of CacheRefreshInterval is 60 seconds.</span></span>  
  
7.  <span data-ttu-id="91690-150">Dans le volet de détails, cliquez sur la base de données MessageBox que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="91690-150">In the details pane, right-click the MessageBox database that you want to delete, and click **Delete**.</span></span>  
  
8.  <span data-ttu-id="91690-151">Après avoir lu le message d’avertissement, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="91690-151">After reading the warning message, click **OK**.</span></span>  
  
9. <span data-ttu-id="91690-152">Dans l’arborescence de la console, développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="91690-152">In the console tree, expand the BizTalk group, click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
10. <span data-ttu-id="91690-153">Dans le volet de détails, cliquez avec le bouton droit sur toutes les instances d'hôte en cours d'exécution pour les arrêter et les redémarrer.</span><span class="sxs-lookup"><span data-stu-id="91690-153">In the details pane, right-click all running host instances, and stop and restart each one.</span></span>  
  
11. <span data-ttu-id="91690-154">Sur le serveur hébergeant la base de données MessageBox, ouvrez SQL Server Enterprise Manager ou SQL Server Management Studio, en fonction de la version de SQL Server utilisée, puis supprimez la base de données.</span><span class="sxs-lookup"><span data-stu-id="91690-154">On the server where the MessageBox database resides, open SQL Server Enterprise Manager or SQL Server Management Studio, depending on which version of SQL Server you are using, and then delete the database.</span></span>  
  
     <span data-ttu-id="91690-155">Pour plus d'informations sur la suppression d'une base de données dans SQL Server, consultez la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="91690-155">For information about how to delete a database in SQL Server, see SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91690-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91690-156">See Also</span></span>  
 <span data-ttu-id="91690-157">[Gestion des bases de données MessageBox](../core/managing-messagebox-databases.md) </span><span class="sxs-lookup"><span data-stu-id="91690-157">[Managing MessageBox Databases](../core/managing-messagebox-databases.md) </span></span>  
 <span data-ttu-id="91690-158">[Comment ajouter une nouvelle base de données MessageBox](../core/how-to-add-a-new-messagebox-database.md) </span><span class="sxs-lookup"><span data-stu-id="91690-158">[How to Add a New MessageBox Database](../core/how-to-add-a-new-messagebox-database.md) </span></span>  
 <span data-ttu-id="91690-159">[Comment désactiver la Publication des nouveaux messages](../core/how-to-disable-new-message-publication.md) </span><span class="sxs-lookup"><span data-stu-id="91690-159">[How to Disable New Message Publication](../core/how-to-disable-new-message-publication.md) </span></span>  
 [<span data-ttu-id="91690-160">La base de données MessageBox</span><span class="sxs-lookup"><span data-stu-id="91690-160">The MessageBox Database</span></span>](../core/the-messagebox-database.md)