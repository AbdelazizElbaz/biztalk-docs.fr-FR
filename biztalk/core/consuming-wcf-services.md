---
title: Utilisation des Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- WCF services, consuming
ms.assetid: ca6c0514-c1df-43ad-8f02-df117271b0b5
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3fc0764295cbbc793b07757691e1f0c730a4049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="consuming-wcf-services"></a>Utilisation des services WCF
L'utilisation de services WCF vous permet d'ajouter des services WCF existants à vos processus d'entreprise. Vous pouvez agréger plusieurs services WCF au sein d'une seule orchestration.  
  
 Vous pouvez utiliser (appeler) un service WCF depuis votre orchestration à l'aide de l'Assistant Consommation de service WCF BizTalk. Celui-ci crée les types de ports et de messages nécessaires à l'utilisation des services WCF. L'Assistant Consommation de service WCF BizTalk crée deux fichiers de liaison qui peuvent être importés à l'aide de l'outil de ligne de commande de développement ou de l'Assistant pour configurer les ports d'envoi avec les adaptateurs WCF de la liaison fournie par le système et l'adaptateur WCF-Custom. Il vous permet d'utiliser les en-têtes SOAP avec un service WCF consommé, de modifier l'URI d'un service WCF consommé et de définir de manière dynamique le service WCF pour un service Web consommé. Les adaptateurs d'envoi WCF utilisent les services WCF et les emplacements de réception WCF publient les services WCF.  
  
 Les adaptateurs d’envoi WCF BizTalk incluent cinq adaptateurs d’envoi physiques qui représentent les liaisons prédéfinies WCF **BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, et **NetMsmqBinding**. Les adaptateurs WCF BizTalk incluent également les adaptateurs personnalisés qui vous permettent de configurer librement les informations de liaison et de comportement WCF d'un port d'envoi. Pour plus d’informations sur la façon de configurer un gestionnaire d’envoi WCF et le port d’envoi, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Considérations relatives à l’utilisation des Services WCF avec WCF des adaptateurs d’envoi](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)  
  
-   [En-têtes SOAP avec les Services WCF utilisés](../core/soap-headers-with-consumed-wcf-services.md)  
  
-   [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [Comment utiliser l’Assistant consommation de Service WCF BizTalk pour utiliser un Service WCF](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)  
  
-   [Comment gérer les contrats d’erreurs typées dans les Orchestrations](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)  
  
-   [Spécification des Actions SOAP pour WCF des adaptateurs d’envoi](../core/specifying-soap-actions-for-wcf-send-adapters.md)