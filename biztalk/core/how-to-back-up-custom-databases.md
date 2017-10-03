---
title: "Comment sauvegarder des bases de données personnalisées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom databases
- customizing, custom databases
- backing up, custom databases
ms.assetid: 86bebf3c-968e-4fad-9dab-ced1b04aaac7
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2993de90de3f7b768cc5368012d1f27f8940a99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-custom-databases"></a>Sauvegarde des bases de données personnalisées
Comme vos bases de données personnalisées ne sont pas installées avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], elles ne sont pas incluses dans la liste par défaut des bases de données que le travail de sauvegarde de BizTalk Server doit marquer et sauvegarder. Si vous souhaitez que ce travail sauvegarde vos bases de données personnalisées, vous devez les y ajouter manuellement.  
  
## <a name="prerequisites"></a>Conditions préalables  
  
1.  SQL Server doit être configuré pour utiliser le modèle de récupération complète afin de garantir l'intégrité des données dans les jeux de sauvegarde de bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  Pour plus d’informations, consultez [journaux](../core/log-shipping.md).  
  
2.  Pour sauvegarder vos bases de données personnalisées, vous devez ouvrir une session à l'aide d'un compte d'utilisateur ayant accès à chacune des bases données en cours de sauvegarde.  
  
     Grâce au rôle SQL Server BTS_BACKUP_USERS inclus dans BizTalk Server, le compte d'utilisateur utilisé pour sauvegarder vos bases de données n'a pas besoin d'autorisations d'administrateur dans SQL Server, sauf pour le serveur principal contrôlant le processus de sauvegarde.  
  
     Notez les points suivants relatifs à la configuration du compte d'utilisateur utilisé pour la sauvegarde des bases de données :  
  
    -   Vous devez créer un compte de connexion SQL Server pour cet utilisateur et affecter ce dernier au rôle BTS_BACKUP_USERS sur chaque serveur.  
  
    -   Les travaux de sauvegarde de BizTalk Server peuvent être configurés pour une exécution sous un compte d'utilisateur différent de celui utilisé pour le service SQL Server Agent.  
  
    -   Vous devez configurer l'exécution du service SQL Server Agent sous un compte de domaine. Si toutes les bases de données sont situées sur le même ordinateur, vous pouvez configurer le service SQL Server Agent pour utiliser un compte local.  
  
### <a name="to-back-up-custom-databases"></a>Pour sauvegarder les bases de données personnalisées  
  
1.  Créez les objets dans la nouvelle base de données :  
  
    -   Accédez au répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema, puis exécutez Backup_Setup_All_Procs.sql et Backup_Setup_All_Tables.sql sur toutes les bases de données personnalisées que vous souhaitez sauvegarder. Ceci permet de créer les procédures, la table et le rôle nécessaires, et d'affecter les autorisations aux procédures stockées.  
  
2.  Configurez les éléments suivants :  
  
    -   Liez le serveur SQL Server hébergeant la base de données de gestion BizTalk au serveur SQL Server hébergeant la nouvelle base de données. Le compte utilisé pour exécuter le service SQL Server Agent sur le serveur SQL Server de gestion doit être un compte de domaine mappé à chaque ordinateur hébergeant une base de données à sauvegarder. Si les bases de données se trouvent sur le même ordinateur, vous pouvez ignorer cette étape. Cette opération est effectuée automatiquement.  
  
    -   Ajoutez un compte de connexion au serveur SQL Server hébergeant la nouvelle base de données pour le compte exécutant le service SQL Server Agent sur la base de données de gestion SQL Server. Si les bases de données se trouvent sur le même ordinateur, vous pouvez ignorer cette étape.  
  
    -   Ajoutez un utilisateur dans la nouvelle base de données pour le compte de connexion que vous venez de créer, puis ajoutez-le au rôle BTS_BACKUP_USERS. Les scripts créent ce rôle et octroient à celui-ci les autorisations d'exécution sur les procédures nécessaires lors de la première étape.  
  
3.  À l’aide de SQL Server Enterprise Manager ou SQL Server Management Studio, dans la base de données de gestion BizTalk (BizTalkMgmtDb), modifiez le **adm_OtherBackupDatabases** table pour inclure une ligne pour chacun de vos bases de données personnalisés.  
  
4.  Tapez les noms des nouveaux serveur et base de données dans les colonnes correspondantes, comme indiqué dans le tableau suivant.  
  
    |Colonne|Valeur|  
    |------------|-----------|  
    |DefaultDatabaseName|Nom convivial de votre base de données personnalisée.|  
    |DatabaseName|Nom de votre base de données personnalisée.|  
    |ServerName|Nom de l'ordinateur exécutant SQL Server.|  
    |BTSServerName|Nom du serveur BizTalk Server. Cette valeur n'est pas utilisée mais doit tout de même être renseignée.|  
  
 Le travail de sauvegarde de BizTalk Server sauvegarde vos bases de données personnalisées lors de sa prochaine exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)