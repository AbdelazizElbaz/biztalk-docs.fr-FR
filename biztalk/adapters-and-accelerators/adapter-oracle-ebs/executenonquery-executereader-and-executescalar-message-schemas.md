---
title: "Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et ExecuteScalar Operations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8aa5fdb2-1e7f-4a34-a1e5-c16d8fb477d5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b42ed9075ad16708f835786fd1fd09b414d06ebb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-the-executenonquery-executereader-and-executescalar-operations"></a>Schémas de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar
Le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] expose les opérations sortantes ExecuteNonQuery, ExecuteReader et ExecuteScalar au niveau racine pour exécuter des instructions SQL arbitraires ou des blocs de PL/SQL dans Oracle E-Business Suite.  
  
 Pour plus d’informations sur :  
  
-   Ces opérations, consultez [prise en charge de ExecuteNonQuery, ExecuteReader, ExecuteScalar opérations et](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md).  
  
-   Effectuez ces opérations à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [ExecuteReader, ExecuteScalar ou opérations ExecuteNonQuery dans SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md).  
  
## <a name="message-structure-for-the-executenonquery-executereader-and-executescalar-operations"></a>Structure de message pour la méthode ExecuteNonQuery, ExecuteReader et d’opérations de ExecuteScalar  
 Les messages dans ces opérations suivent un modèle d’échange de message demande-réponse, et le tableau suivant illustre la structure de ces messages de demande et de réponse.  
  
> [!NOTE]
>  Consultez les descriptions de l’entité après le tableau.  
  
|Opération|Message XML|  
|---------------|-----------------|  
|ExecuteNonQuery demande|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQuery xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query>   <OutputRefCursorNames>     <string>[stringvalue1]</string>     <string>[stringvalue2]</string>     …   </OutputRefCursorNames> </ExecuteNonQuery>`|  
|ExecuteNonQuery réponse|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteNonQueryResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteNonQueryResult>[value]</ExecuteNonQueryResult>   <OutputRefCursors>     <DataSet>       <Any>[value]</Any>       <Any>[value]</Any>       …     </DataSet>   </OutputRefCursors> </ExecuteNonQueryResponse>`|  
|ExecuteReader demande|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReader xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteReader>`|  
|ExecuteReader réponse|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteReaderResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteReaderResult>     <Any>[value]</Any>     <Any>[value]</Any>       …   </ExecuteReaderResult> </ExecuteReaderResponse>`|  
|ExecuteScalar demande|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalar xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <Query>[PL/SQL block]</Query> </ExecuteScalar>`|  
|ExecuteScalar réponse|`<?xml version="1.0" encoding="utf-8" ?> <ExecuteScalarResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/GenericOperation/ ">   <ExecuteScalarResult>[value]</ExecuteScalarResult> </ExecuteScalarResponse>`|  
  
 Descriptions de l’entité :  
  
 [Bloc PL/SQL] = l’intégralité du bloc PL/SQL à exécuter.  
  
 [stringvalue1] = une valeur dans le tableau de chaînes.  
  
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