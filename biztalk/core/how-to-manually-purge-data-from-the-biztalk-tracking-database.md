---
title: "Purge manuelle des données de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging, manually
- purging, warnings
ms.assetid: f350d850-5034-4166-940c-8d10b7b445fb
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb8bf8d87f7868367c252cdc75842b234cb06ff9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manually-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="96025-102">Purge manuelle des données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="96025-102">How to Manually Purge Data from the BizTalk Tracking Database</span></span>
<span data-ttu-id="96025-103">Le travail de purge et d'archivage DTA de SQL Server Agent permet de limiter les actions manuelles d'effacement des données de la base de données des suivis BizTalk (BizTalkDTADb), du fait de la purge continue de la base et du compactage des données de suivi stockées.</span><span class="sxs-lookup"><span data-stu-id="96025-103">The DTA Archive and Purge SQL Server Agent job reduces the need to manually purge data from the BizTalk Tracking (BizTalkDTADb) database due to continuous purging of the database and compaction of stored tracking data.</span></span> <span data-ttu-id="96025-104">Vous pouvez toutefois être amené à effacer les données manuellement si votre base de données BizTalkDTADb a atteint une taille telle que les performances se dégradent de plus en plus et que, en dépit du travail de purge et d'archivage DTA, la croissance de la base ne peut être contenue.</span><span class="sxs-lookup"><span data-stu-id="96025-104">You might need to manually purge data if your BizTalk Tracking (BizTalkDTADb) database has grown so much that sustained performance degradation is occurring and the DTA Archive and Purge job is unable to keep up with the database growth.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="96025-105">Cette procédure supprime de la base BizTalkDTADb toutes les données de suivi pour les instances terminées, quelle que soit leur heure d'achèvement.</span><span class="sxs-lookup"><span data-stu-id="96025-105">Performing this procedure deletes all tracking data for completed instances from the BizTalk Tracking (BizTalkDTADb) database regardless of completion time.</span></span> <span data-ttu-id="96025-106">Avant de l'exécuter, il est recommandé d'archiver séparément la base de données des suivis BizTalk et les autres bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="96025-106">Before performing this procedure, you should archive the BizTalk Tracking (BizTalkDTADb) database separately from the other [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="96025-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="96025-107">Prerequisites</span></span>  
 <span data-ttu-id="96025-108">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="96025-108">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-manually-purge-data-from-the-biztalk-tracking-database"></a><span data-ttu-id="96025-109">Pour purger manuellement les données de la base de données des suivis BizTalk</span><span class="sxs-lookup"><span data-stu-id="96025-109">To manually purge data from the BizTalk Tracking database</span></span>  
  
1.  <span data-ttu-id="96025-110">Sauvegardez vos bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="96025-110">Backup your BizTalk Server databases.</span></span>  
  
2.  <span data-ttu-id="96025-111">Archivez la base de données des suivis BizTalk (BizTalkDTADb).</span><span class="sxs-lookup"><span data-stu-id="96025-111">Archive the BizTalk Tracking (BizTalkDTADb) database.</span></span>  
  
3.  <span data-ttu-id="96025-112">Ouvrez la console Services.</span><span class="sxs-lookup"><span data-stu-id="96025-112">Open the Services console.</span></span> <span data-ttu-id="96025-113">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="96025-113">Click **Start**, click **Run**, and then type **services.msc**.</span></span> <span data-ttu-id="96025-114">Si un **contrôle de compte d’utilisateur** boîte de dialogue s’affiche, cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="96025-114">If a **User Account Control** dialog is displayed, click **Continue**.</span></span>  
  
4.  <span data-ttu-id="96025-115">Lorsque la console Services apparaît, arrêtez les services suivants.</span><span class="sxs-lookup"><span data-stu-id="96025-115">When the Services console appears, locate and then stop each of the following services.</span></span> <span data-ttu-id="96025-116">Pour arrêter un service, cliquez sur la ligne de service dans le **Services** volet, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="96025-116">To stop a service, right-click the service row in the **Services** pane, and then click **Stop**.</span></span>  
  
    -   <span data-ttu-id="96025-117">Service BizTalkServiceBizTalkGroup : BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="96025-117">BizTalkServiceBizTalkGroup : BizTalkServerApplication</span></span>  
  
    -   <span data-ttu-id="96025-118">Service d'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="96025-118">Enterprise Single Sign-On Service</span></span>  
  
         <span data-ttu-id="96025-119">Si le service BizTalkServiceBizTalkGroup : service BizTalkServerApplication est en cours d’exécution lorsque vous essayez d’arrêter l’entreprise unique Service d’authentification, un **arrêter les autres Services** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="96025-119">If the BizTalkServiceBizTalkGroup : BizTalkServerApplication service is running when you try to shut down the Enterprise Singe Sign-On Service, a **Stop Other Services** dialog will be displayed.</span></span> <span data-ttu-id="96025-120">Cliquez sur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="96025-120">Click **Yes**.</span></span>  
  
    -   <span data-ttu-id="96025-121">Service de mise à jour du moteur des règles</span><span class="sxs-lookup"><span data-stu-id="96025-121">Rule Engine Update Service</span></span>  
  
5.  <span data-ttu-id="96025-122">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="96025-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span> <span data-ttu-id="96025-123">Si un **contrôle de compte d’utilisateur** boîte de dialogue s’affiche, vérifiez que l’action décrite est ce que vous souhaitez, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="96025-123">If a **User Account Control** dialog is displayed, verify that the action described is what you want, and then click **Continue**.</span></span>  
  
6.  <span data-ttu-id="96025-124">Dans le **Console d’Administration de BizTalk Server** dans le volet Explorateur, sur le côté gauche de la fenêtre, double-cliquez sur **groupe BizTalk** pour développer la liste, puis double-cliquez sur **plateforme Paramètres**, puis cliquez sur **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="96025-124">In the **BizTalk Server Administration Console** in the explorer pane on the left side of the window, double-click **BizTalk Group** to expand the list below it, then double-click **Platform Settings**, and then click **Host Instances**.</span></span> <span data-ttu-id="96025-125">Cela affiche une liste des instances d’hôte (le **Instances d’hôte** volet) et les propriétés associées, sur le côté droit de l’écran.</span><span class="sxs-lookup"><span data-stu-id="96025-125">This will display a list of host instances (the **Host Instances** pane) and related properties, on the right side of the screen.</span></span>  
  
7.  <span data-ttu-id="96025-126">Dans le **Instances d’hôte** volet, cliquez sur chaque instance d’hôte en cours d’exécution, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="96025-126">In the **Host Instances** pane, right-click each running host instance, and then click **Stop**.</span></span>  
  
8.  <span data-ttu-id="96025-127">Cliquez sur **Démarrer**, accédez à **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="96025-127">Click **Start**, go to **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="96025-128">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="96025-128">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="96025-129">**net stop iisadmin /y**</span><span class="sxs-lookup"><span data-stu-id="96025-129">**net stop iisadmin /y**</span></span>  
  
     <span data-ttu-id="96025-130">Cela interrompt le service d'administration IIS ainsi que tous les services dépendants, un à un, et empêche les nouvelles données d'être écrites dans la base de données BizTalkDTADb tant qu'une purge des données est en cours.</span><span class="sxs-lookup"><span data-stu-id="96025-130">This stops the IIS Admin Service and all dependent services, one-by-one and prevents new data from being written to the BizTalkDTADb while data is being purged.</span></span> <span data-ttu-id="96025-131">Dressez la liste des services pendant leur arrêt.</span><span class="sxs-lookup"><span data-stu-id="96025-131">Write down the list of services as each one is stopped.</span></span> <span data-ttu-id="96025-132">Celle-ci vous sera utile par la suite lors du redémarrage du service IIS.</span><span class="sxs-lookup"><span data-stu-id="96025-132">You will need to use this list of services later when you restart IIS.</span></span>  
  
     <span data-ttu-id="96025-133">Les résultats renvoyés suite à l'exécution de la commande se présentent comme dans l'exemple ci-dessous (les services dépendants répertoriés sur votre ordinateur peuvent être quelque peu différents) :</span><span class="sxs-lookup"><span data-stu-id="96025-133">Below is an example of the output you will see after issuing this command (the dependent services listed on your computer may vary):</span></span>  
  
    ```  
    The following services are dependent on the IIS Admin Service service. Stopping the IIS Admin Service service will also stop these services.  
    World Wide Web Publishing Service  
    HTTP SSL  
    ```  
  
10. <span data-ttu-id="96025-134">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="96025-134">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP2**, and then click **SQL Server Management Studio**.</span></span>  
  
11. <span data-ttu-id="96025-135">Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL Server approprié.</span><span class="sxs-lookup"><span data-stu-id="96025-135">In the **Connect to Server** dialog box, specify the name of the SQL Server where the BizTalk Tracking (BizTalkDTADb) database resides and the appropriate authentication type, and then click **Connect** to connect to the appropriate SQL Server.</span></span>  
  
12. <span data-ttu-id="96025-136">Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **bases de données**, double-cliquez sur le **BizTalkDTADb** de base de données, double-cliquez sur  **Programmabilité**, puis cliquez sur **de procédures stockées**.</span><span class="sxs-lookup"><span data-stu-id="96025-136">In **Microsoft SQL Server Management Studio**, double-click **Databases**, double-click the **BizTalkDTADb** database, double-click **Programmability**, and then click **Stored Procedures**.</span></span>  
  
13. <span data-ttu-id="96025-137">Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **dtasp_PurgeAllCompletedTrackingData**, puis cliquez sur **exécuter la procédure stockée**.</span><span class="sxs-lookup"><span data-stu-id="96025-137">In the **Object Explorer Details** pane, right-click **dtasp_PurgeAllCompletedTrackingData**, and then click **Execute Stored Procedure**.</span></span>  
  
14. <span data-ttu-id="96025-138">Dans le **exécuter la procédure** boîte de dialogue, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="96025-138">In the **Execute Procedure** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="96025-139">Cette procédure stockée supprime toutes les données de suivi associées aux instances terminées, quelle que soit leur heure d'achèvement.</span><span class="sxs-lookup"><span data-stu-id="96025-139">This stored procedure deletes all tracking data associated with completed instances regardless of their completion time.</span></span>  
  
15. <span data-ttu-id="96025-140">Ouvrez Services.</span><span class="sxs-lookup"><span data-stu-id="96025-140">Open Services.</span></span> <span data-ttu-id="96025-141">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="96025-141">Click **Start**, click **Run**, and then type **services.msc**.</span></span> <span data-ttu-id="96025-142">Si un **contrôle de compte d’utilisateur** boîte de dialogue s’affiche, vérifiez que l’action décrite est ce que vous souhaitez, puis cliquez sur **continuer**.</span><span class="sxs-lookup"><span data-stu-id="96025-142">If a **User Account Control** dialog is displayed, verify that the action described is what you want, and then click **Continue**.</span></span>  
  
16. <span data-ttu-id="96025-143">Cliquez sur chacun des services suivants, puis cliquez sur **Démarrer**:</span><span class="sxs-lookup"><span data-stu-id="96025-143">Right-click each of the following services, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="96025-144">Service BizTalkServiceBizTalkGroup : BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="96025-144">BizTalkServiceBizTalkGroup : BizTalkServerApplication</span></span>  
  
    -   <span data-ttu-id="96025-145">Service d'authentification unique de l'entreprise</span><span class="sxs-lookup"><span data-stu-id="96025-145">Enterprise Single Sign-On Service</span></span>  
  
    -   <span data-ttu-id="96025-146">Service de mise à jour du moteur des règles</span><span class="sxs-lookup"><span data-stu-id="96025-146">Rule Engine Update Service</span></span>  
  
17. <span data-ttu-id="96025-147">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="96025-147">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
18. <span data-ttu-id="96025-148">Dans le **Console d’Administration de BizTalk Server**, double-cliquez sur le **groupe BizTalk**, double-cliquez sur **paramètres de plateforme**, puis cliquez sur **hôte Instances**.</span><span class="sxs-lookup"><span data-stu-id="96025-148">In the **BizTalk Server Administration Console**, double-click the **BizTalk Group**, double-click **Platform Settings**, and then click **Host Instances**.</span></span>  
  
19. <span data-ttu-id="96025-149">Dans le **détails de l’Explorateur d’objets** volet, cliquez sur chaque instance d’hôte arrêtée, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="96025-149">In the **Object Explorer Details** pane, right-click each stopped host instance, and then click **Start**.</span></span>  
  
20. <span data-ttu-id="96025-150">Démarrez une invite de commandes, comme indiqué à l'étape 8 ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="96025-150">Start a command prompt, as described in step 8 above.</span></span>  
  
21. <span data-ttu-id="96025-151">À l’invite de commandes, redémarrez chacun des services IIS que vous avez arrêtés à l’étape 4.</span><span class="sxs-lookup"><span data-stu-id="96025-151">At the command prompt, restart each of the IIS services that you stopped in step 4.</span></span> <span data-ttu-id="96025-152">Type :</span><span class="sxs-lookup"><span data-stu-id="96025-152">Type:</span></span>  
  
     <span data-ttu-id="96025-153">**Net start**  *\<IISserviceName\>*</span><span class="sxs-lookup"><span data-stu-id="96025-153">**net start** *\<IISserviceName\>*</span></span>  
  
     <span data-ttu-id="96025-154">Où  *\<IISserviceName\>*  est le nom du service IIS à redémarrer.</span><span class="sxs-lookup"><span data-stu-id="96025-154">Where *\<IISserviceName\>* is the name of the IIS service you want to restart.</span></span> <span data-ttu-id="96025-155">Vous devez répéter cette commande pour chaque service IIS.</span><span class="sxs-lookup"><span data-stu-id="96025-155">You must repeat this command for each of the IIS services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96025-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96025-156">See Also</span></span>  
 <span data-ttu-id="96025-157">[Archivage et la purge de la base de données de suivi de BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="96025-157">[Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md) </span></span>  
 <span data-ttu-id="96025-158">[Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="96025-158">[Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server-databases.md) </span></span>  
 [<span data-ttu-id="96025-159">Comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="96025-159">How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services</span></span>](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md)