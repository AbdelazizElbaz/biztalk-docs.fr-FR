---
title: "Comment déplacer la Database1 d’importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, Primary Import database [BAM]
- Primary Import database [BAM], migrating
ms.assetid: fab13fea-5c35-4a9f-977d-cc45545c54b2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a63c556bfb95f4b22a3256540d3ecb336a17f7f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-move-the-bam-primary-import-database"></a>Déplacement de la base de données d'importation principale BAM
Cette procédure vous permet de déplacer la base de données d'importation principale BAM vers un autre serveur.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-move-the-bam-primary-import-database"></a>Pour déplacer la base de données d'importation principale BAM  
  
1.  Arrêtez tous les services BizTalk Server. Pour plus d’informations, consultez [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
2.  Arrêtez le service IIS.  
  
3.  Arrêtez le service de notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
        ```  
        Net stop NS$BamAlerts  
        ```  
  
4.  Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données d'importation principale BAM sur l'ancien serveur.  
  
5.  Copiez la base de données d'importation principale BAM sur le nouveau serveur SQL Server.  
  
6.  Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données d'importation principale BAM sur le nouveau serveur.  
  
7.  Sur un ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], accédez au dossier suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.  
  
8.  Avec le bouton droit **SampleUpdateInfo.xml**, puis cliquez sur **modifier**.  
  
9. Dans la section base de données primaire importation du fichier, remplacez **« SourceServer »** avec le nom du système source et puis remplacez **« DestinationServer »** avec le nom du système de destination.  
  
    > [!IMPORTANT]
    >  Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.  
  
    > [!NOTE]
    >  Si vous avez renommé les bases de données BizTalk Server, vous devez également mettre à jour comme il se doit les noms des bases de données.  
  
10. Supprimez les marques de commentaire dans les lignes suivantes du fichier XML :  
  
    ```  
    - <UpdateConfiguration>  
      <MessageBoxDB oldDBName="BizTalkMsgboxDb" oldDBServer="Server01" newDBName="BizTalkMsgboxDb" newDBServer="Server01" IsMaster="1" />   
      <TrackingDB oldDBName="BizTalkDTADb" oldDBServer="Server01" newDBName="BizTalkDTADb" newDBServer="Server01" />   
      <ManagementDB oldDBName="BizTalkMgmtDb" oldDBServer="Server01" newDBName="BizTalkMgmtDb" newDBServer="Server01" />   
    - <BAM>  
    - <DeploymentUnit Name="OldPrimaryImportDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="PrimaryImportDatabase">  
      <Property Name="ServerName">Server02</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="ArchivingDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMArchive</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="AnalysisDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMAnalysis</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="StarSchemaDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMStarSchema</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="Alert">  
      <Property Name="DBServer">Server01</Property>   
      <Property Name="InstanceDatabaseName">BAMAlerts</Property>   
      </DeploymentUnit>  
      </BAM>  
    - <OtherDatabases>  
      <Database Name="SSO" oldDBName="SSODB" oldDBServer="Server01" newDBName="SSODB" newDBServer="Server01" />   
      </OtherDatabases>  
      </UpdateConfiguration>  
    ```  
  
11. Lorsque vous avez terminé la modification du fichier, enregistrez-le et fermez-le.  
  
12. Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
13. À l'invite de commandes, accédez au répertoire suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\Restore.  
  
14. À l'invite de commandes, tapez :  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
15. Mettez à jour la référence à la base de données d'importation principale BAM dans tous les fichiers Microsoft Excel de données actives BAM. Pour chaque fichier :  
  
    1.  Ouvrez le fichier Excel de données actives. Le nom de fichier se termine par _LiveData.xls.  
  
    2.  Sur le **BAM** menu, cliquez sur **connexion DB BAM**.  
  
    3.  Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez la base de données SQL Server et BAMPrimaryImport, puis cliquez sur **OK**.  
  
    4.  Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.  
  
    5.  Dans le menu **Fichier** , cliquez sur **Enregistrer**.  
  
16. Mettez à jour le nom du serveur et celui de la base de données dans tous les lots DTS de l'analyse BAM dotés du préfixe « BAM_AN_ » ou « BAM_DM_ » en suivant la procédure ci-dessous :  
  
    1.  Sur le serveur hébergeant l'analyse BAM, ouvrez SQL Server Enterprise Manager.  
  
    2.  Ouvrez le **Data Transformation Services** dossier.  
  
    3.  Ouvrez le **lots locaux** dossier, puis ouvrez les packages DTS.  
  
    4.  Sur le **Package** menu, cliquez sur **propriétés**.  
  
    5.  Sur le **les Variables globales** , onglet de la mettre à jour les valeurs pour le serveur d’importation principale et la base de données.  
  
    6.  Modifiez les lignes suivantes de sorte qu'elles correspondent au nouveau serveur et à la nouvelle base de données :  
  
         PrimaryImportServer = «*\<nom_serveur\>*»  
  
         PrimaryImportDatabase = «*\<DatabaseName\>*»  
  
17. Démarrez tous les services BizTalk Server. Pour plus d’informations, consultez [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).  
  
18. Démarrez le service IIS.  
  
19. Démarrez le service de notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
        ```  
        Net start NS$BamAlerts  
        ```  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données BizTalk Server](../core/moving-biztalk-server-databases.md)