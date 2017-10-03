---
title: "Mise à l’échelle de vos Solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, scaling
- scaling, scaling out
- scaling, performance
- scaling, about scaling
- scaling, scaling up
- scaling
ms.assetid: e2acbaa4-29d3-4c89-ac1f-c0641cfa0442
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5417e303ea8486ef5bdee8e57c66d4783fb197ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-your-solutions"></a>Mise à l'échelle des solutions
L'architecture BizTalk Server offre de grandes possibilités d'évolutivité. Les modèles d'évolutivité que vous choisissez dépendent de la complexité de votre scénario, de votre matériel et de vos exigences en termes de débit et de latence. Il est préférable de démarrer par une petite topologie, puis d'essayer de procéder à une évolution horizontale ou verticale en suivant les instructions fournies dans cette section.  
  
## <a name="scaling-out-and-scaling-up"></a>Évolutions horizontale et verticale  
 Il existe deux manières de faire évoluer votre système BizTalk Server :  
  
-   L'évolution horizontale consiste à ajouter des ordinateurs supplémentaires. Par exemple, si BizTalk Server est engorgé au niveau des ressources d'UC, l'ajout d'un autre serveur double ces ressources et éventuellement le débit.  
  
-   L'évolution verticale consiste à mettre à niveau l'ordinateur existant. Par exemple, vous pouvez transformer un ordinateur 4 processeurs BizTalk Server en un ordinateur 8 processeurs.  
  
 Un système BizTalk Server possède deux niveaux : le niveau de BizTalk Server et le niveau de SQL Server, qui contient vos bases de données MessageBox. Dans n'importe quel scénario, vous pouvez procéder à l'évolution verticale ou horizontale de chaque niveau. Autrement dit, vous pouvez procéder à l'évolution horizontale ou verticale de BizTalk Server et de la base de données MessageBox.  
  
 Dans de nombreux cas, le niveau BizTalk commence par devenir un engorgement ; vous cherchez alors à en améliorer les performances en procédant à son évolution horizontale. Pourtant, à un certain point, en fonction de la complexité de votre système et du matériel utilisé, vous ne pouvez plus procéder à l'évolution horizontale du niveau BizTalk ; le niveau SQL Server devient alors l'engorgement. Vous procédez alors à l'évolution verticale du niveau SQL Server, puis à son évolution horizontale en lui ajoutant d'autres bases de données MessageBox.  
  
> [!NOTE]
>  Une nouvelle base de données MessageBox ne signifie pas nécessairement ici un autre serveur. Un même serveur SQL Server peut posséder plusieurs bases de données MessageBox. De même, plusieurs bases de données MessageBox engendrent des coûts DTC et un tronçon réseau si elles se trouvent sur des ordinateurs différents.  
  
 En théorie, vous pouvez faire évoluer horizontalement le niveau SQL Server indéfiniment tant que la base de données principale MessageBox n'est pas saturée.  
  
 Les rubriques de cette section décrivent ces modèles d'évolution de façon plus détaillée. Elles expliquent également comment adapter chaque modèle et déterminer à partir de quel moment vous ne pouvez plus utiliser un modèle pour faire évoluer votre système.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Quelle est l’évolutivité ?](../core/what-is-scalability.md)  
  
-   [Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md)  
  
-   [Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md)  
  
-   [Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md)  
  
-   [L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)   
 [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Bases de données à grande échelle](../core/scaled-out-databases.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)