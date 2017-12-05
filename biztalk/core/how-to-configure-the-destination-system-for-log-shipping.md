---
title: "Comment configurer le système de Destination pour l’envoi de journaux | Documents Microsoft"
ms.custom: 
ms.date: 2015-12-03
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- system failures, preventing
- log shipping
- databases, backing up
- backing up, databases
- system failures, backing up
- backing up, system failures
ms.assetid: 7b4425f5-b105-4fb2-a503-94ca1e75ad55
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 611544e77de738c904fa673b56dbec75fd17d4bd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-destination-system-for-log-shipping"></a>Comment configurer le système de Destination pour l’envoi de journaux
La copie des journaux de transaction offre des fonctionnalités de serveur de secours, ce qui réduit le temps mort en cas de défaillance du système. L'envoi de journaux vous permet d'envoyer automatiquement des journaux des transactions à partir du système source vers le système de destination. Au niveau du système de destination, les journaux des transactions sont restaurés dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données ; les maintenant étroitement synchronisées avec les bases de données source.  
  
 L'envoi de journaux fonctionne dans les environnements monoserveur et de serveur distribué. Le serveur ou groupe de serveurs contenant des données actives est appelé « système source (ou principal) ». Le serveur ou groupe de serveurs utilisés pour restaurer les sauvegardes de base de données produites par le système source (ou principal) est appelé « système de destination (ou secondaire) ».  
  
 [À propos de l’envoi de journaux](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server) dans l’instruction SQL, documentation fournit des détails spécifiques.  
  
 Vous pouvez utiliser les étapes suivantes pour créer un système de destination constitué d'un seul serveur pour un système source unique. Si le système de destination compte plusieurs serveurs, répétez les étapes sur chaque serveur de destination.  
  
> [!IMPORTANT]
>  Conservez toujours une copie de vos fichiers de sauvegarde dans un emplacement sécurisé : même si vous disposez de sauvegardes de journal, vous ne pouvez pas restaurer vos bases de données sans les fichiers de sauvegarde.  
  
## <a name="prerequisites"></a>Conditions préalables  
* Connectez-vous en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.  
  
* Utilisez la même version de SQL Server sur les systèmes source et de destination. SQL Server doit être installé dans le même emplacement relatif sur les systèmes source et de destination.  
  
* Le répertoire du journal des transactions SQL (fichiers .LDF) présent sur le système source doit également exister sur le système de destination. Si tel n'est pas le cas, créez le répertoire en lui donnant les mêmes nom et autorisations que sur le système source.  
  
### <a name="configure-the-destination-system-for-log-shipping"></a>Configurer le système de destination pour l’envoi de journaux  
  
1.  Sur le système de destination, ouvrez **SQL Server Management Studio**et vous connecter à votre serveur SQL Server. Sélectionnez **master** à partir de bases de données disponibles.  
  
2.  Sur le **fichier** menu, **ouvrir** le script SQL suivant :  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Schema.sql  
    ```  
  
3.  Sur le **requête** menu, sélectionnez **Execute**.  
  
     Le *LogShipping_Destination_Schema* supprime et recrée les tables utilisées pour la restauration des bases de données source sur le système de destination. Cela inclut les tables permettant de stocker la liste des bases de données en cours de récupération, les copies de l'historique des sauvegardes importées à partir de la base de données BizTalkMgmtDb du système source, ainsi que les informations sur les travaux de l'Agent SQL Server configurés pour être exécutés sur les bases de données sources.  
  
4.  Sur le **fichier** menu, **ouvrir** le script SQL suivant :  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Logic.sql  
    ```  
  
5.  Sur le **requête** menu, sélectionnez **Execute**.  
  
6.  Sur l’ou les ordinateurs que vous avez identifié en tant que le système de destination, ouvrez **SQL Server Management Studio** et se connecter à SQL Server.  
  
7.  Sélectionnez **nouvelle requête**. Dans la fenêtre de requête, collez la commande suivante :  
  
    ```  
    exec bts_ConfigureBizTalkLogShipping @nvcDescription = '<MyLogShippingSolution>',  
    @nvcMgmtDatabaseName = '<BizTalkServerManagementDatabaseName>',  
    @nvcMgmtServerName = '<BizTalkServerManagementDatabaseServer>',  
    @SourceServerName = null, -- null indicates that this destination server restores all databases  
    @fLinkServers = 1 -- 1 automatically links the server to the management database  
    ```  
  
     Puis :  
  
    1.  Sur le système de destination, activez  **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**.  
  
    2.  Dans la fenêtre de requête, remplacez  *\<MyLogShippingSolution\>*  avec une description significative, entourée par des guillemets simples.  
  
    3.  Dans la fenêtre de requête, remplacez  *\<BizTalkServerManagementDatabaseName\>*  et  *\<BizTalkServerManagementDatabaseServer\>*  avec le nom et l’emplacement de votre base de données de gestion BizTalk source, entouré de guillemets simples.  
  
    > [!NOTE]
    >  Si vous disposez de plusieurs serveurs sources, vous pouvez restaurer chaque serveur source sur son propre serveur de destination. Sur chaque serveur de destination, dans le  **@SourceServerName = null** paramètre, remplacez *null* par le nom du serveur source approprié, entouré de guillemets simples (par exemple,  **@SourceServerName = 'MySourceServer'**).  
  
8.  Sur le **requête** menu, sélectionnez **Execute**.  
  
    > [!IMPORTANT]
    >  En cas d'échec de la requête, vous devez résoudre le problème lié à la requête, puis recommencer cette procédure, à partir de l'étape 1, pour reconfigurer le système de destination.  
  
    > [!NOTE]
    >  Les travaux de restauration sur le système de destination tentent de recréer les journaux et les fichiers de données pour chaque base de données restaurée dans le même emplacement où ils se trouvaient sur le serveur de bases de données source.  
  
9. Sur le système de destination dans **SQL Server Management Studio**, développez **l’Agent SQL Server**, développez **travaux**.  
  
     Dans le volet de détails, il existe trois nouveaux travaux :  
  
    -   **Obtenir l’historique de sauvegarde des journaux de BizTalk Server**  
  
         Ce travail BizTalk déplace des enregistrements d'historique de sauvegarde de la source vers la destination. Par défaut, ce travail est planifié pour être exécuté toutes les minutes. Il est exécuté aussi souvent que possible afin de déplacer des enregistrements de l'historique depuis la source vers la destination En cas de défaillance du système source, le serveur identifié comme système de destination continue de traiter les enregistrements de l'historique déjà importés.  
  
    -   **Restauration de bases de données de copie des journaux de serveur BizTalk Server**  
  
         Ce travail BizTalk restaure les fichiers de sauvegarde des bases de données indiquées pour la source vers le serveur de destination. Par défaut, ce travail est planifié pour être exécuté toutes les minutes. Ce travail est exécuté en permanence, tant que des fichiers de sauvegarde sont à restaurer. Pour plus de précautions, vous pouvez exécuter ce travail une fois de plus pour vous assurer qu'il est bien fait.  
  
    -   **ENVOI des journaux de restauration jusqu'à une marque**  
  
         Ce travail BizTalk restaure toutes les bases de données jusqu'à une marque dans la dernière sauvegarde du journal. Cela garantit la cohérence transactionnelle de toutes les bases de données. En outre, ce travail recrée, sur le système de destination, tous les travaux de l'Agent SQL Server qui étaient sur le système source.  
  
    > [!IMPORTANT]
    >  Vous devez surveiller ces travaux pour vous assurer qu'ils n'échouent pas.  
  
10. Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], accédez au dossier suivant :  
  
     ordinateur 32 bits : %SystemDrive%\Program Files\Microsoft BizTalk Server \<version\>\Schema\Restore  
  
     ordinateur 64 bits : %SystemDrive%\Program Files (x86) \Microsoft BizTalk Server \<version\>\Bins32\Schema\Restore  
  
11. Avec le bouton droit **SampleUpdateInfo.xml**, puis sélectionnez **modifier**. Procédez comme suit :  
  
    -   Remplacez toutes les instances de **« SourceServer »** avec le nom du système source.  
  
    -   Remplacez toutes les instances de **« DestinationServer »** avec le nom du système de destination.  
  
    > [!IMPORTANT]
    >  Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.  
  
    > [!NOTE]
    >  Si vous avez renommé une des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez également mettre à jour les noms de base de données dans le fichier XML.  
  
    > [!NOTE]
    >  Si vous avez configuré l’analyse BAM, vous devez ajouter les lignes suivantes dans le **OtherDatabases** section de la **SampleUpdateInfo.xml** fichier pour les bases de données BAMAlertsApplication et BAMAlertsNSMain :   
    > `<Database Name="BAM Alerts Application DB" oldDBName="BAMAlertsApplication" oldDBServer="SourceServer" newDBName=" BAMAlertsApplication" newDBServer="DestinationServer"/>`  
    > `<Database Name="BAM Alerts Instance DB" oldDBName="BAMAlertsNSMain" oldDBServer="SourceServer" newDBName="BAMAlertsNSMain" newDBServer="DestinationServer"/>`  
    >   
    >  Si vous avez modifié le nom par défaut de ces deux bases de données, utilisez les noms de bases de données réels.  
  
12. Si vous avez plusieurs bases de données MessageBox dans votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système, ajouter une ligne messageboxdb supplémentaire à la liste, puis définissez **IsMaster = « 0 »** pour les bases de données non-master.  
  
13. Si vous utilisez l'analyse BAM ou le moteur de règles, supprimez les commentaires dans ces lignes, si nécessaire.  
  
14. Si vous avez des bases de données personnalisées, ajoutez-les sous la  **\<OtherDatabases\>**  section. Consultez [comment sauvegarder des bases de données personnalisées](../core/how-to-back-up-custom-databases.md).  
  
15. Lorsque vous avez fini de modifier le fichier, enregistrez-le et fermez-le.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Comment faire pour restaurer vos bases de données](../core/how-to-restore-your-databases.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [Comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md)   
 [Comment sauvegarder des bases de données personnalisées](../core/how-to-back-up-custom-databases.md)