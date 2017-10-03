---
title: "Structure de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, MQSeries adapters
- MQSeries adapters, architecture
ms.assetid: d25caf6a-3f93-4164-9c92-489b919a624d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6239b78f0b9bd2c44a314b7ba0ba6ace8f3b78e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="structure-of-the-mqseries-adapter"></a>Structure de l’adaptateur MQSeries
L’adaptateur MQSeries comporte deux parties : l’adaptateur s’exécutant sous [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et une application COM +, MQSAgent, exécutée sous MQSeries Server pour Windows. Cette relation est représentée dans la figure suivante.  
  
 ![Composants de l’adaptateur MQSeries](../core/media/bts-dev-mqoverallstructure.gif "BTS_Dev_MQOverallStructure")  
  
 L'adaptateur communique avec l'application MQSAgent, qui communique avec MQSeries Server pour Windows. Vous pouvez installer l'agent sur le même ordinateur que l'adaptateur si vous y installez également MQSeries Server pour Windows.  
  
 Le côté envoi de l'adaptateur envoie le message à MQSAgent. MQSAgent puis, à l’aide de **MQPut**, envoie le message au Gestionnaire de file d’attente MQSeries.  
  
 Le côté réception de l'adaptateur interroge MQSAgent pour rechercher des messages. Lorsqu’un message, MQSAgent effectue une **MQGet** pour récupérer le message. MQSAgent inclut un intervalle d'attente codé en dur de trois secondes pour la récupération du message à partir du gestionnaire de file d'attente.  
  
> [!NOTE]
>  Vous pouvez définir l'intervalle d'interrogation de l'adaptateur. Lorsque vous définissez l'intervalle d'interrogation sur une valeur inférieure à trois secondes, l'intervalle d'attente est défini sur l'intervalle d'interrogation.  
  
 Les actions d'envoi et de réception des messages peuvent se produire dans les transactions. Ceci permet à l'adaptateur d'annuler le message et, le cas échéant, de retenter les opérations d'envoi ou de réception. Pour plus d’informations sur les transactions, consultez [le traitement par lot de l’adaptateur MQSeries et de traitement des transactions](../core/mqseries-adapter-batching-and-transaction-handling.md).  
  
 Le fait que l'adaptateur fonctionne sur plusieurs ordinateurs peut entraîner des problèmes de sécurité. Un programme hostile peut emprunter l'identité de l'agent et capturer des données. Pour plus d’informations sur la protection améliorée de la carte et l’agent, consultez [sécurité de l’adaptateur MQSeries](../core/mqseries-adapter-security.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur MQSeries](../core/mqseries-adapter-architecture.md)   
 [Nouveautés de l’adaptateur MQSeries ?](../core/what-is-the-mqseries-adapter.md)