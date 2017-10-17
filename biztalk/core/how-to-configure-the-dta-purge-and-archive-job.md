---
title: Configurer la Purge DTA et archiver le travail | Documents Microsoft
description: "Définir les paramètres du travail DTA Purge and Archive dans SQL Server Agent pour maintenir la base de données de suivi dans BizTalk Server"
ms.custom: 
ms.date: 10/11/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 156ccf9b-284f-4b96-a395-92936e8cebcf
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 149719b7eea50ce53c14298597c94729162d43b0
ms.sourcegitcommit: 1fb633fcf919ce3124405420a5d9faa79d9d508e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2017
---
# <a name="configure-the-dta-purge-and-archive-job"></a>Configurer la Purge DTA et les travaux d’archivage
Avant d'archiver ou de purger des données de la base de données des suivis BizTalk (BizTalkDTADb), vous devez configurer le travail de purge et d'archivage DTA (BizTalkDTADb). Cette tâche est configurée pour appeler la procédure stockée dtasp_BackupAndPurgeTrackingDatabase, qui utilise les six paramètres que vous devez configurer.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Connectez-vous avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server.  
  
## <a name="configure-the-dta-purge-and-archive-job"></a>Configurer la purge DTA et les travaux d’archivage  
  
1.  Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), ouvrez **SQL Server Management Studio**.  
  
2.  Dans **se connecter au serveur**, entrez le nom du serveur SQL server où le suivi BizTalk (BizTalkDTADb) de base de données réside, entrez le type d’authentification, puis sélectionnez **connexion** pour se connecter à SQL server.  
  
3. Double-cliquez sur **l’Agent SQL Server**, puis sélectionnez **travaux**.  
  
4.  Dans **détails de l’Explorateur d’objets**, avec le bouton droit **DTA Purge and Archive (BizTalkDTADb)**, puis sélectionnez **propriétés**.  
  
5.  Dans **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)**, sous **sélectionner une page**, sélectionnez **étapes**.  
  
6.  Dans le **liste des étapes du travail**, sélectionnez **archiver et purger**, puis sélectionnez **modifier**.  
  
7.  Dans **général**, dans le **commande** zone, mettre à jour les paramètres suivants, puis sélectionnez **OK**.  
  
    -   @nLiveHourstinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées. Il s’agit d’un paramètre obligatoire sans valeur par défaut.  
  
    -   @nLiveDaystinyint : toute instance terminée datant que les (heures) + (jours) seront supprimées avec toutes les données associées. Intervalle par défaut est 0 jour.  
  
        > [!NOTE]
        >  Pour les besoins de la base de données des suivis BizTalk (BizTalkDTADb), la somme du nombre d'heures et du nombre de jours d'activité est égale aux données de la fenêtre active que vous souhaitez conserver dans votre environnement BizTalk Server. Les données associées à une instance achevée et antérieures aux données de la fenêtre active sont supprimées.  
  
    -   @nHardDeleteDaystinyint : toutes les données (même si elle est incomplète) antérieurs à cela sera supprimé. L'intervalle de temps défini pour HardDeleteDays doit être supérieur à celui figurant dans les données de la fenêtre active. Celle-ci indique la durée de conservation souhaitée des données de suivi dans la base de données des suivis BizTalk (BizTalkDTADb). Tout élément plus ancien peut être sélectionné pour être archivé lors de la prochaine opération d'archivage, puis éliminé. Valeur par défaut est 0 jour.  
  
    -   @nvcFoldernvarchar (1024) : dossier dans lequel placer les fichiers de sauvegarde. Il s’agit d’un paramètre obligatoire sans valeur par défaut.  
  
    -   @nvcValidatingServersysname : serveur sur lequel la validation est exécutée. La valeur NULL indique qu'aucune validation n'est en cours d'exécution. La valeur par défaut est NULL.  
  
    -   @fForceBackupint, valeur par défaut est 0. Elle est réservée à un usage ultérieur.  
  
    -   @fHardDeleteRunningInstancesint - valeur par défaut est 0. Lorsque cette propriété a la valeur 1, il supprime toutes les exécutant des instances de service antérieures à la @nHardDeleteDays valeur. 
    
        > [!NOTE]
        > Le @fHardDeleteRunningInstances propriété est disponible à partir de [BizTalk Server 2016 Cumulative Update 1](https://support.microsoft.com/help/3208238/cumulative-update-1-for-microsoft-biztalk-server-2016), [BizTalk Server 2013 R2 Cumulative Update 6](https://support.microsoft.com/en-us/help/4020020/cumulative-update-package-6-for-biztalk-server-2013-r2), et [cumulés de BizTalk Server 2013 Mettre à jour 5](https://support.microsoft.com/help/3194301/cumulative-update-5-for-biztalk-server-2013).  
  
    Votre commande modifiée doit ressembler à ce qui suit. Dans l’exemple suivant, il est de 1 heure, une fenêtre active, de purge de 1 jour et suppressions en cours d’exécution plus de 1 jour des instances de service :  
  
    ```  
    exec dtasp_BackupAndPurgeTrackingDatabase 1, 0, 1, '\\MyBizTalkServer\backup', null, 0, 1  
    ```  
  
8.  Sur le **propriétés du travail - DTA Purge and Archive (BizTalkDTADb)** boîte de dialogue **sélectionner une page**, sélectionnez **général**, sélectionnez le **activé**case à cocher, puis sélectionnez **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)
