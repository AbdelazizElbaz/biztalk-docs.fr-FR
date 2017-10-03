---
title: "Fonctionnalités pour les clients de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f638154b-0a09-4f89-9c52-2a62fafec7dc
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0d1df3a7d5c5748db4b0d3f365d80d84ff1f670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-sql-adapter-clients"></a>Fonctionnalités pour les clients de l’adaptateur SQL
Outre les fonctionnalités présentées dans toutes les rubriques de [vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md), le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] fournit également les fonctionnalités suivantes qui sont utiles pour les clients de la carte :  
  
-   **Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**. Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] en spécifiant certaines propriétés de liaison. Par exemple, les clients peuvent spécifier le nombre maximal de connexions autorisées dans un pool de connexions pour une chaîne de connexion spécifique en définissant le **MaxConnectionPoolSize** propriété de liaison. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
-   **Prise en charge des valeurs null pour les paramètres de l’opération**. Les clients de l’adaptateur peuvent fournir des valeurs null pour les paramètres de l’opération à l’aide de l’attribut « nillable » XSD.  
  
-   **Prise en charge pour les ports dynamiques dans BizTalk**. Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message. Pour plus d’informations, consultez [configurer des ports dynamiques](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md).  
  
-   **Prise en charge pour les compteurs de performance**. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge les compteurs de performances basée sur WCF pour une utilisation par les clients de la carte. Pour plus d’informations sur les compteurs de performance, consultez [utiliser des compteurs de performances avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/use-performance-counters-with-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/overview-of-biztalk-adapter-for-sql-server.md)