---
title: "Comment activer la Validation de l’archivage automatique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, archives [Tracking database]
- archiving [Tracking database], validating archive
ms.assetid: 406ca54a-6b1f-4bdb-9bad-bea5ea0f6e66
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e654d22a08a7b07210ded9c319953c288065927a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-automatic-archive-validation"></a>Activation de la validation automatique de l'archivage
La validation d'archivage permet de valider les archives lors de leur création. Avant de pouvoir activer la validation d'archivage automatique, vous devez configurer un serveur de base de données secondaire, également appelé « serveur de validation ». Le processus d'archivage consistant en une simple sauvegarde, l'image réelle stockée sur le disque peut être altérée suite à une défaillance matérielle.  
  
 La fonction de validation d'archivage vous permet de vous assurer que l'archive (la sauvegarde) a été correctement créée et peut être restaurée. Chaque nouvelle création d'archive est notifiée au serveur de validation. Le serveur de validation tente de restaurer l'archive. Le serveur de validation doit être une autre instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], différente de celle dans laquelle le travail s'exécute. La version de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur la validation de serveur doit être la même version que le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] utilisé pour héberger les bases de données.  
  
 Si la restauration s'effectue correctement, le serveur de validation communique cette information à la base de données des suivis BizTalk (BizTalkDTADb). La purge des données n'a lieu qu'une fois la restauration correctement terminée.  
  
 Si la restauration ne s'effectue pas correctement, le serveur de validation communique cette information à la base de données des suivis BizTalk (BizTalkDTADb). Le travail de purge crée une autre archive et attend la validation de la nouvelle archive. Ceci vous évite toute perte de données de suivi due à une archive endommagée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
### <a name="to-enable-automatic-archive-validation"></a>Activation de la validation de l'archivage automatique  
  
1.  Sur le serveur de validation, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio** .  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] où vous pouvez valider l’archive en effectuant un test du processus de restauration, puis cliquez sur **connexion** pour se connecter à la serveur SQL Server approprié.  
  
    > [!NOTE]
    >  Ce serveur ne doit pas être un autre serveur de base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], car cela réduit les performances du système lors de la validation de l'archivage.  
  
3.  Dans **Microsoft SQL Server Management Studio**, cliquez sur **fichier**, cliquez sur **ouvrir**, puis cliquez sur **fichier**.  
  
4.  Dans le **ouvrir le fichier** boîte de dialogue, cliquez sur Parcourir pour le script SQL suivant :  
  
    ```  
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\BTS_Tracking_ValidateArchive.sql  
    ```  
  
    > [!NOTE]
    >  Vous aurez peut-être besoin de copier le script de l'ordinateur qui exécute [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur le serveur de validation.  
  
5.  Cliquez sur le **requête** menu, puis sur **Execute**.  
  
    > [!NOTE]
    >  Le script BTS_Tracking_ValidateArchive.sql fonctionne uniquement si le dossier dans lequel vous archivez votre base de données des suivis BizTalk (BizTalkDTADb) est un partage réseau.  
  
     Le script BTS_Tracking_ValidateArchive.sql crée un travail SQL Server Agent nommé ValidateArchive.  
  
6.  Le processus d’archivage et de purge pouvant utiliser ou met à jour des bases de données de différents serveurs SQL Server, vous devez donc définir des serveurs liés entre les instances de SQL Server concernées. Dans **SQL Server Management Studio**, double-cliquez sur **objets serveur**, avec le bouton droit **des serveurs liés**, puis cliquez sur **nouveau serveur lié**.  
  
     Vous devez configurer un serveur lié entre :  
  
    -   chacune de vos bases de données MessageBox BizTalk (BizTalkMsgBoxDb) et la base de données des suivis BizTalk (BizTalkDTADb) si celles-ci résident sur des serveurs différents ;  
  
    -   la base de données des suivis BizTalk (BizTalkDTADb) et le serveur de validation pour la validation de l'archivage.  
  
    -   Les comptes de service de l'Agent SQL Server sur l'ordinateur qui héberge la base de données MessageBox BizTalk (BizTalkMsgBoxDb) doivent disposer des autorisations db_datareader et db_datawriter pour la base de données des suivis BizTalk (BizTalkDTADb) qui réside sur le serveur lié.  
  
    > [!NOTE]
    >  Le compte utilisé pour exécuter le travail doit disposer des privilèges de l'opérateur de base de données (DBO, Database Operator) sur les deux bases de données.  
  
7.  Dans le **nouveau serveur lié** boîte de dialogue le **général** page **serveur lié**, entrez le nom du serveur que vous voulez lier à.  
  
     Il peut s'agir, par exemple, du serveur hébergeant la base de données MessageBox BizTalk (BizTalkMsgBoxDb), la base de données des suivis BizTalk (BizTalkDTADb) ou le serveur de validation.  
  
8.  Sous **type de serveur**, cliquez sur **SQL Server**, puis cliquez sur **OK**.  
  
9. Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.  
  
10. Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **ValidateArchive**, puis cliquez sur **propriétés**.  
  
11. Dans le **propriétés du travail - ValidateArchive** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.  
  
12. Dans le **liste des étapes du travail**, cliquez sur **valider**, puis cliquez sur **modifier**.  
  
13. Sur le **général** page, dans le **commande** zone, dans la commande, **exec dtasp_ValidateArchive null null**, remplacez null, null avec le nom du serveur hébergeant le BizTalk Suivi de base de données, entouré de guillemets, suivis du nom de la base de données des suivis BizTalk, entouré de guillemets, simples, puis cliquez sur **OK**. Exemple :  
  
     **EXEC dtasp_ValidateArchive '**  *\<TrackingServerName\>*  **','**  *\<TrackingDatabaseName\>*  **'**  
  
> [!NOTE]
>  Le travail ValidateArchive ne comporte pas de planification et vous ne devez pas configurer de planification pour ce travail. Le travail de purge et d'archivage de la base de données des suivis (BizTalkDTADb) démarre ce travail automatiquement lors de la création d'une archive.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)