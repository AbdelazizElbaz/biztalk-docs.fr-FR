---
title: "Comment déplacer la Database2 d’importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc4f2656-2faa-4503-9551-05e1b6eceb1a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd6abeeb04521e95b32b4d6007dcc7f1f532bdbb
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-bam-primary-import-database"></a>Déplacement de la base de données d'importation principale BAM
Cette procédure vous permet de déplacer la base de données d'importation principale BAM vers un autre serveur. À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données d’importation principale BAM implique deux étapes principales :  
  
-   [Déplacement de la base de données importation principale BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_MovingBAMPI)  
  
-   [Mise à jour des références à la nouvelle base de données importation principale BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
##  <a name="BKMK_MovingBAMPI"></a>Déplacement de la base de données importation principale BAM  
 Les étapes de la procédure suivante pour déplacer la base de données d’importation principale BAM.  
  
#### <a name="to-move-the-bam-primary-import-database"></a>Pour déplacer la base de données d'importation principale BAM  
  
1.  Arrêtez toute analyse BAM cube mise à jour et les données maintenance SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données d’importation principale BAM.  
  
2.  Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
3.  Arrêtez le service IIS.  
  
4.  Arrêtez le service de Notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
         **Net stop NS$ BamAlerts**  
  
5.  Sauvegardez la principale BAM importer la base de données sur l’ancien serveur. Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions sur la sauvegarde d’une base de données à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.  
  
6.  Copier la base de données d’importation principale BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
7.  Restaurez la base de données importation principale BAM sur le nouveau serveur. Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions relatives à la restauration d’une base de données à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.  
  
    > [!NOTE]  
    >  Si vous restaurez la base de données d'importation principale BAM à partir d'une sauvegarde, vous devez également restaurer les bases de données des archives BAM, de schémas en étoile BAM et d'analyse BAM à l'aide d'une sauvegarde antérieure à la sauvegarde principale BAM.  
  
##  <a name="BKMK_BAMPIRef"></a>Mise à jour des références à la nouvelle base de données importation principale BAM  
 Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références à la nouvelle base importation principale BAM. Les références suivantes doivent être mises à jour :  
  
-   Mettre à jour toutes les bases de données BizTalk avec le nouveau nom de serveur. Vous pouvez le faire en utilisant le script UpdateDatabase.vbs. Consultez [pour mettre à jour des bases de données BizTalk avec le nouveau nom de serveur](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB).  
  
-   Mettre à jour le fichier Web.config pour le portail BAM. Consultez [pour mettre à jour le fichier Web.config pour le portail BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config).  
  
-   Mettre à jour la référence à la base d’importation principale BAM dans tous les fichiers de données actives d’analyse BAM, Microsoft Excel. Consultez [pour mettre à jour la référence dans les fichiers de données actives d’analyse BAM, Microsoft Excel](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel).  
  
-   Mettre à jour les nouveaux noms de serveur et de base de données dans tous les packages SSIS d’analyse BAM. Consultez [pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg).  
  
-   Mettre à jour les nouveaux noms de serveur et de base de données dans des sources de données pour tous les cubes OLAP. Consultez [pour mettre à jour les noms de serveur et base de données dans des sources de données pour tous les cubes OLAP](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP).  
  
###  <a name="BKMK_UpdateDB"></a>Pour mettre à jour des bases de données BizTalk avec le nouveau nom de serveur  
  
1.  Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :  
  
         **% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\bins32\Schema\Restore**  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
2.  Avec le bouton droit **SampleUpdateInfo.xml**, puis cliquez sur **modifier**.  
  
3.  Ajoutez des marques de commentaire à toutes les sections de la base de données, à l'exception de BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert.  
  
4.  Dans le `OldPrimaryImportDatabase` section du fichier, pour le `ServerName` propriété, remplacez **SourceServer** avec le nom du serveur existant dans lequel se trouve la base de données.  
  
5.  Dans le `PrimaryImportDatabase` section du fichier, pour le `ServerName` propriété, remplacez **DestinationServer** avec le nom du serveur où vous avez déplacé la base de données d’importation principale BAM  
  
6.  BizTalkMgmtDb, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert sections, définir la « SourceServer » et « Serveur de Destination » pour le nom du serveur où se trouvent les bases de données.  
  
    > [!IMPORTANT]  
    >  Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.  
  
    > [!NOTE]  
    >  Si vous avez renommé l'une des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez également mettre à jour les noms des bases de données.  
  
7.  Lorsque vous avez terminé la modification du fichier, enregistrez-le et fermez-le.  
  
8.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
9. À l'invite de commandes, accédez au répertoire suivant :  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :  
  
         **% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Schema\Restore**  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**  
  
10. À l'invite de commandes, tapez :  
  
     **cscript UpdateDatabase.vbs SampleUpdateInfo.xml**  
  
###  <a name="BKMK_Config"></a>Pour mettre à jour le fichier Web.config pour le portail BAM  
  
1.  Sur un ordinateur exécutant BizTalk Server, la mise à jour les fichiers Web.config sous  **\<lecteur\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**. Mettre à jour les noms de serveur et de base de données dans la section suivante dans le fichier Web.config :  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
    </appSettings>  
    ```  
  
2.  Sur un ordinateur exécutant BizTalk Server, la mise à jour les fichiers Web.config sous  **\<lecteur\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**. Mettre à jour les noms de serveur et de base de données dans la section suivante dans le fichier Web.config :  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
      <add key="MaxResultRows" value="2000" />  
    </appSettings>  
    ```  
  
3.  Enregistrez et fermez les fichiers.  
  
###  <a name="BKMK_UpdateExcel"></a>Pour mettre à jour la référence dans les fichiers de données actives d’analyse BAM, Microsoft Excel  
  
1.  Ouvrez le fichier Excel de données actives. Le nom de fichier se termine par _LiveData.xls.  
  
2.  Sur le **BAM** menu, cliquez sur **connexion DB BAM**.  
  
3.  Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur et le BAMPrimaryImport de base de données, puis cliquez sur **OK**.  
  
4.  Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.  
  
5.  Dans le menu **Fichier** , cliquez sur **Enregistrer**.  
  
###  <a name="BKMK_UpdatePckg"></a>Pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS  
  
1.  Mettre à jour les noms de serveur et de base de données dans tous les lots analyse BAM SSIS qui sont précédés de « BAM_AN_ » ou « BAM_DM_ ». Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.  
  
2.  Créez un projet dans SQL Server Business Intelligence Development Studio. Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue le **Types de projets** , cliquez sur **projets Business Intelligence**. Dans le volet droit, dans le **modèles** , cliquez sur **projet Integration Services**, puis cliquez sur **OK**.  
  
4.  Dans le **projet Integration Services** avec le bouton droit de la boîte de dialogue Explorateur de solutions, **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.  
  
5.  Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient les packages BAM_AN_ * et BAM_DM_ *.  
  
6.  Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.  
  
7.  Dans le **Package SSIS** boîte de dialogue, sélectionnez le package que vous souhaitez mettre à jour, cliquez sur **OK**, puis cliquez sur **OK**.  
  
     À présent, le package s'affiche dans l'Explorateur de solutions.  
  
8.  Dans l’Explorateur de solutions, double-cliquez sur le package que vous avez ajouté à l’étape précédente. Dans **gestionnaires de connexions** onglet (disponible dans la moitié inférieure de l’écran), double-cliquez sur le nombre de sources de données 1 (base de données BAMPrimaryImport).  
  
9. Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur, puis cliquez sur **OK**.  
  
10. Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs de la **PrimaryImportDatabase** et  **PrimaryImportServer** variables. Vous devez mettre à jour les valeurs pour pointer vers le nouveau serveur et base de données.  
  
    > [!NOTE]  
    >  Répétez l’étape 4 et 10 pour tous les packages que vous souhaitez mettre à jour.  
  
11. Cliquez sur puis **fichier** menu, puis sur **Enregistrer tout**.  
  
12. Démarrez SQL Server Management Studio. Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur  **SQL Server Management Studio**.  
  
13. Dans le **se connecter au serveur** boîte de dialogue, à partir de la **Server** liste de type liste déroulante, sélectionnez **Integration Services**.  
  
14. Spécifiez le nom du serveur et les informations d’identification pour se connecter au serveur et cliquez sur **OK**.  
  
15. Dans le **l’Explorateur d’objets**, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.  
  
16. Dans le **détails de l’Explorateur d’objets** onglet, cliquez sur le package de mise à jour précédemment, puis sur **importer un Package**.  
  
17. Dans le **importer un Package** boîte de dialogue, à partir de la **emplacement du Package** la liste déroulante, sélectionnez **système de fichiers**.  
  
18. Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le fichier .dtsx pour le package que vous souhaitez importer, puis cliquez sur **ouvrir**.  
  
19. Cliquez dans la zone Nom du Package pour remplir automatiquement la zone.  
  
    > [!NOTE]  
    >  Répétez l’étape 16 à 19 pour tous les packages que vous souhaitez mettre à jour.  
  
20. Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.  
  
21. Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.  
  
###  <a name="BKMK_UpdateDSOLAP"></a>Pour mettre à jour les noms de serveur et base de données dans des sources de données pour tous les cubes OLAP  
  
1.  Mettre à jour les noms de serveur et de base de données dans des sources de données pour tous les cubes OLAP. Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, pour le **type de serveur** liste déroulante, sélectionnez **Analysis Services**, fournissez le nom du serveur, sélectionnez une méthode d’authentification (et fournir des informations d’identification si nécessaire), puis cliquez sur **connexion**.  
  
3.  Dans l’Explorateur d’objets, développez **bases de données**, développez **BAMAnalysis**, développez **des Sources de données**, puis double-cliquez sur une source de données.  
  
4.  Dans le **propriétés Source de données** boîte de dialogue, cliquez sur le bouton de sélection **(...)**  contre le **chaîne de connexion** propriété.  
  
5.  Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** , entrez le nom du serveur hébergeant la base de données, cliquez sur **OK**, puis cliquez sur  **OK**.  
  
6.  Démarrer toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
7.  Démarrez le service IIS.  
  
8.  Démarrez le service de Notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
         **Net start NS$ BamAlerts**  
  
9. Résoudre toutes les instances de suivi incomplètes.  Pour plus d’informations sur la résolution des instances d’activité BAM incomplètes, consultez [comment résoudre les Instances d’activité incomplètes](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données](../technical-guides/moving-databases.md)