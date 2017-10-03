---
title: "Opérations sur les fonctions et procédures avec des paramètres REF CURSOR dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IN REF CURSOR
- REF CURSOR
- OUT REF CURSOR
- IN OUT REF CURSOR
ms.assetid: 691c4aca-3454-41d6-b211-a4d37f215331
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a918553cd687d80a5898c7171981dffbcf7b092c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-ref-cursor-parameters-in-oracle-database"></a>Opérations sur les fonctions et procédures avec des paramètres REF CURSOR dans la base de données Oracle
Un REF CURSOR est un type de données PL/SQL qui représente un pointeur vers un jeu de résultats côté serveur généré en exécutant une requête. Un type REF CURSOR permet d’entrée et de sortie de diffusion en continu de données et est idéal pour le transfert de grandes quantités de données vers et à partir d’un code de PL/SQL. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fortement typée et faiblement typé (SYS_REFCURSOR) REF CURSOR qui peuvent être passés aux procédures PL/SQL et aux fonctions, OUT ou IN des paramètres est prise en charge.  
  
-   **DANS LES REF CURSOR**. Clients de la carte doivent utiliser un IN REF CURSOR, vous devez fournir un code de PL/SQL (en tant que chaîne) qui s’ouvre de REF CURSOR à la base de données Oracle. L’adaptateur crée la variable et lui affecte le REF CURSOR ouvert et appelle une fonction ou une procédure avec cette variable. Par conséquent, les paramètres IN REF CURSOR dans PL/SQL de procédure stockée et les fonctions doivent être représentées sous forme de chaînes qui prennent un bloc de code PL/SQL en tant que valeur d’entrée, le marquage de la variable de sortie REF CURSOR avec un « ? ».  
  
-   **LES REF CURSOR**. LES REF CURSOR paramètres sont retournés sous la forme des jeux de résultats de fortement typée ou faiblement typée. Le type de jeu de résultats retourné dépend de si le paramètre REF CURSOR est déclaré comme un REF CURSOR fortement typée ou faiblement typée dans la définition de procédure ou fonction stockée sur le serveur Oracle.  
  
-   **DANS les paramètres des REF CURSOR**. Étant donné que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] modélise les paramètres IN REF CURSOR comme des chaînes et des paramètres de sortie REF CURSOR en tant que types complexes, il ne peut pas prendre en charge un seul type d’un paramètre dans des REF CURSOR. Pour cette raison, il traite des paramètres dans des REF CURSOR comme deux paramètres différents : un paramètre IN dans le message de demande et d’un paramètre OUT dans le message de réponse.  
  
 Pour plus d’informations sur :  
  
-   Appel d’une fonction ou procédure impliquant des paramètres REF CURSOR à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [appeler des fonctions et procédures avec des REF CURSOR dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-ref-cursors-in-oracle-db-using-biztalk-server.md).  
  
-   Appeler une fonction ou procédure impliquant des paramètres REF CURSOR à l’aide du modèle de service WCF, consultez [exécuter les opérations à l’aide de REF CURSOR dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-operations-using-ref-cursors-in-oracle-database-using-the-wcf-service-model.md).  
  
-   Structure XML de REF CURSOR pris en charge par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [des schémas de Message pour REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à la base de données Oracle à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-oracle-database/connect-to-oracle-database-using-the-adapter.md)