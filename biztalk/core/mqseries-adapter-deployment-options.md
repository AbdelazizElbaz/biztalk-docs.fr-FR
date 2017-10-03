---
title: "Options de déploiement de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, deploying
- deploying, MQSeries adapters
ms.assetid: d9380aff-40ea-419b-88e2-1e2ec3f023cb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88fa674c38df8b31c1954234846fd3939ed8568
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-deployment-options"></a>Options de déploiement de l’adaptateur MQSeries
L'adaptateur MQSeries vous permet de configurer votre matériel avec une grande flexibilité. Il existe au moins 3 principaux modèles d'utilisation :  
  
-   BizTalk Server, l'adaptateur, et MQSeries Server pour Windows sur le même ordinateur.  
  
-   BizTalk Server et l'adaptateur sur un premier ordinateur, et un serveur MQSeries pour Windows (y compris le MQSAgent) sur un second ordinateur, relié à un ou plusieurs ordinateurs supplémentaires qui exécutent un serveur MQSeries.  
  
-   Installations multiples de BizTalk Server dans un groupe et l'adaptateur, et le serveur MQSeries (y compris MQSAgent) sur un ordinateur séparé.  
  
-   L'adaptateur fonctionne correctement si vous mettez en cluster le serveur MQSeries et les gestionnaires de file d'attente MQSeries.  
  
    > [!NOTE]
    >  Dans ce cas, l'application MQSAgent COM+ ne doit pas être mise en cluster. A la place, l'application MQSAgent COM+ doit être installée et configurée au niveau des deux nœuds du cluster. Dans ce scénario, si l'application MQSAgent COM+ s'arrête, le prochain appel de la part du client la redémarre.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’adaptateur MQSeries](../core/using-the-mqseries-adapter.md)