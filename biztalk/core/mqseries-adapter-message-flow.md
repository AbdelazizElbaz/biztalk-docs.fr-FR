---
title: Flux de messages de l’adaptateur MQSeries | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, message flow
ms.assetid: aa5c8523-afd6-4181-9c11-a150857a7790
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5df8549f99d376ea518b160ac1505aaac7feb5fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-message-flow"></a>Flux de messages de l’adaptateur MQSeries
Un message en provenance d'un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est d'abord transmis à un serveur MQSeries exécuté sous Windows. Le serveur MQSeries exécuté sous Windows peut se trouver sur l'ordinateur exécutant BizTalk Server. Le message est routé via l'ordinateur MQSeries Server pour Windows vers un hôte de serveur MQSeries sur un système d'exploitation tel qu'UNIX. Une application récupère ensuite le message dans la file d'attente MQSeries.  
  
 Un message en provenance d'une application est d'abord envoyé à une file d'attente MQSeries sur un serveur MQSeries. Le serveur MQSeries transmet le message à l'ordinateur MQSeries Server pour Windows. BizTalk Server reçoit le message de l'ordinateur MQSeries Server pour Windows et le transmet à l'application appropriée.  
  
 L'adaptateur MQSeries prend en charge les scénarios de messagerie suivants.  
  
|**Scénario**|**Description**|  
|------------------|---------------------|  
|Recevoir|L'adaptateur reçoit un message de MQSeries Server, qui est transmis à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|Envoi (port statique unidirectionnel)|L'adaptateur route un message en provenance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|Envoi dynamique|Permet à l'application de sélectionner une adresse de destination (URI) en cours d'exécution.|  
|Réception dynamique|Permet à l’application sélectionner une adresse source (URI) au moment de l’exécution en définissant le **MQSeries.DynamicReceive** propriété de contexte **Oui** et en spécifiant l’adresse de réception dynamique.|  
|Correlation|Les messages en provenance de l'adaptateur sont corrélés avec des instances spécifiques d'une orchestration, capables de gérer plusieurs types de message.<br /><br /> MQSeries Server peut créer l'identificateur de corrélation à l'aide d'une sollicitation-réponse, ou BizTalk Server peut créer l'identificateur de corrélation.<br /><br /> Pour plus d'informations sur les ensembles de corrélations, consultez l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
  
 Pour plus d'informations sur l'utilisation de ports et d'adaptateurs dans des pipelines, des orchestrations et le routage basé sur le contenu, consultez l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur l’utilisation des identificateurs de corrélation dans l’adaptateur, consultez [mise en corrélation de demande-réponse d’à l’aide des Messages](../core/correlating-messages-using-request-reply.md).  
  
 Pour plus d’informations sur les propriétés d’en-tête disponibles pour le filtrage dans l’adaptateur, consultez [propriétés associées à BizTalk Server](../core/properties-related-to-biztalk-server.md) et [propriétés de contexte MQSeries](../core/mqseries-context-properties.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’adaptateur MQSeries](../core/using-the-mqseries-adapter.md)