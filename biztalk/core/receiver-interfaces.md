---
title: "Interfaces de récepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7ab77d4-705a-4b39-8c33-a7532ae6484c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77b42530d721a6dcee52e082fe46deae9ae06405
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receiver-interfaces"></a>Interfaces de réception
En plus des interfaces d’adaptateur standard, adaptateurs de réception doivent implémenter **IBTTransportConfig**. C'est dans cette interface que le moteur de messagerie BizTalk fournit la configuration de l'emplacement de réception à l'adaptateur.  
  
## <a name="request-response-adapters"></a>Adaptateurs de requête-réponse  
 Les adaptateurs ont parfois également besoin de traiter des messages d'envoi. Les adaptateurs qui en sont capables sont généralement appelés adaptateurs bidirectionnels ou de requête-réponse. Pour être en mesure d’envoyer des messages, un adaptateur de réception doit implémenter **IBTTransmitter**.  
  
 L’illustration suivante montre les interfaces implémentées par les adaptateurs de réception.  
  
> [!NOTE]
>  Le **IBTBatchTransmitter** interface n’est pas prise en charge pour les adaptateurs de requête-réponse.  
  
 ![](../core/media/requestresponseadapters.gif "RequestResponseAdapters")