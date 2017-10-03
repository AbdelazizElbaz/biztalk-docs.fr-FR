---
title: "Mise à l’échelle verticale du niveau de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, examples
- scaling, scaling up
ms.assetid: 9002006a-f301-4e15-94b9-6caffd7c527c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55176072cd33e20dd1024bf2d9d1c39bca4567a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-up-the-biztalk-server-tier"></a>Montée en puissance par unité du niveau BizTalk Server
Pour faire évoluer verticalement le niveau BizTalk, vous devez mettre à niveau l'unité centrale, la mémoire, les E/S et d'autres ressources. L'exemple de la figure suivante montre comment procéder depuis un ordinateur biprocesseur vers un ordinateur quadriprocesseur.  
  
 ![Échelle &#45; haut BTS](../core/media/scaleupbts.gif "ScaleUpBTS")  
  
 Les scénarios d'évolution verticale du niveau BizTalk sont similaires à ceux utilisés pour l'évolution horizontale :  
  
-   BizTalk Server devient un goulot d'étranglement qui peut avoir pour origine un des problèmes suivants :  
  
-   UC : si le scénario utilise des pipelines, des mappages ou des orchestrations qui sollicitent beaucoup l'UC, les serveurs BizTalk Server n'auront pas de marge au niveau de l'UC.  
  
-   Mémoire et E/S : si les ordinateurs existants ont atteint leur limite maximale concernant la mémoire et les E/S, et que l'ordinateur doit être mis à niveau.  
  
-   Si l'évolution horizontale est trop onéreuse.  
  
-   Si l'évolution horizontale ne résorbe pas le goulot d'étranglement. Par exemple, elle n'a pas d'effet sur les goulots d'étranglement suivants :  
  
    -   transformations de messages volumineux ;  
  
    -   grand nombre de messages par échange ;  
  
    -   mémoire très sollicitée par certains composants BTS comme les pipelines ou les adaptateurs ;  
  
    -   transport, comme EDI.  
  
## <a name="when-you-cant-scale-up-the-biztalk-tier"></a>Cas dans lesquels l'évolution verticale du niveau BizTalk est impossible  
  
-   La base de données MessageBox est le goulot d'étranglement.  
  
-   Un adaptateur devient le goulot d'étranglement. Par exemple, si vous utilisez un adaptateur, une fois que vous augmentez le nombre de récepteurs BizTalk, les conflits de verrouillage peut augmenter sur l’application de serveur principal où l’adaptateur BizTalk est extrayant des données à partir de. Cela limite vos possibilités d'évolution verticale pour cet adaptateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md)   
 [L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md)   
 [Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md)   
 [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)   
 [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Bases de données à grande échelle](../core/scaled-out-databases.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)