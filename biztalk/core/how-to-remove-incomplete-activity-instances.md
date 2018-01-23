---
title: "Supprimer des Instances d’activité incomplètes | Documents Microsoft"
description: "Exécutez le script RemoveDanglingInstances SQL personnalisé pour supprimer des instances incomplètes à partir de la base de données d’importation principale BAM dans BizTalk Server"
ms.custom: 
ms.date: 01/18/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7060578c-6267-487b-8530-efa18f9431ce
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 542d92b838b1638a2d018c6325d4c40467545c42
ms.sourcegitcommit: 9e7a7dc5544d30d4523c0b3cdaa59f4890e7a4e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="remove-incomplete-activity-instances"></a><span data-ttu-id="3838b-103">Supprimer des Instances d’activité incomplètes</span><span class="sxs-lookup"><span data-stu-id="3838b-103">Remove Incomplete Activity Instances</span></span>
<span data-ttu-id="3838b-104">Lorsqu'un fichier de définition d'analyse BAM est déployé, cinq tables sont créées dans la base de données d'importation principale BAM pour chaque activité définie dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="3838b-104">When a BAM definition file is deployed, five tables are created in the BAM Primary Import database for each activity defined in the definition file.</span></span> <span data-ttu-id="3838b-105">Ces tables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3838b-105">These tables are:</span></span>  
  
-   <span data-ttu-id="3838b-106">bam_`ActivityName`_Active</span><span class="sxs-lookup"><span data-stu-id="3838b-106">bam_`ActivityName`_Active</span></span>  
  
-   <span data-ttu-id="3838b-107">bam_`ActivityName`_Completed</span><span class="sxs-lookup"><span data-stu-id="3838b-107">bam_`ActivityName`_Completed</span></span>  
  
-   <span data-ttu-id="3838b-108">bam_`ActivityName`_ActiveRelationships</span><span class="sxs-lookup"><span data-stu-id="3838b-108">bam_`ActivityName`_ActiveRelationships</span></span>  
  
-   <span data-ttu-id="3838b-109">bam_`ActivityName`_CompletedRelationships</span><span class="sxs-lookup"><span data-stu-id="3838b-109">bam_`ActivityName`_CompletedRelationships</span></span>  
  
-   <span data-ttu-id="3838b-110">bam_`ActivityName`_Continuations</span><span class="sxs-lookup"><span data-stu-id="3838b-110">bam_`ActivityName`_Continuations</span></span>  
  
 <span data-ttu-id="3838b-111">Où `ActivityName` est le nom de l'activité définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3838b-111">Where `ActivityName` is the name of the activity that the user has defined.</span></span>  
  
 <span data-ttu-id="3838b-112">Au cours du fonctionnement normal, les données incomplètes restent dans la table bam_`ActivityName`_Active.</span><span class="sxs-lookup"><span data-stu-id="3838b-112">During normal execution, incomplete data remains in the bam_`ActivityName`_Active table.</span></span> <span data-ttu-id="3838b-113">Si les données ont des relations et des références, puis il seront des données dans l’analyse bam\_`ActivityName`_ActiveRelationships table.</span><span class="sxs-lookup"><span data-stu-id="3838b-113">If the data has relations and references, then there will be data in the bam\_`ActivityName`_ActiveRelationships table.</span></span>  
  
 <span data-ttu-id="3838b-114">Pendant le suivi d'activités qui utilisent des continuations, il peut y avoir des instances dans lesquelles une activité est restée à l'état non terminé dans les bases de données de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="3838b-114">During the tracking of activities that use continuations, there may be instances in which an activity is left in an incomplete state in the BAM databases.</span></span> <span data-ttu-id="3838b-115">Vous pouvez utiliser le script de création des procédures stockées à la fin de cette rubrique pour créer une procédure stockée qui purgera les enregistrements incomplets.</span><span class="sxs-lookup"><span data-stu-id="3838b-115">You can use the stored procedure creation script at the end of this topic to create a stored procedure that will purge the incomplete records.</span></span>  
  
 <span data-ttu-id="3838b-116">Pour créer la procédure stockée, copiez le script et exécutez-le sur la base de données d'importation principale BAM en utilisant SQL Server Management.</span><span class="sxs-lookup"><span data-stu-id="3838b-116">To create the stored procedure, copy the script and execute it against the BAM Primary Import database by using SQL Server Management.</span></span> <span data-ttu-id="3838b-117">Le script va générer une procédure stockée nommée **RemoveDanglingInstances** dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="3838b-117">The script will generate a stored procedure named **RemoveDanglingInstances** in the database.</span></span>  
  
## <a name="create-the-removedanglinginstances-stored-procedure"></a><span data-ttu-id="3838b-118">Créer la procédure stockée de RemoveDanglingInstances</span><span class="sxs-lookup"><span data-stu-id="3838b-118">Create the RemoveDanglingInstances stored procedure</span></span>  
  
1.  <span data-ttu-id="3838b-119">Ouvrez **SQL Server Management Studio**et vous connecter à SQL server.</span><span class="sxs-lookup"><span data-stu-id="3838b-119">Open **SQL Server Management Studio**, and connect to the SQL server.</span></span>
  
2.  <span data-ttu-id="3838b-120">Développez le nom du serveur, **bases de données**, puis sélectionnez la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="3838b-120">Expand the server name, expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
3.  <span data-ttu-id="3838b-121">Cliquez sur **Nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="3838b-121">Click **New Query**.</span></span>  
  
4.  <span data-ttu-id="3838b-122">Copiez le script de création de procédure stockée et collez-le dans le volet de requête.</span><span class="sxs-lookup"><span data-stu-id="3838b-122">Copy the stored procedure creation script, and paste it into the query pane.</span></span>  
  
5.  <span data-ttu-id="3838b-123">**Exécutez** le script.</span><span class="sxs-lookup"><span data-stu-id="3838b-123">**Execute** the script.</span></span> <span data-ttu-id="3838b-124">La procédure stockée résultante peut être affichée dans la liste des procédures stockées en tant que dbo. RemoveDanglingInstances.</span><span class="sxs-lookup"><span data-stu-id="3838b-124">The resulting stored procedure can be viewed in the list of stored procedures as dbo.RemoveDanglingInstances.</span></span>  
  
## <a name="remove-incomplete-activity-instances"></a><span data-ttu-id="3838b-125">Supprimer des instances d’activité incomplètes</span><span class="sxs-lookup"><span data-stu-id="3838b-125">Remove incomplete activity instances</span></span>  
  
1.  <span data-ttu-id="3838b-126">Ouvrez **SQL Server Management Studio**et vous connecter à SQL server.</span><span class="sxs-lookup"><span data-stu-id="3838b-126">Open **SQL Server Management Studio**, and connect to the SQL server.</span></span>
  
2.  <span data-ttu-id="3838b-127">Développez le nom du serveur, **bases de données**, puis sélectionnez la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="3838b-127">Expand the server name, expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
3.  <span data-ttu-id="3838b-128">Cliquez sur **Nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="3838b-128">Click **New Query**.</span></span>  
  
4.  <span data-ttu-id="3838b-129">Dans le volet requête, tapez `exec RemoveDanglingInstances` et les paramètres appropriés pour l’opération de suppression que vous effectuez.</span><span class="sxs-lookup"><span data-stu-id="3838b-129">In the query pane, type `exec RemoveDanglingInstances` and the appropriate parameters for the remove operation you are performing.</span></span> <span data-ttu-id="3838b-130">Par exemple, pour supprimer toutes les instances incomplètes de l’activité de bon de commande, tapez `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`.</span><span class="sxs-lookup"><span data-stu-id="3838b-130">For example, to remove all incomplete instances of the Purchase Order activity, type `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`.</span></span>  
  
5.  <span data-ttu-id="3838b-131">**Exécutez** le script.</span><span class="sxs-lookup"><span data-stu-id="3838b-131">**Execute** the script.</span></span>  
  
## <a name="removedanglinginstances-usage-examples"></a><span data-ttu-id="3838b-132">Exemples d'utilisation de RemoveDanglingInstances</span><span class="sxs-lookup"><span data-stu-id="3838b-132">RemoveDanglingInstances Usage Examples</span></span>  
 <span data-ttu-id="3838b-133">La procédure stockée peut recevoir quatre paramètres :</span><span class="sxs-lookup"><span data-stu-id="3838b-133">The stored procedure can receive four parameters:</span></span>  
  
|<span data-ttu-id="3838b-134">Paramètre</span><span class="sxs-lookup"><span data-stu-id="3838b-134">Parameter</span></span>|<span data-ttu-id="3838b-135"> Description</span><span class="sxs-lookup"><span data-stu-id="3838b-135">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3838b-136">@ActivityName nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="3838b-136">@ActivityName nvarchar(128)</span></span>|<span data-ttu-id="3838b-137">Spécifie le nom de l'instance d'activité incomplète à supprimer.</span><span class="sxs-lookup"><span data-stu-id="3838b-137">Specifies the name of the incomplete activity instance to remove.</span></span>|  
|<span data-ttu-id="3838b-138">@ActivityId nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="3838b-138">@ActivityId nvarchar(128)</span></span>|<span data-ttu-id="3838b-139">(Facultatif) Spécifie que la procédure stockée doit supprimer uniquement l'instance en suspens portant l'identificateur d'instance indiqué.</span><span class="sxs-lookup"><span data-stu-id="3838b-139">(Optional) Specifies that the stored procedure remove only the dangling instance with the specified instance identifier.</span></span>|  
|<span data-ttu-id="3838b-140">@DateThresholddate/heure</span><span class="sxs-lookup"><span data-stu-id="3838b-140">@DateThreshold datetime</span></span>|<span data-ttu-id="3838b-141">(Facultatif) Spécifie que les instances de tous les actifs de la table active antérieures (non égal à et plus anciennes et plus que des anciennes) à la date donnée sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="3838b-141">(Optional) Specifies that all the active instances in the active table that are older (not equal to and older, only older) than the given date are removed.</span></span>|  
|<span data-ttu-id="3838b-142">@NewTableExtensionnvarchar (30)</span><span class="sxs-lookup"><span data-stu-id="3838b-142">@NewTableExtension nvarchar(30)</span></span>|<span data-ttu-id="3838b-143">(Facultatif) Spécifie que la procédure stockée crée de nouvelles tables en concaténant l'extension fournie et le nom des tables d'activités existantes.</span><span class="sxs-lookup"><span data-stu-id="3838b-143">(Optional) Specifies that the stored procedure creates three new tables by concatenating the supplied extension to the existing activity tables.</span></span><br /><br /> <span data-ttu-id="3838b-144">Les tables résultantes seront les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3838b-144">The resulting tables will be:</span></span><br /><br /> <span data-ttu-id="3838b-145">bam_ActivityName_Active_\<Extension\></span><span class="sxs-lookup"><span data-stu-id="3838b-145">bam_ActivityName_Active_\<Extension\></span></span><br /><br /> <span data-ttu-id="3838b-146">bam_ActivityName_ActiveRelationships_\<Extension\></span><span class="sxs-lookup"><span data-stu-id="3838b-146">bam_ActivityName_ActiveRelationships_\<Extension\></span></span><br /><br /> <span data-ttu-id="3838b-147">bam_ActivityName_Continuations_\<Extension\></span><span class="sxs-lookup"><span data-stu-id="3838b-147">bam_ActivityName_Continuations_\<Extension\></span></span><br /><br /> <span data-ttu-id="3838b-148">Les instances incomplètes sont déplacées vers les nouvelles tables au lieu d'être purgées de la base de données.</span><span class="sxs-lookup"><span data-stu-id="3838b-148">The incomplete instances are moved to the new tables rather than being purged from the database.</span></span><br /><br /> <span data-ttu-id="3838b-149">Si les tables existent déjà, la procédure stockée les réutilise ; sinon, elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="3838b-149">If the tables already exist, the stored procedure reuses them; otherwise they are created.</span></span> <span data-ttu-id="3838b-150">**Important :** si les tables existent déjà, la procédure stockée suppose que leurs schémas correspondent à ceux qui serait utilisé si elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="3838b-150">**Important:**  If the tables already exist, the stored procedure assumes that their schemas match the ones that would be used if they were created.</span></span> <span data-ttu-id="3838b-151">Si un schéma ne correspond pas, la procédure stockée ne pourra pas insérer les enregistrements et l'opération de suppression échouera.</span><span class="sxs-lookup"><span data-stu-id="3838b-151">If a schema does not match, the stored procedure will fail to insert the records and the remove operation will fail.</span></span>|  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`  
  
 <span data-ttu-id="3838b-152">Supprime toutes les instances actives de l'activité 'PurchaseOrder' dans les tables actives, relations actives et continuations.</span><span class="sxs-lookup"><span data-stu-id="3838b-152">Removes all active instances of the 'PurchaseOrder' activity in the active, active relationships, and continuations tables.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567'`  
  
 <span data-ttu-id="3838b-153">Supprime uniquement l'instance d'activité portant l'ID d'activité 'PO220567' dans les tables actives, relations actives et continuations pour l'activité 'PurchaseOrder'.</span><span class="sxs-lookup"><span data-stu-id="3838b-153">Removes only the activity instance that has an Activity ID of 'PO220567' from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 <span data-ttu-id="3838b-154">Supprime toutes les instances d'activité dont l'heure de dernière modification (LastModified) est antérieure au 2 février 2005 19:27:03.533 dans les tables actives, relations actives et continuations pour l'activité </span><span class="sxs-lookup"><span data-stu-id="3838b-154">Removes all the activity instances that have a LastModified time that is older than Feb 2nd, 2005 7:27:03.533 PM from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 <span data-ttu-id="3838b-155">Supprime l'instance d'activité dont l'ID d'activité est PO220567 uniquement si la valeur de la colonne LastModified est antérieure au 2 février 2005 19:27:03.533.</span><span class="sxs-lookup"><span data-stu-id="3838b-155">Removes the activity instance whose activity ID is PO220567 only if its LastModified column is older than Feb 2nd, 2005 7:27:03.533 PM.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533', @NewTableExtension=N'Dangling'`  
  
 <span data-ttu-id="3838b-156">Crée les tables suivantes dans la base de données :</span><span class="sxs-lookup"><span data-stu-id="3838b-156">Creates the following tables in the database:</span></span>  
  
 <span data-ttu-id="3838b-157">bam_PurchaseOrder_Active_Dangling</span><span class="sxs-lookup"><span data-stu-id="3838b-157">bam_PurchaseOrder_Active_Dangling</span></span>  
  
 <span data-ttu-id="3838b-158">bam_PurchaseOrder_ActiveRelationships_Dangling</span><span class="sxs-lookup"><span data-stu-id="3838b-158">bam_PurchaseOrder_ActiveRelationships_Dangling</span></span>  
  
 <span data-ttu-id="3838b-159">bam_PurchaseOrder_Continuations_Dangling</span><span class="sxs-lookup"><span data-stu-id="3838b-159">bam_PurchaseOrder_Continuations_Dangling</span></span>  
  
 <span data-ttu-id="3838b-160">La procédure stockée copie toutes les instances d'activité incomplètes antérieures au 2 février 2005 19:27:03.533 dans les tables actives, relations actives et continuations pour l'activité 'PurchaseOrder', et les insère dans les tables nouvellement créées </span><span class="sxs-lookup"><span data-stu-id="3838b-160">The stored procedure copies all incomplete activity instances that are older than Feb 2nd, 2005 7:27:03.533 PM from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity, and inserts them into the newly created tables.</span></span> <span data-ttu-id="3838b-161">Les instances d'activité copiées sont ensuite supprimées des tables actives, relations actives et continuations.</span><span class="sxs-lookup"><span data-stu-id="3838b-161">The copied activity instances are then removed from the active, active relationships, and continuations tables.</span></span>  
  
## <a name="stored-procedure-creation-script"></a><span data-ttu-id="3838b-162">Script de création de la procédure stockée</span><span class="sxs-lookup"><span data-stu-id="3838b-162">Stored Procedure Creation Script</span></span>  
  
```  
EXEC sp_stored_procedures @sp_name = 'RemoveDanglingInstances'  
IF @@ROWCOUNT > 0 DROP PROCEDURE RemoveDanglingInstances  
GO  
  
CREATE PROCEDURE RemoveDanglingInstances  
    @ActivityName nvarchar(128),  
    @ActivityId nvarchar(128) = NULL,  
    @DateThreshold datetime = NULL,  
    @NewTableExtension nvarchar(30) = NULL  
AS  
    DECLARE @QueryString nvarchar(4000)  
    DECLARE @ActiveTableName sysname  
    DECLARE @ActiveRelationshipsTableName sysname  
    DECLARE @ContinuationsTableName sysname  
    DECLARE @DanglingActiveTableName sysname  
    DECLARE @DanglingActiveRelationshipsTableName sysname  
    DECLARE @DanglingContinuationsTableName sysname  
  
    SET @ActiveTableName = 'bam_' + @ActivityName + '_Active'  
    SET @ActiveRelationshipsTableName = 'bam_' + @ActivityName + '_ActiveRelationships'  
    SET @ContinuationsTableName = 'bam_' + @ActivityName + '_Continuations'  
  
    SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
    BEGIN TRAN  
  
    DECLARE @LockActivity nvarchar(128)  
    SELECT @LockActivity = ActivityName  
    FROM bam_Metadata_Activities WITH (XLOCK)  
    WHERE ActivityName = @ActivityName  
  
    EXEC sp_tables @table_name = #DanglingActivities  
    IF @@ROWCOUNT > 0 DROP TABLE #DanglingActivities  
  
    CREATE TABLE #DanglingActivities(ActivityID nvarchar(128) PRIMARY KEY)  
  
    SET @QueryString = N'INSERT INTO #DanglingActivities (ActivityID) SELECT ActivityID FROM [bam_' + @ActivityName + '_Active]'  
  
    IF (@DateThreshold is not NULL) OR (@ActivityId is not NULL)  
    BEGIN  
        SET @QueryString = @QueryString + ' WHERE'  
    END  
  
    IF (@DateThreshold is not NULL)  
    BEGIN  
        SET @QueryString = @QueryString + ' LastModified < N''' + CONVERT(nvarchar(50), @DateThreshold, 109) + ''''  
        IF (@ActivityId is not NULL)  
        BEGIN  
            SET @QueryString = @QueryString + ' AND'  
        END  
    END  
  
    IF (@ActivityId is not NULL)  
    BEGIN  
        SET @QueryString = @QueryString + ' ActivityID = N''' + @ActivityId + ''''  
    END  
  
    EXEC sp_executesql @QueryString  
    SELECT * FROM #DanglingActivities  
  
    SET @QueryString = N''  
  
    -- If the user gave a table extension, the dangling instances will be inserted  
    -- into that table.   
    IF (isnull(@NewTableExtension, '') <> '')  
    BEGIN  
        SET @DanglingActiveTableName = @ActiveTableName + '_' + @NewTableExtension  
        SET @DanglingActiveRelationshipsTableName = @ActiveRelationshipsTableName + '_' + @NewTableExtension  
        SET @DanglingContinuationsTableName = @ContinuationsTableName + '_' + @NewTableExtension  
  
        -- If the table for the dangling instances exists then insert into it  
        -- If the table does not exist, then create the dangling instances table  
        -- and then insert into it. SELECT INTO will do that.  
        EXEC sp_tables @table_name = @DanglingActiveTableName  
        IF @@ROWCOUNT > 0  
        BEGIN  
            SET @QueryString = N'INSERT INTO ' + '[' + @DanglingActiveTableName + '] SELECT active.* FROM [' + @ActiveTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
        ELSE  
        BEGIN  
            SET @QueryString = N'SELECT active.* INTO [' + @DanglingActiveTableName + '] FROM [' + @ActiveTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
  
        -- Now do what you did for the Active Instances table for the   
        -- ActiveRelationships table  
        EXEC sp_tables @table_name = @DanglingActiveRelationshipsTableName  
        IF @@ROWCOUNT > 0  
        BEGIN  
            SET @QueryString = N'INSERT INTO ' + '[' + @DanglingActiveRelationshipsTableName + '] SELECT active.* FROM [' + @ActiveRelationshipsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
        ELSE  
        BEGIN  
            SET @QueryString = N'SELECT active.* INTO [' + @DanglingActiveRelationshipsTableName + '] FROM [' + @ActiveRelationshipsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
  
        -- And finally for the continuations table  
        EXEC sp_tables @table_name = @DanglingContinuationsTableName  
        IF @@ROWCOUNT > 0  
        BEGIN  
            SET @QueryString = N'INSERT INTO ' + '[' + @DanglingContinuationsTableName + '] SELECT active.* FROM [' + @ContinuationsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ParentActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
        ELSE  
        BEGIN  
            SET @QueryString = N'SELECT active.* INTO [' + @DanglingContinuationsTableName + '] FROM [' + @ContinuationsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ParentActivityID = dangling.ActivityID'  
            EXEC sp_executesql @QueryString  
        END  
    END  
  
    -- Remove the dangling instances from the Active Instances Table  
    SET @QueryString = 'DELETE FROM [' + @ActiveTableName + '] FROM [' + @ActiveTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID '  
    EXEC sp_executesql @QueryString  
  
    SET @QueryString = 'DELETE FROM [' + @ActiveRelationshipsTableName + '] FROM [' + @ActiveRelationshipsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ActivityID = dangling.ActivityID '  
    EXEC sp_executesql @QueryString  
  
    SET @QueryString = 'DELETE FROM [' + @ContinuationsTableName + '] FROM [' + @ContinuationsTableName + '] active INNER JOIN #DanglingActivities dangling ON active.ParentActivityID = dangling.ActivityID '  
    EXEC sp_executesql @QueryString  
  
    DROP TABLE #DanglingActivities  
  
    COMMIT TRAN      
GO  
```  

## <a name="another-method-of-resolving-incomplete-instances"></a><span data-ttu-id="3838b-163">Une autre méthode de résolution des instances incomplètes</span><span class="sxs-lookup"><span data-stu-id="3838b-163">Another method of resolving incomplete instances</span></span>
<span data-ttu-id="3838b-164">Vous pouvez également résoudre des instances d’activité incomplètes à partir de la base de données à l’aide d’une requête SQL.</span><span class="sxs-lookup"><span data-stu-id="3838b-164">You can also resolve incomplete activity instances from the BAMPrimaryImport database by using a SQL query.</span></span> <span data-ttu-id="3838b-165">Consultez [résoudre des instances d’activité incomplètes](how-to-resolve-incomplete-activity-instances.md).</span><span class="sxs-lookup"><span data-stu-id="3838b-165">See [Resolve incomplete activity instances](how-to-resolve-incomplete-activity-instances.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3838b-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3838b-166">See Also</span></span>  
 [<span data-ttu-id="3838b-167">Gestion des bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="3838b-167">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)
