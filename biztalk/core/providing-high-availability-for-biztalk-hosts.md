---
title: "Offrant une haute disponibilité pour les hôtes BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- planning, hosts
- hosts, high availability
- messages, routing
- deploying, high availability
- high availability, hosts
- hosts
- hosts, planning
- MessageBox database
ms.assetid: 9583b85c-7cad-4016-8065-5ca7de3f4359
caps.latest.revision: "47"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f964a8e170c2215c4abb2b6b5842f8fe0e159457
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="providing-high-availability-for-biztalk-hosts"></a>Configuration de la haute disponibilité pour des hôtes BizTalk
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait preuve d'une grande flexibilité en matière de haute disponibilité, car il permet, de façon stratégique, de dédier des hôtes logiques à l'exécution d'éléments précis d'une fonctionnalité tels que la réception et l'envoi de messages ou le traitement des orchestrations.  
  
 Un hôte BizTalk est un conteneur logique se trouvant dans un groupe de serveurs BizTalk Server et capable de contenir des éléments BizTalk Server tels que des gestionnaires d'adaptateur, des emplacements de réception (y compris des pipelines) et des orchestrations. En général, il faut regrouper dans un hôte particulier des éléments ayant des exigences similaires en termes d'évolutivité. Par exemple, vous devez regrouper les emplacements de réception dans un hôte « Réception », les ports d'envoi dans un hôte « Envoi » et les orchestrations dans un hôte « Traitement ».  
  
 Une fois un hôte (ou conteneur logique) créé, vous pouvez configurer les instances de l'hôte pour s'exécuter sur les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] physiques du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Une instance d'hôte s'exécute en tant que service Windows sur le ou les ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] désignés. Bien qu'il soit impossible d'exécuter plusieurs instances du même hôte sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] donné, vous pouvez exécuter plusieurs instances d'un hôte particulier en configurant les instances de l'hôte sur des ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] distincts, dans un groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également exécuter plusieurs instances de différents hôtes sur un seul ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les éléments présents dans les hôtes BizTalk permettent l'exécution des fonctions suivantes :  
  
-   **Réception** ces éléments effectuent le traitement initial des messages après leur récupération dans un emplacement de réception. Lorsqu’un ordinateur hôte contient un élément de réception, tel qu’un emplacement de réception ou d’un pipeline, il agit comme une limite de sécurité, et le message de décodage et le déchiffrement se produit dans un pipeline au sein de l’hôte.  
  
-   **Envoi** ces éléments effectuent le traitement final des messages avant leur transmission au port d’envoi. Lorsqu'un hôte contient un élément de réception, par exemple un emplacement de réception ou un pipeline, il agit comme une limite de sécurité, et le décodage ainsi que le déchiffrement du message sont réalisés dans un pipeline au sein de l'hôte.  
  
-   **Traitement** ces éléments traitent les messages selon les instructions contenues dans une orchestration.  
  
 Bien qu'un seul hôte BizTalk puisse contenir les éléments qui reçoivent, envoient et traitent les messages, il est recommandé de créer différents hôtes pour chaque fonction pour créer des limites de sécurité et faciliter la gestion et l'évolutivité. Il est notamment préférable d'utiliser des hôtes différents pour les opérations de traitement, d'envoi et de réception, et de séparer les éléments approuvés des éléments non approuvés.  
  
 Par exemple, si vous recevez un message, exécutez une orchestration et recevez dix messages, vous devez séparer les fonctions d'envoi et de réception et les répartir sur deux hôtes distincts. En effet, le trafic correspondant aux éléments d'envoi sera dix fois plus important que celui des éléments de réception. Si vous recevez un message, exécutez une orchestration et envoyez un seul message, vous pouvez considérer ces éléments comme des unités de travail et les regrouper dans un seul et même hôte. Une autre possibilité consiste à les répartir entre trois hôtes différents afin d'améliorer les performances et la flexibilité.  
  
 Hôtes BizTalk sont un des deux types, **In-process** ou **isolé**. Hôtes in-process s’exécuter à l’intérieur de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime traiter tandis que les hôtes isolés ne s’exécutent pas le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processus d’exécution. Le tableau suivant répertorie les éléments que chaque type d'hôte est susceptible de contenir.  
  
|**Type d’hôte**|**Conteneur logique pour**|  
|-------------------|-------------------------------|  
|In-Process|-Orchestrations<br />-Gestionnaires d’envoi de l’adaptateur<br />-Réception de l’adaptateur gestionnaires autres que HTTP et SOAP|  
|Isolé|Gestionnaires de réception HTTP et SOAP|  
  
 Pour plus d’informations sur les hôtes et les instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md).  
  
 Pour obtenir des hôtes BizTalk à haute disponibilité, vous devez disposer d'au moins deux instances de l'hôte pour chaque hôte de votre environnement (sur au moins deux ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]). L'existence de plusieurs instances pour chaque hôte garantit que, lorsqu'une instance d'hôte est indisponible, les autres ordinateurs exécutant les instances de cet hôte prennent le relais de l'instance défaillante et que l'ensemble du système continue de fonctionner en évitant au maximum les interruptions.  
  
## <a name="message-persistence"></a>Persistance des messages  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appuie essentiellement sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour la haute disponibilité car chaque hôte impliqué dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistre les messages dans la base de données MessageBox de BizTalk. Par exemple, lorsque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message entrant, l'hôte de réception le stocke dans la base de données MessageBox avant que d'autres hôtes le récupèrent pour le faire passer dans un processus d'orchestration avant de l'envoyer.  
  
 Si votre solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comprend une orchestration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] achemine le message vers l'hôte exécutant le processus d'entreprise (hôte de traitement) et enregistre le message dans la base de données MessageBox une fois l'orchestration terminée. L'hôte d'envoi extrait ensuite le message de la base de données MessageBox avant de l'envoyer à l'application externe concernée par l'intermédiaire de l'adaptateur d'envoi approprié.  
  
## <a name="separating-the-host-and-database-functions"></a>Séparation des fonctions d'hôte et de base de données  
 Étant donné que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sépare les données des hôtes qui les traitent, pour créer un environnement hautement disponible, vous pouvez séparer les fonctions d'hôte (envoi, réception et traitement) propres à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des fonctions de la base de données qui sont exécutées dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Vous pouvez ainsi mettre à l'échelle les hôtes de traitement, d'envoi et de réception indépendamment des bases de données. Les couches d'exécution et de base de données sont liées, c'est-à-dire que, si vous augmentez le nombre d'ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devrez probablement augmenter le nombre d'ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour gérer la charge supplémentaire. Cependant, aucun lien direct n'existe entre la couche de la base de données et celle de BizTalk. Il s'agit en effet de deux couches indépendantes que vous pouvez mettre à l'échelle de façon distincte.  
  
 Les opérations à effectuer pour obtenir une haute disponibilité des hôtes sont différentes de celles qui permettent d'obtenir une haute disponibilité des bases de données. Les sections suivantes comprennent des informations sur la procédure à suivre pour que les hôtes de réception, d'envoi et de traitement soient hautement disponibles. Pour plus d’informations sur la façon de rendre la couche de base de données hautement disponible, consultez [fournir une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md).  
  
 Dans des déploiements où les processus de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont plus nombreux que ceux de SQL Server, vous pouvez configurer plusieurs ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de sorte qu'ils utilisent l'ordinateur exécutant SQL Server. Dans une telle configuration, les ressources utilisées sont celles disponibles sur chaque ordinateur. Par exemple, si l'utilisation de l'UC ou de la mémoire est élevée (supérieure à 75 %) sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], mais faible (inférieure à 25 %) sur celui de SQL Server, vous pouvez ajouter des ordinateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] destinés à répartir la charge de travail et augmenter l'utilisation des ressources sur l'ordinateur SQL Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)  
  
-   [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)  
  
-   [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)  
  
-   [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Offrant une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [Haute disponibilité pour Enterprise Single Sign-On](../core/high-availability-for-enterprise-single-sign-on.md)