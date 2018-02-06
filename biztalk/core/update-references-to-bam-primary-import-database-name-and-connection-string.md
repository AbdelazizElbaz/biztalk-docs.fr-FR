---
title: "Mettre à jour la chaîne de nom et une connexion de base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 02/01/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c58db0-f14f-429a-813c-bae29f6950d3
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91792b66fa82be633123501f651d9a34784915ce
ms.sourcegitcommit: c670558deccec266f90ae7ed042dba1105b15596
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="update-references-to-the-bam-primary-import-database-name-and-connection-string"></a><span data-ttu-id="ec096-102">Mettre à jour les références au nom de base de données d’importation principale BAM et de la chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="ec096-102">Update References to the BAM Primary Import Database Name and Connection String</span></span>
<span data-ttu-id="ec096-103">Si vous avez sauvegardé votre base de données BAMPrimaryImport, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.</span><span class="sxs-lookup"><span data-stu-id="ec096-103">If you backed up your BAMPrimaryImport database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.</span></span>  
  
 <span data-ttu-id="ec096-104">Le service Bus d'événements BAM déplace les données d'événements de la base de données MessageBox vers la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="ec096-104">The BAM Event Bus service moves event data from the MessageBox database to the BAMPrimaryImport database.</span></span> <span data-ttu-id="ec096-105">Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-105">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span> <span data-ttu-id="ec096-106">Pour plus d’informations sur le service Bus d’événements BAM, consultez [gestion Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md).</span><span class="sxs-lookup"><span data-stu-id="ec096-106">For more information about the BAM Event Bus service, see [Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md).</span></span>  
  
 <span data-ttu-id="ec096-107">Pour restaurer la base de données, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="ec096-107">To restore the BAMPrimaryImport database, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="ec096-108">Vous devez en outre suivre les étapes générales suivantes, qui sont suivies d'une procédure qui les décrit en détails :</span><span class="sxs-lookup"><span data-stu-id="ec096-108">In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:</span></span>  
  
-   <span data-ttu-id="ec096-109">Mettez à jour la connexion 1 SQL dans tous les lots DTS BAM pour faire référence au nouveau nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-109">Update the SQL Connection 1 in all BAM DTS packages to refer to the new database name.</span></span>  
  
-   <span data-ttu-id="ec096-110">Mettez à jour le fichier web.config avec le nouveau nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-110">Update the web.config file with the new database name.</span></span>  
  
-   <span data-ttu-id="ec096-111">Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM.</span><span class="sxs-lookup"><span data-stu-id="ec096-111">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ec096-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ec096-112">Prerequisites</span></span>  
<span data-ttu-id="ec096-113">Connectez-vous en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="ec096-113">Sign in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="update-the-references"></a><span data-ttu-id="ec096-114">Mettre à jour les références</span><span class="sxs-lookup"><span data-stu-id="ec096-114">Update the references</span></span>  
  
1.  <span data-ttu-id="ec096-115">Arrêtez toute mise à jour du cube d'analyse BAM et tout lot DTS (Data Transformation Services), ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="ec096-115">Stop any BAM cube update and data maintenance Data Transformation Services (DTS) packages, or prevent them from running until you have restored the BAMPrimaryImport database.</span></span>  
  
2.  <span data-ttu-id="ec096-116">Arrêtez le service de l'application BizTalk (y compris le service Bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-116">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.</span></span>  
  
    1.  <span data-ttu-id="ec096-117">À partir de la **Démarrer** menu, tapez **services.msc**, puis ouvrez **Services**.</span><span class="sxs-lookup"><span data-stu-id="ec096-117">From the **Start** menu, type **services.msc**, and open **Services**.</span></span>  
  
    2.  <span data-ttu-id="ec096-118">Avec le bouton droit le **groupe BizTalk des services BizTalk : BizTalkServerApplication** service, puis **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="ec096-118">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service, and then **Stop**.</span></span>  
  
3.  <span data-ttu-id="ec096-119">Restaurer la base de données (les étapes [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md)).</span><span class="sxs-lookup"><span data-stu-id="ec096-119">Restore the BAMPrimaryImport database (steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md)).</span></span>  
  
4.  <span data-ttu-id="ec096-120">Mettez à jour les fichiers Web.Config suivants :</span><span class="sxs-lookup"><span data-stu-id="ec096-120">Update the following Web.Config files:</span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="ec096-121">\BAMPortal\BamManagementService\Web.Config.</span><span class="sxs-lookup"><span data-stu-id="ec096-121">\BAMPortal\BamManagementService\Web.Config.</span></span>  
  
         <span data-ttu-id="ec096-122">Remplacez le  *\<nom_serveur\>*  avec le nouveau nom de serveur, de chaîne et  *\<DatabaseName\>*  avec le nouveau nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-122">Replace the *\<ServerName\>* string with the new server name, and *\<DatabaseName\>* with the new database name.</span></span> <span data-ttu-id="ec096-123">Mettez à jour les chaînes de connexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec096-123">Update the following connection strings:</span></span>  
  
         <span data-ttu-id="ec096-124">\<appSettings\></span><span class="sxs-lookup"><span data-stu-id="ec096-124">\<appSettings\></span></span>  
  
         <span data-ttu-id="ec096-125"><add key="BamServer" value="*\<ServerName\>*" /\></span><span class="sxs-lookup"><span data-stu-id="ec096-125"><add key="BamServer" value="*\<ServerName\>*" /\></span></span>  
  
         <span data-ttu-id="ec096-126"><add key="BamDatabase" value="*\<DatabaseName\>*" /\></span><span class="sxs-lookup"><span data-stu-id="ec096-126"><add key="BamDatabase" value="*\<DatabaseName\>*" /\></span></span>  
  
         <span data-ttu-id="ec096-127">\<add key="MaxResultRows" value="2000" /\></span><span class="sxs-lookup"><span data-stu-id="ec096-127">\<add key="MaxResultRows" value="2000" /\></span></span>  
  
         <span data-ttu-id="ec096-128">\</appSettings\></span><span class="sxs-lookup"><span data-stu-id="ec096-128">\</appSettings\></span></span>  
  
    -   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="ec096-129">\BAMPortal\BamQueryService\Web.Config.</span><span class="sxs-lookup"><span data-stu-id="ec096-129">\BAMPortal\BamQueryService\Web.Config.</span></span>  
  
         <span data-ttu-id="ec096-130">Remplacez le  *\<nom_serveur\>*  de chaîne avec le nouveau nom de serveur et  *\<DatabaseName\>*  avec le nouveau nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-130">Replace the *\<ServerName\>* string with the new server name and *\<DatabaseName\>* with the new database name.</span></span> <span data-ttu-id="ec096-131">Mettez à jour les chaînes de connexion suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec096-131">Update the following connection strings:</span></span>  
  
         <span data-ttu-id="ec096-132">\<appSettings\></span><span class="sxs-lookup"><span data-stu-id="ec096-132">\<appSettings\></span></span>  
  
         <span data-ttu-id="ec096-133">\<add key="BamServer" value="*\<ServerName\>*" /\></span><span class="sxs-lookup"><span data-stu-id="ec096-133">\<add key="BamServer" value="*\<ServerName\>*" /\></span></span>  
  
         <span data-ttu-id="ec096-134">\<add key="BamDatabase" value="*\<DatabaseName\>*" /\></span><span class="sxs-lookup"><span data-stu-id="ec096-134">\<add key="BamDatabase" value="*\<DatabaseName\>*" /\></span></span>  
  
         <span data-ttu-id="ec096-135">\<add key="MaxResultRows" value="2000" /\></span><span class="sxs-lookup"><span data-stu-id="ec096-135">\<add key="MaxResultRows" value="2000" /\></span></span>  
  
         <span data-ttu-id="ec096-136">\</appSettings\></span><span class="sxs-lookup"><span data-stu-id="ec096-136">\</appSettings\></span></span>  
  
5.  <span data-ttu-id="ec096-137">Ouvrez une invite de commandes (menu Démarrer > invite de commandes), puis accédez au répertoire suivant : [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Schema\Restore.</span><span class="sxs-lookup"><span data-stu-id="ec096-137">Open a command prompt (Start menu > Command Prompt), and navigate to the following directory: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Schema\Restore.</span></span>  
  
6.  <span data-ttu-id="ec096-138">Avec le bouton droit **SampleUpdateInfo.xml**, et **modifier**.</span><span class="sxs-lookup"><span data-stu-id="ec096-138">Right-click **SampleUpdateInfo.xml**, and **Edit**.</span></span>  
  
    1.  <span data-ttu-id="ec096-139">Commentez toutes les sections de la base de données à l’exception de la OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert.</span><span class="sxs-lookup"><span data-stu-id="ec096-139">Comment out all of the database sections except for the  OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.</span></span> 
    2.  <span data-ttu-id="ec096-140">Pour OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert sections, définissez la **SourceServer** et **serveur de Destination** à la nom du serveur où se trouvent les bases de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-140">For the OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the **SourceServer** and **Destination Server** to the name of the existing server where those databases reside.</span></span>  
  
    3.  <span data-ttu-id="ec096-141">Pour PrimaryImportDatabase, définissez le **« SourceServer »** au nom du serveur où vous avez déplacé la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="ec096-141">For PrimaryImportDatabase, set the **"SourceServer"** to the name of the server where you have moved the BAM Primary Import database.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="ec096-142">Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.</span><span class="sxs-lookup"><span data-stu-id="ec096-142">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="ec096-143">Si vous avez renommé une des bases de données BizTalk Server, veillez à mettre à jour les noms de base de données.</span><span class="sxs-lookup"><span data-stu-id="ec096-143">If you renamed any of the BizTalk Server databases, be sure to also update the database names.</span></span>  
  
    4.  <span data-ttu-id="ec096-144">Lorsque vous avez fini de modifier le fichier, enregistrez-le et fermez-le.</span><span class="sxs-lookup"><span data-stu-id="ec096-144">When you are finished editing the file, save it, and exit.</span></span>  
  
7.  <span data-ttu-id="ec096-145">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ec096-145">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="ec096-146">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="ec096-146">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ec096-147">Uniquement exécuter UpdateDatabase.vbs une seule fois.</span><span class="sxs-lookup"><span data-stu-id="ec096-147">Only run UpdateDatabase.vbs once.</span></span>  
    > 
    >  <span data-ttu-id="ec096-148">Sur les ordinateurs 64 bits, exécutez UpdateDatabase.vbs à partir d’une invite de commandes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ec096-148">On 64-bit computers, run UpdateDatabase.vbs from a 64-bit command prompt.</span></span>  
  
8. <span data-ttu-id="ec096-149">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="ec096-149">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="ec096-150">\Tracking</span><span class="sxs-lookup"><span data-stu-id="ec096-150">\Tracking</span></span>  
  
9. <span data-ttu-id="ec096-151">À l'invite de commandes, modifiez bm.exe.config, remplacez la valeur de key="DefaultServer" par le nouveau nom du serveur, puis enregistrez le fichier.</span><span class="sxs-lookup"><span data-stu-id="ec096-151">At the command prompt, edit bm.exe.config, change the value of key="DefaultServer" to the new server name, and then save the file.</span></span>  
  
10. <span data-ttu-id="ec096-152">Mettez à jour la référence à la base de données BAMPrimaryImport dans tous les fichiers Microsoft Excel de données actives BAM.</span><span class="sxs-lookup"><span data-stu-id="ec096-152">Update the reference to BAMPrimaryImport database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="ec096-153">Pour chaque fichier :</span><span class="sxs-lookup"><span data-stu-id="ec096-153">For each file:</span></span>  
  
    1.  <span data-ttu-id="ec096-154">Ouvrez le fichier Excel de données actives.</span><span class="sxs-lookup"><span data-stu-id="ec096-154">Open the Excel live data file.</span></span> <span data-ttu-id="ec096-155">Le nom de fichier se termine par _LiveData.xls.</span><span class="sxs-lookup"><span data-stu-id="ec096-155">The file name ends with _LiveData.xls.</span></span>  
  
    2.  <span data-ttu-id="ec096-156">Sur le **BAM** menu, cliquez sur **connexion DB BAM**.</span><span class="sxs-lookup"><span data-stu-id="ec096-156">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
    3.  <span data-ttu-id="ec096-157">Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez la base de données SQL Server et BAMPrimaryImport, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec096-157">In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="ec096-158">Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.</span><span class="sxs-lookup"><span data-stu-id="ec096-158">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
    5.  <span data-ttu-id="ec096-159">Dans le menu **Fichier** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="ec096-159">On the **File** menu, click **Save**.</span></span>  
  
11. <span data-ttu-id="ec096-160">Redémarrez le service de l'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ec096-160">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="ec096-161">Ouvrez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="ec096-161">Open **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="ec096-162">Avec le bouton droit le **groupe BizTalk des services BizTalk : BizTalkServerApplication** service, puis **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ec096-162">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service, and then **Start**.</span></span>  
  
12. <span data-ttu-id="ec096-163">Activez les mises à jour du cube d'analyse BAM et les lots DTS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="ec096-163">Enable any BAM cube update and data maintenance DTS packages.</span></span>  
  
13. <span data-ttu-id="ec096-164">Pour résoudre toutes les instances de suivi incomplètes, consultez [résoudre les Instances d’activité incomplètes](../core/how-to-resolve-incomplete-activity-instances.md).</span><span class="sxs-lookup"><span data-stu-id="ec096-164">To resolve any incomplete trace instances, see [Resolve Incomplete Activity Instances](../core/how-to-resolve-incomplete-activity-instances.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec096-165">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec096-165">See Also</span></span>  
 [<span data-ttu-id="ec096-166">Sauvegarde et restauration de l’analyse BAM</span><span class="sxs-lookup"><span data-stu-id="ec096-166">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)
