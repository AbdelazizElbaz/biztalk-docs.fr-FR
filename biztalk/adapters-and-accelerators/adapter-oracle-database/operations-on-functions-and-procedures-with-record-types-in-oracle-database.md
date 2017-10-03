---
title: "Opérations sur les fonctions et procédures avec des Types d’enregistrements de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RECORD type
ms.assetid: 28ecb76c-de82-43df-83cc-917c482417b3
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46daadeaa5d1fc1060217f044a9d143488c38d7c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-functions-and-procedures-with-record-types-in-oracle-database"></a>Opérations sur les fonctions et procédures avec des Types d’enregistrements de base de données Oracle
Types d’enregistrements Oracle sont utilisés pour représenter des informations hiérarchiques dans les paramètres passés aux procédures et fonctions de PL/SQL. Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] met en évidence des types d’enregistrement en tant que types XML complexes. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge les types de types d’enregistrements suivants :  
  
-   Types d’enregistrements qui sont déclarés en tant que TABLE % ROWTYPE paramètres dans les procédures stockées et fonctions.  
  
-   Types d’enregistrements qui sont déclarés en tant que paramètres de TYPE d’enregistrement dans les packages de PL/SQL, par exemple, tapez rec_type1 est RECORD(name varchar2(100), age number(3));  
  
-   Types d’enregistrements qui contiennent des enregistrements imbriqués.  
  
-   Types d’enregistrements qui s’affichent, OUT ou paramètres dans des procédures ou des fonctions.  
  
-   Types d’enregistrements qui sont des valeurs de retour des fonctions.  
  
    > [!NOTE]
    >  Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ne prend pas en charge les types BFILE en tant que membres de l’enregistrement.  
  
 Pour plus d’informations sur :  
  
-   Appeler une fonction ou procédure impliquant des types d’enregistrements à l’aide du modèle de service WCF, consultez [exécuter les opérations à l’aide des Types d’enregistrements dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/using-record-types-in-oracle-database-using-the-wcf-service-model.md).  
  
-   Appel d’une fonction ou procédure impliquant l’enregistrement à l’aide des types [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [appeler des fonctions et procédures avec des Types d’enregistrements à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-functions-and-procedures-with-record-types-in-oracle-db-with-biztalk-server.md).  
  
-   Structure XML de l’enregistrement des types pris en charge par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], consultez [des schémas de Message pour les Types d’enregistrements](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-record-types.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)