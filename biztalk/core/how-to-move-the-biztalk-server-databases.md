---
title: "Déplacer les bases de données BizTalk Server | Documents Microsoft"
description: "Étapes pour déplacer les bases de données BizTalk Server vers un nouveau serveur, y compris l’arrêt des services et à l’aide des travaux de l’Agent SQL Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec302e6d-c89d-4fe7-849f-97b5566e8ba4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12bd1d6bc8a46d4e63dc69166d87f3678a0e3272
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-biztalk-server-databases"></a>Déplacement des bases de données BizTalk Server

## <a name="overview"></a>Vue d'ensemble
Cette procédure permet de déplacer les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] principales vers un autre serveur. Elle permet également de déplacer les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] d'un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] local vers un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distant ou vers un cluster [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  

## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] le rôle de serveur fixe sysadmin pour effectuer cette procédure.  
  
## <a name="move-steps"></a>Étapes de déplacement
  
1.  Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [redémarrer les Services BizTalk Server et arrêt de BizTalk Server](how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).
  
    > [!IMPORTANT]
    >  Il est important de vérifier que tous les services et travaux [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont arrêtés avant de déplacer les bases de données.  
  
2.  Arrêtez le service IIS.  
  
3.  Arrêtez le service SQL Server Agent.  
  
4.  Sauvegardez les bases de données BizTalk en suivant les procédures de sauvegarde de base de données comme décrit dans [sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
5.  Restauration de bases de données sur le nouveau serveur de la base de données BizTalk restaurer procédures au [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).  
  
6.  Script de travaux de SQL Server Agent répertoriés ci-dessous pour le transfert vers le nouveau serveur, comme décrit dans [comment sauvegarder et restaurer des travaux de l’Agent SQL](../core/how-to-back-up-and-restore-sql-agent-jobs.md).  Exécutez chacun des scripts sur le nouveau serveur pour recréer les travaux.  
  
     Exécutez chacun des scripts sur le nouveau serveur pour recréer les travaux. Certains travaux, tels que les **sauvegarde de BizTalk Server (BizTalkMsgBoxDb)** , doivent être reconfigurés sauf si les nouveaux chemins de fichier du serveur et le nom du serveur sont identiques à l’ancien serveur.  
  
    > [!NOTE]
    >  Vous pouvez également utiliser DTS/SSIS **transfert de travaux** de tâches pour déplacer les travaux vers le nouveau serveur, mais la plupart des utilisateurs sera probablement plus facile de générer un script les travaux à l’aide de SQL Management Studio.  
  
7.  Outre les travaux de l’Agent SQL Server comme décrit dans l’étape précédente, vous devez également un script connexions comme décrit dans [comment sauvegarder et restaurer les connexions SQL Server](../core/how-to-back-up-and-restore-sql-server-logins.md). Ces comptes de connexion doivent être restaurés sur le serveur de destination.  
  
8.  Restaurer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données en suivant les étapes 9 à 22 [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md). Cette procédure permet de mettre à jour la base de données de gestion BizTalk (BizTalkMgmtDb) et le Registre avec le nouvel emplacement des bases de données BizTalk.  
  
    > [!NOTE]
    >  Dans le **SampleUpdateInfo.xml** de fichier, commentaire pour toutes les bases de données à l’exception de celles que vous avez déplacé vers le nouveau serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données BizTalk Server](../core/moving-biztalk-server-databases.md)