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
# <a name="remove-incomplete-activity-instances"></a>Supprimer des Instances d’activité incomplètes
Lorsqu'un fichier de définition d'analyse BAM est déployé, cinq tables sont créées dans la base de données d'importation principale BAM pour chaque activité définie dans ce fichier. Ces tables sont les suivantes :  
  
-   bam_`ActivityName`_Active  
  
-   bam_`ActivityName`_Completed  
  
-   bam_`ActivityName`_ActiveRelationships  
  
-   bam_`ActivityName`_CompletedRelationships  
  
-   bam_`ActivityName`_Continuations  
  
 Où `ActivityName` est le nom de l'activité définie par l'utilisateur.  
  
 Au cours du fonctionnement normal, les données incomplètes restent dans la table bam_`ActivityName`_Active. Si les données ont des relations et des références, puis il seront des données dans l’analyse bam\_`ActivityName`_ActiveRelationships table.  
  
 Pendant le suivi d'activités qui utilisent des continuations, il peut y avoir des instances dans lesquelles une activité est restée à l'état non terminé dans les bases de données de l'analyse BAM. Vous pouvez utiliser le script de création des procédures stockées à la fin de cette rubrique pour créer une procédure stockée qui purgera les enregistrements incomplets.  
  
 Pour créer la procédure stockée, copiez le script et exécutez-le sur la base de données d'importation principale BAM en utilisant SQL Server Management. Le script va générer une procédure stockée nommée **RemoveDanglingInstances** dans la base de données.  
  
## <a name="create-the-removedanglinginstances-stored-procedure"></a>Créer la procédure stockée de RemoveDanglingInstances  
  
1.  Ouvrez **SQL Server Management Studio**et vous connecter à SQL server.
  
2.  Développez le nom du serveur, **bases de données**, puis sélectionnez la base de données d’importation principale BAM.  
  
3.  Cliquez sur **Nouvelle requête**.  
  
4.  Copiez le script de création de procédure stockée et collez-le dans le volet de requête.  
  
5.  **Exécutez** le script. La procédure stockée résultante peut être affichée dans la liste des procédures stockées en tant que dbo. RemoveDanglingInstances.  
  
## <a name="remove-incomplete-activity-instances"></a>Supprimer des instances d’activité incomplètes  
  
1.  Ouvrez **SQL Server Management Studio**et vous connecter à SQL server.
  
2.  Développez le nom du serveur, **bases de données**, puis sélectionnez la base de données d’importation principale BAM.  
  
3.  Cliquez sur **Nouvelle requête**.  
  
4.  Dans le volet requête, tapez `exec RemoveDanglingInstances` et les paramètres appropriés pour l’opération de suppression que vous effectuez. Par exemple, pour supprimer toutes les instances incomplètes de l’activité de bon de commande, tapez `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`.  
  
5.  **Exécutez** le script.  
  
## <a name="removedanglinginstances-usage-examples"></a>Exemples d'utilisation de RemoveDanglingInstances  
 La procédure stockée peut recevoir quatre paramètres :  
  
|Paramètre| Description|  
|---------------|-----------------|  
|@ActivityName nvarchar(128)|Spécifie le nom de l'instance d'activité incomplète à supprimer.|  
|@ActivityId nvarchar(128)|(Facultatif) Spécifie que la procédure stockée doit supprimer uniquement l'instance en suspens portant l'identificateur d'instance indiqué.|  
|@DateThresholddate/heure|(Facultatif) Spécifie que les instances de tous les actifs de la table active antérieures (non égal à et plus anciennes et plus que des anciennes) à la date donnée sont supprimés.|  
|@NewTableExtensionnvarchar (30)|(Facultatif) Spécifie que la procédure stockée crée de nouvelles tables en concaténant l'extension fournie et le nom des tables d'activités existantes.<br /><br /> Les tables résultantes seront les suivantes :<br /><br /> bam_ActivityName_Active_\<Extension\><br /><br /> bam_ActivityName_ActiveRelationships_\<Extension\><br /><br /> bam_ActivityName_Continuations_\<Extension\><br /><br /> Les instances incomplètes sont déplacées vers les nouvelles tables au lieu d'être purgées de la base de données.<br /><br /> Si les tables existent déjà, la procédure stockée les réutilise ; sinon, elles sont créées. **Important :** si les tables existent déjà, la procédure stockée suppose que leurs schémas correspondent à ceux qui serait utilisé si elles ont été créées. Si un schéma ne correspond pas, la procédure stockée ne pourra pas insérer les enregistrements et l'opération de suppression échouera.|  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder'`  
  
 Supprime toutes les instances actives de l'activité 'PurchaseOrder' dans les tables actives, relations actives et continuations.  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567'`  
  
 Supprime uniquement l'instance d'activité portant l'ID d'activité 'PO220567' dans les tables actives, relations actives et continuations pour l'activité 'PurchaseOrder'.  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 Supprime toutes les instances d'activité dont l'heure de dernière modification (LastModified) est antérieure au 2 février 2005 19:27:03.533 dans les tables actives, relations actives et continuations pour l'activité   
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @ActivityId = 'PO220567', @DateThreshold='2005-02-02 19:27:03:533'`  
  
 Supprime l'instance d'activité dont l'ID d'activité est PO220567 uniquement si la valeur de la colonne LastModified est antérieure au 2 février 2005 19:27:03.533.  
  
 `exec RemoveDanglingInstances @ActivityName = 'PurchaseOrder', @DateThreshold='2005-02-02 19:27:03:533', @NewTableExtension=N'Dangling'`  
  
 Crée les tables suivantes dans la base de données :  
  
 bam_PurchaseOrder_Active_Dangling  
  
 bam_PurchaseOrder_ActiveRelationships_Dangling  
  
 bam_PurchaseOrder_Continuations_Dangling  
  
 La procédure stockée copie toutes les instances d'activité incomplètes antérieures au 2 février 2005 19:27:03.533 dans les tables actives, relations actives et continuations pour l'activité 'PurchaseOrder', et les insère dans les tables nouvellement créées  Les instances d'activité copiées sont ensuite supprimées des tables actives, relations actives et continuations.  
  
## <a name="stored-procedure-creation-script"></a>Script de création de la procédure stockée  
  
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

## <a name="another-method-of-resolving-incomplete-instances"></a>Une autre méthode de résolution des instances incomplètes
Vous pouvez également résoudre des instances d’activité incomplètes à partir de la base de données à l’aide d’une requête SQL. Consultez [résoudre des instances d’activité incomplètes](how-to-resolve-incomplete-activity-instances.md).

## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données BAM](../core/managing-bam-databases.md)
