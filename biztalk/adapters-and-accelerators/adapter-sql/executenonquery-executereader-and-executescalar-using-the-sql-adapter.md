---
title: "Exécuter ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3fda0544-a028-4a95-aae6-1f6a90764c5d
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f68f4378a4d89d2a997f5a78a524e4f6bfca2c18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-executenonquery-executereader-and-executescalar-operations-using-the-sql-adapter"></a>Exécuter ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et à l’aide de l’adaptateur SQL
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose les opérations suivantes à la racine :  
  
-   **ExecuteNonQuery**: cette opération permet d’exécuter les instructions SQL arbitraires dans SQL Server si vous ne souhaitez pas que n’importe quel jeu de résultats à retourner. Vous pouvez cette opération permet de créer des objets de base de données ou modifier des données dans une base de données en exécutant UPDATE, INSERT ou DELETE. La valeur de retour de cette opération est de type de données Int32 et :  
  
    -   Pour les instructions UPDATE, INSERT et DELETE, la valeur de retour est le nombre de lignes affectées par l’instruction SQL.  
  
    -   Pour tous les autres types d’instructions, la valeur de retour est **-1**.  
  
-   **ExecuteReader**: cette opération permet d’exécuter les instructions SQL arbitraires dans SQL Server, si vous souhaitez que le jeu de résultats à retourner, si elle existe, comme un tableau de jeu de données. Pour plus d’informations sur le jeu de données, consultez « Classe DataSet » à [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).  
  
-   **ExecuteScalar**: cette opération permet d’exécuter les instructions SQL arbitraires dans SQL Server pour retourner une valeur unique. Cette opération retourne la valeur uniquement dans la première colonne de la première ligne du jeu de résultats retourné par l’instruction SQL.  
  
    > [!NOTE]
    >  L’avantage de ExecuteScalar ExecuteReader est que la charge de message de réponse de l’opération ExecuteScalar est beaucoup plus petit comparée à celui retourné par l’opération ExecuteReader. Par conséquent, si vous avez ne besoin qu’une seule valeur doit être retournée, vous devez utiliser ExecuteScalar au lieu de ExecuteReader.  
  
 Vous pouvez utiliser l’opération ExecuteNonQuery, ExecuteReader ou ExecuteScalar d’exécuter plusieurs instructions SQL.  
  
 Pour plus d’informations sur ces opérations à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185435(v=bts.10).aspx)