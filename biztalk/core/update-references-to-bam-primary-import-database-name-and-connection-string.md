---
title: "Comment mettre à jour les références au nom de base de données d’importation principale BAM et de la chaîne de connexion | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring [BAM], connection strings
- Primary Import database [BAM], updating references
- connection strings, restoring
- connection strings, BAM
- restoring, BAM
- restoring [BAM], Primary Import database
- restoring [BAM], updating references
- Primary Import database [BAM], restoring
- BAM, restoring
- restoring, connection strings
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23efa3df9c59732c8459018a886f7f499d268eff
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-references-to-the-bam-primary-import-database-name-and-connection-string"></a><span data-ttu-id="8726e-102">Mise à jour des références au nom de la base de données d'importation principale BAM et à la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="8726e-102">How to Update References to the BAM Primary Import Database Name and Connection String</span></span>
<span data-ttu-id="8726e-103">Si vous avez sauvegardé votre base de données BAMPrimaryImport, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.</span><span class="sxs-lookup"><span data-stu-id="8726e-103">If you backed up your BAMPrimaryImport database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.</span></span>  
  
 <span data-ttu-id="8726e-104">Le service Bus d'événements BAM déplace les données d'événements de la base de données MessageBox vers la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="8726e-104">The BAM Event Bus service moves event data from the MessageBox database to the BAMPrimaryImport database.</span></span> <span data-ttu-id="8726e-105">Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-105">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span> <span data-ttu-id="8726e-106">Pour plus d’informations sur le service Bus d’événements BAM, consultez [gestion Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md).</span><span class="sxs-lookup"><span data-stu-id="8726e-106">For more information about the BAM Event Bus service, see [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md).</span></span>  
  
 <span data-ttu-id="8726e-107">Pour restaurer la base de données, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8726e-107">To restore the BAMPrimaryImport database, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="8726e-108">Vous devez en outre suivre les étapes générales suivantes, qui sont suivies d'une procédure qui les décrit en détails :</span><span class="sxs-lookup"><span data-stu-id="8726e-108">In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:</span></span>  
  
-   <span data-ttu-id="8726e-109">Mettez à jour la connexion 1 SQL dans tous les lots DTS BAM pour faire référence au nouveau nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-109">Update the SQL Connection 1 in all BAM DTS packages to refer to the new database name.</span></span>  
  
-   <span data-ttu-id="8726e-110">Mettez à jour le fichier web.config avec le nouveau nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-110">Update the web.config file with the new database name.</span></span>  
  
-   <span data-ttu-id="8726e-111">Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM.</span><span class="sxs-lookup"><span data-stu-id="8726e-111">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8726e-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8726e-112">Prerequisites</span></span>  
 <span data-ttu-id="8726e-113">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8726e-113">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-bamprimaryimport-database-name-and-connection-string"></a><span data-ttu-id="8726e-114">Pour mettre à jour les références au nom et à la chaîne de connexion de la base de données BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="8726e-114">To update references to the BAMPrimaryImport database name and connection string</span></span>  
  
1.  <span data-ttu-id="8726e-115">Arrêtez toute mise à jour du cube d'analyse BAM et tout lot DTS (Data Transformation Services), ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="8726e-115">Stop any BAM cube update and data maintenance Data Transformation Services (DTS) packages, or prevent them from running until you have restored the BAMPrimaryImport database.</span></span>  
  
2.  <span data-ttu-id="8726e-116">Arrêtez le service de l'application BizTalk (y compris le service Bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-116">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.</span></span>  
  
    1.  <span data-ttu-id="8726e-117">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="8726e-117">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="8726e-118">Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="8726e-118">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.</span></span>  
  
3.  <span data-ttu-id="8726e-119">Restaurer la base de données, effectuez les opérations dans [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8726e-119">Restore the BAMPrimaryImport database, performing the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span>  
  
4.  <span data-ttu-id="8726e-120">Mettez à jour les fichiers Web.Config suivants :</span><span class="sxs-lookup"><span data-stu-id="8726e-120">Update the following Web.Config files:</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8726e-121">BAMPortal\BamManagementService\Web.Config.</span><span class="sxs-lookup"><span data-stu-id="8726e-121">BAMPortal\BamManagementService\Web.Config.</span></span>  
  
         <span data-ttu-id="8726e-122">Remplacez le  *\<nom_serveur\>*  de chaîne avec le nouveau nom de serveur et  *\<DatabaseName\>*  avec le nouveau nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-122">Replace the *\<ServerName\>* string with the new server name and *\<DatabaseName\>* with the new database name.</span></span> <span data-ttu-id="8726e-123">Mettez à jour les chaînes de connexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="8726e-123">Update the following connection strings:</span></span>  
  
         <span data-ttu-id="8726e-124">\<appSettings\></span><span class="sxs-lookup"><span data-stu-id="8726e-124">\<appSettings\></span></span>  
  
         <span data-ttu-id="8726e-125">< ajouter la clé = valeur de « BamServer » = «*\<nom_serveur\>*"/\></span><span class="sxs-lookup"><span data-stu-id="8726e-125"><add key="BamServer" value="*\<ServerName\>*" /\></span></span>  
  
         <span data-ttu-id="8726e-126">< Ajouter clé = valeur de « BamDatabase » = «*\<DatabaseName\>*"/\></span><span class="sxs-lookup"><span data-stu-id="8726e-126"><add key="BamDatabase" value="*\<DatabaseName\>*" /\></span></span>  
  
         <span data-ttu-id="8726e-127">\<ajouter la clé = valeur de « MaxResultRows » = « 2000 » /\></span><span class="sxs-lookup"><span data-stu-id="8726e-127">\<add key="MaxResultRows" value="2000" /\></span></span>  
  
         <span data-ttu-id="8726e-128">\</appSettings\></span><span class="sxs-lookup"><span data-stu-id="8726e-128">\</appSettings\></span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8726e-129">BAMPortal\BamQueryService\Web.Config.</span><span class="sxs-lookup"><span data-stu-id="8726e-129">BAMPortal\BamQueryService\Web.Config.</span></span>  
  
         <span data-ttu-id="8726e-130">Remplacez le  *\<nom_serveur\>*  de chaîne avec le nouveau nom de serveur et  *\<DatabaseName\>*  avec le nouveau nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-130">Replace the *\<ServerName\>* string with the new server name and *\<DatabaseName\>* with the new database name.</span></span> <span data-ttu-id="8726e-131">Mettez à jour les chaînes de connexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="8726e-131">Update the following connection strings:</span></span>  
  
         <span data-ttu-id="8726e-132">\<appSettings\></span><span class="sxs-lookup"><span data-stu-id="8726e-132">\<appSettings\></span></span>  
  
         <span data-ttu-id="8726e-133">\<ajouter la clé = valeur de « BamServer » = «*\<nom_serveur\>*"/\></span><span class="sxs-lookup"><span data-stu-id="8726e-133">\<add key="BamServer" value="*\<ServerName\>*" /\></span></span>  
  
         <span data-ttu-id="8726e-134">\<ajouter la clé = valeur de « BamDatabase » = «*\<DatabaseName\>*"/\></span><span class="sxs-lookup"><span data-stu-id="8726e-134">\<add key="BamDatabase" value="*\<DatabaseName\>*" /\></span></span>  
  
         <span data-ttu-id="8726e-135">\<ajouter la clé = valeur de « MaxResultRows » = « 2000 » /\></span><span class="sxs-lookup"><span data-stu-id="8726e-135">\<add key="MaxResultRows" value="2000" /\></span></span>  
  
         <span data-ttu-id="8726e-136">\</appSettings\></span><span class="sxs-lookup"><span data-stu-id="8726e-136">\</appSettings\></span></span>  
  
5.  <span data-ttu-id="8726e-137">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8726e-137">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="8726e-138">Accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.</span><span class="sxs-lookup"><span data-stu-id="8726e-138">Navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.</span></span>  
  
7.  <span data-ttu-id="8726e-139">Avec le bouton droit **SampleUpdateInfo.xml**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="8726e-139">Right-click **SampleUpdateInfo.xml**, and then click **Edit**.</span></span>  
  
    1.  <span data-ttu-id="8726e-140">Ajoutez des marques de commentaire à toutes les sections de la base de données, à l'exception de BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert.</span><span class="sxs-lookup"><span data-stu-id="8726e-140">Comment out all of the database sections except for the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.</span></span>  
  
    2.  <span data-ttu-id="8726e-141">Pour le BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et les alertes sections, définissez la **« SourceServer »** et **« Serveur de Destination »**  au nom du serveur où se trouvent les bases de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-141">For the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the **"SourceServer"** and **"Destination Server"** to the name of the existing server where those databases reside.</span></span>  
  
    3.  <span data-ttu-id="8726e-142">Pour PrimaryImportDatabase, définissez le **« SourceServer »** au nom du serveur où vous avez déplacé la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="8726e-142">For PrimaryImportDatabase, set the **"SourceServer"** to the name of the server where you have moved the BAM Primary Import database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="8726e-143">Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.</span><span class="sxs-lookup"><span data-stu-id="8726e-143">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="8726e-144">Si vous avez renommé les bases de données BizTalk Server, vous devez également mettre à jour comme il se doit les noms des bases de données.</span><span class="sxs-lookup"><span data-stu-id="8726e-144">If you renamed any of the BizTalk Server databases, you must also update the database names as appropriate.</span></span>  
  
    4.  <span data-ttu-id="8726e-145">Lorsque vous avez terminé la modification du fichier, enregistrez-le et fermez-le.</span><span class="sxs-lookup"><span data-stu-id="8726e-145">When you are finished editing the file, save it and exit.</span></span>  
  
8.  <span data-ttu-id="8726e-146">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="8726e-146">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="8726e-147">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="8726e-147">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8726e-148">Vous devez exécuter UpdateDatabase.vbs une seule fois.</span><span class="sxs-lookup"><span data-stu-id="8726e-148">You only need to run UpdateDatabase.vbs once.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8726e-149">Sur les ordinateurs 64 bits, vous devez exécuter UpdateDatabase.vbs à partir d'une invite de commandes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="8726e-149">On 64-bit computers, you must run UpdateDatabase.vbs from a 64-bit command prompt.</span></span>  
  
9. <span data-ttu-id="8726e-150">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="8726e-150">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="8726e-151">Tracking</span><span class="sxs-lookup"><span data-stu-id="8726e-151">Tracking</span></span>  
  
10. <span data-ttu-id="8726e-152">À l'invite de commandes, modifiez bm.exe.config, remplacez la valeur de key="DefaultServer" par le nouveau nom du serveur, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="8726e-152">At the command prompt, edit bm.exe.config, change the value of key="DefaultServer" to the new server name, and then save the file.</span></span>  
  
11. <span data-ttu-id="8726e-153">Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM.</span><span class="sxs-lookup"><span data-stu-id="8726e-153">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="8726e-154">Pour chaque fichier :</span><span class="sxs-lookup"><span data-stu-id="8726e-154">For each file:</span></span>  
  
    1.  <span data-ttu-id="8726e-155">Ouvrez le fichier Excel de données actives.</span><span class="sxs-lookup"><span data-stu-id="8726e-155">Open the Excel live data file.</span></span> <span data-ttu-id="8726e-156">Le nom de fichier se termine par _LiveData.xls.</span><span class="sxs-lookup"><span data-stu-id="8726e-156">The file name ends with _LiveData.xls.</span></span>  
  
    2.  <span data-ttu-id="8726e-157">Sur le **BAM** menu, cliquez sur **connexion DB BAM**.</span><span class="sxs-lookup"><span data-stu-id="8726e-157">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
    3.  <span data-ttu-id="8726e-158">Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez la base de données SQL Server et BAMPrimaryImport, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8726e-158">In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="8726e-159">Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.</span><span class="sxs-lookup"><span data-stu-id="8726e-159">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
    5.  <span data-ttu-id="8726e-160">Dans le menu **Fichier** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="8726e-160">On the **File** menu, click **Save**.</span></span>  
  
12. <span data-ttu-id="8726e-161">Redémarrez le service de l'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8726e-161">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="8726e-162">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="8726e-162">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="8726e-163">Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="8726e-163">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.</span></span>  
  
13. <span data-ttu-id="8726e-164">Activez les mises à jour du cube d'analyse BAM et les lots DTS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="8726e-164">Enable any BAM cube update and data maintenance DTS packages.</span></span>  
  
14. <span data-ttu-id="8726e-165">Pour résoudre toutes les instances de suivi incomplètes, consultez [comment résoudre les Instances d’activité incomplètes](../core/how-to-resolve-incomplete-activity-instances.md).</span><span class="sxs-lookup"><span data-stu-id="8726e-165">To resolve any incomplete trace instances, see [How to Resolve Incomplete Activity Instances](../core/how-to-resolve-incomplete-activity-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8726e-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8726e-166">See Also</span></span>  
 [<span data-ttu-id="8726e-167">Sauvegarde et restauration de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="8726e-167">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)