---
title: Comment configurer le travail de sauvegarde de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, backing up
- backing up, Tracking database
- backing up, user accounts
- backing up, MessageBox database
- databases, backing up
- MessageBox database, backing up
- backing up, databases
- backing up, prerequisites
- configuring, backup jobs
- backing up, warnings
- backing up, backup jobs
- user accounts, backing up
- backing up, configuring
ms.assetid: 026622c9-fcb4-4db0-af48-1379feb30372
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 488e76c3d29c58107e85ad58ed4fad50de671315
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-backup-biztalk-server-job"></a>Comment configurer le travail de sauvegarde de BizTalk Server
Cette rubrique répertorie les étapes nécessaires pour configurer le travail de sauvegarde de BizTalk Server.  
  
 Vous devez configurer le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avant de sauvegarder [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour configurer la sauvegarde, vous devez effectuer la plupart (voire l'ensemble) des tâches suivantes :  
  
-   modifier le travail de l'Agent SQL Server **Sauvegarde de BizTalk Server (BizTalkMgmtDb)** pour identifier les serveurs SQL principal et de destination, ainsi que les autres options de sauvegarde ;  
  
-   choisir un compte d'utilisateur Windows pour sauvegarder vos bases de données et créer une connexion SQL Server pour ce compte ;  
  
-   mapper les connexions SQL Server au rôle de base de données BTS_BACKUP_USERS dans les bases de données BizTalk Server.  
  
-   Assurez-vous que le service MSDTC est actif sur tous les nœuds. Sinon, l'ajout d'un serveur lié entre le nœud source et le nœud de destination échoue.  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
-   Certaines opérations de configuration et de sauvegarde telles que celle-ci requièrent l'appartenance au rôle SQL Server sysadmin. Pour sauvegarder votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, vous devez ouvrir une session sur le serveur principal avec un compte qui est membre du rôle serveur sysadmin SQL Server sur le serveur principal. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]configuration ajoute un rôle de base de données nommé BTS_BACKUP_USERS afin que le compte d’utilisateur utilisé pour sauvegarder vos bases de données ne nécessite pas d’autorisations de l’administrateur système (rôle sysadmin SQL Server) sur tous les serveurs SQL qui peuvent être impliqués dans une sauvegarde, à l’exception de la serveur principal.  
  
-   Vous devez décider quel compte de connexion que vous utilisez pour effectuer votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les sauvegardes de base de données. Vous pouvez utiliser un compte local, voire plusieurs comptes. Toutefois, il est souvent plus simple de créer un compte d'utilisateur de domaine Windows dédié à cette fin. Vous devez configurer un compte de connexion SQL Server pour cet utilisateur. Celui-ci doit être mappé à une connexion SQL Server pour tous les serveurs SQL participant au processus de sauvegarde, en tant que serveur principal (source) ou secondaire (destination). Affecter l’utilisateur au rôle de base de données BizTalk BTS_BACKUP_USERS pour chacune de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données vous sauvegardez.  
  
-   Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne supprime pas les fichiers de sauvegarde obsolètes. Vous devez donc gérer ceux-ci manuellement afin de conserver de l'espace libre sur le disque. Une fois que vous avez créé une sauvegarde complète de vos bases de données, vous devez déplacer les fichiers de sauvegarde obsolètes vers un périphérique de stockage d'archives pour libérer de l'espace sur le disque principal. « BizTalk Bill » a téléchargeable [packages SSIS](http://www.biztalkbill.com/2015/05/26/ssis-packages-to-help-management-biztalk-server-environments/) pour gérer ces fichiers.  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'écrit pas les données de suivi directement dans la base de données des suivis BizTalk : elle les met en cache dans la base de données MessageBox, puis les déplace vers la base de données des suivis BizTalk. Si des données MessageBox sont perdues, certaines données de suivi peuvent l'être également.  
  
## <a name="prerequisites"></a>Conditions préalables  
* Connectez-vous à SQL Server à l’aide d’un compte qui est membre du rôle sysadmin SQL Server.  
  
* Configurez l'exécution du service SQL Server Agent sous un compte de domaine (recommandé, même si des comptes locaux peuvent être utilisés), avec une connexion d'utilisateur mappée sur chaque instance de SQL Server.  
  
## <a name="configure-the-backup-biztalk-server-job"></a>Configurer le travail de sauvegarde de BizTalk Server  
  
1.  Sur le serveur SQL qui héberge la base de données de gestion BizTalk, ouvrez **SQL Server Management Studio**et vous connecter à votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
2.  Développez **Agent SQL Server**, puis **Travaux**.  
  
3.  Cliquez avec le bouton droit sur **Sauvegarde de BizTalk Server (BizTalkMgmtDb)** et sélectionnez **Propriétés**. Dans les propriétés du travail, sélectionnez **Étapes**.  
  
4.  Sélectionnez l'étape **Définir l'option de compression** et sélectionnez **Modifier**. Dans la zone **Commande** , définissez la valeur sur 1 :  
  
    ```  
    exec [dbo].[sp_SetBackupCompression] @bCompression = 1 /*0 - Do not use Compression, 1 - Use Compression */  
    ```  
  
     Sélectionnez **OK**.  
  
5.  Sélectionnez l'étape **BackupFull** , puis **Modifier**. Dans la zone **Commande** , modifiez les valeurs des paramètres :  
  
    1.  **Frequency**(Fréquence) : la valeur par défaut est **d** (quotidienne). Il s'agit du paramètre recommandé. Les valeurs **h** (horaire), **w** (hebdomadaire), **m** (mensuelle) et **y** (annuelle) sont également disponibles.  
  
    2.  **Name**: la valeur par défaut est **BTS**. Cette valeur est utilisée dans le nom du fichier de sauvegarde.  
  
    3.  **Emplacement des fichiers de sauvegarde**: remplacez '*\<chemin d’accès de destination >*» avec le chemin d’accès complet (le chemin d’accès doit inclure les guillemets simples) à l’ordinateur et le dossier dans lequel vous souhaitez sauvegarder le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
        > [!IMPORTANT]
        >  -   Si vous spécifiez un chemin d'accès local, vous devez copier manuellement tous les fichiers dans le même dossier sur le système de destination chaque fois que le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée de nouveaux fichiers.  
        >   
        >      Pour spécifier un chemin d’accès à distance, entrez un partage UNC tel que \\ \\  *\<nom_serveur >*\\*\<SharedDrive >* \\ , où  *\<nom_serveur >* est le nom du serveur où vous voulez les fichiers, et  *\<SharedDrive >* est le nom du lecteur partagé ou du dossier.  
        >   
        >      La sauvegarde de données sur un réseau peut faire l’objet d’éventuels problèmes réseau. Si vous utilisez un emplacement distant, vérifiez que la sauvegarde a réussi lorsque le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] termine.  
        > -   Pour éviter de perdre des données, configurez un disque distinct pour la sauvegarde et le stockage des données des bases de données et des journaux. Cette étape est nécessaire afin que vous puissiez accéder aux sauvegardes en cas de défaillance du disque de stockage des données ou des journaux.  
  
    4.  **Force full backup after partial backup failures**(Forcer la sauvegarde complète en cas d'échec de sauvegarde partielle) : la valeur par défaut est **0** lorsque l'option n'est pas spécifiée. Cela signifie qu'en cas d'échec d'une sauvegarde de journal, aucune sauvegarde complète n'est effectuée jusqu'au prochain intervalle de sauvegarde complète. Remplacez par la valeur **1** si vous souhaitez qu'une sauvegarde complète soit effectuée après un échec de sauvegarde de journal.  
  
    5.  **Heure de l’heure locale pour le processus de sauvegarde à exécuter**: la valeur par défaut est NULL lorsque ne pas spécifié, ce qui signifie que le travail sauvegarde n’est pas associé avec le fuseau horaire de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur et est exécuté à minuit UTC (0000) de temps. Si vous souhaitez pour effectuer sur une heure dans le fuseau horaire de la sauvegarde la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur, entrez une valeur entière comprise entre 0 (minuit) et 23 (11 PM) en tant que l’heure de l’heure locale pour le **BackupHour** paramètre.  
  
     Dans l'exemple suivant, les sauvegardes quotidiennes sont créées à 14 h 00 et stockées sur le lecteur m:\ :  
  
    ```  
    exec [dbo].[sp_BackupAllFull_Schedule]   
    'd' /* Frequency */,   
    'BTS' /* Name */,   
    'm:\BizTalkBackups' /* location of backup files */,   
    0 /* 0 (default) or 1 ForceFullBackupAfterPartialSetFailure */,   
    '2' /* local time hour for the backup process to run */  
    ```  
  
     Sélectionnez **OK**.  
  
6.  Sélectionnez l'étape **MarkAndBackupLog** , puis **Modifier**. Dans le **commande** zone, remplacez **'***\<chemin d’accès de destination >***'** avec le chemin d’accès complet (y compris les guillemets simples) à la ordinateur et le dossier dans lequel vous voulez stocker le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des journaux de base de données. Le  *\<chemin d’accès de destination >* peut être local ou un chemin d’accès UNC vers un autre serveur.  
  
     L'étape MarkAndBackupLog marque les journaux pour la sauvegarde, puis les sauvegarde.  
  
    > [!IMPORTANT]
    >  Pour éviter de perdre des données, le  *\<chemin d’accès de destination >* doit spécifier un ordinateur pour stocker les journaux de base de données qui est différent de celui sur lequel les journaux de base de données d’origine.  
  
     Sélectionnez **OK**.  
  
7.  Sélectionnez l'étape **Effacer l'historique de sauvegarde** , puis **Modifier**. Dans le **commande** , changez **DaysToKeep =***\<nombre >* au nombre de jours pendant lesquels vous souhaitez conserver l’historique de sauvegarde :  
  
    ```  
    exec [dbo].[sp_DeleteBackupHistory] @DaysToKeep=14  
    ```  
  
    > [!NOTE]
    >  Le paramètre **DaysToKeep** spécifie le délai pendant lequel l'historique des sauvegardes est conservé dans la table Adm_BackupHistory. La suppression régulière de l'historique des sauvegardes permet de maintenir une taille appropriée pour la table Adm_BackupHistory. La valeur par défaut du paramètre **DaysToKeep** est 14 jours.  
  
     Sélectionnez **OK** et fermez toutes les fenêtres de propriétés.  
  
8.  Ce paramètre est facultatif. Modifiez la planification de la sauvegarde. Consultez [comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md).  
  
    > [!NOTE]
    >  Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté la première fois que vous le configurez. Par défaut, le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] effectue ensuite une sauvegarde complète une fois par jour et des sauvegardes de journal toutes les 15 minutes.  
  
9. Cliquez avec le bouton droit sur le travail **Sauvegarde de BizTalk Server** et sélectionnez **Activer**. L'état doit passer à **Réussite**.  
  
## <a name="spforcefullbackup-stored-procedure"></a>Procédure stockée sp_ForceFullBackup  
  
> [!NOTE]
>  La procédure stockée sp_ForceFullBackup dans la base de données BizTalkMgmtDb permet de réaliser une sauvegarde complète ad hoc des données et des fichiers journaux. La procédure stockée met à jour la table adm_ForceFullBackup avec la valeur 1. Lors de la prochaine exécution du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un jeu de sauvegarde de base de données complète est créé.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md)