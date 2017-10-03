---
title: "Opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70f3b863-da3c-45b0-98f2-469a62286ebf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e1d6d2c52ce0772297bb2834c13f31a55d7b7a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-tables-and-views-that-contain-large-data-types-using-the-sql-adapter"></a>Opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] fournit la prise en charge pour les types de données de grande taille de SQL Server suivants :  
  
-   Varchar (max)  
  
-   Nvarchar (max)  
  
-   Varbinary (max)  
  
 Pour lire les valeurs de données de grande taille à partir de SQL Server, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose l’opération de sélection.  
  
 Pour écrire des valeurs de données de grande taille dans SQL Server, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expose l’opération de définition < nom_colonne >, où < nom_colonne > est le nom de la colonne de type varchar (max), nvarchar (max) ou varbinary (max). L’opération Set < nom_colonne > permet également aux clients de carte d’écrire des données FILESTREAM dans SQL Server 2008.  
  
> [!NOTE]
>  L’opération Set < nom_colonne > est disponible uniquement pour les tables et les vues qui contiennent des colonnes avec un des trois types de données de grande taille mentionnés précédemment.  
  
 Pour plus d’informations sur l’exécution d’opérations sur les tables et les vues dans SQL Server qui contiennent des types de données de grande taille, consultez [opérations sur les tables et vues qui contiennent des types de données de grande taille à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/supported-operations-on-tables-and-views-with-large-data-types-with-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Se connecter à un système SAP à l’aide de l’adaptateur](../../adapters-and-accelerators/adapter-sap/connect-to-an-sap-system-using-the-adapter.md)