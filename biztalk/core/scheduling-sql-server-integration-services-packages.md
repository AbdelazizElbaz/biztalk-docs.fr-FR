---
title: Planification de SQL Server Integration Services Packages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037ae2cf-c352-4823-95df-9a723f2b5a81
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17d8518a8c74f1fef77cf713852f1dfc87c8ef23
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="scheduling-sql-server-integration-services-packages"></a>Planification des packages SQL Server Integration Services
Les utilisateurs créent les vues BAM en fonction des données stockées dans un cube OLAP (Online Analytical Processing). Le package Integration Services de mise à jour du cube actualise les données du cube afin que les données affichées dans les vues OLAP soient correctes.  
  
 Vous devez exécuter ce package au moins une fois pour que les vues OLAP fonctionnent. Pour une maintenance continue, vous devez planifier une exécution régulière de ce package.  
  
> [!IMPORTANT]
>  Si vous avez restauré la base de données de schémas en étoile BAM ou arrêté [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] avant d'exécuter le package Integration Services de mise à jour du cube, vous devez actualiser les sources de données dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager ou redémarrer le service OLAP afin que le package puisse être exécuté correctement.  
  
 Vous pouvez planifier l'exécution d'un package enregistré à un moment précis, ponctuellement ou à intervalles réguliers. Exemple :  
  
-   Tous les jours à minuit.  
  
-   chaque semaine, le dimanche, à 6h00 ;  
  
-   le premier jour du mois, ou le dernier.  
  
 Un package planifié est exécuté par [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de la même façon qu'un travail.  
  
 Pour plus d’informations sur l’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages, consultez [http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738).  
  
> [!NOTE]
>  Par défaut, la journalisation pour l’archivage et la mise à jour de cube des packages BAM SSIS est activée et stockée dans la base de données msdb. Au fil du temps, cette fonctionnalité peut créer un volume considérable de données de journal des événements SSIS en raison d’un grand nombre d’activités BAM ou d’une exécution fréquente de packages SSIS appartenant à l’analyse BAM. Pour résoudre ce problème, vous pouvez supprimer les anciennes entrées de journal, car celles-ci sont principalement utilisées à des fins de débogage.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter ces procédures, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
### <a name="to-run-the-cube-update-integration-services-package"></a>Pour exécuter le package Integration Services de mise à jour du cube  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue le **type de serveur** la liste déroulante, sélectionnez **Integration Services**.  
  
3.  Dans le **nom du serveur** liste déroulante, sélectionnez le nom du serveur sur lequel vous exécutez le package.  
  
4.  Dans le **authentification** liste déroulante, sélectionnez le type d’authentification que vous utilisez pour vous connecter au serveur.  
  
5.  Si nécessaire, tapez votre nom d’utilisateur et un mot de passe.  
  
6.  Cliquez sur **Se connecter**.  
  
7.  Dans l’arborescence de la console, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.  
  
8.  Cliquez sur le **BAM_AN_\<nom de la vue\>**  du package, puis cliquez sur **exécuter le Package**.  
  
### <a name="to-run-the-maintaining-bam-data-integration-services-package"></a>Pour exécuter le package Integration Services de maintenance des données BAM  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue le **type de serveur** la liste déroulante, sélectionnez **Integration Services**.  
  
3.  Dans le **nom du serveur** liste déroulante, sélectionnez le nom du serveur sur lequel vous exécutez le package.  
  
4.  Dans le **authentification** liste déroulante, sélectionnez le type d’authentification que vous utilisez pour vous connecter au serveur.  
  
5.  Si nécessaire, tapez votre nom d’utilisateur et un mot de passe.  
  
6.  Cliquez sur **Se connecter**.  
  
7.  Dans l’arborescence de la console, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.  
  
8.  Cliquez sur le **BAM_DM_\<nom de l’activité\>**  du package, puis cliquez sur **exécuter le Package**.  
  
### <a name="to-schedule-the-packages-to-run-regularly"></a>Pour planifier l'exécution régulière des packages  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue le **type de serveur** la liste déroulante, sélectionnez **moteur de base de données**.  
  
3.  Dans le **nom du serveur** liste déroulante, sélectionnez le nom du serveur sur lequel vous exécutez le package.  
  
4.  Dans le **authentification** liste déroulante, sélectionnez le type d’authentification que vous utilisez pour vous connecter au serveur.  
  
5.  Si nécessaire, tapez votre nom d’utilisateur et un mot de passe.  
  
6.  Cliquez sur **Se connecter**.  
  
7.  Dans l’arborescence de la console, développez votre serveur, puis sélectionnez **l’Agent SQL Server**.  
  
8.  Si **l’Agent SQL Server** est désactivé, cliquez sur **l’Agent SQL Server**, puis sélectionnez **Démarrer**.  
  
9. Avec le bouton droit **l’Agent SQL Server**, puis sélectionnez **nouveau travail**.  
  
10. Dans le **nouveau travail** boîte de dialogue, tapez un nom pour la tâche dans le **nom** zone de texte.  
  
11. Dans le **sélectionner une page** fenêtre, cliquez sur **étapes**, puis cliquez sur **nouveau**. Cette opération ouvre le **nouvelle étape du travail** boîte de dialogue.  
  
12. Dans le **nom de l’étape** texte, tapez le nom d’identification de l’étape.  
  
13. Dans le **Type** la liste déroulante, sélectionnez **Package SQL Server Integration Services** et dans le **source du Package** la liste déroulante, sélectionnez **magasin de packages SSIS** .  
  
14. Dans le **Server** liste déroulante, sélectionnez le serveur sur lequel vous exécutez la tâche.  
  
15. Cliquez sur le bouton de sélection de fichier pour le **Package** texte, sélectionnez le package que vous planifiez (soit la **BAM_DM_\<nom de l’activité\>**  ou **BAM_AN_ \<Nom de la vue\>**  package), puis cliquez sur **OK**.  
  
16. Dans le **sélectionner une page** fenêtre, cliquez sur **planifications**, puis cliquez sur **nouveau**. Cette opération ouvre le **nouvelle planification du travail** boîte de dialogue.  
  
17. Dans le **nom** zone de texte, tapez un nom pour la planification.  
  
18. Créez votre planification en vous servant des champs de fréquence.  
  
19. Cliquez sur **OK** pour enregistrer le travail.  
  
    > [!NOTE]
    >  Si BAM est configuré avec une instance de SQL Server autre que l'instance par défaut, le BAM_AN_POCube DTSPackage n'est pas planifié/exécuté correctement. Vous devez modifier le fichier de configuration pour autoriser la poursuite de l'exécution des packages. Pour plus d’informations, reportez-vous à la section « Modification du contenu du fichier Configuration » à [http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768).  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données BAM](../core/managing-bam-databases.md)