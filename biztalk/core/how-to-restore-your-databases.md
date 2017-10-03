---
title: "Comment faire pour restaurer vos bases de données | Documents Microsoft"
ms.custom: 
ms.date: 2016-05-10
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- restoring [BAM], Star Schema database, Star Schema database [BAM], restoring
- restoring, 64-bit environments
- Star Schema database [BAM], restoring
- restoring [BAM], Analysis database
- log shipping
- databases, restoring
- Archive database [BAM], restoring
- backing up, restoring
- Analysis database [BAM], restoring
- restoring [BAM], Archive database
- restoring [BAM], Star Schema database
- databases, restoring [64-bit environment]
- Primary Import database [BAM], restoring
- 64-bit environments, restoring databases
- restoring, databases
ms.assetid: 0176932a-6b3d-4502-975b-a76296189092
caps.latest.revision: "52"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6833fff893a692475e97e7722d9d65658eace0d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-your-databases"></a>Restauration de vos bases de données
Vous devez restaurer toutes les bases de données à la même marque afin de garantir un état transactionnel cohérent entre les bases de données. Consultez [Transactions marquées, sauvegardes complètes et sauvegardes de journaux](../core/marked-transactions-full-backups-and-log-backups.md).  
  
 S'il n'y a qu'un serveur dans le système de destination, vérifiez que tous les jeux de sauvegarde de journal (à l'exception du jeu le plus récent) ont été restaurés. Consultez [affichage de l’historique de restauration des sauvegardes](../core/viewing-the-history-of-restored-backups.md). Si tous les jeux de sauvegarde de journal n'ont pas été restaurés et que le travail de restauration n'est pas en cours d'exécution, exécutez ce dernier (manuellement le cas échéant). S'il reste des jeux de sauvegarde pouvant être restaurés, ils sont traités par le travail jusqu'à ce que qu'ils soient tous restaurés.  
  
 S'il y a plusieurs serveurs dans le système de destination, tous les serveurs doivent être restaurés vers le même jeu de sauvegarde. Consultez l'historique de restauration sur chaque serveur et vérifiez que le jeu de sauvegarde le plus récent restauré est identique sur tous les serveurs. Si ce n'est pas le cas, vous devez exécuter manuellement le travail de restauration sur chaque serveur pour lequel le jeu de sauvegarde le plus récent doit être restauré.  
  
 Une fois tous les serveurs restaurés vers le même jeu de sauvegarde, le jeu final peut être restauré manuellement.  
  
 La table adm_BackupHistory est le point d'historique central pour l'envoi des journaux du système source. Tous les travaux de sauvegarde effectués sont enregistrés dans cette table. Tous les serveurs du système de destination lisent cette table pour recevoir les informations nécessaires à l'exécution des travaux de restauration.  
  
> [!NOTE]
>  Si vous restaurez la base de données d'importation principale BAM à partir d'une sauvegarde, vous devez également restaurer les bases de données des archives BAM, de schémas en étoile BAM et d'analyse BAM à l'aide d'une sauvegarde antérieure à la sauvegarde principale BAM. Consultez [sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md).  
  
> [!NOTE]
>  Si vous déplacez les sauvegardes complètes ou de journal d'une base de données source de l'emplacement dans lequel le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les a placées, vous devez mettre à jour la ligne associée à cette base de données dans la table bts_LogShippingDatabases sur le système de destination en pointant LogFileLocation ou DBFileLocation sur le nouvel emplacement dans lequel le système de destination doit lire les fichiers de sauvegarde complète/de journal. Cette table est renseignée lorsque vous exécutez la procédure stockée bts_ConfigureBtsLogShipping. Par défaut, ces colonnes sont définies sur la valeur Null (qui indique que le système de destination doit lire les fichiers de sauvegarde à partir de l'emplacement stocké dans la table adm_BackupHistory).  
  
> [!IMPORTANT]
>  Conservez toujours une copie de vos fichiers de sauvegarde dans un emplacement sécurisé : même si vous disposez de sauvegardes de journal, vous ne pouvez pas restaurer vos bases de données sans les fichiers de sauvegarde.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Connectez-vous à SQL Server en utilisant un compte qui est membre du rôle sysadmin SQL Server.  
  
### <a name="to-restore-your-databases"></a>Pour restaurer vos bases de données  
  
1.  Sur le système de destination, ouvrez **SQL Server Management Studio**et vous connecter à votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
2.  Développez **Agent SQL Server**, puis **Travaux**. Procédez comme suit :  
  
    1.  Cliquez avec le bouton droit sur le travail **Envoi de journaux de BizTalk Server - Obtenir l'historique des sauvegardes** , puis sélectionnez **Désactiver**. L'état passe à Réussite.  
  
    2.  Cliquez avec le bouton droit sur le travail **Envoi de journaux de BizTalk Server - Restaurer les bases de données** , puis sélectionnez **Désactiver**. L'état passe à Réussite.  
  
    3.  Cliquez sur le travail **Envoi de journaux de BizTalk Server - Restaurer à la marque** et sélectionnez **Démarrer le travail à l'étape**. Sélectionnez **ID d'étape 1** , puis **Démarrer**.  
  
         Lorsque l’état passe à **réussite**, les travaux de l’Agent SQL Server et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont restaurés dans le système de destination.  
  
    > [!IMPORTANT]
    >  Si l' **État** est Erreur, sélectionnez le lien dans le champ Message pour déterminer la cause. Ces travaux doivent avoir l'état Réussite avant de continuer.  
  
3.  Sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] où vous avez modifié le fichier SampleUpdateInfo.xml, ouvrez une invite de commandes et accédez à :  
  
     ordinateur 32 bits :`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
     ordinateur 64 bits :`%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
4.  À l'invite de commandes, tapez :  
  
     `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
  
     Ce script met à jour toutes les tables qui stockent des informations sur l'emplacement des autres bases de données.  
  
    > [!IMPORTANT]
    >  -   Exécutez UpdateDatabase.vbs sur **un** serveur dans le groupe BizTalk.  
    > -   Sur les ordinateurs 64 bits, vous devez exécuter UpdateDatabase.vbs à partir d'une invite de commandes 64 bits. Notez que l'invite de commandes par défaut sur les ordinateurs 64 bits est une invite de commandes 64 bits et se trouve dans %SystemDrive%\windows\System32\cmd.exe.  
    > -   Le moteur EDI BizTalk ne nécessite aucune de ses propres modifications à SampleUpdateInfo.xml lors de la restauration des bases de données.  Il s’appuie sur la connectivité à la base de données BizTalkDTADb pour accéder aux tables EDI.  
  
5.  Copiez le fichier SampleUpdateInfo.xml modifié dans le dossier suivant sur **chaque** ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans ce groupe BizTalk :  
  
     ordinateur 32 bits : copier vers`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
     ordinateur 64 bits : copier vers`%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`  
  
6.  Sur **chaque** ordinateur dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de groupe, ouvrez une invite de commandes et accédez à :  
  
     ordinateur 32 bits :`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`  
  
     ordinateur 64 bits :`%SystemDrive%Program Files (x86)Microsoft BizTalk Server <version>Bins32SchemaRestore`  
  
7.  À l'invite de commandes, tapez :  
  
     `cscript UpdateRegistry.vbs SampleUpdateInfo.xml`  
  
     Ce script met à jour toutes les entrées de Registre qui stockent des informations sur l'emplacement des autres bases de données.  
  
    > [!IMPORTANT]
    >  Exécutez UpdateRegistry.vbs sur **chaque** serveur dans le groupe BizTalk.  
    >   
    >  Sur les ordinateurs 64 bits, vous devez exécuter UpdateRegistry.vbs à partir d'une invite de commandes 64 bits.  Notez que l'invite de commandes par défaut sur les ordinateurs 64 bits est une invite de commandes 64 bits et se trouve dans %SystemDrive%\windows\System32\cmd.exe.  
  
8.  Redémarrez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Consultez [comment faire pour démarrer, arrêter, suspendre, reprendre ou redémarrer le serveur BizTalk Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
9. Une fois vos bases de données restaurées, redémarrez le service WMI (Windows Management Instrumentation) :  
  
    1.  Ouvrez **services.msc**.  
  
    2.  Cliquez avec le bouton droit sur **Windows Management Instrumentation**, puis sélectionnez **Redémarrer**.  
  
10. Ouvrez **Administration de BizTalk Server.** Procédez comme suit :  
  
    1.  Cliquez avec le bouton droit sur le projet **BizTalk Group** , puis sélectionnez **Supprimer**.  
  
    2.  Cliquez avec le bouton droit sur le nœud **Administration de BizTalk Server** et sélectionnez **Se connecter au groupe existant**.  
  
    3.  Dans **Nom du serveur SQL**, sélectionnez le nom de l'instance SQL Server qui héberge la base de données de gestion BizTalk. Lorsque vous sélectionnez l'instance SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détecte automatiquement les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l'ordinateur.  
  
    4.  Dans **Nom de la base de données**, sélectionnez votre base de données de gestion BizTalk (**BizTalkMgmtDb** par défaut), puis sélectionnez **OK**.  
  
     La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ajoute le groupe BizTalk à la console Administration.  
  
     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est désormais restauré et doit être en cours d'exécution. Configurez ensuite le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour commencer l'écriture des sauvegardes vers un nouveau serveur de destination. Vous devez également reconfigurer un nouveau système de destination.  
  
> [!IMPORTANT]
>  Si vous utilisez le moteur des règles, vous devez redémarrer le service de mise à jour du moteur des règles sur chaque serveur du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après la restauration des bases de données. Consultez [comment faire pour démarrer, arrêter, suspendre, reprendre ou redémarrer le serveur BizTalk Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
> [!NOTE]
>  Si vous utilisez l'analyse BAM, vous devez à présent restaurer les bases de données BAM. Consultez [sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)