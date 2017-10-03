---
title: "L’ajout d’une Compensation personnalisée à une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, compensations
- Compensate shape [Orchestration Designer]
- Compensate shape [Orchestration Designer], orchestrations
- Compensation property
- orchestrations, transactional
- orchestrations, customizing
- customizing, orchestrations
- Compensate shape [Orchestration Designer], custom compensation
ms.assetid: d153498d-8f98-42ae-90b9-e3083d669aef
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eadb9cba6e5a49be516a8095b01f93ca7a490f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-custom-compensation-to-an-orchestration"></a>L’ajout d’une Compensation personnalisée à une Orchestration
Une transaction d'orchestration configurée comme à long terme peut avoir un code de compensation personnalisé qui inverse ou annule ses effets. Si l’orchestration est terminée avec succès et a été appelée par une autre orchestration, l’orchestration d’appel peut appeler son bloc de compensation à l’aide un **compenser** forme.  
  
### <a name="to-specify-that-an-orchestration-will-use-custom-compensation"></a>Spécification qu'une orchestration utilisera une compensation personnalisée  
  
1.  Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.  
  
2.  Dans la fenêtre Propriétés, sélectionnez **personnalisé** dans la liste déroulante pour le **Compensation** propriété.  
  
     Le **Compensation** onglet s’affiche en regard du **Orchestration** onglet en bas de l’aire de conception.  
  
### <a name="to-design-custom-compensation-for-an-orchestration"></a>Conception d'une compensation personnalisée pour une orchestration  
  
1.  Cliquez sur le **Compensation** onglet en bas de l’aire de conception.  
  
     Le **aire de conception de Compensation** s’affiche.  
  
2.  Ajouter des formes pour le **aire de conception de Compensation** tout comme vous le feriez dans le **aire de conception d’Orchestration**.  
  
     Pour plus d’informations, consultez [Ajout de formes aux Orchestrations](../core/how-to-add-shapes-to-orchestrations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Rendre les Orchestrations transactionnelles](../core/making-orchestrations-transactional.md)