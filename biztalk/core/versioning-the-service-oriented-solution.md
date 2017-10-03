---
title: "Le contrôle de version du Service orienté solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, service solutions
- service solution tutorial, versioning
ms.assetid: 0e09720f-53f2-4b38-aae3-a79ddfd35be5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af1c5d1475fc37322be9a8483963bbfd1432fbb4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="versioning-the-service-oriented-solution"></a>Solution orientée services de contrôle de version du Service
Les deux orchestrations qui agissent comme frontaux à la solution, **CustomerServiceReceiveSend** et **CustomerServiceNativeRequestResponse**, appelez le centre, l’orchestration de travail,  **CustomerService**. Les appels de l'orchestration dépendent du numéro de version de l'assembly contenant l'orchestration. Comme les trois orchestrations sont situées dans le même assembly, il n'existe aucun problème de contrôle de version.  
  
 En outre, le processus d'entreprise implémenté par les orchestrations est un processus de requête-réponse de très courte durée, qui se termine rapidement. C'est pourquoi, la question du contrôle de version du processus d'entreprise ne se pose pas dans cette solution : en effet, les orchestrations sont associées à un assembly unique et une version unique.  
  
 Cependant, les orchestrations utilisent bien les schémas de l'assembly de schéma. Si les schémas sont révisés et compilés dans une autre version, vous devez recompiler les orchestrations avec la dernière version de l'assembly de schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md)