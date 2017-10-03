---
title: Transactionnel Orchestrations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, compensations
- orchestrations, transactional
- Transaction Type property
ms.assetid: c4f0b6ca-d939-4d3a-b7ef-53c6aafdea9c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8c6fb466e0c3cc5cae4a076237d1dbc970b5794
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transacted-orchestrations"></a>Orchestrations traitées
Au même titre que les étendues, les orchestrations peuvent être transactionnelles. En fait, une orchestration peut être considérée comme une étendue. En général, les mêmes règles s'appliquent pour les orchestrations traitées et les étendues traitées.  
  
> [!NOTE]
>  L'une des différences existant entre les orchestrations et les étendues est que les premières ne disposent pas de gestionnaires d'exception.  
  
## <a name="orchestration-compensation"></a>Compensation d'orchestration  
 Si le **Type de Transaction** propriété de l’orchestration est définie à long terme ou atomique, vous pouvez également sélectionner une valeur pour le **Compensation** propriété, qui peut être par défaut ou personnalisé.  
  
 Si vous sélectionnez **personnalisé** pour la compensation, un **Compensation** onglet s’affiche à côté de l’aire de conception d’Orchestration. Cette surface aura la même apparence que la surface de conception de l'orchestration et vous pourrez y ajouter des formes et des ports de la même manière.  
  
 Les compensations n'ont lieu que sur les orchestrations appelées par d'autres orchestrations. Vous pouvez compenser une instance d’orchestration spécifique à l’aide de la **identificateur** propriété sur le **appeler Orchestration** forme.  
  
> [!IMPORTANT]
>  Si une compensation existe sur une orchestration de niveau supérieur, elle sera ignorée par le moteur d'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Rendre les Orchestrations transactionnelles](../core/making-orchestrations-transactional.md)   
 [L’utilisation de Transactions et la gestion des Exceptions](../core/using-transactions-and-handling-exceptions.md)