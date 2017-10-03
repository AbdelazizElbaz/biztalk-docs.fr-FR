---
title: "Opérations sur les tables et les vues qui contiennent des données dans la base de données Oracle LOB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data type
- binary file
- UpdateLOB
- ReadLOB
- LOB data types
- NCLOB
- large object
- binary large object
- CLOB
- national character large object
- BFILE
- BLOB
- character large object
ms.assetid: 25afd8c7-8ca3-4855-a231-2bec28c9a5cb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba5e110af598ac75ca9a8b6e7ebf2e5e8acc7aee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-tables-and-views-that-contain-lob-data-in-oracle-database"></a>Opérations sur les tables et vues qui contiennent des données LOB dans une base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge les types de données Oracle LOB (large object) :  
  
-   Objet binaire volumineux (BLOB)  
  
-   Grand objet CLOB (Character)  
  
-   Objet volumineux de caractères nationaux (NCLOB)  
  
-   Fichier binaire (BFILE). Pour plus d’informations, consultez [opérations sur les Tables contenant des Types de données BFILE](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
  
 Sur la base de données Oracle, les types de données LOB sont utilisés pour stocker de grandes quantités de données (jusqu'à 4 Go). Les types LOB prend en charge l’entrée et la sortie de diffusion en continu.  
  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence les opérations suivantes pour les tables et vues qui contiennent des colonnes LOB :  
  
-   **ReadLOB**. L’opération ReadLOB apparaissent pour les tables et vues qui contiennent des colonnes BLOB, CLOB, NCLOB et BFILE. À l’aide de l’opération ReadLOB, les clients de l’adaptateur peuvent lire des valeurs dans une colonne LOB comme un flux de données. Cette opération prend le nom de colonne de type de données LOB et une chaîne de filtre en tant que paramètres. Les clients de l’adaptateur doivent s’assurer que la chaîne de filtre extrait une ligne correspondante. S’il existe plus d’une ligne correspondante, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] retourne uniquement la colonne LOB de la première ligne (correspondance).  
  
    > [!NOTE]
    >  L’opération ReadLOB est conçue pour prendre en charge la diffusion en continu d’entrée des données LOB dans le modèle de service WCF. Vous devez utiliser une opération de sélection de table pour lire des données LOB à partir d’un modèle de canal WCF ou [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution. Pour plus d’informations sur la diffusion en continu, consultez [prise en charge de diffusion en continu pour les Types de données dans la base de données Oracle LOB](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md).  
  
-   **UpdateLOB**. L’opération UpdateLOB apparaissent pour les tables et vues qui contiennent des colonnes BLOB, CLOB et NCLOB. À l’aide de l’opération UpdateLOB, les clients de l’adaptateur peuvent mettre à jour les valeurs dans une colonne LOB. Cette opération prend le nom de colonne de type liée aux données LOB, une chaîne de filtrage, et base64binary codée comme paramètres. Les clients de l’adaptateur doivent s’assurer que la chaîne de filtre extrait une ligne correspondante ; dans le cas contraire le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] lève une XmlReaderParsingException.  
  
    > [!NOTE]
    >  L’opération UpdateLOB :  
    >   
    >  -   N’est pas prise en charge pour le type de données BFILE. Les clients de l’adaptateur peuvent également utiliser l’opération de mise à jour. Pour plus d’informations, consultez [opérations sur les Tables contenant des Types de données BFILE](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md).  
    > -   Doit être effectuée dans le cadre d’une transaction. Pour garantir cela, le **UseAmbientTransaction** liaison de la propriété doit être définie sur **True**. Pour plus d’informations sur la **UseAmbientTransaction** liaison de propriété, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
> [!NOTE]
>  ReadLOB et UpdateLOB fonctionnent sur une seule colonne LOB dans une seule ligne du tableau. Pour fonctionner sur des colonnes LOB dans plusieurs lignes ou sur plusieurs colonnes LOB dans une seule ligne, vous devez appeler ReadLOB ou UpdateLOB pour chaque colonne cible au sein de chaque ligne de la cible.  
  
 Pour plus d’informations sur :  
  
-   Appeler l’opération sur une table de base de données Oracle à l’aide de la UpdateLOB [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [effectuant des opérations sur les Tables avec des données de Types d’objet volumineuses par à l’aide de BizTalk Server](https://msdn.microsoft.com/library/cc185405(v=bts.10).aspx). (Vous devez utiliser une opération de sélection de table pour lire les types de données LOB dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].)  
  
-   Appeler des opérations ReadLOB et UpdateLOB sur une table de base de données Oracle à l’aide du modèle de service WCF, consultez [exécuter des opérations sur des Tables avec des Types d’objets volumineux à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sql/read-or-update-tables-and-views-with-large-data-types-in-sql-with-a-wcf-service.md).  
  
-   Structure et des actions SOAP pour effectuer des opérations ReadLOB et UpdateLOB des messages, consultez [des schémas de Message pour des opérations spéciales LOB](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185259(v=bts.10).aspx)