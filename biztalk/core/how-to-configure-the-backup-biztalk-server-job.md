---
title: Configurer le travail de sauvegarde de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 11/02/2017
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
ms.openlocfilehash: 67765cfacc7753d649c14677c5399e9c2c7b1e39
ms.sourcegitcommit: 6095645d541bf84f39ff5f342f782284c22e875b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2017
---
# <a name="configure-the-backup-biztalk-server-job"></a>Configurer le travail de sauvegarde de BizTalk Server
Répertorie les étapes nécessaires pour configurer le travail de sauvegarde de BizTalk Server.  

## <a name="overview"></a>Vue d'ensemble
Une fois que vous installez et configurez BizTalk Server, configurez la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tâche pour sauvegarder vos données. Le **sauvegarde de BizTalk Server (BizTalkMgmtDb)** le travail inclut les étapes suivantes :

-   Étape 1 – **Option de Compression Set**: activer ou désactiver la compression lors de la sauvegarde

-   Étape 2 : **BackupFull**: exécutions de base de données des sauvegardes complètes de bases de données BizTalk Server

-   Étape 3 : **MarkAndBackUpLog**: sauvegarde les journaux de base de données BizTalk Server

-   Étape 4 : **effacer l’historique de sauvegarde**: choisissez la durée de conservation de l’historique de sauvegarde

Pour configurer cette tâche, vous devez :  
  
-   Identifier les serveurs SQL principal et de destination et autres options de sauvegarde
  
-   Choisissez un compte d’utilisateur Windows pour sauvegarder vos bases de données et de créer une connexion SQL Server pour ce compte
  
-   mapper les connexions SQL Server au rôle de base de données BTS_BACKUP_USERS dans les bases de données BizTalk Server.
  
-   Assurez-vous que le service MSDTC est actif sur tous les nœuds. Sinon, Échec de l’ajout d’un serveur lié entre le nœud source et le nœud de destination
  
## <a name="before-you-begin"></a>Avant de commencer  
  
-   Certaines opérations de sauvegarde et de configuration nécessitent l’appartenance au rôle sysadmin SQL Server. Pour sauvegarder votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, vous devez être connecté sur le serveur principal avec un compte qui est membre du rôle de serveur sysadmin SQL Server. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]configuration ajoute le rôle de base de données BTS_BACKUP_USERS. Le compte d’utilisateur utilisé pour sauvegarder vos bases de données ne nécessite pas d’autorisations de l’administrateur système (rôle de SQL Server sysadmin) sur tous les serveurs SQL qui peuvent être impliqués dans une sauvegarde, à l’exception du serveur principal.  
  
-   Décidez à laquelle l’authentification dans le compte que vous utilisez pour exécuter votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les sauvegardes de base de données. Vous pouvez utiliser un compte local, voire plusieurs comptes. Toutefois, il est souvent plus simple de créer un compte d'utilisateur de domaine Windows dédié à cette fin. Vous devez configurer un compte de connexion SQL Server pour cet utilisateur. Celui-ci doit être mappé à une connexion SQL Server pour tous les serveurs SQL participant au processus de sauvegarde, en tant que serveur principal (source) ou secondaire (destination). Affecter l’utilisateur au rôle de base de données BizTalk BTS_BACKUP_USERS pour chacune de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données vous sauvegardez.  
  
-   Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne supprime pas les fichiers de sauvegarde obsolètes. Vous devez donc gérer ceux-ci manuellement afin de conserver de l'espace libre sur le disque. Une fois que vous avez créé une sauvegarde complète de vos bases de données, vous devez déplacer les fichiers de sauvegarde obsolètes vers un périphérique de stockage d'archives pour libérer de l'espace sur le disque principal. Consultez le [packages SSIS](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) pour gérer ces fichiers.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]n’écrit pas les données de suivi directement à la base de données des suivis BizTalk ; au lieu de cela, il met en cache les données dans la base de données MessageBox et puis les déplace vers la base de données des suivis BizTalk. Si des données MessageBox sont perdues, certaines données de suivi peuvent l'être également.  
  
## <a name="prerequisites"></a>Conditions préalables  
* Connectez-vous à SQL Server à l’aide d’un compte qui est membre du rôle sysadmin SQL Server.  
  
* Configurez l'exécution du service SQL Server Agent sous un compte de domaine (recommandé, même si des comptes locaux peuvent être utilisés), avec une connexion d'utilisateur mappée sur chaque instance de SQL Server.  
  
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
  
    3. **Emplacement des fichiers de sauvegarde**: remplacez '*\<chemin d’accès de destination >*» avec le chemin d’accès complet (le chemin d’accès doit inclure les guillemets simples) à l’ordinateur et le dossier dans lequel vous souhaitez sauvegarder le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  

        > [!IMPORTANT]
        >  - Si vous entrez un chemin d’accès local, vous devez copier manuellement tous les fichiers dans le même dossier sur le système de destination chaque fois que la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail crée de nouveaux fichiers.  
        >   
        >      Pour spécifier un chemin d’accès à distance, entrez un partage UNC tel que \\ \\  *\<nom_serveur >*\\*\<SharedDrive >* \\ , où  *\<nom_serveur >* est le nom du serveur où vous voulez les fichiers, et  *\<SharedDrive >* est le nom du lecteur partagé ou du dossier.  
        >   
        >      La sauvegarde de données sur un réseau peut faire l’objet d’éventuels problèmes réseau. Si vous utilisez un emplacement distant, vérifiez que la sauvegarde a réussi lorsque le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] termine.  
        > - Pour éviter de perdre des données, configurez un disque distinct pour la sauvegarde et le stockage des données des bases de données et des journaux. Cette étape est nécessaire afin que vous puissiez accéder aux sauvegardes en cas de défaillance du disque de stockage des données ou des journaux.  

    4. Ce paramètre est facultatif. **Force une sauvegarde complète après des échecs de sauvegarde partielles** (@ForceFullBackupAfterPartialSetFailure) : la valeur par défaut est **0**. Si une sauvegarde du journal échoue, aucune sauvegarde complète ne sont exécutées jusqu'à ce que le prochain intervalle de fréquence de sauvegarde complète. Remplacez par **1** si vous souhaitez une sauvegarde complète est exécutée chaque fois qu’un échec de sauvegarde de journal se produit.
    
    5. Ce paramètre est facultatif. **Heure de l’heure locale pour le processus de sauvegarde à exécuter**: la valeur par défaut est NULL. La tâche de sauvegarde n’est pas associée avec le fuseau horaire de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur et s’exécute à minuit UTC (0000) de temps. Si vous souhaitez sauvegarde à une heure spécifique dans le fuseau horaire de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur, entrez une valeur entière comprise entre 0 (minuit) et 23 (11 PM) en tant que l’heure de l’heure locale pour le **BackupHour** paramètre. 

    6. Ce paramètre est facultatif. **Utiliser l’heure locale** (@UseLocalTime) : indique la procédure pour utiliser l’heure locale. La valeur par défaut est 0 et utilise actuel UTC heure – GETUTCDATE() – 2007-05-04 01:34:11.933. Si la valeur 1, puis il utilise l’heure locale – GETDATE() – 2007-05-03 18:34:11.933
  
    Dans l’exemple suivant, les sauvegardes quotidiennes sont créées à 14 h 00 et stockées sur le lecteur m:\ :  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    0 /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  
  
     Sélectionnez **OK**.  
  
6.  Sélectionnez le **MarkAndBackupLog** pas à pas, puis sélectionnez **modifier**. Dans le **commande** zone, mettre à jour les valeurs de paramètre :  
  
    1.  **@MarkName**: Cela fait partie de la convention d’affectation de noms pour les fichiers de sauvegarde : <Server Name>  _<Database Name>  **_journal_**< nom de marque de journal >_<Timestamp>  
    
    2.  **@BackupPath**: Chemin de destination complet (y compris les guillemets simples) à l’ordinateur et le dossier dans lequel vous voulez stocker le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des journaux de base de données. Le  *\<chemin d’accès de destination >* peut être local ou un chemin d’accès UNC vers un autre serveur.  
  
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
  
## <a name="spforcefullbackup-stored-procedure"></a>Procédure stockée sp_ForceFullBackup  
  
Le **sp_ForceFullBackup** procédure stockée dans le **BizTalkMgmtDb** base de données peut servir à exécuter ad hoc sauvegarde complète des fichiers journaux et de données. La procédure stockée met à jour la table adm_ForceFullBackup avec la valeur 1. Lors de la prochaine exécution du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un jeu de sauvegarde de base de données complète est créé.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [Comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md)
