---
title: "Base de données Oracle interrogation à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c3aef30-956d-4585-b2de-7eebb919fab5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2578d00518a9f1632e690e84db04426575619109
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="poll-oracle-database-using-biztalk-server"></a>Base de données Oracle interrogation à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour recevoir des messages d’interrogation de la base de données Oracle. L’adaptateur offre deux moyens de l’interrogation de la base de données Oracle :  
  
-   **À l’aide des instructions SELECT**. Vous pouvez spécifier une instruction SELECT simple pour interroger les tables et les vues dans la base de données Oracle. L’adaptateur s’exécute l’instruction SELECT à des intervalles spécifiés et retourne le résultat pour les clients de la carte.  
  
-   **À l’aide de procédures stockées, des fonctions, ou des procédures ou des fonctions dans un package**. Vous pouvez spécifier une procédure stockée, fonction ou procédure ou une fonction dans un package pour interroger la base de données Oracle. L’adaptateur s’exécute le message de demande à des intervalles spécifiés et retourne le résultat pour les clients de la carte.  
  
 La principale différence dans les deux approches est que les clients de l’adaptateur de manière spécifient une instruction d’interrogation que l’adaptateur utilise pour interroger la base de données Oracle. Alors que l’instruction d’interrogation pour la première approche est une simple instruction SELECT, l’instruction d’interrogation pour l’autre approche est un message de demande qui exécute la procédure stockée, la fonction, ou la procédure ou la fonction dans un package. Les clients de carte spécifient l’instruction d’interrogation, pour des méthodes suivantes, dans le **PollingStatement** propriété de liaison. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
 Les rubriques de cette section fournissent des instructions sur la façon d’interrogation à l’aide d’une instruction SELECT et une procédure stockée, fonction ou procédure ou fonctionnent dans un package.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Base de données Oracle interrogation à l’aide de l’instruction SELECT](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-database-using-the-select-statement.md)  
  
-   [Base de données Oracle interrogation à l’aide de procédures stockées, fonctions, ou les procédures et fonctions](../../adapters-and-accelerators/adapter-oracle-database/poll-oracle-db-using-stored-procedures-functions-or-packaged-procedures.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)