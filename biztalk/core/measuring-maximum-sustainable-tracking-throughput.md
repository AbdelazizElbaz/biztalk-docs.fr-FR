---
title: "Mesurer le débit de suivi maximal acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35605427-0217-4bdd-8b4a-3e68b3f5f452
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af62a8c49f8ac5a36d3607696bef8e3173d7573e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="measuring-maximum-sustainable-tracking-throughput"></a>Mesure du débit de suivi maximal acceptable
Après avoir déployé une solution sectorielle sur la plateforme [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez faire le suivi du système et l'analyser afin de comprendre ce qui suit :  
  
-   performances du système ;  
  
-   exceptions et erreurs susceptibles de se produire et pourquoi ;  
  
-   état actuel des processus d'entreprise implémentés en tant que solutions BizTalk.  
  
 Pour de nombreuses organisations, il est également important d’enregistrer les messages bruts réels transitant via le système à des fins de non-répudiation. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]fournit deux types de fonctionnalités de suivi qui remplissent ces conditions :  
  
-   **Suivi des données et activité (DTA) suivi**. DTA effectue le suivi de propriétés de message définies par l'utilisateur, d'événements de débogage d'orchestration, d'événements de flux de message et d'état de l'instance du service. Ce suivi permet d'interroger les données stockées dans la base de données des suivis DTA BizTalk (BizTalkDTADb). Le suivi DTA inclut également le suivi de messages bruts, connus en tant que corps de message, pour la résolution des problèmes et à des fins de non-répudiation.  
  
-   **Le suivi de Business Activity Monitoring (BAM)**. BAM utilise un profil de suivi défini par l'utilisateur pour effectuer le suivi de l'état d'un processus d'entreprise dans un ensemble spécial de bases de données BAM.  
  
 Dans cette rubrique, nous allons décrire l'architecture DTA et une approche systématique afin de déterminer le débit maximal acceptable qu'un système utilisant DTA peut soutenir indéfiniment. Bien que DTA et BAM partagent certains composants architecturaux, cette rubrique décrit seulement le comportement de DTA. Pour plus d’informations sur l’architecture BAM, consultez [analyse BAM (Business Activity)](../core/business-activity-monitoring-bam.md).  
  
## <a name="overview-of-dta-tracking-architecture"></a>Vue d'ensemble de l'architecture de suivi DTA  
 Alors que des messages sont transférés sur le système, différents éléments suivis tels que des corps de message, des propriétés et des événements, traversent une série de processus et de bases de données dont le but ultime consiste à les écrire dans la base de données BizTalkDTADb. Une fois ces éléments consignés dans la base de données BizTalkDTADb, vous pouvez utiliser le suivi pour interroger les données suivies. Pour plus d’informations sur la configuration et à l’aide de la BizTalkDTADb de la base de données et le suivi des modifications, consultez [affichage de l’historique et les données de suivi](../core/viewing-historical-and-tracked-data.md).  
  
 Pour garantir la viabilité du système et son fonctionnement indéfini à un débit de messages donné, le chemin emprunté par les éléments suivis pour accéder à la base de données BizTalkDTADb et la base de données elle-même doivent rester sains. Par exemple, les messages accumulés dans les tables de base de données en chemin ou dans le DTA peuvent provoquer la croissance du fichier de base de données non lié qui ne serait pas acceptable si elle n'était pas gérée correctement.  
  
 Commençons par comprendre l'architecture et les chemins de communication que les informations suivies traversent. Ceci expose les ressources clés et les indicateurs de performance que vous devez analyser afin de déterminer dans quelle mesure le système de suivi suit le flux de messages qui traversent le moteur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 La figure suivante présente l'architecture de suivi DTA et les chemins de communication.  
  
 ![Vue d’ensemble du suivi DTA](../core/media/dtatrackingoverview.gif "DTATrackingOverview")  
  
 Si l'on prend les processus numérotés dans la figure dans l'ordre, tous les flux de données DTA entrent et sortent de la base de données BizTalkDTADb de la façon suivante :  
  
1.  Le processus d'exécution de BizTalk Server intègre un composant appelé l'intercepteur, dont la fonction consiste à mettre en cache les éléments suivis au moment de l'exécution et, lors du prochain aller-retour dans la base de données MessageBox (par exemple, pour la mise en file d'attente d'un message dans la base de données MessageBox), à transférer ces éléments mis en cache dans cette base de données. L'intercepteur détermine les éléments à suivre en analysant la configuration de suivi (également appelée profil de suivi) qui est obtenue à partir de la base de données de gestion et mise en cache dans chaque instance d'exécution de l'hôte pour être utilisée par l'intercepteur.  
  
     Comme le montre la figure précédente, deux flux de données sont insérés dans la base de données MessageBox :  
  
    -   l'un est représenté par la table Spool ;  
  
    -   l'autre est représenté par la table TrackingData.  
  
     Les corps de message suivis utilisent les deux flux, à savoir que les corps de message (semblables à des blobs de données) sont traités via un ensemble de tables représentées par la table Spool. Les événements de message associés aux corps de message (par exemple, les identificateurs de message, à quel moment les corps de message ont été suivis, à quelles instances les corps de message sont associés) sont gérés via la table TrackingData. Tous les éléments suivis, qui ne sont pas associés au suivi des corps de message, sont gérés uniquement via la table TrackingData.  
  
2.  La base de données MessageBox n'est que la première étape des données suivies ; elle est utilisée pour mettre en cache les données suivies de sorte que le composant d'exécution puisse continuer le traitement sans être directement bloqué par d'autres traitements des données de suivi.  
  
     Pour que les corps de message suivis (blobs) soient transférés à la base de données BizTalkDTADb afin que vous puissiez les afficher et les archiver dans un emplacement de stockage plus permanent, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait appel à un travail d'agent SQL, appelé TrackedMessages_Copy_BizTalkMsgBoxDb, qui est exécuté sur chaque serveur de base de données MessageBox. Ce travail doit copier les corps de message marqués pour suivi dans la base de données BizTalkDTADb.  
  
3.  Toutes les données suivies autres que les corps de message sont déplacées de la base de données MessageBox dans la base de données BizTalkDTADb par un service appelé TDDS, qui est exécuté dans un ou plusieurs hôtes [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. À chaque fois qu'un hôte est configuré pour le suivi via les pages de propriétés de l'hôte de la console Administration de BizTalk Server, le sous-service TDDS est exécuté dans chaque instance de cet hôte.  
  
4.  Sauf si la base de données BizTalkDTADb est purgée régulièrement, elle reste non liée, ce qui, à terme, risque de poser des problèmes de fonctionnement. Une seul travail de l'agent SQL, appelé BizTalkDTADb (travail de purge et d'archivage DTA), effectue le travail de purge de la base de données BizTalkDTADb. Par défaut, ce travail est exécuté toutes les minutes et purge toutes les instances terminées antérieures à certaines durées configurées par l'utilisateur (par exemple, 24 heures).  
  
     Pour plus d’informations sur le travail DTA Purge and Archive, consultez [la configuration de la Purge et archivage](../core/how-to-configure-the-dta-purge-and-archive-job.md).  
  
5.  Ce travail peut également archiver les données BizTalkDTADb en tant que sauvegarde SQL pour un stockage de longue durée et/ou l'affichage hors ligne des données. Si les données BizTalkDTADb archivées doivent être interrogées, elles doivent d'abord être restaurées en tant que nouvelle base de données dans SQL Server. Vous pouvez ensuite utiliser le suivi ou l'Analyseur de requêtes SQL pour les interroger.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comprendre le comportement de performances de suivi DTA](../core/understanding-dta-tracking-performance-behavior.md)  
  
-   [Scénarios de test pour mesurer le débit maximal acceptable du suivi DTA](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)  
  
-   [Trucs et astuces pour trouver le débit maximal acceptable du suivi DTA](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions pour le dimensionnement de la base de données de suivi](../core/tracking-database-sizing-guidelines.md)