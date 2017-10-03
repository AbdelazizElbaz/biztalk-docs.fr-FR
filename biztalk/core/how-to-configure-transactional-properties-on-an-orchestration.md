---
title: "Comment configurer les propriétés transactionnelles sur une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- atomic transactions
- orchestrations, transactions
- transactions, long-running
- orchestrations, configuring
- transactions, atomic
ms.assetid: 8eec6019-4d96-4ed6-8a90-9403738d8af4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9164a9f5670a996a62450a19d802c97b89d8e242
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-transactional-properties-on-an-orchestration"></a>Comment configurer les propriétés transactionnelles sur une Orchestration
Une orchestration peut être traitée comme une transaction atomique, une transaction à long terme, ou aucune des deux.  
  
### <a name="to-make-your-orchestration-an-atomic-transaction"></a>Pour traiter votre orchestration comme une transaction atomique  
  
1.  Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.  
  
2.  Dans la fenêtre Propriétés, sélectionnez **atomique** dans la liste déroulante pour le **Type de Transaction** propriété.  
  
     **Lot**, **Compensation**, **niveau d’Isolation**, **réessayer**, **délai d’attente**, et **Transaction Identificateur** apparaissent en tant que propriétés dans la fenêtre Propriétés, exactement comme pour n’importe quelle étendue. Pour plus d’informations sur ces propriétés, consultez [comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md).  
  
### <a name="to-make-your-orchestration-a-long-running-transaction"></a>Pour traiter votre orchestration comme une transaction à long terme  
  
1.  Dans la fenêtre Vue Orchestration, sélectionnez **propriétés d’Orchestration**.  
  
2.  Dans la fenêtre Propriétés, sélectionnez **Long terme** dans la liste déroulante pour le **Type de Transaction** propriété.  
  
     **Compensation**, **délai d’attente**, et **identificateur de Transaction** apparaissent en tant que propriétés dans la fenêtre Propriétés. Pour plus d’informations sur ces propriétés, comme pour n’importe quelle étendue. Pour plus d’informations sur ces propriétés, consultez [comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Rendre les Orchestrations transactionnelles](../core/making-orchestrations-transactional.md)