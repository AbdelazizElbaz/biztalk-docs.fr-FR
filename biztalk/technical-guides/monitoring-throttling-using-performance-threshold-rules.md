---
title: "Analyse de la limitation à l’aide de règles de seuil de performances | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc2c3024-a54b-4485-8110-c2ec9ec52721
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aedf8040b821230b6541785426731f1cef32099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="monitoring-throttling-using-performance-threshold-rules"></a>Analyse de la limitation à l’aide de règles de seuil de performances
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]initialisera la limitation pour protéger le système d’atteindre un état irrécupérable. La limitation peut indiquer un problème et vous aider à identifier sa source. Après avoir identifié la cause du goulot d’étranglement en fonction de l’état de limitation, analysez les compteurs de performances afin de réduire la source du problème.  
  
 Par exemple, une contention élevée sur la base de données MessageBox, peut-être en raison d’une utilisation élevée du processeur, ce qui peut être dû à la pagination excessive sur le disque, qui à son tour, peut être dû à une insuffisance de mémoire. Une contention élevée dans la MessageBox peut également provenir d’un conflit de verrouillage, qui peut être dû à des lecteurs de disques saturés.  
  
 Analyse l’état de limitation de remise de messages et l’état de limitation de publication de Message pour chaque instance d’hôte est généralement un bon point de départ de lors de la résolution des problèmes de limitation. Si la valeur de ces compteurs n’est pas zéro, il est un bon indicateur que la limitation s’applique au sein du système BizTalk Server et il est possible d’analyser la cause du goulot d’étranglement. Pour obtenir des descriptions sur les autres compteurs de performance, consultez [identifier les goulots d’étranglement au niveau de la base de données](http://go.microsoft.com/fwlink/?LinkID=154678) (http://go.microsoft.com/fwlink/?LinkID=154678) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
## <a name="biztalk-server-system-performance-counters"></a>Compteurs de performances du système BizTalk Server  
  
|Objet|Instance|Compteur|Objet de la surveillance|  
|------------|--------------|-------------|------------------------|  
|Processeur|_Total|% temps processeur|Conflit de ressources|  
|Traiter|BTSNTSvc|Octets virtuels|Fuite/encombrement de mémoire|  
|Traiter|BTSNTSvc|Octets privés|Fuite/encombrement de mémoire|  
|Traiter|BTSNTSvc|Nombre de handles|Conflit de ressources|  
|Traiter|BTSNTSvc|Nombre de threads|Conflit de ressources|  
|Disque physique|_Total|% inactivité|Conflit de ressources|  
|Disque physique|_Total|Longueur actuelle de la file d'attente du disque|Conflit de ressources|  
  
## <a name="biztalk-application-counters"></a>Compteurs d'application BizTalk  
  
|Objet|Instance|Compteur| Description|  
|------------|--------------|-------------|-----------------|  
|Messagerie BizTalk|RxHost|Nombre de documents reçus par seconde|Vitesse d'entrée|  
|Messagerie BizTalk|TxHost|Nombre de documents traités par seconde|Vitesse de sortie|  
|XLANG/Orchestrations|PxHost|Orchestrations réussies par seconde|Vitesse de traitement|  
|BizTalk : MessageBox : compteurs généraux|MsgBoxName|Taille mise en file d'attente|Taille cumulée de toutes les files d'attente hôte|  
|BizTalk : MessageBox : compteurs généraux|MsgBoxName|Taille données de suivi|Taille de la table TrackingData de la MessageBox|  
|BizTalk : MessageBox : héberger des compteurs|PxHost:MsgBoxName|File d'attente hôte - Longueur|Nombre de messages dans la file d'attente hôte spécifiée|  
|BizTalk : MessageBox : héberger des compteurs|TxHost:MsgBoxName|File d'attente hôte - Longueur|Nombre de messages dans la file d'attente hôte spécifiée|  
|BizTalk : Agent des messages|RxHost|Taille des bases de données|Taille de la file d'attente de publication (PxHost)|  
|BizTalk : Agent des messages|PxHost|Taille des bases de données|Taille de la file d'attente de publication (TxHost)|  
|BizTalk : Agent des messages|HostName|État de limitation de remise de messages|Affecte les transports XLANG et sortants|  
|BizTalk : Agent des messages|HostName|État de limitation de publication de messages|Affecte les transports XLANG et entrants|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Analyse de limitation](../technical-guides/monitoring-for-throttling.md)