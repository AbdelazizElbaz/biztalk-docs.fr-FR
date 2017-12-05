---
title: "Le déplacement de Notification BAM Services Databases1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89b4938e-ea4a-48d3-80c3-eb9401e28323
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d0ae3e4b5af7304eb07973fd5e19efce2e68c99
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-bam-notification-services-databases"></a><span data-ttu-id="4afb6-102">Déplacement des bases de données des services de notification BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-102">How to Move the BAM Notification Services Databases</span></span>
<span data-ttu-id="4afb6-103">Vous pouvez utiliser cette procédure pour déplacer la base de données des Services de Notification BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="4afb6-103">You can use this procedure to move the BAM Notification Services database to another server.</span></span>  <span data-ttu-id="4afb6-104">À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données des Services de Notification BAM implique deux étapes principales :</span><span class="sxs-lookup"><span data-stu-id="4afb6-104">From an end-to-end scenario perspective, moving the BAM Notification Services database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="4afb6-105">Déplacement de la base de données des Services de Notification BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-105">Moving the BAM Notification Services Database</span></span>](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiMoveDB)  
  
-   [<span data-ttu-id="4afb6-106">Bases de données des Services de mise à jour des références à la nouvelle Notification BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-106">Updating References to the New BAM Notification Services Databases</span></span>](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdate)  
  
> [!NOTE]  
>  <span data-ttu-id="4afb6-107">Vous devez déplacer la base de données d’Application (BAMAlertsApplication) des Services de Notification BAM et de la base de données de l’Instance (BAMAlertsNSMain) des Services de Notification BAM ensemble.</span><span class="sxs-lookup"><span data-stu-id="4afb6-107">You must move the BAM Notification Services Application (BAMAlertsApplication) database and the BAM Notification Services Instance (BAMAlertsNSMain) database together.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4afb6-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4afb6-108">Prerequisites</span></span>  
 <span data-ttu-id="4afb6-109">Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4afb6-109">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_NotiMoveDB"></a><span data-ttu-id="4afb6-110">Déplacement de la base de données des Services de Notification BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-110">Moving the BAM Notification Services Database</span></span>  
 <span data-ttu-id="4afb6-111">Les étapes de la procédure suivante pour déplacer la base de données des Services de Notification BAM.</span><span class="sxs-lookup"><span data-stu-id="4afb6-111">Perform the steps in the following procedure to move the BAM Notification Services database.</span></span>  
  
#### <a name="to-move-the-bam-notification-services-database"></a><span data-ttu-id="4afb6-112">Pour déplacer la base de données des Services de Notification BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-112">To move the BAM Notification Services database</span></span>  
  
1.  <span data-ttu-id="4afb6-113">Arrêtez toute analyse BAM cube mise à jour et les données maintenance SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données des Services de Notification BAM.</span><span class="sxs-lookup"><span data-stu-id="4afb6-113">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Notification Services database.</span></span>  
  
2.  <span data-ttu-id="4afb6-114">Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4afb6-114">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="4afb6-115">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="4afb6-115">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="4afb6-116">Arrêtez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="4afb6-116">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="4afb6-117">Arrêtez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="4afb6-117">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="4afb6-118">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4afb6-118">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="4afb6-119">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="4afb6-119">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="4afb6-120">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="4afb6-120">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="4afb6-121">Sauvegardez la base de données des Services de Notification BAM sur l’ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="4afb6-121">Back up the BAM Notification Services database on the old server.</span></span> <span data-ttu-id="4afb6-122">Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la sauvegarde d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="4afb6-122">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4afb6-123">Effectuez cette étape pour les bases de données BAMAlertsApplication et BAMAlertsNSMain.</span><span class="sxs-lookup"><span data-stu-id="4afb6-123">Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.</span></span>  
  
6.  <span data-ttu-id="4afb6-124">Copier la base de données des Services de Notification BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4afb6-124">Copy the BAM Notification Services database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="4afb6-125">Restaurez la base de données des Services de Notification BAM sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="4afb6-125">Restore the BAM Notification Services database on the new server.</span></span> <span data-ttu-id="4afb6-126">Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la façon de restaurer une base de données.</span><span class="sxs-lookup"><span data-stu-id="4afb6-126">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4afb6-127">Effectuez cette étape pour les bases de données BAMAlertsApplication et BAMAlertsNSMain.</span><span class="sxs-lookup"><span data-stu-id="4afb6-127">Perform this step for both BAMAlertsApplication and BAMAlertsNSMain databases.</span></span>  
  
##  <a name="BKMK_NotiUpdate"></a><span data-ttu-id="4afb6-128">Bases de données des Services de mise à jour des références à la nouvelle Notification BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-128">Updating References to the New BAM Notification Services Databases</span></span>  
 <span data-ttu-id="4afb6-129">Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références aux nouvelles bases de données de Services de Notification BAM.</span><span class="sxs-lookup"><span data-stu-id="4afb6-129">After you have moved the database, you must update all the references to the new BAM Notification Services databases.</span></span> <span data-ttu-id="4afb6-130">Les références suivantes doivent être mises à jour :</span><span class="sxs-lookup"><span data-stu-id="4afb6-130">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="4afb6-131">Mettre à jour la configuration BAM avec les nouveaux noms de base de données et le serveur.</span><span class="sxs-lookup"><span data-stu-id="4afb6-131">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="4afb6-132">Consultez [pour mettre à jour la configuration BAM](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig).</span><span class="sxs-lookup"><span data-stu-id="4afb6-132">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiUpdateBAMConfig).</span></span>  
  
-   <span data-ttu-id="4afb6-133">Réinscrivez le Service de Notification sur tous les ordinateurs dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.</span><span class="sxs-lookup"><span data-stu-id="4afb6-133">Re-register the Notification Service on all computers in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="4afb6-134">Consultez [inscrire les Services de Notification](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister).</span><span class="sxs-lookup"><span data-stu-id="4afb6-134">See [Register the Notification Services](../technical-guides/how-to-move-the-bam-notification-services-databases1.md#BKMK_NotiRegister).</span></span>  
  
###  <a name="BKMK_NotiUpdateBAMConfig"></a><span data-ttu-id="4afb6-135">Pour mettre à jour la configuration BAM</span><span class="sxs-lookup"><span data-stu-id="4afb6-135">To update the BAM configuration</span></span>  
  
1.  <span data-ttu-id="4afb6-136">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="4afb6-136">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="4afb6-137">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4afb6-137">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="4afb6-138">Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="4afb6-138">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
        -   <span data-ttu-id="4afb6-139">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="4afb6-139">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="4afb6-140">**% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="4afb6-140">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
        -   <span data-ttu-id="4afb6-141">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="4afb6-141">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="4afb6-142">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="4afb6-142">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    3.  <span data-ttu-id="4afb6-143">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="4afb6-143">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="4afb6-144">**BM.exe get-config –filename:BAMConfiguration.xml-server :\<nom_serveur\> -base de données :\<base de données\>**</span><span class="sxs-lookup"><span data-stu-id="4afb6-144">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername\> -database:\<database\>**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="4afb6-145">Lorsque vous exécutez cette commande, remplacez le nom actuel du serveur à partir duquel obtenir les informations de configuration pour <servername> et remplacez-le par le nom réel de la base de données à partir duquel obtenir les informations de configuration <database>.</span><span class="sxs-lookup"><span data-stu-id="4afb6-145">When running this command, substitute the actual name of the server from which to get the configuration information for <servername> and substitute the actual name of the database from which to get the configuration information for <database>.</span></span> <span data-ttu-id="4afb6-146">Pour plus d’informations sur l’utilisation de l’utilitaire de gestion BAM (BM), consultez [Infrastructure de gestion des commandes](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="4afb6-146">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2.  <span data-ttu-id="4afb6-147">Modifiez le fichier BAMConfiguration.xml et définissez la **DBServer** propriétés dans la `<DeploymentUnit Name="Alert">` section pour le nouveau nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="4afb6-147">Edit the BAMConfiguration.xml file and change the **DBServer** properties in the `<DeploymentUnit Name="Alert">` section to the new server name.</span></span>  
  
3.  <span data-ttu-id="4afb6-148">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="4afb6-148">Save and close the BAMConfiguration.xml file.</span></span>  
  
4.  <span data-ttu-id="4afb6-149">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4afb6-149">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="4afb6-150">Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="4afb6-150">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="4afb6-151">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="4afb6-151">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="4afb6-152">**% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="4afb6-152">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    -   <span data-ttu-id="4afb6-153">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="4afb6-153">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="4afb6-154">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="4afb6-154">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6.  <span data-ttu-id="4afb6-155">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="4afb6-155">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="4afb6-156">**BM.exe update-config-FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="4afb6-156">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <a name="BKMK_NotiRegister"></a><span data-ttu-id="4afb6-157">Inscrire les Services de Notification</span><span class="sxs-lookup"><span data-stu-id="4afb6-157">Register the Notification Services</span></span>  
 <span data-ttu-id="4afb6-158">Une fois que vous avez déplacé la base de données des Services de Notification BAM, vous devez réenregistrer le Service de Notification sur tous les ordinateurs qui exécutent les Services de Notification (NSservice.exe) dans le groupe BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="4afb6-158">After you have moved the BAM Notification Services database, you must re-register the Notification Service on all computers in the BizTalk Server group that are running Notification Services (NSservice.exe).</span></span> <span data-ttu-id="4afb6-159">Cela permet aux services de notification de se connecter aux bases de données dans leur nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="4afb6-159">This enables Notification Services to connect to the databases in their new location.</span></span> <span data-ttu-id="4afb6-160">Pour obtenir des instructions sur la façon d’inscrire les Services de Notification, suivez les étapes 5 à 11 à [comment la mise à jour des références aux bases de données Services de Notification BAM](http://go.microsoft.com/fwlink/?LinkId=156684) (http://go.microsoft.com/fwlink/?LinkId=156684) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="4afb6-160">For instructions on how to register the Notification Services, follow steps 5 through 11 at [How to Update References to the BAM Notification Services Databases](http://go.microsoft.com/fwlink/?LinkId=156684) (http://go.microsoft.com/fwlink/?LinkId=156684) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="4afb6-161">Notez les points suivants lors de l’exécution des étapes indiquées dans le lien précédent :</span><span class="sxs-lookup"><span data-stu-id="4afb6-161">Note the following while performing steps mentioned in the preceding link:</span></span>  
  
-   <span data-ttu-id="4afb6-162">Les étapes 5 et 6 dans le lien précédent doivent être effectuées sur les serveurs répertoriés dans le fichier XML de configuration BAM pour les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4afb6-162">Steps 5 and 6 in the preceding link must be performed on the servers listed in the BAM configuration XML for the following properties:</span></span>  
  
    ```  
    <DeploymentUnit Name="Alert">  
      <Property Name="GeneratorServerName">Server_Name</Property>  
      <Property Name="ProviderServerName">Server_Name</Property>  
      <Property Name="DistributorServerName">Server_Name</Property>  
    </DeploymentUnit>  
  
    ```  
  
-   <span data-ttu-id="4afb6-163">Étape 7 à 11 doit être effectuée sur l’ordinateur qui héberge le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="4afb6-163">Step 7 through 11 must be performed on the computer that hosts the BAM portal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4afb6-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4afb6-164">See Also</span></span>  
 [<span data-ttu-id="4afb6-165">Déplacement de bases de données</span><span class="sxs-lookup"><span data-stu-id="4afb6-165">Moving Databases</span></span>](../technical-guides/moving-databases.md)