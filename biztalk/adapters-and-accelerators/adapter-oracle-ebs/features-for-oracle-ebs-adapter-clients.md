---
title: "Fonctionnalités pour les clients de l’adaptateur Oracle eBusiness Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50256fb7-5f0c-4b32-87e6-98f49da0b360
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2da086390fe049a5333dda40a35e19f46298dda1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="features-for-oracle-ebs-adapter-clients"></a>Fonctionnalités pour les clients de l’adaptateur Oracle eBusiness Suite
Outre les fonctionnalités présentées dans toutes les rubriques de [vue d’ensemble de l’adaptateur BizTalk pour Oracle E-Business Suite](http://msdn.microsoft.com/library/4f18fa2e-4e97-4c28-b38d-fc39ac53789e), le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] fournit également les fonctionnalités suivantes qui sont utiles pour les clients de la carte :  
  
-   **Prise en charge de la configuration des cartes à l’aide des propriétés de liaison**. Les clients de l’adaptateur peuvent configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] en spécifiant certaines propriétés de liaison. Par exemple, les clients peuvent configurer l’adaptateur pour utiliser le pool de connexions ODP.NET en définissant le **UseOracleConnectionPool** propriété de liaison. Pour plus d’informations, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
-   **Prise en charge des valeurs null pour les paramètres de l’opération**. Les clients de l’adaptateur peuvent fournir des valeurs null pour les paramètres de l’opération à l’aide de l’attribut « nil » dans le code XML d’entrée.  
  
-   **Prise en charge pour les ports dynamiques dans BizTalk**. Via BizTalk [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend en charge un port dynamique qui active le routage dynamique de messages de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] basée sur les propriétés de contexte de message. Pour plus d’informations, consultez [configurer les Ports dynamiques dans l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
[Comprendre l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)