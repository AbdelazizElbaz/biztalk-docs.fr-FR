---
title: "Suivi des activités et contrôle d’intégrité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c5d7415-38da-47b5-8dbc-0a2ea74548d9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b1720535b58a50fe0c5bd3478bc9b9ec90d0d8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="health-and-activity-tracking"></a>Suivi des activités et du fonctionnement
Le **intégrité et l’activité de suivi** outil a été supprimé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009.  Le rôle de l’outil HAT était de suivre et d’afficher des informations relatives aux live et les données de message historiques stockées dans la base de données des suivis BizTalk.  Il permettait également de déboguer le flux d'une orchestration et d'afficher le flux d'un message via un affichage séquentiel.  Un Générateur de requête prenait en charge les requêtes standard et personnalisées sur les données de suivi.  
  
 Si l'outil Suivi des activités et du fonctionnement n'est plus invoqué directement à partir du menu [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ses fonctionnalités de suivi sont toujours indirectement disponibles dans l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  Les informations relatives aux activités et au fonctionnement sont accessibles grâce à une intégration améliorée et à des requêtes de suivi supplémentaires au sein de la page Hub du groupe dans la console Administration de BizTalk Server.  
  
 La majorité de la documentation qui entoure le suivi des activités et du fonctionnement des données, consultez [afficher un Message de suivi et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md).  Certaines informations de cette section inclut [meilleures pratiques pour le Message et le suivi des données d’Instance](../core/best-practices-for-message-and-instance-data-tracking.md), [comprendre des données de suivi](../core/understanding-tracked-data.md), [affichage de l’historique et les données de suivi](../core/viewing-historical-and-tracked-data.md), [Affichage des flux de messages](../core/viewing-message-flow.md), et [débogage d’une Orchestration](../core/debugging-an-orchestration.md).  
  
 Pour plus d'informations sur les améliorations et les requêtes supplémentaires dans cette page, consultez les rubriques suivantes :  
  
-   [À l’aide de la Page Hub du groupe](../core/using-the-group-hub-page.md)  
  
-   [À l’aide de l’onglet requête de la Console Administration](../core/using-the-administration-console-query-tab.md)  
  
-   [Comment rechercher des événements de Message suivis](../core/how-to-search-for-tracked-message-events.md)  
  
-   [Comment rechercher des Instances de Service suivies](../core/how-to-search-for-tracked-service-instances.md)