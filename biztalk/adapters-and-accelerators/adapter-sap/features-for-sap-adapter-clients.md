---
title: "Fonctionnalités pour les clients de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic ports
- adapters, features
- XML data streaming
- performance counters
- adapters, support for dynamic ports in BizTalk Server
- adapters, support for message versioning
- adapters, support for XML data streaming
- adapters, support for performance counters
- adapters, support for configuring adapters using binding properties
ms.assetid: 9003c2c1-931d-405e-9a58-660032195af7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6516ff99f599d02cdf27aa7c0c07752747749021
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-sap-adapter-clients"></a>Fonctionnalités pour les clients de l’adaptateur SAP
Outre les fonctionnalités présentées dans toutes les rubriques de [présentation de l’Architecture de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md), le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] fournit également les fonctionnalités suivantes qui sont utiles pour les clients de la carte.  
  
-   **Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**. Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en spécifiant certaines propriétés de liaison. Par exemple, les clients peuvent configurer l’adaptateur pour spécifier le nombre maximal de connexions dans le pool de connexions de la carte en spécifiant une valeur pour le **MaxConnectionsPerSystem** propriété de liaison. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
-   **Prise en charge pour les ports dynamiques dans BizTalk Server**. Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message. Pour plus d’informations, consultez [configurer des ports dynamiques](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md).
  
-   **Prise en charge pour le versioning de messages**. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge message contrôle de version pour prendre en charge pour les schémas de message différent dans les versions futures de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [prise en charge du Versioning de Message](../../adapters-and-accelerators/adapter-sap/message-versioning-support1.md).  
  
    > [!NOTE]
    >  Cette fonctionnalité ne fournit pas de compatibilité descendante avec les versions précédentes de la carte.  
  
-   **Prise en charge pour les compteurs de performance**. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les compteurs de performances basée sur WCF pour une utilisation par les clients de la carte. Pour plus d’informations sur les compteurs de performance, consultez [utiliser des compteurs de performances avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/use-performance-counters-with-the-sap-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)