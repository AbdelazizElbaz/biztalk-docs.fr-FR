---
title: "Référence de message pour la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: process management solution tutorial, message reference
ms.assetid: 0595817e-da5d-426a-9ee1-0c5d04334de6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dff6d7397bc8dbb6ac9280736d59bb4ebdcc63f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-reference-for-the-business-process-management-solution"></a>Référence du message pour la Solution gestion des processus d’entreprise
Cette section répertorie les messages et types de messages utilisés par chaque orchestration dans la solution.  
  
 Dans la table, \< *SolutionPrefix*> remplace Microsoft.Samples.BizTalk.SouthridgeVideo pour faciliter la lecture de la table.  
  
> [!NOTE]
>  Un message de type **System.Xml.XmlDocument** indique un type de message défini par une classe .NET plutôt qu’un schéma.  
  
 Les orchestrations, les messages et les types sont les suivants.  
  
|Orchestration|Message|Type de message|  
|-------------------|-------------|------------------|  
|Activate.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|Activate.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|Analyze.odx|BadXmlOrderMsg|System.Xml.XmlDocument|  
|Analyze.odx|FixedXmlOrderMsg|System.Xml.XmlDocument|  
|Analyze.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|Analyze.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder1.odx|TerminatedMsg|\<SolutionPrefix >. SchemaClasses.Terminated|  
|CableOrder1.odx|OrderMgrMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|CableOrder1.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder1.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder1.odx|CompletionMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|CableOrder1.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|CableOrder1.odx|AckMsg|\<SolutionPrefix >. SchemaClasses.OrderAck|  
|CableOrder1.odx|InterruptMsg|\<SolutionPrefix >. SchemaClasses.Interrupt|  
|CableOrder2.odx|OrderMgrMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|CableOrder2.odx|TerminatedMsg|\<SolutionPrefix >. SchemaClasses.Terminated|  
|CableOrder2.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder2.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|CableOrder2.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|CableOrder2.odx|CompleteOrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|CableOrder2.odx|AckMsg|\<SolutionPrefix >. SchemaClasses.OrderAck|  
|CableOrder2.odx|CompletionMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|Cancel.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|Cancel.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|Cancel.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|Change.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|CheckInterrupt.odx|InterruptMsg|\<SolutionPrefix >. SchemaClasses.Interrupt|  
|Complete.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|Complete.odx|XmlOrderMsg|System.Xml.XmlDocument|  
|ErrorHandler.odx|InterruptMsg|\<SolutionPrefix >. SchemaClasses.Interrupt|  
|ErrorHandler.odx|OrderStatusMsg|\<SolutionPrefix >. SchemaClasses.OrderStatus|  
|ErrorHandler.odx|ResponseMsg|\<SolutionPrefix >. SchemaClasses.OrderStatus|  
|ErrorHandler.odx|OriginalMsg|System.Xml.XmlDocument|  
|ErrorHandler.odx|ReturnedMsg|System.Xml.XmlDocument|  
|ExceptionHandler.odx|OriginalMsg|System.Xml.XmlDocument|  
|Interrupter.odx|InterruptMsg|\<SolutionPrefix >. SchemaClasses.Interrupt|  
|OrderBroker.odx|CSRConfMsg|\<SolutionPrefix >. OrderBrokerSchemas.CSR_OrderRequestSchema|  
|OrderBroker.odx|CSROrderMsg|\<SolutionPrefix >. OrderBrokerSchemas.CSR_OrderRequestSchema|  
|OrderBroker.odx|HistoryInsertMsg|\<SolutionPrefix >. OrderBrokerSchemas.SQLHistoryInsertSchema.HistoryInsert|  
|OrderBroker.odx|ServicingMsg|\<SolutionPrefix >. OrderBrokerSchemas.Servicing_OrderRequestSchema|  
|OrderBroker.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
|OrderBroker.odx|OrderMgrMsg|\<SolutionPrefix >. OrderBroker.OrderMgrMPMsg|  
|OrderManager.odx|CompletionMsg|\<SolutionPrefix >. SchemaClasses.OrderStatus|  
|OrderManager.odx|NewOrderMgrMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|OrderManager.odx|OrderMgrMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|OrderManager.odx|OrderAck|\<SolutionPrefix >. SchemaClasses.OrderAck|  
|OrderManager.odx|TerminatedMsg|\<SolutionPrefix >. SchemaClasses.Terminated|  
|OrderManager.odx|ErrorMsg|\<SolutionPrefix >. OrderManager.OrderMgrMsgType|  
|Validate.odx|BadXmlOrderMsg|System.Xml.XmlDocument|  
|Validate.odx|FixedXmlOrderMsg|System.Xml.XmlDocument|  
|Validate.odx|OrderMsg|\<SolutionPrefix >. Schemas.OrderSchema|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de la Solution de gestion du processus métier](../core/business-process-management-solution-reference.md)   
 [Champs et les Messages de clé](../core/key-messages-and-fields.md)   
 [Flux de commandes par le biais du Gestionnaire de processus](../core/order-flow-through-the-process-manager.md)