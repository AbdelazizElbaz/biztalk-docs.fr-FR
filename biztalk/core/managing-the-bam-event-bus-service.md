---
title: "La gestion de Service Bus d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MessageBox database, migrating data
- Primary Import database [BAM], migrating data
- migrating, data [BAM]
- managing [BAM], Event Bus Service
- Event Bus Service [BAM], managing
- Tracking Data Decode Service (TDDS)
ms.assetid: 556e7fe2-4a7d-46f6-8e55-f41be4e666dc
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f265201e371a86072c06b336b4d00bb1742f5f6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-the-bam-event-bus-service"></a>Gestion du service Bus d'événements BAM
Le service Bus d'événements BAM, ou service TDDS (Tracking Data Decode Service), traite les données de suivi (flux) stockées dans une base de données source et les conserve de manière telle qu'elles peuvent être aisément interrogées par la suite.  
  
 Le service Bus d'événements BAM déplace les données décisionnelles vers les données d'analyse du fonctionnement de BizTalk et la base de données d'importation principale BAM vers la base de données des suivis. Le service Bus d'événements BAM s'exécute en tant que sous-service dans les services BizTalk.  
  
 Pour analyser les activités d'une application transactionnelle telle que Microsoft BizTalk® Server, vous devez récupérer des données d'événements en cours d'exécution, puis les stocker momentanément dans la base de données où est conservé l'état de l'application (la base de données MessageBox, par exemple).  
  
> [!NOTE]
>  Évitez de créer sur un même ordinateur plusieurs instances d'application hébergeant les suivis pour les différents groupes BizTalk. Si les instances qui effectuent le suivi de différents groupes BizTalk existent sur le même ordinateur, vous ne serez pas en mesure de distinguer les événements qui appartiennent à quels groupes BizTalk dans la Console Administration de BizTalk ou dans le journal des événements, car tous les groupes BizTalk s’affichent avec le même nom.  
  
 Le service Bus d'événements BAM lit les données d'événements, les décode et les stocke dans une base de données Microsoft SQL Server™ où vous pouvez facilement interroger les données.  
  
 Le service Bus d'événements BAM offre les avantages suivants :  
  
-   Les données d'événements correspondent systématiquement à l'état de l'application et ne reflètent jamais la progression d'éléments non validée.  
  
-   L'impact sur les performances de l'application en cours d'exécution est minime, car les données d'événements conservent peu d'enregistrements dans la transaction locale, ce qui reflète les changements limités de l'état de l'application.  
  
-   Le stockage SQL Server pour l'état de l'application est ensuite optimisé pour des performances d'exécution accrues. Les données sont décodées par le service TDDS et stockées dans une base de données distincte : la base de données d'importation principale BAM ou la base de données des suivis. Lorsque les rapports sont générés, les données sont interrogées à partir de la base de données et affectent la base de données MessageBox, qui stocke l'état de l'application.  
  
-   Les opérations nécessaires au stockage des données d'événements dans un format permettant des interrogations ultérieures ne sont pas effectuées dans les serveurs et les bases de données de l'application. Elles sont confiées aux ordinateurs qui exécutent le service Bus d'événements BAM et la base de données SQL Server de destination.  
  
-   Les données d'événement sont traitées avec une faible latence, ce qui permet un traitement plus rapide des requêtes TDDS. Les services Bus d'événements BAM coordonnent leurs ressources pour obtenir la latence la plus faible possible.  
  
 Le serveur de Bus d'événements BAM obtient une telle coordination en utilisant une connexion à une base de données centrale contenant les informations de configuration. Chaque service Bus d'événements BAM actif envoie à la base de données centrale un message par minute contenant l'état du service Bus à un moment précis dans le temps.  
  
 Ce message est appelé message de pulsation. Chaque service Bus d'événements BAM recherche également les nouvelles tâches à effectuer. Par exemple, le service Bus d'événements BAM recherche les sessions non propriétaires telles qu'une base de données MessageBox venant d'être ajoutée.  
  
 Une session de Bus d'événements BAM correspond au mouvement des données d'événements entre la base de données source (MessageBox, par exemple) et la base de données de destination comprenant les données d'événements dans un format permettant les interrogations. Le même service Bus peut traiter une ou plusieurs sessions.  
  
 Le schéma suivant représente un groupe de serveurs Bus d'événements BAM constituant un pool de serveurs Bus.  
  
 ![](../core/media/ebiz-bam-admin-evntbuspool.gif "ebiz_bam_admin_evntbuspool")  
Schéma d'un pool de serveurs Bus d'événements BAM  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Compteurs de Performance BAM](../core/bam-performance-counters.md)  
  
-   [Procédures stockées de Service Bus d’événements BAM](../core/bam-event-bus-service-stored-procedures.md)  
  
-   [Basculement du serveur BAM événement Bus Service](../core/bam-event-bus-service-server-failover.md)  
  
-   [Création d’Instances de Service Bus d’événements BAM](../core/creating-instances-of-the-bam-event-bus-service.md)