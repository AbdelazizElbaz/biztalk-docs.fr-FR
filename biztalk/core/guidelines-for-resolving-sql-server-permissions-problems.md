---
title: "Instructions pour la résolution des problèmes d’autorisations SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 60c24512-5f65-4363-b806-8dd52b22f179
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db02fd2a981d3f1dc34924e680caf5926f67871a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-resolving-sql-server-permissions-problems"></a>Instructions pour la résolution des problèmes d'autorisation liés à SQL Server
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exploite pleinement les bases de données Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour les opérations d'exécution. Il est par conséquent important que les autorisations [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] soient définies correctement. Cette rubrique fournit des indications générales pour minimiser [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des problèmes d’autorisation et les étapes que vous pouvez suivre pour résoudre les problèmes [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des problèmes d’autorisation qui affectent [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="general-guidelines"></a>Règles générales  
  
-   **Utiliser des utilisateurs et des groupes pour une installation multiserveur de BizTalk Server**  
  
     Vous devez utiliser des groupes d'utilisateurs et des comptes de domaine lors de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour une exécution sur plusieurs ordinateurs, par exemple, lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sont installés sur des ordinateurs distincts. N’essayez pas de configurer ou exécutez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un *pass-through* scénario d’authentification par laquelle des paires nom d’utilisateur et mots de passe sont créés sur chaque ordinateur pour éviter d’utiliser des comptes et groupes de domaine. Bien qu'un tel scénario puisse fonctionner correctement dans certains cas, il entraînera l'échec de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans d'autres scénarios. De plus, ce n'est pas une configuration prise en charge.  
  
     Pour plus d’informations sur l’installation et la configuration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement multiserveurs, téléchargez le Guide d’Installation à [Installation Guides Related to BizTalk Server 2013](http://go.microsoft.com/fwlink/p/?LinkID=269582).  
  
-   **Assurez-vous que les utilisateurs Windows et les groupes appropriés sont définis dans les rôles SQL Server appropriés**  
  
     Vérifiez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] l’appartenance au rôle tel qu’il figure dans la table dans la rubrique [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
-   **Utilisateur SQL Server Profiler pour diagnostiquer les problèmes d’autorisations**  
  
     Configurer un [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] trace Profiler pour surveiller le **événement d’échec de la connexion d’Audit** pour recueillir des informations détaillées sur les échecs d’autorisation. Pour plus d'informations sur l'utilisation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Profiler, consultez la documentation de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="the-sql-server-jobs-that-are-installed-with-biztalk-server-fail-to-execute"></a>Les travaux SQL Server installés avec BizTalk Server ne peuvent pas être exécutés  
  
##### <a name="problem"></a>Problème  
 Les travaux SQL Server installés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] échouent et des erreurs similaires aux erreurs suivantes sont générées dans le journal de l'application [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] :  
  
 Type d'événement : Avertissement  
  
 Source d'événement : SQLSERVERAGENT  
  
 Catégorie d'événement : Moteur de travail  
  
 ID d’événement : 208  
  
 Date : 29/06/2008  
  
 Heure : 16:45:01  
  
 Utilisateur : n/a  
  
 Ordinateur : *SQLServer*  
  
 Description :  
  
 Travail planifié de SQL Server « Backup BizTalk Server »  
  
 (0x4AC7C44A48541443927A56C5C6699ECF) - État : Échec - Appelé le : 29-6-2008 13:45:01 - Message : Le travail a échoué.  Le travail a été appelé par Planification 305 (MarkAndBackupLogSched). La dernière étape exécutée est l'étape 1 (BackupFull).  
  
 **- et -**  
  
 Type d'événement : Informations  
  
 Source d'événement : MSSQLSERVER  
  
 Catégorie d'événement : (4)  
  
 ID de l'événement : 17055  
  
 Date : 29/06/2008  
  
 Heure : 16:45:01  
  
 Utilisateur : n/a  
  
 Ordinateur : *SQLServer*  
  
 Description :  
  
 18456 : Échec de l'ouverture de session pour l'utilisateur 'NT AUTHORITY\SYSTEM'  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si la connexion BUILTIN\Administrators a été supprimée de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Si cette connexion est supprimée, sqlmaint.exe ne pourra pas se connecter à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], ce qui empêchera les travaux SQL d'être exécutés.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, recréez la connexion BUILTIN\Administrators et ajoutez-la au rôle db_owner des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et de la base de données Master.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de SQL Server](../core/troubleshooting-sql-server.md)   
 [Résolution des problèmes d’autorisations BizTalk Server](../core/troubleshooting-biztalk-server-permissions.md)