---
title: "Purger les données de la base de données de suivi de BizTalk | Documents Microsoft"
description: "Configurer la procédure stockée dtasp_PurgeTrackingDatabase pour purger la base de données de suivi (BizTalkDTADB) dans BizTalk Server"
ms.custom: 
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06217a7d5012eb402698ad35e76ccfc886952f6e
ms.sourcegitcommit: 5e6ef63416e8885a5ee91bd65618a842b3a0cc54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2017
---
# <a name="purge-data-from-the-biztalk-tracking-database"></a>Purge des données de base de données de suivi BizTalk
Lors de la purge des données de la base de données des suivis BizTalk (BizTalkDTADb), le travail de purge et d'archivage DTA implique l'élimination de divers types d'informations de suivi de cette base de données, comme les données de suivi du moteur de règles, les données relatives aux instances de service et de message ou relatives aux événements d'orchestration.  
  
> [!IMPORTANT]
>  Cette procédure ne permet pas d'archiver la base de données des suivis BizTalk (BizTalkDTADb).  
  
> [!WARNING]
>  Si une exception est interceptée et traitée dans une orchestration alors que le suivi n'est pas activé, une instance de suivi orpheline dotée d'un état Démarré et d'informations sur l'exception peut être insérée dans la base de données des suivis BizTalk (BizTalkDTADb). Cet enregistrement demeure après la purge de la base de données.  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server pour effectuer cette procédure.  
  
## <a name="purge-data-from-the-biztalk-tracking-database"></a>Purge des données de la base de données des suivis BizTalk  
  
1.  Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), ouvrez **SQL Server Management Studio**. 
  
2.  Dans **se connecter au serveur**, entrez le nom du serveur SQL server où le suivi BizTalk (BizTalkDTADb) de base de données réside, entrez le type d’authentification, puis sélectionnez **connexion** pour se connecter à SQL server. 
  
3.  Double-cliquez sur **l’Agent SQL Server**, puis sélectionnez **travaux**.  
  
4.  Dans **détails de l’Explorateur d’objets**, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis sélectionnez **propriétés**.  
  
5.  Dans **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)**, sous **sélectionner une page**, sélectionnez **étapes**.  
  
6.  Dans **liste des étapes du travail**, sélectionnez **archiver et purger**, puis sélectionnez **modifier**.  
  
7.  Dans **propriétés étape du travail - Archive and Purge**, dans le **général** page, dans le **commande** , changez **exec dtasp_BackupAndPurgeTrackingDatabase** à **exec dtasp_PurgeTrackingDatabase**.  
  
    > [!CAUTION]
    >  Le **exec dtasp_PurgeTrackingDatabase** procédure stockée n’archive pas la base de données des suivis BizTalk (BizTalkDTADb). N'ayez recours à cette option que si vous êtes sûr de ne plus avoir besoin des données de suivi archivées.  
  
8.  Dans le **commande** zone, mettre à jour les paramètres suivants, puis sélectionnez **OK**.  
  
    -   @nHourstinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées.  
  
    -   @nDaystinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées. Le délai par défaut est de 1 jour.  
  
    -   @nHardDaystinyint : toutes les données antérieures à cette date seront supprimées, même si les données sont incomplètes. L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active. Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb). Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.  
  
    -   @dtLastBackup: Affectez la valeur **GetUTCDate()** pour purger les données à partir de la base de données des suivis BizTalk (BizTalkDTADb). Lorsque la valeur **NULL**, données ne sont pas purgées à partir de la base de données.  

    -  @fHardDeleteRunningInstancesint - valeur par défaut est 0. Lorsque cette propriété a la valeur 1, il supprime toutes les exécutant des instances de service antérieures à la @nHardDeleteDays valeur.  
    
        > [!NOTE] 
        > Le @fHardDeleteRunningInstances propriété est disponible à partir de [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), et [cumulés de BizTalk Server 2013 Mettre à jour 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).   

    Le script modifié ressemble à ce qui suit :  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup, 1  
    ```  
    
9. Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, sélectionnez **général**, sélectionnez le **activé**case à cocher, puis sélectionnez **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)
