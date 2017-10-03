---
title: "Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et ExecuteScalar Operations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51f8cb98-8da8-40c1-bf87-4aad5a24bba2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0aaef682ad0528e8d22e043da94dc31e4f723f24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a>Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose les opérations sortantes ExecuteNonQuery, ExecuteReader et ExecuteScalar au niveau racine pour exécuter les instructions SQL arbitraires dans SQL Server.  
  
 Pour plus d’informations sur :  
  
-   Ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
-   Effectuez ces opérations à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a>Structure de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar  
 Les messages dans ces opérations suivent un modèle d’échange de message demande-réponse, et le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
|Opération|Message XML| Description|  
|---------------|-----------------|-----------------|  
|ExecuteNonQuery demande|`<ExecuteNonQuery xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">    <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query>  </ExecuteNonQuery>`|Dans la `<Query>` balise, vous pouvez spécifier plusieurs instructions de PL/SQL séparées par un point-virgule.|  
|ExecuteNonQuery réponse|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult> </ExecuteNonQueryResponse>`|Pour les instructions UPDATE, INSERT et DELETE, `[value]` représente le nombre de lignes affectées par les instructions de PL/SQL dans le *ExecuteNonQuery demande* message. Pour tous les autres types d’instructions, `[value]` est -1.|  
|ExecuteReader demande|`<ExecuteReader xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteReader>`|Dans la `<Query>` balise, vous pouvez spécifier plusieurs instructions de PL/SQL séparées par un point-virgule.|  
|ExecuteReader réponse|`<?xml version="1.0" encoding="utf-8" ?>  <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteReaderResult>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </ExecuteReaderResult> </ExecuteReaderResponse>`|Le jeu de résultats est le message de réponse des instructions PL/SQL exécutées dans le *ExecuteReader demande* de message et est retourné sous forme de tableau du jeu de données. Pour plus d’informations sur le jeu de données, consultez « Classe DataSet » à [http://go.microsoft.com/fwlink/?LinkID=196853](http://go.microsoft.com/fwlink/?LinkID=196853).|  
|ExecuteScalar demande|`<ExecuteScalar xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <Query>[PL/SQL STATEMENT1];[PL/SQL STATEMENT2];…</Query> </ExecuteScalar>`|Dans la `<Query>` balise, vous pouvez spécifier plusieurs instructions de PL/SQL séparées par un point-virgule.|  
|ExecuteScalar réponse|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/GenericTableOp/">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|Le `[value]` représente la valeur de la première colonne de la première ligne du jeu de résultats retourné par les instructions de PL/SQL dans le *ExecuteScalar demande* message.|  
  
 [Instruction PL/SQL] = l’instruction PL/SQL entière doit être exécuté.  
  
## <a name="message-action-for-the-executenonquery-executereader-and-executescalar-operations"></a>Action du message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar  
 Le tableau suivant répertorie les actions de message utilisés par les opérations ExecuteNonQuery, ExecuteReader et ExecuteScalar.  
  
|Opération|Action|  
|---------------|------------|  
|ExecuteNonQuery demande|GenericOp/ExecuteNonQuery|  
|ExecuteNonQuery réponse|GenericOp/ExecuteNonQuery/réponse|  
|ExecuteReader demande|GenericOp/ExecuteReader|  
|ExecuteReader réponse|GenericOp/ExecuteReader/réponse|  
|ExecuteScalar demande|GenericOp/ExecuteScalar|  
|ExecuteScalar réponse|GenericOp/ExecuteScalar/réponse|  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md)