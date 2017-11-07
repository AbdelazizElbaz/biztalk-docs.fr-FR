---
title: Planifier le travail de sauvegarde de BizTalk Server | Documents Microsoft
description: "Configurez les paramètres de la tâche de sauvegarde de BizTalk Server, définissez une planification de l’exécution mensuelle, hebdomadaire, quotidienne ou toutes les heures"
ms.custom: 
ms.date: 11/02/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e89fff4-da87-4cdc-acc4-46f03c3269fc
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f09ca97f65605ac3bf427d1c1fcc322a14feb53
ms.sourcegitcommit: 9aaed443492b74729171fef79c634bff561af929
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2017
---
# <a name="schedule-the-backup-biztalk-server-job"></a>Planifier le travail de sauvegarde de BizTalk Server
Le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté selon la planification du service SQL Server Agent. Si vous souhaitez varier la fréquence des sauvegardes, vous pouvez modifier la planification du travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de SQL Server Management Studio.  
  
## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre du rôle serveur fixé sysadmin SQL Server.  
  
## <a name="schedule-the-backup-biztalk-server-job"></a>Planifier le travail de sauvegarde de BizTalk Server
  
1.  Sur le serveur SQL qui héberge la base de données de gestion BizTalk, ouvrez **SQL Server Management Studio**.

2.  Dans **se connecter au serveur**, entrez le nom du serveur SQL sur lequel le serveur BizTalk Server résident des bases de données, sélectionnez le type d’authentification, puis **connexion**.  
  
3.  Dans l’Explorateur d’objets, double-cliquez sur **l’Agent SQL Server**, puis sélectionnez **travaux**.  
  
4.  Dans le volet détails, cliquez sur **sauvegarde de BizTalk Server (BizTalkMgmtDb)**, puis sélectionnez **propriétés**.  
  
5.  Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)**, sous **sélectionner une page**, sélectionnez **étapes**.  
  
6.  Dans le **liste des étapes du travail**, sélectionnez **BackupFull**, puis sélectionnez **modifier**.  
  
7.  Dans le **propriétés étape du travail - BackupFull**, dans le **commande** zone, de mise à jour de la commande en changeant la fréquence pour exécuter une sauvegarde complète : **'h'** (horaire), **avait '**  (quotidienne), **« w »** (hebdomadaire), **suis '** (mensuelle), **'y'** (annuelle). Sélectionnez **OK**.  
  
    > [!NOTE]
    >  La première fois que le travail de sauvegarde de BizTalk Server s’exécute, il réalise une sauvegarde complète.  
    
8.  Configurer d’autres  **@frequency**  paramètres :  
  
    - **@ForceFullBackupAfterPartialSetFailure**: La valeur par défaut est **false**. Lorsque **false**, si la sauvegarde complète échoue, le système attend que le prochain cycle jusqu'à ce que la sauvegarde complète est effectuée.  
    
        > [!NOTE]
        >  Si votre  **@frequency**  paramètre est long (par exemple, hebdomadaire, mensuelle, annuelle), puis à ce paramètre **false** peut être dangereuse. Dans ce scénario, il peut être préférable de définir cet indicateur **true**. Lorsque **true**, chaque fois une défaillance, le système force lui-même pour créer une sauvegarde complète. Il peut y avoir un impact sur les performances, mais il est safter d’un système récupérable.
  
    - **@BackupHour**: La valeur par défaut NULL. Ce paramètre est directement lié à  **@Frequency** . Lorsque vous définissez la fréquence **h** (horaire), vous définissez les heures du jour que vous souhaitez que la sauvegarde complète à exécuter. Vous pouvez choisir une valeur comprise entre 0 (minuit) et 23 (11 PM). Si ce champ est vide, la sauvegarde complète s’exécute toutes les heures.  
    
       > [!NOTE]
        >  Si vous définissez ce paramètre avec une valeur en dehors de la plage comprise entre 0 et 23 (par exemple, 100 ou -1), le système force ce dernier à 0.
  
    - **@UseLocalTime**: Un paramètre supplémentaire qui stipule pour utiliser l’heure locale. Par défaut, la tâche fonctionne avec l’heure UTC. Par conséquent, si vous résidez en Australie (qui est UTC + 10 heures), votre sauvegarde s’exécute au lieu de 10 à minuit. Comme meilleure pratique, il est recommandé d’affecter à ce **1** (true).  
  
9.  Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)**, sous **sélectionner une page**, cliquez sur **planifications**.  
  
10. Dans le **liste planification**, cliquez sur **MarkAndBackupLogSched**, puis cliquez sur **modifier**.  
  
11. Dans le **propriétés de planification du travail - MarkAndBackupLogSched**, type de planification, sélectionnez **périodique** dans la liste déroulante.  
  
     Par défaut, l'exécution du travail est planifiée toutes les 15 minutes.  
     
    > [!NOTE]
    >  Vous pouvez modifier cette valeur en fonction de vos exigences, mais le premier test dans un environnement hors production. La valeur des résultats trop faibles dans des sauvegardes fréquentes et l’ajoute à la charge de l’arrière-plan de votre environnement SQL. Une valeur trop élevée peut augmenter la taille des journaux de transactions et affecter les performances. Dans certaines situations, il est recommandé de laisser la valeur par défaut.    
  
12. Mettre à jour la planification si vous le souhaitez, puis sélectionnez **OK**.  
  
    > [!NOTE]
    >  [Planification de travaux](https://docs.microsoft.com/sql/ssms/agent/schedule-a-job) fournit plus de détails.
  
13. Dans le **propriétés du travail - Backup BizTalk Server (BizTalkMgmtDb)**, cliquez sur **OK**.  
  
## <a name="more-good-stuff"></a>Autre contenu intéressant  
 [Configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)   
 [Configurer le système de Destination pour l’envoi de journaux](../core/how-to-configure-the-destination-system-for-log-shipping.md)   
 [Restaurer vos bases de données](../core/how-to-restore-your-databases.md)   
 [Informations avancées sur la sauvegarde et la restauration](../core/advanced-information-about-backup-and-restore1.md)
