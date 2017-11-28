---
title: "Création d’une vue partitionnée dans la base de données d’archivage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- databases, partitioning
- partitioning
- Archive database [BAM], partitioning
ms.assetid: f9ef7480-2e37-4477-92c8-b5686ae9b54b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f6000c95b94570b5f058073537fa926fd1651c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-partitioned-view-in-the-archiving-database"></a><span data-ttu-id="eba3c-102">Création d'une vue partitionnée dans la base de données d'archivage</span><span class="sxs-lookup"><span data-stu-id="eba3c-102">Creating a Partitioned View in the Archiving Database</span></span>
<span data-ttu-id="eba3c-103">Lorsque vous exécutez le lot de gestion de données BAM (BAM_DM_`<activity name>`NomActivité>), l'analyse BAM copie chaque partition de la base de données d'importation principale BAM dans une table distincte de la base de données des archives BAM.</span><span class="sxs-lookup"><span data-stu-id="eba3c-103">When you run the BAM data maintenance package (BAM_DM_`<activity name>`) BAM copies each partition in the BAM Primary Import database to a separate table in the BAM Archive database.</span></span> <span data-ttu-id="eba3c-104">Si vous détachez la base de données des archives et la rattachez à des fins de requête, il sera difficile de localiser les données pour votre requête.</span><span class="sxs-lookup"><span data-stu-id="eba3c-104">If you detach the archive database and reattach it for querying, it will be difficult to locate the data for your query.</span></span>  
  
 <span data-ttu-id="eba3c-105">Vous pouvez créer des vues partitionnées dans la base de données des archives BAM afin de faciliter la localisation des données.</span><span class="sxs-lookup"><span data-stu-id="eba3c-105">You can create partitioned views in the BAM Archive database to facilitate locating the data.</span></span> <span data-ttu-id="eba3c-106">L'analyse BAM prend en charge jusqu'à 253 partitions.</span><span class="sxs-lookup"><span data-stu-id="eba3c-106">BAM supports up to 253 partitions.</span></span> <span data-ttu-id="eba3c-107">Pour chaque activité, l'analyse BAM génère un lot DTS de gestion de données BAM, qui copie les données d'activité dans la base de données des archives BAM, puis les supprime de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="eba3c-107">For each activity, BAM generates one BAM data maintenance DTS package, which copies the activity data to the BAM Archive database and then removes it from the BAM Primary Import database.</span></span> <span data-ttu-id="eba3c-108">Si la base de données des archives rencontre une défaillance après la copie des données mais avant la prochaine sauvegarde, les données sont perdues.</span><span class="sxs-lookup"><span data-stu-id="eba3c-108">If the archive database fails after the data is copied but before the next backup, data is lost.</span></span>  
  
 <span data-ttu-id="eba3c-109">La solution est d'avoir un lot d'archives unique, qui copie d'abord les anciennes données à partir de toutes les activités, puis sauvegarde la base de données des archives BAM pour supprimer finalement les partitions copiées à partir de la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="eba3c-109">The solution to prevent lost data is to have a single archiving package, which first copies the old data from all activities, then backs up the BAM Archive database, and finally drops the partitions that were copied from the BAM Primary Import database.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="eba3c-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="eba3c-110">Prerequisites</span></span>  
 <span data-ttu-id="eba3c-111">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="eba3c-111">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-create-a-partitioned-view-in-the-bam-archive-database-in-sql-server-2008-sp1-or-sql-server-2008-r2"></a><span data-ttu-id="eba3c-112">Pour créer une vue partitionnée dans la base de données des archives BAM sous SQL Server 2008 SP1 ou SQL Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="eba3c-112">To create a partitioned view in the BAM Archive database in SQL Server 2008 SP1 or SQL Server 2008 R2</span></span>  
  
1.  <span data-ttu-id="eba3c-113">Ouvrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="eba3c-113">Open SQL Server Management Studio.</span></span>  
  
2.  <span data-ttu-id="eba3c-114">Sélectionnez la base de données des archives BAM, puis cliquez sur **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="eba3c-114">Select the BAM Archive database, and then click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eba3c-115">Sur le **requête** menu, pointez sur **résultats** puis cliquez sur **résultats dans du texte**.</span><span class="sxs-lookup"><span data-stu-id="eba3c-115">On the **Query** menu, point to **Results To** and then click **Results to Text**.</span></span>  
  
4.  <span data-ttu-id="eba3c-116">Copiez le script SQL suivant dans le volet de requête.</span><span class="sxs-lookup"><span data-stu-id="eba3c-116">Copy the following SQL script into the query pane.</span></span> <span data-ttu-id="eba3c-117">Remplacez \<nom de l’activité > avec votre nom de l’activité, puis remplacez `<view type>` avec l’option **Instances** afficher pour l’instance ou **relations** pour une vue de relation.</span><span class="sxs-lookup"><span data-stu-id="eba3c-117">Replace \<activity name> with your activity name, and replace `<view type>` with either **Instances** for instance view or **Relationships** for relationship view.</span></span>  
  
    ```  
    set nocount on  
  
    declare @activityName as nvarchar(128)  
    declare @viewType as nvarchar(50)  
    set @activityName = N'<activity name>'-- Substitute your activity name here  
    set @viewType = N'<view type>'-- Substitute the view type here, either "Instances" or "Relationships"  
  
    declare @tableName nvarchar(128)  
    declare @viewName nvarchar(128)  
    declare @isFirstTable bit  
    declare @scriptLine nvarchar(300)  
  
    set @viewName = N'bam_' + @activityName + '_' + @viewType + 'View'  
    select N'SELECT Name FROM sysobjects where name = N''' + @viewName + ''' and type = ''V'''   
     + char(13) + char(10) + 'IF @@ROWCOUNT > 0 DROP VIEW ' + @viewName   
     + char(13) + char(10) + 'GO'  
  
    select 'CREATE VIEW ' +  @viewName + ' AS ' + char(13) + char(10)  
  
    declare instance_cursor cursor local for  
    select name from sysobjects   
    where name like N'bam_' + @activityName + '_' + @viewType + '_%' and type = 'U'  
  
    SET @isFirstTable = 1  
    OPEN instance_cursor  
    FETCH NEXT FROM instance_cursor INTO @tableName  
  
    WHILE @@fetch_status = 0   
    BEGIN  
  
    if @isFirstTable = 1  
    BEGIN  
    SET @scriptLine = N'SELECT * FROM [' + @tableName + ']'  
    SET @isFirstTable = 0  
    END  
    ELSE  
    SET @scriptLine = N'UNION ALL SELECT * FROM [' + @tableName + ']'  
  
    SELECT @scriptLine  
  
    FETCH NEXT FROM instance_cursor INTO @tableName  
    END  
    CLOSE instance_cursor  
    DEALLOCATE instance_cursor  
  
    select 'GO'  
    set nocount off  
    ```  
  
5.  <span data-ttu-id="eba3c-118">exécutez la requête.</span><span class="sxs-lookup"><span data-stu-id="eba3c-118">Execute the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eba3c-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eba3c-119">See Also</span></span>  
 <span data-ttu-id="eba3c-120">[Lots DTS BAM](../core/bam-dts-packages.md) </span><span class="sxs-lookup"><span data-stu-id="eba3c-120">[BAM DTS Packages](../core/bam-dts-packages.md) </span></span>  
 [<span data-ttu-id="eba3c-121">La sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur</span><span class="sxs-lookup"><span data-stu-id="eba3c-121">How to Back Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)