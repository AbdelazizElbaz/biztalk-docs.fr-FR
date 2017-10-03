---
title: "Gestion des exceptions dans la Solution gestion des processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, tutorials
- process management solution tutorial, errors
ms.assetid: ac9fcb33-7dac-448e-88b8-04d4d439ea6a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1cd3134b8ed4e2fc6fd4a50d9b64397692ea32b7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exception-handling-in-the-business-process-management-solution"></a>Gestion des exceptions dans la Solution gestion des processus d’entreprise
La solution de gestion des processus d'entreprise utilise une orchestration spéciale de gestion des exceptions, ainsi que la gestion des exceptions standard de BizTalk Server. Pour les erreurs d'adaptateur, de pipeline, de mappage et de routage, elle utilise la nouvelle fonctionnalité de création de rapports d'erreurs. Ce système personnalisé repose sur le **ExceptionHandler** orchestration. La solution utilise le **ExceptionHandler** orchestration pour retenter une opération ou un appel susceptible de réussir après un problème temporaire.  
  
> [!NOTE]
>  Vous pouvez réutiliser le code à partir d’orchestrations, tel que **activer**, qui utilisent la **ExceptionHandler** orchestration. Toutes ces orchestrations incluent une étendue nommée **CallingCode** avec une **Exception** bloc. Remplacez le code dans le **CallingCode** étendue avec votre code. Le **Exception** bloc définit toutes les variables qui doivent appeler le **ExceptionHandler** orchestration. Vous devez modifier les valeurs affectées aux variables.  
  
 La solution utilise des exceptions personnalisées, ainsi que des exceptions BizTalk prédéfinies, pour les situations dans lesquelles l'erreur est irrécupérable (par exemple, message de commande malformé).  
  
> [!NOTE]
>  La solution utilise un adaptateur personnalisé pour la gestion des erreurs sur certains ports. Pour plus d’informations sur la carte, consultez [l’adaptateur Ops](../core/the-ops-adapter.md).  
  
 Cette section décrit la **ExceptionHandler** orchestration ainsi que les exceptions personnalisées. Par ailleurs, elle explique brièvement l'utilisation de la fonctionnalité de création de rapports d'erreurs par la solution.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [L’Orchestration ExceptionHandler](../core/the-exceptionhandler-orchestration.md)  
  
-   [Exceptions personnalisées](../core/custom-exceptions.md)