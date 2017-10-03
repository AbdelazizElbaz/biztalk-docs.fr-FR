---
title: "Exécuter des opérations composites dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b877d8e3-2016-40e8-888f-6b768021d6b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd5595823fab4f25948e3d88db759ae525f62130
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-composite-operations-in-oracle-database"></a>Exécuter des opérations composites dans la base de données Oracle
Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] permet aux clients d’adaptateur effectuer des opérations composites qui peuvent inclure plusieurs des opérations suivantes et dans n’importe quel ordre :  
  
-   Sélectionnez, Insert, Update et les opérations Delete sur les tables et les vues.  
  
-   Procédures stockées, fonctions et procédures ou fonctions dans des packages qui sont signalées en tant qu’opérations dans l’adaptateur.  
  
 Les opérations dans une opération composite peuvent cibler des tables et des vues dans la même base de données ou les bases de données différentes. Toutefois, les données ne peut pas être partagées ou réutilisées dans plusieurs opérations dans une opération composite. Par exemple, dans une opération composite, le jeu de résultats d’une opération de sélection ne peut pas être utilisé comme paramètre d’entrée pour une procédure stockée.  
  
 Chaque opération dans une opération composite est effectuée à l’aide d’une connexion distincte. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme autant de connexions à partir du pool de connexions ODP.NET en tant que le nombre d’opérations dans une opération composite et libère les connexions que les opérations sont exécutées. Toutefois, si une opération dans l’opération composite renvoie un jeu de résultats, la connexion est libérée uniquement après que le message est utilisé.  
  
> [!IMPORTANT]
>  Si vous rencontrez des problèmes de délai d’attente lors de l’exécution d’une opération composite ce peut être, car le nombre de connexions est inférieur au nombre d’opérations dans une opération composite impliquant :  
>   
>  -   Les procédures stockées contenant des BFILE, BLOB, CLOB, NCLOB et REF CURSOR comme OUT ou IN OUT.  
> -   Sélectionnez l’opération.  
>   
>  Pour résoudre ce problème, vous devez vous assurer que s’il existe le nombre de « n » de ces opérations dans une opération composite, la valeur spécifiée pour le **MinPoolSize** propriété de liaison est « n + 1 » ou supérieur. Pour plus d’informations sur la **MinPoolSize** liaison de propriété, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
 Pour plus d’informations sur :  
  
-   Comment effectuer des opérations composites dans [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [exécuter des opérations composites sur la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-composite-operations-on-oracle-database-using-biztalk-server.md).  
  
-   Schémas pour l’opération composite de messages, consultez [des schémas de Message pour l’opération Composite](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-composite-operation2.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)