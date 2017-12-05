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
ms.openlocfilehash: f9b5ff05391eed424e7b910296cc5aa801f8cab1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="planning-for-high-availability"></a>Planification pour une haute disponibilité
Haute disponibilité pour BizTalk Server se concentre sur la récupération des composants fonctionnels susceptibles d’interrompre la disponibilité dans un déploiement de BizTalk Server.  
  
 Pour illustrer la haute disponibilité dans BizTalk Server, vous devez provoquer un échec et mesurer l’efficacité du produit en mode de récupération. Un déploiement de BizTalk Server hautement disponible rend les erreurs et échecs transparent pour les systèmes et applications externes et garantit que tous les services continuent de fonctionner correctement avec une perturbation minimale.  
  
 Conception d’un déploiement de BizTalk Server qui offre une haute disponibilité implique l’implémentation de redondance pour chacun des composants fonctionnels impliquées dans une intégration d’application ou un scénario de processus d’intégration d’entreprise. BizTalk Server simplifie l’implémentation de ces scénarios en séparant conceptuellement les données à partir de la *hôtes* qui traitent les données. A *hôte* est un conteneur logique de BizTalk éléments, tels que les orchestrations, gestionnaires d’envoi et les gestionnaires de réception. Vous créez *instances d’hôte* et les attribuer à l’ordinateur hôte. Une instance de l'hôte est la représentation physique d'un hôte sur un serveur particulier. Il est le processus du service BizTalk Server appelé BTSNTSvc.exe ou un autre processus, par exemple, le processus IIS. Par conséquent, offrant une haute disponibilité pour BizTalk Server implique l’exécution de plusieurs *instances d’hôte* et clustering avec les bases de données BizTalk Server, comme suit :  
  
-   **Architecture pour les hôtes BizTalk**. BizTalk Server vous permet de séparer les hôtes et d’exécuter plusieurs instances d’hôte pour fournir une haute disponibilité pour les fonctions clés telles que la réception des messages, le traitement des orchestrations et envoyer des messages. Ces hôtes ne nécessitent pas de mise en cluster ni mécanisme d’équilibrage de charge, car BizTalk Server répartit automatiquement la charge entre plusieurs ordinateurs à partir d’instances de l’hôte. Toutefois, héberge les gestionnaires de réception en cours d’exécution pour les adaptateurs HTTP et SOAP requièrent un mécanisme d’équilibrage de charge telles que charger équilibrage réseau (NLB) pour fournir une haute disponibilité et les ordinateurs hôtes exécutant les gestionnaires de réception FTP, MSMQ, POP3, SQL et SAP nécessitent un mécanisme de clustering pour fournir une haute disponibilité.  
  
    > [!NOTE]  
    >  Vous devez toujours mettre en cluster SAP adaptateur pour prendre en charge un scénario de validation en deux phases de réception.  
  
-   **Architecture des bases de données BizTalk Server**. Configuration à haute disponibilité pour les bases de données BizTalk Server se compose généralement de deux ou plusieurs ordinateurs de base de données SQL Server configurées dans une configuration de cluster de serveurs actif/passif. Ces ordinateurs partagent une ressource de disque commune (par exemple un volume RAID 1 + 0 baie de disques SCSI ou d’un réseau de zone de stockage) et utiliser le Clustering de basculement Windows pour fournir la tolérance de pannes de redondance et de sauvegarde.  
  
 Un autre composant fonctionnel BizTalk qui est essentiel pour la haute disponibilité est le serveur de secret principal. BizTalk Server repose sur ce service pour obtenir la clé de chiffrement.  
  
 Cette section fournit des informations sur la façon d’aborder la haute disponibilité dans chacune de ces catégories. Comme une solution de haute disponibilité de BizTalk Server repose sur Windows et SQL Server, assurez-vous de déployer ces produits et à haute disponibilité avant de configurer les hôtes BizTalk Server. Les liens suivants comportent des informations sur la façon d'assurer la haute disponibilité pour ces produits sous-jacents :  
  
-   **Solutions haute disponibilité (SQL Server)] (https://docs.microsoft.com/sql/sql-server/failover-clusters/high-availability-solutions-sql-server)**  
  
-   **[Clustering de basculement dans Windows Server](https://docs.microsoft.com/windows-server/failover-clustering/failover-clustering-overview)**
  
## <a name="understanding-the-impact-of-a-component-failure"></a>Comprendre l’Impact de la défaillance d’un composant  
 Le tableau suivant répertorie les composants et les dépendances d’un environnement BizTalk Server et l’impact sur l’environnement BizTalk Server, si la dépendance ou le composant échoue. Vous devez envisager l’étendue d’une défaillance de décider d’un composant ou une dépendance de cluster.  
  
|Composant ou dépendance|Étendue de l’échec|  
|-----------------------------|----------------------|  
|SQL Server|Échelle du système. Si SQL Server ne parvient pas BizTalk Server sera impossible de traiter les documents.|  
|Serveur de secret principal|Échelle du système. Si le serveur de secret principal échoue puis BizTalk Server ne pourra pas traiter les documents. <br/>**Remarque :** si le serveur de secret principal échoue, chaque serveur BizTalk server dans le groupe BizTalk continuera à utiliser une copie en mémoire en cache le secret principal jusqu'à ce que le service SSO sur que BizTalk server est redémarré. Si le service SSO est redémarré sur les serveurs BizTalk Server, puis la copie mise en cache du secret est libérée de la mémoire et les serveurs BizTalk Server doivent être en mesure de contacter le serveur de secret principal pour obtenir une autre copie du secret. Ne redémarrez pas le service SSO de l’entreprise sur les serveurs BizTalk dans un groupe si le serveur de secret principal échoue et que vous souhaitez poursuivre le traitement des documents de BizTalk server.|  
|MSDTC|Serveur. En cas de MSDTC n’importe quel composant sur le serveur qui nécessite la prise en charge de la transaction échoue. <br/>**Remarque :** , car SQL Server et le serveur de secret principal sont dépendantes de MSDTC pour la prise en charge de la transaction, l’étendue de l’échec sera au niveau du système si le MSDTC sur SQL server ou du serveur de secret principal échoue. BizTalk Server requiert la prise en charge des transactions lors de la communication avec SQL Server et le serveur de secret principal au cours des opérations d’exécution.|  
|Instance de l'hôte BizTalk|Serveur. Tous les composants hébergées dans une instance d’hôte BizTalk ne pourront pas participer au traitement de document si l’instance d’hôte échoue.|  
|Microsoft Message Queuing (MSMQ)|Serveur. En cas de MSMQ puis tout traitement de document dont dépend le service MSMQ, telles que l’adaptateur MSMQ, est arrêté sur le serveur.|  
|Système de fichiers|Serveur. Si le système de fichiers échoue puis tout traitement de document qui est dépendante du système de fichiers, telles que l’adaptateur File, est arrêté sur le serveur.|  
  
 Pour être en mesure de mieux gérer un système BizTalk Server hautement disponible, vous devez disposer d’une bonne compréhension de la pile BizTalk : Windows Server, le contrôleur de domaine (DNS, DHCP), BizTalk Server, SQL Server, le serveur IIS, serveur de fichiers, serveur MSMQ, des applications externes. Cette section se concentre sur la haute disponibilité de BizTalk Server et l’ordinateur SQL Server dépendant.  
  
## <a name="biztalk-server-high-availability-examples"></a>Exemples de haute disponibilité de BizTalk Server  
 Pour plus d’exemples de scénarios dans Microsoft BizTalk Server offrant une haute disponibilité via des niveaux de montée en charge des ordinateurs hôtes, consultez [scénarios de haute disponibilité exemple BizTalk Server](../core/sample-biztalk-server-high-availability-scenarios.md).
  
## <a name="see-also"></a>Voir aussi  
 [Haute disponibilité pour les hôtes BizTalk](../technical-guides/high-availability-for-biztalk-hosts.md)   
 [Haute disponibilité pour les bases de données](../technical-guides/high-availability-for-databases.md)   
 [Haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md)   
 [Liste de contrôle : Accroissement de la disponibilité avec la récupération d’urgence](../technical-guides/checklist-increasing-availability-with-disaster-recovery.md)