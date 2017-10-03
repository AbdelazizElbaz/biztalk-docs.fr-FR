---
title: Comment planifier le travail de sauvegarde de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, scheduling
- backing up, backup jobs
- scheduling, backup jobs
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d6b40ae933874e1c25cb3a93dbbeab514ef5dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-schedule-the-backup-biztalk-server-job"></a>Planification du travail de sauvegarde de BizTalk Server
Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté selon la planification du service SQL Server Agent. Si vous souhaitez varier la fréquence des sauvegardes, vous pouvez modifier la planification du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de SQL Server Management Studio.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-schedule-the-backup-biztalk-server-job-sql-server-2008"></a>Planification du travail de sauvegarde de BizTalk Server (SQL Server 2008)  
  
1.  Sur l’ordinateur qui contient la base de données de gestion BizTalk, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **Microsoft SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, spécifiez le nom du serveur SQL sur lequel BizTalk Server bases de données résident et l’authentification appropriée, puis tapez **connexion**.  
  
3.  Dans l’Explorateur d’objets, double-cliquez sur **l’Agent SQL Server**, puis cliquez sur **travaux**.  
  
4.  Dans le volet détails, cliquez sur **sauvegarde de BizTalk Server (BizTalkMgmtDb)**, puis cliquez sur **propriétés**.  
  
5.  Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)** boîte de dialogue **sélectionner une page**, cliquez sur **étapes**.  
  
6.  Dans le **liste des étapes du travail**, cliquez sur **BackupFull**, puis cliquez sur **modifier**.  
  
7.  Dans le **propriétés étape du travail - BackupFull** boîte de dialogue le **commande** , modifiez la commande en changeant la fréquence à laquelle effectuer une sauvegarde complète de l’intervalle souhaité : **'h'** (horaire), **avait '** (quotidienne), **« w »** (hebdomadaire), **suis '** (mensuelle), **'y'** (annuelle), puis cliquez sur **OK** .  
  
    > [!NOTE]
    >  Une sauvegarde complète est effectuée à la première exécution du travail de sauvegarde de BizTalk Server lors d'une nouvelle période.  
  
8.  Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)** boîte de dialogue **sélectionner une page**, cliquez sur **planifications**.  
  
9. Dans le **liste planification**, cliquez sur **MarkAndBackupLogSched**, puis cliquez sur **modifier**.  
  
10. Dans le **propriétés de planification du travail - MarkAndBackupLogSched** planification, sélectionnez le type de la boîte de dialogue **périodique** dans la zone de liste déroulante (si elle n’est pas déjà sélectionnée).  
  
     Par défaut, l'exécution du travail est planifiée toutes les 15 minutes.  
  
11. Mettre à jour la planification comme vous le souhaitez, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la planification des travaux de l’Agent SQL Server, consultez «[Scheduling Jobs](http://go.microsoft.com/fwlink/?LinkId=195887). »  
  
12. Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)** boîte de dialogue, cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [Comment configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [Comment faire pour restaurer vos bases de données](../core/how-to-restore-your-databases.md)   
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)