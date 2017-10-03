---
title: "Comment configurer l’envoi de Pipelines pour TIBCO Enterprise Message Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines
- setting send pipelines
- pipelines, send
ms.assetid: 6a84d874-4b4d-4b23-913f-f5c72af1e96e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d037782e2580d52c6609c3669e2805aae92ce9eb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-send-pipelines-for-tibco-enterprise-message-service"></a>Configuration des pipelines d'envoi pour TIBCO Enterprise Message Service
L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service requiert la sélection de XMLTransmit et XMLReceive pour les pipelines d'envoi et de réception, respectivement.  
  
### <a name="to-set-pipelines"></a>Pour définir les pipelines  
  
1.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez souhaité application.  
  
2.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue zone, procédez comme suit :  
  
    1.  Tapez un nom pour le port d’envoi, par exemple, `SendToTIBCOEMS`.  
  
    2.  À partir de la **Type** la liste déroulante, sélectionnez **TIBCO EMS**.  
  
    3.  À partir de la **Gestionnaire d’envoi** liste déroulante, sélectionnez l’URI.  
  
    4.  Dans la liste déroulante Pipeline d’envoi, sélectionnez **Microsoft.BizTalk.DefaultPipelines.XMLTransmit**.  
  
    5.  À partir de la **Pipeline de réception** la liste déroulante, sélectionnez **Microsoft.BizTalk.DefaultPiplelines.XMLReceive**.  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure de Pipelines de réception pour TIBCO Enterprise Message Service](../core/how-to-set-receive-pipelines-for-tibco-enterprise-message-service.md)