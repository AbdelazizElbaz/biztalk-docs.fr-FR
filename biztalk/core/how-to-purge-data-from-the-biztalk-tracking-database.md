---
title: "Purge des données de la base de données de suivi de BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, purging
- purging
- DTA Purge and Archive job, purging data
- purging, DTA Purge and Archive job
ms.assetid: cdf12866-442d-4c1f-b10f-ebf8d665d521
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01c56629aaa0934010ba79637b4e4a134bf29f26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-purge-data-from-the-biztalk-tracking-database"></a>Purge des données de la base de données des suivis BizTalk
Lors de la purge des données de la base de données des suivis BizTalk (BizTalkDTADb), le travail de purge et d'archivage DTA implique l'élimination de divers types d'informations de suivi de cette base de données, comme les données de suivi du moteur de règles, les données relatives aux instances de service et de message ou relatives aux événements d'orchestration.  
  
> [!IMPORTANT]
>  Cette procédure ne permet pas d'archiver la base de données des suivis BizTalk (BizTalkDTADb).  
  
> [!WARNING]
>  Si une exception est interceptée et traitée dans une orchestration alors que le suivi n'est pas activé, une instance de suivi orpheline dotée d'un état Démarré et d'informations sur l'exception peut être insérée dans la base de données des suivis BizTalk (BizTalkDTADb). Cet enregistrement demeure après la purge de la base de données.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-purge-data-from-the-biztalk-tracking-database"></a>Pour purger les données de la base de données des suivis BizTalk  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL où se trouve la base de données des suivis BizTalk (BizTalkDTADb) et le type d’authentification approprié, puis cliquez sur **connexion** à se connecter à SQL Server.  
  
3.  Dans **Microsoft SQL Server Management Studio**, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.  
  
4.  Dans le **détails de l’Explorateur d’objets** volet, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.  
  
6.  Dans le **liste des étapes du travail**, cliquez sur **archiver et purger**, puis cliquez sur **modifier**.  
  
7.  Dans le **propriétés étape du travail - Archive and Purge** boîte de dialogue le **général** page, dans le **commande** , changez **exec dtasp_ BackupAndPurgeTrackingDatabase** à **exec dtasp_PurgeTrackingDatabase**.  
  
    > [!CAUTION]
    >  Le **exec dtasp_PurgeTrackingDatabase** procédure stockée n’archive pas la base de données des suivis BizTalk (BizTalkDTADb). N'ayez recours à cette option que si vous êtes sûr de ne plus avoir besoin des données de suivi archivées.  
  
8.  Dans le **commande** zone, modifiez les paramètres ci-dessous comme il convient, puis cliquez sur **OK**.  
  
    -   @nHourstinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées.  
  
    -   @nDaystinyint : toute instance terminée datant de plus de (en heures) + (jours) seront supprimées avec toutes les données associées. Le délai par défaut est de 1 jour.  
  
    -   @nHardDaystinyint : toutes les données antérieures à cette date seront supprimées, même si les données sont incomplètes. L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active. Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb). Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé.  
  
    -   @dtLastBackup: Affectez la valeur **GetUTCDate()** pour purger les données à partir de la base de données des suivis BizTalk (BizTalkDTADb). Lorsque la valeur **NULL**, données ne sont pas purgées à partir de la base de données.  
  
     Le script modifié doit être similaire à ceci :  
  
    ```  
    declare @dtLastBackup datetime set @dtLastBackup = GetUTCDate() exec dtasp_PurgeTrackingDatabase 1, 0, 1, @dtLastBackup  
    ```  
  
9. Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, cliquez sur **général**, sélectionnez le **activé**case à cocher, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)