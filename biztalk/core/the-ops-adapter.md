---
title: "L’adaptateur Ops | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, Ops adapters
- Ops adapters, about Ops adapters
- Ops adapters
- process management solution tutorial, Ops adapters
- process management solution tutorial, errors
ms.assetid: 7f747a5f-14af-4e4c-bc29-f083f8f00bd0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67463adf4e1e960ab6608e67595a679804aa223e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-ops-adapter"></a>L’adaptateur Ops
La conception de la solution permet, dans la mesure du possible, de transmettre aux systèmes d'opérations les messages et les erreurs posant problème afin que ceux-ci prennent une décision concernant la résolution de l'erreur ou l'arrêt de la commande. L'adaptateur Ops, combiné à la nouvelle fonctionnalité de rapports d'erreurs, traite la plupart de ces cas.  
  
 La solution fait appel à l'adaptateur sur un port configuré de manière à utiliser la fonctionnalité de rapports d'erreurs. Lorsqu’il reçoit une erreur, l’adaptateur appelle deux méthodes, **initialiser** et **Execute**, d’une classe dans un assembly spécifié. Dans la solution, ces méthodes envoient l'erreur au groupe d'opérations approprié.  
  
 La solution inclut un exemple de gestionnaire, bien que vous puissiez facilement écrire le vôtre et l'utiliser dans d'autres solutions. Pour obtenir des informations générales sur la nouvelle fonctionnalité de création de rapports d’erreurs, consultez [à l’aide d’Échec de routage des messages](../core/using-failed-message-routing.md).  
  
> [!NOTE]
>  L’adaptateur Ops est générée à l’aide de l’infrastructure d’adaptateurs. Pour plus d’informations sur la création de cartes avec l’infrastructure, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).  
  
 Cette section présente le fonctionnement ainsi que la configuration de l'adaptateur et fournit des détails sur les assemblys du gestionnaire d'erreurs. En conclusion, vous trouverez des détails sur l'implémentation qui peuvent s'avérer utiles aux utilisateurs souhaitant modifier l'adaptateur ou l'utiliser dans d'autres applications.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À l’aide de l’adaptateur Ops](../core/using-the-ops-adapter.md)  
  
-   [Le Gestionnaire d’erreurs Operations exemple](../core/the-sample-operations-error-handler.md)  
  
-   [Détails d’implémentation adaptateur OPS](../core/ops-adapter-implementation-details.md)