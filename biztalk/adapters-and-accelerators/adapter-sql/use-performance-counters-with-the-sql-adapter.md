---
title: "Utiliser des compteurs de Performance avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae381b78-d89e-4cf2-810b-821e49422463
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f81189e34346d377686dac79b44e5a9b34889dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="use-performance-counters-with-the-sql-adapter"></a>Utiliser des compteurs de Performance avec l’adaptateur SQL
[!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]les clients peuvent utiliser les compteurs de performance pour évaluer les performances des adaptateurs. Le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] programme d’installation crée la catégorie de compteur de performances «[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]», ainsi que l’installation du Pack d’adaptateurs.  
  
## <a name="the-lob-time-cumulative-performance-counter"></a>Le compteur de Performance du temps (cumulatif) LOB  
 Le **.NET l’adaptateur BizTalk pour SQL** catégorie possède un compteur de performances « Temps LOB (cumulé) ». Ce compteur de performance indique la durée, en millisecondes, prenant à la bibliothèque cliente SQL Server pour effectuer une action qui initialise de l’adaptateur. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] crée une instance du compteur de performance pour chaque action, d’un nom d’instance et base de données SQL Server spécifique. Les instances sont créées dans le modèle suivant :  
  
```  
<processId>:<appDomainId>:<endpointId>:<actionId>  
```  
  
 Le `<endpointId>` est dérivée en tant que `<sql_server_name>, <instance_name>, <database_name>`.  
  
 Le \<actionId\> est dérivée de la manière suivante :  
  
-   Pour ouvrir une connexion, l’ID d’action est « Open ».  
  
-   Pour les opérations entrantes, l’ID de l’action est « Entrant ».  
  
-   Pour les opérations sortantes, l’ID d’action est l’action de l’opération appelée, avec « / » remplacé par un trait de soulignement « _ ». En outre, l’ID d’action est préfixé avec le « ExecuteScalar », « ExecuteReader » ou « ExecuteNonQuery » selon la méthode que l’adaptateur utilise en interne pour effectuer l’opération sur la base de données SQL Server. Par exemple, l’adaptateur utilise en interne la **ExecuteReader** méthode à exécuter une procédure stockée dans SQL Server. Par conséquent, l’ID d’action pour la procédure stockée, MyProcedure, sera :  
  
    ```  
    ExecuteReader_Procedure_dbo_MyProcedure  
    ```  

 Le compteur de performance est initialisé uniquement après que l’adaptateur effectue le premier appel à la base de données SQL Server. En outre, le [InstanceLifetime a](https://msdn.microsoft.com/library/system.diagnostics.performancecounter.instancelifetime.aspx) du compteur de performance est définie sur « Processus », ce qui signifie que le compteur de performances cesse d’exister dès que le programme qui crée le compteur se termine.
  
> [!NOTE]
>  La précision du compteur de performance de temps LOB (cumulé) est 16 millisecondes.  
  
## <a name="enabling-performance-counters"></a>Activation des compteurs de performances  
 Les compteurs de performance peuvent être activés ou désactivés en définissant la propriété de liaison **EnablePerformanceCounters**. Pour activer les compteurs de performances, définissez la **EnablePerformanceCounters** liaison de propriété **True**. Pour désactiver les compteurs de performances, définissez **EnablePerformanceCounters** à **False**. Par défaut, la propriété est définie **False**. Pour plus d’informations sur cette propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
## <a name="performance-counters-and-the-wcf-lob-adapter-sdk"></a>Compteurs de performance et le Kit de développement logiciel de l’adaptateur LOB WCF  
 Modification de la valeur de la **EnablePerformanceCounters** également de propriété de liaison modifie la valeur du compteur de performance correspondant pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]. En outre, la propriété de liaison pour le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, tandis que pour les [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est dynamique. Par conséquent, s’il existe deux instances de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] de liaison dans le domaine d’application et le **EnablePerformanceCounters** liaison de la propriété est définie sur **True** dans un et **False** dans l’autre, le compteur spécifique à l’adaptateur sera activé dans un et désactivé pour l’autre. Toutefois, étant donné que la propriété de liaison pour [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] est statique, elle est soit définie **True** ou **False** selon quelle valeur a été spécifié en dernier.  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)