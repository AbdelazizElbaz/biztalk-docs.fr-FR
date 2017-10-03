---
title: "Opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues qui contiennent des données LOB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f6e8db6-ba68-4e3f-84b2-1cc31ce89bcb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a0804aa58174912a29cec9039d55579e4e705a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-interface-tables-interface-views-tables-and-views-that-contain-lob-data"></a>Opérations sur les Tables d’Interface, les vues de l’Interface, les Tables et les vues qui contiennent des données LOB
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] prend en charge les types de données Oracle LOB (large object) :  
  
-   Objet binaire volumineux (BLOB)  
  
-   Grand objet CLOB (Character)  
  
-   Objet volumineux de caractères nationaux (NCLOB)  
  
-   Fichier binaire (BFILE). Pour plus d’informations, consultez [opérations sur les Tables que contient BFILE des Types de données](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
  
 Dans la base de données Oracle, les types de données LOB sont utilisés pour stocker de grandes quantités de données, jusqu'à 4 gigaoctets (Go). À l’exception du type de données BFILE, types de données LOB prend en charge l’entrée et la sortie de diffusion en continu.  

## <a name="operations-for-tables-and-views"></a>Opérations pour les tables et vues  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] met en évidence les opérations suivantes pour les tables d’interface, les vues de l’interface, les tables et les vues qui contiennent des colonnes LOB :  
  
-   **Read_\<LOBColName >**: le `Read_<LOBColName>` opération apparaissent pour les tables d’interface, les vues de l’interface, les tables et les vues qui contiennent des colonnes BLOB, CLOB, NCLOB et BFILE, où \<LOBColName > est le nom de la colonne de type objet BLOB, CLOB, NCLOB et BFILE. À l’aide de la Read_\<LOBColName > opération, les clients de l’adaptateur peuvent lire des valeurs dans une colonne LOB sous la forme d’un flux de données. Cette opération prend une chaîne de filtre en tant que paramètre.  
  
    > [!NOTE]
    >  Le `Read_<LOBColName>` opération est conçue pour prendre en charge la diffusion en continu d’entrée des données LOB dans le modèle de service WCF. Vous devez utiliser une opération de sélection de table pour lire des données LOB à partir d’un modèle de canal WCF ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   **En attente_\<LOBColName >**: le `Update_<LOBColName>` opération apparaissent pour les tables d’interface et les tables uniquement contient des colonnes BLOB, CLOB et NCLOB, où \<LOBColName > est le nom de la colonne de type BLOB, CLOB, et NCLOB. À l’aide de l’en attente_\<LOBColName > opération, les clients de l’adaptateur peuvent mettre à jour les valeurs dans une colonne LOB. Pour le type de données objet BLOB, cette opération prend des données de base64binary encodée comme paramètre, alors que pour les types de données CLOB et NCLOB, cette opération prend un filtre de chaîne comme paramètre.  
  
    > [!NOTE]
    >  Le `Update_<LOBColName>` opération :  
    >   
    >  -   N’est pas prise en charge pour le type de données BFILE. Les clients de l’adaptateur peuvent également utiliser l’opération de mise à jour. Pour plus d’informations, consultez [opérations sur les Tables que contient BFILE des Types de données](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
    > -   N’est pas exposée pour les vues et les vues de l’interface.  
    > -   Doit être effectuée dans le cadre d’une transaction. Pour garantir cela, le **UseAmbientTransaction** liaison de la propriété doit être définie sur **True**. Pour plus d’informations sur la **UseAmbientTransaction** liaison de propriété, consultez [Rad sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
> [!IMPORTANT]
>  Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] surfaces un `Read_<LOBColName>` et une `Update_<LOBColName>` opération pour chaque colonne LOB dans une table. Par conséquent, s’il existe deux colonnes LOB dans une table (LOBCol1 et LOBCol2), vous avez deux `Read_<LOBColName>` operations (Read_LOBCol1 et Read_LOBCol2) et deux `Update_<LOBColName>` operations (Update_LOBCol1 et Update_LOBCol2).  
  
## <a name="more-good-info"></a>Plus d’informations correct  
  
-   Appel de la `Read_<LOBColName>` et `Update_<LOBColName>` opérations sur une table dans la base de données sous-jacente à l’aide d’Oracle E-Business Suite [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations sur des Tables avec les grandes données Types à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md).  
  
-   Structure et pour effectuer des actions SOAP des messages `Read_<LOBColName>` et `Update_<LOBColName>` opérations, consultez [des schémas de Message pour des opérations spéciales LOB](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-special-lob-operations1.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)