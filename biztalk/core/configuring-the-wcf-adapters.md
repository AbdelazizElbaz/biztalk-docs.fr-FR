---
title: Configuration des adaptateurs WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetTcpBinding [WCF adapters]
- configuring [WCF adapters]
- WCF adapters, pre-defined bindings
- configuring [WCF adapters], about configuring WCF adapters
- WsHttpBinding [WCF adapters]
- BasicHttpBinding [WCF adapters]
- NetNamedPipeBinding [WCF adapters]
- NetMsmqBinding [WCF adapters]
- bindings, pre-defined [WCF adapters]
- WCF adapters, configuring
ms.assetid: af01e2d4-303d-407a-b853-dd90b0246a8a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dde69bb5b2014a20509778e27230840e47c0b36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-the-wcf-adapters"></a>Configuration des adaptateurs WCF
Les adaptateurs BizTalk pour Windows Communication Foundation (WCF) permettent à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de communiquer avec les applications WCF. Les adaptateurs WCF BizTalk incluent cinq adaptateurs physiques qui représentent les liaisons prédéfinies WCF :**BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**,  **NetNamedPipeBinding**, et **NetMsmqBinding**. Les adaptateurs WCF pour les liaisons prédéfinies simplifient la définition des informations nécessaires pour la plupart des configurations d'application.  
  
 Les adaptateurs WCF BizTalk incluent également deux adaptateurs qui vous permettent de configurer librement les informations de liaison et de comportement WCF de l'emplacement de réception et du port d'envoi.  
  
 Tous les adaptateurs WCF possèdent des boîtes de dialogue de propriétés de transport similaires pour les ports d'envoi et les emplacements de réception. Toutefois, les tâches de configuration des adaptateurs WCF dépendent de l'adaptateur physique. Les tâches qui ne sont pas directement liées aux liaisons de l'adaptateur (telles que l'installation de certificats) sont identiques pour tous les adaptateurs WCF. Cette section présente les tâches communes à tous les adaptateurs WCF. Pour plus d’informations sur les tâches qui diffèrent pour chaque carte, consultez les rubriques correspondantes de l’adaptateur dans [adaptateurs WCF](../core/wcf-adapters.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)  
  
-   [Recommandations de sécurité pour les adaptateurs WCF](../core/wcf-adapters-security-recommendations.md)  
  
-   [Installation des certificats pour les adaptateurs WCF](../core/installing-certificates-for-the-wcf-adapters.md)  
  
-   [En spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md)  
  
-   [Comment activer les Points d’extensibilité WCF avec les adaptateurs WCF](../core/how-to-enable-the-wcf-extensibility-points-with-the-wcf-adapters.md)  
  
-   [Compteurs de Performance des adaptateurs WCF](../core/wcf-adapters-performance-counters.md)  
  
-   [Seule l’authentification prise en charge pour les adaptateurs WCF](../core/single-sign-on-support-for-the-wcf-adapters.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateurs WCF](../core/wcf-adapters.md)