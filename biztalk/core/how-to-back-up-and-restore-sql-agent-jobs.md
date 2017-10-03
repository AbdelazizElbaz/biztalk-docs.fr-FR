---
title: "Comment sauvegarder et restaurer des travaux de l’Agent SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f82fc5a5-5ea5-476c-bed1-c5d41a50e673
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 253055f9a45dfdb9864d4d5202661e750d28b1b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-and-restore-sql-agent-jobs"></a>Sauvegarde et restauration des travaux de l'Agent SQL
Cette rubrique décrit la sauvegarde et la restauration des travaux de l'Agent SQL Server. Vous devez sauvegarder vos travaux SQL après les avoir configurés.  
  
## <a name="biztalk-server-jobs"></a>Travaux BizTalk Server  
 Les travaux d'Agent SQL Server suivants sont associés à BizTalk Server. Les travaux installés sur chaque serveur sont différentes selon les fonctionnalités qui sont installées et configurées. La plupart de ces travaux sont créés lors de l'installation de BizTalk Server. Plusieurs d'entre eux sont créés lors de la configuration de l'envoi de journaux.  
  
-   Backup BizTalk Server (BizTalkMgmtDb)  
  
-   CleanupBTFExpiredEntriesJob_BizTalkMgmtDb  
  
-   DTA Purge and Archive (BizTalkDTADb)  
  
-   MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_Message_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb  
  
-   MessageBox_Parts_Cleanup_BizTalkMsgBoxDb  
  
-   MessageBox_UpdateStats_BizTalkMsgBoxDb  
  
-   Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb  
  
-   PurgeSubscriptionsJob_BizTalkMsgBoxDb  
  
-   Rules_Database_Cleanup_BizTalkRuleEngineDb  
  
-   TrackedMessages_Copy_BizTalkMsgBoxDb  
  
-   Envoi de journaux de BizTalk Server - Obtenir l'historique des sauvegardes  
  
-   Envoi de journaux de BizTalk Server - Restaurer la base de données  
  
-   Envoi de journaux de BizTalk Server - Restaurer à la marque  
  
## <a name="back-up-a-job-using-a-script"></a>Sauvegarder un travail à l’aide d’un script  
  
1.  Ouvrez **SQL Server Management Studio**.  
  
2.  Développez **Agent SQL Server**, puis **Travaux**.  
  
3.  Avec le bouton droit de la tâche que vous souhaitez créer un script de sauvegarde, puis **tâche de Script en tant que**.  
  
4.  Sélectionnez **CREATE To** ou **DROP To**, puis sélectionnez **nouvelle fenêtre d’éditeur de requête**, **fichier**, ou **Presse-papiers** Pour sélectionner une destination pour le script. En règle générale, la destination est un fichier avec un **.sql** extension.  
  
5.  Répétez cette procédure depuis l'étape 3 pour chaque travail pour lequel créer un script. Consultez la liste des travaux liés à BizTalk Server pour identifier ceux pour lesquels créer un script.  
  
     Au minimum, vous devez sauvegarder le **sauvegarde de BizTalk Server (BizTalkMgmtDb)** de la tâche après sa configuration.  
  
## <a name="restore-a-job-from-a-script"></a>Restaurer un travail à partir d’un script  
  
1.  Ouvrez **SQL Server Management Studio**.  
  
2.  Sur le **fichier** menu, **ouvrir** le fichier contenant le travail sous forme de script.  
  
3.  Exécutez le script pour créer le travail.  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Comment sauvegarder et restaurer les connexions SQL Server](../core/how-to-back-up-and-restore-sql-server-logins.md)