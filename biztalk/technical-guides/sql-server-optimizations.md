---
title: Optimisations de SQL Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb735b54-595e-4dd0-9e4d-9a5e7a007a78
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36317d99387fde1d7b5e1c56b45255129daedb25
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-optimizations"></a>Optimisations de SQL Server
BizTalk Server est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données jusqu'à 13 dans SQL Server. Étant un des principaux objectifs de création de BizTalk Server pour vous assurer qu’aucun message n’est perdu, BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC. Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server.  
  
Cette section décrit les méthodes générales pour optimiser les performances de SQL Server, ainsi que des méthodes pour optimiser les performances de la base de données qui sont spécifiques à un environnement BizTalk Server. Les liens suivants sont aussi bonnes ressources : 

- [BizTalk Server : Recommandations pour l’installation, le dimensionnement, déploiement et maintenance d’une Solution](https://social.technet.microsoft.com/wiki/contents/articles/666.biztalk-server-recommendations-for-installing-sizing-deploying-and-maintaining-a-solution.aspx)

- [Guide d’optimisation des performances BizTalk Server](biztalk-server-2013-performance-optimization-guide.md)

  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Préconfiguration des optimisations des bases de données](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [Postconfiguration des optimisations des bases de données](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [Optimisation des groupes de fichiers pour les bases de données](../technical-guides/optimizing-filegroups-for-the-databases1.md)