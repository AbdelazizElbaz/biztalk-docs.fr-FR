---
title: "Les étapes à la configuration pour optimiser votre environnement | Documents Microsoft"
description: "Tâches à effectuer après l’installation et configuration de BizTalk Server, y compris configurer les travaux de l’Agent SQL, d’installer des schémas EDI, de créer des ordinateurs hôtes et les instances d’hôte et bien plus encore dans BizTalk Server"
ms.custom: 
ms.prod: biztalk-server
ms.date: 09/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0fef6ea-e7cc-4ea9-936d-5d638bc43feb
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 80c5f4b69e8204c89ebb3dd74252e85e815b1867
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="post-configuration-steps-to-optimize-your-environment"></a>Étapes d’optimisation de l’environnement après configuration
Étapes de post-configuration visant à améliorer les performances, effectuer la maintenance de l’environnement BizTalk et installer les schémas EDI.

## <a name="disable-shared-memory-protocol-in-sql-server"></a>Désactivation du protocole de mémoire partagée dans SQL Server

1. Ouvrez le **Gestionnaire de configuration SQL Server**.
2. Développez **Configuration du réseau SQL Server** et sélectionnez **Protocoles pour MSSQLSERVER**.
3. Cliquez avec le bouton droit sur **Mémoire partagée** et sélectionnez **Désactiver**.
4. Sélectionnez **Services SQL Server**, puis cliquez avec le bouton droit sur **SQL Server (MSSQLSERVER)** et sélectionnez **Redémarrer**.
5. Fermez le **Gestionnaire de configuration SQL Server**.

## <a name="configure-the-sql-agent-jobs"></a>Configuration des travaux de l’Agent SQL

1. Démarrez **SQL Server Management Studio** et connectez-vous au **moteur de base de données**.
2. Développez **Agent SQL Server**, puis **Travaux**. Configurez les travaux suivants :  

    Nom du travail  |Description  |Pourquoi vous en avez besoin  
    ---------|---------|---------
    Sauvegarde de BizTalk Server | Sauvegarde les bases de données et les fichiers journaux de BizTalk Server. Dans le cadre de la configuration de ce travail, vous déterminez divers paramètres tels que la fréquence et l’emplacement de fichier.<br/><br/>Les liens suivants décrivent le travail de l’Agent SQL et ses paramètres :<br/><br/>[Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)<br/>[Configuration du travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)|Ce travail de l’Agent SQL tronque par ailleurs les journaux des transactions, ce qui permet d’améliorer les performances.<br/><br/>Ce travail ne supprime pas les fichiers de sauvegarde, même les fichiers plus anciens. Pour supprimer les fichiers de sauvegarde, consultez la rubrique Échec du travail « Sauvegarde de BizTalk Server » suite à l’accumulation de fichiers sur le serveur de base de données Microsoft BizTalk Server.
    Purge et archivage DTA |Tronque et archive la base de données des suivis BizTalk Server (BizTalkDTADb). Dans le cadre de la configuration du travail, vous déterminez les paramètres tels que le délai de conservation des instances terminées et de toutes les données.<br/><br/>Les liens suivants décrivent le travail de l’Agent SQL et ses paramètres : <br/><br/>[Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)<br/>[Configuration du travail de purge et d’archivage DTA](../core/how-to-configure-the-dta-purge-and-archive-job.md)|Ce travail de l’Agent SQL affecte directement les performances en conservant les événements de l’hôte de suivi et de purge du suivi.

## <a name="maintain-your-backup-files"></a>Maintenance de vos fichiers de sauvegarde

BizTalk Server n’inclut aucune tâche pour supprimer les fichiers de sauvegarde. Par conséquent, vous décidez seul de la façon dont vous effectuez la maintenance de vos fichiers de sauvegarde. De nombreux utilisateurs créent la procédure stockée sp_DeleteBackupHistoryAndFiles, puis appellent cette procédure stockée directement dans la tâche de sauvegarde de BizTalk Server. D’autres créent un plan de maintenance. C'est vous qui choisissez. Cette rubrique répertorie les deux options.

#### <a name="option-1-create-the-spdeletebackuphistoryandfiles-stored-procedure"></a>Option 1 : Créer la procédure stockée sp_DeleteBackupHistoryAndFiles

1. Dans SQL Server Management Studio, sélectionnez la base de données de gestion BizTalk (BizTalkMgmtDb). 
2. Sélectionnez **Nouvelle requête** et exécutez le script T-SQL suivant pour créer la procédure stockée sp_DeleteBackupHistoryAndFiles : 

    ```
    CREATE PROCEDURE [dbo].[sp_DeleteBackupHistoryAndFiles] @DaysToKeep smallint = null
    AS

    BEGIN
    set nocount on
    IF @DaysToKeep IS NULL OR @DaysToKeep <= 1
    RETURN
    /*
    Only delete full sets
    If a set spans a day in such a way that some items fall into the deleted group and the other does not, do not delete the set
    */

    DECLARE DeleteBackupFiles CURSOR
    FOR SELECT 'del "' + [BackupFileLocation] + '\' + [BackupFileName] + '"' FROM [adm_BackupHistory]
    WHERE  datediff( dd, [BackupDateTime], getdate() ) >= @DaysToKeep
    AND [BackupSetId] NOT IN ( SELECT [BackupSetId] FROM [dbo].[adm_BackupHistory] [h2] WHERE [h2].[BackupSetId] = [BackupSetId] AND datediff( dd, [h2].[BackupDateTime], getdate() ) < @DaysToKeep )
 
    DECLARE @cmd varchar(400)
    OPEN DeleteBackupFiles
    FETCH NEXT FROM DeleteBackupFiles INTO @cmd
    WHILE (@@fetch_status <> -1)
    BEGIN
        IF (@@fetch_status <> -2)
        BEGIN
            EXEC master.dbo.xp_cmdshell @cmd, NO_OUTPUT
            delete from [adm_BackupHistory] WHERE CURRENT OF DeleteBackupFiles
            print @cmd
        END
        FETCH NEXT FROM DeleteBackupFiles INTO @cmd
    END

    CLOSE DeleteBackupFiles
    DEALLOCATE DeleteBackupFiles
    END
    GO
    ```

3. Ouvrez le travail de sauvegarde de BizTalk Server et sélectionnez **Étapes**.
4. Modifiez l’étape **Effacer l’historique de sauvegarde** afin d’appeler la nouvelle procédure stockée *sp_DeleteBackupHistoryAndFiles* à la place de la procédure stockée *sp_DeleteBackupHistory* précédente.
5. Sélectionnez **OK** pour enregistrer vos modifications.

#### <a name="option-2-create-a-maintenance-plan"></a>Option 2 : Créer un plan de maintenance

1. Dans SQL Server Management Studio, développez **Gestion**, cliquez avec le bouton droit sur **Plans de maintenance** et sélectionnez **Assistant Plan de maintenance**.
2. Nommez le plan (par exemple, nommez-le *Vider les fichiers de sauvegarde*), puis sélectionnez le bouton **Modifier** situé à côté de **Planification**.
3. Choisissez la fréquence à laquelle vous souhaitez vider les fichiers de sauvegarde. Ces paramètres sont à votre entière discrétion. Sélectionnez **OK**, puis sélectionnez **Suivant**.
4. Sélectionnez **Tâche de nettoyage de maintenance**, puis **Suivant**.
5. Dans la fenêtre **Tâche de nettoyage**, accédez à **Rechercher dans le dossier et supprimer les fichiers...**, sélectionnez votre dossier de sauvegarde (peut-être f:\BizTalkBackUps) et entrez **.bak** pour l’extension de fichier. Vous pouvez également choisir de supprimer les fichiers en fonction de leur ancienneté. Par exemple, entrez 3 pour supprimer les fichiers antérieurs à 3 semaines. Sélectionnez **Suivant**.
6. Terminez l’Assistant et entrez toutes les informations supplémentaires que vous souhaitez. Sélectionnez **Terminer**.

  
## <a name="install-edi-schemas-and-more-edi-as2-configuration"></a>Installation des schémas EDI et d’autres configurations EDI AS2
 Les fichiers de schéma EANCOM, EDIFACT, HIPAA et X12 sont inclus dans un fichier exécutable à extraction automatique nommé MicrosoftEdiXSDTemplates.exe. Pour créer des solutions EDI, extrayez ces fichiers et déployez-les avec vos projets. Pour installer et extraire ces fichiers :  
  
1.  Exécutez l’installation [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] et installez le composant **Outils et kit de développement**. Ce composant télécharge le fichier de schéma EDI MicrosoftEdiXSDTemplates.exe dans le dossier \XSD_Schema\EDI.  
  
    > [!NOTE]
    > Si vous procédez à une mise à niveau de [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], le fichier MicrosoftEdiXSDTemplates.exe de l’installation existante est remplacé par le fichier MicrosoftEdiXSDTemplates.exe associé à la mise à niveau. Si vous avez besoin des schémas précédents, sauvegardez le fichier MicrosoftEdiXSDTemplates.exe précédent.  
  
    > [!NOTE] 
    > Si vous mettez à niveau les schémas de message lors de la mise à niveau de [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] vers une version ultérieure, vous rencontrerez peut-être des problèmes lors de l’utilisation des schémas mis à jour ou devrez effectuer des étapes de mise à jour supplémentaires. Consultez la section « Considérations de mise à jour des schémas » dans [Considérations importantes relatives à la mise à jour d’applications](../core/important-considerations-for-updating-applications.md)
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\XSD_Schema\EDI et double-cliquez sur MicrosoftEdiXSDTemplates.exe.  
  
3.  Extrayez les schémas dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\XSD_Schema\EDI. Lorsque vous extrayez ces schémas, ils sont stockés dans les dossiers EANCOM, EDIFACT, HIPAA et X12.  
  
#### <a name="add-a-reference-to-the-biztalk-server-edi-application"></a>Ajout d’une référence à l’application EDI BizTalk Server  
 Les schémas, pipelines et orchestrations EDI sont déployés dans l’**application EDI BizTalk**. Pour utiliser toute autre application comme application EDI, ajoutez une référence à l’**application EDI BizTalk**. Étapes :  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], développez **Applications**. Cliquez avec le bouton droit sur l’application que vous souhaitez utiliser pour EDI (tel que *BizTalk Application 1*), sélectionnez **Ajouter**, puis **Références**.  
  
2.  Sélectionnez **Application EDI BizTalk**, puis **OK** pour enregistrer vos modifications.  
  
> [!TIP]
>  Pour afficher les références à d’autres applications, cliquez avec le bouton droit sur n’importe quelle application et sélectionnez **Propriétés**. Sélectionnez **Références**. Vous pouvez également ajouter de nouvelles références et supprimer des références existantes.  
  
> [!NOTE]
>  N’ajoutez pas d’artefacts personnalisés à l’application EDI BizTalk. Il est préférable de laisser cette application telle qu’elle est.  
  
#### <a name="start-batch-orchestrations"></a>Démarrage des orchestrations de traitement par lot  
 Si vous permettez à un tiers de recevoir et/ou d’envoyer des lots EDI, démarrez les orchestrations de traitement par lot. Celles-ci ne sont pas démarrées par l'Assistant Installation ou Configuration. Étapes :  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], développez **Application EDI BizTalk**, puis sélectionnez**Orchestrations**.  
  
2.  Cliquez avec le bouton droit sur chacune des orchestrations suivantes et sélectionnez **Démarrer** :  
  
    -   Microsoft.BizTalk.Edi.BatchSuspendOrchestration.BatchElementSuspendService (assembly : Microsoft.BizTalk.Edi.BatchingOrchestration.dll)  
  
    -   Microsoft.BizTalk.Edi.BatchingOrchestration.BatchingService (assembly : Microsoft.BizTalk.Edi.BatchingOrchestration.dll)  
  
    -   Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService (assembly : Microsoft.BizTalk.Edi.RoutingOrchestration.dll)  
  
> [!NOTE]
>  Les orchestrations de traitement par lot EDI ne doivent être démarrées que si vous recevez et/ou envoyez des lots EDI. Leur démarrage hors de cette condition peut affecter les performances du système.  
  
#### <a name="migrate-edi-artifacts-from-a-previous-biztalk-version"></a>Migrer des artefacts EDI à partir d’une version précédente de BizTalk  
 La manière dont les partenaires commerciaux sont gérés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a été mise à jour dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 et les versions ultérieures. Dans les versions antérieures de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un tiers était créé uniquement pour le partenaire commercial et non pas pour le partenaire hébergeant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 et supérieur, un tiers doit être créé pour tous les partenaires commerciaux, y compris celui hébergeant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans les versions antérieures de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les propriétés des protocoles d’encodage (X12 et EDIFACT) et de transport (AS2) sont définies au niveau du tiers. Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010 et ultérieur, ces propriétés sont définies dans des contrats.  
  
 Pour migrer des données de tiers à partir de versions précédentes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un outil de migration de tiers. Tenez compte des chemins de migration suivants :  
  
|Version [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|Chemin de migration|  
|---------------------------------------------------------------------------------------|--------------------|  
|**[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]**|Procédez à une mise à niveau vers BizTalk Server 2009. Ensuite, utilisez l’outil de migration de tiers inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 pour migrer vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.<br /><br /> **Ou** utilisez l’outil de migration de tiers inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 pour migrer vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010. Effectuez ensuite la mise à niveau vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.|  
|**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009**|Utilisez l'outil de migration de tiers inclus dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2 pour migrer directement vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.|  
|**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2010**|Mise à niveau vers [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013/2013 R2.|  
  
 L'outil de migration de tiers est disponible sur le support [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans le dossier \PartyMigrationTool.  

  
## <a name="install-biztalk-health-monitor-bhm"></a>Installation de BizTalk Health Monitor (BHM)

BizTalk Health Monitor fournit un tableau de bord pour créer et afficher des rapports de la visionneuse MessageBox, créer des requêtes personnalisées, exécuter des tâches de marque de fin de champ, surveiller plusieurs environnements BizTalk, etc. Si vous êtes responsable d’un environnement BizTalk, nous vous conseillons d’installer et d’utiliser cet outil pour vérifier l’intégrité de l’environnement BizTalk et en effectuer la maintenance.

Liens clés :

[Téléchargement de BHM](https://www.microsoft.com/download/details.aspx?id=43716)  
[Installation de BHM](http://social.technet.microsoft.com/wiki/contents/articles/26466.biztalk-server-how-to-install-the-new-biztalk-health-monitor-snap-in.aspx)  
[Blog officiel de BHM](https://blogs.msdn.microsoft.com/biztalkhealthmonitor/)

## <a name="create-your-hosts-and-host-instances"></a>Création de vos hôtes et instances d’hôtes
Il est recommandé de séparer certaines tâches clés entre des hôtes distincts. Par exemple, créez toujours un hôte exclusivement réservé au suivi. Créez un autre hôte/une autre instance d’hôte dédié(e) à la réception des messages, un autre hôte/une autre instance d’hôte à l’envoi des messages et un autre hôte/une autre instance d’hôte à l’orchestration. 

Il existe de nombreuses recommandations dans ce domaine. En voici quelques-unes pour bien démarrer : 

[Gestion des hôtes et des instances d’hôte BizTalk](../core/managing-biztalk-hosts-and-host-instances.md)  
[Configuration de la haute disponibilité pour des hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)  
[Bonnes pratiques : Créer et configurer l’hôte BizTalk Server et l’hôte](http://social.technet.microsoft.com/wiki/contents/articles/19701.biztalk-server-best-practices-create-and-configure-biztalk-server-host-and-host-instances.aspx)  
[Exécution d’orchestrations dans plusieurs hôtes sur le même ordinateur](http://social.technet.microsoft.com/wiki/contents/articles/31183.biztalk-server-running-orchestrations-in-multiple-hosts-on-the-same-computer.aspx)  
[PowerShell pour créer et configurer l’hôte BizTalk Server, les Instances d’hôte et les gestionnaires](https://gallery.technet.microsoft.com/PowerShell-to-Configure-43d77916)  
[Ressources BizTalk Server sur le TechNet Wiki](http://social.technet.microsoft.com/wiki/contents/articles/2240.biztalk-server-resources-on-the-technet-wiki.aspx)
