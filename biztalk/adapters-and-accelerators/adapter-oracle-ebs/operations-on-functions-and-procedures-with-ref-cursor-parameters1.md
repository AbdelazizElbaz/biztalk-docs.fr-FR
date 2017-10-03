---
title: "Opérations sur les fonctions et procédures avec des REF CURSOR Parameters1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6801c1e-7992-40a0-bab7-87957840cedd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dee169bca7546c404edaccce6b7a1835e3c209a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-ref-cursor-parameters"></a>Opérations sur les fonctions et procédures avec des paramètres REF CURSOR
Un REF CURSOR est un type de données PL/SQL qui représente un pointeur vers un jeu de résultats côté serveur généré en exécutant une requête. Un type REF CURSOR permet d’entrée et de sortie de diffusion en continu de données et est idéal pour le transfert de grandes quantités de données vers et à partir d’un code de PL/SQL. 

## <a name="strongly-typed-and-weakly-typed-ref-cursors"></a>Fortement typée et faiblement typée REF CURSOR
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] fortement typée et faiblement typé (SYS_REFCURSOR) REF CURSOR qui peuvent être passés à des procédures de PL/SQL et les fonctions que dans les paramètres de sortie est prise en charge.  
  
-   **DANS LES REF CURSOR**. Clients de la carte doivent utiliser un IN REF CURSOR, vous devez fournir un code de PL/SQL (en tant que chaîne) qui s’ouvre de REF CURSOR à la base de données Oracle. L’adaptateur crée la variable et lui affecte le REF CURSOR ouvert et appelle une fonction ou une procédure avec cette variable. Par conséquent, les paramètres IN REF CURSOR dans PL/SQL de procédure stockée et les fonctions doivent être représentées sous forme de chaînes qui prennent un bloc de code PL/SQL en tant que valeur d’entrée, le marquage de la variable de sortie REF CURSOR avec un « ? ».  
  
-   **LES REF CURSOR**. LES REF CURSOR paramètres sont retournés sous la forme des jeux de résultats de fortement typée ou faiblement typée. Le type de jeu de résultats retourné dépend de si le paramètre REF CURSOR est déclaré comme un REF CURSOR fortement typée ou faiblement typée dans la définition de procédure ou fonction stockée sur le serveur Oracle.  
  
-   **DANS les paramètres des REF CURSOR**.  Étant donné que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] modélise les paramètres IN REF CURSOR comme des chaînes et des paramètres de sortie REF CURSOR en tant que types complexes, il ne peut pas prendre en charge un seul type d’un paramètre dans des REF CURSOR. Pour cette raison, il traite des paramètres dans des REF CURSOR comme deux paramètres différents : un paramètre IN dans le message de demande et d’un paramètre OUT dans le message de réponse.  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)