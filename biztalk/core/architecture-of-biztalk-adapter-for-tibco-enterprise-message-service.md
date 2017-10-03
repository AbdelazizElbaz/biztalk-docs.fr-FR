---
title: "Architecture de l’adaptateur BizTalk pour TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transmit adapter
- one-way receive operations
- architecture
- one-way send operations
- receive adapter
ms.assetid: 304c7236-aacd-4761-8c33-e876b53e84ff
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88c7bc6420efb67085e4f3a05f6daf0c5dbd2feb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-tibco-enterprise-message-service"></a>Architecture de l'adaptateur BizTalk pour TIBCO Enterprise Message Service
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service constitue un moyen d'échanger des données commerciales en temps réel entre les systèmes TIBCO EMS et BizTalk Server. L'adaptateur permet l'interaction entre une application XML et TIBCO EMS.  
  
 L'adaptateur accepte les messages XML qui permettent aux applications BizTalk de communiquer avec TIBCO EMS à l'aide d'un des éléments suivants :  
  
-   **Adaptateur de transmission**: utilise un port d’envoi unidirectionnel statique pour envoyer un message à TIBCO EMS.  
  
-   **Adaptateur de réception**: utilise un unidirectionnel statique port de réception pour recevoir des messages de TIBCO EMS.  
  
## <a name="one-way-send-operation"></a>Opération d'envoi unidirectionnelle  
 La figure suivante illustre l'architecture d'une opération d'envoi unidirectionnelle à l'aide de l'adaptateur BizTalk pour TIBCO EMS.  
  
 ![](../core/media/tibcoems-architecture-send.gif "TIBCOEMS_architecture_send")  
  
## <a name="one-way-receive-operation"></a>Opération de réception unidirectionnelle  
 La figure suivante illustre l'architecture d'une opération de réception unidirectionnelle à l'aide de l'adaptateur BizTalk pour TIBCO EMS.  
  
 ![](../core/media/tibcoems-architecture-receive.gif "TIBCOEMS_architecture_receive")  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de l’adaptateur](../core/adapter-features.md)   
 [Planification et Architecture](../core/planning-and-architecture16.md)