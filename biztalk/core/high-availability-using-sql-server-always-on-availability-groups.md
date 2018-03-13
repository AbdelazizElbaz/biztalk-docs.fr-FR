---
title: "Haute disponibilité à l’aide de SQL Server groupes de disponibilité AlwaysOn | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4511a578-77d2-49ee-99bd-f0406ad625d0
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d065013cb4975e6d37e2ab50211c5207852ece64
ms.sourcegitcommit: 6fe505d37e81dc2da43f89548e8977b60a6f5dbd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2018
---
# <a name="high-availability-using-sql-server-always-on-availability-groups"></a>Haute disponibilité à l’aide de SQL Server groupes de disponibilité AlwaysOn
Configurer la haute disponibilité à l’aide de groupes de disponibilité AlwaysOn de SQL Server.

> [!TIP] 
[Configuration de BizTalk Server 2016 à l’aide de la disponibilité de groupes LAB](https://skastberg.wordpress.com/2017/02/22/setting-up-my-biztalk-server-2016-using-availability-groups-lab/) fournit un guide pas à pas écrit par un ingénieur Microsoft. Il est basé sur un environnement lab et comprend des observations. Regarde.  

> [!IMPORTANT]
> * Groupes de disponibilité AlwaysOn est disponible à partir de SQL Server 2016. Si vous utilisez une version antérieure de SQL Server, cette rubrique ne s’applique pas à vous. 
> * BizTalk Server 2016 prend en charge le mode de validation synchrone ; mode de validation asynchrone n’est pas pris en charge. Récupération d’urgence, il est recommandé pour configurer la tâche de sauvegarde de BizTalk Server et utiliser des journaux de transaction. Consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md) pour des détails spécifiques.
> 
>    [Modes de disponibilité](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/availability-modes-always-on-availability-groups) en détail les options de validation avec des groupes de disponibilité AlwaysOn. 


## <a name="background-and-history"></a>Historique

BizTalk Server s’appuie fortement sur SQL Server pour la persistance des données. Autres composants et les hôtes BizTalk Server ont des rôles spécifiques lors de l’intégration d’applications d’entreprise hétérogènes, telles que la réception, le traitement ou routage des messages. L’ordinateur de base de données enregistre ces travaux et l’enregistre sur disque. 

BizTalk Server utilise le Clustering de basculement SQL Server et l’envoi de journaux pour fournir une haute disponibilité, sauvegarde et restauration et récupération d’urgence pour ses bases de données locales. Dans Azure IaaS (machines virtuelles), les versions précédentes de SQL Server ne gèrent pas les Instances de Cluster de basculement (aucune prise en charge MSDTC). Par conséquent, BizTalk n’a pas une solution de haute disponibilité lors de l’utilisation de machines virtuelles Azure.

À compter de SQL Server 2016, groupes de disponibilité AlwaysOn de SQL Server prend en charge MSDTC sur site et à l’aide de machines virtuelles Azure. Par conséquent, la fonctionnalité AlwaysOn de SQL Server 2016 est prise en charge pour BizTalk bases de données locale ou dans les scénarios Azure IaaS. 

## <a name="sql-server-2016-alwayson-availability-groups"></a>Groupes de disponibilité AlwaysOn de SQL Server 2016 
Déploiement des groupes de disponibilité AlwaysOn requiert un cluster de Clustering de basculement Windows Server (WSFC). Chaque réplica de disponibilité d'un groupe de disponibilité donné doit résider sur un nœud différent du même cluster WSFC. Un groupe de ressources WSFC est créé pour chaque groupe de disponibilité que vous créez. Le cluster WSFC surveille ce groupe de ressources pour évaluer l'intégrité du réplica principal.  

L'illustration suivante montre un groupe de disponibilité qui contient un réplica principal et quatre réplicas secondaires.  
 
 ![SQLAG_PrimaryReplica](../core/media/sqlag-primaryreplica.png)

Les clients peuvent se connecter au réplica principal d’un groupe de disponibilité donné à l’aide d’un écouteur de groupe de disponibilité. Un écouteur fournit un ensemble de ressources qui sont attachés à un groupe de disponibilité donné pour diriger les connexions clientes au réplica de disponibilité approprié. 

>[!IMPORTANT]
> SQL Server 2016 prend en charge MSDTC avec groupes de disponibilité AlwaysOn (AG) sur Windows Server 2016 et Windows Server 2012 R2. **Windows Server 2012 R2** requiert le [3090973](https://support.microsoft.com/kb/3090973) correctif Windows Installer. 
> **Windows Server 2016** requiert que le [clé de Registre RemoteAccessEnabled](https://support.microsoft.com/kb/3182294) être activée.

SQL Server ne prend pas en charge MSDTC avec le groupe de disponibilité AlwaysOn pour toutes les versions antérieures à 2016.  

MSDTC entre les bases de données sur la même instance de SQL Server n’est pas pris en charge avec les groupes de disponibilité AlwaysOn de SQL Server. Cela signifie qu’aucun deux bases de données BizTalk dans une transaction distribuée ne peuvent être hébergées sur la même instance SQL server. Pour des raisons de cohérence transactionnelle, les bases de données BizTalk participant à une transaction distribuée doivent être hébergés sur différentes instances de SQL server. Notez que peu importe si les instances SQL sont sur le même ordinateur ou sur des ordinateurs différents.  


## <a name="providing-high-availability-for-biztalk-databases-using-alwayson-availability-groups"></a>Offrant une haute disponibilité pour les bases de données BizTalk à l’aide de groupes de disponibilité AlwaysOn 
Dans la configuration de base de BizTalk Server, un minimum de 9 bases de données sont créés notamment BAM et les règles de bases de données. En raison de la ressource MSDTC limitation avec des groupes de disponibilité mentionné précédemment, une configuration telle que les éléments suivants ne garantit pas la cohérence transactionnelle. 

![SQLAG_NoTrans](../core/media/sqlag-notrans.gif)
 
Nous recommandons que les bases de données BizTalk Server sont regroupés dans les quatre instances de SQL Server suivantes :
 
| Instance |Rôle |Bases de données de ce groupe BizTalk  |
|--- | --- | ---|
|1 |Authentification |SSODB|
|2 |Gestion |BizTalkMgmtDb| 
|3 |Runtime |BizTalkMsgBoxDb<br/> BizTalkRulesEngineDb<br/> BAMPrimaryImport<br/>BAMStarSchema <br/>BAMAlertsApplication |
|4 |Suivi |BizTalkDTADb<br/>EsbItineraryDb<br/>EsbExceptionDb | 
 
Dans un scénario de MessageBox à grande échelle (il s’agit d’une configuration avec plusieurs MessageBox), il existe plusieurs bases de données MessageBox, et chaque base de données MessageBox doit se trouver sur sa propre instance de SQL Server. 

BizTalk Server dépend également de SQL Server Analysis Services et SQL Server Integration Services pour l’analyse BAM et d’archivage. SQL Server ne fournit pas une solution haute disponibilité pour les Services d’intégration ou d’Analysis Services dans Azure IaaS. Il est donc recommandé d’utiliser une autre instance de SQL Server autonome pour les bases de données BAMArchive et BAMAnalysis Analysis Services. Pour les installations locales, Instance de Clustering de basculement de SQL peut être utilisée pour définir une configuration de haute disponibilité. 

Cette configuration est illustrée ci-dessous et recommandée pour les bases de données BizTalk dans les groupes de disponibilité :  

![SQLAG_Recommended](../core/media/sqlag-recommended.png)
 
En même temps que les bases de données SQL Server, configuration de BizTalk Server crée également des connexions de sécurité de SQL Server et les travaux de l’Agent SQL. Groupes de disponibilité AlwaysOn fournir uniquement la possibilité de gérer des bases de données à l’intérieur d’un groupe de disponibilité. Connexions et les travaux de l’Agent SQL pour BizTalk doivent être créés et mis à jour/gérés manuellement sur tous les réplicas de disponibilité.  

La liste suivante des connexions de sécurité de SQL Server sont associés à BizTalk Server. Vous avez peut-être créées pour vos applications BizTalk Server de connexions supplémentaires. Dans ce cas, vous devez les répliquer sur chaque instance de SQL Server qui héberge un réplica de bases de données BizTalk. 

1. Utilisateurs d’applications BizTalk (un ou plusieurs correspondant à chaque hôte in-process) 
2. BizTalk utilisateurs d’hôtes isolés (un ou plusieurs correspondant à chaque hôte isolé) 
3. Administrateurs BizTalk Server 
4. Opérateurs interentreprises BizTalk Server 
5. Opérateurs BizTalk Server 
6. Administrateurs SSO 
7. Utilisateur d’alertes BAM 
8. Utilisateur de service Web de gestion de l'analyse BAM 
9. Compte de Service de mise à jour de moteur règle 

Si vous avez créé des hôtes supplémentaires ou que vous créerez ultérieurement des hôtes supplémentaires, il y aura des connexions SQL créées dans le cadre de ce processus. Il se peut que vous devez vous assurer de créer ces connexions SQL manuellement sur les réplicas correspondants.

Les travaux d'Agent SQL Server suivants sont associés à BizTalk Server. Les travaux installés sur chaque serveur sont différentes selon les fonctionnalités qui sont installées et configurées. La plupart de ces travaux sont créés lors de la configuration de BizTalk Server. Plusieurs d'entre eux sont créés lors de la configuration de l'envoi de journaux. Ces travaux doivent être répliqués sur chaque instance de réplica d’hébergement SQL Server de leur base de données BizTalk correspondant. Cela doit être effectué manuellement. 

- Travaux de BizTalkMgmtDb : 
    - Backup BizTalk Server (BizTalkMgmtDb) 
    - CleanupBTFExpiredEntriesJob_BizTalkMgmtDb 
    - Monitor BizTalk Server (BizTalkMgmtDb) 
- Travaux de BizTalkMsgBoxDb : 
    - MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb 
    - MessageBox_Message_Cleanup_BizTalkMsgBoxDb
    - MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb
    - MessageBox_Parts_Cleanup_BizTalkMsgBoxDb 
    - MessageBox_UpdateStats_BizTalkMsgBoxDb 
    - Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 
    - PurgeSubscriptionsJob_BizTalkMsgBoxDb 
    - TrackedMessages_Copy_BizTalkMsgBoxDb 
- Travaux sur les boîtes de message supplémentaires
- Travail de BizTalkDTADb : 
    - DTA Purge and Archive (BizTalkDTADb) 
- Travail de BizTalkRulesEngineDb : 
    - Rules_Database_Cleanup_BizTalkRuleEngineDb 
- Travail de BAMAlertsApplication : 
    - 0 ou plus DelAlertHistJob 

Contrairement aux Instances de Clustering de basculement SQL, dans les groupes de disponibilité tous les réplicas sont active, en cours d’exécution et disponible. Lorsque les travaux de l’Agent SQL sont dupliqués sur chaque réplica pour le basculement, ils s’exécuter sur le réplica correspondant, indépendamment de si elle est actuellement dans le rôle principal ou secondaire. Pour vous assurer que ces travaux sont exécutés uniquement sur le réplica principal actuel, toutes les étapes de chaque tâche doivent être placés dans un bloc IF, comme indiqué : 

    IF (sys.fn_hadr_is_primary_replica(‘dbname’) = 1)  
    BEGIN  
    …  
    END
  
Remplacez `‘dbname’` avec le nom de base de données correspondant, par rapport à laquelle le travail est configuré pour s’exécuter. L’exemple suivant illustre cette modification pour TrackedMessages_Copy_BizTalkMsgBoxDb sur BizTalkMsgBoxDb : 
 
 ![SQLAG_AgentJob](../core/media/sqlag-agentjob.gif)

### <a name="configure-biztalk-server-when-availability-groups-are-already-set-up"></a>Configuration de BizTalk Server lorsque les groupes de disponibilité sont déjà configurées

1. Vérifiez votre configuration requise du système d’exploitation : 
* Sur tous les **Windows Server 2012 R2** les ordinateurs, installer le [3090973 MSDTC correctif](https://support.microsoft.com/kb/3090973) (ouvre un article de la base de connaissances)
* Sur tous les **Windows Server 2016** ordinateurs, activez la [clé de Registre RemoteAccessEnabled](https://support.microsoft.com/kb/3182294) (ouvre un article de la base de connaissances)
2. Assurez-vous d’avoir au moins quatre instances SQL différentes qui hébergent les bases de données BizTalk différents. Les réplicas secondaires doivent également être configurés sur différentes instances SQL. Cela entraîne un minimum de 8 instances SQL (1 réplica principal et 1 secondaire pour chacune des instances de 4), ainsi qu’un minimum de 4 groupes de disponibilité. Consultez l’illustration ci-dessus pour cette configuration de groupe de disponibilité. Assurez-vous que les groupes de disponibilité sont créés avec le **par base de données prise en charge DTC** option car il ne peut pas être modifiée ultérieurement. 
3. Lorsque configuration de BizTalk Server et en spécifiant le nom du serveur SQL, utilisez le nom de l’écouteur du groupe de disponibilité au lieu du nom d’ordinateur réel. Cela crée les bases de données BizTalk, les connexions et les travaux SQL Agent sur le réplica principal actuel. 
4. Arrêter le traitement BizTalk (Instances de l’hôte, Service d’authentification unique, IIS, Service de mise à jour du moteur de règles, BAMAlerts Service et ainsi de suite) et arrêter les travaux de l’Agent SQL. 
5. Ajoutez maintenant les bases de données BIzTalk aux groupes de disponibilité respectif. 
6. Placez le corps d’étapes de travail de l’Agent SQL dans `IF` bloc (mentionnée précédemment) pour vous assurer qu’ils s’exécuter uniquement si la cible est le réplica principal. 
7. Script des connexions et des travaux de l’Agent SQL pour les répliquer sur le réplica correspondant. 
8. Réplication SQL DBMail compte et un profil pour les alertes BAM sur des instances SQL correspondants qui héberge le réplica secondaire. 
9. Si vous ajoutez une base de données MessageBox supplémentaires ou déploiement d’une nouvelle activité/vue BAM version ultérieure, puis de nouveau les travaux de SQL Server sont créés pour les nouvelles bases de données de zone message ou de la base de données d’alertes BAM sur le réplica principal actuel. Veillez à modifier sur le réplica principal et ensuite créer manuellement sur les réplicas secondaires correspondants. 

Cette configuration peut également être effectuée à l’aide des Instances de SQL qui héberge le réplica principal. Dans ce cas, après la configuration de BizTalk, exécutez le `UpdateDatabase.vbs` et `UpdateRegistry.vbs` des scripts sur les ordinateurs BizTalk après avoir effectué les étapes ci-dessus. Ce sujet est abordé plus en détail dans la section suivante.  
 
### <a name="move-biztalk-server-databases-of-an-existing-biztalk-system-to-availability-groups"></a>Déplacer des bases de données BizTalk Server d’un système BizTalk existant aux groupes de disponibilité

1. Vérifiez votre configuration requise du système d’exploitation : 
* Sur tous les **Windows Server 2012 R2** les ordinateurs, installer le [3090973 MSDTC correctif](https://support.microsoft.com/kb/3090973) (ouvre un article de la base de connaissances)
* Sur tous les **Windows Server 2016** ordinateurs, activez la [clé de Registre RemoteAccessEnabled](https://support.microsoft.com/kb/3182294) (ouvre un article de la base de connaissances)
2. Assurez-vous d’avoir au moins quatre instances SQL différentes qui hébergent les bases de données BizTalk différents. Les réplicas secondaires doivent également être configurés sur différentes instances SQL. Cela entraîne un minimum de 8 instances SQL (1 réplica principal et 1 secondaire pour chacune des instances de 4), ainsi qu’un minimum de 4 groupes de disponibilité. Consultez l’illustration ci-dessus pour cette configuration de groupe de disponibilité. Assurez-vous que les groupes de disponibilité sont créés avec **par base de données prise en charge DTC** option car il ne peut pas être modifiée ultérieurement.  
3. Arrêter le traitement de BizTalk et les travaux de l’Agent SQL. 
4. Effectuez une sauvegarde complète de toutes les bases de données BizTalk. 
5. Restaurez les bases de données BizTalk sur les instances SQL actuellement dans le rôle principal du groupe de disponibilité. 
6. Script des connexions et l’Agent SQL travaux sur les Instances de SQL correspondantes actuellement dans le rôle principal du groupe de disponibilité.  
7. Exécutez le `UpdateDatabase.vbs` et `UpdateRegistry.vbs` des scripts sur les ordinateurs BizTalk en procédant comme suit. Entrez l’écouteur du groupe de disponibilité en tant que le nouveau nom du serveur dans le fichier xml des informations de mise à jour d’entrée.  
    1. Arrêtez tous les services BizTalk et SSO de l’entreprise sur le serveur BizTalk. Arrêter le Service SQL Agent sur SQL Server. 
    2. Sur BizTalk Server, modifiez SampleUpdateInfo.xml dans le dossier suivant : 
 
        ordinateur 32 bits : `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore`
 
        ordinateur 64 bits : `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore`
 
            1. Replace "SourceServer" with the source server name (old SQL Server hosting old databases).  
            2. Replace "DestinationServer" with the name of the destination server, which should be the availability group listener name.  
            3. If you have the BAMAnalysis, BAM databases or RuleEngineDB, uncomment the appropriate sections. 

    3. Ouvrez une invite de commandes et accédez à : 
 
        ordinateur 32 bits : `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore` 
 
        ordinateur 64 bits : `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore` 
 
        À l’invite de commandes, exécutez :  
    `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
 
        Exécutez UpdateDatabase.vbs sur un seul serveur dans le groupe BizTalk. 

    4. Copiez le fichier SampleUpdateInfo.xml modifié dans le dossier suivant sur chaque ordinateur BizTalk Server dans ce groupe BizTalk : 
 
        ordinateur 32 bits : `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore` 
 
        ordinateur 64 bits : `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore` 
 
    5. Sur chaque ordinateur dans le groupe BizTalk Server, ouvrez une invite de commandes et accédez à : 
 
        ordinateur 32 bits : `%SystemRoot%\Program Files\Microsoft BizTalk Server 20xx\Schema\Restore`
 
        ordinateur 64 bits : `%SystemRoot%\Program Files (x86)\Microsoft BizTalk Server 20xx\Bins32\Schema\Restore` 
 
        À l’invite de commandes, exécutez :  
    `cscript UpdateRegistry.vbs SampleUpdateInfo.xml` 
 
        Exécutez UpdateRegistry.vbs sur chaque serveur dans le groupe BizTalk. 
 
8. Maintenant, déplacez les bases de données dans leurs groupes respectifs de la disponibilité. 
9. Répliquer le profil de DBMail SQL et le compte pour les alertes BAM sur SQL d’instances qui héberge le réplica de la base de données BAMAlerts. 
10. Placez le corps d’étapes de travail de l’Agent SQL dans un bloc IF pour vous assurer qu’ils s’exécuter uniquement si la cible est le serveur principal. 
11. Script des connexions et des travaux de l’Agent SQL pour les répliquer sur le réplica correspondant. Le script UpdateDatabase met également à jour le nom du serveur dans les travaux de Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb et TrackedMessages_Copy_BizTalkMsgBoxDb. Par conséquent, un script les travaux SQL Agent uniquement après l’exécution du script UpdateDatabase. 

## <a name="requirements"></a>Spécifications 
* BizTalk Server Enterprise 2016
* SQL Server 2016 Enterprise
* Windows Server 2012 R2
* Windows Server 2016 

### <a name="availability-group-listener-configured-with-non-default-port-1433"></a>Écouteur de groupe de disponibilité configuré sans valeur par défaut du port (1433) 
Utiliser l’alias SQL sur les ordinateurs BizTalk Server. 

### <a name="supporting-availability-group-multi-subnet-failovers"></a>Prise en charge de basculements de sous-réseaux multiples de groupe de disponibilité 
BizTalk Server utilise OLE DB Microsoft pour les connexions de base de données, ce qui ne prend pas en charge la **MultiSubnetFailover** l’option de connexion. BizTalk Server ne prend pas en charge la `MultiSubnetFailover (=TRUE)` option de connexion et cela peuvent entraîner des temps de récupération plus élevée pendant le basculement de sous-réseaux multiples. 

### <a name="read-only-routing"></a>Routage en lecture seule 
Routage en lecture seule fait référence à la capacité de SQL Server pour acheminer les connexions entrantes pour un écouteur de groupe de disponibilité vers un réplica secondaire est configuré pour autoriser des charges de travail en lecture seule. 

BizTalk n’utilise pas le routage en lecture seule pour une des connexions à ses bases de données. Cela signifie que l’option « Secondaire accessible en lecture » sur les réplicas de disponibilité dans le groupe de disponibilité n’a pas de tout impact sur les connexions de base de données BizTalk. 

### <a name="behavior-of-biztalk-server-host-instances-during-sql-server-failover"></a>Comportement des instances de l'hôte BizTalk Server pendant le basculement de SQL Server 
Si le groupe de disponibilité de SQL Server rencontre un basculement, les bases de données BizTalk Server sur le groupe de disponibilité sont temporairement indisponibles. 

#### <a name="behavior-of-in-process-host-instances-during-sql-server-failover"></a>Comportement des instances de l'hôte In-process au cours d'un basculement SQL Server 
Si les bases de données BizTalk Server ne sont pas disponibles, une instance in-process d’un hôte BizTalk Server est recyclée jusqu'à ce que la connexion à SQL Server est restaurée. Une fois la connexion aux bases de données SQL Server est restaurée, le traitement des documents reprend normalement.
 
#### <a name="behavior-of-isolated-host-instances-during-sql-server-failover"></a>Comportement des instances de l'hôte isolé au cours d'un basculement de SQL Server 
Si les bases de données BizTalk Server ne sont pas disponibles, puis s’arrête une instance isolée d’un hôte BizTalk Server, et une erreur semblable au suivant est générée dans le journal de l’Application BizTalk Server : 

    All receive locations are being temporarily disabled because either the MessageBox or Configuration database is not available. When these databases become available, the receive locations will be automatically enabled.
 
Une fois la connexion aux bases de données SQL Server est restaurée, un message d’information semblable au suivant est écrit dans le journal de l’Application BizTalk Server et le traitement des documents reprend normalement : 

    All receive locations are being enabled because both the MessageBox and Configuration databases are back online.

#### <a name="biztalk-server-log-shipping-for-disaster-recovery"></a>Journaux de BizTalk Server pour la récupération d’urgence 
BizTalk Server implémente des fonctionnalités en attente de base de données via l’utilisation de base de données de journaux de transaction. BizTalk Server d’envoi de journaux automatise la sauvegarde et la restauration de bases de données et leurs fichiers journaux des transactions, ce qui permet un serveur de secours reprendre le traitement de base de données dans le cas où la production de base de données de serveur échoue. 

**Bases de données secondaires dans le groupe de disponibilité ne sont pas des sauvegardes.** Continuer à sauvegarder des bases de données BizTalk et leurs journaux des transactions à l’aide de tâches d’envoi de journaux de BizTalk Server. Envoi de journaux BizTalk implémentation garantit que les sauvegardes sont toujours effectuées sur le réplica principal actuel de chaque base de données. Le paramètre de préférence de sauvegarde sur le groupe de disponibilité n’est pas reconnue par les travaux de l’envoi de journaux de BizTalk Server. 

Si vous ajoutez d’autres bases de données BizTalk à l’opération de sauvegarde de bases de données BizTalk, veillez à utiliser le nom de l’écouteur du groupe de disponibilité que le serveur de base de données pour eux lorsque vous configurez la sauvegarde.  
 
## <a name="references"></a>Références 
 
* [Offrant une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md)  
* [Prise en charge du logiciel Microsoft server pour les machines virtuelles Microsoft Azure](https://support.microsoft.com/kb/2721672)  
* [Mise en miroir de bases de données SQL Server, service VSS et AlwaysOn](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)  
* [Vue d’ensemble des groupes de disponibilité AlwaysOn (SQL Server)](https://msdn.microsoft.com/library/ff877884.aspx)  
* [Prise en charge des Transactions de bases de données croisées pour la mise en miroir de base de données ou de groupes de disponibilité AlwaysOn (SQL Server)](https://msdn.microsoft.com/library/ms366279.aspx)  
* [Reenlist ne peut pas être appelée lorsque SQL Server reçoit le résultat de la transaction à partir de MSDTC dans Windows Server 2012 R2](https://support.microsoft.com/kb/3090973)  
* [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)  
* [Comment déplacer les bases de données BizTalk Server](../core/how-to-move-the-biztalk-server-databases.md)  
* [Comment faire pour restaurer vos bases de données](../core/how-to-restore-your-databases.md)   
* [Délais d’attente de connexion dans le groupe de disponibilité de sous-réseaux multiples](https://blogs.msdn.microsoft.com/alwaysonpro/2014/06/03/connection-timeouts-in-multi-subnet-availability-group/)  
 
## <a name="known-limitations"></a>Limitations connues 

Ces limitations sont destinés, groupe de disponibilité AlwaysOn SQL Server, BizTalk Server et de Machines virtuelles Azure. Ces limitations peuvent ou ne peuvent pas obtenir traitées dans les futures. 

* Connexions, les travaux de l’Agent SQL, le profil de messagerie de base de données SQL et les comptes ne sont pas gérés au sein de groupes de disponibilité. Cela nécessite une modification manuelle de tâches pour vous assurer qu’ils s’exécuter sur le réplica principal. 
* SQL Server Analysis Services et SQL Server Integration Services ne participent pas les groupes de disponibilité. Sans cette prise en charge de SQL Server, il n’existe aucune solution de haute disponibilité pour ces Machines virtuelles Azure. Fonctionnalités d’analyse BAM de BizTalk Server dépendent de ces services. 
* Groupes de disponibilité ne prend pas en charge MSDTC entre les bases de données sur la même instance SQL. Par conséquent, une instance SQL 8 minimale requises pour configurer BizTalk. 
* Pour résoudre le MSDTC limitations avec groupes de disponibilité, les bases de données BizTalk peuvent être configurées à l’aide d’un minimum de deux serveurs hébergeant chaque quatre instances SQL. Toutefois, dans des Machines virtuelles Azure, équilibrage de charge interne ne prend pas en charge plusieurs adresses IP. Cela nous oblige à créer chaque instance de SQL sur un serveur distinct. 
* BizTalk Server ne peut pas utiliser le routage en lecture seule. 
* BizTalk Server ne définit pas le `MultiSubnetFailover` propriété de connexion. 
* Les travaux de sauvegarde de BizTalk à l’aide de l’envoi de journaux sera toujours cibler le réplica principal, quelles que soient les préférences de sauvegarde définie sur le groupe de disponibilité. 
 
