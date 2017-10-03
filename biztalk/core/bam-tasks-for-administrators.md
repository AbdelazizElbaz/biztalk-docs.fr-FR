---
title: "Tâches d’analyse BAM pour les administrateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d9ae9a6-50fa-4f82-8e48-8dffa55c127f
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b529a0510ee56a92d3957a84a91d635666016f1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-tasks-for-administrators"></a>Tâches BAM pour les administrateurs 
Cette rubrique décrit les tâches typiques que les administrateurs BAM sont amenés à effectuer dans le cadre de la gestion de l'infrastructure BAM.  
  
## <a name="configuring-bam"></a>Configuration de l'analyse BAM  
 La configuration initiale de l'analyse BAM est effectuée avec l'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cet Assistant permet aux administrateurs d'effectuer les tâches suivantes :  
  
-   Activer les outils d'analyse BAM  
  
-   Activer SQL Server Analysis Services pour les agrégations BAM  
  
-   Indiquer le nom du serveur et des bases de données utilisés par les outils d'analyse BAM  
  
-   Activer les services de notification SQL Server pour les alertes BAM  
  
-   Indiquer le compte utilisé pour exécuter le service de notification BAM  
  
-   Indiquer le serveur SMTP utilisé pour envoyer les alertes BAM  
  
-   Indiquer l'emplacement du fichier dans lequel les alertes BAM sont stockées  
  
-   Indiquer le nom du serveur SQL Server sur lequel résident les bases de données d'alertes BAM  
  
-   Indiquer le préfixe des noms de base de données d'alertes  
  
-   Activer le portail BAM sur un ordinateur  
  
-   Indiquer les comptes de service Web utilisés pour exécuter le portail BAM  
  
-   Indiquer les groupes Windows qui bénéficient d'un accès au portail BAM  
  
-   Spécifier l'emplacement du site Web du portail BAM  
  
 Pour plus d'informations sur l'utilisation de l'Assistant Configuration, voir les rubriques suivantes :  
  
-   [Configuration des alertes BAM à l’aide de la Configuration de BizTalk Server](http://msdn.microsoft.com/library/04d79f8c-9e7f-4ba8-83ce-f79c33fb8e60)  
  
-   [Configuration des outils BAM à l’aide de la Configuration de BizTalk Server](http://msdn.microsoft.com/library/075a1627-5bc2-488c-a88c-42c86cc8c3bb)  
  
-   [Configuration du portail BAM à l’aide de la Configuration de BizTalk Server](http://msdn.microsoft.com/library/8af7cccb-823e-48bd-9743-dfbba4bafa11)  
  
### <a name="distributed-notification-services"></a>Services de notification distribués  
 Configurer l'analyse BAM pour qu'elle s'exécute dans un environnement distribué permet d'améliorer les performances en matière de traitement des alertes et des notifications. Lorsque vous configurez l'analyse BAM, les rôles Fournisseur, Générateur et Distributeur des services de notification doivent se trouver sur des ordinateurs différents. En outre, vous devez installer les services de notification dans un environnement multiserveur.  
  
##### <a name="to-configure-distributed-notification-services"></a>Pour configurer les services de notification distribués  
  
1.  Installez [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] Notification Services. Pour plus d’informations sur les Services de Notification distribués, consultez le [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] documentation des Services de Notification à l’adresse [http://go.microsoft.com/fwlink/?LinkId=68095](http://go.microsoft.com/fwlink/?LinkId=68095).  
  
    > [!NOTE]
    >  Notification Services n'est pas inclus dans [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]. Si vous utilisez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], installez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services lorsque vous installez [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] en sélectionnant le **fournisseur d’alertes BAM pour les Services de Notification SQL** sous **supplémentaires Logiciel** sur la **Installation des composants** page de l’Assistant installation.  
  
2.  Pour créer la notification BAM service sur chaque ordinateur dans l’environnement distribué, exécutez C:\Program Files\Microsoft SQL Server\90\NotificationServices\9.0.242\bin\nscontrol register - nom bamalerts-server \<nom du serveur > - service - serviceusername \<compte_utilisateur_alertes > - servicepassword \<mot_de_passe > à partir d’une invite de commandes.  
  
3.  Modifiez le fichier de configuration de l'infrastructure BAM sur chaque ordinateur en cours de configuration pour les services de notification distribués. Pour obtenir le fichier de configuration, utilisez la **bm.exe get-config - FileName :\<fichier de sortie >** commande.  
  
4.  Modifiez le fichier de configuration pour qu'il référence les serveurs de l'environnement des services de notification distribués :  
  
    ```  
    <Property Name="GeneratorServerName">PFIDWYUK</Property>  
    <Property Name="ProviderServerName">PFIDWYUK</Property>  
    <Property Name="DistributorServerName">PFIDWYUK</Property>  
    ```  
  
5.  Utilisez la mise à jour de bm.exe-config - FileName :\<le fichier de configuration > pour mettre à jour la configuration BAM.  
  
6.  Redémarrez les services de notification sur tous les ordinateurs de l'environnement distribué.  
  
 Pour plus d’informations sur l’installation de BAM dans un environnement multiserveur, consultez [Installation Guides Related to BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582) et [installer et configurer analyse BAM (Business Activity Monitoring) d’un à plusieurs ordinateurs Environnement](http://go.microsoft.com/fwlink/p/?LinkID=208597).  
  
### <a name="moving-the-bam-primary-import-database"></a>Déplacement de la base de données importation principale BAM  
 À un moment ou à un autre, il sera nécessaire de déplacer la base de données d'importation principale BAM , par exemple, lorsque vous effectuez une mise à niveau du matériel ou procédez à une évolution verticale. Avant de déplacer la base de données, vous devez effectuer une opération de sauvegarde et de restauration. Pour plus d’informations sur ce processus, consultez [sauvegarde et restauration de BAM](../core/backing-up-and-restoring-bam.md).  
  
### <a name="working-with-bam-definitions"></a>Utilisation des définitions BAM  
 Les administrateurs peuvent intervenir de nombreuses façons sur les définitions BAM, et ce, principalement grâce à l'utilitaire de gestion de l'analyse BAM. Cet utilitaire permet d'effectuer les tâches suivantes :  
  
-   Modifier des activités : Vous pouvez utiliser la **déployer-all**, **mise à jour-all**, **remove-activity**, **set- actvitywindow** les commandes de l’utilitaire de gestion BAM Pour modifier les activités déployées.  
  
-   Appliquer des index aux tables d'activité pour améliorer les performances : Vous utilisez la **index créer** et **delete-index** commandes pour modifier les index d’activités.  
  
-   Définir la sécurité des vues : Vous pouvez utiliser la **-ajouter un compte** et **remove-account** commandes pour accorder aux utilisateurs droits d’accès à des vues.  
  
-   Configurer la navigation distribuée entre les activités : Vous utilisez la **enable-reference** et **disable-reference** commandes pour configurer la navigation distribuée des activités. Pour plus d’informations sur la navigation distribuée des activités, consultez [la gestion distribuée Navigation des activités distantes](../core/managing-distributed-navigation-of-remote-activities.md).  
  
-   Réaliser un audit des modifications : Vous pouvez répertorier les modifications apportées à l’infrastructure dynamique BAM à l’aide du **get-changes** commande.  
  
 Pour obtenir une description de toutes les commandes disponibles via l’utilitaire de gestion de l’analyse BAM, consultez [utilitaire de gestion BAM](../core/bam-management-utility.md). Pour obtenir des exemples d’utilisation de l’utilitaire de gestion BAM pour travailler avec les définitions BAM, consultez [gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md).  
  
## <a name="configuring-multiple-biztalk-groups-to-reference-a-single-bam-database"></a>Configuration de plusieurs groupes BizTalk pour qu'ils référencent une seule base de données BAM  
 Lors de la configuration BAM pour utiliser un nouveau ou existant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe, vous pouvez configurer le groupe pour utiliser les mêmes bases de données BAM qui sont déjà en cours d’utilisation par un autre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe.  Pour configurer l’analyse BAM de cette manière, vous devez effectuer les tâches suivantes :  
  
-   Obtenez les informations de configuration à partir de la base de données d'importation principale BAM à l'aide de l'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ces informations incluent notamment le nom du serveur et le nom de la base de données. Notez l'état des cases à cocher. Veillez à obtenir les informations de configuration figurant sur les pages Outils BAM et Alertes BAM  
  
-   Configurez l'analyse BAM pour le nouveau groupe, puis entrez exactement les mêmes informations que celles déjà configurées pour la table d'importation principale cible. Lorsque vous entrez les informations de configuration du nouveau groupe, utilisez toutes les informations recueillies à partir du groupe existant, à l'exception du champ Utilisateur d'alertes BAM, que vous devez laisser vide.  
  
## <a name="backing-up-and-restoring-bam"></a>Backing Up and Restoring BAM  
 En tant qu'administrateur, vous devriez vous préparer aux situations de reprise sur sinistre. Pour cela, sauvegardez les bases de données Analyse BAM, Analyse des suivis, Schémas en étoile BAM, Archives BAM et Importation principale BAM au cas où vous devriez les restaurer.  Pour plus d’informations sur la sauvegarde et restauration des bases de données BAM, consultez [sauvegarde et restauration de BAM](../core/backing-up-and-restoring-bam.md).  
  
## <a name="working-with-renamed-servers"></a>Utilisation des serveurs renommés  
 Lorsque vous renommez un serveur ou déplacez l’infrastructure BAM d'un serveur à un autre, vous devez mettre à jour les définitions BAM dans le classeur Excel.  
  
 Les scénarios dans lesquels vous avez besoin de mettre à jour le classeur sont  :  
  
-   un scénario intermédiaire dans lequel l'infrastructure BAM est déplacée vers une nouvelle base de données. Pour vous assurer que les classeurs Excel sont toujours fonctionnels, vous devez les redéployer ou les faire migrer, puis les remettre à jour.  
  
-   un scénario dans lequel l'ordinateur sur lequel est exécuté BizTalk Server est renommé. Cela nécessite la mise à jour les packages DTS et la source de données OLAP en plus de la mise à jour le classeur.  
  
 Il existe deux manières de mettre à jour le classeur Excel :  
  
-   Vous pouvez exécuter la commande de l'utilitaire de gestion de l'analyse BAM suivante à partir du nouveau serveur :  
  
     **BM.exe update-livedataworkbook-nom :\<classeur des données actives à la mise à jour >**  
  
    > [!NOTE]
    >  Vous pouvez également spécifier le nom du nouveau serveur et/ou le nom de base de données d’importation principale BAM : **bm.exe update-livedataworkbook-nom :\<classeur des données actives à la mise à jour > [-Server :\<serveur >] [-base de données :\< base de données >]**  
  
-   Vous pouvez aussi mettre à jour le classeur de données Excel dans Excel :  
  
    1.  Ouvrez le classeur que vous voulez mettre à jour.  
  
    2.  Dans le menu BAM, cliquez sur **connexion Db BAM**.  
  
    3.  Entrez le nom du nouveau serveur et celui de la base de données d'importation principale BAM.  
  
## <a name="managing-alerts"></a>Gestion des alertes  
 En tant qu'administrateur, vous pouvez gérer les alertes de diverses façons :  
  
 Vous pouvez utiliser l'utilitaire de gestion de l'analyse BAM pour déployer et supprimer les alertes. Vous pouvez également vous servir de l'utilitaire pour ajouter et supprimer des abonnements ainsi que pour activer ou désactiver des alertes. Pour plus d’informations sur l’utilisation de l’utilitaire de gestion de l’analyse BAM, consultez [utilitaire de gestion BAM](../core/bam-management-utility.md), [gestion de la sécurité BAM](../core/managing-bam-security.md), et [la gestion des définitions BAM](../core/managing-bam-definitions.md).  
  
 Vous pouvez également créer et supprimer des alertes par l'intermédiaire du portail BAM.  Pour plus d’informations sur la création d’alertes à l’aide du portail BAM, consultez [recherches d’activité dans le portail BAM](../core/activity-searches-in-the-bam-portal.md).  
  
### <a name="cleaning-up-the-alerts-chronicle-table"></a>Nettoyage de la table des chroniques des alertes  
 Si des alertes BAM sont configurées, un travail SQL est créé pour chaque vue d'activité créée. Le travail est nommé selon le modèle suivant :  
  
 bam_\<nom de la vue > _\<vue d’activité > _DelAlertHistJob  
  
 Ce travail nettoie les données pour les alertes d’instance spécifié d’audit \<vue d’activité > dans la table Bam_Metadata_AlertChronicle. Si vous avez défini des alertes d'instance sur cette vue d'activité en particulier, une nouvelle ligne est ajoutée à cette table à chaque déclenchement de l'alerte.  
  
 Vous pouvez exécuter ce travail manuellement pour nettoyer la table ou planifier son exécution en fonction des besoins de votre application ou de votre environnement.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion BAM](../core/managing-bam.md)