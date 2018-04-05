---
title: Qu'est-ce que l'évolutivité ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, scalability
ms.assetid: ac6acefd-864a-4f22-a136-a1951fe71e96
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a6208319fb8c195558101433cd1668ab0e0f064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-scalability"></a>Qu'est-ce que l'évolutivité ?
L'évolutivité est la capacité d'un système à se développer en fonction des besoins d'une entreprise. Le but est de pouvoir ajouter du matériel supplémentaire ou de mettre à niveau le matériel existant sans qu'il soit nécessaire d'effectuer des modifications importantes au niveau de l'application. Dans le contexte d'un système BizTalk Server, l'évolutivité fait référence à la capacité de BizTalk à s'adapter à l'augmentation de vos exigences en termes de débit et à répondre à votre besoin de réduire les temps d'attente.  
  
 Après l'optimisation et la personnalisation de différents composants de BizTalk, des engorgements au niveau des ordinateurs BizTalk ou de la base de données MessageBox restent possibles. Dans les environnements BizTalk, les engorgements sont généralement liés à l'UC, à la mémoire, aux E/S et aux conflits de verrouillage. Lorsque des engorgements commencent à se produire, vous devez soit mettre à niveau le matériel, soit ajouter de nouveaux équipements à la topologie existante. Par chance, l'architecture BizTalk Server facilite considérablement ces opérations. Vous pouvez, par exemple, ajouter plusieurs ordinateurs BizTalk Server au groupe et également ajouter des bases de données MessageBox supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md)   
 [Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md)   
 [Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md)   
 [L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md)   
 [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)   
 [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Bases de données à grande échelle](../core/scaled-out-databases.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)