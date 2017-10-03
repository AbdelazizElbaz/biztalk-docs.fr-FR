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
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783c09b1155202ac8fe5a964d16c24d33082c26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sql-server-optimizations"></a>Optimisations de SQL Server
BizTalk Server est extrêmement de base de données applications exigeantes qui peuvent nécessiter la création de bases de données jusqu'à 13 dans SQL Server. Étant un des principaux objectifs de création de BizTalk Server pour vous assurer qu’aucun message n’est perdu, BizTalk Server conserve les données sur le disque avec une fréquence élevée et en outre, le fait dans le contexte d’une transaction MSDTC. Par conséquent, les performances de la base de données est primordiale pour les performances globales d’une solution BizTalk Server.  
  
 Cette section décrit les méthodes générales pour optimiser les performances de SQL Server, ainsi que des méthodes pour optimiser les performances de la base de données qui sont spécifiques à un environnement BizTalk Server. Pour plus d’informations sur l’optimisation de BizTalk les performances de base de données, consultez l’article TechNet de l’optimisation de base de données BizTalk à [http://go.microsoft.com/fwlink/?LinkId=118001](http://go.microsoft.com/fwlink/?LinkId=118001).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Base de données de la Configuration préalable Optimizations1](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [À la Configuration de base de données Optimizations1](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [Optimisation des groupes de fichiers pour le Databases1](../technical-guides/optimizing-filegroups-for-the-databases1.md)