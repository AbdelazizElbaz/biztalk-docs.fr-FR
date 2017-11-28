---
title: Configurer le travail de sauvegarde de BizTalk Server | Documents Microsoft
description: 
ms.custom: 
ms.date: 11/22/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1afb4f28584d65401220761dcee626fe63f913b
ms.sourcegitcommit: f4c0d7bc4b617688c643101a34062db90014851a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2017
---
# <a name="configure-the-backup-biztalk-server-job"></a>Configurer le travail de sauvegarde de BizTalk Server
Une fois que vous installez et configurez BizTalk Server, configurez la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tâche pour sauvegarder vos données. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] Feature Pack 2**, vous pouvez sauvegarder vos bases de données et des fichiers journaux à un compte de stockage d’objets blob Azure. 


## <a name="overview"></a>Vue d'ensemble
Le **sauvegarde de BizTalk Server (BizTalkMgmtDb)** le travail inclut les étapes suivantes :

-   Étape 1 – **Option de Compression Set**: activer ou désactiver la compression lors de la sauvegarde

-   Étape 2 : **BackupFull**: exécutions de base de données des sauvegardes complètes de bases de données BizTalk Server

-   Étape 3 : **MarkAndBackUpLog**: sauvegarde les journaux de base de données BizTalk Server

-   Étape 4 : **effacer l’historique de sauvegarde**: choisissez la durée de conservation de l’historique de sauvegarde

Pour configurer cette tâche, vous devez :  
  
-   Identifier les serveurs SQL principal et de destination et autres options de sauvegarde
  
-   Choisissez un compte d’utilisateur Windows pour sauvegarder vos bases de données, créez une connexion SQL Server pour ce compte
  
-   mapper les connexions SQL Server au rôle de base de données BTS_BACKUP_USERS dans les bases de données BizTalk Server.
  
-   Assurez-vous que le service MSDTC est actif sur tous les nœuds. Sinon, ajout d’un serveur lié entre le nœud source et le nœud de destination échoue.
  
## <a name="before-you-begin"></a>Avant de commencer  
  
-   Certaines opérations de sauvegarde et de configuration nécessitent l’appartenance au rôle sysadmin SQL Server. Pour sauvegarder votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] signer des bases de données, dans le serveur principal avec un compte qui est membre du rôle de serveur sysadmin SQL Server. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]configuration ajoute le rôle de base de données BTS_BACKUP_USERS. Le compte d’utilisateur utilisé pour sauvegarder vos bases de données ne nécessite pas d’autorisations de l’administrateur système (rôle de SQL Server sysadmin) sur tous les serveurs SQL qui peuvent être impliqués dans une sauvegarde, à l’exception du serveur principal.  
  
-   Décidez à laquelle l’authentification dans le compte que vous utilisez pour exécuter votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les sauvegardes de base de données. Vous pouvez utiliser un compte local, et vous pouvez utiliser plusieurs comptes. Mais il est généralement plus simple et plus sûr de créer un compte utilisateur de domaine Windows dédié spécialement dans ce but. Vous devez configurer un compte de connexion SQL Server pour cet utilisateur. Celui-ci doit être mappé à une connexion SQL Server pour tous les serveurs SQL participant au processus de sauvegarde, en tant que serveur principal (source) ou secondaire (destination). Affecter l’utilisateur au rôle de base de données BizTalk BTS_BACKUP_USERS pour chacune de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données vous sauvegardez.  
  
-   Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne supprime pas les fichiers de sauvegarde obsolètes. Vous devez donc gérer ceux-ci manuellement afin de conserver de l'espace libre sur le disque. Une fois que vous avez créé une sauvegarde complète de vos bases de données, vous devez déplacer les fichiers de sauvegarde obsolètes vers un périphérique de stockage d'archives pour libérer de l'espace sur le disque principal. Consultez le [packages SSIS](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) pour gérer ces fichiers.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]n’écrit pas les données de suivi directement à la base de données des suivis BizTalk ; au lieu de cela, il met en cache les données dans la base de données MessageBox et puis les déplace vers la base de données des suivis BizTalk. Si des données MessageBox sont perdues, certaines données de suivi peuvent l'être également.  
  
## <a name="prerequisites"></a>Conditions préalables  
* Connectez-vous à SQL Server à l’aide d’un compte qui est membre du rôle sysadmin SQL Server.  
  
* Configurez l'exécution du service SQL Server Agent sous un compte de domaine (recommandé, même si des comptes locaux peuvent être utilisés), avec une connexion d'utilisateur mappée sur chaque instance de SQL Server.  

* Pour utiliser un compte de stockage d’objets blob Azure, vous devez un [compte de stockage à usage général](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account#create-a-storage-account), un conteneur au sein de votre compte de stockage d’objets blob, une [signature d’accès partagé](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS) (SAS) et un [informations d’identification SQL à l’aide de la SAP](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#credential). Une fois créé, avoir votre point de terminaison URL du service blob prêt, qui ressemble à https://*yourstorageaccount*.blob.core.windows.net/*containername*. 

    > [!TIP]
    > Si vous n’avez existant d’objets blob de stockage Azure configuré avec une SAP, puis le [script PowerShell de SAS](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url#SAS) peut créer et le conteneur. [SQL Server Backup to URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url) fournit une vue d’ensemble et les étapes spécifiques.
  
## <a name="configure-the-job"></a>Configurer la tâche  
  
1.  Sur le serveur SQL qui héberge la base de données de gestion BizTalk, ouvrez **SQL Server Management Studio**et vous connecter à votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
2.  Développez **Agent SQL Server**, puis **Travaux**.  
  
3.  Cliquez avec le bouton droit sur **Sauvegarde de BizTalk Server (BizTalkMgmtDb)** et sélectionnez **Propriétés**. Dans les propriétés du travail, sélectionnez **Étapes**.  
  
4.  Sélectionnez le **définir l’Option de Compression** pas à pas, puis sélectionnez **modifier**:  

    Cette étape appelle les `sp_SetBackupCompression` procédure stockée dans la base de gestion BizTalk (BizTalkMgmtDb) pour définir la valeur sur le `adm_BackupSettings` table. La procédure stockée possède un seul paramètre :  **@bCompression** . Par défaut, il est défini **0** (compression de la sauvegarde est désactivée). Pour appliquer la compression, remplacez la valeur par **1**:  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     Sélectionnez **OK**.  
  
5.  Sélectionnez le **BackupFull** pas à pas, puis sélectionnez **modifier**. Dans le **commande** zone, mettre à jour les valeurs de paramètre :  
  
    1. **Fréquence**: la valeur par défaut est **d** (quotidienne) ; ce qui est le paramètre recommandé. Les valeurs **h** (horaire), **w** (hebdomadaire), **m** (mensuelle) et **y** (annuelle) sont également disponibles.  
  
    2. **Name**: la valeur par défaut est **BTS**. Cette valeur est utilisée dans le nom du fichier de sauvegarde.  
  
    3. **Emplacement des fichiers de sauvegarde**: remplacez '*\<chemin d’accès de destination >*» avec le chemin d’accès complet (le chemin d’accès doit inclure les guillemets simples) à l’ordinateur et le dossier dans lequel vous souhaitez sauvegarder le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, ou l’URL du point de terminaison de service blob à un compte de stockage d’objets blob Azure.  

        > [!IMPORTANT]
        > - Si vous entrez un chemin d’accès local, vous devez copier manuellement tous les fichiers dans le même dossier sur le système de destination chaque fois que la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail crée de nouveaux fichiers.  
        >   
        >      Pour utiliser un chemin d’accès à distance, entrez un partage UNC tel que \\ \\  *\<nom_serveur >*\\*\<SharedDrive >*\\, où  *\<nom_serveur >* est le nom du serveur où vous voulez les fichiers, et  *\<SharedDrive >* est le nom du lecteur partagé ou du dossier.  
        >   
        >      La sauvegarde de données sur un réseau peut faire l’objet d’éventuels problèmes réseau. Si vous utilisez un emplacement distant, vérifiez que la sauvegarde a réussi lorsque le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] termine.  
        > - Pour éviter de perdre des données, configurez un disque distinct pour la sauvegarde et le stockage des données des bases de données et des journaux. Cette étape est nécessaire afin que vous puissiez accéder aux sauvegardes en cas de défaillance du disque de stockage des données ou des journaux.  
        > - Lorsque la sauvegarde sur un compte d’objets blob Azure, entrez le **point de terminaison de service Blob** URL et le nom du conteneur, qui sont répertoriées dans les propriétés du service blob dans le [portail Azure](https://portal.azure.com).

    4. Ce paramètre est facultatif. **Force une sauvegarde complète après des échecs de sauvegarde partielles** (@ForceFullBackupAfterPartialSetFailure) : la valeur par défaut est **0**. Si une sauvegarde du journal échoue, aucune sauvegarde complète ne sont exécutées jusqu'à ce que le prochain intervalle de fréquence de sauvegarde complète. Remplacez par **1** si vous souhaitez une sauvegarde complète est exécutée chaque fois qu’un échec de sauvegarde de journal se produit.
    
    5. Ce paramètre est facultatif. **Heure de l’heure locale pour le processus de sauvegarde à exécuter** (@BackupHour) : la valeur par défaut est **NULL**. La tâche de sauvegarde n’est pas associée avec le fuseau horaire de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur et s’exécute à minuit UTC (0000) de temps. Si vous souhaitez sauvegarde à une heure spécifique dans le fuseau horaire de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur, entrez une valeur entière comprise entre 0 (minuit) et 23 (11 PM) en tant que l’heure de l’heure locale. 

    6. Ce paramètre est facultatif. **Utiliser l’heure locale** (@UseLocalTime) : indique la procédure pour utiliser l’heure locale. La valeur par défaut est **0**et utilise actuel UTC heure – GETUTCDATE() – 2007-05-04 01:34:11.933. Si la valeur **1**, puis il utilise l’heure locale – GETDATE() – 2007-05-03 18:34:11.933
  
    Dans l’exemple suivant, les sauvegardes quotidiennes sont créées à 14 h 00 et stockées sur le lecteur m:\ :  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    '0' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  

    Dans l’exemple suivant, les sauvegardes hebdomadaires sont créés à minuit heure UTC et stockées dans votre compte Azure blob : 

    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'w' /* Frequency */,   
    'BTS' /* Name */,   
    'http://yourstorageaccount.blob.core.windows.net/yourcontainer/' /* location of backup files */,   
    '1' /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */
    ```  

     Sélectionnez **OK**.  
  
6.  Sélectionnez le **MarkAndBackupLog** pas à pas, puis sélectionnez **modifier**. Dans le **commande** zone, mettre à jour les valeurs de paramètre :  
  
    1.  **@MarkName**: Cela fait partie de la convention d’affectation de noms pour les fichiers de sauvegarde : <Server Name>  _<Database Name>  **_journal_**< nom de marque de journal >_<Timestamp>  
    
    2.  **@BackupPath**: Chemin de destination complet (y compris les guillemets simples) à l’ordinateur et le dossier où stocker le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux, ou le compte de stockage d’objets blob Azure et le conteneur de base de données. Le  *\<chemin d’accès de destination >* peut également être local ou un chemin d’accès UNC vers un autre serveur.  
  
     L'étape MarkAndBackupLog marque les journaux pour la sauvegarde, puis les sauvegarde.  
  
    > [!IMPORTANT]
    >  Pour éviter **perdre des données** et **amélioration des performances**, le  *\<chemin d’accès de destination >* doit être défini sur un autre ordinateur ou un disque dur, différente de celle utilisée pour stocker les journaux de base de données d’origine.  
  
     Sélectionnez **OK**.  
  
7.  Sélectionnez le **effacer l’historique de sauvegarde** pas à pas, puis sélectionnez **modifier**. Dans le **commande** zone, mettre à jour les valeurs de paramètre :  
  
    1.  **@DaysToKeep**: Valeur par défaut est **14 jours**. Détermine la durée pendant laquelle l’historique de sauvegarde est conservée le `Adm_BackupHistory` table. Effacer régulièrement de l’historique de sauvegarde vous permet d’assurer le `Adm_BackupHistory` table à une taille appropriée. 
    
    2.  Ce paramètre est facultatif. **@UseLocalTime**: Indique la procédure pour utiliser l’heure locale. La valeur par défaut est 0 : Il utilise actuel UTC heure – GETUTCDATE() – 2007-05-04 01:34:11.933. Si la valeur 1, puis il utilise l’heure locale – GETDATE() – 2007-05-03 18:34:11.933
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14, @UseLocalTime =1 
    ```  
  
    > [!NOTE]
    >  Cette étape **pas** supprimer les fichiers de sauvegarde à partir du chemin de destination.  
    
     Sélectionnez **OK** et fermez toutes les fenêtres de propriétés.  
  
8.  Ce paramètre est facultatif. Modifiez la planification de la sauvegarde. Consultez [comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md).  
  
    > [!NOTE]
    >  Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté la première fois que vous le configurez. Par défaut, lors des exécutions suivantes, la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tâche réalise une sauvegarde complète une fois par jour et effectue des sauvegardes de journal toutes les 15 minutes.  
  
9. Avec le bouton droit le **sauvegarde de BizTalk Server** de la tâche, puis sélectionnez **activer**. L'état doit passer à **Réussite**.  

## <a name="execute-backupsetupallprocssql-and-logshippingdestinationlogicsql"></a>Exécutez Backup_Setup_All_Procs.sql et LogShipping_Destination_Logic.sql

**[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]Feature Pack 2 (FP2)** utilisé les scripts Backup_Setup_All_Procs.sql et LogShipping_Destination_Logic.sql `\Program Files (x86)\Microsoft BizTalk Server *your version*\Schema`. 

Si votre travail de sauvegarde de BizTalk Server est déjà configuré et que vous souhaitez basculer à l’aide d’Azure d’objets blob (au lieu d’un disque), puis également les opérations suivantes : 

1. Sur le serveur SQL Server, exécutez le `Backup_Setup_All_Procs.sql` script sur toutes les bases de données personnalisées qui sont sauvegardés par le travail de sauvegarde de BizTalk Server. Par défaut, FP2 met automatiquement à jour les bases de données BizTalk ; Il ne met pas à jour toutes les bases de données personnalisées (ces bases de données dans le `adm_OtherBackupDatabases` table dans BizTalkMgmtDb).

    [Dans les bases de données personnalisées](how-to-back-up-custom-databases.md) fournit plus de détails sur les bases de données personnalisées. 

2. **Si vous utilisez [journaux](log-shipping.md)**, exécutez le script LogShipping_Destination_Logic.sql sur le système de destination SQL Server. Si vous n’utilisez pas des journaux, puis exécuter ce script.

    [Configurer le système de Destination pour l’envoi de journaux](how-to-configure-the-destination-system-for-log-shipping.md) fournit plus de détails sur le système de destination.

## <a name="spforcefullbackup-stored-procedure"></a>Procédure stockée sp_ForceFullBackup  
  
Le **sp_ForceFullBackup** procédure stockée dans le **BizTalkMgmtDb** base de données peut servir à exécuter ad hoc sauvegarde complète des fichiers journaux et de données. La procédure stockée met à jour la table adm_ForceFullBackup avec la valeur 1. Lors de la prochaine exécution du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un jeu de sauvegarde de base de données complète est créé.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [Planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md)  
 [Comptes de stockage Azure](https://docs.microsoft.com/azure/storage/common/storage-create-storage-account)  
 [Sauvegarde SQL Server vers une URL](https://docs.microsoft.com/sql/relational-databases/backup-restore/sql-server-backup-to-url)
