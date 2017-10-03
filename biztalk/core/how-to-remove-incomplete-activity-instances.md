---
title: "Comment supprimer des Instances d’activité incomplètes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
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
ms.openlocfilehash: 99c2f77b6883b7ffba997551c4121013a4379267
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-incomplete-activity-instances"></a><span data-ttu-id="36d7e-102">Suppression d'instances d'activités incomplètes</span><span class="sxs-lookup"><span data-stu-id="36d7e-102">How to Remove Incomplete Activity Instances</span></span>
<span data-ttu-id="36d7e-103">Lorsqu'un fichier de définition d'analyse BAM est déployé, cinq tables sont créées dans la base de données d'importation principale BAM pour chaque activité définie dans ce fichier.</span><span class="sxs-lookup"><span data-stu-id="36d7e-103">When a BAM definition file is deployed, five tables are created in the BAM Primary Import database for each activity defined in the definition file.</span></span> <span data-ttu-id="36d7e-104">Ces tables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="36d7e-104">These tables are:</span></span>  
  
-   <span data-ttu-id="36d7e-105">bam_`ActivityName`_Active</span><span class="sxs-lookup"><span data-stu-id="36d7e-105">bam_`ActivityName`_Active</span></span>  
  
-   <span data-ttu-id="36d7e-106">bam_`ActivityName`_Completed</span><span class="sxs-lookup"><span data-stu-id="36d7e-106">bam_`ActivityName`_Completed</span></span>  
  
-   <span data-ttu-id="36d7e-107">bam_`ActivityName`_ActiveRelationships</span><span class="sxs-lookup"><span data-stu-id="36d7e-107">bam_`ActivityName`_ActiveRelationships</span></span>  
  
-   <span data-ttu-id="36d7e-108">bam_`ActivityName`_CompletedRelationships</span><span class="sxs-lookup"><span data-stu-id="36d7e-108">bam_`ActivityName`_CompletedRelationships</span></span>  
  
-   <span data-ttu-id="36d7e-109">bam_`ActivityName`_Continuations</span><span class="sxs-lookup"><span data-stu-id="36d7e-109">bam_`ActivityName`_Continuations</span></span>  
  
 <span data-ttu-id="36d7e-110">Où `ActivityName` est le nom de l'activité définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="36d7e-110">Where `ActivityName` is the name of the activity that the user has defined.</span></span>  
  
 <span data-ttu-id="36d7e-111">Au cours du fonctionnement normal, les données incomplètes restent dans la table bam_`ActivityName`_Active.</span><span class="sxs-lookup"><span data-stu-id="36d7e-111">During normal execution, incomplete data remains in the bam_`ActivityName`_Active table.</span></span> <span data-ttu-id="36d7e-112">Si les données ont des relations et des références, puis il seront des données dans l’analyse bam\_`ActivityName`_ActiveRelationships table.</span><span class="sxs-lookup"><span data-stu-id="36d7e-112">If the data has relations and references, then there will be data in the bam\_`ActivityName`_ActiveRelationships table.</span></span>  
  
 <span data-ttu-id="36d7e-113">Pendant le suivi d'activités qui utilisent des continuations, il peut y avoir des instances dans lesquelles une activité est restée à l'état non terminé dans les bases de données de l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="36d7e-113">During the tracking of activities that use continuations, there may be instances in which an activity is left in an incomplete state in the BAM databases.</span></span> <span data-ttu-id="36d7e-114">Vous pouvez utiliser le script de création des procédures stockées à la fin de cette rubrique pour créer une procédure stockée qui purgera les enregistrements incomplets.</span><span class="sxs-lookup"><span data-stu-id="36d7e-114">You can use the stored procedure creation script at the end of this topic to create a stored procedure that will purge the incomplete records.</span></span>  
  
 <span data-ttu-id="36d7e-115">Pour créer la procédure stockée, copiez le script et exécutez-le sur la base de données d'importation principale BAM en utilisant SQL Server Management.</span><span class="sxs-lookup"><span data-stu-id="36d7e-115">To create the stored procedure, copy the script and execute it against the BAM Primary Import database by using SQL Server Management.</span></span> <span data-ttu-id="36d7e-116">Le script va générer une procédure stockée nommée **RemoveDanglingInstances** dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="36d7e-116">The script will generate a stored procedure named **RemoveDanglingInstances** in the database.</span></span>  
  
### <a name="to-create-the-removedanglinginstances-stored-procedure"></a><span data-ttu-id="36d7e-117">Pour créer la procédure stockée RemoveDanglingInstances</span><span class="sxs-lookup"><span data-stu-id="36d7e-117">To create the RemoveDanglingInstances stored procedure</span></span>  
  
1.  <span data-ttu-id="36d7e-118">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="36d7e-118">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="36d7e-119">Dans le **se connecter au serveur** boîte de dialogue, sélectionnez le serveur SQL server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="36d7e-119">In the **Connect to Server** dialog box, select the SQL server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="36d7e-120">Développez le nom du serveur, **bases de données**, puis sélectionnez la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="36d7e-120">Expand the server name, expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
4.  <span data-ttu-id="36d7e-121">Cliquez sur **Nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="36d7e-121">Click **New Query**.</span></span>  
  
5.  <span data-ttu-id="36d7e-122">Copiez le script de création de la procédure stockée et collez-le dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="36d7e-122">Copy the stored procedure creation script and paste it into the right pane.</span></span>  
  
6.  <span data-ttu-id="36d7e-123">Cliquez sur **Execute** pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="36d7e-123">Click **Execute** to run the script.</span></span> <span data-ttu-id="36d7e-124">La procédure stockée résultante peut être affichée dans la liste des procédures stockées en tant que dbo. RemoveDanglingInstances.</span><span class="sxs-lookup"><span data-stu-id="36d7e-124">The resulting stored procedure can be viewed in the list of stored procedures as dbo.RemoveDanglingInstances.</span></span>  
  
### <a name="to-remove-incomplete-activity-instances"></a><span data-ttu-id="36d7e-125">Pour supprimer les instances d'activité incomplètes</span><span class="sxs-lookup"><span data-stu-id="36d7e-125">To remove incomplete activity instances</span></span>  
  
1.  <span data-ttu-id="36d7e-126">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="36d7e-126">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="36d7e-127">Dans le **se connecter au serveur** boîte de dialogue, sélectionnez le serveur SQL server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="36d7e-127">In the **Connect to Server** dialog box, select the SQL server and the appropriate authentication method, and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="36d7e-128">Développez le nom du serveur, **bases de données**, puis sélectionnez la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="36d7e-128">Expand the server name, expand **Databases**, and then select the BAM Primary Import database.</span></span>  
  
4.  <span data-ttu-id="36d7e-129">Cliquez sur **Nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="36d7e-129">Click **New Query**.</span></span>  
  
5.  <span data-ttu-id="36d7e-130">Dans le volet droit, tapez `exec RemoveDanglingInstances` et les paramètres appropriés pour l’opération de suppression que vous effectuez.</span><span class="sxs-lookup"><span data-stu-id="36d7e-130">In the right pane, type `exec RemoveDanglingInstances` and the appropriate parameters for the remove operation you are performing.</span></span> <span data-ttu-id="36d7e-131">Par exemple, pour supprimer toutes les instances incomplètes de l’activité de bon de commande, tapez `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`.</span><span class="sxs-lookup"><span data-stu-id="36d7e-131">For example, to remove all incomplete instances of the Purchase Order activity, type `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`.</span></span>  
  
6.  <span data-ttu-id="36d7e-132">Cliquez sur **Execute** pour exécuter le script.</span><span class="sxs-lookup"><span data-stu-id="36d7e-132">Click **Execute** to run the script.</span></span>  
  
## <a name="removedanglinginstances-usage-examples"></a><span data-ttu-id="36d7e-133">Exemples d'utilisation de RemoveDanglingInstances</span><span class="sxs-lookup"><span data-stu-id="36d7e-133">RemoveDanglingInstances Usage Examples</span></span>  
 <span data-ttu-id="36d7e-134">La procédure stockée peut recevoir quatre paramètres :</span><span class="sxs-lookup"><span data-stu-id="36d7e-134">The stored procedure can receive four parameters:</span></span>  
  
|<span data-ttu-id="36d7e-135">Paramètre</span><span class="sxs-lookup"><span data-stu-id="36d7e-135">Parameter</span></span>|<span data-ttu-id="36d7e-136"> Description</span><span class="sxs-lookup"><span data-stu-id="36d7e-136">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36d7e-137">@ActivityName nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="36d7e-137">@ActivityName nvarchar(128)</span></span>|<span data-ttu-id="36d7e-138">Spécifie le nom de l'instance d'activité incomplète à supprimer.</span><span class="sxs-lookup"><span data-stu-id="36d7e-138">Specifies the name of the incomplete activity instance to remove.</span></span>|  
|<span data-ttu-id="36d7e-139">@ActivityId nvarchar(128)</span><span class="sxs-lookup"><span data-stu-id="36d7e-139">@ActivityId nvarchar(128)</span></span>|<span data-ttu-id="36d7e-140">(Facultatif) Spécifie que la procédure stockée doit supprimer uniquement l'instance en suspens portant l'identificateur d'instance indiqué.</span><span class="sxs-lookup"><span data-stu-id="36d7e-140">(Optional) Specifies that the stored procedure remove only the dangling instance with the specified instance identifier.</span></span>|  
|<span data-ttu-id="36d7e-141">@DateThresholddate/heure</span><span class="sxs-lookup"><span data-stu-id="36d7e-141">@DateThreshold datetime</span></span>|<span data-ttu-id="36d7e-142">(Facultatif) Spécifie que les instances de tous les actifs de la table active antérieures (non égal à et plus anciennes et plus que des anciennes) à la date donnée sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="36d7e-142">(Optional) Specifies that all the active instances in the active table that are older (not equal to and older, only older) than the given date are removed.</span></span>|  
|<span data-ttu-id="36d7e-143">@NewTableExtensionnvarchar (30)</span><span class="sxs-lookup"><span data-stu-id="36d7e-143">@NewTableExtension nvarchar(30)</span></span>|<span data-ttu-id="36d7e-144">(Facultatif) Spécifie que la procédure stockée crée de nouvelles tables en concaténant l'extension fournie et le nom des tables d'activités existantes.</span><span class="sxs-lookup"><span data-stu-id="36d7e-144">(Optional) Specifies that the stored procedure creates three new tables by concatenating the supplied extension to the existing activity tables.</span></span><br /><br /> <span data-ttu-id="36d7e-145">Les tables résultantes seront les suivantes :</span><span class="sxs-lookup"><span data-stu-id="36d7e-145">The resulting tables will be:</span></span><br /><br /> <span data-ttu-id="36d7e-146">bam_ActivityName_Active_\<Extension ></span><span class="sxs-lookup"><span data-stu-id="36d7e-146">bam_ActivityName_Active_\<Extension></span></span><br /><br /> <span data-ttu-id="36d7e-147">bam_ActivityName_ActiveRelationships_\<Extension ></span><span class="sxs-lookup"><span data-stu-id="36d7e-147">bam_ActivityName_ActiveRelationships_\<Extension></span></span><br /><br /> <span data-ttu-id="36d7e-148">bam_ActivityName_Continuations_\<Extension ></span><span class="sxs-lookup"><span data-stu-id="36d7e-148">bam_ActivityName_Continuations_\<Extension></span></span><br /><br /> <span data-ttu-id="36d7e-149">Les instances incomplètes sont déplacées vers les nouvelles tables au lieu d'être purgées de la base de données.</span><span class="sxs-lookup"><span data-stu-id="36d7e-149">The incomplete instances are moved to the new tables rather than being purged from the database.</span></span><br /><br /> <span data-ttu-id="36d7e-150">Si les tables existent déjà, la procédure stockée les réutilise ; sinon, elles sont créées.</span><span class="sxs-lookup"><span data-stu-id="36d7e-150">If the tables already exist, the stored procedure reuses them; otherwise they are created.</span></span> <span data-ttu-id="36d7e-151">**Important :** si les tables existent déjà, la procédure stockée suppose que leurs schémas correspondent à ceux qui serait utilisé si elles ont été créées.</span><span class="sxs-lookup"><span data-stu-id="36d7e-151">**Important:**  If the tables already exist, the stored procedure assumes that their schemas match the ones that would be used if they were created.</span></span> <span data-ttu-id="36d7e-152">Si un schéma ne correspond pas, la procédure stockée ne pourra pas insérer les enregistrements et l'opération de suppression échouera.</span><span class="sxs-lookup"><span data-stu-id="36d7e-152">If a schema does not match, the stored procedure will fail to insert the records and the remove operation will fail.</span></span>|  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`  
  
 <span data-ttu-id="36d7e-153">Supprime toutes les instances actives de l'activité 'PurchaseOrder' dans les tables actives, relations actives et continuations.</span><span class="sxs-lookup"><span data-stu-id="36d7e-153">Removes all active instances of the 'PurchaseOrder' activity in the active, active relationships, and continuations tables.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567'`  
  
 <span data-ttu-id="36d7e-154">Supprime uniquement l'instance d'activité portant l'ID d'activité 'PO220567' dans les tables actives, relations actives et continuations pour l'activité 'PurchaseOrder'.</span><span class="sxs-lookup"><span data-stu-id="36d7e-154">Removes only the activity instance that has an Activity ID of 'PO220567' from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 <span data-ttu-id="36d7e-155">Supprime toutes les instances d'activité dont l'heure de dernière modification (LastModified) est antérieure au 2 février 2005 19:27:03.533 dans les tables actives, relations actives et continuations pour l'activité </span><span class="sxs-lookup"><span data-stu-id="36d7e-155">Removes all the activity instances that have a LastModified time that is older than Feb 2nd, 2005 7:27:03.533 PM from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 <span data-ttu-id="36d7e-156">Supprime l'instance d'activité dont l'ID d'activité est PO220567 uniquement si la valeur de la colonne LastModified est antérieure au 2 février 2005 19:27:03.533.</span><span class="sxs-lookup"><span data-stu-id="36d7e-156">Removes the activity instance whose activity ID is PO220567 only if its LastModified column is older than Feb 2nd, 2005 7:27:03.533 PM.</span></span>  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533', @NewTableExtension=N'Dangling'`  
  
 <span data-ttu-id="36d7e-157">Crée les tables suivantes dans la base de données :</span><span class="sxs-lookup"><span data-stu-id="36d7e-157">Creates the following tables in the database:</span></span>  
  
 <span data-ttu-id="36d7e-158">bam_PurchaseOrder_Active_Dangling</span><span class="sxs-lookup"><span data-stu-id="36d7e-158">bam_PurchaseOrder_Active_Dangling</span></span>  
  
 <span data-ttu-id="36d7e-159">bam_PurchaseOrder_ActiveRelationships_Dangling</span><span class="sxs-lookup"><span data-stu-id="36d7e-159">bam_PurchaseOrder_ActiveRelationships_Dangling</span></span>  
  
 <span data-ttu-id="36d7e-160">bam_PurchaseOrder_Continuations_Dangling</span><span class="sxs-lookup"><span data-stu-id="36d7e-160">bam_PurchaseOrder_Continuations_Dangling</span></span>  
  
 <span data-ttu-id="36d7e-161">La procédure stockée copie toutes les instances d'activité incomplètes antérieures au 2 février 2005 19:27:03.533 dans les tables actives, relations actives et continuations pour l'activité 'PurchaseOrder', et les insère dans les tables nouvellement créées </span><span class="sxs-lookup"><span data-stu-id="36d7e-161">The stored procedure copies all incomplete activity instances that are older than Feb 2nd, 2005 7:27:03.533 PM from the active, active relationships, and continuations tables for the 'PurchaseOrder' activity, and inserts them into the newly created tables.</span></span> <span data-ttu-id="36d7e-162">Les instances d'activité copiées sont ensuite supprimées des tables actives, relations actives et continuations.</span><span class="sxs-lookup"><span data-stu-id="36d7e-162">The copied activity instances are then removed from the active, active relationships, and continuations tables.</span></span>  
  
## <a name="stored-procedure-creation-script"></a><span data-ttu-id="36d7e-163">Script de création de la procédure stockée</span><span class="sxs-lookup"><span data-stu-id="36d7e-163">Stored Procedure Creation Script</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="36d7e-164">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36d7e-164">See Also</span></span>  
 [<span data-ttu-id="36d7e-165">Gestion des bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="36d7e-165">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)