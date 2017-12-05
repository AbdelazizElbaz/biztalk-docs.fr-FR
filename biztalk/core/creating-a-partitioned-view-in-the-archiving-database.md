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
ms.openlocfilehash: 42adf8f614f124c9b17597a44cdaaba9d7ed4f93
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-a-partitioned-view-in-the-archiving-database"></a>Création d'une vue partitionnée dans la base de données d'archivage
Lorsque vous exécutez le lot de gestion de données BAM (BAM_DM_`<activity name>`NomActivité>), l'analyse BAM copie chaque partition de la base de données d'importation principale BAM dans une table distincte de la base de données des archives BAM. Si vous détachez la base de données des archives et la rattachez à des fins de requête, il sera difficile de localiser les données pour votre requête.  
  
 Vous pouvez créer des vues partitionnées dans la base de données des archives BAM afin de faciliter la localisation des données. L'analyse BAM prend en charge jusqu'à 253 partitions. Pour chaque activité, l'analyse BAM génère un lot DTS de gestion de données BAM, qui copie les données d'activité dans la base de données des archives BAM, puis les supprime de la base de données d'importation principale BAM. Si la base de données des archives rencontre une défaillance après la copie des données mais avant la prochaine sauvegarde, les données sont perdues.  
  
 La solution est d'avoir un lot d'archives unique, qui copie d'abord les anciennes données à partir de toutes les activités, puis sauvegarde la base de données des archives BAM pour supprimer finalement les partitions copiées à partir de la base de données d'importation principale BAM.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.  
  
### <a name="to-create-a-partitioned-view-in-the-bam-archive-database-in-sql-server-2008-sp1-or-sql-server-2008-r2"></a>Pour créer une vue partitionnée dans la base de données des archives BAM sous SQL Server 2008 SP1 ou SQL Server 2008 R2  
  
1.  Ouvrez SQL Server Management Studio.  
  
2.  Sélectionnez la base de données des archives BAM, puis cliquez sur **nouvelle requête**.  
  
3.  Sur le **requête** menu, pointez sur **résultats** puis cliquez sur **résultats dans du texte**.  
  
4.  Copiez le script SQL suivant dans le volet de requête. Remplacez \<nom de l’activité\> avec votre nom de l’activité, puis remplacez `<view type>` avec l’option **Instances** afficher pour l’instance ou **relations** pour une vue de relation.  
  
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
  
5.  exécutez la requête.  
  
## <a name="see-also"></a>Voir aussi  
 [Lots DTS BAM](../core/bam-dts-packages.md)   
 [La sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur](../core/how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases.md)