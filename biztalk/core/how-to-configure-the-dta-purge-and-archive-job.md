---
title: Comment faire pour configurer la DTA Purge et archivage du projet | Documents Microsoft
ms.custom: 
ms.date: 2015-11-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- purging, configuring
- DTA Purge and Archive job, configuring
- archiving [Tracking database], DTA Purge and Archive job
- archiving [Tracking database], configuring
- purging, DTA Purge and Archive job
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f4985e657f26945aa2fdc168b273dbfdb159efc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-dta-purge-and-archive-job"></a>Configuration du travail de purge et d'archivage DTA
Avant d'archiver ou de purger des données de la base de données des suivis BizTalk (BizTalkDTADb), vous devez configurer le travail de purge et d'archivage DTA (BizTalkDTADb). Cette tâche est configurée pour appeler la procédure stockée dtasp_BackupAndPurgeTrackingDatabase, qui utilise les six paramètres que vous devez configurer.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server comme suit.  
  
### <a name="to-configure-the-dta-purge-and-archive-job"></a>Pour configurer le travail de purge et d'archivage DTA  
  
1.  Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), ouvrez **SQL Server Management Studio**.  
  
2.  Dans **se connecter au serveur**, entrez le nom du serveur SQL server où le suivi BizTalk (BizTalkDTADb) de base de données réside, entrez le type d’authentification, puis sélectionnez **connexion** pour se connecter à SQL server.  
  
3.  Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.  
  
4.  Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.  
  
6.  Dans le **liste des étapes du travail**, cliquez sur **archiver et purger**, puis cliquez sur **modifier**.  
  
7.  Sur le **général** page, dans le **commande** zone, modifiez les paramètres ci-dessous comme il convient, puis cliquez sur **OK**.  
  
    -   @nLiveHourstinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées. Il s’agit d’un paramètre obligatoire sans valeur par défaut.  
  
    -   @nLiveDaystinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées. Intervalle par défaut est 0 jour.  
  
        > [!NOTE]
        >  Pour les besoins de la base de données des suivis BizTalk (BizTalkDTADb), la somme du nombre d'heures et du nombre de jours d'activité est égale aux données de la fenêtre active que vous souhaitez conserver dans votre environnement BizTalk Server. Les données associées à une instance achevée et antérieures aux données de la fenêtre active sont supprimées.  
  
    -   @nHardDeleteDaystinyint : toutes les données (même si elle est incomplète) antérieurs à cela sera supprimé. L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active. Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb). Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé. Valeur par défaut est 0 jour.  
  
    -   @nvcFoldernvarchar (1024) : dossier dans lequel placer les fichiers de sauvegarde. Il s’agit d’un paramètre obligatoire sans valeur par défaut.  
  
    -   @nvcValidatingServersysname : serveur sur lequel la validation est exécutée. La valeur NULL indique qu'aucune validation n'est en cours d'exécution. La valeur par défaut est NULL.  
  
    -   @fForceBackupint, valeur par défaut est 0. Elle est réservée à un usage ultérieur.  
  
     La commande modifiée doit ressembler à ce qui suit. Dans l’exemple suivant, il est de 1 heure, une fenêtre active et de purge de 1 jour :  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0  
    ```  
  
8.  Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **général**, sélectionnez le **activé**case à cocher, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)