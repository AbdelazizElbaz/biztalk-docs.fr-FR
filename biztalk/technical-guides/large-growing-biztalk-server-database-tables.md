---
title: "Grand croissance des Tables de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f30372f7-ab90-4ebb-9022-ac3ae3309459
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1253f57a38ea0658d15e536a4f7b614cc52aed7f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="large-growing-biztalk-server-database-tables"></a>Grand croissance des Tables de base de données BizTalk Server
Le tableau suivant répertorie les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tables généralement la croissance la plus grande. Vous pouvez utiliser ces données pour déterminer l’origine d’un problème potentiel.  

## <a name="tables-list"></a>Liste des tables
|Table| Description|Commentaires|  
|-----------|-----------------|--------------|  
|*HostNameQ*_Suspended table|Cette table contient une référence à des messages dans la table de mise en attente qui sont associés à des instances suspendues pour cet hôte. Cette table est dans la base de données BizTalkMsgBoxDb.|Si le *HostNameQ*_Suspended tables ont plusieurs enregistrements, les tables pourraient être contenant les instances suspendues valides qui s’affichent dans le **Hub du groupe** page. Vous pouvez mettre fin à ces instances. Si ces instances n’apparaissent pas dans le **Hub du groupe**, les instances sont probablement la mise en cache instances ou orphelins des rapports d’échec de routage. Lorsque vous terminez les instances suspendues, vous nettoyer les éléments dans cette table et de leurs lignes associées dans les tables du spouleur et des Instances.|  
|*HostNameQ* table|Cette table contient une référence à des messages dans la table de mise en attente qui sont associés à l’hôte et ne sont pas interrompus. Cette table est dans la base de données BizTalkMsgBoxDb.|Si le *HostNameQ* tables ont plusieurs enregistrements, les types suivants d’instances peuvent exister :<br /><br /> -Les instances prêts à l’exécution<br />-Instances actives<br />-Instances en attente.<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]a besoin de temps « » et les instances de processus. Cette table peut augmenter lorsque le taux de traitement distance les autres secteurs la vitesse de sortie de traitement. Ce scénario peut également se produire en raison d’une base de données BizTalkDTADb volumineuse ou des retards de disque SQL Server.|  
|Spouler, articles et les Fragments de tables|Ces tables stockent les données de message réel dans la base de données BizTalkMsgBoxDb.|Les tables de mise en attente, les composants et les Fragments ayant des enregistrements de nombreux implique qu’il existe un grand nombre de messages sont actuellement actifs, mise en attente ou suspendue. Selon la taille, le nombre de parties et les paramètres de la fragmentation dans ces tables, un seul message peut générer toutes ces tables. Chaque message possède exactement une ligne dans la table du spouleur et au moins une ligne dans la table des parties.|  
|Tableau d’instances|Cette table stocke toutes les instances et leur état actuel dans la base de données BizTalkMsgBoxDb.|Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrateur ne doit pas permettre de nombreuses instances suspendues doivent demeurer dans la table d’Instances. Nombre d’instances mises en attente en principe rester uniquement si la logique métier requiert les orchestrations longues. N’oubliez pas de que cette instance d’un service peut être associé à de nombreux messages dans la table du spouleur.|  
|TrackingData*_x_x* table|Cette table stocke les événements suivis dans la base de données BizTalkMsgBoxDb pour le suivi des données décoder Service TDDS (service) pour déplacer les événements de la base de données BizTalkDTADb.|Si le TrackingData_*x_x* tables sont grandes, soit le service TDDS n’est pas en cours d’exécution ou ne fonctionne pas correctement. Si le service TDDS est en cours d’exécution, passez en revue les journaux des événements et la table TDDS_FailedTrackingData dans la base de données BizTalkDTADb pour des informations sur l’erreur.|  
|Tracking_Fragments*x*, Tracking_Parts*x*, Tracking_Spool*x* tables|Deux de chacune de ces tables est dans les bases de données BizTalkMsgBoxDb et BizTalkDTADb. Est en ligne, et l’autre est hors connexion.|Le **TrackedMessages_Copy_BizTalkMsgBoxDb** travail de l’Agent SQL Server déplace les corps des messages suivis directement à ces tables dans la base de données BizTalkDTADb.|  
|table de dta_ServiceInstances|Cette table stocke les événements suivis pour les instances de service dans la base de données BizTalkDTADb.|Si cette table est volumineuse, la base de données BizTalkDTADb est probablement volumineux.|  
|table de dta_DebugTrace|Cette table stocke les événements de débogueur Orchestration dans la base de données BizTalkDTADb.|Si la table dta_DebugTrace possède un nombre d’enregistrements, forme de l’orchestration de suivi est utilisé ou a été utilisée. Si le débogage d’orchestration n’est pas nécessaire pour les opérations courantes, désactiver la forme de l’orchestration de suivi pour toutes les orchestrations. Si la forme de l’orchestration de suivi est déjà désactivé et une file d’attente existe dans la base de données BizTalkMsgBoxDb, la table dta_DebugTrace peut-être continuer à croître car le service TDDS continue de déplacer ces données dans la table dta_DebugTrace.<br /><br /> Pour contrôler la taille de la base de données BizTalkDTADb, vous pouvez choisir de désactiver le suivi global. Consultez [comment désactiver le suivi Global](../core/how-to-turn-off-global-tracking.md) et [suivi les instructions de dimensionnement de la base de données](../core/tracking-database-sizing-guidelines.md).|  
|table de dta_MessageInOutEvents|Cette table stocke les messages d’événements de suivi dans la base de données BizTalkDTADb. Ces messages d’événement suivi incluent des informations de contexte de message.|Si les tables dta_DebugTrace et dta_MessageInOutEvents dans la base de données BizTalkTrackingDb sont trop volumineux, vous pouvez tronquer les tables manuellement après l’arrêt de l’hôte de suivi. Pour obtenir des instructions sur la façon de tronquer les tables, consultez les détails de « table dta_DebugTrace » dans [952555 de la base de connaissances : comment gérer et dépanner les bases de données BizTalk Server](https://support.microsoft.com/help/952555/how-to-maintain-and-troubleshoot-biztalk-server-databases).|  
|table de dta_ServiceInstanceExceptions|Cette table stocke des informations d’erreur pour toute instance de service suspendue dans la base de données BizTalkDTADb.|En général, la table dta_ServiceInstanceExceptions devient volumineuse dans un environnement qui a régulièrement suspendu des instances.|
