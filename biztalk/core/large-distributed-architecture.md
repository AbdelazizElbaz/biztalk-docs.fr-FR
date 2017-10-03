---
title: Large Distributed Architecture | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, examples
- data, domains
- corporate domains
- networks
- domain types, service
- domain types, processing
- screened subnet
- service domains
- domain types, corporate
- domain types, data
- perimeter networks
- processing domains
- demilitarized zone
- architecture, large distributions
ms.assetid: 3cfc07c4-0b1d-489b-9a29-55187fde0539
caps.latest.revision: "26"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c29bda1c60b59db42fabacaa0c02175aed90bda
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="large-distributed-architecture"></a>Architecture distribuée étendue
Pour plus d’informations sur l’architecture système pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] déploiement, consultez [exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md).  
  
 L'architecture présentée dans cette section est destinée à un environnement de production. Elle n'inclut pas d'environnement de développement ou de test, ni de recommandations relatives à un réseau de gestion pour l'environnement. Pour plus d’informations sur la configuration d’un développement vers un environnement de test et d’un test dans un environnement de production de mise en lots, consultez [déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md).  
  
 La figure suivante illustre une architecture de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement distribuée, qui prend en compte la sécurité.  
  
 ![Large Distributed Architecture](../core/media/06c5ae00-17aa-42f5-88d1-487bf7720183.gif "06c5ae00-17aa-42f5-88d1-487bf7720183")  
Architecture distribuée sécurisée de BizTalk Server  
  
 Cette architecture contient les cinq domaines suivants :  
  
 **Réseau de périmètre.** Le réseau de périmètre (également appelé DMZ, zone démilitarisée et sous-réseau filtré) contient des serveurs qui fournissent des services Internet pour une entreprise. Ce domaine peut contenir des serveurs hébergeant les emplacements physiques auxquels ou à partir desquels les services de transport Internet envoient ou reçoivent les messages échangés avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce domaine ne comprend pas de serveurs BizTalk Server, d'emplacements de réception BizTalk ni de serveurs d'authentification unique de l'entreprise (SSO). Si vous vous servez de l'adaptateur SOAP ou HTTP, vous pouvez utiliser des règles de proxy inverse (l'implémentation du serveur Forefront Threat Management Gateway [TMG] 2010 est appelée Publication sur le Web) pour relayer le message en provenance du pare-feu connecté à Internet (FW4) vers le pare-feu protégeant le domaine des interfaces de service (FW3). Pour plus d’informations sur les règles de publication Web, consultez le site Web de Microsoft à [http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340).  
  
 Dans la figure ci-dessus, les serveurs figurant dans le réseau de périmètre sont ceux qui se trouvent dans un domaine à l'extérieur de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Par conséquent, certains de ces serveurs peuvent également se trouver dans emplacements distants. Par exemple, le serveur FTP (File Transfer Protocol) pourrait se trouver dans un emplacement distant, tandis que le serveur SMTP (Simple Mail Transfer Protocol) pourrait être le serveur de messagerie de l’entreprise, un serveur de fournisseur de services Internet (ISP) ou un serveur SMTP distant.  
  
 **Domaine des Interfaces de service.** Il s'agit du domaine où commence le traitement des messages. Ce domaine contient les serveurs sur lesquels se trouvent les gestionnaires de réception et d'envoi de BizTalk. C'est là que les ports, emplacements de réception, pipelines, mappages, schémas et assemblys de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] se trouvent pour recevoir, router et envoyer des messages. Le nombre de serveurs BizTalk Server présents dans ce domaine dépend du nombre d'hôtes et d'instances de l'hôte dont vous avez besoin pour répondre aux exigences de performances de votre société.  
  
 **Domaine des services.** Ce domaine contient les services que les serveurs du domaine des interfaces de service considèrent comme fiables et nécessaires pour traiter correctement les messages, mais qui nécessitent une couche de protection supplémentaire contre d'éventuelles attaques en provenance du réseau de périmètre, par exemple des serveurs de traitement qui assurent les orchestrations, les pipelines, les services SSO, le moteur de règles d'entreprise et d'autres processus d'entreprise de BizTalk.  
  
 Ce domaine contient également les services auxquels le domaine de l'entreprise doit accéder, mais que vous devez protéger contre d'éventuelles menaces extérieures. Un des serveurs dans ce domaine héberge les outils d’administration : l’utilitaire d’administration Enterprise Single Sign-On (SSO) et de la Console Administration de BizTalk. Ce domaine comprend également le serveur de secret principal SSO, qui contient le secret principal (clé de chiffrement) que le système SSO utilise pour chiffrer les données dans la base de données SSO. L'un des serveurs de ce domaine a une instance d'hôte qui prend en charge le suivi des données d'analyse du fonctionnement et de l'entreprise.  
  
> [!NOTE]
>  Dans un système SSO, certains serveurs de traitement peuvent contenir uniquement le service SSO sans composant BizTalk Server. Pour plus d’informations, consultez [haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md).  
  
 **Domaine de données.** Le domaine des données est le plus éloigné d'Internet, car il contient les bases de données SQL Server qui stockent des données d'entreprise et de traitement critiques. Il ne considère aucune autre domaine comme fiable. Si chaque base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut se trouver sur un serveur distinct exécutant SQL Server, il est recommandé de combiner les bases de données en fonction du type principal de traitement qu'elles effectuent (principalement des opérations de lecture, principalement des opérations d'écriture, ou les deux) :  
  
-   Un serveur SQL Server pour chaque base de données MessageBox. Vous pouvez ajouter des bases de données MessageBox pour l'équilibrage de charge. Il s'agit de bases de données assurant une activité intense de lecture et d'écriture.  
  
-   Un serveur SQL Server pour la base de données SSO. BizTalk Server lit des opérations principalement dans cette base de données. Cette base de données conserve des données sensibles. Les autorisations d'accès qui lui sont appliquées doivent être très restrictives.  
  
-   Un serveur SQL Server pour la gestion de BizTalk et les bases de données du moteur de règles d’entreprise. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]principalement lit des opérations dans ces bases de données. Ce serveur contient également la base de données des suivis dont l'activité d'écriture est intense.  
  
-   Un serveur SQL Server pour la base de données des suivis du serveur d'analyse.  
  
-   Un serveur SQL Server pour la base de données Microsoft Operations Manager (MOM).  
  
-   Un serveur SQL Server pour la copie des journaux de transaction au niveau du système de destination.  
  
> [!IMPORTANT]
>  Pour la protection de basculement, nous vous recommandons de que mettre en cluster chaque base de données BizTalk. Pour plus d’informations sur le clustering de basculement SQL Server, consultez le Site de Web Microsoft MSDN à [http://go.microsoft.com/fwlink/?LinkId=131016](http://go.microsoft.com/fwlink/?LinkId=131016).  
  
> [!NOTE]
>  Pour plus d’informations sur le système de destination pour l’envoi de journaux, consultez [sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-the-biztalk-server-databases.md).  
  
 Dans la figure précédente, le serveur Forefront Threat Management Gateway (TMG) 2010 agit en tant que pare-feu logiciel pour aider à protéger et à contenir chacun de ces domaines. En outre, chaque domaine a son propre contrôleur de domaine, avec une approbation établie à partir du domaine contenant les serveurs critiques (domaine des données) vers les serveurs connectés à l'extérieur (réseau de périmètre et domaine de l'entreprise), et les serveurs ont accès uniquement aux services opérés dans d'autres domaines auxquels ils doivent se connecter. Aucun pare-feu ne restreint le trafic vers le domaine des données en provenance des interfaces de service et des domaines de services (FW1). De même, aucun pare-feu (FW2) ne restreint le trafic vers le domaine des services, en provenance des interfaces de service et des domaines d'opération.  
  
 **Domaine d’entreprise.** Il s'agit du domaine intranet qui contient tous les ordinateurs de bureau de votre société ou service, ainsi que tous les serveurs fournissant des services aux travailleurs de l'information qui opèrent en leur sein. Ce domaine comprend deux conteneurs logiques distincts :  
  
-   **Services intranet.** Ce conteneur comprend les serveurs qui échangent des messages avec des partenaires internes pour les adaptateurs SQL et FILE. Bien qu'il s'agisse d'un intranet, il diffère du réseau d'entreprise où la plupart des utilisateurs ont leurs comptes et services. Comme le réseau de périmètre illustré dans la figure, certains serveurs de ce conteneur peuvent se trouver dans un emplacement différent. Par exemple, l'emplacement (dossier) d'envoi et de réception pour l'adaptateur FILE peut se situer à n'importe quel niveau à l'extérieur du domaine des interfaces de service, tandis que vous placez le serveur exécutant SQL Server pour l'adaptateur SQL dans le domaine des interfaces de service.  
  
-   **Opérations.** Ce conteneur comprend les clients du service Terminal Server que les informaticiens utilisent pour administrer, maintenir et surveiller à distance les performances et l'intégrité de tous les serveurs de l'environnement. Grâce aux services Terminal Server, les informaticiens se connectent au serveur d'administration du domaine des services, à partir duquel ils effectuent des tâches d'administration pour tous les serveurs de l'environnement.  
  
 Si des ordinateurs de développement peuvent figurer dans le domaine de l'entreprise, leur configuration n'entre pas dans le cadre de ce document.  
  
 Pour plus d’informations sur l’architecture de BizTalk Server, y compris les services de traitement d’informations, consultez [grande Architecture distribuée avec les Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md).  
  
 Les relations d'approbation entre les domaines sont les suivantes :  
  
-   Le domaine des données n'approuve aucun autre domaine.  
  
-   Le domaine des interfaces de service approuve le domaine des données.  
  
-   Le domaine des services approuve le domaine des données.  
  
-   Le domaine de l'entreprise approuve les domaines des services.  
  
 Pour plus d’informations sur la configuration d’un pare-feu pour les domaines et approbations, consultez le site Web de support technique et de Microsoft Help à [http://go.microsoft.com/fwlink/?LinkId=25230](http://go.microsoft.com/fwlink/?LinkId=25230).  
  
 Bien que le figure précédente se concentre sur la sécurité, vous pouvez également étendre l'architecture avec un équilibrage de la charge réseau et des services de cluster pour assurer la disponibilité et les performances.  
  
 Pour plus d’informations sur la haute disponibilité, consultez [planification pour une haute disponibilité](../core/planning-for-high-availability3.md).  
  
 Pour plus d’informations sur les performances, consultez [planification des performances de débit soutenu](../core/planning-for-sustained-performance.md).  
  
 Le tableau suivant résume les types de serveurs que vous pouvez configurer avec un équilibrage de la charge réseau en fonction du contrat de niveau de service (SLA) que vous devez respecter :  
  
|Nom|Type|Domaine|  
|----------|----------|------------|  
|HTTP (Réc.)|Services Internet (IIS)|Réseau de périmètre|  
|Gestionnaire de réception (isolé)|Services Internet (IIS)|Domaine des interfaces de service|  
|Portail BAM|Services Internet (IIS)|Domaine des interfaces de service|  
  
 Le tableau suivant résume les types de serveurs que vous pouvez mettre en cluster en fonction du contrat de niveau de service (SLA) que vous devez exécuter :  
  
|Nom|Type|Domaine|  
|----------|----------|------------|  
|Exchange (envoi)|Exchange Server|Réseau de périmètre|  
|Gestionnaire de réception (hôte In-process) pour adaptateurs FTP et POP3|BizTalk Server|Domaine des interfaces de service<br /><br /> Domaine de l'entreprise|  
|Serveur de secret principal|BizTalk Server|Domaine des services|  
|Tous les serveurs SQL Server|SQL Server|Domaine des données|  
  
 Pour plus d’informations sur l’architecture de BizTalk Server, y compris les services de traitement d’informations, consultez [grande Architecture distribuée avec les Services destinés aux travailleurs](../core/large-distributed-architecture-with-information-worker-services.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’architecture BizTalk Server](../core/sample-biztalk-server-architectures.md)   
 [Architecture réduite](../core/scaled-down-architecture.md)