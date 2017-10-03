---
title: "Comment créer un environnement d’hébergement de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- hosting environments, creating
- managing [hosts], hosting environments
- hosts, environments
- managing [hosts], creating
- creating, hosting environment
ms.assetid: 6f335139-1121-45ff-88da-5c626b8fff97
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa31308db26970d3d8274d42720dfba1cb5f00c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-biztalk-server-hosting-environment"></a>Création d'un environnement d'hébergement BizTalk Server
Avant de créer votre environnement d'hébergement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], observez les recommandations suivantes :  
  
-   **Utilisez différents hôtes pour les orchestrations approuvées et non approuvés et les gestionnaires de réception**  
  
     Tous les éléments exécutés dans un hôte (par exemple, les orchestrations, les pipelines ou les gestionnaires de réception et d'envoi) fonctionnent sous la même identité et ont accès aux files de travail et files d'attente de messages interrompus de cet hôte.  
  
     En cas d'échec de l'envoi d'un message à une orchestration en raison d'erreurs d'autorisation, le message est placé dans la file d'attente de messages interrompus de l'hôte où le processus d'envoi (un pipeline de réception ou une autre orchestration) est exécuté. Toutefois, si l'orchestration et le processus d'envoi (par exemple, un pipeline de réception) sont exécutés dans le même hôte, l'orchestration peut toujours accéder au message dans la file d'attente de messages interrompus. L'exécution d'une orchestration non approuvée dans un hôte approuvé peut compromettre votre système.  
  
     Il est recommandé d'exécuter les orchestrations non approuvées dans un hôte distinct avec un compte de service différent de celui des hôtes approuvés de votre groupe BizTalk. Pour plus d’informations sur la désignation d’un hôte comme approuvé, voir [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
-   **Limiter la taille de base de données et de journal dans les bases de données BizTalk Server**  
  
     La taille de la base de données MessageBox BizTalk et de la base de données des suivis BizTalk augmente beaucoup plus rapidement que celle des autres bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans le cadre de votre programme de sauvegarde et de maintenance, vous devez fréquemment mettre à jour ces bases de données.  
  
     Par défaut, dans les tables des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], aucune limite de taille n'est définie pour les journaux. Il est recommandé, dans le cadre de votre programme de sauvegarde et de maintenance, de limiter la taille des journaux afin d'éviter que ceux-ci ne deviennent trop volumineux et ne saturent l'espace disque. Pour plus d’informations sur la gestion de la taille de la base de données de suivi, consultez [l’archivage et la purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md).  
  
-   **Utiliser le clustering de SQL Server**  
  
     Pour garantir une haute disponibilité des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est recommandé de mettre en cluster les serveurs SQL Server sur lesquels sont stockées les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette opération permet de réduire les temps d'arrêt en cas de défaillance de l'une des bases de données ou du serveur SQL Server. Pour plus d'informations sur la mise en cluster du serveur SQL Server, consultez la rubrique « Failover Clustering Architecture », relative à l'architecture de clusters avec basculement, dans la documentation en ligne de SQL Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   Les instructions contenues dans la procédure suivante supposent que vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec l'option d'installation complète. Si vous n’avez pas installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avec l’option installation complète, certains objets d’administration répertoriés à l’étape 1 ne peuvent pas être sur votre système.  
  
### <a name="to-create-a-biztalk-server-hosting-environment"></a>Pour créer un environnement d'hébergement BizTalk Server  
  
1.  Créez un projet BizTalk dans la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la création d’un nouveau [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de groupe, consultez [groupes de configuration à l’aide de la Configuration de BizTalk Server](http://msdn.microsoft.com/library/16beb7bb-091c-4056-8622-cc79c95186e9).  
  
     La configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée les objets d'administration suivants :  
  
    |Objet d'administration| Description|  
    |---------------------------|-----------------|  
    |**Administration de BizTalk** base de données (BizTalkMgmtDb)|Base de données constituant la banque centrale de méta-informations de tous les serveurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**BizTalk MessageBox** base de données (BizTalkMsgBoxDb)|Base de données stockant les prédicats d'abonnement. Elle constitue une plateforme d'hôte dans laquelle sont conservées les files d'attente et les tables d'état de chaque hôte de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. La base de données MessageBox stocke également les messages et les propriétés de message. Pour plus d’informations sur les bases de données MessageBox, y compris l’ajout de bases de données MessageBox supplémentaires, consultez [la gestion des bases de données MessageBox](../core/managing-messagebox-databases.md).|  
    |**Server**|Ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé et configuré, et sur lequel les instances d'hôte sont exécutées. Les instances d'hôte sont créées à partir d'un hôte créé sur un serveur. Pour plus d’informations sur la création d’un ordinateur hôte, consultez [la création d’un nouvel hôte](../core/how-to-create-a-new-host.md). Pour plus d’informations sur la création d’instances d’hôte, consultez [l’ajout d’une Instance d’hôte](../core/how-to-add-a-host-instance.md).|  
    |**Importation principale BAM** base de données (BAMPrimaryImport)|Base de données dans laquelle l'outil d'analyse BAM collecte les données de suivi.|  
    |**Moteur de règles** base de données (BizTalkRuleEngineDb)|Base de données constituant un référentiel de stratégies, de règles et de vocabulaires pour les références de données dans les règles d'entreprise.|  
    |**Suivi BizTalk** base de données (BizTalkDTADb)|Base de données stockant les données d'entreprise et d'analyse du fonctionnement traitées par le moteur de suivis [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**L’authentification unique** base de données (SSODB)|Base de données stockant les informations d'identification.|  
    |**Hôte in-process** avec les instances d’hôte correspondantes|Hôte de type In-process s'exécutant dans l'espace de processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**Hôte isolé** avec les instances d’hôte correspondantes|Hôte isolé s'exécutant en dehors de l'installation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |HTTP/S, Message Queuing BizTalk, FILE, SMTP, SOAP et SQL|L'Assistant Configuration crée les adaptateurs intégrés à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
  
2.  Ajoutez des composants à votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] selon les besoins à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou de WMI. Pour déployer votre solution, ajoutez des bases de données MessageBox, des hôtes et des serveurs.  
  
3.  Créez des instances d'hôte sur les serveurs mappés à l'aide de la console Administration de BizTalk ou de WMI. Cette étape détermine les serveurs sur lesquels doit fonctionner [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. À mesure de l'évolution des besoins de votre entreprise, vous pouvez ajouter ou supprimer des serveurs et modifier le mappage serveur-hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Ordinateurs hôtes](../core/hosts.md)   
 [Instances d’hôte](../core/host-instances.md)