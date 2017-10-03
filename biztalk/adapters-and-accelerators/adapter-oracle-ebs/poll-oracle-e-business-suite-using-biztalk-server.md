---
title: "Interrogation Oracle E-Business Suite à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a22b99a5-1715-4351-b0e0-6b8dcfacd9eb
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9b5d0743d39dfcf6cbab7e1da20a8a3fb1382fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-e-business-suite-using-biztalk-server"></a>Interrogation Oracle E-Business Suite à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour recevoir des messages d’interrogation de la base de données Oracle. L’adaptateur offre deux moyens de l’interrogation de la base de données Oracle :  
  
-   **À l’aide des instructions SELECT**. Vous pouvez spécifier une instruction SELECT simple pour interroger la base de données Oracle. L’adaptateur s’exécute l’instruction SELECT à des intervalles spécifiés et retourne le résultat pour les clients de la carte.  
  
-   **À l’aide de procédures stockées**. Vous pouvez spécifier une procédure stockée pour interroger la base de données Oracle. L’adaptateur exécute la procédure stockée à des intervalles spécifiés et retourne le résultat pour les clients de la carte.  
  
 La principale différence dans les deux approches est que les clients de l’adaptateur de manière spécifient une instruction d’interrogation que l’adaptateur utilise pour interroger la base de données Oracle. Alors que l’instruction d’interrogation pour la première approche est une simple instruction SELECT, l’instruction d’interrogation pour l’approche de la procédure stockée est un message de demande qui exécute la procédure stockée. Les clients de carte spécifient l’instruction d’interrogation, pour les deux approches, pour le **PollingInput** propriété de liaison. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 Les rubriques de cette section fournissent des instructions sur la façon d’interroger à l’aide d’une instruction SELECT et une procédure stockée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Interrogation Oracle E-Business Suite à l’aide d’une instruction SELECT](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-select-statement.md)  
  
-   [Interrogation Oracle E-Business Suite à l’aide de procédures stockées](../../adapters-and-accelerators/adapter-oracle-ebs/poll-oracle-e-business-suite-using-stored-procedures.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)