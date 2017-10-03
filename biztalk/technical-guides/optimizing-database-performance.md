---
title: "Optimisation des performances de la base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a95caf60-f1f5-458f-8a81-0aead88f07be
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe9148c5b14c5c915de9a8d16699856922e051a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-database-performance"></a>Optimisation des performances de la base de données
BizTalk Server est une application de beaucoup de ressources de base de données qui peut nécessiter la création de bases de données jusqu'à 13 dans SQL Server. Étant un des principaux objectifs de création de BizTalk Server pour vous assurer qu’aucun message n’est perdu, BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC. Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server.  
  
 Cette section décrit les méthodes générales pour optimiser les performances de SQL Server, ainsi que des méthodes pour optimiser les performances de la base de données qui sont spécifiques à un environnement BizTalk Server. Pour plus d’informations sur l’optimisation des performances de base de données BizTalk, consultez le [livre blanc sur l’optimisation de base de données BizTalk](http://go.microsoft.com/fwlink/?LinkId=101578) (http://go.microsoft.com/fwlink/?LinkId=101578).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Base de données de la Configuration préalable Optimizations2](../technical-guides/pre-configuration-database-optimizations2.md)  
  
-   [À la Configuration de base de données Optimizations2](../technical-guides/post-configuration-database-optimizations2.md)  
  
-   [Optimisation des groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)  
  
-   [Script de groupes de fichiers SQL de base de données MessageBox de BizTalk Server](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md)  
  
-   [Analyse des performances de SQL Server](../technical-guides/monitoring-sql-server-performance.md)