---
title: "Planification pour une haute disponibilité2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65271fd5-5294-406f-87f8-3aa394c235a2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 310414b094b7175c6b07fc92697b460e6dd2a830
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-high-availability"></a>Planification pour une haute disponibilité
Pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], la haute disponibilité est surtout orientée sur la récupération des composants fonctionnels susceptibles d'interrompre la disponibilité dans un déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour illustrer la haute disponibilité dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], vous devez provoquer un échec et mesurer l’efficacité du produit en mode de récupération. Haute disponibilité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement rend les erreurs et échecs transparent pour les systèmes et les applications externes et garantit que tous les services continuent de fonctionner correctement avec une perturbation minimale.  
  
 Conception d’un [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] déploiement qui offre une haute disponibilité implique l’implémentation de redondance pour chacun des composants fonctionnels impliqués dans un scénario de l’intégration de processus entreprise ou application. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]simplifie l’implémentation de ces scénarios en séparant conceptuellement les données à partir de la *hôtes* qui traitent les données. A *hôte* est un conteneur logique de BizTalk éléments, tels que les orchestrations, gestionnaires d’envoi et les gestionnaires de réception. Vous créez *instances d’hôte* et les attribuer à l’ordinateur hôte. Une instance de l'hôte est la représentation physique d'un hôte sur un serveur particulier. Il s’agit du [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] processus du service appelé BTSNTSvc.exe ou un autre processus, par exemple, le processus IIS. Offrant ainsi une haute disponibilité pour [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] implique l’exécution de plusieurs *instances d’hôte* et le clustering de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données, comme suit :  
  
-   **Architecture pour les hôtes BizTalk**. [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]vous permet de séparer les hôtes et d’exécuter plusieurs instances d’hôte pour fournir une haute disponibilité pour les fonctions clés telles que la réception des messages, le traitement des orchestrations et envoyer des messages. Ces hôtes ne requièrent pas de mise en cluster ou de mécanisme d'équilibrage de charge, car [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] répartit automatiquement la charge entre les différents ordinateurs par le biais des instances d'hôte. Toutefois, héberge les gestionnaires de réception en cours d’exécution pour les adaptateurs HTTP et SOAP requièrent un mécanisme d’équilibrage de charge telles que charger équilibrage réseau (NLB) pour fournir une haute disponibilité et les ordinateurs hôtes exécutant les gestionnaires de réception FTP, MSMQ, POP3, SQL et SAP nécessitent un mécanisme de clustering pour fournir une haute disponibilité.  
  
    > [!NOTE]  
    >  Vous devez toujours mettre en cluster SAP adaptateur pour prendre en charge un scénario de validation en deux phases de réception.  
  
-   **Architecture des bases de données BizTalk Server**. Configuration à haute disponibilité pour le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] bases de données se compose généralement de deux ou plusieurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de base de données des ordinateurs configurés dans une configuration de cluster de serveurs actif/passif. Ces ordinateurs partagent une ressource de disque commune (par exemple un volume RAID 1 + 0 baie de disques SCSI ou d’un réseau de zone de stockage) et utiliser le Clustering de basculement Windows pour fournir la tolérance de pannes de redondance et de sauvegarde.  
  
 Un autre composant fonctionnel BizTalk qui est essentiel pour la haute disponibilité est le serveur de secret principal. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s’appuie sur ce service pour obtenir la clé de chiffrement.  
  
 Cette section fournit des informations sur la façon d’aborder la haute disponibilité dans chacune de ces catégories. Car un [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] solution haute disponibilité repose sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], assurez-vous de déployer ces produits et à haute disponibilité avant de configurer les hôtes [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. Les liens suivants comportent des informations sur la façon d'assurer la haute disponibilité pour ces produits sous-jacents :  
  
-   **Livre blanc : Haute disponibilité : Always On Technologies** disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=156812](http://go.microsoft.com/fwlink/?LinkId=156812).  
  
-   Obtenir plus d’informations sur la résolution des problèmes avec Windows Server 2008 à le [déploiement Windows Server 2008, la gestion et la résolution des problèmes de page](http://go.microsoft.com/fwlink/?LinkId=156813) (http://go.microsoft.com/fwlink/?LinkId=156813).  
  
-   Obtenir plus d’informations sur la disponibilité et évolutivité dans Windows Server 2008 à [disponibilité et évolutivité](http://go.microsoft.com/fwlink/?LinkId=156814) (http://go.microsoft.com/fwlink/?LinkId=156814).  
  
-   Consultez le **haute disponibilité** section de la [page Windows Server 2008 R2 Articles et livres blancs](http://go.microsoft.com/fwlink/?LinkId=157760) (http://go.microsoft.com/fwlink/?LinkId=157760).  
  
## <a name="understanding-the-impact-of-a-component-failure"></a>Comprendre l’Impact de la défaillance d’un composant  
 Le tableau suivant répertorie les composants et les dépendances d’un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement et l’impact sur les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement si la dépendance ou le composant échoue. Vous devez envisager l’étendue d’une défaillance de décider d’un composant ou une dépendance de cluster.  
  
|Composant ou dépendance|Étendue de l’échec|  
|-----------------------------|----------------------|  
|[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]|Échelle du système. Si [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] échoue puis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne pourra pas traiter les documents.|  
|Serveur de secret principal|Échelle du système. Si le serveur de secret principal échoue, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne pourra pas traiter les documents. **Remarque :** si le serveur de secret principal échoue, chaque serveur BizTalk server dans le groupe BizTalk continuera à utiliser une copie en mémoire en cache le secret principal jusqu'à ce que le service SSO sur que BizTalk server est redémarré. Si le service SSO est redémarré sur les serveurs BizTalk Server, puis la copie mise en cache du secret est libérée de la mémoire et les serveurs BizTalk Server doivent être en mesure de contacter le serveur de secret principal pour obtenir une autre copie du secret. Ne redémarrez pas le service SSO de l’entreprise sur les serveurs BizTalk dans un groupe si le serveur de secret principal échoue et que vous souhaitez poursuivre le traitement des documents de BizTalk server.|  
|MSDTC|Serveur. En cas de MSDTC n’importe quel composant sur le serveur qui nécessite la prise en charge de la transaction échoue. **Remarque :** car [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et le serveur de secret principal sont dépendants de MSDTC pour la prise en charge de la transaction, l’étendue de l’échec sera au niveau du système si le MSDTC sur SQL server ou du serveur de secret principal échoue. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]requiert la prise en charge des transactions lors de la communication avec [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et le serveur de secret principal au cours des opérations d’exécution.|  
|Instance de l'hôte BizTalk|Serveur. Tous les composants hébergées dans une instance d’hôte BizTalk ne pourront pas participer au traitement de document si l’instance d’hôte échoue.|  
|Microsoft Message Queuing (MSMQ)|Serveur. En cas de MSMQ puis tout traitement de document dont dépend le service MSMQ, telles que l’adaptateur MSMQ, est arrêté sur le serveur.|  
|Système de fichiers|Serveur. Si le système de fichiers échoue puis tout traitement de document qui est dépendante du système de fichiers, telles que l’adaptateur File, est arrêté sur le serveur.|  
  
 Pour être en mesure de mieux gérer une haute disponibilité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système, vous devez avoir une bonne compréhension de la pile BizTalk : [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)], contrôleur de domaine (DNS, DHCP), [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], IIS server, serveur de fichiers, serveur MSMQ, des applications externes. Cette section se concentre sur la haute disponibilité de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et dépendantes [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.  
  
## <a name="biztalk-server-high-availability-examples"></a>Exemples de haute disponibilité de BizTalk Server  
 Pour des exemples de scénarios dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui fournissent une haute disponibilité via des niveaux de montée en charge des ordinateurs hôtes, consultez [exemples BizTalk Server haute disponibilité de scénarios](http://go.microsoft.com/fwlink/?LinkId=156815) (http://go.microsoft.com/fwlink/?LinkId=156815).  
  
## <a name="see-also"></a>Voir aussi  
 [Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)   
 [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [Liste de vérification : Accroître la disponibilité avec la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)