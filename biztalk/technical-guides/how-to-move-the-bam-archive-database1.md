---
title: "Comment déplacer la Database1 archives BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e371321c-6b8d-4be6-a6d2-926f6218db01
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 383aef74519f7527383d9f681f83ace2e515eba7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-move-the-bam-archive-database"></a>Déplacement de la base de données des archives BAM
Cette procédure vous permet de déplacer la base de données des archives BAM vers un autre serveur.  À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données des archives BAM implique deux étapes principales :  
  
-   [Déplacement de la base de données des archives BAM](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_MovingArch)  
  
-   [Mise à jour des références à la nouvelle base de données des archives BAM](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArch)  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
##  <a name="BKMK_MovingArch"></a>Déplacement de la base de données des archives BAM  
 Effectuez les opérations dans la procédure suivante pour déplacer la base de données des archives BAM.  
  
#### <a name="to-move-the-bam-archive-database"></a>Pour déplacer la base de données des archives BAM  
  
1.  Arrêtez toute analyse BAM cube mise à jour et les données maintenance SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données des archives BAM.  
  
2.  Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
3.  Arrêtez le service IIS.  
  
4.  Arrêtez le service de Notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
         **Net stop NS$ BamAlerts**  
  
5.  Sauvegardez la base de données des archives BAM sur l’ancien serveur. Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la sauvegarde d’une base de données.  
  
6.  Copier la base de données des archives BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
7.  Restaurez la base de données des archives BAM sur le nouveau serveur. Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la façon de restaurer une base de données.  
  
##  <a name="BKMK_UpdateArch"></a>Mise à jour des références à la nouvelle base de données des archives BAM  
 Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références à la base de données des archives BAM nouvelle. Les références suivantes doivent être mises à jour :  
  
-   Mettre à jour la configuration BAM avec les nouveaux noms de base de données et le serveur. Consultez [pour mettre à jour la configuration BAM](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchConfig).  
  
-   Mettre à jour les nouveaux noms de serveur et de base de données dans tous les packages SSIS d’analyse BAM. Consultez [pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS](../technical-guides/how-to-move-the-bam-archive-database1.md#BKMK_UpdateArchSSIS).  
  
###  <a name="BKMK_UpdateArchConfig"></a>Pour mettre à jour la configuration BAM  
  
1.  Obtenez une copie du fichier .xml utilisé pour restaurer BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :  
  
        -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :  
  
             **% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**  
  
        -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :  
  
             **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
    3.  À l'invite de commandes, tapez :  
  
         **BM.exe get-config –filename:BAMConfiguration.xml-server :\<nom_serveur\> -base de données :\<base de données\>**  
  
        > [!NOTE]  
        >  Lorsque vous exécutez cette commande, remplacez le nom actuel du serveur à partir duquel obtenir les informations de configuration pour \<nom_serveur\> et remplacez-le par le nom réel de la base de données à partir duquel obtenir les informations de configuration \<base de données\>. Pour plus d’informations sur l’utilisation de l’utilitaire de gestion BAM (BM), consultez [Infrastructure de gestion des commandes](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
2.  Modifiez le fichier BAMConfiguration.xml et définissez la **nom_serveur** dans la `<DeploymentUnit Name="ArchivingDatabase">` section pour le nouveau nom du serveur.  
  
3.  Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.  
  
4.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
5.  Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :  
  
         **% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**  
  
    -   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :  
  
         **%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**  
  
6.  À l'invite de commandes, tapez :  
  
     **BM.exe update-config-FileName:BAMConfiguration.xml**  
  
###  <a name="BKMK_UpdateArchSSIS"></a>Pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS  
  
1.  Mettre à jour les noms de serveur et de base de données dans tous les lots analyse BAM SSIS qui sont précédés de « BAM_DM_ ». Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.  
  
2.  Créez un projet dans SQL Server Business Intelligence Development Studio. Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.  
  
3.  Dans le **nouveau projet** boîte de dialogue le **Types de projets** , cliquez sur **projets Business Intelligence**. Dans le volet droit, dans le **modèles** , cliquez sur **projet Integration Services**, puis cliquez sur **OK**.  
  
4.  Dans le **projet Integration Services** avec le bouton droit de la boîte de dialogue Explorateur de solutions, **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.  
  
5.  Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient les packages BAM_DM_ *.  
  
6.  Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.  
  
7.  Dans le **Package SSIS** boîte de dialogue, sélectionnez le package que vous souhaitez mettre à jour, cliquez sur **OK**, puis cliquez sur **OK**.  
  
     À présent, le package s'affiche dans l'Explorateur de solutions.  
  
8.  Dans l’Explorateur de solutions, double-cliquez sur le package que vous avez ajouté à l’étape précédente. Dans **gestionnaires de connexions** onglet (disponible dans la moitié inférieure de l’écran), double-cliquez sur le nombre de sources de données 2 (base de données BAMArchive).  
  
9. Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Répétez cette opération pour le numéro de source de données 3 (base de données MSDB).  
  
10. Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs de la **ArchivingDatabase**, **ArchivingServer** , **PrimaryImportDatabase**, et **PrimaryImportServer** variables. Vous devez mettre à jour les valeurs pour pointer vers le nouveau serveur et base de données.  
  
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
  
21. Démarrer toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services. Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
22. Démarrez le service IIS.  
  
23. Démarrez le service de Notification des alertes BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, tapez :  
  
         **Net start NS$ BamAlerts**  
  
24. Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.  
  
> [!TIP]  
>  Comme une bonne pratique, vous devez également déplacer les packages SSIS BAM_DM_ * pour le serveur qui héberge la base de données BAMArchive.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données](../technical-guides/moving-databases.md)