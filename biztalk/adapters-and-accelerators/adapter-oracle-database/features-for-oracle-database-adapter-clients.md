---
title: "Fonctionnalités pour les clients de carte de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data streaming, support for
- binding properties
- adapter, features
- adapters, configuring
- message versioning, support for
- XML data streaming
- performance counters, support for
- dynamic ports in BizTalk, support for
- data streaming
ms.assetid: 63b52573-80a5-4206-95c3-478b86718fee
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b120c948ef3d9821af0a79e91fd718e3a1f33137
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-oracle-database-adapter-clients"></a>Fonctionnalités pour les clients de carte de base de données Oracle
Outre les fonctionnalités présentées dans toutes les rubriques de [vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md), le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fournit également les fonctionnalités suivantes qui sont utiles pour les clients de la carte :  
  
-   **Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**. Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] en spécifiant certaines propriétés de liaison. Par exemple, les clients peuvent configurer l’adaptateur pour utiliser le pool de connexions ODP.NET en définissant le **UseOracleConnectionPool** propriété de liaison. Pour plus d’informations, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
-   **Prise en charge des valeurs null pour les paramètres de l’opération**. Les clients de l’adaptateur peuvent fournir des valeurs null pour les paramètres de l’opération à l’aide de l’attribut « nil » dans le code XML d’entrée.  
  
-   **Prise en charge pour les ports dynamiques dans BizTalk**. Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message. Pour plus d’informations, consultez [configurer des ports dynamiques](../../adapters-and-accelerators/adapter-oracle-database/configure-dynamic-ports-in-the-oracle-database-adapter.md).  
  
-   **Prise en charge pour les compteurs de performance**. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge les compteurs de performances basée sur WCF pour une utilisation par les clients de la carte. Pour plus d’informations sur les compteurs de performance, consultez [les compteurs de Performance](../../core/performance-counters.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)