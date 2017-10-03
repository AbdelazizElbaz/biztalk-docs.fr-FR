---
title: "L’évolution verticale du niveau SQL Server | Documents Microsoft"
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
- SQL Server, scaling
- scaling, scaling up
- scaling, strategies
ms.assetid: 4352c4af-6861-43d9-b433-9ca25668b439
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c654c4a3b1bba166ae8a49918f6ef31827cf041
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-up-the-sql-server-tier"></a>Évolution verticale du niveau serveur SQL Server
Dans ce modèle, la base de données SQL MessageBox existante est mise à niveau pour évoluer en fonction des exigences en matière de débit et de latence.  
  
 La figure suivante montre un scénario dans lequel la base de données principale MessageBox passe d'un serveur à quatre processeurs à un serveur à huit processeurs.  
  
 ![Échelle &#45; haut MSGBOX](../core/media/scaleupmsgbox2.gif "ScaleUpMsgBox2")  
  
## <a name="when-to-scale-up-the-sql-tier"></a>Quand faut-il effectuer une évolution verticale du niveau SQL ?  
  
-   Lorsque la base de données principale MessageBox peut évoluer verticalement.  
  
-   Lorsque la base de données principale MessageBox est à l'origine d'engorgements. Ces engorgements peuvent être notamment :  
  
    -   **Processeur** en cas de scénarios d’orchestration très coûteux et complexes, boîte de Message consomme des ressources du processeur élevées. Faire évoluer le serveur SQL verticalement en ajoutant des UC devrait faire évoluer le scénario.  
  
    -   **Mémoire ou e/s** mémoire ou e/s peut être goulot d’étranglement et peuvent être mis à niveau.  
  
-   Lorsque l'évolution verticale est moins chère que l'évolution horizontale, l'évolution verticale peut résoudre ces goulots d'étranglement. Par exemple, si la base de données principale MessageBox présente un problème de conflit de verrouillage SQL, l'évolutivité verticale ne peut pas résoudre ce problème.  
  
## <a name="when-do-you-decide-sql-cannot-scale-up"></a>Quand décidez-vous que SQL ne peut pas faire l'objet d'une évolutivité verticale ?  
 L'évolutivité verticale ne peut pas résoudre les engorgements liés à un conflit de verrouillage se produisant sur le niveau SQL. Si ce type d'engorgement se produit, l'évolutivité horizontale est une meilleure option que l'évolutivité verticale.  
  
## <a name="strategies-and-considerations-for-scaling-up-the-sql-tier"></a>Stratégies et considérations pour l'évolutivité verticale du niveau SQL  
  
-   Faites évoluer verticalement la base de données principale MessageBox, puis horizontalement.  
  
-   La base de données MessageBox maître sera finalement le goulot d’étranglement. Pour cette raison, elle devrait être plus rapide et plus conséquente (par exemple, un ordinateur Itanium 64 bits ou x64 à processeur double).  
  
## <a name="see-also"></a>Voir aussi  
 [Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md)   
 [Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md)   
 [Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md)   
 [Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md)   
 [Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md)   
 [Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md)   
 [À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md)   
 [Bases de données à grande échelle](../core/scaled-out-databases.md)   
 [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)