---
title: "Dépannage de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f6707c5-7c6e-4375-bfa6-9b1a86ec5e81
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66d6d35ac668a324ed28f7c9519b32812e10cb3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-sql-server"></a>Dépannage de SQL Server
La majeure partie des problèmes de Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui affectent Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se répartissent dans les catégories suivantes :  
  
-   problèmes de connectivité ;  
  
-   problèmes d'autorisations ;  
  
-   problèmes de taille de la base de données.  
  
 Cette rubrique présente chacune de ces catégories et les étapes à suivre pour résoudre les problèmes associés.  
  
## <a name="connectivity-related-problems"></a>Problèmes de connectivité  
 Les incidents suivants sont la plupart du temps associés à des problèmes de connectivité entre l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] hébergeant les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="errors-related-to-failed-transactions-or-communication-with-the-underlying-transaction-manager-errors-are-written-to-the-biztalk-server-application-log"></a>Les erreurs liées à des échecs de transactions ou les erreurs de « communication avec le gestionnaire de transactions sous-jacent » sont consignées dans le journal de l'application BizTalk Server.  
  
##### <a name="problem"></a>Problème  
 Les erreurs indiquant l'échec d'une transaction MSDTC ou un problème de communication avec le gestionnaire de transactions sous-jacent sont consignées dans le journal de l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##### <a name="cause"></a>Cause  
 Connectivité MSDTC entre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]et[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] a échoué.  
  
##### <a name="resolution"></a>Résolution  
 Pour plus d’informations sur la résolution des problèmes de connectivité MSDTC entre le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur et le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur qui héberge le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md).  
  
#### <a name="error-a-connection-was-successfully-established-with-the-server-but-then-an-error-occurred-during-the-pre-login-handshake-occurs-when-connecting-to-remote-sql-server-databases-on-sql-server-2008"></a>Une erreur du type « Une connexion a été correctement établie avec le serveur, mais une erreur s'est produite lors de l'établissement de la liaison avant connexion » s'est produite lors de la connexion aux bases de données SQL Server distantes sur SQL Server 2008.  
  
##### <a name="problem"></a>Problème  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] perd la connectivité avec un ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] distant hébergeant les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et un message d'erreur est généré :  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire si l'une ou plusieurs des conditions suivantes sont remplies :  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] n'est pas configuré pour accepter les connexions distantes.  
  
-   Les protocoles nécessaires pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ne sont activés ni sur l'ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ni sur l'ordinateur client [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui exécute [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre le problème, procédez comme suit :  
  
-   Le **Surface Area Configuration SQL Server** outil n’est pas disponible dans SQL Server 2008. Pour activer les connexions distantes pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur un ordinateur exécutant SQL Server 2008, suivez les instructions de l'aide en ligne de SQL Server 2008.  
  
-   Utilisez le **Gestionnaire de Configuration SQL Server** outil permettant d’activer la **TCP/IP** et/ou la **canaux nommés** protocoles sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Gestionnaire de Configuration SQL Server**.  
  
    2.  Cliquez pour développer **Configuration du réseau SQL Server** puis cliquez sur **protocoles pour MSSQLSERVER**.  
  
    3.  Cliquez sur le **TCP/IP** de protocole, puis cliquez sur **activer**.  
  
    4.  Cliquez sur le **canaux nommés** de protocole, puis cliquez sur **activer**.  
  
    5.  Fermer le **Gestionnaire de Configuration SQL Server** outil.  
  
-   Utilisez le **Gestionnaire de Configuration SQL Server** outil permettant d’activer la **TCP/IP** et/ou la **canaux nommés** protocoles sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur client qui est en cours d’exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, puis cliquez sur **Gestionnaire de Configuration SQL Server**.  
  
    2.  Cliquez pour développer **Configuration du réseau SQL Server** puis cliquez sur **ClientProtocols**.  
  
    3.  Cliquez sur le **TCP/IP** de protocole, puis cliquez sur **activer**.  
  
    4.  Cliquez sur le **canaux nommés** de protocole, puis cliquez sur **activer**.  
  
    5.  Fermer le **Gestionnaire de Configuration SQL Server** outil.  
  
    > [!NOTE]
    >  Assurez-vous qu'au moins l'un des protocoles sur l'ordinateur client [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] correspond aux protocoles activés sur l'ordinateur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
#### <a name="a-biztalk-host-instance-fails-and-a-general-network-error-is-written-to-the-application-log-when-the-biztalk-server-based-server-processes-a-high-volume-of-documents"></a>Une instance d’hôte BizTalk échoue et une erreur « Réseau générale » est consignée dans le journal des applications lorsque le serveur BizTalk Server traite un volume important de documents  
  
##### <a name="problem"></a>Problème  
 Lorsque le serveur BizTalk Server traite un volume important de documents, une instance d'hôte BizTalk échoue et une erreur réseau générale est consignée dans le journal de l'application.  
  
##### <a name="cause"></a>Cause  
 Ce problème survient car Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] implémente un composant de sécurité qui limite la taille de la file d'attente pour les connexions TCP/IP simultanées au serveur. Ce composant a pour but d'empêcher les attaques de type refus de service.  
  
##### <a name="resolution"></a>Résolution  
 Pour plus d’informations sur la résolution de ce problème, consultez [éviter les Exceptions DBNETLIB](../core/avoiding-dbnetlib-exceptions.md).  
  
## <a name="permissions-related-problems"></a>Problèmes d'autorisations  
  
#### <a name="biztalk-server-run-time-or-design-time-operations-fail-and-a-cannot-open-database-requested-in-login-database-error-is-written-to-the-application-log-of-the-biztalk-server-or-sql-server-computer"></a>BizTalk Server, les opérations d’exécution ou au moment du design échouent et un « Impossible d’ouvrir demandée dans la connexion de base de données \<base de données > » erreur est écrite dans le journal des applications de l’ordinateur BizTalk Server ou SQL Server  
  
##### <a name="problem"></a>Problème  
 Une opération d'exécution ou de conception a échoué et une erreur du type suivant est consignée dans le journal d'application de l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] :  
  
 Impossible d’ouvrir de base de données demandée dans la connexion \< *base de données*>. La connexion échoue.   
Échec de la connexion pour l’utilisateur \< *nom d’utilisateur*>.  
  
##### <a name="cause"></a>Cause  
 Cette erreur peut se produire si le compte spécifié ne fait pas partie du groupe Windows ou du rôle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] approprié.  
  
##### <a name="resolution"></a>Résolution  
 Assurez-vous que le compte spécifié est membre du groupe Windows ou du rôle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] approprié. Pour plus d’informations sur les appartenances, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
## <a name="database-sizing-problems"></a>Problèmes de taille de la base de données  
 Si les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] grossissent sans contrôle, les performances de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pourront en être affectées. Pour contrôler la croissance des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], procédez comme suit.  
  
#### <a name="the-biztalk-server-messagebox-database-is-growing-unchecked-and-impacting-overall-performance"></a>La base de données BizTalk Server MessageBox grossit sans contrôle et a un impact négatif sur les performances.  
  
##### <a name="problem"></a>Problème  
 La croissance de la base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] MessageBox affectent les performances de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire si les travaux d'Agent SQL qui doivent assurer la maintenance des bases [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne sont pas exécutés.  
  
##### <a name="resolution"></a>Résolution  
 Assurez-vous que les travaux d'Agent SQL qui doivent assurer la maintenance des bases [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont exécutés. Consultez [Structure de base de données et les travaux](../core/database-structure-and-jobs.md) pour obtenir la liste complète des travaux de l’Agent SQL qui sont installés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
#### <a name="the-biztalk-server-tracking-database-is-growing-unchecked-and-impacting-overall-performance"></a>La base de données de suivi BizTalk Server grossit sans contrôle et a un impact négatif sur les performances.  
  
##### <a name="problem"></a>Problème  
 La base de données de suivi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] grossit sans contrôle et les performances de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en sont affectées.  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire si aucune mesure n'est prise pour purger et archiver la base de données de suivi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
##### <a name="resolution"></a>Résolution  
 Il convient de prendre des mesures pour purger et archiver la base de données de suivi [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Consultez [l’archivage et la purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions pour la résolution des problèmes d’autorisations SQL Server](../core/guidelines-for-resolving-sql-server-permissions-problems.md)