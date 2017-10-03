---
title: "Désinstallez et annulez la configuration de BizTalk Server pour le supprimer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9ea8757-ca49-421b-bf7b-89344201398a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce643460d7c5256829624de5ba4c32d664c26ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="uninstall-and-unconfigure-biztalk-server-to-remove-it"></a>Désinstallation et annulation de la configuration de BizTalk Server pour le supprimer
Désinstallez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et annulez sa configuration. 
  
##  <a name="BKMK_BeforeYouBegin"></a> Avant de commencer  
  
-   Avant la désinstallation, vous devez annuler la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Cette rubrique répertorie divers travaux, packages et bases de données à supprimer. Les noms répertoriés ici sont les noms par défaut. Votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise peut-être des noms autres que les noms par défaut.  
  
-   Effectuez les étapes dans l'ordre indiqué. Autrement, l'installation ne s'effectue pas complètement.  
  
##  <a name="BKMK_Unconfigure"></a> Annulation de la configuration de BizTalk Server  
  
1.  Cliquez avec le bouton droit sur **Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]**, puis sélectionnez **Exécuter en tant qu’administrateur**.  
  
2.  Dans la configuration, sélectionnez **Annuler la configuration des composants**.  
  
3.  Sélectionnez les composants dont vous souhaitez annuler la configuration, puis sélectionnez **OK**. Si vous êtes invité à continuer, sélectionnez **Oui**. Pour tout supprimer de l’ordinateur, vous pouvez sélectionner tous les composants.  
  
4.  Sélectionnez **Suivant** et suivez les instructions de l’Assistant.  
  
 Un fichier journal est généré dans un dossier temporaire, similaire à : C:\Users\nom_utilisateur\AppData\Local\Temp\ConfigLog(8-29-2016 0h37m59s).log.  
  
##  <a name="BKMK_Uninstall"></a> Désinstallation des composants d’exécution de BizTalk Server  
  
1.  Ouvrez **Programmes et fonctionnalités**.  
  
2.  Sélectionnez votre version de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans la liste et sélectionnez **Désinstaller**.  
  
3.  **Supprimez**-la et suivez les instructions de l’Assistant.  
  
 Un fichier journal est généré dans un dossier temporaire, similaire à : C:\Users\\*nom_utilisateur*\AppData\Local\Setup(083016 xxxxxx).htm  
  
##  <a name="BKMK_UninstallSSO"></a> Désinstallation de l’authentification unique de l’entreprise  
  
1.  Ouvrez **Programmes et fonctionnalités**.  
  
2.  Sélectionnez **Microsoft Enterprise Single Sign-On** dans la liste, puis sélectionnez **Désinstaller**.  
  
3.  **Supprimez** cette fonctionnalité et suivez les instructions de l’Assistant.  
  
 Un fichier journal est généré dans un dossier temporaire, similaire à : C:\Users\\*nom_utilisateur*\AppData\Local\Setup(083016 xxxxxx).htm  
  
##  <a name="BKMK_RemoveRemaining"></a> Suppression des travaux, des bases de données et des packages SQL  
  
#### <a name="delete-sql-server-agent-jobs"></a>Suppression des travaux de l'Agent SQL Server  
  
1.  Ouvrez **SQL Server Management Studio** comme administrateur.  
  
2.  Dans **SQL Server Management Studio**, connectez-vous au **moteur de base de données**, puis développez **SQL Server Agent** et **Travaux**.  
  
3.  Supprimez les travaux suivants (cliquez avec le bouton droit sur le travail et sélectionnez **Supprimer**) :  
  
    -   Backup BizTalk Server (BizTalkMgmtDb)  
  
    -   CleanupBTFExpiredEntriesJob_BizTalkMgmtDb  
  
    -   DTA Purge and Archive (BizTalkDTADb)  
  
    -   MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_Message_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb  
  
    -   MessageBox_Parts_Cleanup_BizTalkMsgBoxDb  
  
    -   MessageBox_UpdateStats_BizTalkMsgBoxDb  
  
    -   Monitor BizTalk Server (BizTalkMgmtDb)  
  
    -   Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb  
  
    -   PurgeSubscriptionsJob_BizTalkMsgBoxDb  
  
    -   Rules_Database_Cleanup_BizTalkRuleEngineDb  
  
    -   TrackedMessages_Copy_BizTalkMsgBoxDb  
  
        > [!NOTE]
        >  Si vous avez déployé BAM, vous devez également supprimer la table bam_\<*nom du Cube*> _\<*nom de la vue*> tâche.  
  
#### <a name="delete-biztalk-server-databases"></a>Suppression des bases de données BizTalk Server  
  
1.  Dans l’**Explorateur d’objets**, développez **Bases de données**.  
  
2.  Supprimez les bases de données suivantes (cliquez avec le bouton droit sur la base de données et sélectionnez **Supprimer**) :  
  
    -   BAMArchive  
  
    -   BAMPrimaryImport  
  
    -   BAMStarSchema  
  
    -   BizTalkDTADb  
  
    -   BizTalkMgmtDb  
  
    -   BizTalkMsgBoxDb  
  
    -   BizTalkRuleEngineDb  
  
    -   SSODB  
  
#### <a name="remove-sql-server-integration-services-packages"></a>Suppression des packages SQL Server Integration Services  
  
1.  Dans l’**Explorateur d’objets**, **connectez**-vous à **Integration Services**.  
  
2.  Développez **Packages stockés** puis **MSDB**.  
  
3.  Supprimez les packages avec les préfixes suivants (cliquez avec le bouton droit sur le package et sélectionnez **Supprimer**) :  
  
    -   BAM_AN_\<*nom du Cube*>  
  
    -   BAM_DM_\<*afficher le nom*>  
  
